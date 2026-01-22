# Volatility Modeling of National Bank of Malawi Stock Using GARCH

This project analyzes **National Bank of Malawi (NBM)** stock price data and models its **conditional volatility** using a **GARCH(1,1)** framework.  
The analysis follows standard financial econometrics practice, including return diagnostics, volatility clustering analysis, and walk-forward volatility forecasting.

---

## Data

- **Source:** Malawi Stock Exchange historical data (`MSE_FINAL.csv`)
- **Frequency:** Daily
- **Asset:** National Bank of Malawi (NBM)

---

## Methodology

### 1. Return Construction
Log returns are computed as:

\[
r_t = \ln\left(\frac{P_t}{P_{t-1}}\right)
\]

This transformation improves stationarity and is standard for ARCH/GARCH modeling.

---

### 2. Data Cleaning
- Extreme outliers (daily returns beyond ±100%) are identified and removed
- This mitigates distortions caused by illiquidity or data errors common in emerging markets

---

### 3. Exploratory Analysis
- Return distribution (histogram & KDE)
- Autocorrelation Function (ACF)
- Partial Autocorrelation Function (PACF)

Results confirm:
- No linear autocorrelation in returns
- Presence of volatility clustering

---

### 4. Volatility Modeling
A **GARCH(1,1)** model is fitted:

\[
\sigma_t^2 = \omega + \alpha \varepsilon_{t-1}^2 + \beta \sigma_{t-1}^2
\]

The model is estimated using **walk-forward validation**, avoiding look-ahead bias.

---

### 5. Forecast Evaluation
- Predicted conditional volatility is compared to realized volatility
- Realized volatility is computed using a rolling standard deviation
- Scale mismatches (daily vs annualized volatility) are explicitly diagnosed and corrected

---

## Key Insights

- NBM returns show no serial correlation, consistent with weak-form efficiency
- Volatility exhibits persistence, well captured by GARCH(1,1)
- Walk-forward GARCH forecasts track volatility regimes reasonably well
- Scale alignment (daily vs annualized volatility) is critical for proper evaluation

---

## Requirements

- Python 3.9+
- pandas
- numpy
- matplotlib
- seaborn
- statsmodels
- arch

Install dependencies:

```bash
pip install pandas numpy matplotlib seaborn statsmodels arch
