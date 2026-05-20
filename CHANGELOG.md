# Changelog

Todas las versiones siguen [Semantic Versioning](https://semver.org/):
- **MAJOR** — cambio de arquitectura que rompe compatibilidad
- **MINOR** — nuevas features o conocimiento que mejora el sistema
- **PATCH** — correcciones, ediciones de skills existentes, fixes de encoding

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
