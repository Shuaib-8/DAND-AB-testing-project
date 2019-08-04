### Date created for project and README Files
Created the project file on: ```13/07/19```
<br>
Created the README file on: ```19/07/19```

### Project Title
**Analyze A/B Test Results**

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
