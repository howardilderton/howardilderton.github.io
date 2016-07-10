title: "Indigo, minimalist jekyll theme"
layout: post
date: 2016-01-23 22:10
tag: jekyll
image: /assets/images/jekyll-logo-light-solid.png
headerImage: true
projects: true
hidden: true # don't count this post in blog pagination
description: "This is a simple and minimalist template for Jekyll for those who likes to eat noodles."
jemoji: '<img class="emoji" title=":ramen:" alt=":ramen:" src="https://assets.github.com/images/icons/emoji/unicode/1f35c.png" height="20" width="20" align="absmiddle">'
author: johndoe
externalLink: false


# Project 2
## Step 1: Exploring your data.

##### Load your data in using Pandas and start to explore. Save all of your early exploration code here and include in your final submission.


```python
#initialize libraries and functions
import pandas as pd
import numpy as np
import seaborn as sns
import html5lib
import pylab as pl
import scipy.stats as stats
%matplotlib inline
```


```python
#import chart data into dataframe
df = pd.read_csv('/home/howard/DS/DSI-HK-1/projects/project-02/assets/billboard.csv')
```


```python
#initial exploration - columns
df.columns
```




    Index([u'year', u'artist.inverted', u'track', u'time', u'genre',
           u'date.entered', u'date.peaked', u'x1st.week', u'x2nd.week',
           u'x3rd.week', u'x4th.week', u'x5th.week', u'x6th.week', u'x7th.week',
           u'x8th.week', u'x9th.week', u'x10th.week', u'x11th.week', u'x12th.week',
           u'x13th.week', u'x14th.week', u'x15th.week', u'x16th.week',
           u'x17th.week', u'x18th.week', u'x19th.week', u'x20th.week',
           u'x21st.week', u'x22nd.week', u'x23rd.week', u'x24th.week',
           u'x25th.week', u'x26th.week', u'x27th.week', u'x28th.week',
           u'x29th.week', u'x30th.week', u'x31st.week', u'x32nd.week',
           u'x33rd.week', u'x34th.week', u'x35th.week', u'x36th.week',
           u'x37th.week', u'x38th.week', u'x39th.week', u'x40th.week',
           u'x41st.week', u'x42nd.week', u'x43rd.week', u'x44th.week',
           u'x45th.week', u'x46th.week', u'x47th.week', u'x48th.week',
           u'x49th.week', u'x50th.week', u'x51st.week', u'x52nd.week',
           u'x53rd.week', u'x54th.week', u'x55th.week', u'x56th.week',
           u'x57th.week', u'x58th.week', u'x59th.week', u'x60th.week',
           u'x61st.week', u'x62nd.week', u'x63rd.week', u'x64th.week',
           u'x65th.week', u'x66th.week', u'x67th.week', u'x68th.week',
           u'x69th.week', u'x70th.week', u'x71st.week', u'x72nd.week',
           u'x73rd.week', u'x74th.week', u'x75th.week', u'x76th.week'],
          dtype='object')




```python
#initial exploration - shape
df.shape
```




    (317, 83)




