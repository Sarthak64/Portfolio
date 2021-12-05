# Project: Data Loading 
Data 1202 – Data Analysis Tools Analytics
Sarthak Bhayana - 100807101

## Getting Started

### `Prerequisites` 
1) Python Version 3.8 or above (https://www.python.org/downloads)
2) Anaconda (https://www.anaconda.com/products/individual)

### `Installation`
```
pip install mysql-connector-python
```
### `Import Libraries`
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sqlalchemy import create_engine
```

pandas help in storing the data in tabular format. This helps in easy daTa manipulation and wrangling.  [Documentation](https://pandas.pydata.org/docs/)

NumPy is a library for the Python programming language, adding support for large, multi-dimensional arrays and matrices, along with a large collection of high-level mathematical data.library for Python, NumPy adds support for big, multi-dimensional arrays and matrices and a vast number of high-level mathematical functions that may be used to work on these arrays. [Documentation](https://numpy.org/doc/stable/user/whatisnumpy.html)

For the Python programming language and its NumPy extension, Matplotlib is a charting or a visualization libraryof the common GUI toolkits that may be used to embed plots into programmes. [Documentation](https://matplotlib.org/stable/)

### `Load complete Dataset`
```
data = pd.read_csv("youtube_dataset.csv")
data.head()
```

#### pandas.read_csv
DataFrame may be read from a comma-separated (csv) file. In addition, the file can be broken into parts or iterated upon. [More Info](https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html#pandas-read-csv)

### `Function to Calculate Channel Type Distribution`
```
def ChannelTypeDist(df, row_select):
    filter_data= data.iloc[:row_select, [2,9]]
    dist_data = filter_data.groupby(['channeltype'],sort = True).count() 
    return dist_data
```

the function above seledts rows 2 to 8 from dataset and group them on the paramter= "channeltype"

#### pandas.DataFrame.iloc
Indexing for positional selection that is only dependent on integer location. It's possible to use the iloc[] function with either an integer or a boolean array, depending on your needs. [More Info](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.iloc.html)

#### pandas.DataFrame.groupby
You may either use a mapper or a series of columns to group DataFrames. Splitting the object, applying a function, and combining the results are all part of groupby operations. When dealing with vast volumes of data, this may be a useful tool. [More Info](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.groupby.html)

### `Load to CSV`
```
export_data = data.iloc[:1000,:] #filter top 1000 rows
export_data.to_csv("YoutubeTop1000.csv") # Load into CSV
print('Data Loaded Successfully into CSV')
```
The iloc[:1000,:] function helps in selecting the to 1000 rows and alll the columnns from the dataset
#### pandas.DataFrame.to_csv
Write object to a comma-separated (csv) file. [More Info](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.to_csv.html)


### `Load to Database`
```
engine = create_engine("mysql+mysqldb://root:password@localhost/assignment4") #Create Connection
export_data.to_sql('YoutubeTop1000', con=engine, if_exists='append') # Load Data
print('Data Loaded Successfully into MySql')
```
#### pandas.DataFrame.to_sql
Create a SQL database from a DataFrame. SQLAlchemy [1] databases are supported. It is possible to create, add to, or overwrite tables.
[More Info](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.to_sql.html)

### Authors
Sarthak Bhayana 

## Acknowledgments
* Prof. Omar Al-Trad, Durham College 
* Python MySql-Connector Documentation


