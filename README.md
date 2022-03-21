# Movies Extract, Transform and Load

## "Module 8 Challenge"

The purpose of this challenge is to create an automated pipeline that takes in new data, performs the appropriate transformations, and loads the data into existing tables.

The coding is refactored to create one function, that takes in, the three files:

* Wikipedia data
* Kaggle metadata, and
* MovieLens rating

and with these information, the ETL process takes place by adding the data to a PostgreSQL database in two tables:

* Movies, and
* Ratings

This is done using Python (Jupyter Notebook) and pgAdmin 4, and their capabilities to read, filter, sort, append, replace, drop, order, groupby, functions, regex, etc.


## Deliverable 1

ETL function written to read in the three data files.

![11](Images/11.png)

The function converts the Wikipedia JSON file to a Pandas DataFrame, and the DataFrame is displayed in the ETL_function_test.ipynb file.

![12](Images/12.png)

​The function converts the Kaggle metadata file to a Pandas DataFrame, and the DataFrame is displayed in the ETL_function_test.ipynb file.

The conversion to DF was done on "ETL_function_test.ipynb" file's step # 8.

![13](Images/13.png)

​The function converts the MovieLens ratings data file to a Pandas DataFrame, and the DataFrame is displayed in the ETL_function_test.ipynb file.

The conversion to DF was done on "ETL_function_test.ipynb" file's step # 8.

![14](Images/14.png)


## Deliverable 2

The TV shows are filtered out, and the wiki_movies_df DataFrame is created.

![21](Images/21.png)

A try-except block is used to catch errors while extracting the IMDb IDs with a regular expression and dropping duplicate IDs.

![22](Images/22.png)

The extraction and transformation of the Wikipedia data in the ETL function does the following:

* A list comprehension is used to keep columns with non-null values.

![23](Images/23.png)

* The non-null box office data is converted to string values using the lambda and join functions.

![24](Images/24.png)

* A regular expression is used to match the six elements of "form_one" of the box office data.

![25](Images/25.png)

* A regular expression is used to match the three elements of "form_two" of the box office data.

![26](Images/26.png)

The following columns are cleaned in the Wikipedia DataFrame:

* The box office column

![27](Images/27.png)

* The budget column

![28](Images/28.png)

* The release date column

![29](Images/29.png)

* The running time column
​
![210](Images/210.png)

The cleaned Wikipedia data is converted to a Pandas DataFrame, and the DataFrame is displayed in the ETL_clean_wiki_movies.ipynb file.

![211](Images/211.png)


## Deliverable 3

The "Extraction and Transformation" of the Kaggle metadata, using the ETL function does the following:

The Kaggle metadata is cleaned.

![31](Images/31.png)

The Wikipedia and Kaggle DataFrames are merged.

![32](Images/32.png)

The following is performed on the merged Wikipedia and Kaggle DataFrames to create the movies_df:

* Unnecessary columns are dropped.

![33](Images/33.png)

* A function is used to fill in the missing Kaggle data.

![34](Images/34.png)

* The movies_df DataFrame is filtered to keep specific columns.

![35](Images/35.png)

* The movies_df DataFrame columns are renamed.

![36](Images/36.png)

The "Extraction and Transformation" of the MovieLens ratings data using the ETL function does the following:

* The ratings counts are cleaned.

![37](Images/37.png)

* The movies_df DataFrame is merged with the cleaned ratings DataFrame to create the * movies_with_ratings_df DataFrame.

![38](Images/38.png)

* The empty values in the movies_with_ratings_df DataFrame are filled with “0”.

![39](Images/39.png)

The movies_with_ratings_df and the movies_df DataFrames are displayed in the ETL_clean_kaggle_data.ipynb file.

![310](Images/310.png)

![311](Images/311.png)


## Deliverable 4

The data from the movies_df DataFrame replaces the current data in the movies table in the SQL database, as determined by the movies_query.png.

![41](Images/movies_query.png)

The data from the MovieLens rating CSV file is added to the ratings table in the SQL database, as determined by the ratings_query.png.

![42](Images/ratings_query.png)

The elapsed time to add the data to the database is displayed in the ETL_create_database.ipynb file.

![43](Images/43.png)