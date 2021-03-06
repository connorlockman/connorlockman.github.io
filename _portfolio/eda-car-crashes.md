---
title: "Exploring Car Crash Data in Michigan"
layout: collection
permalink: /p/p2
collection: portfolio
header:
  teaser: /assets/images/yield/teaser.png
author_profile: true
---
This project uses exploratory data analysis to visualize underlying car crash data for Southeast Michigan.  This step uses python, pandas, matplotlib, and seaborn to highlight trends that exist within the data.




```python
import pandas as pd
```


```python
df = pd.read_csv('combined_dataset.csv')
#df = pd.read_csv('crash_funding_data.csv')
```

    /Users/connorlockman/anaconda3/lib/python3.7/site-packages/IPython/core/interactiveshell.py:3057: DtypeWarning: Columns (28,48,49) have mixed types. Specify dtype option on import or set low_memory=False.
      interactivity=interactivity, compiler=compiler, result=result)



```python
df.head()
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
      <th>Unnamed: 0</th>
      <th>ACOUNT</th>
      <th>ALCOHOL</th>
      <th>BCOUNT</th>
      <th>BICYCLE</th>
      <th>CARTODB_ID</th>
      <th>CCOUNT</th>
      <th>CNTNAME</th>
      <th>COMMERCIAL</th>
      <th>COMMUNITY</th>
      <th>...</th>
      <th>UNITS</th>
      <th>WEATHER</th>
      <th>WEEKDAY</th>
      <th>WORK_ZONE</th>
      <th>X</th>
      <th>XCORD</th>
      <th>Y</th>
      <th>YCORD</th>
      <th>YEAR</th>
      <th>YOUNG</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Washtenaw</td>
      <td>NaN</td>
      <td>Ann Arbor</td>
      <td>...</td>
      <td>2</td>
      <td>5</td>
      <td>2</td>
      <td>NaN</td>
      <td>-83.771023</td>
      <td>-83.77102</td>
      <td>42.287878</td>
      <td>42.28787</td>
      <td>2017</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Oakland</td>
      <td>NaN</td>
      <td>Brandon Twp</td>
      <td>...</td>
      <td>1</td>
      <td>5</td>
      <td>2</td>
      <td>NaN</td>
      <td>-83.421944</td>
      <td>-83.42194</td>
      <td>42.810271</td>
      <td>42.81026</td>
      <td>2017</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Oakland</td>
      <td>NaN</td>
      <td>Bloomfield Twp</td>
      <td>...</td>
      <td>1</td>
      <td>5</td>
      <td>2</td>
      <td>NaN</td>
      <td>-83.234323</td>
      <td>-83.23432</td>
      <td>42.615461</td>
      <td>42.61546</td>
      <td>2017</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Oakland</td>
      <td>NaN</td>
      <td>Orchard Lake Village</td>
      <td>...</td>
      <td>2</td>
      <td>2</td>
      <td>3</td>
      <td>NaN</td>
      <td>-83.362812</td>
      <td>-83.36281</td>
      <td>42.578827</td>
      <td>42.57882</td>
      <td>2017</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Livingston</td>
      <td>NaN</td>
      <td>Hartland Twp</td>
      <td>...</td>
      <td>2</td>
      <td>2</td>
      <td>5</td>
      <td>NaN</td>
      <td>-83.753034</td>
      <td>-83.75303</td>
      <td>42.656270</td>
      <td>42.65626</td>
      <td>2017</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 61 columns</p>
</div>



## What does our combined dataset look like?


```python
len(df)
```




    709900



We have 709,900 crash cases in this dataset.

### what about the distribution among years?


```python
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
from scipy import stats
sns.set(color_codes=True)
```


```python
x = df['YEAR']
```


```python
yr_2014 = len(df.loc[df['YEAR'] == 2014])
yr_2015 = len(df.loc[df['YEAR'] == 2015])
yr_2016 = len(df.loc[df['YEAR'] == 2016])
yr_2017 = len(df.loc[df['YEAR'] == 2017])
yr_2018 = len(df.loc[df['YEAR'] == 2018])
```


```python
yr_2017
```




    145362




```python
x_axis = ['2014','2015','2016','2017','2018']
```


```python
y_axis = [yr_2014,yr_2015,yr_2016,yr_2017,yr_2018]
```


```python
sns.barplot(x=x_axis, y=y_axis)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x10a7701d0>





<img src="/assets/images/yield/output_13_1.png" width="100%">


We see that each year has a very similar total number of car crashes.

## When are these car crashes occuring?

### Let's look at the aggregate day counts


```python
dates_result = df.groupby('DATE_FULL').size().sort_values(ascending=True)
```


```python
dates_result
```




    DATE_FULL
    12/25/2014     136
    01/01/2015     155
    01/03/2016     155
    12/25/2015     156
    03/23/2014     160
    07/06/2014     162
    03/30/2014     163
    12/25/2016     169
    04/13/2014     172
    07/05/2015     174
    04/27/2014     176
    04/05/2015     181
    04/20/2014     183
    04/06/2014     185
    01/12/2014     185
    09/09/2018     186
    03/04/2018     186
    02/25/2018     188
    03/11/2018     188
    12/07/2014     188
    03/16/2014     189
    03/29/2015     190
    12/28/2014     191
    02/19/2017     191
    12/27/2015     192
    11/26/2015     192
    12/25/2018     193
    07/16/2017     193
    12/14/2014     193
    04/22/2018     194
                  ...
    10/31/2014     768
    11/20/2018     778
    12/24/2017     780
    12/11/2016     794
    01/10/2017     795
    12/18/2015     796
    02/09/2018     797
    01/16/2014     797
    01/31/2017     818
    01/02/2014     832
    02/09/2016     845
    04/17/2018     848
    12/13/2017     870
    03/01/2016     872
    02/05/2014     874
    01/09/2015     879
    01/03/2014     913
    11/21/2015     917
    03/13/2014     941
    12/09/2017     965
    01/08/2014     982
    01/09/2018     992
    01/29/2018     993
    12/08/2016    1007
    12/11/2017    1018
    03/12/2014    1021
    02/24/2016    1126
    11/19/2014    1287
    01/07/2014    1313
    03/13/2017    1369
    Length: 1826, dtype: int64



