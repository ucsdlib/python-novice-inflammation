

```python
import pandas
```

* interested in understanding the relationship b/t the weather and the number of mosquitos occuring during a particular year
* relationship at a particular site and whether or not it is consistent across sites
* data in csv files
* contains: single location data, rows holds single year info, mosiquito numbers and avg temps and rainfall 

year,temperature,rainfall,mosquitos  
2001,80,157,150  
2002,85,252,2177  
2003,86,154,153  

### Learning objectives
* conduct variable assignment, looping, and conditionals in python
* use an external py library
* read tabular data from a file
* subset and perform analysis on data
* display simple graphs


```python
cd /Users/jtdennis/workshops/python-intermediate-mosquitoes/data
```

    /Users/jtdennis/workshops/python-intermediate-mosquitoes/data



```python
pandas.read_csv('A1_mosquito_data.csv')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>temperature</th>
      <th>rainfall</th>
      <th>mosquitos</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2001</td>
      <td>80</td>
      <td>157</td>
      <td>150</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2002</td>
      <td>85</td>
      <td>252</td>
      <td>217</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2003</td>
      <td>86</td>
      <td>154</td>
      <td>153</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2004</td>
      <td>87</td>
      <td>159</td>
      <td>158</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2005</td>
      <td>74</td>
      <td>292</td>
      <td>243</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2006</td>
      <td>75</td>
      <td>283</td>
      <td>237</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2007</td>
      <td>80</td>
      <td>214</td>
      <td>190</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2008</td>
      <td>85</td>
      <td>197</td>
      <td>181</td>
    </tr>
    <tr>
      <th>8</th>
      <td>2009</td>
      <td>74</td>
      <td>231</td>
      <td>200</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2010</td>
      <td>74</td>
      <td>207</td>
      <td>184</td>
    </tr>
  </tbody>
</table>
</div>



* read_csv() function belongs to pandas library
* dot notation 



```python
data = pandas.read_csv('A1_mosquito_data.csv')
```


```python
print(data)
```

       year  temperature  rainfall  mosquitos
    0  2001           80       157        150
    1  2002           85       252        217
    2  2003           86       154        153
    3  2004           87       159        158
    4  2005           74       292        243
    5  2006           75       283        237
    6  2007           80       214        190
    7  2008           85       197        181
    8  2009           74       231        200
    9  2010           74       207        184



```python
data
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>temperature</th>
      <th>rainfall</th>
      <th>mosquitos</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2001</td>
      <td>80</td>
      <td>157</td>
      <td>150</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2002</td>
      <td>85</td>
      <td>252</td>
      <td>217</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2003</td>
      <td>86</td>
      <td>154</td>
      <td>153</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2004</td>
      <td>87</td>
      <td>159</td>
      <td>158</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2005</td>
      <td>74</td>
      <td>292</td>
      <td>243</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2006</td>
      <td>75</td>
      <td>283</td>
      <td>237</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2007</td>
      <td>80</td>
      <td>214</td>
      <td>190</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2008</td>
      <td>85</td>
      <td>197</td>
      <td>181</td>
    </tr>
    <tr>
      <th>8</th>
      <td>2009</td>
      <td>74</td>
      <td>231</td>
      <td>200</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2010</td>
      <td>74</td>
      <td>207</td>
      <td>184</td>
    </tr>
  </tbody>
</table>
</div>



* Once we have the data we can start playing with it.
* first let's ask what type of thing it is


```python
print(type(data))
```

    <class 'pandas.core.frame.DataFrame'>


* started in a data structure of DataFrame
* there are other data structures (remember numpy arrays from last class)
* we can select an individual column of data using it's name:


```python
print(data['year'])
```

    0    2001
    1    2002
    2    2003
    3    2004
    4    2005
    5    2006
    6    2007
    7    2008
    8    2009
    9    2010
    Name: year, dtype: int64


* or we can select several columns of data at once


```python
print(data[['rainfall', 'temperature']])
```

       rainfall  temperature
    0       157           80
    1       252           85
    2       154           86
    3       159           87
    4       292           74
    5       283           75
    6       214           80
    7       197           85
    8       231           74
    9       207           74


* we can subset rows using slices
* let's get first two rows


```python
print(data[0:2])
```

       year  temperature  rainfall  mosquitos
    0  2001           80       157        150
    1  2002           85       252        217


* remember python uses 0 based indexing
* starts at the first value and goes up to, but doesn't include the second value
* one thing we can't do with this syntax is directly as for data from a single row


