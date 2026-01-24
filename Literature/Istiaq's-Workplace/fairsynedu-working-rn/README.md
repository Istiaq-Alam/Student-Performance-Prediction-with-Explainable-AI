Student Performance Prediction

This repository contains the code for the study "Beyond Performance: Explaining and Ensuring Fairness in Student Academic Performance Prediction with Machine Learning" (Appl. Sci. 2020, 10). The notebook implements student performance prediction using the UCI Student Performance dataset, with Logistic Regression, Random Forest, and XGBoost models, SMOTE for class imbalance, fairness analysis via AIF360, and explainability via SHAP and LIME.

Requirements





Python 3.10



Libraries:





pandas==1.5.3



numpy==1.25.2



scikit-learn==1.2.2



xgboost==1.5.0



imbalanced-learn==0.10.1



aif360==0.5.0



shap==0.41.0



lime==0.2.0.1

How to Run





Open student_performance_prediction.ipynb in Google Colab.



Run the first cell to install required libraries.



Execute the remaining cells sequentially to load data, train models, perform fairness analysis, and generate SHAP/LIME visualizations.



Results are saved to model_performance.csv.

Dataset





UCI Student Performance Dataset: https://archive.ics.uci.edu/ml/machine-learning-databases/00320/student-por.csv

Notes





Ensure an internet connection to download the dataset and install libraries.



The notebook is designed to replicate the methodology described in the paper, including hyperparameter tuning, fairness metrics (DP, EO), and explainability.

Citation

If you use this code, please cite: Kesgin, K., Kiraz, S., Kosunalp, S., & Stoycheva, B. (2020). Beyond Performance: Explaining and Ensuring Fairness in Student Academic Performance Prediction with Machine Learning. Applied Sciences, 10.
