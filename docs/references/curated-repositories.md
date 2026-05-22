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

---

## 10. Diseño Web y Animaciones con Scroll (UI/UX Dinámico)

| Repositorio | Stack | Qué enseña |
|-------------|-------|-----------|
| [darkroomengineering/lenis](https://github.com/darkroomengineering/lenis) | JS nativo | Smooth scrolling moderno y ligero; estándar en sitios Awwwards, integrado con API nativa del navegador |
| [framer/motion](https://github.com/framer/motion) | React | Animaciones con físicas reales: transiciones de página, microinteracciones, `useScroll` para animaciones atadas a posición |
| [locomotivemtl/locomotive-scroll](https://github.com/locomotivemtl/locomotive-scroll) | JS / CSS | Detección de elementos en viewport, parallax asíncrono, ideal para landing pages inmersivas |
| [greensock/GSAP](https://github.com/greensock/GSAP) | JS | Motor de animación web más potente; ScrollTrigger orquesta secuencias complejas controladas por la rueda del ratón |
| [pmndrs/drei](https://github.com/pmndrs/drei) | React / Three.js | Helpers para react-three-fiber: cámara, entornos HDRI, efectos 3D atados al scroll |

### Notas de uso

**lenis** — Reemplaza a opciones antiguas como LocomotiveScroll en proyectos nuevos.
Estudiar para: scroll suave sin jank, integración con GSAP ScrollTrigger.

**framer/motion** — La librería de animación estándar en el ecosistema React.
Estudiar para: `AnimatePresence`, transiciones de layout, gestos táctiles, scroll-linked animations.

**GSAP + ScrollTrigger** — Para secuencias de animación de nivel agencia/premiado.
Estudiar para: timelines, scrubbing, pin de secciones, parallax multi-capa.

**drei** — Simplifica react-three-fiber drásticamente.
Estudiar para: integrar modelos 3D con scroll sin escribir código WebGL raw.

---

## 11. Dashboards Poderosos y Paneles de Gestión

| Repositorio | Stack | Qué enseña |
|-------------|-------|-----------|
| [tremorlabs/tremor](https://github.com/tremorlabs/tremor) | React / Tailwind | Componentes de dashboard analítico: métricas, gráficas, KPIs financieros de forma rápida y elegante |
| [refinedev/refine](https://github.com/refinedev/refine) | React | Framework para apps intensivas de datos: autenticación global, ruteo, conexiones nativas a Supabase / REST |
| [marmelab/react-admin](https://github.com/marmelab/react-admin) | React | Framework empresarial back-office: CRUD masivo, consumo de REST/GraphQL, nivel de producción |
| [ant-design/ant-design-pro](https://github.com/ant-design/ant-design-pro) | React / Ant Design | Solución corporativa lista para usar: permisos, tablas infinitas, formularios anidados |
| [epicweb-dev/epic-stack](https://github.com/epicweb-dev/epic-stack) | Remix / SQLite | Stack full-stack con mejores prácticas: DB, auth, panels, seguridad y despliegue integrados |

### Notas de uso

**tremor** — El atajo más rápido para dashboards analíticos profesionales.
Estudiar para: AreaChart, BarList, KPICard — componentes listos con semántica de negocio.

**refine** — Para portales B2B y herramientas internas complejas.
Estudiar para: data providers, RBAC (control de acceso por rol), hooks de CRUD con cualquier backend.

**react-admin** — Cuando el cliente necesita un back-office de nivel enterprise sin construirlo desde cero.
Estudiar para: `<Resource>`, `<DataGrid>`, autenticación y permisos granulares.

**epic-stack** — Referencia de "la forma correcta" de hacer un proyecto full-stack moderno.
Estudiar para: arquitectura completa, testing, observabilidad y flujo de despliegue.

---

## 12. Optimización de Tokens y Model Context Protocol (MCP)

| Repositorio | Stack | Qué enseña |
|-------------|-------|-----------|
| [rtk-ai/rtk](https://github.com/rtk-ai/rtk) | Rust | Proxy CLI que reduce consumo de tokens 60-90%: agrupa, trunca y deduplica salidas de terminal antes del modelo |
| [alexgreensh/token-optimizer](https://github.com/alexgreensh/token-optimizer) | TS / Claude Code | Plugin de dashboard de tokens en tiempo real: localiza tokens perdidos, sobrevive compactaciones, evita deterioro |
| [ooples/token-optimizer-mcp](https://github.com/ooples/token-optimizer-mcp) | MCP | Servidor MCP que entrega resúmenes estructurales del código en lugar de archivos completos |
| [affaan-m/ECC](https://github.com/affaan-m/ECC) | Claude Code | Arnés completo: memoria a largo plazo, reglas y estrategias agresivas de reducción de costos en investigación |
| [microsoft/LLMLingua](https://github.com/microsoft/LLMLingua) | Python | Compresión de prompts a nivel investigación: elimina tokens redundantes sin perder semántica esencial |
| [anthropics/anthropic-cookbook](https://github.com/anthropics/anthropic-cookbook) | Python / Jupyter | Repositorio oficial Anthropic: prompts complejos, Tool Use, prompt caching y uso eficiente de la API |

### Notas de uso

**rtk** — Para sesiones largas de Claude Code donde el costo de tokens es preocupante.
Estudiar para: arquitectura de proxies de contexto, compresión de salidas de terminal.

**LLMLingua (Microsoft)** — Compresión algorítmica de prompts gigantes.
Estudiar para: pipelines de RAG donde los documentos de contexto son demasiado largos.

**anthropic-cookbook** — El mejor punto de partida para cualquier integración con la API de Claude.
Estudiar para: prompt caching, batching, streaming, tool use estructurado.

---

## 13. Automatizaciones, Potenciadores y Flujos de IA

| Repositorio | Stack | Qué enseña |
|-------------|-------|-----------|
| [langflow-ai/langflow](https://github.com/langflow-ai/langflow) | Python / React | GUI drag & drop para LangChain: prototipar agentes y sistemas RAG conectando nodos visualmente |
| [langgenius/dify](https://github.com/langgenius/dify) | Python / Next.js | Plataforma completa LLM: flujos visuales, agentes, bases vectoriales y gestión de prompts en un lugar |
| [FlowiseAI/Flowise](https://github.com/FlowiseAI/Flowise) | Node.js | Chatbots personalizados conectados a GitHub repos o PDFs; muy popular para RAG de documentos |
| [mendableai/firecrawl](https://github.com/mendableai/firecrawl) | Python / TypeScript | Crawler web para IA: convierte sitios enteros en Markdown limpio, optimizado para inyección de contexto |
| [activepieces/activepieces](https://github.com/activepieces/activepieces) | TypeScript | Alternativa open-source a Zapier: correos, tickets, CRMs, notificaciones sin licencias costosas |
| [automatisch/automatisch](https://github.com/automatisch/automatisch) | TypeScript | Automatización auto-alojada con foco en privacidad: marketing y ventas sin enviar datos a terceros |

### Notas de uso

**langflow / dify / flowise** — El trío para prototipado visual de agentes IA.
Estudiar para: entender cómo se conectan LLMs, herramientas, vectorstores y memoria en un flujo.
Diferencia: Dify es el más completo (producción), Langflow el más educativo, Flowise el más rápido.

**firecrawl** — Esencial cuando Claude necesita consumir contenido web como contexto.
Estudiar para: scraping limpio → Markdown → inyección eficiente de tokens en el prompt.

**activepieces / automatisch** — Alternativas a n8n y Zapier auto-alojadas.
Estudiar para: automatizar procesos de negocio sin dependencia de servicios de terceros ni costos de licencia.

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
| `scroll-animation-guide` | domain-intelligence | mcp-enhancement | lenis / GSAP |
| `rag-pipeline-builder` | multi-mcp-coordination | workflow-automation | firecrawl / dify |
| `token-budget-monitor` | sequential-workflow | mcp-enhancement | LLMLingua / rtk |
| `admin-panel-scaffold` | sequential-workflow | workflow-automation | refine / react-admin |

---

*Próxima revisión: cuando se explore alguno de estos repositorios en profundidad.*
