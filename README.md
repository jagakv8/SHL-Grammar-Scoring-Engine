# SHL Grammar Scoring Engine

## Overview

This project was developed for the SHL Research Intern private Kaggle challenge.

The objective is to predict a continuous grammar score from spoken English audio samples.

The dataset contains:

- 769 labelled training samples
- 216 test samples
- Grammar scores ranging from 0 to 5

## Approach

The solution uses pretrained speech representation models to extract acoustic and phonetic information from the spoken audio.

### 1. WavLM

WavLM representations are extracted from selected hidden layers and used as high-dimensional speech features.

### 2. Wav2Vec2

Wav2Vec2 representations are extracted as a complementary speech representation.

### 3. Feature Fusion

The selected WavLM and Wav2Vec2 representations are concatenated, resulting in a 2304-dimensional feature vector.

### 4. Regression

The combined features are standardized and used with Ridge Regression.

The final model uses:

- Model: Ridge Regression
- Alpha: 300
- Target range: 0 to 5

## Evaluation

Using an 80/20 train-validation split:

| Metric | RMSE |
|---|---:|
| Training RMSE | 0.3202 |
| Validation RMSE | 0.6175 |

## Competition Submission

The repository includes the best competition submission:

`champion_wav2vec2_05.csv`

This file contains predictions for all 216 test samples.

The submitted competition score for this file was **0.4409 RMSE**.

## Files

```text
SHL-Grammar-Scoring-Engine/
├── README.md
├── shl_grammar_scoring.ipynb
└── champion_wav2vec2_05.csv
