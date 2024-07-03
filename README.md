# Student-Dropout-Prediction
The goal of this project is to use machine learning algorithms to predict undergraduate student outcomes through the analysis of a large dataset that include financial data, academic progress data, and static data.Our methodical approach to data integration,
cleaning, and analysis seeks to identify the main factors that influence student performance
and dropout risk. The F-Beta score, a performance metric that strikes a compromise between
recall and precision, will be used to assess the initiative's progress and determine how
accurate our dropout predictions were.

# Deep Dive into the Dataset
The dataset is a comprehensive collection of data points covering aspects of student
progress, financial aid, and static background information across multiple academic years:

Progress Data: Tracks students' academic progress over terms by reflecting academic
activities such as course enrollments, grades, credits, and learning objectives.

Financial Data: Details on scholarships, loans, grants, and work-study programs.

Static Data: includes demographic data such age, gender, race/ethnicity, educational
history, GPA from high school, and previous college enrollment. Because it remains
constant over time, this data set is static.

# Python Libraries Used
<img width="1408" alt="Screenshot 2024-07-03 at 2 13 19 PM" src="https://github.com/jjw0930/Student-Dropout-Prediction/assets/163229179/4579f9af-9ed2-47f1-8aae-9deba6eba9b6">


# Data Cleaning and Preparation
Data cleansing was conducted on three distinct datasets involving the removal ofcolumns with over 40% missing values, the substitution of -1 values with NaN, and theexclusion of rows with negative values in the value columns. 

The column named ['WithLeading ID'] was renamed to ['StudentID']. Additionally, the variables for ['MaritalStatus', 'gradelevel', 'housing'] were converted into numerical codes to transform theminto categorical variables, facilitating better analysis. Financial data, previouslysegmented by academic years and categories, was consolidated by summing the valueswithin each category, resulting in new variables that represent the total amounts forloans, scholarships, work-study programs, and grants for each academic year. These new variables were then integrated back into the original dataset, enhancing itsstructure for further analysis.

Create a new column named ['TermID'] to store both the term and year information.This DataFrame will retain the first column, which represents unique ['StudentID'], alongwith the newly created ['TermID'] and the values from the ['TermGPA'] column.For eachspecified column in the list ['CompleteDevMath', 'CompleteDevEnglish', 'Complete1','Complete2', 'CompleteCIP1', 'CompleteCIP2', 'DegreeTypeSought'], the function willcalculate both the total GPA and the count of terms. The resulting total and count foreach column will be added to the new columns. These new columns will be named['Total_ColumnName', 'Count_ColumnName'], respectively, where ['ColumnName'] is thename of the column being processed.

# Analytical Approach
Data Preprocessing:
I approached categorical and numerical data in distinct ways:Mean imputation and standard scaling were used to numerical characteristics, whileone-hot encoding was used to fill categorical variables with the most common values.After that, I used TestIDs and Dropout labels to select datasets for Kaggle testing andtraining. After this configuration, operations were combined and the inputs (X) andoutputs (Y) for the models were specified. I separated the data after preprocessing toproduce separate training and test sets. The best-performing model was subsequentlychosen after we tested several classifiers on the validation set. This model was then used to forecast results on the Kaggle test data, resulting in an output of a structuredDataFrame.

Feature Engineering:
I designed features based on my investigation to represent thestudents' socioeconomic and academic attributes. Using significance scores, I trained aDecision Tree with a fixed seed to discover important predictive variables and ensurereproducibility. The dataset was refined by using a Random Forest for feature selectionand LDA to reduce dimensionality. I also added Polynomial Features and InteractiveFeature Generation to the data, which improved the models' predictive accuracy (asindicated by the F-Beta score) for student dropout predictions.

Model Selection and Evaluation:
Multiple models were tested for their predictiveaccuracy, including Logistic Regression, Random Forest, XGBoost, KNN, and LDA. Themodels were evaluated based on accuracy, precision, recall, and F1 scores to select thebest performer for predicting student outcomes. The analysis revealed XGBoost,augmented by Polynomial Features, as the standout performer, achieving an impressiveaccuracy of 0.9604565837749695, showcasing its superior predictive capability.

# Challenges and Solutions
Data Integration:
The challenge of merging datasets from various sources was met bydeveloping a consistent schema and using Python scripts for automated merging andcleaning.

Model Selection:
The diverse nature of the data necessitated the testing of multiplemodels. Cross-validation and grid search techniques were employed to identify themodels that best fit our data.

Model Accuracy Improvement:
Addressing low model accuracy was a key challenge.Initially, hyperparameter adjustments provided some improvement, but the realbreakthrough came from using cross-validation to reveal overestimations of modelperformance. This led to a deeper dive into data processing and cleaning. Analyzingvariable relationships and enhancing data relevance through thorough cleaningsignificantly improved model accuracy. Exploring multiple solutions, such as datatransformation and optimizing variable correlations, was crucial in solving this problem.

# Conclusion
The value of meticulous data preparation and the potential of machine learning ineducational research are demonstrated by this undertaking. Our analysis yields actionableinsights that can guide actions aimed at improving student retention rates by identifyingcritical factors influencing student outcomes.
