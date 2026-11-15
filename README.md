## Airline-Customer-Satisfaction-Analysis
Analysis of airline passenger satisfaction and service quality using Python, Pandas, and data visualization.

### Project Overview
This project analyzes airline passenger reviews and ratings to understand customer satisfaction and service quality. It compares overall passenger ratings and evaluates seven airline service categories to identify areas that may require improvement.

### Project Objectives

- Classify overall passenger ratings into satisfaction categories.
- Calculate and compare average ratings across seven service categories.
- Identify the three lowest-rated service areas.
- Compare ratings between passengers who recommend the airline and those who do not.
- Analyze satisfaction across airlines, traveller types, and seat types.
- Conduct a detailed analysis of Hainan Airlines, the highest-rated airline, by comparing overall ratings based on trip verification and
  recommendation status.
- Analyse the relationship between different service quality factors using correlation analysis.
- Compare average overall ratings across different traveller types and seat types to understand variations in customer experience.
- Analyse customer satisfaction across Indian airlines based on traveller types and seat categories.
- Compare service quality ratings between highly satisfied and poorly satisfied passengers across Indian airlines to identify areas
  requiring improvement.

### Dataset Source

**Source:** Mendeley Data – Airline Travel Reviews Data (Skytrax)

**Dataset Link:** https://data.mendeley.com/datasets/vgjk58vf8h/1

**Rows and Columns:** Dataset contains 64,740 rows and 19 columns before data cleaning.

### Tools and Technologies

- Python
- Jupyter Notebook
- Pandas
- Matplotlib
- Seaborn
- Plotly

### Repository Contents

- Airline_Customer_Satisfaction_Analysis_SRS.pdf – Software Requirements Specification
- Airline_Customer_Satisfaction_Analysis_Phase1.ipynb – Phase 1 analysis notebook
- Airline_Customer_Satisfaction_Analysis_Phase2.ipynb – Phase 2 analysis notebook
- Airline_Customer_Satisfaction_Analysis_Phase2.ipynb – Phase 3 analysis notebook
- data/ – Dataset folder

### How to Run the Notebook

1. Download or clone this repository.
2. Install Python, Jupyter Notebook, and the required libraries.
3. Open the notebook in Jupyter Notebook.
4. Ensure the dataset is available in the data/ folder.
5. Run the notebook cells from top to bottom.

### Project Planning and SRS

- Identified and selected a suitable Skytrax airline review dataset based on the project requirements and given conditions.
- Defined the project scope, objectives, and requirements for the Airline Customer Satisfaction & Service Quality Analysis project.
- Prepared the Software Requirements Specification (SRS) document and selected the Skytrax airline review dataset for analysis.

### Data Cleaning and Preprocessing

- Imported and inspected the dataset, identified and handled missing values, removed duplicate records, standardized categorical            values,converted date columns into datetime format, and validated rating ranges. Created two new features: satisfaction_level and         average_service_rating, to support further analysis.

#### 1. Creating a Copy of the Dataset
     
- Created a copy of the original dataset to preserve the raw data. This allows cleaning operations to be performed without changing the     original dataset.
  
#### 2. Checking Missing Values
   
- Checked missing values in each column to identify incomplete data and decide how to handle them.
  
#### 3. Checking and Removing Duplicate Records
   
- Identified 64 duplicate records and removed them while keeping the first occurrence to avoid repeated entries affecting the analysis.
- Checked again to confirm that no duplicate records remained.
 
#### 4. Converting Date Columns
   
- Converted review_date and date_flown from text into datetime format to make them suitable for date-based operations and analysis.
- Assigned the first day of the month as a placeholder for date_flown because the exact travel date was unavailable.
  
#### 5.Handling Missing Values in Numerical Rating Columns
 
- Identified missing values in the over_all_rating column and the seven service-rating columns.
- Retained the missing values without replacement because they represent unavailable passenger feedback.
- Avoided replacing missing ratings with assumed values, as this could affect the accuracy of the analysis.
- Pandas automatically excludes missing values from statistical calculations where applicable.
- The available ratings will be used for further analysis, and the number of valid responses will be considered while interpreting the      results.
- The wifi__connectivity column was removed because it contained a high proportion of missing values (approximately 63.5%).
- This helps keep the service quality analysis focused on categories with more available responses.
  
#### 7. Validating Rating Values
   
- Checked whether overall ratings were within the 1–10 range and service ratings were within the 1–5 range to identify invalid values.
  
#### 8. Handling Missing Values in Categorical Columns

##### 1. Checking Missing Values
   
- Checked missing values in the categorical columns to understand the amount of missing data and decide suitable handling methods.
  
##### 2. Mode Imputation

