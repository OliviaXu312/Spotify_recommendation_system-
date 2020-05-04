# Spotify_recommendation_system-


# Spotify Recommendation System

ANLY 502 - Final Project
Group Mountain Dew


Group Numbers:
Yanou Yang
Xinya Xu
Wenhao Jiang
Leilin Wang

# Executive Summary

The recommendation system is widely used in online media service providers. Especially for Spotify, better the recommended songs, more likely the user will keep using Spotify. Since users cannot search for all songs manually, if Spotify can provide the recommendations of the songs that users would highly like, then there are higher chances of Spotify staying relevant and becoming successful. So our goal is to develop a recommender system for Spotify playlist. Given a set of user’s behavior features, a recommendation system should be able to generate a list of recommended tracks that meets a certain user’s preference. 

Spotify has released a dataset called “Million Playlist Dataset” which would be used as a dataset to train our model. The main problem here is to identify the various ways to recommend the next song to the user or the playlist. There are two main methods in collaborative filtering. The first one is user rating various songs and then the recommended songs were provided to them resulting in highly favorable outputs from the model. But since, we cannot always ask a user to rate the songs but rather songs are liked or disliked in Spotify. Therefore, the second method to model the system was based on this idea. We got implicit feedback like views, clicks, likes, or shares in our dataset, so we transformed it into numbers to represent the strength in observations of user actions’ preference. The generated results were in accordance with the user’s choices as well as on the statistical viewpoints. More information about the project and the methods used are detailed in the given report.

# Introduction

Music recommender systems have recently exploded in popularity thanks to music streaming services like Spotify and Apple Music. By some accounts, almost half of all current music consumption is by the way of these services. While recommender systems have been around for quite some time and are very well researched, music recommender systems differ from their more common siblings in some important ways: the duration of the items is less (3-5 min for a song vs 90 minutes for a movie ), the items are consumed in sequence with multiple items consumed in a session, repeated recommendations have a different significance. Music Recommender Systems then require different approaches from traditional recommender systems. 

This project’s goal is to develop a recommender system for a playlist, which would enable Spotify to seamlessly support their users in creating and expanding the playlists by making recommendations based on their choices and preferences. Furthermore, the recommender system does not require any rich and varied supply of music data, instead requiring only basic information as input such as the title of the playlist, the tracks currently in the playlist, and the user behavior with those tracks.

First, we need to decide on the plan to approach this dataset to train our model. There are two basic methods of music recommendation-metadata information retrieval and collaborative filtering. 

Metadata information retrieval uses editorial information supplied by the creators, such as the title of the song, artist name, and lyrics to find some target songs. Though it is fast and accurate, the drawbacks are obvious. First of all, the user has to know about the editorial information for a particular music item. Secondly, it is also time-consuming to maintain increasing metadata. Moreover, the recommendation results are relatively poor, since it can only recommend music based on editorial metadata and none of the users’ information has been considered.

Collaborative filtering is able to recommend items via the choice of other similar users. As one of the most successful approaches in recommendation systems, it assumes that if user X and Y rate n items similarly or have similar behavior, they will rate or act on other items similarly. Instead of calculating the similarity between items, a set of ‘nearest neighbor’ users for each user whose past ratings have the strongest correlation are found. Therefore, scores for the unseen items are predicted based on a combination of the scores known from the nearest neighbors.

For this project, We will use neural collaborative filtering to build the playlist recommendation system. We also plan to do some exploratory analyses, like looking at numbers of unique tracks and users’ behavior distribution that helps further understanding in methodology. We may also do some playlist clustering and PCA, to find interesting patterns in these user-generated playlists. 

# Data Exploration

Before we build the machine learning model for this project, first we need to know what our data looks like, to understand what people like before we recommend anything to them. 

The dataset we use consists of two parts. The first part is as what we introduced before, containing all the user action upon a single track for a session, including information of skipping, seeking back, etc. The other part of the data contains specific features of these tracks. The columns include the same ‘track_id’, loudness, danceability, tempo, time signature, etc. All these variables are vectorized to numbers beforehand. The rows do not contain any missing value or NA. So the dataset is very clean, and ready to use. The pictures below show a short glance of the two parts of data. 


# Methdology

Recommendation systems predict what users would like in the future based on their behavior patterns. The most basic models for recommendation systems are collaborative filtering models.  

Collaborative filtering models which are based on the assumption that people tend to like things similar to the historical things they like, and things liked by other people who have the same favour with them. 

In this project, we used matrix factorization-based collaborative filtering, that treats the entries in the user-item matrix as explicit preferences given by the user to the item, for example, users giving rating to movies. So to the spotify dataset, firstly, an explicit rating to each movie should be defined. The rating formula is defined as follows.