```python
data[1]
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-17-c805864c0d75> in <module>()
    ----> 1 data[1]
    

    /Users/jtdennis/anaconda/envs/py35/lib/python3.5/site-packages/pandas/core/frame.py in __getitem__(self, key)
       1967             return self._getitem_multilevel(key)
       1968         else:
    -> 1969             return self._getitem_column(key)
       1970 
       1971     def _getitem_column(self, key):


    /Users/jtdennis/anaconda/envs/py35/lib/python3.5/site-packages/pandas/core/frame.py in _getitem_column(self, key)
       1974         # get column
       1975         if self.columns.is_unique:
    -> 1976             return self._get_item_cache(key)
       1977 
       1978         # duplicate columns & possible reduce dimensionality


    /Users/jtdennis/anaconda/envs/py35/lib/python3.5/site-packages/pandas/core/generic.py in _get_item_cache(self, item)
       1089         res = cache.get(item)
       1090         if res is None:
    -> 1091             values = self._data.get(item)
       1092             res = self._box_item_values(item, values)
       1093             cache[item] = res


    /Users/jtdennis/anaconda/envs/py35/lib/python3.5/site-packages/pandas/core/internals.py in get(self, item, fastpath)
       3209 
       3210             if not isnull(item):
    -> 3211                 loc = self.items.get_loc(item)
       3212             else:
       3213                 indexer = np.arange(len(self.items))[isnull(self.items)]


    /Users/jtdennis/anaconda/envs/py35/lib/python3.5/site-packages/pandas/core/index.py in get_loc(self, key, method, tolerance)
       1757                                  'backfill or nearest lookups')
       1758             key = _values_from_object(key)
    -> 1759             return self._engine.get_loc(key)
       1760 
       1761         indexer = self.get_indexer([key], method=method,


    pandas/index.pyx in pandas.index.IndexEngine.get_loc (pandas/index.c:3979)()


    pandas/index.pyx in pandas.index.IndexEngine.get_loc (pandas/index.c:3843)()


    pandas/hashtable.pyx in pandas.hashtable.PyObjectHashTable.get_item (pandas/hashtable.c:12265)()


    pandas/hashtable.pyx in pandas.hashtable.PyObjectHashTable.get_item (pandas/hashtable.c:12216)()


    KeyError: 1


* this is b/c data[1] is unambiguous
* if we want a single row we can either take a slice that returns a single row


```python
print(data[1:2])
```

       year  temperature  rainfall  mosquitos
    1  2002           85       252        217


* or use the `.iloc` method, which stands for "integer location" since we are looking up the row based on its integer:


```python
print(data.iloc[1])
```

    year           2002
    temperature      85
    rainfall        252
    mosquitos       217
    Name: 1, dtype: int64


* we can also use this syntax to get larger subsets


```python
print(data.iloc[1:3])
```

       year  temperature  rainfall  mosquitos
    1  2002           85       252        217
    2  2003           86       154        153


* we can also subset the data based on the value of other rows:


```python
print(data['temperature'][data['year'] > 2005])
```

    5    75
    6    80
    7    85
    8    74
    9    74
    Name: temperature, dtype: int64


* data frames also know how to perform common math
* mean


```python
print(data.mean())
```

    year           2005.5
    temperature      80.0
    rainfall        214.6
    mosquitos       191.3
    dtype: float64



```python
print(data.max())
```

    year           2010
    temperature      87
    rainfall        292
    mosquitos       243
    dtype: int64



```python
print(data['temperature'].min())
```

    74



```python
print(data['mosquitos'][1:3].std())
```

    45.2548339959


## Challenge

Import the data from A2_mosquito_data.csv, create a new variable that holds a data frame with only the weather data, and print the means and standard deviations for the weather variables.


```python
data2 = pandas.read_csv('A2_mosquito_data.csv')
data2.head()
weather = data2[["temperature","rainfall"]]
print(data2.temperature.mean(), data2.temperature.std(), data2.rainfall.mean(), data2.rainfall.std())
```

    80.3921568627 6.13540033371 207.039215686 56.5603963156


## Loops

* we can loop over the data and perform operations
* remember loop structure:

```python
for item in list:
   do_something
```

* let's look over temperatures and print out their values in degrees Celsius


```python
temps = data['temperature']
for temp_in_f in temps:
    temp_in_c = (temp_in_f - 32) * 5/9
    print(temp_in_c)
```

    26.6666666667
    29.4444444444
    30.0
    30.5555555556
    23.3333333333
    23.8888888889
    26.6666666667
    29.4444444444
    23.3333333333
    23.3333333333


## Conditionals 

* let's review conditionals from last week (if/then/else)

```python
if condition: 
   do_something
```

* So if we want to loop over the temperatures and print out only those temperatures that are > 80


```python
data['temperature'][0]
```




    80




```python
temp = data['temperature'][0]
if temp > 75:
    print("The temperature is greater than 75")
```

    The temperature is greater than 75


* We can also use `==` for equality
* `<=` for less than or equal to
* `>=` for greater than or equal to
* `!=` for not equal to

* we can add conditions with elif and else


```python
temp = data['temperature'][0]
if temp <= 80:
    print("the temp is < 80")
elif temp > 80:
    print("the temp is > 80")
else:
    print("the temp is equal to 80")
```

    the temp is < 80


### Challenge:
>**Import the data from A2_mosquito_data.csv, determine the mean temperate, and loop over the temperature values. For each value print out whether it is greater than the mean, less than the mean, or equal to the mean.**


```python
for temp in data2["temperature"]:
    if temp > data2.temperature.mean():
        print(temp, "is greater than", data2.temperature.mean())
    else:
        print(temp, "is less than", data2.temperature.mean())
