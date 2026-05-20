# Quick Start — Programación de Flujos

## Stack base recomendado

| Necesidad | Herramienta |
|-----------|-------------|
| Automatización no-code | n8n (self-hosted o cloud) |
| Integración SaaS | Make (ex-Integromat) |
| Scripting avanzado | Python + requests / httpx |
| Webhooks y triggers | n8n / Cloudflare Workers |
| Almacenamiento temporal | Airtable / Google Sheets |

## Primer paso

1. Mapear el flujo actual a mano: ¿qué entra, qué pasa, qué sale?
2. Identificar las herramientas involucradas (¿tiene MCPs disponibles?).
3. Elegir el patrón del skill que aplica:
   - Flujo lineal → `sequential-workflow`
   - Múltiples servicios → `multi-mcp-coordination`
   - Ciclos de revisión → `iterative-refinement`
4. Documentar el flujo en un `instructions.md` dentro de `skills/`.

## Checklist antes de entregar

- [ ] El flujo tiene manejo de errores (¿qué pasa si falla un paso?)
- [ ] Credenciales en variables de entorno, no hardcodeadas
- [ ] Existe un trigger de prueba documentado
- [ ] El flujo fue ejecutado al menos 3 veces en test sin errores
- [ ] Existe un skill en el índice si el flujo es reutilizable

## Skills relevantes

*(Agregar skills de automatización cuando se creen)*
