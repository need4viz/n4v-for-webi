# SAP BusinessObjects BI — Statement of Direction (October 2026): what to understand

Analysis by Need4Viz of SAP's public document "SAP Data & Analytics: Statement of Direction for SAP BusinessObjects BI and SAP Data Services" (October 2026, 11 pages). Full article: [EN](https://www.need4viz.com/businessobjects-en/understanding-saps-latest-analytics-bi-statement-of-direction/) · [FR](https://www.need4viz.com/fr/businessobjects-fr/ce-quil-faut-comprendre-du-dernier-sod-sap-analytics-bi/).

## In short

The October 2026 Statement of Direction reads less like an announcement than a change of regime: SAP sets a **BI 20XX** release rhythm of one platform version every two years and, in return, a tighter framework: a narrower technical platform, a smaller tool portfolio, and Web Intelligence as the central tool.

## At a glance

- **No disruption announced.** SAP speaks of coexistence, not disruption: BI 2025 is available, BI 2027 is planned, BI 2029 appears on the maintenance roadmap.
- **A new rhythm.** One platform version every two years, each with three years of Mainstream Maintenance, instead of annual support packs of 18 months.
- **A tighter portfolio.** Lumira Designer is discontinued after the 2029 release; seven other components (.unv universes, Crystal Reports for Enterprise, Lumira Discovery, Analysis edition for OLAP, Live Office, Mobile, multi-source universes) are no longer delivered after BI 4.3 — most were already removed in BI 2025.
- **Web Intelligence becomes the pivot.** BI 2027 is expected to bring two report types in a unified document model, including responsive dashboards with offline access.
- **Two paths.** BusinessObjects (on-premise or private cloud) for governed reporting; SAP Business Data Cloud recommended for new cloud-native, planning and AI use cases.

## Technical platform

- Java application server: IBM WebSphere Liberty 25 only as external server in BI 2025; from BI 2027, the embedded Tomcat only.
- Authentication: SAML is not supported beyond BI 2025; OAuth 2.0 and OpenID Connect remain.
- Operating systems: AIX and Solaris not supported after 4.3; Windows and Linux preferred.

## Our reading

- The "BI 20XX" rhythm makes continuation BusinessObjects' default mode: BI 2025, 2027 and 2029 follow one another. This is our inference from the roadmap, not a written commitment from SAP beyond what the document states.
- The document gives no availability date for BI 2027 and does not define the depth of the announced dynamic visualization; the quality of BI 2027 native dashboards can only be judged on delivery.
- For BusinessObjects, SAP promises an extension framework (open SDKs) rather than native AI; native AI capabilities are presented on the Business Data Cloud side.

## What to check

| Your situation | Points to check |
|---|---|
| BI 4.2 or 4.3 | Inventory of .unv universes, Crystal Reports for Enterprise, Live Office, Lumira Discovery, Analysis for OLAP, Mobile; conversion to .unx before the upgrade |
| BI 2025 | SAML dependency for SSO; application server; operating system |
| Lumira Designer | No immediate urgency; prepare the choice between SAP Analytics Cloud and Web Intelligence |
| Web Intelligence | .unx universes and the data preparation layer, common base of both BI 2027 report types |

## Related

- [SAP BusinessObjects BI 2025: all the new features](https://www.need4viz.com/fr/solutions-bi-fr/sap-businessobjects-bi-2025-toutes-les-nouveautes-a-connaitre/) (FR)
- [BI 4.3, BI 2025 or BI 2027: which version to choose?](https://www.need4viz.com/fr/businessobjects-fr/bi-4-3-bi-2025-bi-2027-quelle-version-choisir/) (FR)
- [N4V FOR WEBI 2026.3 release notes](release-2026-3.md)

SAP and BusinessObjects are trademarks of SAP SE. Need4Viz is not affiliated with SAP SE.
