# Airline Customer Satisfaction & Service Quality Analysis

A Python-based analysis of airline passenger reviews to understand customer satisfaction, compare service quality, and identify opportunities to improve the passenger experience.

---

## Project Overview

This project explores passenger reviews and ratings from the Skytrax airline travel reviews dataset. It examines overall customer ratings, satisfaction levels, six service quality dimensions, and differences across airlines and passenger groups.

The analysis focuses on **customer experience and service quality**. It does not analyse flight delays or cancellations and does not use synthetic data.

## Project Objectives

- Classify passenger ratings into Poor, Medium, and High satisfaction levels.
- Evaluate and compare the six airline service quality dimensions.
- Identify the lowest-rated service areas and opportunities for improvement.
- Compare overall ratings by recommendation status.
- Compare airline performance using average overall ratings and review counts.
- Explore satisfaction across traveller types and seat categories.
- Compare service quality between highly satisfied and poorly satisfied passengers.
- Examine global airline performance and conduct a focused analysis of Hainan Airlines.
- Explore customer satisfaction and service quality among Indian airlines.
- Examine relationships between the six service quality dimensions using correlation analysis.

## Project Scope

| Included in the analysis | Outside the scope |
|---|---|
| Overall passenger ratings and satisfaction levels | Flight delays and cancellations |
| Six service quality dimensions | Predictive modelling |
| Airline and passenger-group comparisons | Synthetic or artificially generated data |
| Recommendation status and trip verification | Causal claims about customer satisfaction |

## Dataset

