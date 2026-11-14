# Airline-Customer-Satisfaction-Analysis
Analysis of airline passenger satisfaction and service quality using Python, Pandas, and data visualization.

## Project Overview
This project analyzes airline passenger reviews and ratings to understand customer satisfaction and service quality. It compares overall passenger ratings and evaluates seven airline service categories to identify areas that may require improvement.

## Project Objectives

- Classify overall passenger ratings into satisfaction categories.
- Calculate and compare average ratings across seven service categories.
- Identify the three lowest-rated service areas.
- Compare ratings between passengers who recommend the airline and those who do not.
- Analyze satisfaction across airlines, traveller types, and seat types.

## Dataset Source

**Source:** Mendeley Data – Airline Travel Reviews Data (Skytrax)

**Dataset Link:** https://data.mendeley.com/datasets/vgjk58vf8h/1

**Rows and Columns:** Dataset contains 64,740 rows and 19 columns before data cleaning.

## Tools and Technologies

- Python
- Jupyter Notebook
- Pandas
- Matplotlib
- Seaborn
- Plotly

## Repository Contents

- Airline_Customer_Satisfaction_Analysis_SRS.pdf – Software Requirements Specification
- Airline_Customer_Satisfaction_Analysis_Phase1.ipynb – Phase 1 analysis notebook
- Airline_Customer_Satisfaction_Analysis_Phase2.ipynb – Phase 2 analysis notebook
- data/ – Dataset folder

## How to Run the Notebook

1. Download or clone this repository.
2. Install Python, Jupyter Notebook, and the required libraries.
3. Open the notebook in Jupyter Notebook.
4. Ensure the dataset is available in the data/ folder.
5. Run the notebook cells from top to bottom.

## Phase 1 – Project Planning and SRS

- Identified and selected a suitable Skytrax airline review dataset based on the project requirements and given conditions.
- Defined the project scope, objectives, and requirements for the Airline Customer Satisfaction & Service Quality Analysis project.
- Prepared the Software Requirements Specification (SRS) document and selected the Skytrax airline review dataset for analysis.

## Phase 2 – Data Cleaning and Preprocessing

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

## Exploratory Data Analysis (EDA)

After completing data cleaning and preprocessing, Exploratory Data Analysis (EDA) was performed to understand the dataset, examine rating distributions, and explore passenger satisfaction patterns.

#### Descriptive Statistics
   
- Used describe() to examine the statistical summary of numerical columns and describe(include='str') to understand statistical summary of
  categorical columns.
  
#### Univariate,Bivariate and Multivariate Analysis

**1. Overall Rating and Satisfaction Level Distribution**

- Performed univariate analysis to examine the distribution of over_all_rating and satisfaction_level.
- Used histograms with Matplotlib to visualize passenger rating patterns.
- Used pie chart with Matplotlib to visualize satisfaction distribution.
- Calculated the percentage of passengers in each satisfaction category.
- Finding: Poor satisfaction was highest (47.65%), followed by High (41.65%) and Medium (10.70%).
- This indicates a need for airlines to improve customer satisfaction and service quality.
  
**2. Average Rating for Service Quality**

- Performed univariate analysis to examine the average ratings of six service categories using the mean() function.
- Used a Matplotlib bar chart to compare the average ratings.
- Sorted the ratings in ascending order to identify the lowest-rated services.
**Findings:**
- Cabin staff service received the highest rating (3.07).
- Ground service received the lowest rating (2.58), followed by value for money (2.61).
- Other service categories received ratings between 2.80 and 2.84.
- The results highlight ground service and value for money as key areas for improvement.
  
**3. Trip Verification Analysis**
   
- This analysis examines the distribution of verified and non-verified passenger reviews to understand how many reviews are associated
  with confirmed travel experiences.
- Used a Seaborn count plot to visualize the number of reviews in each category.
- Finding: Identified the number of reviews associated with verified and non-verified travel experiences.
  
**4. Recommendation Status Analysis** 

- Examined the percentage distribution of Yes and No recommendations.
- Used a bar chart to compare the average overall ratings for both categories.
**Findings:**
- 61.70% of passengers did not recommend the airline(average rating: 1.87).
- 38.30% recommended the airline(average rating: 8.34).
- The analysis shows a strong relationship between overall ratings and passengers' recommendation decisions.
 
**5. Airline-Wise Overall Rating Analysis**

- Grouped reviews by airline and calculated the review count and average overall rating.
- Set a minimum threshold of 100 reviews to ensure a fair comparison.
- Used a bar chart to compare the top 5 and bottom 5 airlines.
** Findings:** Hainan Airlines received the highest average rating (8.49), while Silver Airways received the lowest (1.82).

**6. Traveller Type-wise Overall Rating Analysis**

- Grouped reviews by traveller type and calculated the review count and average overall rating.
- Used a bar chart to compare average ratings across traveller categories.
**Findings:**
- Solo travellers had the highest number of reviews (23,271) and the highest average rating (4.76), while family travellers
  had the lowest average rating (3.82).

**7. Customer Satisfaction Analysis by Seat Type**
   
- Examined the distribution of High, Medium, and Poor satisfaction levels across different seat types.
- Used a Seaborn count plot to compare satisfaction levels across seat categories.
- Finding: Economy Class had the highest number of reviews, while the plot helped compare satisfaction patterns across all seat types.





## Expected Outcomes
- Passenger satisfaction analysis
- Comparison of seven service categories
- Identification of the three lowest-rated service areas
- Visualizations and key findings related to airline service quality


