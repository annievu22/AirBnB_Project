# 🏠 Airbnb NYC Data Analytics Project
![Python](https://img.shields.io/badge/Language-Python-purple)
![Tableau](https://img.shields.io/badge/Visualization-Tableau-pink)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)
![Data](https://img.shields.io/badge/Data-Airbnb‒NYC-red)

> A Python and Tableau analysis of NYC Airbnb data, revealing pricing dynamics, room type availability, and neighborhood performance, to improve platform strategy and user satisfaction.

---

## 1. Overview

This project analyzes New York City Airbnb listings using Python and Tableau to explore pricing strategies, room types, and geographic availability across boroughs. It aims to uncover trends that influence host performance, booking behavior, and neighborhood dynamics.

Data cleaning and transformation were performed in Python, with exploratory statistics and pattern detection applied across key variables like price, reviews, and availability. Results were visualized in Tableau to assist users and hosts in making smarter booking and listing decisions.

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

### 2.2. Business Impact & Insights

- Entire home/apt listings dominate in Manhattan and Brooklyn, commanding the highest prices.  
- Shared rooms and private rooms are more common in the Bronx and Queens, catering to budget travelers.  
- Review trends reflect seasonal surges, especially in summer months.  
- Some neighborhoods show high availability but lower review counts, signaling potential oversupply or visibility issues.  
- The dashboard helps hosts optimize pricing and helps users make informed booking decisions.

---

## 3. Data Sources & Schema

The dataset was downloaded from Kaggle and imported into Google Colab for transformation and analysis using Python. It contains over 48,000 Airbnb listings across the five boroughs of New York City.

### 🔗 Dataset Links

- **Kaggle Source:**  
  [🌐 View on Kaggle](https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data)

- **Google Drive Download:**  
  [📁 View Dataset (Google Drive)](https://drive.google.com/file/d/1XlNNEdb7O-8lRjbf29FlcZT9dKlozmR2/view?usp=sharing)

### 📝 Table: `airbnb_nyc_2023`

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


## 4. Methodology & Python Analysis

This section outlines the end-to-end process of cleaning, transforming, and analyzing the NYC Airbnb dataset using Python. Each step laid the foundation for interactive Tableau visualizations.

### 4.1. Data Cleaning

* **Converted `last review` to datetime format** → Enabled time-based filtering and recency insights.

```python
df['last review'] = pd.to_datetime(df['last review'], errors='coerce')
```

* **Filled missing `reviews per month` with 0** → Avoided null-related distortions in review-based metrics.

```python
df['reviews per month'] = df['reviews per month'].fillna(0)
```

* **Cleaned `price` and `service fee` columns** → Removed dollar signs and casted to float for analysis.

```python
df['price'] = df['price'].replace('[\$,]', '', regex=True).astype(float)
df['service fee'] = df['service fee'].replace('[\$,]', '', regex=True).astype(float)
```

* **Standardized categorical values (e.g., borough names)** → Fixed typos like `'manhatan'` for accurate grouping.

```python
df['neighbourhood group'] = df['neighbourhood group'].replace({'manhatan': 'Manhattan'})
```

* **Dropped duplicates and irrelevant columns** → Removed noisy features such as `license` and `house_rules`.

```python
df.drop_duplicates(inplace=True)
```

> These cleaning steps ensured data consistency, enabled reliable analysis, and supported visual design.

### 4.2. Exploratory Data Analysis (EDA)

* **Room Type Distribution** → Assessed accommodation types across listings.

```python
df['room type'].value_counts()
```

* **Average Price by Borough and Room Type** → Compared pricing patterns across areas.

```python
df.groupby(['neighbourhood group', 'room type'])['price'].mean().round(2).reset_index()
```

* **Top 10 Neighborhoods by Total Reviews** → Ranked areas by popularity and engagement.

```python
df.groupby('neighbourhood')['number of reviews'].sum().sort_values(ascending=False).head(10)
```

* **Availability Distribution** → Evaluated listing availability throughout the year.

```python
df['availability 365'].value_counts().sort_index()
```

> These insights informed key dashboard visuals related to demand, price competitiveness, and listing saturation.

## 5. Tableau Dashboard Design

- This Tableau dashboard enables users to explore pricing, room type, and neighborhood availability patterns across NYC through dynamic filters and location-based visuals.

🔗 [View Full Dashboard on Tableau Public](https://public.tableau.com/views/AirBnBProject_17531229773270/Dashboard1)

### Dashboard Snapshot

![Airbnb Tableau Dashboard](https://raw.githubusercontent.com/annievu22/AirBnB_Project/main/AirBnB%20Project%20-%20Tableau%20Snapshot.png)

### Walkthrough of Key Visuals:

* **Borough Selector (Dropdown Filter):**  
  Filters all visuals to selected boroughs—Manhattan, Brooklyn, etc.

* **Listing Count and Room Type Distribution:**  
  Pie chart showing share of Entire Home, Private Room, and Shared Room.

* **Average Price by Borough (Bar Chart):**  
  Ranks boroughs by average nightly price for all listings.

* **Top Neighborhoods by Reviews (Horizontal Bar Chart):**  
  Shows the neighborhoods with the most cumulative reviews.

* **Price vs. Number of Reviews (Scatter Plot):**  
  Highlights relationship between price and review volume for listings.

* **Availability Histogram:**  
  Displays how many listings are available throughout the year (0–365 days).

> These visuals allow users to identify patterns in pricing, availability, and demand, driving strategic decisions for both hosts and travelers.

---

## 5. Final Conclusion

This project demonstrates how Airbnb data can be transformed through Python and visualized with Tableau to reveal valuable market insights. By exploring pricing patterns, review behaviors, and listing availability, we help users better understand how location and room type affect performance.

**Key business insights:**

- Manhattan listings command higher prices but show mixed review volumes  
- Brooklyn has a high number of affordable listings with steady demand  
- Shared and private rooms cater to budget-conscious travelers, especially outside Manhattan  
- Availability data can inform seasonal pricing strategies or operational improvements

**Future enhancement:**

In future work, this project can be enhanced by:
- Adding time series of bookings to study trends over time  
- Integrating external data (crime rates, tourism flows, etc.) for contextual insights  
- Applying regression models or clustering to classify high-performing listings

Overall, this project showcases practical data analytics skills and the ability to turn complex datasets into clear, actionable insights for business users.
