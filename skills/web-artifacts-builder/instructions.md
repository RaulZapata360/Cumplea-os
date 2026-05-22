# Web Artifacts Builder

Genera SVG y componentes HTML/CSS semánticamente correctos que no se rompen al
moverlos entre contextos (web, PDF, email, Notion). La causa número uno de SVG
roto es la estructura semántica incorrecta, no las coordenadas.

## Estructura canónica de un SVG técnico

```svg
<svg xmlns="http://www.w3.org/2000/svg"
     xmlns:xlink="http://www.w3.org/1999/xlink"
     viewBox="0 0 800 600"
     width="800" height="600"
     role="img"
     aria-label="Descripción del diagrama">

  <!-- 1. Metadatos -->
  <title>Nombre del plano o diagrama</title>
  <desc>Descripción breve del contenido</desc>

  <!-- 2. Definiciones reutilizables -->
  <defs>
    <!-- Patterns, símbolos, gradientes, filtros, marcadores -->
    <marker id="flecha" viewBox="0 0 10 10" refX="9" refY="5"
            markerWidth="6" markerHeight="6" orient="auto">
      <path d="M 0 0 L 10 5 L 0 10 z" fill="#333"/>
    </marker>
  </defs>

  <!-- 3. Fondo -->
  <rect width="800" height="600" fill="white"/>

  <!-- 4. Grupos de contenido, cada uno con id descriptivo -->
  <g id="capa-estructura">
    <!-- elementos estructurales principales -->
  </g>

  <g id="capa-anotaciones">
    <!-- cotas, etiquetas, notas -->
  </g>

  <g id="capa-titulo">
    <!-- bloque de título y leyenda -->
  </g>

</svg>
```

## Los 6 tags de SVG que más se usan mal

### `<defs>` — Solo definiciones, nunca elementos visibles directos
```svg
<defs>
  <symbol id="icono-cimentacion" viewBox="0 0 20 20">
    <!-- El símbolo no se renderiza hasta que se llame con <use> -->
    <rect x="0" y="10" width="20" height="10" fill="#999"/>
    <line x1="10" y1="0" x2="10" y2="10" stroke="#333" stroke-width="1.5"/>
  </symbol>
</defs>
```

### `<g>` — Agrupación lógica con transform
```svg
<!-- Agrupar elementos relacionados con un id descriptivo -->
<g id="seccion-viga" transform="translate(100, 50)">
  <!-- todos los elementos de la sección trabajan con coordenadas locales -->
</g>
```

### `<pattern>` — Texturas y rellenos repetitivos
```svg
<defs>
  <pattern id="concreto" x="0" y="0" width="8" height="8"
           patternUnits="userSpaceOnUse">
    <!-- siempre en defs, nunca inline -->
  </pattern>
</defs>
<rect fill="url(#concreto)" .../>  <!-- referencia por id -->
```

### `<use>` — Instanciar símbolos
```svg
<!-- href (moderno) y xlink:href (compatibilidad) -->
<use href="#icono-cimentacion" x="200" y="300"/>
<use href="#icono-cimentacion" x="400" y="300"/>
```

### CSS embebido — Estilos que no se pierden
```svg
<defs>
  <style>
    .linea-eje { stroke: #e74c3c; stroke-width: 0.5; stroke-dasharray: 8,4,2,4; }
    .linea-estructura { stroke: #000; stroke-width: 1.5; fill: none; }
    .texto-cota { font-family: Arial, sans-serif; font-size: 8px; fill: #333; }
    .texto-titulo { font-family: Arial, sans-serif; font-size: 12px; font-weight: bold; }
  </style>
</defs>
<!-- Uso -->
<line class="linea-eje" x1="0" y1="100" x2="800" y2="100"/>
<text class="texto-cota" x="50" y="90">2.50 m</text>
```

### `<clipPath>` — Recortar sin deformar
```svg
<defs>
  <clipPath id="zona-dibujo">
    <rect x="40" y="40" width="720" height="480"/>
  </clipPath>
</defs>
<g clip-path="url(#zona-dibujo)">
  <!-- los elementos aquí no saldrán del área de dibujo -->
</g>
```

## Proceso

```
1. ESTRUCTURA  → definir capas (estructura, anotaciones, título) antes de escribir
2. DEFS        → declarar todos los patterns, símbolos y estilos en <defs>
3. FONDO       → rect blanco explícito (no confiar en el default del renderer)
4. CONTENIDO   → construir por capas, de lo más grande a lo más pequeño
5. ESTILOS     → CSS embebido en <style> dentro de <defs>, nunca atributos inline repetidos
6. VALIDAR     → correr por el skill `ui-visual-validator` antes de exportar
```

## Reglas

- Siempre incluir `xmlns="http://www.w3.org/2000/svg"` en el tag raíz
- Siempre incluir `xmlns:xlink="http://www.w3.org/1999/xlink"` si se usan `<use>`
- Nunca usar `style` inline si el mismo estilo se repite más de 2 veces → moverlo a `<style>`
- Los IDs deben ser únicos en todo el documento — nunca repetir un id
- Nunca usar gradientes complejos si el destino es PDF (usar fills sólidos o patterns)
- El fondo blanco explícito es obligatorio — sin él, PDF puede renderizar fondo negro

## Variaciones

**Artefacto interactivo (web):** agregar `<script>` con event listeners para hover/click en elementos del diagrama.

**SVG para PDF:** omitir `<script>`, usar solo fills sólidos o patterns de líneas, fuentes seguras (Arial, Helvetica).

**SVG para email/Notion:** simplificar al máximo — sin `<defs>` complejos, sin CSS, solo atributos inline básicos.
