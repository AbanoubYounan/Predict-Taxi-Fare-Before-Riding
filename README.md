# **Objective**
The goal of this project is to build a machine learning model that predicts the fare of a taxi trip before riding to make it easier for users, especially tourists and strangers, to know how much they will pay.

# **EXECUTIVE SUMMARY**    
This project based on 2022 NYC Yellow Cab trip record data (https://data.cityofnewyork.us/Transportation/2022-Yellow-Taxi-Trip-Data/qp3b-zxtp).
To that end, I will demonstrate the phases of the data science pipeline:
1. **[Random Sampling](#sampl)** Make a Random Sample from the large original CSV file with (39.7 Milions rows & Size More than 3.5 GB) to make the analysis and modeling process more efficient.
2. **[Exploratory Data Analysis-EDA](#eda)**
    1. **[Discovering & Structuring](#discStruc)** Check out the overall shape, size, and content of the dataset and transform the data into a usable format for analysis.
    2. **[Cleaning](#clean)**: Check for outliers, missing data, and needs for conversions or transformations.
    3. **[Feature Engineering](#fEng)**:
        1. **[Feature Transformation](#fTrans)**
        2. **[Feature Selection](#fSel)**
        3. **[Feature Engineering](#fEng2)**
    4. **[Validating](#Valid)** Validate Data to ensure it's ready for modeling phase.
    5. **[Presenting](#present)**: Presenting EDA findings.
3. **[Algorithm Development](#ml)**: Train, test, and refine various models to predict the target variable.  Given that our dependent variable `trip_duration` is a continuous outcome,  the regression algorithms to be protoyped are as follows:
 - [Multivarite Linear Regression](#linear)  


4. **[Model Deployment](#deployment)**: Apply the best performing model to the test set for contest submission.


# **ABOUT THE DATA**  
The  dataset is based on the 2022 NYC Yellow Cab trip record data. Its variables are as follows:

| **Variable Name** | **Description** | **Type**|          
| :------------------ |:-------------|:-------------|   
|vendor_id    | A code indicating the TPEP provider that provided the record.     | Number|
|pickup_datetime |  date and time when the meter was engaged|  Data & Time|
|dropoff_datetime|  date and time when the meter was disengaged|  Data & Time|
|passenger_count|  the number of passengers in the vehicle (driver entered value)|  Number|
|trip_distance |  The elapsed trip distance in miles reported by the taximeter.| Number|
|RatecodeID | The final rate code in effect at the end of the trip. | Number |
|PULocationID | TLC Taxi Zone in which the taximeter was engaged|  Number |
|DOLocationID  |   TLC Taxi Zone in which the taximeter was disengaged|  Number |
|store_and_fwd_flag | This flag indicates whether the trip record was held in vehicle memory before sending to the vendor because the vehicle did not have a connection to the server - Y=store and forward; N=not a store and forward trip   | Plain-text|
|payment_type | A numeric code signifying how the passenger paid for the trip. | Number |
|fare_amount | 	The time-and-distance fare calculated by the meter. | Number |
|extra | Miscellaneous extras and surcharges. | Number |
|mta_tax | 	Tax that is automatically triggered based on the metered rate in use.| Number |
|tip_amount | This field is automatically populated for credit card tips. Cash tips are not included. | Number|
|tolls_amount | Total amount of all tolls paid in trip. | Number |
|improvement_surcharge | Improvement surcharge assessed trips at the flag drop. The improvement surcharge began being levied in 2015. | Number |
|total_amount | The total amount charged to passengers. Does not include cash tips. | Number|
|congestion_surcharge | Total amount collected in trip for NYS congestion surcharge. | Number |
|airport_fee | For pick up only at LaGuardia and John F. Kennedy Airports. | Number |