```

    82 is greater than 80.3921568627
    70 is less than 80.3921568627
    89 is greater than 80.3921568627
    74 is less than 80.3921568627
    78 is less than 80.3921568627
    85 is greater than 80.3921568627
    86 is greater than 80.3921568627
    75 is less than 80.3921568627
    70 is less than 80.3921568627
    86 is greater than 80.3921568627
    83 is greater than 80.3921568627
    78 is less than 80.3921568627
    87 is greater than 80.3921568627
    76 is less than 80.3921568627
    86 is greater than 80.3921568627
    90 is greater than 80.3921568627
    76 is less than 80.3921568627
    87 is greater than 80.3921568627
    88 is greater than 80.3921568627
    87 is greater than 80.3921568627
    81 is greater than 80.3921568627
    74 is less than 80.3921568627
    85 is greater than 80.3921568627
    71 is less than 80.3921568627
    80 is less than 80.3921568627
    72 is less than 80.3921568627
    76 is less than 80.3921568627
    85 is greater than 80.3921568627
    83 is greater than 80.3921568627
    86 is greater than 80.3921568627
    82 is greater than 80.3921568627
    77 is less than 80.3921568627
    74 is less than 80.3921568627
    70 is less than 80.3921568627
    77 is less than 80.3921568627
    89 is greater than 80.3921568627
    83 is greater than 80.3921568627
    80 is less than 80.3921568627
    86 is greater than 80.3921568627
    72 is less than 80.3921568627
    79 is less than 80.3921568627
    85 is greater than 80.3921568627
    86 is greater than 80.3921568627
    72 is less than 80.3921568627
    78 is less than 80.3921568627
    71 is less than 80.3921568627
    88 is greater than 80.3921568627
    79 is less than 80.3921568627
    73 is less than 80.3921568627
    86 is greater than 80.3921568627
    87 is greater than 80.3921568627


### Plotting


```python
%matplotlib inline
```


```python
from matplotlib import pyplot as plt
```

* couple new things in the import statement above
    1. we can import part of a library using `from library import submodule` syntax
    2. we can use a different name to refer to the by using `as new name` - this called aliasing
* let's make a simple plot showing how the number of mosquitos varies over time


```python
data = pandas.read_csv('A2_mosquito_data.csv')
plt.plot(data['year'], data['mosquitos'])
```




    [<matplotlib.lines.Line2D at 0x10ad7a080>]




![png](Analyzing%20Mosquito%20Data_files/Analyzing%20Mosquito%20Data_49_1.png)


* more complicated plots can be created by adding more info
* let's look at how the diff. weather variables vary over time


```python
plt.figure(figsize=(10.0,3.0))

plt.subplot(1,2,1)
plt.plot(data['year'], data['temperature'], 'ro-')
plt.xlabel('Year')
plt.ylabel('Temperature')

plt.subplot(1,2,2)
plt.plot(data['year'], data['rainfall'], 'bs-')
plt.xlabel('year')
plt.ylabel('rain fall')
```




    <matplotlib.text.Text at 0x10d294080>




![png](Analyzing%20Mosquito%20Data_files/Analyzing%20Mosquito%20Data_51_1.png)


### Challenge

>**Using the data in A2_mosquito_data.csv plot the relationship between the number of mosquitos and temperature and the number of mosquitos and rainfall.**


```python
plt.figure(figsize=(10.0,3.0))

plt.subplot(1,2,1)
plt.plot(data2['year'], data['temperature'], 'ro-')
plt.xlabel('Year')
plt.ylabel('Temperature')

plt.subplot(1,2,2)
plt.plot(data['year'], data['rainfall'], 'bs-')
plt.xlabel('year')
plt.ylabel('rain fall')
```




    <matplotlib.text.Text at 0x10d294080>




![png](Analyzing%20Mosquito%20Data_files/Analyzing%20Mosquito%20Data_53_1.png)


## Modularization and Doc

* relationship b/t the weather and the number of mosquitos so that we can control mosiquitos
* relationships across sites

** learning objectives**

* write code for ppl, not computers
* break programs into chunks 
* write functions
* document code


```python
import pandas as pd
```


```python
data = pd.read_csv('A2_mosquito_data.csv')
```


```python
print(data)
```

        year  temperature  rainfall  mosquitos
    0   1960           82       200        180
    1   1961           70       227        194
    2   1962           89       231        207
    3   1963           74       114        121
    4   1964           78       147        140
    5   1965           85       151        148
    6   1966           86       172        162
    7   1967           75       106        112
    8   1968           70       276        230
    9   1969           86       165        162
    10  1970           83       222        198
    11  1971           78       297        247
    12  1972           87       288        248
    13  1973           76       286        239
    14  1974           86       231        202
    15  1975           90       284        243
    16  1976           76       190        175
    17  1977           87       257        225
    18  1978           88       128        133
    19  1979           87       218        199
    20  1980           81       206        184
    21  1981           74       175        160
    22  1982           85       202        187
    23  1983           71       130        126
    24  1984           80       225        200
    25  1985           72       196        173
    26  1986           76       261        222
    27  1987           85       111        121
    28  1988           83       247        210
    29  1989           86       137        142
    30  1990           82       159        152
    31  1991           77       172        160
    32  1992           74       280        231
    33  1993           70       291        238
    34  1994           77       126        125
    35  1995           89       191        178
    36  1996           83       298        248
    37  1997           80       282        237
    38  1998           86       219        195
    39  1999           72       143        134
    40  2000           79       262        221
    41  2001           85       189        175
    42  2002           86       205        186
    43  2003           72       195        173
    44  2004           78       148        146
    45  2005           71       262        219
    46  2006           88       255        226
    47  2007           79       262        221
    48  2008           73       198        176
    49  2009           86       215        187
    50  2010           87       127        129


* write code for people not computers
* use meaniful variable names


```python
import pandas as pd

data = pd.read_csv('A2_mosquito_data.csv')
print(data.head())
```

       year  temperature  rainfall  mosquitos
    0  1960           82       200        180
    1  1961           70       227        194
    2  1962           89       231        207
    3  1963           74       114        121
    4  1964           78       147        140


* let's go ahead and conduct a regression on the data
* we will use `statsmodels` library to conduct the regression


```python
!conda install -y statsmodels
```

    Using Anaconda Cloud api site https://api.anaconda.org
    Fetching package metadata: ....
    Solving package specifications: .........
    
    Package plan for installation in environment /Users/jtdennis/anaconda/envs/py35:
    
    The following packages will be downloaded:
    
        package                    |            build
        ---------------------------|-----------------
        patsy-0.4.1                |           py35_0         370 KB
        statsmodels-0.6.1          |      np110py35_0         4.8 MB
        ------------------------------------------------------------
                                               Total:         5.1 MB
    
    The following NEW packages will be INSTALLED:
    
        patsy:       0.4.1-py35_0     
        statsmodels: 0.6.1-np110py35_0
    
    Fetching packages ...
    patsy-0.4.1-py 100% |################################| Time: 0:00:00   1.11 MB/s
    statsmodels-0. 100% |################################| Time: 0:00:01   4.26 MB/s
    Extracting packages ...
    [      COMPLETE      ]|###################################################| 100%
    Linking packages ...
    [      COMPLETE      ]|###################################################| 100%



```python
import statsmodels.api as sm

