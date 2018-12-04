# Introduction
pandas is hands down one of the best libraries of python. It supports reading and writing excel spreadsheets, CSV's and a whole lot of manipulation. It is more like a mandatory library you need to know if you’re dealing with datasets from excel files and CSV files. i.e. for machine learning and data science.

### Note
I would highly recommend that you run the examples given as you read the tutorial. It will help you a get a visual understanding of how the data is being stored and manipulated.

## Installing pandas
Simply go to your command line tool and type

`pip install pandas`

Ensure that the installation was successful by launching Python and writing,
```python
import pandas as pd
print pd.__version__
```

## Using pandas
Just import it into your program using
```python
import pandas as pd
```
and we're good to go.

# Storing Data - Data Structures
pandas introduces two new data structures to Python - Series and DataFrame, both of which are built on top of NumPy (this means it's fast).

## Series
A Series is a one-dimensional object similar to an array, list, or column in a table. It will assign a labeled index to each item in the Series. By default, each item will receive an index label from 0 to N, where N is the length of the Series minus one.

```python
# create a Series with an arbitrary list
s = pd.Series([7, 'Heisenberg', 3.14, -1789710578, 'Happy Eating!'])
```

Alternatively, you can specify an index to use when creating the Series.
```python
s = pd.Series([7, 'Heisenberg', 3.14, -1789710578, 'Happy Eating!'],
              index=['A', 'Z', 'C', 'Y', 'E'])
```

The Series constructor can convert a dictonary as well, using the keys of the dictionary as its index.
```python
d = {'Chicago': 1000, 'New York': 1300, 'Portland': 900, 'San Francisco': 1100,
     'Austin': 450, 'Boston': None}
cities = pd.Series(d)
```

### Working with a pandas Series
You can use the index to select specific items from the Series.
```python
cities[['Chicago', 'Portland', 'San Francisco']]
```

Or you can use boolean indexing for selection.
```python
cities[cities < 1000] # selects all cities with value < 1000
```

You can also change the values in a Series on the fly.
```python
# changing based on the index
print('Old value:', cities['Chicago'])
cities['Chicago'] = 1400
print('New value:', cities['Chicago'])
```

Mathematical operations can be done using scalars and functions.
```python
# divide city values by 3
cities / 3
```

## Dataframe
A DataFrame is a tablular data structure comprised of rows and columns, akin to a spreadsheet, database table, or R's data.frame object. You can also think of a DataFrame as a group of Series objects that share an index (the column names).

### Reading data
To create a DataFrame out of common Python data structures, we can pass a dictionary of lists to the DataFrame constructor.

Using the columns parameter allows us to tell the constructor how we'd like the columns ordered. By default, the DataFrame constructor will order the columns alphabetically (though this isn't the case when reading from a file).
```python
data = {'year': [2010, 2011, 2012, 2011, 2012, 2010, 2011, 2012],
        'team': ['Bears', 'Bears', 'Bears', 'Packers', 'Packers', 'Lions', 'Lions', 'Lions'],
        'wins': [11, 8, 10, 15, 11, 6, 10, 4],
        'losses': [5, 8, 6, 1, 5, 10, 6, 12]}
football = pd.DataFrame(data, columns=['year', 'team', 'wins', 'losses'])
```

Much more often, you'll have a dataset you want to read into a DataFrame. CSV files are one of the most common ways to store datasets.

Reading a CSV is as simple as calling the read_csv function. By default, the read_csv function expects the column separator to be a comma, but you can change that using the sep parameter.
```python
df = pd.read_csv(filepath, sep=) # stores csv data into a DataFrame df
```

### Working with a pandas DataFrame
Now that we know how to read CSV files using Python and pandas we continue with working with pandas DataFrames. We begin with the basics: head, tail, describe, info.

The head function enables us to print the first x rows. By default we see the first 5 rows but we can, of course, have a look at more or less rows. tail, as should be obvious by now, prints the last x rows. The info function gives an overview of the type of data in the DataFrame. describe is used to compute summary statistics for each numerical (default) column.

```python
df = pd.read_csv('https://vincentarelbundock.github.io/' \
'Rdatasets/csv/carData/Wong.csv', sep=',')
df.head(4) # display the first 4 rows
df.tail() # display the last 5 rows
df.info()
df.describe()
```

We can also create a new variable (column) within a pandas DataFrame, by naming it and assigning it a value.
```python
df['newCol'] = (df['someCol'] + df['otherCol'])/2
```

Other times we may also want to drop columns from a pandas DataFrame. Removing columns can be done using _drop_.
```python
df.drop('newCol')
```
Note, to drop columns, and not rows, the _axis_ argument is set to 1 and to make the changes to the DataFrame we set _inplace_ to True.

There are many methods for selecting rows of a DataFrame. One simple method is by using _query_.
In the case below, we select observations from df where sex is male and iq is greater than 80. Note that the ampersand “&“ ensures both conditions are met. One may also use the "|" (OR) symbol.
```python
df_male80 = df.query('iq > 80 & sex == "Male"')
```
***
## Further Reading
Given above was a very small demonstration of what pandas is capable of. There are a ton more methods and ways to manipulate and analyse data in pandas. Here are a few sources you can check out to learn more:
* https://pandas.pydata.org/pandas-docs/stable/
* https://www.dataquest.io/blog/pandas-python-tutorial/
* https://www.datacamp.com/community/tutorials/pandas-tutorial-dataframe-python
* https://www.marsja.se/pandas-dataframe-read-csv-excel-subset/
* https://www.dezyre.com/data-science-in-python-tutorial/pandas-introductory-tutorial-part-1
 






