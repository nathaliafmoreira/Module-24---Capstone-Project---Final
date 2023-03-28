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

The projection of stock indices such as Nasdaq, Dow Jones, S&P 500, and in the case of Brazil the Ibovespa, is an important driver for different participants in the stock market.
From the point of view of Stock Brokers, Investment Banks, Buy Side and international investors, the variation of these indices in the short and long term directs investment strategies in search of the best risk x return relationship.
From the perspective of the stock exchange, in the case of Brazil, we have only one company responsible for the capital market infrastructure, which provides trading services in an exchange and OTC environment, the prediction of the index with the main companies traded on the exchange allows the company to be prepared in the long term for projection of transaction capacity, the higher the index, the greater the number of negotiations and for budget and strategic planning, given that the company's revenue is linked to trading on the stock exchange environment. In the short term, in atypical moments, it anticipates warnings to the market about possible volatilities and in extreme cases it prepares the systems and teams for Circuit Breaker cases, for example.

#### 3. Research Question

The main objective of the project is to predict the IBOVESPA index, of the stock exchange (B3) in the short and long term: to know how many "points" the index will have at the close of the next day (short term) and how many points the index will have in a period of approximately one year ahead.
Short-term and long-term projections are used differently, but are equally important to all parties involved. Despite knowing that the longer the term, the greater the chances of the index suffering abrupt variations due to adverse effects, such as the pandemic, political scenario, crises in specific sectors, international economic scenario with flight of investors to more attractive markets.

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

To measure the performance of the models, the metrics: MAE(Mean Absolute Error), RMSE (root mean squared error) and MAPE (Mean absolute percentage error) were applied.
Basically, the MAE is the average of the difference between the projected value and the realized value, without considering whether this difference is positive or negative, so all differences have the same weight. The MAPE is how much the MAE represents of the total actual values, how much we are wrong in percentage.
RMSE is also an error measure, but unlike the others, it gives more weight to outliers.


| Evaluation Metric | Model 1      | Model 2      | Model 3      | Model 4      | Model 5       |
| ----------------- | -------------| -------------| -------------| -------------| ------------- |
| MAE               | 9804.08      | 6307.40      | 1197.43      | 2168.88      | 1344.52       |
| RMSE              | 12380.87     | 7229.78      | 3383.60      | 2631.31      | 1989.30       |
| MAPE              | 9.08%        | 5.65%        | 1.09 %       | 1.94%        | 1.34%         |

For all metrics, the smaller the value, the better the model.
All models had a MAPE below 10%, so they are considered models with good performance, but it is always necessary to pay attention to the use of the model, because some situations require greater precision.

Evaluating the metrics for the 5 models, we found that the models that presented the best performance were models 03 and 05. However, model 03 presented the highest RMSE, which indicates that it has more errors of greater magnitude (outliers). Thus, considering the three metrics, the model that performed best was model 05, which is the model to which the variables of GDP, Interest Rate and Foreign Investment were added to the time series. Model 05, in a macro way, is based on the last 10 days to project the next day.


#### 7. Recommendations

Based on the observed results, we can conclude that:
- Long-term projections are less accurate
- Short-term projections are more accurate

Predicting an index composed of shares of several companies over a very long period of time can serve to guide strategic planning and for longer-term budgeting purposes. Given that for these purposes it is not necessary to have an exact index quotation number.
For this purpose, my recommendation is to use models 01 and 02 that use the ARIMA method, since the decision tree model (model 03) needs very long series to project long periods.
If it is necessary to project the index for a year from now, I recommend that the model be retrained every quarter, including the most recent periods for monitoring and route adjustment if necessary.

For short-term forecasts, for example, knowing whether the stock market will go up or down the next day, the more accurate the better the model, because based on that, individual investors, investment banks, brokers, funds, define their application strategies to get better return. In this case, my recommendation would be to use model 04, which has a smaller error for short-term projections.

#### 8. Next Steps

Some improvements could be integrated to increase the quality of the projections of the analyzed models.
For example:
- Depending on the use, carry out the individual projection of the stocks and not the index as a whole, because this better directs investment decision-making.
- Evaluate other variables that help explain the behavior of the index, such as political instability, quarterly GDP data released by the Central Bank of the Country, among others.
- In the case of the decision tree, work with a shorter projection period to actually be able to evaluate the performance of the out-of-sample model.
- Test the models with other hyperparameters.

#### Outline of project

- [Link to notebook]()

##### Contact and Further Information
nathaliafmoreira@gmail.com
