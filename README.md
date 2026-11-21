# Airline-Customer-Satisfaction-Analysis
Analysis of airline passenger satisfaction and service quality using Python, Pandas, and data visualization.

## Project Overview
This project analyzes airline passenger reviews and ratings to understand customer satisfaction and service quality. It compares overall passenger ratings and evaluates six airline service categories to identify areas that may require improvement.

## Project Objectives

- Classify overall passenger ratings into satisfaction categories.
- Calculate and compare average ratings across six service categories.
- Identify the three lowest-rated service areas.
- Compare ratings between passengers who recommend the airline and those who do not.
- Analyze satisfaction across airlines, traveller types, and seat types.
- Compared service quality ratings between highly satisfied and poorly satisfied passengers across global airlines to identify
  differences in service performance and areas requiring improvement.
- Conduct a detailed analysis of Hainan Airlines, the highest-rated airline, by comparing overall ratings based on trip verification and
  recommendation status.
- Analyse the relationship between different service quality factors using correlation analysis.
- Compare average overall ratings across different traveller types and seat types to understand variations in customer experience.
- Analyse customer satisfaction across Indian airlines based on traveller types and seat categories.
- Compare service quality ratings between highly satisfied and poorly satisfied passengers across Indian airlines to identify areas
  requiring improvement.

## Dataset Source

**Source:** Mendeley Data – Airline Travel Reviews Data (Skytrax)

**Dataset Link:** https://data.mendeley.com/datasets/vgjk58vf8h/1

**Rows and Columns:** Dataset contains 64,740 rows and 19 columns before data cleaning.

## Tools and Technologies

| Tool / Library | Purpose |
|---|---|
| Python | Programming language used for data analysis. |
| Jupyter Notebook | Environment used to write and run the analysis notebooks. |
| Pandas | Used for data loading, cleaning, manipulation, and analysis. |
| Matplotlib | Used to create data visualisations and charts. |
| Seaborn | Used to create statistical visualisations. |
| Plotly | Used to create interactive visualisations. |

## Repository Contents

- Airline_Customer_Satisfaction_Analysis_SRS.pdf – Software Requirements Specification
- Airline_Customer_Satisfaction_Analysis-Notebook
- Airline_Customer_Satisfaction_Analysis- Project Report Documentation
- Data/ – Dataset folder: Created to organise and store the project dataset. Since the original dataset exceeded GitHub's file size
  limitations, it was added to the repository using Git. Additionally, a compressed ZIP file of the dataset was kept in the repository
  for convenience.

  
## How to Run the Notebook

1. Download or clone this repository.
2. Install Python, Jupyter Notebook, and the required libraries.
3. Open the notebook in Jupyter Notebook.
4. Ensure the dataset is available in the data/ folder.
5. Run the notebook cells from top to bottom.

## Phase 1: Project Planning and Initial Dataset Exploration

- Identified and selected a suitable Skytrax airline review dataset based on the project requirements.
- Defined the project scope, objectives and requirements for the Airline Customer Satisfaction & Service Quality Analysis project.
- Imported the required Python libraries, including Pandas, NumPy, Matplotlib and Seaborn.
- Loaded the airline review dataset into a Pandas DataFrame.
- Performed initial dataset inspection using head(), tail(), shape, columns, info() and dtypes.
- Examined the first and last records to understand the dataset contents.
- Checked the dataset dimensions, column names, data types and non-null information to understand its structure before proceeding with
  data cleaning and preprocessing.

## Phase 2: Data Cleaning and Preprocessing

- Imported and inspected the dataset, identified and handled missing values, removed duplicate records, standardized categorical            values,converted date columns into datetime format, and validated rating ranges. Created two new features: satisfaction_level and         average_service_rating, to support further analysis.

### 1. Creating a Copy of the Dataset
     
- Created a copy of the original dataset to preserve the raw data. This allows cleaning operations to be performed without changing the     original dataset.
  
### 2. Checking and Removing Duplicate Records
   
- Identified 64 duplicate records and removed them while keeping the first occurrence to avoid repeated entries affecting the analysis.
- Checked again to confirm that no duplicate records remained.

