# Regularized-Logistic-Regression-Model
This project builds a recommendation system for a labor and delivery medical unit. The data used for this project is caesarin.csv: https://www.dropbox.com/sh/ao0ppfu4ykg05bd/AADtKIrHpNky4-vzPvicJ7UXa?dl=0&amp;preview=caesarian.csv.  

The file contains historical data from a labor and delivery unit. Given the attributes of a newly arrived patient we built a classification system using a regularized logistic regression model that recommended the type of delivery, either caesarian or normal delivery.  

Attributes:  

Age  

delivery number: this is the 1st delivery for the expectant mother or the 2nd deliver etc.  

delivery time: 0 = timely, 1 = premature, 2 = latecomer  

blood pressure: 0 = low, 1 = normal, 2 = high  heart problem: 0 = no, 1 = yes   

Target: 

caesarian: 0 = no, 1 = yes  

The following data preprocessing operations were performed:   

Imputation of missing values:  

Replace the missing age values with the integer equal to the round down of the mean of age.  

Replace the missing delivery number values with the most frequent delivery number.  

Encode the categorical variables using the one-hot encoding.  

Standardize the new features by removing the mean and scaling to unit variance.  

The goal of this project is to think about the use of predictive models in business  decisions.   

Considering the following hypothetical financial situation at the medical unit, which is given in relative terms.    

The profit/value of a caesarian delivery is $200 above the average value of a medical procedure per hour at the unit (this is considered a reference value). 

On the other hand, the profit/value of a normal delivery is -$400 compared with the reference profit due to the long timespan that normal deliveries require.   

Furthermore, if the medical unit performs caesarian on a patient who does not require one, then the insurance company refuses to pay on average $200 for the procedure/hour, loss which is directly absorbed by the unit. 

If the unit performs normal delivery for a patient who requires a caesarian, then due to complications the unit loses on average $50.  

The project is comparing logistic regression models where the evaluation is performed using accuracy scoring and expected value scoring.

It trains L2-regularized logistic regression models using LogisticRegressionCV with 100 regularization coefficients and 3-fold cross-validation. 

Setting the following parameters: multi_class='multinomial', solver='lbfgs', max_iter=1000. 

The maximum iteration has been increased to ensure convergence of the optimization problem.   

Trained a model where the regularization coefficient is determined using the accuracy as the scoring function.   

Trained another model where the regularization coefficient is determined using the expected value as the scoring function.   

Writes a function EV_score(estimator, X, y) that takes an estimator, an input X and an output y and calculates the expected value based on the profit/value matrix and the confusion matrix calculated using the predictions estimator(X) and the given output y.
