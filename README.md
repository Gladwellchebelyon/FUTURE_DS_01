# FUTURE_DS_01Titanic Survival Analysis 

 ![image.png](attachment:image.png)
 

This project aims to analyze and predict passenger survival on the Titanic using a dataset from Kaggle. Through data cleaning, exploratory data analysis (EDA), and feature engineering, this project identifies key factors influencing survival, setting up a solid foundation for model building and evaluation.



Table of Contents

           Project Overview
           Dataset Information
           Data Cleaning and Preparation
           Feature Engineering
           Exploratory Data Analysis (EDA)
           Results
           Technologies Used
           Getting Started
           Acknowledgements
           
           
           
Project Overview

The Titanic dataset provides data on the passengers of the RMS Titanic, including their age, gender, class, and whether they survived the tragedy. This project focuses on understanding which factors played a significant role in survival and builds a predictive model based on these insights.



The primary goals of this project are to:

Clean and prepare the dataset for analysis.
Engineer features that might improve model accuracy.
Perform exploratory data analysis to uncover patterns and trends.
Use these insights to guide model selection and evaluation.



Dataset Information

The dataset contains information about Titanic passengers, including:

Survived: Indicator of survival (1 = survived, 0 = did not survive)
Pclass: Passenger class (1st, 2nd, 3rd)
Sex: Gender of the passenger
Age: Passenger’s age in years
SibSp: Number of siblings/spouses aboard
Parch: Number of parents/children aboard
Fare: Ticket fare
Embarked: Port of embarkation (C, Q, S)
The data is split into train_df and test_df for model training and evaluation.



Data Cleaning and Preparation

Handling Missing Values:

Imputed missing Age values with the median age.
Filled missing Embarked values with the most common embarkation point.
Excluded or simplified the Cabin feature due to a high proportion of missing values.


Correcting Data Types:

Converted Pclass and Survived to categorical types to optimize memory and improve analysis efficiency.


Outlier Treatment:

Capped outliers in Age and Fare using the IQR method to reduce their influence on model training.


Feature Engineering

Family Size: Created a new feature, FamilySize, by combining SibSp and Parch, plus 1 to account for the individual passenger.



      python
      Copy code
train_df['FamilySize'] = train_df['SibSp'] + train_df['Parch'] + 1
test_df['FamilySize'] = test_df['SibSp'] + test_df['Parch'] + 1


IsAlone: Added a feature to indicate whether a passenger was alone (FamilySize = 1) or with family (FamilySize > 1).

python
Copy code
train_df['IsAlone'] = (train_df['FamilySize'] == 1).astype(int)
test_df['IsAlone'] = (test_df['FamilySize'] == 1).astype(int)




Exploratory Data Analysis (EDA)


Univariate Analysis:

Examined distributions of continuous variables (Age, Fare) and visualized categorical variables (Pclass, Sex, Embarked) to understand the makeup of the dataset.


Bivariate Analysis:

Analyzed survival rates by Pclass, Sex, and FamilySize to identify which factors might be associated with higher chances of survival.


Multivariate Analysis:

Generated a correlation heatmap to assess relationships between numerical features, especially checking if Fare and Pclass were highly correlated, indicating redundancy.



Results
The EDA provided the following insights:

Class and Gender: First-class passengers and females had significantly higher survival rates.
Family Size: Larger family sizes showed lower survival rates, while passengers who were alone had a distinct survival pattern.
Fare and Age: Higher fare was associated with higher survival likelihood, likely due to class differences.
These findings guided feature selection and the choice of algorithms for predictive modeling.



Technologies Used
Python: For data analysis and modeling
Pandas: Data manipulation and analysis
Matplotlib & Seaborn: Data visualization
Scikit-Learn: Model building and evaluation



Getting Started
Clone the repository and navigate to the project directory.

bash
Copy code
git clone https://github.com/username/Titanic-Survival-Analysis.git
cd Titanic-Survival-Analysis



Install required packages:

bash
Copy code
pip install -r requirements.txt


Run the analysis:

Open the Jupyter Notebook (Titanic_EDA_Modeling.ipynb) to follow along with the data cleaning, feature engineering, and EDA steps.



Acknowledgements
Kaggle for the Titanic dataset: Titanic: Machine Learning from Disaster
Scikit-Learn documentation for machine learning tools and resources






