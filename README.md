[README-2.md](https://github.com/user-attachments/files/33546051/README-2.md)
# Monte Carlo Portfolio Risk Simulator

A Python-based Monte Carlo simulation that models one year of returns for a four-asset investment portfolio. It runs 10,000 simulated investment paths and visualizes the distribution of ending portfolio values, alongside a simple estimate of 95% Value-at-Risk (VaR).

## Project Overview

The notebook uses NumPy to generate daily asset returns, combines them into portfolio returns, compounds the returns over 252 trading days, and plots the resulting final portfolio values.

## Technologies Used

- **Python**
- **NumPy** — random return generation and numerical calculations
- **Pandas** — imported in the notebook (not currently used in the shown calculations)
- **Matplotlib** — histogram visualization

## Simulation Configuration

The notebook uses the following settings:

| Parameter | Value |
|---|---:|
| Number of simulations | 10,000 |
| Trading days per simulation | 252 |
| Number of assets | 4 |
| Initial portfolio value | 1.0 |
| Portfolio weights | 25% per asset |
| Random seed | 42 |

The four assets represent illustrative categories: Technology, Bonds, Gold, and Emerging Markets. Their daily means and volatilities are defined as arrays in the notebook.

## How It Works

1. **Initialize parameters** — set the random seed, simulation count, asset means, asset volatilities, and equal portfolio weights.
2. **Simulate daily returns** — generate normally distributed random values for 10,000 paths, 252 trading days, and four assets.
3. **Calculate portfolio returns** — combine the asset returns using the portfolio weights.
4. **Compound returns** — use `numpy.log1p()` and `numpy.exp()` to accumulate daily returns and calculate each path's ending portfolio value.
5. **Measure and visualize risk** — plot a histogram of ending values, calculate the standard deviation of ending values, and estimate 95% VaR using the 5th percentile.

## Key Concepts

- **Monte Carlo simulation:** explores a range of possible outcomes by repeatedly sampling random returns.
- **Compounding:** models how returns accumulate over multiple trading days.
- **Log returns:** `numpy.log1p()` converts simple returns to log returns, which can be summed across time; `numpy.exp()` converts cumulative log returns back to a growth multiplier.
- **95% Value-at-Risk (VaR):** in this notebook, VaR is estimated as `1.0 - the 5th percentile of final portfolio values`, assuming an initial portfolio value of 1.0.
- **Outcome standard deviation:** the notebook reports the standard deviation of final portfolio values. This is the dispersion of ending outcomes, not annualized daily volatility.

## Requirements

Install the required libraries if they are not already available:

```bash
pip install numpy pandas matplotlib
```

## How to Run

1. Open `monte_carlo_portfolio.ipynb` in Jupyter Notebook, JupyterLab, or a compatible notebook environment.
2. Ensure the required Python libraries are installed.
3. Run the notebook cells from top to bottom.
4. Review the histogram and printed risk metrics.

## Output

The notebook displays a histogram of simulated final portfolio values and prints:
- The shape of the simulated return array
- The shape of the final portfolio values array
- The standard deviation of final portfolio outcomes
- The estimated 95% one-year VaR

**Note:** The current notebook displays results but does not save them to a CSV file. Add a `pandas.DataFrame(...).to_csv(...)` step if you want to export the simulated ending values.

## Limitations

- Asset returns are modeled using normal distributions with fixed daily means and volatilities.
- The simulation assumes equal portfolio weights and does not model rebalancing, transaction costs, taxes, or changing market conditions.
- The asset categories are illustrative; the parameters are assumptions, not a forecast or a guarantee of future performance.
- VaR summarizes a percentile-based loss threshold and does not describe the size of losses beyond that threshold.
