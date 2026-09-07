# Equity Portfolio Backtesting in R

An R-based historical backtest comparing contrarian ("buy low") and momentum ("buy high") stock-selection strategies across a universe of ten large technology companies in 2018.

> **Project context:** This analysis originated as a group project for a graduate-level Data Analytics with R course. Individual contributions are documented in the [Attribution](#attribution) section.

## Project overview

The project simulates management of a $5 million equity portfolio. The initial capital is divided equally among five stocks, with whole shares purchased at daily closing prices. The portfolio is then rebalanced periodically using one of two rules:

- **Contrarian strategy:** select the five stocks with the largest percentage declines over the preceding interval.
- **Momentum strategy:** select the five stocks with the largest percentage gains over the preceding interval.

The analysis tracks daily mark-to-market (MTM) value, estimates dividend payments, compares both strategies with an equal-stock-price benchmark, examines USD/JPY conversion effects, and evaluates different rebalancing intervals.

## Stock universe

IBM, Microsoft, Alphabet, Apple, Amazon, Meta, Netflix, Tesla, Oracle, and SAP.

## Tools and methods

- R 4.4
- `dplyr` and `tidyr` for data transformation
- `ggplot2` for visualization
- Historical daily closing and adjusted-closing prices
- Whole-share portfolio accounting
- Periodic portfolio rebalancing
- Daily mark-to-market valuation
- In-sample parameter sweep over rebalancing intervals

## Selected results

Starting with $5 million, the original analysis reported:

| Strategy | Rebalancing interval | Final portfolio value |
| --- | ---: | ---: |
| Contrarian | 5 business days | $5,317,037 |
| Momentum | 5 business days | $4,824,152 |
| Contrarian, best in-sample result | 194 business days | $5,926,309 |
| Momentum, best in-sample result | 29 business days | $5,420,556 |

The frequency-search results are **in-sample**: each interval was selected and evaluated using the same 2018 period. They describe what worked best retrospectively within this dataset and should not be interpreted as evidence of future performance.

The four reported ending values above were independently recalculated from the supplied CSV files using the notebook's trading and dividend conventions.

## Repository contents

```text
.
├── README.md
├── equity_portfolio_backtest.ipynb
├── data/
│   ├── README.md
│   └── raw/
│       └── 11 CSV files
├── .gitignore
└── requirements.md
```

The notebook contains the complete analytical workflow and saved output. GitHub renders `.ipynb` files directly in the browser.

## Running the analysis

1. Install R and Jupyter with an R kernel.
2. Install the packages listed in [`requirements.md`](requirements.md).
3. Confirm that the supplied CSV files are present in `data/raw/`.
4. Run the notebook from top to bottom.

## Assumptions and limitations

- Transaction costs, bid-ask spreads, slippage, taxes, and management fees are excluded.
- Trades use daily closing prices and assume execution at those prices.
- Only whole shares are purchased; residual funds remain as cash without interest.
- The ten-stock universe is small and was selected in advance, so it is not representative of the broader market.
- The original benchmark averages nominal stock prices. Because higher-priced stocks receive more influence, it is not a conventional equal-weighted total-return index.
- Dividend amounts are inferred from differences between closing-price and adjusted-closing-price ratios rather than obtained from a dedicated corporate-actions dataset.
- Strategy parameters are optimized and evaluated on the same one-year period, creating substantial overfitting risk.
- The analysis covers only 2018 and does not include out-of-sample validation.

This project is an educational backtest, not investment advice.

## Potential improvements

- Replace the price-average benchmark with a normalized equal-weight total-return index.
- Retrieve prices and corporate actions programmatically from a documented source.
- Separate parameter selection from out-of-sample evaluation.
- Add transaction costs and slippage.
- Report volatility, maximum drawdown, Sharpe ratio, and turnover alongside ending value.
- Test the strategies across multiple market regimes.
- Add automated checks for portfolio conservation and missing market data.

## Attribution

**Course:** Data Analytics with R  
**Institution:** New Jersey Institute of Technology  
**Team members:** Steven Meyer, Matthew Pennington, and Theo Edgehill  
**My contributions:** My contributions primarily involved data cleaning, visualization, and formatting the final HTML submission.

Historical price data in the original assignment were obtained from Yahoo Finance. USD/JPY data were obtained from Myfxbook. Review each provider's redistribution terms before committing raw data to a public repository.
