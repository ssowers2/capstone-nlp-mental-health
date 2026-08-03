# Methodology

## Data Preparation

The original dataset contained three files representing Neutral, Depression, and Suicidal Tendencies posts. The files were validated, cleaned, and merged into a single dataset.

## Text Preprocessing

Text was normalized, repaired, tokenized, lemmatized, and filtered to remove noise while preserving meaningful negation terms.

## Feature Engineering

The final processed text was converted into TF-IDF features. The dataset was divided into 80% training data and 20% testing data using stratified sampling.

## Predictive Modeling

Four supervised machine learning models were trained:

- Logistic Regression
- Multinomial Naïve Bayes
- Linear Support Vector Machine
- Random Forest

Each model was evaluated using accuracy, weighted precision, weighted recall, and weighted F1-score.
