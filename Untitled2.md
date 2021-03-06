

```python
# Panal Data structure, kinda analog of a three-dimentional analogue of DataFrame. 
import numpy as np 
import pandas as pd 
from pandas import DataFrame as df
import pandas_datareader.data as web
from datetime import date
```


```python
sdate = date(2016,1,3)
edate = date.today()
```


```python
pdata = pd.Panel(dict((stock, web.get_data_yahoo(stock, sdate, edate)) for stock in ["AAPL","MSFT","GOOGL"]))
```


```python
pdata
```




    <class 'pandas.core.panel.Panel'>
    Dimensions: 3 (items) x 314 (major_axis) x 6 (minor_axis)
    Items axis: AAPL to MSFT
    Major_axis axis: 2016-01-04 00:00:00 to 2017-03-31 00:00:00
    Minor_axis axis: Open to Adj Close




```python
# items = open,close
# major_axis=date
# minor_axis=tickers
pdata = pdata.swapaxes('items', 'minor')
# Interchange axes and swap values axes appropriately
pdata["Adj Close"]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>AAPL</th>
      <th>GOOGL</th>
      <th>MSFT</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-01-04</th>
      <td>102.612183</td>
      <td>759.440002</td>
      <td>53.015032</td>
    </tr>
    <tr>
      <th>2016-01-05</th>
      <td>100.040792</td>
      <td>761.530029</td>
      <td>53.256889</td>
    </tr>
    <tr>
      <th>2016-01-06</th>
      <td>98.083025</td>
      <td>759.330017</td>
      <td>52.289462</td>
    </tr>
    <tr>
      <th>2016-01-07</th>
      <td>93.943473</td>
      <td>741.000000</td>
      <td>50.470697</td>
    </tr>
    <tr>
      <th>2016-01-08</th>
      <td>94.440222</td>
      <td>730.909973</td>
      <td>50.625489</td>
    </tr>
    <tr>
      <th>2016-01-11</th>
      <td>95.969420</td>
      <td>733.070007</td>
      <td>50.596463</td>
    </tr>
    <tr>
      <th>2016-01-12</th>
      <td>97.362258</td>
      <td>745.340027</td>
      <td>51.060828</td>
    </tr>
    <tr>
      <th>2016-01-13</th>
      <td>94.859047</td>
      <td>719.570007</td>
      <td>49.957961</td>
    </tr>
    <tr>
      <th>2016-01-14</th>
      <td>96.933690</td>
      <td>731.390015</td>
      <td>51.380081</td>
    </tr>
    <tr>
      <th>2016-01-15</th>
      <td>94.605802</td>
      <td>710.489990</td>
      <td>49.329136</td>
    </tr>
    <tr>
      <th>2016-01-19</th>
      <td>94.148022</td>
      <td>719.080017</td>
      <td>48.913141</td>
    </tr>
    <tr>
      <th>2016-01-20</th>
      <td>94.274641</td>
      <td>718.559998</td>
      <td>49.135649</td>
    </tr>
    <tr>
      <th>2016-01-21</th>
      <td>93.797377</td>
      <td>726.669983</td>
      <td>48.835745</td>
    </tr>
    <tr>
      <th>2016-01-22</th>
      <td>98.784315</td>
      <td>745.460022</td>
      <td>50.586791</td>
    </tr>
    <tr>
      <th>2016-01-25</th>
      <td>96.855775</td>
      <td>733.619995</td>
      <td>50.103077</td>
    </tr>
    <tr>
      <th>2016-01-26</th>
      <td>97.391477</td>
      <td>733.789978</td>
      <td>50.470697</td>
    </tr>
    <tr>
      <th>2016-01-27</th>
      <td>90.992218</td>
      <td>717.580017</td>
      <td>49.551643</td>
    </tr>
    <tr>
      <th>2016-01-28</th>
      <td>91.644804</td>
      <td>748.299988</td>
      <td>50.364283</td>
    </tr>
    <tr>
      <th>2016-01-29</th>
      <td>94.810344</td>
      <td>761.349976</td>
      <td>53.295587</td>
    </tr>
    <tr>
      <th>2016-02-01</th>
      <td>93.923996</td>
      <td>770.770020</td>
      <td>52.927964</td>
    </tr>
    <tr>
      <th>2016-02-02</th>
      <td>92.024676</td>
      <td>780.909973</td>
      <td>51.273663</td>
    </tr>
    <tr>
      <th>2016-02-03</th>
      <td>93.846074</td>
      <td>749.380005</td>
      <td>50.461024</td>
    </tr>
    <tr>
      <th>2016-02-04</th>
      <td>94.600127</td>
      <td>730.030029</td>
      <td>50.306236</td>
    </tr>
    <tr>
      <th>2016-02-05</th>
      <td>92.073538</td>
      <td>703.760010</td>
      <td>48.526169</td>
    </tr>
    <tr>
      <th>2016-02-08</th>
      <td>93.043048</td>
      <td>704.159973</td>
      <td>47.800598</td>
    </tr>
    <tr>
      <th>2016-02-09</th>
      <td>93.023458</td>
      <td>701.020020</td>
      <td>47.674832</td>
    </tr>
    <tr>
      <th>2016-02-10</th>
      <td>92.318363</td>
      <td>706.849976</td>
      <td>48.090826</td>
    </tr>
    <tr>
      <th>2016-02-11</th>
      <td>91.760163</td>
      <td>706.359985</td>
      <td>48.071477</td>
    </tr>
    <tr>
      <th>2016-02-12</th>
      <td>92.044160</td>
      <td>706.890015</td>
      <td>48.855094</td>
    </tr>
    <tr>
      <th>2016-02-16</th>
      <td>94.639300</td>
      <td>717.640015</td>
      <td>49.780749</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2017-02-17</th>
      <td>135.720001</td>
      <td>846.549988</td>
      <td>64.620003</td>
    </tr>
    <tr>
      <th>2017-02-21</th>
      <td>136.699997</td>
      <td>849.270020</td>
      <td>64.489998</td>
    </tr>
    <tr>
      <th>2017-02-22</th>
      <td>137.110001</td>
      <td>851.359985</td>
      <td>64.360001</td>
    </tr>
    <tr>
      <th>2017-02-23</th>
      <td>136.529999</td>
      <td>851.000000</td>
      <td>64.620003</td>
    </tr>
    <tr>
      <th>2017-02-24</th>
      <td>136.660004</td>
      <td>847.809998</td>
      <td>64.620003</td>
    </tr>
    <tr>
      <th>2017-02-27</th>
      <td>136.929993</td>
      <td>849.669983</td>
      <td>64.230003</td>
    </tr>
    <tr>
      <th>2017-02-28</th>
      <td>136.990005</td>
      <td>844.929993</td>
      <td>63.980000</td>
    </tr>
    <tr>
      <th>2017-03-01</th>
      <td>139.789993</td>
      <td>856.750000</td>
      <td>64.940002</td>
    </tr>
    <tr>
      <th>2017-03-02</th>
      <td>138.960007</td>
      <td>849.849976</td>
      <td>64.010002</td>
    </tr>
    <tr>
      <th>2017-03-03</th>
      <td>139.779999</td>
      <td>849.080017</td>
      <td>64.250000</td>
    </tr>
    <tr>
      <th>2017-03-06</th>
      <td>139.339996</td>
      <td>847.270020</td>
      <td>64.269997</td>
    </tr>
    <tr>
      <th>2017-03-07</th>
      <td>139.520004</td>
      <td>851.150024</td>
      <td>64.400002</td>
    </tr>
    <tr>
      <th>2017-03-08</th>
      <td>139.000000</td>
      <td>853.640015</td>
      <td>64.989998</td>
    </tr>
    <tr>
      <th>2017-03-09</th>
      <td>138.679993</td>
      <td>857.840027</td>
      <td>64.730003</td>
    </tr>
    <tr>
      <th>2017-03-10</th>
      <td>139.139999</td>
      <td>861.409973</td>
      <td>64.930000</td>
    </tr>
    <tr>
      <th>2017-03-13</th>
      <td>139.199997</td>
      <td>864.580017</td>
      <td>64.709999</td>
    </tr>
    <tr>
      <th>2017-03-14</th>
      <td>138.990005</td>
      <td>865.909973</td>
      <td>64.410004</td>
    </tr>
    <tr>
      <th>2017-03-15</th>
      <td>140.460007</td>
      <td>868.390015</td>
      <td>64.750000</td>
    </tr>
    <tr>
      <th>2017-03-16</th>
      <td>140.690002</td>
      <td>870.000000</td>
      <td>64.639999</td>
    </tr>
    <tr>
      <th>2017-03-17</th>
      <td>139.990005</td>
      <td>872.369995</td>
      <td>64.870003</td>
    </tr>
    <tr>
      <th>2017-03-20</th>
      <td>141.460007</td>
      <td>867.909973</td>
      <td>64.930000</td>
    </tr>
    <tr>
      <th>2017-03-21</th>
      <td>139.839996</td>
      <td>850.140015</td>
      <td>64.209999</td>
    </tr>
    <tr>
      <th>2017-03-22</th>
      <td>141.419998</td>
      <td>849.799988</td>
      <td>65.029999</td>
    </tr>
    <tr>
      <th>2017-03-23</th>
      <td>140.919998</td>
      <td>839.650024</td>
      <td>64.870003</td>
    </tr>
    <tr>
      <th>2017-03-24</th>
      <td>140.639999</td>
      <td>835.140015</td>
      <td>64.980003</td>
    </tr>
    <tr>
      <th>2017-03-27</th>
      <td>140.880005</td>
      <td>838.510010</td>
      <td>65.099998</td>
    </tr>
    <tr>
      <th>2017-03-28</th>
      <td>143.800003</td>
      <td>840.630005</td>
      <td>65.290001</td>
    </tr>
    <tr>
      <th>2017-03-29</th>
      <td>144.119995</td>
      <td>849.869995</td>
      <td>65.470001</td>
    </tr>
    <tr>
      <th>2017-03-30</th>
      <td>143.929993</td>
      <td>849.479980</td>
      <td>65.709999</td>
    </tr>
    <tr>
      <th>2017-03-31</th>
      <td>143.660004</td>
      <td>847.799988</td>
      <td>65.860001</td>
    </tr>
  </tbody>
</table>
<p>314 rows × 3 columns</p>
</div>




```python
# ix-based label indexing generalizes to three dimensions, 
# so we can select all data at a particular date or a range of dates
pdata.ix[:,'1/20/2017',:]
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
  </thead>
  <tbody>
    <tr>
      <th>AAPL</th>
      <td>120.449997</td>
      <td>120.449997</td>
      <td>119.730003</td>
      <td>120.000000</td>
      <td>32597900.0</td>
      <td>119.481976</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>829.090027</td>
      <td>829.239990</td>
      <td>824.599976</td>
      <td>828.169983</td>
      <td>1277300.0</td>
      <td>828.169983</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>62.669998</td>
      <td>62.820000</td>
      <td>62.369999</td>
      <td>62.740002</td>
      <td>30213500.0</td>
      <td>62.361932</td>
    </tr>
  </tbody>
