# Neural_Network_Charity_Analysis

## Overview
The purpose of this analysis was to help develop a machine learning algorithm for a client to help predict in what organizations to invest as to minimize the risk of not having anything to show for it. So it will help analyze and conclude if it is worth investing in a proyect and expect good results from it.  

## Results
**This document will talk about the final version of the model, as it is the most optimized.**

### Data Preprocessing 
* For the model the variable considered as the target variable was the column named "IS_SUCCESFUL" which as described by the client answers the question: Was the money used effectively? So in other words the model will use the information provided to predict if the money that might be invested will be used effectively. 

* For the features of the model it was decided to use all but 4 columns, this was decided after deep consideration of what the variable describes and by trial and error through multiple optimizations options. The columns considered as features were: 
  * APPLICATION_TYPE—Alphabet Soup application type
  * LIATION—Affiliated sector of industry
  * CLASSIFICATION—Government organization classification
  * USE_CASE—Use case for funding
  * ORGANIZATION—Organization type
  * INCOME_AMT—Income classification
  * SPECIAL_CONSIDERATIONS—Special consideration for application
  * ASK_AMT—Funding amount requested
  
As for "EIN" and "NAME" the reason they were cut was because they hold no relevance information for the prediction as they were only tags and hold no actual value. "STATUS" has a different reason, the column hold two values that only said if the project was active or not but most values were 1 so they really showed no actual influence over the overall data and results, maybe this time measurment was not the ideal one, it could been "ACTIVE_TIME" in years or months. Finally "IS_SUCCESFUL" was also removed as it the target variable. 

* For the input data left a binnig and encoding was done to the variables that showed a large number of unique values throughout the data as long as the type of data it hold allowed it. Wth help of python it was found that APPLICATION_TYPE and CLASSIFICATION was in need of binning. 

![Count_application](https://user-images.githubusercontent.com/110573146/223318120-680909a3-1af4-432e-9e94-f7e32f750740.png)

For "APPLICATION_TYPE" all the values that had less than 100 counts were gathered into "others", at first the value was set in 1800 but it was later determined that it left out a lot of important information and it was better to have a little more info. Also the decision was backed up with the density plot. The resultant groups were 10 plus an "other" category.

![density_application](https://user-images.githubusercontent.com/110573146/223318469-f934c94c-3590-4e21-82ec-a33b710ad3ff.png)

Next "CLASSIFICATION" was also binned to values with less than 100 counts as to help spread more the information as the top category had a large count. The results were 11 groups plus an "other" category with overall good values spreading. 

![count_classification](https://user-images.githubusercontent.com/110573146/223319257-2815c120-ffb5-41a3-9f8e-c5b24cdc8721.png)

![density_classification](https://user-images.githubusercontent.com/110573146/223319290-7b760ca0-d304-4fd3-9f91-0b14a1a4fa28.png)

### Compiling, Training and Evaluating the model
* For the neural network model it was decided to use 3 layers as it is especulated that even the most complex datasets can be modeled with 3 layers and afeter several trials with 2 layers and having no big result adding a third layer seemed as a good optimization option. 100 neurons were decided for each layer as, having a larger number could overfit the data so 100 is a good number as to let the features interact with each other. The activation formula used was RelU as it is a good fit to nonlinear datasets with positive values and most importantly is its excelent performance with more complex data.

* Unfortunately it was not possible to achieve the desired performance of 75% or more of accuracy for the model. As it can be seen, 4 different attemps were made to try and achieve this, but to not avail. The overall performance of all the attemps averaged to 72% for the test data and 74% for the train. 

* To try to achieve a good optimization model several attempts were made, like for example: drop the STATUS column for the features, bin less values as to have more information for CLASSIFICATION and APPLICATION_TYPE or to help spread the data even more. Also more neurons were added to the model, a third layer was and more epochs also were additionated as to try give the model mpre time to train and adapt. These steps were made only to the final optimization model, but many others attemps were made like dropping more columns or adding more neurons to the two layers or even changing the activation to tanh but overall the final optimization attempt was a cluster of the previous attempts. **All the attempts can be found in this repository.**

## Summary
Finally it can be said that the model does not meet the necessary requirements to be used to predict the effectiveness of money invested in organizations as it only predicts between 72% and 74% of the ones that are succesful. Another model is reccomended to keep testing this dataset as to prove two things: 
1. The dataset is enough to convey a good predcition.
2. The deep learning model can still be modified as to get a better result without overfitting the data.

Random Forest Classifier is reccomended as it has as good of precision as deep learning and also it is faster to implement and it could be useful to better conclude about the datset, if maybe the data is not enough or maybe if neural network does not adjust itself to this case. Any case it is good to have comparissons for future reference.
