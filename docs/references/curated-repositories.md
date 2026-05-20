# Repositorios de Referencia — Por Dominio

**Fuente:** Selección curada de repositorios open-source para arquitecturas modernas,
datos espaciales y flujos de trabajo avanzados.
**Última revisión:** 2025-05-20

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

## Skills futuros identificados

A partir de estos repositorios, los siguientes skills tienen alta prioridad:

| Skill futuro | Patrón | Categoría | Fuente |
|---|---|---|---|
| `bim-ifc-extractor` | sequential-workflow | workflow-automation | IfcOpenShell |
| `point-cloud-processor` | sequential-workflow | workflow-automation | PDAL |
| `mcp-server-builder` | sequential-workflow | mcp-enhancement | mcp-for-beginners |
| `react-pdf-generator` | sequential-workflow | document-creation | react-pdf |
| `pdf-form-filler` | sequential-workflow | workflow-automation | pdf-lib |

---

*Próxima revisión: cuando se explore alguno de estos repositorios en profundidad.*
