# Kepler's Objects of Interest Classification

## Overview
This project focuses on analyzing the Cumulative Kepler Objects of Interest (KOIs) dataset from the National Aeronautics and Space Administration Exoplanet Archive. The primary goal is to train machine learning models—specifically Logistic Regression and XGBoost—to accurately predict whether these celestial objects are confirmed planets, candidates, or false positives.

## Dataset
The data originates from the Kepler mission, which was launched in 2009 to survey a region of our galaxy and determine which stars host planets. The target variable for this analysis is `koi_disposition`, which categorizes the objects into three classes:
* **CANDIDATE** (Encoded numerically as 0)
* **CONFIRMED** (Encoded numerically as 1)
* **FALSE POSITIVE** (Encoded numerically as 2)

The dataset exhibits a class imbalance, with 'False Positive' being the majority class (representing 50.59% of the distribution). This imbalance was accounted for during the model training process.

## Data Preparation and Feature Engineering
* **Feature Selection:** 22 features were manually selected based on the dataset documentation. These include vetting flags, transit and fit parameters, strength/detection statistics, and stellar parameters.
* **Handling Missing Data:** The data was checked for missing values, and sixteen columns containing missing values were imputed using the median.
* **Target Encoding:** The categorical target variable was numerically encoded for model compatibility. Checks confirmed that no missing values were present in the initial target column.

## Methodology
Two primary models were trained and evaluated:
* **Logistic Regression:** Served as an effective baseline that demonstrated an initial ability to capture the underlying relationships between the features and target variable. A coefficient heatmap was also plotted to analyze feature suitability.
* **XGBoost:** Selected for further parameter tuning and optimization due to its superior baseline performance and ability to handle complex, non-linear relationships.

## Results and Conclusion
* Both baseline models performed well without overfitting the data, indicating good generalization capabilities.
* After parameter tuning, the optimized XGBoost model achieved the best overall results and successfully captured most of the complex relationships present in the data.
* Despite overall performance improvements, confusion matrices revealed some persistent overlap and confusion between the 'Candidate' and 'Confirmed' classes, highlighting the inherent difficulty in distinguishing between the two based solely on transit data.

## Repository Files
* `Keplers objects of interest analysis code.ipynb`: The Jupyter Notebook containing the data ingestion pipeline, feature selection, preprocessing, and the training/evaluation of the Logistic Regression and XGBoost classifiers.
* `Kepler's objects of interest report.pdf`: A comprehensive report detailing the project's background, exploratory data analysis, class distributions, methodology, and final conclusions.
