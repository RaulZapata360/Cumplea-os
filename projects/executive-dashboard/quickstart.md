# Quick Start — Dashboard Ejecutivo

## Stack base recomendado

| Necesidad | Herramienta |
|-----------|-------------|
| Dashboard interactivo web | Looker Studio (gratis) / Power BI |
| Visualización con código | Python + Plotly / Dash |
| Fuente de datos | Google Sheets / BigQuery / SQL |
| Exportación a PDF | Puppeteer / weasyprint |
| KPIs en tiempo real | Conexión directa a API o BD |

## Primer paso

1. Definir con el cliente los 3-5 KPIs principales (no más).
2. Identificar la fuente de datos y su frecuencia de actualización.
3. Decidir el formato: ¿interactivo en vivo o reporte PDF periódico?
4. Crear estructura del proyecto:
   ```
   /
   ├── data/            ← fuentes o conexiones
   ├── charts/          ← componentes de visualización
   ├── dashboard/       ← layout principal
   └── exports/         ← PDFs o snapshots generados
   ```

## Checklist antes de entregar

- [ ] Los KPIs tienen definición clara (fórmula + fuente de dato)
- [ ] Los colores y tipografía están alineados con la marca del cliente
- [ ] El dashboard carga en menos de 3 segundos
- [ ] Existe un acceso de solo lectura para el cliente
- [ ] Hay un owner definido para mantener los datos actualizados

## Skills relevantes

*(Agregar skills de visualización cuando se creen)*
