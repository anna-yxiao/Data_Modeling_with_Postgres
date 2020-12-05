### Description
A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. This project is to create a database schema and ETL pipeline for song play analysis. We define fact and dimension tables for a star schema for the particular analytic focus, and write an ETL pipeline that transfers data from files in two local directories into these tables in Postgres using Python and SQL.


### Database Schema Design and Table Creation
The star schema has one fact table (songplays) and four dimension tables (users, songs, artists, and time).

![ER Diagram](ER_Diagram.jpg)

The script, `create_tables.py`, connects to the Sparkify database, drops any tables if they exist, and creates the tables.

The `DROP` and `CREATE` statements in `sql_queries.py` specify all columns for each of the five tables and the process of table creation.

### ETL Pipeline
The script, `etl.py`, connects to the Sparkify database, extracts and processes the `log_data` and `song_data`, and loads data into the five tables.

### Example Queries
1. Which user listens to the most songs?
```
SELECT user_id, COUNT(songplay_id) 
FROM songplays 
GROUP BY user_id 
ORDER BY count(songplay_id) DESC 
LIMIT 1;
```

2. How many paid users do we have in the `users` table?
```
SELECT COUNT(user_id) 
FROM users 
WHERE level = 'paid';
```
