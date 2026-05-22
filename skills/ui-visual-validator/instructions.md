# UI Visual Validator

Audita SVG o componentes HTML/CSS antes de renderizar o exportar. Detecta los errores
silenciosos que no lanzan excepciones pero rompen la visualización: líneas invisibles,
texto desbordado, elementos cortados, coordenadas fuera del canvas.

## Cuándo activar este skill

- Antes de convertir SVG a PDF
- Cuando un SVG "se ve raro" sin saber exactamente qué falla
- Después de generar SVG con código o IA para validar antes de entregar
- Cuando el cliente reporta que "algo se ve diferente" en su visor

## Checklist de auditoría SVG

### Estructura y semántica
```
[ ] viewBox definido en el tag <svg> raíz
[ ] xmlns="http://www.w3.org/2000/svg" presente
[ ] No hay IDs duplicados en el documento
[ ] Todos los href en <use> apuntan a IDs que existen en <defs>
[ ] Los <pattern> y <symbol> están dentro de <defs>
```

### Visibilidad de líneas
```
[ ] stroke-width > 0 en todas las líneas visibles (0 = invisible)
[ ] stroke-width >= 0.5 para líneas que deben verse en PDF impreso
[ ] No hay líneas con stroke="none" que debían ser visibles
[ ] No hay líneas con stroke="white" sobre fondo blanco
```

### Rellenos y fondos
```
[ ] Existe un <rect> de fondo blanco explícito como primer elemento del SVG
[ ] No hay fill="transparent" donde se esperaba un relleno visible
[ ] Los colores de fill y stroke no son iguales al color de fondo
[ ] Sin gradientes si el destino es PDF (reemplazar por fills sólidos)
```

### Coordenadas y recortes
```
[ ] No hay coordenadas negativas (elementos fuera del viewBox)
[ ] El viewBox abarca todos los elementos visibles más margen
[ ] Los grupos con transform="translate()" no empujan elementos fuera del canvas
[ ] Los <clipPath> no están recortando más de lo esperado
```

### Texto
```
[ ] font-family especificado (no depender del default del sistema)
[ ] font-size > 0 en todos los elementos <text>
[ ] No hay text con fill="none" (invisible) que debía ser visible
[ ] Los textos con text-anchor="middle" están centrados en el punto correcto
[ ] Textos largos no desbordan su contenedor — verificar con bounding box
```

### Compatibilidad PDF
```
[ ] Sin elementos <script> si el destino es PDF
[ ] Sin animaciones CSS si el destino es PDF
[ ] Sin filtros SVG complejos (blur, drop-shadow) si el destino es PDF
[ ] Fuentes son "seguras" (Arial, Helvetica, Times, Courier) o están embebidas
```

## Proceso de diagnóstico

### Paso 1 — Recibir el SVG y listar elementos

Contar y listar:
- Número de `<g>`, `<rect>`, `<line>`, `<text>`, `<use>`, `<path>`, `<circle>`
- IDs definidos en `<defs>`
- IDs referenciados en `href` y `fill="url(#...)"`

### Paso 2 — Verificar referencias cruzadas

Para cada `<use href="#id">`: ¿existe `<symbol id="id">` en `<defs>`?
Para cada `fill="url(#id)"`: ¿existe `<pattern id="id">` en `<defs>`?
Para cada `clip-path="url(#id)"`: ¿existe `<clipPath id="id">`?

### Paso 3 — Calcular bounding box del contenido

Recorrer todos los elementos y calcular:
```
x_min = mínimo de todos los x, cx - r
y_min = mínimo de todos los y, cy - r
x_max = máximo de todos los x + width, cx + r
y_max = máximo de todos los y + height, cy + r
```
Comparar con el viewBox declarado. Si algún elemento está fuera → reportar cuál.

### Paso 4 — Reportar hallazgos

Entregar el reporte en este formato:

```markdown
## Auditoría SVG — [nombre del archivo o descripción]

### Errores críticos (rompen la visualización)
- [descripción exacta del error + línea o elemento afectado]

### Advertencias (degradan la calidad)
- [descripción + impacto esperado]

### OK
- [qué está correcto y no requiere cambios]

### Acciones recomendadas
1. [acción concreta para el error 1]
2. [acción concreta para el error 2]
```

## Errores más comunes y sus síntomas

| Síntoma visual | Causa probable | Dónde buscar |
|---------------|----------------|--------------|
| Línea que no aparece | stroke-width="0" o stroke="none" | Todos los `<line>` y `<path>` |
| Elemento en esquina equivocada | transform mal aplicado o negativo | `<g transform="translate(...)">` |
| Texto ilegible | font-size muy pequeño o fill igual al fondo | Todos los `<text>` |
| Plano cortado en PDF | viewBox más pequeño que el contenido | Atributo viewBox del `<svg>` |
| Fondo negro en PDF | Sin `<rect fill="white">` explícito | Primer hijo del `<svg>` |
| Símbolo no renderiza | `<use>` apunta a ID inexistente | `<defs>` vs todos los `<use>` |
| Pattern sale como bloque sólido | `patternUnits` incorrecto | Atributo del `<pattern>` |

## Reglas

- Nunca marcar un SVG como "listo" sin pasar al menos los checks de líneas y coordenadas
- Si hay más de 3 errores críticos, corregir y re-auditar antes de exportar
- Los errores de fuente solo se descubren al abrir en un sistema diferente — siempre usar fonts seguras
- Un SVG que se ve bien en el navegador puede romperse en PDF por gradientes o filtros — siempre verificar en PDF también
