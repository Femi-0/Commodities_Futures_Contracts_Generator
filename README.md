## Background

In this project, we build a tool that analyzes historical data and predicts prices to help commodities traders and investors determine the best trading strategies and make informed decisions. Also, it helps commodities traders and investors to ascertain what machine learning model will best predict. The project samples data of the top four metals, Gold, Silver, Platinum, and Palladium, for ten years obtained from Amark.com, Yahoo Finance and Federal Reserve Economic Data (FRED). This tool adapts extensively trained algorithmic trading, machine learning models, and natural language processing techniques for sentiment analysis, forecast momentum, and prices.

### Data Source

We download data as CSV files from Yahoo Finance and Federal Reserve Economic Data. These websites provide sufficient information on the four metals selected for this project. Next, we import relevant libraries, set functions, and variables.

### Prepare & Cleanup Reference Data 

Import CSV files and create dateframe. Filter the index and close columns, remove non-sum characters and correct the formatting. Use the percentage change function to generate returns from close prices and drop all null values from the dataframe.

### Algorithmic Trading Signals
 •  Short and long window Simple Moving Average (SMA) values – we generate the fast and slow simple moving averages. When actual returns are greater than or equal to 0, generate signal to buy stock long while when actual returns are less than 0, generate signal to sell stock short. We generate DMAC signal where 1 is when SMA Fast is less than the SMA Slow and 0 is when SMA Fast is greater than the SMA Slow. Using the Dual Moving Average Crossover (DMAC) signal, we calculate the points in time at which a position should be taken, 1 or -1.

•	 Bollinger Bands – we use Bollinger bands to determine when to buy, sell or hold position. Generate the SMA, the upper-band and lower-band. When Close price is greater than or equal to 0, generate signal to buy stock long while when Close price is less than 0, generate signal to sell stock short.

•	 Natural Language Processing - Use information on News API to perform NLTK sentiment analysis. We update and download VADER Lexicon. 

### Assess Signals Algorithm

We evaluate the trade algorithm and include trade costs. Calculate after transaction cost on returns. We generate the annualized sharpe ratios to show performance between risk and return.

### Apply Machine Learning Methods

We preprocess signals dateframe for SMA Long and Short Windows, Bollinger Bands and NLP.

•	 SMA Long and Short Windows – We prepare and cleanup the dataframe. Create features and set targets. Sort data in ascending order then split the data into train,        test. We select the start and end of the training period with an offset of 3 months. Also same is repeated for the DMAC training period.

   We generate the X train and Y train dataframes. Then generate the X test and Y test dataframes. We create a StandardScaler instance, then apply the scaler model to    fit the X-train data. Furthermore, transform th X train and X test dataframes using the X scaler.

•	 Bollinger Bands – Above is replicated.

•	 NLP - 


https://docs.google.com/presentation/d/1ockfQjUo3ZwGYMgeEZbA42cQ1vNgXpskm-I82LjQy7A/edit?usp=sharing
