# PortfolioValCalcEngine
# Few Assumptions:
- Position Feed file name "PositionFile.txt" is the feed file configured in the spring config which contains the feed data. This file is configured to be part
  of src/resources
- I have simple trigger(which generates position statement of the portfolio for every 5 mins which is configured) and cron trigger which generates position 
  statement at 5 PM Mon-Fri


# Changes:
  - I have updated the formula for GBM to remove 7257600 , since didn't understand the meaning of it and also the 
  delta t which is within 0.5-2 secs , the formula gives me same stock price all time. Might be I have missed something here.
  - European call/put calculation- I have used 252 as business days for calculating Time to maturity . 
    Also when TimeToMaturity is zero ,intrinsic value is used as option price 
 
# How to run the program
 - Download the zip file , unzip it.
 - Make sure you have jdk  1.7 or 1.8  and ant version greater than 1.10
 - run ant from the directory where build.xml is located
 - Ant automatically does downloading of jars from repo using ivy , and then compile,jar,run
 Note:Application will be running continuously  and keep printing NAV on the console and generate text file as per the config in the spring in the simpleTrigger and cronTrigger
  - Ant task "junitreport" runs the independent test cases added
 
 
# Few Things to Improve from my side : 
  - We can implement Filewatcher for position feed file 
  - As of now for this application i  have implemented via single thread in the sense timer thread is responsible for generating market data , updating listening and also invoking the console publisher.
  Might be if needed we can parallelise  based on the market data feed.
 
