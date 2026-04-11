![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# Assessment | Statistical Evaluation Mini-Project

## Overview

This assessment brings together the core skills from the Statistics for Data Science module. You will explore a real dataset through correlation analysis and group comparisons, then train a simple classifier and quantify the uncertainty around its performance using bootstrap confidence intervals.

You will work with the **Auto MPG** dataset, which contains fuel-efficiency data for cars from the 1970s–80s along with technical specifications and region of origin. The dataset is available directly from seaborn, so there is nothing to download.

## Learning Goals

- Compute and interpret Pearson and Spearman correlations with significance tests
- Perform one-way ANOVA and post-hoc comparisons to evaluate group differences
- Use bootstrap resampling to construct confidence intervals for classification metrics
- Communicate statistical findings clearly through visualizations and written interpretation

## Prerequisites

- Python 3.9+
- Libraries: pandas, numpy, scipy, scikit-learn, matplotlib, seaborn

```bash
pip install pandas numpy scipy scikit-learn matplotlib seaborn
```

## Requirements

1. **Fork** the assessment repository to your GitHub account.
2. **Clone** your fork locally.
3. Work inside the Jupyter notebook named **`m3-13-assessment.ipynb`**.
4. Use `random_state=42` wherever randomness is involved.
5. Commit and push your work regularly.

## Loading the Dataset

```python
import seaborn as sns

mpg = sns.load_dataset("mpg")
mpg = mpg.dropna()
```

The dataset includes the following columns:

| Column | Type | Description |
|---|---|---|
| mpg | float | Miles per gallon (fuel efficiency) |
| cylinders | int | Number of cylinders |
| displacement | float | Engine displacement (cubic inches) |
| horsepower | float | Engine horsepower |
| weight | float | Vehicle weight (lbs) |
| acceleration | float | 0–60 mph time (seconds) |
| model_year | int | Model year (70–82) |
| origin | str | Region of manufacture: usa, europe, japan |
| name | str | Car name |

## Tasks

### Task 1 — Correlation Analysis

Explore the relationships between numeric variables in the dataset.

1. Choose at least three pairs of numeric variables (e.g., mpg vs. weight, displacement vs. horsepower) and compute both Pearson and Spearman correlation coefficients.
2. Test each correlation for significance and report the p-values.
3. Create a correlation heatmap and at least two scatter plots with regression lines. Annotate each plot with the correlation coefficient.
4. In a Markdown cell, briefly explain when Pearson vs. Spearman is more appropriate, using examples from your results.

### Task 2 — Group Comparisons

Compare a numeric variable across the three origin groups (usa, europe, japan).

1. Choose a numeric variable (e.g., mpg) and visualize its distribution per origin group using box plots or violin plots.
2. Check ANOVA assumptions: normality within each group (Shapiro-Wilk) and homogeneity of variance (Levene's test).
3. Perform a one-way ANOVA and report the F-statistic, p-value, and eta-squared effect size.
4. If the ANOVA is significant, run Tukey's HSD post-hoc test and state which groups differ.

### Task 3 — Classification with Bootstrap Confidence Intervals

Train a classifier to predict **origin** from the numeric features, then quantify how certain you can be about its performance.

1. Prepare the data: use the numeric columns as features and `origin` as the target. Split into train (75 %) and test (25 %) sets with stratification.
2. Train at least two classifiers (e.g., Logistic Regression and Decision Tree) with default hyperparameters.
3. Print a classification report for each model.
4. Write a function `bootstrap_metric(y_true, y_pred, metric_fn, n_boot=2000, seed=42)` and use it to compute 95 % bootstrap confidence intervals for F1, precision, and recall for each model.
5. Visualize the CIs (e.g., dot-and-whisker plot) and state which model you would recommend and why.

### Task 4 — Summary

Write a short summary (150–250 words) in a final Markdown cell that answers:

1. What were the strongest correlations you found, and what do they tell you about fuel efficiency?
2. Do cars from different origins differ significantly in the variable you tested? Which groups stand out?
3. Which classifier would you recommend, and how confident are you in its performance based on the bootstrap CIs?

## Submission

### What to submit

- A completed Jupyter notebook (`m3-13-assessment.ipynb`) with all code, outputs, and Markdown explanations.

### Definition of done

- [ ] Correlation analysis with Pearson/Spearman, p-values, heatmap, and scatter plots (Task 1)
- [ ] ANOVA with assumption checks, effect size, and post-hoc test (Task 2)
- [ ] Two classifiers trained with bootstrap 95 % CIs for F1, precision, and recall (Task 3)
- [ ] Written summary connecting findings across all tasks (Task 4)
- [ ] Notebook runs top-to-bottom without errors

### How to submit

1. Stage and commit your changes:
   ```bash
   git add .
   git commit -m "Complete m3-13 assessment"
   ```
2. Push to your fork:
   ```bash
   git push origin main
   ```
3. Open a **Pull Request** from your fork to the original repository.
4. Paste the Pull Request URL into the Student Portal.

## Evaluation Criteria

| Criterion | Weight | Description |
|---|---|---|
| Correlation Analysis | 25 % | Correct computation, appropriate method choice, annotated visualizations |
| Group Comparisons | 25 % | Proper assumption checks, correct ANOVA execution, post-hoc interpretation |
| Bootstrap ML Metrics | 30 % | Correct bootstrap implementation, CI visualization, model recommendation |
| Summary & Communication | 15 % | Clear, evidence-based summary connecting all tasks |
| Code Quality | 5 % | Clean, organized notebook that runs without errors |
