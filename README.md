# SC1015: Data Science Mini Project - Sleep & Lifestyle

School of Computer Science and Engineering \
Nanyang Technological University \
Lab: FCSB \
Group :  

Members: 
1. Jacob Loh Jun Cong ([@JacLoh](https://github.com/JacLoh))
2. 
3.

---
### Description:
This repository contains the Jupyter Notebooks, datasets, video presentation and the source materials used for our SC1015 (Introduction to Data Science and A.I.) Project.
This ReadMe only consists of a brief outline of our project.
---
### Table of Contents:
1. [Problem Formulation](#1-Problem-Formlation)
2. [Data Preparation & Cleaning and Exploratory Data Analysis](#2-Data-Preparation-and-Cleaning)
3. [Dimensionality Reduction](#4-Dimensionality-Reduction)
4. [Clustering](#5-Clustering)
5. [Data Driven Insights and Conclusion](#6-Data-Driven-Insights-and-Conclusion)
6. [References](#7-References)
---
### 1. [Problem Formulation]([https://github.com/Roland13579/SC1015-DS-Project/blob/main/SC1015%20Data%20Prep%20%26%20Cleaning%20and%20Exploratory%20Data%20Analysis.ipynb])

**Our Dataset:** [Sleep Health and Lifestyle Dataset](https://www.kaggle.com/datasets/uom190346a/sleep-health-and-lifestyle-dataset)
**Our Question:** How do different lifestyle predictor variables affect Sleep Quality? 


### 2. [Data Preparation & Cleaning and Exploratory Data Analysis](https://github.com/Roland13579/SC1015-DS-Project/blob/main/SC1015%20Data%20Prep%20%26%20Cleaning%20and%20Exploratory%20Data%20Analysis.ipynb)
Firstly, We prepared and cleaned the data to ensure an accurate model for machine learning later on. Then, we used Exploratory Data Analysis to identify patterns and relationships and the respectively deductions.  

Outline of Data Preparation & Cleaning and EDA:
1. **Merging categories**: Categories that had the same meaning were merged. Categories that are too poorly represented in the dataset to allow significant analysis were removed.
2. **Checking for outliers**: Check for outliers outside (Q1 - 1.5 * IQR) or (Q3 + 1.5 * IQR). 
3. **Explored Skewness and distribution:**: Mean, Median and Mode were analysed to arrive at deductions for skewness and distribution to better understand data.
4. **Explored Numerical data with Correlation matrix :** Numerical variables with the highest correlation to Quality of Sleep were identified, to be used for regression later. 
5. **Explored Categorical data with Boxplot:** Categorical variables with the highest correlation to Quality of Sleep were identified, to be used for classification later

 Please refer to the Jupyter Notebook for the full Exploratory Data Analysis of our dataset.

### 3. [Dimensionality Reduction](https://github.com/ardnep/ntu-sc1015-mini-project/blob/a1e85b5ec7fdeeaca5ddf6c4cdc55a9e95874124/Part_3_Dimension_Reduction.ipynb)
Our DataFrame with `6` variables after encoding was converted to a DataFrame  with `94` which is a very high dimensional data. 

This meant a few problems (curse of dimensionality):
1. It would probably not result in nicely formulated clusters.
2. High dimensional data is difficult to work with because of space and time increases when running algorithms on them.
3. High dimensional data is difficult to visualize.

So, **Multiple Correspondence Analysis (MCA)** was used to reduce these dimensions. The reason we chose MCA was that the general convention with dimensionality reduction is Principal Component Analysis (PCA), however it does not work well with categorical data which is what we have. MCA works well with multiple columns of categorical data. 

Using MCA, the dimensions were reduced from `94` columns to just `42`!


### 4. [Clustering](https://github.com/ardnep/ntu-sc1015-mini-project/blob/56310313487023eea95119db424cf0f41322d7fa/Part_4_Clustering.ipynb)

With these `42` columns, we then performed clustering. We chose the **Hierarchical Density-Based Spatial Clustering of Applications with Noise (HDBCAN)**. 

The reasons for this are:
1. This is a density based clustering algorithm which means it does not need the specification of the number of clusters. Essentially, this algorithm will not *force* any point into a cluster. Instead, points which do not really belong to any cluster are labeled "noise". This is clearly useful for us since we are doing anomaly detection (outlier/noise detection).
2. Because this is density based, the shape of our data does not matter which is useful since we are working with high dimensional data and it is not possible for us to visualize and understand what kind of shapes our data might have. 
3. With a non-hierarchical DBSCAN, there are certain hyperparameters that are difficult to tune. HDBSCAN removes the need to tune some of these parameters. 
4. Because HDBSCAN is a hierarchical clustering algorithm even if we have a high dimensional data, we can use dendrograms to somewhat visualize the clusters and make inferences.

More details on HDBSCAN and its parameters are presented in the Jupyter Notebook on Clustering.

In this section, we performed the following:
1. Clustering with Random Parameters
2. Hyperparameter Tuning with GridSearchCV using DBCV Score
3. Readjusting Parameters (GridSearchCV does not work well in this case)
4. Clustering with New Parameters

Our final clustering resulted in a total of `3` clusters and `6206` outliers (out of `19362` total points).

### 5. [Data Driven Insights and Conclusion](https://github.com/ardnep/ntu-sc1015-mini-project/blob/e79194b4337bb109729f915ef474e608031fd4f8/Part_5_Data_Driven_Insights.ipynb)
Here, we re-combined our variables related to success and the clustered variables related to conventionality to see if there are any differences between outliers and non-outliers. We performed a comparative Exploratory Data Analysis on the outliers vs. non-outliers to see if we can infer anything from the similarities and differences. 

In this section, we also looked at the characteristics of the individuals in our `3` clusters using the variables related to conventionality. The findings have been presented in the Jupyter Notebook on Data Driven Insights. 

Most notably, however, we found that there were no difference in the distribution of the Salary or the Job Satisfaction among Outliers and Non-outliers (Conventional individuals and non-conventional individuals). So, we concluded that unconventionality might NOT be an indicator of success. 

### 6. References




