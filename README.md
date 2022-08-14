# Prosper Loan Data Analysis
## by Carmen Wong


## Dataset

This [Loan dataset](https://www.google.com/url?q=https://s3.amazonaws.com/udacity-hosted-downloads/ud651/prosperLoanData.csv&sa=D&ust=1581581520570000) was from Prosper. It contain 113,937 loans with 81 variables on each loan from 2005-11-09 to 2014-03-10, including loan amount, borrower rate (or interest rate), current loan status, borrower income, and many others. The description of the 48 variables could be refer to this [variable dictionary document](https://docs.google.com/spreadsheets/d/1gDyi_L4UvIrLTEC6Wri5nbaMmkGmLQBk-Yx3z0XDEtI/edit#gid=0). 

### Wraggling
Due to the dataset was not clean and included a lot irrelavant data for my analysis, the following list of data quality and tidiness issues had been identified, cleaned and restructed for my analysis.

#### Data Quality Issues
* Duplicate rows
    * There were 871 rows with same ListingKey and ListingNumber
    * Theese duplicated row were dropped
    
* Employment Status 
    * Both 'Full-time' and 'Part-time' were changed to 'Employed'
    * NaN is same as 'Not available'. They were changed to 'Not-available' to be consistent with 'Self-employed'
    * Change 'Not employed' to 'Unemployed'
    
* CreditScoreRangeLower and CreditScoreRangeUpper
    * Replaced the NaN value with the mean
    * Dropped the 133 rows with zero CreditScoreRangeLower
    * Added a column for the average credit score 'AvgCreditScore'

* ProsperScore
    * Rename the column name to ProsperRiskScore. That's more accurately reflected the description according to the variable dictionary
    
* IncomeRange
    * 'Not employed' is not a salary range. Changed those values to '$0' since 'Not employed' has no income.

#### Data Tidiness Issues
* CreditScoreRangeLower & CreditScoreRangeUpper has a strong linear relationship and it is more useful to take the average of them. Added a column for the average credit score 'AvgCreditScore' and dropped both CreditScoreRangeLower & CreditScoreRangeUpper columns



## Summary of Findings
* 77.12% of the loans are with term of 36 months
* 21.45% of the loans are with term of 60 months
* 10.59% of the loans are charged off
* 04.39% of the loans are defaulted
* 33.67% of the loans are completed
* 49.35% of the loans are current
* CA, FL, NY, TX and IL are the top 5 states carried the most loans
* CA is the top number 1 states carried the most loans and by more than double compare to the second most loans, TX state
* During the period from 2005-11-09 to 2014-03-10, 
    * The average annual borrowing rate is 19.28%; the minimun is 0% and the maximum is 49.75%
    * The average anuual borrowing APR is 21.88%; the minimun is 0.6% and the maximum is 51.23%
    * The difference between annual rate and annual APR is about 2.6%
* Majority of people are in the income range between $25,000 to $74,999
* The average credit score is 695.83. The highest is 889.50 and lowest is 369.50
* There is a strong relationship between rate and APR
* People with higher credit score got lower rate and lower APR loans
* Most people with credit score above 700 got loans with 10% or lower
* People with credit score lower than ~520 can not get a loan
* Overall, people with higher credit score got large amount of loans
* People with credit score between ~725 to ~875 got loans with &#36;35,000
* People with credit score between ~620 to ~725 got loans with &#36;25,000
* However, people with credit score closer to 900 didn't get many loans. A valid assumption here is perhaps that they didn't need it
* People with income below &#36$50,000; got more smaller amount (~5000) of loans
* People with income of &#36100,000 or moe got less loans but bigger amount of loans
* Most of the loan ~&#36;7500 and below were either 12 months or 36 months term
* Most of the loan higher than ~&#36;7500 were 60 months term
* I was surprise to see the trend that people started to borrow money from August and trailed off after January. I was thinking people need the most money in October to early November time frame to prepare for the holiday
* People with higher loan amount actually paid less in interest
* Surprise to find there were a few deliquencies with credit score of 850
* I found scatter plot is very useful to see a overall relationship, expecially with alpha option



## Key Insights for Presentation
* I was surprised to see the trend that people started to borrow money as early as August and trailed off after January. My impression was people need the most money in October to early November time frame to prepare for the holiday and before Summer start
* California is the number one state that carried the most loans and is double the number of loans of the second most state, Texas.
* You need credit score above 730 to get loans above $25,000 and you most likely can not get any loan if your credit score is less than 530.
* People with loan higher then $25,000 actually paid less in interest rate than lower amount of loans.
* Surprise to find there were a few deliquencies with credit score of 850