</table>
</div>




```python
pdata.ix["Adj Close", '1/20/2017':'1/27/2017',:]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>AAPL</th>
      <th>GOOGL</th>
      <th>MSFT</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017-01-20</th>
      <td>119.481976</td>
      <td>828.169983</td>
      <td>62.361932</td>
    </tr>
    <tr>
      <th>2017-01-23</th>
      <td>119.561633</td>
      <td>844.429993</td>
      <td>62.580604</td>
    </tr>
    <tr>
      <th>2017-01-24</th>
      <td>119.452107</td>
      <td>849.530029</td>
      <td>63.137231</td>
    </tr>
    <tr>
      <th>2017-01-25</th>
      <td>121.353858</td>
      <td>858.450012</td>
      <td>63.296267</td>
    </tr>
    <tr>
      <th>2017-01-26</th>
      <td>121.413604</td>
      <td>856.979980</td>
      <td>63.882708</td>
    </tr>
    <tr>
      <th>2017-01-27</th>
      <td>121.423555</td>
      <td>845.030029</td>
      <td>65.383610</td>
    </tr>
  </tbody>
</table>
</div>




```python
# an alternative way to represent panel data, is in "stacked" DateFrame form
stacked = pdata.ix[:, '1/20/2017':,:].to_frame()
stacked
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
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
      <th>minor</th>
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
      <th rowspan="3" valign="top">2017-01-20</th>
      <th>AAPL</th>
      <td>120.449997</td>
      <td>120.449997</td>
      <td>119.730003</td>
      <td>120.000000</td>
      <td>32597900.0</td>
      <td>119.481976</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>829.090027</td>
      <td>829.239990</td>
      <td>824.599976</td>
      <td>828.169983</td>
      <td>1277300.0</td>
      <td>828.169983</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>62.669998</td>
      <td>62.820000</td>
      <td>62.369999</td>
      <td>62.740002</td>
      <td>30213500.0</td>
      <td>62.361932</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-01-23</th>
      <th>AAPL</th>
      <td>120.000000</td>
      <td>120.809998</td>
      <td>119.769997</td>
      <td>120.080002</td>
      <td>22050200.0</td>
      <td>119.561633</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>831.609985</td>
      <td>845.539978</td>
      <td>828.700012</td>
      <td>844.429993</td>
      <td>2453600.0</td>
      <td>844.429993</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>62.700001</td>
      <td>63.119999</td>
      <td>62.570000</td>
      <td>62.959999</td>
      <td>23097600.0</td>
      <td>62.580604</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-01-24</th>
      <th>AAPL</th>
      <td>119.550003</td>
      <td>120.099998</td>
      <td>119.500000</td>
      <td>119.970001</td>
      <td>23211000.0</td>
      <td>119.452107</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>846.979980</td>
      <td>851.520020</td>
      <td>842.280029</td>
      <td>849.530029</td>
      <td>1686200.0</td>
      <td>849.530029</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>63.200001</td>
      <td>63.740002</td>
      <td>62.939999</td>
      <td>63.520000</td>
      <td>24672900.0</td>
      <td>63.137231</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-01-25</th>
      <th>AAPL</th>
      <td>120.419998</td>
      <td>122.099998</td>
      <td>120.279999</td>
      <td>121.879997</td>
      <td>32377600.0</td>
      <td>121.353858</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>853.549988</td>
      <td>858.789978</td>
      <td>849.739990</td>
      <td>858.450012</td>
      <td>1655400.0</td>
      <td>858.450012</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>63.950001</td>
      <td>64.099998</td>
      <td>63.450001</td>
      <td>63.680000</td>
      <td>23672700.0</td>
      <td>63.296267</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-01-26</th>
      <th>AAPL</th>
      <td>121.669998</td>
      <td>122.440002</td>
      <td>121.599998</td>
      <td>121.940002</td>
      <td>26337600.0</td>
      <td>121.413604</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>859.049988</td>
      <td>861.000000</td>
      <td>850.520020</td>
      <td>856.979980</td>
      <td>3076800.0</td>
      <td>856.979980</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>64.120003</td>
      <td>64.540001</td>
      <td>63.549999</td>
      <td>64.269997</td>
      <td>43554600.0</td>
      <td>63.882708</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-01-27</th>
      <th>AAPL</th>
      <td>122.139999</td>
      <td>122.349998</td>
      <td>121.599998</td>
      <td>121.949997</td>
      <td>20562900.0</td>
      <td>121.423555</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>859.000000</td>
      <td>867.000000</td>
      <td>841.900024</td>
      <td>845.030029</td>
      <td>3749600.0</td>
      <td>845.030029</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>65.389999</td>
      <td>65.910004</td>
      <td>64.889999</td>
      <td>65.779999</td>
      <td>44818000.0</td>
      <td>65.383610</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-01-30</th>
      <th>AAPL</th>
      <td>120.930000</td>
      <td>121.629997</td>
      <td>120.660004</td>
      <td>121.629997</td>
      <td>30377500.0</td>
      <td>121.104937</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>837.059998</td>
      <td>837.229980</td>
      <td>821.030029</td>
      <td>823.830017</td>
      <td>3512000.0</td>
      <td>823.830017</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>65.690002</td>
      <td>65.790001</td>
      <td>64.800003</td>
      <td>65.129997</td>
      <td>31651400.0</td>
      <td>64.737526</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-01-31</th>
      <th>AAPL</th>
      <td>121.150002</td>
      <td>121.389999</td>
      <td>120.620003</td>
      <td>121.349998</td>
      <td>49201000.0</td>
      <td>120.826147</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>819.500000</td>
      <td>823.070007</td>
      <td>813.400024</td>
      <td>820.190002</td>
      <td>2015400.0</td>
      <td>820.190002</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>64.860001</td>
      <td>65.150002</td>
      <td>64.260002</td>
      <td>64.650002</td>
      <td>25270500.0</td>
      <td>64.260423</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-02-01</th>
      <th>AAPL</th>
      <td>127.029999</td>
      <td>130.490005</td>
      <td>127.010002</td>
      <td>128.750000</td>
      <td>111985000.0</td>
      <td>128.194203</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>824.000000</td>
      <td>824.000000</td>
      <td>812.250000</td>
      <td>815.239990</td>
      <td>2244300.0</td>
      <td>815.239990</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>64.360001</td>
      <td>64.620003</td>
      <td>63.470001</td>
      <td>63.580002</td>
      <td>39671500.0</td>
      <td>63.196871</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-02-02</th>
      <th>AAPL</th>
      <td>127.980003</td>
      <td>129.389999</td>
      <td>127.779999</td>
      <td>128.529999</td>
      <td>33710400.0</td>
      <td>127.975152</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>815.000000</td>
      <td>824.559998</td>
      <td>812.049988</td>
      <td>818.260010</td>
      <td>1684000.0</td>
      <td>818.260010</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>63.250000</td>
      <td>63.410000</td>
      <td>62.750000</td>
      <td>63.169998</td>
      <td>45827000.0</td>
      <td>62.789338</td>
    </tr>
    <tr>
      <th>...</th>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-03-20</th>
      <th>AAPL</th>
      <td>140.399994</td>
      <td>141.500000</td>
      <td>140.229996</td>
      <td>141.460007</td>
      <td>20213100.0</td>
      <td>141.460007</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>869.479980</td>
      <td>870.340027</td>
      <td>864.669983</td>
      <td>867.909973</td>
      <td>1501400.0</td>
      <td>867.909973</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>64.910004</td>
      <td>65.180000</td>
      <td>64.720001</td>
      <td>64.930000</td>
      <td>12744200.0</td>
      <td>64.930000</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-03-21</th>
      <th>AAPL</th>
      <td>142.110001</td>
      <td>142.800003</td>
      <td>139.729996</td>
      <td>139.839996</td>
      <td>39116800.0</td>
      <td>139.839996</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>870.059998</td>
      <td>873.469971</td>
      <td>847.690002</td>
      <td>850.140015</td>
      <td>2515200.0</td>
      <td>850.140015</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>65.190002</td>
      <td>65.500000</td>
      <td>64.129997</td>
      <td>64.209999</td>
      <td>26191800.0</td>
      <td>64.209999</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-03-22</th>
      <th>AAPL</th>
      <td>139.850006</td>
      <td>141.600006</td>
      <td>139.759995</td>
      <td>141.419998</td>
      <td>25787600.0</td>
      <td>141.419998</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>849.479980</td>
      <td>855.349976</td>
      <td>847.000000</td>
      <td>849.799988</td>
      <td>1358000.0</td>
      <td>849.799988</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>64.120003</td>
      <td>65.139999</td>
      <td>64.120003</td>
      <td>65.029999</td>
      <td>20632800.0</td>
      <td>65.029999</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-03-23</th>
      <th>AAPL</th>
      <td>141.259995</td>
      <td>141.580002</td>
      <td>140.610001</td>
      <td>140.919998</td>
      <td>20285700.0</td>
      <td>140.919998</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>841.390015</td>
      <td>841.690002</td>
      <td>833.000000</td>
      <td>839.650024</td>
      <td>3285200.0</td>
      <td>839.650024</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>64.940002</td>
      <td>65.239998</td>
      <td>64.769997</td>
      <td>64.870003</td>
      <td>18819600.0</td>
      <td>64.870003</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-03-24</th>
      <th>AAPL</th>
      <td>141.500000</td>
      <td>141.740005</td>
      <td>140.350006</td>
      <td>140.639999</td>
      <td>22025300.0</td>
      <td>140.639999</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>842.000000</td>
      <td>844.000000</td>
      <td>829.099976</td>
      <td>835.140015</td>
      <td>2092600.0</td>
      <td>835.140015</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>65.360001</td>
      <td>65.449997</td>
      <td>64.760002</td>
      <td>64.980003</td>
      <td>22373200.0</td>
      <td>64.980003</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-03-27</th>
      <th>AAPL</th>
      <td>139.389999</td>
      <td>141.220001</td>
      <td>138.619995</td>
      <td>140.880005</td>
      <td>23493200.0</td>
      <td>140.880005</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>828.090027</td>
      <td>841.380005</td>
      <td>824.299988</td>
      <td>838.510010</td>
      <td>1934600.0</td>
      <td>838.510010</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>64.629997</td>
      <td>65.220001</td>
      <td>64.349998</td>
      <td>65.099998</td>
      <td>18550200.0</td>
      <td>65.099998</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-03-28</th>
      <th>AAPL</th>
      <td>140.910004</td>
      <td>144.039993</td>
      <td>140.619995</td>
      <td>143.800003</td>
      <td>33320700.0</td>
      <td>143.800003</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>839.690002</td>
      <td>845.400024</td>
      <td>832.270020</td>
      <td>840.630005</td>
      <td>1515500.0</td>
      <td>840.630005</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>64.959999</td>
      <td>65.470001</td>
      <td>64.650002</td>
      <td>65.290001</td>
      <td>20039300.0</td>
      <td>65.290001</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-03-29</th>
      <th>AAPL</th>
      <td>143.679993</td>
      <td>144.490005</td>
      <td>143.190002</td>
      <td>144.119995</td>
      <td>29120900.0</td>
      <td>144.119995</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>842.750000</td>
      <td>851.590027</td>
      <td>841.380005</td>
      <td>849.869995</td>
      <td>1437000.0</td>
      <td>849.869995</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>65.120003</td>
      <td>65.500000</td>
      <td>64.949997</td>
      <td>65.470001</td>
      <td>13512400.0</td>
      <td>65.470001</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-03-30</th>
      <th>AAPL</th>
      <td>144.190002</td>
      <td>144.500000</td>
      <td>143.500000</td>
      <td>143.929993</td>
      <td>21179100.0</td>
      <td>143.929993</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>851.979980</td>
      <td>852.000000</td>
      <td>846.770020</td>
      <td>849.479980</td>
      <td>948100.0</td>
      <td>849.479980</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>65.419998</td>
      <td>65.980003</td>
      <td>65.360001</td>
      <td>65.709999</td>
      <td>15100400.0</td>
      <td>65.709999</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2017-03-31</th>
      <th>AAPL</th>
      <td>143.720001</td>
      <td>144.270004</td>
      <td>143.009995</td>
      <td>143.660004</td>
      <td>19534100.0</td>
      <td>143.660004</td>
    </tr>
    <tr>
      <th>GOOGL</th>
      <td>846.830017</td>
      <td>849.559998</td>
      <td>845.239990</td>
      <td>847.799988</td>
      <td>1437200.0</td>
      <td>847.799988</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>65.650002</td>
      <td>66.190002</td>
      <td>65.449997</td>
      <td>65.860001</td>
      <td>21001100.0</td>
      <td>65.860001</td>
    </tr>
  </tbody>
