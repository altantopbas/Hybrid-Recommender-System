
# Hybrid Recommender System

## 🎯 Business Problem

Generate 10 movie recommendations for the user with the given ID using both item-based and user-based recommender methods.

## 📊 Dataset Story
The dataset, was provided by MovieLens, a movie recommendation service. It contains the movies along with the rating scores given to these movies. The dataset includes 20,000,263 ratings across 27,278 movies. It was created on October 17, 2016, and covers data from 138,493 users between January 9, 1995, and March 31, 2015. Users were selected randomly, and all selected users have rated at least 20 movies.

movie.csv:

- 3 Variables, 27278 Observations, 1.5 MB
- movieId: Unique movie number.
- title: Movie name
- genres: Movie genres

rating.csv:

- 4 Variables, 20000263 Observations, 690.4 MB
- userid: Unique User ID. (UniqueID)
- movieId: Unique Movie Number. (UniqueID)
- rating: Rating given to the movie a by user
- timestamp: Evaluation Date

# - Project Tasks
## 👩👨 User Based Recommendation¶
### Task 1: Data Preparation
    1. Read the movie, rating datasets

    2. Add the movie names and genres of the IDs from the movie data set to the rating data set.

    3. Keep the names of the movies with less than 1000 total votes in the list and remove them from the data set.

    4. Create a pivot table for the dataframe with userIDs in the index, movie names in the columns, and ratings as values.

    5. Functionalize all operations performed.

### Task 2: Determining the movies the user has watched to make suggestions
    1. Choose the random user id.

    2. Create a new dataframe named random_user_df consisting of observation units belonging to the selected user.

    3. Assign the movies voted by the selected users to a list named movies_watched

### Task 3: Accessing Data and IDs of Other Users Watching the Same Movies
    1. Select the columns corresponding to the movies watched by the selected user from user_movie_df, and create a new DataFrame named movies_watched_df.

    2. Create a new DataFrame named user_movie_count, which contains information on how many of the selected user's watched movies each user has also watched.

    3. Create a list named users_same_movies containing the user IDs of those who have watched at least 60% of the movies rated by the selected user.

### Task 4: Determining the Most Similar Users to the User to be Recommended
    1. Filter the movies_watched_df DataFrame to include only the users in the users_same_movies list, who are similar to the selected user.

    2. Create a new DataFrame called corr_df, which contains the correlation values between users.

    3. Filter the users who have a high correlation (greater than 0.65) with the selected user and create a new DataFrame named top_users.

    4. Merge the top_users DataFrame with the ratings dataset.

### Task 5: Calculating Weighted Average Recommendation Score and Keeping Top 5 Movies
    1. Create a new variable named weighted_rating, which is the product of each user's correlation and their rating.

    2. Create a new DataFrame named recommendation_df that contains the movie IDs and the average weighted_rating for each movie across all users.

    3. In recommendation_df, select the movies with a weighted_rating greater than 3.5 and sort them by weighted_rating.

    4. Retrieve the movie titles from the movies dataset and select the top 5 movies to recommend.

## 🛅 Item Based Recommendation
### Task 1: Provide item-based recommendations based on the most recently and highest-rated movie watched by the user.
    1. Load the movie and rating datasets.

    2. From the movies rated 5 by the selected user, retrieve the ID of the most recently rated one.

    3. Filter the user_movie_df DataFrame (created in the user-based recommendation section) using the selected movie ID.

    4. Using the filtered DataFrame, compute the correlation between the selected movie and other movies, then sort the results.

    5. Exclude the selected movie itself and provide the top 5 movies as recommendations.
