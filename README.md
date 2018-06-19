
## Booleans and Conditionals with Pandas <a id="toc"></a>

### Table of Contents

1. [Introduction](#intro)
2. [Pandas Review](#pandas)
3. [Subsetting Dataframes](#subset)
4. [Practice Questions](#practice)

### Introduction <a id="intro"></a>
In this lab you'll get further practice and review with using conditionals, functions and the pandas package. All of these are common skills in a data science workflow.

### Pandas Review <a id="pandas"></a>
Remember that pandas is a great python package for spreadsheets. This often comes up in many business settings as many people may use Microsoft excel or a similar spreadsheet program. However, pandas allows you to progromatticaly manipulate data in many other ways. File sizes can also be much larger (an excel spreadsheet is limited to ~1M rows).

![](./images/pandas_data_structures.png)


```python
import pandas as pd
```


```python
df = pd.read_csv('WorldCupMatches.csv')
print(len(df))
df.head()
```

    4572





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
      <th>Year</th>
      <th>Datetime</th>
      <th>Stage</th>
      <th>Stadium</th>
      <th>City</th>
      <th>Home Team Name</th>
      <th>Home Team Goals</th>
      <th>Away Team Goals</th>
      <th>Away Team Name</th>
      <th>Win conditions</th>
      <th>Attendance</th>
      <th>Half-time Home Goals</th>
      <th>Half-time Away Goals</th>
      <th>Referee</th>
      <th>Assistant 1</th>
      <th>Assistant 2</th>
      <th>RoundID</th>
      <th>MatchID</th>
      <th>Home Team Initials</th>
      <th>Away Team Initials</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1930.0</td>
      <td>13 Jul 1930 - 15:00</td>
      <td>Group 1</td>
      <td>Pocitos</td>
      <td>Montevideo</td>
      <td>France</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>Mexico</td>
      <td></td>
      <td>4444.0</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>LOMBARDI Domingo (URU)</td>
      <td>CRISTOPHE Henry (BEL)</td>
      <td>REGO Gilberto (BRA)</td>
      <td>201.0</td>
      <td>1096.0</td>
      <td>FRA</td>
      <td>MEX</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1930.0</td>
      <td>13 Jul 1930 - 15:00</td>
      <td>Group 4</td>
      <td>Parque Central</td>
      <td>Montevideo</td>
      <td>USA</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>Belgium</td>
      <td></td>
      <td>18346.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>MACIAS Jose (ARG)</td>
      <td>MATEUCCI Francisco (URU)</td>
      <td>WARNKEN Alberto (CHI)</td>
      <td>201.0</td>
      <td>1090.0</td>
      <td>USA</td>
      <td>BEL</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1930.0</td>
      <td>14 Jul 1930 - 12:45</td>
      <td>Group 2</td>
      <td>Parque Central</td>
      <td>Montevideo</td>
      <td>Yugoslavia</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>Brazil</td>
      <td></td>
      <td>24059.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>TEJADA Anibal (URU)</td>
      <td>VALLARINO Ricardo (URU)</td>
      <td>BALWAY Thomas (FRA)</td>
      <td>201.0</td>
      <td>1093.0</td>
      <td>YUG</td>
      <td>BRA</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1930.0</td>
      <td>14 Jul 1930 - 14:50</td>
      <td>Group 3</td>
      <td>Pocitos</td>
      <td>Montevideo</td>
      <td>Romania</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>Peru</td>
      <td></td>
      <td>2549.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>WARNKEN Alberto (CHI)</td>
      <td>LANGENUS Jean (BEL)</td>
      <td>MATEUCCI Francisco (URU)</td>
      <td>201.0</td>
      <td>1098.0</td>
      <td>ROU</td>
      <td>PER</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1930.0</td>
      <td>15 Jul 1930 - 16:00</td>
      <td>Group 1</td>
      <td>Parque Central</td>
      <td>Montevideo</td>
      <td>Argentina</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>France</td>
      <td></td>
      <td>23409.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>REGO Gilberto (BRA)</td>
      <td>SAUCEDO Ulises (BOL)</td>
      <td>RADULESCU Constantin (ROU)</td>
      <td>201.0</td>
      <td>1085.0</td>
      <td>ARG</td>
      <td>FRA</td>
    </tr>
  </tbody>
</table>
</div>



## Subsetting Pandas DataFrames <a id="subset"></a>

First lets recall how we can access a series (or column) of a Pandas DataFrame:


```python
df['Year']
```




    0       1930.0
    1       1930.0
    2       1930.0
    3       1930.0
    4       1930.0
    5       1930.0
    6       1930.0
    7       1930.0
    8       1930.0
    9       1930.0
    10      1930.0
    11      1930.0
    12      1930.0
    13      1930.0
    14      1930.0
    15      1930.0
    16      1930.0
    17      1930.0
    18      1934.0
    19      1934.0
    20      1934.0
    21      1934.0
    22      1934.0
    23      1934.0
    24      1934.0
    25      1934.0
    26      1934.0
    27      1934.0
    28      1934.0
    29      1934.0
             ...  
    4542       NaN
    4543       NaN
    4544       NaN
    4545       NaN
    4546       NaN
    4547       NaN
    4548       NaN
    4549       NaN
    4550       NaN
    4551       NaN
    4552       NaN
    4553       NaN
    4554       NaN
    4555       NaN
    4556       NaN
    4557       NaN
    4558       NaN
    4559       NaN
    4560       NaN
    4561       NaN
    4562       NaN
    4563       NaN
    4564       NaN
    4565       NaN
    4566       NaN
    4567       NaN
    4568       NaN
    4569       NaN
    4570       NaN
    4571       NaN
    Name: Year, Length: 4572, dtype: float64



Interesting. Note how many of the later entries have NaN which is a null value.  
If you wanted to, you could set these to some arbitrary value (such as 0) with the following:


```python
df = df.fillna(value=0)
```

Alternatively, we could have filtered out all of the null values.  
To do this, we'll use the .isnull() method for pandas series.  
Check out the documentation:


```python
df.Year.isnull?
```

Let's reload the original DataFrame to check this out.


```python
df = pd.read_csv('WorldCupMatches.csv')
print(len(df))
df.head()
```

    4572





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
      <th>Year</th>
      <th>Datetime</th>
      <th>Stage</th>
      <th>Stadium</th>
      <th>City</th>
      <th>Home Team Name</th>
      <th>Home Team Goals</th>
      <th>Away Team Goals</th>
      <th>Away Team Name</th>
      <th>Win conditions</th>
      <th>Attendance</th>
      <th>Half-time Home Goals</th>
      <th>Half-time Away Goals</th>
      <th>Referee</th>
      <th>Assistant 1</th>
      <th>Assistant 2</th>
      <th>RoundID</th>
      <th>MatchID</th>
      <th>Home Team Initials</th>
      <th>Away Team Initials</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1930.0</td>
      <td>13 Jul 1930 - 15:00</td>
      <td>Group 1</td>
      <td>Pocitos</td>
      <td>Montevideo</td>
      <td>France</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>Mexico</td>
      <td></td>
      <td>4444.0</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>LOMBARDI Domingo (URU)</td>
      <td>CRISTOPHE Henry (BEL)</td>
      <td>REGO Gilberto (BRA)</td>
      <td>201.0</td>
      <td>1096.0</td>
      <td>FRA</td>
      <td>MEX</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1930.0</td>
      <td>13 Jul 1930 - 15:00</td>
      <td>Group 4</td>
      <td>Parque Central</td>
      <td>Montevideo</td>
      <td>USA</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>Belgium</td>
      <td></td>
      <td>18346.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>MACIAS Jose (ARG)</td>
      <td>MATEUCCI Francisco (URU)</td>
      <td>WARNKEN Alberto (CHI)</td>
      <td>201.0</td>
      <td>1090.0</td>
      <td>USA</td>
      <td>BEL</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1930.0</td>
      <td>14 Jul 1930 - 12:45</td>
      <td>Group 2</td>
      <td>Parque Central</td>
      <td>Montevideo</td>
      <td>Yugoslavia</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>Brazil</td>
      <td></td>
      <td>24059.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>TEJADA Anibal (URU)</td>
      <td>VALLARINO Ricardo (URU)</td>
      <td>BALWAY Thomas (FRA)</td>
      <td>201.0</td>
      <td>1093.0</td>
      <td>YUG</td>
      <td>BRA</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1930.0</td>
      <td>14 Jul 1930 - 14:50</td>
      <td>Group 3</td>
      <td>Pocitos</td>
      <td>Montevideo</td>
      <td>Romania</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>Peru</td>
      <td></td>
      <td>2549.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>WARNKEN Alberto (CHI)</td>
      <td>LANGENUS Jean (BEL)</td>
      <td>MATEUCCI Francisco (URU)</td>
      <td>201.0</td>
      <td>1098.0</td>
      <td>ROU</td>
      <td>PER</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1930.0</td>
      <td>15 Jul 1930 - 16:00</td>
      <td>Group 1</td>
      <td>Parque Central</td>
      <td>Montevideo</td>
      <td>Argentina</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>France</td>
      <td></td>
      <td>23409.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>REGO Gilberto (BRA)</td>
      <td>SAUCEDO Ulises (BOL)</td>
      <td>RADULESCU Constantin (ROU)</td>
      <td>201.0</td>
      <td>1085.0</td>
      <td>ARG</td>
      <td>FRA</td>
    </tr>
  </tbody>
</table>
</div>



Take a look at the boolean that is returned by the .isnull() method:


```python
df.Year.isnull()
```




    0       False
    1       False
    2       False
    3       False
    4       False
    5       False
    6       False
    7       False
    8       False
    9       False
    10      False
    11      False
    12      False
    13      False
    14      False
    15      False
    16      False
    17      False
    18      False
    19      False
    20      False
    21      False
    22      False
    23      False
    24      False
    25      False
    26      False
    27      False
    28      False
    29      False
            ...  
    4542     True
    4543     True
    4544     True
    4545     True
    4546     True
    4547     True
    4548     True
    4549     True
    4550     True
    4551     True
    4552     True
    4553     True
    4554     True
    4555     True
    4556     True
    4557     True
    4558     True
    4559     True
    4560     True
    4561     True
    4562     True
    4563     True
    4564     True
    4565     True
    4566     True
    4567     True
    4568     True
    4569     True
    4570     True
    4571     True
    Name: Year, Length: 4572, dtype: bool



Now look at how we can use that to subset the dataframe, returning only those rows for which the boolean is true:


```python
df[df.Year.isnull()]
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
      <th>Year</th>
      <th>Datetime</th>
      <th>Stage</th>
      <th>Stadium</th>
      <th>City</th>
      <th>Home Team Name</th>
      <th>Home Team Goals</th>
      <th>Away Team Goals</th>
      <th>Away Team Name</th>
      <th>Win conditions</th>
      <th>Attendance</th>
      <th>Half-time Home Goals</th>
      <th>Half-time Away Goals</th>
      <th>Referee</th>
      <th>Assistant 1</th>
      <th>Assistant 2</th>
      <th>RoundID</th>
      <th>MatchID</th>
      <th>Home Team Initials</th>
      <th>Away Team Initials</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>852</th>
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
      <th>853</th>
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
      <th>854</th>
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
      <th>855</th>
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
      <th>856</th>
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
      <th>857</th>
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
      <th>858</th>
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
      <th>859</th>
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
      <th>860</th>
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
      <th>861</th>
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
      <th>862</th>
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
      <th>863</th>
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
      <th>864</th>
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
      <th>865</th>
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
      <th>866</th>
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
      <th>867</th>
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
      <th>868</th>
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
      <th>869</th>
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
      <th>870</th>
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
      <th>871</th>
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
      <th>872</th>
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
      <th>873</th>
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
      <th>874</th>
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
      <th>875</th>
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
      <th>876</th>
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
      <th>877</th>
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
      <th>878</th>
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
      <th>879</th>
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
      <th>880</th>
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
      <th>881</th>
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
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>4542</th>
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
      <th>4543</th>
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
      <th>4544</th>
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
      <th>4545</th>
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
      <th>4546</th>
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
      <th>4547</th>
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
      <th>4548</th>
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
      <th>4549</th>
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
      <th>4550</th>
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
      <th>4551</th>
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
      <th>4552</th>
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
      <th>4553</th>
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
      <th>4554</th>
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
      <th>4555</th>
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
      <th>4556</th>
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
      <th>4557</th>
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
      <th>4558</th>
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
      <th>4559</th>
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
      <th>4560</th>
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
      <th>4561</th>
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
      <th>4562</th>
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
      <th>4563</th>
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
      <th>4564</th>
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
      <th>4565</th>
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
      <th>4566</th>
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
      <th>4567</th>
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
      <th>4568</th>
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
      <th>4569</th>
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
      <th>4570</th>
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
      <th>4571</th>
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
<p>3720 rows × 20 columns</p>
</div>



Notice how the first row returned was 852. (Everything before that must have had a value for the year.)  
More commonly, we might want to return all of the rows that are not null:


```python
df[~df.Year.isnull()] #The tilde (~) negates the boolean, making every True statement False and vice versa.
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
      <th>Year</th>
      <th>Datetime</th>
      <th>Stage</th>
      <th>Stadium</th>
      <th>City</th>
      <th>Home Team Name</th>
      <th>Home Team Goals</th>
      <th>Away Team Goals</th>
      <th>Away Team Name</th>
      <th>Win conditions</th>
      <th>Attendance</th>
      <th>Half-time Home Goals</th>
      <th>Half-time Away Goals</th>
      <th>Referee</th>
      <th>Assistant 1</th>
      <th>Assistant 2</th>
      <th>RoundID</th>
      <th>MatchID</th>
      <th>Home Team Initials</th>
      <th>Away Team Initials</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1930.0</td>
      <td>13 Jul 1930 - 15:00</td>
      <td>Group 1</td>
      <td>Pocitos</td>
      <td>Montevideo</td>
      <td>France</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>Mexico</td>
      <td></td>
      <td>4444.0</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>LOMBARDI Domingo (URU)</td>
      <td>CRISTOPHE Henry (BEL)</td>
      <td>REGO Gilberto (BRA)</td>
      <td>201.0</td>
      <td>1096.0</td>
      <td>FRA</td>
      <td>MEX</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1930.0</td>
      <td>13 Jul 1930 - 15:00</td>
      <td>Group 4</td>
      <td>Parque Central</td>
      <td>Montevideo</td>
      <td>USA</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>Belgium</td>
      <td></td>
      <td>18346.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>MACIAS Jose (ARG)</td>
      <td>MATEUCCI Francisco (URU)</td>
      <td>WARNKEN Alberto (CHI)</td>
      <td>201.0</td>
      <td>1090.0</td>
      <td>USA</td>
      <td>BEL</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1930.0</td>
      <td>14 Jul 1930 - 12:45</td>
      <td>Group 2</td>
      <td>Parque Central</td>
      <td>Montevideo</td>
      <td>Yugoslavia</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>Brazil</td>
      <td></td>
      <td>24059.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>TEJADA Anibal (URU)</td>
      <td>VALLARINO Ricardo (URU)</td>
      <td>BALWAY Thomas (FRA)</td>
      <td>201.0</td>
      <td>1093.0</td>
      <td>YUG</td>
      <td>BRA</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1930.0</td>
      <td>14 Jul 1930 - 14:50</td>
      <td>Group 3</td>
      <td>Pocitos</td>
      <td>Montevideo</td>
      <td>Romania</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>Peru</td>
      <td></td>
      <td>2549.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>WARNKEN Alberto (CHI)</td>
      <td>LANGENUS Jean (BEL)</td>
      <td>MATEUCCI Francisco (URU)</td>
      <td>201.0</td>
      <td>1098.0</td>
      <td>ROU</td>
      <td>PER</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1930.0</td>
      <td>15 Jul 1930 - 16:00</td>
      <td>Group 1</td>
      <td>Parque Central</td>
      <td>Montevideo</td>
      <td>Argentina</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>France</td>
      <td></td>
      <td>23409.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>REGO Gilberto (BRA)</td>
      <td>SAUCEDO Ulises (BOL)</td>
      <td>RADULESCU Constantin (ROU)</td>
      <td>201.0</td>
      <td>1085.0</td>
      <td>ARG</td>
      <td>FRA</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1930.0</td>
      <td>16 Jul 1930 - 14:45</td>
      <td>Group 1</td>
      <td>Parque Central</td>
      <td>Montevideo</td>
      <td>Chile</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>Mexico</td>
      <td></td>
      <td>9249.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>CRISTOPHE Henry (BEL)</td>
      <td>APHESTEGUY Martin (URU)</td>
      <td>LANGENUS Jean (BEL)</td>
      <td>201.0</td>
      <td>1095.0</td>
      <td>CHI</td>
      <td>MEX</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1930.0</td>
      <td>17 Jul 1930 - 12:45</td>
      <td>Group 2</td>
      <td>Parque Central</td>
      <td>Montevideo</td>
      <td>Yugoslavia</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>Bolivia</td>
      <td></td>
      <td>18306.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>MATEUCCI Francisco (URU)</td>
      <td>LOMBARDI Domingo (URU)</td>
      <td>WARNKEN Alberto (CHI)</td>
      <td>201.0</td>
      <td>1092.0</td>
      <td>YUG</td>
      <td>BOL</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1930.0</td>
      <td>17 Jul 1930 - 14:45</td>
      <td>Group 4</td>
      <td>Parque Central</td>
      <td>Montevideo</td>
      <td>USA</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>Paraguay</td>
      <td></td>
      <td>18306.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>MACIAS Jose (ARG)</td>
      <td>APHESTEGUY Martin (URU)</td>
      <td>TEJADA Anibal (URU)</td>
      <td>201.0</td>
      <td>1097.0</td>
      <td>USA</td>
      <td>PAR</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1930.0</td>
      <td>18 Jul 1930 - 14:30</td>
      <td>Group 3</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Uruguay</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>Peru</td>
      <td></td>
      <td>57735.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>LANGENUS Jean (BEL)</td>
      <td>BALWAY Thomas (FRA)</td>
      <td>CRISTOPHE Henry (BEL)</td>
      <td>201.0</td>
      <td>1099.0</td>
      <td>URU</td>
      <td>PER</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1930.0</td>
      <td>19 Jul 1930 - 12:50</td>
      <td>Group 1</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Chile</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>France</td>
      <td></td>
      <td>2000.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>TEJADA Anibal (URU)</td>
      <td>LOMBARDI Domingo (URU)</td>
      <td>REGO Gilberto (BRA)</td>
      <td>201.0</td>
      <td>1094.0</td>
      <td>CHI</td>
      <td>FRA</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1930.0</td>
      <td>19 Jul 1930 - 15:00</td>
      <td>Group 1</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Argentina</td>
      <td>6.0</td>
      <td>3.0</td>
      <td>Mexico</td>
      <td></td>
      <td>42100.0</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>SAUCEDO Ulises (BOL)</td>
      <td>ALONSO Gualberto (URU)</td>
      <td>RADULESCU Constantin (ROU)</td>
      <td>201.0</td>
      <td>1086.0</td>
      <td>ARG</td>
      <td>MEX</td>
    </tr>
    <tr>
      <th>11</th>
      <td>1930.0</td>
      <td>20 Jul 1930 - 13:00</td>
      <td>Group 2</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Brazil</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>Bolivia</td>
      <td></td>
      <td>25466.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>BALWAY Thomas (FRA)</td>
      <td>MATEUCCI Francisco (URU)</td>
      <td>VALLEJO Gaspar (MEX)</td>
      <td>201.0</td>
      <td>1091.0</td>
      <td>BRA</td>
      <td>BOL</td>
    </tr>
    <tr>
      <th>12</th>
      <td>1930.0</td>
      <td>20 Jul 1930 - 15:00</td>
      <td>Group 4</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Paraguay</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>Belgium</td>
      <td></td>
      <td>12000.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>VALLARINO Ricardo (URU)</td>
      <td>MACIAS Jose (ARG)</td>
      <td>LOMBARDI Domingo (URU)</td>
      <td>201.0</td>
      <td>1089.0</td>
      <td>PAR</td>
      <td>BEL</td>
    </tr>
    <tr>
      <th>13</th>
      <td>1930.0</td>
      <td>21 Jul 1930 - 14:50</td>
      <td>Group 3</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Uruguay</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>Romania</td>
      <td></td>
      <td>70022.0</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>REGO Gilberto (BRA)</td>
      <td>WARNKEN Alberto (CHI)</td>
      <td>SAUCEDO Ulises (BOL)</td>
      <td>201.0</td>
      <td>1100.0</td>
      <td>URU</td>
      <td>ROU</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1930.0</td>
      <td>22 Jul 1930 - 14:45</td>
      <td>Group 1</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Argentina</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>Chile</td>
      <td></td>
      <td>41459.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>LANGENUS Jean (BEL)</td>
      <td>CRISTOPHE Henry (BEL)</td>
      <td>SAUCEDO Ulises (BOL)</td>
      <td>201.0</td>
      <td>1084.0</td>
      <td>ARG</td>
      <td>CHI</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1930.0</td>
      <td>26 Jul 1930 - 14:45</td>
      <td>Semi-finals</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Argentina</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>USA</td>
      <td></td>
      <td>72886.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>LANGENUS Jean (BEL)</td>
      <td>VALLEJO Gaspar (MEX)</td>
      <td>WARNKEN Alberto (CHI)</td>
      <td>202.0</td>
      <td>1088.0</td>
      <td>ARG</td>
      <td>USA</td>
    </tr>
    <tr>
      <th>16</th>
      <td>1930.0</td>
      <td>27 Jul 1930 - 14:45</td>
      <td>Semi-finals</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Uruguay</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>Yugoslavia</td>
      <td></td>
      <td>79867.0</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>REGO Gilberto (BRA)</td>
      <td>SAUCEDO Ulises (BOL)</td>
      <td>BALWAY Thomas (FRA)</td>
      <td>202.0</td>
      <td>1101.0</td>
      <td>URU</td>
      <td>YUG</td>
    </tr>
    <tr>
      <th>17</th>
      <td>1930.0</td>
      <td>30 Jul 1930 - 14:15</td>
      <td>Final</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Uruguay</td>
      <td>4.0</td>
      <td>2.0</td>
      <td>Argentina</td>
      <td></td>
      <td>68346.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>LANGENUS Jean (BEL)</td>
      <td>SAUCEDO Ulises (BOL)</td>
      <td>CRISTOPHE Henry (BEL)</td>
      <td>405.0</td>
      <td>1087.0</td>
      <td>URU</td>
      <td>ARG</td>
    </tr>
    <tr>
      <th>18</th>
      <td>1934.0</td>
      <td>27 May 1934 - 16:30</td>
      <td>Preliminary round</td>
      <td>Stadio Benito Mussolini</td>
      <td>Turin</td>
      <td>Austria</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>France</td>
      <td>Austria win after extra time</td>
      <td>16000.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>VAN MOORSEL Johannes (NED)</td>
      <td>CAIRONI Camillo (ITA)</td>
      <td>BAERT Louis (BEL)</td>
      <td>204.0</td>
      <td>1104.0</td>
      <td>AUT</td>
      <td>FRA</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1934.0</td>
      <td>27 May 1934 - 16:30</td>
      <td>Preliminary round</td>
      <td>Giorgio Ascarelli</td>
      <td>Naples</td>
      <td>Hungary</td>
      <td>4.0</td>
      <td>2.0</td>
      <td>Egypt</td>
      <td></td>
      <td>9000.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>BARLASSINA Rinaldo (ITA)</td>
      <td>DATTILO Generoso (ITA)</td>
      <td>SASSI Otello (ITA)</td>
      <td>204.0</td>
      <td>1119.0</td>
      <td>HUN</td>
      <td>EGY</td>
    </tr>
    <tr>
      <th>20</th>
      <td>1934.0</td>
      <td>27 May 1934 - 16:30</td>
      <td>Preliminary round</td>
      <td>San Siro</td>
      <td>Milan</td>
      <td>Switzerland</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>Netherlands</td>
      <td></td>
      <td>33000.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>EKLIND Ivan (SWE)</td>
      <td>BERANEK Alois (AUT)</td>
      <td>BONIVENTO Ferruccio (ITA)</td>
      <td>204.0</td>
      <td>1133.0</td>
      <td>SUI</td>
      <td>NED</td>
    </tr>
    <tr>
      <th>21</th>
      <td>1934.0</td>
      <td>27 May 1934 - 16:30</td>
      <td>Preliminary round</td>
      <td>Littorale</td>
      <td>Bologna</td>
      <td>Sweden</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>Argentina</td>
      <td></td>
      <td>14000.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>BRAUN Eugen (AUT)</td>
      <td>CARRARO Albino (ITA)</td>
      <td>TURBIANI Giuseppe (ITA)</td>
      <td>204.0</td>
      <td>1102.0</td>
      <td>SWE</td>
      <td>ARG</td>
    </tr>
    <tr>
      <th>22</th>
      <td>1934.0</td>
      <td>27 May 1934 - 16:30</td>
      <td>Preliminary round</td>
      <td>Giovanni Berta</td>
      <td>Florence</td>
      <td>Germany</td>
      <td>5.0</td>
      <td>2.0</td>
      <td>Belgium</td>
      <td></td>
      <td>8000.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>MATTEA Francesco (ITA)</td>
      <td>MELANDRI Ermenegildo (ITA)</td>
      <td>BAERT Jacques (FRA)</td>
      <td>204.0</td>
      <td>1108.0</td>
      <td>GER</td>
      <td>BEL</td>
    </tr>
    <tr>
      <th>23</th>
      <td>1934.0</td>
      <td>27 May 1934 - 16:30</td>
      <td>Preliminary round</td>
      <td>Luigi Ferraris</td>
      <td>Genoa</td>
      <td>Spain</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>Brazil</td>
      <td></td>
      <td>21000.0</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>BIRLEM Alfred (GER)</td>
      <td>CARMINATI Ettore (ITA)</td>
      <td>IVANCSICS Mihaly (HUN)</td>
      <td>204.0</td>
      <td>1111.0</td>
      <td>ESP</td>
      <td>BRA</td>
    </tr>
    <tr>
      <th>24</th>
      <td>1934.0</td>
      <td>27 May 1934 - 16:30</td>
      <td>Preliminary round</td>
      <td>Nazionale PNF</td>
      <td>Rome</td>
      <td>Italy</td>
      <td>7.0</td>
      <td>1.0</td>
      <td>USA</td>
      <td></td>
      <td>25000.0</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>MERCET Rene (SUI)</td>
      <td>ESCARTIN Pedro (ESP)</td>
      <td>ZENISEK Bohumil (TCH)</td>
      <td>204.0</td>
      <td>1135.0</td>
      <td>ITA</td>
      <td>USA</td>
    </tr>
    <tr>
      <th>25</th>
      <td>1934.0</td>
      <td>27 May 1934 - 16:30</td>
      <td>Preliminary round</td>
      <td>Littorio</td>
      <td>Trieste</td>
      <td>Czechoslovakia</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>Romania</td>
      <td></td>
      <td>9000.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>LANGENUS Jean (BEL)</td>
      <td>SCARPI Giuseppe (ITA)</td>
      <td>SCORZONI Raffaele (ITA)</td>
      <td>204.0</td>
      <td>1141.0</td>
      <td>TCH</td>
      <td>ROU</td>
    </tr>
    <tr>
      <th>26</th>
      <td>1934.0</td>
      <td>31 May 1934 - 16:30</td>
      <td>Quarter-finals</td>
      <td>Stadio Benito Mussolini</td>
      <td>Turin</td>
      <td>Czechoslovakia</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>Switzerland</td>
      <td></td>
      <td>12000.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>BERANEK Alois (AUT)</td>
      <td>MOHAMED Youssuf (EGY)</td>
      <td>BAERT Jacques (FRA)</td>
      <td>418.0</td>
      <td>1143.0</td>
      <td>TCH</td>
      <td>SUI</td>
    </tr>
    <tr>
      <th>27</th>
      <td>1934.0</td>
      <td>31 May 1934 - 16:30</td>
      <td>Quarter-finals</td>
      <td>San Siro</td>
      <td>Milan</td>
      <td>Germany</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>Sweden</td>
      <td></td>
      <td>3000.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>BARLASSINA Rinaldo (ITA)</td>
      <td>MERCET Rene (SUI)</td>
      <td>VAN MOORSEL Johannes (NED)</td>
      <td>418.0</td>
      <td>1129.0</td>
      <td>GER</td>
      <td>SWE</td>
    </tr>
    <tr>
      <th>28</th>
      <td>1934.0</td>
      <td>31 May 1934 - 16:30</td>
      <td>Quarter-finals</td>
      <td>Giovanni Berta</td>
      <td>Florence</td>
      <td>Italy</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>Spain</td>
      <td></td>
      <td>35000.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>BAERT Louis (BEL)</td>
      <td>ZENISEK Bohumil (TCH)</td>
      <td>IVANCSICS Mihaly (HUN)</td>
      <td>418.0</td>
      <td>1122.0</td>
      <td>ITA</td>
      <td>ESP</td>
    </tr>
    <tr>
      <th>29</th>
      <td>1934.0</td>
      <td>31 May 1934 - 16:30</td>
      <td>Quarter-finals</td>
      <td>Littorale</td>
      <td>Bologna</td>
      <td>Austria</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>Hungary</td>
      <td></td>
      <td>23000.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>MATTEA Francesco (ITA)</td>
      <td>ESCARTIN Pedro (ESP)</td>
      <td>BIRLEM Alfred (GER)</td>
      <td>418.0</td>
      <td>1106.0</td>
      <td>AUT</td>
      <td>HUN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>822</th>
      <td>2014.0</td>
      <td>30 Jun 2014 - 13:00</td>
      <td>Round of 16</td>
      <td>Estadio Nacional</td>
      <td>Brasilia</td>
      <td>France</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>Nigeria</td>
      <td></td>
      <td>67882.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>GEIGER Mark (USA)</td>
      <td>HURD Sean (USA)</td>
      <td>FLETCHER Joe (CAN)</td>
      <td>255951.0</td>
      <td>300186462.0</td>
      <td>FRA</td>
      <td>NGA</td>
    </tr>
    <tr>
      <th>823</th>
      <td>2014.0</td>
      <td>30 Jun 2014 - 17:00</td>
      <td>Round of 16</td>
      <td>Estadio Beira-Rio</td>
      <td>Porto Alegre</td>
      <td>Germany</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>Algeria</td>
      <td>Germany win after extra time</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>RICCI Sandro (BRA)</td>
      <td>DE CARVALHO Emerson (BRA)</td>
      <td>VAN GASSE Marcelo (BRA)</td>
      <td>255951.0</td>
      <td>300186460.0</td>
      <td>GER</td>
      <td>ALG</td>
    </tr>
    <tr>
      <th>824</th>
      <td>2014.0</td>
      <td>04 Jul 2014 - 17:00</td>
      <td>Quarter-finals</td>
      <td>Estadio Castelao</td>
      <td>Fortaleza</td>
      <td>Brazil</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>Colombia</td>
      <td></td>
      <td>60342.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>Carlos VELASCO CARBALLO (ESP)</td>
      <td>ALONSO FERNANDEZ Roberto (ESP)</td>
      <td>YUSTE Juan (ESP)</td>
      <td>255953.0</td>
      <td>300186461.0</td>
      <td>BRA</td>
      <td>COL</td>
    </tr>
    <tr>
      <th>825</th>
      <td>2014.0</td>
      <td>04 Jul 2014 - 13:00</td>
      <td>Quarter-finals</td>
      <td>Estadio do Maracana</td>
      <td>Rio De Janeiro</td>
      <td>France</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Germany</td>
      <td></td>
      <td>74240.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>PITANA Nestor (ARG)</td>
      <td>MAIDANA Hernan (ARG)</td>
      <td>BELATTI Juan Pablo (ARG)</td>
      <td>255953.0</td>
      <td>300186485.0</td>
      <td>FRA</td>
      <td>GER</td>
    </tr>
    <tr>
      <th>826</th>
      <td>2014.0</td>
      <td>08 Jul 2014 - 17:00</td>
      <td>Semi-finals</td>
      <td>Estadio Mineirao</td>
      <td>Belo Horizonte</td>
      <td>Brazil</td>
      <td>1.0</td>
      <td>7.0</td>
      <td>Germany</td>
      <td></td>
      <td>58141.0</td>
      <td>0.0</td>
      <td>5.0</td>
      <td>RODRIGUEZ Marco (MEX)</td>
      <td>TORRENTERA Marvin (MEX)</td>
      <td>QUINTERO Marcos (MEX)</td>
      <td>255955.0</td>
      <td>300186474.0</td>
      <td>BRA</td>
      <td>GER</td>
    </tr>
    <tr>
      <th>827</th>
      <td>2014.0</td>
      <td>12 Jul 2014 - 17:00</td>
      <td>Play-off for third place</td>
      <td>Estadio Nacional</td>
      <td>Brasilia</td>
      <td>Brazil</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>Netherlands</td>
      <td></td>
      <td>68034.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>HAIMOUDI Djamel (ALG)</td>
      <td>ACHIK Redouane (MAR)</td>
      <td>ETCHIALI Abdelhak (ALG)</td>
      <td>255957.0</td>
      <td>300186502.0</td>
      <td>BRA</td>
      <td>NED</td>
    </tr>
    <tr>
      <th>828</th>
      <td>2014.0</td>
      <td>13 Jul 2014 - 16:00</td>
      <td>Final</td>
      <td>Estadio do Maracana</td>
      <td>Rio De Janeiro</td>
      <td>Germany</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>Argentina</td>
      <td>Germany win after extra time</td>
      <td>74738.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Nicola RIZZOLI (ITA)</td>
      <td>Renato FAVERANI (ITA)</td>
      <td>Andrea STEFANI (ITA)</td>
      <td>255959.0</td>
      <td>300186501.0</td>
      <td>GER</td>
      <td>ARG</td>
    </tr>
    <tr>
      <th>829</th>
      <td>2014.0</td>
      <td>09 Jul 2014 - 17:00</td>
      <td>Semi-finals</td>
      <td>Arena de Sao Paulo</td>
      <td>Sao Paulo</td>
      <td>Netherlands</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Argentina</td>
      <td>Argentina win on penalties (2 - 4)</td>
      <td>63267.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>C�neyt �AKIR (TUR)</td>
      <td>DURAN Bahattin (TUR)</td>
      <td>ONGUN Tarik (TUR)</td>
      <td>255955.0</td>
      <td>300186490.0</td>
      <td>NED</td>
      <td>ARG</td>
    </tr>
    <tr>
      <th>830</th>
      <td>2014.0</td>
      <td>05 Jul 2014 - 17:00</td>
      <td>Quarter-finals</td>
      <td>Arena Fonte Nova</td>
      <td>Salvador</td>
      <td>Netherlands</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Costa Rica</td>
      <td>Netherlands win on penalties (4 - 3)</td>
      <td>51179.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Ravshan IRMATOV (UZB)</td>
      <td>RASULOV Abduxamidullo (UZB)</td>
      <td>KOCHKAROV Bakhadyr (KGZ)</td>
      <td>255953.0</td>
      <td>300186488.0</td>
      <td>NED</td>
      <td>CRC</td>
    </tr>
    <tr>
      <th>831</th>
      <td>2014.0</td>
      <td>05 Jul 2014 - 13:00</td>
      <td>Quarter-finals</td>
      <td>Estadio Nacional</td>
      <td>Brasilia</td>
      <td>Argentina</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>Belgium</td>
      <td></td>
      <td>68551.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>Nicola RIZZOLI (ITA)</td>
      <td>Renato FAVERANI (ITA)</td>
      <td>Andrea STEFANI (ITA)</td>
      <td>255953.0</td>
      <td>300186504.0</td>
      <td>ARG</td>
      <td>BEL</td>
    </tr>
    <tr>
      <th>832</th>
      <td>2014.0</td>
      <td>29 Jun 2014 - 13:00</td>
      <td>Round of 16</td>
      <td>Estadio Castelao</td>
      <td>Fortaleza</td>
      <td>Netherlands</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>Mexico</td>
      <td></td>
      <td>58817.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>PROENCA Pedro (POR)</td>
      <td>MIRANDA Bertino (POR)</td>
      <td>TRIGO Jose (POR)</td>
      <td>255951.0</td>
      <td>300186508.0</td>
      <td>NED</td>
      <td>MEX</td>
    </tr>
    <tr>
      <th>833</th>
      <td>2014.0</td>
      <td>29 Jun 2014 - 17:00</td>
      <td>Round of 16</td>
      <td>Arena Pernambuco</td>
      <td>Recife</td>
      <td>Costa Rica</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>Greece</td>
      <td>Costa Rica win on penalties (5 - 3)</td>
      <td>41242.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Ben WILLIAMS (AUS)</td>
      <td>CREAM Matthew (AUS)</td>
      <td>ANAZ Hakan (AUS)</td>
      <td>255951.0</td>
      <td>300186459.0</td>
      <td>CRC</td>
      <td>GRE</td>
    </tr>
    <tr>
      <th>834</th>
      <td>2014.0</td>
      <td>01 Jul 2014 - 13:00</td>
      <td>Round of 16</td>
      <td>Arena de Sao Paulo</td>
      <td>Sao Paulo</td>
      <td>Argentina</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>Switzerland</td>
      <td>Argentina win after extra time</td>
      <td>63255.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>ERIKSSON Jonas (SWE)</td>
      <td>KLASENIUS Mathias (SWE)</td>
      <td>WARNMARK Daniel (SWE)</td>
      <td>255951.0</td>
      <td>300186503.0</td>
      <td>ARG</td>
      <td>SUI</td>
    </tr>
    <tr>
      <th>835</th>
      <td>2014.0</td>
      <td>01 Jul 2014 - 17:00</td>
      <td>Round of 16</td>
      <td>Arena Fonte Nova</td>
      <td>Salvador</td>
      <td>Belgium</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>USA</td>
      <td>Belgium win after extra time</td>
      <td>51227.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>HAIMOUDI Djamel (ALG)</td>
      <td>ACHIK Redouane (MAR)</td>
      <td>ETCHIALI Abdelhak (ALG)</td>
      <td>255951.0</td>
      <td>300186497.0</td>
      <td>BEL</td>
      <td>USA</td>
    </tr>
    <tr>
      <th>836</th>
      <td>2014.0</td>
      <td>28 Jun 2014 - 13:00</td>
      <td>Round of 16</td>
      <td>Estadio Mineirao</td>
      <td>Belo Horizonte</td>
      <td>Brazil</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>Chile</td>
      <td>Brazil win on penalties (3 - 2)</td>
      <td>57714.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>WEBB Howard (ENG)</td>
      <td>MULLARKEY Michael (ENG)</td>
      <td>Darren CANN (ENG)</td>
      <td>255951.0</td>
      <td>300186487.0</td>
      <td>BRA</td>
      <td>CHI</td>
    </tr>
    <tr>
      <th>837</th>
      <td>2014.0</td>
      <td>28 Jun 2014 - 17:00</td>
      <td>Round of 16</td>
      <td>Estadio do Maracana</td>
      <td>Rio De Janeiro</td>
      <td>Colombia</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>Uruguay</td>
      <td></td>
      <td>73804.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>Bj�rn KUIPERS (NED)</td>
      <td>Sander VAN ROEKEL (NED)</td>
      <td>Erwin ZEINSTRA (NED)</td>
      <td>255951.0</td>
      <td>300186491.0</td>
      <td>COL</td>
      <td>URU</td>
    </tr>
    <tr>
      <th>838</th>
      <td>2014.0</td>
      <td>29 Jun 2014 - 13:00</td>
      <td>Round of 16</td>
      <td>Estadio Castelao</td>
      <td>Fortaleza</td>
      <td>Netherlands</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>Mexico</td>
      <td></td>
      <td>58817.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>PROENCA Pedro (POR)</td>
      <td>MIRANDA Bertino (POR)</td>
      <td>TRIGO Jose (POR)</td>
      <td>255951.0</td>
      <td>300186508.0</td>
      <td>NED</td>
      <td>MEX</td>
    </tr>
    <tr>
      <th>839</th>
      <td>2014.0</td>
      <td>29 Jun 2014 - 17:00</td>
      <td>Round of 16</td>
      <td>Arena Pernambuco</td>
      <td>Recife</td>
      <td>Costa Rica</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>Greece</td>
      <td>Costa Rica win on penalties (5 - 3)</td>
      <td>41242.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Ben WILLIAMS (AUS)</td>
      <td>CREAM Matthew (AUS)</td>
      <td>ANAZ Hakan (AUS)</td>
      <td>255951.0</td>
      <td>300186459.0</td>
      <td>CRC</td>
      <td>GRE</td>
    </tr>
    <tr>
      <th>840</th>
      <td>2014.0</td>
      <td>30 Jun 2014 - 13:00</td>
      <td>Round of 16</td>
      <td>Estadio Nacional</td>
      <td>Brasilia</td>
      <td>France</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>Nigeria</td>
      <td></td>
      <td>67882.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>GEIGER Mark (USA)</td>
      <td>HURD Sean (USA)</td>
      <td>FLETCHER Joe (CAN)</td>
      <td>255951.0</td>
      <td>300186462.0</td>
      <td>FRA</td>
      <td>NGA</td>
    </tr>
    <tr>
      <th>841</th>
      <td>2014.0</td>
      <td>30 Jun 2014 - 17:00</td>
      <td>Round of 16</td>
      <td>Estadio Beira-Rio</td>
      <td>Porto Alegre</td>
      <td>Germany</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>Algeria</td>
      <td>Germany win after extra time</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>RICCI Sandro (BRA)</td>
      <td>DE CARVALHO Emerson (BRA)</td>
      <td>VAN GASSE Marcelo (BRA)</td>
      <td>255951.0</td>
      <td>300186460.0</td>
      <td>GER</td>
      <td>ALG</td>
    </tr>
    <tr>
      <th>842</th>
      <td>2014.0</td>
      <td>01 Jul 2014 - 13:00</td>
      <td>Round of 16</td>
      <td>Arena de Sao Paulo</td>
      <td>Sao Paulo</td>
      <td>Argentina</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>Switzerland</td>
      <td>Argentina win after extra time</td>
      <td>63255.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>ERIKSSON Jonas (SWE)</td>
      <td>KLASENIUS Mathias (SWE)</td>
      <td>WARNMARK Daniel (SWE)</td>
      <td>255951.0</td>
      <td>300186503.0</td>
      <td>ARG</td>
      <td>SUI</td>
    </tr>
    <tr>
      <th>843</th>
      <td>2014.0</td>
      <td>01 Jul 2014 - 17:00</td>
      <td>Round of 16</td>
      <td>Arena Fonte Nova</td>
      <td>Salvador</td>
      <td>Belgium</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>USA</td>
      <td>Belgium win after extra time</td>
      <td>51227.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>HAIMOUDI Djamel (ALG)</td>
      <td>ACHIK Redouane (MAR)</td>
      <td>ETCHIALI Abdelhak (ALG)</td>
      <td>255951.0</td>
      <td>300186497.0</td>
      <td>BEL</td>
      <td>USA</td>
    </tr>
    <tr>
      <th>844</th>
      <td>2014.0</td>
      <td>04 Jul 2014 - 13:00</td>
      <td>Quarter-finals</td>
      <td>Estadio do Maracana</td>
      <td>Rio De Janeiro</td>
      <td>France</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Germany</td>
      <td></td>
      <td>74240.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>PITANA Nestor (ARG)</td>
      <td>MAIDANA Hernan (ARG)</td>
      <td>BELATTI Juan Pablo (ARG)</td>
      <td>255953.0</td>
      <td>300186485.0</td>
      <td>FRA</td>
      <td>GER</td>
    </tr>
    <tr>
      <th>845</th>
      <td>2014.0</td>
      <td>04 Jul 2014 - 17:00</td>
      <td>Quarter-finals</td>
      <td>Estadio Castelao</td>
      <td>Fortaleza</td>
      <td>Brazil</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>Colombia</td>
      <td></td>
      <td>60342.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>Carlos VELASCO CARBALLO (ESP)</td>
      <td>ALONSO FERNANDEZ Roberto (ESP)</td>
      <td>YUSTE Juan (ESP)</td>
      <td>255953.0</td>
      <td>300186461.0</td>
      <td>BRA</td>
      <td>COL</td>
    </tr>
    <tr>
      <th>846</th>
      <td>2014.0</td>
      <td>05 Jul 2014 - 13:00</td>
      <td>Quarter-finals</td>
      <td>Estadio Nacional</td>
      <td>Brasilia</td>
      <td>Argentina</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>Belgium</td>
      <td></td>
      <td>68551.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>Nicola RIZZOLI (ITA)</td>
      <td>Renato FAVERANI (ITA)</td>
      <td>Andrea STEFANI (ITA)</td>
      <td>255953.0</td>
      <td>300186504.0</td>
      <td>ARG</td>
      <td>BEL</td>
    </tr>
    <tr>
      <th>847</th>
      <td>2014.0</td>
      <td>05 Jul 2014 - 17:00</td>
      <td>Quarter-finals</td>
      <td>Arena Fonte Nova</td>
      <td>Salvador</td>
      <td>Netherlands</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Costa Rica</td>
      <td>Netherlands win on penalties (4 - 3)</td>
      <td>51179.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Ravshan IRMATOV (UZB)</td>
      <td>RASULOV Abduxamidullo (UZB)</td>
      <td>KOCHKAROV Bakhadyr (KGZ)</td>
      <td>255953.0</td>
      <td>300186488.0</td>
      <td>NED</td>
      <td>CRC</td>
    </tr>
    <tr>
      <th>848</th>
      <td>2014.0</td>
      <td>08 Jul 2014 - 17:00</td>
      <td>Semi-finals</td>
      <td>Estadio Mineirao</td>
      <td>Belo Horizonte</td>
      <td>Brazil</td>
      <td>1.0</td>
      <td>7.0</td>
      <td>Germany</td>
      <td></td>
      <td>58141.0</td>
      <td>0.0</td>
      <td>5.0</td>
      <td>RODRIGUEZ Marco (MEX)</td>
      <td>TORRENTERA Marvin (MEX)</td>
      <td>QUINTERO Marcos (MEX)</td>
      <td>255955.0</td>
      <td>300186474.0</td>
      <td>BRA</td>
      <td>GER</td>
    </tr>
    <tr>
      <th>849</th>
      <td>2014.0</td>
      <td>09 Jul 2014 - 17:00</td>
      <td>Semi-finals</td>
      <td>Arena de Sao Paulo</td>
      <td>Sao Paulo</td>
      <td>Netherlands</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Argentina</td>
      <td>Argentina win on penalties (2 - 4)</td>
      <td>63267.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>C�neyt �AKIR (TUR)</td>
      <td>DURAN Bahattin (TUR)</td>
      <td>ONGUN Tarik (TUR)</td>
      <td>255955.0</td>
      <td>300186490.0</td>
      <td>NED</td>
      <td>ARG</td>
    </tr>
    <tr>
      <th>850</th>
      <td>2014.0</td>
      <td>12 Jul 2014 - 17:00</td>
      <td>Play-off for third place</td>
      <td>Estadio Nacional</td>
      <td>Brasilia</td>
      <td>Brazil</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>Netherlands</td>
      <td></td>
      <td>68034.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>HAIMOUDI Djamel (ALG)</td>
      <td>ACHIK Redouane (MAR)</td>
      <td>ETCHIALI Abdelhak (ALG)</td>
      <td>255957.0</td>
      <td>300186502.0</td>
      <td>BRA</td>
      <td>NED</td>
    </tr>
    <tr>
      <th>851</th>
      <td>2014.0</td>
      <td>13 Jul 2014 - 16:00</td>
      <td>Final</td>
      <td>Estadio do Maracana</td>
      <td>Rio De Janeiro</td>
      <td>Germany</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>Argentina</td>
      <td>Germany win after extra time</td>
      <td>74738.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Nicola RIZZOLI (ITA)</td>
      <td>Renato FAVERANI (ITA)</td>
      <td>Andrea STEFANI (ITA)</td>
      <td>255959.0</td>
      <td>300186501.0</td>
      <td>GER</td>
      <td>ARG</td>
    </tr>
  </tbody>
</table>
<p>852 rows × 20 columns</p>
</div>



Aside from the .isnull() method, we can also use a simple equality check:


```python
df[df.Year==1930]
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
      <th>Year</th>
      <th>Datetime</th>
      <th>Stage</th>
      <th>Stadium</th>
      <th>City</th>
      <th>Home Team Name</th>
      <th>Home Team Goals</th>
      <th>Away Team Goals</th>
      <th>Away Team Name</th>
      <th>Win conditions</th>
      <th>Attendance</th>
      <th>Half-time Home Goals</th>
      <th>Half-time Away Goals</th>
      <th>Referee</th>
      <th>Assistant 1</th>
      <th>Assistant 2</th>
      <th>RoundID</th>
      <th>MatchID</th>
      <th>Home Team Initials</th>
      <th>Away Team Initials</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1930.0</td>
      <td>13 Jul 1930 - 15:00</td>
      <td>Group 1</td>
      <td>Pocitos</td>
      <td>Montevideo</td>
      <td>France</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>Mexico</td>
      <td></td>
      <td>4444.0</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>LOMBARDI Domingo (URU)</td>
      <td>CRISTOPHE Henry (BEL)</td>
      <td>REGO Gilberto (BRA)</td>
      <td>201.0</td>
      <td>1096.0</td>
      <td>FRA</td>
      <td>MEX</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1930.0</td>
      <td>13 Jul 1930 - 15:00</td>
      <td>Group 4</td>
      <td>Parque Central</td>
      <td>Montevideo</td>
      <td>USA</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>Belgium</td>
      <td></td>
      <td>18346.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>MACIAS Jose (ARG)</td>
      <td>MATEUCCI Francisco (URU)</td>
      <td>WARNKEN Alberto (CHI)</td>
      <td>201.0</td>
      <td>1090.0</td>
      <td>USA</td>
      <td>BEL</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1930.0</td>
      <td>14 Jul 1930 - 12:45</td>
      <td>Group 2</td>
      <td>Parque Central</td>
      <td>Montevideo</td>
      <td>Yugoslavia</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>Brazil</td>
      <td></td>
      <td>24059.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>TEJADA Anibal (URU)</td>
      <td>VALLARINO Ricardo (URU)</td>
      <td>BALWAY Thomas (FRA)</td>
      <td>201.0</td>
      <td>1093.0</td>
      <td>YUG</td>
      <td>BRA</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1930.0</td>
      <td>14 Jul 1930 - 14:50</td>
      <td>Group 3</td>
      <td>Pocitos</td>
      <td>Montevideo</td>
      <td>Romania</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>Peru</td>
      <td></td>
      <td>2549.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>WARNKEN Alberto (CHI)</td>
      <td>LANGENUS Jean (BEL)</td>
      <td>MATEUCCI Francisco (URU)</td>
      <td>201.0</td>
      <td>1098.0</td>
      <td>ROU</td>
      <td>PER</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1930.0</td>
      <td>15 Jul 1930 - 16:00</td>
      <td>Group 1</td>
      <td>Parque Central</td>
      <td>Montevideo</td>
      <td>Argentina</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>France</td>
      <td></td>
      <td>23409.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>REGO Gilberto (BRA)</td>
      <td>SAUCEDO Ulises (BOL)</td>
      <td>RADULESCU Constantin (ROU)</td>
      <td>201.0</td>
      <td>1085.0</td>
      <td>ARG</td>
      <td>FRA</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1930.0</td>
      <td>16 Jul 1930 - 14:45</td>
      <td>Group 1</td>
      <td>Parque Central</td>
      <td>Montevideo</td>
      <td>Chile</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>Mexico</td>
      <td></td>
      <td>9249.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>CRISTOPHE Henry (BEL)</td>
      <td>APHESTEGUY Martin (URU)</td>
      <td>LANGENUS Jean (BEL)</td>
      <td>201.0</td>
      <td>1095.0</td>
      <td>CHI</td>
      <td>MEX</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1930.0</td>
      <td>17 Jul 1930 - 12:45</td>
      <td>Group 2</td>
      <td>Parque Central</td>
      <td>Montevideo</td>
      <td>Yugoslavia</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>Bolivia</td>
      <td></td>
      <td>18306.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>MATEUCCI Francisco (URU)</td>
      <td>LOMBARDI Domingo (URU)</td>
      <td>WARNKEN Alberto (CHI)</td>
      <td>201.0</td>
      <td>1092.0</td>
      <td>YUG</td>
      <td>BOL</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1930.0</td>
      <td>17 Jul 1930 - 14:45</td>
      <td>Group 4</td>
      <td>Parque Central</td>
      <td>Montevideo</td>
      <td>USA</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>Paraguay</td>
      <td></td>
      <td>18306.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>MACIAS Jose (ARG)</td>
      <td>APHESTEGUY Martin (URU)</td>
      <td>TEJADA Anibal (URU)</td>
      <td>201.0</td>
      <td>1097.0</td>
      <td>USA</td>
      <td>PAR</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1930.0</td>
      <td>18 Jul 1930 - 14:30</td>
      <td>Group 3</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Uruguay</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>Peru</td>
      <td></td>
      <td>57735.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>LANGENUS Jean (BEL)</td>
      <td>BALWAY Thomas (FRA)</td>
      <td>CRISTOPHE Henry (BEL)</td>
      <td>201.0</td>
      <td>1099.0</td>
      <td>URU</td>
      <td>PER</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1930.0</td>
      <td>19 Jul 1930 - 12:50</td>
      <td>Group 1</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Chile</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>France</td>
      <td></td>
      <td>2000.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>TEJADA Anibal (URU)</td>
      <td>LOMBARDI Domingo (URU)</td>
      <td>REGO Gilberto (BRA)</td>
      <td>201.0</td>
      <td>1094.0</td>
      <td>CHI</td>
      <td>FRA</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1930.0</td>
      <td>19 Jul 1930 - 15:00</td>
      <td>Group 1</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Argentina</td>
      <td>6.0</td>
      <td>3.0</td>
      <td>Mexico</td>
      <td></td>
      <td>42100.0</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>SAUCEDO Ulises (BOL)</td>
      <td>ALONSO Gualberto (URU)</td>
      <td>RADULESCU Constantin (ROU)</td>
      <td>201.0</td>
      <td>1086.0</td>
      <td>ARG</td>
      <td>MEX</td>
    </tr>
    <tr>
      <th>11</th>
      <td>1930.0</td>
      <td>20 Jul 1930 - 13:00</td>
      <td>Group 2</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Brazil</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>Bolivia</td>
      <td></td>
      <td>25466.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>BALWAY Thomas (FRA)</td>
      <td>MATEUCCI Francisco (URU)</td>
      <td>VALLEJO Gaspar (MEX)</td>
      <td>201.0</td>
      <td>1091.0</td>
      <td>BRA</td>
      <td>BOL</td>
    </tr>
    <tr>
      <th>12</th>
      <td>1930.0</td>
      <td>20 Jul 1930 - 15:00</td>
      <td>Group 4</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Paraguay</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>Belgium</td>
      <td></td>
      <td>12000.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>VALLARINO Ricardo (URU)</td>
      <td>MACIAS Jose (ARG)</td>
      <td>LOMBARDI Domingo (URU)</td>
      <td>201.0</td>
      <td>1089.0</td>
      <td>PAR</td>
      <td>BEL</td>
    </tr>
    <tr>
      <th>13</th>
      <td>1930.0</td>
      <td>21 Jul 1930 - 14:50</td>
      <td>Group 3</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Uruguay</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>Romania</td>
      <td></td>
      <td>70022.0</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>REGO Gilberto (BRA)</td>
      <td>WARNKEN Alberto (CHI)</td>
      <td>SAUCEDO Ulises (BOL)</td>
      <td>201.0</td>
      <td>1100.0</td>
      <td>URU</td>
      <td>ROU</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1930.0</td>
      <td>22 Jul 1930 - 14:45</td>
      <td>Group 1</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Argentina</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>Chile</td>
      <td></td>
      <td>41459.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>LANGENUS Jean (BEL)</td>
      <td>CRISTOPHE Henry (BEL)</td>
      <td>SAUCEDO Ulises (BOL)</td>
      <td>201.0</td>
      <td>1084.0</td>
      <td>ARG</td>
      <td>CHI</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1930.0</td>
      <td>26 Jul 1930 - 14:45</td>
      <td>Semi-finals</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Argentina</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>USA</td>
      <td></td>
      <td>72886.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>LANGENUS Jean (BEL)</td>
      <td>VALLEJO Gaspar (MEX)</td>
      <td>WARNKEN Alberto (CHI)</td>
      <td>202.0</td>
      <td>1088.0</td>
      <td>ARG</td>
      <td>USA</td>
    </tr>
    <tr>
      <th>16</th>
      <td>1930.0</td>
      <td>27 Jul 1930 - 14:45</td>
      <td>Semi-finals</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Uruguay</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>Yugoslavia</td>
      <td></td>
      <td>79867.0</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>REGO Gilberto (BRA)</td>
      <td>SAUCEDO Ulises (BOL)</td>
      <td>BALWAY Thomas (FRA)</td>
      <td>202.0</td>
      <td>1101.0</td>
      <td>URU</td>
      <td>YUG</td>
    </tr>
    <tr>
      <th>17</th>
      <td>1930.0</td>
      <td>30 Jul 1930 - 14:15</td>
      <td>Final</td>
      <td>Estadio Centenario</td>
      <td>Montevideo</td>
      <td>Uruguay</td>
      <td>4.0</td>
      <td>2.0</td>
      <td>Argentina</td>
      <td></td>
      <td>68346.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>LANGENUS Jean (BEL)</td>
      <td>SAUCEDO Ulises (BOL)</td>
      <td>CRISTOPHE Henry (BEL)</td>
      <td>405.0</td>
      <td>1087.0</td>
      <td>URU</td>
      <td>ARG</td>
    </tr>
  </tbody>
</table>
</div>



Or we can use string methods to filter based on text:


```python
df[df['Home Team Name'].str.contains('M')]
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-14-8f5cb2ac3c7f> in <module>()
    ----> 1 df[df['Home Team Name'].str.contains('M')]
    

    ~/anaconda3/lib/python3.6/site-packages/pandas/core/frame.py in __getitem__(self, key)
       2677         if isinstance(key, (Series, np.ndarray, Index, list)):
       2678             # either boolean or fancy integer index
    -> 2679             return self._getitem_array(key)
       2680         elif isinstance(key, DataFrame):
       2681             return self._getitem_frame(key)


    ~/anaconda3/lib/python3.6/site-packages/pandas/core/frame.py in _getitem_array(self, key)
       2704     def _getitem_array(self, key):
       2705         # also raises Exception if object array with NA values
    -> 2706         if com.is_bool_indexer(key):
       2707             # warning here just in case -- previously __setitem__ was
       2708             # reindexing but __getitem__ was not; it seems more reasonable to


    ~/anaconda3/lib/python3.6/site-packages/pandas/core/common.py in is_bool_indexer(key)
        102             if not lib.is_bool_array(key):
        103                 if isna(key).any():
    --> 104                     raise ValueError('cannot index with vector containing '
        105                                      'NA / NaN values')
        106                 return False


    ValueError: cannot index with vector containing NA / NaN values


Whoops! Now you see one of many reasons why we might need to remove (or fill) null values.
Which leads us to some time for practice!

### Practice Questions <a id="practice"></a>

1. Subset the DataFrame to only non-null rows.


```python
#Your code for question 1 goes here.
```

2. How many of the matches were in Montevideo?  


```python
#Your code for question 2 goes here.
```

3. How many matches did USA play in 2014?  

Hint: they could have been home or away.  

You can combine conditions like this:  
df[(condition1) | (condition2)] #Returns rows where either condition is true  
df[(condition1) & (condition2)] #Returns rows where both conditions are true  


```python
#Your code for question 3 goes here.
```

4. How many teams played in 1986?


```python
#Your code for question 4 goes here.
```

5. How many matches were there with 5 or more total goals?


```python
#Your code for question 5 goes here.
```

6. Come up with and answer, two other questions you could answer by filtering or subsetting. this DataFrame.


```python
#6a Question:

#6a Solution (with code):
```


```python
#6b Question:

#6b Solution (with code):
```

## [Back to Top](#toc)