- Replaced missing values in the seat_type,type_of_traveller, route and recommended columns, with the mode (most frequently occurring
  category).
- These columns had a manageable proportion of missing values compared with the total number of records. 
- This helped retain records while maintaining consistency in the categorical data.
   
##### 3. Removing the aircraft Column
   
- Removed the aircraft column because it contained a high proportion of missing values (approximately 56.7%) and was not required for the   project's analysis objectives.I decided to drop this column rather than use incomplete information.
  
##### 4. Handling Missing Values in Remaining Categorical Columns Using Unknown
   
- Replaced missing values in the remaining categorical columns with Unknown to preserve records without making assumptions about the        missing information.
- This also helps distinguish unavailable information from existing categories.
  
##### 5. Handling Missing Values in Date Columns

- Checked missing values in the date_flown column.
- Retained missing values without replacement because the actual travel month and year were unavailable.
- Avoided filling missing dates with assumed values to maintain the accuracy of date-based analysis.

#### 9.Standardising Categorical Columns

##### 1. Checking Categorical Value Counts
   
- Examined the value counts of each categorical column to understand the category distribution and identify inconsistent labels.
  
##### 2. Standardising the trip_verified Column
   
- Identified inconsistent labels in the trip_verified column and standardised them into three categories: Verified, Not Verified, and
  Unknown.
- This helps maintain uniformity and avoids treating similar labels as separate categories.
  
##### 3. Removing Unwanted Spaces
   
- Removed leading and trailing spaces from all categorical columns to maintain consistent category values and avoid unwanted variations.
  
##### 4. Cleaning Text Columns (review_header and review_text)

- Converted the review_header column to title case to maintain consistent text formatting.
- Converted the review_text column to lowercase for uniformity.
- Removed commas from both columns to eliminate unnecessary punctuation.

##### 5. Standardising route column values

- Identified unwanted commas in a few route values and removed them to maintain consistent formatting across the route column.

##### 6. Rechecking Categorical Value Counts
   
- Examined the value counts again after standardisation and space removal to verify consistency in the categorical data.

#### 10. Dataset Overview and Exploration

- Examined the dataset using head(), columns, shape, info() and describe() to understand its structure, column names, dimensions, data
  types, non-null values and statistical summary.
- Checked the dataset shape after removing unnecessary columns to verify the updated number of rows and columns before proceeding with
   further analysis.

#### 11. Feature Engineering

- Created two new columns from the existing dataset to support further analysis and provide better insights into passenger satisfaction
  and service quality.

##### 1. Creating the satisfaction_level Column
   
- Created a new column named satisfaction_level using the over_all_rating column.
- Categorised passenger ratings into three groups: Poor, Medium and Positive.
- Assigned Unknown to records with missing overall ratings.
- This feature helps analyse passenger satisfaction levels and calculate the percentage of ratings in each category.
  
##### 2. Creating the average_service_rating Column
   
- Created a new column named average_service_rating by calculating the row-wise average of the six service-rating columns.
- This feature provides an overall measure of passenger experience across different service aspects.
- Missing ratings were excluded from the average calculation.
- Rows with all six service ratings missing retained a missing value.
  
### Final Dataset Overview

- Verified the final dataset after completing data cleaning, preprocessing and feature engineering.
- The final dataset contains 64,676 rows and 19 columns.
- The cleaned and structured dataset is now ready for Exploratory Data Analysis (EDA).

### Exploratory Data Analysis and Insights

**1. Introduction**
   
Exploratory Data Analysis (EDA) was performed to understand customer satisfaction patterns, evaluate airline performance and identify service quality factors influencing passenger experience.

The analysis was conducted using Python libraries such as Pandas, Matplotlib, Seaborn and Plotly. Univariate, bivariate and multivariate techniques were used to explore individual variables and relationships between different variables.

**2. Objectives of EDA**
   
- Understand the distribution of overall customer ratings and satisfaction levels.
- Identify the lowest-rated service categories.
- Compare customer ratings based on recommendation status.
- Evaluate global airline performance and identify the highest- and lowest-rated airlines.
- Investigate the performance of Hainan Airlines through detailed analysis.
- Understand relationships between service quality factors.
- Compare ratings across traveller types and seat categories.
- Evaluate customer satisfaction and service quality among Indian airlines.
- Identify areas where airlines can improve customer experience.
  
**3. EDA Methodology**
   
#### 3.1 Univariate Analysis
     Univariate analysis was performed to understand individual variables and their distributions.

