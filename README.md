# Car-Insurance-Claim-Predictor
Create a simple model to predict whether a customer will make a claim on their insurance during the policy period.
The csv dataset was acquired from Datacamp Guided Project.
# Project/Goals
...
The goal of the project is to identify the single feature of the data that is the best predictor of whether a customer will put in a claim. The steps involve:
1. Reading in and exploring the dataset
2. Finding and possibly filling missing values
3. Preparing for modeling
4. Building and storing the models
5. Measuring performance
6. Finding the best performing model
## Data dictionary
| Column | Description |
|--------|-------------|
| `id` | Unique client identifier |
| `age` | Client's age: <br> <ul><li>`0`: 16-15</li><li>`1`: 26-39</li><li>`2`: 40-64</li><li>`3`: 65+</li></ul> |
| `gender` | Client's gender: <br> <ul><li>`0`: Female</li><li>`1`: Male</li></ul> |
| `driving_experience` | Years the client has been driving: <br> <ul><li>`0`: 0-9</li><li>`1`: 10-19</li><li>`2`: 20-29</li><li>`3`: 30+</li></ul> |
| `education` | Client's level of education: <br> <ul><li>`0`: No education</li><li>`1`: High school</li><li>`2`: University</li></ul> |
| `income` | Client's income level: <br> <ul><li>`0`: Poverty</li><li>`1`: Working class</li><li>`2`: Middle class</li><li>`3`: Upper class</li></ul> |
| `credit_score` | Client's credit score (between zero and one) |
| `vehicle_ownership` | Client's vehicle ownership status: <br><ul><li>`0`: Does not own their vehilce (paying off finance)</li><li>`1`: Owns their vehicle</li></ul> |
| `vehcile_year` | Year of vehicle registration: <br><ul><li>`0`: Before 2015</li><li>`1`: 2015 or later</li></ul> |
| `married` | Client's marital status: <br><ul><li>`0`: Not married</li><li>`1`: Married</li></ul> |
| `children` | Client's number of children |
| `postal_code` | Client's postal code | 
| `annual_mileage` | Number of miles driven by the client each year |
| `vehicle_type` | Type of car: <br> <ul><li>`0`: Sedan</li><li>`1`: Sports car</li></ul> |
| `speeding_violations` | Total number of speeding violations received by the client | 
| `duis` | Number of times the client has been caught driving under the influence of alcohol |
| `past_accidents` | Total number of previous accidents the client has been involved in |
| `outcome` | Whether the client made a claim on their car insurance (response variable): <br><ul><li>`0`: No claim</li><li>`1`: Made a claim</li></ul> |
# Process
1. Reading in and exploring the dataset
Create a pandas DataFrame and examine for data types, missing values, and distributions.
Exploring the data
•	Read in the dataset as a pandas DataFrame using pd.read_csv(). 
•	Explore the data to see what the values look like, the data types, missing values, and distributions. 
•	You can use methods such as .head(), .info(), and .describe().
2. Filling missing values
Prepare data for modeling by ensuring there are no missing values.
Filling missing values with an appropriate statistic
•	Two of the columns have missing values, and their values appear to be normally distributed.
•	Replace missing values in these columns with the mean.
•	You can use the Series .fillna() method to fill missing values, passing the .mean() of the respective column.
3. Preparing for modeling
Create variables for modeling and storing the results.
Creating a list to store the models
•	Create an empty list called models to store each model object created.
•	You can create an empty list using square brackets, e.g., a_list = [].
4. Building and storing the models
Build one model per feature and save the results to a list.
Modeling with a for loop
•	Loop through features.
•	Inside the for loop, create a Logistic Regression model to estimate the relationship between "outcome" and the iterator from features, fitting the data, and saving as a variable called models.
•	You can use an f-string to pass a variable inside a string through the use of curly brackets {}. For example, to print the name of the iterator feature in a for loop:
for col in features: print(f"{col}"") 
•	Append the model to the models list.
5. Measuring performance
Calculate the accuracy of each model.
Creating a list to store model accuracies
•	Create an empty list and store it as accuracies.
6. Finding the best performing model
Locate which model has the highest accuracy score.
Identifying the index of accuracies with the largest score
You can find the index of an item in a list by calling the list's .index() method.
Inside .index(), you need to look up the max() value in accuracies.
Mapping the highest accuracy to the feature
Slice features using square brackets [] containing the index of the model in “accuracies” with the highest score.
Use .pd.DataFrame() to create a pandas DataFrame, passing a dictionary with "best_feature" and "best_accuracy" as keys, along with the feature and its accuracy score as values.
 Set the index keyword argument equal to a list containing 0.

 # Results
 •	Among our predicted model with each feature, 'age' and 'driving_experience' have the the highest accuracy score of respectively: age: 0.7779141104294478, driving_experience: 0.7711656441717791. The model suggests that there are two best candidate models to predict whether a customer will make a claim on their insurance during the policy period, with 'age' having a slightly better accuracy than 'driving_experience'.

 •	Business insights drawn from the prediction visualizations:
 In reality, the underlying theme of car insurance contracts are based on risk assumptions of how likely the insured will claim on the insurance to determine the rates charged. Our prediction visualization reveals an interesting finding that the accuracy score is not always the preferred metric to choose a machine learning model for business.
 If everything's risk-based in this case, predicting more people claiming the auto insurance is better and less risky than predicting less than the actual number. Our client might prefer to use 'driving_experience' as the main predictor.

 # Challenges

# Future Goals
