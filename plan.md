# Plan — Domestic share in Top-10 bestseller lists (2013–2022)

## Goal
Create a clear, principle-driven time-series figure comparing domestic dominance in Top-10 bestseller lists for:
- Germany
- EU peers (avg of France, Italy, Spain; not pooled)
- United States

## Definitions
Domestic (proxy):
An entry is domestic if the market country appears in the author nationality field (to handle multi-nationality entries).

Domestic share of Top-10 (per year, per market):
domestic_share_top10 = (# Top-10 entries counted domestic) / (total Top-10 entries)

EU peers (avg):
For each year, compute the unweighted mean of the country-level domestic shares for France, Italy, Spain.

## Data workflow
Input:
- `data/raw/international_bestsellers.csv`

Derivation (notebook):
- Notebook: `notebooks/01_prepare_data.ipynb`

Steps:
1) Parse year from `date`
2) Filter years 2013–2022
3) Filter markets: Germany, France, Italy, Spain, United States
4) Restrict to Top-10 ranks (rank 1–10)
5) Compute `is_domestic` (market appears in nationality list; split on `,` or `;`)
6) Aggregate per year × country → domestic share + counts
7) Create market groups:
   - Germany (as-is)
   - United States (as-is)
   - EU peers (avg): mean of France/Italy/Spain shares per year (unweighted, not pooled)

Output used by Vega:
- `data/derived/domestic_share_top10_marketgroup_yearly_2013_2022.csv`

## Visualization design intent (Vega-Lite)
- Line chart with points for year-to-year comparisons.
- Germany emphasized with stronger opacity; EU peers and US muted but readable.
- Horizontal gridlines only (reduced clutter).
- Legend on the right (no in-line labels).