We see that the most car crashes in this dataset occurred on March 13th of 2017.  With a little investigation we see that the bottom of the list makes sense with christmas day emerging as one the days with the least number of car crashes.  Days at the top of this list mainly fall in the winter months and we can see that with some investigation that these days typically had wintery conditions with snow, ice, or very low temperatures occuring.


```python
fig, ax = plt.subplots(figsize=(15,7))
result_dates = df.groupby('DATE_FULL').size().plot(ax=ax)
```



<img src="/assets/images/yield/output_20_0.png" width="100%">


### Let's look at the hourly distribution of crashes


```python
fig, ax = plt.subplots(figsize=(15,7))
df.groupby('HOUR').size().plot(ax=ax)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x116c99b38>




<img src="/assets/images/yield/output_22_1.png" width="100%">


We can see in this figure that their is a bimodial distribution of crashes with a spike in the morning during the traditional morning rush hour times of 6 - 9 and a larger spike in the afternoon around 5 - 7 pm during the evening rush hour period.  Intuitively, this makes sense.

## Which city has the most car crashes and the least?


```python
df.groupby('COMMUNITY').size().sort_values(ascending =True)
```




    COMMUNITY
    Novi Twp                              1
    Southfield Twp                        1
    Fenton (Livingston)                   1
    Estral Beach                          5
    Grosse Pointe Shores (Macomb)        11
    Lake Angelus                         14
    Leonard                              17
    Memphis (St. Clair)                  17
    Barton Hills                         21
    Petersburg                           22
    Maybee                               29
    Emmett                               39
    Richmond (St. Clair)                 39
    Memphis (Macomb)                     44
    Armada                               61
    Luna Pier                            76
    Carleton                             89
    Yale                                 98
    Algonac                             124
    Capac                               128
    Freedom Twp                         140
    Milan (Monroe)                      143
    East China Twp                      153
    Manchester                          154
    Ortonville                          170
    Grosse Pointe Shores (Wayne)        176
    Pinckney                            199
    South Rockwood                      199
    River Rouge                         218
    Grant Twp                           218
                                      ...  
    Redford Twp                        6079
    Dearborn Heights                   6163
    Ypsilanti Twp                      6341
    Pittsfield Twp                     6852
    St. Clair Shores                   7470
    Madison Heights                    7511
    West Bloomfield Twp                7684
    Bloomfield Twp                     7948
    Westland                           8590
    Waterford Twp                      9357
    Shelby Twp                         9407
    Macomb Twp                         9426
    Roseville                          9626
    Novi                              10128
    Pontiac                           10160
    Auburn Hills                      10435
    Royal Oak                         10582
    Canton Twp                        10609
    Taylor                            11847
    Clinton Twp                       11957
    Rochester Hills                   11959
    Farmington Hills                  15760
    Troy                              17085
    Dearborn                          17505
    Southfield                        18002
    Ann Arbor                         18250
    Livonia                           18341
    Warren                            23681
    Sterling Heights                  23796
    Detroit                          115539
    Length: 237, dtype: int64



237 cities featured crash data for the region

We see that Detroit emerges as the city with the most crashes.  We can believe this because it is clearly the largest city in South East Michigan with a population close to 675,000.  It is also the economic center of the region and has many of the areas jobs. Cities that fall to the bottom of the list have, generally smaller populations. For insantance, Barton Hills which is located just to the west of ann arbor had 21 crashes and has a population of 320. These results pose a question of how to normalize this data and whether that should be by total population or number of jobs in the region.  We decide to rely on the raw data because we don't have an indication about which is the appropriate normalization process.

### County


```python
df.groupby('CNTNAME').size().sort_values(ascending =False)
```




    CNTNAME
    Wayne         260891
    Oakland       204977
    Macomb        125741
    Washtenaw      56091
    Livingston     24111
    Monroe         19052
    St. Clair      19037
    dtype: int64




```python
pop = [1.75,1.25,.871,.368,.189,.149,.159]
county = ['Wayne','Oakland','Macomb','Washtenaw','Livingston','Monroe','St. Clair']
```


```python
sns.barplot(x=pop, y=county)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1162a79b0>





<img src="/assets/images/yield/output_31_1.png" width="100%">


## Who is involved in these car crashes?


```python
who_df = df[['PEDESTRIAN', 'BICYCLE', 'MOTORCYCLE',
       'TRAIN', 'DISTRACTED','ELDERLY','YOUNG']]
```


```python
who_df.head()
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
      <th>PEDESTRIAN</th>
      <th>BICYCLE</th>
      <th>MOTORCYCLE</th>
      <th>TRAIN</th>
      <th>DISTRACTED</th>
      <th>ELDERLY</th>
      <th>YOUNG</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
ped_lst = df.loc[who_df['PEDESTRIAN']==1]
```


```python
ped = len(ped_lst)
```


```python
ped / 709000
```




    0.008899858956276445




```python
bike_lst = df.loc[who_df['BICYCLE']==1]
```


```python
bike = len(bike_lst)
```


```python
moto_lst = df.loc[df['MOTORCYCLE']==1]
```


```python
moto = len(moto_lst)
```


```python
train_lst = df.loc[df['TRAIN']==1]
```


```python
train = len(train_lst)
```


```python
distracted_lst = df.loc[df['DISTRACTED']==1]
```


```python
distracted = len(distracted_lst)
```


```python
young_lst = df.loc[df['YOUNG']==1]
```


```python
young = len(young_lst)
```


```python
young / 709000
```




    0.3330253878702398




```python
old_lst = df.loc[df['ELDERLY']==1]
```


```python
old = len(old_lst)
```


```python
x_axis = ['ped','bike','moto','train']
y_axis = [ped, bike,moto,train]
```


