# Game Recommendation System with Sentimental Analyzer

The recommendation system is based on users' ratings, the sentimental analyzer for user's reviews to impute the ratings.


## Intuition

User reviews could reflect how user will rate the game more accuratly. And there are many reviews without ratings. <br>
If we could use the review to predict the users' ratings, it will improve the Collaborative Filtering recommendation system. 

Upon some EDA, the reviews could form topic clusters, which means it's very possible that using review to predict could make a difference.


## DATASET

Currently I'm using user reviews from Metacritic and Steam. I got the dataset from Kaggle, links are as below.

| Metacritic | Steam |
|:---:|:---:|
|280k|17k|
|[Metacritic Video Game Comments](https://www.kaggle.com/datasets/dahlia25/metacritic-video-game-comments)|[Steam Game Review Dataset](https://www.kaggle.com/datasets/arashnic/game-review-dataset)|



I've working on adding the following dataset:

[RAWG](https://www.kaggle.com/datasets/jummyegg/rawg-game-dataset):

This dataset contains 474417 video games on over 50 platforms including mobiles. All game information was obtained using Python with RAWG API. This dataset was last updated on Dec 22nd 2020.

[Steam Store Games](https://www.kaggle.com/datasets/nikdavis/steam-store-games?select=steam.csv): 

Combined data of 27,000 games scraped from Steam and SteamSpy APIs<br>




## DATA PREPERATION

### Data Wrangling

I did basic cleaning and check, to select the features for the next step.

### EDA

Explored on metacritic and steam datasets, plus processed and cleaned text.

It's always difficult to deside how to impute the missing data, so I thought of using the comments to predict might be a good way. <br>
I did topic modeling, and found out it could form clusters on different platform (Metacritic and Steam). Thus it show that involving sentimental analyzer for imputing user score for the game shoudl work.
The clusters are as below:<br>

<img src="https://user-images.githubusercontent.com/73181107/208791404-4e67d3e8-27cc-4541-90d8-d480a1796663.png" width="500">

## MODLING

### Sentimental Analyzer

#### Baseline
|MODELS|MSE|MAE|TRAINING TIME|
|---|---|---|---|
|random forest|4.52|1.52|24m|
|xgboost|4.57|1.59|14.6s|
|Tensorflow|4.35|1.49|26.1s|


The models using GPU is much faster, so for the fine tuning, I didn't involve random forest.

#### Final model

The best performance I got so far, is the model trained with: <br>
Tensorflow, 235301 comments, a vocabulary size set as 200.

For some technical issue, my GPU can't work with a vocabulary size over 200 with tensorflow, but it still works better than XGBoost.
|Model|Vocabulary Size|MSE|MAE|R2|Traning Time|
|---|---|---|---|---|---|
|Tensorflow|200|4.07|1.45|0.32|25.5s|
|XGBoost|5000|3.93|1.46|0.34|113.8s|



### Recommendeation System
The table below is the score of RMSE

|Model|No Impute|XGB Impute|TensorFlow Impute|
|---|---|---|---|
|SVD|3.98|3.896|3.898|
|KNN|4.03|3.937|3.940|


It shows that using the sentimental analyzer improved the score, even just a tiny bit.

## FUTURE APPROACH
- Improve sentimental analyzer models
- Improve recommendation system models
- Collect more data and use the current data by scraping
- Merge to a RNN neural network
- Try Google's new recommendation system



## Environment

 - tensorflow: need to build tf environment
 
    [Installation Guide](https://www.tensorflow.org/install)
 
 - XGBoost: requires certain version of Python. i.e. Python 3.6
 
    [Installation Guide](https://xgboost.readthedocs.io/en/stable/install.html)
    
    
    
## CONTACT INFORMATION
With questions or feedback on this repository, please reach out via:

[GitHub](https://github.com/vivyhasadream)

[LinkedIn](https://www.linkedin.com/in/viviannayan/) 
 
## SPECIAL THANKS
The awsome intructor **Praveen Gowtham**

 
 

