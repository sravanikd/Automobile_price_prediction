Notes:

1.The Pandas Library is a useful tool that enables us to read various datasets into a data frame;

2.Used pandas.read_csv() function to read the csv file. 
Because the data does not include headers, an argument headers = None inside the read_csv() method is added, so that pandas will not automatically set the first row as a header.

3. dataframe.head(n) method to check the top n rows of the dataframe; dataframe.head() shows 5 rows from the top.

4.drop missing values along the column "price" as follows:
  df.dropna(subset=["col_name"], axis=0)
  
5.save the dataframe df as automobile.csv to your local machine, you may use the syntax below:
            Data-Format	  Read	        Save
            csv	      pd.read_csv()	  df.to_csv()
            json	    pd.read_json()	df.to_json()
            excel	    pd.read_excel()	df.to_excel()
            hdf	      pd.read_hdf()	  df.to_hdf()
            sql	      pd.read_sql()	  df.to_sql()
6.df.dtypes : to check data types of attributes of our dataset

7. df.describe() :
This method will provide various summary statistics, excluding NaN (Not a Number) values
get a statistical summary of each column, such as count, column mean value, column standard deviation, etc

   df.describe(include = "all") : describe all the columns in "df" 
  
  
8.You can select the columns of a data frame by indicating the name of each column, for example, you can select the three columns as follows:

    dataframe[[' column 1 ',column 2', 'column 3']] 

9.Where "column" is the name of the column, you can apply the method ".describe()" to get the statistics of those columns as follows:

dataframe[[' column 1 ',column 2', 'column 3'] ].describe()

10.dataframe.info :It provides a concise summary of your DataFrame.

11. If no headers by default. Create a list of headers and attribute them to df.columns
      ex: headers=[1,2,3,4]
          df.columns=headers
