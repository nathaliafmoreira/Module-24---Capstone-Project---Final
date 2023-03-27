# Module-24---Capstone-Project---Final

### Ibovespa Forecast

**Nathalia Moreira**

#### 1. Executive summary

The objective of this project will be to predict the value of the Ibovespa index. This index is followed by the main financial institutions in the country and is the thermometer of the Brazilian economy. It is composed of around 90 companies, to be part of the index companies must meet certain criteria, thus the index composition is periodically reviewed by the stock exchange (B3). Each company has a weight in the index related to its market cap, according to data released by B3 in March/2023, the companies with the greatest weight in the index are Vale, Itaú and Petrobras. The combination of the price of the shares that make up the index and the respective weight of each company, results in a value in points for the Ibovespa.

The graph below shows the evolution of the IBOVESPA index in recent years:

![image](https://user-images.githubusercontent.com/116108563/228059606-2a5641fc-5e75-41e2-bd3e-8a3c51fd8241.png)

In the graph above we can see that we have two points that deserve to be highlighted:

- In 2016, Brazil faced a year of political instability resulting in the impeachment of the president who was in government. This period was one of great volatility on the stock exchange due to market uncertainty.

- In the year 2020, with the explosion of cases of covid 19, the stock exchange had to trigger the circuit breaker 6 times in a period of 8 trading sessions. This procedure interrupts the trading of assets on the stock exchange at unusual market times. It is not possible to carry out trades on the exchange during this period.

From the graph we can also see that there is a growing trend, so this time series is clearly not stationary.


#### 2. Rationale

The projection of some indices (Nasdaq, Dow Jones, S&P 500, etc) created by the stock exchanges, it is important for investment analysts to decide on the investment in a country and for the stock exchanges themselves for the purpose of budgetary projections and planning.

#### 3. Research Question

The main objective of the project is to predict the IBOVESPA index, of the stock exchange (B3) in the short and long term: to know how many "points" the index will have at the close of the next day (short term) and how many points the index will have in a period of approximately one year ahead

#### 4. Data Sources

To obtain historical data, it was initially planned to consult B3's own website, but historical information is better structured on the Yahoo Finance website. The period from Jan/11 to Feb/2023 was used.

Ibovespa Historical Data:

https://finance.yahoo.com/quote/%5EBVSP/history?period1=1294012800&period2=1677542400&interval=1d&filter=history&frequency=1d&includeAdjustedClose=true

To complement the analysis, GDP, foreign investment and interest rate data obtained from The World Bank were used.
These data were extracted by API and correspond to the period from 2011 to 2021 (last year available for the indicators).

Annual macroeconomic data for Brazil:

https://databank.worldbank.org/reports.aspx?source=2&series=NY.GDP.MKTP.KD.ZG&country=BRA#


#### 5. Methodology

As the dataset used is a time series, some techniques will be applied to project Ibovespa:
- Model 1 - Forecast with Decomposition Models: using STLForecast with ARIMA Model.
- Model 2 - ARIMA Model (using autoARIMA)
- Model 3 - Decision Tree
- Model 4 - LSTM (Univariate time series)
- Model 5 - LSTM (Multivariate time series)


#### 6. Results
What did your research find?

| Evaluation Metric | Model 1      | Model 2      | Model 3      | Model 4      | Model 5       |
| ----------------- | -------------| -------------| -------------| -------------| ------------- |
| MAE               | 9804.08      | 6307.40      | 1197.43      | 2168.88      | 1344.52       |
| RMSE              | 12380.87     | 7229.78      | 3383.60      | 2631.31      | 1989.30       |
| MAPE              | 9.08%        | 5.65%        | 1.09 %       | 1.94%        | 1.34%         |


#### 7. Recommendations

#### 8. Next Steps


#### Outline of project

- [Link to notebook]()

##### Contact and Further Information
nathaliafmoreira@gmail.com
