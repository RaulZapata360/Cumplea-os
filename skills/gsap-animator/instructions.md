# GSAP Animator

Genera animaciones web con GSAP (GreenSock): tweens, timelines y animaciones
vinculadas a scroll. Condensa los skills oficiales `gsap-core`, `gsap-timeline`
y `gsap-scrolltrigger` del repositorio `greensock/gsap-skills` en un solo flujo
de trabajo, con variaciones por framework.

## Cuándo usar GSAP (vs lenis/framer-motion)

| Necesidad | Herramienta |
|-----------|-------------|
| Secuencias complejas con control preciso (pausar, invertir, reescalar tiempo) | GSAP |
| Animación vinculada a scroll con pinning de secciones | GSAP + ScrollTrigger |
| Microinteracciones simples en React con física declarativa | framer/motion |
| Solo suavizar el scroll nativo sin animar elementos | lenis |
| Transiciones de layout automáticas entre estados de UI | framer/motion |

GSAP gana cuando hay timelines con muchos pasos, sincronización exacta con el
scroll, o necesitas controlar la animación imperativamente (play/pause/reverse/seek).

## Paso 1 — Tween básico

```js
import gsap from "gsap";

gsap.to(".caja", {
  x: 200,
  rotation: 360,
  duration: 1.5,
  ease: "power2.out",
});
```

### Vars comunes

| Var | Uso |
|-----|-----|
| `duration` | segundos |
| `delay` | segundos antes de iniciar |
| `ease` | `"power2.out"`, `"elastic.out(1, 0.3)"`, `"none"` para linear |
| `stagger` | retraso incremental entre elementos de un selector múltiple |
| `repeat` | `-1` para infinito |
| `yoyo` | `true` para alternar ida y vuelta |
| `onComplete` / `onStart` | callbacks |

### Transforms — siempre camelCase, siempre sobre transform, nunca sobre layout

```js
// Correcto — anima transform, no reflow
gsap.to(".caja", { x: 100, y: 50, scale: 1.2, rotation: 45 });

// Incorrecto — anima propiedades de layout, fuerza repintado costoso
gsap.to(".caja", { left: "100px", width: "200px" });
```

Alias de transform disponibles: `x`, `y`, `scale`, `scaleX`, `scaleY`, `rotation`, `skewX`, `skewY`.
`autoAlpha` combina `opacity` + `visibility` en una sola propiedad.

### Responsive con matchMedia

```js
gsap.matchMedia().add("(prefers-reduced-motion: no-preference)", () => {
  gsap.to(".caja", { x: 200, duration: 1 });
});
```

Siempre respetar `prefers-reduced-motion` — es un requisito de accesibilidad, no opcional.

## Paso 2 — Timeline para secuencias

```js
const tl = gsap.timeline({ defaults: { duration: 0.6, ease: "power2.out" } });

tl.to(".titulo", { autoAlpha: 1, y: 0 })
  .to(".subtitulo", { autoAlpha: 1, y: 0 }, "-=0.3")   // empieza 0.3s antes de que termine el anterior
  .to(".cta", { autoAlpha: 1, scale: 1 }, "<")          // empieza al mismo tiempo que el anterior
  .addLabel("seccionLista")
  .to(".item", { autoAlpha: 1, stagger: 0.1 });
```

### Parámetros de posición

| Sintaxis | Significado |
|----------|-------------|
| `"+=0.5"` | 0.5s después de que termina el tween anterior |
| `"-=0.3"` | 0.3s antes de que termine el tween anterior (overlap) |
| `"<"` | al mismo tiempo que el tween anterior empieza |
| `">"` | al mismo tiempo que el tween anterior termina |
| `"miEtiqueta"` | en la posición de una etiqueta nombrada |

## Paso 3 — ScrollTrigger para animación ligada al scroll

```js
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

gsap.to(".panel", {
  x: -500,
  ease: "none",
  scrollTrigger: {
    trigger: ".contenedor",
    start: "top top",
    end: "+=1000",
    scrub: true,      // ata el progreso de la animación al scroll, no al tiempo
    pin: true,         // fija la sección mientras dura el scroll
    markers: false,    // true solo durante desarrollo
  },
});
```

### Vars clave de ScrollTrigger

| Var | Uso |
|-----|-----|
| `trigger` | elemento que activa el scroll-trigger |
| `start` / `end` | `"top top"`, `"top center"`, `"+=500"` |
| `scrub` | `true` o un número (suavizado) — ata animación al scroll en vez del tiempo |
| `pin` | fija el elemento mientras la animación corre |
| `toggleActions` | `"play pause resume reset"` para controlar el comportamiento al entrar/salir del viewport |

## Variaciones por framework

### React — hook useGSAP
```jsx
import { useGSAP } from "@gsap/react";
import { useRef } from "react";
import gsap from "gsap";

function Componente() {
  const contenedorRef = useRef(null);

  useGSAP(() => {
    gsap.to(".caja", { x: 200, duration: 1 });
  }, { scope: contenedorRef });  // limpieza automática al desmontar

  return <div ref={contenedorRef}><div className="caja" /></div>;
}
```
`useGSAP` limpia automáticamente las animaciones al desmontar — evita memory leaks.
Para SSR (Next.js), envolver en `useGSAP` previene ejecución durante el render del servidor.

### Vue / Svelte — ciclo de vida manual
```js
// Vue: onMounted + onUnmounted
import { onMounted, onUnmounted } from "vue";
import gsap from "gsap";

let ctx;
onMounted(() => {
  ctx = gsap.context(() => {
    gsap.to(".caja", { x: 200 });
  });
});
onUnmounted(() => ctx.revert());
```
`gsap.context()` agrupa animaciones para poder revertirlas todas con `.revert()`
al desmontar — el equivalente manual de lo que `useGSAP` hace automático en React.

### Vanilla JS
Sin limpieza automática — si el elemento se remueve del DOM dinámicamente,
llamar `.kill()` sobre el tween o timeline explícitamente para evitar fugas.

## Reglas (anti-patrones)

- Nunca animar `width`, `height`, `top`, `left` — siempre usar transforms (`x`, `y`, `scale`)
- Nunca crear un ScrollTrigger sin `markers: false` en producción
- Nunca olvidar `gsap.registerPlugin(ScrollTrigger)` antes de usarlo
- Nunca ignorar `prefers-reduced-motion` — envolver animaciones decorativas en `matchMedia`
- En React, nunca animar fuera de `useGSAP` — se pierde la limpieza automática
- En Vue/Svelte, nunca omitir `.revert()` en el cleanup — causa animaciones fantasma al re-montar
- Nunca usar `scrub: true` y `repeat` en el mismo ScrollTrigger — son comportamientos incompatibles

## Output esperado

Código JS/TSX listo para integrar, con:
1. Import correcto de GSAP y plugins necesarios (`gsap.registerPlugin(...)`)
2. Cleanup apropiado según el framework detectado
3. Comentario indicando qué dispara la animación (scroll, mount, hover, click)
4. `matchMedia` si la animación es puramente decorativa (no funcional)

## Fuente

Condensado de los skills oficiales `gsap-core`, `gsap-timeline` y `gsap-scrolltrigger`
del repositorio [greensock/gsap-skills](https://github.com/greensock/gsap-skills)
(mantenido por el equipo de GreenSock). Para plugins adicionales (Flip, Draggable,
SplitText, ScrambleText, físicos) o utilidades (`clamp`, `mapRange`, `snap`),
consultar el repositorio original — no están cubiertos en este skill condensado.
