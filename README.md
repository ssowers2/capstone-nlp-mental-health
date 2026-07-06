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

## Results

...

## References

...

## Project Progress

- [x] Repository created
- [x] Development environment configured
- [x] Dataset selected
- [ ] Merge datasets
- [ ] Data validation
- [ ] Text preprocessing
- [ ] Exploratory Data Analysis
- [ ] Feature engineering
- [ ] Logistic Regression
- [ ] Naïve Bayes
- [ ] Random Forest (optional)
- [ ] Model evaluation
- [ ] Final paper
- [ ] Final presentation


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