```python
sns.barplot(x=x_axis, y=y_axis)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1181a75f8>





<img src="/assets/images/yield/output_52_1.png" width="100%">


We can see here that pedestrians are involved in the most crash instances while trains are fairly rare in the crash data.


```python
x_axis = ['old','young','distracted']
y_axis = [old, young,distracted]
```


```python
sns.barplot(x=x_axis, y=y_axis)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x119e3c0b8>





<img src="/assets/images/yield/output_55_1.png" width="100%">



```python
old + young + distracted
```




    372701




```python
709900 - 372701
```




    337199



We see that with using some of the demographic features that we are still 337,199 crash accounts short.  This builds insight into that while we do know a little about who is involved in these crashes, we don't have full understanding about them across the board.

## Weather

How does weathe impact this car crash data?


```python
df.groupby('WEATHER').size().sort_values(ascending =False)
```




    WEATHER
    1     436696
    2     142019
    4      63503
    5      47649
    98     11278
    3       3289
    7       2354
    8       2000
    6       1019
    9         42
    10        27
    0         24
    dtype: int64



1 = clear

2 = cloudy

3 = FOG

4 = RAIN

5 = SNOW

6 =  SEVERE CROSSWINDS

7 = SLEET / HAIL

8 = BLOWING SNOW

9 = BLOWING SAND SOIL DIRT

10 = SMOKE

98 = UNKNOWN

0 = NOT ENTERED



```python
Y = [436696,142019,63503,47649,11278,3289,2354,2000,1019,42,27,24]
#X = [1,2,4,5,98,3,7,8,6,9,10,0]
X = ['CLEAR','CLOUDY','FOG','RAIN','SNOW','SEVERE CROSSWINDS','SLEET / HAIL','BLOWING SNOW','BLOWING SAND SOIL DIRT','SMOKE','UNKNOWN','NOT ENTERED']
```


```python
sum(Y)
```




    709900



Every case in the data has a weather code assigned to it.


```python
sns.barplot(x=X, y=Y)
plt.xticks(rotation='vertical')
```




    (array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11]),
     <a list of 12 Text xticklabel objects>)





<img src="/assets/images/yield/output_65_1.png" width="100%">


The vast majority of crashes occur under clear or cloudy circumstances.

## Road Conditions

Weather doesn't seem to be a major factor, but could road factors be impacting the data?


```python
df.columns
```




    Index(['Unnamed: 0', 'ACOUNT', 'ALCOHOL', 'BCOUNT', 'BICYCLE', 'CARTODB_ID',
           'CCOUNT', 'CNTNAME', 'COMMERCIAL', 'COMMUNITY', 'CRASHID', 'CRSHTYPEO',
           'DATE_FULL', 'DAY', 'DEER', 'DISTRACTED', 'DIS_CTRL_I', 'DRUG',
           'ELDERLY', 'EMERGENCY', 'FALINKID', 'FID', 'HIGH_SEVER', 'HITNRUN',
           'HOUR', 'HWY_CLSS_C', 'INTERROAD', 'INTR_INVL_', 'JURIS', 'KCOUNT',
           'LANEDEPART', 'LIGHTING', 'MAINROAD', 'MONTH', 'MOTORCYCLE', 'MP',
           'NFC', 'OBJECTID', 'OCCUPANTS', 'PEDESTRIAN', 'PR', 'PROPDAMG',
           'REDLIGHTRU', 'ROADCONDIT', 'ROADLANES', 'SCHOOLBUS', 'SEMMCD',
           'SPEEDLIMIT', 'SURFACE', 'TIME_FULL', 'TRAIN', 'UNITS', 'WEATHER',
           'WEEKDAY', 'WORK_ZONE', 'X', 'XCORD', 'Y', 'YCORD', 'YEAR', 'YOUNG'],
          dtype='object')




```python
df.groupby('WORK_ZONE').size().sort_values(ascending =False)
```




    WORK_ZONE
    0.0    141201
    1.0      2743
    dtype: int64




```python
2743 + 141201
```




    143944



We can't be certain of anything about workzones because it appears that we dont have data for many of the years in question


```python
df.groupby('ROADCONDIT').size().sort_values(ascending =False)
```




    ROADCONDIT
    1     500506
    2     114178
    4      41835
    3      34048
    6       6193
    98      4955
    97      3390
    8       2250
    5       2185
    7        254
    10        47
    0         38
    9         21
    dtype: int64



1 = dry

2 = wet

3 = ice

4 = snow

5 =  Mud, Dirt, Gravel

6 = slush

7 = debris

8 = Water (Standing/Moving)

9 = Sand

10 = Oily

97 = other

98 = unknown

0 = null / not entered


```python
Y = [500506,114178,41835,34048,6193,4955,3390,2250,2185,254,47,38,21]
X = ['dry','wet','ice','snow','Mud, Dirt, Gravel', 'Slush','debris','Water (Standing/Moving)','Sand','Oily','other','unknown','null / not entered']
```


```python
sns.barplot(x=X, y=Y)
plt.xticks(rotation='vertical')
```




    (array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12]),
     <a list of 13 Text xticklabel objects>)





<img src="/assets/images/yield/output_75_1.png" width="100%">



```python
df.groupby('HWY_CLSS_C').size().sort_values(ascending =False)
```




    HWY_CLSS_C
    9    420484
    3    129568
    1    103871
    2     41057
    4      9031
    5      4076
    7      1079
    0       734
    dtype: int64




```python
df.groupby('ROADLANES').size().sort_values(ascending =False)
```




    ROADLANES
     2    252048
     5    134424
     3    132193
     4    125930
     1     24694
     6     23295
     7     12496
     8      4144
     9       632
     0        40
    -2         2
    -4         2
    dtype: int64




```python
df.groupby('SPEEDLIMIT').size().sort_values(ascending =False)
```




    SPEEDLIMIT
    45    160483
    25    114022
    35     95293
    70     86459
    40     82383
    55     73438
    50     49487
    30     33187
    0       8746
    15      2520
    60      1406
    20       923
    65       781
    10       355
    5        216
    75       195
    46         2
    26         1
    23         1
    8          1
    80         1
    dtype: int64




