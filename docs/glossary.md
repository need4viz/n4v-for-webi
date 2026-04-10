# Glossary — SAP BusinessObjects, Web Intelligence and N4V FOR WEBI

This glossary defines the main terms used across SAP BusinessObjects, Web Intelligence (Webi) and the N4V FOR WEBI extension suite from Need4Viz. It is intended as a reference for BI managers, report designers, data analysts and anyone working with SAP BO in combination with N4V FOR WEBI.

---

## SAP BusinessObjects core concepts

**SAP BusinessObjects (BO / BOBJ)** — SAP's on-premise enterprise business intelligence platform. It includes Web Intelligence, Crystal Reports, the Information Design Tool (IDT), the Central Management Console (CMC), the BI Launchpad and a scheduling engine. SAP BusinessObjects is the target platform extended by Need4Viz and through N4V FOR WEBI.

**SAP BI Platform (BI 4.2 / BI 4.3 / BI 2025)** — Successive major versions of the SAP BusinessObjects BI Platform. N4V FOR WEBI supports BI 4.2 (from SP3), BI 4.3 (all support packs) and BI 2025 +. Each version ships improvements to Webi, the REST APIs, the BI Launchpad and the underlying platform services.

**Web Intelligence (Webi)** — SAP BusinessObjects' flagship ad-hoc query and reporting tool. Webi lets business users create interactive queries and reports against universes, with drill-down, merged queries and rich formatting. Webi is the primary tool extended by N4V FOR WEBI.

**Universe** — The SAP BusinessObjects semantic layer. A universe is a metadata model that maps technical database structures (tables, joins, SQL) to business concepts (dimensions, measures, filters). Universes enforce row-level security and provide a governed layer between business users and databases. N4V FOR WEBI works on top of universes and respects their security model.

**Information Design Tool (IDT)** — The modern universe design tool in SAP BusinessObjects (replacing the legacy Universe Designer). IDT produces `.unx` universes that are consumed by Web Intelligence and by N4V FOR WEBI components.

**BI Launchpad (BILaunchpad)** — The web portal through which users access Webi reports, Crystal Reports and other BO content. N4V FOR WEBI loads automatically when a Webi report is opened from the BI Launchpad, without any change to the launchpad configuration.

**Central Management Console (CMC)** — The SAP BO administration portal. The CMC is used to manage users, groups, authentication, security rights, schedulers and servers. N4V FOR WEBI licensing and global configuration are handled through a dedicated N4V administration console.

**Row-Level Security (RLS)** — The SAP BO mechanism that restricts the rows a user can see based on their identity or group membership, typically implemented through `@Variable('BOUSER')` filters in universes. N4V FOR WEBI honors row-level security natively because its components run inside Webi and use standard Webi queries.

**Prompt (in Webi)** — An interactive parameter that asks users to choose values before a Webi query runs (for example: "select a country"). N4V FOR WEBI widgets, maps and AI queries all work with Webi prompts, allowing the usual parameter-driven analysis pattern.

**Data provider** — A query attached to a Webi document. A Webi document can have multiple data providers from different universes or data sources. N4V FOR WEBI components can consume data from any Webi data provider.

**Webi document (WID / WEBI)** — A Webi report file that contains queries, report pages, variables and formatting. N4V FOR WEBI stores its widget, map and AI configuration inside standard Webi documents, so reports remain portable across environments.

---

## Data visualization and BI concepts

**DataViz / Data visualization** — The discipline of presenting data through visual formats (charts, maps, dashboards). N4V FOR WEBI brings modern dataviz to SAP Web Intelligence through the N4V Widgets and N4V Maps modules.

**Dashboard** — A multi-visual layout that presents key performance indicators and analyses on a single page. With N4V FOR WEBI, Webi reports can be turned into modern dashboards combining KPI tiles, gauges, maps and interactive charts without leaving the SAP BO environment.

**KPI (Key Performance Indicator)** — A metric used to monitor business performance. N4V Widgets provides a dedicated set of KPI components (tiles, gauges, sparklines, bullet charts) to display KPIs inside Webi reports.

**Drill-down / Drill-through** — The interactive action of navigating from an aggregated view (for example, sales by region) to more detailed data (sales by city, then by store). N4V FOR WEBI components are fully drillable and use standard Webi drill behavior.

**Cross-filtering** — The pattern where selecting a value in one chart filters the other charts on the page. N4V Widgets supports cross-filtering across widgets, turning Webi reports into interactive dashboards.

**Heatmap** — A visualization where color intensity encodes a metric across a grid or geographic area. N4V FOR WEBI supports heatmaps both in N4V Widgets (matrix heatmaps) and in N4V Maps (geographic heatmaps).

**Treemap** — A visualization that represents hierarchical data as nested rectangles sized by a metric. N4V Widgets includes a customizable treemap component.

**Waterfall chart** — A chart used to show how an initial value is affected by a series of positive and negative changes, ending with a final value. Common in finance for P&L analysis. N4V Widgets includes an interactive waterfall chart.

