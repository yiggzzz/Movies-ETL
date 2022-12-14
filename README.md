# ETL - Extract, Transform and Load
*An ETL Movies Analysis using Python, RegEx and SQL Databases*

## Project Overview

### Challenge
Raw data exists in multiple places and forms. In order to perform any kind of data analysis, this data needs to be cleaned and structured. Data pipeline process **ETL – Extract, Transform, and Load** is a core concept in data engineering, ensuring that data is consistent, maintains its integrity, and nontheless strives for automatization of data wrangling. Without a consistent and robust data structure, it’s nearly impossible to perform any meaningful analysis. 

<p align="center">  
<img src="ETL.png" width="75%" height="75%">
</p>

<p align="center">  
    <i>Figure 1: ETL process (1).</i>
</p>

### Purpose
The Amazing Prime, a video streaming company, decided to sponsor a *hackathon*, where participants trying to predict which low budget movies being released will become popular. Participants of a hackathon need a clean data in order to perform analyses for their algorithms. In order to provide organized and clean dataset, this project focuses on *ETL** or **Extract, Transform and Load** process and includes the following:

-	**Extracting** data from two different sources. 
    - web scrape of Wikipedia website for all movies released since 1990
    - data from Kaggle website for rating data.
-	**Transforming** data using Jupyter Notebook, Python, Pandas and Python RegEx module.
-	**Loading** data using PostgreSQL and pgAdmin to host final cleaned data set.

## Overview of the code

The goal of this analysis is to create automated pipeline that extracts, transform and loads data. This analysis consists of four parts, where each step is building up from beginning of extracting data and function testing, through transformation and cleaning process to its final step connect and load to the database. The entire process of ETL can be executed with a single call of the function ***extract_transform_load*** in the final step [ETL_create_database.ipynb](ETL_create_database.ipynb). The ETL process is broken down into four jupyter notebook files:

1.	[ETL_function_test.ipynb](ETL_function_test.ipynb)
    - Data is extracted from the website in JSON and CSV formats.
    - Data is transformed into Pandas data frames.
    - JSON file requires extra step – loading file first and then transforming into data frame.

2.	[ETL_clean_wiki_movies.ipynb](ETL_clean_wiki_movies.ipynb)
    - Function *clean_movie* combines scattered data of alternative languages into one column *alt_titles*. 
    - Its subfunction *change_column_name* organizes column names into consistent pattern.
    - In the function *extract_transform_load* the transformation process of wiki movies data begins and includes:
 
         - Python **list comprehensions**.
         - apply() and map() methods in combination with **lambda functions**.    
         - regular expressions or **RegEx**.
        
3.	[ETL_clean_kaggle_data.ipynb](ETL_clean_kaggle_data.ipynb)
    - Function *extract_transform_load* gets new tasks for cleaning Kaggle data and includes:
    
        - Changing datatypes, using methods pd.to_numeric, astype() and python comparison operators for Boolean types.
        - Filling missing values and filtering unwanted columns.
        - Merging data frames using *pd_merge* method.
        
4.	[ETL_create_database.ipynb](ETL_create_database.ipynb)
    - Finally, the function in its final step connects to the database by **sqlalchemy** library and **to_sql** method. 
    - Complete ETL process can be executed with a single function *extract_transform_load* call.

## THINGS LEARNED
- Create an ETL pipeline from raw data to a SQL database.
- Extract data from disparate sources using Python.
- Clean and transform data using Pandas.
- Use regular expressions to parse data and to transform text into numbers.
0 Load data with PostgreSQL.

## Five Assumptions Made

It's important to ensure that the following assumptions about the data are true:

1. The function performs all transformation steps, with no errors.
2. Data is sorted uniquely and in the same way in all input datasets. If this is not the case then the merge will be unable to match in some columns.
3. That the data is merged using a unique identifier such as "imdb_id" to avoid having duplicated rows in data.
4. Some columns will have null values as a result of missing data.
5. The function performs all load steps with no errors, while existing data is removed while the load step reloads the data in SQL.

## Resources

Data Sources: 

-	Wikipedia web scrape [JSON file](Resources/wikipedia-movies.json)
-	Kaggle data from [Kaggle.com](https://www.kaggle.com/rounakbanik/the-movies-dataset) - two files: movies_metadata.csv and ratings.csv

Dependencies:
-	Please see Jupyter Notebook [ETL_create_database.ipynb](ETL_create_database.ipynb) for complete list of dependencies


## Software/Tools

PostgreSQL, Pandas, Python, ETL Pipelines, Regular Expressions, Jupyter Notebook


## Other Useful Articles
- [apply & map methods](https://www.geeksforgeeks.org/difference-between-map-applymap-and-apply-methods-in-pandas/)
- [List comprehension](https://www.youtube.com/watch?v=3dt4OGnU5sM&feature=youtu.be)
- [More list comprehension](https://realpython.com/list-comprehension-python/)
- [Lambda functions](https://realpython.com/python-lambda/)
- [RegEx](https://www.programiz.com/python-programming/regex)
