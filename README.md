# Neural_Network_Charity_Analysis
Neural Network Binary Classifier

## Project Overview
 Alphabet Soup is a philanthropic organization that provides substantial funding to organizations that are dedicated to protecting the environment, improve individuals well being, and unify the world.  They have donated over $10B in the last 20 years.  The organization is looking for an approach to help predict which donations will used effectively thus maximizing the benefit of their donations. 
 
 The Data Science team will build a Neural Network Binary Classifier based on previous donations and results to forecast which new applicants are most likely to  succeed.


## Results
 Neural Network models require data preprocessing.  Below is a summary of the approaches / steps taken:
   * The 'IS_SUCCESSFUL' variable is the target for this analysis. Alphabet Soup has provided this boolean indicator to identify successful donations.
   * Upon examining the remaining features the following choices were made:
    
      - The 'EIN' and 'NAME' features were dropped.  Both features are unique to individual applicants and neither provides insight the model could use to improve the final accuracy.
    
      - The final list of features chosen are: 
          - 'APPLICATION_TYPE', 'AFFILIATION', 'CLASSIFICATION','USE_CASE', 'ORGANIZATION', 'STATUS', 'INCOME_AMT', 'SPECIAL_CONSIDERATIONS', 'ASK_AMT'
      
      - The non-numeric features were identified and a category analysis performed on all of them.  Both 'APPLICATION_TYPE' and 'CLASSIFICATION' had more than ten (10) categories so the less common categories were consolidated into an 'Other' group.
      
      - Finally, all the non-numeric categories were processed using the OneHotEncoder method creating new boolean columns for each category and the original features were dropped.
 
 After the preprocessing is completed the model is built, compiled, trained, and evaluated.  
   * The initial model had one(1) hidden layer and twenty-two(22) neurons, about have the number of the input features. (For model ROT, see : [RulesofThumb](https://towardsdatascience.com/17-rules-of-thumb-for-building-a-neural-network-93356f9930af)


## Summary
Only the EasyEnsemble presents as a reasonable model and could be used to flag early potential issues but further analysis and improvements (or alternatives) before using in a production setting.  All the other models are inadequate to use.  They will poorly identify actual loss scenarios while identifying too many false positives - certainly a negative for customer satisfaction.

 ## Resources
 Data: Lending Club provided credit history

 Software: Python 3.7.10, Jupyter Notebook 6.3, pandas 1.2.4, numpy 1.19.5, scikit-learn 0.24.1, imbalanced-learn 0.8.0, Git Bash 4.4.23