```python
df.groupby('SURFACE').size().sort_values(ascending =False)
```




    SURFACE
    Asphalt     91780
    Concrete    39784
                10760
    Gravel       1609
    Brick          11
    dtype: int64



## Road Funding

We are interested in building road funding into this data and conducting some analysis on this


```python
df_funding = pd.read_csv('community.csv')
```


```python
df_funding.head()
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
      <th>County</th>
      <th>Community</th>
      <th>Annual Amount</th>
      <th>Road Miles</th>
      <th>Average Per Mile</th>
      <th>Unnamed: 5</th>
      <th>Unnamed: 6</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Livingston</td>
      <td>Brighton</td>
      <td>$465,346</td>
      <td>29.44</td>
      <td>$15,807</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Livingston</td>
      <td>Fowlerville</td>
      <td>$207,751</td>
      <td>13.84</td>
      <td>$15,011</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Livingston</td>
      <td>Howell</td>
      <td>$576,420</td>
      <td>36.64</td>
      <td>$15,732</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Livingston</td>
      <td>Pinckney</td>
      <td>$150,719</td>
      <td>11.37</td>
      <td>$13,256</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Macomb</td>
      <td>Armada</td>
      <td>$106,664</td>
      <td>7.21</td>
      <td>$14,794</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_funding = df_funding.rename(columns={'Community': 'COMMUNITY'})
```


```python
df_funding.loc[df_funding['COMMUNITY']=='Brandon Twp']
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
      <th>County</th>
      <th>COMMUNITY</th>
      <th>Annual Amount</th>
      <th>Road Miles</th>
      <th>Average Per Mile</th>
      <th>Unnamed: 5</th>
      <th>Unnamed: 6</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
</div>



Not all the cities from our original crash data are represented in our funding data


```python
len(df_funding)
```




    120




```python
result = pd.merge(df,df_funding,how='left', on='COMMUNITY')
```


```python
result.head()
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
      <th>Unnamed: 0</th>
      <th>ACOUNT</th>
      <th>ALCOHOL</th>
      <th>BCOUNT</th>
      <th>BICYCLE</th>
      <th>CARTODB_ID</th>
      <th>CCOUNT</th>
      <th>CNTNAME</th>
      <th>COMMERCIAL</th>
      <th>COMMUNITY</th>
      <th>...</th>
      <th>Y</th>
      <th>YCORD</th>
      <th>YEAR</th>
      <th>YOUNG</th>
      <th>County</th>
      <th>Annual Amount</th>
      <th>Road Miles</th>
      <th>Average Per Mile</th>
      <th>Unnamed: 5</th>
      <th>Unnamed: 6</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Washtenaw</td>
      <td>NaN</td>
      <td>Ann Arbor</td>
      <td>...</td>
      <td>42.287878</td>
      <td>42.28787</td>
      <td>2017</td>
      <td>0</td>
      <td>Washtenaw</td>
      <td>$7,535,530</td>
      <td>296.70</td>
      <td>$25,398</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Oakland</td>
      <td>NaN</td>
      <td>Brandon Twp</td>
      <td>...</td>
      <td>42.810271</td>
      <td>42.81026</td>
      <td>2017</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Oakland</td>
      <td>NaN</td>
      <td>Bloomfield Twp</td>
      <td>...</td>
      <td>42.615461</td>
      <td>42.61546</td>
      <td>2017</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Oakland</td>
      <td>NaN</td>
      <td>Orchard Lake Village</td>
      <td>...</td>
      <td>42.578827</td>
      <td>42.57882</td>
      <td>2017</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Livingston</td>
      <td>NaN</td>
      <td>Hartland Twp</td>
      <td>...</td>
      <td>42.656270</td>
      <td>42.65626</td>
      <td>2017</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 67 columns</p>
</div>




```python
len(result)
```




    709900




```python
result.groupby('Average Per Mile').size().sort_values(ascending =False)
```




    Average Per Mile
    $21,086    115539
    $21,519     23796
    $20,750     23681
    $17,127     18341
    $25,398     18250
    $20,736     18002
    $24,417     17505
    $16,196     17085
    $17,714     15760
    $17,795     11959
    $20,205     11847
    $18,210     10582
    $19,761     10435
    $18,627     10160
    $19,849     10128
    $22,508      9626
    $22,851      8590
    $18,385      7511
    $18,710      7470
    $18,235      6163
    $14,372      5958
    $20,253      5766
    $16,871      4704
    $18,874      4606
    $20,474      4391
    $32,256      4312
    $20,791      4300
    $14,715      3923
    $16,188      3745
    $19,519      3343
                ...  
    $17,430       530
    $15,920       529
    $14,503       494
    $14,983       474
    $17,953       463
    $18,172       459
    $13,952       401
    $17,990       359
    $12,525       343
    $16,313       298
    $13,131       290
    $13,965       266
    $11,944       224
    $15,011       219
    $16,727       218
    $13,256       199
    $11,354       199
    $13,864       170
    $10,463       154
    $13,948       128
    $13,452       124
    $12,711        98
    $14,614        89
    $9,113         76
    $14,794        61
    $7,884         39
    $10,603        29
    $11,498        22
    $10,925        17
    $8,188          5
    Length: 103, dtype: int64




