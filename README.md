# GMF Investments - Financial Time Series Forecasting

Welcome to the GMF Investments repository! This project demonstrates how financial analysts can use time series forecasting to enhance portfolio management strategies. The goal of this project is to apply predictive modeling to historical financial data to guide investment decisions, optimize asset allocation, and minimize risks.

## Project Overview

**GMF Investments** is a forward-thinking financial advisory firm specializing in personalized portfolio management. This project utilizes time series forecasting models to analyze historical financial data and predict future market trends, ultimately aiding in portfolio management for clients.

By leveraging **YFinance** data and employing advanced models such as ARIMA and LSTM, this project aims to forecast stock prices and market indices, helping financial analysts and clients make data-driven decisions.

### Key Assets
- **Tesla (TSLA)**: A high-growth, high-risk stock in the consumer discretionary sector (Automobile Manufacturing).
- **Vanguard Total Bond Market ETF (BND)**: A bond ETF that provides stability and low risk.
- **S&P 500 ETF (SPY)**: An ETF that tracks the broad U.S. stock market, providing diversified market exposure.

## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Installation](#installation)
- [Usage](#usage)
- [Analysis](#analysis)
- [Results](#results)
- [License](#license)

## Data Sources

The data used in this project was sourced from **YFinance**, covering the period from January 1, 2015, to January 31, 2025. The dataset includes:

- **TSLA**: Daily stock prices (Open, High, Low, Close), volume, and volatility.
- **BND**: Daily bond ETF prices (Open, High, Low, Close), volume, and volatility.
- **SPY**: Daily S&P 500 ETF prices (Open, High, Low, Close), volume, and volatility.

Each dataset includes the following columns:
- **Date**: Trading day timestamp.
- **Open**, **High**, **Low**, **Close**: Daily price metrics.
- **Adj Close**: Adjusted closing price to account for dividends and splits.
- **Volume**: Total number of shares traded.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/1Light/kaim-week-11.git
   cd kaim-week-11
   ```

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Install additional dependencies if needed (for data visualization, machine learning, etc.):
   ```bash
   pip install matplotlib seaborn statsmodels yfinance tensorflow
   ```

## Usage

To start analyzing the financial data, use the following steps:

1. **Download the Data**:  
   Use the `yfinance` library to download historical data for TSLA, BND, and SPY. 
   
   ```python
   import yfinance as yf

   # Define the ticker symbols
   tickers = ['TSLA', 'BND', 'SPY']

   # Download data
   data = yf.download(tickers, start='2015-01-01', end='2025-01-31')
   ```

2. **Preprocess the Data**:  
   Clean the data by checking for missing values and correcting data types. This also includes normalization and scaling for machine learning models.
   
   ```python
   # Check for missing values
   data.isnull().sum()

   # Handle missing data (interpolation or forward fill)
   data.fillna(method='ffill', inplace=True)
   ```

3. **Perform Exploratory Data Analysis (EDA)**:  
   Visualize the data to understand trends, volatility, and patterns.
   
   ```python
   import matplotlib.pyplot as plt

   # Plot closing prices for all assets
   data['Close'].plot(figsize=(12, 6))
   plt.title("Closing Prices for TSLA, BND, and SPY")
   plt.show()
   ```

4. **Build Time Series Forecasting Models**:  
   Utilize ARIMA, GARCH, and LSTM models to predict future stock prices and market trends.
   
   ```python
   from statsmodels.tsa.arima.model import ARIMA

   # Fit ARIMA model
   arima_model = ARIMA(data['TSLA']['Close'], order=(5,1,0))
   arima_results = arima_model.fit()
   ```

5. **Evaluate and Recommend Portfolio Adjustments**:  
   Use the forecasts to recommend changes in the portfolio, based on predicted trends and volatility.

## Analysis

The project involves the following key steps:

1. **Data Preprocessing**: Loading and cleaning historical financial data.
2. **Exploratory Data Analysis (EDA)**: Visualizing key metrics such as closing prices, daily percentage changes, and volatility.
3. **Time Series Modeling**: Developing models to forecast future market trends, including ARIMA and LSTM models.
4. **Volatility and Risk Analysis**: Assessing short-term and long-term market volatility to make informed decisions on asset allocation.

## Results

### Key Insights:
- **TSLA**: High growth but volatile. Major price fluctuations observed during periods of market uncertainty.
- **BND**: Stable returns with minimal volatility, useful for portfolio diversification.
- **SPY**: Offers moderate-risk exposure to the broader U.S. market, providing a balanced risk-return profile.

### Performance Metrics:
- **Value at Risk (VaR)**: Quantified potential loss under normal market conditions.
- **Sharpe Ratio**: Measures risk-adjusted returns for portfolio optimization.

### Volatility Analysis:
- Rolling mean and standard deviation calculations were used to assess short-term price volatility, particularly during periods of geopolitical and economic uncertainty.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---