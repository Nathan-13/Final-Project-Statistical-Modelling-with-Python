# Final-Project-Statistical-Modelling-with-Python

## Project/Goals

This project aims to thoroughly examine the positioning and correlation between bike-share stations and points of interest within the city of Hamilton, Ontario, Canada. To achieve this goal, we obtain data from multiple sources:
* Data about bike-share stations is retrieved from the Citybikes API.
* Information regarding points of interest is collected through APIs provided by Yelp and Foursquare (FSQ).

At the end of this exercise, the result of this project should provide insights into the spatial relationships between these elements through a systematic analysis, contributing to a better understanding of urban dynamics in Hamilton, ON, Canada.

## Process
### 1. Accessing Data Using APIs:
The project begins by accessing data from various Application Programming Interfaces (APIs). Specifically:
* Source bike-share station data from the Citybikes API. This entails extracting pertinent information such as station latitude, longitude, and the number of available bikes. Subsequently, we structure these parsed details into a data frame.
* Utilize the Foursquare API to gather data concerning bike stations within Hamilton. In this process, we send requests for all Hamilton-based bike stations with a search radius restricted to 1000 meters. Additionally, we limit the results to a maximum of 20 items for each station. Following the reception of the API response, we extract Points of Interest (POI) data and transform it into a data frame.
* Likewise, for the Yelp API, we initiate requests to obtain information regarding bike stations located within Hamilton. We employ a search radius of 1000 meters and set a limit of 20 results for each station. Once we acquire the API response, we extract the relevant POI details, converting them into a data frame.

These steps outline the data acquisition process, encompassing the extraction and organization of bike station and POI data from multiple APIs to facilitate comprehensive analysis.

### 2. Cleaning and Transforming Data Using Python:
Following data acquisition, a rigorous cleaning and transformation process ensures data integrity. This process encompasses rectifying inconsistencies, handling missing values, and standardizing data formats. Notably, this procedure is applied to both the Yelp and Foursquare datasets. The outcomes of this transformation are subsequently compared, and the assessment encompasses the following aspects:
* Number of Points of Interest (POIs): A comparison is made regarding the quantity of POIs returned by each API for the city of Hamilton. A higher count of POIs may signify a more extensive and diverse range of available places within the area.
* Depth of Information: The completeness of information provided for each POI is evaluated. This includes essential details such as names, addresses, categories, ratings, and user-generated content such as reviews and photos. A comprehensive dataset for each POI can serve as an indicator of data quality.
* User Reviews: An analysis is conducted to assess the volume and quality of user reviews for each POI. A more significant number of studies and higher ratings suggest that one API boasts a more engaged user base and superior coverage in terms of user-generated content.

By systematically evaluating these factors, the project aims to discern differences and similarities between the Yelp and Foursquare datasets, providing valuable insights into the reliability and richness of the data obtained from each source.

### 3. Performing Exploratory Data Analysis (EDA):
The results obtained in the previous stage are merged into two distinct DataFrames: one combining bike station data with Foursquare results and the other merging bike station data with Yelp results. These new data frames are subjected to statistical techniques and data visualizations to unveil valuable insights, detect underlying patterns, and identify emerging trends. This in-depth analysis is instrumental in thoroughly comprehending the dataset's characteristics.
The project undertakes a comparative assessment of the quality of results obtained from the Yelp and Foursquare APIs concerning Hamilton bike stations. This evaluation focuses on the completeness of information and the extent of coverage each API provides.
Conclusively, the findings derived from the CityBikes API and the merged DataFrames are systematically loaded into an SQLite3 database. The dataset is meticulously explored before and after the merging process to validate its integrity and structure, ensuring the reliability and coherence of the data for subsequent analyses.

### 4. Model Building
This project entails the development of a regression model that elucidates the correlation between the number of bikes within a specific area and the attributes of Points of Interest (POIs) located therein. The linear regression model's primary objective is to forecast the 'number_of_bikes' using the predictor variables 'poi_ratings,' 'poi_review_count,' and 'poi_distance.'

## Results
(fill in what you found about the comparative quality of API coverage in your chosen area and the results of your model.)
### Quality of API coverage
The Yelp result has no NaN values in 'categories', 'ratings', and 'review_count'. This indicates that all these columns have complete data with no missing values. While there are missing values in 'categories', 'ratings', 'total_ratings', 'total_tips', and 'total_photos' of the Foursquare result. These missing values in 'categories' suggest that there are some POIs without assigned categories in the dataset. Additionally, 'ratings', 'total_ratings', 'total_tips', and 'total_photos' columns have a significant number of missing values, indicating potential data incompleteness or issues. Overall, the Yelp API reuslt has a cleaner dataset with fewer missing values compared to the Foursquare API result, where several columns have a notable number of missing values.

### Regression Model Results
The linear regression model aims to predict the 'number_of_bikes' using the predictor variables 'poi_ratings,' 'poi_review_count,' and 'poi_distance.' Here's an interpretation of the results:
* The R-squared value, which stands at 0.020, indicates that the model can explain only 2.0% of the variance in the 'number_of_bikes' variable. This low R-squared value suggests that the model does not fit the data well, and most of the variability in 'number_of_bikes' remains unexplained by the chosen predictor variables.
* The Adjusted R-squared, closely resembling the R-squared value at 0.019, considers the number of predictor variables in the model. The similarity between the R-squared and Adjusted R-squared values suggests that introducing additional predictor variables may not significantly enhance the model's performance.
* const: The 'const' coefficient corresponds to the intercept of the regression equation. In this context, it has an approximate value of 12.4142. This implies that when all other predictor variables are set to zero, the predicted 'number_of_bikes' is approximately 12.4142.
* poi_ratings: The coefficient associated with 'poi_ratings' is -0.3612. This indicates that for each unit increase in the 'poi_ratings' variable, the estimated 'number_of_bikes' decreases by approximately 0.3612 units, assuming all other predictor variables remain constant.
* poi_review_count: The coefficient for 'poi_review_count' is -0.0091. This signifies that for each additional review included in the 'poi_review_count,' the predicted 'number_of_bikes' decreases by approximately 0.0091 units, holding all other predictor variables constant.
* poi_distance: The 'poi_distance' coefficient is 0.0021. This means that for every unit increment in the 'poi_distance' variable, the estimated 'number_of_bikes' increases by approximately 0.0021 units, assuming that all other predictor variables remain unchanged.

Overall, the model could better explain the variance in 'number_of_bikes.' The low R-squared value and non-normality in residuals suggest that there may be better fits for this data than the linear regression model.

## Challenges 
The challenges faced in this project include:
* The Yelp API has rate limits on the number of requests that can be made within a specific time frame. Ensuring efficient data retrieval within these limits while collecting comprehensive data can be challenging.
* Developing a regression model to predict 'number_of_bikes' based on POI attributes requires careful model selection and interpretation. Understanding the significance and limitations of the model's results is crucial for drawing meaningful conclusions.

## Future Goals
In an ideal scenario, I preferred incorporating a broader range of queries and categories for organizing and analyzing this dataset. With a more extensive and more diverse dataset, I could have developed a more robust and effective model. This might have enabled me to derive concrete answers to my initial questions and comprehensively understand the subject matter.