# The Blockbuster Goes Abroad

## Objective:

Build a regression model to predict foreign lifetime gross for top domestic movies (6 figure+ opening weekend) from 2000 - 2019. 

## Data Sources:

- [Box Office Mojo's](https://www.boxofficemojo.com/) top lifetime grossing films and movie profiles using BeautifulSoup
- [The Numbers'](https://www.the-numbers.com/) adaptation and sequel movie lists.
- Kaggle datasets ([1](https://www.kaggle.com/satkarjain/imdb-movie-19722019) and [2](https://www.kaggle.com/stefanoleone992/imdb-extensive-dataset)) of IMDB movie ratings.

## Approach: 

Features inputs model included domestic opening weekend gross; year released; foreign market count; distribution company; genres; MPAA rating; whether the film was an adaptation indicator, a sequel; and IMDB audience rating. Additionally, feature engineering was utilized to add dummy variables for categorical features (genres, distribution company, MPAA rating, adaptation indicator, sequel indicator), standardize time features (year released was engineered into years since release), and multiplicative terms were added for feature interactions. The training data was evaluated via train-val-test on linear regression, degree 2 polynomial transformation regression, and LASSO regression models (with standard scaled features and 5 K-fold cross validation), in order to optimize for R2 and MAE.

## Results:

A simple linear regression model with multiple multiplicative interaction terms was selected. Features included in the final model are domestic opening weekend gross (along with its interactions with foreign market count, Disney as distribution company, adventure genre, comedy genre, and sequel indicator), years since release (along with its interaction with comedy genre), sequel indicator's interactions with adventure and action genres, Disney as distribution company's interactions with foreign market count and adaptation indicator, and action genre's interaction with PG-12 MPAA rating.

The features were used to predict movie foreign lifetime gross (defined by markets outside of the U.S., Canada, and Puerto Rico) in USD. The model was optimized for R2 and mean absolute error. The final model's test data outputted an R2 of 0.58 and MSE of 88.32 million USD. For comparison, the average predicted foreign lifetime gross was 227.20 million USD.

