**Momentum Trading Strategy with 52-week high filter**

This project implements a momentum-based trading strategy screening stocks based on their 52-week high and executes trades using Python. It simulates a portfolio of stocks (constituent of Dow Jones 30), tracks portfolio value, calculates drawdowns, and visualises results with heatmaps and return distributions. The project leverages Yahoo Finance for historical stock data.

The trading strategy is underpinned by academic research on momentum strategies improved by closeness to 52-week high. 
George, T. J., & Hwang, C.-Y. (2004). The 52-week high and momentum investing. The Journal of Finance, 59(3), 2145-2176. Retrieved from
https://www.bauer.uh.edu/tgeorge/papers/gh4-paper.pdf

**How the model works in layman's terms**

The model identifies stocks that reached a new 52-week high and buys at the closing price (submitting an order at the closing auction).
The model will not hold two positions of the same ticker at one time. 

**Assumptions**

Trading commissions are 3 basis points

**Limitations**

Survivorship bias as the tickers used in the returns below are DOW constituents as of 1 December and not from the start date of the sample time period. 
Returns are gross and do not account for dividends and other corporate actions.

**Notes**

Acknowledging Generative AI was used extensively to write the Python code.

The period chosen is 5 year between June 2019 and June 2025. Period was selected to illustrate how the model has smaller drawdowns during market volatility around COVID in April 2020. This period was also chosen to show that the model largely holds cash when the index is performing poorly and this contributes to the models lower drawdowns, for example during 2022, a negative year for Dow Jones, the model held more cash. 


**Further research**

For this sample period, the portfolio returns are similar to the benchmark (Dow Jones Industrial Average Index), the model has a higher Sharpe ratio (risk adjusted return). Further development of the model might include testing with stocks from other country markets (DAX, Nikkei, so on), employing leverage, adjusting position sizing based on the number of index constituents at 52 week high as a signal for upward price momentum to continue 

Welcome your feedback or discussion 


**Features**

Momentum Strategy Logic: Buys stocks that break their 52-week high and holds them for a fixed period (default 15 days).

Portfolio Tracking: Tracks cash, invested capital, total portfolio value, and commissions daily.

Benchmark Comparison: Compares portfolio performance against the Dow Jones Industrial Average (DJI).

Drawdown Analysis: Calculates and reports the largest portfolio and benchmark drawdowns.

Visualisations:

Portfolio vs DJI line chart

Monthly returns heatmaps for portfolio and DJI

Distribution of trade returns histogram

Trade Reporting: Generates first/last 10 trades and monthly holdings, including stocks that could not be funded due to cash constraints.

Installation
git clone <repository-url>
cd <repository-folder>
pip install -r requirements.txt


**Required packages:**

pandas

numpy

yfinance

matplotlib

seaborn

scikit-learn

Usage
from momentum_strategy import momentum_52week_strategy

tickers = ["AAPL","AMGN","AXP","BA","CAT","CRM","CSCO","CVX","DIS","DOW","GS",
           "HD","HON","IBM","INTC","JNJ","JPM","KO","MCD","MMM","MRK","MSFT",
           "NKE","PFE","PG","RTX","TRV","UNH","V","VZ","WMT"]

trades, pv, open_positions, monthly_info, pv_first_of_month = momentum_52week_strategy(
    tickers,
    "2019-06-30",
    "2025-06-30"
)


trades: DataFrame of all executed trades

pv: Daily portfolio value

open_positions: List of currently held positions

monthly_info: Monthly portfolio summary

pv_first_of_month: Portfolio snapshot on the first trading day of each month

**License**

This project is released under the MIT License, which allows free use, modification, and distribution while requiring attribution to the original author.


**Visualisation**

The strategy produces three key visualizations:

Portfolio vs DJI Line Chart: Tracks total value of the portfolio against the Dow Jones index.

Monthly Returns Heatmap: Visualises monthly portfolio and DJI returns.

Distribution of Trade Returns: Shows the spread of individual trade returns.
