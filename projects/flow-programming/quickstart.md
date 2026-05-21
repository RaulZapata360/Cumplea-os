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

## Repositorios de referencia

### Orquestación y DAGs
| Repositorio | Para qué |
|-------------|----------|
| [apache/airflow](https://github.com/apache/airflow) | DAGs, dependencias entre tareas, reintentos automáticos, ejecuciones programadas |
| [n8n-io/n8n](https://github.com/n8n-io/n8n) | Automatización visual por nodos, iterar sobre arrays, conectar APIs y scripts |
| [prefecthq/prefect](https://github.com/prefecthq/prefect) | Convertir funciones Python en pipelines resilientes y observables |

### Flujos de IA y agentes
| Repositorio | Para qué |
|-------------|----------|
| [langflow-ai/langflow](https://github.com/langflow-ai/langflow) | GUI drag & drop para LangChain: prototipar agentes y sistemas RAG visualmente |
| [langgenius/dify](https://github.com/langgenius/dify) | Plataforma completa LLM: flujos, agentes, vectorstores, gestión de prompts |
| [FlowiseAI/Flowise](https://github.com/FlowiseAI/Flowise) | Chatbots conectados a repos o PDFs; rápido para RAG de documentos |
| [mendableai/firecrawl](https://github.com/mendableai/firecrawl) | Convierte sitios web en Markdown limpio para inyección eficiente de contexto |

### Automatización de negocios
| Repositorio | Para qué |
|-------------|----------|
| [activepieces/activepieces](https://github.com/activepieces/activepieces) | Alternativa open-source a Zapier: correos, tickets, CRMs sin licencias costosas |
| [automatisch/automatisch](https://github.com/automatisch/automatisch) | Automatización auto-alojada con foco en privacidad: sin enviar datos a terceros |

### MCP
| Repositorio | Para qué |
|-------------|----------|
| [microsoft/mcp-for-beginners](https://github.com/microsoft/mcp-for-beginners) | Fundamentos MCP: arquitectura cliente-servidor, herramientas, recursos |
| [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) | Implementaciones de referencia: Google Drive, PostgreSQL, GitHub, filesystem |

## Skills relevantes

*(Agregar skills de automatización cuando se creen)*
