# Python Project for Data Science

**Course description**: In this mini-course you will be assuming the role of a Data Scientist / Data Analyst. In this role you will be given a scenario and data to begin your Python project. During this process you will perform specific tasks such as extracting data, web scraping, visualizing data, and creating a dashboard.

---

## 💼 Project Overview: [An Analysis of Tesla and Gamestop Stock Data]()

### 🟦 Project Materials

* [Completed IBM Lab Jupyter Notebook]()
* [Visualizations]()

### 🟦 Introduction

For this project, you will assume the role of a Data Scientist / Data Analyst working for a new startup investment firm that helps customers invest their money in stocks. Your job is to extract financial data like historical share price and quarterly revenue reportings from various sources using Python libraries and webscraping on popular stocks. After collecting this data you will visualize it in a dashboard to identify patterns or trends. The stocks we will work with are Tesla, Amazon, AMD, and GameStop.

#### Useful Word Definitions:

  * **Stock**: a security that represents the ownership of a fraction of a corporation
  * **Shares**: a unit of stock
  * **Investor**: someone who buys and sells stocks for profit
  * **Stock ticker**: a report of the price of a certain stock

### 🟦 Data Collection Using APIs

#### 1. Import the necessary libraries and modules
```
import yfinance as yf
import pandas as pd
import plotly.graph_objects as go
import requests
from bs4 import BeautifulSoup
from plotly.subplots import make_subplots
```

#### 2. Create yfinance ticker objects for Tesla and Gamestop stocks
```
tesla = yf.Ticker("TSLA")

gamestop = yf.Ticker("GME")
```

#### 3. Extract the stock information and save it as a dataframe 
```
tesla_data = tesla.history(period="max")

gamestop_data = gamestop.history(period="max")
```

#### 4. Reset the index of both dataframes and display the first five rows
```
tesla_data.reset_index(inplace=True)

gamestop_data.reset_index(inplace=True)
```

  * Display first five rows of ```tesla_data``` DataFrame
```
tesla_data.head(5)
```
<img src="" width="1100">
