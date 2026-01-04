# Analysis of Digital Payment Inclusion Determinants in High-Income Economies

## Project Overview
This project focuses on identifying the key determinants of digital payment adoption in high-income countries using the World Bank Global Findex database. The objective is to determine whether digital exclusion is primarily driven by demographic factors (age, gender, education) or by lack of access to "Infrastructural Enablers" such as digitally enabled accounts and debit cards.

The analysis utilizes a variety of machine learning classification models to rank feature importance and provide actionable insights for financial institutions and policy makers.

* Target Variable: anydigpayment - the primary metric for this study is whether a respondent has engaged in digital financial activity.

* Explanatory Variables: set of predictors, including demographic traits (such as age, gender, and education), indicators of financial infrastructure (such as account and card ownership), and behavioral factors like internet usage or saving patterns.

## Methodology
#### 1. Data Collection and Preparation
* Feature Selection: removing redundant columns and non-predictive identifiers;
* Data Quality Check: identifying missing values to ensure dataset completeness;
* Binary Recoding: standardizing variables (such as gender and workforce status) into a consistent 0-1 format to facilitate model interpretation;
* Categorical Alignment: re-mapping education levels and financial enablers to ensure correct ordinal relationships and numerical consistency

#### 2. Exploratory data analysis (EDA)
* Target Variable Distribution: visualization of the payment rate to identify class imbalance (~72% vs 28%), justifying the use of weighted scoring in later modeling stages;
* Descriptive statistics for age and categorical feature visualization to observe the frequency of different respondent profiles within the dataset;
* Chi-Square Test of Independence: statistical testing to verify the association between each categorical feature and the target variable;
* Multicollinearity Analysis (VIF): Calculation of the Variance Inflation Factor for all features.

#### 3. Modeling
The modeling strategy focused on comparing different classification architectures to identify the most robust predictors of digital inclusion while handling the identified class imbalance. This included:
* Handling Class Imbalance: implementation of class_weight='balanced' for all models to ensure the minority class (digitally excluded) is accurately represented and penalized during training;
* Logistic Regression with Odds Ratio: evaluation of linear relationships between predictors and digital adoption, utilizing Odds Ratio to quantify the magnitude of impact for each feature;
* Decision Tree: performing a comparison of model accuracy across different tree depths to find the optimal max_depth and building the final tree based on these findings to prevent overfitting;
* Random Forest Ensemble: utilizing an ensemble of trees to capture complex non-linear interactions between demographic and infrastructural features;
* Gradient Boosting: implementation of a sequential boosting algorithm to achieve maximum predictive precision by focusing on correcting errors from previous iterations.

## Results
Evaluation of the models was performed by first calculating statistical metrics (Accuracy, Precision, Recall, F1-score) and then conducting visual diagnostics through confusion matrices, ROC curves, and feature importance plots. To verify the actual influence of specific drivers, permutation importance was utilized across all architectures.

The models were validated using an out-of-sample approach. Performance was evaluated through a diagnostic pipeline:
* Statistical Metrics: calculation of Accuracy, Precision, Recall, and F1-score to assess overall predictive power;
* Confusion Matrices: analysis of classification errors to verify the model's ability to distinguish between digitally active and excluded individuals;
* ROC Curves: visualization of the Trade-off between True Positive and False Positive rates, confirming high model discriminative ability;
* Feature Importance Plots: identification of key drivers using built-in model attributes.

**Model Performance Comparison**

| Model | Accuracy | F1 (0) | F1 (1) | F1 (Macro) | F1 (Weighted) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Decision Tree** | **0.9355** | **0.8831** | **0.9555** | **0.9193** | **0.9358** |
| Random Forest | 0.9296 | 0.8756 | 0.9509 | 0.9132 | 0.9304 |
| Logistic Regression | 0.9271 | 0.8724 | 0.9489 | 0.9107 | 0.9281 |
| Gradient Boosting | 0.9245 | 0.8598 | 0.9483 | 0.9041 | 0.9242 |

*(0 - digitally excluded, 1 - digitally active)

The models achieved high stability across all architectures, with Accuracy and F1-scores exceeding 0.92. The F1-scores for the minority class remain above 0.85, confirming the models' effectiveness in identifying digitally excluded individuals. The near-identical performance of Logistic Regression (AUC 0.9633) and Random Forest (AUC 0.9634) suggests that relationships in this dataset are primarily linear, making simpler, more interpretable models equally effective.

Analysis of feature importance across all architectures reveals that digital account ownership and debit card access are the absolute primary drivers of financial inclusion. Once these infrastructural tools are accounted for, demographic traits such as age, gender, and education show minimal to zero impact on predictive performance. This leads to the conclusion that in high-income economies, digital inclusion is driven by infrastructure availability rather than demographic characteristics. Strategic focus should therefore remain on expanding access to digital banking tools to achieve full financial inclusion.


### Tech Stack
* **Language:** Python
* **Libraries:** Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn, Statsmodels
* **Models:** Logistic Regression, Decision Tree, Random Forest, Gradient Boosting





Author: Katarzyna Kędra

Contact: https://www.linkedin.com/in/katarzyna-k%C4%99dra-20b2a9399/
