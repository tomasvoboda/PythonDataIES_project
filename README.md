# PythonDataIES_project
ML model predicting the probability of providing a loan

## Project Intro/Objective
The project aims to build a machine learning model that predicts the probability of a customer being approved for a loan based on their specific characteristics. This model is designed to be used directly by the customer to assess their eligibility for a loan before they apply. By inputting their relevant data into the model, the customer will receive a personalized probability score indicating their likelihood of a loan approval. Based on a Kaggle dataset.

### Methods Used
* Data Visualization
* etc.

### Technologies
* Python
* Pandas, jupyter
* etc. 

## Project description

The main python script is 'train.py'. The project environment is specified in 'MLproject' and 'conda.yaml'. A user can install the conda environment by running 
```bash
conda env create -f conda.yaml
```
and activate it with
```bash
conda activate Loan_prediction
```

The script 'train.py' can be run inside the terminal using command 
```bash
python train.py
```

Moreover, a user can select his or her own custom parameters for the models training. The parameters eligible for setting are 'max_iter', 'penalty', 'solver' and 'C' for the logistic regression, and 'n_estimators', 'max_leaf_nodes', 'criterion', and 'max_depth' for the random forest. Their enabled values, default values and definitions are identical with the sklearn package documentation
[Logistic_regression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html)
[Random forest](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html)

More information can be found inside the help using
```bash
python train.py -h
```

An exampel of a command generating logistic regression with maximum iterations set to 200 and random forest with criterion set to 'entropy', keeping other parameters in default, looks like
```bash
python train.py -logit--max_iter 200 -rf--criterion entropy
```

Model metrics for given parameters are displayed in the terminal after a command is completed. A user can find results of both models through the mlflow UI using the link generated by the following command 
```bash
mlflow ui 
```

After the logit and rf runs are completed, the best-performing model based on the rmse metric out of these two and all preceding ones inside the "Loan_prediction" experiment is selected. This model is then registered and set to production stage. Finally, the basic prediction is performed inside a terminal. 


## Needs to be done

Adding more comments and functions description + check the custom parameteres compatibility and ranges (some of them cannot be used with others, some are only positive,...) + add loggings to warn about wrong form of input parameters 

Hyperparameters tuning

Serve the best-performing model

The project ends with model deployment, the idea is a web form predicting the probability after filling the independent variables.
