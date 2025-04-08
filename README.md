# 🛡️ Food Hygiene Analysis Project

## 💡 Overview
This project analyzes food hygiene ratings across the United Kingdom using data provided by the **UK Food Standards Agency**. By leveraging **MongoDB** and **Python**, it identifies trends, explores hygiene practices, and provides meaningful insights for *Eat Safe, Love* magazine.

---

## 🛠️ Database Setup and Preparation
Before starting the analysis, the database was set up and refined for accuracy.

### Initial Setup
- Imported the dataset (`establishments.json`) into MongoDB:
  ```bash
  mongoimport --db uk_food --collection establishments --file establishments.json --jsonArray
  ```
- Verified the data load and connected to the MongoDB database using PyMongo.

### Database Updates
- **Added "Penang Flavours":** Included the new halal restaurant in Greenwich for analysis.
- **Updated Business Type ID:** Retrieved and assigned the correct `BusinessTypeID` for "Restaurant/Cafe/Canteen."
- **Removed Dover Establishments:** Deleted all entries within the Dover Local Authority as requested.
- **Normalized Data Types:** Converted latitude, longitude, and `RatingValue` fields to appropriate formats for analysis.

---

## 🔍 Analysis Highlights

### ✅ Establishments with Hygiene Score = 20
- **Query:** Establishments with a **Hygiene Score of 20**.
- **Number of Results:** 41
- **Insights:** Identified businesses with significant hygiene concerns for targeted improvement efforts.

---

### 🏙️ Establishments in London with RatingValue ≥ 4
- **Query:** Establishments in London with **RatingValue ≥ 4**.
- **Number of Results:** 33
- **Insights:** Focused on high-performing establishments within the **City of London Corporation**.

---

### 📍 Proximity Analysis: Top 5 Near Penang Flavours
- **Query:** Establishments within 0.01 degrees of `"Penang Flavours"` (Latitude: 51.490142, Longitude: 0.083840).
- **Sorting:** By **Hygiene Score** (ascending).
- **Number of Results:** 5
- **Insights:** Highlighted nearby businesses with excellent hygiene ratings.

| Business Name                     | Type                                  | Address                         | PostCode   | Hygiene Score | Structural Score | Confidence Score | Distance    |
|-----------------------------------|---------------------------------------|---------------------------------|------------|---------------|------------------|------------------|-------------|
| Volunteer                         | Pub/bar/nightclub                    | 130-132 Plumstead High Street  | SE18 1JQ   | 0             | 0                | 0                | 4646.97 m   |
| Plumstead Manor Nursery           | Caring Premises                      | Plumstead Manor School Old...  | SE18 1QG   | 0             | 0                | 5                | 4646.97 m   |
| Atlantic Fish Bar                 | Takeaway/sandwich shop               | 35 Lakedale Road               | SE18 1PR   | 0             | 0                | 5                | 4646.97 m   |
| Iceland                           | Retailers - supermarkets/hypermarkets| 144-146 Plumstead High Street  | SE18 1JQ   | 0             | 5                | 5                | 4646.94 m   |
| Howe and Co Fish and Chips - Van 17 | Mobile caterer                       | 107A Plumstead High Street     | SE18 1SE   | 0             | 0                | 0                | 4646.96 m   |

---

### 🧼 Local Authorities with Hygiene Score = 0
- **Query:** Local Authorities with establishments scoring **Hygiene = 0**.
- **Total Local Authorities:** 55
- **Top 3:**
  1. **Thanet:** 1130 establishments.
  2. **Greenwich:** 882 establishments.
  3. **Maidstone:** 713 establishments.

| Local Authority         | Count of Establishments with Hygiene Score = 0 |
|--------------------------|-----------------------------------------------|
| Thanet                  | 1130                                          |
| Greenwich               | 882                                           |
| Maidstone               | 713                                           |
| Newham                  | 711                                           |
| Swale                   | 686                                           |

---

## 🛠️ Technologies Used
- **MongoDB** 🐾: NoSQL database for data storage and querying.
- **PyMongo** 🐍: Python client for MongoDB operations.
- **Pandas** 📊: Data processing and visualization.
- **Jupyter Notebook** 📓: Interactive Python environment.

## References
UK Food Standards AgencyLinks to an external site. (2022). UK food hygiene rating data API. https://ratings.food.gov.uk/open-data/en-GBLinks to an external site.. Contains public sector information licensed under the Open Government Licence v3.0Links to an external site.
Accessed Sept 9, 2022 and Sept 12, 2022 with the establishment settings as follows: longitude=51.5072, latitude=-0.1276, maxdistancelimit=4567, pagesize=10000, sortoptionkey=distance, pagenumber=(1,2,3,4,5,6,7,8).

