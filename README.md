
## House Price Prediction 

Use Machine Learning to create a model that predicts the price of a house.


  
## Acknowledgements

 - [Kaggle Dataset](https://www.kaggle.com/amitabhajoy/bengaluru-house-price-data)
 - [codebasics Youtube Channel](https://www.youtube.com/playlist?list=PLeo1K3hjS3uu7clOTtwsp94PcHbzqpAdg)

  

## Author

- [@PiyalBanik](https://twitter.com/PiyalBanik)

  
## Business Understanding
Buying a home in a city like Bengaluru is a tricky choice. While the major factors are usually the same for all metro cities, there are others to be considered for Bengaluru. What are the factors that decide the price of a house in Bengaluru? 

## Analytical Approach: 

Our target variable is Quantitative [take on continuous number], and hence we need regression models for this task.

## Data Requirements & Data Collection:

I needed a dataset that would have various characteristics of the house in Bengaluru and the associated price. 

The dataset is taken from kaggle

## Data Understanding

This step is part of Exploratory Data Analysis

The shape of the datasets (13320, 9). In total there are 9 features with price being the target variable

Missing values
- Location 
- Size
- Society
- Bath
- Balcony 

But, the number of missing values for location, size, bath, and balcony is not much. Society has maximum missing values and we need to decide whether to drop the feature or impute it. 


Few observations
- There are four different types of areas with 'Super built-up Area' having the maximum count. And there are no missing values. We can convert this feature into dummy variables.
- There are 4 different values for balconies, 2 and 1 being the most common ones. There are many houses that do not have a balcony and there are 609 missing values. Missing values are very less than the total number of observations, hence, we can drop those observations.
- Out target variable price is right-skewed with the maximum values being less than 500
- for me 'availability' feature won't be useful in deciding the price of a house. 
- 'total_sqrt' variable requires a lot of cleaning
- there are 2688 different 'society' values with 1524 having a single observation [drop]
- 'bath' contains outliers
  
## Data Cleaning

- Dropped availability and society 
- Dropped obervations having null values (610 in total)
- 'Size' variable cleaned so that it contain only digits

'total_sqft' variable had 3 problems in it
- the values were objects
- there are values that are expressed as ranges
- there are values having 'sq meters, perch' term in them

Cleaning of 'total_sqft'
- convert objects to floats
- convert ranges to averages
- drop rows having other terms in it


'location' variable has way too many unique values which will not be efficient to convert to dummy variables.
- 1254 unique values
- 1017 locations having less than 10 houses

Cleaning of 'location'
- set the location value to 'others' for those locations having less than 10 houses. 


### 6.2 Outlier Removal

It is unusual as per the domain knowledge to have a house with less than 300 sq feet per bedroom. So we have removed 655 observations having such cases. 

Created a new column 'price_per_sqft' which will be used to detect outliers. 
- minimum value is way too low
- maximum value is way too high
- removed observations having +- 3 std from the mean value

## Feature Engineering
Create Dummy Variables
- Location
- Area type

## Modeling & Evaluation

Trained Multiple Linear Regression and received an accuracy of 82.23% using Cross-validation