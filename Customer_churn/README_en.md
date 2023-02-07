Conducted a study of clients leaving Beta-Bank. We have selected a model and parameters that can show whether the client will leave the bank in the near future or not. A model with an extremely large value of the F1-measure. Additionally, the model was evaluated by the AUC-ROC parameters, comparing its value with the F1-measure. Various methods of dealing with imbalance.

We have determined the two most successful models - CatBoostClassifier with the best F1-measure and ROC-AUC measure obtained with threshold=0.25 and RandomForestClassifier with threshold 0.3. The optimal hyperparameters were selected for them.

In addition, we found that in the presence of an imbalance for our task, the best option is to change the threshold for the RandomForestClassifier and a little for the CatBoostClassifier.
Increasing the sample proved to be better than decreasing it. But not suitable for CatBoostClassifier and RandomForestClassifier
The most important signs that bank marketers should pay attention to:

client age
number of bank products used by the client
account balance
estimated salary
credit rating
To predict churn, you can use a model based on the Random Forest algorithm with the parameters RandomForestClassifier(class_weight={1: 3.4}, max_depth=18, min_samples_leaf=4,min_samples_split=12, n_estimators=83) and the CatBoostClassifier model(random_seed=42,logging_level= 'Silent',custom_loss= ['F1'], loss_function= 'Logloss')