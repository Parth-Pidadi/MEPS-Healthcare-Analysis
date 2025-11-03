This project presents a comprehensive analysis of healthcare expenditures, chronic disease prevalence, and mental health patterns in the United States using the Medical Expenditure Panel Survey (MEPS) 2020 Full-Year Consolidated Data File (HC-224). Through a combination of statistical modeling and machine learning techniques, we derive data-driven insights to inform preventive healthcare strategies and promote equitable access to care.

Research Questions
This analysis addresses three key research questions:

RQ1: Healthcare Expenditure Drivers – Which components of medical expenditure most significantly contribute to total annual healthcare spending?
RQ2: Chronic Disease and Demographics – What is the association between demographic factors and chronic disease prevalence?
RQ3: Lifestyle and Psychological Distress – How do lifestyle factors and health behaviors relate to psychological distress?

Dataset

Source: Agency for Healthcare Research and Quality (AHRQ)
File: MEPS HC-224: 2020 Full-Year Consolidated Data File
Sample Size: 27,805 individuals
Variables Selected: 38 out of 1,451 available variables
Categories: Demographics, chronic conditions, behavioral factors, healthcare expenditures, insurance coverage

Key Variables

Expenditure Components: Office-based visits, inpatient care, emergency room, prescription drugs, therapist services
Chronic Conditions: High blood pressure, coronary heart disease, arthritis, diabetes
Behavioral Indicators: Physical activity, sleep quality, smoking frequency, alcohol consumption
Demographics: Age, sex, race, region, family size, education, income

Methodology
RQ1: Expenditure Analysis

Multiple linear regression with log-transformed variables
ANOVA for variance decomposition
XGBoost regression for predictive modeling
Feature importance analysis

RQ2: Chronic Disease Prediction

Logistic regression on full dataset
Random forest classification
Variable importance ranking
Performance metrics: Accuracy, Sensitivity, Specificity

RQ3: Lifestyle and Mental Health

Principal Component Analysis (PCA) for dimensionality reduction
K-means clustering for behavioral profiling
Multiple classification models (Logistic Regression, Random Forest)
ROC curve analysis and AUC comparison

Key Findings
Healthcare Expenditures

Prescription drugs consistently ranked as a top cost driver due to high frequency and cost
Inpatient hospital care showed the largest per-case financial impact despite lower frequency
Office-based doctor visits contributed significantly to total spending due to high utilization

Chronic Disease

Age emerged as the strongest predictor of chronic disease presence
Family size showed a negative association with chronic conditions
Both logistic regression and random forest achieved ~82% classification accuracy

Psychological Distress

Poor sleep quality, low physical activity, and high smoking frequency were strongly associated with elevated distress
Four distinct behavioral clusters identified through PCA and K-means
Logistic regression achieved the highest AUC (0.896) for distress prediction

Repository Structure
├── data/
│   └── meps_2020_hc224.csv          # MEPS 2020 dataset
├── code/
│   ├── analysis.Rmd                  # Main R Markdown analysis file
│   └── helper_functions.R            # Custom R functions
├── output/
│   ├── healthcare_analysis_report.pdf # Final report
│   └── presentation.pptx             # Project presentation
├── figures/
│   └── [visualization outputs]       # Generated plots and charts
├── README.md                         # This file
└── LICENSE                           # License information
Requirements
R Version

R >= 4.0.0

Required Packages
rinstall.packages(c(
  "tidyverse",      # Data manipulation and visualization
  "caret",          # Machine learning framework
  "xgboost",        # Gradient boosting
  "randomForest",   # Random forest models
  "glmnet",         # Regularized regression
  "pROC",           # ROC curve analysis
  "factoextra",     # PCA visualization
  "cluster",        # Clustering algorithms
  "knitr",          # Report generation
  "kableExtra"      # Table formatting
))
Usage

Clone the repository

bashgit clone https://github.com/yourusername/meps-healthcare-analysis.git
cd meps-healthcare-analysis

Download the dataset

Visit MEPS Data Center
Download the HC-224 dataset
Place the file in the data/ directory


Run the analysis

r# Open R/RStudio and set working directory
setwd("path/to/meps-healthcare-analysis")

# Knit the R Markdown file
rmarkdown::render("code/analysis.Rmd")
Results Summary
Research QuestionPrimary MethodKey MetricFindingRQ1: ExpenditureXGBoost RegressionR² = 0.715Prescription drugs and inpatient care are primary cost driversRQ2: Chronic DiseaseRandom ForestAccuracy = 81.6%Age and family size are strongest predictorsRQ3: Mental HealthLogistic RegressionAUC = 0.896Sleep quality and physical activity strongly predict distress
Limitations

Analysis based on single-year (2020) data during COVID-19 pandemic
Self-reported survey data may contain reporting bias
Simplified categorical variables may overlook within-group variations
Binary classification of distress may lose information about severity gradients

Future Work

Extend to multi-year panel analysis for longitudinal trends
Integrate external data sources (EHRs, insurance claims)
Apply advanced hyperparameter tuning techniques
Conduct subgroup analyses by race, age, and geographic region

References

Agency for Healthcare Research and Quality (AHRQ). Medical Expenditure Panel Survey (MEPS) HC-224: 2020 Full Year Consolidated Data File. Link
Karunakaran, R., et al. (2024). Predictive interpretable analytics models for forecasting healthcare expenditures. Health Data Science, 4, 100053.
