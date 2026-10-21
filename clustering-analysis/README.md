# Clustering Analysis of 2020 Daily Stock Returns

How do stocks move together during a crisis? This project groups 22 stocks by how their daily returns moved together in 2020, the year of the COVID-19 crash, the vaccine race and the Kodak spike.

📄 **[Read the full report (PDF)](Clustering%20Analysis.pdf)**

## Key findings

- **All five clustering methods agree on the same five clusters**, which makes the result robust rather than a quirk of one method.
- **Three sector groups:** cyclical stocks (banking, energy, chemicals), large pharma, and big tech.
- **Two outliers, each with its own story:** Moderna, driven by vaccine news, and Kodak, driven by a one-off speculative spike.

## Data

- **251 trading days** of daily returns for **22 stocks** in 2020
- **File:** [`daily_stock_returns_2020.dat`](daily_stock_returns_2020.d)

## Methods

1. Pearson correlations between all stocks, converted into a distance (1 − r)
2. Hierarchical clustering: average, complete and single linkage
3. Ward's method, using chord distance because Ward requires Euclidean distances
4. PAM (k-medoids) as a non-hierarchical cross-check
5. Number of clusters chosen with silhouette analysis; methods compared with cophenetic correlations
6. Results shown with dendrograms, heatmaps and MDS plots

## Files

| File | Description |
|---|---|
| `Clustering_Analysis.R` | Full analysis code |
| `daily_stock_returns_2020.dat` | Daily return data |
| `Clustering Analysis.pdf` | Full report with all figures |

## How to reproduce

1. Clone the repo and open R in this folder.
2. Run `Clustering_Analysis.R`.

## Tools

R · hierarchical clustering · PAM · silhouette analysis · MDS

## Author

**Zahid Pashayev** · [LinkedIn](https://www.linkedin.com/in/zahid-pashayev)
