# Fighting by Numbers: UFC Fight Outcome Prediction Using AutoML

## Overview

Fighting by Numbers is a machine learning research project focused on predicting Ultimate Fighting Championship (UFC) fight outcomes using automated machine learning, temporal feature engineering, and betting market analysis.

The project introduces a time-aware prediction framework that combines fighter performance metrics, opponent-adjusted statistics, Elo ratings, and betting odds to generate calibrated win probabilities for UFC bouts.

Using more than 8,500 UFC fights spanning 1994–2026, the system achieved:

* 69.7% Prediction Accuracy
* 0.7486 ROC-AUC
* 0.5891 Log Loss
* Outperformed Vegas Favorites across all major evaluation metrics

## Research Objective

Traditional UFC prediction models rely heavily on static fighter attributes such as:

* Height
* Reach
* Age
* Win-Loss Records

These features fail to capture fighter momentum, recent form, quality of competition, and evolving performance trends.

This project addresses those limitations through:

* Automated Machine Learning (AutoML)
* Temporal Feature Engineering
* Bayesian Opponent Adjustment
* Elo Rating Systems
* Betting Market Calibration

## Dataset

Source:

* UFCStats
* BestFightOdds

Dataset Characteristics:

| Metric                    | Value       |
| ------------------------- | ----------- |
| Total Fights              | 8,517       |
| Date Range                | 1994 – 2026 |
| Weight Classes            | 15          |
| Betting Coverage          | 70.4%       |
| Modern Era Fights (2020+) | 3,057       |

## Methodology

### Data Preprocessing

* Male divisions only
* Minimum fighter experience threshold
* Removal of split-decision fights
* Fighter position randomization to eliminate corner bias
* Strict temporal validation to prevent data leakage

### Feature Engineering

#### Exponentially Weighted Moving Averages (EWMA)

Recent performances receive higher weight than older fights.

Used for:

* Striking Metrics
* Grappling Metrics
* Defensive Metrics

#### Bayesian Opponent Adjustment

Fighter statistics are adjusted according to opponent quality.

Examples:

* Strikes landed against elite defenders receive higher value.
* Statistics accumulated against weaker competition are penalized.

#### Elo Ratings

Dynamic skill ratings calculated before every fight.

Used to capture:

* Relative fighter strength
* Momentum shifts
* Skill evolution over time

#### Physical Ratios

* Reach Ratio
* Age Ratio
* Height Ratio

These features consistently demonstrated predictive value across weight classes.

## Model Architecture

The system uses AutoGluon AutoML to create a weighted ensemble consisting of:

* LightGBM
* XGBoost
* CatBoost
* FastAI Neural Networks
* Tabular Neural Networks
* TabPFN Transformers

Bagging and stacking were disabled to avoid temporal leakage and fighter memorization.

## Results

### Prediction Performance

| Model                | Accuracy | ROC-AUC | Log Loss |
| -------------------- | -------- | ------- | -------- |
| Vegas Favorites      | 67.0%    | 0.7259  | 0.6094   |
| UFC Prediction Model | 69.7%    | 0.7486  | 0.5891   |

### Financial Performance

The model was evaluated using historical betting simulations.

| Strategy           | ROI    |
| ------------------ | ------ |
| All Predictions    | +6.6%  |
| Edge > 5%          | +9.2%  |
| Edge > 10%         | +15.0% |
| Extreme Edge > 15% | +41.2% |

The model demonstrated positive expected value opportunities and strong risk-adjusted returns through Sharpe Ratio analysis.

## Key Findings

### Biological Alpha

Age emerged as one of the strongest non-odds predictors.

Findings showed:

* Younger fighters win 56.8% of the time.
* At a 10-year age gap, younger fighters win approximately 69% of fights.

### Chaos Ceiling

Despite advanced feature engineering and ensemble learning, model accuracy consistently plateaued around 70%.

This suggests a theoretical prediction ceiling in MMA caused by:

* Flash knockouts
* Injuries
* Fight-ending randomness
* Judging variance

### Market Inefficiencies

The model identified situations where betting markets systematically undervalued:

* Younger fighters
* Opponent-adjusted performance
* Recent momentum
* Hidden statistical advantages

## Technology Stack

### Machine Learning

* AutoGluon
* LightGBM
* XGBoost
* CatBoost
* TabPFN
* FastAI

### Data Engineering

* Python
* Pandas
* NumPy

### Analysis & Visualization

* Matplotlib
* Seaborn
* Jupyter Notebooks

### Infrastructure

* Kaggle Linux Environment
* AWS Ecosystem

## Future Improvements

* Integration of social media sentiment analysis
* Fighter interview sentiment scoring
* Regional MMA record ingestion
* Real-time odds monitoring
* Transformer-based tabular models
* AWS Mitra experimentation
* Live prediction API deployment

## Research Paper

This repository accompanies the paper:

"Fighting by Numbers: Using Automated Machine Learning to Predict UFC Fight Outcomes"

Authors:

* Aditya Parkhe
* Prathamesh Talele

## Disclaimer

This project is intended for educational, research, and sports analytics purposes only.

Past performance does not guarantee future betting outcomes. Nothing in this repository should be considered financial or gambling advice.
