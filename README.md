![Vaccines Picture](https://github.com/elizabeth524/Phase-3-Project/blob/main/Images/H1N1vaccine.jpeg)

# H1N1 Vaccination Rates

### Author: [Elizabeth Webster](https://github.com/elizabeth524)

## Overview

In this project, we will be building models to predict whether or not a person would receive an H1N1 vaccine based on many factors.  Our goal is to build a model with the highest possible accuracy for the test data set.

## Business Problem

This data is being prepared for a company that distributes vaccines.  They are hoping to use this information to predict the number of vaccines they will need for a certain population. 

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
People are much more likely to get vaccinated if it is recommended by their doctor.

![Education Plot](https://github.com/elizabeth524/Phase-3-Project/blob/main/Images/Education%20Level.png)
More people with a higher education level get vaccinated.

![H1N1 Plot](https://github.com/elizabeth524/Phase-3-Project/blob/main/Images/H1N1%20Knowledge.png)
Those who have more knowledge on the H1N1 virus are more likely to get vaccinated.

### Comparing Model Scores

We will only talk about our best Decision Tree, Random Forest, and XG Boost when comparing models.  It is important to note that there is still a class imbalance in our test dataset.  This will cause our precision, recall, and f1-score to be lower for the smaller class (1).  This does not mean that our model is not performing well, only that it does not have enough data.

Our Decision Tree model is not overfit.  The scores for the training data and the test data are very similar.  However, we only have an accuracy score of 81% for the test data.

Even though we adjusted our parameters to combat overfitting in our Random Forests, this model is still scoring much better for the training set than for the test set.  However, this model does give us an accuracy score of 83% for the test set.

The XG Boost model is arguably our best model.  It is not overfit to the training data, and also gives us an accuracy score of 84% for our test data.

## Conclusion and Recommendations

If the company has access to all of this information for it's population groups, then I would recommend using the XG Boost model in order to predict the number of vaccines that they would need to distribute.  This model performed the best without being overfit to the training data.

However, it is unlikely that the company will be able to gather such a vast amount of information from every population. In this case, I recommend:

* Distributing more vaccines to populations with a higher percentage of college graduates.
* Working with clinics and doctors to understand the amount of patients they are recommending the vaccine to.

## Next Steps

* Tackle the Class Imbalance
As shown in the Jupyter Notebook, the class imbalance in the test set is negatively affecting our precision, recall, and f1-scores.  To help address this issue, more information from those who receive the vaccine should be gathered.

* Vaccination Rates by Group
It would be interesting to look deeper into the vaccination rates by each group (ie, age, race, geographical region).  This could help the company better understand which groups to focus their distribution on.

* Promoting through Clinics
Since Doctor Recommendation plays such a large part in whether or not a person will get the vaccine, the company could work with clinics and doctors to help educate about and promote the vaccine.

## For More Information

See the full analysis in the [Jupyter Notebook](https://github.com/elizabeth524/Phase-3-Project/blob/main/H1N1_Data.ipynb) or review my [presentation](https://github.com/elizabeth524/Phase-3-Project/blob/main/H1N1_Vaccination_Presentation.pdf).

For additional information, contact Elizabeth Webster at [eaw524@gmail.com](eaw524@gmail.com)