reg_results = sm.OLS.from_formula('mosquitos ~ temperature + rainfall', data).fit()
reg_results.summary()
```




<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>        <td>mosquitos</td>    <th>  R-squared:         </th> <td>   0.997</td>
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th> <td>   0.997</td>
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th> <td>   7889.</td>
</tr>
<tr>
  <th>Date:</th>             <td>Tue, 26 Apr 2016</td> <th>  Prob (F-statistic):</th> <td>3.68e-61</td>
</tr>
<tr>
  <th>Time:</th>                 <td>13:53:00</td>     <th>  Log-Likelihood:    </th> <td> -111.54</td>
</tr>
<tr>
  <th>No. Observations:</th>      <td>    51</td>      <th>  AIC:               </th> <td>   229.1</td>
</tr>
<tr>
  <th>Df Residuals:</th>          <td>    48</td>      <th>  BIC:               </th> <td>   234.9</td>
</tr>
<tr>
  <th>Df Model:</th>              <td>     2</td>      <th>                     </th>     <td> </td>   
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>     <td> </td>   
</tr>
</table>
<table class="simpletable">
<tr>
       <td></td>          <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th> <th>[95.0% Conf. Int.]</th> 
</tr>
<tr>
  <th>Intercept</th>   <td>    2.0445</td> <td>    4.305</td> <td>    0.475</td> <td> 0.637</td> <td>   -6.610    10.699</td>
</tr>
<tr>
  <th>temperature</th> <td>    0.4844</td> <td>    0.051</td> <td>    9.457</td> <td> 0.000</td> <td>    0.381     0.587</td>
</tr>
<tr>
  <th>rainfall</th>    <td>    0.6967</td> <td>    0.006</td> <td>  125.385</td> <td> 0.000</td> <td>    0.686     0.708</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td> 1.651</td> <th>  Durbin-Watson:     </th> <td>   1.872</td>
</tr>
<tr>
  <th>Prob(Omnibus):</th> <td> 0.438</td> <th>  Jarque-Bera (JB):  </th> <td>   0.906</td>
</tr>
<tr>
  <th>Skew:</th>          <td>-0.278</td> <th>  Prob(JB):          </th> <td>   0.636</td>
</tr>
<tr>
  <th>Kurtosis:</th>      <td> 3.343</td> <th>  Cond. No.          </th> <td>3.16e+03</td>
</tr>
</table>



* `statsmodels` lets us use the names of the columns in our dataframe to clearly specify the form of the model we want
* the code is readable 
* `summary` method gives usa visual representative as a result
* we can look up particular values related to teh regression using `regr_results` 


```python
print(reg_results.params)
```

    Intercept      2.044527
    temperature    0.484413
    rainfall       0.696717
    dtype: float64



```python
print(reg_results.rsquared)
```

    0.996966873691


* we can also assign them to variables


```python
parameters = reg_results.params
rsquared = reg_results.rsquared
```

* we can plot the observed data agains the values precicted by our regression 
* first let's turn on inline plotting


```python
%matplotlib inline
```


```python
import matplotlib.pyplot as plt

predicted = parameters[0] + parameters[1] * data['temperature'] + parameters[2] * data['rainfall']
plt.plot(predicted, data['mosquitos'], 'ro')
min_mosquitos, max_mosquitos = min(data['mosquitos']), max(data['mosquitos'])
plt.plot([min_mosquitos, max_mosquitos], [min_mosquitos, max_mosquitos], 'k-')
```




    [<matplotlib.lines.Line2D at 0x11046e908>]




![png](Analyzing%20Mosquito%20Data_files/Analyzing%20Mosquito%20Data_70_1.png)



```python
import pandas as pd
import statsmodels.api as sm
import matplotlib.pyplot as plt

data = pd.read_csv('A2_mosquito_data.csv')
data['temperature'] = (data['temperature'] - 32) * 5 / 9.0
regr_results = sm.OLS.from_formula('mosquitos ~ temperature + rainfall', data).fit()
parameters = regr_results.params
rsquared = regr_results.rsquared
predicted = parameters[0] + parameters[1] * data['temperature'] + parameters[2] * data['rainfall']
plt.plot(predicted, data['mosquitos'], 'ro')
min_mosquitos, max_mosquitos = min(data['mosquitos']), max(data['mosquitos'])
plt.plot([min_mosquitos, max_mosquitos], [min_mosquitos, max_mosquitos], 'k-')
print(parameters)
print("R^2 = ", rsquared)
```

    Intercept      17.545739
    temperature     0.871943
    rainfall        0.696717
    dtype: float64
    R^2 =  0.996966873691


* now we need to loop all the data files, but we'd need to grow our code more
* need to break our code into manageble sized chunks 
* creating functions

### Functions

* review: 

```python
def function_name(inputs):
    do stuff
    return output
```

* general form

**EXAMPLE: function that returns the value of a number squared**


```python
def square(x):
    x_squared = x ** 2
    return x_squared

print('Four sqared is', square(4))
print('Five squared is', square(5))
```

    Four sqared is 16
    Five squared is 25



```python
#we can also return the desired value directly
def square(x):
    return x ** 2

