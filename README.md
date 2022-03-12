# Chicago Crime Data analytics

This is a class project for a data science programing class. I worked with Emilio Cabrera, Lucas Fernandez, and Branda Huang

The .ipynb is in a Zip file as the map visualization package creates a large file. 

We downloaded the data from Chicago's police department statistics website. 

Below is a description of the project. 

## Description of Project Goals
Description. For our project we utilized the data set of crimes for the city of Chicago, where we looked for patterns of crime across different geographical areas, time of day, season, crime type and the arrest rate across the city. Please see the attached PowerPoint named Attachment Directory, to see the Appendices.
The dataset reflects reported incidents of crime (apart from murders) that occurred in the City of Chicago from 2001 to present, minus the most recent seven days. Data is extracted from the Chicago Police Department's Citizen Law Enforcement Analysis and Reporting (CLEAR) system. The dataset contains more than 7,369,258 records/rows of data across 22 different variables. (Appendix A) 
The following is a list of questions that our group set out to answer: 
•	When is the best time of the year to visit Chicago?
•	Is there a specific  time of day one should tour Chicago?
•	Which wards have the highest/lowest crime rates?
•	Did COVID-19 or the legalization of weed influence crime?
•	Is there a way to predict the likelihood of an arrest given the features of the crime committed?
Importance. The dataset is valuable as it rich in size and being updated daily. Another valuable aspect of our dataset is its applicability to travelers, Chicago municipalities, and local third-party businesses.
As safety is key component when traveling, Chicago’s 50+ million annual tourists could use the dataset along with our report when visiting the city. It also might prove valuable to Chicago’s current 2.7 million residents.
At the government and municipal level there’s constant criticism surrounding allocations of funds. Certain neighborhoods require more resources/funds than others due to the residual effects of crime such as jails, social workers, cameras, and security to name a few. 
The applicability does not stop at the government level, third party businesses could us this data for strategic purposes, such as certain areas to avoid opening a business due safety and sustainability purposes. On that note, business related to crime services would know where to open.

 
## Exploratory Analysis
YoY Crime Trends. From 2016 to 2019 there had been an annual decrease in crime ranging 1% to 3%, while 2020 saw a drastic drop of about 20% in crime. Our analysis further investigates this drop with the legalization of marijuana and COVID-19 being two possible explanations.

Legalization of Marijuana. In 2020 it became legal to have up to 30g of weed on your person in the city of Chicago. This influences the number of crimes because the number of potential crimes decreases. We do not care about how many crimes are seen but how many are committed. We need to soft the data to find the cannabis related crimes within the dataset and then be able to control for them. 

Time. When looking at the ‘time of day’ for a given crime occurrence, crimes are most common during the hours of Dusk (4pm-8pm) and Afternoon (12pm-4pm). Finding that the afternoon was a prevalent time of day for crime was unusual at first but made sense as it remained more dangerous relative to sunrise and early morning. (Appendix C). 

Average Crime Rates. Over the past 20 years of our data, the average number of crimes per day was about 1100. However, the average number of crimes per day during COVID was about 560. This led us to believe that COVID might have had a big effect on crime. We later found that the period shortly before COVID had an average 1400 crimes per day. We needed to test whether COVID reduced this rate or if the reduction was a part of the long-term trend of decreasing crime.

Safety in Wards. When looking at the safety in different wards, the number of crimes in the 10 most dangerous wards is more than three times higher than in the safest wards. An average of 32 crimes are reported daily in dangerous wards. Some of the most dangerous wards are 2, 24, 27, 28, and 42 while wards 19, 33, 39, 45, and 48 are the safest areas in Chicago. (Appendix D, E)

 
## Solution & Insights
Crime Trends.
•	Season. After segmenting the crime occurrences based off time of year/season, there is a high correlation between Summer and crime. (Appendix B)
•	Time of Day. After segmenting based off time of day, the afternoon (12pm - 4pm) was the most dangerous time of day while the safest time of day was sunrise (5am - 9am). Due to this correlation, one might recommend starting the daily commute early in Chicago to avoid crime. (Appendix C)
•	Trends over year: 30% more crimes were reported in the first 10 years (2001-2010) than that in the second 10 years (2011-2020). Moreover, the dangerous and the safe areas have stayed the dangerous and safe areas over the past 20 years. Particularly, 42nd Ward became more dangerous and 38th became safer in the past 5 years. (Appendix F)
•	Safest / Dangerous Wards: Northern Chicago above Lincoln Park is safe. As for Southern Chicago, the west part of Southern Chicago seems quite safe while the east part tends to be dangerous. Moreover, the southwest region below West North Ave has historically been and remains to be the most dangerous – 2001 to present. (Appendix G, H)
•	Safest / Dangerous Streets: West part of Garfield Park is the most dangerous area. More specifically, the block of West Jackson Blvd and South Pulaski Road are the most dangerous streets. (Appendix G, H)
Multilinear Regression on Crime. 
Crime, cannabis legislation, and a dropping crime rate. When looking at the data we wanted to control for as many factors as possible. We started with the presence of cannabis related crimes. Chicago passed legislation to allow a certain amount of cannabis per person, we hypothesized that this would drop the crime rate, so we controlled for this. We found a negative correlation between this and crime rate. During further visualization techniques we found an overall decline in crime over the period, not just corresponding to cannabis. We decided to use Day as an instrumental variable. This was to control for all the variables that could not be quantified, or we did not have data for. Possible cultural shifts could contribute to the drop, we cannot easily quantify that. It would also control for more wealth coming into the area and shifting the crime rate. This variable captures much of what we cannot and helped us create a strong regression model to find the effect that COVID had on the crime rate (Appendix I, J, K)
COVID on Crime. We found that COVID did have a significant effect on the reduction of the crime rate. It related to a little less than a 10% decrease in crime per day in the city of Chicago, in addition to the decrease caused by changing social factors which lead to a constant decrease over the past 20 years. (Appendix I)

## Logistic Regression on Arrests.
Regression Setup. The basis for the problem to our logistic regression was: Is there a way to predict the likelihood of an arrest given the features of the crime committed? The predictor variables used for the model are time of day, type of crime, location description, and District in the city, all of which are categorical variables. District and Primary Type are the chosen predictors for location and type of crime to avoid highly correlated variables representing the same features. The number of iterations is set to 200 to make the model time efficient.
Results. The results of the logistic regression are a training and testing accuracy of 87.70% and 87.72%, respectively. The baseline accuracy for the testing data is 80.92%. The accuracy of the model outperforms baseline and gives us somewhat accurate results, though an accuracy above 90% is desired. The sensitivity of the model, however, was only 44.20% indicating that the model has trouble predicting positives. (Appendix L)
Interpretation. The features that have the greatest impact on the arrest are the primary type of crime and then the location description to a lesser extent. The types of crime with the highest arrest rates are Narcotics, Prostitution, Gambling, and Liquor Law Violations while the crime with the lowest arrest rates were Deceptive Practice, Non-Criminal (so not even arrest worthy), Theft, and Criminal Damage. Intuitively, this makes sense as the crimes with high arrest rates are “victimless crimes” where the crime is only reported by the arresting police officer. These types of crimes go heavily under reported so the arrest rate appears artificially high. The crimes with low arrest rates appear to be common, low-impact non-violent crimes indicating that police in Chicago may not view these as a high priority. Location description has some impact on arrest rates as places like department stores had high arrest rates while nursing homes had low arrest rates. Surprisingly, the time of day and district has minor impact on the arrest rate. (Appendix M)
