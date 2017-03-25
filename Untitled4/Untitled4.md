

```python
# Importing liabraries and DataReader
import pandas as pd 
import pandas_datareader.data as web
import matplotlib.pyplot as plt 
import datetime
from datetime import date
```


```python
# Setting time range
start = date(2016,1,1)
end = date.today()
```


```python
# Getting data for a stock
stock_price = web.DataReader("TWTR", "yahoo", start, end)
stock_price.head(2)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Adj Close</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-01-04</th>
      <td>22.639999</td>
      <td>22.84</td>
      <td>22.110001</td>
      <td>22.559999</td>
      <td>15325000</td>
      <td>22.559999</td>
    </tr>
    <tr>
      <th>2016-01-05</th>
      <td>22.790001</td>
      <td>23.00</td>
      <td>21.850000</td>
      <td>21.920000</td>
      <td>17077700</td>
      <td>21.920000</td>
    </tr>
  </tbody>
</table>
</div>




```python
stock_price["MA"] = stock_price["Adj Close"].rolling(window=10).mean()
# stock_price.head()
stock_price.tail()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Adj Close</th>
      <th>MA</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017-03-20</th>
      <td>15.11</td>
      <td>15.11</td>
      <td>14.82</td>
      <td>15.09</td>
      <td>12454200</td>
      <td>15.09</td>
      <td>15.168</td>
    </tr>
    <tr>
      <th>2017-03-21</th>
      <td>15.08</td>
      <td>15.10</td>
      <td>14.50</td>
      <td>14.54</td>
      <td>19047000</td>
      <td>14.54</td>
      <td>15.104</td>
    </tr>
    <tr>
      <th>2017-03-22</th>
      <td>14.50</td>
      <td>14.99</td>
      <td>14.32</td>
      <td>14.98</td>
      <td>21034200</td>
      <td>14.98</td>
      <td>15.078</td>
    </tr>
    <tr>
      <th>2017-03-23</th>
      <td>14.99</td>
      <td>15.05</td>
      <td>14.73</td>
      <td>14.93</td>
      <td>11254100</td>
      <td>14.93</td>
      <td>15.049</td>
    </tr>
    <tr>
      <th>2017-03-24</th>
      <td>15.06</td>
      <td>15.37</td>
      <td>15.03</td>
      <td>15.14</td>
      <td>15514800</td>
      <td>15.14</td>
      <td>15.051</td>
    </tr>
  </tbody>
</table>
</div>




```python
# stock_price.plot()
stock_price[["Adj Close", "MA"]].plot()
plt.show()
```


![png](output_4_0.png)



```python
# we create grids
price_fig = plt.subplot2grid((6,1),(0,0), rowspan=5, colspan=1)
volume_fig = plt.subplot2grid((6,1),(5,0), rowspan=1, colspan=1, sharex=price_fig)
```


```python
price_fig.plot(stock_price.index, stock_price['Adj Close'])
price_fig.plot(stock_price.index, stock_price['MA'])
volume_fig.bar(stock_price.index, stock_price['Volume'])

plt.show()
```


![png](output_6_0.png)



```python

```
