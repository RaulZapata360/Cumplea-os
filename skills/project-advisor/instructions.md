# Project Advisor

Analiza cualquier proyecto nuevo y entrega un plan de skills concreto.
No esperes que te pidan skills específicos — diagnostica tú mismo y recomienda.

## Cuándo activarse

- Al inicio de una sesión en un proyecto que no has visto antes
- Cuando alguien dice "quiero integrar el repositorio de skills a este proyecto"
- Cuando detectas dolor repetitivo sin solución sistemática ("siempre tarda X", "nunca documentamos Y")
- Cuando te comparten un repo nuevo y preguntan qué pueden mejorar con IA

---

## Proceso

### Paso 1 — Reconocimiento (preguntas clave)

Si no tienes contexto suficiente, hace estas preguntas antes de cualquier recomendación:

```
1. ¿Cuál es el dominio principal del proyecto?
   (web, ingeniería/cálculo, marketing/contenido, automatización, finanzas/dashboards)

2. ¿Qué produce el proyecto?
   (documentos, apps, reportes, datos procesados, contenido publicable)

3. ¿Cuál es el cuello de botella más doloroso hoy?
   (lo que más tiempo quita o más errores produce)

4. ¿Hay flujos que se repiten sin estar documentados?
   (reuniones de kickoff, reportes semanales, entregas al cliente, revisiones)
```

Si ya tienes contexto del proyecto (leíste archivos, CLAUDE.md, README), salta directo al Paso 2.

---

### Paso 2 — Diagnóstico

Clasifica el proyecto en uno o más de estos perfiles:

| Perfil | Señales | Categoría dominante |
|--------|---------|---------------------|
| **Web / Frontend** | HTML, CSS, React, Next.js, Vercel, Tailwind | document-creation + workflow-automation |
| **Ingeniería / Cálculo** | Python, normativas, topografía, memorias, planos | document-creation + workflow-automation |
| **Marketing / Contenido** | copywriting, LinkedIn, email, SEO, ads, campañas | document-creation |
| **Automatización** | n8n, Airflow, APIs, webhooks, scripts | workflow-automation + mcp-enhancement |
| **Finanzas / Dashboards** | KPIs, reportes ejecutivos, tablas, métricas | document-creation + workflow-automation |

Un proyecto puede tener 2 perfiles activos al mismo tiempo.

---

### Paso 3 — Recomendación

Entrega la recomendación en este formato exacto. Sin intro larga — directo al plan:

```markdown
## Plan de Skills para [Nombre del Proyecto]

### Impacto inmediato — implementar esta semana
| Skill | Por qué |
|-------|---------|
| `skill-id` | [problema concreto que resuelve en este proyecto] |

### Impacto a mediano plazo — próximo mes
| Skill | Por qué |
|-------|---------|
| `skill-id` | [flujo que optimiza cuando esté implementado] |

### Skills futuros a vigilar
- `skill-futuro` — aún no existe en el repo, pero este proyecto lo necesitará porque [razón]

### Repositorios de referencia relevantes
| Repo | Aplicación específica en este proyecto |
|------|---------------------------------------|
| [repo] | [para qué exactamente aquí] |

### Primer paso concreto
[Una sola acción que pueden hacer hoy para empezar — específica, no genérica]
```

---

### Paso 4 — Integración (si la piden)

Según el contexto del proyecto, recomienda el método de integración:

**Si el proyecto ya tiene CLAUDE.md:**
Agregar al CLAUDE.md existente una sección "Skills disponibles" apuntando al índice.

**Si el proyecto no tiene CLAUDE.md:**
Crear uno con referencia al repositorio de skills como contexto permanente.

**Si el proyecto usa Claude Projects:**
Los archivos mínimos a subir como contexto son:
- `skills/index.yaml`
- `skills/HOW_TO_USE.md`
- El `quickstart.md` del dominio relevante

**Si el proyecto es un repositorio Git:**
```bash
git submodule add https://github.com/RaulZapata360/Cumplea-os.git .skills
```

---

### Paso 5 — Cerrar el ciclo

Antes de terminar la sesión en el proyecto externo, preguntar:

> "¿Algo de lo que hicimos hoy debería convertirse en un skill nuevo
> o mejorar uno existente en el repositorio?"

Si la respuesta es sí → abrir el repositorio y aplicar la mejora.

---

## Reglas

- Nunca recomendar más de 3 skills de "impacto inmediato" — el exceso paraliza
- Siempre incluir UNA acción concreta de primer paso, no una lista vaga
- Si el proyecto no encaja en ningún dominio conocido, decirlo explícitamente y preguntar antes de forzar una categoría
- Si un skill recomendado no existe aún, marcarlo como "futuro" y registrarlo en `docs/references/curated-repositories.md`
- No recomendar skills que el proyecto claramente ya tiene cubiertos de otra forma

## Variaciones

**Invasión rápida (5 min):** Solo Paso 1 y 3 — diagnóstico exprés para proyectos simples o urgentes.

**Invasión profunda:** Los 5 pasos completos — para proyectos nuevos o complejos donde la adopción debe ser sistemática.

**Revisión periódica:** Ejecutar Paso 2 y 3 cada mes en el mismo proyecto para detectar si aparecieron nuevas necesidades.
