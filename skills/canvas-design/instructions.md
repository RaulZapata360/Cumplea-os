# Canvas Design

Diseña layouts SVG 2D técnicos con coordenadas precisas. Resuelve el mayor problema
de los LLM con SVG: calcular mal las dimensiones absolutas. La solución es trabajar
siempre con variables de escala y coordenadas relativas antes de escribir un solo punto.

## El principio central: escala primero, coordenadas después

Nunca empieces con coordenadas absolutas. Siempre define primero:

```svg
<!-- Variables de escala (comentario de referencia, no código real) -->
<!-- escala: 1 unidad = 10px -->
<!-- ancho_total: 800px = 80 unidades -->
<!-- alto_total: 600px = 60 unidades -->
<!-- margen: 40px = 4 unidades -->
```

Luego calcula todas las coordenadas derivadas de esas variables.
Esto hace que cualquier ajuste de escala sea un cambio en un solo lugar.

## Proceso

### Paso 1 — Definir el viewBox y la escala
```svg
<svg xmlns="http://www.w3.org/2000/svg"
     viewBox="0 0 800 600"
     width="800" height="600">
```
Regla: el viewBox define el sistema de coordenadas interno. `width`/`height` son el tamaño
de renderizado. Si el viewBox es `0 0 100 100` y width es `800px`, 1 unidad = 8px.

### Paso 2 — Trazar el bounding box de cada elemento

Antes de escribir el código, listar:
```
Elemento          x    y    ancho  alto
Marco exterior    0    0    800    600
Zona de dibujo   40   40   720    520
Título           40   540  720    40
Escala gráfica   600  540  120    40
```

### Paso 3 — Construir de afuera hacia adentro

Orden de construcción:
1. Fondo y marco exterior
2. Zonas y contenedores (`<g>` con `transform="translate(x,y)"`)
3. Elementos estructurales principales
4. Cotas y anotaciones
5. Leyenda y título

### Paso 4 — Usar `transform="translate()"` para grupos

En lugar de calcular coordenadas absolutas para cada sub-elemento, mover el origen:

```svg
<!-- En lugar de: línea desde (40,60) hasta (200,60) -->
<!-- Usar: grupo en (40,40), línea desde (0,20) hasta (160,20) -->
<g transform="translate(40, 40)">
  <line x1="0" y1="20" x2="160" y2="20" stroke="black" stroke-width="1"/>
</g>
```

## Elementos técnicos de referencia

### Línea de cota (dimensioning)
```svg
<g transform="translate(x, y)">
  <!-- Línea principal -->
  <line x1="0" y1="0" x2="100" y2="0" stroke="#333" stroke-width="0.5"/>
  <!-- Extremos -->
  <line x1="0" y1="-4" x2="0" y2="4" stroke="#333" stroke-width="0.5"/>
  <line x1="100" y1="-4" x2="100" y2="4" stroke="#333" stroke-width="0.5"/>
  <!-- Texto centrado -->
  <text x="50" y="-6" text-anchor="middle" font-size="8" font-family="Arial">5.00 m</text>
</g>
```

### Eje de simetría
```svg
<line x1="0" y1="0" x2="0" y2="200"
      stroke="#e74c3c" stroke-width="0.5"
      stroke-dasharray="8,4,2,4"/>
```

### Marco de plano (title block)
```svg
<rect x="0" y="0" width="800" height="600" fill="none" stroke="#000" stroke-width="2"/>
<rect x="0" y="540" width="800" height="60" fill="none" stroke="#000" stroke-width="1"/>
<text x="400" y="570" text-anchor="middle" font-size="12" font-family="Arial" font-weight="bold">
  TÍTULO DEL PLANO
</text>
```

## Checklist antes de entregar el SVG

- [ ] viewBox definido y consistente con las dimensiones de los elementos
- [ ] Escala documentada en comentario al inicio del SVG
- [ ] Todos los grupos usan `transform="translate()"` en lugar de coordenadas absolutas
- [ ] No hay elementos con coordenadas negativas (causan recorte en PDF)
- [ ] stroke-width mínimo de 0.3 para líneas visibles en PDF
- [ ] font-family especificado en cada texto (no depender de defaults del sistema)

## Reglas

- Siempre definir viewBox explícito — nunca omitirlo
- Nunca usar unidades CSS (px, em, %) dentro del SVG si el destino es PDF
- Usar `text-anchor="middle"` para etiquetas centradas, `"start"` para las alineadas a la izquierda
- Si hay más de 3 elementos similares, derivar al skill `algorithmic-art` para generarlos con fórmulas
- Para elementos reutilizables (símbolo de cimentación, perfil IPN), derivar al skill `core-components`
