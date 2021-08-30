# Credit Line Increase Model Card
[comment]: <> (# is for the biggest capital)

### Basic Information
[comment]: <> (### is for the third biggest capital, the more #, the smaller the type)

* **Person or organization developing model**: Zijian `zjwang@gwu.edu`, Ming `mtang60@gwu.edu`, Yuqi `wyuqi30@gwu.edu`, Ziling `ziling@gwu.edu`
* **Model date**: August 29, 2021
* **Model version**: 0.22.2.post1
* **License**: Apache
* **Model implementation code**: [DNSC_6301_Group10.ipynb](https://github.com/cathy9/6301_group10/blob/dev/6301_group10.ipynb)

[comment]: <> ("``" is used to display a grey box)
[comment]: <> (the first * illustrate the unordered list and "** **" is used for emphasizing,"[]" mean adding a link)

### Intended Use
* **Primary intended uses**: This model is an *example* probability of default classifier, with an *example* use case for determining eligibility for a credit line increase.
* **Primary intended users**: Students in GWU DNSC 6301 bootcamp.
* **Out-of-scope use cases**: Any use beyond an educational example is out-of-scope.

[comment]: <> (the first * illustrate the unordered list and "** **" is used for emphasizing)

### Training Data

* Data dictionary: 

| Name | Modeling Role | Measurement Level| Description|
| ---- | ------------- | ---------------- | ---------- |
|**ID**| ID | int | unique row indentifier |
| **LIMIT_BAL** | input | float | amount of previously awarded credit |
| **SEX** | demographic information | int | 1 = male; 2 = female
| **RACE** | demographic information | int | 1 = hispanic; 2 = black; 3 = white; 4 = asian |
| **EDUCATION** | demographic information | int | 1 = graduate school; 2 = university; 3 = high school; 4 = others |
| **MARRIAGE** | demographic information | int | 1 = married; 2 = single; 3 = others |
| **AGE** | demographic information | int | age in years |
| **PAY_0, PAY_2 - PAY_6** | inputs | int | history of past payment; PAY_0 = the repayment status in September, 2005; PAY_2 = the repayment status in August, 2005; ...; PAY_6 = the repayment status in April, 2005. The measurement scale for the repayment status is: -1 = pay duly; 1 = payment delay for one month; 2 = payment delay for two months; ...; 8 = payment delay for eight months; 9 = payment delay for nine months and above |
| **BILL_AMT1 - BILL_AMT6** | inputs | float | amount of bill statement; BILL_AMNT1 = amount of bill statement in September, 2005; BILL_AMT2 = amount of bill statement in August, 2005; ...; BILL_AMT6 = amount of bill statement in April, 2005 |
| **PAY_AMT1 - PAY_AMT6** | inputs | float | amount of previous payment; PAY_AMT1 = amount paid in September, 2005; PAY_AMT2 = amount paid in August, 2005; ...; PAY_AMT6 = amount paid in April, 2005 |
| **DELINQ_NEXT**| target | int | whether a customer's next payment is delinquent (late), 1 = late; 0 = on-time |

[comment]: <> (When adding a table, hyphens could divide the words which for the first row, and pipe could seperate the column)

* **Source of training data**: GWU Blackboard, email `jphall@gwu.edu` for more information
* **How training data was divided into training and validation data**: 50% training, 25% validation, 25% test
* **Number of rows in training and validation data**:
  * Training rows: 15,000
  * Validation rows: 7,500

### Test Data
* **Source of test data**: GWU Blackboard, email `jphall@gwu.edu` for more information
* **Number of rows in test data**: 7,500
* **State any differences in columns between training and test data**: None

### Data Details
* **Columns used as inputs in the final model**: 'LIMIT_BAL', 'PAY_0', 'PAY_2', 'PAY_3', 'PAY_4', 'PAY_5', 'PAY_6', 'BILL_AMT1', 'BILL_AMT2', 'BILL_AMT3', 'BILL_AMT4', 'BILL_AMT5', 'BILL_AMT6', 'PAY_AMT1', 'PAY_AMT2', 'PAY_AMT3', 'PAY_AMT4', 'PAY_AMT5', 'PAY_AMT6'
* **Columns used as targets in the final model**: 'DELINQ_NEXT'
* **Type of model**: Decision Tree
* **Software used to implement the model**: Python 3 
* **Version of the modeling software**: 0.22.2.post1
* **Hyperparameters or other settings of model**: None

### Quantitative Analysis 
* **Metrics used to evaluate final model**: Training AUC, Validation AUC, AIR, 5-Fold SD,Tree depth...
* **Final values of the metrics for all data**: 
Confusion matrix by RACE=1
             actual: 1 actual: 0
predicted: 1       447       387
predicted: 0       139       501
(Hispanic)

Confusion matrix by RACE=2
             actual: 1 actual: 0
predicted: 1       449       348
predicted: 0       157       537
(Black)

Confusion matrix by RACE=3
             actual: 1 actual: 0
predicted: 1       176       813
predicted: 0        72      1228
(White)

Confusion matrix by RACE=4
             actual: 1 actual: 0
predicted: 1       186       784
predicted: 0        59      1217
(Asian)

White proportion accepted: 0.568
Hispanic proportion accepted: 0.434
hispanic-to-white AIR: 0.76

White proportion accepted: 0.568
Black proportion accepted: 0.465
black-to-white AIR: 0.82

White proportion accepted: 0.568
Asian proportion accepted: 0.568
asian-to-white AIR: 1.00

Confusion matrix by SEX=1
             actual: 1 actual: 0
predicted: 1       546       905
predicted: 0       179      1292
(Male)

Confusion matrix by SEX=2
             actual: 1 actual: 0
predicted: 1       712      1427
predicted: 0       248      2191
(Female)

Male proportion accepted: 0.503
Female proportion accepted: 0.533
female-to-male AIR: 1.06

* **Plots related to the data**:



![pic1](https://raw.githubusercontent.com/BA-WangZijian/MSBA-6301-group/main/11.png)
![pic2](https://raw.githubusercontent.com/BA-WangZijian/MSBA-6301-group/main/22.png)
![pic3](https://raw.githubusercontent.com/BA-WangZijian/MSBA-6301-group/main/33.png)
![pic4](https://raw.githubusercontent.com/BA-WangZijian/MSBA-6301-group/main/44.png)
![pic5](https://raw.githubusercontent.com/BA-WangZijian/MSBA-6301-group/main/55.png)
![pic5](https://raw.githubusercontent.com/BA-WangZijian/MSBA-6301-group/main/66.png)
![pic5](https://raw.githubusercontent.com/BA-WangZijian/MSBA-6301-group/main/77.png)

### Ethical considerations 
* **Describe potential negative impacts of using your model**: 

Using the ARIMA model to predict time series data must be stable, or it is stable after being differentiated. If the data is unstable, the law cannot be captured. For example, stable data has no trend or seasonality; that is, its mean value has a constant amplitude on the time axis, and its variance tends to the same stable value on the time axis.
However, it may be that the contact time is relatively short, the use of this model is less and the understanding is not deep enough, so we have not encountered such troubles at present.

* **Describe potential uncertainties relating to the impacts of using your model**: 

The uncertainty of this model exists in only capturing linear relationships, not nonlinear relationships.This is something we need to judge in advance.ARIMA model is used to predict time series data, which must be stable. If the data is unstable, the law cannot be captured. Stock data, for example, cannot be predicted by ARIMA because stock data are unstable and often subject to changes in policy and news.


* **Describe any unexpected or results**: 

As a beginner, this lesson brings us to the world of code. After experiencing it, I have a lot of insights. I think code is also a way to exchange ideas. The quality of the code is very important, but high-quality program code is not so easy to produce, it requires careful thinking and research. Second, many times I spend a lot of precious time trying to solve a problem, but in fact, I can get results by simply searching at the beginning. There are countless examples of this. When I encounter a problem, it is likely that someone else has encountered the same problem long ago and found a solution. Save yourself some time, Google first, Google will surprise you.

