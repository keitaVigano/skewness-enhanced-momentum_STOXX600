# STOXX600 Skewness-Enhanced Momentum Strategies

This repository contains a financial analysis project on long-short equity strategies applied to the STOXX Europe 600 index. The project focuses on enhancing traditional momentum strategies using skewness-based filters and volatility scaling.

## Objective

The primary goal is to assess whether incorporating skewness into momentum-based strategies improves performance across different market capitalizations (small, medium, and large caps). The analysis also evaluates the impact of volatility adjustment on performance stability.

## Repository Structure

| File                      | Description                                                       |
|---------------------------|-------------------------------------------------------------------|
| `analysis.ipynb`          | Main notebook with data loading, strategy implementation, metrics |
| `Europe_3_Factors.csv`    | Fama-French 3-factor model data for European equities             |
| `STOXX600.csv`            | Monthly returns of STOXX600 index components                      |
| `Stoxx 600 Originale.xlsm`| Original raw dataset of STOXX600 prices and constituents          |
| `Germany_3Month_Bond.csv` | Monthly risk-free rate proxy from 3 months german bund            |
| `.gitignore`              | Git configuration to ignore non-essential files                   |
| `LICENSE`                 | MIT license file                                                  |
| `README.md`               | This project description                                          |

## Methodology

- **Momentum**: computed as cumulative returns over a past window (typically 6–12 months)
- **Skewness filtering**: proxy for expected skewness based on maximum daily returns (SKEWMAX)
- **Volatility scaling**: adjusts portfolio weights to target constant volatility
- **Risk-free rate**: computed dynamically from monthly `^IRX` values
- **Performance metrics**:
  - Annualized CAPM alpha and FF3 alpha
  - Sharpe ratio
  - Sortino ratio
  - Information ratio
  - Annualized volatility
  - Downside volatility
  - Maximum drawdown

## Strategy Variants

Each strategy is implemented in three variants:

- `base`: pure momentum strategy
- `skew+mom`: filtered by skewness and momentum
- `skew+mom+vol`: volatility-scaled version of the above

These are tested separately on:

- Small-cap stocks
- Mid-cap stocks
- Large-cap stocks

## Reproducibility

To ensure the code runs consistently across environments, use Conda to create the environment from the provided file:

```bash
conda env create -f environment.yaml
conda activate momentum_skewness
```

## Summary

The notebook presents all performance metrics in a comparative table and includes observations on trade-offs between alpha, risk-adjusted returns, and drawdowns.

## License

This project is distributed under the MIT License.
