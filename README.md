Maritime CO₂ Emissions - ESG Report 

An interactive Power BI report analysing CO₂ emissions, fuel consumption and technical efficiency of ships reporting under the EU MRV (Monitoring, Reporting and Verification) scheme, 2018–2024.

The report answers three business questions:

Efficiency benchmarking – Which ship types dominate CO₂ emissions, where are they registered, and who are the outliers?
Flag state concentration – Which flag states carry the highest emission load, and where is regulatory risk concentrated?
Decarbonisation trends – Is the fleet on track for a 2030 reduction target, and which segments are improving fastest?

Data source: DNV MRV database (EU MRV public data) Tools: Power BI Desktop, Power Query, DAX Data model: star schema with an automated refresh pipeline

1. Overview

Show Image

The landing page summarises the fleet in four headline KPIs:

Total CO₂ emissions (Mt)
CO₂ intensity (kg CO₂ per nautical mile)
Fuel consumption (Mt)
Year-over-year change

From here the user navigates to three thematic pages. Each page is built around one of the business questions above.

The Smart Data Architecture panel explains the pipeline. Adding the next year's MRV file automatically refreshes every indicator, trend and compliance view, with no manual changes to the model.

2. Fleet Emissions Breakdown

Show Image

Question: Which ship types dominate CO₂ emissions, and where are those ships registered?

Visuals

KPI cards: total CO₂, CO₂ intensity, fuel consumption, YoY change.
Bar chart: CO₂ emissions by ship type.
Bubble chart: CO₂ emissions vs fuel consumption by ship type, with bubble size showing average time at sea. It uses a log scale so that small segments, such as offshore and cruise, stay visible next to container ships.
Map: CO₂ emissions by flag state (country of registry).
Insight banner: the share of total emissions produced by the top 3 ship types.

Key insights

Container ships are by far the largest emitting segment, followed by bulk carriers and oil tankers.
The top 3 ship types account for more than half of total fleet CO₂.
Emissions are concentrated in a handful of open registries rather than in the ships' operating regions.

Filters: reporting period, ship type, monitoring method.

3. Technical Efficiency & Verifier Analysis

Show Image

Question: Which vessels are technically inefficient, where are they flagged, and who verifies the fleet?

Visuals

Efficiency distribution matrix: number of ship-year records by ship type and technical efficiency band (EEDI / EIV, g CO₂ / t·nm), with heat-map shading.
Vessel detail table: ships in the highest bands (100–200+ g CO₂ / t·nm). These are the least efficient vessels and the likely data-quality outliers.
Donut chart: top 10 flags of registry by total CO₂.
Bar chart: market share of accredited verifiers, as a % of IMO numbers verified.
KPI cards: vessels analysed (unique IMO numbers), most efficient segment, number of active verifiers.

Key insights

Liberia, Panama and the Marshall Islands are the three largest flags by CO₂. Together they carry over 40% of the top-10 emission load.
The verification market is concentrated. DNV verifies about 25% of ships and ABS about 16%. In total, 28 bodies are active.
Most vessels sit in the 2–20 g CO₂ / t·nm range. Values far above 200 point to reporting errors and are flagged for review rather than treated as real performance.

Note: a higher EEDI / EIV value means lower technical efficiency.

4. Decarbonisation Trends

Show Image

Question: Is the fleet on track for its 2030 reduction target?

Visuals

KPI cards: total CO₂, YoY change, gap to the 2030 target, best-performing segment (lowest average CO₂ intensity), and CO₂ intensity.
Line chart: actual CO₂ emissions for 2018–2024 against two reference paths up to 2030:
BAU trajectory – emissions growing at an assumed annual rate with no additional measures.
Target trajectory – a linear reduction path to the 2030 target.

Methodology

Both reference paths are anchored to 2018 actual emissions in the current filter context, since 2018 is the first MRV reporting year. When a ship type or monitoring method is selected, the target and BAU lines are recalculated for that segment, so every segment is compared against its own baseline.
The fleet's CO₂ intensity is calculated as a weighted value (total CO₂ ÷ total distance), not as a simple average of per-ship values.

Key insights

Emissions fell in 2020–2021, mostly because of reduced activity during COVID-19, then rose again from 2022.
In 2024 emissions were about 17% higher than in 2023, which puts the fleet above the target path.
General cargo ships have the lowest average CO₂ intensity of all segments.
Data Model

The report uses a star schema:

Fact table: annual MRV emission reports, one row per ship per reporting year.
Dimensions: date (year), ship (IMO number, name, type), flag state, verifier, monitoring method.

New MRV files are appended through Power Query. All measures are written in DAX and respond to the slicers, so no visual needs editing when new data arrives.

Number Formatting
Metric	Unit	Format
CO₂ emissions	Mt (million tonnes)	1,119.2 Mt
Fuel consumption	Mt	360.8 Mt
CO₂ intensity	kg CO₂ / nautical mile	842.4
Technical efficiency	g CO₂ / t·nm	12.5
YoY change	%	+17.0%
Limitations
MRV data starts in 2018, so no pre-2018 baseline (for example IMO's 2008 reference year) can be computed from this dataset.
Ships that change flag or name during a year can appear more than once at the vessel level.
The technical efficiency values are reported as submitted. Extreme values have not been corrected and are shown as outliers.


[🔗 View interactive dashboard](https://app.powerbi.com/view?r=eyJrIjoiMjFmODRiYjctMjE5OC00ZGVjLTgxMmMtMmExMzUzYzk2YmQyIiwidCI6IjNkZmU5YWI2LTgxYmYtNDkxYy1iNjcwLTAxYzgyNGEwOWUxOSJ9)
