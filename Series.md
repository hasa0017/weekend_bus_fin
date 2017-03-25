
Intro to Data Structures - Series


```python
import numpy as np
import pandas as pd

```


```python
 s = pd.Series(np.random.randn(5), index=['a', 'b', 'c', 'd', 'e'])

```


```python
s
```




    a   -0.029926
    b   -0.765909
    c   -2.153789
    d   -1.397156
    e   -1.122329
    dtype: float64




```python
s*(-1)
```




    a    0.029926
    b    0.765909
    c    2.153789
    d    1.397156
    e    1.122329
    dtype: float64




```python
s[0]
```




    -0.029925891380597317




```python
s[:3]
```




    a   -0.029926
    b   -0.765909
    c   -2.153789
    dtype: float64




```python
s[2:3]
```




    c   -2.153789
    dtype: float64




```python
s[[4, 3, 1]]
```




    e   -1.122329
    d   -1.397156
    b   -0.765909
    dtype: float64




```python
s + 20
```




    a    19.970074
    b    19.234091
    c    17.846211
    d    18.602844
    e    18.877671
    dtype: float64




```python

```
