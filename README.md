# Neural_Network_Charity_Analysis
Neural Network Binary Classifier

## Project Overview
 Alphabet Soup is a philanthropic organization that provides substantial funding to organizations that are dedicated to protecting the environment, improve individuals well being, and unify the world.  They have donated over $10B in the last 20 years.  The organization is looking for an approach to help predict which donations will used effectively thus maximizing the benefit of their donations. 
 
 The Data Science team will build a Neural Network Binary Classifier based on previous donations and results to forecast which new applicants are most likely to  succeed.


## Results
 Preprocessing: steps taken:
   * The 'IS_SUCCESSFUL' variable is the target for this analysis. Alphabet Soup has provided this boolean indicator to identify successful donations.
   * Upon examining the remaining features the following choices were made:
    
      - The 'EIN' and 'NAME' features were dropped.  Both features are unique to individual applicants and neither provides insight the model could use to improve the final accuracy.
    
      - The final list of features chosen are: 
          - 'APPLICATION_TYPE', 'AFFILIATION', 'CLASSIFICATION','USE_CASE', 'ORGANIZATION', 'STATUS', 'INCOME_AMT', 'SPECIAL_CONSIDERATIONS', 'ASK_AMT'
      
      - The non-numeric features were identified and a category analysis performed on all of them.  Both 'APPLICATION_TYPE' and 'CLASSIFICATION' had more than ten (10) categories so the less common categories were consolidated into an 'Other' group.
      
      - All the non-numeric categories were processed using the OneHotEncoder method creating new boolean columns for each category and the original features were dropped.
      - All features were scaled using the sklearn StandardScaler module
 
 Model creation: design, compilation, evaluation.  
   * The initial model had one(1) hidden layer and twenty-two(22) neurons, about have the number of the input features (see [ROT](https://towardsdatascience.com/17-rules-of-thumb-for-building-a-neural-network-93356f9930af)). The single hidden layer used the RELU activation function; RELU is one of the most frequently used functions and is a good starting point. The output function used for all iterations is a sigmoid function as the expected result is boolean, i.e., the applicant will be effective/approved or not.  50 epochs were chosen as a starting point.
      - Initial results were modest and did *not* achieve an accuracy of > 75%.  See full results below in [Table 1](#Table-1-Summary-of-Results-and-Optimizations)
   * Options changed to try and increase the accuracy of the model:
      - Add a second hidden layer with 11 neurons, using RELU, 50 epoch
      - Increase the number of neurons on each hidden layer from (22,11) to (32,16), 50 epoch
      - Using 2 hidden layers, (32,16) neurons, increase to 200 epoch
   * _None_ of the optimizations resulted in improved accuracy and should be dropped (they only added complexity and elongated run times).  

## Summary
The results of the original model and optimizations undertaken are in [Table 1](#Table-1-Summary-of-Results-and-Optimizations).  While some additional options (using different activation functions) ot further data analysis might yield some improvement, it is recommended that a RandomForest Classification model be tested as an alternative. RandomForest models provide many benefits. In this case the robust handling of outlier and nonlinear data (ASK_AMT) and the additional insight provided by feature importance ranking should provide better results.

 ## Resources
 Data: Applicant detail file provided by Alphabet Soup

 Software: Python 3.7.10, Jupyter Notebook 6.3, pandas 1.2.4, numpy 1.19.5, scikit-learn 0.24.1, tensorflow 2.5.0, Git Bash 4.4.23



## Table 1. Summary of Results and Optimizations
| Model Trial        | Loss   | Accuracy | Comments                                                             |
| :----------------- | :----- | :------- | :------------------------------------------------------------------- |
| Base Model (D1/D2) | 0.5540 | 0.7286   | Basic data cleanup / encoding, one hidden layer (RELU, 22), 50 epoch |
| Option 1           | 0.5537 | 0.7277   | Add a second hidden layer (RELU, 11), 50 epoch                       |
| Option 2           | 0.5559 | 0.7303   | Increase the neurons from (22, 11) to (32,16), 50 epoch              |
| Option 3           | 0.5644 | 0.7276   | Option 2 plus increase to 200 epoch                                  |

