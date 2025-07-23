# 🏠 Airbnb NYC Data Analytics Project
![Python](https://img.shields.io/badge/Language-Python-purple)
![Tableau](https://img.shields.io/badge/Visualization-Tableau-pink)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)
![Data](https://img.shields.io/badge/Data-Airbnb‒NYC-red)

> A Python and Tableau analysis of NYC Airbnb data, revealing pricing dynamics, room type availability, and neighborhood performance, to improve platform strategy and user satisfaction.

---

## 1. Overview

This project analyzes over 100,000 Airbnb listings in New York City using Python (pandas, seaborn, matplotlib) and visualizes findings with Tableau. It focuses on pricing patterns, room type distribution, neighborhood activity, and availability to support smarter hosting and booking decisions.

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

### Table: `airbnb_nyc_2023`

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

### 4.1. Tech Stack

- **Python (pandas, matplotlib, seaborn):** For cleaning, transforming, and exploring the dataset
- **Tableau Public:** For building an interactive dashboard highlighting pricing trends and geographic distributions

### 4.2. Methodology Overview

a. **Data Cleaning:**
   - Converted string-based dates to proper `datetime` objects  
   - Handled missing values in key columns (e.g., `reviews per month`, `last review`)  
   - Cleaned monetary columns by stripping symbols and casting to float  
   - Dropped columns with excessive null values and irrelevant features  
   - Standardized inconsistent values and removed duplicate records

b. **Initial Exploration:**
   - Generated descriptive statistics to understand data ranges, averages, and distributions  
   - Explored patterns in price, reviews, and availability using group-by logic and value counts

c. **Insight Extraction:**
   - Analyzed trends in room type pricing, geographic listing density, and host behavior  
   - Identified top neighborhoods and availability patterns to guide dashboard metrics

d. **Dashboard Development:**
   - Designed an interactive Tableau dashboard with borough filters and key KPIs  
   - Visualizations included price trends, listing counts, review volume, and availability distributions  
   - Dashboard link: [View on Tableau Public](https://public.tableau.com/views/AirBnBProject_17531229773270/Dashboard1)

> This end-to-end process enabled a structured analysis of NYC’s Airbnb market and provided actionable insights for hosts and platform strategists.

---

## 5. Python Code & Exploratory Data Analysis (EDA)

This section documents how Python was used to clean, transform, and analyze the data before dashboard creation.

### 5.1. Data Cleaning

- Removed listings with `price = 0` or missing critical values  
- Converted `'last_review'` to `datetime` using `pd.to_datetime()`  
- Replaced missing `'reviews per month'` with `0`  
- Cleaned formatting for `price` and `service fee` by removing dollar signs and converting to numeric  
- Standardized borough names (e.g., fixing typos like `'manhatan'`)  
- Dropped duplicated records and irrelevant columns (`house_rules`, `license`)

```python
df['last review'] = pd.to_datetime(df['last review'], errors='coerce')
df['reviews per month'] = df['reviews per month'].fillna(0)
df['price'] = df['price'].replace('[\$,]', '', regex=True).astype(float)
df['service fee'] = df['service fee'].replace('[\$,]', '', regex=True).astype(float)
df['neighbourhood group'] = df['neighbourhood group'].replace({'manhatan': 'Manhattan'})
df.drop_duplicates(inplace=True)
```

### 5.2. Exploratory & Descriptive Analysis

- **Average Price by Room Type and Borough:**

```python
df.groupby(['neighbourhood group', 'room type'])['price'].mean().round(2).reset_index()
```

- **Top Neighborhoods by Review Count:**

```python
df.groupby('neighbourhood')['number of reviews'].sum().sort_values(ascending=False).head(10)
```

- **Room Type Distribution:**

```python
df['room type'].value_counts()
```

- **Availability Distribution:**

```python
df['availability 365'].value_counts().sort_index()
```

These Python-based EDA steps provided the foundational insights used to design the final Tableau dashboard.

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

This project demonstrates how Airbnb data can be transformed through Python and visualized with Tableau to reveal valuable market insights. By exploring pricing patterns, review behaviors, and listing availability, we help users better understand how location and room type affect performance.

Key business insights include:
- Manhattan listings command higher prices but show mixed review volumes  
- Brooklyn has a high number of affordable listings with steady demand  
- Shared and private rooms cater to budget-conscious travelers, especially outside Manhattan  
- Availability data can inform seasonal pricing strategies or operational improvements

This end-to-end pipeline, from SQL data prep to Tableau visualization, provides a model for understanding platform-based marketplaces and supports smarter hosting, pricing, and planning strategies.

In future work, this project can be enhanced by:
- Adding time series of bookings to study trends over time  
- Integrating external data (crime rates, tourism flows, etc.) for contextual insights  
- Applying regression models or clustering to classify high-performing listings

Overall, this project showcases practical data analytics skills and the ability to turn complex datasets into clear, actionable insights for business users.
