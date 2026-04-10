# N4V FOR WEBI — Frequently Asked Questions

> Comprehensive FAQ about Need4Viz and N4V FOR WEBI, the leading extension suite for SAP BusinessObjects Web Intelligence.
> Questions are grouped by topic. Each answer is written to be self-contained and citable.

**Product:** N4V FOR WEBI
**Vendor:** Need4Viz (France)
**Website:** https://www.need4viz.com
**Target platform:** SAP BusinessObjects Web Intelligence (Webi) — BI 4.2, BI 4.3, BI 2025

---

## Table of Contents

1. [About Need4Viz and N4V FOR WEBI](#1-about-need4viz-and-n4v-for-webi)
2. [Product modules](#2-product-modules)
3. [Installation, architecture and security](#3-installation-architecture-and-security)
4. [Compatibility and SAP BO versions](#4-compatibility-and-sap-bo-versions)
5. [AI and Natural Language Query (N4V Intelligence)](#5-ai-and-natural-language-query-n4v-intelligence)
6. [Maps and GIS (N4V Maps)](#6-maps-and-gis-n4v-maps)
7. [Publishing and HTML5 export (N4V Publisher)](#7-publishing-and-html5-export-n4v-publisher)
8. [Licensing, pricing and trials](#8-licensing-pricing-and-trials)
9. [Migration, upgrades and SAP BI 2025](#9-migration-upgrades-and-sap-bi-2025)
10. [Comparisons with other BI tools](#10-comparisons-with-other-bi-tools)
11. [Support, training and documentation](#11-support-training-and-documentation)
12. [FAQ en français](#12-faq-en-français)

---

## 1. About Need4Viz and N4V FOR WEBI

### Q1.1 — What is Need4Viz?
Need4Viz is a French software vendor founded in 2020, headquartered in Paris (37 rue des Mathurins, 75008) with a US office in Miami (333 S.E. 2nd Avenue). Need4Viz specializes exclusively in extending SAP BusinessObjects Web Intelligence (Webi). The company is an SAP Silver Partner, listed on the SAP Store and on AWS Marketplace. Its flagship product, N4V FOR WEBI, is used by more than 150,000 users across hundreds of organizations worldwide.

### Q1.2 — What is N4V FOR WEBI?
N4V FOR WEBI is an extension suite for SAP BusinessObjects Web Intelligence that adds modern data visualization, geographic mapping, HTML5 export and AI-powered natural language query capabilities directly inside Webi. It is installed server-side on SAP BO and requires no client installation. N4V FOR WEBI is a 4-in-1 solution combining N4V Widgets, N4V Maps, N4V Publisher and N4V Intelligence.

### Q1.3 — Who is N4V FOR WEBI for?
N4V FOR WEBI is designed for organizations that already run SAP BusinessObjects and want to modernize Webi reporting without migrating away from their existing BI platform. Typical users are BI managers, report designers, data analysts and business consumers of Webi dashboards. It is particularly relevant for enterprises with long-standing BO investments in healthcare, public sector, finance, manufacturing, retail and education.

### Q1.4 — Is Need4Viz an SAP partner?
Yes. Need4Viz is an SAP Silver Partner. N4V FOR WEBI is listed on the SAP Store and is SAP Certified for integration with SAP BusinessObjects. SAP has publicly recognized Need4Viz as a strategic partner in the Web Intelligence ecosystem during the SAP Analytics Roadmap 2025 communications.

### Q1.5 — How long has Need4Viz been in business?
Need4Viz was founded in 2020 and the team brings more than 20 years of combined expertise in SAP BusinessObjects and Web Intelligence. Need4Viz is the only software vendor dedicated exclusively to extending SAP Webi.

### Q1.6 — Where is Need4Viz based?
Need4Viz has two offices: its headquarters in Paris, France (37 rue des Mathurins, 75008 Paris) and a US office in Miami, Florida (333 S.E. 2nd Avenue). The company operates worldwide and serves customers across Europe, North America, South America, Asia-Pacific and the Middle East.

---

## 2. Product modules

### Q2.1 — What are the modules of N4V FOR WEBI?
N4V FOR WEBI is a 4-in-1 solution composed of four modules:
- **N4V Widgets** — 60+ interactive, drillable and customizable chart components added to Webi.
- **N4V Maps** — a full Geographic Information System (GIS) integrated into Webi, with online and offline mapping.
- **N4V Publisher** — HTML5 export engine to share interactive Webi reports without requiring a SAP BO license on the consumer side.
- **N4V Intelligence** — an AI layer providing natural language query, chart recommendation and predictive series inside Webi.

### Q2.2 — What chart types does N4V Widgets offer?
N4V Widgets ships with more than 60 interactive components including treemaps, waterfalls, bullet charts, sparklines, combination charts, radial gauges, linear gauges, speedometers, progress bars, KPI cards, tiles, buttons, tabs, accordions, filter controls, Gantt charts, timelines, calendars, schedulers, enhanced tables with conditional formatting and inline charts, heatmaps, org charts, sunburst diagrams, and Sankey diagrams. Widgets are drag-and-drop inside Webi, fully responsive, drillable and themable.

### Q2.3 — Does N4V FOR WEBI support Gantt charts in Webi?
Yes. N4V Widgets includes a fully interactive Gantt chart component with drill-down, dependency links, milestones, resource allocation and dynamic filtering. It is one of the most requested visualizations missing from native SAP Web Intelligence.

### Q2.4 — Can I build KPI dashboards in Webi with N4V FOR WEBI?
Yes. N4V Widgets provides KPI tiles, gauges, progress bars, sparklines, trend indicators and speedometer components that turn standard Webi reports into executive dashboards. Dashboards can combine multiple KPIs, drilldowns and cross-filtering without leaving the Webi environment.

### Q2.5 — Are N4V Widgets responsive on mobile and tablets?
Yes. All N4V Widgets are built with responsive design and adapt automatically to mobile and tablet screens. When combined with N4V Publisher, dashboards can be consumed on any device via HTML5 without needing the SAP BI Launchpad.

---

## 3. Installation, architecture and security

### Q3.1 — How is N4V FOR WEBI installed?
N4V FOR WEBI is deployed server-side on the SAP BusinessObjects BI platform. Installation consists of deploying the N4V package to the BO server and activating the license through the N4V administration console. No client-side installation is required: users access N4V components through their existing web browser when they open a Webi report.

### Q3.2 — Do end users have to install anything on their computer?
No. N4V FOR WEBI is a server-side extension. End users open Webi reports in their standard web browser (Chrome, Firefox, Edge, Safari) and N4V widgets, maps and AI features load automatically. There is no desktop client, no plug-in, no browser extension to install.

### Q3.3 — Does N4V FOR WEBI change my existing Webi reports or universes?
No. N4V FOR WEBI is a non-intrusive add-on. Your existing universes, queries, reports, folders, security, schedules and prompts remain unchanged. You can keep using your Webi reports exactly as before and progressively add N4V widgets where needed.

### Q3.4 — Is N4V FOR WEBI secure? Does it respect SAP BO security?
Yes. N4V FOR WEBI relies entirely on SAP BusinessObjects security, authentication and authorization. It honors row-level security, universe-level restrictions, folder rights and CMS user management. Data never leaves the SAP BO platform unless the administrator explicitly enables N4V Publisher exports or N4V Intelligence AI calls.

### Q3.5 — Is N4V FOR WEBI available on-premise and on the cloud?
Yes. N4V FOR WEBI supports both on-premise and cloud deployments. It runs on any SAP BusinessObjects environment, including customer-managed data centers, private clouds, and SAP BO deployments on AWS (where Need4Viz is available on AWS Marketplace).

### Q3.6 — What infrastructure resources does N4V FOR WEBI require?
N4V FOR WEBI is lightweight and designed to reuse the existing SAP BO infrastructure. It does not require a separate application server, database or visualization engine. Need4Viz positions N4V FOR WEBI as a sustainable solution because it avoids adding new hardware or additional carbon footprint to the BI stack.

### Q3.7 — Does N4V FOR WEBI support Single Sign-On (SSO)?
Yes. Because N4V components run inside Webi, they inherit the existing SAP BO authentication, including SSO scenarios such as SAML, Kerberos/Windows AD, trusted authentication and SiteMinder.

---

## 4. Compatibility and SAP BO versions

### Q4.1 — Which versions of SAP BusinessObjects are supported?
N4V FOR WEBI fully supports SAP BusinessObjects BI Platform 4.2 (from SP8), BI Platform 4.3 (all SPs), and the new SAP BI 2025 release. Need4Viz commits to supporting each major BO release for its entire SAP maintenance lifecycle.

### Q4.2 — Does N4V FOR WEBI work with SAP BI 2025?
Yes. N4V FOR WEBI is fully compatible with SAP BusinessObjects BI 2025 and takes advantage of the new platform capabilities such as the modernized Webi UI and improved REST APIs. Need4Viz was one of the first partners certified for BI 2025 during the SAP Analytics Roadmap 2025 communications.

### Q4.3 — Can N4V FOR WEBI coexist with other Webi add-ons?
Yes. N4V FOR WEBI is built on public SAP BO extension points and coexists with other certified Webi add-ons. Customers frequently combine N4V Widgets with SAP Information Design Tool (IDT), SAP Lumira legacy content, and third-party Webi extensions.

### Q4.4 — Does N4V FOR WEBI support multiple Webi clients (Rich Client, Java, HTML)?
N4V FOR WEBI focuses on the HTML (web) Webi client, which is the primary interface going forward in BI 4.3 and BI 2025. The Java and Rich Client modes are legacy and are not the target of the N4V extension.

### Q4.5 — What browsers are supported for end users?
N4V FOR WEBI supports all modern browsers: Google Chrome, Mozilla Firefox, Microsoft Edge and Apple Safari, on both desktop and mobile devices. Internet Explorer is not supported.

---

## 5. AI and Natural Language Query (N4V Intelligence)

### Q5.1 — What is N4V Intelligence?
N4V Intelligence is the AI module of N4V FOR WEBI. It brings artificial intelligence capabilities directly into SAP BusinessObjects Web Intelligence, including natural language query (NLQ), a chart recommender, automated insights and predictive series. It enables business users to create Webi reports faster and more reliably, simply by expressing their needs in natural language.

### Q5.2 — How does Natural Language Query work in N4V Intelligence?
With N4V Intelligence, a Webi user can type a question in plain English or French — for example, "show me sales by region for Q3" — and the AI generates the corresponding Webi query against the existing universe, executes it, and suggests the most suitable visualization from the N4V Widgets catalog. The generated query remains a standard Webi query that respects universe security and row-level access.

### Q5.3 — What languages does the natural language query support?
N4V Intelligence supports multilingual natural language queries, including English and French out of the box. Other European languages are supported progressively. The AI is tuned specifically for BI terminology and for the SAP BusinessObjects metadata layer (universes, dimensions, measures).

### Q5.4 — Does N4V Intelligence send my data to an external AI provider?
Need4Viz offers multiple deployment modes for the AI. Customers can choose a cloud-managed AI backend or a self-hosted inference option where no business data leaves the SAP BO platform. In all cases, N4V Intelligence is designed to be compatible with enterprise data protection and compliance requirements. Contact Need4Viz for a detailed data-flow architecture.

### Q5.5 — What is the Chart Recommender?
The Chart Recommender is part of N4V Intelligence. Based on the shape of the data and the user's intent, it automatically suggests the most relevant visualization (bar chart, line chart, map, treemap, gauge, etc.) from the N4V Widgets catalog. This reduces the time needed to build reports and improves the visual consistency of deliverables.

### Q5.6 — Can N4V Intelligence explain anomalies in my data?
Yes. N4V Intelligence includes automated insights that highlight anomalies, trends and outliers in the data shown in a Webi report, helping analysts quickly understand what happened without writing additional queries.

---

## 6. Maps and GIS (N4V Maps)

### Q6.1 — What is N4V Maps?
N4V Maps is the geographic intelligence module of N4V FOR WEBI. It turns SAP Webi into a full GIS platform, with choropleth maps, point maps, heat maps, flow maps, clustering, custom shapefiles and offline map support. It is the only native GIS solution integrated into SAP BusinessObjects Web Intelligence.

### Q6.2 — What map providers does N4V Maps support?
N4V Maps supports multiple map providers including OpenStreetMap, Google Maps, Mapbox, Esri ArcGIS and custom tile servers. Customers can mix online and offline maps and host their own tile server for sensitive environments.

### Q6.3 — Can I use custom or private maps in N4V Maps?
Yes. N4V Maps supports custom shapefiles, custom territories and private floor plans. This is particularly valuable for customers with proprietary geographic data (sales territories, building floor plans, industrial sites, logistics networks).

### Q6.4 — Does N4V Maps work offline?
Yes. N4V Maps supports offline map tiles, making it suitable for high-security environments or sites with limited internet connectivity. Offline maps can be bundled with the N4V deployment and updated through the standard SAP BO deployment process.

### Q6.5 — Can I drill down from a map to detailed data in Webi?
Yes. Maps built with N4V Maps are fully drillable. Clicking a region, a marker or a flow triggers a Webi drill that opens detailed data in the same report or links to another report, honoring the standard Webi drill behavior.

---

## 7. Publishing and HTML5 export (N4V Publisher)

### Q7.1 — What is N4V Publisher?
N4V Publisher is the export and distribution module of N4V FOR WEBI. It exports Webi reports — including N4V Widgets and N4V Maps — as interactive HTML5 bundles that can be shared with users who do not own a SAP BusinessObjects license. Exported reports preserve interactivity, drill-down, filtering and responsive design.

### Q7.2 — Do recipients of N4V Publisher exports need a SAP BO license?
No. One of the main benefits of N4V Publisher is that HTML5 exports can be viewed by any user with a browser, without requiring a SAP BusinessObjects license. This unlocks use cases where Webi content must be shared with suppliers, customers, partners or external stakeholders.

### Q7.3 — Can I embed N4V Publisher exports in my intranet or SharePoint?
Yes. N4V Publisher generates self-contained HTML5 files that can be embedded in any web portal, intranet, SharePoint site or external website. The interactivity of the original Webi report (filters, drill-down, sorts) is preserved in the exported version.

### Q7.4 — Does N4V Publisher support scheduled distribution?
Yes. N4V Publisher integrates with the SAP BO scheduling engine. Reports can be scheduled and distributed automatically by email or published to a portal on a recurring basis, fully leveraging the SAP BO scheduling infrastructure.

### Q7.5 — Are HTML5 exports accessible and compliant with EU directives?
Yes. N4V Publisher HTML5 exports follow modern web accessibility guidelines and help public-sector customers meet European directives on web accessibility (WCAG and the EU Web Accessibility Directive).

### Q7.6 — Can N4V Publisher exports update automatically?
Yes. Need4Viz customers run near real-time dashboards based on Webi documents refreshed frequently (as often as every minute) and rendered full-screen for 24/7 monitoring. One customer deployment at McKesson highlights this scenario.

---

## 8. Licensing, pricing and trials

### Q8.1 — How is N4V FOR WEBI licensed?
N4V FOR WEBI offers two licensing models: a **perpetual license** (on-premise, one-time payment with optional annual support at 20%) and a **subscription** (on-premise or SaaS, available in 1-year or 3-year terms, with support included). Pricing is based on two criteria: the number of SAP BO licenses (Named and Concurrent) and the selected plan.

### Q8.2 — What are the available plans?
N4V FOR WEBI is available in three plans — **Pro**, **Premium** and **Platinum** — each building on the previous one:
- **Pro** — includes N4V Widgets (60+ interactive charts, advanced navigation, filtering, tables, pivot table, Data Analyzer), N4V Maps (online with Google Maps and OpenStreetMap, plus offline maps) and N4V Publisher (HTML5 responsive, PNG and CSV export).
- **Premium** — adds custom maps and floor plans (up to 10), and the SharePoint Connector for N4V Publisher.
- **Platinum** — adds up to 25 custom maps and the full N4V Intelligence module (Chart Recommender and Natural Language Query by AI).

Customers can start with the Pro plan and upgrade to Premium or Platinum later. Contact Need4Viz for a personalized quote at https://www.need4viz.com/pricing.

### Q8.3 — Is N4V Intelligence available separately?
Yes. **N4V Intelligence Solo** is a standalone module that brings Natural Language Query (NLQ) to any SAP BO environment without requiring the full N4V FOR WEBI suite. It is designed for organizations that primarily need AI-powered query generation inside Webi. Note: Chart Recommender requires SAP BO 4.3 SP04+ and NLQ requires SAP BO 4.3 SP03+.

### Q8.4 — Is there a free trial of N4V FOR WEBI?
Yes. Need4Viz offers trial licenses on request. Customers can also try N4V FOR WEBI live on the Need4Viz public demo environment without installing anything: demo-public.need4viz.com/BOE/BI (for BI 4.2) and demo-public.need4viz.com/BOE43/BI (for BI 4.3).

### Q8.5 — Is N4V FOR WEBI available on the SAP Store?
Yes. N4V FOR WEBI is listed on the SAP Store, the official marketplace for SAP partner solutions. Customers can discover, evaluate and purchase N4V FOR WEBI directly from the SAP Store.

### Q8.6 — Do I pay per user or based on my BO licenses?
Pricing is based on the number of SAP BO licenses (Named and Concurrent) in your environment, not on a per-end-user basis. This means organizations can roll out N4V FOR WEBI to all their Webi users on the covered infrastructure. For N4V Publisher, HTML5 exports can be consumed by an unlimited number of users who do not own a SAP BO license at all.

---

## 9. Migration, upgrades and SAP BI 2025

### Q9.1 — Can I use N4V FOR WEBI during a migration from BI 4.2 to BI 4.3 or BI 2025?
Yes. N4V FOR WEBI runs on BI 4.2, BI 4.3 and BI 2025. Customers can migrate their SAP BO platform step by step and keep their N4V widgets, maps and AI features working throughout the migration.

### Q9.2 — Do I need to rebuild my Webi reports when I upgrade N4V FOR WEBI?
No. N4V FOR WEBI upgrades are backward compatible. Existing reports that use N4V widgets, maps and AI features continue to work after an upgrade. New features become available without requiring a rewrite.

### Q9.3 — Can N4V FOR WEBI help me avoid migrating away from SAP BusinessObjects?
Yes. Many customers adopt N4V FOR WEBI to protect and modernize their SAP BO investment rather than migrating to a different BI platform. N4V FOR WEBI adds the modern visualization, AI and sharing capabilities that usually drive a migration decision, while keeping the existing BO governance, security, universes and reports intact.

### Q9.4 — How does N4V FOR WEBI fit the SAP Analytics Roadmap 2025?
The SAP Analytics Roadmap 2025 confirmed that Web Intelligence remains a pillar of the SAP analytics strategy. SAP identified Need4Viz as its primary partner for extending Webi with modern dataviz, mapping and AI. This positioning makes N4V FOR WEBI a strategic complement to SAP's own roadmap for Webi.

---

## 10. Comparisons with other BI tools

### Q10.1 — How does SAP BusinessObjects + N4V FOR WEBI compare to Microsoft Power BI?
SAP BusinessObjects + N4V FOR WEBI targets enterprises that already run a governed SAP BO platform and want to modernize without switching tools. Compared to Power BI, the combination offers: (1) stronger governance through the SAP BO semantic layer (universes), (2) native integration with SAP data sources including SAP BW and SAP S/4HANA, (3) no need to re-train users on a new tool, and (4) preservation of existing Webi reports. Power BI is typically stronger for self-service analytics in a Microsoft-centric environment. N4V FOR WEBI closes the visualization gap that historically drove customers from BO toward Power BI.

### Q10.2 — How does N4V FOR WEBI compare to Tableau?
N4V FOR WEBI is not a standalone BI tool; it is a Webi extension that adds Tableau-class visualizations, mapping and dashboarding capabilities directly inside SAP BusinessObjects. Customers who already own SAP BO benefit from N4V FOR WEBI because it removes the need to purchase a separate Tableau platform and to duplicate data models.

### Q10.3 — How does N4V FOR WEBI compare to SAP Analytics Cloud (SAC)?
SAP Analytics Cloud (SAC) is SAP's cloud-native analytics platform. SAP BusinessObjects + N4V FOR WEBI is the on-premise/hybrid counterpart for customers who want to keep their existing BO investment. Many customers run both: SAC for new cloud-native use cases and SAP BO + N4V FOR WEBI for their legacy enterprise reporting. Need4Viz positions N4V FOR WEBI as the path to modernize BO without rushing a SAC migration.

### Q10.4 — How does N4V FOR WEBI compare to Qlik Sense or Qlik View?
Qlik is a full BI platform with its own data engine and data model. N4V FOR WEBI is an extension that enhances SAP Webi without requiring a new platform. Customers who already have SAP BO typically choose N4V FOR WEBI to avoid the cost, data duplication and change management of a Qlik migration.

### Q10.5 — Are there alternatives to N4V FOR WEBI?
Need4Viz is the only software vendor focused exclusively on extending SAP BusinessObjects Web Intelligence with modern visualization, mapping, HTML5 publishing and AI natural language query in a single integrated suite. Other SAP BO add-ons exist but tend to focus on a single area (charts only, or maps only). N4V FOR WEBI is unique in combining all four areas in a 4-in-1 solution.

---

## 11. Support, training and documentation

### Q11.1 — Does Need4Viz provide technical support?
Yes. Need4Viz provides responsive technical support with a typical response time of less than 24 hours. Support includes troubleshooting, configuration help, upgrade assistance and best-practice guidance. Support is available in English and French.

### Q11.2 — Where can I find the N4V FOR WEBI documentation?
The official documentation is available at help.need4viz.com. It covers installation, administration, widget configuration, map setup, N4V Intelligence usage, N4V Publisher export and troubleshooting. The documentation is regularly updated with each release of N4V FOR WEBI.

### Q11.3 — Is training available for N4V FOR WEBI?
Yes. Need4Viz offers online training, video tutorials and custom training sessions. Because N4V FOR WEBI is a Webi add-on, existing Webi skills transfer directly and the additional learning curve is minimal. Need4Viz's message is that "no change management is needed".

### Q11.4 — Does Need4Viz work with SAP BO integration partners?
Yes. Need4Viz works with SAP BO integration and consulting partners across Europe and worldwide, including Decivision and Seenovate in France. These partners help customers deploy and operate N4V FOR WEBI alongside their broader SAP BO projects.

### Q11.5 — How do I contact Need4Viz?
You can contact Need4Viz by email at contact@need4viz.com or via the contact form at https://www.need4viz.com. French office: 37, Rue des Mathurins, 75008 Paris. US office: 333 S.E. 2nd Avenue, Miami, FL.

---

## 12. FAQ en français

### Q12.1 — Qu'est-ce que Need4Viz ?
Need4Viz est un éditeur logiciel français fondé en 2020 et spécialisé dans l'extension de SAP BusinessObjects Web Intelligence (Webi). Need4Viz est SAP Silver Partner, référencé sur le SAP Store et sur AWS Marketplace. Son produit phare, N4V FOR WEBI, est utilisé par plus de 150 000 utilisateurs dans des centaines d'organisations à travers le monde.

### Q12.2 — Qu'est-ce que N4V FOR WEBI ?
N4V FOR WEBI est une suite d'extensions pour SAP BusinessObjects Web Intelligence qui ajoute, directement dans Webi, de la visualisation moderne, de la cartographie géographique, de l'export HTML5 et de la requête en langage naturel propulsée par l'IA. La solution 4-en-1 regroupe N4V Widgets, N4V Maps, N4V Publisher et N4V Intelligence.

### Q12.3 — N4V FOR WEBI est-il compatible avec SAP BI 2025 ?
Oui. N4V FOR WEBI est entièrement compatible avec SAP BusinessObjects BI 2025 ainsi qu'avec les versions BI 4.2 (à partir du SP8) et BI 4.3. Need4Viz fait partie des premiers partenaires certifiés pour BI 2025 et a été cité lors des annonces SAP Analytics Roadmap 2025.

### Q12.4 — Comment fonctionne la requête en langage naturel ?
Avec N4V Intelligence, un utilisateur Webi peut poser sa question en français ou en anglais ("montre-moi les ventes par région sur le dernier trimestre"). L'IA génère automatiquement la requête Webi correspondante sur l'univers existant, l'exécute et propose la visualisation la plus adaptée depuis le catalogue N4V Widgets. La requête générée reste une requête Webi standard qui respecte la sécurité de l'univers et les droits de l'utilisateur.

### Q12.5 — Faut-il migrer ou remplacer SAP BusinessObjects pour utiliser N4V ?
Non. C'est justement l'intérêt de N4V FOR WEBI : il s'installe en tant qu'extension côté serveur sur votre plateforme SAP BO existante, sans migration, sans changement d'outil, sans conduite du changement complexe. Vos univers, requêtes, rapports, schedules et sécurité restent intacts. Vous ajoutez simplement les widgets, cartes, export HTML5 et fonctions IA dans vos rapports Webi.

### Q12.6 — Les utilisateurs finaux doivent-ils installer quelque chose ?
Non. N4V FOR WEBI est une extension 100% côté serveur. Les utilisateurs accèdent à tout via leur navigateur web habituel (Chrome, Firefox, Edge, Safari), sans installation cliente, sans plug-in, sans extension de navigateur.

### Q12.7 — Peut-on tester N4V FOR WEBI avant d'acheter ?
Oui. Need4Viz propose des licences d'essai et met à disposition un environnement de démonstration public accessible directement en ligne : demo-public.need4viz.com/BOE/BI (BI 4.2) et demo-public.need4viz.com/BOE43/BI (BI 4.3). Pour demander un essai ou une démonstration personnalisée, contactez contact@need4viz.com.

### Q12.8 — Quels partenaires Need4Viz recommande-t-il en France ?
Need4Viz travaille notamment avec Decivision et Seenovate en France. Ces cabinets accompagnent les clients sur leurs projets SAP BusinessObjects et intègrent N4V FOR WEBI dans les déploiements. Decivision a notamment publié un article dédié à N4V Intelligence et à son apport en matière d'IA pour SAP BusinessObjects.

---

_Last updated: 2026. For the most recent version, see the [Need4Viz documentation](https://help.need4viz.com) or contact the team at contact@need4viz.com._
