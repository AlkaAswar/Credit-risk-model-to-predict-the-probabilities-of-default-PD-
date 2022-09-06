# Credit-risk-model-to-predict-the-probabilities-of-default-PD-
### Problem Statement
Assignment: Predict the probabilities of default
-------------------------

1)Develop a data-driven credit risk model to predict the probabilities of default (PD)

2)Can you assign credit scores to existing or potential borrowers

## Steps Performed 
### 1. Understand The Business Problem
##### What is Credit Risk?
In simple words, it is the risk of borrower not repaying loan, credit card or any other type of loan. Sometimes customers pay some installments of loan but don't repay the full amount which includes principal amount plus interest. For example, you took a personal loan of USD 100,000 for 10 years at 9% interest rate. You paid a few initial installments of loan to the bank but stopped paying afterwards. Remaining unpaid installments are worth USD 30,000. It's a loss to the bank.
so, we have to find out the probability of defaulter and which features are highly important for that.

### 2. Load The Data And Understand 
so we have total 74 columns and 466285 rows are present in our dataset
using data.dictonary file we understand the columns description

 0   id                            
 1   member_id                    
 2   loan_amnt                     
 3   funded_amnt                   
 4   funded_amnt_inv              
 5   term                          
 6   int_rate                     
 7   installment                  
 8   grade                       
 9   sub_grade                     
 10  emp_title                    
 11  emp_length                    
 12  home_ownership                
 13  annual_inc                   
 14  verification_status           
 15  issue_d                      
 16  loan_status                   
 17  pymnt_plan                    
 18  url                           
 19  desc                          
 20  purpose                      
 21  title                         
 22  zip_code                     
 23  addr_state                    
 24  dti                          
 25  delinq_2yrs                  
 26  earliest_cr_line             
 27  inq_last_6mths               
 28  mths_since_last_delinq       
 29  mths_since_last_record       
 30  open_acc                     
 31  pub_rec                      
 32  revol_bal                    
 33  revol_util                 
 34  total_acc                    
 35  initial_list_status          
 36  out_prncp                   
 37  out_prncp_inv               
 38  total_pymnt                  
 39  total_pymnt_inv              
 40  total_rec_prncp              
 41  total_rec_int                
 42  total_rec_late_fee           
 43  recoveries                   
 44  collection_recovery_fee     
 45  last_pymnt_d                 
 46  last_pymnt_amnt             
 47  next_pymnt_d                
 48  last_credit_pull_d           
 49  collections_12_mths_ex_med   
 50  mths_since_last_major_derog  
 51  policy_code                 
 52  application_type             
 53  annual_inc_joint             
 54  dti_joint                   
 55  verification_status_joint   
 56  acc_now_delinq             
 57  tot_coll_amt                 
 58  tot_cur_bal                  
 59  open_acc_6m                  
 60  open_il_6m                   
 61  open_il_12m                  
 62  open_il_24m                  
 63  mths_since_rcnt_il           
 64  total_bal_il                 
 65  il_util                     
 66  open_rv_12m                  
 67  open_rv_24m                  
 68  max_bal_bc                   
 69  all_util                     
 70  total_rev_hi_lim             
 71  inq_fi                       
 72  total_cu_tl                  
 73  inq_last_12m      
 
 ### 3. Perform EDA / Data Cleaning
 here we cleaned the data first like to 
 
 #### shape             - (rows-466285, columns-74)
 
 #### null values       - There are null values are present in some columns
 
emp_title                  27588

emp_length                 21008

annual_inc                     4

desc                      340302

title                         20

delinq_2yrs                   29

earliest_cr_line              29

inq_last_6mths                29

mths_since_last_delinq    250351

mths_since_last_record    403647

open_acc                      29

pub_rec                       29

revol_util                   340

total_acc                     29

#### We will Drop features missing more than 20% data.
 
#### will filled remaining columns with columns mean.

#### duplicated - No

### 4. Pre-processing and Exploratory Analysis

In this step we visualized the each column of data and to see the data in and out

loan_status - is our target variable so we take only default values as a 1 and remaining all set as a 0
and stored this values in a new column i.e "target" column

there are some columns are not important so we drop that


### Handling Categorical columns

There are some columns are categorical 

 'term',
 
 'sub_grade',
 
 'home_ownership',
 
 'verification_status',
 
 'pymnt_plan',
 
 'purpose',
 
 'addr_state',
 
 'initial_list_status'
 
 so using " One hot encoding technique " we handle this columns
 
 so now our data is clean there is no missing values are present  
 and shape of oure dataset is (466285, 126)
 
 ### 5. Train/Test Splitting Data
 
X_train = data.drop('target', axis=1)

X_test = data.drop('target', axis=1)

y_train = data['target']

y_test = data['target']

 ### 6. Model Building
 ####  Building our credit scoring model
 
 We performed 3 model here which gave us best accuracy
 
####  1. Random Forest Classifier
 Accuracy - 0.999944240110662
 
 Probability -
 
y_test	default_proba	ypred
  
0 	0	        1.0   	0

1	  0	        1.0	    0

2	  0	        1.0	    0

3	  0	        1.0	    0

4	  0	        1.0	    0

------------------precision--recall---f1-score---support----------------

           0       1.00      1.00      1.00    465453
           
           1       1.00      0.97      0.98       832
           
    accuracy                           1.00    466285
    
 

####  2. Logistic Regression
Accuracy - 0.9982156835411818

Probability - 
array([[9.99577023e-01, 4.22976889e-04],
       [9.97479926e-01, 2.52007362e-03],
       [9.99296158e-01, 7.03841732e-04],
       ...,
       [9.98556893e-01, 1.44310653e-03],
       [9.96231590e-01, 3.76841005e-03],
       [9.99159906e-01, 8.40093605e-04]])

####  3. XGBClassifier
Accuracy - 99.87%

So here we can see all the model are performed very well but we got highest accuracy from Random Forest Algorithm.
we can performed others algorithms also but we got the higest accuracy with this model so stopped here.
