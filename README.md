# 🏠 Airbnb NYC Data Analytics Project
![SQL](https://img.shields.io/badge/SQL-MySQL-blue)
![Tableau](https://img.shields.io/badge/Visualization-Tableau-orange)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)
![Data](https://img.shields.io/badge/Data-Airbnb‒NYC-informational)

> A data-driven analysis of Airbnb listings in New York City to uncover key insights in pricing, room types, and neighborhood trends, with the goal of improving platform strategy and user satisfaction.

---

## 1. Overview

This project analyzes over 100,000 Airbnb listings across New York City to uncover patterns in pricing, availability, and property types. By combining SQL querying and Tableau visualization, the analysis supports data-driven decision-making for both hosts and platform users.

The project uses a cleaned dataset from Kaggle and applies CTEs, aggregation, filtering, and joins to extract insights. Results are visualized through an interactive Tableau dashboard.

---

## 2. Business Objectives

### 2.1. Business Problem

With over 100,000 listings, Airbnb hosts and users often struggle to understand how factors like location, room type, and seasonality affect pricing and demand. Business users need data-driven insights to optimize listings and identify underserved areas.

> **Key questions** addressed in this analysis:
> - Where are Airbnb listings most concentrated within NYC?
> - How does price vary across boroughs and room types?
> - What is the distribution of room types and availability?
> - How have reviews changed over time?
> - What neighborhoods show strong performance or potential for growth?

### 2.2. Goal of the Dashboard

To deliver an interactive visual tool that:
- Helps users and hosts compare pricing by room type and borough  
- Reveals trends in reviews and listing availability over time  
- Highlights underserved neighborhoods or property types  
- Supports strategic decisions for property investments or platform improvements

### 2.3. Business Impact & Insights

- Entire home/apt listings dominate in Manhattan and Brooklyn, commanding the highest prices  
- Shared rooms and private rooms are more common in the Bronx and Queens, catering to budget travelers  
- Review trends reflect seasonal surges, especially in summer months  
- Some neighborhoods show high availability but lower review counts, signaling potential oversupply or visibility issues  
- The dashboard helps hosts optimize pricing and helps users make informed booking decisions

---

## 3. Data Sources & Schema

The dataset was downloaded from Kaggle and imported into MySQL Workbench for querying and transformation. It contains over 48,000 Airbnb listings across the five boroughs of New York City.

### 🔗 Dataset Links

- **Kaggle Source:**  
  Open dataset published by Inside Airbnb, providing comprehensive listing and host details.  
  [🌐 View on Kaggle](https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data)

- **Download via Google Drive:**  
  CSV file for direct access and analysis.  
  [📁 View Dataset (Google Drive)](https://drive.google.com/file/d/1XlNNEdb7O-8lRjbf29FlcZT9dKlozmR2/view?usp=sharing)

### 3.1. Table: `airbnb_nyc_2023`

| Column Name         | Description                                         |
|---------------------|-----------------------------------------------------|
| id                  | Unique listing ID                                  |
| name                | Name/title of the listing                          |
| host_id             | Unique ID of the host                              |
| neighbourhood_group| One of the 5 boroughs in NYC                        |
| neighbourhood       | Name of the neighborhood                          |
| latitude, longitude | Geolocation of the property                        |
| room_type           | Type of accommodation: Entire, Private, Shared     |
| price               | Nightly price in USD                               |
| minimum_nights      | Minimum nights required to book                    |
| number_of_reviews   | Total number of reviews for the listing            |
| last_review         | Date of most recent review                         |
| reviews_per_month   | Avg. number of reviews per month                   |
| calculated_host_listings_count | Number of listings by the same host   |
| availability_365    | Days available in the calendar year                |

---

## 4. Teck Stack & Methodology

This project uses SQL for querying and cleaning, followed by Tableau to present interactive visuals and insights.

### 4.1. Tech Stack

- **SQL (MySQL Workbench):** Used for data exploration, filtering, and aggregation, including joins and subqueries.
- **Python (pandas, seaborn):** Used in the initial phase for light cleaning and data type verification.
- **Tableau Public:** Used for dashboard design and publishing interactive visualizations.

### 4.2. Methodology

a. **Data Cleaning:**
   - Verified and formatted date columns using `STR_TO_DATE()`
   - Removed listings with missing or zero prices using `WHERE price > 0`
   - Replaced empty strings with `NULL` using `NULLIF()`

b. **Exploratory Analysis in SQL:**
   - Aggregated average price by room type and borough
   - Counted listings per neighborhood and host
   - Examined review patterns and availability distributions
   - Flagged hosts with multiple listings to analyze market behavior

c. **Advanced SQL Logic:**
   - Created **CTEs** to group listing types and pricing buckets
   - Used **window functions** to rank top neighborhoods by number of reviews
   - Applied **joins** to enrich the data with neighborhood-level summaries

d. **Visualization Design:**
   - Developed a Tableau dashboard focused on key metrics like price, reviews, availability, and distribution
   - Added filters by borough so users can easily explore trends in each area of NYC.
   - Dashboard hosted on [Tableau Public](https://public.tableau.com/views/AirBnBProject_17531229773270/Dashboard1)

> These steps created a comprehensive view of Airbnb’s NYC market, allowing for performance benchmarking and targeted improvements.

---

## 5. SQL Data Preparation & Analytical Workflow

This section documents how SQL was used to clean and analyze the data prior to dashboard creation.

### 5.1. Data Cleaning

- Removed listings with `price = 0` or missing values in key fields  
- Converted review dates using `STR_TO_DATE(last_review, '%Y-%m-%d')`  
- Used `CAST()` to ensure numeric fields like `price` and `availability` were correctly typed

### 5.2. Exploratory & Descriptive Analysis

- **Average Price by Room Type and Borough:**
  ```sql
  SELECT neighbourhood_group, room_type, ROUND(AVG(price), 2) AS avg_price
  FROM airbnb_nyc_2023
  WHERE price > 0
  GROUP BY neighbourhood_group, room_type;
  ```

- **Top Neighborhoods by Reviews:**
  ```sql
  SELECT neighbourhood, SUM(number_of_reviews) AS total_reviews
  FROM airbnb_nyc_2023
  GROUP BY neighbourhood
  ORDER BY total_reviews DESC
  LIMIT 10;
  ```

- **Room Type Distribution:**
  ```sql
  SELECT room_type, COUNT(*) AS count
  FROM airbnb_nyc_2023
  GROUP BY room_type;
  ```

- **Availability Distribution:**
  ```sql
  SELECT availability_365, COUNT(*) AS listing_count
  FROM airbnb_nyc_2023
  GROUP BY availability_365;
  ```

---

## 6. Tableau Dashboard

🔗 [View Full Dashboard on Tableau Public](https://public.tableau.com/views/AirBnBProject_17531229773270/Dashboard1)

### Dashboard Snapshot

Below is a snapshot of the Tableau dashboard:

![Airbnb Tableau Dashboard](https://raw.githubusercontent.com/annievu22/AirBnB_Project/main/AirBnB%20Project%20-%20Tableau%20Snapshot.png)

### Walkthrough of Key Visuals:

- **Borough Selector (Dropdown Filter):**  
  Filters all visuals to selected boroughs—Manhattan, Brooklyn, etc.

- **Listing Count and Room Type Distribution:**  
  Pie chart showing share of Entire Home, Private Room, and Shared Room.

- **Average Price by Borough (Bar Chart):**  
  Ranks boroughs by average nightly price for all listings.

- **Top Neighborhoods by Reviews (Horizontal Bar Chart):**  
  Shows the neighborhoods with the most cumulative reviews.

- **Price vs. Number of Reviews (Scatter Plot):**  
  Highlights relationship between price and review volume for listings.

- **Availability Histogram:**  
  Displays how many listings are available throughout the year (0–365 days).

> These visuals allow users to identify patterns in pricing, availability, and demand, driving strategic decisions for both hosts and travelers.

---
## 7. Final Conclusion

This project demonstrates how Airbnb data can be transformed through SQL and visualized with Tableau to reveal valuable market insights. By exploring pricing patterns, review behaviors, and listing availability, we help users better understand how location and room type affect performance.

Key business insights include:
- Manhattan listings command higher prices but show mixed review volumes  
- Brooklyn has a high number of affordable listings with steady demand  
- Shared and private rooms cater to budget-conscious travelers, especially outside Manhattan  
- Availability data can inform seasonal pricing strategies or operational improvements

This end-to-end pipeline—from SQL data prep to Tableau visualization—provides a model for understanding platform-based marketplaces and supports smarter hosting, pricing, and planning strategies.

In future work, this project can be enhanced by:
- Adding time series of bookings to study trends over time  
- Integrating external data (crime rates, tourism flows, etc.) for contextual insights  
- Applying regression models or clustering to classify high-performing listings

Overall, this project showcases practical data analytics skills and the ability to turn complex datasets into clear, actionable insights for business users.
