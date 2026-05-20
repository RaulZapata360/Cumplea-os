# Errores comunes en deploy Vercel

## 404 en rutas estáticas
- Causa: `vercel.json` sin `routes` definido.
- Fix: Agrega la entrada `routes` que redirige `(.*)` al archivo correspondiente.

## Build falla por env vars faltantes
- Causa: La app lee una env var en build time que no está configurada en Vercel.
- Fix: Ve a Settings → Environment Variables en el dashboard de Vercel y agrega la var.

## Imágenes no cargan
- Causa: Rutas relativas en HTML que no coinciden con la estructura de deploy.
- Fix: Usa rutas absolutas desde la raíz (`/images/foto.jpg` en vez de `images/foto.jpg`).

## Deploy cuelgado en BUILDING
- Causa: Dependencia que tarda mucho o loop infinito en build script.
- Fix: Revisa build logs con `get_deployment_build_logs` y busca el último mensaje antes del cuelgue.
