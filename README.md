# BSPW Visualization — Domestic share in Top-10 bestseller lists (2013–2022)

This mini-project uses an international bestseller dataset to examine how strongly Top-10 lists are dominated by domestic authors, comparing **Germany** with **EU peers** and the **United States** over time.

## Research question
**Domestic share in Top-10 bestseller lists: Germany vs EU peers vs United States (2013–2022).**

Domestic is defined as: **author nationality matches market country** (proxy; not language/translation).

EU peers (avg) is computed as the **unweighted mean of country-level domestic shares** for **France, Italy, Spain** (not pooled titles).

## Data source
The raw dataset is taken from:
https://data.post45.org/posts/international-bestsellers/

Raw file in this repo:
- `data/raw/international_bestsellers.csv`

## Derived data (used by Vega)
To keep the visualization reproducible and simple, the Vega chart reads a small derived table:

- `data/derived/domestic_share_top10_marketgroup_yearly_2013_2022.csv`

Schema:
- `year` (int)
- `market_group` (Germany / EU peers (avg) / United States)
- `domestic_share_top10` (float, 0–1)

## Visualization
Final Vega-Lite spec:
- `viz/domestic_share_top10_germany_vs_eu_vs_us.vl.json`

The chart shows the **share of domestic authors among Top-10 bestseller entries** by year for three market groups.

## How to reproduce
1) Run the notebook to regenerate the derived CSV:
   - `notebooks/01_prepare_data.ipynb`

2) Open the Vega-Lite spec (e.g., in the Vega editor) and ensure the data URL points to the derived CSV in this repo.

## Notes / limitations
- “Domestic” is a **nationality proxy**; it does not directly measure translation status or language of publication.
- EU peers is an **average of country-level shares**, not a pooled share across all EU-peer titles.