# BSPW – International Bestsellers (Vega Visualization)

This repository supports the BSPW visualization portfolio task (Vega/Vega-Lite).

## Dataset
**International Bestsellers (June 2013 – December 2022)**  
Monthly Top-10 fiction bestseller lists for multiple countries.

- Dataset page (source): https://data.post45.org/posts/international-bestsellers/
- File used in this repo: `data/raw/international_bestsellers.csv`


## Planned analysis question
**Are women equally represented at the very top of bestseller lists?**  
For each country and each year, we compare:
1) women share among **rank #1** titles vs  
2) women share among **all top-10** entries.

Countries used for the visualization: **France, Germany, Italy, Spain, United States**.

## Output
- Derived analysis table: `data/derived/` (yearly aggregation)
- Vega-Lite specification: `viz/`
- Exported figure: `figures/`
