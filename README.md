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
## Technologies ##

This project was created with: 

- RStudio version 4.1.1

- Microsoft Excel

-------------------------------------------------------
## Installation and Use ##

Preliminary steps:

Installation of RStudio will be required:  https://www.rstudio.com/products/rstudio/ 

Download the five .csv files from this project.

In RStudio:

Point RStudio to the location of the downloaded files:
- File -> change dir…
- Navigate to the appropriate location where the five .csv files are located.

These files are now ready to be used in RStudion to recreate the multiple linear regression model.  Please note that two files are included in the GitHub documentation; "Project Code.r" is the code formatted for R and "Project Code_TEXT" contains the same information but is a plain text file.

-------------------------------------------------------
## Coding Steps for Creating the Prediction Model ##

**Read in the training and test files**

These data do not include a header and any null value will be replaced by the "?"

*Training data*

![DataIn](https://user-images.githubusercontent.com/95941708/145654209-d63be5d7-dda5-44e6-95a0-69b16ef2fe1d.PNG)

```
bit=read.csv("bit.csv",header=F,na.strings="?")
nas=read.csv("nas.csv",header=F,na.strings="?")
gld=read.csv("GoldTrain.csv",header=F,na.strings="?")
```
*Test data*

![TestIn](https://user-images.githubusercontent.com/95941708/145655567-61a3c6d7-59df-49d7-b76b-0de9ac2ee1a2.PNG)

```
nasTest=read.csv("NASTest.csv",header=F,na.strings="?")
gldTest=read.csv("GoldTest.csv",header=F,na.strings="?")
```
**Create the multiple linear model** 

*Use lm() to create the model and store it in the variable called mrm*

*Use the summary() command to identify key information*

- bit$V1 is the Bitcoin trainig data with the column data stored in variable "V1"

- bit$V1 is the outcome variable

- nas$V1 is the NASDAQ Composite Index trainig data with the column data stored in variable "V1"

- gld$V1 is the gold trainig data with the column data stored in variable "V1"

- nas$V1 and gld$V1 are the predictor variables

![Model_Summary](https://user-images.githubusercontent.com/95941708/145654306-1bb8bcdb-32ac-460c-8566-d79d43c469ab.PNG)
```
mrm=lm(bit$V1~nas$V1+gld$V1)
summary(mrm)
```

*To visualize the data relationships, create scatterplots by using the plot () command*
```
plot (mrm)
```
*Use the multiple linear regression model created (mrm) to predict the price of Bitcoin
The test data replaces the training data for both the NASDAQ Composite Index and the price of gold, the predictor variables
The interval "confidence" is used to generate a predicted value with 95% confidence interval*

![predictData](https://user-images.githubusercontent.com/95941708/145654389-82e9590e-9038-4b69-a57e-81900ae23645.PNG)
```
predict(mrm,data.frame(nas=nasTest, gld=gldTest),interval = "confidence")
```
-------------------------------------------------------
# Conclusion #

While this exercise was effective, the price of Bitcoin is difficult to predict using the multiple linear regression model created.  The r-squared value of 46% indicates a low level of accuracy and with the value of Bitcoin being as volatile as it is, this model is of little use in this capacity.  
