# Skills & Projects — Base de conocimiento operacional

Repositorio central de skills, patrones y quick starts para proyectos.
Al iniciar cualquier trabajo nuevo, este repositorio da el punto de partida.

---

## Cómo funciona

### Skills — Progressive Disclosure (3 niveles)

Claude carga solo lo que necesita:

| Nivel | Archivo | Cuándo se carga |
|-------|---------|-----------------|
| 1 | `skills/index.yaml` | Siempre (pocos tokens) |
| 2 | `skills/<id>/instructions.md` | Al hacer match con la tarea |
| 3 | `skills/<id>/files/` | Bajo demanda |

Cada skill tiene dos ejes de clasificación:
- **`pattern`** — cómo se comporta (5 patrones, ver `skills/patterns.yaml`)
- **`category`** — qué produce (3 categorías, ver `skills/categories.yaml`)

### Projects — Quick starts por tipo de proyecto

Al iniciar un proyecto, cargar el quickstart correspondiente:

| Tipo | Quickstart |
|------|------------|
| Diseño Web | `projects/web-design/quickstart.md` |
| Cálculo Estructural | `projects/structural-calc/quickstart.md` |
| Programación de Flujos | `projects/flow-programming/quickstart.md` |
| Dashboard Ejecutivo | `projects/executive-dashboard/quickstart.md` |

---

## Estructura completa

```
skills/
  index.yaml              <- Catálogo de skills (Nivel 1, siempre en contexto)
  patterns.yaml           <- 5 design patterns de comportamiento
  categories.yaml         <- 3 categorías de output
  HOW_TO_USE.md           <- Guía para agregar skills nuevos
  <skill-id>/
    instructions.md       <- Workflow completo (Nivel 2)
    files/                <- Scripts, templates, refs (Nivel 3)

projects/
  index.yaml              <- Catálogo de tipos de proyecto
  web-design/
    quickstart.md
  structural-calc/
    quickstart.md
  flow-programming/
    quickstart.md
  executive-dashboard/
    quickstart.md

_archive/
  birthday-site/          <- Proyecto anterior (inactivo)
```

---

## Para agregar contenido nuevo

- **Skill nuevo** → ver `skills/HOW_TO_USE.md`
- **Tipo de proyecto nuevo** → agregar entrada en `projects/index.yaml` + crear carpeta con `quickstart.md`
- **Patrón o categoría** → editar `skills/patterns.yaml` o `skills/categories.yaml`
