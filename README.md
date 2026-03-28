# LoanTap Credit Risk Analysis (Industry : Digital Lending / Finance)
This project explores LoanTap's borrower data to analyze patterns influencing personal loan repayment and defaults, focusing on demographic, financial, and credit behavior attributes.

# Project Overview
This project examines LoanTap's underwriting data to uncover how borrower characteristics (like credit grade, home ownership, employment, and location) impact the likelihood of loan default. It aims to answer key questions such as: Which job titles are most reliable? How do credit grades affect repayment? The insights and predictive models derived will help LoanTap strengthen its underwriting framework, scale lending responsibly, and minimize non-performing assets (NPAs) while maximizing profitable lending opportunities.

# Problem Statement
LoanTap needs to systematically determine if a credit line should be extended to an individual based on their attributes. The objective is to build a robust Logistic Regression model to predict whether a borrower will fully repay or default (charge-off) on a Personal Loan. Furthermore, the project aims to optimize the precision-recall tradeoff to reduce financial losses from defaults without wrongly rejecting genuine, creditworthy customers.

# Objectives
 * Analyze borrower demographic, financial, and credit data to identify patterns driving repayment and default risk.
 * Perform comprehensive exploratory data analysis, handle missing values, cap outliers, and engineer new features (e.g., extracting geographical data from addresses).
 * Build and evaluate Logistic Regression models to predict loan status, utilizing metrics like ROC-AUC, Precision, Recall, and F1-score.
 * Address the high class imbalance using techniques like Class Weights and SMOTE.
 * Optimize the probability threshold to balance the precision-recall tradeoff per the bank's risk appetite.
 * Provide actionable business recommendations on credit approval strategies.

# Data Set
 * loan_amnt: The listed amount of the loan applied for by the borrower.
 * term: The number of payments on the loan (36 or 60 months).
 * int_rate: Interest Rate on the loan.
 * installment: The monthly payment owed by the borrower.
 * grade & sub_grade: LoanTap assigned loan grades.
 * emp_title: The job title supplied by the Borrower.
 * emp_length: Employment length in years (0 to 10+).
 * home_ownership: Home ownership status (e.g., Rent, Mortgage, Own).
 * annual_inc: Self-reported annual income.
 * verification_status: Indicates if income was verified.
 * issue_d: The month which the loan was funded.
 * loan_status: Current status of the loan (Target Variable).
 * purpose & title: Category and title for the loan request.
 * dti: Debt-to-income ratio.
 * earliest_cr_line: Month the earliest reported credit line was opened.
 * open_acc & total_acc: Number of open credit lines and total credit lines.
 * pub_rec & pub_rec_bankruptcies: Number of derogatory public records and bankruptcies.
 * revol_bal & revol_util: Total credit revolving balance and utilization rate.
 * initial_list_status: Initial listing status (W, F).
 * application_type: Individual or joint application.
 * mort_acc: Number of mortgage accounts.
 * Address: Address of the individual.

# Milestones
 * Loaded and inspected the dataset (396,030 records, 27 columns).
 * Checked data quality: No duplicates found; missing values in mort_acc, emp_title, emp_length, etc., were imputed using median and mode strategies.
 * Conducted outlier treatment using 95th percentile capping for features like annual_inc, revol_bal, and installment.
 * Engineered new features by extracting state, zip_code, issue_month, issue_year, and earliest_cr_line_year from datetime and text columns.
 * Performed Label Encoding and One-Hot Encoding on categorical variables, expanding the dataset to 57 columns.
 * Split the data into Train (60%), Validation (20%), and Test (20%) sets, and applied MinMaxScaler.
 * Trained multiple Logistic Regression models: Base Model, Class-Weighted Model, and SMOTE Model.
 * Evaluated models using Confusion Matrices, ROC-AUC, and Precision-Recall curves.
 * Optimized the classification threshold (0.51) for the Class-Weighted model to favor high precision.
 * Extracted and visualized feature importances to determine key default drivers.

# Findings
 * The dataset is highly imbalanced: 80.39% of loans are "Fully Paid" and 19.61% are "Charged Off".
 * There is a highly positive correlation (0.95) between the loan amount and the monthly installment.
 * Charged-off loans generally feature higher median loan amounts (14,000 vs 12,000), higher interest rates (15.61% vs 12.99%), and higher Debt-to-Income (DTI) ratios.
 * Borrowers who successfully fully pay their loans tend to have higher median annual incomes (65,000 vs 59,000).
 * Credit Grade is a strong predictor: Grade 'A' has the highest proportion of fully paid loans, while Grade 'G' has the highest proportion of charged-off loans.
 * Homeownership impacts repayment: Borrowers with a "MORTGAGE" are most likely to fully pay, whereas those who "RENT" have the highest proportion of charged-off loans.
 * The Class Weight Logistic Regression Model, when adjusted to a threshold of 0.51, proved to be the most robust on test data, yielding an Accuracy of 80%, Precision of 95%, Recall of 80%, and an F1 Score of 0.86.
 * Geographical location heavily dictates the outcome; multiple specific zip_code features ranked as the absolute highest in feature importance.

# Recommendations
 * **Focus on High-Reliability Job Titles:** Target marketing and favorable terms toward specific professions, such as Teachers and Managers, who exhibit the highest historical loan repayment ratios.
 * **Prioritize 36-Month Terms:** Continue heavily promoting 36-month loan terms, as they align well with successful borrower repayment patterns compared to 60-month terms.
 * **Leverage Credit Grades Heavily:** Use the assigned credit grades as strict underwriting gates; offer the most competitive terms to Grade A/B borrowers and apply strict scrutiny or higher interest rates to lower grades.
 * **Factor in Home Ownership:** Give underwriting preference or slightly better rates to applicants with Mortgages or who Own their homes, as they demonstrate better financial stability than renters.
 * **Geographic Risk Profiling:** Integrate geographical data (Zip Codes) into dynamic credit pricing to mitigate risks associated with regional economic variability.
 * **Deploy the Precision-Optimized Model:** Implement the Class-Weighted Logistic Regression model with the 0.51 threshold to heavily minimize false positives, directly answering the business need to avoid costly NPAs.

# Colab Link :
 * https://colab.research.google.com/drive/1l55B0ofvx5wx_4evkDKbwS2qsGBJOkYP

# Data Link :
 * https://drive.google.com/file/d/1HEWuh-tZ9skrDJ2A9UCVIlqSBDrVR72R/view?usp=drive_link
