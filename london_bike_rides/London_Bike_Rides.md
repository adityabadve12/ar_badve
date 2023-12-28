# Importing libraries


```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import warnings
warnings.filterwarnings('ignore')

```

# Loading the dataset


```python
df = pd.read_csv('london_merged.csv')
```

# Data Exploration


```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 17414 entries, 0 to 17413
    Data columns (total 10 columns):
     #   Column        Non-Null Count  Dtype  
    ---  ------        --------------  -----  
     0   timestamp     17414 non-null  object 
     1   cnt           17414 non-null  int64  
     2   t1            17414 non-null  float64
     3   t2            17414 non-null  float64
     4   hum           17414 non-null  float64
     5   wind_speed    17414 non-null  float64
     6   weather_code  17414 non-null  float64
     7   is_holiday    17414 non-null  float64
     8   is_weekend    17414 non-null  float64
     9   season        17414 non-null  float64
    dtypes: float64(8), int64(1), object(1)
    memory usage: 1.3+ MB
    


```python
df.shape
```




    (17414, 10)




```python
df.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>timestamp</th>
      <th>cnt</th>
      <th>t1</th>
      <th>t2</th>
      <th>hum</th>
      <th>wind_speed</th>
      <th>weather_code</th>
      <th>is_holiday</th>
      <th>is_weekend</th>
      <th>season</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2015-01-04 00:00:00</td>
      <td>182</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>93.0</td>
      <td>6.0</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015-01-04 01:00:00</td>
      <td>138</td>
      <td>3.0</td>
      <td>2.5</td>
      <td>93.0</td>
      <td>5.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2015-01-04 02:00:00</td>
      <td>134</td>
      <td>2.5</td>
      <td>2.5</td>
      <td>96.5</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2015-01-04 03:00:00</td>
      <td>72</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>100.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2015-01-04 04:00:00</td>
      <td>47</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>93.0</td>
      <td>6.5</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2015-01-04 05:00:00</td>
      <td>46</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>93.0</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2015-01-04 06:00:00</td>
      <td>51</td>
      <td>1.0</td>
      <td>-1.0</td>
      <td>100.0</td>
      <td>7.0</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2015-01-04 07:00:00</td>
      <td>75</td>
      <td>1.0</td>
      <td>-1.0</td>
      <td>100.0</td>
      <td>7.0</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>2015-01-04 08:00:00</td>
      <td>131</td>
      <td>1.5</td>
      <td>-1.0</td>
      <td>96.5</td>
      <td>8.0</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2015-01-04 09:00:00</td>
      <td>301</td>
      <td>2.0</td>
      <td>-0.5</td>
      <td>100.0</td>
      <td>9.0</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>3.0</td>
    </tr>
  </tbody>
</table>
</div>



# Counting the unique values in the weather_code column 


```python
df.weather_code.value_counts()
```




    1.0     6150
    2.0     4034
    3.0     3551
    7.0     2141
    4.0     1464
    26.0      60
    10.0      14
    Name: weather_code, dtype: int64



# Counting the unique values in the season column


```python
df.season.value_counts()
```




    0.0    4394
    1.0    4387
    3.0    4330
    2.0    4303
    Name: season, dtype: int64



# Specifying the column names as per convenience


```python
new_col_dict = {
    'timestamp': 'time' ,     
    'cnt' : 'count'   ,         
    't1' : 'real_temp_C' ,           
    't2' : 'feels_like_temp_C' ,           
    'hum' : 'humidity_percent'  ,         
    'wind_speed' : 'wind_speed_kph'  ,  
    'weather_code' : 'weather',  
    'is_holiday' :    'is_holiday',
    'is_weekend' :     'is_weekend', 
    'season' :     'season',  
}



```

# Renaming the columns to the specified column names



```python
df.rename(new_col_dict, axis =1, inplace=True)
```

# Changing the humidity values to percentage (i.e. a value between 0 and 1)



```python
df.humidity_percent = df.humidity_percent/100
```

# Creating dictionary for Season so that we can map the integers 0-3 to the actual written values



```python
season_dict = {
'0.0' : 'Spring',
    '1.0' : 'Summer',
    '2.0' : 'Autumn',
    '3.0' : 'Winter',
}
```

# Creating dictionary for Weather so that we can map the integers 0-3 to the actual written values



```python
weather_dict = {
'1.0' : 'Clear' ,    
'2.0' : 'Scattered clouds' , 
    '3.0' : 'Broken clouds' , 
    '7.0' : 'Cloudy' , 
    '4.0' : 'Rain' , 
    '26.0' : 'Rain with thunderstorm' , 
    '10.0' : 'Snowfall' , 
}
```

# Changing the data type of Season column to string


```python
df.season = df.season.astype("str")
```

# Changing the data type of Weather column to string


```python
df.weather = df.weather.astype("str")
```

# Mapping the values of Season column (0-3) to the actual written seasons


```python
df.season = df.season.map(season_dict)
```

# Mapping the values of Season column (0-3) to the actual written seasons


```python
df.weather = df.weather.map(weather_dict)
```

# Checking the dataframe to see if the mapping function has worked


```python
df.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>time</th>
      <th>count</th>
      <th>real_temp_C</th>
      <th>feels_like_temp_C</th>
      <th>humidity_percent</th>
      <th>wind_speed_kph</th>
      <th>weather</th>
      <th>is_holiday</th>
      <th>is_weekend</th>
      <th>season</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2015-01-04 00:00:00</td>
      <td>182</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>0.930</td>
      <td>6.0</td>
      <td>Broken clouds</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Winter</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015-01-04 01:00:00</td>
      <td>138</td>
      <td>3.0</td>
      <td>2.5</td>
      <td>0.930</td>
      <td>5.0</td>
      <td>Clear</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Winter</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2015-01-04 02:00:00</td>
      <td>134</td>
      <td>2.5</td>
      <td>2.5</td>
      <td>0.965</td>
      <td>0.0</td>
      <td>Clear</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Winter</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2015-01-04 03:00:00</td>
      <td>72</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>1.000</td>
      <td>0.0</td>
      <td>Clear</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Winter</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2015-01-04 04:00:00</td>
      <td>47</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.930</td>
      <td>6.5</td>
      <td>Clear</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Winter</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2015-01-04 05:00:00</td>
      <td>46</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>0.930</td>
      <td>4.0</td>
      <td>Clear</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Winter</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2015-01-04 06:00:00</td>
      <td>51</td>
      <td>1.0</td>
      <td>-1.0</td>
      <td>1.000</td>
      <td>7.0</td>
      <td>Rain</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Winter</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2015-01-04 07:00:00</td>
      <td>75</td>
      <td>1.0</td>
      <td>-1.0</td>
      <td>1.000</td>
      <td>7.0</td>
      <td>Rain</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Winter</td>
    </tr>
    <tr>
      <th>8</th>
      <td>2015-01-04 08:00:00</td>
      <td>131</td>
      <td>1.5</td>
      <td>-1.0</td>
      <td>0.965</td>
      <td>8.0</td>
      <td>Rain</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Winter</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2015-01-04 09:00:00</td>
      <td>301</td>
      <td>2.0</td>
      <td>-0.5</td>
      <td>1.000</td>
      <td>9.0</td>
      <td>Broken clouds</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Winter</td>
    </tr>
  </tbody>
</table>
</div>



# Writing the final dataframe to an excel file which we will use in our Power BI visualisations. The file will be 'london_bikes_output.xlsx'


```python
df.to_excel("london_bikes_output.xlsx",
              sheet_name='Data')
```
