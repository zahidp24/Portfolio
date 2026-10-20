# Analysis & Forecast of Stock Volatility

Can high-frequency data predict tomorrow's volatility better than standard GARCH models? This project compares six models for forecasting the realized volatility of a stock, using 1,500 daily observations from January 2010 to January 2016.

📓 **[View the notebook](Stock_Volatility_Analysis_Forecast.ipynb)**

## Key findings

- **Models using high-frequency information forecast best.** Adding semi-volatility, realized skewness and kurtosis improves forecasts over standard return-based GARCH models.
- **Forecasts were tested out of sample**, using both expanding and rolling windows, and compared formally with Diebold-Mariano tests.

## Data

- **1,500 daily observations** of realized volatility measures for one asset (Asset 12), January 2010 to January 2016
- **File:** [`12.RData`](12.RData)

## Models compared

1. AR
2. HAR (Corsi, 2009)
3. HAR-RS, adding semi-volatility
4. HAR-RS-RK, adding realized skewness and kurtosis
5. Realized GARCH (Hansen, Huang & Shek, 2012)
6. ARMA-GARCH

## Evaluation

- **In sample:** R², coefficient significance with Newey-West standard errors
- **Out of sample:** MSE, MAE, Diebold-Mariano tests, Mincer-Zarnowitz regressions

## Files

| File | Description |
|---|---|
| `Stock_Volatility_Analysis_Forecast.ipynb` | Full analysis (R notebook) |
| `Stock_Volatility_Analysis_Forecast.html` | Same notebook as a web page, for viewing without Jupyter |
| `12.RData` | Dataset |

## How to reproduce

1. Install the R packages:
```r
   install.packages(c("xts", "forecast", "rugarch", "lmtest", "sandwich"))
```
2. Open the notebook in Jupyter with an R kernel (IRkernel), or copy the code into RStudio.
3. Run all cells.

## Tools

R · Jupyter · rugarch · HAR models · forecast evaluation

## Author

**Zahid Pashayev** · [LinkedIn](https://www.linkedin.com/in/zahid-pashayev)
