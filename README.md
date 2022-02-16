# Yield-Prediction-and-Variety-Recommendations


Improving the procedure for estimating the total amount of seed that needs to be produced can save a global seed company millions of dollars. By building a predictive model for the dry yield (how much useful product was harvested/extracted) of crops in Southern India, I was able to develop a procedure for forecasting the dried yield per acre of a farm. Recommending specific high yield varieties to locations within the region was another method that I used to improve the efficiency of the farms. The ideas behind this project can be applied to other crops and can be scaled to bigger regions.


Business Understanding
The value of the total seed produced in this region is about $60 million. So a variability of 1.5% in the projected production can result in a loss of about $1 million for a surplus, and $2.5 million for a deficit. Minimizing this uncertainty can be vital especially when scaling up to bigger regions.

The problem is to estimate the amount of seed that will be required for regions in Southern India and by building a predictive model for the dry yield per acre, the total seed production can be better estimated. Recommending specific high yield varieties for the different locations and also providing recommendations for each variety are also other ideas that can be incorporated into the solution.

Data Understanding
Crop Data
I received anonymized crop data from a major global seed company, which contains the yield for different varieties at different locations.

Weather and Location Data
The location data included in the dataset is not anonymized and was used to “scrape” or obtain weather data based on the date when the variety was sowed (Indian Meteorological Department, data.gov.in). I also gathered latitude, longitude and elevation for the different locations and tested these features.

Data Preparation
The Gross Yield was removed and the response was converted to Dried Yield Per Acre (Dried Yield / Standing Area).


The Sown and Harvest dates were combined to create the Days Till Harvest.

![image](https://user-images.githubusercontent.com/96236642/154263804-0fa5de4e-f650-4d3f-8d30-68a0c6794531.png)


![image](https://user-images.githubusercontent.com/96236642/154263833-7507c38d-2880-4643-b061-ff6d140b32bb.png)


The Sowing Month and Sowing Week were combined to create the Sowing Week of Year.

![image](https://user-images.githubusercontent.com/96236642/154263876-4ebaf97f-d0da-47d2-b5da-f75ae6419129.png)


![image](https://user-images.githubusercontent.com/96236642/154263974-5639c70a-c603-47c9-8bdc-900664540ba2.png)

The weather data was aggregated based on the first 3 months after the plant was sown. For regression the data was also transformed to degree 2 and 3 polynomials and those models were also compared. The predictors were also standardized and finally, the varieties were converted to dummy variables.

Modeling
Inference and Recommendations:

Regression for a better understanding of the coefficients and to recommend the varieties.
Matrix Factorization - Singular Value Decomposition (SVD): Matrix factorization was attempted to try to recommend varieties to particular locations for which data was not available. Using the dry yield as a "rating", varieties were recommended and compared to the regression recommendations. This was not entirely successful as domain knowledge along with other factors are very influential in this area. There are biological and agricultural reasons for specific varieties being planted at particular locations and this matrix factorization technique would struggle to incorporate that.


![image](https://user-images.githubusercontent.com/96236642/154264046-9bd3e387-1df1-4b3c-a2b5-c7737ee46ce8.png)


Prediction models:

Random Forest Regressor.
Gradient Boosted Regressor.
Evaluation
10-fold cross validation, polynomial models did not perform very well.


![image](https://user-images.githubusercontent.com/96236642/154264089-296367a2-8e94-4a25-b53e-0d6c5890e547.png)


If information can be obtained. The model could be validated with historical results in those areas too.

Deployment
Interface with map of India and the relevant states highlighted. The bubbles present on the states would display, when hovered over, the locations and the varieties that are recommended along with recommendations for the varieties.


![image](https://user-images.githubusercontent.com/96236642/154264141-194d0f94-3787-44e5-ac3d-505b1a3a686a.png)



![image](https://user-images.githubusercontent.com/96236642/154264176-51cc105e-c799-457a-a02f-e6bc892f8e99.png)



Further Work

Quantify recommendations for varieties: Currently the direction in which the factors affect yield is available. I would like to quantify these effects and hopefully give more precise recommendations.

Incorporate more weather variables: Temperature, humidity, hours of sunlight.
Incorporate soil data.

Gather location-based variety data for recommendations: If all the varieties can be tested at the different locations, then varieties for which there wasn't data before can be recommended to particular locations.

Attempt to use mixed models (treating some predictors as random variables).