print(square(3))
```

    9


* remember if we want to use the results of a function later we need to store it


```python
two_squared = square(2)
print(two_squared)
```

    4


## Challenge - function 

1. Write a function that converts temperature from Fahrenheit to Celcius and use it to replace

>```python
data['temperature'] = (data['temperature'] - 32) * 5 / 9.0
```

in our program.

2. Write a function called analyze() that takes data as an input, performs the regression, makes the observed-predicted plot, and returns parameters.


```python
def fahr_to_celsius(temp_fahr):
    temp_celsius = (temp_fahr- 32) * 5/9
    return temp_celsius

print(fahr_to_celsius(32))
```

    0.0


*Walk through someone’s result. When discussing talk about different names. E.g., fahr_to_celcius is better than temp_to_celcius since it is explicit both the input and the output. Talk about the fact that even though this doesn’t save us any lines of code it’s still easier to read.*

## More pandas 

* Let's exlore using pandas some more
* We can get attributes of the data frame, like it's columns


```python
data = pandas.read_csv("A1_mosquito_data.csv", sep=",")
```


```python
data.columns
```




    Index(['year', 'temperature', 'rainfall', 'mosquitos'], dtype='object')




```python
%matplotlib inline
```

* we can plot a single variable using the dot notation to plot from a dataframe objtect


```python
data['temperature'].plot(color="black", marker="*")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x10ff26400>




![png](Analyzing%20Mosquito%20Data_files/Analyzing%20Mosquito%20Data_87_1.png)


* we can also set the index of the data frame


```python
data.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>temperature</th>
      <th>rainfall</th>
      <th>mosquitos</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2001</td>
      <td>80</td>
      <td>157</td>
      <td>150</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2002</td>
      <td>85</td>
      <td>252</td>
      <td>217</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2003</td>
      <td>86</td>
      <td>154</td>
      <td>153</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2004</td>
      <td>87</td>
      <td>159</td>
      <td>158</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2005</td>
      <td>74</td>
      <td>292</td>
      <td>243</td>
    </tr>
  </tbody>
</table>
</div>



* pandas has a concept of row index that you can set to what you want
* in this case, let's set our row index to `year`
* by default it will read in as the integer index


```python
data.set_index('year')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>temperature</th>
      <th>rainfall</th>
      <th>mosquitos</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2001</th>
      <td>80</td>
      <td>157</td>
      <td>150</td>
    </tr>
    <tr>
      <th>2002</th>
      <td>85</td>
      <td>252</td>
      <td>217</td>
    </tr>
    <tr>
      <th>2003</th>
      <td>86</td>
      <td>154</td>
      <td>153</td>
    </tr>
    <tr>
      <th>2004</th>
      <td>87</td>
      <td>159</td>
      <td>158</td>
    </tr>
    <tr>
      <th>2005</th>
      <td>74</td>
      <td>292</td>
      <td>243</td>
    </tr>
    <tr>
      <th>2006</th>
      <td>75</td>
      <td>283</td>
      <td>237</td>
    </tr>
    <tr>
      <th>2007</th>
      <td>80</td>
      <td>214</td>
      <td>190</td>
    </tr>
    <tr>
      <th>2008</th>
      <td>85</td>
      <td>197</td>
      <td>181</td>
    </tr>
    <tr>
      <th>2009</th>
      <td>74</td>
      <td>231</td>
      <td>200</td>
    </tr>
    <tr>
      <th>2010</th>
      <td>74</td>
      <td>207</td>
      <td>184</td>
    </tr>
  </tbody>
</table>
</div>




```python
data
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>temperature</th>
      <th>rainfall</th>
      <th>mosquitos</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2001</td>
      <td>80</td>
      <td>157</td>
      <td>150</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2002</td>
      <td>85</td>
      <td>252</td>
      <td>217</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2003</td>
      <td>86</td>
      <td>154</td>
      <td>153</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2004</td>
      <td>87</td>
      <td>159</td>
      <td>158</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2005</td>
      <td>74</td>
      <td>292</td>
      <td>243</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2006</td>
      <td>75</td>
      <td>283</td>
      <td>237</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2007</td>
      <td>80</td>
      <td>214</td>
      <td>190</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2008</td>
      <td>85</td>
      <td>197</td>
      <td>181</td>
    </tr>
    <tr>
      <th>8</th>
      <td>2009</td>
      <td>74</td>
      <td>231</td>
      <td>200</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2010</td>
      <td>74</td>
      <td>207</td>
      <td>184</td>
    </tr>
  </tbody>
</table>
</div>



* we can save that setting by overwriting our data


```python
data = data.set_index('year')
```


```python
data.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>temperature</th>
      <th>rainfall</th>
      <th>mosquitos</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2001</th>
      <td>80</td>
      <td>157</td>
      <td>150</td>
    </tr>
    <tr>
      <th>2002</th>
      <td>85</td>
      <td>252</td>
      <td>217</td>
    </tr>
    <tr>
      <th>2003</th>
      <td>86</td>
      <td>154</td>
      <td>153</td>
    </tr>
    <tr>
      <th>2004</th>
      <td>87</td>
      <td>159</td>
      <td>158</td>
    </tr>
    <tr>
      <th>2005</th>
      <td>74</td>
      <td>292</td>
      <td>243</td>
    </tr>
  </tbody>
</table>
</div>




```python
data['temperature'].plot()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x10ff64828>




![png](Analyzing%20Mosquito%20Data_files/Analyzing%20Mosquito%20Data_96_1.png)


* ah what happened to the x axes labels?  
* our index is not the right data type


```python
data.index
```




    Int64Index([2001, 2002, 2003, 2004, 2005, 2006, 2007, 2008, 2009, 2010], dtype='int64', name='year')



* lets fix and rerun the plot making our index into a string


```python
data.index = data.index.map(str)
```


```python
data['temperature'].plot()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11051a668>




