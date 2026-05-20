# Skill: Deploy a Vercel

**Cuándo usar este skill:** el usuario quiere publicar un proyecto web (estático, Next.js, Vite, etc.) en Vercel.

---

## Paso 1 — Verificar vercel.json

Confirma que existe `vercel.json` en la raíz. Si no existe, créalo.
Para proyectos estáticos usa la plantilla en `files/vercel-static.json`.

## Paso 2 — Variables de entorno

Si el proyecto usa `.env`, pregunta al usuario qué vars necesitan estar en producción antes de deployar. Nunca incluyas `.env` en el commit.

## Paso 3 — Deploy

Usa la herramienta MCP de Vercel (`mcp__...__deploy_to_vercel`) o el CLI:

```bash
vercel --prod
```

Pasa el `project_id` y `team_id` si ya existen (los encuentras en `mcp__...__list_projects`).

## Paso 4 — Verificar

Después del deploy:
1. Llama a `mcp__...__get_deployment` con el deployment ID retornado.
2. Confirma que el estado sea `READY`.
3. Comparte la URL de producción al usuario.

## Paso 5 — Si falla

- Revisa logs con `mcp__...__get_deployment_build_logs`.
- Los errores más comunes están en `files/common-errors.md`.

---

**Output esperado:** URL de producción activa y confirmación de estado `READY`.
