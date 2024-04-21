# SC1015: Data Science Mini Project - Sleep & Lifestyle

School of Computer Science and Engineering \
Nanyang Technological University \
Lab: FCSB \
Group :  7

Members: 
1. Jacob Loh Jun Cong ([@JacLoh](https://github.com/JacLoh))
2. Alden Budiman ([@Alden Budiman](https://github.com/aldenbudiman))
3. Ronald ([@Roland13579](https://github.com/Roland13579))

---
### Description:
This repository contains the Jupyter Notebooks, datasets and the source materials used for our SC1015 (Introduction to Data Science and A.I.) Project. \
This ReadMe only consists of a brief outline of our project.
---
### Table of Contents:
1. [Problem Formulation](#1-Problem-Formlation)
2. [Data Preparation & Cleaning and Exploratory Data Analysis](#2-Data-Preparation-and-Cleaning)
3. [Machine Learning for Numerical Data](#3-Machine-Learning-for-Numerical-Data)
4. [Model Building Using Both Numerical and Categorical Data](#4-Model-Building-Using-Both-Numerical-and-Categorical-Data)
5. [Conclusion](#5-Conclusion)
---
### 1. [Problem Formulation](https://github.com/Roland13579/SC1015-DS-Project/blob/main/SC1015_Data_Prep_%26_Cleaning_and_Exploratory_Data_Analysis%20(1).ipynb)

Sleep is an essential function that serves a variety of important physical and psychological functions but up to two-thirds of adults occasionally experience insomnia symptoms, affecting daily functions. Hence, what modifications should we make to improve our sleep quality to allow us to have higher productivity and quality of life?
**Our Dataset:** [Sleep Health and Lifestyle Dataset](https://www.kaggle.com/datasets/uom190346a/sleep-health-and-lifestyle-dataset) \
**Our Question:** How do different lifestyle predictor variables affect Sleep Quality? 


### 2. [Data Preparation & Cleaning and Exploratory Data Analysis](https://github.com/Roland13579/SC1015-DS-Project/blob/main/SC1015_Data_Prep_%26_Cleaning_and_Exploratory_Data_Analysis%20(1).ipynb)
Firstly, We prepared and cleaned the data to ensure an accurate model for machine learning later on. Then, we used Exploratory Data Analysis to identify patterns and relationships to arrive at the respectively deductions.  

Outline of Data Preparation & Cleaning and EDA:
1. **Merging categories**: Categories that had the same meaning were merged. Categories that are too poorly represented in the dataset to allow significant analysis were removed.
2. **Checking for outliers**: Check for outliers outside (Q1 - 1.5 * IQR) or (Q3 + 1.5 * IQR). 
3. **Explored Skewness and distribution:**: Mean, Median and Mode were analysed to arrive at deductions for skewness and distribution to better understand data.
4. **Explored Numerical data with Correlation matrix :** Numerical variables with the highest correlation to Quality of Sleep were identified, to be used for regression later. 
5. **Explored Categorical data with Boxplot:** Categorical variables with the highest correlation to Quality of Sleep were identified, to be used for classification later

 Please refer to the Jupyter Notebook for the full Exploratory Data Analysis of our dataset.

### 3. [Machine Learning for Numerical Data](https://github.com/Roland13579/SC1015-DS-Project/blob/main/Machine%20Learning%20for%20Numerical%20Datas.ipynb)

For the machine learning process on numerical data. We will conduct the analysis across 3 different models.

We begin our analysis with Linear Regression, aiming to identify strong relationships between predictor variables and sleep quality. Stronger relationships are characterized by higher explained variance (R²) and lower Mean Absolute Error (MAE). Our analysis on "Daily Steps," "Sleep Duration," "Age," and "Heart Rate" reveals sleep duration as the strongest indicator, followed by heart rate, age, and daily steps.

The second model, Random Forest Regression compares the actual quality of sleep to the predicted quality of sleep using multiple decision trees. Random Forest Regression demonstrates improved predictive accuracy over linear models, evidenced by its lower Mean Squared Error (MSE). Visualizing predictions through blue (training) and red (testing) dots, we observe alignment with the line of perfect prediction, indicating effectiveness in estimating actual sleep quality.

Lastly, moving on to OLS Linear Regression, our aim is to create a model closely fitting the data with minimal error. Minimizing standard errors enhances coefficient estimate precision, ensuring reliable predictions. We address multicollinearity by reducing the condition number, achieved by removing variables with high p-values. Initially including all variables in the OLS model revealed a high condition number. After eliminating non-significant variables like Daily Steps, we achieved a model with lesser multicollinearity. Further refinements led to a well-fitted model with a healthy condition number and p-values. To assess the reliability of our OLS regression model, we compare the training Mean Absolute Error (MAE) to the naive baseline. Consistent error distribution in both training and testing datasets indicates no overfitting.

Please refer to "[Machine Learning for Numerical Datas](https://github.com/Roland13579/SC1015-DS-Project/blob/main/Machine%20Learning%20for%20Numerical%20Datas.ipynb)" for more details.

### 4. [Model Building Using Both Numerical and Categorical Data](https://github.com/Roland13579/SC1015-DS-Project/blob/main/ModelBuilding-Numerical%26Categorical.ipynb)

We start by separating the data into feature and target variables followed by data scaling to ensure contribution equality. Then, we do a 75-25 split on our data, separating them into train and test data. Next, we'll start building our 9 models for predicting "Quality of Sleep", which consists of Naive Bayes, Decision Tree, Random Forest, Extra Trees, K-Nearest-Neighbors(KNN), Logistic Regression, AdaBoost, Gradient Boosting, and LightGBM.

Model building process:
1. Use GridSearch to find the best metrics to use when building our model to maximize accuracy (When needed)
2. Build the model using the metrics obtained from using GridSearch on our train data
3. Test out the model on the test data to gain an accuracy score
4. Make a confusion matrix to visualize the predictions made by the model

After repeating this process for all the models, we're able to compare all the results produced by the models. These results show that Random Forests, KNN, Gradient Boosting, and LightGBM were the best-performing models for predicting "Quality of Sleep" with an accuracy of 98.94%.

By printing out the most important variables in predicting "Quality of Sleep", we can also conclude that "Sleep Duration"(Numerical), "Stress Level"(Categorical), and "Occupation"(Categorical) were the top 3 contributors to the accuracy of our models.

Please refer to "[ModelBuilding-Numerical&Categorical](https://github.com/Roland13579/SC1015-DS-Project/blob/main/ModelBuilding-Numerical%26Categorical.ipynb)" for more details.

### 5. Conclusion
To summarise our findings, we have concluded that the numerical variables Sleep Duration and Heart Rate as well as Categorical variables Stress Level and Occupation are the most significant factors affecting quality of sleep. Throughout the process of deriving this conclusion, we have picked 3 best models - OLS Linear Regression, Random Forest and Gradient Boosting. OLS Linear Regression streamlines the numerical variables down to the most significant few by minimising standard errors and multicollinearity. Random Forest excels at finding optimal predictive values by aggregating the decisions of multiple decision trees, while Gradient Boosting effectively finds optimal predictive values by repeatedly improving the model's performance through the combination of weak learners. 






