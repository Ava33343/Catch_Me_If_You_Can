# Slippery Whales
## _A Whale Off the Port(folio)_

![Portfolio Analysis](Images/portfolio-analysis.png)

## Background

The investment division of Harold's company has been investing in algorithmic trading strategies. Some of the investment managers love them, some hate them, but they all think their way is best.

You just learned these quantitative analysis techniques with Python and Pandas, so Harold has come to you with a challenge—to help him determine which portfolio is performing the best across many areas: volatility, returns, risk, and Sharpe ratios.

A tool (an analysis notebook) is created to analyze and visualize the major metrics of the portfolios across all of these areas, and determine which portfolio outperformed the others. You will be given the historical daily returns of several portfolios: some from the firm's algorithmic portfolios, some that represent the portfolios of famous "whale" investors like Warren Buffett, and some from the big hedge and mutual funds. You will then use this analysis to create a custom portfolio of stocks and compare its performance to that of the other portfolios, as well as the larger market (S&P 500).

In this homework assignment, you will be accomplishing three main tasks:

1. [Read in and Wrangle Returns Data](#Prepare-the-Data)
2. [Determine Success of Each Portfolio](#Conduct-Quantitative-Analysis)
3. [Choose and Evaluate a Custom Portfolio](#Create-Custom-Portfolio)

---

### Prepare the Data

First, read and clean several CSV files for analysis. The CSV files include whale portfolio returns, algorithmic trading portfolio returns, and S&P 500 historical prices. 

1. Use Pandas to read in each of the [CSV files](Code_and_Resources) as a DataFrame. Be sure to convert the dates to a `DateTimeIndex`.

2. Detect and remove null values.

3. Remove dollar signs from the numeric values and convert the data types as needed.

4. The whale portfolios and algorithmic portfolio CSV files contain daily returns, but the S&P 500 CSV file contains closing prices. Convert the S&P 500 closing prices to daily returns.

5. Join `Whale Returns`, `Algorithmic Returns`, and the `S&P 500 Returns` into a single DataFrame with columns for each portfolio's returns.

  ![returns-dataframe.png](Images/returns-dataframe.png)

### Conduct Quantitative Analysis

#### Performance Analysis

Based on Figure A1, Tiger Global Management LLC and Berkshire Hathaway Inc exhibited most volatile behavior in daily returns. Comparable volatilities to S&P 500 are provided by Paulson & Co. Inc., Algo 1, Algo 2 and Soros Fund Management LLC. The daily returns of all portfolios are positively correlated.

Examples of exceptions are Tiger Global Management LLC's sudden rise in daily returns during the first quarter of 2017 and its sharp dip towards the end of the first quarter in 2019.

Based on Figure A2, the plot for cumulative daily returns, Paulson & Co. Inc. from Whale Portfolio had the lowest cumulative return. The highest cumulative return was gained by Algo 2 from Algo Portfolio. S&P 500 ranks the third highest return by the end of April 2019.

Algo 1 and Berkshire Hathaway Inc outperforms S&P 500 by the end of 2019. The best performance measured by cumulative returns was Algo 1. S&P 500 underperforms Algo 1 portfolio in three out of the four years. 2018 was the only year that S&P 500 outperforms Algo 1 by 0.1 approximately in cumulative returns.

Algo 2 strategy returned slightly lower than that of S&P 500 thoughout the four year window, with the gap widening starting from the second half of 2018. It is followed by Soros Fund Management LLC and Tiger Global Management LLC. Cumulative returns gaps increased for both following a dip prior to the start of 2019. Paulson & Co. Inc. demonstrated decreasing cumulative returns during the entire time frame. 

When made of equally weighted investment components of their kind, the Algo Portfolio is our top choice.

From Figure A3 and A4 above for daily and cumulative returns for weighted portfolios vs. S&P 500, Algo Portfolio consisted of equally weighted Algo 1 and Algo 2 strategies outperforms the market indicated by cumulative returns of S&P 500 portfolio stocks. The portfolio of whale investors and management funds, however, returned close to the market up until the last quarter of 2016. The gap in returns widened continuously into 2019.

the cumulative returns ranking from the highest to the lowest are: Algo, S&P 500 and Whale Portfolio, respectively.

The chart on daily returns shows greatest volatility in the market, represented by S&P 500. Algo Portfolio demonstrate the most modest risk. Portfolio composed of equally weighted whales investments shows volatility in beween the two.

In conclusion, Algo Portfolio is the safest bet amongst the three.

#### Risk Analysis

To start off, box plots for each portfolio are compared to others in the same domain. The three domains are whale investors, algos and S&P 500.

Tiger Gloabl Management LLC manifested the greatest risk in its portfolios, shown by the spread of daily returns.

Figure B1 shows the distribution in daily returns of strategies adopted by whale investors and their managed funds, in the form of box plots.

Paulson & Co. Inc. exhibit least spread in its daily returns, followed by Soros Fund Management LLC. Berkshire Hathaway Inc ranked the second most volatile of the four.

In Figure B2, we can conclude that the middle 50% of the daily returns for Algo 2 strategy is more spread out. To the contrary, the daily returns for Algo 1 is more widely spread out compared to provided by Algo 2 strategy.

Figure B3 tells us that the range of middle half of market daily returns is slighly less than 0.01, based on S&P 500.

The more spreadout the daily returns, the riskier the portfolio.

Based on the box plots in Figure B5, the Inter-quartile ranges (IQR = Q3-Q1) is the least (least volatile) for PAULSON & CO. INC., Algo 1, S&P 500, and SOROS FUND MANAGEMENT LLC. It suggests the middle half of the daily returns for those management strategies are less spreadout, i.e. less risky.

Meanwhile, the spread of daily returns is the most closely packed for PAULSON & CO. INC., suggesting that it is the least riskly out of the seven portfolios. Nevertheless, this alone does not guarantee a safer bet as rewards are not taken into account yet. We will look into details of sharpe ratios in later sections.

Portfolios that have daily returns more widely spread out than market S&P 500 are: BERKSHIRE HATHAWAY INC, TIGER GLOBAL MANAGEMENT LLC, and Algo 2. The conclusion is reinforced by their standard deviations, of 0.0128, 0.0108 and 0.0084, respectively. All three of them are higher than that of the 0.0081 for S&P 500 during the same timeframe.

As proven by the numbers, the standard deviation of Algo Portfolio is 0.00675. It is the least among the three portfolios. The most risky one is S&P 500 Portfolio. Its standard deviation on daily returns is 0.00811. The Whale Portfolio has risk in the middle while closer to that of the S&P 500 Index Portfolio.

According to annualized standard deviations, the conclusion is consistent with those of the box plots and standard deviation of daily returns. Portfolios of Algo 2, Tiger Global Management LLC and Berkshire Hathaway Inc are more risky compared to S&P 500 Portfolio.

If weighted equally among the portfolios of their types, S&P 500 Portfolio is the most risky of the three. Algo Portfolio is the safest and least volatile. Whale Portfolio has risk close to S&P 500 while remaining in the middle of the three.

#### Rolling Statistics

Higher standard deviation suggest greater variation in daily returns. It is associated with higher risks. A rolling 21-day standard deviation smoothes out the daily standard deviation plot, making it easier to identify trends.

Plots on rolling 21-day standard deviations of the market and portfolios in Figure C1 and C2 suggests higher-than-market risks for Tiger Global Management LLC and Berkshire Hathaway Inc. The risk for Algo 1 strategy was seeing higher than the rest more often starting from the fourth quarter of 2018.

Based on the correlation chart and heatmap, all portfolios are positively correlated with S&P 500. Algo 2 portfolio most closely mimic the movement of S&P 500, given its 0.859 correlation. It is followed by Soros Fund Management LLC and Berkshire Hathaway Inc. with S&P 500 correlations of 0.838 and 0.751 respectively. On the other hand, Algo 1 least tracks S&P 500, provided that it has correlation of 0.279. Paulson & Co. Inc. and Tiger Global Management LLC both have correlations greater than 0.6 with S&P 500 Index.

In Figure C4. above, Algo 2 is sensitive to movements of S&P 500 as its beta is wavering around 1 that is the beta for S&P 500. It is moving in the same direction with S&P movements. On maximum, it reacts 1.8 times to S&P 500 movement. To the contrary, it could move as litte as between a half to two thirds of the size of movements in S&P 500. However, on average, it does not appear to be overly or less responsive to movements of S&P 500 in the given time span.

According to Figure C6, the 60-day rolling beta measures sensitivity of the stock price Berkshire Hathaway Inc. relative to movements of S&P 500 market index. It moves in concert with S&_ 500 in the same directions and approximately the same average sale in sensitivity. As show in the graph, the two-month rolling beta ranges from as low as 0.6 around March 2017 to its peak near 1.9 close to October 2018. In the chart, it started around 0.7 from July 2015, followed by an increase to 1.4 in April 2016. It peaked close to 1.8 twice in July and December 2017, preceded by gradual declines, as previously mentioned, to its minimum towards the end of 2018. The market sensitivity falls close to 0.8 in July 2018. Then, it rose by 1 to its peak, i.e. most sensitive moment at the end of 2018. A gradual decline by 0.5 was seen in the first quarter of 2019.

According to Figure C7 and C8, returns of Tiger Global Management LLC and Berkshire Hathaway Inc were more volatile, in other words, riskier than the market index, S&P 500.

Based on heatmap and correlation table above, returns of portfolios and S&P 500 are highly correlated. Algo 2 exhibit maximum correlation with S&P 500, namely 99.6% of its returns can be explained by that of S&P 500 . On the other hand, 90.6% of Paulson & Co. Inc's daily prices can be explained by S&P 500. It is the least correlated with S&P 500.

Figure C9 shows that Algo 2 portfolio has nearly the same sensitivity to price movement of S&P 500. It is because its exponentially weighted beta is close to 1, the index base. Meanwhile, its average appears to be below 1, indicating that Algo 2 is relatively less sensitive to price movements of S&P 500.

From the overlaying chart Figure C10, above, we can see that the both EMAs and SMAs indicate that Algo 2 price movements closely traces those of S&P 500. The EMAs have a higher correlation than SMAs as more closing prices agrees with each other based on movement in the same direction and similar magnitude. The range of 21-day EMAs exceed that of the SMAs over the same period of time because it weighs recent price movements more heavily. In comparison, SMAs averages out price movement over the specified 21 days.

Exponentially weighted daily returns and standard deviations, shown in Figure C11 and C12 above, reinforce our conclusion that the portfolios of Tiger Global Management LLC and Berkshire Hathaway are riskier than S&P 500. In addition, Soros Fund Management LLC also adopts a riskier portfolio, compared to the market S&P 500.

The correlation table and heatmap indicate a higher correlation between portfolio returns of Berkshire Hathaway Inc and Algo 1, Algo2, and S&P 500. It has a relatively lower correlation with Soros Fund Management LLC and Paulson & Co. Inc. The correlation between 60-day rolling portfolio return of Berkshire Hathaway and S&P 500 is 0.974. It shows tha 97.4% of the movement in exponentially weighted 60-day rolling returns can be explained by returns movement of S&P 500 during the same time period. In comparison, according to 60-day rolling SMA portfolio returns, only 0.751, i.e. 75.1% of the daily returns can be explained by movement in S&P 500 on the same rolling basis. 

Based on exponentially weighted 60-day rolling beta in Figure C13, Berkshire Hathaway Inc. has its stock price moving slightly more sentivite compared to movement in S&P 500, in the same direction. On average, it is 25% more sensitive to market movements captured by S&P 500."

From the chart above, Figure C14, we can see that the 60-day exponential moving averages of Berkshire Hathaway Inc react in greater magnitude and same direction compared to returns of S&P 500, indicating a beta greater than 1. As suggested by 60-day simple moving averages of Berkshire Hathaway Inc, the company price move in the same direction as S&P 500. However, it demonstrate a smoother sensitivity because price changes further back were weighed the same as those that are closer to date, diluting the price sensitivity to movements of S&P 500.

### Plot Sharpe Ratios

According to the bar charts in Figure C15, Algo 1 strategy outperform returns of the market index, S&P 500, and the whales. It is becuase its sharpe ratio is 1.25, the highest amongst all seven portfolios, meaning that it gives the greatest return per unit of risk. Algo 2 strategy falls below returns of S&P 500 and Berkshire Hathaway Inc by 0.15 and 0.12 in return per unit of risk, respectively. It still beats Soros Fund Management LLC, Tiger Global Management LLC and Paulson & Co. Inc. The last couple returns negative annualized sharpe ratios.


### Comparison with 21-Day Exponential Moving Averages

On the same chart, the exponential moving averages (EMA) appear more volatile than simple moving averages. Illustrated in Figure D7, it is because exponents were used in calculation and magnifies changes in returns. We can see that the 21-day rolling returns of DIY portfolio act in concert with those of S&P 500, demonstrated both by SMAs and EMAs. While EMAs emphasize more recent returns, it draws rolling correlation between DIY portfolio and S&P500 closer compared to those represented by SMAs. The heatmap on correlation between EMAs appears to have a paler color compared to the SMA correlation heatmap, suggesting higher correlation between portfolio returns. 

To select a portfolio based on data from 12/2014 to 1/2020 Based on annualized standard deviation, Berkshire Hathaway Inc. needs to be dropped as it was the riskiest and most volatile. Algo 2 and Soros Fund Management LLC have high correlations. Thus, they need to be excluded from the portfolio. Paulso & Co. Inc. has a negative sharpe ratio and needs to be excluded. 

### Create Custom Portfolio

_**Screener on finviz.com**_

Descriptive(6): Market Cap. "Large ($10bln to $20bln)" Target Price "5% Above Price" Divident Yield "Positive (>0%)" Average Volume "Over 100K" IPO Date "More than 5 years ago" Current Volume "Over 100K"

Fundamental(4): PE "Under 30", Debt/Equity "Under 1", Operating Margin "Over 5%", Net Profit Margin "Positive (>0%);

Technical(7): 20-Day Simple Moving Average "Price above SMA20" Beta "Under 1.5" 50-Day Simple Moving Average "SMA50 below SMA20" 200-Day Simple Moving Average "SMA200 below SMA50" 52-Week High/Low "New High" RSI(14) "Not Oversold (>50)" Pattern "TL Resistance"

Narrowed down to seven stocks: AJG (Financial), CFG (Financial), CI (Healthcare), ETN (Industrial Goods), ICE (Financial), LHX (Technology), RCL (Services)

Looking at charts Out of the three financial stocks: AJG, CFG and ICE, CFG stays in the portfolio for higher trading volume supporting the price break out. Wave theory suggests that a peak can be formed following breaking out at $40.

Stocks remaining in the portfolio are: CFG (Financial), CI (Healthcare), ETN (Industrial Goods), LHX (Technology), RCL (Services)

Due to limit in resources and management challenges, considering volume, sectors, diversification and season, three stocks stays in the portfolio: CFG, ETN, LHX.

---

Alternatively,

"Harold is ecstatic that you were able to help him prove that the algorithmic trading portfolios are doing so well compared to the market and whales portfolios. However, now you are wondering whether you can choose your own portfolio that performs just as well as the algorithmic portfolios. Investigate by doing the following:

1. Visit [Google Sheets](https://docs.google.com/spreadsheets/) and use the in-built Google Finance function to choose 3-5 stocks for your own portfolio.

2. Download the data as CSV files and calculate the portfolio returns.

3. Add your portfolio returns to the DataFrame with the other portfolios and rerun the analysis. How does your portfolio fair?"

---

## Conclusion

In conclusion, the Optimized Portpolio provides highest return with less risk.

According to Exponentially Weighted Rolling 21-Day Cumulative Returns of Portfolios vs. S&P 500, Figure E4, the Optimized Portfolio consisting of equally weighted DIY, Tiger Global Management LLC, Algo 1 and S&P 500 portfolios has the highest return, followed by S&P 500, all-inclusive portfolio and the DIY portfolio consisted of euqally weighted CFG, ETN, LHX.

The volatility of the S&P 500 is highest, followed by DIY, all-inclusive and finally the Optimized portfolio, as shown in Figure E5. The least risky is the DIY portfolio consisted of equally weighted CFG, ETN and LHX.

Therefore, the screening strategy of dropping stocks with highest volatility, correlation and negative beta is effective.


**File:** [Whale Analysis](Code_and_Resources/whale_analysis.ipynb)

---

## Resources

[Pandas API Docs](https://pandas.pydata.org/pandas-docs/stable/reference/index.html)

---

## Hints

* After reading each CSV file, don't forget to sort each DataFrame in ascending order by the Date using `sort_index`. This is especially important when working with time series data as we want to make sure Date indexes go from earliest to latest.

* The Pandas functions used in class this week will be useful for this assignment.

* Be sure to use `head()` or `tail()` when you want to look at your data but don't want to print to a large DataFrame.

---

## References

CU Fintech Bootcamp Repository retrieved at https://columbia.bootcampcontent.com/columbia-bootcamp/CU-NYC-FIN-PT-12-2019-U-C
https://stackoverflow.com/questions/55578739/how-to-reset-index-of-multiple-pandas-dataframes-using-a-loop-in-python
https://stackoverflow.com/questions/29310116/removing-time-from-datetime-variable-in-pandas
https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.reset_index.html
https://support.google.com/docs/answer/3093281?hl=en
https://finviz.com/map.ashx
https://www.youtube.com/watch?v=bWpe30R2VnM
https://www.youtube.com/watch?v=Bvaz9y5UP3M&t=2s
https://www.intelligenttrendfollower.com/
http://www.intelligenttrendfollower.com/wp-content/uploads/2018/09/ITF-Trend-Following-Mini-Course.pdf
https://www.youtube.com/watch?v=lkM2CY2jk-Y&t=199s
https://www.youtube.com/watch?v=cGSQNrY3g4U
https://www.youtube.com/watch?v=N-NPaB-T-QY
