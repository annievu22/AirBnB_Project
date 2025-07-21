# 📊 Airbnb Data Analytics Project

> A data-driven analysis of Airbnb listings in New York City to uncover key insights in pricing, room types, and neighborhood trends, with the goal of improving platform strategy and user satisfaction.

---

## 🔍 1. Overview

This project explores Airbnb’s listing data using Python and Tableau to deliver actionable business insights. The analysis focuses on room types, listing prices, neighborhood patterns, and customer engagement through reviews. It is motivated by Airbnb’s growing adoption of data and AI to enhance the customer experience, reduce host complaints, and optimize listing performance.

---

## 🎯 2. Business Objectives

- Analyze pricing dynamics and their relation to room types.
- Understand the geographic distribution of listings and reviews.
- Identify booking and review trends over time to support strategic decisions.
- Uncover potential improvement areas for host performance and user experience.

---

## 📂 3. Dataset Description

- **Source**: Airbnb Open Data  
- **Size**: 100,000+ rows, 26 columns  
- **Columns** include: `price`, `room type`, `neighbourhood group`, `reviews per month`, `last review`, `availability`, etc.

---

## 🧱 4. Data Schema

| Category              | Columns (examples)                                  |
|----------------------|------------------------------------------------------|
| Identification        | `id`, `host id`, `host name`, `host_identity_verified` |
| Location              | `neighbourhood`, `neighbourhood group`, `lat`, `long` |
| Listing Information   | `room type`, `price`, `minimum nights`, `availability 365` |
| Engagement Metrics    | `number of reviews`, `last review`, `reviews per month` |

---

## 🧹 5. Data Cleaning & Preparation (Python)

- Removed missing and duplicate records  
- Converted columns to correct data types (`price`, `last review`)  
- Filled NA values in key columns such as reviews and price  
- Dropped irrelevant columns: `license`, `house_rules`  
- Final cleaned dataset: **101,410 rows × 24 columns**  

📄 *See code in: `Air Bnb data analysis project.pdf`*

---

## 📌 6. Key Business Questions

- 📈 What is the distribution of listing prices?
- 🏠 How are different room types distributed?
- 📍 How are listings distributed across different neighborhoods?
- 💰 What is the relationship between price and room type?
- 🗓️ How has the number of reviews changed over time?

---

## 🧠 7. Methodology & Tools

- **Python (pandas, seaborn, matplotlib)** for data cleaning and EDA  
- **Tableau** for interactive dashboards and visualization  
- Focused on descriptive analytics & comparative analysis

---

## 📊 8. Visualizations & Dashboard Highlights (Tableau)

> 📷 *See screenshots in `/images/` folder or below:*

- **Distribution of Room Types**: Entire home/apt and private rooms dominate  
- **Neighborhood Trends**: Manhattan and Brooklyn account for over 80% of listings  
- **Price Heatmap**: Average prices vary slightly across boroughs  
- **Review Trends Over Time**: Sharp decline post-2020 likely due to pandemic  
- **Top Hosts Analysis**: Ranking by total reviews per neighborhood  

---

## 💡 9. Insights & Recommendations

- 🏙️ Focus marketing on Brooklyn & Manhattan where demand is highest  
- 💲 Encourage hosts with private/shared rooms to adopt dynamic pricing strategies  
- 📅 Seasonal spikes in bookings (May–July) can inform promotional timing  
- 🤖 Airbnb should continue leveraging AI to match users with listings based on past preferences and review behavior

---

## ✅ 10. Final Conclusion

This project demonstrates how combining Python-based EDA and Tableau dashboards can drive business understanding in the short-term rental market. The insights derived from the NYC dataset can inform pricing, product offerings, and platform strategies for Airbnb.

---

## 🛠️ 11. Tools & Technologies

| Tool       | Purpose                         |
|------------|---------------------------------|
| Python     | Data cleaning & analysis        |
| Pandas     | Data manipulation               |
| Seaborn    | Visualizations                  |
| Tableau    | Dashboards & storytelling       |
| GitHub     | Project version control         |

---

## 📁 12. Repository Structure

