# CSV to Presentations

Automatically converts tabular data (CSV, Excel) into professional PowerPoint presentations with charts and tables. Use for quarterly reports, data presentations, and executive summaries.

## How to Trigger

```
"Turn this quarterly data into slides for Monday's meeting"
"Convert this CSV into a PowerPoint presentation"
[Attach or paste CSV data]
```

## Implementation

**Required libraries:** `pandas`, `python-pptx`

```python
import pandas as pd
from pptx import Presentation
from pptx.util import Inches, Pt
from pptx.chart.data import CategoryChartData
from pptx.enum.chart import XL_CHART_TYPE
from pptx.dml.color import RGBColor

df = pd.read_csv('quarterly_metrics.csv')

prs = Presentation()
prs.slide_width = Inches(10)
prs.slide_height = Inches(7.5)

# ── Title Slide ──────────────────────────────────────────────────────────────
slide = prs.slides.add_slide(prs.slide_layouts[0])
slide.shapes.title.text = "Q1-Q4 Performance Report"
slide.placeholders[1].text = "Quarterly Metrics Overview"

# ── Data Summary Slide (Table) ───────────────────────────────────────────────
slide = prs.slides.add_slide(prs.slide_layouts[5])
slide.shapes.title.text = "Key Metrics Summary"

rows, cols = df.shape[0] + 1, df.shape[1]
table = slide.shapes.add_table(
    rows, cols,
    Inches(1), Inches(2), Inches(8), Inches(4)
).table

# Header row
for col_idx, col_name in enumerate(df.columns):
    cell = table.cell(0, col_idx)
    cell.text = col_name
    cell.fill.solid()
    cell.fill.fore_color.rgb = RGBColor(31, 71, 136)
    cell.text_frame.paragraphs[0].font.color.rgb = RGBColor(255, 255, 255)
    cell.text_frame.paragraphs[0].font.bold = True

# Data rows
for row_idx, row_data in df.iterrows():
    for col_idx, value in enumerate(row_data):
        table.cell(row_idx + 1, col_idx).text = str(value)

# ── Chart Slide: Revenue Trend (Line) ────────────────────────────────────────
slide = prs.slides.add_slide(prs.slide_layouts[5])
slide.shapes.title.text = "Revenue Trend"

chart_data = CategoryChartData()
chart_data.categories = df['Quarter'].tolist()
chart_data.add_series('Revenue', df['Revenue'].tolist())

chart = slide.shapes.add_chart(
    XL_CHART_TYPE.LINE,
    Inches(1), Inches(2), Inches(8), Inches(5),
    chart_data
).chart
chart.has_legend = True

# ── Chart Slide: User Growth (Column) ────────────────────────────────────────
slide = prs.slides.add_slide(prs.slide_layouts[5])
slide.shapes.title.text = "User Growth"

chart_data = CategoryChartData()
chart_data.categories = df['Quarter'].tolist()
chart_data.add_series('Active Users', df['Active_Users'].tolist())

slide.shapes.add_chart(
    XL_CHART_TYPE.COLUMN_CLUSTERED,
    Inches(1), Inches(2), Inches(8), Inches(5),
    chart_data
)

# ── Save ──────────────────────────────────────────────────────────────────────
prs.save('data_presentation.pptx')
print("Presentation created with data table and charts!")
```

## Customization Points

- **Theme colors**: Change `RGBColor(31, 71, 136)` for header background
- **Chart type**: Swap `XL_CHART_TYPE.LINE` for `BAR_CLUSTERED`, `PIE`, etc.
- **Column mapping**: Replace `'Quarter'`, `'Revenue'`, `'Active_Users'` with actual column names from the user's CSV
- **Output path**: Change `'data_presentation.pptx'` to desired output location

## Adapt to User's Data

Before running, inspect the CSV:
1. List available columns and their data types
2. Ask the user which columns to use as categories (X-axis) and which as series (Y-axis)
3. Ask which chart types best fit the data (trend → line, comparison → bar, composition → pie)
4. Confirm the output filename and location
