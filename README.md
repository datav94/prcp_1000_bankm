# The Portugese Bank Marketing Dataset

| Project particulars |                                                                   |
|---------------------|-------------------------------------------------------------------|
| Team ID             | PTID-CDS-NOV21-1232                                               |
| Project ID          | PRCP-1000-ProtugeseBank                                           |
| Team Members        | Shazzadur Rehman, Harish Hari, Yashwanth Shankaran, Gorecha Viral |

"The data is related with direct marketing campaigns (phone calls) of a Portuguese banking institution. The classification goal is to predict if the client will subscribe to a term deposit (variable y). "

### __dataset definition__
    - age (numeric)
    - job : type of job (categorical: "admin.","unknown","unemployed","management","housemaid","entrepreneur","student","blue-collar","self-employed","retired","technician","services") 
    - marital : marital status (categorical: "married","divorced","single"; note: "divorced" means divorced or widowed)
    - education (categorical: "unknown","secondary","primary","tertiary")
    - default: has credit in default? (binary: "yes","no")
    - balance: average yearly balance, in euros (numeric) 
    - housing: has housing loan? (binary: "yes","no")
    - loan: has personal loan? (binary: "yes","no")

##### related with the last contact of the current campaign:
    - contact: contact communication type (categorical: "unknown","telephone","cellular") 
    - day: last contact day of the month (numeric)
    - month: last contact month of year (categorical: "jan", "feb", "mar", ..., "nov", "dec")
    - duration: last contact duration, in seconds (numeric) - remove this as it is not usefull before call and after call its not needed as after call y is already known. It may be relevant to data when analysing which employee performed better

##### other attributes:
    - campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
    - pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric, -means client was not previously contacted)
    - previous: number of contacts performed before this campaign and for this client (numeric)
    - poutcome: outcome of the previous marketing campaign (categorical: "unknown","other","failure","success")
    
##### additional attributes (only in bank-additional dataset)
    - emp.var.rate: employment variation rate - quarterly indicator (numeric)
    - cons.price.idx: consumer price index - monthly indicator (numeric)     
    - cons.conf.idx: consumer confidence index - monthly indicator (numeric)     
    - euribor3m: euribor 3 month rate - daily indicator (numeric)
    - nr.employed: number of employees - quarterly indicator (numeric)

## __Question__
    1. predict whether the person will apply for term deposit over the marketing phone call

## __STEPS:__

1. Import libraries
2. import dataset
3. EDA
4. data - preprocessing
5. splits
6. model train
7. model evaluation
7. model selection
8. hyperparameter tuning


## __Analysis__

### __Inferences from EDA:__

- Only 1.8% of the population are student with the highest contacts made towards admin job role at 26%
- 60% of the contacted population is married
- 30% of contacted population has university degree, 24.2% are high school graduates and a very minimal amount of population is illiterate
- 79.7% population does not have any credit default
- 53.8% population has housing loan
- 84.4% population does not have a personal loan 
- 63.9% contacts were made to cell phones 
- The month of may has the highest contact rate at 33.5% 
- Thursdays have seen the highest contact rate at 20.9% followed very closely by mon at 20.7%
- 86.5% of the population contact has poutcome non existant which implies they were not contacted during previous campaigns
- The response pie chart shows that the dataset is highly imbalanced
- Age, duration, campaign, previous and consumer confidence index has very high number of outliers that needs treatment using yeo-johnson power transform

### __Correlation / Heatmap plot inferences__
- The highest correlation is between euribor3m and emp_var_rate which is not relavent to the problem at hand
- Followed by emp_var_rate and nr_employed which is convenient because a higher number of employees in the bank would lead to a high number of employee variation rate
- duration has a good correlation with response which does mean there is a relation between duration of last call and the response received which can be further clarified during visualization
- pdays has correlation with response which suggests that someone contacted within less amount of days after being contacted once during the campaign has a higher probability towards a positive response
- nr_employed has an inverse correlation with response as well and due to its high correlation with emp_var_rate we can conclude that the lesser the emp_var_rate the higher the probability of getting a positive response

### __Inferences from Visualization:__

#### __Among the people who subscribed__
- Single ones subscibe more than married or divorced
- Students have the highest subscription rate
- people with one loan subscribe more than those with no loans or more than one loans
- Subscription rate is higher for those contacted on their cellphones
- Thursdays have seen higher subscription rate as it should be as thursdays have highest contact rates during the course of any week
- The month of march has seen the highest subscription rate
- Those who had subscribed to term deposit in earlier campaigns tend to subscribe during this campaigns
- As it is evident those with no credit default has a considerably high subscription rates 
- Those above the age of 60 i.e. elderly people has a high tendency to subscribe to term deposit

### __Inference from lmplot__
- those contacts which lasted less than 1200 seconds and had been contacted less than 6 times during this campaign has resulted into subscription to term deposit at a considerably high rate

### __Inferences form Kernal density estimate plots and scatter plots__
- Kernal density estimate plots draft the cumulative density of data points with respect to each of the two features provided and we can further infer the correlation of theirs as seen in the heatmaps


### __Conclusion and further research__

### __Conclusion__
1. As seen from inferences the best subscription rate can be achieved during the month of march especially on thursdays
2. Try calling more students and those who are retired that will give better subscription rates
3. Make sure the employees do not frequently vary while contacting a customer
4. Make sure the price and confidence index are in acceptable lower ranges during the contact periods
5. Make sure the contact duration does not exceed 1200 seconds and the number of contacts made should be less than 6
6. calling in more elderly people especially those above 60 will provide better subscription rate

### __Further work__
1. Usage of tensorflow or pytorch framework on model building to achieve better precision and recall on yes as the one achieved here is not acceptable
2. Usage of L1 Regularization will provide better results
3. Collect better more data for better models