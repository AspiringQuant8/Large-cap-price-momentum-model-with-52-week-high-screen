**Momentum trading strategy with 52-week high filter**

This project implements a momentum-based trading strategy screening stocks based on their 52-week high. It simulates a portfolio of stocks (constituents of Dow Jones 30), tracks portfolio value, calculates drawdowns, and visualises results with heatmaps and return distributions. The project leverages Yahoo Finance for historical stock data.

The trading strategy is underpinned by academic research on momentum strategies improved by closeness to 52-week high. 

Reference to paper:
George, T. J., & Hwang, C.-Y. (2004). The 52-week high and momentum investing. The Journal of Finance, 59(3), 2145-2176. Retrieved from
https://www.bauer.uh.edu/tgeorge/papers/gh4-paper.pdf

**How the model works in layman's terms**

The model identifies stocks that reached a new 52-week high and buys at the closing price (submitting an order to fill in closing auction).
Stock that meet the criteria are held for 15 trading days. The model does not hold two positions of the same ticker at one time. 

**Assumptions**

Trading commissions are 3 basis points.

**Limitations**

Survivorship bias as the tickers used in the sample data are Dow Jones Industrial Average Index constituents as of 1 December 2025 and not from the start date of the sample time period. 
Returns are gross returns and do not account for dividends and other corporate actions.

**Notes**

Acknowledging generative AI was used extensively to write the Python code.

The period chosen is 5 year between June 2019 and June 2025. This period was selected to illustrate how the model has smaller drawdowns compared to the benchmark Dow Jones index during market declines - for example during the COVID-19 pandemic stock market volatility during March and April 2020. This period was also chosen to show that the model largely holds cash when the index is performing poorly, contributing to lower drawdowns. For example during 2022, a negative year for Dow Jones, the model held more cash. 

<img width="492" height="256" alt="Screenshot 2025-12-02 at 12 46 43" src="https://github.com/user-attachments/assets/7022ea5f-ac16-4938-a439-84c7753d8f22" />

<img width="925" height="437" alt="Screenshot 2025-12-02 at 12 46 26" src="https://github.com/user-attachments/assets/209ff2b0-cfda-4f4c-bb3b-2228665ef865" />


**Further research**

For this sample period, the portfolio returns are similar to the benchmark (Dow Jones Industrial Average Index), the model has a higher Sharpe ratio (risk adjusted return). Further development of the model might include testing with stocks from other country markets (DAX, Nikkei, so on), employing leverage, adjusting position sizing based on the number of index constituents at 52 week high as a signal for upward price momentum to continue.

Welcome your feedback and discussion 

**Dow Jones Industrial Average Index constituents as of 1 December 2025**

tickers = ["AAPL","AMGN","AXP","BA","CAT","CRM","CSCO","CVX","DIS","DOW","GS",
           "HD","HON","IBM","INTC","JNJ","JPM","KO","MCD","MMM","MRK","MSFT",
           "NKE","PFE","PG","RTX","TRV","UNH","V","VZ","WMT"]

**Back test period**

2019-06-30 to 2025-06-30


**Features**

Momentum Strategy Logic: Buys stocks that break their 52-week high and holds them for a fixed period (default 15 days).

Portfolio Tracking: Tracks cash, invested capital, total portfolio value, and commissions daily.

Benchmark Comparison: Compares portfolio performance against the Dow Jones Industrial Average (DJI).

Drawdown Analysis: Calculates and reports the largest portfolio and benchmark drawdowns.

**Visualisation**

The strategy produces three key visualisations:

Portfolio vs DJI Line Chart: Tracks total value of the portfolio against the Dow Jones index.

Monthly Returns Heatmap: Visualises monthly portfolio and DJI returns.

Distribution of Trade Returns: Shows the spread of individual trade returns.


**Installation**
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


**License**

This project is released under the MIT License, which allows free use, modification, and distribution while requiring attribution to the original author.

