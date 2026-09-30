# Instructor Effectiveness Analysis

A data science project that analyzes instructor performance across course batches, develops an effectiveness scoring framework, categorizes instructors into effectiveness tiers, and uses machine learning to predict those tiers.

## Project Overview

The dataset contains information about course batches handled by different instructors. Since an instructor can be associated with multiple batches, the analysis is performed at both the batch level and instructor level.

The project focuses on three major areas:

- Learner outcomes
- Learner engagement
- Learner feedback

These metrics are combined to create an overall instructor effectiveness score.

## Objectives

- Perform exploratory data analysis on instructor and course-batch data.
- Analyze distributions and relationships between performance variables.
- Normalize the effectiveness-related features.
- Develop an instructor effectiveness scoring methodology.
- Aggregate batch-level data to the instructor level.
- Categorize instructors into Low, Medium, and High effectiveness tiers.
- Train a machine learning classification model to predict effectiveness tiers.
- Evaluate the model using classification metrics.
- Analyze feature importance.

## Effectiveness Scoring

The effectiveness score is based on three dimensions:

### 1. Learner Outcomes — 50%

Includes:

- Completion Rate
- Score Improvement
- Average Quiz Score
- Non-Dropout Rate

### 2. Learner Engagement — 30%

Includes:

- Average Watch Time
- Assignment Submission Rate
- Forum Activity Rate

### 3. Learner Feedback — 20%

Includes:

- Average Feedback Score
- Feedback Response Rate

The final effectiveness score is calculated as:

`Final Effectiveness = (Outcome Score × 0.50) + (Engagement Score × 0.30) + (Feedback Score × 0.20)`

The resulting score ranges from 0 to 1, where higher values represent higher effectiveness.

## Effectiveness Tiers

Instructors are categorized using the 25th and 75th percentiles of the instructor-level effectiveness scores.

- **Low:** Below the 25th percentile
- **Medium:** Between the 25th and 75th percentiles
- **High:** Above the 75th percentile

The final dataset contains:

- 30 Low-effectiveness instructors
- 60 Medium-effectiveness instructors
- 30 High-effectiveness instructors

## Machine Learning

A **Random Forest Classifier** was used to predict the effectiveness tier.

The model uses instructor-level performance features including:

- `completion_rate`
- `avg_score_improvement`
- `avg_quiz_score`
- `not_drop_rate`
- `avg_watch_time`
- `assignment_submission_rate`
- `forum_activity_rate`
- `avg_feedback_score`
- `feedback_response_rate`

`instructor_id` and `final_effectiveness` were excluded from the model inputs.

The data was divided into:

- 80% training data
- 20% testing data

## Results

The Random Forest model achieved:

- **Accuracy:** 100%
- **Precision:** 1.00
- **Recall:** 1.00
- **F1-score:** 1.00

The most important features were:

1. `not_drop_rate`
2. `completion_rate`
3. `avg_score_improvement`
4. `avg_quiz_score`

## Important Methodological Note

The effectiveness tiers were created using the same underlying features that were later used as inputs to the machine learning model.

Therefore, the high classification performance indicates that the model can successfully reproduce the defined effectiveness-tier methodology. It should not be interpreted as independent validation of instructor effectiveness.

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

