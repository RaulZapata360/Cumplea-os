# Instrucciones permanentes — Sistema de Skills

## Regla: Retroalimentación al repositorio de skills

Si estás usando este repositorio como referencia desde **otro proyecto** y detectas
cualquiera de estos casos:

- Un skill existente tiene un paso incorrecto, desactualizado o mejorable
- Descubres un patrón, técnica o enfoque que haría más útil un skill actual
- El proyecto en curso genera un workflow nuevo que vale la pena convertir en skill
- Un quickstart de `projects/` no refleja la realidad de cómo se trabaja ese dominio

**Entonces:**

1. Completa primero la tarea del proyecto actual.
2. Antes de cerrar la sesión, abre (o vuelve a) este repositorio.
3. Aplica la mejora en el skill o archivo correspondiente.
4. Haz commit con mensaje claro: qué mejoró y desde qué tipo de proyecto surgió.
5. Actualiza `CHANGELOG.md` si el cambio es suficientemente relevante (PATCH o mayor).

**El objetivo:** este repositorio se vuelve más preciso con cada proyecto que lo usa,
no solo con sesiones dedicadas a mejorarlo.

---

## Contexto del repositorio

Este es el repositorio central de skills de IA de Raul Zapata.
Rama de desarrollo activa: `claude/ai-skill-review-system-Fm3HU`.

Estructura clave:
- `skills/index.yaml` — catálogo Nivel 1, siempre en contexto
- `skills/<id>/instructions.md` — workflow completo, carga bajo match
- `skills/<id>/files/` — scripts y templates, carga bajo demanda
- `projects/` — quickstarts por dominio de trabajo
- `docs/references/` — conocimiento externo que alimenta el sistema
- `CHANGELOG.md` — historial de versiones semánticas
