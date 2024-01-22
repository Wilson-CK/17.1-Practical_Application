## <span style="font-size:larger;">**Practical Application Assignment: Comparing Classifiers**</span>

**Goals:**
- Compare the performance of the classifiers (k-nearest neighbors, logistic regression, decision trees, and support vector machines)
- Use a dataset related to the marketing of bank products over the telephone

**Github repository:** https://github.com/Wilson-CK/17.1-Practical_Application

**Link to Jupyter Notebook:** [https://github.com/Wilson-CK/Car_Prices_Analysis/blob/main/11.1-Wilson-Try_It.ipynb](https://github.com/Wilson-CK/17.1-Practical_Application/blob/main/17.1-Practical_Assignment.ipynb)

What's included:  This README, Jupyter notebook, and original data files. 

## <span style="font-size:larger;">Understanding the Data</span>

- Dataset references the UCI Machine Learning repository:  https://archive.ics.uci.edu/ml/datasets/bank+marketing

- The data is from a Portuguese banking institution and is a collection of the results of multiple marketing campaigns. The dataset collected is related to 17 campaigns that occurred between May 2008 and November 2010. Each campaign involved phone marketing with a human agent as the interlocutor, and sometimes an auxiliary use of the Internet online banking channel. The results for all channels were managed in an integrated fashion and outputted together.

## <span style="font-size:larger;">Read in the Data</span>

In the dataset, we observe a total of 21 columns. These columns are categorized into two types:

1) Numerical/Quantitative DataTypes:
Numerical data represents information in numerical form rather than in language or descriptive form. Examples include age, duration, campaign, pdays, previous, emp.var.rate, cons.price.idx, cons.conf.idx, euribor3m, and nr.employed.

2) Categorical/Qualitative DataTypes:
Categorical data is characterized by names or labels. Examples of categorical columns in our dataset are job, marital, education, default, housing, loan, poutcome, contact, month, day_of_week, and y.

## <span style="font-size:larger;">Understanding the Features</span>

- Utilizing the describe function provides a comprehensive understanding of the dataset. It allows us to grasp the range, means, standard deviations, maximum and minimum values, as well as percentiles of the data. This comprehensive overview enhances our ability to interpret and analyze the dataset effectively.

- Upon closer inspection, it becomes evident that the data ranges across columns exhibit significant variations. For instance, the mean of nr.employed is 5167.035911, while the mean of emp.var.rate is 0.081886. Such disparities in scales highlight the need for normalization to improve the overall quality of our data.

## <span style="font-size:larger;">Understanding the Task</span>

The business objective of the task is to develop a model that effectively explains the success of a contact, specifically whether the client subscribes to the deposit. The primary goals of this model are to enhance campaign efficiency by:

1. Identifying key characteristics that significantly impact success in subscribing to the deposit.
2. Facilitating better resource management, including human effort, phone calls, and time, through informed decision-making.
3. Enabling the selection of a high-quality and cost-effective set of potential customers who are likely to make a purchase.
   
Achieving these objectives will contribute to a more targeted and efficient marketing strategy, optimizing the allocation of resources and improving the overall success rate of deposit subscriptions.

## <span style="font-size:larger;">Engineering Features</span>

- Age, with its moderate dispersion, does not yield significant insights when related to other variables.

- For Jobs, Marital, and Education, a straightforward analysis based on the count of each variable might be the most informative. However, when related to other variables, the results are inconclusive. It's worth noting that these variables exhibit 'yes,' 'unknown,' and 'no' values for loan, default, and housing.

- To construct a socio-economic group of variables, we can create a composite variable termed 'bank_se.'

## <span style="font-size:larger;">A Baseline Model</span>

To outperform the baseline, our classifier should exhibit the following qualities:
- High training accuracy to effectively learn from the training data.
- Low false positive value, indicating a minimized rate of incorrectly predicted positive instances.
- High test accuracy, demonstrating robust performance on unseen data.

Additionally, we will evaluate the classifier using the area under the Receiver Operating Characteristic (ROC) Area Under the Curve (AUC), a metric that assesses the trade-off between true positive rate and false positive rate. AUC results will be categorized as follows:

- Excellent for AUC values between 0.9-1
- Good for AUC values between 0.8-0.9
- Fair for AUC values between 0.7-0.8
- Poor for AUC values between 0.6-0.7
- Failed for AUC values between 0.5-0.6

