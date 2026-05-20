# Skills System — Progressive Disclosure

Repositorio de skills reutilizables para proyectos de IA.

El sistema usa **Progressive Disclosure en 3 niveles** para que Claude cargue solo lo que necesita y mantenga el contexto liviano:

| Nivel | Archivo | Cuándo se carga |
|-------|---------|-----------------|
| 1 | `skills/index.yaml` | Siempre (pocos tokens) |
| 2 | `skills/<id>/instructions.md` | Al hacer match con la tarea |
| 3 | `skills/<id>/files/` | Bajo demanda |

## Estructura

```
skills/
  index.yaml                    <- Nivel 1: catálogo completo
  HOW_TO_USE.md                 <- Guía para agregar skills
  <skill-id>/
    instructions.md             <- Nivel 2: workflow completo
    files/                      <- Nivel 3: scripts, templates

_archive/
  birthday-site/                <- Proyecto anterior (inactivo)
```

## Empezar

Lee `skills/HOW_TO_USE.md` para agregar un skill nuevo.
