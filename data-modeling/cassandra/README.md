# ApacheCassandra project

## Datasets

one dataset: in folder event_data
CSV files partitioned by date
examples:
event_data/2018-11-08-events.csv
event_data/2018-11-09-events.csv

columns : artist	firstName	gender	itemInSession	lastName	length	level	location	sessionId	song	userId


## Project Template

create event_datafile_new.csv dataset to create a denormalized dataset in a jupyter file 
model data tables
provide qeries to model ata tables
load the data into tables and run queries

code written in Python in a jupyter file


## Create tables

Design tables to answer the queries outlined in the project template :


### 1. Give me the artist, song title and song's length in the music app history that was heard during  sessionId = 338, and itemInSession  = 4

Table session_music
        sessionId int,
        itemInSession int, 
        artist text, 
        song text, 
        length decimal, 
        PRIMARY KEY (sessionId,itemInSession )
        
### 2. Give me only the following: name of artist, song (sorted by itemInSession) and user (first and last name) for userid = 10, sessionid = 182

Table user_music 
         userid int,
         sessionid int,
         iteminsession int, 
         artist text, 
         song text, 
         firstname text, 
         lastname text,
         PRIMARY KEY ((userid,sessionid),iteminsession )
         
### 3. Give me every user name (first and last) in my music app history who listened to the song 'All Hands Against His Own'

Table music_history 
        song text, 
        userid int, 
        firstname text, 
        lastname text, 
        PRIMARY KEY (song,userid)
  
## Build ETL Pipeline

    * import libraries
    * create csv file
    * create cluster
    * create keyspace
    * queries to create tables
    * queries to insert into tables
    * queries to check tables
    * drop tables

 