### 3. Initial Data Type Check:
- Before starting the data cleaning process,I checked the data types of all 19 columns using the Pandas dtypes attribute.

Observations:
- The dataset contained 19 columns.
- over_all_rating and the six service rating columns were in float64 format.
- The remaining 11 columns were stored as string (str) data types.
- The date columns review_date and date_flown were stored as strings instead of datetime format.
- Converted review_date and date_flown from text into datetime format to make them suitable for date-based operations and analysis.
- Assigned the first day of the month as a placeholder for date_flown because the exact travel date was unavailable.
  
### 4. Checking Missing Values
   
- Checked missing values in each column to identify incomplete data and decide how to handle them.
- Missing values were identified in both numerical and categorical columns.
- The wifi__connectivity column had the highest number of missing values (41,118), followed by aircraft (36,767) and
  inflight_entertainment (21,162).
- Other columns contained varying numbers of missing values, which were reviewed to decide the appropriate missing-value treatment.
- This step helped identify columns requiring missing-value handling and supported decisions about retaining or dropping columns during
  data cleaning.
  
### 4.1 Handling Missing Values in Numerical Rating Columns
 
- Identified missing values in the over_all_rating column and the seven service-rating columns.
- Retained the missing values without replacement because they represent unavailable passenger feedback.
- Avoided replacing missing ratings with assumed values, as this could affect the accuracy of the analysis.
- Pandas automatically excludes missing values from statistical calculations where applicable.
- The available ratings will be used for further analysis, and the number of valid responses will be considered while interpreting the      results.
- The wifi__connectivity column was removed because it contained a high proportion of missing values (approximately 63.5%).
- This helps keep the service quality analysis focused on categories with more available responses.
  
### 4.2 Handling Missing Values in Categorical Columns

#### 1. Checking Missing Values
   
- Checked missing values in the categorical columns to understand the amount of missing data and decide suitable handling methods.
  
#### 2. Mode Imputation

- Replaced missing values in the seat_type,type_of_traveller, route and recommended columns, with the mode (most frequently occurring
  category).
- These columns had a manageable proportion of missing values compared with the total number of records. 
- This helped retain records while maintaining consistency in the categorical data.
   
#### 3. Removing the aircraft Column
   
- Removed the aircraft column because it contained a high proportion of missing values (approximately 56.7%) and was not required for the   project's analysis objectives.I decided to drop this column rather than use incomplete information.
  
#### 4. Handling Missing Values in Remaining Categorical Columns Using Unknown
   
- Replaced missing values in the remaining categorical columns with Unknown to preserve records without making assumptions about the        missing information.
- This also helps distinguish unavailable information from existing categories.
  
### 5. Handling Missing Values in Date Columns

- Checked missing values in the date_flown column.
- Retained missing values without replacement because the actual travel month and year were unavailable.
- Avoided filling missing dates with assumed values to maintain the accuracy of date-based analysis.

### 6. Validating Rating Values
   
- Checked whether overall ratings were within the 1–10 range and service ratings were within the 1–5 range to identify invalid values.

### 7. Standardising Categorical Columns

#### 7.1 Checking Categorical Value Counts
   
- Examined the value counts of each categorical column to understand the category distribution and identify inconsistent labels.
  
#### 7.2 Standardising the trip_verified Column
   
- Identified inconsistent labels in the trip_verified column and standardised them into three categories: Verified, Not Verified, and
  Unknown.
- This helps maintain uniformity and avoids treating similar labels as separate categories.
  
#### 7.3 Removing Unwanted Spaces
   
- Removed leading and trailing spaces from all categorical columns to maintain consistent category values and avoid unwanted variations.
  
#### 7.4 Cleaning Text Columns (review_header and review_text)

- Converted the review_header column to title case to maintain consistent text formatting.
- Converted the review_text column to lowercase for uniformity.
- Removed commas from both columns to eliminate unnecessary punctuation.

#### 7.5 Standardising route column values

