# League of Legends Champion Specific Statistical Analysis
League of Legends Champion Specific Statistical Analysis is a comprehensive data science project conducted at UCSD for DC80. This project consists of a multitide of analysis from start to end including data extraction/cleaning, exploratory data analysis, hypothesis testing, outline of a baseline model, finalized model, and fairness analysis. The project's main objective is to investigate further on the significance of the champion selection process and how various factors related to it can influence match statistics such as the match outcome. 

Authors: Angela Wu

## Introduction
### General Introduction
Text
### Introduction of Columns
This dataset contains an array of columns containing a multitude of game data from various professional League of Legends matches. With over 30 columns of different game data, the following is an introduction of some of the key columns used in this statistical analysis:
| Column | Description |
|---|---|
| 'deaths' | Number of deaths in a game |

- `gameid`: This column represents the unique identifier for each match/game that is played, which lets us distinguish between different matches.
  
- `teamid`: This column represents the unique identifier for each team.
  
- `league`: This column represents which professional League of Legends competition or region the match was played in.
  
- `side`: This column represents which side this team played on for a certain match (rev vs. blue)
  
- `result`: This column represents the outcome of a match. Specifically, 1 represents the team won, and 0 represents the team lost.
  
- `ban1`: This column represents the 1st champion banned by the opposing team in the corresponding League of Legends match.
- `ban2`: This column represents the 2nd champion banned by the opposing team in the corresponding League of Legends match.
- `ban3`: This column represents the 3rd champion banned by the opposing team in the corresponding League of Legends match.
- `ban4`: This column represents the 4th champion banned by the opposing team in the corresponding League of Legends match.
- `ban5`: This column represents the 5th champion banned by the opposing team in the corresponding League of Legends match.

- `pick1`: This column represents the 1st champion picked by the team in the corresponding League of Legends match.
- `pick2`: This column represents the 2st champion picked by the team in the corresponding League of Legends match.
- `pick3`: This column represents the 3st champion picked by the team in the corresponding League of Legends match.
- `pick4`: This column represents the 4st champion picked by the team in the corresponding League of Legends match.
- `pick5`: This column represents the 5st champion picked by the team in the corresponding League of Legends match.
  
## Data Cleaning and Exploratory Data Analysis
### Data Cleaning
Text
### Univariate Analysis
More text
<iframe
  src="assets/champion_pick_univariate.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
<iframe
  src="assets/match_outcome_univariate.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Bivariate Analysis
Even more text
<iframe
  src="assets/champion_bivariate.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
<iframe
  src="assets/winrate_side_bivariate.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Interesing Aggregates
So much text.

## Assessment of Missingness
### NMAR Analysis
Wowzers.
### Missingness Dependency
Bazinga!
<iframe
  src="assets/mar_dependent.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
<iframe
  src="assets/mar_independent.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>


## Hypothesis Testing
My p-value is so small.
<iframe
  src="assets/aurelionsol_hypothesis.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

## Framing a Prediction Problem
Will my p-value still be small?

## Baseline Model
P-value is small.

## Final Model
P-value will always be small.

## Fairness Analysis
Unfair.
