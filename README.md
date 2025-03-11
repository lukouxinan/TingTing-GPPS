# GPPS (Genes to Predict Platinum response Signature)

## 1. Description

The GPPS (Genes to Predict Platinum response Signature) is a sophisticated random forest model that leverages a carefully selected panel of five genes—PAX2, TFPI2, APOA1, ADIRF, and CRISP3—to accurately predict the response to platinum-based chemotherapy in ovarian cancer patients.

## Requirements


+ python3
+ pickle 
+ pandas
+ numpy


## 2. Usage
```
import pickle

with open('GPPS_model.pkl', 'rb') as f:
    model = pickle.load(f)

data = {
    'ADIRF': [1.640876, 0.301936, 0.487909],
    'APOA1': [36.304516, 32.732344, 13.746991],
    'CRISP3': [9.434357, 9.562321, 9.191212],
    'PAX2': [0.311354, 0.495126, 0.078641],
    'TFPI2': [17.910101, 7.421908, 8.136076]
}
sample_input = pd.DataFrame(data)
sample_input.index = ['sample1', 'sample2', 'sample3']
sample_pred = pd.DataFrame(GPPS.predict_proba(sample_input), index=sample_input.index,columns=['Sensitive_probability','Resistant_probability'])
sample_pred 
```

## 3. Input 

The test data must be normalized by "Rank-in" method[1]. The input is a pandas dataframe with the following columns:
```
         ADIRF	      APOA1	     CRISP3	      PAX2	       TFPI2
sample1	1.640876	36.304516	9.434357	0.311354	17.910101
sample2	0.301936	32.732344	9.562321	0.495126	7.421908
sample3	0.487909	13.746991	9.191212	0.078641	8.136076
 
```

### 4. Output
```
        Sensitive_probability	Resistant_probability
sample1	    0.6	                        0.4
sample2	    0.7	                        0.3
sample3	    1.0	                        0.0
```
+ Sensitive_probability: the probability of the sample being responsive to platinum-based chemotherapy.
+ Resistant_probability: the probability of the sample being resistant to platinum-based chemotherapy.

**You can reference the code in the [test.ipynb](./test.ipynb) file.**



[1] [Tang K, Ji X, Zhou M, Deng Z, Huang Y, Zheng G, Cao ZJ. NAR: Rank-in: enabling integrative analysis across microarray and RNA-seq for cancer. 2021, 49(17):e99-e99.](https://academic.oup.com/nar/article/49/17/e99/6313237?login=false)