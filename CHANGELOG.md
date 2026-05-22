# Changelog

Todas las versiones siguen [Semantic Versioning](https://semver.org/):
- **MAJOR** — cambio de arquitectura que rompe compatibilidad
- **MINOR** — nuevas features o conocimiento que mejora el sistema
- **PATCH** — correcciones, ediciones de skills existentes, fixes de encoding

---

## [1.6.0] — 2026-05-21

### Agregado — 7 skills para SVG técnico y exportación a PDF

| Skill | Patrón | Categoría |
|-------|--------|-----------|
| `mermaid-expert` | domain-intelligence | document-creation |
| `canvas-design` | iterative-refinement | document-creation |
| `algorithmic-art` | sequential-workflow | document-creation |
| `web-artifacts-builder` | sequential-workflow | document-creation |
| `core-components` | domain-intelligence | workflow-automation |
| `svg-to-pdf` | sequential-workflow | workflow-automation |
| `ui-visual-validator` | sequential-workflow | workflow-automation |

### Cobertura nueva
- **Precisión geométrica CAD:** canvas-design (coordenadas con escala variable) + algorithmic-art (patterns y fórmulas para materiales)
- **Estructura SVG correcta:** web-artifacts-builder (defs, style, capas) + core-components (symbol/use, bloques reutilizables)
- **Pipeline de exportación:** svg-to-pdf (5 problemas frecuentes + herramientas) + ui-visual-validator (auditoría pre-export)
- **Diagramas de arquitectura:** mermaid-expert (flowchart, sequence, erDiagram, classDiagram)

### Contexto
Skills orientados al dominio de ingeniería y planos técnicos. Resuelven los tres dolores
principales con SVG en LLMs: coordenadas incorrectas, estructura semántica rota y
conversión a PDF con pérdida de información visual.

---

## [1.5.0] — 2026-05-21

### Agregado
- `docs/invasion-plan.md` — protocolo completo de 5 fases para adopción en proyectos externos:
  Reconocimiento → Diagnóstico → Recomendación → Despliegue → Retroalimentación
- `skills/project-advisor/` — skill nuevo (`context-aware-branching`) que ejecuta el diagnóstico
  y entrega un plan de skills con formato estándar: primarios, mediano plazo, futuros, repos

### Mejorado
- `skills/index.yaml` — agrega `project-advisor` (skill 21, primer `context-aware-branching`)
- `CLAUDE.md` — agrega regla de "invasión a proyectos nuevos" con referencia al protocolo

### Contexto
El repositorio ahora tiene su propio mecanismo de expansión: cuando Claude llega a un
proyecto nuevo con acceso a este repo, el protocolo de invasión se activa automáticamente.
El sistema se adopta solo, sin esperar que alguien pregunte qué skills existen.

---

## [1.4.0] — 2026-05-21

### Agregado
- `docs/references/curated-repositories.md` — 4 nuevos dominios (secciones 10-13), 22 repos:
  - Animaciones y scroll: lenis, framer/motion, locomotive-scroll, GSAP, drei
  - Dashboards y paneles: tremor, refine, react-admin, ant-design-pro, epic-stack
  - Optimización de tokens/MCP: rtk, token-optimizer, token-optimizer-mcp, ECC, LLMLingua, anthropic-cookbook
  - Flujos de IA: langflow, dify, Flowise, firecrawl, activepieces, automatisch
- 4 nuevos skills futuros: `scroll-animation-guide`, `rag-pipeline-builder`,
  `token-budget-monitor`, `admin-panel-scaffold`

### Mejorado
- `projects/web-design/quickstart.md` — reorganizado en 4 grupos con subs-tablas:
  UI/Componentes, Animaciones, 3D e imágenes, Stack y frameworks
- `projects/executive-dashboard/quickstart.md` — agrega tremor, refine, react-admin,
  ant-design-pro; reorganizado en Componentes y Finanzas/Analítica
- `projects/flow-programming/quickstart.md` — reorganizado en 4 grupos:
  DAGs, Flujos de IA, Automatización de negocios, MCP

### Contexto
Tercera ronda de repositorios curados. El total pasa a 45 repos en 13 dominios.
El repositorio cubre ahora: ingeniería, web, 3D, PDF, MCP, DAGs, finanzas,
marketing, UI/UX, animaciones, dashboards, optimización de tokens y flujos de IA.

---

## [1.3.0] — 2026-05-20

### Agregado
- `docs/references/curated-repositories.md` — 4 nuevos dominios (secciones 6-9):
  - Workflows & DAGs: apache/airflow, n8n-io/n8n, prefecthq/prefect
  - Finanzas: midday-ai/midday, ghostfolio/ghostfolio
  - Marketing y analítica: dubinc/dub, PostHog/posthog
  - UI/UX: shadcn-ui/ui, radix-ui/primitives, vercel/satori
- 4 nuevos skills futuros identificados: `dag-workflow-builder`, `financial-dashboard`,
  `campaign-analytics`, `og-image-generator`

### Mejorado
- `projects/flow-programming/quickstart.md` — repos de Airflow, n8n, Prefect
- `projects/executive-dashboard/quickstart.md` — repos de midday, ghostfolio, PostHog
  + skills relevantes completados (`metric-explainer`, `csv-to-presentations`)
- `projects/web-design/quickstart.md` — repos de shadcn, radix-ui, satori

### Contexto
Segunda ronda de repositorios curados, cerrando los dominios de automatización,
finanzas, analítica de crecimiento y UI/UX. Los 4 quickstarts ahora tienen
referencias de código para cada área de trabajo.

---

## [1.2.0] — 2026-05-20

### Agregado
- `docs/references/curated-repositories.md` — selección curada de 14 repositorios open-source
  en 5 dominios: Ingeniería/Topografía, Web/CRM, Visualización 3D, PDF, MCP
- `docs/references/README.md` actualizado con la nueva entrada en la tabla de fuentes
- Skills futuros identificados: `bim-ifc-extractor`, `point-cloud-processor`,
  `mcp-server-builder`, `react-pdf-generator`, `pdf-form-filler`

### Mejorado
- `projects/structural-calc/quickstart.md` — sección de repositorios de referencia
  (PDAL, IfcOpenShell, geopandas) + skills relevantes
- `projects/web-design/quickstart.md` — sección de repositorios de referencia
  (three.js, Next.js examples, twenty, nextcrm-app, react-pdf)
- `projects/flow-programming/quickstart.md` — sección de repositorios de referencia
  (mcp-for-beginners, modelcontextprotocol/servers)

### Contexto
Los repositorios curados conectan cada dominio de proyecto con fuentes de aprendizaje
concretas. Los quickstarts ahora tienen referencias directas a código open-source para
arquitecturas de ingeniería, web, visualización 3D, documentos y flujos MCP.

---

## [1.1.0] — 2025-05-20

### Mejorado
- `skills/HOW_TO_USE.md` enriquecido con 4 conceptos del ebook:
  - Checklist de 7 elementos obligatorios por skill
  - Fórmula de descripción (Qué + Cuándo + Triggers)
  - Protocolo T3 de testing (activación, funcional, valor)
  - Principio Goldilocks para calibrar triggers

### Agregado
- `docs/references/claude-course-ebook.md` — conocimiento extraído del ebook
  "Claude Complete Course" (Krystian Wojtarowicz & Damian Danelczyk)
- `docs/references/README.md` — guía para mantener la base de conocimiento
- `CHANGELOG.md` — este archivo, sistema de versiones desde v1.0.0

### Contexto
El ebook validó la arquitectura existente (Progressive Disclosure, 5 patrones,
3 categorías). Las mejoras de esta versión provienen de los gaps detectados al
comparar nuestras skills con el checklist oficial de 7 elementos.

---

## [1.0.0] — 2025-05-20

### Arquitectura base establecida
- Sistema de skills con Progressive Disclosure (3 niveles)
- `skills/index.yaml` como catálogo Nivel 1 (siempre en contexto)
- `skills/patterns.yaml` — 5 design patterns de comportamiento
- `skills/categories.yaml` — 3 categorías de output
- `skills/HOW_TO_USE.md` — guía de contribución
- `projects/` — 4 quickstarts: web-design, structural-calc, flow-programming, executive-dashboard

### 20 skills iniciales

| id | pattern | category |
|----|---------|----------|
| pdf-generator | sequential-workflow | document-creation |
| pdf-reader | sequential-workflow | workflow-automation |
| writing-partner | iterative-refinement | document-creation |
| meeting-notes-extractor | sequential-workflow | document-creation |
| cta-optimizer | sequential-workflow | document-creation |
| linkedin-post-generator | sequential-workflow | document-creation |
| ab-copy-variants-generator | sequential-workflow | document-creation |
| hook-engineer | sequential-workflow | document-creation |
| seo-intent-analyzer | sequential-workflow | document-creation |
| content-optimizer | sequential-workflow | document-creation |
| csv-to-presentations | sequential-workflow | document-creation |
| career-ladder-builder | sequential-workflow | document-creation |
| campaign-retrospective-builder | sequential-workflow | document-creation |
| decision-logger | sequential-workflow | document-creation |
| partnership-proposal-writer | domain-intelligence | document-creation |
| youtube-thumbnail-designer | iterative-refinement | document-creation |
| job-description-optimizer | sequential-workflow | document-creation |
| metric-explainer | sequential-workflow | document-creation |
| sop-standardizer | sequential-workflow | document-creation |
| example-deploy-vercel | sequential-workflow | workflow-automation |

### Archivado
- `_archive/birthday-site/` — proyecto original del repositorio

---

## [0.1.0] — 2025-05-20 *(pre-sistema)*

Repositorio originalmente contenía un sitio web de cumpleaños (HTML + Vercel).
Archivado en `_archive/birthday-site/` al iniciar el sistema de skills.