</table>
<p>150 rows × 6 columns</p>
</div>




```python
stacked["Adj Close"]
```




    Date        minor
    2017-01-20  AAPL     119.481976
                GOOGL    828.169983
                MSFT      62.361932
    2017-01-23  AAPL     119.561633
                GOOGL    844.429993
                MSFT      62.580604
    2017-01-24  AAPL     119.452107
                GOOGL    849.530029
                MSFT      63.137231
    2017-01-25  AAPL     121.353858
                GOOGL    858.450012
                MSFT      63.296267
    2017-01-26  AAPL     121.413604
                GOOGL    856.979980
                MSFT      63.882708
    2017-01-27  AAPL     121.423555
                GOOGL    845.030029
                MSFT      65.383610
    2017-01-30  AAPL     121.104937
                GOOGL    823.830017
                MSFT      64.737526
    2017-01-31  AAPL     120.826147
                GOOGL    820.190002
                MSFT      64.260423
    2017-02-01  AAPL     128.194203
                GOOGL    815.239990
                MSFT      63.196871
    2017-02-02  AAPL     127.975152
                GOOGL    818.260010
                MSFT      62.789338
                            ...    
    2017-03-20  AAPL     141.460007
                GOOGL    867.909973
                MSFT      64.930000
    2017-03-21  AAPL     139.839996
                GOOGL    850.140015
                MSFT      64.209999
    2017-03-22  AAPL     141.419998
                GOOGL    849.799988
                MSFT      65.029999
    2017-03-23  AAPL     140.919998
                GOOGL    839.650024
                MSFT      64.870003
    2017-03-24  AAPL     140.639999
                GOOGL    835.140015
                MSFT      64.980003
    2017-03-27  AAPL     140.880005
                GOOGL    838.510010
                MSFT      65.099998
    2017-03-28  AAPL     143.800003
                GOOGL    840.630005
                MSFT      65.290001
    2017-03-29  AAPL     144.119995
                GOOGL    849.869995
                MSFT      65.470001
    2017-03-30  AAPL     143.929993
                GOOGL    849.479980
                MSFT      65.709999
    2017-03-31  AAPL     143.660004
                GOOGL    847.799988
                MSFT      65.860001
    Name: Adj Close, dtype: float64




```python

```