```python
fig, ax = plt.subplots(figsize=(15,7))
result.groupby('Average Per Mile').size().plot(ax=ax)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1198aa6d8>





<img src="/assets/images/yield/output_91_1.png" width="100%">


We see here that we both don't have information for all of the cities in our crash data and that the most crashes are occuring in municipalities that fund their roads on average of 21,086.  The real issue here is that the different values are so highly specific that they are just representing the different cities. We need to bin these values


```python
result[['Currency']] = result[['Average Per Mile']].replace('[\$,]','',regex=True).astype(float)
```


```python
result.head()
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
      <th>Unnamed: 0</th>
      <th>ACOUNT</th>
      <th>ALCOHOL</th>
      <th>BCOUNT</th>
      <th>BICYCLE</th>
      <th>CARTODB_ID</th>
      <th>CCOUNT</th>
      <th>CNTNAME</th>
      <th>COMMERCIAL</th>
      <th>COMMUNITY</th>
      <th>...</th>
      <th>YCORD</th>
      <th>YEAR</th>
      <th>YOUNG</th>
      <th>County</th>
      <th>Annual Amount</th>
      <th>Road Miles</th>
      <th>Average Per Mile</th>
      <th>Unnamed: 5</th>
      <th>Unnamed: 6</th>
      <th>Currency</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Washtenaw</td>
      <td>NaN</td>
      <td>Ann Arbor</td>
      <td>...</td>
      <td>42.28787</td>
      <td>2017</td>
      <td>0</td>
      <td>Washtenaw</td>
      <td>$7,535,530</td>
      <td>296.70</td>
      <td>$25,398</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>25398.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Oakland</td>
      <td>NaN</td>
      <td>Brandon Twp</td>
      <td>...</td>
      <td>42.81026</td>
      <td>2017</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Oakland</td>
      <td>NaN</td>
      <td>Bloomfield Twp</td>
      <td>...</td>
      <td>42.61546</td>
      <td>2017</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Oakland</td>
      <td>NaN</td>
      <td>Orchard Lake Village</td>
      <td>...</td>
      <td>42.57882</td>
      <td>2017</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Livingston</td>
      <td>NaN</td>
      <td>Hartland Twp</td>
      <td>...</td>
      <td>42.65626</td>
      <td>2017</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 68 columns</p>
</div>




```python
result['bin'] = pd.cut(result['Currency'], [0, 5000, 10000,15000,20000,25000,30000])
```


```python
result.head()
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
      <th>Unnamed: 0</th>
      <th>ACOUNT</th>
      <th>ALCOHOL</th>
      <th>BCOUNT</th>
      <th>BICYCLE</th>
      <th>CARTODB_ID</th>
      <th>CCOUNT</th>
      <th>CNTNAME</th>
      <th>COMMERCIAL</th>
      <th>COMMUNITY</th>
      <th>...</th>
      <th>YEAR</th>
      <th>YOUNG</th>
      <th>County</th>
      <th>Annual Amount</th>
      <th>Road Miles</th>
      <th>Average Per Mile</th>
      <th>Unnamed: 5</th>
      <th>Unnamed: 6</th>
      <th>Currency</th>
      <th>bin</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Washtenaw</td>
      <td>NaN</td>
      <td>Ann Arbor</td>
      <td>...</td>
      <td>2017</td>
      <td>0</td>
      <td>Washtenaw</td>
      <td>$7,535,530</td>
      <td>296.70</td>
      <td>$25,398</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>25398.0</td>
      <td>(25000.0, 30000.0]</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Oakland</td>
      <td>NaN</td>
      <td>Brandon Twp</td>
      <td>...</td>
      <td>2017</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Oakland</td>
      <td>NaN</td>
      <td>Bloomfield Twp</td>
      <td>...</td>
      <td>2017</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Oakland</td>
      <td>NaN</td>
      <td>Orchard Lake Village</td>
      <td>...</td>
      <td>2017</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Livingston</td>
      <td>NaN</td>
      <td>Hartland Twp</td>
      <td>...</td>
      <td>2017</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 69 columns</p>
</div>




```python
result.groupby('bin').size().sort_values(ascending =False)
```




    bin
    (20000, 25000]    244713
    (15000, 20000]    194008
    (10000, 15000]     18789
    (25000, 30000]     18250
    (5000, 10000]       2130
    (0, 5000]              0
    dtype: int64




```python
fig, ax = plt.subplots(figsize=(15,7))
result.groupby('bin').size().plot(ax=ax)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1199966a0>





<img src="/assets/images/yield/output_98_1.png" width="100%">


## Ann Arbor

Let's look at a specific city in our data and see if the overarching trends are represented


```python
df_aa = df.loc[df['COMMUNITY']=='Ann Arbor']
```


