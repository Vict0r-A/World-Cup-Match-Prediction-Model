 
# World Cup 2026 Match Predictor

This project uses machine learning to predict the outcome of international football matches, with a focus on applying the model to the 2026 FIFA World Cup.

The model predicts one of three possible match outcomes:

- Draw
- Team 1 Win
- Team 2 Win


 

## Project Overview

Football is difficult to predict because match results are influenced by many factors, including team strength, tactics, form, injuries, venue, tournament pressure, and randomness.

This project attempts to model international football outcomes using historical match data and engineered features such as:

- Team Elo ratings
- Elo difference between teams
- Recent team form
- Recent goals scored and conceded
- Recent goal difference trends
- Host and neutral venue information

The model was trained using a chronological train-test split to reduce data leakage and better reflect real-world prediction, where future results should not influence past training data.

 

## Related Article

I wrote a Medium article explaining the motivation, process, challenges, and results behind this project:

[Can Machine Learning be used to predict World Cup matches?](https://medium.com/@thevictoradams/can-machine-learning-be-used-to-predict-world-cup-matches-84ed9e8978ae)

 

## LinkedIn Post

I also shared this project on LinkedIn as part of my football analytics and machine learning content.

LinkedIn post: `[Here](https://www.linkedin.com/posts/victor-adams-22519431a_machinelearning-datascience-footballanalytics-share-7471525367896514560-ii7X/?utm_source=share&utm_medium=member_desktop&rcm=ACoAAFDUIT0BsOFrgpcaY_YtUECNzj0UIw-Z42Y)`

LinkedIn profile: `linkedin.com/in/victor-adams-22519431a/`

 

## Model Target

The model is a multi-class classifier with the following target labels:

| Label | Meaning |
|---|---|
| 0 | Draw |
| 1 | Team 1 Win |
| 2 | Team 2 Win |

 

## Features Used

The model uses football-specific features designed to represent both long-term team strength and recent performance.

```python
team_1_elo
team_2_elo
elo_gap
neutral_encoded
team_1_host

team_1_last5_goals_for_avg
team_1_last5_goals_against_avg
team_1_last5_goal_difference_avg
team_1_last5_wins
team_1_last5_draws
team_1_last5_losses
team_1_last5_form_points

team_2_last5_goals_for_avg
team_2_last5_goals_against_avg
team_2_last5_goal_difference_avg
team_2_last5_wins
team_2_last5_draws
team_2_last5_losses
team_2_last5_form_points
````

These features allow the model to compare each team's overall strength, recent attacking performance, defensive performance, and form.

 

## Model Performance

The final model achieved the following performance on the test set:

```text
Model Accuracy: 0.6022167487684729
Model Log Loss: 0.8966873560958508
```

Rounded summary:

```text
Accuracy: 60.22%
Log Loss: 0.8967
```

 

## Classification Report

```text
              precision    recall  f1-score   support

        Draw       0.36      0.11      0.17       186
  Team 1 Win       0.64      0.85      0.73       390
  Team 2 Win       0.58      0.58      0.58       236

    accuracy                           0.60       812
   macro avg       0.53      0.51      0.49       812
weighted avg       0.56      0.60      0.56       812
```

 

## Confusion Matrix

```text
[[ 21 111  54]
 [ 14 331  45]
 [ 24  75 137]]
```

The confusion matrix can be interpreted as:

| Actual / Predicted | Draw | Team 1 Win | Team 2 Win |
| ------------------ | ---: | ---------: | ---------: |
| Draw               |   21 |        111 |         54 |
| Team 1 Win         |   14 |        331 |         45 |
| Team 2 Win         |   24 |         75 |        137 |

 

## Results Interpretation

The model achieved an accuracy of approximately **60.22%**, which is a reasonable result for a three-class football prediction problem.

The model performed best when predicting **Team 1 Win**, achieving:

* Precision: 0.64
* Recall: 0.85
* F1-score: 0.73

This means the model was strong at identifying matches where Team 1 was likely to win.

The model also performed reasonably when predicting **Team 2 Win**, achieving an F1-score of 0.58.

However, draw prediction was the weakest area of the model. The draw class achieved:

* Precision: 0.36
* Recall: 0.11
* F1-score: 0.17

This shows that the model struggled to correctly identify draws and often predicted a winning team instead.

 

## Key Challenge: Predicting Draws

Draws are one of the hardest outcomes to predict in football.

From the confusion matrix:

```text
Actual draws: 186
Correctly predicted draws: 21
Draws predicted as Team 1 wins: 111
Draws predicted as Team 2 wins: 54
```

This shows that the model often preferred predicting a winner instead of a draw.

This is a common issue in football prediction because draws can happen in many different situations. For example, a draw may occur because two teams are evenly matched, because a weaker team defends well, because of poor finishing, or because of random match events.

---

## Why Accuracy Alone Is Not Enough

Although the model achieved around **60% accuracy**, accuracy does not tell the full story.

The classification report shows that the model is much better at predicting wins than draws. This is why additional metrics such as precision, recall, F1-score, log loss, and the confusion matrix are important.

Log loss is also useful because it evaluates the quality of the model's predicted probabilities, not just whether the final class prediction was correct.

A model can make the correct prediction but still be poorly calibrated if its probability estimates are unreliable. For this reason, log loss provides an additional way to evaluate how confident and realistic the model's predictions are.

 
 

## Future Improvements

Potential improvements include:

* Add player-level data such as injuries, squad strength, and player availability
* Add team market value or squad value as a feature
* Add FIFA ranking data
* Add confederation strength features
 
 
---

## Project Goal

The goal of this project is to explore how machine learning can be used to predict international football match outcomes and apply those predictions to a World Cup simulation.
 
 

## Technologies Used

* Python
* pandas
* NumPy
* scikit-learn
* XGBoost
* Matplotlib
* Seaborn

 

## Author

Victor Adams

 
 
 
