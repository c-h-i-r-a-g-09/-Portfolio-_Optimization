# -Portfolio-_Optimization
 Portfolio Optimization using Modern Portfolio Theory using markowitz model

# Stock Portfolio Optimization & Analysis

A comprehensive Python-based portfolio optimization project that analyzes Indian stock market data (NSE) to identify optimal investment portfolios using Modern Portfolio Theory and the Efficient Frontier.


> This project was developed as part of coursework in Financial Engineering/Quantitative Finance and demonstrates production-ready code that can be adapted for real-time portfolio management systems.

## 📊 Project Overview

This project implements a quantitative approach to stock selection and portfolio optimization by:
- Screening 48 Indian stocks based on fundamental metrics
- Selecting top 10 stocks using a composite scoring system
- Analyzing historical price data and returns
- Generating optimal portfolio allocations using Monte Carlo simulation
- Visualizing risk-return tradeoffs through the Efficient Frontier

### 🔴 Real-Time Capabilities

This implementation supports **real-time analysis** with:
- **Live Data Fetching**: Automatically pulls latest stock data from Yahoo Finance API
- **Dynamic Date Ranges**: Uses current date as end_date for up-to-date analysis
- **On-Demand Screening**: Recalculates fundamental scores with fresh market data
- **Automated Portfolio Rebalancing**: Can be scheduled to run daily/weekly for portfolio updates

## 🎯 Key Features

- **Fundamental Analysis**: Multi-factor scoring based on profitability, market cap, financial strength, and valuation
- **Technical Analysis**: Moving averages (50-day & 200-day) and price trend visualization
- **Risk Analytics**: Daily returns distribution, correlation analysis, and volatility metrics
- **Portfolio Optimization**: Monte Carlo simulation with 10,000 random portfolios
- **Interactive Visualizations**: Plotly-based efficient frontier with Sharpe ratio heatmap

## 🛠️ Technologies Used

- **Python 3.x**
- **Data Analysis**: pandas, numpy
- **Data Source**: yfinance (Yahoo Finance API)
- **Visualization**: matplotlib, seaborn, plotly
- **Statistical Analysis**: scipy (implied through portfolio calculations)

## 📦 Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/portfolio-optimization.git
cd portfolio-optimization

# Install required packages
pip install pandas numpy yfinance matplotlib seaborn plotly tqdm
```

## 🚀 Usage

### Basic Analysis
```python
# Run the main analysis
python portfolio_analysis.py

# The script will:
# 1. Fetch stock data from Yahoo Finance
# 2. Calculate fundamental scores
# 3. Generate visualizations
# 4. Plot the efficient frontier
```

### Real-Time Implementation

#### Option 1: Run on-demand for latest data
```python
# The script automatically uses today's date
# Just run it whenever you need updated analysis
python portfolio_analysis.py
```

#### Option 2: Schedule automated runs (Unix/Linux/Mac)
```bash
# Add to crontab for daily execution at 6 PM IST
0 18 * * * /usr/bin/python3 /path/to/portfolio_analysis.py

# For weekly execution (every Monday)
0 18 * * 1 /usr/bin/python3 /path/to/portfolio_analysis.py
```

#### Option 3: Real-Time Monitoring Setup
```python
# Create a monitoring script for continuous updates
import schedule
import time

def run_analysis():
    exec(open('portfolio_analysis.py').read())
    print(f"Analysis completed at {datetime.now()}")

# Schedule to run every day at market close (3:30 PM IST)
schedule.every().day.at("15:30").do(run_analysis)

while True:
    schedule.run_pending()
    time.sleep(3600)  # Check every hour
```

### Real-Time API Integration (Advanced)
For institutional/production use, integrate with live data feeds:
```python
# Example with real-time data provider
from realtime_data_provider import get_live_prices

