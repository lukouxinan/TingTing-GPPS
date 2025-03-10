# GPPS (Genes to Predict Platinum response Signature)

## 1. Description

The GPPS (Genes to Predict Platinum response Signature) is a sophisticated random forest model that leverages a carefully selected panel of five genes—PAX2, TFPI2, APOA1, ADIRF, and CRISP3—to accurately predict the response to platinum-based chemotherapy in ovarian cancer patients.

## Requirements

```
+ python3
+ pickle 
+ pandas
+ numpy
+ scikit-learn
```

## 2. Usage
```
import pickle

with open('GPPS_model.pkl', 'rb') as f:
    model = pickle.load(f)

test_pred = model.predict_proba(test_data)
```

## 3. Input 

The test must be normalized by "Rank-in" method[1]. The input is a pandas dataframe with the following columns:
```
            PAX2, TFPI2, APOA1, ADIRF, CRISP3
 sample1    1.3, 2.5, 6.1, 1.5, 4.6
 sample2    2.7, 4.5, 3.2, 2.4, 3.5
 ......
 sampleN    3.2, 5.9, 3.5, 4.6, 1.1
 
```

### 4. Output
```
           predict_proba
sample1    0.123
sample2    0.345
......
sampleN    0.678
```
+ predict_proba: the probability of the sample being responsive to platinum-based chemotherapy.


[1] [Tang K, Ji X, Zhou M, Deng Z, Huang Y, Zheng G, Cao ZJ. NAR: Rank-in: enabling integrative analysis across microarray and RNA-seq for cancer. 2021, 49(17):e99-e99.](https://academic.oup.com/nar/article/49/17/e99/6313237?login=false)