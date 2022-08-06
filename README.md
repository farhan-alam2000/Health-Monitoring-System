# IOT based Health Monitoring System

Demonstration video link - https://www.youtube.com/watch?v=cfOU3Oz8VY0 

# Problem Statement

Health, according to the World Health Organization, is "a state of complete physical, 
mental and social well-being and not merely the absence of disease and infirmity”. 
But in modern times, physical health is not prioritised by the youth owing to fast paced work life and the constant need to outrun other competitors. With most of the people leading sedentary lifestyles, it’s pretty obvious why health issues are on the up. Most of the time, people with serious health diseases do not find out about it until it’s too late. 
Due to COVID-19, mental and social health has also taken a hit because we are all but confined to our houses, with no real interaction with the outer world. These issues further aggravate physical health. It is clear that remote healthcare monitoring is the future, as communicable diseases like COVID-19 become common.

#Role of IoT
The Internet of Things is a relatively new idea that is defined as the integration of all network-connected devices that can be managed via the web and, in turn, offer real-time information to allow interaction with people who use it.
Our project falls under the IoT realm, as it involves things sensing, interpreting, and communicating with other things, as well as exchanging information with people.
Sensors: MAX30100 Pulse Oximeter Sensor, DS18B20 Temperature Sensor, DHT11 Humidity and Temperature sensor
Actuator: Notification Message (Email)
Thing: Health Monitoring Device
Processor/Controller: ESP8266 NodeMCU
Connectivity: NodeMCU, Thinger.IO IoT Cloud Platform

# BACKGROUND INFORMATION : Dataset for  ML
Before training the model, analysis of data is necessary to determine important attributes and the correlation between the attributes. For this purpose we have used Power BI to determine the univariate and bivariate relationship between attributes and visualise the dataset. Inferences from EDA (Exploratory data analysis) are as follows -

Age and gender are less important features as the ratio of total population to sick population is same irrespective of the gender and age.
Scatter plot diagram of body temperature vs fever clearly shows that around 98-99 degrees Fahrenheit people get feverish.
To have a rough idea of normal range of pulse rate and blood oxygen level we have plotted a line chart for ‘pulse rate vs medical aid required’ and ‘blood oxygen level vs medical aid required.

The dataset consists of 5 attributes that are:
Body Temperature (in Fahrenheit) 
Pulse rate 
Blood Oxygen Level
Age
Gender
Data Filtering

The ML model used is multivariate logistic regression. Model is trained on a labelled dataset to determine whether the patient requires medical aid based on his/her current vitals. Filters applied before training the models are-
Fields having invalid readings (extremely low or extremely high) due to hardware malfunction were removed.
Dataset was divided into two subsets because we used two different models for generating different inferences.
To make the algorithm more robust and reduce false positives, following filters to reduce noise are also applied
Fields with missing values, or NULL values were removed because it can give false results.
Temperature was rounded up to 1 decimal place.
Fields having out of bound readings (Eg. Blood oxygen level more than 100%) were removed.
Data Aggregation 

For training the models, dataset was divided into 2 subsets. After training subsets were aggregated and a new attribute was introduced “Medical_aid_required” that determines the patient’s current condition and takes necessary action (in our case email notification is sent to patient’s family and doctor).

# HARDWARE COMPONENTS

i. ESP8266 NodeMCU 

ii. MAX30100 Pulse Oximeter Sensor

iii. DS18B20 Temperature Sensor

iv. DHT11 Humidity & Temperature Sensor

v. Resistors and connecting wires.


# WORKING AND METHODOLOGY

Approach

The patient keeps their finger on the pulse oximeter sensor, and the body temperature sensor in their armpit. 
The sensors of the monitoring system sense the following parameters:

-> Pulse Rate (BPM)

-> Blood Oxygen Level (SpO2)

-> Body Temperature

-> Room Temperature

-> Room Humidity


Room temperature and humidity are measured so that the person monitoring can get to know if the temperature or humidity is too high or too low, so they can lower temperature of the room by turning on the AC, or shifting the patient to another room with less sunlight, etc. The sensors send the values to the NodeMCU (ESP8266) wifi module, which sends the data through the internet to the Thinger.IO cloud platform, where the readings of the patient can be viewed remotely. 
Through the readings of the various values, the Machine Learning model predicts whether the patient needs medical aid or not. If the ML model (that uses multivariate logistic regression) predicts yes, an email notification is sent immediately to the email ID stored by the person monitoring on the Thinger.IO platform.
At Thinger.IO, the readings of all the parameters are displayed on the dashboard, and also listed are all the devices connected. The data is also stored at regular intervals in the data buckets as rows and columns.

# CONCLUSION
We used IoT to measure and display patient’s health metrics remotely and in real time.
The results are examined, and our system has come out to be stable. The collection of data is fairly precise, and it has features like instant notification email as instructed by the ML model.
The temperature of the participants was measured using a body temperature sensor, which produced temperature readings of 97.3, 97.2, and 97.6 (°F), indicating relatively accurate and stable testability. Similarly, the pulse oximeter sensor detects pulse rates of 76, 77, and 77 (beats/min) and oxygen levels of 95, 95, and 96 percent (SpO2), which are similar to the results of a medical pulse oximeter.
The user's pulse rate, body temperature, and heart rate, as well as room temperature and humidity, have been collected by the remote patient health monitoring system designed in this study. The ML model used to predict if the patient needs medical aid also has an accuracy of 92.3%. 
More research should be carried out w.r.t. aspects that lead to an increase in health risks. The use of IoT for remote monitoring will increase as data will be collected for a long span. In the coming years, this will provide a science based and potent foundation for identifying, controlling and preventing chronic and high-risk diseases.


# For more details, circuit diagrams and visualizations refer the PPT
















