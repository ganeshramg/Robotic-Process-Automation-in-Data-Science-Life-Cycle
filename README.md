# Robotic Process Automation in Data Science Life Cycle - Dissertation at Livewire - Ganesh Ram Gururajan

## Purpose:
Automating a process is a huge financial benefit. Automation of Data Science life cycle(at least till data imputation) will be of 
great advantage to a lot of companies and Data Scientists as huge time is spent in Data Cleaning alone.

## Disclaimer:
This code can be used only on semi-cleaned Dataset

## Final Result: The end result of this project is to print the best model and the correspoding evaluation.
For example : 'The best model is RandomForestRegressor with minimum absolute error of 10' or, 'The best model is XGBoostClassifier with
maximum accuracy of 98%'

## Requirements:
 Python,
 Pandas,
 Numpy,
 Sci-kit Learn,
 Seaborn
 
## Process: 
### Data Import
The path of the dataset along with target column is specified with a * in between

### 0. ML Needed
If the target column has huge number of unique values, then we go with 'Regression', otherwise, it's 'Classification'. In this project,
I've selected a threshold of 10 to decide on the process

### 1. Removal of Columns with high missing data
A dictionary with keys as column names and values as a percentage of missing columns is created. In this project, I've removed columns 
with more than 30% missing data

### 2. Imputation of Missing Data
Columns with missing values of more than 0.1% and less than 35% are imputed by mean_imputation for numerical columns and 
mode_imputation for categorical columns

### 3. Dropping missing values
Now that, after the above processes, we are left with data which has a maximum of only 0.1% missing data, which can be dropped
using dropna() funcion. After dropping we have completely imputed data, i.e., no missing values

### 4. Creating Dummies for Categorical columns
### (To avoid using pd.get_dummies or OneHotEncoder) I've written my own encoder for this project. 
First we store the unique values in a list called 'Categories' and apply a function to each categorical column which returns the
index of the categories present in that column, which itself can be used as dummies. There's a separate repo called **ganesh_encoder** 
at **github.com/ganeshramg** to help you understand it better

### 5. Defining dependant and Independant variable
X is independant and Y is dependant
so X is data.drop(target_column); specified in the first step of this project
Y is data(target_column)

### 6. Train Test Split
Using the train_test_split.py from the model_selection of sci-kit learn, We split the entire data into training and testing set. In
project, I've used a test_size of 0.25, stratify=y if we need classification

### 7. Machine Learning
I've selected my top four algorithms : Decision Tree, Random Forest, XGBoost, Adaboost. This is the order is which the process takes 
place. If ML Needed is Classification, import the correspoding classfication algorithms, else, import the correspoding 
regression algorithms. Also, evaluation is imported accordingly, accuracy_score for classification and mean_absolute_error for 
regression

### 8. Fit
Fit the training data for all the four algorithms

### 9. Predict
Predict using X_test column from test data for all the four algorithms and store it in pred_1 to pred_4

### 10. Evaluation
Store the accuracy scores in a list(for classification), or mean_absolute_errors in a list(for regression)

### 11. Result
If classification was performed, find the element in algorithms list with index of max(accuracy_scores), 
If regression was performed find the element in algorithms list with index of min(mean_absolute_error). Print the result

## This is a very basic automation and is a small step towards achieving completely integrated automation of Decision Making.

# Thank You
