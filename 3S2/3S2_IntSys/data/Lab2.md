# Data preprocessing & Visualization
---
[Go Back](../README.md)

---
## Introduction
### Objectives
- Understand the data
- Remove or fill empty rows or columns
- Eliminate inconsistent values
### Some concepts
- Data is structured in `DataFrames` that contains `Series`
	- `DataFrame` is a two-dimensional labelled data structure (Similar to a matrix).
	- `Series` is a one-dimensional labelled data structure (Similar to an array).
	- Each column in a `DataFrame` is a `Series`.
 - Some functions return a modified version of a `DataFrame`.
	 - By default they do not modify the `DataFrame`.
	 - To modify directly without generating a copy specify the arg `inplace=True` .
---
## Obtaining the data
```python
import pandas as pd

data_source = "..." # Can be an URL or a local path.

# Read from csv file 
data = pd.read_csv(data_source)

# Read from pickle file (Serialize oython objects)
# More storage efficient and stores the type of data
data = pd.read_pickle(data_source)

# Read from JSON file
data = pd.read_json(data_source)

# Read from a sheet of an Excel file
data = pd.read_excel('data.xlsx', sheet_name='Sheet1')
```
---
## Exploring the data
### Counting columns & rows
```python
# Count rows
len(data)

# Get list of column names
data.columns

# Count columns
len(data.columns)

# Get a tuple (number rows , number columns)
data.shape
```
### Accessing the data
```python
# Accesss the first N rows
data.head(N)

# Accesss the last N rows
data.tail(N)

# Access a column
data['MyCol']

# Access multiple columns
data[['Driver', 'Team']]

# Get an array representation
data.values
```
### Filtering data
```python
# Get the row number as a DataFrame
data.loc[row]

# Access a position (row is an index but col a col name)
data.loc[row, 'MyCol']

# Access a position (row and col are the index numbers)
data.iloc[row, col]

# Filter by condition
data.loc[condition]
# Examples:
data.loc[ data['MyCol'] == value ]
data.loc[ data['MyCol'] >  value ]
data.loc[ (data['MyCol1'] > value1) & (data['MyCol2'] > value2) ]
data.loc[ data['MyCol'].isin( [value1, value2] ) ]
data.loc[ data['MyCol'].str.contains(value)]

# Sorting data
data.sort_values(ascending = False).reset_index()

# Grouping data by same MyCol1
data.groupby('MyCol1') # Some other thing must be applied to the grouped data
# Example.
data.groupby('MyCol1')['MyCol2'].unique()
data.groupby('MyCol1')['MyCol2'].mean()
data.groupby('MyCol1')['MyCol2'].max()
```
### Statistics
```python
# For each column obtaine number non-null and type
data.info()

# Get statistics all columns or an specific columns
data.describe()
data['MyCol'].describe()

# Get unique values for a column
data['MyCol'].unique()

# Get number of unique values for a column
data['MyCol'].nunique()

# Get if there are empty values
data.isnull().any()
data['MyCol'].isnull().any()

# Get the number of empty values
data.isnull().sum()
data['MyCol'].isnull().sum()

# Other statistics
data['MyCol'].mean()   # Mean (average)
data['MyCol'].median() # Median
data['MyCol'].mode()   # Mode (most frequent value)
data['MyCol'].min()
data['MyCol'].max()
data['MyCol'].std()    # Standard deviation
data['MyCol'].var()    # Variance
```
---
## Cleaning data
### Changing types
```python
# Check data types of each column
data.dtypes

# Change column type to another primitive type
# type can be: int, float, str, bool
data['MyCol'] = data['MyCol'].astype(type)

# Convert dates to datetime format
data['MyCol'] = pd.to_datetime(data['MyCol'])

# Convert a column to timedelta (useful for duration calculations)
data['MyCol'] = pd.to_timedelta(data['MyCol'])
```
### Dealing with unwanted values
```python
# Remove a column
data.drop(columns = ['MyCol'], inplace = True)

# Remove the row at position N
data.drop(N, inplace = True)

# Remove rows with missing values
data.dropna(inplace=True)

# Remove columns with missing values
data.dropna(axis=1, inplace=True)

# Drop rows where a specific column has missing values
data.dropna(subset=['MyCol'], inplace=True)

# Drop rows where all values are missing
data.dropna(how='all', inplace=True)

# Fill missign cells of a column with a value
data['MyCol'].fillna(value, inplace=True)
```
---
## Saving data
```python
data.to_pickle('my_data.pkl')
```
---
## Visualisation
```python
import matplotlib.pyplot as plt
import seaborn as sns

sns.set_style('whitegrid') # Sets the style of the plots

plt.figure(figsize = (12,6)) # Size for the graph
hist = sns.type_of_plot() # Use the funtion to plot the desired graph
hist.set_xlabel("X label")
hist.set_ylabel("Y label")
hist.set_title("Title")
plt.show()
```
- For `1` variable:
	- Histogram (quantitative): `sns.histplot()`
	- Histogram (categorical): `sns.countplot()`
	- `sns.kdeplot()`
- For `2` variables:
	- Bars: `sns.barplot`
	- Line: `sns.lineplot`
	- Scatter: `sns.scatterplot`
	- Regression line: `sns.regplot`
---