# BSPW Visualization — Domestic share in Top-10 bestseller lists (2013–2022)

This mini-project uses an international bestseller dataset to examine how strongly Top-10 bestseller lists are dominated by domestic authors, comparing **Germany** with **EU peers (avg)** and the **United States** over time.

## Research question
**Domestic share in Top-10 bestseller lists: Germany vs EU peers vs United States (2013–2022).**

**Domestic (proxy)**: an entry is counted as domestic if the author nationality includes the market country (author nationality matches market country; proxy, not language/translation).

**EU peers (avg)**: unweighted mean of country-level domestic shares for **France, Italy, Spain** (not pooled titles).

## Data source
Dataset: Post45 — International bestsellers  
Raw file in this repo: `data/raw/international_bestsellers.csv`

## Derived data (used by Vega)
To keep the visualization reproducible and lightweight, the Vega chart reads a small derived table:

- `data/derived/domestic_share_top10_marketgroup_yearly_2013_2022.csv`

Schema:
- `year` (int)
- `market_group` (Germany / EU peers (avg) / United States)
- `domestic_share_top10_pct` (float, 0–100)
- `n_top10_valid` (int)
- `n_domestic` (int)

## Visualization
Final Vega-Lite spec:
- `viz/domestic_share_top10_germany_vs_eu_vs_us.vl.json`

## How to reproduce
1) Run the notebook to regenerate the derived CSV:
   - `notebooks/01_prepare_data.ipynb`

2) Open the Vega-Lite spec (e.g., in the Vega editor). The data URL points to the derived CSV in this repo.

## Notes / limitations
- “Domestic” is based on an **author nationality proxy**; it does not measure translation status or publication language.
- EU peers (avg) is the **mean of country-level shares**, not a pooled share across all EU-peer titles.