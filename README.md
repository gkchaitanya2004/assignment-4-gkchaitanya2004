# 📘 Assignment – GMM-Based Synthetic Sampling for Imbalanced Data

## Name : Krishna Chaitanya
## Roll No :DA25M011

## 📂 Submission \Contents
- `subbmission.ipynb` → The single notebook that contains all code, visualizations, and explanations for this assignment.

## 📌 Overview

This project explores different resampling strategies to handle class imbalance in credit card fraud detection. Since fraudulent transactions make up only a tiny fraction of the dataset, traditional models tend to achieve very high accuracy by predicting almost everything as “non-fraud.” However, such models fail to catch actual fraud cases. 

To address this issue I compared performance of a Logistic Regression classifier on four different training sets: the original imbalanced data, data balanced using Gaussian Mixture Model method (GMM) and data balanced using a clustering-based undersampling + GMM approach (CBU) and evaluate them using metrics that are robust to imbalance (Precision, Recall, and F1-score).

## Approach 

### Model-1 : Baseline Model
- Trained and **Logistic Regression Model** on the imbalanced dataset by spiltting data into train and test (mainting class imbalance as it is) using `train_test_split` from **sklearn** library.
- Achieved high accuracy, but relatively low precision and recall.

### Model-2 : GMM Model
- Resample minority class data using `GMM` from **sklearn** library python which generated synthetic minority samples
- This boosted recall significantly but reduce precision due to addition of **false positives**.

### Model-3 : Clustering-Based Undersampling (CBU) + GMM Approach
- 

## 📊 Results
| Method       | Accuracy | Precision | Recall | F1 Score |
|--------------|----------|-----------|--------|----------|
| **Baseline** | 1        | 0.83      | 0.64   | 0.72     |
| **SMOTE**    | 0.97     | 0.06      | 0.88   | 0.11     |
| **CBO**      | 0.99     | 0.09      | 0.88   | 0.17     |
| **GMM**      | 0.982    | 0.08      | 0.89   | 0.14     |
| **CBU+GMM**  | 0.972    | 0.05      | 0.89   | 0.1      |


## Conclusion

#### Which method performed the best?

- For **credit card** fraud the most important metric isnt accuracy its **recall**.

    - It is acceptable if we flagged a **non-fraud** transaction to **fraud** (not everytime) 

    - But we must avoid flagging a fraud transaction as non-fraud since that leads to financial loss.

- Therefore, we care about catching as many fraud cases as possible. So recall should be high

- In the **baseline** model although accuracy is `high` recall is `low` risk of not identifying a fradulent transaction

- However **GMM**,**GMM+CBU** have maximum recall followed by **CBO and SMOTE**. 

- Between these, GMM stands out:
    - It has **high recall** like  and GMM+CBU.
    - But unlike them, it also achieves **better precision**, meaning it is better at identifying which transactions are actually fraud.

- **Conclusion:** Overall **GMM** is a best resampling strategy that the company should adopt as it balances high recall with relatively stronger precision compared to other techniques
