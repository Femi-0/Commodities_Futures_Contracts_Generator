## Background

In this project, we build a tool that analyzes historical data and predicts prices to help commodities traders and investors determine the best trading strategies and make informed decisions. Also, it helps commodities traders and investors to ascertain what machine learning model will best predict. The project samples data of the top four metals, Gold, Silver, Platinum, and Palladium, for ten years obtained from Amark.com, Yahoo Finance and Federal Reserve Economic Data (FRED). This tool adapts extensively trained algorithmic trading, machine learning models, and natural language processing techniques for sentiment analysis, forecast momentum, and prices.

### Data Source

We download data as CSV files from Amark.com, Yahoo Finance and Federal Reserve Economic Data. These websites provide sufficient information on the four metals selected for this project. Next, we import relevant libraries, set functions, and variables.

### Prepare & Cleanup Reference Data 

Import CSV files and create dateframe. Filter the index and close columns, remove non-sum characters and correct the formatting. Use the percentage change function to generate returns from close prices and drop all null values from the dataframe.

### Algorithmic Trading Signals

We will use Short and Long Window Simple Moving Average, Bollinger Bands and Natural Language Processing.

* Short and Long Window Simple Moving Average (SMA) values – we generate the fast and slow simple moving averages. When actual returns are greater than or equal to 0, generate signal to buy stock long while when actual returns are less than 0, generate signal to sell stock short. We generate DMAC signal where 1 is when SMA Fast is less than the SMA Slow and 0 is when SMA Fast is greater than the SMA Slow. Using the Dual Moving Average Crossover (DMAC) signal, we calculate the points in time at which a position should be taken, 1 or -1.

* Bollinger Bands – we use Bollinger bands to determine when to buy, sell or hold position. Generate the SMA, the upper-band and lower-band. When Close price is greater than or equal to 0, generate signal to buy stock long while when Close price is less than 0, generate signal to sell stock short.

* Natural Language Processing - Use information on News API to perform NLTK sentiment analysis. We update and download VADER Lexicon sentiment analyzer. 

### Assess Signals Algorithm

We evaluate the trade algorithm and include trade costs. Calculate after transaction cost on returns. We generate the annualized sharpe ratios to show performance between risk and return.

### Apply Machine Learning Methods

We preprocess signals dateframe for SMA Long and Short Windows, Bollinger Bands and NLP.

* SMA Long and Short Windows – We prepare and cleanup the dataframe. Create features and set targets. Sort data in ascending order then split the data into train,        test. We select the start and end of the training period with an offset of 3 months. Also same is repeated for the DMAC training period.

   We generate the X train and Y train dataframes. Then generate the X test and Y test dataframes. We create a StandardScaler instance, then apply the scaler model to    fit the X-train data. Furthermore, transform th X train and X test dataframes using the X scaler.

* Bollinger Bands – Above is replicated.

* NLP - Use information on News API to perform NLTK sentiment analysis. We update and download VADER Lexicon sentiment analyzer. Then fetch news on Gold, Silver,        Platinum and Palladium, sorting by relevance and maintaining a page size of 100. We set up sentiment variables then create the sentiment score for each metal.

*SVC and XGBoost for prediction – We apply these two machine learning algorithm to confirm which will give a better return.

#### Apply SVC for prediction

We create the classifier model, fit the model to the data using X train scaled and Y train. Then use the trained model to predict the trading signals for the training data. We create training report, create report dataframe then add the SVM model predictions to the dataframe. We add the actual returns to the dataframe and add the strategy returns to the dataframe. We then return the model, predictions and training report.

#### Apply XGBoost for prediction

Replicate above steps as it applies to XGBoost.

## Findings

* Due to historical market performance, the imbalanced dataset skewed towards “hold” instead of buy/sell making the Machine Learning prediction methods unreliable.

* Each metal has its own volatility, as a result each metal may have its own key metrics that have not been identified in our current dataset.

* Providing financial advice based on the dataset used is not recommended as additional long-term data will be required to assist the model in predictions.

## Shortcomings

* Finding a news API that can provide historical data at no cost.


* Our attempt to use website scraper on news websites with no API was unsuccessful. We will explore this in future projects.


* When using NLP, we were getting articles regarding Gold Medals like the Olympics or a new Platinum record which wasn’t quite relevant to the data we needed.


## Considerations for future project

* To use a User Interface for a real-life user experience.

* Explore more news websites to be used for NLP.






https://docs.google.com/presentation/d/1ockfQjUo3ZwGYMgeEZbA42cQ1vNgXpskm-I82LjQy7A/edit?usp=sharing
