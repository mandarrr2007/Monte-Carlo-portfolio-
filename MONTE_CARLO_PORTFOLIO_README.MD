# Monte Carlo Portfolio Risk Simulator

This project simulates 10,000 one-year investment paths for a 4-asset portfolio to evaluate its performance, volatility, and Value-at-Risk (VaR).

## Project Structure

1. **Parameters & Initialization**: Define asset weights, expected daily returns, and daily volatilities (representing Tech, Bonds, Gold, and Emerging Markets) with a random seed.
2. **Daily Returns Simulation**: Generate 10,000 × 252 × 4 normal distribution paths based on historical asset characteristics using `numpy` vectorization.
3. **Portfolio Performance**: Aggregate individual asset returns to calculate cumulative portfolio value utilizing log returns (`np.log1p` & `np.exp`) to represent compounding performance properly.
4. **Risk Evaluation & Visualization**: Chart the distribution of simulated ending capital via a histogram, estimating both portfolio volatility and 95% Value-at-Risk (VaR).

## Key Concepts
- **Log Returns**: Used to safely aggregate compounding multi-period asset movements linearly.
- **Value-at-Risk (95% VaR)**: The threshold at the 5th percentile of outcome distribution showing the maximum expected loss with 95% confidence.

## Outputs Generated
- **`portfolio_simulation_results.csv`**: Contains simulated ending values of the portfolio across all 10,000 runs.