- Identified and corrected inconsistent formatting in the route column.
- Replaced the invalid character combination ,_ with _ to maintain a consistent route format.
- Removed the unwanted opening curly bracket { from route values.
- These corrections helped standardise route names and improve consistency for further analysis.

#### 7.6 Rechecking Categorical Value Counts
   
- Examined the value counts again after standardisation and space removal to verify consistency in the categorical data.

### 8. Dataset Overview and Exploration

- Examined the dataset using head(), columns, shape, info() and describe() to understand its structure, column names, dimensions, data
  types, non-null values and statistical summary.
- Checked the dataset shape after removing unnecessary columns to verify the updated number of rows and columns before proceeding with
  further analysis.

### 9. Feature Engineering

- Created two new columns from the existing dataset to support further analysis and provide better insights into passenger satisfaction
  and service quality.

#### 1. Creating the satisfaction_level Column
   
- Created a new column named satisfaction_level using the over_all_rating column.
- Categorised passenger ratings into three groups: Poor, Medium and High.
- Assigned Unknown to records with missing overall ratings.
- This feature helps analyse passenger satisfaction levels and calculate the percentage of ratings in each category.
  
#### 2. Creating the average_service_rating Column
   
- Created a new column named average_service_rating by calculating the row-wise average of the six service-rating columns.
- This feature provides an overall measure of passenger experience across different service aspects.
- Missing ratings were excluded from the average calculation.
- Rows with all six service ratings missing retained a missing value.
  
### Final Dataset Overview

- In this phase,I cleaned and prepared the airline review dataset for further analysis. 
- Removed duplicate records, handled missing values using suitable methods, corrected data types, standardised categorical and text
  values, and validated rating ranges. 
- Removed columns with a high proportion of missing values and created two new features: satisfaction_level and average_service_rating.
- Verified the final dataset after completing data cleaning, preprocessing and feature engineering.
- The final dataset contains 64,676 rows and 19 columns.
- The cleaned and structured dataset is now ready for Exploratory Data Analysis (EDA).

## Phase 3: Exploratory Data Analysis(EDA)

### 1. Introduction
   
Exploratory Data Analysis (EDA) was performed to understand customer satisfaction patterns, evaluate airline performance and identify service quality factors influencing passenger experience.

The analysis was conducted using Python libraries such as Pandas, Matplotlib, Seaborn and Plotly. Univariate, bivariate and multivariate techniques were used to explore individual variables and relationships between different variables.

### 2. Objectives of EDA
   
- Understand the distribution of overall customer ratings and satisfaction levels.
- Identify the lowest-rated service categories.
- Compare customer ratings based on recommendation status.
- Evaluate global airline performance and identify the highest- and lowest-rated airlines.
- Evaluate customer satisfaction and service quality among Indian airlines.
- Investigate the performance of Hainan Airlines through detailed analysis.
- Understand relationships between service quality factors.
- Compare ratings across traveller types and seat categories.
- Evaluate customer satisfaction and service quality among Indian airlines.
- Identify areas where airlines can improve customer experience.

### 3. Numerical and Categorical Data Description

##### 1. Numerical Data – describe()
   
- Used the describe() function to generate descriptive statistics for numerical columns, including count, mean, standard deviation,
  minimum, maximum and quartile values.
  
##### 3. Categorical Data – describe()
   
- Used the describe(include='str') function to summarise categorical columns. It provides the count, number of unique values, most
  frequent value and its frequency.

##### Important difference:

- df.describe() – summarises numerical columns by default.
- df.describe(include='str') – summarises categorical columns.
- df.describe(include='all') – provides summaries for both types.
  
### 4. EDA Methodology
   
#### 4.1 Univariate Analysis
     Univariate analysis was performed to understand individual variables and their distributions.

##### Analyses performed:
- Analysed the distribution of overall customer ratings using histogram.
- Examined customer satisfaction distribution across Poor, Medium and High categories.
- Analysed available ratings across the six service categories.
- Examined distributions of traveller types, seat types, trip verification and recommendation status.
  
#### 4.2 Bivariate Analysis
     Bivariate analysis was performed to understand relationships between two variables.

##### Analyses performed:
- Compared average overall ratings between customers who recommended the airline and those who did not.
- Compared average overall ratings across global airlines, considering airlines with at least 100 reviews.
- Analysed the relationship between seat type and customer satisfaction level using Seaborn visualisations.
- Compared service quality ratings between highly satisfied and poorly satisfied passengers across global airlines.
- Compared average overall ratings across traveller types and seat types.
- Evaluate customer satisfaction and service quality among Indian airlines.
  
#### 4.3 Multivariate Analysis
     Multivariate analysis was performed to examine relationships among three or more variables.

##### Analyses performed:
- Examined correlations among the six service quality factors using a correlation matrix and heatmap.
- Analysed customer ratings based on traveller type and seat category.
- Compared customer satisfaction across Indian airlines, traveller types and seat categories.
- Compared service quality ratings between highly satisfied and poorly satisfied passengers across Indian airlines.
- Conducted detailed Hainan Airlines analysis by comparing overall ratings based on trip verification and recommendation status.

#### 4.4 Data Wrangling

1. DataFrame Creation and Aggregation
   
- Grouped the airline review data using Pandas groupby() to calculate summary statistics, such as average overall ratings and High
  satisfaction percentages for each airline during the analysis.

3. DataFrame Merging (pd.merge())
   
- Used the Pandas merge() function to combine two DataFrames using the common column airline_name.
- Combined average overall ratings and High satisfaction percentages.
- Used an Inner Join (how='inner') to retain airlines present in both DataFrames.
- Created a consolidated DataFrame for comparing airline performance.
  
3. DataFrame Concatenation (pd.concat())
   
- Used the Pandas concat() function to combine the Top 5 and Bottom 5 airline DataFrames.
- Combined the two DataFrames vertically.
- Created a single DataFrame containing the selected airlines.
- Used the combined DataFrame for comparing service quality across the top-performing and bottom-performing airlines.

### 5. Important Findings and Key Insights
   
#### 5.1 Overall Customer Rating Distribution

##### Findings:
- Average overall rating: 4.34 out of 10.
- Median rating: 3.
- Most frequently given rating:1.
  
##### Key Insight:
The concentration of low ratings indicates that a considerable proportion of passengers reported unsatisfactory airline experiences.

#### 5.2 Customer Satisfaction Distribution

##### Findings:

- Poor satisfaction accounted for the highest percentage of reviews at 47.65%.
- High satisfaction represented 41.65% of reviews.
- Medium satisfaction accounted for the lowest percentage at 10.70%.
- Overall, Poor satisfaction was higher than High satisfaction, indicating that negative passenger experiences formed a significant
  portion of the reviews.

##### Key Insight:

- Poor satisfaction was more common than high satisfaction, indicating a need for improvements in overall passenger experience.

#### 5.3 Global Airline Performance Comparison

##### Findings:

- Hainan Airlines recorded the highest average overall rating of 8.49.
- China Southern Airlines ranked second with an average rating of 7.99.
- Garuda Indonesia followed with an average rating of 7.95.
- Silver Airways recorded the lowest average rating of 1.82.
- GoAir also received a low average rating of 1.92.
- Only airlines with at least 100 reviews were included in the comparison.
  
##### Key Insight:

Hainan Airlines emerged as the highest-rated airline in the comparison. It was selected for further detailed analysis to understand its customer ratings and recommendation patterns.

#### 5.4 Global Service Ratings: High vs Poor Satisfaction

##### Findings:

- Highly satisfied passengers gave higher ratings across all six service categories.
- Cabin staff service received the highest rating among highly satisfied passengers.
- Value for money showed the largest difference between the two satisfaction groups.
- Ground service and value for money received comparatively low ratings among poorly satisfied passengers.
  
##### Key Insight:

- Better service ratings were associated with higher customer satisfaction. Value for money and ground service were important areas for
  improvement.

#### 5.5 Detailed Hainan Airlines Analysis

##### Findings:

- Verified passengers who recommended Hainan Airlines gave the highest average rating of 9.22, based on 269 reviews.
- Verified passengers who did not recommend the airline gave a much lower average rating of 3.62.
- Not Verified passengers who recommended the airline gave an average rating of 9.00, based on 5 reviews.
- Passengers with Unknown verification status who recommended the airline gave an average rating of 8.65.
- Overall, passengers who recommended Hainan Airlines gave considerably higher average ratings than those who did not recommend it.

##### Key Insight:

- Verified customers who recommended Hainan Airlines gave the highest average rating of 9.22. In contrast, verified customers who did not  recommend the airline gave an average rating of 3.62. This highlights a strong association between recommendation behaviour and overall
 customer ratings.

#### 5.6 Global Service Quality Analysis

##### Findings:

- Cabin staff service received the highest average rating of 3.07.
- Seat comfort received an average rating of 2.84.
- Inflight entertainment received an average rating of 2.83.
- Food and beverages received an average rating of 2.80.
- Value for money received a relatively low average rating of 2.61.
- Ground service received the lowest average rating of 2.58.
  
##### Key Insight:

Cabin staff service performed relatively better, whereas ground service was the weakest service area. Ground service requires greater attention to improve passenger experience.

#### 5.7 Traveller Type and Seat Type Analysis

##### Findings:

- Highest average rating: Solo Leisure passengers in Business Class – 6.79.
- Lowest average rating: Couple Leisure passengers in Economy Class – 3.53.
- Economy Class accounted for the highest number of reviews.
  
##### Key Insight:

Customer ratings varied according to traveller type and seat category. Business Class generally received higher ratings across the traveller groups shown in the analysis.

#### 5.8 Correlation Between Service Ratings

##### Findings:

- All six service factors showed positive correlations.
- Strongest correlation: Ground service and value for money – 0.80.
- Weakest correlation: Inflight entertainment and ground service – 0.60.
  
##### Key Insight:

Customers who rated one service factor highly tended to give higher ratings to other service factors as well. Ground service and value for money showed the strongest relationship.

#### 5.9 Indian Airline Customer Satisfaction

##### Findings:

- Vistara appeared frequently among the combinations with higher satisfaction percentages.
- Solo Leisure passengers travelling in Vistara Premium Economy recorded the highest displayed satisfaction percentage of 81.82%.
- Satisfaction varied across airlines, traveller types and seat categories.
  
##### Key Insight:

Customer satisfaction differed across Indian airlines and passenger categories. Vistara showed strong satisfaction in several combinations, particularly among Solo Leisure passengers in Premium Economy.

#### 5.10 Indian Airline Service Quality Analysis

##### Findings:

- Value for money showed the largest difference between the two satisfaction groups.
- Ground service and cabin staff service also showed considerable differences.
- Inflight entertainment remained a comparatively weaker-rated factor even among highly satisfied passengers.
  
##### Key Insight:

Value for money was the strongest differentiating factor between highly satisfied and poorly satisfied passengers. Improving value for money and other weaker service areas may help airlines improve customer satisfaction.

### 6. Project Documentation

- The project documentation provides a detailed explanation of the project workflow, including the business problem, objectives, dataset
  information, data preparation, analysis methods, key findings, business recommendations and conclusions.
  The following documents are included:
  
  - **Software Requirements Specification (SRS):** Describes the project requirements, objectives and scope.
  - **Main Project Report:** Documents the complete project process, from data preparation to analysis, findings and conclusions.

### 7. Challenges Faced During Analysis

The following challenges were encountered while analysing the airline review dataset:

1. Missing Values: Several columns contained missing values,making data cleaning and preprocessing challenging. The aircraft and
   wifi__connectivity columns had a high percentage of missing values, making them unsuitable for further analysis.
2. Duplicate Records: Duplicate records were identified and removed to avoid repeated entries affecting the analysis.
3. Inconsistent Data: Some categorical values and date formats required standardisation and correction before analysis.
4. Different Rating Scales: Overall ratings were recorded on a 1–10 scale, whereas service quality ratings used a 1–5 scale. These
  differences were considered while performing comparisons.
5. Uneven Data Distribution: Customer reviews were not evenly distributed across airlines, traveller types and seat categories. This made
   some comparisons less representative due to differences in the number of reviews.
6. Visualisation Challenges: Some charts contained too many categories or overlapping data points. Appropriate chart types, filtering and
   formatting were used to improve readability.
   
### 8. Suggestions and Recommendations
   
Based on the analysis, the following recommendations can help airlines improve customer experience:
- Improve Ground Services: Focus on check-in procedures, airport assistance and other ground service experiences.
- Improve Value for Money: Review ticket pricing and ensure that the services provided match customer expectations.
- Enhance Inflight Entertainment: Improve entertainment options to provide a better onboard experience.
- Maintain Cabin Staff Performance: Continue strengthening cabin staff service, which received the highest average rating globally.
- Investigate Customer Complaints: Examine feedback from customers who gave low ratings and did not recommend the airline.
- Focus on Passenger Segments: Consider the different expectations of passengers based on traveller type and seat category.
- Monitor Customer Satisfaction: Regularly analyse customer feedback to identify service weaknesses and track improvements.
  
### 9. Project Outcomes

Through this analysis, the following outcomes were achieved:

#### 1. Understanding Overall Customer Ratings and Satisfaction Patterns

Analysed overall customer ratings and satisfaction levels across airline reviews to understand passenger experiences. Identified the distribution of Poor, Medium and High satisfaction levels and observed that Poor satisfaction accounted for the largest proportion of reviews.

#### 2. Evaluation of Global Airline Performance

Compared the average overall ratings of different airlines to identify the highest- and lowest-rated airlines. Hainan Airlines recorded the highest average rating of 8.49, while Silver Airways recorded the lowest average rating of 1.82 among airlines with at least 100 reviews.

#### 3. Detailed Analysis of Hainan Airlines

Selected Hainan Airlines for further analysis based on its highest average overall rating. Examined passenger ratings based on trip verification and recommendation status. The analysis showed that passengers who recommended the airline generally gave higher average ratings than those who did not recommend it.

#### 4. Comparison of Service Quality Ratings

Compared six service quality factors between highly satisfied and poorly satisfied passengers. Identified differences in ratings across seat comfort, cabin staff service, food and beverages, inflight entertainment, ground service and value for money. Value for money showed one of the largest differences between the two satisfaction groups.

#### 5. Correlation Analysis of Service Quality Factors

Examined the relationships among the six service quality factors using correlation analysis. Identified positive correlations between all service factors, with ground service and value for money showing the strongest correlation. This helped understand how different service factors are related to one another.

#### 6. Analysis of Traveller Types and Seat Categories

Evaluated customer ratings across different traveller types and seat categories. Identified variations in average ratings among Solo Leisure, Couple Leisure, Family Leisure and Business travellers. Also examined how passenger satisfaction varied across different seat categories.

#### 7. Indian Airline Performance and Service Quality Analysis

Focused on Indian airlines to compare customer satisfaction and service quality. Examined satisfaction patterns across airlines, traveller types and seat categories. Also compared service ratings between highly satisfied and poorly satisfied passengers to identify stronger and weaker service areas.

#### 8. Identification of Service Areas for Improvement

Identified service factors that received comparatively lower ratings, particularly ground service and value for money. The findings highlight areas where airlines may need to focus on improving service quality and passenger experience.

### 10. Areas for Improvement

**Value for Money:** Improve the balance between ticket prices and the quality of services provided.

**Ground Service:** Improve airport assistance, check-in support, boarding services and passenger handling.

**Inflight Entertainment:** Improve entertainment options and system quality.

**Food and Beverages:** Focus on food quality, variety and passenger preferences.

**Seat Comfort:** Improve seating comfort and passenger convenience.

**Cabin Staff Service:** Maintain good staff behaviour, communication and passenger support.

### 11. Conclusion
   
- This project provided a detailed analysis of airline customer satisfaction and service quality using passenger ratings and
  recommendation data. Through univariate, bivariate and multivariate analysis, different patterns in customer ratings, satisfaction
  levels, airline performance and service quality were identified.
  
- The analysis highlighted Hainan Airlines as the highest-rated airline in the global comparison and identified ground service and value
  for money as important areas requiring improvement. It also revealed differences in customer experiences across traveller types, seat
  categories and Indian airlines.
  
- Overall, the project demonstrates how data analysis can help understand passenger satisfaction, identify service weaknesses and support   data-driven decisions. The findings can help airlines identify areas for improvement, enhance passenger experiences and improve service   quality.




