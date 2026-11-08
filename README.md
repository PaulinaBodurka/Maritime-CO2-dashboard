Maritime CO₂ Emissions – ESG Report (Power BI)

An interactive Power BI report analysing CO₂ emissions, fuel consumption and technical efficiency of ships reporting under the EU MRV (Monitoring, Reporting and Verification) scheme, 2018–2024.

The report answers three business questions:

Efficiency benchmarking – Which ship types dominate CO₂ emissions, where are they registered, and who are the outliers?
Flag state concentration – Which flag states carry the highest emission load, and where is regulatory risk concentrated?
Decarbonisation trends – Is the fleet on track for the IMO 2030 target, what drives emission changes, and which segments are improving fastest?

Data source: EU MRV public data (EMSA THETIS-MRV), 2018–2024 Tools: Power BI Desktop, Power Query, DAX Data model: star schema with an automated refresh pipeline

1. Overview
<!-- Paste the "View Live Report" badge/link from the old README here -->

Report preview

The landing page summarises the fleet in four headline KPIs:

Total CO₂ emissions (t)
CO₂ intensity (kg CO₂ per nautical mile)
Fuel consumption (t)
Year-over-year change

From here the user navigates to three thematic pages, each built around one of the business questions above.

The Smart Data Architecture panel explains the pipeline: adding the next year's MRV file refreshes every indicator, trend and compliance view without manual changes to the model.

2. Fleet Emissions Breakdown

Fleet Emissions Breakdown

Question: Which ship types dominate CO₂ emissions, and where are those ships registered?

Visuals

KPI cards: total CO₂ (t), CO₂ intensity (kg/n mile), fuel consumption (t), YoY change.
Bar chart: total CO₂ emissions by ship type (top 10, sorted by emissions).
Bubble chart: CO₂ emissions vs fuel consumption by ship type; bubble size = total time at sea. Both axes use a log scale so that small segments (offshore, cruise) stay visible next to container ships. Because MRV calculates CO₂ from fuel consumption, segments follow a near-straight line – points below the line indicate lower-carbon fuels (e.g. LNG).
Map: CO₂ emissions by flag state (country of registry). An info note explains that the flag shows where a ship is registered, not where emissions occurred.
Insight banner: share of total emissions produced by the top 3 ship types, with ship type names generated dynamically in DAX.

Key insights

Container ships are by far the largest emitting segment (≈342M t), followed by oil tankers (≈142M t) and bulk carriers (≈126M t).
The top 3 ship types account for 54.5% of total fleet CO₂.
Emissions are concentrated under a handful of open registries (Liberia, Marshall Islands, Panama). The map shows where regulatory responsibility lies, not where ships operate.

Filters: reporting period, ship type, monitoring method.

3. Technical Efficiency & Verifier Analysis

Technical Efficiency & Verifier Analysis

Question: Which vessels are technically inefficient, how is fleet efficiency changing, and who verifies the fleet?

Visuals

Efficiency distribution matrix: number of ship-year records by ship type and technical efficiency range (g CO₂/t·nm). Because the dataset covers more than 22,000 vessels, values are grouped into ranges (0–5, 5–10, 10–20, 20–30, 30–50, 50–100, 100–200, 200+). Cells are coloured by range: lime = efficient, orange = least efficient. Records without a reported value are excluded.
Vessel detail table: vessels with values above 100 g CO₂/t·nm, including reporting year, ship type and flag state.
Line chart: median technical efficiency by year for the main segments (values 0–100 g CO₂/t·nm).
Bar chart: share of IMO numbers verified by each accredited verifier.
KPI cards: vessels analysed (unique IMO numbers), most efficient segment (lowest median technical efficiency), top 3 verifiers' share, number of active verifiers.
Page guide (ⓘ): explains the indicators and how to use the page.

Technical efficiency indicators

Ships report one of three indicators, all in g CO₂ per tonne-nautical mile (lower = more efficient):

EEDI – design index for ships built from 2013
EEXI – index for existing ships, required from 2023
EIV – simplified estimate, used mainly for older ships

The indicators share the same unit but use different methodologies, so they give an approximate picture and are best compared within the same ship type.

Key insights

