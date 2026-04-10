# N4V Intelligence — AI features for SAP BusinessObjects Web Intelligence

**N4V Intelligence** is the AI module of N4V FOR WEBI. It brings modern artificial intelligence capabilities directly into SAP BusinessObjects Web Intelligence (Webi), without requiring a migration to another analytics platform. This document details each AI feature, how it works, the typical use cases and the way it integrates with the rest of N4V FOR WEBI.

---

## What is N4V Intelligence?

N4V Intelligence is one of the four modules of N4V FOR WEBI, alongside N4V Widgets, N4V Maps and N4V Publisher. It adds an AI layer on top of SAP Webi that:

1. Understands user questions in natural language.
2. Generates the corresponding Webi query against the existing universe.
3. Executes the query inside the SAP BO platform, honoring security and row-level access.
4. Selects the most suitable visualization from the N4V Widgets catalog.
5. Forecasts future values when relevant.

The result: a modern conversational analytics experience inside an existing SAP BusinessObjects environment, with no data movement and no new BI tool.

---

## 1. Natural Language Query (NLQ)

### How it works
A Webi user types a question in plain English or French — for example:
- "Show me sales by region for Q3"
- "Compare this year vs last year by product category"
- "Top 10 customers by revenue in Europe"
- "Montre-moi l'évolution du chiffre d'affaires par mois sur les deux dernières années"

N4V Intelligence interprets the question, maps it to the dimensions, measures and filters of the existing universe, generates a standard Webi query and runs it. The result is returned as a regular Webi data provider, displayed with a visualization picked by the Chart Recommender.

### Key properties
- **Universe-aware** — the AI uses the existing SAP BO semantic layer, so business users query through the same governed metadata they already use.
- **Security-aware** — the generated query respects row-level security, universe rights and user-level restrictions.
- **Multilingual** — English and French are supported out of the box, with other European languages supported progressively.
- **Deterministic output** — the generated query can be reviewed, saved and modified like any other Webi query.

### Typical use cases
- Fast ad-hoc analysis without writing SQL or building a Webi query manually.
- Empowering business users who are not Webi query builders.
- Accelerating report creation during workshops and business reviews.
- Building prototypes before formalizing a recurring report.

---

## 2. Chart Recommender

### How it works
Once the data is available (from an NLQ query or from a regular Webi query), the Chart Recommender analyzes the shape of the result set — number of dimensions, number of measures, cardinality, presence of time, hierarchy — and recommends the most suitable visualization from the 60+ widgets of N4V Widgets.

### Examples
- Time series with a single measure → line chart or sparkline
- Part-to-whole with less than 6 categories → donut or pie chart
- Part-to-whole with many categories → treemap
- Two measures with a qualitative dimension → bullet chart (target vs actual)
- Flow between categories → Sankey diagram
- Hierarchical performance → sunburst
- Geographic dimension → map

### Benefits
- Reduces time spent choosing a chart type.
- Improves visual consistency across reports.
- Helps non-expert users follow dataviz best practices.

---

## 3. Predictive series

### How it works
On a time-series visualization, N4V Intelligence can extend the historical data with a predictive forecast. The forecast is computed from the history available in the Webi data provider and rendered alongside the actuals, with a confidence band.

### Typical use cases
- Sales forecasting for short-term planning.
- Traffic and demand forecasting for operational planning.
- Energy consumption forecasting for sustainability reporting.
- Budget and cash-flow projections.

### Properties
- Works with any time-series measure available in the Webi data provider.
- Configurable forecast horizon.
- Integrates naturally with N4V Widgets line and combination charts.

---

## 4. Security, data protection and deployment options

N4V Intelligence is designed to meet enterprise security and compliance expectations.

- **On-premise inference option** — for customers who cannot send data outside their infrastructure, N4V Intelligence can be deployed with an on-premise or customer-managed inference backend.
- **Cloud inference option** — customers who prefer a managed experience can use the cloud-hosted N4V Intelligence service.
- **Row-level security enforcement** — AI-generated queries respect the existing SAP BO row-level security, universe restrictions and user rights. Users never get access to data they could not query via a regular Webi query.
- **Audit-friendly** — the generated queries and the resulting reports are stored as standard Webi documents, visible in the CMC audit trail.

Contact Need4Viz for a detailed data-flow architecture tailored to your compliance requirements.

---

## 5. How N4V Intelligence connects to the other N4V modules

N4V Intelligence is the orchestration layer that ties together the rest of N4V FOR WEBI:

- **N4V Widgets** — the Chart Recommender picks visualizations from the 60+ widgets of N4V Widgets.
- **N4V Maps** — when the question involves a geographic dimension, the Chart Recommender suggests a map built with N4V Maps.
- **N4V Publisher** — AI-driven reports can be exported as interactive HTML5 bundles via N4V Publisher and shared with users who do not own a SAP BO license.

This integrated approach is what makes N4V FOR WEBI a 4-in-1 solution rather than a collection of standalone features.

---

## 6. Why it matters

The usual drivers of a BI platform migration — "we need AI", "we need self-service", "we need natural language" — can now be addressed inside SAP BusinessObjects. Adding N4V Intelligence to an existing SAP BO platform is faster, cheaper and less disruptive than migrating Webi reports to another tool.

This is also the reason why SAP has publicly recognized Need4Viz as a strategic partner for extending Webi with modern visualization, mapping and AI during the SAP Analytics Roadmap 2025 communications.

---

_For a demo of N4V Intelligence against your own universe or a sample dataset, contact Need4Viz at contact@need4viz.com or visit https://www.need4viz.com._
