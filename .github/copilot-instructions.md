# AI Agent Instructions

## Project Context

This is a photovoltaic data analysis and machine learning project.

The project contains four seasonal photovoltaic datasets:

- Spring 2022-2023
- Summer 2022-2023
- Autumn 2022-2023
- Winter 2022-2023

The current objective is to perform EDA before selecting one dataset for a Random Forest model.

The current target variable is expected to be:

`Active_Power`

The planned machine learning task is Random Forest regression, but this must be confirmed before final model development.

---

## General Rules

Before changing code, understand the current project structure and notebook stage.

Do not make assumptions when the data or project requirements are unclear.

If an important assumption is required, explain it before implementing it.

Do not skip EDA steps just to reach the machine learning stage faster.

Do not perform dataset selection before comparative EDA is complete.

---

## Data Rules

Raw data is located in:

```text
data/raw/
```

Never modify or overwrite raw CSV files.

Processed data belongs in:

```text
data/processed/
```

Use relative paths.

Never use absolute machine-specific paths.

Example:

```python
pd.read_csv("../data/raw/file.csv")
```

Do not use:

```python
pd.read_csv("C:/Users/username/file.csv")
```

---

## EDA Rules

The current EDA notebook is:

```text
notebooks/01_eda.ipynb
```

Follow this order:

1. Import libraries
2. Load datasets
3. Dataset overview
4. Data types
5. Missing values
6. Duplicate values
7. Invalid values
8. Constant features
9. Timestamp analysis
10. Descriptive statistics
11. Target analysis
12. Feature analysis
13. Correlation analysis
14. Dataset comparison
15. EDA findings
16. Dataset selection

Do not introduce machine learning code into the EDA notebook unless explicitly requested.

---

## Simplicity Rule

Use simple Python and pandas code.

The project is intended to be understood by a student team.

Prefer straightforward code such as:

```python
df.head()
df.info()
df.describe()
df.isnull().sum()
df.corr()
```

Avoid unnecessary:

- complex class structures
- excessive helper functions
- decorators
- advanced abstractions
- complicated pipelines
- unnecessary dependencies

Do not optimize code prematurely.

Readability is more important than abstraction during EDA.

---

## Notebook Rules

Keep notebook cells logically separated.

Use Markdown headings to explain each analysis stage.

Each major analysis should follow:

```text
Purpose
↓
Code
↓
Output
↓
Interpretation
```

Do not create dozens of tiny cells without a meaningful reason.

Do not hide important preprocessing inside a single large cell.

---

## Visualization Rules

Use Matplotlib and Seaborn.

Plots should have:

- clear titles
- readable axis labels
- appropriate figure size
- meaningful variable names

Do not generate unnecessary visualizations.

Prioritize:

- Active Power distribution
- Active Power over time
- Global Horizontal Radiation distribution
- Radiation vs Active Power
- Correlation matrix
- Important feature distributions
- Dataset comparison

---

## Timestamp Rules

Do not assume all timestamp formats are identical.

Inspect the raw timestamp values first.

Convert timestamps carefully.

After conversion, verify:

- minimum timestamp
- maximum timestamp
- sampling interval

Do not discard timestamp information before understanding its role.

---

## Missing Value Rules

Always inspect missing values before preprocessing.

Do not automatically use:

```python
df.fillna(df.mean())
```

Missing values must be understood first.

Check whether missing values occur:

- randomly
- in consecutive periods
- in specific variables
- during specific time periods

The final imputation strategy belongs to the preprocessing stage, not the initial EDA stage.

---

## Invalid Value Rules

Some sensor datasets may contain sentinel values.

Extremely large negative values may represent invalid measurements.

Do not automatically treat every extreme value as an outlier.

First determine whether the value is:

- physically possible
- a sensor error
- a missing-value code
- a legitimate measurement

Document the reasoning before replacing or removing such values.

---

## Feature Rules

Potential features include:

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

Do not automatically use every available feature.

Check:

- variation
- missing values
- invalid values
- physical meaning
- relationship with the target

A constant feature should be identified before modeling.

---

## Target Rules

The current target is:

```text
Active_Power
```

Do not transform or remove target values without justification.

Inspect:

- distribution
- range
- outliers
- time-series behavior
- possible zero-production periods

Negative values near zero should not automatically be removed.

Investigate their context first.

---

## Dataset Selection Rules

Do not declare a dataset "best" based on a single metric.

Do not use only:

- row count
- correlation
- missing-value percentage
- maximum power

Dataset selection should consider several EDA findings together.

The agent may summarize evidence for each dataset but should not make an unsupported selection.

---

## Machine Learning Rules

When modeling begins:

Target:

```text
Active_Power
```

Potential model:

```text
RandomForestRegressor
```

Before training:

1. Finish EDA.
2. Clean invalid values.
3. Handle missing values.
4. Select features.
5. Check data leakage.
6. Engineer features if justified.
7. Split data appropriately.
8. Train model.
9. Evaluate model.
10. Analyze feature importance.

Because the data is time-dependent, do not randomly shuffle observations without justification.

Consider chronological train/test splitting.

---

## Data Leakage Rules

Never allow information from the test period to influence training or preprocessing.

Do not:

- calculate preprocessing statistics using the full dataset before splitting
- use future observations as input for past predictions
- randomly mix future and past observations when evaluating temporal prediction

Any potential leakage must be explicitly considered.

---

## Model Evaluation

Use appropriate regression metrics such as:

```text
MAE
MSE
RMSE
R²
```

Do not rely on R² alone.

Report model performance together with the evaluation methodology.

---

## Code Modification Rules

When asked to modify an existing notebook:

1. Inspect the existing structure.
2. Preserve working code.
3. Modify only the relevant section.
4. Do not rewrite unrelated sections.
5. Do not silently change analytical assumptions.
6. Keep existing variable naming consistent unless there is a clear reason to change it.

When adding code, explain where it belongs if the location is ambiguous.

---

## Dependency Rules

Prefer existing dependencies.

Do not add a new Python package unless necessary.

Current expected dependencies:

```text
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyter
```

If a new dependency is necessary, explain why before adding it.

---

## Quality Control

Before considering a notebook section complete, verify:

- code runs without errors
- variable names are consistent
- plots have meaningful labels
- results are reproducible
- no raw data was modified
- no unsupported assumptions were introduced
- conclusions are supported by the output

Never claim that an analysis was performed if the code was not actually executed.

---

## Communication Style

When explaining changes:

- be concise
- use technical but accessible language
- explain the reason behind important changes
- distinguish observation from interpretation
- do not overcomplicate explanations

Use English in code and notebook headings.

The analysis itself may use Indonesian when communicating with the project team.