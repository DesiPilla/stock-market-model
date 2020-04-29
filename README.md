# Purpose

This is the final project for the course Introduction to Machine Learning (CISC 684) at the University of Delaware. The course instructor is Dr. Amo Tong. The team members associated with this project are Kleio Baxevani, Prem Chand, and Desiderio Pilla, who are all students in the Master of Science in Data Science (MSDS) program at UD.

# Problem Statement
The goal of this project is to create an algorithm that increases the profit realized by investors. This goal will be acheived by using two models, a Logistic Regression and Neural Network. The data was scraped from the internet for individual stocks. This includes daily price and trading data, as well as earnings data for every quarter since 1995. The scraped data was manipulated to calculate a variety of value- and momentum-based metrics.

# Premise

## Background

---
The stock market is a platform through with securities (also referred to as shares, stocks, equity, etc.) are traded daily. When an individual or corporation buys a share of a stock, they are purchasing a fraction of ownership of the publicly traded company the stock belongs to. 

The price of a single share changes throughout the business hours of the stock exchange it is traded on, normally 9 am to 5 pm, Monday to Friday in the United States. During these hours, the market is *open*, and securities can be bought and sold freely. When the market closes, no securities can be traded. The price of a share can fluctuate between the close of the market and the next time it opens; often, news or earnings reports about a company can have a major impact on the value of a stock, and take place after market hours. Investors are unable to trade shares of any company until the market opens, by which the opening share price will already reflect the new information revealed since the previous day's close. Some institutions are given the ability to trade pre- and post-hours, but not the typical investor.

There are many economic metrics used to measure the value of a security. There are *momentum* indicators, which measure if the price of a share is rising, falling, how quickly, and for how long. There are *value* metrics, which compare the *actual* price of a security with a mathematical calculation of what the price *should* be. This calculation varies for every analyst, though some common metrics take into account a companiy's revenue, profit, cash flow, liabilities, etc.

## Goal

---

The goal of this project is to create an algorithm that increases the profit realized by investors. 

## Methods

---

This goal will be acheived by using two models, a *Logistic Regression* and *Neural Network*.

The data was scraped from the internet for individual stocks. This includes daily price and trading data, as well as earnings data for every quarter since 1995.

The scraped data was manipulated to calculate a variety of value- and momentum-based metrics.

For each trial, a testing date is given. The training data includes a 1 or 2 year period (chosen as a hyperparamter of the model) occurring at least *n* days before the testing date. The test data is comprised of the 6 month period following the testing date.

*N* corresponds the the classifcation of an instance. This data has a binary classification defined by whether or not the price of the security increased *n* business days after the current date. It is for this reason that there must be a gap of *n* days between the training and test data. This value is also selected as a hyperparameter of the model. Predicting the price of a stock 1 day into the future (which would practically yield the highest returns), is nearly impossible. It is unrealistic to do so given the feature spaced used in this project, as no geopolitical or media information was gleaned.

*Note: This model does not take dividend payouts into account, and all stock prices are split-adjusted.

## Performance

---

Economic climates can vary by month, quarter, and year. To gain a more accurate understanding of a model's performance, every 6 month period was tested from the period beginning on January 1st, 2003 to the period beginning on January 1st, 2016 (which ends on July 1st, 2016). The total returns of the model are then aggregated and compared with the total returns of the *unengaged investor*.

The *unengaged investor* is a control group to compare the model against. Many analysts try to predict the market, and end up making less money than they would have if they didn't do anything. The *unengaged investor* mimics the returns that would be realized if a stock was bought on the first day of a period and kept untili the final day of the period (also referred to at the *static return*). The model buys and sells a security each day depending on the predicted classification of the test data. 

When an instance is classified as True (meaning the model expects the share price to increase in the future), the model buys a share of the stock. It then holds the stock until it classifies an instance as False (meaning the model expects the share price to decrease in the future). The maximum returns would be realized if the model were to buy a security the day before it increases, and sell it the day before it decreases, for every day in the test period. The inverse is also possible, which would be the worst case.

The performance of this model will not be measured by the accuracy of its predictions. Rather, the most practical measurement of this model are to compare its returns to the *unengaged investor*. If the model produces higher returns than an investor who did not use the model and merely held a security for the duration of the period, than utilizing the model to guide investment decisions will have been worthwhile.

*Note: Other measures of success could have also been selected. For example, one could have optimized the model to reduce volatility or minimize losses. This project, however, optimizes the model by maximizing returns without regard for volaility or short-term losses.*

# Evaluation

## Results

Below are the annualized returns of each model for the tested companies:

|Stock                   |Static Return|Logistic Regression|Neural Network|
|-----------------------:|------------:|------------------:|-------------:|
|Amazon.com, Inc.        |30.55%       |**31.51%**         |21.95%        |
|DuPont de Nemours, Inc. |3.69%        |**5.66%**          |**7.93%**     |
|Exxon Mobil Corporation |7.46%        |**11.74%**         |**13.47%**    |
|IBM Corporation         |4.80%        |**7.66%**          |**8.31%**     |
|Johnson & Johnson       |5.90%        |3.70%              |**7.25%**     |
|J.P. Morgan Chase & Co. |6.84%        |1.95%              |**8.92%**     |
|Microsoft Corporation   |4.89%        |**7.79%**          |**6.55%**     |
|Walt Disney Co          |13.83%       |13.68%             |**16.11%**    |

*Bolded returns reflect annualized returns that were greater than the unengaged investor*

## Conclusions

The above chart shows that the model was able to successfully outperform the unengaged investor for all 8 securities tested. Companies were chosen from a broad range of sectors to test the robustness of the model.

The logistic regression proved to be the more lucrative investing technique for 5/8 holdings, with an average return of 0.72% /yr greater than the static return.

The neural network proved to be the more lucrative investing technique for 7/8 holdings, with an average return of 1.57% /yr greater than the static return. Among the 7 stocks in which the model performed better, the average return was 3.02% /yr greater than the static return.

## Recommendations

While the model appears to have performed well, I would not recommend using this to guide any investment decisions. The use of averaging over many years and multiple economic cycles is naiive, expecially considering the lack of information used in the decision making process of these models. This model can serve as a guide, but it should not be used to pick which securities to buy. **The purpose of this model is to maximize the returns of a holding, not to give input on which stocks will outperform others.**