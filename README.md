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

Below is the first linear regression performed comparing home team wins, home team betting odds, and over/under hitting.  This regression analysis has a very low R squared value of 0.03.  When looking into the two variables, it is clear that Over Hits has a very low relation to the Y variable, with a p-value of 0.55 (far greater than the 0.05 cutoff).  Additionally, the significance F, a measure of how closely the variables contribute to the final equation is high, at 0.0096.  This makes sense, as the over hitting likely has very little relation to the home team winning.  Thus, a new linear regression model was performed using exclusively implied probabiliy odds.

![alt text](https://github.com/AdamShmanske/Analyzing-Expected-vs-Actual-Betting-Odds/blob/master/Regression%201.png)

Below is the second linear regression performed comparing home team wins, and home team betting odds.  This regression still has a very low r-squared value.  However, the p-value for the implied probability is very low at 0.00275.  This means that the implied probability factor is a very accurate indicator of the home team winning or losing.  The intercept has a coefficient of -0.058, and a p-value of 0.77.  This is a high p-value, and likely most of the error comes from the very low winning percentages on the graph (such as less than 5% since a team cannot have a negative winning percentage). Additionally, even with these flaws the variables more closely predict the data, with a significance F value of 0.00275.  The coefficient for the implied probability factor is 1.04.  This yields a linear regression formula of -0.058 + (1.04 x Implied Probability).  While this is very difficult to conceptualize, a visual display of this data is much easier to understand.

![alt text](https://github.com/AdamShmanske/Analyzing-Expected-vs-Actual-Betting-Odds/blob/master/Regression%202.png)

The graph below is a scatter plot comparing perfect odds, expected odds, and the true odds that our linear regression formula estimates. The X-axis shows implied winning odds.  In an ideal world, if you have a 50% chance of winning a bet through odds (see +100 example above), you should win the bet 50% of the time.  This is represented by the blue points on this graph.  The linear regression equation for this graph is Y=X, and the R-squared value is a perfect 1.  The orange points on the graph are the predicted true odds from our linear regression equation created above.  For example, to find the true expected value for a +100 bet, you calculate (-0.058 + (1.04 x 50%)) to find 46.2% as the true betting odds for this bet.  The linear regression equation for this graph is -0.058 + (1.04 x Implied Probability), and has an extremely high R-squared value of 0.997.  As you can see, the true betting odds for all points on this line are all below the "perfect" betting odds if Sportsbooks did not take a cut.

![alt text](https://github.com/AdamShmanske/Analyzing-Expected-vs-Actual-Betting-Odds/blob/master/IP%20vs%20Actual%20Odds%20Graph.png)

## Business Answer
While the data has been analyzed and multiple linear regression models have been performed, you may be wondering in simple terms how this answers the question "How hard is it for a professional sports better to consistently make a profit off of the sportsbook's betting odds?".  


## Excel Directions
Detailed instructions and all calculations performed in this project can be found by clicking this link.