# Replace yfinance with live feed
live_data = get_live_prices(tickers)
# Continue with existing analysis pipeline
```

## 📈 Methodology

### 1. Stock Screening
Initial universe of 48 NSE stocks screened using:
- **Profitability Score**: Based on profit margins
- **Market Cap Score**: Log-transformed market capitalization
- **Financial Strength Score**: Inverse debt-to-equity ratio
- **Valuation Score**: Inverse P/E ratio

### 2. Top 10 Stock Selection
Selected stocks (as of analysis date):
1. HDFCAMC.NS (HDFC Asset Management)
2. OBEROIRLTY.NS (Oberoi Realty)
3. GODREJPROP.NS (Godrej Properties)
4. OFSS.NS (Oracle Financial Services)
5. FEDERALBNK.NS (Federal Bank)
6. NMDC.NS (National Mineral Development Corp)
7. BANDHANBNK.NS (Bandhan Bank)
8. M&MFIN.NS (Mahindra & Mahindra Financial)
9. AUBANK.NS (AU Small Finance Bank)
10. INDUSTOWER.NS (Indus Towers)

### 3. Portfolio Optimization
- **Time Period**: 1 year historical data (Oct 2023 - Oct 2024)
- **Optimization Method**: Monte Carlo simulation (10,000 portfolios)
- **Objective**: Maximize Sharpe Ratio (risk-adjusted returns)
- **Constraints**: Weights sum to 1 (fully invested portfolio)

## 📊 Key Outputs

### Visualizations Generated:
1. **Price Charts**: Adjusted close prices with 50-day and 200-day moving averages
2. **Volume Analysis**: Trading volume trends for each stock
3. **Return Distributions**: Histograms showing daily return patterns
4. **Correlation Matrix**: Heatmap of inter-stock correlations
5. **Efficient Frontier**: Interactive scatter plot showing risk-return tradeoff

### Performance Metrics:
- Annualized returns
- Volatility (standard deviation)
- Sharpe ratios
- Correlation coefficients

## 📝 Sample Results

```
Top Stock by Total Score:
HDFCAMC.NS - Total Score: 89.27
- Profitability Score: 61.23
- Market Cap Score: 27.66
- Financial Strength: 0.36
- Valuation Score: 0.02

Expected Annual Returns Range: -10.16% to 120.93%
Portfolio Volatility Range: 25% to 47%
```

## 🔍 Analysis Period

- **Data Collection**: Rolling 1-year window (dynamically calculated)
- **Current Implementation**: October 12, 2023 - October 12, 2024 (example run)
- **Real-Time Mode**: Automatically uses `today - 365 days` to `today`
- **Market**: National Stock Exchange of India (NSE)
- **Frequency**: Daily data with intraday compatibility
- **Market Hours**: NSE trades 9:15 AM - 3:30 PM IST

### Data Freshness
The system automatically fetches the latest available data:
```python
end_date = date.today().strftime("%Y-%m-%d")  # Always current
start_date = (date.today() - timedelta(days=365)).strftime("%Y-%m-%d")
```

## 🏢 Real-World Applications

This project demonstrates skills applicable to:

### Financial Institutions
- **Asset Management Firms**: Portfolio construction and rebalancing
- **Investment Banks**: Quantitative research and trading strategies
- **Hedge Funds**: Systematic trading strategy development
- **Wealth Management**: Client portfolio optimization

### Practical Use Cases
1. **Personal Portfolio Management**: Individual investors can run this weekly to rebalance
2. **Robo-Advisory Systems**: Backend engine for automated investment platforms
3. **Risk Management**: Monitor portfolio risk metrics in real-time
4. **Research & Backtesting**: Test investment strategies with historical data
5. **Educational Tool**: Teach Modern Portfolio Theory with live market data

### Industry-Ready Features
- ✅ Modular code structure for easy integration
- ✅ Error handling for market holidays and missing data
- ✅ Scalable to thousands of stocks
- ✅ Compatible with various data providers
- ✅ Export-ready outputs (CSV, JSON, Excel)
- ✅ API-ready for web/mobile applications

## 🔧 Extending for Production

### Adding Real-Time Alerts
```python
def check_rebalancing_trigger(portfolio_weights, current_weights, threshold=0.05):
    """Alert when portfolio drifts beyond threshold"""
    if abs(portfolio_weights - current_weights).max() > threshold:
        send_notification("Portfolio rebalancing recommended")
```

### Database Integration
```python
# Store results in database for historical tracking
import sqlite3

def save_portfolio_results(date, weights, returns, risk):
    conn = sqlite3.connect('portfolio_history.db')
    # Save analysis results
    conn.execute("INSERT INTO portfolios VALUES (?, ?, ?, ?)", 
                 (date, weights, returns, risk))
    conn.commit()
