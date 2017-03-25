

```python
#import pandas
import pandas as pd 

```


```python
# create Data Frame object
stocks = ["IBM", "APPLE", "TWTTR", "GE", "MSFT"]
prices = [115.00, 119.14, 19.77, 25.99, 26]

```


```python
portfolio = list(zip(stocks,prices))
print(portfolio)
```

    [('IBM', 115.0), ('APPLE', 119.14), ('TWTTR', 19.77), ('GE', 25.99), ('MSFT', 26)]



```python
df = pd.DataFrame(data=portfolio, columns=['stocks', 'prices'])
print(df)
```

      stocks  prices
    0    IBM  115.00
    1  APPLE  119.14
    2  TWTTR   19.77
    3     GE   25.99
    4   MSFT   26.00



```python
#lets add another col
df['new_col'] = " "
df['new_col'] = 5

print(df)

```

      stocks  prices  new_col
    0    IBM  115.00        5
    1  APPLE  119.14        5
    2  TWTTR   19.77        5
    3     GE   25.99        5
    4   MSFT   26.00        5



```python
# access the item by loc
print(df.loc[2])
```

    stocks     TWTTR
    prices     19.77
    new_col        5
    Name: 2, dtype: object



```python
# slicing df
print(df.loc[1:3])
```

      stocks  prices  new_col
    1  APPLE  119.14        5
    2  TWTTR   19.77        5
    3     GE   25.99        5



```python
# lets write this to csv file
df.to_csv("rrr_portfolio.csv", index=True)
```


```python

```
