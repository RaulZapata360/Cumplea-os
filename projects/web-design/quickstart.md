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

| Repositorio | Para qué |
|-------------|----------|
| [shadcn-ui/ui](https://github.com/shadcn-ui/ui) | Componentes Tailwind copiables: sistema de diseño profesional sin dependencia de paquete |
| [radix-ui/primitives](https://github.com/radix-ui/primitives) | Fundamentos de accesibilidad: foco, ARIA, estado interno de dropdowns y modales |
| [vercel/satori](https://github.com/vercel/satori) | Generar imágenes Open Graph dinámicas desde HTML/CSS |
| [mrdoob/three.js](https://github.com/mrdoob/three.js) | Renderizado 3D en navegador: modelos, texturas, animaciones |
| [vercel/next.js examples](https://github.com/vercel/next.js/tree/canary/examples) | Auth, DB, pagos, cientos de integraciones listas |
| [twentyhq/twenty](https://github.com/twentyhq/twenty) | Arquitectura CRM escalable con TypeScript/React |
| [pdovhomilja/nextcrm-app](https://github.com/pdovhomilja/nextcrm-app) | CRM completo: Next.js + Prisma + PostgreSQL + shadcn/ui |
| [diegomura/react-pdf](https://github.com/diegomura/react-pdf) | PDFs desde componentes React para reportes y entregas |

## Skills relevantes

- `example-deploy-vercel` — deploy a Vercel paso a paso