```

### API Endpoint (Flask Example)
```python
from flask import Flask, jsonify
app = Flask(__name__)

@app.route('/api/optimal-portfolio', methods=['GET'])
def get_optimal_portfolio():
    # Run analysis
    weights = run_optimization()
    return jsonify({
        'weights': weights.tolist(),
        'timestamp': datetime.now().isoformat(),
        'expected_return': float(portfolio_return),
        'risk': float(portfolio_volatility)
    })
```

## ⚠️ Disclaimer

This project is for **educational and research purposes** only. While it uses real-time data and production-ready code architecture, it should NOT be considered as financial advice. 

**Important Notes for Real-Time Usage:**
- Market data may have delays (typically 15-20 minutes for free APIs)
- Past performance does not guarantee future results
- Transaction costs, taxes, and slippage are not included in calculations
- Always validate results before making investment decisions
- Consider consulting with a qualified financial advisor
- Test thoroughly with paper trading before live deployment

**For Production Deployment:**
- Implement proper risk management controls
- Add comprehensive error handling and logging
- Use authenticated data feeds for real-time accuracy
- Include transaction cost modeling
- Implement position sizing and leverage controls
- Add compliance and regulatory checks

## 🤝 Contributing

Contributions are welcome! This project is actively maintained and open to enhancements for real-time capabilities.

### Areas for Contribution:
- 🔴 Real-time data feed integrations (NSE, Bloomberg, Alpha Vantage)
- 📊 Additional risk metrics (VaR, CVaR, Maximum Drawdown)
- 🤖 Machine learning models for return prediction
- 📱 Web dashboard for live portfolio monitoring
- 🔔 Alert systems for rebalancing triggers
- 📈 Backtesting framework with transaction costs
- 🌐 Multi-market support (BSE, US stocks, cryptocurrencies)




**Learning Outcomes Demonstrated:**
- Application of Modern Portfolio Theory
- Quantitative analysis of financial instruments
- Risk-return optimization techniques
- Data visualization for financial decision-making
- Python programming for finance
- Real-time data processing and analysis

**Skills Acquired:**
- Financial modeling and analysis
- Statistical computing with Python
- API integration for financial data
- Time-series analysis
- Portfolio optimization algorithms
- Data visualization best practices

## 📧 Contact

Your Name - [Chirag Arora](chiragarora1309@gmail.com)


## 📚 References

- Modern Portfolio Theory (Markowitz, 1952)
- Yahoo Finance API Documentation
- Python for Finance: Mastering Data-Driven Finance
- NSE India Market Data Guidelines
- Sharpe Ratio and Portfolio Performance Metrics

## 🚀 Future Enhancements

### Planned Features:
- [ ] Real-time WebSocket integration for live price updates
- [ ] Machine learning price prediction models
- [ ] Sentiment analysis from financial news
- [ ] Multi-objective optimization (ESG scores, sector limits)
- [ ] Mobile app integration via REST API
- [ ] Backtesting engine with historical performance
- [ ] Transaction cost and tax optimization
- [ ] Portfolio stress testing and scenario analysis
- [ ] Integration with trading platforms (Zerodha, Upstox APIs)

### Enterprise Features (Roadmap):
- [ ] Multi-user portfolio tracking
- [ ] Cloud deployment (AWS/GCP/Azure)
- [ ] Real-time risk monitoring dashboard
- [ ] Automated rebalancing execution
- [ ] Regulatory reporting (SEBI compliance)

## 🏆 Project Achievements

- ✅ Successfully screened and analyzed 48 NSE stocks
- ✅ Implemented complete quantitative portfolio optimization pipeline
- ✅ Generated 10,000+ simulated portfolios for efficient frontier
- ✅ Created interactive visualizations for financial decision-making
- ✅ Built modular, scalable, and production-ready codebase
- ✅ Demonstrated real-time data fetching capabilities
- ✅ Applied industry-standard financial metrics and methodologies

---

**⭐ Star this repository if you found it helpful!**  
**🔔 Watch for updates and new features!**  
**🍴 Fork to customize for your own portfolio!**

---
