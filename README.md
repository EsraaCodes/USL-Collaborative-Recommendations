# USL-Collaborative-Recommendations
🎬 Item-Based Collaborative Filtering Movie Recommendation System
📌 Overview

This project implements an Item-Based Collaborative Filtering recommendation system using the MovieLens dataset.
Instead of recommending movies based on similar users, this approach recommends movies based on similar items (movies), which is more stable since movies do not change frequently.

The model predicts the top 10 similar movies based on user rating behavior.

🧠 Why Item-Based Filtering?

Movies change less frequently than users

Model can be retrained periodically (e.g., weekly)

More scalable than user-based filtering

Performs well on sparse rating matrices

📂 Dataset Description
ratings.csv

Contains user ratings for movies:

userId → Unique identifier for users

movieId → Movie identifier

rating → Rating given by a user

timestamp → Time of rating (not used)

movies.csv

Contains movie metadata:

movieId → Movie identifier

title → Movie title

genres → Movie genres (not used in filtering)

⚙️ Data Preprocessing
1️⃣ Pivot Table Creation

Ratings are converted into a movie-user matrix:

Rows → Movies

Columns → Users

Values → Ratings

Missing values are filled with 0 to represent unrated movies.

2️⃣ Handling Sparsity

Real-world recommendation systems are highly sparse.
To reduce noise and improve performance:

Movies with < 10 ratings are removed

Users with < 50 ratings are removed

This filtering ensures better quality recommendations.

🧩 Sparse Matrix Optimization

Since the dataset is still sparse, we use Compressed Sparse Row (CSR) Matrix from scipy:

Saves memory

Improves computation speed

Fully compatible with scikit-learn

Most machine learning models work efficiently with sparse matrices.

🔍 Similarity & Model

Algorithm: K-Nearest Neighbors (KNN)

Metric: Cosine similarity

Why cosine?

Works well with sparse data

Measures similarity in rating patterns

Faster and more reliable than Euclidean distance

NearestNeighbors(metric='cosine', algorithm='brute')

🎯 Recommendation Function

The system:

Takes a movie name as input

Finds its nearest neighbors using cosine similarity

Returns the top 10 most similar movies

Example:
get_movie_recommendation("Iron Man")


📽️ Output:

Up (2009)

Guardians of the Galaxy (2014)

Avengers (2012)

Batman Begins (2005)

Avatar (2009)

📊 Results

The model successfully recommends movies based on:

User rating behavior

Item similarity

Historical interaction patterns

This confirms the effectiveness of Item-Based Collaborative Filtering.

➕ Extension: K-Means Clustering

To further enhance analysis, K-Means clustering is added to:

Group movies based on rating patterns

Identify clusters of similar movies

Support exploratory analysis and visualization

This combination improves understanding of movie similarity beyond pairwise comparisons.

🛠️ Technologies Used

Python

Pandas & NumPy

Scikit-learn

SciPy (CSR Matrix)

Matplotlib & Seaborn

🚀 Conclusion

This project demonstrates a scalable and efficient item-based recommendation system using collaborative filtering.
By handling sparsity, using cosine similarity, and optimizing with sparse matrices, the system provides accurate movie recommendations.

📌 How to Run
pip install -r requirements.txt


Run the notebook or script and call:

get_movie_recommendation("Movie Name")