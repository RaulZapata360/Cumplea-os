# SVG to PDF

Convierte SVG técnicos a PDF sin romper líneas, fuentes ni proporciones. Los tres
problemas más comunes — fuentes sustituidas, líneas desaparecidas y coordenadas
cortadas — tienen causas específicas y soluciones directas.

## Los 5 problemas más frecuentes al convertir SVG a PDF

| Problema | Causa | Solución |
|----------|-------|----------|
| Fuentes cambian o desaparecen | La fuente no está embebida ni disponible | Usar fuentes seguras o convertir texto a path |
| Líneas muy delgadas desaparecen | stroke-width < 0.3 en pantalla = invisible en impresión | stroke-width mínimo 0.5 para impresión |
| El plano sale cortado | viewBox no coincide con el contenido real | Ajustar viewBox para que incluya todos los elementos |
| Fondo negro en lugar de blanco | No hay rect de fondo explícito | Agregar `<rect width="100%" height="100%" fill="white"/>` |
| Gradientes se convierten en raster | Los motores PDF rasterizan gradientes complejos | Reemplazar con fills sólidos o patterns de líneas |

## Proceso

### Paso 1 — Pre-validación del SVG

Antes de convertir, verificar (o correr skill `ui-visual-validator`):

```
[ ] viewBox definido y sin coordenadas negativas
[ ] Fondo blanco explícito como primer elemento
[ ] stroke-width mínimo 0.5 en todas las líneas
[ ] Fuentes especificadas como stack seguro: font-family="Arial, Helvetica, sans-serif"
[ ] Sin gradientes — solo fills sólidos o patterns
[ ] Sin elementos con opacity: 0 que ocupen espacio (borrar o comentar)
```

### Paso 2 — Ajustar el viewBox al contenido

El viewBox debe abrazar exactamente el contenido. Si el plano tiene margen de 20 unidades:
```svg
<!-- Sin margen (contenido cortado) -->
<svg viewBox="0 0 800 600">

<!-- Con margen explícito -->
<svg viewBox="-20 -20 840 640">
```

Para calcular el viewBox correcto:
```
x_min = coordenada X más pequeña de todos los elementos - margen
y_min = coordenada Y más pequeña de todos los elementos - margen
ancho = (x_max - x_min) + 2 * margen
alto  = (y_max - y_min) + 2 * margen
```

### Paso 3 — Preparar fuentes

**Opción A — Stack de fuentes seguras (más simple):**
```svg
<style>
  text { font-family: Arial, Helvetica, sans-serif; }
</style>
```

**Opción B — Convertir texto crítico a `<path>` (más robusto):**
Para texto con fuente específica en planos donde la exactitud tipográfica importa,
convertir cada texto a path usando Inkscape o FontForge antes de exportar a PDF.

**Opción C — Embeber fuente como base64 en `<style>`:**
```svg
<style>
  @font-face {
    font-family: 'MiFuente';
    src: url('data:font/woff2;base64,...') format('woff2');
  }
</style>
```

### Paso 4 — Herramientas de conversión

**Python (más control):**
```python
# Instalar: pip install cairosvg
import cairosvg

cairosvg.svg2pdf(
    url="plano.svg",
    write_to="plano.pdf",
    output_width=794,   # A4 en puntos (72dpi)
    output_height=1123
)
```

**Node.js (puppeteer — máxima fidelidad):**
```javascript
const puppeteer = require('puppeteer');
const browser = await puppeteer.launch();
const page = await browser.newPage();
await page.goto('file://' + path.resolve('plano.svg'));
await page.pdf({
  path: 'plano.pdf',
  printBackground: true,
  width: '297mm',
  height: '210mm',
});
await browser.close();
```
Puppeteer usa el motor de Chrome — la conversión más fiel a como se ve en el navegador.

**Inkscape CLI:**
```bash
inkscape plano.svg --export-type=pdf --export-filename=plano.pdf
```

### Paso 5 — Post-validación

Abrir el PDF y verificar:
```
[ ] Todas las líneas visibles (ninguna desapareció por stroke-width cero)
[ ] Fuentes correctas o sustituidas por la fuente fallback esperada
[ ] Sin recortes en los bordes
[ ] Fondo blanco (no negro, no transparente)
[ ] Tamaño de página correcto (A4, A3, carta o custom según el plano)
[ ] Zonas de hatch/pattern renderizadas como vectores, no como imagen pixelada
```

## Tamaños de página de referencia

| Formato | Dimensiones (mm) | Uso típico |
|---------|-----------------|------------|
| A4 | 210 × 297 | Memorias, informes |
| A3 | 297 × 420 | Planos de detalle |
| A1 | 594 × 841 | Planos de conjunto |
| Carta | 215.9 × 279.4 | Documentos EUA/Colombia |

## Reglas

- Nunca usar `opacity` en elementos de línea para simular colores grises — usar `stroke="#aaa"` directamente
- Los patterns deben usar `patternUnits="userSpaceOnUse"` para mantener escala en PDF
- Si se usa Puppeteer, el SVG debe tener `width` y `height` explícitos en mm o en pts
- Verificar siempre el PDF en un visor diferente al que lo generó (Adobe Reader vs Preview)
- Para planos con múltiples hojas, generar un SVG por hoja y combinar PDFs después
