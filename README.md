# Analysis of Seattle airbnb Data


## Installations

To run the project you should ue jupyter notebooks. A number of Python libraries are required, including Numpy, Padas, Matplotlib, Seaborn and various models and functions from sklearn.


## Project Motivation

I carried out this project for an assignment in the Udacity Nanodegree program.
The objective was to pick a data set and analyse it to answer three defined business questions.
I decided to use the suggested airbnb dataset containing listings for Seattle (in 2016).

The three business questions I aim to answer are:

Concerning airbnb rental listings in Seattle (as of April 2016)

1. How does the neighbourhood of the property affect the price?
2. How does the property type affect the price?
3. How effectively can I predict the price of a listing using a machine learning model?


## File Descriptions

* Seattle_airbnb.ipynb : Jupyter notebook containing my analysis
* calendar.csv : availability of each listing per day
* listings.csv: full descriptions of properties listed for rental on airbnb
* reviews.csv: reviews for each listing

The three csv data files were sourced from Kaggle https://www.kaggle.com/airbnb/seattle/data.
More detail can be sourced there.



## Interacting With The Project

The Notebook is self-contained, provided you have Python and Jupyter notebooks you should be able to load the ipynb file and run all cells.  The data files need to be saved in a "Seattle" sub-folder for the import commands to work. 

## The Process

### Business Understanding

The analysis aims to explore the Seattle airbnb data to try and gain insights into what affects the price of a listing.  Three specicic questions the analysis aims to address are:

Concerning airbnb rental listings in Seattle (as of April 2016)

1. How does the neighbourhood of the property affect the price?
2. How does the property type affect the price?
3. How effectively can I predict the price of a listing using a machine learning model?


### Data Understanding

The are three data files, calendar, reviews and listings.  Although I inspect them all, ultimately my analysis uses the listings data.
The listings data contains 3,818 rows; each representings a property listed for rental in Seattle (as of 1st April 2016).  There are 92 seperate columns, including the price.  

Some of the columns are not in an ideal format for analysis or machine learnings, so I undetake a number of data cleaning and processing steps.

### Data Preparation

In the notebook, jump to the "Explore Listings Data" heading.  Here I undertake the following checks:

#### Explore Listings Data

1. Check Data Types
2. Check for missing values
3. Identify complete columns

#### Explore Price

1. Clean price column - remove $ signs and converter to numeric
2. Remove single price null row
3. Inspect price distribution using histogram
4. Drop numeric columns which will not be useful features (as as id)
5. Plot correlation matrix
6. Plot boxplot of price by property type
7. Plot boxplot of price by superhost status

#### Cleaning Data for Model

Host Verifications
* Process host verification column to have a seperate binary column for each verification type

Amenities
* Process amenities column to have a seperate binary column for each amenity_type

Categorical Variables
* Convert categorical variables cancellation_policy, property_type, room_type, host_is_superhost into dummy columns

Numeric Features
* Select existing numeric features for use in model.  Drop square_feet as it has too many null values.

### Modelling

1. Flag price column as the target variable
2. Split into training set (70%) and test set (30%)
3. Train multiple models and evaluate with Mean absolute erro, root mean squared error and R Squared
      * LinearRegression
      * KNeighboursRegressor
      * SGDRegressor
      * Lasso
      * ElasticNet
      * Ridge
      * SVR-linear
      * SVR-rbf

4. Run cross folds validation on each model, computing the R squared
5. Select top 3 models (Ridge, Lasso and ElasticNet) and fine tune hyperparameters using GridSearch


### Evaluation
1. Identfy best performing model and hyperparameters, - Lasso with alpha = 1.0
2. Check Mean Absolute Error, Root Mean Squared Error and R Squared of best model
3. Examine coefficients to see which features are most helpful for the model prediction
4. Plot coefficients on histogram
5. Plot model errors on histogram
6. Plot mean absolute errors on histogram


### Deployment

Model does not need to be deployed, but could be used by stakeholders or potential customers in the Seattle airbnb market.

## Acknowledgements

Author: Neale Denton
Data: sourced from Kaggle.com

This code is free to use, modify and share with or without attribution, but attribution appreciated!