![png](Analyzing%20Mosquito%20Data_files/Analyzing%20Mosquito%20Data_101_1.png)


* one attribute of data frames is `dtypes` - tells us what our data types are


```python
data.dtypes
```




    temperature    int64
    rainfall       int64
    mosquitos      int64
    dtype: object



* Subsetting and filtering data frames
* let's see only temp greater than 80


```python
data[data["temperature"] > 80]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>temperature</th>
      <th>rainfall</th>
      <th>mosquitos</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2002</th>
      <td>85</td>
      <td>252</td>
      <td>217</td>
    </tr>
    <tr>
      <th>2003</th>
      <td>86</td>
      <td>154</td>
      <td>153</td>
    </tr>
    <tr>
      <th>2004</th>
      <td>87</td>
      <td>159</td>
      <td>158</td>
    </tr>
    <tr>
      <th>2008</th>
      <td>85</td>
      <td>197</td>
      <td>181</td>
    </tr>
  </tbody>
</table>
</div>




```python
data[data["temperature"] > 80]["rainfall"]
```




    1    252
    2    154
    3    159
    7    197
    Name: rainfall, dtype: int64




```python
type(data)
```




    pandas.core.frame.DataFrame



* let's grab mosiquitos where rainfall is less than 200

### Challenge

>Select the mosiquitos where rainfall is less than 200


```python
data[data['rainfall'] < 200]['mosquitos']
```




    0    150
    2    153
    3    158
    7    181
    Name: mosquitos, dtype: int64



* this is equivalent statement:


```python
data['mosquitos'][data['rainfall'] < 200]
```




    2001    150
    2003    153
    2004    158
    2008    181
    Name: mosquitos, dtype: int64



* we can also get the max of that returned object


```python
data[data['rainfall'] < 200]['mosquitos'].max()
```




    181



**NOTE** - we can walk through this step by step

* we can also assign it to a variable for later


```python
mosquitos_with_low_rainfall = data['mosquitos'][data['rainfall'] < 200]
```


```python
type(mosquitos_with_low_rainfall)
```




    pandas.core.series.Series




```python
mosquitos_with_low_rainfall
```




    2001    150
    2003    153
    2004    158
    2008    181
    Name: mosquitos, dtype: int64




```python
mosquitos_with_low_rainfall.index
```




    Index(['2001', '2003', '2004', '2008'], dtype='object')




```python
data.plot()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x110614978>




![png](Analyzing%20Mosquito%20Data_files/Analyzing%20Mosquito%20Data_121_1.png)


## Functions

Documenting our functions. Using function with pandas objects.


```python
def fahr_to_celsius(temp_fahr):
    temp_celsius = (temp_fahr- 32) * 5/9
    return temp_celsius
```


```python
fahr_to_celsius(32)
```




    0.0




```python
fahr_to_celsius(212)
```




    100.0



* 
* let's comment our function


```python
#this is a comment
def fahr_to_celsius(temp_fahr):
    temp_celsius = (temp_fahr- 32) * 5/9
    return temp_celsius
```


```python
"this is a string"
```




    'this is a string'




```python
#doesn't work
"a multiline 
string
"
```


      File "<ipython-input-24-316711d988ad>", line 2
        "a multiline
                     ^
    SyntaxError: EOL while scanning string literal



* a triple quote (single or double) will let us do a multi lined string


```python
multiline_string = ''' line one
line 2
one more
'''
```


```python
print(multiline_string)
```

     line one
    line 2
    one more
    



```python
#when we see the literal string we see the new line character
multiline_string
```




    ' line one\nline 2\none more\n'




```python
def fahr_to_celsius(temp_fahr):
    """Convert Fahrenheit to Celsiuss
    
    Return Celsius conversion of input
    """
    temp_celsius = (temp_fahr- 32) * 5/9
    return temp_celsius
```


```python
# use a question after the function to get python help
fahr_to_celsius?
```

    Object `fahr_to_celsius` not found.



```python
data.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>temperature</th>
      <th>rainfall</th>
      <th>mosquitos</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2001</th>
      <td>80</td>
      <td>157</td>
      <td>150</td>
    </tr>
    <tr>
      <th>2002</th>
      <td>85</td>
      <td>252</td>
      <td>217</td>
    </tr>
    <tr>
      <th>2003</th>
      <td>86</td>
      <td>154</td>
      <td>153</td>
    </tr>
    <tr>
      <th>2004</th>
      <td>87</td>
      <td>159</td>
      <td>158</td>
    </tr>
    <tr>
      <th>2005</th>
      <td>74</td>
      <td>292</td>
      <td>243</td>
    </tr>
  </tbody>
</table>
</div>



* now we have the have the function we can apply it to our data frame
* let's see how that looks and then save to the data frame itself 


```python
fahr_to_celsius(data['temperature'])
```




    0    26.666667
    1    29.444444
    2    30.000000
    3    30.555556
    4    23.333333
    5    23.888889
    6    26.666667
    7    29.444444
    8    23.333333
    9    23.333333
    Name: temperature, dtype: float64




```python
data["temperature_c"] = fahr_to_celsius(data['temperature'])
```


```python
data.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>temperature</th>
      <th>rainfall</th>
      <th>mosquitos</th>
      <th>temperature_c</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2001</td>
      <td>80</td>
      <td>157</td>
      <td>150</td>
      <td>26.666667</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2002</td>
      <td>85</td>
      <td>252</td>
      <td>217</td>
      <td>29.444444</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2003</td>
      <td>86</td>
      <td>154</td>
      <td>153</td>
      <td>30.000000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2004</td>
      <td>87</td>
      <td>159</td>
      <td>158</td>
      <td>30.555556</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2005</td>
      <td>74</td>
      <td>292</td>
      <td>243</td>
      <td>23.333333</td>
    </tr>
  </tbody>
