# League of Legends Champion Specific Statistical Analysis
League of Legends Champion Specific Statistical Analysis is a comprehensive data science project conducted at UCSD for DC80. This project consists of a multitide of analysis from start to end including data extraction/cleaning, exploratory data analysis, hypothesis testing, outline of a baseline model, finalized model, and fairness analysis. The project's main objective is to investigate further on the significance of the champion selection process and how various factors related to it can influence match statistics such as the match outcome. 

Authors: Angela Wu

## Introduction
### General Introduction
League of Legends (LoL) is a hugely popular multiplayer online battle arena game developed by Riot Games. With around 100 million players, LoL is one of the most influential and well-known esports games of all time. The data set analyzed in this analysis is developed by Oracle’s Elixir, and focuses on data from 2022 of professional LoL esport matches. The dataset has over 30 columns and 150589 rows that together, provide gameplay statistics on a multitude of matches and offer insight on team behavior, champion selection, and match results.

As a player of MOBA games, it is known that choosing different champions will result in different outcomes. Certain champions are seen as “meta” because they are stronger or more versatile, and as a result, will lead to a higher chance of winning. However, more statistical analysis is required to make and prove these “common-sense” conclusions that are often anecdotal at nature. Like mentioned earlier, this project's main objective is to investigate the effect of champion selection on various factors such as match outcome.

The central question of this project is:

> Does champion selection significantly impact match outcomes in professional League of Legends play?

This question is important because in LoL matches, champion selection occurs before gameplay begins, meaning it represents a strategic decision that can shape the entire course of a match. So, by understanding how champion choices correlate with winning, significant insight can be provided on balancing and drafting strategy. For data scientists and LoL players, answering this question will help distinguish genuine patterns from meaningless bias.

### Introduction of Columns
This dataset contains an array of columns containing a multitude of game data from various professional League of Legends matches. With over 30 columns of different game data, the following is an introduction of some of the key columns used in this statistical analysis:

- `gameid`: This column represents the unique identifier for each match/game that is played, which lets us distinguish between different matches.

- `teamid`: This column represents the unique identifier for each team.
  
- `league`: This column represents which professional League of Legends competition or region the match was played in.
  
- `side`: This column represents which side this team played on for a certain match (rev vs. blue).
  
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
I performed univariate analysis on champion pick frequencies in the dataset:
<iframe
  src="assets/champion_pick_univariate.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
The barchart displays the top 10 most picked champions in pro play during the 2022 season. Significant differences in champion pick preference is noticeably present, with the most picked champion picked 3743 times. It is interesting to note that the most preferable champions that are typically picked does not correspond to the champions with the highest win rate. It is also important to note that some champions have been picked significantly less during the season, as seen with Aurelion Sol (picked 5 times). 


Another univariate analysis I performed on match outcomes:
<iframe
  src="assets/match_outcome_univariate.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
This barchart displays the distribution of match outcomes in the dataset, where a value of 1 represents a win and 0 represents a loss. The distribution is exactly balanced, with wins and losses occurring at exactly equal frequencies. This is an expected result, as each game results in exactly one winning team and one losing team. This distribution provides an important foundation/baseline for the analysis since the target variable is not heavily imbalanced. Standard classification metrics such as accuracy are appropriate for evaluating predictive models in later steps.


### Bivariate Analysis
I performed bivariate analysis on champion picks (picks 1-5) and the result statistic in the dataset. This allows me to analyze the winrate of each champion.
<iframe
  src="assets/champion_bivariate.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
The graph displays the win rates of the top 10 champions with the highest win rates in the dataet. I choose to focus on this subset to narrow down the focus and highlight whether the most popular draft choices coincides with match success. Though there seem to be a notable difference in winrates between champions, an important thing to note is that some champions, such as Aurelion Sol, only appeared a total of < 10 total times. This makes their observed win rates less reliable due to the limitations of insufficient sample size. Another thing to point out is that many champions still perform within a relative range, suggesting that champion win rate is not the sole factor in determining match success. Futher analysis is necessary to discern other factors that are at play such as team composition. 

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
