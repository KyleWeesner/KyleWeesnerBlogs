# Mood's Median Test

One way to test non-normally distributed data is by using the Mood's Median Test.  This non-parametric test compares the medians of two samples to determine if there is significant difference in the samples.  This test is generally not used for larger sample sizes.  Mood's Median Tes is t used when the data includes outliers (e.g., for salary information, most people earn between $20k and $130k but the data includes one or two that earn multi-millions per year causing a Mean value to be greatly affected by one or just a few data points).  This can be done by hand but is usually done by some type of statistical software.  

## Median Test Process with scipy

### State your Null and Alternative Hypothesis
- Ho: Null hypothesis no significant difference between variables
- Ha or H1: Alternative Hypothesis there is a significant difference between variables

### Collect Data



For explainitory process created a list that is non-normally disctributed with outliers.
```
np.random.seed(1)
TownA_no_outlier = np.random.randint(20000, 100000, 95).tolist()
np.random.seed(2)
TownA_outlier = np.random.randint(200000, 300000, 5).tolist()
TownA = TownA_no_outlier + TownA_outlier
```
```
np.random.shuffle(TownA) #shuffled after joining lists. Due to this method when repeated will get different results
south_city, north_city = train_test_split(TownA, test_size=.5) #created two samples to comapre 
```
Made up 100 annual salaries for citizens of TownA and created two sample sizes from the population list. 

```
fig, ax = plt.subplots(figsize =(10, 5))
ax.hist(TownA, bins=10)

ax.set_title("Annual Income of TownA Citizens")
ax.set_xlabel("Annual Income")
# Show plot
plt.show()
```
![Example_Histogram_blog](https://user-images.githubusercontent.com/100227270/163664858-fff7c944-5847-41aa-a26e-2651caa135e7.jpg)


### Perfrom Test 
#### [scipy.stats.median_test](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.median_test.html) Doctumentation

```
stat, p, med, tbl = median_test(south_city, north_city)
stat, p, med, tbl
```
![median_test output](https://user-images.githubusercontent.com/100227270/163665395-a5a7d3d0-0d34-4fdc-a56e-3f949cfed0f8.JPG)


### Reject or Fail to reject Null Hypothesis

## Outputs and Parameters from scipy.stats_median_test