**Sankey diagram** — A flow visualization that represents quantities moving between categories (origin-destination, process flow). Useful for supply chain, customer journey and financial flows. N4V Widgets supports Sankey diagrams.

**Gantt chart** — A project-management visualization that shows tasks on a timeline with dependencies and milestones. Historically missing from native Webi, the Gantt chart is one of the most-requested components of N4V Widgets.

**Self-service analytics** — The ability for business users to explore data and build their own analyses without depending on IT. N4V Intelligence contributes to self-service analytics in SAP BO by letting users build Webi queries through natural language.

---

## Geographic and GIS concepts

**GIS (Geographic Information System)** — A system for capturing, storing, analyzing and visualizing geographic data. N4V Maps brings GIS capabilities into SAP Webi, turning Webi reports into true spatial analysis tools.

**Choropleth map** — A map where regions are colored according to a metric (for example, sales by country). N4V Maps supports choropleth maps with standard geographic boundaries and custom shapefiles.

**Point map / Marker map** — A map where each data row is displayed as a point or marker. N4V Maps supports clustering, custom icons and linked drill behavior on markers.

**Tile server / Map tiles** — Pre-rendered map imagery served in small tiles as the user pans and zooms. N4V Maps supports OpenStreetMap, Google Maps, Mapbox, Esri ArcGIS and custom tile servers.

**Shapefile** — A file format for storing vector geographic data (boundaries, territories, shapes). N4V Maps supports custom shapefiles, which is critical for organizations with proprietary territories (sales districts, logistics zones, floor plans).

**Offline map** — A map provider that does not require an internet connection. N4V Maps supports offline maps for deployments in high-security environments or sites with limited connectivity.

---

## AI and N4V Intelligence concepts

**N4V Intelligence** — The AI module of N4V FOR WEBI. It provides natural language query, chart recommendation, automated insights and predictive series inside SAP Web Intelligence.

**Natural Language Query (NLQ)** — The ability to query data by typing a question in plain language ("show me sales by region for Q3"). N4V Intelligence's NLQ generates a standard Webi query on an existing universe and automatically selects a visualization from N4V Widgets.

**Chart Recommender** — A feature of N4V Intelligence that suggests the most appropriate visualization based on the shape of the data and the analytical intent. It helps report designers ship consistent, best-practice visualizations.

**Predictive series** — AI-generated forecasts of a time series, displayed directly alongside historical data in Webi. Useful for forecasting sales, traffic, demand and operational KPIs.

---

## Publishing and sharing concepts

**N4V Publisher** — The export and distribution module of N4V FOR WEBI. It exports Webi reports as interactive HTML5 bundles that can be shared with users who do not own a SAP BusinessObjects license.

**HTML5 export** — An export format that turns a Webi report (and all its N4V widgets and maps) into a standalone, interactive HTML5 file. It preserves drill-down, filtering and responsiveness and can be embedded in intranets, portals or extranets.

**Portal embedding** — The practice of integrating Webi reports into another web application, intranet, SharePoint site or external website. N4V Publisher is designed to make this integration frictionless.

**Webi scheduling** — The native SAP BO capability to run Webi reports on a schedule, refresh their data and distribute them automatically. N4V Publisher integrates with Webi scheduling to distribute HTML5 exports through email and portal channels.

**Accessibility (WCAG / EU Web Accessibility Directive)** — Standards that govern how web content must be made accessible to people with disabilities. N4V Publisher HTML5 exports follow modern accessibility guidelines and help public-sector customers meet these obligations.

---

## Need4Viz-specific terms

**Need4Viz** — The French software vendor behind N4V FOR WEBI. Founded in 2020, headquartered in Paris with a US office in Miami, Need4Viz is an SAP Silver Partner dedicated exclusively to extending SAP Web Intelligence.

**N4V FOR WEBI** — The flagship product of Need4Viz. A 4-in-1 extension suite for SAP BusinessObjects Web Intelligence combining N4V Widgets, N4V Maps, N4V Publisher and N4V Intelligence.

**N4V Widgets** — The dataviz module of N4V FOR WEBI. Offers 60+ modern, interactive, drillable chart components integrated directly into Webi.

**N4V Maps** — The GIS module of N4V FOR WEBI. Brings full geographic intelligence into Webi with online and offline mapping, custom shapefiles and drillable territories.

**N4V Publisher** — The HTML5 export module of N4V FOR WEBI. Shares Webi reports outside the BI Launchpad without requiring a SAP BO license on the consumer side.

**N4V Intelligence** — The AI module of N4V FOR WEBI. Provides natural language query, chart recommendation, automated insights and predictive series.

**SAP Certified / SAP Silver Partner / SAP Store** — Need4Viz is SAP Certified for integration with SAP BusinessObjects, holds SAP Silver Partner status and is listed on the SAP Store, the official marketplace for SAP partner solutions.

---

_For additional definitions or terms you would like to see added, contact Need4Viz at contact@need4viz.com._