```python
#initial exploration - head
df.head(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>artist.inverted</th>
      <th>track</th>
      <th>time</th>
      <th>genre</th>
      <th>date.entered</th>
      <th>date.peaked</th>
      <th>x1st.week</th>
      <th>x2nd.week</th>
      <th>x3rd.week</th>
      <th>...</th>
      <th>x67th.week</th>
      <th>x68th.week</th>
      <th>x69th.week</th>
      <th>x70th.week</th>
      <th>x71st.week</th>
      <th>x72nd.week</th>
      <th>x73rd.week</th>
      <th>x74th.week</th>
      <th>x75th.week</th>
      <th>x76th.week</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2000</td>
      <td>Destiny's Child</td>
      <td>Independent Women Part I</td>
      <td>3:38</td>
      <td>Rock</td>
      <td>2000-09-23</td>
      <td>2000-11-18</td>
      <td>78</td>
      <td>63.0</td>
      <td>49.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>1</th>
      <td>2000</td>
      <td>Santana</td>
      <td>Maria, Maria</td>
      <td>4:18</td>
      <td>Rock</td>
      <td>2000-02-12</td>
      <td>2000-04-08</td>
      <td>15</td>
      <td>8.0</td>
      <td>6.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <td>2000</td>
      <td>Savage Garden</td>
      <td>I Knew I Loved You</td>
      <td>4:07</td>
      <td>Rock</td>
      <td>1999-10-23</td>
      <td>2000-01-29</td>
      <td>71</td>
      <td>48.0</td>
      <td>43.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
<p>3 rows × 83 columns</p>
</div>




```python
#initial exploration - tail
df.tail(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>artist.inverted</th>
      <th>track</th>
      <th>time</th>
      <th>genre</th>
      <th>date.entered</th>
      <th>date.peaked</th>
      <th>x1st.week</th>
      <th>x2nd.week</th>
      <th>x3rd.week</th>
      <th>...</th>
      <th>x67th.week</th>
      <th>x68th.week</th>
      <th>x69th.week</th>
      <th>x70th.week</th>
      <th>x71st.week</th>
      <th>x72nd.week</th>
      <th>x73rd.week</th>
      <th>x74th.week</th>
      <th>x75th.week</th>
      <th>x76th.week</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>314</th>
      <td>2000</td>
      <td>Zombie Nation</td>
      <td>Kernkraft 400</td>
      <td>3:30</td>
      <td>Rock</td>
      <td>2000-09-02</td>
      <td>2000-09-02</td>
      <td>99</td>
      <td>99.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>315</th>
      <td>2000</td>
      <td>Eastsidaz, The</td>
      <td>Got Beef</td>
      <td>3:58</td>
      <td>Rap</td>
      <td>2000-07-01</td>
      <td>2000-07-01</td>
      <td>99</td>
      <td>99.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>316</th>
      <td>2000</td>
      <td>Fragma</td>
      <td>Toca's Miracle</td>
      <td>3:22</td>
      <td>R&amp;B</td>
      <td>2000-10-28</td>
      <td>2000-10-28</td>
      <td>99</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
<p>3 rows × 83 columns</p>
</div>




```python
#initial exploration - describe
df.describe()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>x1st.week</th>
      <th>x2nd.week</th>
      <th>x3rd.week</th>
      <th>x4th.week</th>
      <th>x5th.week</th>
      <th>x6th.week</th>
      <th>x7th.week</th>
      <th>x8th.week</th>
      <th>x9th.week</th>
      <th>...</th>
      <th>x67th.week</th>
      <th>x68th.week</th>
      <th>x69th.week</th>
      <th>x70th.week</th>
      <th>x71st.week</th>
      <th>x72nd.week</th>
      <th>x73rd.week</th>
      <th>x74th.week</th>
      <th>x75th.week</th>
      <th>x76th.week</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>317.0</td>
      <td>317.000000</td>
      <td>312.000000</td>
      <td>307.000000</td>
      <td>300.000000</td>
      <td>292.000000</td>
      <td>280.000000</td>
      <td>269.000000</td>
      <td>260.000000</td>
      <td>253.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2000.0</td>
      <td>79.958991</td>
      <td>71.173077</td>
      <td>65.045603</td>
      <td>59.763333</td>
      <td>56.339041</td>
      <td>52.360714</td>
      <td>49.219331</td>
      <td>47.119231</td>
      <td>46.343874</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>std</th>
      <td>0.0</td>
      <td>14.686865</td>
      <td>18.200443</td>
      <td>20.752302</td>
      <td>22.324619</td>
      <td>23.780022</td>
      <td>24.473273</td>
      <td>25.654279</td>
      <td>26.370782</td>
      <td>27.136419</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>min</th>
      <td>2000.0</td>
      <td>15.000000</td>
      <td>8.000000</td>
      <td>6.000000</td>
      <td>5.000000</td>
      <td>2.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>25%</th>
      <td>2000.0</td>
      <td>74.000000</td>
      <td>63.000000</td>
      <td>53.000000</td>
      <td>44.750000</td>
      <td>38.750000</td>
      <td>33.750000</td>
      <td>30.000000</td>
      <td>27.000000</td>
      <td>26.000000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>50%</th>
      <td>2000.0</td>
      <td>81.000000</td>
      <td>73.000000</td>
      <td>66.000000</td>
      <td>61.000000</td>
      <td>57.000000</td>
      <td>51.500000</td>
      <td>47.000000</td>
      <td>45.500000</td>
      <td>42.000000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>75%</th>
      <td>2000.0</td>
      <td>91.000000</td>
      <td>84.000000</td>
      <td>79.000000</td>
      <td>76.000000</td>
      <td>73.250000</td>
      <td>72.250000</td>
      <td>67.000000</td>
      <td>67.000000</td>
      <td>67.000000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>max</th>
      <td>2000.0</td>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>99.000000</td>
      <td>100.000000</td>
      <td>99.000000</td>
      <td>100.000000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
<p>8 rows × 77 columns</p>
</div>




```python
#initial exploration - describe columns 25:
df.ix[:,25:].describe()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>x19th.week</th>
      <th>x20th.week</th>
      <th>x21st.week</th>
      <th>x22nd.week</th>
      <th>x23rd.week</th>
      <th>x24th.week</th>
      <th>x25th.week</th>
      <th>x26th.week</th>
      <th>x27th.week</th>
      <th>x28th.week</th>
      <th>...</th>
      <th>x67th.week</th>
      <th>x68th.week</th>
      <th>x69th.week</th>
      <th>x70th.week</th>
      <th>x71st.week</th>
      <th>x72nd.week</th>
      <th>x73rd.week</th>
      <th>x74th.week</th>
      <th>x75th.week</th>
      <th>x76th.week</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>156.000000</td>
      <td>146.000000</td>
      <td>65.000000</td>
      <td>55.000000</td>
      <td>48.00000</td>
      <td>46.000000</td>
      <td>38.000000</td>
      <td>36.00000</td>
      <td>29.000000</td>
      <td>24.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>53.166667</td>
      <td>54.267123</td>
      <td>26.184615</td>
      <td>25.636364</td>
      <td>23.81250</td>
      <td>26.782609</td>
      <td>26.131579</td>
      <td>28.00000</td>
      <td>27.344828</td>
      <td>25.000000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>std</th>
      <td>33.022540</td>
      <td>32.890475</td>
      <td>20.232162</td>
      <td>21.127798</td>
      <td>18.23564</td>
      <td>18.556716</td>
      <td>18.737404</td>
      <td>19.14904</td>
      <td>19.736254</td>
      <td>16.229335</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>min</th>
      <td>1.000000</td>
      <td>2.000000</td>
      <td>3.000000</td>
      <td>3.000000</td>
      <td>3.00000</td>
      <td>3.000000</td>
      <td>2.000000</td>
      <td>1.00000</td>
      <td>1.000000</td>
      <td>2.000000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>25%</th>
      <td>20.750000</td>
      <td>22.250000</td>
      <td>10.000000</td>
      <td>9.000000</td>
      <td>10.00000</td>
      <td>12.000000</td>
      <td>12.250000</td>
      <td>13.75000</td>
      <td>12.000000</td>
      <td>14.500000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>50%</th>
      <td>55.500000</td>
      <td>58.500000</td>
      <td>24.000000</td>
      <td>21.000000</td>
      <td>20.50000</td>
      <td>21.500000</td>
      <td>22.500000</td>
      <td>26.00000</td>
      <td>26.000000</td>
      <td>23.500000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>75%</th>
      <td>85.000000</td>
      <td>87.000000</td>
      <td>35.000000</td>
      <td>36.500000</td>
      <td>36.00000</td>
      <td>40.500000</td>
      <td>38.250000</td>
      <td>40.25000</td>
      <td>38.000000</td>
      <td>37.500000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>max</th>
      <td>99.000000</td>
      <td>100.000000</td>
      <td>97.000000</td>
      <td>100.000000</td>
      <td>91.00000</td>
      <td>91.000000</td>
      <td>90.000000</td>
      <td>89.00000</td>
      <td>86.000000</td>
      <td>58.000000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
<p>8 rows × 58 columns</p>
</div>




```python
#count by genre
df['genre'].value_counts()
```




    Rock           137
    Country         74
    Rap             58
    R&B             23
    Pop              9
    Latin            9
    Electronica      4
    Gospel           1
    Jazz             1
    Reggae           1
    Name: genre, dtype: int64



##### Write a brief description of your data, and any interesting observations you've made thus far. 

317 rows x 83 columns

Dataset reflects Track Title, Artist and Track Length for Tracks which peaked in the Top 100 during the year 2000
Some tracks were entered in 1999 but peaked in 2000

NaN data assumed to reflect track has fallen out of top 100
Some blank fields - assumed to reflect track has fallen out of top 100

## Step 2: Clean your data.

##### Do some rudimentary cleaning. Rename any columns that are poorly named, shorten any strings that may be too long, fill in any missing values. Explain your rationale for the way you choose to "impute" the missing data.


```python
#remove columns with no data, tidy headers
#NaNs and BLANKS left as is - assumed to indicate track has dropped out of the top 100

df_clean = df.dropna(axis=1, how='all')
print df.shape
print df_clean.shape
```

    (317, 83)
    (317, 72)



```python
#update column header
df_clean.columns = (u'year', u'artist', u'track', u'time', u'genre',
       u'entered', u'peaked', u'x1st', u'x2nd',
       u'x3rd', u'x4th', u'x5th', u'x6th', u'x7th',
       u'x8th', u'x9th', u'x10th', u'x11th', u'x12th',
       u'x13th', u'x14th', u'x15th', u'x16th',
       u'x17th', u'x18th', u'x19th', u'x20th',
       u'x21st', u'x22nd', u'x23rd', u'x24th',
       u'x25th', u'x26th', u'x27th', u'x28th',
       u'x29th', u'x30th', u'x31st', u'x32nd',
       u'x33rd', u'x34th', u'x35th', u'x36th',
       u'x37th', u'x38th', u'x39th', u'x40th',
       u'x41st', u'x42nd', u'x43rd', u'x44th',
       u'x45th', u'x46th', u'x47th', u'x48th',
       u'x49th', u'x50th', u'x51st', u'x52nd',
       u'x53rd', u'x54th', u'x55th', u'x56th',
       u'x57th', u'x58th', u'x59th', u'x60th',
       u'x61st', u'x62nd', u'x63rd', u'x64th',
       u'x65th')
```


```python
df_artist = pd.read_csv('artist_info.csv')
```


```python
df_artist.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>artist.inverted</th>
      <th>artist.gen</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Destiny's Child</td>
      <td>group</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Santana</td>
      <td>male</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Savage Garden</td>
      <td>group</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Madonna</td>
      <td>female</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Aguilera, Christina</td>
      <td>female</td>
    </tr>
  </tbody>
</table>
</div>




```python
#pd.concat([df_clean,df_artist],join_axes=['artist','artist.inverted'])
df_artist['artist.gen'].value_counts()
```




    male      126
    group     108
    female     83
    Name: artist.gen, dtype: int64




```python
print df_artist.shape
```

    (317, 2)


##### Using Pandas' built in `melt` function, pivot the weekly ranking data to be long rather than wide. As a result, you will have removed the 72 'week' columns and replace it with two: Week and Ranking. There will now be multiple entries for each song, one for each week on the Billboard rankings.


```python
#create long dataframe using track, weekly_position
week_cols = df_clean.columns[7:]
weekly_tracks = pd.melt(df_clean, id_vars=['track'], value_vars = [i for i in week_cols])
weekly_tracks = weekly_tracks.dropna(how='any')
```


```python
#tracks in charts for longest period
weekly_tracks['track'].value_counts().head(10)
```




    Higher                        57
    Amazed                        55
    Breathe                       53
    Kryptonite                    53
    With Arms Wide Open           47
    I Wanna Know                  44
    Everything You Want           41
    Bent                          39
    He Wasn't Man Enough          37
    (Hot S**t) Country Grammar    34
    Name: track, dtype: int64




```python
#create long dataframe using genre, weekly_position
weekly_genre = pd.melt(df_clean, id_vars=['genre'], value_vars = [i for i in week_cols])
weekly_genre.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>genre</th>
      <th>variable</th>
      <th>value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Rock</td>
      <td>x1st</td>
      <td>78.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Rock</td>
      <td>x1st</td>
      <td>15.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Rock</td>
      <td>x1st</td>
      <td>71.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Rock</td>
      <td>x1st</td>
      <td>41.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rock</td>
      <td>x1st</td>
      <td>57.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
weekly_genre_grouped = weekly_genre.groupby(['genre', 'variable'])
weekly_genre_grouped.mean().head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>value</th>
    </tr>
    <tr>
      <th>genre</th>
      <th>variable</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="5" valign="top">Country</th>
      <th>x10th</th>
      <td>52.377049</td>
    </tr>
    <tr>
      <th>x11th</th>
      <td>51.016949</td>
    </tr>
    <tr>
      <th>x12th</th>
      <td>50.714286</td>
    </tr>
    <tr>
      <th>x13th</th>
      <td>52.301887</td>
    </tr>
    <tr>
      <th>x14th</th>
      <td>55.333333</td>
    </tr>
  </tbody>
</table>
</div>




```python
#average position by genre
pd.pivot_table(weekly_genre, index=["genre"],values=["value"],aggfunc=np.mean)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>value</th>
    </tr>
    <tr>
      <th>genre</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Country</th>
      <td>61.687500</td>
    </tr>
    <tr>
      <th>Electronica</th>
      <td>62.847222</td>
    </tr>
    <tr>
      <th>Gospel</th>
      <td>67.750000</td>
    </tr>
    <tr>
      <th>Jazz</th>
      <td>51.800000</td>
    </tr>
    <tr>
      <th>Latin</th>
      <td>47.653179</td>
    </tr>
    <tr>
      <th>Pop</th>
      <td>54.963504</td>
    </tr>
    <tr>
      <th>R&amp;B</th>
      <td>67.632184</td>
    </tr>
    <tr>
      <th>Rap</th>
      <td>56.236559</td>
    </tr>
    <tr>
      <th>Reggae</th>
      <td>72.400000</td>
    </tr>
    <tr>
      <th>Rock</th>
      <td>42.206803</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_clean.groupby(['genre']).mean()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>x1st</th>
      <th>x2nd</th>
      <th>x3rd</th>
      <th>x4th</th>
      <th>x5th</th>
      <th>x6th</th>
      <th>x7th</th>
      <th>x8th</th>
      <th>x9th</th>
      <th>...</th>
      <th>x56th</th>
      <th>x57th</th>
      <th>x58th</th>
      <th>x59th</th>
      <th>x60th</th>
      <th>x61st</th>
      <th>x62nd</th>
      <th>x63rd</th>
      <th>x64th</th>
      <th>x65th</th>
    </tr>
    <tr>
      <th>genre</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
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
      <th>Country</th>
      <td>2000.0</td>
      <td>82.405405</td>
      <td>75.256757</td>
      <td>71.808219</td>
      <td>68.309859</td>
      <td>65.271429</td>
      <td>62.357143</td>
      <td>57.692308</td>
      <td>54.859375</td>
      <td>52.983871</td>
      <td>...</td>
      <td>25.0</td>
      <td>26.0</td>
      <td>31.0</td>
      <td>32.0</td>
      <td>37.0</td>
      <td>42.0</td>
      <td>42.0</td>
      <td>45.0</td>
      <td>50.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Electronica</th>
      <td>2000.0</td>
      <td>84.500000</td>
      <td>71.000000</td>
      <td>64.000000</td>
      <td>61.000000</td>
      <td>57.000000</td>
      <td>54.000000</td>
      <td>54.500000</td>
      <td>52.250000</td>
      <td>51.500000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>Gospel</th>
      <td>2000.0</td>
      <td>76.000000</td>
      <td>76.000000</td>
      <td>74.000000</td>
      <td>69.000000</td>
      <td>68.000000</td>
      <td>67.000000</td>
      <td>61.000000</td>
      <td>58.000000</td>
      <td>57.000000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>Jazz</th>
      <td>2000.0</td>
      <td>89.000000</td>
      <td>89.000000</td>
      <td>7.000000</td>
      <td>8.000000</td>
      <td>66.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>Latin</th>
      <td>2000.0</td>
      <td>73.222222</td>
      <td>64.333333</td>
      <td>58.777778</td>
      <td>52.666667</td>
      <td>52.000000</td>
      <td>42.625000</td>
      <td>38.500000</td>
      <td>39.000000</td>
      <td>39.625000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>Pop</th>
      <td>2000.0</td>
      <td>79.222222</td>
      <td>68.000000</td>
      <td>65.500000</td>
      <td>60.333333</td>
      <td>52.125000</td>
      <td>40.285714</td>
      <td>36.142857</td>
      <td>33.857143</td>
      <td>36.285714</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>R&amp;B</th>
      <td>2000.0</td>
      <td>84.086957</td>
      <td>74.095238</td>
      <td>67.190476</td>
      <td>60.894737</td>
      <td>61.473684</td>
      <td>56.000000</td>
      <td>58.294118</td>
      <td>63.294118</td>
      <td>62.062500</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>Rap</th>
      <td>2000.0</td>
      <td>85.172414</td>
      <td>76.228070</td>
      <td>68.781818</td>
      <td>63.925926</td>
      <td>60.384615</td>
      <td>55.714286</td>
      <td>53.723404</td>
      <td>50.255814</td>
      <td>51.976744</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>Reggae</th>
      <td>2000.0</td>
      <td>72.000000</td>
      <td>72.000000</td>
      <td>63.000000</td>
      <td>56.000000</td>
      <td>62.000000</td>
      <td>63.000000</td>
      <td>54.000000</td>
      <td>60.000000</td>
      <td>69.000000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>Rock</th>
      <td>2000.0</td>
      <td>76.116788</td>
      <td>66.852941</td>
      <td>60.298507</td>
      <td>54.015267</td>
      <td>49.330709</td>
      <td>45.894309</td>
      <td>42.689076</td>
      <td>40.234783</td>
      <td>38.819820</td>
      <td>...</td>
      <td>26.0</td>
      <td>29.0</td>
      <td>32.0</td>
      <td>39.0</td>
      <td>39.0</td>
      <td>43.0</td>
      <td>47.0</td>
      <td>50.0</td>
      <td>50.0</td>
      <td>49.0</td>
    </tr>
  </tbody>
</table>
<p>10 rows × 66 columns</p>
</div>




```python
df_audio = pd.read_csv('spotify_audio_data.csv')

```


```python
df_audio.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>track</th>
      <th>ID</th>
      <th>acousticness</th>
      <th>analysis_url</th>
      <th>danceability</th>
      <th>duration_ms</th>
      <th>energy</th>
      <th>id</th>
      <th>instrumentalness</th>
      <th>key</th>
      <th>liveness</th>
      <th>loudness</th>
      <th>mode</th>
      <th>speechiness</th>
      <th>tempo</th>
      <th>time_signature</th>
      <th>track_href</th>
      <th>type</th>
      <th>uri</th>
      <th>valence</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Independent Women Part I</td>
      <td>7JuMBlUywiUQdgjYtpJvsf</td>
      <td>0.34700</td>
      <td>https://api.spotify.com/v1/audio-analysis/7JuM...</td>
      <td>0.742</td>
      <td>221160</td>
      <td>0.591</td>
      <td>7JuMBlUywiUQdgjYtpJvsf</td>
      <td>0.000005</td>
      <td>6</td>
      <td>0.1680</td>
      <td>-3.780</td>
      <td>0</td>
      <td>0.2000</td>
      <td>97.958</td>
      <td>4</td>
      <td>https://api.spotify.com/v1/tracks/7JuMBlUywiUQ...</td>
      <td>audio_features</td>
      <td>spotify:track:7JuMBlUywiUQdgjYtpJvsf</td>
      <td>0.939</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Maria, Maria</td>
      <td>3fucYASejkSMwtAYjFRKlF</td>
      <td>0.04850</td>
      <td>https://api.spotify.com/v1/audio-analysis/3fuc...</td>
      <td>0.779</td>
      <td>262160</td>
      <td>0.631</td>
      <td>3fucYASejkSMwtAYjFRKlF</td>
      <td>0.003160</td>
      <td>2</td>
      <td>0.0349</td>
      <td>-5.314</td>
      <td>1</td>
      <td>0.1150</td>
      <td>97.927</td>
      <td>4</td>
      <td>https://api.spotify.com/v1/tracks/3fucYASejkSM...</td>
      <td>audio_features</td>
      <td>spotify:track:3fucYASejkSMwtAYjFRKlF</td>
      <td>0.666</td>
    </tr>
    <tr>
      <th>2</th>
      <td>I Knew I Loved You</td>
      <td>0dQ8sFlmQakH1r2r9IqlYH</td>
      <td>0.30700</td>
      <td>https://api.spotify.com/v1/audio-analysis/0dQ8...</td>
      <td>0.556</td>
      <td>251253</td>
      <td>0.517</td>
      <td>0dQ8sFlmQakH1r2r9IqlYH</td>
      <td>0.001150</td>
      <td>9</td>
      <td>0.0770</td>
      <td>-8.769</td>
      <td>1</td>
      <td>0.0287</td>
      <td>169.938</td>
      <td>4</td>
      <td>https://api.spotify.com/v1/tracks/0dQ8sFlmQakH...</td>
      <td>audio_features</td>
      <td>spotify:track:0dQ8sFlmQakH1r2r9IqlYH</td>
      <td>0.779</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Music</td>
      <td>27cXevtj5VflsCUAZwr9eI</td>
      <td>0.00153</td>
      <td>https://api.spotify.com/v1/audio-analysis/27cX...</td>
      <td>0.738</td>
      <td>225813</td>
      <td>0.852</td>
      <td>27cXevtj5VflsCUAZwr9eI</td>
      <td>0.089500</td>
      <td>7</td>
      <td>0.1780</td>
      <td>-6.130</td>
      <td>1</td>
      <td>0.0766</td>
      <td>119.735</td>
      <td>4</td>
      <td>https://api.spotify.com/v1/tracks/27cXevtj5Vfl...</td>
      <td>audio_features</td>
      <td>spotify:track:27cXevtj5VflsCUAZwr9eI</td>
      <td>0.841</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Come On Over Baby (All I Want Is You)</td>
      <td>65GZzBP1qyk4zH7c8RIJYD</td>
      <td>0.21600</td>
      <td>https://api.spotify.com/v1/audio-analysis/65GZ...</td>
      <td>0.825</td>
      <td>204533</td>
      <td>0.914</td>
      <td>65GZzBP1qyk4zH7c8RIJYD</td>
      <td>0.000024</td>
      <td>8</td>
      <td>0.2280</td>
      <td>-3.207</td>
      <td>1</td>
      <td>0.1020</td>
      <td>118.912</td>
      <td>4</td>
      <td>https://api.spotify.com/v1/tracks/65GZzBP1qyk4...</td>
      <td>audio_features</td>
      <td>spotify:track:65GZzBP1qyk4zH7c8RIJYD</td>
      <td>0.761</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_audio.describe()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>acousticness</th>
      <th>danceability</th>
      <th>duration_ms</th>
      <th>energy</th>
      <th>instrumentalness</th>
      <th>key</th>
      <th>liveness</th>
      <th>loudness</th>
      <th>mode</th>
      <th>speechiness</th>
      <th>tempo</th>
      <th>time_signature</th>
      <th>valence</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>313.000000</td>
      <td>313.000000</td>
      <td>313.000000</td>
      <td>313.00000</td>
      <td>313.000000</td>
      <td>313.000000</td>
      <td>313.000000</td>
      <td>313.000000</td>
      <td>313.000000</td>
      <td>313.000000</td>
      <td>313.000000</td>
      <td>313.000000</td>
      <td>313.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>0.166198</td>
      <td>0.663748</td>
      <td>248239.003195</td>
      <td>0.68554</td>
      <td>0.018973</td>
      <td>5.146965</td>
      <td>0.173948</td>
      <td>-6.547821</td>
      <td>0.645367</td>
      <td>0.087149</td>
      <td>117.050831</td>
      <td>3.990415</td>
      <td>0.567172</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.174713</td>
      <td>0.145504</td>
      <td>46647.551559</td>
      <td>0.17173</td>
      <td>0.115599</td>
      <td>3.669538</td>
      <td>0.132060</td>
      <td>2.255456</td>
      <td>0.479168</td>
      <td>0.091600</td>
      <td>27.356178</td>
      <td>0.149478</td>
      <td>0.238728</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.000018</td>
      <td>0.160000</td>
      <td>50620.000000</td>
      <td>0.29600</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.027200</td>
      <td>-15.637000</td>
      <td>0.000000</td>
      <td>0.022700</td>
      <td>62.330000</td>
      <td>3.000000</td>
      <td>0.038400</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>0.024900</td>
      <td>0.578000</td>
      <td>217573.000000</td>
      <td>0.54000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>0.082800</td>
      <td>-7.901000</td>
      <td>0.000000</td>
      <td>0.030900</td>
      <td>97.865000</td>
      <td>4.000000</td>
      <td>0.362000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>0.097200</td>
      <td>0.667000</td>
      <td>243587.000000</td>
      <td>0.68900</td>
      <td>0.000000</td>
      <td>5.000000</td>
      <td>0.124000</td>
      <td>-6.231000</td>
      <td>1.000000</td>
      <td>0.044500</td>
      <td>111.993000</td>
      <td>4.000000</td>
      <td>0.591000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>0.263000</td>
      <td>0.765000</td>
      <td>273533.000000</td>
      <td>0.83600</td>
      <td>0.000030</td>
      <td>8.000000</td>
      <td>0.239000</td>
      <td>-5.038000</td>
      <td>1.000000</td>
      <td>0.101000</td>
      <td>132.949000</td>
      <td>4.000000</td>
      <td>0.758000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>0.784000</td>
      <td>0.955000</td>
      <td>430800.000000</td>
      <td>0.98400</td>
      <td>0.885000</td>
      <td>11.000000</td>
      <td>0.959000</td>
      <td>-1.875000</td>
      <td>1.000000</td>
      <td>0.628000</td>
      <td>207.575000</td>
      <td>5.000000</td>
      <td>0.971000</td>
    </tr>
  </tbody>
</table>
</div>




```python
url = 'https://developer.spotify.com/web-api/get-audio-features/'
df_audio_features = pd.read_html(url)
```


```python
#spotify_audio_features
df_aud_feat = df_audio_features[2]
df_aud_feat.set_index('Key',inplace=True)
df_aud_feat
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Value Type</th>
      <th>Value Description</th>
    </tr>
    <tr>
      <th>Key</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>acousticness</th>
      <td>float</td>
      <td>A confidence measure from 0.0 to 1.0 of whethe...</td>
    </tr>
    <tr>
      <th>analysis_url</th>
      <td>string</td>
      <td>An HTTP URL to access the full audio analysis ...</td>
    </tr>
    <tr>
      <th>danceability</th>
      <td>float</td>
      <td>Danceability describes how suitable a track is...</td>
    </tr>
    <tr>
      <th>duration_ms</th>
      <td>int</td>
      <td>The duration of the track in milliseconds.</td>
    </tr>
    <tr>
      <th>energy</th>
      <td>float</td>
      <td>Energy is a measure from 0.0 to 1.0 and repres...</td>
    </tr>
    <tr>
      <th>id</th>
      <td>string</td>
      <td>The Spotify ID for the track.</td>
    </tr>
    <tr>
      <th>instrumentalness</th>
      <td>float</td>
      <td>Predicts whether a track contains no vocals. "...</td>
    </tr>
    <tr>
      <th>key</th>
      <td>int</td>
      <td>The key the track is in. Integers map to pitch...</td>
    </tr>
    <tr>
      <th>liveness</th>
      <td>float</td>
      <td>Detects the presence of an audience in the rec...</td>
    </tr>
    <tr>
      <th>loudness</th>
      <td>float</td>
      <td>The overall loudness of a track in decibels (d...</td>
    </tr>
    <tr>
      <th>mode</th>
      <td>int</td>
      <td>Mode indicates the modality (major or minor) o...</td>
    </tr>
    <tr>
      <th>speechiness</th>
      <td>float</td>
      <td>Speechiness detects the presence of spoken wor...</td>
    </tr>
    <tr>
      <th>tempo</th>
      <td>float</td>
      <td>The overall estimated tempo of a track in beat...</td>
    </tr>
    <tr>
      <th>time_signature</th>
      <td>int</td>
      <td>An estimated overall time signature of a track...</td>
    </tr>
    <tr>
      <th>track_href</th>
      <td>string</td>
      <td>A link to the Web API endpoint providing full ...</td>
    </tr>
    <tr>
      <th>type</th>
      <td>string</td>
      <td>The object type: "audio_features"</td>
    </tr>
    <tr>
      <th>uri</th>
      <td>string</td>
      <td>The Spotify URI for the track.</td>
    </tr>
    <tr>
      <th>valence</th>
      <td>float</td>
      <td>A measure from 0.0 to 1.0 describing the music...</td>
    </tr>
  </tbody>
</table>
</div>



## Step 3: Visualize your data.

##### Using a plotting utility of your choice (Tableau or python modules or both), create visualizations that will provide context to your data. There is no minimum or maximum number of graphs you should generate, but there should be a clear and consistent story being told. Give insights to the distribution, statistics, and relationships of the data. 


```python
def dist_plot(column, data):
    sns.set(rc={"figure.figsize": (10, 7)})
    sns.set_style("white")
    dist = sns.distplot(data, hist_kws={'alpha':0.2}, kde_kws={'linewidth':5})
    dist.set_title('Distribution of ' + column + '\n', fontsize=16)
```


```python
#Genre distribution
genre_chart = df_clean['genre'].value_counts().plot.bar()
genre_chart.set_title("Frequency of tracks by genre")
```




    <matplotlib.text.Text at 0x7f60604be1d0>




![png](output_35_1.png)



```python
#artist type distribution
artist_chart = df_artist['artist.gen'].value_counts().plot.bar()
artist_chart.set_title("Frequency of tracks by artist type")
```




    <matplotlib.text.Text at 0x7f60604681d0>




![png](output_36_1.png)



```python
#artist type distribution
artist_chart = df_artist['artist.gen'].value_counts().plot.pie(figsize=(6,6))
artist_chart.set_title("Frequency of tracks by artist type")
```




    <matplotlib.text.Text at 0x7f6060506ed0>




![png](output_37_1.png)



```python
#quick overview of frequency of audio characteristics
df_audio.hist(figsize=(14,14))
```




    array([[<matplotlib.axes._subplots.AxesSubplot object at 0x7f605e33d650>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x7f605f387050>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x7f605f395710>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x7f6060734350>],
           [<matplotlib.axes._subplots.AxesSubplot object at 0x7f6060998310>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x7f60608e0f50>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x7f60600e98d0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x7f605f2f5510>],
           [<matplotlib.axes._subplots.AxesSubplot object at 0x7f60607c6910>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x7f605f26a1d0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x7f605f36b5d0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x7f605e3226d0>],
           [<matplotlib.axes._subplots.AxesSubplot object at 0x7f605ca11810>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x7f605c943550>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x7f605c8c53d0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x7f605c8a9510>]], dtype=object)




![png](output_38_1.png)



```python
df_audio.columns
```




    Index([u'track', u'ID', u'acousticness', u'analysis_url', u'danceability',
           u'duration_ms', u'energy', u'id', u'instrumentalness', u'key',
           u'liveness', u'loudness', u'mode', u'speechiness', u'tempo',
           u'time_signature', u'track_href', u'type', u'uri', u'valence'],
          dtype='object')




```python
key = 'acousticness'
print df_aud_feat.loc[key,'Value Description']
dist_plot(key, df_audio[key])
```

    A confidence measure from 0.0 to 1.0 of whether the track is acoustic. 1.0 represents high confidence the track is acoustic.



![png](output_40_1.png)



```python
key = 'danceability'
print df_aud_feat.loc[key,'Value Description']
dist_plot(key, df_audio[key])
```

    Danceability describes how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm stability, beat strength, and overall regularity. A value of 0.0 is least danceable and 1.0 is most danceable.



![png](output_41_1.png)



```python
key = 'duration_ms'
print df_aud_feat.loc[key,'Value Description']
dist_plot(key, df_audio[key])
```

    The duration of the track in milliseconds.



![png](output_42_1.png)



```python
key = 'energy'
print df_aud_feat.loc[key,'Value Description']
dist_plot(key, df_audio[key])
```

    Energy is a measure from 0.0 to 1.0 and represents a perceptual measure of intensity and activity. Typically, energetic tracks feel fast, loud, and noisy. For example, death metal has high energy, while a Bach prelude scores low on the scale. Perceptual features contributing to this attribute include dynamic range, perceived loudness, timbre, onset rate, and general entropy.



![png](output_43_1.png)



```python
key = 'instrumentalness'
print df_aud_feat.loc[key,'Value Description']
dist_plot(key, df_audio[key])
```

    Predicts whether a track contains no vocals. "Ooh" and "aah" sounds are treated as instrumental in this context. Rap or spoken word tracks are clearly "vocal". The closer the instrumentalness value is to 1.0, the greater likelihood the track contains no vocal content. Values above 0.5 are intended to represent instrumental tracks, but confidence is higher as the value approaches 1.0.



![png](output_44_1.png)



```python
key = 'key'
print df_aud_feat.loc[key,'Value Description']
dist_plot(key, df_audio[key])
```

    The key the track is in. Integers map to pitches using standard Pitch Class notation. E.g. 0 = C, 1 = C♯/D♭, 2 = D, and so on.



![png](output_45_1.png)



```python
key = 'liveness'
print df_aud_feat.loc[key,'Value Description']
dist_plot(key, df_audio[key])
```

    Detects the presence of an audience in the recording. Higher liveness values represent an increased probability that the track was performed live. A value above 0.8 provides strong likelihood that the track is live.



![png](output_46_1.png)



```python
key = 'loudness'
print df_aud_feat.loc[key,'Value Description']
dist_plot(key, df_audio[key])
```

    The overall loudness of a track in decibels (dB). Loudness values are averaged across the entire track and are useful for comparing relative loudness of tracks. Loudness is the quality of a sound that is the primary psychological correlate of physical strength (amplitude). Values typical range between -60 and 0 db.



![png](output_47_1.png)



```python
key = 'mode'
print df_aud_feat.loc[key,'Value Description']
dist_plot(key, df_audio[key])
```

    Mode indicates the modality (major or minor) of a track, the type of scale from which its melodic content is derived. Major is represented by 1 and minor is 0.



![png](output_48_1.png)



```python
key = 'speechiness'
print df_aud_feat.loc[key,'Value Description']
dist_plot(key, df_audio[key])
```

    Speechiness detects the presence of spoken words in a track. The more exclusively speech-like the recording (e.g. talk show, audio book, poetry), the closer to 1.0 the attribute value. Values above 0.66 describe tracks that are probably made entirely of spoken words. Values between 0.33 and 0.66 describe tracks that may contain both music and speech, either in sections or layered, including such cases as rap music. Values below 0.33 most likely represent music and other non-speech-like tracks.



![png](output_49_1.png)



```python
key = 'tempo'
print df_aud_feat.loc[key,'Value Description']
dist_plot(key, df_audio[key])
```

    The overall estimated tempo of a track in beats per minute (BPM). In musical terminology, tempo is the speed or pace of a given piece and derives directly from the average beat duration.



![png](output_50_1.png)



```python
key = 'time_signature'
print df_aud_feat.loc[key,'Value Description']
dist_plot(key, df_audio[key])
```

    An estimated overall time signature of a track. The time signature (meter) is a notational convention to specify how many beats are in each bar (or measure).



![png](output_51_1.png)



```python
key = 'valence'
print df_aud_feat.loc[key,'Value Description']
dist_plot(key, df_audio[key])
```

    A measure from 0.0 to 1.0 describing the musical positiveness conveyed by a track. Tracks with high valence sound more positive (e.g. happy, cheerful, euphoric), while tracks with low valence sound more negative (e.g. sad, depressed, angry).



![png](output_52_1.png)


## Step 4: Create a Problem Statement.

##### Having explored the data, come up with a problem statement for this data set. You can feel free to introduce data from any other source to support your problem statement, just be sure to provide a link to the origin of the data. Once again- be creative!

For this analysis we are looking at top 100 music charts for music of the '00s.

In order to determine what made a hit soar to the charts we are looking for characteristics shared by chart toppers. Whilst this does not mean songs outside of the charts do not have these characteristics, we would expect certain characteristics to be shared by chart topping hits.

Given we have limited information about the tracks aside from artist and track length, we can look to enrich our data from other sources. These include:
1. audio characteristics - source: SPOTIFY API
2. artist type - source: Google

We could also compare these characteristics with samples of tracks that did not make the charts and determine any statistical differences

## Step 5: Brainstorm your Approach.
##### In bullet-list form, provide a proposed approach for evaluating your problem statement. This can be somewhat high-level, but start to think about ways you can massage the data for maximum efficacy. 

* review/graph all available track / audio characteristics
* identify characteristics common across tracks that may indicate what makes a hit

## Step 6: Create a blog post with your code snippets and visualizations.
##### Data Science is a growing field, and the Tech industry thrives off of collaboration and sharing of knowledge. Blogging is a powerful means for pushing the needle forward in our field. Using your blogging platform of choice, create a post describing each of the 5 steps above. Rather than writing a procedural text, imagine you're describing the data, visualizations, and conclusions you've arrived at to your peers. Aim for a minimum of 500 words. 

https://howardilderton.github.io/projects/

## BONUS: The Content Managers working for the Podcast Publishing Company have recognized you as a thought leader in your field. They've asked you to pen a white paper (minimum 500 words) on the subject of 'What It Means To Have Clean Data'. This will be an opinion piece read by a wide audience, so be sure to back up your statements with real world examples or scenarios.

##### Hint: To get started, look around on the internet for articles, blog posts, papers, youtube videos, podcasts, reddit discussions, anything that will help you understand the challenges and implications of dealing with big data. This should be a personal reflection on everything you've learned this week, and the learning goals that have been set out for you going forward. 

https://howardilderton.github.io/blog/
