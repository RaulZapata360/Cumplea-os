# Quick Start — Cálculo Estructural

## Stack base recomendado

| Necesidad | Herramienta |
|-----------|-------------|
| Cálculo y automatización | Python (numpy, scipy, pandas) |
| Reporte de resultados | Excel / PDF generado por Python |
| Diagramas de sección y planta | matplotlib / plotly |
| Normativa de referencia | NSR-10 (Colombia) / RCDF / ACI 318 |

## Primer paso

1. Definir el tipo de análisis: ¿vigas, losas, marcos, cimentaciones?
2. Identificar la normativa aplicable al proyecto.
3. Definir el formato de entrega: ¿memoria de cálculo en PDF? ¿tabla en Excel?
4. Crear estructura del proyecto:
   ```
   /
   ├── inputs/          ← datos de entrada (cargas, geometría)
   ├── calcs/           ← scripts de cálculo Python
   ├── outputs/         ← reportes generados
   └── refs/            ← artículos de norma relevantes
   ```

## Checklist antes de entregar

- [ ] Unidades consistentes en todo el cálculo
- [ ] Verificación manual de al menos 1 caso crítico
- [ ] Norma citada en el reporte
- [ ] Hipótesis y simplificaciones documentadas
- [ ] Resultados con factores de seguridad explícitos

## Repositorios de referencia

| Repositorio | Para qué |
|-------------|----------|
| [PDAL/PDAL](https://github.com/PDAL/PDAL) | Filtrado de nubes de puntos LiDAR/fotogrametría/drones |
| [IfcOpenShell/IfcOpenShell](https://github.com/IfcOpenShell/IfcOpenShell) | Extracción de volúmenes y parámetros desde modelos BIM/IFC |
| [geopandas/geopandas](https://github.com/geopandas/geopandas) | Análisis geoespacial, áreas, distancias, transformación de coordenadas |

## Skills relevantes

- `pdf-generator` — generar memorias de cálculo en PDF desde Python
- `pdf-reader` — extraer tablas y datos de planos y normativas en PDF
