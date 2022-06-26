# Machine_Learning_Trading_Bot

I'm a financial advisor at one of the top five financial advisory firms in the world. My firm constantly competes with the other major firms to manage and automatically trade assets in a highly dynamic environment. In recent years, my firm has heavily profited by using computer algorithms that can buy and sell faster than human traders.

The speed of these transactions gave my firm a competitive advantage early on. But, people still need to specifically program these systems, which limits their ability to adapt to new data. I'm thus planning to improve the existing algorithmic trading systems and maintain the firm’s competitive advantage in the market. To do so, I'll enhance the existing trading signals with machine learning algorithms that can adapt to new data. 

I will complete this module in four sections including: Establish a Baseline Performance, Tune the Baseline Trading Algorithm, Evaluate a New Machine Learning Classifier, and Create an Evaluation Report.

---

## Establish a Baseline Performance

1. Import the OHLCV dataset into a Pandas DataFrame.

2. Generate trading signals using short(4)- and long(100)-window SMA values. 

3. Split the data into training and testing datasets.

4. Use the `SVC` classifier model from SKLearn's support vector machine (SVM) learning method to fit the training data and make predictions based on the testing data. Review the predictions.

5. Review the classification report associated with the `SVC` model predictions. 

              precision    recall  f1-score   support

        -1.0       0.43      0.04      0.07      1804
         1.0       0.56      0.96      0.71      2288

    accuracy                           0.55      4092
   macro avg       0.49      0.50      0.39      4092
weighted avg       0.50      0.55      0.43      4092

6. Create a predictions DataFrame that contains columns for “Predicted” values, “Actual Returns”, and “Strategy Returns”.

7. Create a cumulative return plot that shows the actual returns vs. the strategy returns. 

![<A vs S>](<Image/A vs S.png>)

*The precision is 0.43 for the −1 class and 0.56 for the 1 class. The recall is 0.04 for the −1 class and 0.96 for the 1 class. Based on the higher recall, it seems that the model is better at predicting the 1 class than the −1 class. Also, by looking at the plot, we can conclude that the Actual Return and Strategy Return is on the same direction from 2015 - 2016. However, after 2016, the Strategy Return does not appears to have as much as Actual Returns.*


## Tune the Baseline Trading Algorithm

In this section, I’ll tune, or adjust, the model’s input features to find the parameters that result in the best trading outcomes. 

1. Tune the training algorithm by changing the size of the training dataset to 6 month. 

              precision    recall  f1-score   support

        -1.0       0.44      0.02      0.04      1732
         1.0       0.56      0.98      0.71      2211

    accuracy                           0.56      3943
   macro avg       0.50      0.50      0.38      3943
weighted avg       0.51      0.56      0.42      3943

![<6 month>](<Image/6month.png>)

*By changing the training dataset to 6 months makes -1.0 precision a little better, but worse in recall. It does not appears to have a big different in 3 month or 6 month training size by looking at the plot.*

2. Tune the trading algorithm by adjusting the SMA-S to 50 and SMA-L to 150 window. 

             precision    recall  f1-score   support

        -1.0       0.52      0.03      0.05      1791
         1.0       0.56      0.98      0.71      2278

    accuracy                           0.56      4069
   macro avg       0.54      0.50      0.38      4069
weighted avg       0.54      0.56      0.42      4069

![<SMA>](<Image/SMA.png>)

*By changing the SMA Short to 50, Long to 150 window increases -1.0 precision, others remain no or slightly change. However, the plot still looks similar to the original plot.*

3. I changed SMA Short to 5 and Long to 50 as well as 6 month training dataset to evaluate the best return. 

              precision    recall  f1-score   support

        -1.0       1.00      0.00      0.00      1757
         1.0       0.56      1.00      0.72      2244

    accuracy                           0.56      4001
   macro avg       0.78      0.50      0.36      4001
weighted avg       0.75      0.56      0.40      4001

![<best>](<Image/best.png>)

*The precision is 1.0 for -1.0 class but recall is 1.0 for 1.0 class. Based on the higher recall, it seems that the model is performing at best on predicting 1.0 class.* 

## Evaluate a New Machine Learning Classifier

In this section, I’ll use the original parameters that the starter code provided. But, I’ll apply them to the performance of a second machine learning model. To do so, complete the following steps:

1. Import a new classifier, `LogisticRegression`.

2. Using the original training data as the baseline model, fit another model with the new classifier.

3. Classification Report:

              precision    recall  f1-score   support

        -1.0       0.44      0.33      0.38      1804
         1.0       0.56      0.66      0.61      2288

    accuracy                           0.52      4092
   macro avg       0.50      0.50      0.49      4092
weighted avg       0.51      0.52      0.51      4092


![<LMR>](<Image/LMR.png>)

*The precision is better off by 0.01 for -1.0 class, and stays the same for 1.0 class. However, the recall for -1.0 class went up to 0.38 for -1.0 class (compare to 0.04 for original testingg), and went to to 0.66 for 1.0 class (original 0.96). This LMR model helps in improving the -1.0 class prediction but not for 1.0 class.* 

## Create an Evaluation Report

*By changing the training dataset to 6 months, and SMA makes -1.0 precision a little better in classification report. When I changed SMA Short to 5 and Long to 50 as well as 6 month training dataset, the precision is 1.0 for -1.0 class but recall is 1.0 for 1.0 class. Based on the higher recall, it seems that the model is performing at best on predicting 1.0 class.* 

*When I adapted Logistic Regression Model, the precision is better off by 0.01 for -1.0 class, and stays the same for 1.0 class. However, the recall for -1.0 class went up to 0.38 for -1.0 class (compare to 0.04 for original testingg), and went to to 0.66 for 1.0 class (original 0.96). I can conclude that this model helps in improving the -1.0 class prediction but not for 1.0 class.* 

*Overall, it tells that with different methods of testing, the results are all benefit to the -1.0 class.* 

## Contributor

Feier Ou
ffeierou1003@gmail.com