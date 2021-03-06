# Introduction

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

They'd like a data engineer to create a Postgres database with tables designed to optimize queries on song play analysis, and bring me on the project. My role is to create a database schema and ETL pipeline for this analysis. I will also test my database and ETL pipeline by running queries given to me by the analytics team from Sparkify and compare my results with their expected results.


## Project Description

In this project, I will model the needed tables with Postgres and build an ETL pipeline using Python. To complete the project, I will need to define fact and dimension tables for a star schema for a particular analytic focus, and write an ETL pipeline that transfers data from files in two local directories into these tables in Postgres using Python and SQL.


## Data to be used

### Song Dataset

The first dataset is a subset of real data from the Million Song Dataset. Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID.

### Log Dataset

The second dataset consists of log files in JSON format generated by this event simulator based on the songs in the dataset above. These simulate activity logs from a music streaming app based on specified configurations. The log files in the dataset are partitioned by year and month. 

## Results

The following files are included in the solution
- test.ipynb displays the first few rows of each table to check the database.
- create_tables.py drops and creates all tables. This file is run to reset all tables before each time running the ETL scripts.
- etl.ipynb reads and processes a single file from song_data and log_data and loads the data into the tables. This notebook contains detailed instructions on the ETL process for each of the tables.
- etl.py reads and processes files from song_data and log_data and loads them into the tables.
- sql_queries.py contains all sql queries, and is imported into the last three files above.


## Project Steps

Below are steps I did to complete the project:

#### Create Tables

Create and drop statements for each tables I included in sql_queries.py. 
Then I run create_tables.py to create database and tables.
To confirm the creation of correct tables and columns I run test.ipynb. 

#### Build ETL Processes

I followed the instructions in the etl.ipynb notebook to develop ETL processes for each table. At the end of each table section I run the according statements in test.ipynb to confirm that records were successfully inserted into each table. So now we have the following fact and dimension tables:

##### Fact Table

songplays: records in log data associated with song plays

##### Dimension Tables

- users: information on users, e.g. name
- songs: songs in the database, e.g. title or length
- artists: artists in the database, e.g. name
- time: timestamps of records in songplays 


#### Build ETL Pipeline

Finally I completed etl.py to be able to process the entire datasets. To start with empty tables I again run create_tables.py before running etl.py to reset everything. The etl.py now loops through all files and populates the tables completely. 
At the end I run test.ipynb to confirm all records were successfully inserted into each table.


#### Conclusion

Now Sparkify is able to analyze the usage of their songs. They can create several statistics on favorite songs or artists and can get information on when users are mostly using the app.








