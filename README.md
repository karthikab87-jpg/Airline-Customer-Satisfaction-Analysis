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

 Note: The dataset file is too large to upload directly to this GitHub repository. Therefore, it has not been included in the repository   Please access the original dataset using the link above and download it from Mendeley Data before running the notebook.

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
- data/ – Dataset folder

## How to Run the Notebook

1. Download or clone this repository.
2. Install Python, Jupyter Notebook, and the required libraries.
3. Open the notebook in Jupyter Notebook.
4. Ensure the dataset is available in the data/ folder.
5. Run the notebook cells from top to bottom.

## Phase 1 – Project Planning and SRS

- Identified and selected a suitable Skytrax airline review dataset based on the project requirements and given conditions.
- Defined the project scope, objectives, and requirements for the Airline Customer Satisfaction & Service Quality Analysis project.       - Prepared the Software Requirements Specification (SRS) document and selected the Skytrax airline review dataset for analysis.

## Phase 2 – Data Cleaning and Preprocessing

- Imported and inspected the dataset, identified and handled missing values, removed duplicate records, standardized categorical            values,converted date columns into datetime format, and validated rating ranges. Created two new features: satisfaction_level and         average_service_rating, to support further analysis.

### 1. Creating a Copy of the Dataset
     
- Created a copy of the original dataset to preserve the raw data. This allows cleaning operations to be performed without changing the     original dataset.
  
### 2. Checking Missing Values
   
- Checked missing values in each column to identify incomplete data and decide how to handle them.
  
3. Checking and Removing Duplicate Records
   
- Identified 64 duplicate records and removed them while keeping the first occurrence to avoid repeated entries affecting the analysis.
  
- Checked again to confirm that no duplicate records remained.
 
4. Converting Date Columns
   
- Converted review_date and date_flown from text into datetime format to make them suitable for date-based operations and analysis.
  
- Assigned the first day of the month as a placeholder for date_flown because the exact travel date was unavailable.

 5.Handling Missing Values in Numerical Rating Columns
 
- Identified missing values in the over_all_rating column and the seven service-rating columns.
  
- Retained the missing values without replacement because they represent unavailable passenger feedback.
  
- Avoided replacing missing ratings with assumed values, as this could affect the accuracy of the analysis.
  
- Pandas automatically excludes missing values from statistical calculations where applicable.
  
- The available ratings will be used for further analysis, and the number of valid responses will be considered while interpreting the      results.
  
- The wifi__connectivity column was removed because it contained a high proportion of missing values (approximately 63.5%).
  
- This helps keep the service quality analysis focused on categories with more available responses.
  
7. Validating Rating Values
   
- Checked whether overall ratings were within the 1–10 range and service ratings were within the 1–5 range to identify invalid values.
  
8.Handling Missing Values in Categorical Columns

1. Checking Missing Values
   
- Checked missing values in the categorical columns to understand the amount of missing data and decide suitable handling methods.
  
2. Handling Missing Values in seat_type
   
- Replaced missing values in the seat_type column with the mode (most frequently occurring category) because only a small number of
  values were missing.    
  
- This helped retain the records and maintain consistency in the categorical data.
  
3. Removing the aircraft Column
   
- Removed the aircraft column because it contained a high proportion of missing values (approximately 56.7%) and was not required for the   project's analysis objectives.
  
4. Handling Missing Values in Remaining Categorical Columns
   
- Replaced missing values in the remaining categorical columns with Unknown to preserve records without making assumptions about the        missing information.
  
- This also helps distinguish unavailable information from existing categories.

9.Standardising Categorical Columns

1. Checking Categorical Value Counts
   
- Examined the value counts of each categorical column to understand the category distribution and identify inconsistent labels.
  
2. Checking review_header and airline_name
   
- Checked both columns and confirmed that they had no missing values.
  
3. Standardising the trip_verified Column
   
- Identified inconsistent labels in the trip_verified column and standardised them into three categories: Verified, Not Verified, and
  Unknown.
  
- This helps maintain uniformity and avoids treating similar labels as separate categories.
  
4. Removing Unwanted Spaces
   
- Removed leading and trailing spaces from all categorical columns to maintain consistent category values and avoid unwanted variations.
  
5. Rechecking Categorical Value Counts
   
- Examined the value counts again after standardisation and space removal to verify consistency in the categorical data.

10.Dataset Overview and Exploration

- Examined the dataset using head(), columns, shape, info() and describe() to understand its structure, column names, dimensions, data
  types, non-null values and statistical summary.
  
- Checked the dataset shape after removing unnecessary columns to verify the updated number of rows and columns before proceeding with
   further analysis.

11.Feature Engineering

- Created two new columns from the existing dataset to support further analysis and provide better insights into passenger satisfaction
   and service quality.

1. Creating the satisfaction_level Column
   
- Created a new column named satisfaction_level using the over_all_rating column.
  
- Categorised passenger ratings into three groups: Poor, Medium and Positive.
  
- Assigned Unknown to records with missing overall ratings.
  
- This feature helps analyse passenger satisfaction levels and calculate the percentage of ratings in each category.
  
2. Creating the average_service_rating Column
   
- Created a new column named average_service_rating by calculating the row-wise average of the six service-rating columns.
  
- This feature provides an overall measure of passenger experience across different service aspects.
  
- Missing ratings were excluded from the average calculation.
  
- Rows with all six service ratings missing retained a missing value.
  
### Final Dataset Overview

- Verified the final dataset after completing data cleaning, preprocessing and feature engineering.
- The final dataset contains 64,676 rows and 19 columns.
- The cleaned and structured dataset is now ready for Exploratory Data Analysis (EDA).
  
## Expected Outcomes
- Passenger satisfaction analysis
- Comparison of seven service categories
- Identification of the three lowest-rated service areas
- Visualizations and key findings related to airline service quality


