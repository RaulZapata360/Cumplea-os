# Algorithmic Art

Genera SVG técnico usando fórmulas matemáticas y patrones repetitivos en lugar de
coordinar puntos x,y a mano. Resuelve el problema de sombreado de materiales, acero
de refuerzo, capas de suelo y cualquier elemento que se repite con lógica geométrica.

## El principio: variables → fórmulas → elementos

Nunca repetir coordenadas. Si hay 12 barras de refuerzo cada 15cm, eso es un loop,
no 12 líneas hardcodeadas.

```python
# Pseudocódigo → luego traduce a SVG
barras = 12
separacion = 15  # px o unidades de escala
recubrimiento = 5
for i in range(barras):
    x = recubrimiento + i * separacion
    # → <circle cx="{x}" cy="..." r="3"/>
```

## Patrones técnicos de uso frecuente

### Acero de refuerzo longitudinal
```svg
<defs>
  <symbol id="barra-refuerzo" viewBox="-3 -3 6 6">
    <circle cx="0" cy="0" r="3" fill="#444" stroke="#000" stroke-width="0.5"/>
  </symbol>
</defs>
<!-- Generar posiciones: x = recubrimiento + i * separacion -->
<use href="#barra-refuerzo" x="10" y="50"/>
<use href="#barra-refuerzo" x="25" y="50"/>
<!-- ... repetir con las posiciones calculadas -->
```

### Sombreado de concreto (hatch)
```svg
<defs>
  <pattern id="hatch-concreto" x="0" y="0" width="8" height="8"
           patternUnits="userSpaceOnUse" patternTransform="rotate(45)">
    <line x1="0" y1="0" x2="0" y2="8" stroke="#999" stroke-width="0.8"/>
  </pattern>
</defs>
<rect x="0" y="0" width="200" height="100" fill="url(#hatch-concreto)" stroke="#000"/>
```

### Sombreado de suelo / relleno
```svg
<defs>
  <pattern id="hatch-suelo" x="0" y="0" width="10" height="10"
           patternUnits="userSpaceOnUse">
    <line x1="0" y1="0" x2="10" y2="10" stroke="#8B6914" stroke-width="0.6"/>
    <line x1="10" y1="0" x2="0" y2="10" stroke="#8B6914" stroke-width="0.6"/>
  </pattern>
</defs>
```

### Mampostería / ladrillo
```svg
<defs>
  <pattern id="hatch-mamposteria" x="0" y="0" width="20" height="10"
           patternUnits="userSpaceOnUse">
    <rect x="0" y="0" width="20" height="10" fill="none" stroke="#666" stroke-width="0.5"/>
    <line x1="10" y1="0" x2="10" y2="5" stroke="#666" stroke-width="0.5"/>
  </pattern>
</defs>
```

### Acero estructural / metal
```svg
<defs>
  <pattern id="hatch-acero" x="0" y="0" width="6" height="6"
           patternUnits="userSpaceOnUse" patternTransform="rotate(45)">
    <line x1="0" y1="3" x2="6" y2="3" stroke="#555" stroke-width="1"/>
  </pattern>
</defs>
```

### Línea de terreno natural
```svg
<!-- Perfil de terreno con puntos calculados algorítmicamente -->
<!-- puntos = [(x0,y0), (x1,y1), ...] generados desde datos de levantamiento -->
<polyline points="0,100 50,95 100,88 150,92 200,80"
          fill="none" stroke="#8B6914" stroke-width="1.5"/>
<!-- Sombreado bajo el perfil -->
<polygon points="0,100 50,95 100,88 150,92 200,80 200,150 0,150"
         fill="url(#hatch-suelo)" stroke="none" opacity="0.6"/>
```

## Proceso para elementos repetitivos

```
1. IDENTIFICAR   → ¿qué elemento se repite? (barras, líneas, cuadrículas, cotas)
2. PARAMETRIZAR  → cantidad, separación, offset inicial, tamaño
3. CALCULAR      → posiciones = [inicio + i * paso for i in range(n)]
4. DEFINIR       → crear <symbol> o <pattern> en <defs>
5. INSTANCIAR    → <use> o <rect fill="url(#pattern)"> con las posiciones calculadas
```

## Generación con Python (cuando el SVG es complejo)

Cuando hay más de 20 elementos o el cálculo es iterativo, usar Python para generar el SVG:

```python
import math

def generar_barras_refuerzo(n, separacion, recubrimiento, y_centro, radio=3):
    elementos = []
    ancho_total = (n - 1) * separacion + 2 * recubrimiento
    x_inicio = recubrimiento
    for i in range(n):
        x = x_inicio + i * separacion
        elementos.append(
            f'<circle cx="{x}" cy="{y_centro}" r="{radio}" '
            f'fill="#444" stroke="#000" stroke-width="0.5"/>'
        )
    return "\n".join(elementos)
```

## Reglas

- Todo elemento que se repite más de 3 veces → convertir a `<pattern>` o `<symbol>` + `<use>`
- Los patterns deben estar en `<defs>` al inicio del SVG, nunca inline
- `patternUnits="userSpaceOnUse"` para patterns que deben mantener escala absoluta
- `patternUnits="objectBoundingBox"` para patterns que deben escalar con el elemento
- Nunca hardcodear más de 5 posiciones iguales — si hay más, calcular y documentar la fórmula

## Variaciones

**Perfil transversal de vía:** terreno + sub-base + base + carpeta asfáltica, cada capa con su propio hatch y dimensión paramétrica.

**Sección transversal de viga:** concreto + barras longitudinales + estribos, todo generado desde variables: base, alto, recubrimiento, número de barras, diámetro.

**Cuadrícula de pilotes:** n×m pilotes con separación definida, generados con doble loop.