- **Source:** Mendeley Data – Airline Travel Reviews Data (Skytrax)
- **Dataset:** [Airline Travel Reviews Data](https://data.mendeley.com/datasets/vgjk58vf8h/1)
- **Original size:** 64,740 rows × 19 columns
- **Final cleaned dataset:** 64,676 rows × 19 columns

The dataset contains passenger review information, airline names, traveller and seat categories, recommendation status, overall ratings, and service quality ratings.

## Tools and Technologies

| Tool / Library | Purpose |
|---|---|
| Python | Programming language used for the analysis |
| Jupyter Notebook | Writing and running the analysis |
| Pandas | Data loading, cleaning, transformation, grouping, and aggregation |
| NumPy | Numerical operations |
| Matplotlib | Data visualisation |
| Seaborn | Statistical visualisation and correlation heatmap |
| Plotly | Interactive visualisations |

## Repository Contents

| Item | Description |
|---|---|
| `Airline_Customer_Satisfaction_Analysis_SRS.pdf` | Software Requirements Specification |
| `Airline_Customer_Satisfaction_Analysis-Notebook` | Project analysis notebook |
| `Airline_Customer_Satisfaction_Analysis_Documentation` | Project documentation |
| `data/` | Folder organised for project data |

**Dataset note:** The original dataset exceeded GitHub's file-size restrictions and could not be uploaded directly into the `data/` folder. A compressed ZIP copy was uploaded separately to the repository.

## How to Run the Project

1. Clone or download this repository.
2. Install Python and Jupyter Notebook.
3. Install the libraries used in the project: Pandas, NumPy, Matplotlib, Seaborn, and Plotly.
4. Make the dataset available in the location expected by the notebook.
5. Open the notebook in Jupyter Notebook.
6. Run the cells in sequence, from top to bottom.

---

## Project Workflow

The project was completed in three phases:

1. **Phase 1 – Project Planning, SRS and Initial Dataset Exploration**
2. **Phase 2 – Data Cleaning, Preprocessing and Feature Engineering**
3. **Phase 3 – Exploratory Data Analysis (EDA)**

<details>
<summary><strong>Phase 1 – Project Planning, SRS and Initial Dataset Exploration</strong></summary>

### Work completed

- Identified and selected the Skytrax airline review dataset based on the project requirements.
- Defined the project title, domain, objectives, scope, and requirements.
- Prepared the Software Requirements Specification (SRS) document.
- Imported the required Python libraries, including Pandas, NumPy, Matplotlib, and Seaborn.
- Loaded the dataset into a Pandas DataFrame.
- Inspected the first and last records using `head()` and `tail()`.
- Examined the dataset dimensions, column names, and data types using `shape`, `columns`, `info()`, and `dtypes`.
- Reviewed non-null information to understand the dataset structure and identify areas requiring further inspection.

### Outcome

The initial exploration provided an understanding of the dataset's structure, variables, dimensions, and data types. This helped establish the preparation steps required before analysis.

</details>

<details>
<summary><strong>Phase 2 – Data Cleaning, Preprocessing and Feature Engineering</strong></summary>

### 1. Creating a working copy

- Created a copy of the original dataset so that cleaning operations could be performed without changing the raw data.

### 2. Checking and removing duplicate records

- Identified 64 duplicate records.
- Removed duplicate records while keeping the first occurrence.
- Checked the dataset again to confirm that duplicate records had been removed.

### 3. Inspecting and converting data types

- Checked the data types of all columns using the Pandas `dtypes` attribute.
- Identified that `review_date` and `date_flown` were stored as strings.
- Converted the date columns to datetime format.
- Used the first day of the month as a placeholder for `date_flown`, because the exact travel date was not available.

### 4. Checking and handling missing values

- Checked missing-value counts across the dataset.
- Retained missing values in numerical rating columns rather than replacing them with assumed ratings.
- Removed `wifi__connectivity` because approximately 63.5% of its values were missing.
- Removed `aircraft` because approximately 56.7% of its values were missing and the column was not required for the project objectives.
- Filled missing `seat_type` values using the mode.
- Replaced missing values in `route` and `type_of_traveller` with `Unknown`, preserving records without making assumptions about the missing information.
- Retained missing `date_flown` values because the actual travel month and year were unavailable.
- Standardised `trip_verified` into three categories: `Verified`, `Not Verified`, and `Unknown`.

### 5. Validating rating values

- Checked that overall ratings were within the 1–10 range.
- Checked that service ratings were within the 1–5 range.
- Retained unavailable rating values as missing rather than imputing assumed scores.

### 6. Standardising categorical and text columns

- Examined category counts to identify inconsistent labels.
- Removed leading and trailing spaces from categorical columns.
- Converted `review_header` to title case.
- Converted `review_text` to lowercase.
- Removed commas from the review text fields as part of text standardisation.
- Corrected inconsistent route formatting, including unwanted characters and symbols.
- Rechecked category counts after standardisation.

### 7. Dataset overview

- Used `head()`, `columns`, `shape`, `info()`, and `describe()` to review the dataset after cleaning.
- Checked the updated dimensions, column names, data types, non-null values, and descriptive statistics.

### 8. Feature engineering

Created two additional features to support the analysis.

**A. `satisfaction_level`**

- Derived this feature from the existing `over_all_rating` column.
- Grouped passenger ratings into three categories: Poor, Medium, and High.
- Assigned `Unknown` where the overall rating was missing.
- Used this feature to examine the distribution of passenger satisfaction.

**B. `average_service_rating`**

- Calculated the row-wise average of the six service quality rating columns.
- Excluded missing service ratings from each row's average calculation.
- Left the result missing when all six service ratings were unavailable.
- Used this feature as an overall measure of the service ratings provided in an individual review.

### Final dataset

After duplicate removal, column selection, missing-value handling, standardisation, and feature engineering, the prepared dataset contained **64,676 rows and 19 columns**.

The cleaned dataset was ready for Exploratory Data Analysis (EDA).

</details>

<details>
<summary><strong>Phase 3 – Exploratory Data Analysis (EDA)</strong></summary>

### 1. EDA objectives

- Understand the distribution of overall ratings and satisfaction levels.
- Identify the lowest-rated service categories.
- Compare overall ratings by recommendation status.
- Evaluate global airline performance.
- Compare service quality between highly satisfied and poorly satisfied passengers.
- Explore Hainan Airlines in greater detail.
- Examine relationships between service quality dimensions.
- Compare ratings across traveller types and seat categories.
- Analyse customer satisfaction and service quality among Indian airlines.

### 2. Descriptive statistics

- Used `describe()` to summarise numerical columns, including count, mean, standard deviation, minimum, maximum, and quartiles.
- Used `describe(include='object')` to summarise categorical columns, including count, unique values, most frequent value, and frequency.
- Used `describe(include='all')` when a combined summary was required.

### 3. Univariate analysis

Examined individual variables and their distributions:

- Overall customer rating distribution using a histogram.
- Passenger satisfaction distribution across Poor, Medium, and High.
- Available ratings across the six service categories.
- Traveller types, seat types, trip verification, and recommendation status.

### 4. Bivariate analysis

Explored relationships between pairs of variables:

- Compared average overall ratings for passengers who recommended the airline and those who did not.
- Compared average overall ratings across airlines, including airlines with at least 100 reviews.
- Examined seat type and satisfaction level.
- Compared service quality ratings between highly satisfied and poorly satisfied passengers across global airlines.
- Compared average overall ratings across traveller types and seat categories.
- Examined customer satisfaction and service quality among Indian airlines.

### 5. Multivariate analysis

Explored relationships involving multiple variables:

- Examined correlations among the six service quality factors using a correlation matrix and heatmap.
- Analysed customer ratings by traveller type and seat category.
- Compared satisfaction across Indian airlines, traveller types, and seat categories.
- Compared service quality between highly satisfied and poorly satisfied passengers across Indian airlines.
- Analysed Hainan Airlines ratings by trip verification and recommendation status.

### 6. Data wrangling and aggregation

- Used Pandas `groupby()` to calculate analysis metrics such as average overall rating and High satisfaction percentage for each airline.
- Used `pd.merge()` to combine airline-level summary DataFrames using `airline_name`, with an inner join to retain airlines present in both.
- Used `pd.concat()` to combine the Top 5 and Bottom 5 airline DataFrames for comparison.

### 7. Key findings and insights

#### Overall customer ratings and satisfaction

- Average overall rating: **4.34 out of 10**.
- Median overall rating: **3**.
- Most frequent overall rating: **1**.
- Poor satisfaction: **47.65%**.
- High satisfaction: **41.65%**.
- Medium satisfaction: **10.70%**.

The proportion of Poor satisfaction was higher than High satisfaction, showing that negative passenger experiences formed a substantial share of the reviews. Satisfaction percentages exclude records with missing overall ratings.

#### Global airline performance

Airline comparisons included airlines with at least 100 reviews.

| Higher average ratings | Average rating | Lower average ratings | Average rating |
|---|---:|---|---:|
| Hainan Airlines | 8.49 | Silver Airways | 1.82 |
| China Southern Airlines | 7.99 | GoAir | 1.92 |
| Garuda Indonesia | 7.95 | ITA Airways | 2.23 |

Hainan Airlines recorded the highest average overall rating in the comparison and was selected for further analysis.

#### Global service quality

| Service category | Average rating (out of 5) |
|---|---:|
| Cabin staff service | 3.07 |
| Seat comfort | 2.84 |
| Inflight entertainment | 2.83 |
| Food and beverages | 2.80 |
| Value for money | 2.61 |
| Ground service | 2.58 |

Cabin staff service had the highest average rating, while ground service had the lowest. Ground service and value for money were identified as areas requiring attention.

#### Recommendation status

- Passengers who recommended the airline generally gave much higher overall ratings than those who did not.
- Average overall rating for reviews marked Yes: **8.34**.
- Average overall rating for reviews marked No: **1.87**.

These averages describe the observed reviews and should not be interpreted as evidence that recommendation status causes higher ratings.

#### Hainan Airlines analysis

- Verified passengers who recommended Hainan Airlines gave an average rating of **9.22**, based on 269 reviews.
- Verified passengers who did not recommend the airline gave an average rating of **3.62**.
- Not Verified passengers who recommended the airline gave an average rating of **9.00**, based on 5 reviews.
- Passengers with Unknown verification status who recommended the airline gave an average rating of **8.65**.

The results show a clear difference in average ratings by recommendation status within the analysed Hainan Airlines reviews. The number of reviews should be considered when interpreting smaller groups.

#### Traveller type and seat category

- Solo Leisure passengers in Business Class recorded the highest average rating shown: **6.79**.
- Couple Leisure passengers in Economy Class recorded the lowest average rating shown: **3.53**.
- Economy Class accounted for the highest number of reviews.

Ratings varied across traveller types and seat categories.

#### Correlation between service quality factors

- All six service factors showed positive correlations.
- Strongest correlation: Ground service and value for money (**0.80**).
- Weakest correlation: Inflight entertainment and ground service (**0.60**).

The positive correlations indicate that higher ratings in one service dimension tended to occur alongside higher ratings in other dimensions. Correlation does not establish causation.

#### Indian airline customer satisfaction

- Vistara appeared frequently among the combinations with higher satisfaction percentages.
- Solo Leisure passengers travelling in Vistara Premium Economy recorded the highest displayed satisfaction percentage: **81.82%**.
- Satisfaction varied across airlines, traveller types, and seat categories.

#### Indian airline service quality

- Value for money showed the largest difference between highly satisfied and poorly satisfied passenger groups.
- Ground service and cabin staff service also showed considerable differences.
- Inflight entertainment remained a comparatively weaker-rated factor even among highly satisfied passengers.

### 8. Challenges encountered

1. **Missing values:** Several columns contained missing information. The aircraft and wifi connectivity columns had high proportions of missing values and were removed.
2. **Duplicate records:** Duplicate entries needed to be identified and removed to avoid repeated records affecting the analysis.
3. **Inconsistent data:** Categorical labels, text fields, route values, and date formats required standardisation.
4. **Different rating scales:** Overall ratings used a 1–10 scale, while service quality ratings used a 1–5 scale.
5. **Uneven data distribution:** Review counts varied across airlines, traveller types, and seat categories, so some group comparisons had fewer observations.
6. **Visualisation challenges:** Some charts contained many categories or overlapping points. Filtering and suitable chart types were used to improve readability.

### 9. Suggestions and recommendations

- **Improve ground services:** Focus on check-in procedures, airport assistance, boarding, and passenger handling.
- **Improve value for money:** Review the balance between ticket prices and the quality of services provided.
- **Enhance inflight entertainment:** Improve entertainment options and system quality.
- **Maintain cabin staff performance:** Continue supporting the service area with the highest average rating.
- **Review customer feedback:** Examine low-rated reviews and feedback from passengers who did not recommend the airline.
- **Consider passenger segments:** Take traveller type and seat category into account when reviewing customer expectations.
- **Monitor satisfaction:** Regularly analyse passenger feedback to identify service weaknesses and track changes over time.

</details>

---

## Project Outcomes

Through the project, the following outcomes were achieved:

1. **Customer satisfaction analysis:** Examined overall ratings and the distribution of Poor, Medium, and High satisfaction.
2. **Global airline comparison:** Compared average overall ratings and identified the highest- and lowest-rated airlines among those with at least 100 reviews.
3. **Focused airline analysis:** Investigated Hainan Airlines ratings by trip verification and recommendation status.
4. **Service quality comparison:** Evaluated six service dimensions and compared ratings between highly satisfied and poorly satisfied passengers.
5. **Correlation analysis:** Identified positive relationships among the service quality factors.
6. **Passenger segment analysis:** Compared ratings across traveller types and seat categories.
7. **Indian airline analysis:** Explored satisfaction and service quality across Indian airlines and passenger groups.
8. **Improvement opportunities:** Identified ground service and value for money as important areas for further attention.

## Conclusion

This project analysed airline customer reviews to understand passenger satisfaction, compare airline performance, and evaluate service quality. Univariate, bivariate, and multivariate analysis helped identify patterns across overall ratings, satisfaction levels, airlines, traveller types, and seat categories.

The analysis identified Hainan Airlines as the highest-rated airline in the global comparison of airlines with at least 100 reviews. It also highlighted ground service and value for money as important areas for improvement. Comparisons between highly satisfied and poorly satisfied passengers showed differences across all six service quality dimensions.

Overall, the project demonstrates how Python-based data analysis can turn customer feedback into useful insights. These findings can help airlines understand passenger experiences, identify weaker service areas, and make more informed decisions to improve service quality.

---

*This project was completed as part of a Data Analytics learning programme.*
