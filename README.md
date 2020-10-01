# Analyzing-Expected-vs-Actual-Betting-Odds
An in depth analysis of implied odds vs the true odds of betting on a sportsbook

## Background
While the Coronavirus Pandemic has affected nearly all aspects of our lives, the impact that this virus will have on state budgets will be felt for years to come.  One of the easiest ways to raise tax revenue is to legalize sports betting, a trend that has been slowly making its way through the United States.  As of now, 18 states have legalized sports betting, 4 more have legalized it and will be operational by the end of 2020, and more states are discussing legalization.  Nearly every state has discussed a sports betting bill, and the need for more tax revenue will accelerate the legalization process in the years to come.

With a new industry emerging, there are new possibilities to make profit off of these sportsbooks.  The number of professional sports betters is increasing dramatically, as they look for a way to profit off of sportsbooks.  These betters attempt to analyze thousands of datapoints in order to create more efficient algorithms to predict game scores than the oddsmakers in Vegas.  If they succeeed, there is an incredible amount of profit.  If they do not, they waste hundreds of hours of time, resources, and money.  This project will not attempt to replicate the predictive models of professional sports betters, but it will instead analyze just how difficult it is to make a profit off of sportsbooks.

## Business Question
How hard is it for a professional sports better to consistently make a profit off of the sportsbook's betting odds?


## Data Question - Open Data
Data Source: [OddsShark.com](https://www.oddsshark.com/nhl/database)
- [My Raw Data](https://github.com/AdamShmanske/Analyzing-Expected-vs-Actual-Betting-Odds/blob/master/NHL%20Sports%20Betting%20Analysis%20and%20Excel%20Instructions.xlsx)

- OddsShark is a publicly available sports betting database.  This database provides up to 30 games worth of data at a time for an available team.  240 datapoints were downloaded from teams in the Metropolitan Division of the NHL (30 games for each team) in order to create this project.  This data source provided game score, winning betting odds, home and away team, and over/under betting odds.  This data was further seperated using tables into Home Team Wins?, Home Team Betting Odds, and Over Wins in order to analyze the data.



## Data Question and Graphical Answer
### How hard is it for a professional sports better to consistently make a profit off of the sportsbook's betting odds?

Using Microsoft Excel's data analyis tool, a linear regression model will be created to measure the correlation between different variables and a home team win.  Home team win will be in the Y input, and home team betting odds and over/under hitting will be in the x input.

It is important to note (for those unfamiliar with sports betting) what exactly a betting odd means.  Betting odds of +100 on a $5 bet means that you either win the bet (gaining $5) or lose the bet (losing your $5 you put in).  In this scenario, the expected values are either $0 or $10, and to have a net expected value on this bet this must mean that both winning and losing have an equal chance of occurring ( (10+0) / 2 ).  Thus, for a +100 bet, the implied probability of this bet hitting (if Sportsbooks gave perfectly fair odds and did not take a cut) is exactly 50%.  A more detailed explanation of how to calculate implied probability for different betting odds is provided in the excel directions (located at the bottom of this repository).

Below is the first regression performed comparing home team wins, home team betting odds, and over/under hitting.  This regression analysis has a very low R squared value of 0.03.  When looking into the two variables,

![alt text](https://github.com/AdamShmanske/Analyzing-Expected-vs-Actual-Betting-Odds/blob/master/Regression%201.png)



![alt text](https://github.com/AdamShmanske/Analyzing-Expected-vs-Actual-Betting-Odds/blob/master/Regression%202.png)


![alt text](https://github.com/AdamShmanske/Analyzing-Expected-vs-Actual-Betting-Odds/blob/master/IP%20vs%20Actual%20Odds%20Graph.png)

## Business Answer



## Excel Directions
