# Game Recommendation System with Sentimental Analyzer

The recommendation system is based on users' ratings, the sentimental analyzer for user's reviews to impute the ratings.


## Intuition
User reviews could reflect how user will rate the game more accuratly. And there are many reviews without ratings. <br>
If we could use the review to predict the users' ratings, it will improve the Collaborative Filtering recommendation system. 

Upon some EDA, the reviews could form topic clusters, which means it's very possible that using review to predict could make a difference.

## Models used
- Sentimental Analyzer

  Random forest, tensorflow, XGBregressor

- Recommendeation System

  Surprise SVD, KNN

## datasets

should be saved in a folder named raw_data

[Metacritic Video Game Comments](https://www.kaggle.com/datasets/dahlia25/metacritic-video-game-comments)

[Steam Game Review Dataset](https://www.kaggle.com/datasets/arashnic/game-review-dataset)

[RAWG](https://www.kaggle.com/datasets/jummyegg/rawg-game-dataset): This dataset contains 474417 video games on over 50 platforms including mobiles. All game information was obtained using Python with RAWG API. This dataset was last updated on Dec 22nd 2020.

[Steam Store Games](https://www.kaggle.com/datasets/nikdavis/steam-store-games?select=steam.csv): Combined data of 27,000 games scraped from Steam and SteamSpy APIs<br>


## file structures

there are 4 categories of the Notebooks, states 4 stages of this projects.

1.* data wrangling files of the above datasets

2.* EDA metacritic and steam datasets, plus process and clean text in this stage

3.* Modelling for Sentimental Analyzer: tested with three models, each work on different environment

4.* Recommendation System: baseline, imputed with tensorflow and XBGoost (at different environment)

## Results

The models are trained using GPU when possible.


## Environment

 - tensorflow: need to build tf environment
 
    [Installation Guide](https://www.tensorflow.org/install)
 
 - XGBoost: requires certain version of Python. i.e. Python 3.6
 
    [Installation Guide](https://xgboost.readthedocs.io/en/stable/install.html)
 
## Special Thanks
The awsome intructor **Praveen Gowtham**

 
 

