# Mental Health Text Classification Using Natural Language Processing

[![Python 3.14+](https://img.shields.io/badge/python-3.14%2B-blue?logo=python)](#)
[![MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](./LICENSE)

> Capstone project for the Master of Science in Data Analytics at Northwest Missouri State University.

## Project Overview

This capstone project applies Natural Language Processing (NLP) and supervised machine learning techniques to classify social media text into one of three categories:

- Neutral
- Depression
- Suicidal Tendencies

The project evaluates multiple machine learning classification models to determine how effectively text can be categorized based on linguistic patterns. The goal is to demonstrate how data analytics and NLP can support mental health research while recognizing that machine learning should supplement—not replace—professional clinical evaluation.

## Dataset

The project uses the Suicide Sentiment Analysis Dataset available through Kaggle.

The original dataset contains three CSV files representing:

- Neutral
- Depression
- Suicidal Tendencies

The datasets are merged into a single processed dataset prior to analysis.

The merged dataset contains two primary attributes: TEXT (social media text) and LABEL (0 = Neutral, 1 = Depression, 2 = Suicidal Tendencies).

Source:
<https://www.kaggle.com/datasets/umar1103/suicide-sentiment-analysis-dataset>

The CSV files required the latin1 encoding during import due to character encoding differences in the original dataset.

## Project Structure

```text
data/
├── raw/
├── processed/
├── docs/
├── notebooks/
├── src/
└── README.md
```

## Technologies

- Python
- Jupyter Notebooks
- pandas
- NumPy
- matplotlib
- scikit-learn
- NLTK / spaCy (if used)
- Git
- GitHub

## Project Workflow

1. Data collection
2. Data validation
3. Text preprocessing
4. Exploratory data analysis
5. Feature engineering
6. Model development
7. Model evaluation
8. Results and conclusions

## Repository Contents

- data/raw/ – Original Kaggle datasets
- data/processed/ – Processed datasets
- notebooks/ – Jupyter notebooks
- src/ – Python source code
- docs/ – Supporting documentation

## Project Progress

- [x] Repository created
- [x] Development environment configured
- [x] Dataset selected
- [x] Merge datasets
- [x] Data validation
- [x] Text preprocessing
- [ ] Exploratory Data Analysis
- [ ] Feature engineering
- [ ] Logistic Regression
- [ ] Naïve Bayes
- [ ] Random Forest (optional)
- [ ] Model evaluation
- [ ] Final paper
- [ ] Final presentation

## Data Preparation

The original Kaggle dataset consisted of three separate CSV files representing the three classification categories:

- Neutral
- Depression
- Suicidal Tendencies

The datasets were imported into Python using pandas and validated prior to merging. The following data preparation steps were completed:

- Loaded all three CSV datasets into separate pandas DataFrames.
- Resolved a character encoding issue by importing the files using the `latin1` encoding.
- Validated dataset dimensions, column names, and data types.
- Removed an unnecessary `Unnamed: 2` column from the Depression dataset that resulted from the original file export.
- Filled missing label values in the Neutral dataset with the appropriate class label (0).
- Removed records containing missing text values because they cannot be used for NLP classification.
- Merged the three datasets into a single dataset.
- Verified the final class distribution after cleaning.
- Saved the cleaned dataset to `data/processed/mental_health_text_dataset.csv`.

### Data Quality Observations

During validation, a small number of records contained character encoding artifacts (for example, malformed characters such as `Ã`). Most affected records remained readable and will be addressed during the text preprocessing phase. Severely corrupted or non-English records will be evaluated for removal if they do not contribute meaningful information to the English-language classification models.

The final cleaned dataset contains:

- **17,699 records**
- **2 attributes**
  - `Label` (target variable)
  - `TEXT` (social media text)

# Data Cleaning and Preprocessing

## Data Validation and Cleaning

The original dataset consisted of three CSV files representing the **Neutral**, **Depression**, and **Suicidal Tendencies** classes. Each dataset was inspected to validate its structure, including:

- Column names
- Data types
- Record counts
- Missing values
- Duplicate records

Data cleaning included:

- Removed the unnecessary `Unnamed: 2` column from the Depression dataset.
- Imported the datasets using the `latin1` encoding to address character encoding inconsistencies.
- Assigned missing labels in the Neutral dataset to the Neutral class (`0`).
- Removed records containing missing text values.
- Merged the three datasets into a single cleaned dataset.
- Exported the cleaned dataset for preprocessing.

**Cleaned dataset size:** **17,699 records**

---

## Text Preprocessing

The cleaned dataset underwent several preprocessing steps to prepare the text for Natural Language Processing (NLP) and machine learning.

Preprocessing included:

- Removed conflicting duplicate records with inconsistent class labels.
- Removed duplicate records with identical text and labels.
- Repaired character encoding artifacts using the **ftfy** Python library.
- Removed HTML tags, URLs, email addresses, user mentions, and common social media editorial markers.
- Converted text to lowercase.
- Replaced numeric values with a common `number` token.
- Removed punctuation.
- Standardized whitespace.
- Tokenized and lemmatized text using the **spaCy** Python library.
- Removed stop words while preserving important negation terms such as *no*, *not*, and *never*.
- Removed records containing no meaningful processed text.

The final processed dataset contains **15,774 records** and serves as the input for exploratory data analysis, feature engineering, and machine learning model development.

---

## Development Guide

### Initial Setup (One-Time)

```shell
# Updates the uv tool itself
uv self update

# Pins the project to Python 3.14 by creating/updating the .python-version file.
# If Python 3.14 isn't installed, uv can install it.
uv python pin 3.14

# It creates the .venv virtual environment (if it doesn't already exist).
# Installs all project dependencies from pyproject.toml.
# Installs the development and documentation dependencies.
# Updates packages if newer compatible versions are available.
uv sync --extra dev --extra docs --upgrade //

uvx pre-commit install
uvx pre-commit run --all-files
```

### Daily Workflow

1. Open VS Code.
2. Open the project folder.
3. Open a terminal.
4. Pull the latest changes (if applicable):

```shell
git pull
```

5. Open the notebook or Python file.
6. Select the `.venv` kernel in Jupyter.
7. Run your code.
8. Save your work.

### Before Committing

Format and lint your code:

```shell
uv run ruff format .
uv run ruff check . --fix
```

### Commit Changes

```shell
git add -A
git commit -m "Describe your changes"
git push
```

### Running Python Modules

```shell
uv run python -m <module_name>
```

### Running Jupyter Notebooks

- Open the notebook.
- Select the project's `.venv` kernel.
- Click **Run All**.

### Updating Dependencies

```shell
uv sync
```

## Git Troubleshooting

### Accidentally Pushed to the Wrong GitHub Repository

If you clone an existing project to use as a template, Git will continue pointing to the original GitHub repository until the remote is changed.

#### Check the current remote

```shell
git remote -v
```

Example:

```text
origin  https://github.com/ssowers2/capstone-nlp-mental-health.git (fetch)
origin  https://github.com/ssowers2/capstone-nlp-mental-health.git (push)
```

#### Change the remote to a new GitHub repository

```shell
git remote set-url origin https://github.com/ssowers2/capstone-nlp-mental-health.git
git remote -v
git push -u origin main
```

### Restore an Existing Repository

If changes were accidentally pushed to the wrong GitHub repository, restore it from a clean local copy.

Verify you are in the correct local project folder:

```shell
git remote -v
git status
```

If everything looks correct, overwrite the GitHub repository with your local version:

```shell
git push --force
```

**Only use `--force` when you intentionally want your local repository to replace the GitHub version.**

### Large Dataset Won't Commit

If Git blocks large raw datasets, keep them locally and ignore them.

Add to `.gitignore`:

```text
data/raw/
```

Remove the files from Git tracking (they remain on your computer):

```shell
git rm --cached data/raw/Neutral.csv
git rm --cached data/raw/Depression.csv
git rm --cached data/raw/Suicadal_tendencies_data.csv
```

Then commit normally.

### Useful Git Commands

Check repository status:

```shell
git status
```

Check commit history:

```shell
git log --oneline
```

Check the connected GitHub repository:

```shell
git remote -v
```
