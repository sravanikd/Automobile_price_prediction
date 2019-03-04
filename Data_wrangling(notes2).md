# Data Wrangling is the process of converting data from the initial format to a format that may be better for analysis.

How to work with missing data?

Steps for working with missing data:

dentify missing data
deal with missing data
correct data format

## Identify and handle missing values
### Identify missing values
    Convert "?" to NaN

In the car dataset, missing data comes with the question mark "?". We replace "?" with NaN (Not a Number), which is Python's default missing value marker, for reasons of computational speed and convenience. Here we use the function:
.replace(A, B, inplace = True) 
to replace A by B

import numpy as np

# replace "?" to NaN
df.replace("?", np.nan, inplace = True)
df.head(5)

### Evaluating for Missing Data
The missing values are converted to Python's default. We use Python's built-in functions to identify these missing values. There are two methods to detect missing data:

.isnull()
.notnull()

The output is a boolean value indicating whether the value that is passed into the argument is in fact missing data.
missing_data = df.isnull()
missing_data.head(5) .  #check if they're true or false,"True" stands for missing value, while "False" stands for not missing value.


### Count missing values in each column
Using a for loop in Python, we can quickly figure out the number of missing values in each column. As mentioned above, "True" represents a missing value, "False" means the value is present in the dataset. In the body of the for loop the method ".
value_counts()" counts the number of "True" values.

for column in missing_data.columns.values.tolist():
    print(column)
    print (missing_data[column].value_counts())
    print("")    
    
# Deal with missing data
## How to deal with missing data?
### drop data
a. drop the whole row
b. drop the whole column
c)replace data
a. replace it by mean
b. replace it by frequency
c. replace it based on other functions
Whole columns should be dropped only if most entries in the column are empty. 
In our dataset, none of the columns are empty enough to drop entirely. 


Calculate the average of the column:
ex1: avg_norm_loss = df["normalized-losses"].astype("float").mean(axis=0)
print("Average of normalized-losses:", avg_norm_loss)

Replace "NaN" by mean value in "normalized-losses" column:
ex2: df["normalized-losses"].replace(np.nan, avg_norm_loss, inplace=True)

Calculate the mean value for 'bore' column:
ex3: avg_bore=df['bore'].astype('float').mean(axis=0)
     print("Average of bore:", avg_bore)
     
Replace NaN by mean value
df["bore"].replace(np.nan, avg_bore, inplace=True)

examples with questions:

1. replace NaN in "stroke" column by mean.
avg_stroke=df['stroke'].astype('float').mean(axis=0)
df['stroke'].replace(np.nan, avg_stroke, inplace=True)

2. Calculate the mean value for the 'horsepower' column:
avg_horsepower = df['horsepower'].astype('float').mean(axis=0)
print("Average horsepower:", avg_horsepower)

3. Replace "NaN" by mean value:
df['horsepower'].replace(np.nan, avg_horsepower, inplace=True)

4.Calculate the mean value for 'peak-rpm' column:
avg_peakrpm=df['peak-rpm'].astype('float').mean(axis=0)
print("Average peak rpm:", avg_peakrpm)

5.Replace NaN by mean value:
df['peak-rpm'].replace(np.nan, avg_peakrpm, inplace=True)

6.To see which values are present in a particular column, we can use the ".value_counts()" method:
df['num-of-doors'].value_counts()

7.We can see that four doors are the most common type. We can also use the ".idxmax()" method to calculate for us the most common type automatically:

df['num-of-doors'].value_counts().idxmax()

8.The replacement procedure is very similar to what we have seen previously

replace the missing 'num-of-doors' values by the most frequent 
df["num-of-doors"].replace(np.nan, "four", inplace=True)

9. let's drop all rows that do not have price data:

# simply drop whole row with NaN in "price" column
df.dropna(subset=["price"], axis=0, inplace=True)

# reset index, because we droped two rows
df.reset_index(drop=True, inplace=True)

10. The last step in data cleaning is checking and making sure that all data is in the correct format (int, float, text or other).

In Pandas, we use

.dtype() to check the data type

.astype() to change the data type

Convert data types to proper format examples: 

df[["bore", "stroke"]] = df[["bore", "stroke"]].astype("float")
df[["normalized-losses"]] = df[["normalized-losses"]].astype("int")
df[["price"]] = df[["price"]].astype("float")
df[["peak-rpm"]] = df[["peak-rpm"]].astype("float")