##### Analyses performed:
- Examined numerical variables using descriptive statistics, including mean, median, standard deviation, minimum and maximum values.
- Examined categorical variables using frequency counts and percentage distributions.
- Analysed the distribution of overall customer ratings using histograms and count plots.
- Examined customer satisfaction distribution across Poor, Medium and High categories.
- Analysed available ratings across the six service categories.
- Examined distributions of traveller types, seat types, trip verification and recommendation status.
  
#### 3.2 Bivariate Analysis
     Bivariate analysis was performed to understand relationships between two variables.

##### Analyses performed:
- Compared average overall ratings between customers who recommended the airline and those who did not.
- Compared average overall ratings across global airlines, considering airlines with at least 100 reviews.
- Analysed the relationship between seat type and customer satisfaction level using Seaborn visualisations.
- Compared average overall ratings across traveller types and seat types.
  
#### 3.3 Multivariate Analysis
     Multivariate analysis was performed to examine relationships among three or more variables.

##### Analyses performed:
- Examined correlations among the six service quality factors using a correlation matrix and heatmap.
- Analysed customer ratings based on traveller type and seat category.
- Compared customer satisfaction across Indian airlines, traveller types and seat categories.
- Compared service quality ratings between highly satisfied and poorly satisfied passengers across Indian airlines.
- Conducted detailed Hainan Airlines analysis by comparing overall ratings based on trip verification and recommendation status.
  
**4. Important Findings and Key Insights**
   
#### 4.1 Overall Customer Rating Distribution

##### Findings:
- Average overall rating: 4.34 out of 10.
- Median rating: 3.
- Most frequently given rating:1.
  
##### Key Insight:

The concentration of low ratings indicates that a considerable proportion of passengers reported unsatisfactory airline experiences.

#### 4.2 Customer Satisfaction Distribution

##### Findings:

- Satisfaction level	Percentage
Poor	47.65%
High	41.65%
Medium	10.70%

##### Key Insight:

- Poor satisfaction was more common than high satisfaction, indicating a need for improvements in overall passenger experience.

#### 4.3 Global Airline Performance Comparison

##### Findings:

- Highest-rated airline: Hainan Airlines – 8.49.
- China Southern Airlines – 7.99.
- Garuda Indonesia – 7.95.
- Lowest-rated airline: Silver Airways – 1.82.
- GoAir – 1.92.
Only airlines with at least 100 reviews were considered.

##### Key Insight:

Hainan Airlines emerged as the highest-rated airline in the comparison. It was selected for further detailed analysis to understand its customer ratings and recommendation patterns.

#### 4.4 Global Service Ratings: High vs Poor Satisfaction

##### Findings:

- Highly satisfied passengers gave higher ratings across all six service categories.
- Cabin staff service received the highest rating among highly satisfied passengers.
- Value for money showed the largest difference between the two satisfaction groups.
- Ground service and value for money received comparatively low ratings among poorly satisfied passengers.
  
##### Key Insight:

- Better service ratings were associated with higher customer satisfaction. Value for money and ground service were important areas for
  improvement.

#### 4.5 Detailed Hainan Airlines Analysis

##### Findings:

- Trip verification	Recommendation	Reviews	Average rating
Verified	Yes	269	9.22
Verified	No	39	3.62
Not Verified	Yes	5	9.00
Unknown	Yes	23	8.65
Unknown	No	3	4.67

##### Key Insight:

- Verified customers who recommended Hainan Airlines gave the highest average rating of 9.22. In contrast, verified customers who did not  recommend the airline gave an average rating of 3.62. This highlights a strong association between recommendation behaviour and overall
 customer ratings.

#### 4.6 Global Service Quality Analysis

##### Findings:

Cabin staff service	3.07
Seat comfort	2.84
Inflight entertainment	2.83
Food and beverages	2.80
Value for money	2.61
Ground service	2.58
- Cabin staff service received the highest average rating.
- Ground service received the lowest average rating.
  
##### Key Insight:

Cabin staff service performed relatively better, whereas ground service was the weakest service area. Ground service requires greater attention to improve passenger experience.

#### 4.7 Traveller Type and Seat Type Analysis

##### Findings:

- Highest average rating: Solo Leisure passengers in Business Class – 6.79.
- Lowest average rating: Couple Leisure passengers in Economy Class – 3.53.
- Economy Class accounted for the highest number of reviews.
  
##### Key Insight:

Customer ratings varied according to traveller type and seat category. Business Class generally received higher ratings across the traveller groups shown in the analysis.

#### 4.8 Correlation Between Service Ratings

##### Findings:

- All six service factors showed positive correlations.
- Strongest correlation: Ground service and value for money – 0.80.
- Weakest correlation: Inflight entertainment and ground service – 0.60.
  
##### Key Insight:

Customers who rated one service factor highly tended to give higher ratings to other service factors as well. Ground service and value for money showed the strongest relationship.

