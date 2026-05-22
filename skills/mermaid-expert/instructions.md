# Mermaid Expert

Genera diagramas técnicos precisos usando sintaxis Mermaid. Antes de escribir código
SVG crudo, evalúa si Mermaid resuelve el problema — ahorra tokens, es reproducible
y se renderiza limpiamente en Markdown, Notion, GitHub y herramientas de documentación.

## Cuándo usar Mermaid vs SVG crudo

| Situación | Usar |
|-----------|------|
| Flujos de proceso, decisiones, pipelines | Mermaid flowchart |
| Secuencias de comunicación entre sistemas | Mermaid sequenceDiagram |
| Relaciones entre entidades (bases de datos) | Mermaid erDiagram |
| Arquitecturas de clases o módulos | Mermaid classDiagram |
| Perfiles topográficos, planos, cotas | SVG crudo (ir a `canvas-design`) |
| Patrones de refuerzo, texturas de materiales | SVG crudo (ir a `algorithmic-art`) |

## Tipos de diagrama y su sintaxis base

### flowchart — Procesos y decisiones
```
flowchart TD
    A[Inicio] --> B{¿Condición?}
    B -- Sí --> C[Acción A]
    B -- No --> D[Acción B]
    C --> E[Fin]
    D --> E
```
Orientaciones: TD (top-down), LR (left-right), BT, RL.

### sequenceDiagram — Comunicación entre actores
```
sequenceDiagram
    actor Usuario
    participant API
    participant DB
    Usuario->>API: POST /datos
    API->>DB: INSERT
    DB-->>API: OK
    API-->>Usuario: 201 Created
```

### erDiagram — Modelo de datos
```
erDiagram
    PROYECTO ||--o{ ELEMENTO : contiene
    ELEMENTO {
        string id
        float area
        string norma
    }
```

### classDiagram — Módulos y herencia
```
classDiagram
    class Viga {
        +float longitud
        +float seccion
        +calcularMomento()
    }
    Viga <|-- VigaSimple
    Viga <|-- VigaContinua
```

## Proceso

```
1. CLASIFICAR   → ¿qué tipo de diagrama representa mejor la información?
2. PLANEAR      → listar nodos/actores/entidades antes de escribir código
3. JERARQUÍA    → definir relaciones: quién conecta con quién y en qué dirección
4. ESCRIBIR     → código Mermaid limpio, un bloque por diagrama
5. VALIDAR      → verificar que la sintaxis no use features beta o no soportados
```

## Reglas

- Nunca mezclar tipos de diagrama en un solo bloque
- Los IDs de nodos no deben tener espacios — usar camelCase o guiones: `procesoA`
- Las etiquetas en corchetes pueden tener texto libre: `A[Texto con espacios]`
- No usar subgraph si el renderer destino no lo soporta (preguntar antes)
- Si el diagrama tiene más de 20 nodos, dividirlo en 2 diagramas con contexto compartido
- Para topografía, perfiles o planos: derivar al skill `canvas-design`

## Variaciones

**Diagrama de arquitectura técnica:** flowchart LR con subgraphs por capa (frontend, backend, DB, infra).

**Diagrama de flujo de cálculo estructural:** flowchart TD con nodos de decisión por normativa (NSR-10, ACI 318) y bifurcaciones según tipo de elemento.

**Mapa de integración de sistemas:** sequenceDiagram con todas las APIs involucradas, mostrando orden de llamadas y manejo de errores.