```python
df_aa.head()
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
      <th>Unnamed: 0</th>
      <th>ACOUNT</th>
      <th>ALCOHOL</th>
      <th>BCOUNT</th>
      <th>BICYCLE</th>
      <th>CARTODB_ID</th>
      <th>CCOUNT</th>
      <th>CNTNAME</th>
      <th>COMMERCIAL</th>
      <th>COMMUNITY</th>
      <th>...</th>
      <th>UNITS</th>
      <th>WEATHER</th>
      <th>WEEKDAY</th>
      <th>WORK_ZONE</th>
      <th>X</th>
      <th>XCORD</th>
      <th>Y</th>
      <th>YCORD</th>
      <th>YEAR</th>
      <th>YOUNG</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Washtenaw</td>
      <td>NaN</td>
      <td>Ann Arbor</td>
      <td>...</td>
      <td>2</td>
      <td>5</td>
      <td>2</td>
      <td>NaN</td>
      <td>-83.771023</td>
      <td>-83.77102</td>
      <td>42.287878</td>
      <td>42.28787</td>
      <td>2017</td>
      <td>0</td>
    </tr>
    <tr>
      <th>21</th>
      <td>21</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Washtenaw</td>
      <td>NaN</td>
      <td>Ann Arbor</td>
      <td>...</td>
      <td>2</td>
      <td>1</td>
      <td>4</td>
      <td>NaN</td>
      <td>-83.707336</td>
      <td>-83.70734</td>
      <td>42.302537</td>
      <td>42.30253</td>
      <td>2017</td>
      <td>0</td>
    </tr>
    <tr>
      <th>52</th>
      <td>52</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>NaN</td>
      <td>1</td>
      <td>Washtenaw</td>
      <td>NaN</td>
      <td>Ann Arbor</td>
      <td>...</td>
      <td>2</td>
      <td>1</td>
      <td>3</td>
      <td>NaN</td>
      <td>-83.749675</td>
      <td>-83.74967</td>
      <td>42.252243</td>
      <td>42.25224</td>
      <td>2017</td>
      <td>0</td>
    </tr>
    <tr>
      <th>121</th>
      <td>121</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Washtenaw</td>
      <td>NaN</td>
      <td>Ann Arbor</td>
      <td>...</td>
      <td>2</td>
      <td>1</td>
      <td>6</td>
      <td>NaN</td>
      <td>-83.739154</td>
      <td>-83.73915</td>
      <td>42.240915</td>
      <td>42.24091</td>
      <td>2017</td>
      <td>1</td>
    </tr>
    <tr>
      <th>131</th>
      <td>131</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Washtenaw</td>
      <td>NaN</td>
      <td>Ann Arbor</td>
      <td>...</td>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>NaN</td>
      <td>-83.735003</td>
      <td>-83.73500</td>
      <td>42.285408</td>
      <td>42.28540</td>
      <td>2017</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 61 columns</p>
</div>




```python
len(df_aa)
```




    18250




```python
709000 / 237
```




    2991.5611814345993




```python
2991.5611814345993 / 709000
```




    0.0042194092827004225




```python
.42 * 237
```




    99.53999999999999



If all was equal, each city would have 2,991 crashes occur within their distinct city limits, but as mentioned above not all is equal.


```python
237 * 2991
```




    708867



We can see that 18,250 car cashes occurred within ann arbor city limits over the course of these five years in question.


```python
18250 / 709000
```




    0.025740479548660086



Each municipality should account for .4 percent of the crashes (if all was equal) but ann arbor is accounting for over 2.5 percent.  This matches where ann arbor fell on our crash total list.


```python
709000 * 0.025740479548660086
```




    18250.0




```python
aa_dates_result = df_aa.groupby('DATE_FULL').size().sort_values(ascending=False)
```


```python
aa_dates_result
```




    DATE_FULL
    11/19/2014    48
    01/01/2014    44
    12/11/2017    43
    03/07/2018    42
    12/18/2014    39
    01/27/2014    37
    01/12/2018    37
    03/13/2017    37
    11/21/2015    36
    04/17/2018    34
    01/05/2015    33
    02/24/2016    33
    01/09/2014    32
    01/28/2014    30
    02/05/2014    29
    02/09/2018    29
    03/12/2014    28
    01/29/2018    28
    11/02/2017    28
    01/09/2018    27
    03/01/2016    26
    01/16/2014    26
    01/23/2014    26
    11/21/2017    26
    11/04/2016    25
    01/29/2017    25
    01/09/2015    25
    11/18/2015    25
    01/22/2014    25
    10/31/2014    24
                  ..
    08/02/2015     2
    07/26/2015     2
    07/15/2018     2
    07/13/2014     2
    07/09/2016     2
    07/04/2018     2
    04/12/2014     2
    07/03/2016     2
    07/03/2015     2
    02/17/2018     2
    12/25/2016     1
    04/07/2014     1
    02/16/2015     1
    03/16/2014     1
    03/04/2018     1
    01/02/2015     1
    12/31/2016     1
    08/28/2016     1
    08/17/2014     1
    11/27/2014     1
    06/04/2017     1
    11/26/2015     1
    11/23/2017     1
    11/22/2018     1
    06/10/2018     1
    06/21/2015     1
    12/31/2017     1
    07/04/2015     1
    07/08/2018     1
    05/24/2015     1
    Length: 1823, dtype: int64



The day with the most crashes in ann arbor places third overall on the crash list for the entire region.


```python
fig, ax = plt.subplots(figsize=(15,7))
aa_result_dates = df_aa.groupby('DATE_FULL').size().plot(ax=ax)
```



<img src="/assets/images/yield/output_115_0.png" width="100%">


This figure follow the trends that appeared in the overall dates figure.  We see spikes in car crashes on select days throughout the winter months.


```python
fig, ax = plt.subplots(figsize=(15,7))
df_aa.groupby('HOUR').size().plot(ax=ax)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11cfe5898>





<img src="/assets/images/yield/output_117_1.png" width="100%">


The hourly distribution of crashes within the city follows the rush hour trend we identified in the total data

Ultimately, this sub sample of data seems to be representative of the full data.

## High severity crashes


```python
df.columns
```




    Index(['Unnamed: 0', 'ACOUNT', 'ALCOHOL', 'BCOUNT', 'BICYCLE', 'CARTODB_ID',
           'CCOUNT', 'CNTNAME', 'COMMERCIAL', 'COMMUNITY', 'CRASHID', 'CRSHTYPEO',
           'DATE_FULL', 'DAY', 'DEER', 'DISTRACTED', 'DIS_CTRL_I', 'DRUG',
           'ELDERLY', 'EMERGENCY', 'FALINKID', 'FID', 'HIGH_SEVER', 'HITNRUN',
           'HOUR', 'HWY_CLSS_C', 'INTERROAD', 'INTR_INVL_', 'JURIS', 'KCOUNT',
           'LANEDEPART', 'LIGHTING', 'MAINROAD', 'MONTH', 'MOTORCYCLE', 'MP',
           'NFC', 'OBJECTID', 'OCCUPANTS', 'PEDESTRIAN', 'PR', 'PROPDAMG',
           'REDLIGHTRU', 'ROADCONDIT', 'ROADLANES', 'SCHOOLBUS', 'SEMMCD',
           'SPEEDLIMIT', 'SURFACE', 'TIME_FULL', 'TRAIN', 'UNITS', 'WEATHER',
           'WEEKDAY', 'WORK_ZONE', 'X', 'XCORD', 'Y', 'YCORD', 'YEAR', 'YOUNG'],
          dtype='object')




```python
sev = df.loc[df['HIGH_SEVER']==1]
```


```python
len(sev)
```




    1782



## Detroit vs Livonia

Conducting some evaluation of the genralizability of clustering groups


```python
det = result.loc[result['COMMUNITY']=='Detroit']
```


