# Incident_Events

 I Helped with some coding, but TY was the most involved. I help with the presentation and presenting. 

 
Concept: The idea of predicting which incident tickets will take longer than 2 days to resolve is valuable. This could help IT departments prioritize and allocate resources more effectively, potentially improving overall service quality and customer satisfaction.
Model Performance: A balanced accuracy score of 70% is a good starting point, especially considering that you're only using information available at ticket creation. However, there might be room for improvement.
Budget and Timeline: $75,000 for 6 months, including a 3-month trial period, seems reasonable for a collaboration project of this nature. It allows for both development and proof-of-concept phases.


Emphasize ROI: Clearly articulate the potential return on investment for ServiceNow. How much time and money could be saved by identifying long-resolution tickets early? Consider presenting a cost-benefit analysis.

ROI: 
Ticket submitted 
Ticket turnaround time. 

Feature Importance: Highlight the most important features in your model. This can demonstrate your understanding of the problem and may provide insights that are valuable to the IT department even without the model.

 This model includes machine learning to predict ticket turn around times. 

Model Improvements: Outline potential ways to improve the model's accuracy, such as incorporating more data sources or using more advanced algorithms. This shows foresight and a commitment to ongoing improvement.

          We extracted the data provided from your team and generated a prediction model for ticket turnaround time. Subsequent to onboarding, we will work with your team to obtain data about the service level agreement and ticket priority level classification criteria. This will enable us to refine the model and tailor it to be used for optimization of ticket turnaround time. 

Amaral, C., Fantinato, M., & Peres, S. (2018). Incident management process enriched event log [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C57S4H.


Integration Plan: Discuss how your model could be integrated into ServiceNow's existing systems. This demonstrates that you've thought about practical implementation.
Collaboration Details: Outline how you plan to work with their teams. Will you need access to certain resources or personnel? How will you ensure knowledge transfer?

This product will be locally hosted by ServiceNow. G4 will contract with ServiceNow as consultants during the implementation stage and will receive credentials and access to API to transfer the IncidentMangement Tool. A representative sample of data will be copied into a dev environment to test the IncidentManagement Tool. 5 ServiceNow employees will be assigned multiple user roles: Client, Customer Service and Admin. Each employee will walk through the process of submitting a ticket, responding to a ticket, and closing a ticket. 
 
Scalability: Address how your solution could be scaled to handle different types of tickets or adapted for other departments.

This product can be scaled to handle tickets in the medical space. 

Performance Metrics: Consider including other relevant metrics besides balanced accuracy, such as precision, recall, or F1 score, especially if they highlight strengths of your model.

count    138571.000000
mean         10.871286
std          27.078124
min           0.000000
25%           0.000000
50%           3.000000
75%          10.000000
max         336.000000
Name: difference, dtype: float64

df_nan["difference"].median()
3 
df_nan["difference"].mean() 10.87


STD is 27 makes sense because 75% of the data is skewed to the right toward the end. (upper quartile) 




https://www.investopedia.com/terms/b/binomialdistribution.asp

https://medium.com/@amit25173/probability-density-function-of-binomial-distribution-dc0e4f1ade8a


Area under graph is equal to 1 









SOME MODELS You only get meaningful results if data is normally distributed 


Resolved – maybe saying resolved and tester is not testing 

So you draw this norm dis curve to show – data from 

#df_nan['difference'] = (df_nan['resolved_at'] - df_nan['opened_at']).dt.days
resovled_closed_diff = (df_resolved['closed_at'] - df_resolved['resolved_at']).dt.days
resovled_closed_diff.value_counts()


Employee efficiency metrics 

SCRUM meetings – ticket moved, resolved, closed 

Ticket with these attributes… most likely going to be closed on X after resolved 


# Define the parameter grid for AdaBoostClassifier
param_grid_ab = {
   'n_estimators': [50, 100, 200, 400, 500],
   'learning_rate': [0.01, 0.1, 0.5, 1.0],
   'algorithm': ['SAMME', 'SAMME.R'],
   'estimator': [
       DecisionTreeClassifier(max_depth=1),
       DecisionTreeClassifier(max_depth=2),
       DecisionTreeClassifier(max_depth=3)



Used multiple models to compare and determine the best model 



Comparison: If possible, compare your model's performance to current methods of prioritizing or predicting ticket resolution times.


Trial Period Objectives: Clearly define what success looks like for the 3-month trial period. Set specific, measurable goals.




Future Potential: Briefly touch on potential future applications or expansions of the model, showing long-term value beyond the initial 6-month period.



