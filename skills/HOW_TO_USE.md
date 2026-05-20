# Sistema de Skills — Progressive Disclosure

Claude solo carga lo que necesita. El flujo tiene 3 niveles:

```
Nivel 1 → skills/index.yaml
           Nombre + descripción de cada skill.
           Pocos tokens. Siempre en contexto.
                │
                ▼ ¿El skill parece relevante?
Nivel 2 → skills/<id>/instructions.md
           Workflow paso a paso, reglas, decisiones.
           Se carga solo al hacer match.
                │
                ▼ ¿Necesita más detalle?
Nivel 3 → skills/<id>/files/
           Scripts Python, templates, referencias.
           Se carga solo bajo demanda.
```

## Para agregar un skill

1. Abre `skills/index.yaml` y agrega la entrada con `id`, `name`, `description`, `pattern`, `tags`.
2. Elige el patrón que mejor describe el comportamiento del skill (ver `skills/patterns.yaml`).
3. Crea la carpeta `skills/<id>/`.
4. Escribe `skills/<id>/instructions.md` con el workflow completo.
5. (Opcional) Agrega archivos de apoyo en `skills/<id>/files/`.

## Los 5 Design Patterns

El campo `pattern` en `index.yaml` le dice a Claude cómo está estructurado el skill antes de leer las instrucciones. Elige uno:

| Pattern | Cuándo usarlo |
|---------|---------------|
| `sequential-workflow` | Pasos en orden fijo, sin bifurcaciones |
| `multi-mcp-coordination` | Orquesta 2+ herramientas o servicios |
| `iterative-refinement` | Ciclos Generar → Revisar → Mejorar |
| `context-aware-branching` | Distintos caminos según el tipo de input |
| `domain-intelligence` | Encapsula reglas de negocio o SOPs internos |

Ver descripción completa y señales de cada patrón en `skills/patterns.yaml`.

## Criterios de un buen skill

- **Nombre**: acción clara en 3-5 palabras.
- **Descripción**: qué hace, cuándo usarlo, qué produce. Máx 2 líneas.
- **Pattern**: el que mejor describe la estructura de comportamiento.
- **Tags**: 2-5 palabras clave para búsqueda rápida.
- **Instructions**: paso a paso, sin ambigüedad. El lector no debe adivinar nada.
- **Files**: solo lo que no cabe en el texto (scripts largos, plantillas, datos).
