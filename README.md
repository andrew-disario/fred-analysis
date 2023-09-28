<h1>Analyze the S&P 500 with FRED, Python, Pandas and Matplotlib</h1>
<p align="center">
<img src="https://github.com/andrew-disario/sp-500/blob/main/SP500.png?raw=true" height="75%" width="75%" alt="sp500"/>
<br />
In this project, we use the Federal Reserve of Economic Data website, Python, Pandas and Matplotlib to analyze the S&P 500.

<h2>Part I - Connect to FRED</h2>

<b> Obtain a FRED API Key </b>
1. Go to [fredaccount.stlouisfed.org/apikey](https://fredaccount.stlouisfed.org/apikey) and select **API Keys**.
2. Select **Request or view your API Keys**.
   - You will have to log in to FRED or create an account if you don't already have one.
3. Provide a description of the reason you are requesting an API key.
4. Check mark the **Terms of Use** box and select **Request API Key**.

<b> Pull FRED Data into Python</b>
1. Import libraries including ```Fred``` from ```fredapi```.
   - You can install ```fredapi``` by running ```!pip install fredapi```.
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import plotly.express as px
from fredapi import Fred
```
2. Set up plot style, Pandas parameters and color palette,
```
plt.style.use('fivethirtyeight')
pd.set_option('max_columns', 500)
color_pal = plt.rcParams["axes.prop_cycle"].by_key()["color"]
```
3. Set up Fred key
```
fred_key = '[ENTER YOUR API KEY HERE]'
```
4. Create the Fred object
```
fred = Fred(api_key = fred_key)
```
5. Use ```fred.search()``` and output results to dataframe
```
sp_search = fred.search('S&P', order_by = 'popularity')

sp_search
```
<p align="center">
<img src="https://github.com/andrew-disario/sp-500/blob/main/sp_search.png?raw=true" height="50%" width="50%" alt="spsearch"/>
<br />
<h2>Part II - Plot Data Using Pandas and Matplotlib</h2>

<b> Pull S&P 500 Data from Fred </b>
1. Use ```fred.get_series()``` to pull data with series id "SP500" and output results to dataframe
```
sp500 = fred.get_series('SP500')
```
2. Use ```.plot()``` to plot data
```
sp500.plot()
```
3. Adjust figure size, line width and give title "S&P 500"
```
sp500.plot(figsize=(10, 5), title='S&P 500', lw=2)
```
<p align="center">
<img src="https://github.com/andrew-disario/sp-500/blob/main/SP500.png?raw=true" height="50%" width="50%" alt="sp500"/>
<br />
