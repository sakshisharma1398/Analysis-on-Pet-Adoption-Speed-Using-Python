# Analysis-on-Pet-Adoption-Speed
The dataset in this Project is collected from PetFinder.my
Detailed descripiton about the dataset is provided with the data_original.csv file.

Exploratory Data Analysis:
I have first started with cleaning and processing the data. Here, I removed the null and duplicate values. Then, I convereted the numerical data into categorical for better understanding and performing descriptive analysis.
I have used multiple graphs which show insights generated from the data.

Subjectivity Analysis(Text Analysis):
In the given dataset there is a description column. I first started with performing basic text analysis i.e. splitting the text, lemmatizing it and removing the stop words.
Then I did a count of the number of times a unique comes across the entire description column. However, no trends were visible with respect to the adoption speed.

Further, I decided to use TextBlob library for preprocessing textual data.
TextBlob provides a simple API for diving into common natural language processing (NLP) tasks such as part-of-speech tagging, noun phrase extraction, sentiment analysis, classification, translation, and more. Generally, a text message will be represented by bag of words. 
Subjectivity quantifies the amount of personal opinion and factual information contained in the text. The higher subjectivity means that the text contains personal opinion rather than factual information. The subjectivity is a float within the range [0.0, 1.0] where 0.0 is very objective and 1.0 is very subjective.
I found out the subjectivity of description column for each pet.
To better understand how the subjectivity is calculated I analyzed the results and found that the more hard facts and information is given in the description the lower the subjectivity.
However, here also I did not see any trend. Hence, it can be concluded that there is no impact of the description on the Adoption Speed for the pet.

Prediciting Adoption Speed Using ML:
I first created dummy variables for all variables.
Then I dropped the irrelevant dummy variables to avoid dummy variable trap.
Further, I normalized the Age column to suit the range of other variables.

Step 1 - Correlation Matrix
To build a high accuracy model it is essential to select features appropriately. I first started feature elimination using Coorelation Matrix.
With high coorelation between feature 1 and feature 2 we can understand that if we have feature 1 in our dataset, feature 2 won’t bring much new information. That’s why there is no point in keeping feature 2 since it only adds to complexity when training a model.
Hence, I dropped independent variables with high correlation.

Step 2 - Testing multicollinearity with VIF
A variance inflation factor (VIF) is a measure of the amount of multicollinearity in regression analysis. Multicollinearity exists when there is a correlation between multiple independent variables in a multiple regression model. This can adversely affect the regression results. Thus, the variance inflation factor can estimate how much the variance of a regression coefficient is inflated due to multicollinearity.
In the above result, we observe that once we have removed columns with high collinearity using the correlation matrix, none of the values have a high VIF. Thus, all the above variables are still to be considered.

Step 3 - Backward Elimination for Feature Elimiation
Backward Elimination works by iteratively removing features that are not predictive of the target variable or have the least predictive power.
Using backward elimination, I was able to further reduce the independent variables from 19 to 15.

Step 4 - Feature Elimination based on feature importance
I also perform a feature importance test to further reduce the number of independent variables.

Hence, the features with highest significance in prediciting Adoption Speed are:
'Age','Color_White', 'Color_Cream','Color_Golden', 'Sterilized_Not Sure', 'Sterilized_Yes', 'Health_Serious Injury','Health_Minor Injury','Size_Medium', 'Vaccinated_Yes'

Machine Learning Models:
I divided the dataset into test and training.
I used 3 ML models to determine the best model for my analysis.

Below are the results of the models.
Test set accuracy of our logistic Regression model is 59.66%
Test set accuracy of our Random Forest Classifier model is 59.37%
Test set accuracy of our Gaussion Naive Bayes model is 57.69%

It is observed that the highest accuracy is provided by the Logistic Regression Model and the Random Forest Classifier.

The attributes that are most relevant for the prediction are: Age, Size, Sterlizied & Health to name a few.

Few suggestions for Animal Shelters to increase the Adoption Rate are as follows:
1 - Animals that are currently in the age-group 4-10 should be given more priority for Adoption. This is because, the animals younger than age 4 are bound to get adopted without much effort, animals above the age 10 have fewer chances to get adopted and thus, any extra effort would barely bring in any improvement.
2 - Animals that are medium in size should be given further priority as small animals are automatically the preferred ones.
3 - Animals with minor injury can be cared for on priority as animals who are perfectly healthy are faster to get adopted. Minor Injuries are likely to be overcome quickly and this would help them be categorized as healthy soon.
4 - Adoption Centers should take extra steps to ensure the animals are sterilized, so it can improve adoption chances.