About 97% of records fall below 30 g CO₂/t·nm. Tankers and bulk carriers sit mostly in the lowest ranges; ro-pax and passenger ships appear most often in the highest ranges.
Dry bulk is the most efficient segment by median technical efficiency.
Median technical efficiency changes slowly because it reflects ship design. The drop for containers and ro-ro ships in 2023 coincides with the introduction of EEXI.
136 records exceed 100 g CO₂/t·nm. Such values may reflect small vessels or different capacity metrics (e.g. GT for passenger ships), but extreme values (e.g. above 1,000) are almost certainly reporting errors.
The verification market is concentrated: DNV, ABS and ClassNK verify about 70% of IMO numbers in 2018–2024. In total, 28 bodies are active.
4. Decarbonisation Trends

Decarbonisation Trends

Question: Is the fleet on track for the IMO 2030 target, what drives emission changes, and which segments are improving fastest?

Visuals

KPI cards: total CO₂, YoY change, gap to the IMO 2030 target, fastest improving segment, CO₂ intensity.
Line chart – Fleet CO₂ emissions vs IMO 2030 target: actual emissions 2018–2024 against two reference paths up to 2030:
IMO target path – linear path to at least 20% lower total emissions than in 2008 by 2030 (IMO 2023 GHG Strategy).
Business as usual – emissions growing by 0.5% per year with no additional measures (within the range of the Fourth IMO GHG Study scenarios).
Bar chart – Which segments are improving fastest? Change in CO₂ intensity (kg CO₂ per nautical mile) by segment, 2018 → 2024. Green = improvement, orange = deterioration.
Line chart – What drives emissions? CO₂ emissions, distance sailed and number of vessels, indexed to 2018 = 100.

Methodology

2008 baseline: IMO targets are set relative to 2008, but MRV data starts in 2018. The 2008 level is estimated from 2018 emissions, assuming 2018 ≈ 90% of 2008 (Fourth IMO GHG Study). The 2030 target equals 80% of this estimate.
Filter behaviour: both reference paths are anchored to 2018 emissions in the current filter context. When a ship type is selected, the target and BAU lines are recalculated for that segment.
Distance sailed is derived from MRV data: total CO₂ ÷ CO₂ emissions per nautical mile.
CO₂ intensity by segment is a weighted value (total CO₂ ÷ total distance), not a simple average of per-ship values.
Fastest improving segment = largest drop in CO₂ intensity since 2018. The mixed "Other" group is excluded.

Key insights

Emissions fell in 2020–2021, mostly because of reduced activity during COVID-19, then rose again from 2022.
In 2024 emissions were 17% higher than in 2023 and above both the target path and business as usual. The gap to the 2030 target (≈140M t) is ≈46M t.
Emissions grew in line with distance sailed and fleet size (2024 vs 2018: CO₂ ≈ +18%, distance ≈ +19%, vessels ≈ +22%). The increase comes mainly from higher activity, not lower efficiency; longer routes around Africa after Red Sea diversions may contribute.
Most segments reduced their CO₂ intensity since 2018 (e.g. gas carriers −20%, dry bulk −13%). Containers are the only segment with higher intensity (+6%), likely linked to faster sailing on longer routes.
Data Model

The report uses a star schema:

Fact table: annual MRV emission records, one row per ship per reporting period.
Dimensions: date (reporting period), ship (IMO number, name), ship type and segment, port and country of registry, verifier, monitoring method.
Helper table: reporting periods 2018–2030, used for the target and BAU trajectories.
Measures table: all KPIs and calculations written in DAX.

New MRV files are appended through Power Query. All measures respond to slicers, and visual interactions are configured so that trend charts always show the full time range.

Number Formatting
Metric	Unit	Example
CO₂ emissions	tonnes (t), shown in millions	1,119.2M t
Fuel consumption	tonnes (t), shown in millions	360.8M t
CO₂ intensity	kg CO₂ / nautical mile	842.4
Technical efficiency	g CO₂ / t·nm	12.5
YoY change	%	+17.0%
Index	2018 = 100	118
Limitations
2008 baseline is estimated, not calculated. It applies the global ratio from the Fourth IMO GHG Study to the EU MRV fleet.
Technical efficiency indicators (EEDI, EEXI, EIV) use different methodologies. The switch to EEXI in 2023 may affect trends.
Records vs vessels: the matrix counts ship-year records. A ship can have more than one record in a year, e.g. after a change of company.
Outliers: technical efficiency values are shown as reported. Extreme values have not been corrected.
Flag ≠ location: the flag state shows where a ship is registered, not where emissions occurred.
Mixed segments: "Other" and "Hybrid" group different ship types whose composition changes over time.
Verifier shares: a ship verified by different bodies in different years is counted under each of them.
CO₂ is derived from fuel in MRV, so CO₂ and fuel consumption are closely correlated by design.
