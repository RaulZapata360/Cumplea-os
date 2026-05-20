# Claude Complete Course — Conocimiento de referencia

**Fuente:** Ebook "Claude Complete Course" — Krystian Wojtarowicz & Damian Danelczyk
**Relevancia:** Valida y completa la arquitectura de este repositorio.
**Última revisión:** 2025-05-20

---

## 1. Progressive Disclosure — 3 Niveles *(confirma nuestra arquitectura)*

Claude solo carga lo que necesita:

| Nivel | Qué es | Cuándo se carga |
|-------|--------|-----------------|
| 1 | Nombre + Descripción (YAML frontmatter) | Siempre — pocos tokens |
| 2 | Instrucciones completas (instructions.md) | Al hacer match con la tarea |
| 3 | Archivos vinculados (files/) | Bajo demanda |

**Principio clave:** Solo cargar lo necesario mantiene la ventana de contexto ligera y rápida.

---

## 2. Fórmula de descripción *(aplicar a todo skill nuevo)*

```
Qué hace + Cuándo usarla + Frases clave de trigger = Descripción perfecta
```

- **Qué hace:** función central del skill
- **Cuándo usarla:** contexto + tipos de archivo + intención del usuario
- **Triggers:** palabras exactas que el usuario escribiría

**Límite:** bajo 1.000 caracteres. Los triggers pueden ser de texto o basados en eventos.

### Ejemplos malos vs buenos

| ❌ Malo | ✅ Bueno |
|---------|---------|
| "ayuda con proyectos" | "Analiza archivos de diseño de Figma y genera documentos de entrega para desarrolladores. Úselo cuando el usuario sube archivos .fig o solicite especificaciones de diseño." |
| "Crea sistemas de documentación sofisticados" | "Gestiona flujos de trabajo de proyectos lineales, incluida la planificación de sprints, la creación de tareas y el seguimiento del estado. Úsalo cuando el usuario mencione sprint, tareas lineales o creación de tickets." |
| "Implementa el modelo de entidad con relaciones jerárquicas" | "Incorporación de cliente de extremo a extremo para PayFlow. Úsalo cuando el usuario pida configurar un nuevo cliente, configurar la facturación o crear planes de suscripción." |

**Regla:** escribe para humanos — usa las palabras que tus usuarios realmente escribirían.

---

## 3. Checklist de 7 elementos por skill *(auditar antes de publicar)*

Todo skill bien construido debe tener:

- [ ] **Descripción** con palabras clave de activación
- [ ] **Instrucciones estructuradas** paso a paso (no párrafos vagos)
- [ ] **Preguntas aclaratorias** para información faltante (no adivinar)
- [ ] **Especificación del formato de salida** (qué produce exactamente)
- [ ] **Sección de reglas** — qué nunca debe ocurrir
- [ ] **Archivos de referencia** para ejemplos y contexto (si aplica)
- [ ] **Variaciones múltiples** — deja que el usuario elija entre opciones

### Instrucciones malas vs buenas

| ❌ Malas | ✅ Buenas |
|---------|---------|
| "Ayude al usuario con sus datos. Valídelos y asegúrese de que todo se vea bien." | Paso 1: Verificar filas, columnas, tipos, valores faltantes / Paso 2: Marco de decisión para cada tipo de problema / Paso 3: Aplicar correcciones registrando cada cambio / Paso 4: Exportar con nombre descriptivo + informe |

**Regla:** pasos > párrafos. Estructura → resultados consistentes.

---

## 4. Protocolo T3 de testing *(antes de promover un skill a global)*

| Test | Pregunta | Cómo |
|------|----------|------|
| **T1 — Activación** | ¿El skill se activa cuando debe? | Usar sesión nueva, probar prompts que sí/no deberían activar |
| **T2 — Funcional** | ¿El output es correcto y consistente? | Ejecutar 4-5 veces con inputs diferentes |
| **T3 — Valor** | ¿Vale la pena este skill? | Evaluar complejidad vs beneficio real |

### Prompts de prueba (para cualquier skill)

