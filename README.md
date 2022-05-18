![Vaccines Picture](https://github.com/elizabeth524/Phase-3-Project/blob/main/Images/H1N1vaccine.jpeg)

# H1N1 Vaccination Rates

### Author: [Elizabeth Webster](https://github.com/elizabeth524)

## Overview

In this project, we will be building models to predict whether or not a person would receive an H1N1 vaccine based on many factors.  Our goal is to build a model with the highest possible accuracy for the test data set.

## Business Problem

This data is being prepared for a company that produces vaccines.  They are hoping to use this information to predict the number of vaccines they will need for a certain population in order to reduce waste. 

## Data

We will be using data from the National 2009 H1N1 Flu Survey:

This data includes many features such as:
* H1N1 Conern
* H1N1 Knowledge
* Personal Behaviors
* Doctor Recommendations
* Vaccine Opinions
* Age
* Education Level
* Race
* Employment

We will be using all of these factors in our model to predict the likelihood of a person receiving a vaccine.

## Methods

### Data Cleaning

We needed to clean this data before we could use it in our models.  The cleaning steps that we followed were:

#### Removing Unnecessary Columns
This dataset included a few columns that were not related to our target (H1N1):
* Seasonal Vaccine Opinions
* Doctor Recommendation for Seasonal Vaccines
There were also three columns that were missing half of the data entries:
* Health Insurance
* Employment Industy
* Employment Occupation
We removed those columns from our dataset completely.
#### Finding and Filling Missing Data
There was a fair amount of missing data in this dataset.  We handled missing data in the following way:
* Create an 'unknown' category for columns missing more than 1000 entries
* Drop the remaining null data (less than 5% of the data)
#### Splitting Data
In order to check how well our models perform, we split our data into two groups:
* Training Data (75% of Data)
* Test Data (25% of Data)
#### Changing Categorical to Numeric Variables
There were many columns in this dataset that were categorical. We used a One Hot Encoder to transform them to numeric values that could be used in our models.
#### Addressing the Class Imbalance
Looking at our data labels, there were only 4006 people who received the H1N1 vaccine versus the 14615 who did not.  Since the difference between these two numbers is so large, we used synthetic minority oversampling (SMOTE) to create 10609 more entries for people who received the vaccine.

### Creating Models

#### Baseline Model
After our data was cleaned, we created a baseline model.  The model that we chose to use was a Decision Stump, a Decision Tree with a very shallow depth, in our case three.  This first model performed fairly well, producing an accuracy of 80%.
#### Random Forests
Our next step was to use an emsemble method to create a model.  Random Forests makes use of more than one model to make predictions, so it is more likely to pick up on different characteristics.  Initially, this model was overfit, meaning it was performing much better on the training data than it was on the testing data.  We had to manually adjust our parameters to address this issue.  The accuracy of this model was 83%.
#### XG Boost
The last model we created was the top gradient boosting algorithm, XG Boost.  This model gave us our best accuracy at 84%.
#### Grid Searches
For each of our models, we performed a Grid Search in order to find the best parameters with which to tune our model.  In the case of the Decision Tree and XG Boost, these best parameters did increase our overall scores.  For Random Forests, however, the Grid Search's best parameters did not address the aggressive overfitting, which is why we had to adjust the parameters manually.

### Feature Importance

Once we had created our Random Forests and XG Boost models, we could look at their top ten feature importances, or which features had the greatest impact on the result.  Some of our top features were:
* Doctor Recommendation
* Education 
* H1N1 Knowledge Level

Vaccination rates based on these factors:

![Doctor Rec Plot](https://github.com/elizabeth524/Phase-3-Project/blob/main/Images/Doctor%20Recommendation.png)

![Education Plot](https://github.com/elizabeth524/Phase-3-Project/blob/main/Images/Education%20Level.png)

![H1N1 Plot](https://github.com/elizabeth524/Phase-3-Project/blob/main/Images/H1N1%20Knowledge.png)

### Comparing Model Scores



## Conclusion and Recommendations


## Next Steps


## For More Information

See the full analysis in the [Jupyter Notebook](https://github.com/elizabeth524/Phase-3-Project/blob/main/H1N1_Data.ipynb) or review my [presentation]().

For additional information, contact Elizabeth Webster at [eaw524@gmail.com](eaw524@gmail.com)