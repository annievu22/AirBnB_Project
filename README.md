# 📊 Airbnb Data Analytics Project

> A data-driven analysis of Airbnb listings in New York City to uncover key insights in pricing, room types, and neighborhood trends, with the goal of improving platform strategy and user satisfaction.

---

## 1. Overview

This project explores Airbnb’s listing data using Python and Tableau to deliver actionable business insights. The analysis focuses on room types, listing prices, neighborhood patterns, and customer engagement through reviews. It is motivated by Airbnb’s growing adoption of data and AI to enhance the customer experience, reduce host complaints, and optimize listing performance.

---

## 2. Business Objectives

- Analyze pricing dynamics and their relation to room types.
- Understand the geographic distribution of listings and reviews.
- Identify booking and review trends over time to support strategic decisions.
- Uncover potential improvement areas for host performance and user experience.

---

## 3. Tech Stack

The dashboard was built using the following tools and technologies:

- **Tableau Public** – Primary platform for building and sharing the interactive dashboard.
- **Python (pandas, matplotlib, seaborn)** – Used for data cleaning, transformation, and exploratory data analysis before loading into Tableau.
- **CSV Format** – Cleaned dataset exported from Python and used as Tableau data source.
- **Calculated Fields & Filters** – Applied in Tableau to dynamically break down pricing, reviews, and room types by region and room category.
- **Export Format** – .png for snapshot previews, and Tableau Public link for full interactivity.

---

## 4. Dataset Description

- **Source**: Airbnb Open Data  
- **Size**: 100,000+ rows, 26 columns  
- **Columns** include: `price`, `room type`, `neighbourhood group`, `reviews per month`, `last review`, `availability`, etc.

---

## 5. Features / Highlights

### 5.1. Business Problem

With over 100,000 Airbnb listings in NYC alone, users and hosts alike struggle to understand how room type, neighborhood, and seasonality affect pricing and performance. Business users also need to spot underserved regions or property types to optimize offerings.

> **Key questions** included:  
> - Where are listings concentrated?  
> - How does pricing vary by room type and borough?  
> - What time periods have higher user engagement?
> - What is the distribution of listing prices?
> - How are different room types distributed?
> - How are listings distributed across different neighborhoods?
> - What is the relationship between price and room type?
> - How has the number of reviews changed over time?

---

### 5.2. Goal of the Dashboard

To create a **user-friendly, interactive dashboard** that:

- Enables users to explore trends in Airbnb listings across New York City
- Supports data-driven decisions in pricing strategy, marketing, and host targeting
- Helps uncover patterns in neighborhood performance and review volume

---

### 5.3. Walkthrough of Key Visuals

- **Key Metrics (Top Cards)**  
  Total Listings, Total Reviews, Avg. Price, Available Days/Year

- **Map of Listings by Neighborhood**  
  Interactive map showing listing density across NYC boroughs

- **Room Type Breakdown**  
  Bar chart comparing counts of entire homes, private rooms, shared rooms, etc.

- **Price Distribution**  
  Histogram visualizing price variability across all listings

- **Listings by Borough (Bar Chart)**  
  Highlights dominance of Manhattan and Brooklyn in total listings

- **Review Trends Over Time (Line Chart)**  
  Tracks changes in review volume to capture seasonality and market shifts

---

### 5.4. Business Impact & Insights

- 📌 **Market Focus**: Manhattan and Brooklyn should remain key focus areas for Airbnb growth.
- 📉 **Review Drop Analysis**: Post-2020 decline in reviews indicates sensitivity to global events (e.g., COVID-19).
- 🧭 **User Targeting**: Data can support host recommendations and neighborhood-based promotion strategies.
- 💡 **Pricing Strategy**: Dynamic pricing models can be fine-tuned based on room type, location, and time of year.

---

## 6. Data Schema

| Category              | Columns (examples)                                  |
|----------------------|------------------------------------------------------|
| Identification        | `id`, `host id`, `host name`, `host_identity_verified` |
| Location              | `neighbourhood`, `neighbourhood group`, `lat`, `long` |
| Listing Information   | `room type`, `price`, `minimum nights`, `availability 365` |
| Engagement Metrics    | `number of reviews`, `last review`, `reviews per month` |

---

## 7. Data Cleaning & Preparation (Python)

- Removed missing and duplicate records  
- Converted columns to correct data types (`price`, `last review`)  
- Filled NA values in key columns such as reviews and price  
- Dropped irrelevant columns: `license`, `house_rules`  
- Final cleaned dataset: **101,410 rows × 24 columns**  

📄 [See Python Code (PDF)](https://drive.google.com/file/d/1K_wCub1eE6EHkVIU7qjzTXVN8TXEfmFG/view?usp=sharing)

---

## 8. Methodology & Tools

- **Python (pandas, seaborn, matplotlib)** for data cleaning and EDA  
- **Tableau** for interactive dashboards and visualization  
- Focused on descriptive analytics & comparative analysis

---

## 9. Visualizations & Dashboard Highlights

🔗 [View Full Dashboard on Tableau Public](https://public.tableau.com/views/AirBnBProject_17531229773270/Dashboard1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

### Dashboard Snapshot

Below is a snapshot of the Tableau dashboard:

![Airbnb Tableau Dashboard](https://raw.githubusercontent.com/annievu22/AirBnB_Project/main/AirBnB%20Project%20-%20Tableau%20Snapshot.png)

---

## 10. Final Conclusion

This project illustrates the power of combining data analytics and interactive visualization to derive meaningful insights from large-scale marketplace data. By cleaning and analyzing over 100,000 Airbnb listings in New York City, I was able to uncover valuable trends in pricing, room types, and geographic distribution that directly inform platform strategy and host decision-making.

Through Python, I built a structured pipeline for data preparation, ensuring accuracy and completeness. Tableau enabled me to transform raw data into a dynamic dashboard that supports real-time exploration, helping users compare boroughs, track seasonal changes, and understand host behavior patterns.

The insights gained can support Airbnb in multiple areas—from optimizing pricing algorithms to targeting underserved neighborhoods. This project not only demonstrates my ability to work with real-world messy data but also shows how to communicate findings effectively through data storytelling.

In the future, this dashboard could be enhanced by:
- Incorporating **time-based filters** to observe trends year-over-year
- Adding **sentiment analysis** from reviews to complement quantitative data
- Connecting **external datasets** such as tourism rates or COVID-19 restrictions for richer context

Overall, the Airbnb Data Analytics Project exemplifies how analytical thinking, technical tools, and visualization techniques can come together to support data-driven decisions in platform-based business models.

