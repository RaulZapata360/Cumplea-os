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

## Skills relevantes

- `example-deploy-vercel` — deploy a Vercel paso a paso
