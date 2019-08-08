### Date created for project and README Files
Created the project file on: ```13/07/19```
<br>
Created the README file on: ```19/07/19```
***
### Project Title
**Analyze A/B Test Results**
***
### Description

A/B tests are very commonly performed by data analysts and data scientists.
For this project, the objective is to understand the results of an A/B test run by a an e-commerce (fictional) website.
<br>
Under such context, the company has developed a new web page to try and increase the number of users who **'convert'** i.e. the number of users who decide to pay for the company's product.
<br>
Using various statistical tests and applied modelling (logistical regression), I will look to conclude whether or not the e-commerce website should implement this new page (Alternative), keep the old page (Null), or perhaps run the experiment longer to make their decision.

**Null hypothesis:** there is *no difference* between the new and old page in terms of the proportion of click through rates
<br>
**Alternative hypothesis:** there is a *difference* between the new and old page in terms of the proportion of click through rates

#### Datasets

The dataset I used to compose an A/B test came in this form containing five columns:

|user_id   |timestamp   |group   |landing_page   |converted   |
|--:|--:|--:|---|---|
851104 | 2017-01-21 ```(YYYY-MM-DD)``` 22:11:48.556739 ```(HH:MM:SS)```| ```Control``` or ```treatment```| ```old_page``` or ```new_page```| 1 - ```TRUE``` 0 - ```FALSE```|

Additionally, I also utilised a dataset containing the country the corresponding users originated from, measuring any interaction/effect during testing:

|user_id   |country  |
|--:|--:|
834778| ```UK```, ```US``` or ```Canada (CA)```

#### Probability/statistical computations

##### Part 1 - Probability
* The proportion of users converted
* The number of times the new_page and treatment don't match
* The probability of an individual converting regardless of the page they receive
* Given that an individual was in the `control group`, what is the probability they converted
* Given that an individual was in the `treatment group`, what is the probability they converted
* What is the probability that an individual received the new page

##### Part 2 - hypothesis (A/B) testing
* Perform the sampling distribution for the difference in converted between the two pages over 10,000 iterations of calculating an estimate from the null.
* The **conversion rate** for *new page* displayed under the null
* The **conversion rate** for *old page* displayed under the null
* Number of individuals in the treatment *(new page)* group
* Number of individuals in the control *(old page)* group
* Find the mean/expected difference (test statistic) between the new and old page - via bootstrap simulation of 10,000 samples
* Illustrating the simulated difference of the mean between the page groups using a histogram (sample distribution)
* Observing the proportion of simulated mean differences of page groups being greater than the actual difference seen in the dataset
* Using built-in SciPy statistic module to perform a z-test, with a `5% error rate (alpha)` for a 95% confidence interval used to find the **z statistic** and **p-value**

##### Part 3 - Regression approach
* **Logistical regression** - the dataset contains categorical (binary) variables we want to observe based on page landings and conversions
* ```statsmodels``` - used to fit the regression model to see if there is a significant difference in conversion based on which page a customer receives.
* Process - create and add an **intercept** column filled with the value 1
    * Create a dummy variable using ```pd.get_dummies``` -  based on which page each user received
    * `1` - when the user receives the treatment
    * `0` - when the user receives the control
    Outcome - fit the model to predict whether or not an individual converts
* Afterwards, interpret the p-value based on the null hypothesis (no difference) and alternative hypothesis (significant difference).
* Model fit/specification - factors to consider:
    * Adding explanatory variables can help explain the relationship about whether an individual converts or not.
        *   Reduce omitted variable bias - another factor not previously included such as the time, given the year, month or season can affect the association (seasonality) between conversions after new page features are implemented.
        > This can better explain the predicted relationship, possibly increasing the correlation coefficient and increasing predictive justifications when added factors support goodness of fit criteria.
    * However, when implementing a model, one must be wary of overfitting data, as adding closely related variables could cause overestimation within the predicted values being observed.
        * Moreover, adding factors can needlessly complexify the model, while possibly misunderstanding causality (little evidence to suggest that changes in one such quantities causes changes in the other) with correlation, which increases the likelihood of making unsound statistical conclusions including false positives.
***
* Country interaction - fit a model to see if an individuals converts, based on individual factors belonging to a control and treatment group of page landing/conversions and the country they originate from.
    * Baseline - Canada
    * Comparison countries - UK AND US
* Multiplicative interaction - country * ab page (interaction between page and country to see if there are significant effects on conversion).

### Files used

The data I used is provided by Udacity.
The files can be accessed here under a ```.csv``` format:
[ab_data](https://drive.google.com/open?id=1_EnnOjfAOcFbqXCpX9RcqHzFBsd8NbQwpSv4m42iVCc)
[countries](https://drive.google.com/open?id=1_EnnOjfAOcFbqXCpX9RcqHzFBsd8NbQwpSv4m42iVCc)

### References

Beyond my Udacity mentor, peers and lectures, I consulted a number of resources including:
* [DataCamp - Statistical thinking I](https://www.datacamp.com/courses/statistical-thinking-in-python-part-1)
Taught by Justin Bois
[DataCamp - Statistical thinking II](https://www.datacamp.com/courses/statistical-thinking-in-python-part-2)
* [Brilliant Statistics](https://brilliant.org/courses/statistics/)
* [Beginner’s Guide to A/B Testing Facebook Ads](https://adespresso.com/guides/facebook-ads-optimization/ab-testing/)
* [Optimization guide - A/B Testing](https://www.optimizely.com/optimization-glossary/ab-testing/)
* [Critical values and p values](https://www.itl.nist.gov/div898/handbook/prc/section1/prc131.htm)
* [UCLA - interpreting a p-value](https://stats.idre.ucla.edu/other/mult-pkg/faq/pvalue-htm/)
