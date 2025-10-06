Final Project for supervised machine learning

Background:
Real estate market is growing fast. The house price in US keeps rising.
How macroeconomic indicators relate to US housing prices?
Whether we can predict future house prices using these factors?


Data:
I used data from the US market — things like GDP, CPI, disposable income, stock prices, population, unemployment, and mortgage rates — and use them to predict the House Price Index as the target.
http://kaggle.com/datasets/faryarmemon/usa-housing-market-factors/data?select=Monthly_Macroeconomic_Factors.csv


Data EDA:
Initially, the dataset looked complete, but then I discovered that the GDP column was actually annual percent change, not the real GDP level — which doesn’t make sense for prediction, since it can go negative.
So I replaced it with the Federal Reserve’s quarterly real GDP data and used linear interpolation to estimate monthly GDP.
Other most serious problem I met is the highly correlated data.


ML approach:
At first, I trained standard regression models including Linear Regression, KNN, Decision Tree, Random Forest, AdaBoost, Gradient Boost, and SVR.
With a random split, results looked great, most of them the R² values above 0.9.
But it was misleading, because random splitting leaks future data into the training set.

Since this is time-series data, I switched to a chronological train-test split, training on earlier years and testing on more recent data.


Result:
Time series train-test split, training on earlier years and testing on more recent data
Model performance dropped significantly
I switched to Lasso Regression, it drops redundant variable.

Before COVID, the model tracks the real house price quite well, Lasso regression's R² around 0.76.
But after COVID, even the best models can’t explain the price surge. Post-COVID house prices are driven by nontraditional factors outside macroeconomic factors.

