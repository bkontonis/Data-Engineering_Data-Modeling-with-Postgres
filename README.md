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
 1. <mark>songplays</mark> - records in log data associated with song plays i.e. records with page NextSong
    - songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent
    
**Dimension Tables**

 2. <code> users </code> - users in the app
    - user_id, first_name, last_name, gender, level
 3. <mark>songs</mark> - songs in music database
    - song_id, title, artist_id, year, duration
 4. <mark>artists</mark> - artists in music database
    - artist_id, name, location, latitude, longitude
 5. <mark>time</mark> - timestamps of records in songplays broken down into specific units
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

 - <mark>os</mark>
 - <mark>glob</mark>
 - <mark>psycopg2</mark>
 - <mark>pandas</mark>
 - <mark>import datetime</mark>

---

## Usage



---

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
