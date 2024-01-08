# NFL_Project (Current Accuracy: 65.3%)

My project predicts which NFL team will cover the spread in a game based on a variety of factors and statistics. 

# What is the spread of an NFL game?: 
The spread is an artifical handicap created by sportsbooks to create an even bet between the two teams competing in a game. 

Example: If a sportsbook projects a team to win by 3-4 points, they could be given a 3.5 point handicap. Therefore the two options to choose would be the favorite (-3.5) or the underdog (+3.5). In selecting the favorite (-3.5), you would need the favorite to win by over 4 points to win the selection. This would mean the favorite covers the spread. On the other hand, in choosing the underdog, you would need the underdog to either win outright or lose by less than 4 points to win the selection. This would mean the underdog covers the spread, and the favorite does not cover.

# What Data Is Being Used
The data consists of all NFL Games since 2002 (not including the 2023 season).

Scores: Dataset uploaded to Kaggle by Spreadspoke, with a row for each game played in the NFL since 1966, including date, season year, home team, away team, weather and stadium information, the scores, and the spread once spreads began being tracked. https://www.kaggle.com/datasets/tobycrabtree/nfl-scores-and-betting-data?select=spreadspoke_scores.csv

Teams:  Dataset uploaded to Kaggle by Spreadspoke, with a row for each team, along with a team ID, and the team's division, conference, and old division before divisional realignment.
https://www.kaggle.com/datasets/tobycrabtree/nfl-scores-and-betting-data?select=nfl_teams.csv

Stats: Dataset uploaded to Kaggle by user CVIAXMIWNPTR, with a row for each game played in the NFL since 2002, and a column for the home team, away team, and each team's statistical output in the game for a variety of statistics. https://www.kaggle.com/datasets/cviaxmiwnptr/nfl-team-stats-20022019-espn

# The Model
The model utilizes sci-kit learn features and is a logistic regression model. 
Game facts being considered in the model:
- Favorite being home or away (Discrete)
- If the game is divisional (Discrete)
- If the game is a playoff game (Discrete)

Team statistical per game averages being considered in the model (for both teams):
- Passing yards
- Passing yards allowed
- Rushing yards
- Rushing yards allowed
- Turnovers
- Against the spread record

The model yields a prediction of either "COVER" or "NO COVER"
COVER: The favorite exceeds their handicap, winning by more than expected
NO COVER: The favorite does not exceed their handicap, either winning by less than expected or losing.

# Flask website
The flask website is a local developmental server that takes in inputs and provides a prediction based o user inputs. For each team statsitic, a custom link is provided to statmuse.com, a reliable sports database that will relay each statstic to the user for conveninent input. It will yield one of two predictions: "COVER" or "NO COVER".


