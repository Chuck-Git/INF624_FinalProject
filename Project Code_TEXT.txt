# Author: Chuck Harrington
# Project title: Using Asset Prices to Predict the Price of Bitcoin
# December 10, 2021
# INF624: Predictive Modeling
####################################################################

# Coding Steps for Predict Project 

# Read in the training and test files
# These data do not include a header and any null value will be replaced by the "?"

# Training data
bit=read.csv("bit.csv", header=F, na.strings="?")
nas=read.csv("nas.csv", header=F, na.strings="?")
gld=read.csv("GoldTraing.csv", header=F, na.strings="?")

# Test data
nasTest=read.csv("NASTest.csv", header=F, na.strings="?")
gldTest=read.csv("GoldTest.csv", header=F, na.strings="?")

# Create the multiple linear model and store it in the variable called mrm
# bit$V1 is the Bitcoin trainig data with the column data stored in variable "V1"
# bit$V1 is the outcome variable
# nas$V1 is the NASDAQ Composite Index trainig data with the column data stored in variable "V1"
# gld$V1 is the gold trainig data with the column data stored in variable "V1"
# nas$V1 and gld$V1 are the predictor variables
mrm = lm(bit$V1~nas$V1+gld$V1)

# Use the summary() command to identify key information
summary (mrm)

# To visualize the data relationships, create scatterplots by using the plot () command
plot (mrm)

# Use the multiple linear regression model created (mrm) to predict the price of Bitcoin
# The test data replaces the training data for both the NASDAQ Composite Index and the price of gold, the predictor variables
# The interval "confidence" is used to generate a predicted value with 95% confidence interval
predict(mrm, data.frame(nas=nasTest, gld=gldTest), interval = "confidence")

########## END ##########
