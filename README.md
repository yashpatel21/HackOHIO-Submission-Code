# HackOHI/O Submission Code

### Team Gray 57

### Problem Statement:
How can we utilize machine learning algorithms to propose student loan forgiveness policies as solutions for the student loan debt crisis and recessions?

### Methodology:
We examined the relationship between student loan debt and the probability of a recession in the near future, as well as the effects of proposed student loan forgiveness policies as a solution. The Federal Reserve Bank of St. Louis’s website (FRED) was used to extract data regarding total GDP per quarter and student loan debt per quarter. Through the combination of the student loan debt per quarter and total GDP per quarter datasets, the percentage of total GDP composed of student loan debt per quarter was calculated and fitted to a logistic curve. Future quarterly values for total GDP and the percentage of total GDP composed by student loan debt per quarter were found through Long Short Term Models and Euler’s Method, respectively. Through the creation of a probability of recession index, the probability of recession per quarter was compared to the percentage of total GDP composed by student loan debt per quarter to construct an exponential regression model. Utilizing a primarily quantitative method of analysis, the percentage of total GDP composed by student loan debt per quarter was found to be strongly associated[p < 1.26696* 10-8] with the probability of recession per quarter(p(R)), with the p(R) tending to peak as the percentage of total GDP composed by student loan debt per quarter strayed away from the carrying capacity of the logistic curve.

### Results/Solution:
Inputting 5 different student loan debt forgiveness policies into our algorithm gives us the following results:

![Results](https://github.com/yashpatel21/HackOHIO-Submission-Code/blob/main/probabilities_results.png)

We disregarded forgiving all student loan debt as the best approach, as this was obvious, and our intention was to find a more viable approach. As a result, we conclude that the long-term student loan forgiveness plan based on the average requirements of borrowers is the best solution. This plan is based on the fact that the average borrower requires forgiveness of $40,000 in student loans, and this would result in an overall decrease of $901B in student loan debt. Utilizing this plan would have the largest impact on decreasing the probabilities of recession to about 7.25978*10-42%.


### Code Files:

#### train.ipynb

-   Trains an LSTM model to predict GDP for a set number of quarters.
-   Save the LSTM model to ./models/final_model.h5

#### predict.ipynb

-   Loads the saved LSTM model from ./models/final_model.h5
-   Predicts GDP for 2019 Q4 to 2021 Q2
-   Saves predicted GDP data to ./final_gdp_pct.csv

#### recession probability.ipynb

-   Uses the method described in [Chauvet and Hamilton (2005)](http://dss.ucsd.edu/~jhamilto/chauvet_hamilton_may_05.pdf) to find probability of recession occuring for a quarter based on that quarter's gdp growth.
-   Uses data from ./final_gdp_pct.csv to calculate probability of recession for 2019 Q4 to 2021 Q2.
-   Saves predicted recession probabilities data to ./final_rec_prob.csv

#### student loans regression.ipynb

-   fits a logistic curve to 1993-2008 data, and then 2009-2019 data.
-   Uses Eulers Method to predict student loans over gdp for 2020.
-   Conducts correlation and exponential regression between 2008 student loan over gdp and recession probabilities, and then 2020 student loan over gdp and recession probabilities.
-   Uses the 2020 exponential regression model to predict recession probabilities for 2020 if either Elizabeth Warren's or Pete Buttigieg's student loan debt forgiveness policies are applied.
