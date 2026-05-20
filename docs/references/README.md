# Base de Conocimiento — Referencias

Esta carpeta almacena el conocimiento externo que alimenta y mejora el sistema de skills.

## Cómo funciona

Cada archivo aquí es una fuente de retroalimentación. Cuando se aprende algo nuevo
sobre diseño de skills, patrones de IA o mejores prácticas, se extrae el conocimiento
relevante y se guarda aquí en formato `.md` estructurado.

El conocimiento de esta carpeta se usa para:
- Auditar skills existentes y detectar gaps
- Mejorar `skills/HOW_TO_USE.md` con nuevas prácticas
- Justificar cambios de versión en `CHANGELOG.md`

## Archivos actuales

| Archivo | Fuente | Versión que lo incorporó |
|---------|--------|--------------------------|
| `claude-course-ebook.md` | Ebook "Claude Complete Course" — Wojtarowicz & Danelczyk | v1.1.0 |

## Cómo agregar conocimiento nuevo

1. Identifica la fuente (ebook, artículo, paper, experiencia propia)
2. Extrae solo lo accionable — no copiar/pegar, sino sintetizar
3. Crea `docs/references/<fuente>.md` con el conocimiento estructurado
4. Actualiza esta tabla
5. Aplica las mejoras al sistema y registra en `CHANGELOG.md` con la versión correspondiente
