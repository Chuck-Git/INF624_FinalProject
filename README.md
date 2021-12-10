# INF624_FinalProject #
# Using Asset Prices to Predict the Price of Bitcoin #

Author: Chuck Harrington
-------------------------------------------------------
## Overview ##

### The purpose of this project is to predict the price of Bitcoin using the NASDAQ Composite index and the price of gold in order to take advantage of the volatile price of Bitcoin. ###
-------------------------------------------------------
RStudio was used to create a multiple linear regression model that used data collected on the NASDAQ Composite Index, Bitcoin and gold.  These data are used to train the multiple linear regression model with a second set of data for the predictor variables, the NASDAQ Composite Index and price of gold, to test the model’s ability to predict the price of Bitcoin.  There are 1255 data points collected for each of the three variables.  70% or 878 data points are used to train the model with the remaining 377 data points used for testing.  These data are included in the .csv files and can be used to recreate the results of the project.   
These data points have been cleaned and match the values generated each day that the U.S. stock market is open during a five-year period from October 2016 – October 2021. 
-------------------------------------------------------
## Installation and Use ##

Preliminary steps:

Installation of RStudio will be required:  https://www.rstudio.com/products/rstudio/ 

Download the five .csv files from this project.

In RStudio:

Point RStudio to the location of the downloaded files 

 File -> change dir…

 Navigate to the appropriate location where the five .csv files are located.

These files are now ready to be used in RStudio to recreate the multiple linear regression model.  Please note that two files are included in the GitHub documentation; “Project Code.r” is the code formatted for R and “Project Code_Text” contains the same information but is a plain text version.
-------------------------------------------------------
# Coding Steps for Creating the Prediction Model #

'''**Read in the training and test files**

These data do not include a header and any null value will be replaced by the "?"

*Training data*

bit=read.csv("bit.csv", header=F, na.strings="?")

nas=read.csv("nas.csv", header=F, na.strings="?")

gld=read.csv("GoldTraing.csv", header=F, na.strings="?")

*Test data*

nasTest=read.csv("NASTest.csv", header=F, na.strings="?")

gldTest=read.csv("GoldTest.csv", header=F, na.strings="?")

*Create the multiple linear model and store it in the variable called mrm*

bit$V1 is the Bitcoin trainig data with the column data stored in variable "V1"

bit$V1 is the outcome variable

nas$V1 is the NASDAQ Composite Index trainig data with the column data stored in variable "V1"

gld$V1 is the gold trainig data with the column data stored in variable "V1"

nas$V1 and gld$V1 are the predictor variables

mrm = lm(bit$V1~nas$V1+gld$V1)

*Use the summary() command to identify key information*

summary (mrm)

*To visualize the data relationships, create scatterplots by using the plot () command*

plot (mrm)

*Use the multiple linear regression model created (mrm) to predict the price of Bitcoin
The test data replaces the training data for both the NASDAQ Composite Index and the price of gold, the predictor variables
The interval "confidence" is used to generate a predicted value with 95% confidence interval*

predict(mrm, data.frame(nas=nasTest, gld=gldTest), interval = "confidence")'''



-------------------------------------------------------