```python
liv = result.loc[result['COMMUNITY']=='Livonia']
```


```python
det.head()
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
      <th>Unnamed: 0</th>
      <th>ACOUNT</th>
      <th>ALCOHOL</th>
      <th>BCOUNT</th>
      <th>BICYCLE</th>
      <th>CARTODB_ID</th>
      <th>CCOUNT</th>
      <th>CNTNAME</th>
      <th>COMMERCIAL</th>
      <th>COMMUNITY</th>
      <th>...</th>
      <th>YEAR</th>
      <th>YOUNG</th>
      <th>County</th>
      <th>Annual Amount</th>
      <th>Road Miles</th>
      <th>Average Per Mile</th>
      <th>Unnamed: 5</th>
      <th>Unnamed: 6</th>
      <th>Currency</th>
      <th>bin</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>16</th>
      <td>16</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Wayne</td>
      <td>NaN</td>
      <td>Detroit</td>
      <td>...</td>
      <td>2017</td>
      <td>0</td>
      <td>Wayne</td>
      <td>$54,202,186</td>
      <td>2,570.50</td>
      <td>$21,086</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>21086.0</td>
      <td>(20000, 25000]</td>
    </tr>
    <tr>
      <th>40</th>
      <td>40</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Wayne</td>
      <td>NaN</td>
      <td>Detroit</td>
      <td>...</td>
      <td>2017</td>
      <td>1</td>
      <td>Wayne</td>
      <td>$54,202,186</td>
      <td>2,570.50</td>
      <td>$21,086</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>21086.0</td>
      <td>(20000, 25000]</td>
    </tr>
    <tr>
      <th>41</th>
      <td>41</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Wayne</td>
      <td>NaN</td>
      <td>Detroit</td>
      <td>...</td>
      <td>2017</td>
      <td>0</td>
      <td>Wayne</td>
      <td>$54,202,186</td>
      <td>2,570.50</td>
      <td>$21,086</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>21086.0</td>
      <td>(20000, 25000]</td>
    </tr>
    <tr>
      <th>43</th>
      <td>43</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Wayne</td>
      <td>NaN</td>
      <td>Detroit</td>
      <td>...</td>
      <td>2017</td>
      <td>0</td>
      <td>Wayne</td>
      <td>$54,202,186</td>
      <td>2,570.50</td>
      <td>$21,086</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>21086.0</td>
      <td>(20000, 25000]</td>
    </tr>
    <tr>
      <th>60</th>
      <td>60</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>2</td>
      <td>Wayne</td>
      <td>NaN</td>
      <td>Detroit</td>
      <td>...</td>
      <td>2017</td>
      <td>0</td>
      <td>Wayne</td>
      <td>$54,202,186</td>
      <td>2,570.50</td>
      <td>$21,086</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>21086.0</td>
      <td>(20000, 25000]</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 69 columns</p>
</div>




```python
len(det)
```




    115539




```python
len(liv)
```




    18341




```python
det.columns
```




    Index(['Unnamed: 0', 'ACOUNT', 'ALCOHOL', 'BCOUNT', 'BICYCLE', 'CARTODB_ID',
           'CCOUNT', 'CNTNAME', 'COMMERCIAL', 'COMMUNITY', 'CRASHID', 'CRSHTYPEO',
           'DATE_FULL', 'DAY', 'DEER', 'DISTRACTED', 'DIS_CTRL_I', 'DRUG',
           'ELDERLY', 'EMERGENCY', 'FALINKID', 'FID', 'HIGH_SEVER', 'HITNRUN',
           'HOUR', 'HWY_CLSS_C', 'INTERROAD', 'INTR_INVL_', 'JURIS', 'KCOUNT',
           'LANEDEPART', 'LIGHTING', 'MAINROAD', 'MONTH', 'MOTORCYCLE', 'MP',
           'NFC', 'OBJECTID', 'OCCUPANTS', 'PEDESTRIAN', 'PR', 'PROPDAMG',
           'REDLIGHTRU', 'ROADCONDIT', 'ROADLANES', 'SCHOOLBUS', 'SEMMCD',
           'SPEEDLIMIT', 'SURFACE', 'TIME_FULL', 'TRAIN', 'UNITS', 'WEATHER',
           'WEEKDAY', 'WORK_ZONE', 'X', 'XCORD', 'Y', 'YCORD', 'YEAR', 'YOUNG',
           'County', 'Annual Amount', 'Road Miles', 'Average Per Mile',
           'Unnamed: 5', 'Unnamed: 6', 'Currency', 'bin'],
          dtype='object')



Let's compare and contrast the rates at which key statistics occur.


```python
det_bike = det.loc[det['BICYCLE']==1]
len(det_bike)
```




    848




```python
848 / 115539
```




    0.007339513064852561




```python
liv_bike = liv.loc[liv['BICYCLE']==1]
len(liv_bike)
```




    117




```python
117 / 18341
```




    0.006379150537048144




```python
det_bus = det.loc[det['SCHOOLBUS']==1]
len(det_bus)
```




    320




```python
320 / 115539
```




    0.0027696275716424757




```python
liv_bus = liv.loc[liv['SCHOOLBUS']==1]
len(liv_bus)
```




    79




```python
79 / 18341
```




    0.004307289678861567




```python
det_moto = det.loc[det['MOTORCYCLE']==1]
len(det_moto)
```




    1068




```python
1068 / 115539
```




    0.009243632020356763




```python
liv_moto = liv.loc[liv['MOTORCYCLE']==1]
len(liv_moto)
```




    126




```python
126 / 18341
```




    0.006869854424513385




```python
det_old = det.loc[det['ELDERLY']==1]
```


```python
len(det_old)
```




    13205




```python
13205 / 115539
```




    0.11429041276105904




```python
liv_old = liv.loc[liv['ELDERLY']==1]
```


```python
len(liv_old)
```




    3671




```python
3671 / 18341
```




    0.20015266343165586




```python
det_young = det.loc[det['YOUNG']==1]
```


```python
len(det_young)
```




    29981




```python
29981 / 115539
```




    0.25948813820441585




```python
liv_young = liv.loc[liv['YOUNG']==1]
```


```python
len(liv_young)
```




    6301




```python
6301 / 18341
```




    0.34354724387983204




```python
det_alc = det.loc[det['ALCOHOL']==1]
```


```python
len(det_alc)
```




    2323




```python
2323 / 115539
```




    0.020105765152892096




```python
liv_alc = liv.loc[liv['ALCOHOL']==1]
```


```python
len(liv_alc)
```




    470




```python
470 / 18341
```




    0.025625647456518182




```python
det_drug = det.loc[det['DRUG']==1]
```


```python
len(det_drug)
```




    626




```python
626 / 115539
```




    0.005418083937025593




```python
liv_drug = liv.loc[liv['DRUG']==1]
```


```python
len(liv_drug)
```




    149




```python
149 / 18341
```




    0.008123875470257893




```python
det_sev = det.loc[det['CRSHTYPEO']==1]
```


```python
len(det_sev)
```




    16170




```python
16170 / 115539
```




    0.13995274322955886




```python
liv_sev = liv.loc[liv['CRSHTYPEO']==1]
```


```python
len(liv_sev)
```




    1782




```python
1782 / 18341
```




    0.09715936971811788




```python
det_dis = det.loc[det['DISTRACTED']==1]
```


```python
len(det_dis)
```




    3678




```python
3678 / 115539
```




    0.031833406901565706




```python
liv_dis = liv.loc[liv['DISTRACTED']==1]
```


```python
len(liv_dis)
```




    577




```python
577 / 18341
```




    0.03145957145193828




```python
det['bin']
```




    16        (20000, 25000]
    40        (20000, 25000]
    41        (20000, 25000]
    43        (20000, 25000]
    60        (20000, 25000]
    68        (20000, 25000]
    76        (20000, 25000]
    94        (20000, 25000]
    108       (20000, 25000]
    109       (20000, 25000]
    128       (20000, 25000]
    156       (20000, 25000]
    175       (20000, 25000]
    179       (20000, 25000]
    180       (20000, 25000]
    182       (20000, 25000]
    190       (20000, 25000]
    192       (20000, 25000]
    198       (20000, 25000]
    209       (20000, 25000]
    214       (20000, 25000]
    218       (20000, 25000]
    224       (20000, 25000]
    235       (20000, 25000]
    245       (20000, 25000]
    247       (20000, 25000]
    250       (20000, 25000]
    251       (20000, 25000]
    254       (20000, 25000]
    258       (20000, 25000]
                   ...      
    709804    (20000, 25000]
    709817    (20000, 25000]
    709818    (20000, 25000]
    709824    (20000, 25000]
    709825    (20000, 25000]
    709827    (20000, 25000]
    709828    (20000, 25000]
    709830    (20000, 25000]
    709831    (20000, 25000]
    709833    (20000, 25000]
    709834    (20000, 25000]
    709840    (20000, 25000]
    709842    (20000, 25000]
    709851    (20000, 25000]
    709852    (20000, 25000]
    709855    (20000, 25000]
    709857    (20000, 25000]
    709858    (20000, 25000]
    709863    (20000, 25000]
    709865    (20000, 25000]
    709866    (20000, 25000]
    709870    (20000, 25000]
    709875    (20000, 25000]
    709878    (20000, 25000]
    709879    (20000, 25000]
    709884    (20000, 25000]
    709889    (20000, 25000]
    709895    (20000, 25000]
    709897    (20000, 25000]
    709898    (20000, 25000]
    Name: bin, Length: 115539, dtype: category
    Categories (6, interval[int64]): [(0, 5000] < (5000, 10000] < (10000, 15000] < (15000, 20000] < (20000, 25000] < (25000, 30000]]




```python
liv['bin']
```




    15        (15000, 20000]
    27        (15000, 20000]
    72        (15000, 20000]
    98        (15000, 20000]
    107       (15000, 20000]
    133       (15000, 20000]
    162       (15000, 20000]
    178       (15000, 20000]
    197       (15000, 20000]
    213       (15000, 20000]
    276       (15000, 20000]
    285       (15000, 20000]
    309       (15000, 20000]
    340       (15000, 20000]
    357       (15000, 20000]
    371       (15000, 20000]
    396       (15000, 20000]
    429       (15000, 20000]
    450       (15000, 20000]
    451       (15000, 20000]
    461       (15000, 20000]
    464       (15000, 20000]
    470       (15000, 20000]
    476       (15000, 20000]
    485       (15000, 20000]
    487       (15000, 20000]
    489       (15000, 20000]
    495       (15000, 20000]
    508       (15000, 20000]
    510       (15000, 20000]
                   ...      
    708660    (15000, 20000]
    708677    (15000, 20000]
    708718    (15000, 20000]
    708720    (15000, 20000]
    708787    (15000, 20000]
    708864    (15000, 20000]
    708902    (15000, 20000]
    708924    (15000, 20000]
    709028    (15000, 20000]
    709042    (15000, 20000]
    709079    (15000, 20000]
    709081    (15000, 20000]
    709092    (15000, 20000]
    709093    (15000, 20000]
    709149    (15000, 20000]
    709162    (15000, 20000]
    709220    (15000, 20000]
    709269    (15000, 20000]
    709323    (15000, 20000]
    709337    (15000, 20000]
    709427    (15000, 20000]
    709441    (15000, 20000]
    709443    (15000, 20000]
    709590    (15000, 20000]
    709618    (15000, 20000]
    709794    (15000, 20000]
    709822    (15000, 20000]
    709850    (15000, 20000]
    709853    (15000, 20000]
    709881    (15000, 20000]
    Name: bin, Length: 18341, dtype: category
    Categories (6, interval[int64]): [(0, 5000] < (5000, 10000] < (10000, 15000] < (15000, 20000] < (20000, 25000] < (25000, 30000]]




```python

```


```python

```
