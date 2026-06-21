# Quick Start — Diseño Web

## Stack base recomendado

| Necesidad | Herramienta |
|-----------|-------------|
| Sitio estático / landing | HTML + Tailwind CSS |
| App con datos / interacción | Next.js + Tailwind |
| Deploy | Vercel |
| Fuentes | Google Fonts |
| Íconos | Lucide / Heroicons |
| Imágenes | Unsplash / assets propios en /public |

## Primer paso

1. Definir con el cliente: ¿es informativo (landing) o funcional (app)?
2. Revisar si existe un skill relevante en `skills/index.yaml` (tags: vercel, deploy, frontend).
3. Crear estructura de carpetas:
   ```
   /
   ├── index.html o app/
   ├── public/images/
   ├── vercel.json
   └── README.md
   ```
4. Usar la plantilla de `skills/example-deploy-vercel/files/vercel-static.json` para config de Vercel.

## Checklist antes de entregar

- [ ] El sitio carga en mobile (viewport meta tag)
- [ ] Imágenes optimizadas (< 200 KB por imagen si es posible)
- [ ] Deploy activo en Vercel con URL de producción
- [ ] Dominio configurado si aplica
- [ ] README con instrucciones mínimas

## Repositorios de referencia

### UI / Componentes
| Repositorio | Para qué |
|-------------|----------|
| [shadcn-ui/ui](https://github.com/shadcn-ui/ui) | Componentes Tailwind copiables: sistema de diseño profesional sin dependencia de paquete |
| [radix-ui/primitives](https://github.com/radix-ui/primitives) | Fundamentos de accesibilidad: foco, ARIA, estado interno de dropdowns y modales |
| [tremorlabs/tremor](https://github.com/tremorlabs/tremor) | Componentes de dashboard analítico listos: métricas, gráficas, KPIs |

### Animaciones y experiencia
| Repositorio | Para qué |
|-------------|----------|
| [darkroomengineering/lenis](https://github.com/darkroomengineering/lenis) | Smooth scrolling moderno; estándar en sitios Awwwards |
| [framer/motion](https://github.com/framer/motion) | Animaciones React con físicas reales y `useScroll` |
| [greensock/GSAP](https://github.com/greensock/GSAP) | Motor de animación más potente; ScrollTrigger para secuencias complejas |
| [locomotivemtl/locomotive-scroll](https://github.com/locomotivemtl/locomotive-scroll) | Parallax asíncrono y detección de elementos en viewport |

### 3D y generación de imágenes
| Repositorio | Para qué |
|-------------|----------|
| [mrdoob/three.js](https://github.com/mrdoob/three.js) | Renderizado 3D en navegador: modelos, texturas, animaciones |
| [pmndrs/drei](https://github.com/pmndrs/drei) | Helpers para react-three-fiber: cámara, HDRI, efectos 3D con scroll |
| [vercel/satori](https://github.com/vercel/satori) | Generar imágenes Open Graph dinámicas desde HTML/CSS |

### Stack y frameworks
| Repositorio | Para qué |
|-------------|----------|
| [vercel/next.js examples](https://github.com/vercel/next.js/tree/canary/examples) | Auth, DB, pagos, cientos de integraciones listas |
| [epicweb-dev/epic-stack](https://github.com/epicweb-dev/epic-stack) | Stack full-stack completo con mejores prácticas de seguridad y despliegue |
| [twentyhq/twenty](https://github.com/twentyhq/twenty) | Arquitectura CRM escalable con TypeScript/React |
| [pdovhomilja/nextcrm-app](https://github.com/pdovhomilja/nextcrm-app) | CRM completo: Next.js + Prisma + PostgreSQL + shadcn/ui |
| [diegomura/react-pdf](https://github.com/diegomura/react-pdf) | PDFs desde componentes React para reportes y entregas |

## Skills relevantes

- `example-deploy-vercel` — deploy a Vercel paso a paso
- `gsap-animator` — animaciones con GSAP: tweens, timelines, ScrollTrigger
- `web-artifacts-builder` — componentes SVG/HTML semánticamente correctos
