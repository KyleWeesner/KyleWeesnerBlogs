# Overview of Hypothesis Testing

<p align="center">
  <img src="https://images.fatherly.com/wp-content/uploads/2021/01/indiana-jones-streaming-raiders-first-scene.jpg?q=65&enable=upscale&w=600" width="250"/> 

Exploring   unknowns can be exciting!  Sometimes!  In everyday life, we unconsciously perform hypothesis testing on some level with decision making. For example, most peoples morning routine consists of brushing teeth.  This can be broken down into many outcomes such as if I don't there will be no difference in smell or my breath will be minty fresh.  By knowing past experiences, data, one can expect that your breath will smell better after brushing than if you had skipped.  This is a general assumption of outcome.  It is likely that sometimes teeth were not brushed, the breath wasn't bad.  Other factors could be involved such as what was eaten or drank the night before.  So to conclude that breath will stink if teeth are not brushed is at best a best guess.  For other more important decisions, statistical data analysis is often used to make these decisions.  Hypothesis testing is crutial in data science for investigating ideas and being able to conclude with a defendable answer.  There are five main steps when hypothesis testing.

## 1. State the Null and Alternative Hypothesis and how confident you want to be in your decision

  When first wanting to test an experimental hypothesis it is crutial to devolop a null and alternative hypothesis.  The null hypothesis is that there is no difference between what you are comparing.  The null hypothesis is considered true until rejected.  The alternative hypothesis is for testing your variable in which you want to test.  The confidence level you use to make a decision, the alpha value, is essentially the amount of risk of being wrong you are willing to accept if you say there is a difference.  In the US, innocent until proven guilty means that the Null hypothesis is innocent.  Depending on the severity of the crime, the criminal justice system sets a certain confidence level, or burden of proof, in order to convict.  Right or wrong, the criminal justtice system has decided that they would rather let a guilty person go free than convict an innocent.  As we know, legal proceedings don't always follow facts and data and are affected by process and rules, but that aside, the general concept is the same, or at least it was intended to be the same.  
  

<img src="http://utee63lakop1ozmny1lmo13a-wpengine.netdna-ssl.com/files/newsletter/I-am-the-null-hypothesis.jpg" width="250"/>

### Generally seen as
- Ho: Null hypothesis no significant difference between variables
- Ha or H1: Alternative Hypothesis there is a significant difference between variables
  
## 2. Collect Data to Test Hypothesis
  
  To be able to test or make inferences about your hypothesis there must be sufficient and valid data.  Software will run a test for you and give you an output for what it is programmed to do.  The difficult part is deciding if you have asked it to do the right thing.  Statisticians always prefer more data.  Why?  More data allows better modeling of the process.  The process is whatever is going on that produces results.  Hypothesis testing is simply a means to determine if there is a difference between 2 or more things.  The difference can be a difference in average values or a difference in distribution or variation.  It can be a difference between sets of data, between a set of data and a defined value, or between a set of data and a subset of that same data.   
  
## 3. Perform the Proper Statistical Test
  
 <img src=https://compote.slate.com/images/4bb1d42b-e0d3-4bfa-9b85-103b63977542.jpg width="200"> Generally, all of these statistical tests measures the varience between groups and returns a p-value.  

    The type of test we choose depends on several factors.  The normality of the data we have, the quantity of data we have, and the number of things we are comparing determines what is the appropriate hypothesis test to use.
- Testing difference in variation:  Levene's Test (non-normal data), F-Test (normal data, 2 data sets), Bartlett's Test (normal data, more than 2 data sets)
- Testing difference in Averages of normally distributed data: for normally distributed data, the average value used is the Mean
  - Z Test, used when comparing a sample mean to a population mean when n>50 
  - 1 Sample T Test, used when comparing a set of data to a defined value (e.g., is the average of this data different than 1.5 statistically)
  - 2 Sample T Test, used when comparing two sets of data (e.g., comparing the average income of people in Tennessee and Texas) or a subset of the data and the entire population (e.g., comparing the average income of people in Texas with the entire US population including Texas)
  - Paired T Test, used when there is a direct relation between the 2 sets (i.e., when there is some factor that links the data sets such as comparing 10 specific people that worked in both Tennessee and Texas and how much they earned in each)
  - ANOVA, used when comparing three or more goups (the result will tell you if one group is different, not which one)
  - Chi Square, used when comparing smaller data sets (unreliable standard deviation calculation).  The expected value is calculated from the data in the total data set and compared to the observed data in a subsets.  Essentially, this method can compare data sets within a population and determine if each data set is conforming to the entire data population.
- Testing difference in Averages of non-normally distributed data:  for non-normally distributed data, the averabe value used is the Median.
  - Kruskal-Wallis Test used when the data does not have outliers (data that is significantly different than the rest of the data)
  - Mood's Median Test used when the data includes outliers (e.g., for salary information, most people earn between $20k and $130k but the data includes one or two that earn multi-millions per year causing a Mean value to be greatly affected by one or just a few data points)

## 4. Reject or Failed to Reject Null Hypothesis
<img src="https://user-images.githubusercontent.com/100227270/159238521-26e0bf91-a6b1-4ffa-9561-477164162b23.png" width="500" height="300" />
  
## 5. Discuss Results
Presenting a summary of your data and the p-value.  Go back to the initial question and state the findings either failing to reject the null or rejecting the null.  By rejecting the null it is equavalent to accepting the alternative hypothesis.
  
  Restating the above, a 'p' value is the calculated probability (in decimal form) of being wrong if it is said there is a difference.  The alpha value is the defined acceptable 'p' value.  The Null hypothesis is that there is no difference and the Alternative hypothesis is that there is a difference.  So if p < alpha, then we reject the Null hypothesis and accept the Alternative hypothese (i.e., this data is guilty of being different).
