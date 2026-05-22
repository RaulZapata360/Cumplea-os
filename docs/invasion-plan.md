# Plan de Invasión — Acceso a Repositorios Nuevos

Cuando este repositorio llega a un proyecto externo, no espera que le pregunten.
Analiza, diagnostica y recomienda. Este documento define el protocolo.

---

## El principio

Un proyecto nuevo no sabe lo que necesita. Sabe lo que duele.
El trabajo de este repositorio es traducir ese dolor en skills concretos.

---

## Las 5 Fases de la Invasión

```
Fase 1 → RECONOCIMIENTO     ¿Qué es este proyecto?
Fase 2 → DIAGNÓSTICO        ¿Qué necesita realmente?
Fase 3 → RECOMENDACIÓN      ¿Qué skills resuelven eso?
Fase 4 → DESPLIEGUE         ¿Cómo se integran los skills?
Fase 5 → RETROALIMENTACIÓN  ¿Qué mejoró en el repositorio?
```

---

## Fase 1 — Reconocimiento

Al llegar a un proyecto nuevo, recopilar:

| Pregunta | Por qué importa |
|----------|-----------------|
| ¿Cuál es el stack tecnológico? | Determina qué skills técnicos aplican |
| ¿Cuál es el dominio? | Activa el quickstart correcto |
| ¿Qué produce el proyecto? | Define la categoría de skills (document-creation / workflow-automation / mcp-enhancement) |
| ¿Cuál es el mayor cuello de botella hoy? | Identifica el skill de mayor impacto inmediato |
| ¿Hay flujos repetitivos sin documentar? | Señala candidatos a nuevos skills |

**Dominios reconocibles:**

| Señal en el proyecto | Dominio |
|----------------------|---------|
| HTML, CSS, React, Next.js, Tailwind | web-design |
| Python, cálculo, topografía, normativas | structural-calc |
| n8n, Airflow, APIs, webhooks, scripts de automatización | flow-programming |
| KPIs, dashboards, reportes ejecutivos, finanzas | executive-dashboard |
| Copywriting, LinkedIn, emails, SEO, ads | marketing-content |

---

## Fase 2 — Diagnóstico

Mapear lo encontrado contra las 3 categorías del sistema:

```
¿El proyecto produce documentos?
  → Activar skills de document-creation

¿El proyecto tiene pasos repetibles que hoy se hacen a mano?
  → Activar skills de workflow-automation

¿El proyecto usa MCPs o herramientas de IA conectadas?
  → Activar skills de mcp-enhancement
```

**Señales de urgencia** — priorizar si aparecen:

- "Siempre pierdo tiempo en X" → skill de workflow-automation
- "El cliente necesita el reporte el viernes" → skill de document-creation
- "Hay que conectar esto con aquello" → skill de multi-mcp-coordination
- "Nunca documentamos por qué tomamos esa decisión" → `decision-logger`
- "El equipo no tiene claro el proceso" → `sop-standardizer`

---

## Fase 3 — Recomendación

### Mapa de recomendación por dominio

**Web / Frontend**
- Skills primarios: `example-deploy-vercel`, `youtube-thumbnail-designer`
- Skills secundarios: `seo-intent-analyzer`, `content-optimizer`
- Quickstart: `projects/web-design/`
- Repos de referencia: shadcn, lenis, framer/motion, GSAP

**Ingeniería / Cálculo**
- Skills primarios: `pdf-generator`, `pdf-reader`
- Skills secundarios: `sop-standardizer`, `decision-logger`
- Quickstart: `projects/structural-calc/`
- Repos de referencia: PDAL, IfcOpenShell, geopandas

**Marketing / Contenido**
- Skills primarios: `hook-engineer`, `linkedin-post-generator`, `cta-optimizer`
- Skills secundarios: `seo-intent-analyzer`, `ab-copy-variants-generator`, `writing-partner`
- Skills de análisis: `campaign-retrospective-builder`, `metric-explainer`
- Repos de referencia: dub, PostHog

**Automatización / Flujos**
- Skills primarios: `sop-standardizer`, `decision-logger`
- Skills secundarios: `meeting-notes-extractor`, `csv-to-presentations`
- Quickstart: `projects/flow-programming/`
- Repos de referencia: Airflow, Prefect, n8n, langflow, dify

**Dashboards / Finanzas**
- Skills primarios: `metric-explainer`, `csv-to-presentations`, `pdf-generator`
- Skills secundarios: `career-ladder-builder`, `campaign-retrospective-builder`
- Quickstart: `projects/executive-dashboard/`
- Repos de referencia: tremor, refine, midday, ghostfolio

### Formato de recomendación

Cuando se entrega la recomendación al proyecto, seguir este formato:

```
## Skills recomendados para [nombre del proyecto]

### Impacto inmediato (implementar esta semana)
- `skill-id` — por qué resuelve el problema X

### Impacto a mediano plazo (próximo mes)
- `skill-id` — por qué mejora el flujo Y

### Skills futuros a vigilar
- `skill-id-futuro` — aún no existe, pero este proyecto lo necesitará

### Repositorios de referencia relevantes
- [repo] — para aprender Z
```

---

## Fase 4 — Despliegue

### Cómo integrar el repositorio de skills en un proyecto externo

**Opción A — CLAUDE.md en el proyecto externo**
```markdown
# Contexto de skills

Este proyecto usa el repositorio de skills de Raul Zapata como referencia.
Ruta local: [ruta al repo clonado]
Índice: skills/index.yaml
Guía de uso: skills/HOW_TO_USE.md
```

**Opción B — Git submodule**
```bash
git submodule add https://github.com/RaulZapata360/Cumplea-os.git skills-repo
```

**Opción C — Claude Project (contexto compartido)**
Subir `skills/index.yaml` + `skills/HOW_TO_USE.md` como archivos de contexto
en el Claude Project del proyecto externo.

### Prioridad de carga

```
Nivel 1: skills/index.yaml         ← siempre en contexto (pocos tokens)
Nivel 2: skills/<id>/instructions.md  ← solo cuando hay match
Nivel 3: skills/<id>/files/        ← solo bajo demanda
```

---

## Fase 5 — Retroalimentación

Al terminar un ciclo de trabajo en el proyecto externo, antes de cerrar la sesión:

1. **¿Se usó algún skill?** → ¿Funcionó como se esperaba?
2. **¿Faltó un paso en las instrucciones?** → Editar `instructions.md`
3. **¿Surgió un flujo nuevo reutilizable?** → Crear skill nuevo
4. **¿El quickstart del dominio era preciso?** → Actualizar `projects/`
5. **Commit + push** al repositorio de skills con mensaje claro de origen

**Regla:** el repositorio debe quedar más preciso después de cada proyecto que lo usa.

---

## Checklist de invasión completa

```
[ ] Reconocimiento: dominio, stack y dolor identificados
[ ] Diagnóstico: categorías de skills mapeadas
[ ] Recomendación: entregada en formato estándar con primarios/secundarios
[ ] Despliegue: repositorio integrado al proyecto (método elegido)
[ ] Retroalimentación: al menos un mejora subida antes de cerrar sesión
```

---

*Este plan se activa automáticamente cuando Claude llega a un nuevo proyecto
y detecta que tiene acceso al repositorio de skills.*
