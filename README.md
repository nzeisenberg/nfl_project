# NFL Project (Current Accuracy: 70%)

My project predicts which NFL team will cover the spread in a game based on a variety of factors and statistics. 

# What is the spread of an NFL game? 
The spread is an artifical handicap created by sportsbooks to create an even bet between the two teams competing in a game. 

Example: If a sportsbook projects a team to win by 3-4 points, they could be given a 3.5 point handicap. Therefore the two options to choose would be the favorite (-3.5) or the underdog (+3.5). 
- In selecting the favorite (-3.5), you would need the favorite to win by over 4 points to win the selection. This would mean the favorite covers the spread.
- On the other hand, in choosing the underdog (+3.5), you would need the underdog to either win outright or lose by less than 4 points to win the selection. This would mean the underdog covers the spread, and the favorite does not cover.

# What Data Is Being Used
The data consists of all NFL Games since 2002 (not including the 2023 season).

The three datasets being used in this project:
- Scores: Dataset uploaded to Kaggle by Spreadspoke, with a row for each game played in the NFL since 1966, including date, season year, home team, away team, weather and stadium information, the scores, and the spread once spreads began being tracked. https://www.kaggle.com/datasets/tobycrabtree/nfl-scores-and-betting-data?select=spreadspoke_scores.csv

- Teams:  Dataset uploaded to Kaggle by Spreadspoke, with a row for each team, along with a team ID, and the team's division, conference, and old division before divisional realignment.
https://www.kaggle.com/datasets/tobycrabtree/nfl-scores-and-betting-data?select=nfl_teams.csv

- Stats: Dataset uploaded to Kaggle by user CVIAXMIWNPTR, with a row for each game played in the NFL since 2002, and a column for the home team, away team, and each team's statistical output in the game for a variety of statistics. https://www.kaggle.com/datasets/cviaxmiwnptr/nfl-team-stats-20022019-espn

# The Model
The model utilizes aggregated prediction probabilties from four classification models (Courtesy of scikit-learn):
- Logistic Regression
- Support Vector Classification
- Random Forest Classification
- Multi-Layer Perceptron Classification

The model takes the mean of all prediction probabilities to create an aggregated prediction probabiltiy
- The label prediction is either 0 or 1 (the probability rounded to either 0 or 1)
- The model selects certain games based on a confidence threshold
- The threshold ensures the model predicts over 20% of games with over 70% accuracy
  
# Features of Model
Game facts being considered:
- If the favorite is home or away (Discrete)
- If the game is divisional (Discrete)
- If the game is a playoff game (Discrete)
- What week of the NFL season the game occured

Team statistical per game averages considered in the model (for both teams):
- Passing yards
- Passing yards allowed
- Rushing yards
- Rushing yards allowed
- Turnovers
- Against the spread record
- Win % entering the game

# Labels
The model yields a prediction of either "COVER" or "NO COVER"

COVER (1): The favorite exceeds their handicap, winning by more than expected

NO COVER (0): The favorite does not exceed their handicap, either winning by less than expected or losing.








