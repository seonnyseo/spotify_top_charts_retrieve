
#README

# Scrapping Spotify Top 50 Charts

### Introduction
---
Spotify is a digital music service that gives users access to millions of songs and has a huge client base all around the world. Driven by the interest in music and the data, we choose to explore more from the data of Spotify. Our goal is to build a “Top 50” music dataset with different categories of songs, including 62 lists of different countries. The data is created by the information of songs and artists and also based on a daily playlist from Spotify users. We would like our data to show the popularity of certain songs, artists and categories.




### Python Library Dependency
---
Dependency: 
*   spotipy (3rd part Python library to help connect to Spotify Web API)
*   pandas
*   bs4
*   requests


### Usage
---
We have two files of our work, one is the Jupyter notebook version that processes step by step and another one is a python file includes a class that creates daily charts csv file directly.

For using the class, plese check out the code below.
```python
charts = spotify_daily_charts_downloader(username = '', scope = '', client_id = '', client_secret = '')
charts.download_chart()
```

These information is required for Spotify Authorization, for further information please check out the Notice below.

* username
* scope 
* client_ide 
* client_secret 



### Dataset Columns description
---

| columns | definition |
|:---:|:---|
| continent |continent in chart|
| country |country in chart|
| rank |Rank in data charts obtained from website is based on daily play counts in the country, which is not supported in API. We assume the rank as ascending order which is returned by API in its track information.|
| song |The name of the song.|
| artist |The name of the artist.|
| album |The name of the album. In case of an album takedown, the value may be an empty string.|
| release_date |The date the song was first released|
| song_popularity |The popularity of the song. The value will be between 0 and 100, with 100 being the most popular. The song’s popularity is calculated from the popularity of all the song’s tracks.|
| song_id |The Spotify ID for the song, each song has one id|
| artist_id |The Spotify ID for the artist, each artist has one id|
| album_id |The Spotify ID for the album, each album has one id|
| followers |Information about the followers of the artist.|
| date |the date we extract the data |
| acousticness: | A confidence measure from 0.0 to 1.0 of whether the track is acoustic. 1.0 represents high confidence the track is acoustic.   |
| dannceability | Danceability describes how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm stability, beat strength, and overall regularity. A value of 0.0 is least danceable and 1.0 is most danceable.|
| energy |Energy is a measure from 0.0 to 1.0 and represents a perceptual measure of intensity and activity. Typically, energetic tracks feel fast, loud, and noisy. For example, death metal has high energy, while a Bach prelude scores low on the scale. Perceptual features contributing to this attribute include dynamic range, perceived loudness, timbre, onset rate, and general entropy.    |
| instrumentalnness |Predicts whether a track contains no vocals. “Ooh” and “aah” sounds are treated as instrumental in this context. Rap or spoken word tracks are clearly “vocal”. The closer the instrumentalness value is to 1.0, the greater likelihood the track contains no vocal content. Values above 0.5 are intended to represent instrumental tracks, but confidence is higher as the value approaches 1.0.|
| livenness |Detects the presence of an audience in the recording. Higher liveness values represent an increased probability that the track was performed live. A value above 0.8 provides strong likelihood that the track is live. |
| loudness |The overall loudness of a track in decibels (dB). Loudness values are averaged across the entire track and are useful for comparing relative loudness of tracks. Loudness is the quality of a sound that is the primary psychological correlate of physical strength (amplitude). Values typical range between -60 and 0 db. |
| speechiness |	Speechiness detects the presence of spoken words in a track. The more exclusively speech-like the recording (e.g. talk show, audio book, poetry), the closer to 1.0 the attribute value. Values above 0.66 describe tracks that are probably made entirely of spoken words. Values between 0.33 and 0.66 describe tracks that may contain both music and speech, either in sections or layered, including such cases as rap music. Values below 0.33 most likely represent music and other non-speech-like tracks. |
| valence |	A measure from 0.0 to 1.0 describing the musical positiveness conveyed by a track. Tracks with high valence sound more positive (e.g. happy, cheerful, euphoric), while tracks with low valence sound more negative (e.g. sad, depressed, angry).|
| genre |A list of the genres the artist is associated with. For example: "Prog Rock" , "Post-Grunge". (If not yet classified, the array is empty.)|
| artist_popularity |The popularity of the artist. The value will be between 0 and 100, with 100 being the most popular. The artist’s popularity is calculated from the popularity of all the artist’s tracks.|
| album_popularity |The popularity of the album. The value will be between 0 and 100, with 100 being the most popular. The popularity is calculated from the popularity of the album’s individual tracks.|




### Notice
---
1.	Spotify only offers Web API officially. But it documents the list of 3rd. party libraries for integrating with the Spotify Web API using several programming languages and platforms. And we use python to connect Spotify through the library.


2.	You are also required to register a Spotify account to get your credentials and put them as specified in the code. For the Authorization, please check out this page.
https://developer.spotify.com/documentation/general/guides/authorization-guide/


3.	Rank in data charts obtained from website is based on daily play counts in the country, which is not supported in API. We assume the rank as ascending order which is returned by API in its track information.


4.	The category of songs we get from the dataset is determined by the category of its artist. However, many artists release many different styles of songs and no single style label can represent the entire songs. We will analyze each song’ acousticness, danceability, energy, instrumentalness, liveness, loudness, speechiness and tempo to determine its style. 

### Challenge and Further Works
---
1. Since Spotipy does not support to get tracks information by using playlist ids, we implemented a temporary method adding into the library instance. It is recommended to keep tracking the update of the Spotipy and fix in in the furture.

2. Since we worked on the Jupyter notebook first, which explains the process step by step, and transformed it to the Python file later, a class in the py file is not organized. We recommend to work refactoring on the class and divide methods more precisely.
