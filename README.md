# MEASURING THE IMPACT OF DISCIPLINE ON NBA PLAYER PERFORMANCE (2018)


## BUSINESS PROBLEM
The NBA league office, comprised of the league comissioner and his cabinet, is responsible for handing out discipline to players upon review or investigation of questionable incidents.  In addition to league discipline, individual teams may punish their players for violating team rules.  Bearing this in mind, the league and especially its teams need to understand the perhaps unforeseen on-court impact that disciplinary actions may have on player performance, if a team intends to optimize its on-court performance and if the league wants its players to play to their capabilities.  This study estimates the average effect that NBA player suspensions have on player performance, and by accomplishing this task, team management can better anticipate the impact that suspensions have on player productivity post-suspension.  Such information will potentially yield results that would allow teams to adjust their gameplans to improve overall team performance.


## METHODOLOGY
1. Obtain data from spotrac.com  on NBA player suspensions, including duration and cause
2. Establish a measure of player performance (game score) and on-court player behavior (per-36 mins: true shooting attempts, personal fouls, turnovers) for each suspended player, and obtain from basketballreference.com
3. Observe the mean difference in player performance and behavior post-suspension and perform t-tests to test for statistically significant differences
4. Model statistics with significant changes (game score only) as a function of player and suspension characteristics

Explanatory Variable Formulation
<img width="1512" alt="explanatory_variables" src="https://github.com/user-attachments/assets/5186faf2-7809-4b42-b8a8-107cb7a99ce4">

Empirical Model Construction

<img width="790" alt="model1" src="https://github.com/user-attachments/assets/f557f531-8a10-4bde-8a74-b7a4ad95db4e">

<img width="790" alt="model2" src="https://github.com/user-attachments/assets/ff4b7f9e-d32a-4cde-9af9-1d2bc1d333f0">

<img width="789" alt="model3" src="https://github.com/user-attachments/assets/71892c94-5052-4dd8-9c98-79af87ed9da3">

<img width="790" alt="models456" src="https://github.com/user-attachments/assets/26b3d4b0-8a5b-4c94-8361-5edcc00bb6eb">

## SKILLS
1. Statistical Analysis - Performed in R, re-run in Stata
2. Supervised Machine Learning (Multiple Linear Regression) - Performed in R and Stata
3. Stepwise Model Building

## RESULTS & BUSINESS RECOMMENDATION

<img width="767" alt="mean_calcs" src="https://github.com/user-attachments/assets/93be55cf-4b6f-4eaa-9cc5-80a42411d08b">

In determining whether or not suspensions have an effect on player performance, the mean calculations show that suspensions have a negative effect on player performance.  That is, a suspension on average causes game score and true shot attempts to decrease, and causes personal fouls and turnovers to increase on average in a player’s first game following a suspension.  

<img width="837" alt="welch_ttests" src="https://github.com/user-attachments/assets/c57c438f-8b0c-45dc-b073-005f8b3131fc">

However, the results of the Welch’s t-test clearly indicate that the only difference which is statistically significant at the 95% significance level was the decrease in average game score.  This result implies that the behavioral changes in player aggressiveness or composure that the study sought to quantify were statistically nonexistent.  However, because these other three response variables comprise the negative terms in game score’s calculation, the fact that their differences are statistically equivalent to zero indicates that at least one of the positive terms in the equation is decreasing from pre-suspension to post-suspension, provided that the true difference in game score is negative.

<img width="845" alt="Regression_Results" src="https://github.com/user-attachments/assets/64b48ca6-74d7-45c7-a43b-77f3139beb9b">

Using linear regression to determine the possible determinants of the negative suspension effect on game score showed that some of the change in game score can be attributed to the maturity characteristics described in model 1.  In particular, it is interesting to observe the differences between veteran and non-veteran players as age increases.  The graph below shows the game score effect versus age by veteran status, and from the graph it is apparent that older, non-veteran players suffer the least among all groups when returning from a suspension.  In fact, after the age of 24, game scores for non-veterans increased from their pre-suspension level on average.  Veterans and non-veterans have nearly identical changes to their game score post-suspension at age 23, but once a player has four years of experience, there is a negligible marginal effect on game score due to aging.  

<img width="850" alt="Regression_Plot_Vet_NonVet" src="https://github.com/user-attachments/assets/a548e9f4-9ab2-4bb8-8966-96790cec3d67">

In Model 2, it is clear that the change in game score can also be partially attributed to effects stemming from multi-game suspensions and suspensions resulting from physical altercations (in addition to the maturity effect described earlier).  Multi-game suspensions decrease game score post-suspension by 7.046 per 36 minutes on average, and this marginal effect is significant at the 5% level.  Although the coefficient on the variable for suspensions from physical altercations is not significant, this variable’s interaction with the multi-game suspension dummy variable is significant at the 1% level, and implies that players returning from a multi-game suspension resulting from a physical altercation boost their game score by 13.09 per 36 minutes on average. 

Across both regression models, minutes played is not significant in explaining the change in game score from pre to post-suspension.  However, minutes played is significant in Model 4.  Among all of the explanatory variables used in the study, minutes played is the only one that can be changed after a suspension occurs, and would yield an interesting result in a player-personnel scenario if Model 4 is indeed valid. 

For example, if player A is playing his first game since being suspended, his game score this game (GS’A) will be affected by the minutes he plays in this game divided by 36 (minsA/36), multiplied by the sum of the game score effect per 36 minutes (α = Model 4 equation) and his average game score per 36 minutes before the suspension (α + GSA).  Mathematically,
GS’A = (minsA/36) * [GSA + α]     

If player B is not a player coming off of a suspension and is the best and only possible replacement for player A, he will play (48 - minsA) in this game, and is expected to have a game score of [(48 - minsA)/36] times his average game score per 36 minutes (GSB).  Mathematically,
GS’B = [(48 - minsA)/36] * GSB   

The personnel decision would come from choosing an amount of minutes for player A, in order to maximize productivity for this position (GS’A + GS’B), under the constraint minsA + minsB = 48.  This could be very useful for NBA team front offices and coaching staffs who seek to optimize the team’s productivity at the position of the player who was previously suspended. 
