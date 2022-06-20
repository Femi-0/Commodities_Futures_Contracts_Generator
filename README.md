## Background

In this project, we build a tool that analyzes historical data and predicts prices to help commodities traders and investors determine the best trading strategies and make informed decisions. Also, it helps commodities traders and investors to ascertain what machine learning model will best predict. The project samples data of the top four metals, Gold, Silver, Platinum, and Palladium, for ten years obtained from Amark.com, Yahoo Finance and Federal Reserve Economic Data (FRED). This tool adapts extensively trained algorithmic trading, machine learning models, and natural language processing techniques for sentiment analysis, forecast momentum, and prices.

### Data Source

We download data as CSV files from Yahoo Finance and Federal Reserve Economic Data. These websites provide sufficient information on the four metals selected for this project. Next, we import relevant libraries, set functions, and variables.

### Prepare & Cleanup Reference Data 

Import CSV files and create dateframe. Filter the index and close columns, remove non-sum characters and correct the formatting. Use the percentage change function to generate returns from close prices and drop all null values from the dataframe.

### Generating Trading Signals
•	Short and long window Simple Moving Average (SMA) values – we generate the fast and slow simple moving averages. When actual returns are greater than or equal to 0, generate signal to buy stock long while when actual returns are less than 0, generate signal to sell stock short. We generate DMAC signal where 1 is when SMA Fast is less than the SMA Slow and 0 is when SMA Fast is greater than the SMA Slow. Using the DMAC signal, we calculate the points in time at which a position should be taken, 1 or -1.

•	Bollinger Bands – we generate the SMA, the upper-band and lower-band. When Close price is greater than or equal to 0, generate signal to buy stock long while when Close price is less than 0, generate signal to sell stock short.

•	Natural Language Processing - Use information on News API to perform NLTK sentiment analysis. We update and download VADER Lexicon. 

### Assess Signals Algorithm

https://docs.google.com/presentation/d/1ockfQjUo3ZwGYMgeEZbA42cQ1vNgXpskm-I82LjQy7A/edit?usp=sharing
