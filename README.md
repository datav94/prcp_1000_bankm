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