The classifier of choice for this task is K-Nearest Neighbors (KNN).

## <span style="font-size:larger;">Additional Models</span>

In addition to the KNN baseline model, I also deployed the following models for comparison:
- Support Vector Model
- Decision Tree Model
- Logistc Regression Model

## <span style="font-size:larger;">Score the Model</span> 

The accuracy of a diagnostic test is quantified by the area under the ROC curve (AUC). A perfect test has an AUC of 1, while a test with an AUC of 0.5 is considered ineffective.

The traditional academic point system for classifying accuracy is as follows:
- AUC of 0.90-1: Excellent (Grade A)
- AUC of 0.80-0.90: Good (Grade B)
- AUC of 0.70-0.80: Fair (Grade C)
- AUC of 0.60-0.70: Poor (Grade D)
- AUC of 0.50-0.60: Fail (Grade F)
  
This guide provides a rough classification based on the AUC value, helping to interpret the diagnostic test's accuracy.


![Model_Scores](https://github.com/Wilson-CK/17.1-Practical_Application/assets/146282056/26858ae0-6669-4c5a-a7da-dfd13c458aba)

## <span style="font-size:larger;">Model Comparisons</span> 

![FP_Comparisons](https://github.com/Wilson-CK/17.1-Practical_Application/assets/146282056/656f43df-2330-4ece-a849-613c152735cb)


In evaluating the models, we consider two types of incorrect predictions:

- False Positives: The model predicts a client subscribed to a term deposit when they did not.
- False Negatives: The model predicts a client did not subscribe when they actually did.
  
In my assessment:

- False Positives are more detrimental because we may erroneously believe we have the client, potentially resulting in missed opportunities in future campaigns.
- False Negatives, while not ideal, mean we still have the client, and any oversight can be rectified in the future.
Therefore, our objective is to identify the best model based on the confusion matrix with the lowest possible False Positives. Upon examination, the Decision Tree Model stands out with the lowest False Positive count, totaling 433.

![Model_Comparisons](https://github.com/Wilson-CK/17.1-Practical_Application/assets/146282056/ed429321-6794-477c-aa96-a925378c1881)

While there's no "perfect" model here, **Logistic Regression** stands out as the optimal choice, demonstrating the best combination of Train and Test Accuracy. It does require more training time than other models, however, in a robust system, it should not have a significant impact to overall efficiency and effectiveness for predictions.

## <span style="font-size:larger;">Improving the Model</span> 

- With tuning using SMOTE method, we are able to increase accuracy from just using max depth of 8 previously to now 6 with DecisionTreeClassifier.

- Bagging with Decision Tree has the best performance according to recall and ROC. The ideal number of neighbors was initially determined to be 24, resulting in an accuracy of 90.5%. Through further experimentation, accuracy has now improved to 93% by reducing the number of neighbors to 8, all achieved without additional feature engineering.

## <span style="font-size:larger;">Executive Summary & Recommendations</span> 

Interpreting the results and leveraging insights from exploratory data analysis, the bank can strategically focus on key features to attract more customers to buy term deposits:

1) **Duration Significance:** The duration of customer engagement has a substantial impact on the deposit outcome. Longer interactions correlate with a higher probability of customers making a deposit. Focusing on strategies to enhance customer engagement during interactions can positively influence deposit outcomes.
2) **Economic Climate Influence:** The state of the country's economy emerges as a pivotal factor. During periods of economic prosperity, customers tend to be more willing to make deposits. Targeting campaigns during these favorable economic periods can maximize effectiveness.
3) **Month-Specific Campaign Strategy:** October, characterized by heightened economic fluctuations, emerges as a challenging month. Consideration should be given to avoiding campaigns during this period to mitigate potential negative impacts.
4) **Occupational Influence:** Individuals in blue-collar jobs, administrative roles, and technical positions exhibit higher probabilities of making a deposit. Tailoring campaigns to resonate with these occupational groups can yield more favorable outcomes.
5) **Education Level Impact:** Customers with a solid educational background, particularly those with a university degree or higher, show a higher likelihood of making a deposit. Recognizing the influence of education on financial behavior can guide targeted strategies for customer segments.

By strategically addressing these key variables, the bank can optimize its approach to attract and retain customers for term deposits.
