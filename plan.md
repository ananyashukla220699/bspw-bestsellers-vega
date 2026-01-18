# Plan — Domestic share in Top-10 bestseller lists (2013–2022)

## Goal
Create a clear, principle-driven time-series figure that compares how much Top-10 bestseller lists are dominated by domestic authors in:
- Germany
- EU peers (avg of France, Italy, Spain; not pooled)
- United States

## Definitions
Domestic (proxy):
An entry is counted as domestic if **author nationality == market country**.

Domestic share of Top-10 (per year, per market):
For each market country and year, compute:

domestic_share_top10 =
(# of Top-10 entries with author nationality == market country) / (total Top-10 entries)

EU peers (avg):
For each year, compute the **unweighted mean** of the domestic shares for France, Italy, and Spain.

## Data workflow
### Input
`data/raw/international_bestsellers.csv`

### Derivation (in notebook)
Notebook: `notebooks/01_prepare_data.ipynb`

Steps:
1) Filter to years 2013–2022.
2) Filter to markets: Germany, France, Italy, Spain, United States.
3) Restrict to Top-10 ranks only (rank 1–10).
4) Create `is_domestic = (author_nationality == market_country)`.
5) Aggregate per year and market:
   - domestic_share_top10 = mean(is_domestic)
6) Create market groups:
   - Germany (as-is)
   - United States (as-is)
   - EU peers (avg): mean of France/Italy/Spain shares per year (unweighted; not pooled)

### Output used by Vega
`data/derived/domestic_share_top10_marketgroup_yearly_2013_2022.csv`

Schema:
- year
- market_group
- domestic_share_top10 (0–1)

## Visualization design intent (Vega-Lite)
- Use a line chart with points to support year-to-year comparisons.
- Emphasize Germany with stronger color; keep EU peers and United States muted but still readable.
- Use a percent y-axis (0–100%).
- Use only horizontal gridlines to reduce clutter.
- Keep subtitle concise but explicit about the proxy definition and EU-peer averaging method.