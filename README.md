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
  height="height: 100%; border: none;"
  frameborder="0"
></iframe>

The barchart displays the top 10 most picked champions in pro play during the 2022 season. Significant differences in champion pick preference is noticeably present, with the most picked champion picked 3743 times. It is interesting to note that the most preferable champions that are typically picked does not correspond to the champions with the highest win rate. It is also important to note that some champions have been picked significantly less during the season, as seen with Aurelion Sol (picked 5 times). 

Another univariate analysis I performed on match outcomes:
<iframe
  src="assets/match_outcome_univariate.html"
  width="800"
  height="height: 100%; border: none;"
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
Among our columns of interest, bans 1-5 stood out as potential candidates for NMAR(Not Missing At Random) analysis. On the surface, the dataset does not reveal the nature of missingness for bans. There dosen't seem to be any obvious trends or dependencies on other columns. However, with some domain knowledge, one could argue that the missingness of bans 1-5 could be classified as a case of NMAR. At the start of a professional League of Legends game, players can decide to leave a ban slot empty. Rather than reflecting dependency with another column in the dataset (as in the case with MAR), this reflects an intentional decision made by a team. Since the missingness of bans depend on the decision itself, this is a case of NMAR. If an extra column `ban_skipped` was considered during data collection which indicated whether a team left at least one slot empty(indicated by 1) or used all bans(indicated by 0), the ban columns would fall under MAR instead.

### Missingness Dependency
For the MAR(Missing At Random) analysis, I will be investigating whether the missingness of the `pick1` column has any dependencies on the other columns in the dataset. The two other columns I explored in relation to `pick1` were `position` and `result`. I used the TVD(Total Variation Distance) as my test statistic and a standard significance threshold of 0.5. I defined a binary indicator column, `pick1_missing`, with the value being `True` when `pick1` is missing and `False` otherwise. I then performed a permutation test to determine the missing mechanism. 

First, I tested whether the missingness of `pick1` depends on `position`. 

**Null Hypothesis**: The proportion of missing values in pick1 is the same for team level rows and player level rows.

**Alternative Hypothesis**: The proportion of missing values in pick1 is NOT the same for team level rows and player level rows.

After performing the permutation test and computing the observed statistic (by computing the absolute difference in missingness rates of pick1 between rows where `position` == `team` and rows where `position` != `team`), I found that the p-value was 0 and the observed statistic was 0.9637656672401083. The plot below displays the empirical distribution of the TVDs. 

<iframe
  src="assets/mar_dependent.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
Since the p-value is less than the threshold of 0.5, I reject the null hypothesis. This shows a strong evidence of dependence between the columns. Therefore, the missingness of `pick1` depends on `position`. 

Second, I tested whether the missingness of `pick1` depends on match outcome, `result`. 

**Null Hypothesis**: The distribution of match outcomes is the same when pick1 is missing and when it is not missing.

**Alternative Hypothesis**: The distribution of match outcomes is NOT the same when pick1 is missing and when it is not missing.

After performing the permutation test, the resulting p-value was 1 and the observed statistic was 0.0. The plot below displays the empirical distribution of the TVDs. 
<iframe
  src="assets/mar_independent.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
Since the p-value is greater than the threshold of 0.5, I failed to reject the null hypothesis. Therefore, the missingness of `pick1` does not depend on `result`. 

## Hypothesis Testing
For the hypothesis test, I wanted to explore whether picking the champion Aurelion Sol during draft is associated with a significantly different win rate as opposed to picking any other champions. It is important to once again note that though Aurelion Sol has the highest win rate in the entire season, he is a champion that has been picked extremely infrequently. This raises the question of whether his apparent advantage in match outcome reflects an actual effect or could just be attributed to the random noise/variation that is often present in small sample sizes. 

**Null Hypothesis**: The probability of winning a match is the same for teams that pick Aurelion Sol and teams that did not pick Aurelion Sol. 

**Alternative Hypothesis**: The probability of winning a match is NOT the same for teams that pick Aurelion Sol and teams that did not pick Aurelion Sol. 

**Test Statistic**: The test statistic used is the difference in win rates between teams that picked Aurelion Sol and teams that did NOT pick Aurelion Sol. 

**Significance Level**: 5%

Below is a histogram that displays the distribution of the test statistics during the hypothesis test: 
<iframe
  src="assets/aurelionsol_hypothesis.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
The hypothesis test concluded a p-value of 0.3791. This is a large p-value that way exceeded the threshold, so we failed to reject the null hypothesis. This result is not surprising, as although Aurelion Sol appears to have a noticeably higher win rate than other champions, his win rate is based on an extremely limited sample size (number of times picked) in the 2022 professional season. Since Aurelion Sol was almost never drafted, not very many games invovled him, which eplains why his observed win rate is highly unstable. A win rate difference as extreme as the observed one occurs frequently just by random chance alone under the null hypothesis. The statistical evidence is insufficient to conclude that picking Aurelion Sol meaningfully increases or decreases a team’s probability of winning.

## Framing a Prediction Problem
Continuing on from the analysis that I performed on the previous sections, I wanted to explore the question: Could I incoporate champion picks as a predictive feature among other relavant features in a machine learning model in an attempt to predict the outcome of a match? Since I plan on predicting results column (target variable that contains a 0 or 1 indicating whether a team lost or won a match), my prediction problem would fall under the category of binary classification. My model is primarily based on champion picks and champion combinations, which are decided during the draft phase. 

Since the purpose of the model is to predict the outcome of a game before the game starts and after the draft selection, the model can only utilize information available before the game starts. Thus, I excluded any in game statistics as they would introduce potential data leakage. I will be using `pick1` - `pick5`, `ban1` - `ban5`, `side`, and `league`. 

To evaluate the performance of the classification model, I will be using accuracy (in this case the proportion of matches for which the model correctly predicts the outcome). Since the response variable `result` is exactly balanced, accuracy provides a meaningful insight and serve as an interpretable measure of overall model performance. Additionally, the main goal of the model is to correctly predict match outcomes and not to prioritize one class over the other, making accuracy the natural and appropriate choice. Other metrics such as the F1 score are more advantageous and suitable for scenarios with an imbalance in the target variable or cases where false positives and false negatives should be weighted differently. 

To avoid overfitting to training data, the data will be split into two parts: 80% training data, and 20% test data.

## Baseline Model
P-value is small.

## Final Model
P-value will always be small.

## Fairness Analysis
Unfair.
