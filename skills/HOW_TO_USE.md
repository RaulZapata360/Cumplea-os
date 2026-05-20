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

---

## Para agregar un skill

1. Abre `skills/index.yaml` y agrega la entrada con `id`, `name`, `description`, `pattern`, `category`, `tags`.
2. Elige el patrón que mejor describe el comportamiento del skill (ver `skills/patterns.yaml`).
3. Elige la categoría de output (ver `skills/categories.yaml`).
4. Crea la carpeta `skills/<id>/`.
5. Escribe `skills/<id>/instructions.md` con el workflow completo.
6. (Opcional) Agrega archivos de apoyo en `skills/<id>/files/`.
7. Pasa el **Checklist de 7 elementos** antes de hacer commit.

---

## Fórmula de descripción

Toda descripción en `index.yaml` debe responder estas 3 preguntas:

```
Qué hace + Cuándo usarlo + Frases de trigger = Descripción perfecta
```

- **Qué hace:** función central del skill (1 oración)
- **Cuándo usarlo:** contexto, tipo de input, intención del usuario
- **Triggers:** palabras exactas que el usuario escribiría para activarlo

**Límite:** bajo 1.000 caracteres. Escribe para humanos — usa las palabras que tus usuarios realmente escribirían.

---

## Checklist de 7 elementos *(pasar antes de hacer commit)*

- [ ] **Descripción** con palabras clave de activación claras
- [ ] **Instrucciones estructuradas** paso a paso (no párrafos vagos)
- [ ] **Preguntas aclaratorias** definidas (qué preguntar si falta información)
- [ ] **Formato de output** especificado (qué produce exactamente el skill)
- [ ] **Sección de reglas** — qué nunca debe ocurrir
- [ ] **Archivos de referencia** en `files/` si el contenido no cabe en instrucciones
- [ ] **Variaciones** — al menos 2 opciones o templates donde aplique

---

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

---

## Las 3 Categorías

El campo `category` clasifica el tipo de output que produce el skill:

| Category | Produce | Enfoque |
|----------|---------|---------|
| `document-creation` | PDFs, reportes, posts, docs | Output |
| `workflow-automation` | Procesos repetibles, pipelines | Proceso |
| `mcp-enhancement` | Guías de uso de un MCP específico | Inteligencia |

Ver detalles en `skills/categories.yaml`.

---

## Protocolo T3 de testing *(antes de promover a global)*

| Test | Pregunta | Cómo ejecutar |
|------|----------|---------------|
| **T1 — Activación** | ¿Se activa cuando debe? | Sesión nueva + prompts que sí/no deben activar |
| **T2 — Funcional** | ¿El output es consistente? | Ejecutar 4-5 veces con inputs diferentes |
| **T3 — Valor** | ¿Vale la pena? | Evaluar complejidad vs beneficio real |

Flujo: **Nivel de Proyecto → Prueba de Batalla (semanas) → Global**

Si el output es inconsistente → ajusta instrucciones.
Si no vale la pena → descarta o simplifica.

---

## Principio Goldilocks *(calibrar triggers)*

```
Subactivación      →    Punto óptimo    ←    Sobreactivación
skill ignorado         activa cuando         activa para todo
                        es relevante

Fix: más triggers       El objetivo          Fix: descripción
                                             más específica
```

Prueba con 3 tipos de prompts:
- **Verde:** debe activarse
- **Rojo:** no debe activarse
- **Gris:** ambiguo — mide la calibración

---

## Criterios de calidad

- **Nombre**: acción clara en 3-5 palabras en kebab-case
- **Instrucciones**: pasos > párrafos. Estructura → resultados consistentes
- **Files**: un tema por archivo, nombres descriptivos con guiones
- **No anidar**: máximo un nivel de subcarpetas en `files/`

---

## Conocimiento de referencia

Ver `docs/references/` para material que alimenta este sistema:
- `docs/references/claude-course-ebook.md` — conceptos del ebook de Krystian & Damian
