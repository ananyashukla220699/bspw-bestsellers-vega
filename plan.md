# Plan (BSPW Visualization – Vega)

## Dataset
International Bestsellers (June 2013 – Dec 2022)
Source: https://data.post45.org/posts/international-bestsellers/
Raw file: data/raw/international_bestsellers.csv

## Research question
Are women equally represented at the very top of bestseller lists?

## Countries (panels)
France, Germany, Italy, Spain, United States

## Metrics (computed yearly per country)
- women_share_rank1: share of rank #1 titles authored by women
- women_share_top10: share of top-10 entries authored by women

## Output files (to be created)
- data/derived/women_share_rank1_vs_top10_yearly.csv
- viz/women_share_rank1_vs_top10_smallmultiples.vl.json
- figures/women_share_rank1_vs_top10.png

## Notes / caveats to document later
- A few missing months in the dataset for some countries.
- Multi-author gender values (e.g., "m; w") will be handled explicitly.
