# Recommendation System For Top 5 Movies

## Group-4 - Phase-4 Project


### Authors:
1. Hellen Mwaniki
2. Jesicah Mutiso
3. Endalkachew Dessalegne
4. Brian Waweru
______________________________________

## 1. Project Overview

A new movie streaming startup, aims to offer a highly personalized viewing experience to differentiate itself in a crowded market. One of its core features is a movie recommendation system that helps users discover films they are likely to enjoy, based on their past preferences. To achieve this, the system uses both collaborative filtering and content-based filtering techniques to recommend the top 5 movies tailored to each user's preferences, whether they’re long-time users or just getting started.

## Business Understanding 
### Business Problem 

In a highly competitive streaming market, retaining users is vital. The ability to accurately suggest content plays a huge role in user engagement. The company wants to implement a recommendation system that can:

- Recommend Top 5 movies to returning users who have rated other movies.

- Recommend Top 5 movies to new users with no past activity.

These two problems reflect common industry challenges:

- Personalization for known users

- Cold Start handling for new users

### Objectives

- Boost engagement by offering tailored movie suggestions.

- Increase user retention through consistent, relevant recommendations.

- Solve the "cold start" problem for new users with no ratings.

## 2. Data Understanding 

We retrieved dataset from MovieLense webset which conisists of 4 csv files of which we used 2 for this project. After importing the necessary libaraires we loaded the dataset `movie.csv` and `rating.csv` in to two Dataframs using `pd.read_csv`. 
1. df_movies - consists of information on movieId, title and genre.
2. df_ratings - consists of information on userId, movieId, rating and timestamp.
This two dataframes share a common column, 'movieId' and hence they are merged as one `df` based on this common factor.

After loading the two dataframes, we checked the number of columns and rows in each dataframe, the datatypes of each column, missing values and checked the descriptive summary of the data. We noted that there are no null values in the dataset.


## 3. Exploratory Data Analysis 

The Number of movies, ratings and users in the datasets, average number of ratings per user and average number of ratings per movie were computed. 
The merged dataset has 100836 ratings, 9724 movies and 610 users. The average number of ratings per user is 165.3 and average number of ratings per movie is 10.37. The most frequent rating is found to be 4. 
Then the most frequently rated movies and the genre distribution of the movies was checked. 

## 4.  Modeling 
## Model for Collaborative Filtering 

* Collaborative filtering(CF) model is used to recommend movie for a user based on user ratings of other movies and other similar uers' ratings.
* For this modeling SVD from the Suprise library is used.
* We splited the dataset into trainset and testset and trained the SVD model with the trainset data.
* Then we added a function that takes in userId and num_recommendations as parametrs and returns top 5 recommended movies, title and genres, for a user.
* This model works well for users with enough ratings of movies.

## Model for Content-Based Filtering

* Content based filtering model is used to recommend similar movies for a new user based on the genre of a movie watched. This model adresses **cold start**, when user has not rated movies yet. It uses TF-IDF to convert the genres into TF-IDF features. It uses cosine similarity to find out the similarity of movies based on their genres TF-IDF vectors.
* We added a function that takes in a movie title and num_recommendations as parametrs and returns top 5 recommended movies, title and genres, for a user.
* This model works well for new users. 

## Hybrid CF-CBF Recommendation Model 

* This recommender system combines CF and CBf models. It normalizes CF and CBF scores for a common scale, blend the two models using a weighting factor alpha(e.g., 0.5) and sort and return top 5 movie recommendations. 
* We added a function which takes in both userId and movie title as an input and return top 5 recommended movies, title and genres, for a user.

## 5. Evaluation 
### 5.1. Evaluation of CF Model on testset

* **Performance metric** Root Mean Square Error **(RMSE)** is used to evaluate the accuracy of the model.
It evaluates the model's predicted ratings versus the actual ratings in the testset. 
A value of about 0.88 of RMSE found shows that the model deviated by about 0.87 ratings from the actual ratings on a 0.5 - 5.0 ratings.
It is below 1.0 and can be considered good model performance

## 6. Conclusions 
* We implemented Collaborative Filtering(CF) using SVD from the Suprise library. It performs better for active users.
* Evaluation matrix RMSE = 0.88 for Collaborative Filtering is achieved. This is acceptable for rating prediction.
* Collaborative Filtering is ideal for personalized recommendations once the user has rated many items/movies.
* We used TF-IDf vectorization of genre for Content-Based Filtering(CBF) to recommend top N unseen movies for all users, addresses cold-start users.
* Hybrid model improves recommendation by combining the two models

## 7. Recommendations 
* Hyperparameter tuning for CF to improve RMSE 
* To include more features such as movie description for TF-IDf to improve the model.
* Optimize the SVD model by using different similarity measures
* Optimaize alpha to balace the right weight of CF and CBF.
* To include evaluation of overall model performance for CBF and hybrid models which was not included in this project due to time constraint.  





## Repository Structure

```
├── README.md                                <- The top-level README for reviewers of this project
├── recommender.ipynb    <- Narrative documentation of analysis in Jupyter notebook
├── Presentation.pdf                         <- PDF version of project presentation

```

