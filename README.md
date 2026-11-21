\# Academic Performance Prediction



Predicting whether a US high-school student reports mostly A/B or mostly C/D/F grades

from alcohol/substance use, lifestyle, health and demographic survey answers.



\## Data

CDC 2023 national Youth Risk Behavior Survey (YRBS), https://www.cdc.gov/yrbs/data/index.html

\- \~20,000 responses, 107 questions; 18 features + 1 target used

\- Target: Q87 (self-reported grades). 1 = mostly A/B, 0 = mostly C/D/F.

&#x20; "Not sure", "None of these grades" and missing values removed resulted in 8,953 students

\- Substance-use answers recoded to binary (any use / no use)



\## Method

\- Stratified 70/15/15 train/validation/test split (6,267 / 1,343 / 1,343)

\- Logistic regression (standardized features, log loss)

\- Decision tree (depth chosen by validation accuracy, depth 4, entropy criterion)



\## Results

| Model 		| Train | Validation | Test |

| Logistic regression | 75.27% | 74.83% | 75.06% |

| Decision tree 	| 75.03% | 74.54% | 74.09% |



The majority-class baseline (always predict A/B) gets 74.09% on the test set, so both models

are only marginally better. Logistic regression correctly identifies 44 of 348 lower-grade

students (recall 12.6%). Accuracy hides weak performance on the minority class, and the results

should not be read as evidence that substance use predicts grades.



\## Limitations / next steps

\- Class imbalance; report precision/recall/F1 and try class weighting

\- Only a subset of survey questions and survey weights not used

\- Self-reported grades



\## Run

pip install -r requirements.txt

jupyter notebook

