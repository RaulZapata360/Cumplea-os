# PDF Generator

Genera documentos PDF profesionales a partir de texto, datos o markdown usando Python. Cubre reportes, memorias de cálculo, propuestas comerciales y cualquier documento estructurado listo para entregar.

## Cuándo usar

- El usuario quiere exportar un reporte, propuesta o documento como PDF
- Se necesita un PDF con diseño: portada, secciones, tablas, gráficas, pie de página
- El output final debe ser un archivo `.pdf` compartible

## Librerías disponibles (elige según el caso)

| Librería | Mejor para | Instalar |
|---|---|---|
| `reportlab` | Control total del layout, tablas complejas, gráficas | `pip install reportlab` |
| `weasyprint` | Renderizar HTML/CSS → PDF, diseño rico | `pip install weasyprint` |
| `fpdf2` | PDFs simples, rápido de implementar | `pip install fpdf2` |
| `markdown + weasyprint` | Convertir markdown a PDF con estilos | ambas |

**Regla de selección:**
- Documento con tablas de datos → `reportlab`
- Documento con diseño visual rico → `weasyprint` + HTML/CSS
- Documento simple (texto + secciones) → `fpdf2`
- Input es markdown → `markdown` + `weasyprint`

## Proceso

```
1. ENTENDER  -> Tipo de documento, contenido, nivel de diseño requerido
2. ELEGIR    -> Seleccionar librería según la tabla anterior
3. ESTRUCTURA -> Definir secciones: portada, índice, cuerpo, anexos
4. GENERAR   -> Implementar y renderizar el PDF
5. VERIFICAR -> Confirmar que el archivo se generó correctamente
```

## Implementación base — reportlab (tablas y datos)

```python
from reportlab.lib.pagesizes import A4, letter
from reportlab.lib.styles import getSampleStyleSheet, ParagraphStyle
from reportlab.lib.units import cm
from reportlab.lib import colors
from reportlab.platypus import (
    SimpleDocTemplate, Paragraph, Spacer, Table, TableStyle,
    PageBreak, HRFlowable
)

# ── Configuración ─────────────────────────────────────────────────────────────
OUTPUT = "reporte.pdf"
doc = SimpleDocTemplate(
    OUTPUT,
    pagesize=A4,
    rightMargin=2*cm, leftMargin=2*cm,
    topMargin=2.5*cm, bottomMargin=2*cm
)

styles = getSampleStyleSheet()
story  = []

# ── Estilos personalizados ────────────────────────────────────────────────────
title_style = ParagraphStyle(
    'CustomTitle',
    parent=styles['Title'],
    fontSize=24,
    spaceAfter=12,
    textColor=colors.HexColor('#1F4788')
)
heading_style = ParagraphStyle(
    'CustomHeading',
    parent=styles['Heading1'],
    fontSize=14,
    spaceBefore=12,
    spaceAfter=6,
    textColor=colors.HexColor('#1F4788')
)
body_style = ParagraphStyle(
    'CustomBody',
    parent=styles['Normal'],
    fontSize=11,
    leading=16,
    spaceAfter=8
)

# ── Portada ───────────────────────────────────────────────────────────────────
story.append(Spacer(1, 4*cm))
story.append(Paragraph("Título del Documento", title_style))
story.append(Paragraph("Subtítulo o descripción breve", styles['Normal']))
story.append(Spacer(1, 1*cm))
story.append(HRFlowable(width="100%", thickness=2, color=colors.HexColor('#1F4788')))
story.append(Spacer(1, 0.5*cm))
story.append(Paragraph("Autor · Fecha · Versión", styles['Normal']))
story.append(PageBreak())

# ── Sección de contenido ──────────────────────────────────────────────────────
story.append(Paragraph("1. Introducción", heading_style))
story.append(Paragraph("Texto de la sección aquí...", body_style))
story.append(Spacer(1, 0.5*cm))

# ── Tabla de datos ────────────────────────────────────────────────────────────
data = [
    ["Parámetro", "Valor", "Unidad", "Estado"],
    ["Carga muerta", "2.5", "kN/m²", "OK"],
    ["Carga viva",   "1.8", "kN/m²", "OK"],
    ["Total",        "4.3", "kN/m²", "✓"],
]
table = Table(data, colWidths=[5*cm, 3*cm, 3*cm, 3*cm])
table.setStyle(TableStyle([
    ('BACKGROUND',  (0, 0), (-1, 0),  colors.HexColor('#1F4788')),
    ('TEXTCOLOR',   (0, 0), (-1, 0),  colors.white),
    ('FONTNAME',    (0, 0), (-1, 0),  'Helvetica-Bold'),
    ('FONTSIZE',    (0, 0), (-1, -1), 10),
    ('ROWBACKGROUNDS', (0, 1), (-1, -1), [colors.white, colors.HexColor('#EEF2FF')]),
    ('GRID',        (0, 0), (-1, -1), 0.5, colors.HexColor('#CCCCCC')),
    ('ALIGN',       (1, 1), (-1, -1), 'CENTER'),
    ('VALIGN',      (0, 0), (-1, -1), 'MIDDLE'),
    ('TOPPADDING',  (0, 0), (-1, -1), 6),
    ('BOTTOMPADDING',(0,0), (-1, -1), 6),
]))
story.append(table)
story.append(Spacer(1, 0.5*cm))

# ── Generar ───────────────────────────────────────────────────────────────────
doc.build(story)
print(f"PDF generado: {OUTPUT}")
```

## Implementación base — weasyprint (HTML/CSS → PDF)

```python
from weasyprint import HTML, CSS

html_content = """
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<style>
  body { font-family: 'Helvetica Neue', Arial, sans-serif; margin: 0; color: #333; }
  .cover { height: 100vh; display: flex; flex-direction: column;
            justify-content: center; padding: 4cm; background: #1F4788; color: white; }
  .cover h1 { font-size: 36px; margin: 0 0 12px; }
  section { padding: 2cm; page-break-before: always; }
  h2 { color: #1F4788; border-bottom: 2px solid #1F4788; padding-bottom: 8px; }
  table { width: 100%; border-collapse: collapse; margin: 16px 0; }
  th { background: #1F4788; color: white; padding: 10px; text-align: left; }
  td { padding: 8px 10px; border-bottom: 1px solid #ddd; }
  tr:nth-child(even) { background: #EEF2FF; }
</style>
</head>
<body>
  <div class="cover">
    <h1>Título del Documento</h1>
    <p>Subtítulo · Fecha · Autor</p>
  </div>
  <section>
    <h2>1. Introducción</h2>
    <p>Contenido de la sección...</p>
    <table>
      <tr><th>Parámetro</th><th>Valor</th><th>Unidad</th></tr>
      <tr><td>Dato 1</td><td>100</td><td>kg</td></tr>
      <tr><td>Dato 2</td><td>200</td><td>m²</td></tr>
    </table>
  </section>
</body>
</html>
"""

HTML(string=html_content).write_pdf("documento.pdf")
print("PDF generado: documento.pdf")
```

## Checklist antes de entregar

- [ ] El PDF abre correctamente sin errores
- [ ] Todas las páginas tienen márgenes consistentes
- [ ] Las tablas no se cortan entre páginas
- [ ] La portada tiene título, autor y fecha
- [ ] Los números de página están presentes (si aplica)
- [ ] El archivo se guardó en la ruta correcta

## Cómo activar

```
"Genera un PDF de este reporte: [contenido o datos]"
"Convierte este markdown a PDF con diseño profesional"
"Crea una memoria de cálculo en PDF con estos resultados"
"Genera una propuesta comercial en PDF para [cliente]"
```
