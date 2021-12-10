# INF624_FinalProject
Using Asset Prices to Predict the Price of Bitcoin
Author: Chuck Harrington
-------------------------------------------------------
Overview
The purpose of this project is to predict the price of Bitcoin using the NASDAQ Composite index and the price of gold in order to take advantage of the volatile price of Bitcoin.
RStudio was used to create a multiple linear regression model that used data collected on the NASDAQ Composite Index, Bitcoin and gold.  These data are used to train the multiple linear regression model with a second set of data for the predictor variables, the NASDAQ Composite Index and price of gold, to test the model’s ability to predict the price of Bitcoin.  There are 1255 data points collected for each of the three variables.  70% or 878 data points are used to train the model with the remaining 377 data points used for testing.  These data are included in the .csv files and can be used to recreate the results of the project.   
These data points have been cleaned and match the values generated each day that the U.S. stock market is open during a five-year period from October 2016 – October 2021. 
-------------------------------------------------------
Installation and Use

Preliminary steps:
Installation of RStudio will be required:  https://www.rstudio.com/products/rstudio/ 
Download the five .csv files from this project.
In RStudio:
Point RStudio to the location of the downloaded files 
	File -> change dir…
	Navigate to the appropriate location where the five .csv files are located.
These files are now ready to be used in RStudio to recreate the multiple linear regression model.  Please note that two files are included in the GitHub documentation.  “Project Code.r” is the code formatted for R and “Project Code_Text” contains the same information but is a plain text version.

-------------------------------------------------------