- **Debe activarse:** prompt directamente relacionado con el skill
- **NO debe activarse:** prompt fuera del scope
- **Área gris:** prompt ambiguo — mide la calibración del trigger

**Si el output es inconsistente** → ajusta instrucciones
**Si no vale la pena** → descarta o simplifica

---

## 5. Principio Goldilocks *(calibrar triggers)*

```
Subactivación          Punto óptimo          Sobreactivación
(skill ignorado)    (se activa cuando        (se activa para todo)
                     es relevante)

→ Agregar más         El objetivo           Hacer la descripción
  palabras de                               más específica ←
  activación
```

**Prueba:** usa prompts que SÍ deben activar, prompts que NO deben activar, y prompts de área gris. Calibra hasta el punto medio.

---

## 6. Estructura de carpetas *(confirma nuestra arquitectura)*

```
skill-id/                    ← nombre en kebab-case
  instructions.md            ← Nivel 2: siempre cargado primero
  files/                     ← Nivel 3: cargado bajo demanda
    referencia.md            ← un tema por archivo
    script.py                ← nombres descriptivos con guiones
```

### 3 reglas de estructura
1. **Nombres descriptivos en minúsculas con guiones** (`clean-csv-data.py`, no `script1.py`)
2. **No anidar más de un nivel** — si necesitas subcarpetas, divide en dos skills
3. **Un tema por archivo de referencia** — Claude solo toma lo que necesita

---

## 7. Skills vs Plugins *(distinción importante para el futuro)*

| Skills | Plugins |
|--------|---------|
| Archivo `instructions.md` en lenguaje llano | Paquete instalable con Skills + MCPs + Comandos |
| Proporciona inteligencia / instrucciones | Proporciona capacidad + inteligencia + conexiones |
| Activado por trigger de lenguaje natural | Instalado en un clic desde un marketplace |
| Autónomo — sin conexiones externas | Conecta con servicios externos (Notion, Slack, GitHub) |
| Cualquiera puede crearlo sin código | Versionado y desplegable para equipos |

**Analogía:** el Plugin es la app que instalas. El Skill es la función integrada dentro de ella.

**Implicación para este repo:** actualmente manejamos Skills. Los Plugins son el siguiente nivel — agrupan varios skills + MCPs en un paquete instalable.

---

## 8. Modelos Claude *(referencia rápida)*

| Modelo | Mejor para | Velocidad | Costo |
|--------|-----------|-----------|-------|
| Haiku | Respuestas rápidas, tareas simples, alto volumen | ★★★ | $ |
| Sonnet | Redacción, análisis, código, trabajo diario — 90% de tareas | ★★ | $$ |
| Opus | Razonamiento complejo, estrategia, análisis profundo | ★ | $$$ |

**Regla:** empieza con Sonnet, cambia solo cuando tengas razón específica.

---

## 9. Prompting — Fórmula ROL + TAREA + CONTEXTO + FORMATO

```
ROL      + TAREA      + CONTEXTO    + FORMATO    = Gran resultado
"Eres un..." "Haz esto..." "Dado que..." "Entrega como..."
```

**3 patrones:**
1. **Rol + Tarea + Formato** — punto de partida para cualquier tarea nueva
2. **Chain of Thought** — pedir razonar paso a paso antes de la respuesta final
3. **Prompts iterativos** — borrador → "hazlo más corto" → "más directo" → "agrega CTA"

---

## 10. Subagentes *(relevante para skills multi-MCP)*

El agente principal coordina. Los subagentes ejecutan tareas específicas con su propia ventana de contexto — ninguno llena la conversación principal.

```
Agente Principal (coordina, recopila resúmenes)
├── Agente Explorador (busca en base de código/docs)
├── Agente Programador (escribe/edita código)
└── Agente Revisor (revisa calidad y errores)
```

**Beneficio clave:** la conversación principal se mantiene en ~15% de contexto — la calidad no decae en proyectos largos.

---

*Fuente: Claude Complete Course Ebook — Krystian Wojtarowicz & Damian Danelczyk*
*Próxima revisión: cuando se publique material nuevo del curso o se detecten nuevos patrones en uso.*
