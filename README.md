<p align="center">
  <img src="Cyclistic Bikeshare Analysis header.png" alt="Cyclistic Hero Banner" style="width:100%; height:auto;">
</p>

## <span style="color:#00838F;">📊 Executive Summary</span>
This project analyzes 12 months of historical trip data for **Cyclistic**, a fictional bike-share company in Chicago. The primary business objective is to understand how annual members and casual riders use bikes differently. The insights derived from this analysis directly inform a new marketing strategy designed to convert casual riders into high-value annual members.

## 🛠️ Data Pipeline & Methodology  
![Data Source](https://img.shields.io/badge/Data%20Source-Cyclistic%20Trips-00838F?style=for-the-badge&logo=googlemaps&logoColor=white)  
12 months of historical trip data (Sept 2025 – August 2026) provided by Motivate International Inc. under the [Divvy Data License Agreement](https://divvybikes.com/data-license-agreement).
* **Data Extraction & Staging:**
Staged monthly CSV files via Google Cloud Storage / Google Drive and imported them into **Google BigQuery**  

* **Data Transformation & Cleaning:** 
  * Combined 12 individual monthly tables using `UNION ALL` into a single master table (~millions of rows). 
  * Filtered out dirty data, including **35 duplicate ride IDs**, **29 impossible trip times** (where end time preceded start time), and **1 missing station records**.
  * Engineered new calculated columns: `ride_length_minutes`, `day_of_week`, `month`, and `year`.

*SQL cleaning and transformation scripts can be found in the `sql/` directory of this repository.*

## <span style="color:#F4D03F;">🚴‍♀️ Key Insights</span>  

### 1. Ride Duration: Casual Riders Take Longer Trips
* **Insight:** Casual riders average a significantly higher ride duration—nearly **9 minutes longer** than annual members.
* **Interpretation:** Annual members primarily use the bikes for point-to-point commuting (fast, direct, and efficient), whereas casual riders use them for leisure, recreation, and longer weekend outings.

### 2. Weekly Trends: Commuters vs. Weekend Explorers
* **Insight:** Member ride volume peaks mid-week (**Tuesday through Thursday**), reflecting standard work and school commuting patterns. Conversely, casual ridership spikes heavily from **Friday through Sunday**.
* **Interpretation:** The weekend surge confirms that casual users treat the service as an activity or weekend amenity rather than a daily utility.

### 3. Geographical Hotspots: Tourism vs. Transit Hubs
* **Insight:** Casual rides heavily cluster around iconic Chicago tourist and recreational landmarks, led by **Navy Pier** and **DuSable Lake Shore Drive**. Members cluster more evenly around residential and commercial transit hubs.
* **Interpretation:** Marketing teams can precisely target physical and digital ad spend where casual riders naturally congregate during peak leisure hours.

## 📈 Interactive Dashboard & Visualizations
You can explore the fully interactive Tableau dashboard containing these charts and regional breakdowns here:
👉 **[View Live Dashboard on Tableau Public](https://public.tableau.com/app/profile/YOUR_PROFILE/viz/YOUR_DASHBOARD)**

*(Insert a screenshot of your dashboard below once uploaded to your repository)*
![Dashboard Preview](assets/dashboard_preview.png)

## 💡 Strategic Recommendations
Based on the data-driven insights, the marketing department should execute the following initiatives:
1. **Geo-Targeted Digital Campaigns:** Deploy weekend-focused mobile ads around Navy Pier, Millennium Park, and Lake Shore Drive highlighting the financial breakdown of annual savings.
2. **In-App Threshold Prompts:** Introduce automated pop-up prompts in the app for casual riders whose trip duration exceeds a certain threshold, showing how much money they would have saved with an annual membership on that single ride.
3. **Summer/Weekend Pass Tiers:** Create a specialized promotional membership tier that bridges the gap for casual weekend riders, easing them into a long-term subscription model.

## 📁 Repository Structure
```text
├── sql/
│   ├── 01_combine_tables.sql
│   └── 02_clean_and_transform.sql
├── assets/
│   └── dashboard_preview.png
└── README.md
