<img src="./images/house.jpg" alt="house" width="300"/>

# Overview
A client wants to purchase a home in Westchester county and wants to ensure their home is a good investment. They measure that by ROI they will get in 5 years. Their budget is $500K. Our firm is asked to recommend 5 zipcodes in Westchester county that would be good options.

# Business Understanding
* Objective: Identify five ZIP codes in Westchester County where a client can purchase a home within a $500,000 budget, aiming for optimal Return on Investment (ROI) over a 5-year period.
* Stakeholder: A prospective homebuyer seeking a property in Westchester County that not only fits within their financial constraints but also promises substantial appreciation.
* Problem: Determining which ZIP codes in Westchester County offer homes priced at or below $500,000 and are projected to yield the highest ROI over a 5-year span.

Key Questions
1. Which ZIP codes in Westchester County have homes available within the $500,000 budget?
2. What are the historical and projected real estate trends in these ZIP codes?
3. Which of these areas are anticipated to provide the highest ROI over the next 10 years?

Success Metric: ROI (Return on Investment) over a 5-year period.

Model Evaluation Metric: AIC

# Data Understanding
The data set we are usuing is from [Zillow](https://www.zillow.com/research/data/) and contains historical home prices across the US from 1996 to 2018.
The columns are:
* RegionID
* RegionName
* City
* State Metro
* CountyName
* SizeRank
* Dates and their median home prices

1. Data Sources and Suitability
* Data Source: The dataset contains historical home prices from 1996 to 2018 for various zip codes in Westchester County. It includes monthly price data, along with location identifiers such as zip codes, city, and county names. Suitability: This data is well-suited for the project because it offers a long historical time series, allowing for the identification of trends and seasonality—essential for reliable real estate price forecasting. The zip code granularity also aligns with the project's goal of pinpointing the top 5 zip codes for home investment.
* Dataset Size: The dataset contains 14,723 rows and 272 columns.
2. Feature Justification
* RegionName (Zip Code): Used to segment price data by location—crucial for identifying high-ROI zip codes.
* City, State, County: Provides geographic context.
* Monthly Price Columns: These serve as the core time series data for price forecasting.
* Metro: Helpful for capturing broader economic trends that might influence local price changes.
3. Data Limitations
* Single Data Source: The data comes solely from Zillow, which introduces a risk of bias. Zillow may adjust or estimate home prices in ways that align with their business goals, potentially affecting the objectivity of the data.
* Timeframe: Data stops at 2018—limiting how recent trends (like post-2020 shifts) impact price predictions.
* Inflation Adjustments: Prices are nominal; without inflation adjustments, real ROI might be skewed.

## Data Preparation
* Filter for Home Prices under $500K
* Check for Null values
* Rename "RegionName" to "Zipcode"
* Filter out data before 2009
* Melt data frame to transform from long to wide format

# Exploratory Data Analysis
We used AutoArima to forecast home prices for the next 5 years for the zipcodes in Westchester within our client's budget.

![Price Forecasts](./images/price_forecasts.png)

# Conclusion
![Top ROIs](./images/top_5_roi.png)

The top zipcodes by expected ROI over 5 years are:
10701 - Yonkers
10704 - Yonkers
10598 - Yorktown
10705 - Yonkers
10703 - Yonkers

## Limitations
This SARIMAX model has a few limitations. 
* The data only goes up to 2018, missing recent market trends. 
* The model assumes linear relationships and normally distributed residuals, though slight non-normality and outliers were observed. It also excludes external factors like interest rates and economic indicators, which could improve accuracy. Auto-ARIMA’s reliance on AIC for model selection may lead to overfitting or underfitting. 
* Lastly, the $500K budget filter doesn’t account for additional costs like property taxes or renovations, which affect ROI.

## Recommendations
Based on the time series analysis and SARIMA modeling, we identified ZIP codes in Westchester County with homes priced at or below $500K and projected their home prices over the next 5 years. By calculating the expected ROI for each ZIP code, we can now highlight the top 5 areas that present the most promising investment opportunities for our client.

## Next Steps
Enhance the Forecasting Model:
* Add exogenous variables (like interest rates, employment rates, and population growth) to further refine the forecast.
* Create model using Facebook’s Prophet and use it for comparison
 
# Links
More details on the analysis can be found [here].(https://github.com/hannahdallas/zillow_time_series_model/blob/main/notebook.ipynb)

The presentation can be found [here](https://docs.google.com/presentation/d/1UnwhOtG6VXyiT7JYCG60OG-SGA8XWjSGLtsaN6632Xw/edit#slide=id.p6)

├── zillow_data.csv   
├── images/              
├── README.md           
├── presentation.pdf      
└── notebook.ipynb  
