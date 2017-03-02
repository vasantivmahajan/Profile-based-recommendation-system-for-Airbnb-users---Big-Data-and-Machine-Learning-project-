# Profile-based-recommendation-system-for-Airbnb-users---Big-Data-and-Machine-Learning-project-

## Problem Statement
Airbnb is an online market place that enables users to list, find and rent vacation homes. Airbnb connects people to unique travel experiences, at any price point, in more than 34,000 cities and 191 countries. Airbnb has a diverse customer base, it is used by people from different age groups, professions and interests. Some customers prefer places which are closer to the city whereas some others love to enjoy the natural beauty by living in cottages. Since every customer has different interests it is essential that the user is recommended houses on the basis of their profile.

## Proposed System:
I along with my team, developed a profile based recommendation system using supervised learning techniques where user’s future trips are predicted on the basis of their past trips and preferences. User's age group, profession, interests and most frequently traveled seasons are taken into consideration for building the user's profile. The proposed system would build a good customer experience by reducing the average time of booking and better demand forecasting. 

## Approach:
 
Step 1: Data Cleaning and Feature Engineering:

Airbnb provides an open source dataset which contains 1.3 million listings that are posted on their website. It also has details regarding the Airbnb users and their past trips. The listings data contains information like number of bed rooms, amenities, ratings, house rules, GPS location, etc. The user's data contains information like age, profession, past trip details, etc. 

Data Cleaning: We handled missing values, garbage values, performed outlier detection and data normalization to clean the data. We used Alterxy tool for these operations.

Feature Engineering: Using the user’s travel history, we computed the seasons in which the user most frequently travels in. We identified the type of apartments the user stays in to identify user’s interests and preferences.

Kindly refer to the Alteryx scripts used for Data Cleaning and Data Transformation.

Step 2: Calculating the score for every listing using Neural Network:

For every listing we computed the score to analyse how suitable a listing is on the basis of age-group, profession, seasons and interests
  Step 2.1: To compute this, for every listing we gathered the user’s that have already stayed in it. We identified the age group they       belonged to, their profession, the seasons in which they travelled and their hobbies. Using min-max normalization technique we           computed the score for each of these parameters and fed it as training data for our neural network. 
  

