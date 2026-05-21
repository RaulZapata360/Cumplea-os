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

## Repositorios de referencia

### Componentes de dashboard
| Repositorio | Para qué |
|-------------|----------|
| [tremorlabs/tremor](https://github.com/tremorlabs/tremor) | Componentes analíticos listos: AreaChart, BarList, KPICard con semántica de negocio |
| [refinedev/refine](https://github.com/refinedev/refine) | Framework para portales B2B: autenticación, RBAC, conexión a Supabase / REST |
| [marmelab/react-admin](https://github.com/marmelab/react-admin) | Back-office empresarial: CRUD masivo, REST/GraphQL, permisos granulares |
| [ant-design/ant-design-pro](https://github.com/ant-design/ant-design-pro) | Solución corporativa: gestión de permisos, tablas infinitas, formularios anidados |

### Finanzas y analítica
| Repositorio | Para qué |
|-------------|----------|
| [midday-ai/midday](https://github.com/midday-ai/midday) | Sistema operativo financiero: facturación, conciliación bancaria, dashboards en Next.js + Supabase |
| [ghostfolio/ghostfolio](https://github.com/ghostfolio/ghostfolio) | Cálculo de ROI, historial de transacciones, gráficos de patrimonio e inversión |
| [PostHog/posthog](https://github.com/PostHog/posthog) | Funnels de conversión, A/B testing en código, event tracking y retención |
| [dubinc/dub](https://github.com/dubinc/dub) | Rastreo de clics, geolocalización, atribución de campañas en Next.js |

## Skills relevantes

- `metric-explainer` — explicar cualquier KPI financiero o SaaS con benchmarks y veredicto
- `csv-to-presentations` — convertir datos tabulares en presentaciones ejecutivas
