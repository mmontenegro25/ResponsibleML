
# 📝 Model Card: Lending Bias-Remediated Model

## Intended Use

- **Business Value**:  
  Our group's best remediated model assists mortgage lenders in making more equitable decisions about loan pricing by predicting whether a loan is high-priced, while minimizing demographic biases across race, gender, and age categories.

- **Designed Use**:  
  The model predicts whether an applicant would receive a high-priced loan, allowing the lender to monitor disparities, detect potential fairness violations, and adjust practices to promote compliance and equity.

- **Intended Users**:  
  Mortgage risk analysts, compliance officers, fair lending auditors, and regulatory reporting teams.

- **Additional Purposes**:  
  This model should not be used for final loan approval decisions, criminal justice predictions, insurance assessments, or employment-related evaluations without retraining and thorough validation for new use cases.

## Training Data

- **Source of Training Data**:  
  Preprocessed historical mortgage lending records from the Home Mortgage Disclosure Act (HMDA) datasets.

- **Training/Validation Split**:  
  70% of the data was used for training, and 30% for validation.

- **Number of Rows**:  
  - Training data: 160,338 rows  
  - Validation data: 19,831 rows

- **Meaning of Training Columns**:  
  - `loan_amount`: The dollar amount of the loan applied for.  
  - `income`: Applicant's income level.  
  - `debt_to_income_ratio`: The ratio of the applicant’s debts to their income.  
  - `property_value`: The appraised value of the property.  
  - `interest_rate`: The mortgage interest rate offered.  
  - (plus additional financial risk features.)

- **Meaning of Engineered Columns**:  
  - Engineered columns such as `income_to_loan_ratio` were used where appropriate.  
  - Protected demographic attributes were isolated and excluded from model training to support fairness objectives.

## Model Details

- **Inputs (Features)**:  
  - `loan_amount`  
  - `income`  
  - `debt_to_income_ratio`  
  - `property_value`  
  - `interest_rate`  
  - (Other non-demographic financial indicators.)

- **Target (Label)**:  
  - `high_priced` — a binary label indicating whether the applicant received a high-priced mortgage loan.

- **Model Type**:  
  - Generalized Linear Model (GLM) built using H2O.ai's `H2OGeneralizedLinearEstimator` (logistic regression for binary classification).

- **Software Used**:  
  - h2o package (H2O-3)  
  - Python 3 environment  
  - Scikit-learn (`sklearn`) for evaluation metrics (e.g., AUC)

- **Version Details**:  
  - H2O.ai likely version 3.32.x or 3.34.x  
  - Scikit-learn version approximately 1.1.x or 1.2.x

- **Hyperparameters/Settings**:  
  - Default GLM settings initially.  
  - Remediation involved excluding protected features and using post-processing fairness techniques rather than hyperparameter tuning.

## Opportunities for Future Analysis

- **Segment-Level Lifetime Value (CLV) Estimation**:  
  Predict long-term revenue contributions of different customer segments for more targeted acquisition and retention strategies.

- **Channel Attribution and Conversion Path Analysis**:  
  Determine which customer touchpoints contribute most to conversions, helping to optimize marketing spend.

- **Customer Churn Prediction**:  
  Build models to identify and engage at-risk customers before they leave, using RFM patterns and engagement data.

- **A/B Testing of Personalization Strategies**:  
  Validate which interventions (e.g., personalized bundles, offers) truly move the needle on conversion or retention.

- **Demographic and Psychographic Profiling**:  
  Enrich behavioral data with demographics and motivations for even more accurate segmentation and targeting.

- **Real-Time Personalization Engines**:  
  Use live data feeds to adjust recommendations and offers dynamically based on user behavior.

- **Geographic and Regional Spend Trends**:  
  Analyze spend behavior by location to better localize promotions and predict market-specific performance.