</table>
</div>



* yay we added a new column on our dataframe
* let's plot using that var and save our plot to the disk


```python
%matplotlib inline
```


```python
import matplotlib.pyplot as plt
```


```python
plt.plot?
```


```python
plt.plot(data['temperature_c'], data['mosquitos'], ".")
plt.savefig('A1_mosquito_data_mosquitos_vs_tempC.png')
```


![png](Analyzing%20Mosquito%20Data_files/Analyzing%20Mosquito%20Data_145_0.png)



```python
!ls *png
```

    A1_mosquito_data_mosquitos_vs_tempC.png


* ok, we've successfully added a column to our data frame and plotted values
* then we saved that image to the file system
* but remember: we have a number of files in that directory


```python
!ls -l *csv
```

    -rw-r--r--  1 jtdennis  2113415076   196 Feb  6 21:11 A1_mosquito_data.csv
    -rw-r--r--  1 jtdennis  2113415076   852 Feb  6 21:11 A2_mosquito_data.csv
    -rw-r--r--  1 jtdennis  2113415076  1837 Apr 27 10:31 A2_mosquito_data_C.csv
    -rw-r--r--  1 jtdennis  2113415076   827 Feb  6 21:11 A3_mosquito_data.csv
    -rw-r--r--  1 jtdennis  2113415076   823 Feb  6 21:11 B1_mosquito_data.csv
    -rw-r--r--  1 jtdennis  2113415076   852 Feb  6 21:11 B2_mosquito_data.csv


* what we want is to be able to read each of those files, plot and save the fig out
* problem is we don't want to have to specify the file name manually
* let's see if we can manipulate our csv filenames 


```python
a = "A1_mosquitos_data.csv"
```


```python
a
```




    'A1_mosquitos_data.csv'



* remember how we sliced off parts of strings last week
* we can reuse that here


```python
a[0:-3] + "png"
```




    'A1_mosquitos_data.png'



* we can also concatenate our last part -- that tells us what we plotted


```python
a[0:-4] + "_mosquitos_vs_tempC.png"
```




    'A1_mosquitos_data_mosquitos_vs_tempC.png'



* we can do string replacement using the replace method


```python
a.replace(".csv", ".png")
```




    'A1_mosquitos_data.png'



**Let's put it all together with our conversion and plotting above into a couple of functions**


```python
def fahr_to_celsius(temp_fahr):
    temp_celsius = (temp_fahr- 32) * 5/9
    return temp_celsius
```


```python
%matplotlib inline
```

* It is often good to write out what you want the function to do step by step


```python
def creat_mosquitos_vs_tempC_plot(filename):
    # write out process here
    #load data
    #conert celsius
    #create the plot
    #save the plot
    pass
    
```

* Then just write out those operations 


```python
def create_mosquitos_vs_tempC_plot(filename):
  # write processing here
    # load data
    print("Loading", filename)
    mosquitos_data = pandas.read_csv(filename)
    # convert celsius
    mosquitos_data["temperature_C"] = fahr_to_celsius(mosquitos_data["temperature"])
    # create the plot
    print("Plotting", filename)
    plt.plot(mosquitos_data["temperature_C"], mosquitos_data["mosquitos"], ".")
    # save the plot
    filename_png = filename[0:-4] + "_mosquitos_vs_tempC.png"
    plt.savefig(filename_png)
    print("Saving", filename_png)
    return filename_png
```


```python
name_of_png = create_mosquitos_vs_tempC_plot('A2_mosquito_data.csv')
```

    Loading A2_mosquito_data.csv
    Plotting A2_mosquito_data.csv
    Saving A2_mosquito_data_mosquitos_vs_tempC.png



![png](Analyzing%20Mosquito%20Data_files/Analyzing%20Mosquito%20Data_165_1.png)


* yay, we sucessfully created a function that takes a filename, reads in data, does a conversion, plots and then saves plot to the file


```python
print(name_of_png)
```

    A2_mosquito_data_mosquitos_vs_tempC.png



```python
create_mosquitos_vs_tempC_plot("B1_mosquito_data.csv")
```

    Loading B1_mosquito_data.csv
    Plotting B1_mosquito_data.csv
    Saving B1_mosquito_data_mosquitos_vs_tempC.png





    'B1_mosquito_data_mosquitos_vs_tempC.png'




![png](Analyzing%20Mosquito%20Data_files/Analyzing%20Mosquito%20Data_168_2.png)



```python
!ls *png
```

    A1_mosquito_data_mosquitos_vs_tempC.png B1_mosquito_data_mosquitos_vs_tempC.png
    A2_mosquito_data_mosquitos_vs_tempC.png


* now, how about instead of returning the new plot filename, let's return the data frame
* we just need to change the return value


```python
def create_mosquitos_vs_tempC_plot(filename):
  # write processing here
    # load data
    print("Loading", filename)
    mosquitos_data = pandas.read_csv(filename)
    # convert celsius
    mosquitos_data["temperature_C"] = fahr_to_celsius(mosquitos_data["temperature"])
    # create the plot
    print("Plotting", filename)
    plt.plot(mosquitos_data["temperature_C"], mosquitos_data["mosquitos"], ".")
    # save the plot
    filename_png = filename[0:-4] + "_mosquitos_vs_tempC.png"
    plt.savefig(filename_png)
    print("Saving", filename_png)
    return mosquitos_data
```


