# Project: Data Modeling with Postgres

---

## Introduction

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

They'd like a data engineer to create a Postgres database with tables designed to optimize queries on song play analysis, and bring you on the project. My role is to create a database schema and ETL pipeline for this analysis.

---

## Project Description

In this project, I apply what I've learned on data modeling with Postgres and build an ETL pipeline using Python. To complete the project, I had to define fact and dimension tables for a star schema for a particular analytic focus, and write an ETL pipeline that transfers data from files in two local directories into these tables in Postgres using Python and SQL.

Using the song and log datasets, I need to create a star schema optimized for queries on song play analysis. This includes the following tables.

**Fact Table**
 1. <code> <b>songplays</b> </code>- records in log data associated with song plays i.e. records with page NextSong
    - songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent
    
**Dimension Tables**

 2. <code> <b>users</b> </code> - users in the app
    - user_id, first_name, last_name, gender, level
 3. <code> <b>songs</b> </code> - songs in music database
    - song_id, title, artist_id, year, duration
 4. <code> <b>artists</b> </code> - artists in music database
    - artist_id, name, location, latitude, longitude
 5. <code> <b>time</b> </code> - timestamps of records in songplays broken down into specific units
    - start_time, hour, day, week, month, year, weekday

This database will help the internal departments of the Sparkify company to do different kinds of analysis to recommend a Sparkify user.

 - Favorite songs of user based on the week day: By joining songplay and songs and user table based on level.
 - Recent listened to songs: By joining songplays and user table can show recommendation on the app based on subscription level.
 - Can help in recommending most popular songs of the day/week.

---

## ETL

 1. Created songs, artist dimension tables from extracting songs_data by selected columns.
 2. Created users, time dimension tables from extracting log_data by selected columns.
 3. Created songplays fact table from the dimensison tables and log_data.

---

## Install

This project was completed using **Python 3** and the following Python libraries were installed:

 - <code> <b>os</b> </code>
 - <code> <b>glob</b> </code>
 - <code> <b>psycopg2</b> </code>
 - <code> <b>pandas</b> </code>
 - <code> <b>datetime</b> </code>

---

## Files

1. <code> <b>sql_queries.py</b> </code>: Contains all the SQL queries of the project and this file can be used in multiple files.

2. <code> <b>create_tables.py</b> </code>: Run this file after writing for creating tables for the project.

3. <code> <b>etl.ipynb</b> </code>: This notebook contains detailed instructions on the ETL process for each of the tables. It was created as a support file in order to create the etl.py file.

4. <code> <b>etl.py</b> </code>: Read and process files from song_data and log_data and load them to tables.

    - <b>Functions in etl.py:</b>
        - <code> <b>process_song_file</b> </code>: Reads the json file, extracts details and inserts into song and artist tables.
        - <code> <b>process_log_file</b> </code>: Reads the json file, extracts details and inserts into DIM tables time and users and also the FACT table songplays.
        - <code> <b>process_data</b> </code>: Finds all the json files in a directory and procees the data using the above two functions. It also shows the status of files processed.
        - <code> <b>main</b> </code>: Connects to sparkifydb and instantiate a cursor. Then uses all the above functions in order to process all the data files in 'data/song_data' and 'data/log_data' and insert the data in the database.

5. <code> <b>test.ipynb</b> </code>: Displays the first few rows of each table to let you check your database.

---

## Execute

1. **create_tables.py**
    - <code> $python3 create_tables.py </code>
2. **etl.py**
    - <code> $python3 etl.py </code>
3. After running the above scripts from the command line you may open the **etl.ipynb** and check if everything went as expected by quering the first lines from each table.


## Authors

Vasilis Kontonis
 - [LinkedIn](https://www.linkedin.com/in/vasilis-kontonis-baa281b4/)
 - [GitHub](https://github.com/bkontonis)

---

## License
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## Acknowledgements
* This project is part of [Data Engineer Nanodegree Program](https://www.udacity.com/course/data-engineer-nanodegree--nd027).
* [Million Song Dataset](http://millionsongdataset.com/) for the **Song Dataset** and [event simulator](https://github.com/Interana/eventsim) for the **Log Dataset**.
