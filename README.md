# <center> Incident Management <center>

# G4v1 beta version´s 70% Accuracy 

We created a scalable AI-powered solution that can be used as a tool to predict ticket turn-around-times and model the system to make informed decisions on phasing, resource allocation and structuring high performance with your team. 

G4 version 1 (G4v1) is a classification model that predicts ticket resolution turn-around-time with a 70% accuracy. To demonstrate G4v1`s performance, we extracted data from your publication then focused on the incident tickets from two categories:

    * tickets resolved in ≤2 
    * tickets resolved in ≥2 

```mermaid
* Flowchart visualization 1: 

    A[Ticket Submitted by Client] --> B[Categorize Ticket by Priority]
    B --> C1[High Priority]
    B --> C2[Medium Priority]
    B --> C3[Low Priority]

    C1 --> D1[Assign to Staff (CS Tech)]
    C2 --> D2[Assign to Staff (CS Tech)]
    C3 --> D3[Assign to Staff (CS Tech)]

    D1 --> E[Check Status (Day 2)]
    D2 --> E
    D3 --> E

    E --> F{Resolved?}
    F -->|Yes| G[End]
    F -->|No| H[Escalate to Developer]

    H --> I[Assign to Developer]
    I --> J[Developer Resolves Ticket]


* Flowchart visualization 2:

[Ticket Submitted by Client]
             |
             V
[Categorize Ticket by Priority]
        /        |         \
   [High]   [Medium]   [Low]
      |          |         |
      V          V         V
[Assign to]  [Assign to] [Assign to]
[Staff]       [Staff]       [Staff]
   (CS Tech)   (CS Tech)   (CS Tech)
      |           |           |
      V           V           V
[Check Status (Day 2)]
      |
      V
[Resolved?] -- No --> [Escalate to Developer]
      |                   |
      V                   V
    [End]        [Assign to Developer]
                           |
                           V
                    [Developer Resolves Ticket]
                           |
                           V
                         [End]

     
 
Incident ticket process:

1. **Ticket Submitted by Client (Day 1)**
   - Start

2. **Categorize Ticket by Priority (Day 1)**
   - **High Priority**
   - **Medium Priority**
   - **Low Priority**

3. **Assign Ticket to Staff (Day 1)**
   - **Customer Service Technician**
   - **Developer** (if applicable based on the category or escalation rules)

4. **Ticket Status Check (Day 2)**
   - **Resolved by Customer Service Technician**
     - **End**
   - **Not Resolved / Escalated**

5. **Escalate Ticket to Higher Priority (Day 2)**
   - **Assign to Developer**

6. **Developer Resolves Ticket**
   - **End**


In this flowchart:

1. A ticket is submitted and categorized by priority on Day 1.
2. It is assigned to the appropriate staff member based on the priority.
3. On Day 2, the status of the ticket is checked:
   - If resolved, the process ends.
   - If not resolved, the ticket is escalated and reassigned to a developer, who then resolves it.

This flow ensures a systematic approach to handling and escalating incident tickets. Resolve issues quickly and speed the pace of innovation, using AI and machine learning.


## G4v1`s AI-Based Forecasting Tool Technical Highlights 

The software is currently a Beta version within 3 to 6 months we will work closely with you to release the final product into production. 


* 24,000 Tickets present within the system. 
    * Data was minded and reviewed by the team to determine the best proof-of-concept AI model. 
* Redundancy in Ticket Numbers and Data Reconciliation 
    * Ticket numbers were found to be redundant, despite being in multiple phases. A decision was made to use a regression model and two categories: resolved_at and opened_at 
* Data showed significant gaps in many categories and contained values such as “?”.
Data provided mixed values of objects and unreadable values which required a multistep data clean up. 
Best practice is to copy the dataframe then  “‘?” objects were replaced with  “NaN” 
df_nan = df.copy()
df_nan = df.replace('?',np.nan)

System identified the unknown “?” and NaN as objects, thus we converted categories of interest into datetime


df_nan['opened_at']= pd.to_datetime(df_nan['opened_at'],dayfirst= True)
df_nan['resolved_at'] = pd.to_datetime(df_nan['resolved_at'], dayfirst = True)


Note: The difference between “resolved at” and “closed on” were reviewed then tabled for future enhancements of this model to be used for your internal system operations and efficiency plans. 

It was determined that the G4v1 model would be constructed to capture the aforementioned two categories: 
tickets resolved in ≤2 
tickets resolved in ≥2 



        Partial Code Example 1: 
            df_nan['target_colum'] = df_nan.apply(lambda row: 1 if pd.isna(row['resolved_at'])
            or (row['resolved_at'] - row['opened_at']).days > 2 else 0, axis = 1)


        Partial Code Example 2-  Converting NaN to integers: 
            if pd.isna(value):
            return -1  # converts NaN values to -1
            return str(value).split(" ")[-1]  # splits the string and then captures the last value

Dataframe was subdivided to isolate an incident ticket number which was found to have the greatest amount of duplicates in each row. Later we concatenated the complete integer training dataframe into one full dataframe for concise processing at the time of training. 
A calculation of the columns against the target column was conducted to ensure that there were no highly correlated values which would cause downstream errors (bias). 

        Partial Code Example 3:

            dfx_y.corr()['target_colum'].sort_values()

* Further steps and code clean up prior to training can be found in the text of the jupiter file. This is intended to facilitate the handoff from G4 Solutions to your team of  developers and data scientists. 



Top Model Performance seen with 7 of the 32 features 
A collaborative venture can help to elucidate the meaning of the missing data and fields which were documented with a “?”
About 50% of data provided consisted of missing information

Case Study: Category “Knowledge” data resolution is likely to generate an increase in value and result in a higher correlation. OnehotEncoder was used with a conversion result of 15,000 zeros and 9,000 ones. 



	Partial code example: 
  
        def onehot_bool(value):
        """parameters: columns with boolean values
        Return: 1 for True and 0 for False
        call: df['column] = df['column'].apply(onehot_bool)"""
        if value == True:
            return int(1)
        return int(0)


#call and replace boolean columns
train_df['knowledge'] = train_df['knowledge'].apply(onehot_bool)
train_df['u_priority_confirmation'] = train_df['u_priority_confirmation'].apply(onehot_bool)

### Scores 

![](https://github.com/Sug-ar-N-Spice/Incident_Management/blob/main/Scores.png)

### Test and Train Plots 
![](https://github.com/Sug-ar-N-Spice/Incident_Management/blob/main/train%20and%20test%20plot.png)


# Operational Excellence and Data-Driven Leadership

![](https://github.com/Sug-ar-N-Spice/Incident_Management/blob/main/2.png)

![](https://github.com/Sug-ar-N-Spice/Incident_Management/blob/main/3.png)

![](https://github.com/Sug-ar-N-Spice/Incident_Management/blob/main/4.png)
![](https://github.com/Sug-ar-N-Spice/Incident_Management/blob/main/5.png)
![](https://github.com/Sug-ar-N-Spice/Incident_Management/blob/main/6.png)
![](https://github.com/Sug-ar-N-Spice/Incident_Management/blob/main/7.png)
