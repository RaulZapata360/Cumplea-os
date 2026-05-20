# Repositorios de Referencia — Por Dominio

**Fuente:** Selección curada de repositorios open-source para arquitecturas modernas,
datos espaciales y flujos de trabajo avanzados.
**Última revisión:** 2026-05-20

---

## 1. Ingeniería, Cálculo y Topografía Espacial

| Repositorio | Qué enseña | Skills relacionados |
|-------------|-----------|---------------------|
| [PDAL/PDAL](https://github.com/PDAL/PDAL) | Filtrado y procesamiento de nubes de puntos (LiDAR, fotogrametría, drones) | `pdf-generator` (memorias de cálculo) |
| [IfcOpenShell/IfcOpenShell](https://github.com/IfcOpenShell/IfcOpenShell) | Extracción de parámetros geométricos y cálculos desde modelos BIM/IFC | Futuro skill: `bim-ifc-extractor` |
| [geopandas/geopandas](https://github.com/geopandas/geopandas) | Operaciones espaciales y cálculos geométricos en Python | `pdf-reader` (extracción de datos) |

### Notas de uso

**PDAL** — Point Data Abstraction Library. Estándar para traducir y procesar nubes de puntos.
Estudiar para: estructurar filtrado de datos de fotogrametría, levantamientos topográficos, drones.

**IfcOpenShell** — Trabaja con formato IFC (Industry Foundation Classes) de BIM.
Estudiar para: extraer volúmenes, áreas, parámetros estructurales directamente de modelos.

**geopandas** — Extiende pandas con tipos de datos espaciales (GeoDataFrame, geometrías).
Estudiar para: análisis geoespacial, transformaciones de coordenadas, cálculos de área/distancia.

---

## 2. Desarrollo Web y Ventas (CRMs / Portales)

| Repositorio | Stack | Qué enseña |
|-------------|-------|-----------|
| [twentyhq/twenty](https://github.com/twentyhq/twenty) | TypeScript / React | Arquitectura CRM escalable, modelo de datos complejo |
| [pdovhomilja/nextcrm-app](https://github.com/pdovhomilja/nextcrm-app) | Next.js 16, React 19, PostgreSQL, Prisma, shadcn/ui | CRM completo: proyectos, facturación, contactos |
| [vercel/next.js examples](https://github.com/vercel/next.js/tree/canary/examples) | Next.js | Autenticación, Supabase, pasarelas de pago, cientos de patrones |

### Notas de uso

**twenty** — Alternativa open-source a Salesforce. Caso de estudio para CRM desde cero.
Estudiar para: modelo de datos de ventas, relaciones entre entidades, UI para pipelines.

**nextcrm-app** — CRM productivo con stack moderno.
Estudiar para: integración Next.js + Prisma + PostgreSQL, gestión de leads y proyectos.

**Next.js examples** — Carpeta de ejemplos oficial. Cientos de integraciones listas.
Estudiar para: auth (NextAuth), DB (Supabase), pagos (Stripe), despliegue (Vercel).

---

## 3. Visualización 3D y Entornos Web

| Repositorio | Qué enseña | Skills relacionados |
|-------------|-----------|---------------------|
| [mrdoob/three.js](https://github.com/mrdoob/three.js) | Renderizado 3D en navegador: iluminación, texturas, GLTF/GLB, físicas | `web-design` quickstart |
| [potree/potree](https://github.com/potree/potree) | Renderizado WebGL de nubes de puntos masivas (LiDAR sin colapsar memoria) | Futuro skill: `potree-viewer` |
| [IFCjs/web-ifc](https://github.com/IFCjs/web-ifc) | Parsing y visualización de modelos BIM en el navegador | Futuro skill: `bim-web-viewer` |

### Notas de uso

**three.js** — Motor 3D web estándar. El directorio `/examples` es un currículum completo.
Estudiar para: modelos 3D en web, visualización de estructuras, terrenos, animaciones.

**Potree** — Especializado en nubes de puntos de gigabytes en WebGL.
Estudiar para: visualizar datos LiDAR o fotogrametría de drones en web sin degradación.

**web-ifc (That Open Company)** — Parsea IFC pesados para web.
Estudiar para: viewer BIM en navegador, extracción de propiedades de elementos estructurales.

---

## 4. Generación y Manipulación de PDFs

| Repositorio | Stack | Qué enseña |
|-------------|-------|-----------|
| [diegomura/react-pdf](https://github.com/diegomura/react-pdf) | React / JSX | PDFs desde componentes React: reportes, libros digitales, control total de diseño |
| [Hopding/pdf-lib](https://github.com/Hopding/pdf-lib) | JavaScript / TypeScript | Editar PDFs existentes: formularios, firmas, unir planos, marcas de agua |

### Notas de uso

**react-pdf** — Crea PDFs con JSX igual que una interfaz React.
Estudiar para: reportes técnicos, guías, e-books generados desde datos.
Complementa: nuestro skill `pdf-generator` (que usa reportlab/weasyprint en Python).

**pdf-lib** — Pura JS, sin dependencias. Edita PDFs ya existentes.
Estudiar para: rellenar formularios, insertar firmas digitales, unir planos de planta,
estampar marcas de agua. Útil para procesos de firma de contratos o entrega de planos.

---

## 5. Model Context Protocol (MCP) y Vibe Coding

| Repositorio | Qué enseña | Skills relacionados |
|-------------|-----------|---------------------|
| [microsoft/mcp-for-beginners](https://github.com/microsoft/mcp-for-beginners) | Fundamentos MCP, laboratorios prácticos, servidores modulares | Futuro skill: `mcp-server-builder` |
| [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) | Implementaciones de referencia: Google Drive, PostgreSQL, GitHub, filesystem | `example-deploy-vercel` (usa MCP Vercel) |

### Notas de uso

**mcp-for-beginners (Microsoft)** — Currículum oficial paso a paso sobre MCP.
Estudiar para: arquitectura cliente-servidor MCP, herramientas, recursos y prompts.
Ideal para crear skills de categoría `mcp-enhancement`.

**modelcontextprotocol/servers** — Implementaciones de referencia oficiales.
Estudiar para: ver cómo conectar Claude con Google Drive, PostgreSQL, GitHub, sistemas
de archivos locales. Cada servidor es un caso de estudio de `multi-mcp-coordination`.

---

## 6. Cálculos en Flujos e Iteraciones (Workflows & DAGs)

| Repositorio | Stack | Qué enseña |
|-------------|-------|-----------|
| [apache/airflow](https://github.com/apache/airflow) | Python | Estándar de la industria para orquestar flujos: dependencias entre tareas, reintentos automáticos, ejecuciones programadas |
| [n8n-io/n8n](https://github.com/n8n-io/n8n) | TypeScript / Node.js | Automatización visual basada en nodos: cómo iterar sobre arrays y pasar datos entre bloques lógicos y APIs |
| [prefecthq/prefect](https://github.com/prefecthq/prefect) | Python | Alternativa moderna a Airflow: convierte funciones de cálculo en pipelines resilientes y observables |

### Notas de uso

**Airflow** — Estándar para cálculos complejos multi-paso (topografía → volúmenes → reporte).
Estudiar para: estructurar DAGs, manejar dependencias entre tareas, reintentos y programación recurrente.

**n8n** — Visual y accesible. Excelente para entender cómo fluyen datos entre bloques.
Estudiar para: automatización sin-código que luego se convierte en skill `workflow-automation`.

**Prefect** — Más pythónico y moderno que Airflow.
Estudiar para: convertir scripts de cálculo existentes en pipelines con observabilidad y resiliencia.

---

## 7. Finanzas y Gestión de Negocios

| Repositorio | Stack | Qué enseña |
|-------------|-------|-----------|
| [midday-ai/midday](https://github.com/midday-ai/midday) | Next.js / Supabase | Sistema operativo financiero open-source: facturación, conciliación bancaria, dashboards financieros |
| [ghostfolio/ghostfolio](https://github.com/ghostfolio/ghostfolio) | Angular / Node.js | Gestión de patrimonio: cálculo de ROI, historial de transacciones, gráficos financieros interactivos |

### Notas de uso

**midday** — El repositorio definitivo para estructurar datos financieros en stack moderno.
Estudiar para: modelo de datos de facturación, conciliación bancaria, dashboards financieros.
Complementa: `executive-dashboard` quickstart.

**ghostfolio** — Especializado en portafolios de inversión.
Estudiar para: cómo se calculan retornos (ROI), historial de transacciones, visualización de patrimonio.
Útil para: clientes que necesitan reportes de rentabilidad o seguimiento de inversiones.

---

## 8. Marketing y Analítica de Crecimiento

| Repositorio | Stack | Qué enseña |
|-------------|-------|-----------|
| [dubinc/dub](https://github.com/dubinc/dub) | Next.js | Infraestructura de enlaces de marketing: rastreo de clics, geolocalización, metadatos SEO, atribución de campañas |
| [PostHog/posthog](https://github.com/PostHog/posthog) | Python / TypeScript | Plataforma de analítica de producto: embudos de conversión, pruebas A/B en código, comportamiento real del usuario |

### Notas de uso

**dub** — Clase magistral de marketing en código.
Estudiar para: rastrear clics, mapear geolocalización, estructurar metadatos para SEO, atribución multi-canal.
Complementa: `seo-intent-analyzer`, `campaign-retrospective-builder`.

**PostHog** — Analítica de producto a escala masiva, todo open-source.
Estudiar para: arquitectura de funnels, implementación de A/B testing, event tracking y retención.
Complementa: `ab-copy-variants-generator`, `cta-optimizer`.

---

## 9. UI / UX (Experiencia e Interfaz de Usuario)

| Repositorio | Stack | Qué enseña |
|-------------|-------|-----------|
| [shadcn-ui/ui](https://github.com/shadcn-ui/ui) | React / Tailwind CSS | No es una librería instalable — es código fuente copiable. Enseña componentes con Tailwind, diseño minimalista e interfaces profesionales |
| [radix-ui/primitives](https://github.com/radix-ui/primitives) | React | Fundamentos invisibles del UX: foco de teclado, accesibilidad para lectores de pantalla, estado interno de componentes complejos |
| [vercel/satori](https://github.com/vercel/satori) | TypeScript | Convierte HTML/CSS en imágenes SVG: generación dinámica de Open Graph images para redes sociales y previsualizaciones de enlaces |

### Notas de uso

**shadcn/ui** — La forma correcta de aprender UI moderna: el código vive en tu proyecto.
Estudiar para: estructura de componentes Tailwind, variantes, temas, sistema de diseño sin dependencia de terceros.
Complementa: `web-design` quickstart, cualquier skill que genere interfaces.

**radix-ui** — Base de shadcn y de gran parte de la web moderna.
Estudiar para: accesibilidad real (a11y), foco de teclado, estados ARIA, componentes complejos (dialogs, dropdowns, menus).

**satori (Vercel)** — Generación de imágenes desde markup.
Estudiar para: Open Graph dinámico, thumbnails para PDFs compartidos en redes, previsualizaciones de contenido.
Complementa: `youtube-thumbnail-designer`, `linkedin-post-generator`.

---

## Skills futuros identificados

A partir de estos repositorios, los siguientes skills tienen alta prioridad:

| Skill futuro | Patrón | Categoría | Fuente |
|---|---|---|---|
| `bim-ifc-extractor` | sequential-workflow | workflow-automation | IfcOpenShell |
| `point-cloud-processor` | sequential-workflow | workflow-automation | PDAL |
| `mcp-server-builder` | sequential-workflow | mcp-enhancement | mcp-for-beginners |
| `react-pdf-generator` | sequential-workflow | document-creation | react-pdf |
| `pdf-form-filler` | sequential-workflow | workflow-automation | pdf-lib |
| `dag-workflow-builder` | sequential-workflow | workflow-automation | Airflow / Prefect |
| `financial-dashboard` | context-aware-branching | document-creation | midday / ghostfolio |
| `campaign-analytics` | sequential-workflow | workflow-automation | PostHog / dub |
| `og-image-generator` | sequential-workflow | document-creation | satori |

---

*Próxima revisión: cuando se explore alguno de estos repositorios en profundidad.*
