# Conditional Volatility of AEX Returns: GARCH vs GJR-GARCH

Does bad news move the Dutch stock market's volatility more than good news? This project models the daily volatility of the **Amsterdam Exchange Index (AEX)** from 2010 to 2023 and tests whether an asymmetric GJR-GARCH model describes it better than a standard GARCH(1,1).

📄 **[Read the full paper (PDF)](paper/AEX_volatility_GARCH_paper.pdf)** · Applied Econometrics term paper, Institute of Economic Studies, Charles University (May 2026)

![News impact curve](/figures/04_news_impact_curve.png)

## Key findings

- **Negative shocks hit volatility about 6x harder than positive ones.** In the GJR-GARCH model, the short-run response to a negative shock is 0.132 versus 0.023 for a positive shock of the same size. The asymmetry term (γ = 0.110) is significant at 1% with robust standard errors.
- **Volatility is highly persistent.** Persistence is about 0.98 in every model, which implies a half-life of roughly 40 to 50 trading days: it takes about two months for half of a volatility spike to fade.
- **Returns are fat-tailed.** Excess kurtosis is 6.8, and the Student-t distribution (≈7.6 degrees of freedom) beats the normal distribution on all four information criteria.
- **Best model: GJR-GARCH(1,1) with Student-t errors.** It wins on AIC, BIC, Shibata and Hannan-Quinn, a likelihood ratio test rejects the symmetric model (p < 0.001), and it passes the Ljung-Box and ARCH-LM residual tests.

## Data

- **Source:** Yahoo Finance, ticker `^AEX`, daily closing prices
- **Period:** 4 January 2010 to 6 March 2023
- **Size:** 3,374 prices → 3,373 daily log returns (one missing holiday price removed)

See [`data/README.md`](data/README.md) for how to get the file.

## Methods

1. **Stationarity:** ADF and KPSS tests on prices and log returns
2. **Mean equation:** ARMA selection with `auto.arima` (BIC) plus manual checks of ARMA(1,1), (2,2), (5,5) → constant mean ARMA(0,0)
3. **ARCH effects:** ACF/PACF of squared residuals, ARCH-LM test, Ljung-Box test
4. **Volatility models:** GARCH(1,1) with normal and Student-t errors, BIC grid search up to GARCH(5,5), GJR-GARCH(1,1) with Student-t errors
5. **Comparison and diagnostics:** information criteria, likelihood ratio test, sign bias test, Nyblom stability test, news impact curve, residual diagnostics

| Model | AIC | BIC | Persistence |
|---|---|---|---|
| GARCH(1,1) Normal | -6.3641 | -6.3568 | 0.987 |
| GARCH(1,1) Student-t | -6.3862 | -6.3771 | 0.987 |
| **GJR-GARCH(1,1) Student-t** | **-6.3903** | **-6.3793** | **0.984** |

![Conditional volatility](outputs/figures/03_conditional_volatility.png)

## Repository structure

```
├── README.md
├── paper/
│   └── AEX_volatility_GARCH_paper.pdf    full term paper
├── R/
│   └── AEX_script.R                      full analysis: tests, models, figures
├── data/
│   ├── README.md                         data source and description
│   └── AEX.csv                           daily AEX prices
└── figures/                              charts used in the paper
    ├── 01_aex_close_price.png
    ├── 02_log_returns.png
    ├── 03_conditional_volatility.png
    └── 04_news_impact_curve.png
```

## How to reproduce

1. Clone the repo and open R in the repository folder.
2. Install the packages:
   ```r
   install.packages(c("tidyverse", "tseries", "xts", "forecast",
                      "moments", "aTSA", "rugarch", "quantmod"))
   ```
3. If `data/AEX.csv` is missing, run `R/00_download_data.R`.
4. Run `R/01_analysis.R`. Results print to the console and figures are saved to `outputs/figures/`.

## Tools

R · rugarch · forecast · tseries · tidyverse · xts

## Authors

**Zahid Pashayev** · [LinkedIn](https://www.linkedin.com/in/YOUR-PROFILE)

Co-author: Maxim Milde