#### 4.9 Indian Airline Customer Satisfaction

##### Findings:

- Vistara appeared frequently among the combinations with higher satisfaction percentages.
- Solo Leisure passengers travelling in Vistara Premium Economy recorded the highest displayed satisfaction percentage of 81.82%.
- Satisfaction varied across airlines, traveller types and seat categories.
  
##### Key Insight:

Customer satisfaction differed across Indian airlines and passenger categories. Vistara showed strong satisfaction in several combinations, particularly among Solo Leisure passengers in Premium Economy.

#### 4.10 Indian Airline Service Quality Analysis

##### Findings:

Service category	High satisfaction	Poor satisfaction
Value for money	4.38	1.24
Cabin staff service	4.28	1.76
Ground service		
Inflight entertainment		

The remaining service-category values can be added from your final comparison output.
- Value for money showed the largest difference between the two satisfaction groups.
- Ground service and cabin staff service also showed considerable differences.
- Inflight entertainment remained a comparatively weaker-rated factor even among highly satisfied passengers.
  
##### Key Insight:

Value for money was the strongest differentiating factor between highly satisfied and poorly satisfied passengers. Improving value for money and other weaker service areas may help airlines improve customer satisfaction.

**5. Challenges Faced During Analysis**

The following challenges were encountered while analysing the airline review dataset:

1. Missing Values: Several columns contained missing values. Aircraft and Wi-Fi connectivity had a high percentage of missing values, making them unsuitable for further analysis.
2. Duplicate Records: Duplicate records were identified and removed to maintain data accuracy.
3. Inconsistent Data: Some categorical values and date formats required standardisation before analysis.
4. Different Rating Scales: Overall ratings were recorded on a 1–10 scale, whereas service quality ratings used a 1–5 scale. These differences were considered during comparisons.
5. Data Distribution: Customer reviews were not evenly distributed across airlines, traveller types and seat categories, making some comparisons less representative than others.
6. Visualisation Challenges: Some charts contained too many categories or overlapping data points. Appropriate chart types, filtering and formatting were used to improve readability.
   
**6. Suggestions and Recommendations**
   
Based on the analysis, the following recommendations can help airlines improve customer experience:
- Improve Ground Services: Focus on check-in procedures, airport assistance and other ground service experiences.
- Improve Value for Money: Review ticket pricing and ensure that the services provided match customer expectations.
- Enhance Inflight Entertainment: Improve entertainment options to provide a better onboard experience.
- Maintain Cabin Staff Performance: Continue strengthening cabin staff service, which received the highest average rating globally.
- Investigate Customer Complaints: Examine feedback from customers who gave low ratings and did not recommend the airline.
- Focus on Passenger Segments: Consider the different expectations of passengers based on traveller type and seat category.
- Monitor Customer Satisfaction: Regularly analyse customer feedback to identify service weaknesses and track improvements.
  
**7. Project Outcomes**

Through this analysis, the following outcomes were achieved:

- Identified overall customer rating and satisfaction patterns across airline reviews.
- Evaluated airline performance and identified the highest- and lowest-rated airlines.
- Identified Hainan Airlines as the highest-rated airline and conducted further detailed analysis.
- Compared service quality ratings between highly satisfied and poorly satisfied passengers.
- Examined relationships among six service quality ratings using correlation analysis.
- Identified variations in customer ratings across traveller types and seat categories.
- Evaluated customer satisfaction and service quality patterns among Indian airlines.
- Identified important service areas that require improvement to enhance passenger satisfaction.

**Areas for Improvement**

**Value for Money:** Improve the balance between ticket prices and the quality of services provided.
**Ground Service:** Improve airport assistance, check-in support, boarding services and passenger handling.
**Inflight Entertainment:** Improve entertainment options and system quality.
**Food and Beverages:** Focus on food quality, variety and passenger preferences.
**Seat Comfort:** Improve seating comfort and passenger convenience.
**Cabin Staff Service:** Maintain good staff behaviour, communication and passenger support.

**8. Conclusion**
   
- This project provided a detailed analysis of airline customer satisfaction and service quality using customer review data. Through univariate, bivariate and multivariate analysis, different patterns in customer ratings, satisfaction levels, airline performance and service quality were identified.

- The analysis highlighted Hainan Airlines as the highest-rated airline in the global comparison and identified ground service and value for money as important areas requiring improvement. It also revealed differences in customer experiences across traveller types, seat categories and Indian airlines.

- Overall, the project demonstrates how data analysis can help understand customer feedback, identify service weaknesses and support data-driven decisions to improve airline service quality and passenger satisfaction. Airlines can use these findings to identify weak service areas, improve passenger experience and make better data-driven decisions.




