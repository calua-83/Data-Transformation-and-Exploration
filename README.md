# Data-Transformation-and-Exploration
Data Transformation and Exploration for Adventure Works Sales Data

## Introduction
 In this project, we're working with the Adventure Works database to generate sales reports using SQLite and the pandas data analysis library in Python. The 
 goal is to perform data extraction, preprocessing, and exploratory data analysis to understand the sales data better and prepare it for reporting or 
 further analysis.
 
## Setting up SQLite Database Connection

- First, we establish a connection to the SQLite database that contains the Adventure Works data.
   import sqlite3
   import pandas as pd
- We then Connected to the SQLite database path = (r'C:\Users\calua\Desktop\3Signet\Sales_Adventure_Works.db')
  connect = sqlite3.connect(path)
  
## Retrieving Table Names from the Database
To understand what data is available, we retrieve and list all the table names in the database.
  cursor = connect.cursor()
  Select all tables in the sales adventure works database
  cursor.execute("Select name from sqlite_master where type ='table';")
  tables = cursor.fetchall()
  
  ## Loading Tables into Pandas DataFrames
  We define a function to load each table into a pandas DataFrame for easier data manipulation.
  Using teh function to takes an SQL query as input and returns a pandas DataFrame containing the results.
  
 ## Data Preprocessing and Validation 
 #### Overview of DataFrames
 - We started by inspecting each DataFrame to understand the data structure, column names, data types, and check for any null values.
 - After loading the data into DataFrames, the next step was to preprocess and validate it.
 - Our data preprocessing tasks included:
    - Handling missing values: Checking for null values in each DataFrame.
    -	Data type conversion: For example, converting date columns to the proper datetime format and ensuring numeric fields (like AnnualIncome) are in the 
      right data type (float).
     	
  ## Resolving Data Quality Issues
  	- Data Quality Issues were identifies and resolved, issues such as incorrect data types and unwanted characters (e.g., commas in numbers, currency 
      symbols).•	Example: Converting the AnnualIncome column to a numeric data type:
    - We standardize string columns by stripping whitespace and capitalizing names to ensure consistency.

  #### Normalize string columns
         query_Customers['FirstName'] = query_Customers['FirstName'].str.strip().str.capitalize()
         query_Customers['LastName'] = query_Customers['LastName'].str.strip().str.capitalize()
         query_Customers['Prefix'] = query_Customers['Prefix'].str.strip().str.capitalize()
         query_Customers.head(5)
         
  ##### Explanation:
	      - The str.strip() method removes leading and trailing whitespace.
	      - The str.capitalize() method converts the first character to uppercase and the rest to lowercase.
         - This helps in maintaining consistency, especially when merging data or performing group-by operations.
         
   ## Detecting Outliers Using the Interquartile Range (IQR) Method
   Outliers can skew analysis hence the need to be investigated or handled appropriately.
   
   #####  We apply the outlier detection function to the following columns:
          •	OrderQuantity in query_sales
          •	ReturnQuantity in query_returns
          •	AnnualIncome in query_Customers
  ##### Observations:
          o	For ReturnQuantity, we find some entries where the return quantity is higher than expected.
          o	For AnnualIncome, we find customers with unusually high incomes, which could be legitimate high earners or data entry errors.

  ## Visualizing Outliers with Boxplots
     We created boxplots to visualize the distribution of data and highlight the outliers.
  ##### Explanation:
       o	We used Seaborn's boxplot to visualize the distribution of the data.
       o	Outliers are automatically indicated in the boxplot, but we can add scatter points to highlight them explicitly.
       o	This visual representation helps in understanding the extent and impact of the outliers.

       ![]([


 ## Conclusion
 This detailed explanation walks through some of the steps taken in transformation and exploration process . By carefully inspecting, cleaning, and 
 visualizing the data ,we are setting a solid foundation for generating insightful sales reports and making data-driven decisions.


    


