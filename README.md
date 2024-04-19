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
2. [Data Preparation and Cleaning](#2-Data-Preparation-and-Cleaning)
3. [Exploratory Data Analysis](#3-Exploratory-Data-Analysis)
4. [Dimensionality Reduction](#4-Dimensionality-Reduction)
5. [Clustering](#5-Clustering)
6. [Data Driven Insights and Conclusion](#6-Data-Driven-Insights-and-Conclusion)
7. [References](#7-References)
---
### 1. [Problem Formulation]([https://github.com/Roland13579/SC1015-DS-Project/blob/main/SC1015%20Data%20Prep%20%26%20Cleaning%20and%20Exploratory%20Data%20Analysis.ipynb])

**Our Dataset:** [Sleep Health and Lifestyle Dataset]([https://www.kaggle.com/datasets/uom190346a/sleep-health-and-lifestyle-dataset]) \
**Our Question:** How do different lifestyle predictor variables affect Sleep Quality? 


### 2. [Data Preparation & Cleaning and Exploratory Data Analysis](https://github.com/Roland13579/SC1015-DS-Project/blob/main/SC1015%20Data%20Prep%20%26%20Cleaning%20and%20Exploratory%20Data%20Analysis.ipynb)
We prepared and cleaned the data for a more accurate model for machine learning later on. Then, we 

We performed the following:
1. **Preliminary Feature Selection:** `8` relevant variables out of `61` were selected.
2. **Dropping `NaN`s**: All the `NaN` values in these `8` variables were dropped. 
3. **Splitting Dataset in Two:** The `8` variables were then split in 2 DataFrames. One with `6` variables relating to conventionality and the other with `2` relating to success. 
4. **Encoding Categorical Variables:** The categorical variables in both the DataFrames were encoded appropriately. 

### 3. [Exploratory Data Analysis](https://github.com/ardnep/ntu-sc1015-mini-project/blob/e79194b4337bb109729f915ef474e608031fd4f8/Part_2_EDA.ipynb)
Then, we explored each of our two DataFrames further using Exploratory Data Analysis to answer questions like are there any patterns we are noticing? What do our success variables look like? What about the conventionality variables? Are there any underlying relationships between them? Can we make any inferences for our question at this stage? 

To achieve this we did the following:
1. **Explored `ConvertedComp`**: This variable is the annual compensation in USD (a.k.a Salary). Median of around $54k was seen. A lot of outliers with high salaries were present.
2. **Explored `JobSat`:** This variable is the job satisfaction (`0-4` scale). Most frequent ratings were `2` and `4`. The mean rating was at `2.3`.
3. **Explored Relationships Between `JobSat` and `ConvertedComp`:** Weak correlation was seen between `JobSat` and `ConvertedComp`.
4. **Explored Variables Related to Conventionality:** Studied which options in the `6` variables were more frequently selected by respondents. 

For further findings and explanations, please refer to the Jupyter Notebook on EDA.

### 4. [Dimensionality Reduction](https://github.com/ardnep/ntu-sc1015-mini-project/blob/a1e85b5ec7fdeeaca5ddf6c4cdc55a9e95874124/Part_3_Dimension_Reduction.ipynb)
Our DataFrame with `6` variables after encoding was converted to a DataFrame  with `94` which is a very high dimensional data. 

This meant a few problems (curse of dimensionality):
1. It would probably not result in nicely formulated clusters.
2. High dimensional data is difficult to work with because of space and time increases when running algorithms on them.
3. High dimensional data is difficult to visualize.

So, **Multiple Correspondence Analysis (MCA)** was used to reduce these dimensions. The reason we chose MCA was that the general convention with dimensionality reduction is Principal Component Analysis (PCA), however it does not work well with categorical data which is what we have. MCA works well with multiple columns of categorical data. 

Using MCA, the dimensions were reduced from `94` columns to just `42`!


### 5. [Clustering](https://github.com/ardnep/ntu-sc1015-mini-project/blob/56310313487023eea95119db424cf0f41322d7fa/Part_4_Clustering.ipynb)

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

### 6. [Data Driven Insights and Conclusion](https://github.com/ardnep/ntu-sc1015-mini-project/blob/e79194b4337bb109729f915ef474e608031fd4f8/Part_5_Data_Driven_Insights.ipynb)
Here, we re-combined our variables related to success and the clustered variables related to conventionality to see if there are any differences between outliers and non-outliers. We performed a comparative Exploratory Data Analysis on the outliers vs. non-outliers to see if we can infer anything from the similarities and differences. 

In this section, we also looked at the characteristics of the individuals in our `3` clusters using the variables related to conventionality. The findings have been presented in the Jupyter Notebook on Data Driven Insights. 

Most notably, however, we found that there were no difference in the distribution of the Salary or the Job Satisfaction among Outliers and Non-outliers (Conventional individuals and non-conventional individuals). So, we concluded that unconventionality might NOT be an indicator of success. 

### 7. References
1. [https://bookdown.org/brian_nguyen0305/Multivariate_Statistical_Analysis_with_R/what-is-mca.html](https://bookdown.org/brian_nguyen0305/Multivariate_Statistical_Analysis_with_R/what-is-mca.html) 
2. [https://pca4ds.github.io/mechanics.html](https://pca4ds.github.io/mechanics.html) 
3. [https://support.minitab.com/en-us/minitab/18/help-and-how-to/modeling-statistics/multivariate/how-to/multiple-correspondence-analysis/interpret-the-results/all-statistics-and-graphs/](https://support.minitab.com/en-us/minitab/18/help-and-how-to/modeling-statistics/multivariate/how-to/multiple-correspondence-analysis/interpret-the-results/all-statistics-and-graphs/)
4. [https://github.com/MaxHalford/prince](https://github.com/MaxHalford/prince)
5. [https://www.researchgate.net/post/What-should-the-minumum-explained-variance-be-to-be-acceptable-in-factor-analysis](https://www.researchgate.net/post/What-should-the-minumum-explained-variance-be-to-be-acceptable-in-factor-analysis)
6. [https://hdbscan.readthedocs.io/en/latest/how_hdbscan_works.html](https://hdbscan.readthedocs.io/en/latest/how_hdbscan_works.html)
7. [https://www.dbs.ifi.lmu.de/~zimek/publications/SDM2014/DBCV.pdf](https://www.dbs.ifi.lmu.de/~zimek/publications/SDM2014/DBCV.pdf)
8. [https://github.com/christopherjenness/DBCV](https://github.com/christopherjenness/DBCV)
9. [https://www.kdnuggets.com/2020/04/dbscan-clustering-algorithm-machine-learning.html](https://www.kdnuggets.com/2020/04/dbscan-clustering-algorithm-machine-learning.html)
10. [https://www.youtube.com/watch?v=dGsxd67IFiU](https://www.youtube.com/watch?v=dGsxd67IFiU)
11. [https://towardsdatascience.com/tuning-with-hdbscan-149865ac2970](https://towardsdatascience.com/tuning-with-hdbscan-149865ac2970)



