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

