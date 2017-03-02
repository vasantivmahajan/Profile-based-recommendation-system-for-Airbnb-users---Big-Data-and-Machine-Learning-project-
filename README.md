# Profile-based-recommendation-system-for-Airbnb-users---Big-Data-and-Machine-Learning-project-

## Problem Statement
Airbnb is an online marketplace that enables users to list, find and rent vacation homes. Airbnb connects people to unique travel experiences, at any price point, in more than 34,000 cities and 191 countries. Airbnb has a diverse customer base, it is used by people from different age groups, professions and interests. Some customers prefer places which are closer to the city whereas some others love to enjoy the natural beauty by living in cottages. Since every customer has different interests it is essential that the user is recommended houses on the basis of their profile.

## Proposed System:
I along with my team, developed a profile based recommendation system using supervised learning techniques where user’s future trips are predicted on the basis of their past trips and preferences. User's age group, profession, interests and most frequently travelled seasons are taken into consideration for building the user's profile. The proposed system would build a good customer experience by reducing the average time of booking and better demand forecasting. 

## Approach:
 
Step 1: Data Cleaning and Feature Engineering:

Airbnb provides an open source dataset which contains 1.3 million listings that are posted on their website. It also has details regarding the Airbnb users and their past trips. The listings data contains information like number of bed rooms, amenities, ratings, house rules, GPS location, etc. The user's data contains information like age, profession, past trip details, etc. 

Data Cleaning: We handled missing values, garbage values, performed outlier detection and data normalization to clean the data. We used Alterxy tool for these operations.

Feature Engineering: Using the user’s travel history, we computed the seasons in which the user most frequently travels in. We identified the type of apartments the user stays in to identify user’s interests and preferences.

Kindly refer to the [Alteryx scripts](https://github.com/vasantivmahajan/Profile-based-recommendation-system-for-Airbnb-users---Big-Data-and-Machine-Learning-project-/tree/master/Alteryx%20scripts) used for Data Cleaning and Data Transformation.

Step 2: Calculating the score for every listing using Neural Network:

For every listing we computed the score to analyse how suitable a listing is on the basis of age-group, profession, seasons and interests:

  Step 2.1: To compute this, for every listing we gathered the user’s that have already stayed in it. We identified the age group they       belonged to, their profession, the seasons in which they travelled and their hobbies. Using min-max normalization technique we           computed the score for each of these parameters and fed it as training data for our neural network. 
  
  Step 2.2: We used a Multi-Layer Perceptron with backpropagation in Neuroph to predict the score for unseen data (listings not used for   training). Refer to the [link](https://github.com/vasantivmahajan/Profile-based-recommendation-system-for-Airbnb-users---Big-Data-and-Machine-Learning-project-/tree/master/Output%20files/All%20listings) for the output of the neural network for every parameter. 
  
This was performed for each of the parameters; age-group, profession, seasons and interests and we computed the score for every listing.

Step 3: Predicting user's future trips:
    
  Step 3.1: We used Train Matchbox Recommender module to train a recommendation model based on the Matchbox recommender engine and used   Score Matchbox Recommender to generate recommendations. We computed the triplets eg: userid, listingid and ageweights (age weights are   the weights that were computed by our neural network for every listing in Step 2. We chose age_weight of the age group to which the     user belongs to). Refer to the Train Matchbox Recommender module [here](https://msdn.microsoft.com/en-us/library/azure/dn905987.aspx). 
  
  Step 3.2: We trained the data and computed the top 25 recommendations for the user based on their age weights. Once we got the top 25   recommendations, we sorted these recommendations by their age weights and top 15 listings were chosen for the user.
  
  Step 3.3: Among those top 15 recommendations, we mapped the hobbies weight for every user and identifies the top 10 listings for the     user
  
  Step 3.4: Among these top 10 recommendations, we mapped the profession weight and identified the top 7 listings for the user. 
  
  Step 3.5: These 7 listings were then recommended to the user.
  
  Refer [here](https://github.com/vasantivmahajan/Profile-based-recommendation-system-for-Airbnb-users---Big-Data-and-Machine-Learning-project-/tree/master/Output%20files/Neural%20network) for the recommended listings for every user.
  
Thus we trained our model and created a web service of the model using R. 

Step 4: Creating a web application:

  Step 4.1: We build a live Spring MVC application where the 1.3 million listings and the user's data were stored in MongoDB. The           listings that were recommended to the user were fed into Mongo DB and were displayed in the application on Google Maps.

  Step 4.2: We created a web service of our model and consumed the web service in our Spring MVC application.
  
  Step 4.3: The latitude and longitude value for every recommended listing was fed to the marker object of google maps and they were    
  bound with a click event done using closures.

Refer to the Project Report for the detailed explanation.

  
  

