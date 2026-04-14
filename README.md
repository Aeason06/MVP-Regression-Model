#  Using Logistic Regression to Predict the NFL MVP 
@AustinCEason<br>
# Introduction
In this project, I will attempt to use NFL data from 2016-2025, sourced from nfl_data_py and pro-football-reference, to predict the 2025 NFL MVP winner. At this point (March 23rd, 2026), it is known that Matthew Stafford won the award, but we can still gather information on what makes a player likely to win MVP and use that to predict future MVPs. <br>

Two things to consider before going any further are: One, MVP is influenced heavily by narrative, which doesn't show up on the stat sheet. Two, betting odds will not be used as a predictor because they are very weak at the start of the season and too strong at the end. I want week-to-week consistency. On top of that, please do not use anything in this repo as betting advice. <br>

# Analysis
To start, I pulled the stats of all QBs to start a minimum of 14 games in each season from 2016 to 2024. Here is a table of the stats that I thought might be useful:
| Variable          | VIF       |
| ----------------- | --------- |
| aggressiveness    | 1.6674    |
| cpoe              | 2.7505    |
| rtg               | 9.5986    |
| age               | 1.2502    |
| tot_Yds           | 2.8738    |
| tot_TD            | 4.1865    |
| TO                | 2.7631    |
| succ_pct          | 4.8063    |
| y_c               | 2.2481    |
| four_qc           | 3.9318    |
| gwd               | 4.1550    |
| Wins              | 2.3669    |
| db_epa            | 8.5048    |

I then assigned a column to each player, containing 0 or 1, indicating whether they won MVP that year. Since only one player can win the MVP every year, the dataset was incredibly unbalanced. Which means we need to make sure we don't create a dumb model, which will be discussed later. <br>

In the table above, you can see VIF (Variance Inflation Factor) values. For the most part, all of the features have a VIF below 5, so multicollinearity is not a concern. Aside from passer rating (rtg) and drop-back EPA (db_epa), which are likely highly correlated. <br>

After looking at different logistic regression models, the features I decided to use were total touchdowns (tot_TD), Wins, drop-back EPA, and aggressiveness. Agressiveness is the percentage of passes a QB threw where the receiver had a yard or less of separation. Heres the model output: <br>

![MVP MO.png](https://github.com/Aeason06/MVP-Regression-Model/blob/main/images/MVP%20MO.png)
<br>

In this output, we can see that Wins are a much stronger predictor than everything else. 


