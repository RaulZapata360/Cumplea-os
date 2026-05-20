# PDF Reader

Extrae el contenido de cualquier PDF — texto, tablas, metadatos — y lo guarda en archivos `.md` estructurados y legibles. Ideal para procesar contratos, reportes, normativas, papers o cualquier documento antes de analizarlo.

## Cuándo usar

- El usuario comparte un PDF y quiere su contenido en texto/markdown
- Se necesita extraer tablas de datos de un PDF
- Se quiere resumir o indexar múltiples PDFs
- El contenido del PDF va a ser procesado por Claude u otro flujo

## Librerías disponibles

| Librería | Mejor para | Instalar |
|---|---|---|
| `pdfplumber` | Texto + tablas con coordenadas precisas | `pip install pdfplumber` |
| `pymupdf` (fitz) | Velocidad, PDFs escaneados, imágenes | `pip install pymupdf` |
| `pdfminer.six` | Texto puro, control fino del layout | `pip install pdfminer.six` |
| `camelot` | Extracción de tablas complejas | `pip install camelot-py[cv]` |

**Regla de selección:**
- PDF con tablas → `pdfplumber` o `camelot`
- PDF grande / rápido → `pymupdf`
- PDF escaneado (imagen) → `pymupdf` + OCR (`pytesseract`)
- Solo texto → `pdfminer.six`

## Proceso

```
1. CARGAR    -> Abrir el PDF e inspeccionar estructura (páginas, columnas, tablas)
2. EXTRAER   -> Texto por sección + tablas por separado
3. LIMPIAR   -> Eliminar artefactos (saltos de línea dobles, headers repetidos, números de página)
4. ESTRUCTURAR -> Mapear H1/H2/H3 desde el formato del PDF (negritas, tamaños, numeración)
5. GUARDAR   -> Escribir archivo .md con el contenido estructurado
```

## Implementación base — pdfplumber (texto + tablas)

```python
import pdfplumber
import re
from pathlib import Path

PDF_PATH = "documento.pdf"
OUT_PATH = Path(PDF_PATH).stem + ".md"

def limpiar_texto(texto: str) -> str:
    texto = re.sub(r'\n{3,}', '\n\n', texto)   # colapsar saltos excesivos
    texto = re.sub(r'[ \t]+', ' ', texto)        # normalizar espacios
    return texto.strip()

def tabla_a_markdown(tabla) -> str:
    if not tabla or not tabla[0]:
        return ""
    # Encabezado
    encabezado = "| " + " | ".join(str(c or "") for c in tabla[0]) + " |"
    separador  = "| " + " | ".join(["---"] * len(tabla[0])) + " |"
    filas = [
        "| " + " | ".join(str(c or "") for c in fila) + " |"
        for fila in tabla[1:]
    ]
    return "\n".join([encabezado, separador] + filas)

lineas_md = [f"# {Path(PDF_PATH).stem}\n"]

with pdfplumber.open(PDF_PATH) as pdf:
    lineas_md.append(f"**Páginas:** {len(pdf.pages)}  ")
    lineas_md.append(f"**Extraído:** {__import__('datetime').date.today()}\n\n---\n")

    for i, pagina in enumerate(pdf.pages, start=1):
        lineas_md.append(f"\n## Página {i}\n")

        # Texto
        texto = pagina.extract_text()
        if texto:
            lineas_md.append(limpiar_texto(texto))

        # Tablas
        tablas = pagina.extract_tables()
        for j, tabla in enumerate(tablas, start=1):
            lineas_md.append(f"\n### Tabla {i}.{j}\n")
            lineas_md.append(tabla_a_markdown(tabla))

with open(OUT_PATH, "w", encoding="utf-8") as f:
    f.write("\n".join(lineas_md))

print(f"Extraído: {OUT_PATH}")
```

## Implementación alternativa — pymupdf (rápida, PDFs grandes)

```python
import fitz  # pymupdf
from pathlib import Path

PDF_PATH = "documento.pdf"
OUT_PATH = Path(PDF_PATH).stem + ".md"

doc = fitz.open(PDF_PATH)
secciones = [f"# {Path(PDF_PATH).stem}\n\n**Páginas:** {doc.page_count}\n\n---\n"]

for i, pagina in enumerate(doc, start=1):
    texto = pagina.get_text("text")
    if texto.strip():
        secciones.append(f"\n## Página {i}\n")
        secciones.append(texto.strip())

with open(OUT_PATH, "w", encoding="utf-8") as f:
    f.write("\n".join(secciones))

doc.close()
print(f"Extraído: {OUT_PATH}")
```

## PDFs escaneados (imagen → texto)

```python
import fitz
import pytesseract
from PIL import Image
import io
from pathlib import Path

PDF_PATH = "escaneado.pdf"
OUT_PATH = Path(PDF_PATH).stem + ".md"

doc = fitz.open(PDF_PATH)
secciones = [f"# {Path(PDF_PATH).stem} (OCR)\n\n---\n"]

for i, pagina in enumerate(doc, start=1):
    # Renderizar página como imagen a 300 DPI
    mat = fitz.Matrix(300/72, 300/72)
    pix = pagina.get_pixmap(matrix=mat)
    img = Image.open(io.BytesIO(pix.tobytes("png")))
    texto = pytesseract.image_to_string(img, lang="spa+eng")
    if texto.strip():
        secciones.append(f"\n## Página {i}\n")
        secciones.append(texto.strip())

with open(OUT_PATH, "w", encoding="utf-8") as f:
    f.write("\n".join(secciones))

print(f"OCR completado: {OUT_PATH}")
```

## Estructura del archivo .md generado

```markdown
# nombre-del-archivo

**Páginas:** 24
**Extraído:** 2025-05-20

---

## Página 1

[Texto de la primera página]

## Página 2

[Texto...]

### Tabla 2.1

| Columna A | Columna B | Columna C |
|---|---|---|
| dato | dato | dato |
```

## Post-extracción: qué hacer con el .md

Una vez extraído, el `.md` puede ser:
- Cargado como contexto en Claude para Q&A sobre el documento
- Indexado en una base de conocimiento
- Resumido con el skill `writing-partner`
- Convertido de vuelta a PDF con el skill `pdf-generator`
- Procesado con `meeting-notes-extractor` si es una transcripción

## Cómo activar

```
"Lee este PDF y guarda su contenido en un archivo markdown"
"Extrae las tablas de este PDF"
"Convierte este PDF a texto para poder analizarlo"
"Tengo un PDF escaneado, extrae el texto con OCR"
```
