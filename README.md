# Hapiness_Analysis

Three hypothesis tests on the 2018 World Happiness Report, done as a university data analysis project.

## The problem

The World Happiness Report ranks countries and publishes the factors behind the score, such as freedom, generosity and perceived corruption. Charts of that data invite conclusions. The project was to state three of those conclusions as hypotheses and check whether the data supports them at a stated significance level.

## What I built

A Jupyter notebook that cleans the 2018 data, plots each factor against rank, and runs three tests.

| Question | Test | Result |
|---|---|---|
| Is Israel's freedom score higher than the mean of Muslim-majority countries? | One-sided z-test, alpha 0.05 | H0 rejected |
| Do Asian and European countries differ in mean generosity? | Welch's t-test, alpha 0.10 | H0 rejected, Asia higher |
| Does freedom differ between the happiest and the least happy quarter of countries? | Welch's t-test, alpha 0.05 | H0 rejected, higher in happy countries |

## Method

- Cleaning: two rows with a zero in Freedom or Generosity were checked against other sources and removed as bad data, along with rows containing N/A.
- No normalization, since the factor columns are already on the same scale.
- Welch's t-test (unequal variances) for the two-sample questions, because there is no reason to assume the two groups of countries have the same variance.
- NumPy, SciPy and Matplotlib only. The data is loaded with the `csv` module.

## Running it

```bash
python3 -m venv .venv && .venv/bin/pip install jupyter numpy scipy matplotlib
```

Download `2018.csv` from the [World Happiness Report dataset on Kaggle](https://www.kaggle.com/datasets/unsdsn/world-happiness) and put it next to the notebook, then:

```bash
.venv/bin/jupyter notebook Elie_Project_DataAnalysis.ipynb
```

## Limits

These are tests on one year of country-level data. They show association, not cause, and the country groupings were chosen by hand.
