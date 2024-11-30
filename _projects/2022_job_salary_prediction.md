---
layout: project
title: Job Salary Prediction
subtitle: "A machine learning intervention to predict job salary through description "
---

# Job Salary Prediction System

## **Problem Statement**
In today's job market, understanding the potential salary of a position based on its attributes is a time-consuming and inefficient process. Job seekers often struggle to compare salaries for similar titles across different job portals, leading to unrealistic expectations and missed opportunities. This project addresses these challenges by creating a system to:
1. Predict whether a job salary falls into a higher or lower range.
2. Quantify the salary based on various attributes like job title, location, and contract type.
3. Analyze geographical salary trends and extract insights from job descriptions using text mining techniques.

---

## **Research Questions**
The project aims to answer:
- What is the salary of a particular profession based on location in the UK?
- How is the median salary distributed across UK counties?
- What are the most frequent parts of speech in job descriptions?
- How does text preprocessing (stopword removal, lemmatization) affect model accuracy?
- Which features are most predictive of salary?

---

## **Dataset Description**
- **Source:** Adzuna Job Board dataset, available on Kaggle.
- **Size:** 195,814 rows (subsampled to 60,000 rows for training and 20,000 rows for testing).
- **Features:**
  - `Id`: Unique identifier for each job ad.
  - `Title`: Job title or role summary.
  - `FullDescription`: Job description (text-based).
  - `LocationNormalized`: Normalized job location.
  - `ContractType`: Full-time or part-time.
  - `ContractTime`: Permanent or contract roles.
  - `SalaryNormalized`: Annualized salary (target variable).

---

## **Workflow**

### **1. Regression Analysis**
- Predicts normalized salaries using structured features.
- **Steps:**
  1. **Exploratory Data Analysis (EDA):**
     - Visualized salary distributions using histograms and KDE plots.
     - Analyzed geographical salary trends using Tableau.
  2. **Feature Engineering:**
     - Converted categorical variables into numeric values.
     - Created flags for "high-cost cities" and other relevant binary features.
  3. **Modeling:**
     - Implemented Random Forest, SVM, Decision Tree, and Lasso regression models.
     - Used Mean Squared Error (MSE), R-score, and Adjusted R-score as evaluation metrics.
  4. **Hyperparameter Tuning:**
     - Optimized the Random Forest model using RandomizedSearchCV.

---

### **2. Classification Analysis**
- Predicts whether a salary is in the higher or lower range.
- **Scenarios:**
  1. **Without Job Descriptions:**
     - Used features like `ContractType`, `ContractTime`, and `Category`.
     - Applied Bernoulli Naive Bayes for classification.
  2. **With Job Descriptions:**
     - Performed text preprocessing (stemming, tokenization, lemmatization).
     - Implemented Bag-of-Words (CountVectorizer) for feature extraction.
     - Classified using Multinomial Naive Bayes.
     - Compared accuracy with and without text preprocessing.

---

## **Descriptive Analytics**
- **Text Mining:**
  - Parts-of-speech (POS) tagging revealed nouns, adjectives, and verbs as dominant categories.
  - Created word clouds to identify the most frequent words in job descriptions.
  - Explored the impact of stopword removal and lemmatization on word distributions.

- **Geographical Analysis:**
  - Found higher median salaries in regions like London, South-East England, and North-East England.
  - Lower salaries observed in regions like Powys and Falkirk.

---

## **Results**

### **Regression Models**
| Model                   | MSE      | R-Score | Adjusted R-Score |
|-------------------------|----------|---------|------------------|
| Random Forest Regressor | 7048.91  | 0.8373  | 0.8371           |
| Decision Tree Regressor | 9707.56  | 0.6915  | 0.6910           |
| SVM Regressor           | 17608.69 | -0.0147 | -0.0164          |
| Lasso Regularization    | 16078.42 | 0.1539  | 0.1525           |

- Random Forest performed the best, with the lowest MSE and highest R-score.
- Feature importance analysis showed `SourceName` and `Title` as the most influential features.

### **Classification Models**
| Scenario                              | Accuracy  |
|---------------------------------------|-----------|
| Without job description               | 75.3%     |
| With job description (stopwords kept) | Higher    |
| With job description (lemmatized)     | Highest   |

- Text-based models outperformed models without job descriptions, highlighting the value of NLP techniques.

---

## **Tools and Technologies**
- **Programming Language:** Python
- **Libraries:** Pandas, Numpy, Scikit-learn, NLTK, Matplotlib, Tableau
- **Machine Learning Models:** Random Forest, Decision Tree, SVM, Lasso, Multinomial/Bernoulli Naive Bayes
- **Visualization Tools:** Tableau, WordCloud
- **NLP Techniques:** Tokenization, Stemming, Lemmatization, POS Tagging

---

## **Discussion and Future Scope**
- **Discussion:**
  - Achieved a robust prediction system for job salaries based on both structured and unstructured data.
  - Leveraged NLP techniques to extract valuable insights from job descriptions.
  - Demonstrated the importance of geographical and categorical features in salary prediction.

- **Future Scope:**
  - Explore additional classifiers like XGBoost or deep learning models for better performance.
  - Implement sentiment analysis on job descriptions for added insights.
  - Use N-grams and TF-IDF for more sophisticated text vectorization.
  - Extend to real-time data from job portals like LinkedIn or Glassdoor using APIs.

---

## **References**
1. [Kaggle: Adzuna Job Salary Prediction](https://www.kaggle.com/c/job-salary-prediction-lkm)
2. [Exploratory Data Analysis](https://towardsdatascience.com/exploratory-data-analysis-8fc1cb20fd15)
3. [Feature Engineering](https://www.heavy.ai/technical-glossary/feature-engineering)
4. [Hyperparameter Tuning](https://neptune.ai/blog/hyperparameter-tuning-in-python-complete-guide)
5. [Feature Importance](https://towardsdatascience.com/understanding-feature-importance-and-how-to-implement-it-in-python-ff0287b20285)
6. [Penn Treebank POS Tags](https://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html)