```python
mosquito_data_A2 = create_mosquitos_vs_tempC_plot("A2_mosquito_data.csv")
```

    Loading A2_mosquito_data.csv
    Plotting A2_mosquito_data.csv
    Saving A2_mosquito_data_mosquitos_vs_tempC.png



![png](Analyzing%20Mosquito%20Data_files/Analyzing%20Mosquito%20Data_172_1.png)


* we can then save that new data out as csv


```python
mosquito_data_A2.to_csv("A2_mosquito_data_C.csv")
```


```python
mosquito_data_A2.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>temperature</th>
      <th>rainfall</th>
      <th>mosquitos</th>
      <th>temperature_C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1960</td>
      <td>82</td>
      <td>200</td>
      <td>180</td>
      <td>27.777778</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1961</td>
      <td>70</td>
      <td>227</td>
      <td>194</td>
      <td>21.111111</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1962</td>
      <td>89</td>
      <td>231</td>
      <td>207</td>
      <td>31.666667</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1963</td>
      <td>74</td>
      <td>114</td>
      <td>121</td>
      <td>23.333333</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1964</td>
      <td>78</td>
      <td>147</td>
      <td>140</td>
      <td>25.555556</td>
    </tr>
  </tbody>
</table>
</div>




```python
!head A2_mosquito_data_C.csv
```

    ,year,temperature,rainfall,mosquitos,temperature_C
    0,1960,82,200,180,27.77777777777778
    1,1961,70,227,194,21.11111111111111
    2,1962,89,231,207,31.666666666666668
    3,1963,74,114,121,23.333333333333332
    4,1964,78,147,140,25.555555555555557
    5,1965,85,151,148,29.444444444444443
    6,1966,86,172,162,30.0
    7,1967,75,106,112,23.88888888888889
    8,1968,70,276,230,21.11111111111111


### Making a module

* Let's write a script! 
* We will turn our functions into a script and use in panadas like our `import` modules



```python
!ls *py
```

    analyze.py



```python
%matplotlib inline
```


```python
import analyze
```


```python
data = analyze.create_mosquitos_vs_tempC_plot("A2_mosquito_data.csv")
```

    Loading A2_mosquito_data.csv
    Plotting A2_mosquito_data.csv
    Saving A2_mosquito_data_mosquitos_vs_tempC.png



![png](Analyzing%20Mosquito%20Data_files/Analyzing%20Mosquito%20Data_181_1.png)



```python
print(data)
```

    A2_mosquito_data_mosquitos_vs_tempC.png


* notice that we added out earlier version of the plotting function to the file -- the one that returned the file
* edit the file and return mosquitos_data instead
* let's rerun the function call


```python
data = analyze.create_mosquitos_vs_tempC_plot("A2_mosquito_data.csv")
```

    Loading A2_mosquito_data.csv
    Plotting A2_mosquito_data.csv
    Saving A2_mosquito_data_mosquitos_vs_tempC.png



![png](Analyzing%20Mosquito%20Data_files/Analyzing%20Mosquito%20Data_184_1.png)



```python
print(data)
```

    A2_mosquito_data_mosquitos_vs_tempC.png


* doesn't work! 
* in juypter we have to explicitly 'reload' the module and this requies importing it from the importlib
* there's also `autoreload` extension 



```python
from importlib import reload
reload(analyze)
```




    <module 'analyze' from '/Users/jtdennis/workshops/intermed-py/analyze.py'>




```python
data = analyze.create_mosquitos_vs_tempC_plot("A2_mosquito_data.csv")
```

    Loading A2_mosquito_data.csv
    Plotting A2_mosquito_data.csv
    Saving A2_mosquito_data_mosquitos_vs_tempC.png



![png](Analyzing%20Mosquito%20Data_files/Analyzing%20Mosquito%20Data_188_1.png)



```python
data.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>temperature</th>
      <th>rainfall</th>
      <th>mosquitos</th>
      <th>temperature_C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1960</td>
      <td>82</td>
      <td>200</td>
      <td>180</td>
      <td>27.777778</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1961</td>
      <td>70</td>
      <td>227</td>
      <td>194</td>
      <td>21.111111</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1962</td>
      <td>89</td>
      <td>231</td>
      <td>207</td>
      <td>31.666667</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1963</td>
      <td>74</td>
      <td>114</td>
      <td>121</td>
      <td>23.333333</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1964</td>
      <td>78</td>
      <td>147</td>
      <td>140</td>
      <td>25.555556</td>
    </tr>
  </tbody>
</table>
</div>




```python
!ls *.png
```

    A1_mosquito_data_mosquitos_vs_tempC.png B1_mosquito_data_mosquitos_vs_tempC.png
    A2_mosquito_data_mosquitos_vs_tempC.png


**Last step -create a Python script that let's us run the above script from the command line**

1. Open another ext file
2. Call it run_analyze_script
3. Add the below to the file (using the cat command to print the file to the notebook)


```python
!cat run_analyze_script.py
```

    import analyze
    import sys 
    
    #filename = "a2_mosquito_data.csv"
    #argv[0] our script filename
    filename = sys.argv[1]
    
    analyze2.create_mosquitos_vs_tempC_plot(filename)


A note about the above: 

`sys.argv[1]` is the second element of the command line arguements - in this case the script filename is the first. So:
>python scriptname.py filename.csv 

sys.argv[0] is scriptname.py  
sys.argv[1] is filename.csv 

1. Lastly open a terminal console (cmd in win)
2. Go to the same directory of the file 
3. Type: `python run_analyze_script.py B1_mosquito_data.csv` in the command line and enter

* Yay! good job. 


```python

```
