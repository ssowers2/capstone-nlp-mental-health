# Project Workflow

This project follows an end-to-end Natural Language Processing and machine learning workflow.

## 1. Data Validation and Preparation

- Load the three source datasets
- Validate columns, data types, missing values, and duplicates
- Resolve encoding issues
- Merge the datasets
- Export the cleaned dataset

## 2. Text Preprocessing

- Repair text encoding artifacts
- Remove URLs, email addresses, mentions, HTML, and editorial markers
- Convert text to lowercase
- Replace numeric values with a common token
- Remove punctuation and normalize whitespace
- Tokenize and lemmatize text
- Remove stop words while preserving negation terms

## 3. Exploratory Data Analysis

- Review class distributions
- Analyze text length
- Examine frequent words
- Analyze bigrams
- Create selected visualizations

## 4. Feature Engineering

- Split the data into training and testing subsets
- Apply TF-IDF vectorization
- Preserve the fitted vectorizer for reuse

## 5. Predictive Modeling

- Train Logistic Regression
- Train Multinomial Naïve Bayes
- Train Linear Support Vector Machine
- Train Random Forest
- Compare model performance

## 6. Interpretation of Results

- Compare accuracy, precision, recall, and F1-score
- Create model performance charts
- Review the confusion matrix
- Interpret class-level strengths and weaknesses
- Select the final model
