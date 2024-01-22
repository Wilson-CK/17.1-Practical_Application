## <span style="font-size:larger;">**Practical Application Assignment: Comparing Classifiers**</span>

**Goals:**
- Compare the performance of the classifiers (k-nearest neighbors, logistic regression, decision trees, and support vector machines)
- Use a dataset related to the marketing of bank products over the telephone

**Github repository:** https://github.com/Wilson-CK/17.1-Practical_Application

**Link to Jupyter Notebook:** [https://github.com/Wilson-CK/Car_Prices_Analysis/blob/main/11.1-Wilson-Try_It.ipynb](https://github.com/Wilson-CK/17.1-Practical_Application/blob/main/17.1-Practical_Assignment.ipynb)

What's included:  This README, Jupyter notebook, and original data files. 

## <span style="font-size:larger;">Understanding the Data</span>

Dataset references the UCI Machine Learning repository:  https://archive.ics.uci.edu/ml/datasets/bank+marketing

The data is from a Portuguese banking institution and is a collection of the results of multiple marketing campaigns. The dataset collected is related to 17 campaigns that occurred between May 2008 and November 2010. Each campaign involved phone marketing with a human agent as the interlocutor, and sometimes an auxiliary use of the Internet online banking channel. The results for all channels were managed in an integrated fashion and outputted together.¶

## <span style="font-size:larger;">Read in the Data</span>

In the dataset, we observe a total of 21 columns. These columns are categorized into two types:

1) Numerical/Quantitative DataTypes:
Numerical data represents information in numerical form rather than in language or descriptive form. Examples include age, duration, campaign, pdays, previous, emp.var.rate, cons.price.idx, cons.conf.idx, euribor3m, and nr.employed.

2) Categorical/Qualitative DataTypes:
Categorical data is characterized by names or labels. Examples of categorical columns in our dataset are job, marital, education, default, housing, loan, poutcome, contact, month, day_of_week, and y.

## <span style="font-size:larger;">Understanding the Features</span>
Utilizing the describe function provides a comprehensive understanding of the dataset. It allows us to grasp the range, means, standard deviations, maximum and minimum values, as well as percentiles of the data. This comprehensive overview enhances our ability to interpret and analyze the dataset effectively.

Upon closer inspection, it becomes evident that the data ranges across columns exhibit significant variations. For instance, the mean of nr.employed is 5167.035911, while the mean of emp.var.rate is 0.081886. Such disparities in scales highlight the need for normalization to improve the overall quality of our data.

## <span style="font-size:larger;">Understanding the Task</span>

The business objective of the task is to develop a model that effectively explains the success of a contact, specifically whether the client subscribes to the deposit. The primary goals of this model are to enhance campaign efficiency by:

1. Identifying key characteristics that significantly impact success in subscribing to the deposit.
2. Facilitating better resource management, including human effort, phone calls, and time, through informed decision-making.
3. Enabling the selection of a high-quality and cost-effective set of potential customers who are likely to make a purchase.
   
Achieving these objectives will contribute to a more targeted and efficient marketing strategy, optimizing the allocation of resources and improving the overall success rate of deposit subscriptions.

## <span style="font-size:larger;">Engineering Features</span>

Bank Client Summary

Age, with its moderate dispersion, does not yield significant insights when related to other variables.

For Jobs, Marital, and Education, a straightforward analysis based on the count of each variable might be the most informative. However, when related to other variables, the results are inconclusive. It's worth noting that these variables exhibit 'yes,' 'unknown,' and 'no' values for loan, default, and housing.

To construct a socio-economic group of variables, we can create a composite variable termed 'bank_se.'

## <span style="font-size:larger;">A Baseline Model</span>

To outperform the baseline, our classifier should exhibit the following qualities:
- High training accuracy to effectively learn from the training data.¶
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

In addition to KNN baseline model, I also deployed the following models for comparison:
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














**Executive summary**

This report unveils the outcomes of our examination into the pricing dynamics of pre-owned cars. Our aim was to pinpoint the critical factors that impact these prices and offer suggestions to enhance the management of dealership inventory.

**Methodology**

Performed data mining analysis against the dataset of ~426K vehicles, leveraging various methods from the cleansing and transformation of data to the generation and assessment of regression models and subsequent validation to ensure the selected model is a high-performing one with reliable result.

**Key Findings**

Relevant Factors: Identified several factors significantly correlated with used car prices, including the car's year, brand, transmission type, body type, and fuel type.

  1.	The features that positively affect price increase the most are:
  
  - The year and odometer of the vehicle: generally, the newer and few miles it possesses, the more expensive it is
  
  - Vehicles with 8, 10, and 12 cyclinders tend to cost more; however, there appears to be lower sales volume than their 6-cyclinder and smaller counterparts
  
  - Diesel fuel and electric vehicles tend to have higher prices
  
  - Pickups and trucks carry higher sticker prices
  
  - Clean and lien-titled vehicles tend to be priced higher than the rebuilt, salvage, missing, and parts-only counterparts

  2.	Missing data: A notable amount (~15%) of missing data exists in the provided dataset.

  3.	There's an interesting dependency of the average car price based on the state of origin, which in turn depends on the brand. A clear example is Washington and Utah states, where the average sale prices tend to be higher than those from other states.

  4.	A critical missing piece is the operating cost and profit margin per each vehicle. While our dataset illustrates the used car prices, a dealer theoretically can make profit at every pricepoint. Furthermore, I couldn't ascertain the supply and demand landscape, e.g. were prices sold above or below asking price, did some cars sit on the lot for an extended period before they were sold, etc..

**Recommendations [Assumption: if charging more money for the vehicle price by the dealer is the goal]**

  1.	Inventory Optimization: Using the predictive model, dealerships can more accurately gauge how much they can charge for cars in their inventory

  2.	Focus on Key Features: Special attention is advised for features with higher influence on prices, such as car year, odometer reading, number of cyclinders, fuel type, and manufacturer brand

  3.	Ongoing Monitoring: As new data becomes available, periodic updates and refinements of the model are recommended to maintain accuracy and relevance

  4.	Additional inputs from dealers: To increase the relevance and impact of the recommendation, dealers should incorporate operating and profit margin data, plus supply and demand landscape of the vehicles

**Conclusion**

The insights derived from this analysis offer valuable guidance to used car dealerships seeking to streamline operations and improve decision-making in the realm of inventory management.

**Next Steps**

Model Implementation: 

  1.	Communication: Report out an overview and detailed analysis of the findings, communicate from:
     
  - Pertinent front-line employees to the C-suite, with each persona having a right-for-role messaging

  - Dealer to dealer - especially sister stores or partners - to share lessons learned and best practices

  2.	Integration: Work in conjunction with the technical team to integrate the predictive model into dealership environments; train the workers on usage and gather continual feedback

  3.	Monitoring and Updates: Set up an ongoing monitoring process to evaluate the accuracy of the model and make updates as necessary

  4.	Continued Exploration: Explore additional variables and features that could influence prices and assess their potential inclusion in the model
