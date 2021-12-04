# The Portugese Bank Marketing Dataset

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

