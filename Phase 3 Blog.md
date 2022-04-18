# Mood's Median Test

One way to test non-normally distributed data is by using the Mood's Median Test.  This non-parametric test that compares the medians of two or more samples to determine if there is significant difference in the samples.  This test is generally not used for larger sample sizes.  Mood's Median Test is used when the data includes outliers (e.g., for salary information, most people earn between $25k and $90k but the data includes one or two that earn multi-millions per year causing a Mean value to be greatly affected by one or just a few data points).  This can be done by hand but is usually done by some type of statistical software.  

<p align="center">
  <img src="https://user-images.githubusercontent.com/100227270/163767211-95066347-fb4f-44d2-9d2f-63b76afa6a43.png"/> 


## Mood's Median Test Process with scipy

For a better overview of the Statistical Analysis process refer to [Overview of Hypothesis Testing](https://github.com/KyleWeesner/KyleWeesnerBlogs/blob/gh-pages/Phase%202%20Blog.md).

### State your Null and Alternative Hypothesis and how confident you want to be in your decision (alpha) 
- Ho: Null hypothesis no significant difference between variables
- Ha or H1: Alternative Hypothesis there is a significant difference between variables

### Data
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/100227270/163767754-b7931178-4fb1-4a82-8d2b-881a07668625.png"/ width=400> 

In most cases data will be found or provided to you but for the explainitory purpose of using and interpreting the median test, I created a list that is non-normally disctributed with outliers to test if there is a difference between the samples.
```
np.random.seed(1) #creating a seed for np.random
TownA_no_outlier = np.random.randint(20000, 100000, 95).tolist() #randomly generating a list
np.random.seed(2) #creating a seed for np.random
TownA_outlier = np.random.randint(200000, 300000, 5).tolist() #randomly generating a list of outliers 
TownA = TownA_no_outlier + TownA_outlier #combining two lists
south_city, north_city = train_test_split(TownA, test_size=.5, random_state=42) #created two evenly split samples to comapre 
```
Made up 100 annual salaries for citizens of TownA and created two sample sizes from the grand sample.   

```
fig, ax = plt.subplots(figsize =(10, 5))
ax.hist(TownA, bins=10)

ax.set_title("Annual Income of TownA Citizens")
ax.set_xlabel("Annual Income")
# Show plot
plt.show()
```
![Example_Histogram_blog](https://user-images.githubusercontent.com/100227270/163664858-fff7c944-5847-41aa-a26e-2651caa135e7.jpg)

Image of the data in a histogram to show the non-normal distribution and outliers. 

### Perfrom Test 
#### [scipy.stats.median_test](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.median_test.html) Doctumentation

Continueing to test if there is a difference of annual income between south and north TownA 
```
stat, p, m, table = median_test(south_city, north_city)
stat, p, m, table
```

![median_test output](https://user-images.githubusercontent.com/100227270/163666799-7caa997f-47e1-4680-afcc-04024d1d9414.JPG)


The test returns 4 values in order stat, p, m, table.  Refer to scipy documentation for further explaination into each value.  The value returned that we are interested in is p which is the p-value.

### Reject or Fail to reject Null Hypothesis

We will compare our originally stated alpha value against our p-value.  Let assume our alpha is 0.05.  Because our p-value > alpha we would accept the Null Hypothesis and reject the Alternate Hypothesis (aka, there is no statistical difference between the annual income between the north and south of TownA).  Note: this test can compare two or more data sets.  When comparing more than two data sets, if p is less than alpha, this is telling you that at least one set is statistically different but does not identify which one.  
