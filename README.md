# Photovoltaic Power Prediction Using Random Forest

## Project Overview

This project analyzes photovoltaic power generation data and develops a machine learning model using Random Forest.

The available data contains photovoltaic power generation and weather-related measurements collected across four seasonal datasets:

- Spring 2022-2023

The project will first perform Exploratory Data Analysis (EDA) on all four datasets before selecting the dataset to be used for machine learning.

The main target variable is:

`Active_Power`

The weather-related variables are potential input features for the model.

---

## Project Objective

The project aims to:

1. Understand the structure and characteristics of the four photovoltaic datasets.
2. Evaluate data quality.
3. Identify missing and invalid values.
4. Analyze the relationship between weather conditions and photovoltaic power generation.
5. Compare the four seasonal datasets.
6. Select a dataset based on objective EDA findings.
7. Prepare the selected dataset for machine learning.
8. Develop a Random Forest model.
9. Evaluate model performance.
10. Analyze feature importance.

---

## Current Project Stage

The project is currently in the **Exploratory Data Analysis (EDA)** stage.

The four datasets have NOT been selected yet.

Therefore, the current priority is to analyze and compare all four datasets objectively.

Do not perform final dataset selection before the EDA has been completed.

---

## Dataset Structure

Each dataset contains photovoltaic power generation and weather measurements.

Expected variables include:

- `timestamp`
- `Active_Power`
- `Wind_Speed`
- `Weather_Temperature_Celsius`
- `Global_Horizontal_Radiation`
- `Wind_Direction`
- `Weather_Daily_Rainfall`
- `Max_Wind_Speed`
- `Air_Pressure`
- `Hail_Accumulation`

`Active_Power` is currently considered the target variable for the planned Random Forest regression task.

This assumption must be validated against the project requirements before final modeling.

---

## Dataset Organization

Raw datasets must be stored in:

```text
data/raw/
```

Expected files:

```text
data/raw/
├── Photovoltaic spring 2022-2023.csv
├── Photovoltaic summer 2022-2023.csv
├── Photovoltaic autumn 2022-2023.csv
└── Photovoltaic winter 2022-2023.csv
```

Processed datasets should be stored separately in:

```text
data/processed/
```

Never overwrite the original raw datasets.

---

## Notebook Organization

The project uses Jupyter Notebook through VS Code.

Current notebook:

```text
notebooks/01_eda.ipynb
```

Planned notebooks:

```text
notebooks/
├── 01_eda.ipynb
├── 02_data_preprocessing.ipynb
├── 03_random_forest.ipynb
└── 04_model_evaluation.ipynb
```

Additional notebooks may be created if the project becomes more complex.

---

## EDA Workflow

The initial EDA should follow this order:

```text
Load Dataset
      ↓
Dataset Overview
      ↓
Data Type Check
      ↓
Missing Value Check
      ↓
Duplicate Check
      ↓
Invalid Value Check
      ↓
Constant Feature Check
      ↓
Timestamp Analysis
      ↓
Descriptive Statistics
      ↓
Target Variable Analysis
      ↓
Feature Analysis
      ↓
Correlation Analysis
      ↓
Dataset Comparison
      ↓
EDA Findings
      ↓
Dataset Selection
```

---

## EDA Requirements

The initial EDA should investigate:

### Dataset Overview

Check:

- number of rows
- number of columns
- column names
- data types
- sample records

### Data Quality

Check:

- missing values
- duplicate rows
- invalid values
- extreme values
- constant features

Do not automatically remove problematic values without understanding their meaning.

### Timestamp

Check:

- timestamp format
- date range
- sampling interval
- possible time-related patterns

Timestamp formats may differ between datasets.

Do not assume that all timestamp columns use the same format.

### Target Variable

Analyze:

`Active_Power`

Recommended analysis:

- descriptive statistics
- histogram
- boxplot
- time-series plot
- minimum and maximum values
- distribution characteristics

### Feature Analysis

Analyze the available weather variables.

Particular attention should be given to:

`Global_Horizontal_Radiation`

because solar radiation is physically related to photovoltaic power generation.

### Correlation Analysis

Analyze:

- correlation matrix
- correlation between numerical features and `Active_Power`
- relationship between `Global_Horizontal_Radiation` and `Active_Power`

Correlation must not be interpreted as proof of causation.

---

## Dataset Selection

Dataset selection must be based on EDA findings.

Possible considerations include:

- data completeness
- number of valid observations
- missing-value percentage
- invalid measurement frequency
- target distribution
- feature variation
- relationship between features and target
- temporal coverage
- suitability for the intended Random Forest task

Do not select a dataset simply because it has:

- the most rows
- the highest correlation
- the highest target value
- the lowest missing value

The final decision should consider multiple characteristics together.

---

## Machine Learning Plan

The current planned task is Random Forest regression.

Target:

```text
Active_Power
```

Potential features:

```text
Wind_Speed
Weather_Temperature_Celsius
Global_Horizontal_Radiation
Wind_Direction
Weather_Daily_Rainfall
Max_Wind_Speed
Air_Pressure
Hail_Accumulation
```

The final feature set must be determined after preprocessing and EDA.

Potential evaluation metrics:

- MAE
- MSE
- RMSE
- R²

The evaluation strategy must consider the temporal nature of photovoltaic data.

Do not randomly shuffle time-series observations without justification.

---

## Data Quality Considerations

Some photovoltaic datasets may contain invalid sensor values or sentinel values.

For example, extremely large negative values in rainfall or hail measurements may represent invalid measurements rather than physical observations.

These values must be investigated before preprocessing.

Do not replace all missing or invalid values with the mean automatically.

The preprocessing strategy must be justified based on the EDA results and the physical meaning of the variables.

---

## Reproducibility

The project should be reproducible.

Use:

- relative file paths
- fixed random states where randomness is used
- clearly documented preprocessing
- clearly documented model parameters

Avoid machine-specific absolute paths such as:

```text
C:/Users/username/...
```

Use project-relative paths instead.

---

## Results

Generated figures should be stored in:

```text
results/figures/
```

Generated tables should be stored in:

```text
results/tables/
```

Model files should be stored in:

```text
models/
```

Do not store generated results inside `data/raw/`.

---

## Coding Style

Use simple and readable Python.

Preferred:

```python
spring = pd.read_csv("../data/raw/Photovoltaic spring 2022-2023.csv")
```

Avoid unnecessarily complex abstractions during the EDA stage.

The code should be understandable by all members of the team.

Use English for:

- variable names
- function names
- comments
- Markdown section titles

Use descriptive variable names.

Good:

```python
missing_percentage
active_power
radiation_correlation
```

Avoid:

```python
x
a1
temp2
data_final_final
```

---

## Technology

Primary tools:

- Python
- Jupyter Notebook
- VS Code
- pandas
- NumPy
- Matplotlib
- Seaborn
- scikit-learn

The project should use standard Python data science libraries unless there is a clear reason to introduce another dependency.

---

## Important Principles

1. Understand the data before modeling.
2. Preserve raw data.
3. Do not hide preprocessing steps.
4. Do not make assumptions about invalid values.
5. Do not select a dataset without evidence.
6. Avoid data leakage.
7. Respect the temporal nature of photovoltaic data.
8. Keep code simple and reproducible.
9. Document important decisions.
10. Prefer scientifically and physically meaningful analysis over purely statistical conclusions.