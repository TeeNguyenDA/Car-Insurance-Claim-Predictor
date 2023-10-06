# Car-Insurance-Claim-Predictor
Create a simple model to predict whether a customer will make a claim on their insurance during the policy period.
The csv dataset was acquired from Datacamp Guided Project.

Machine learning enjoys significant popularity within the insurance industry, known for its strong reliance on data-driven approaches. Insurance companies allocate substantial resources to enhance their pricing strategies and precisely gauge the probability of claim submissions by policyholders. In numerous countries, possessing car insurance is a legal prerequisite for operating a vehicle on public roads, contributing to the extensive size of this market.

# Project/Goals
The data scientist team at On the Road car insurance was tasked with analyzing the company's customer data to pinpoint the most influential feature for creating a highly accurate logistic regression model. The goal of the project is to identify the single feature of the data that is the best predictor of whether a customer will put in a claim, repesented by the value of 1 in the target variable: 'outcome'.

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
1. Load and read the dataset from the csv file

2. Data cleaning
* Statistics summary table
* Plot histogram all columns
* Drop missing values
* Check for duplication
* Encode categorical columns

3. Exploratory and statistical data analysis
* Kolmogorov-Smirnov's test for normality on numerical columns
* Assumption Tests for Logistic Regression Model: Test the assumption that the dependent variable 'outcome' is binary
* Assumption Tests for Logistic Regression Model: est the assumption that the continuous independent variables ('credit_score', 'annual_mileage') being linearly related to the log odds
* Assumption Tests for Logistic Regression Model: Test the assumption of independence between features and absence of multicollinearity by the Corelation Matrix
* Assumption Tests for Logistic Regression Model: Test the assumption that the dataset size is of a large sample size
* Data scaling for numeric columns using sklearn StandardScaler

4. Logistic Regression Model
* Create an empty list called 'models' to store each model object created.
* The goal is to build one simple logistic regression model per feature (except for 'id' and 'outcome) and save the results to the empty list, because many of the features are highly correlated with each other.
* Loop through the features while creating a Logistic Regression model to estimate the relationship between "outcome" and the iterator from features, fitting the data, and append each feature's as each model in the 'models' empty list.
* Measure performance by calculating the accuracy of each model, saved in a list.
* Find the best performing model that have the highest accuracy scores: We took two best performing models with 'age' having the highest accuracy, seconded by 'driving_experience'
* Determine 'driving_experience' is better fit with business needs, due to its having a higher number of prediction for '1' - thus less risky for business holder to assume more clients might claim their auto insurance.

# Results
* Among our predicted model with each feature, 'age' and 'driving_experience' have the the highest accuracy score of respectively: age: 0.7779141104294478, driving_experience: 0.7711656441717791. The model suggests that there are two best candidate models to predict whether a customer will make a claim on their insurance during the policy period, with 'age' having a slightly better accuracy than 'driving_experience'.

* By visualizing the predicted outcome vs. the actual outcome, the prediction model using 'age' predicted less people will claim on their insurance than the acutal numbers. In reality, the underlying theme of car insurance contracts are based on risk assumptions of how likely the insured will claim on the insurance to determine the rates charged. Our prediction visualization reveals an interesting finding that the accuracy score is not always the preferred metric to choose a machine learning model for business. Predicting more people claiming the auto insurance is better and less risky for the business than predicting less than the actual number. Our company might prefer to use 'driving_experience' as the main predictor.

# Challenges
* Time constraint in the entire EDA and model building process
* Looping through a list of 16 feature columns, both numerical and categorical independent variables to find the best fit
* Overreliance on the mandate using only 'accuracy' score to measure the model performance (for simplicity): The model using 'driving_experience' to predict might have been overlooked, thus exposing business risks in risk underestimation.
* Collaborate with teammate via Github source control, and across different time zone

# Future Goals
* Re-evaluate and improve model performance by using not only accuracy score, but also precision score, recall and F1-score and link them to business needs (for example: how much gain/loss will be associated with overestimating and underestimating)
* Explore on a better approach to do feature selection such as RFE and not having to loop through each feature to save time and resources
* Explore more on contemporary machine learning algorithms on the market to improve predictive capabilities in the auto insurance claim scenario: XGBoost, J48, ANN, naïve Bayes, Random Forest (RF) algorithms and so on.
