<p align="center">
  <img src="Cyclistic Bikeshare Analysis header.png" alt="Cyclistic Hero Banner" style="width:100%; height:auto;">
</p>

## <span style="color:#00838F;">📊 Executive Summary</span>  
This project analyzes 12 months of historical trip data for **Cyclistic**, a fictional bike-share company in Chicago. The Director of Marketing, Lily Moreno, believes the company’s future success depends on maximizing the number of annual memberships. 

The primary business objective is to understand how annual members and casual riders use bikes differently. The insights derived from this analysis, backed by compelling data visualizations, directly inform a new marketing strategy designed to convert casual riders into high-value annual members.

---

## 1. ❓ Business Task  
**The Business Task:** Identify the key differences in riding behaviors between annual members and casual riders to inform a targeted digital marketing strategy.

**Guiding Questions:**
1. How do annual members and casual riders use Cyclistic bikes differently?
2. Why would casual riders buy Cyclistic annual memberships?
3. How can Cyclistic use digital media to influence casual riders to become members?

---

## 2. 🗂️ Data Sources  
![Data Source](https://img.shields.io/badge/Data%20Source-Cyclistic%20Trips-00838F?style=for-the-badge&logo=googlemaps&logoColor=white)  

**Data Location & Organization:**
* **Source:** 12 months of historical trip data (Sept 2025 – August 2026) located in the AWS bucket `divvy-tripdata`, provided by Motivate International Inc. under the [Divvy Data License Agreement](https://divvybikes.com/data-license-agreement).
* **Structure:** Organized by month in CSV files containing ride details, timestamps, and geographic coordinates.

**Data Credibility & Integrity (ROCCC):**
* **Reliable & Original:** Data is first-party, sourced directly from the operational database.
* **Comprehensive:** The timeframe is complete and current. 
* **Privacy:** Under the licensing agreement, personally identifiable information (PII) is secured. Pass purchases cannot be connected to credit card numbers.

---

## 3. 🛠️ Data Pipeline & Methodology  
**Data Extraction & Staging:**
Staged monthly CSV files via Google Cloud Storage / Google Drive and imported them into **Google BigQuery** to efficiently process millions of rows. 

**Data Transformation & Cleaning:** 
  * Combined 12 individual monthly tables using `UNION ALL` into a single master dataset. 
  * Filtered out dirty data, including **35 duplicate ride IDs**, **29 impossible trip times** (where end time preceded start time),       and **1  missing station record**.
  * Engineered new calculated columns: `ride_length_minutes`, `day_of_week`, `month`, and `year`.

*SQL cleaning and transformation scripts can be found in the `sql/` directory of this repository.*

---

## <span style="color:#F4D03F;">🚴‍♀️ Key Insights</span>  

### 1. Ride Duration: Casual Riders Take Longer Trips (Lollipop Chart)
* **Insight:** Casual riders average a significantly higher ride duration—nearly **9 minutes longer** than annual members.
* **Interpretation:** Annual members primarily use the bikes for point-to-point commuting (fast, direct, and efficient), whereas casual riders use them for leisure, recreation, and longer outings.
<img src="Avg Ride Length.jpg" alt="Avg Ride Length" width="600">

### 2. Weekly Trends: Commuters vs. Weekend Explorers (Bar Chart)
* **Insight:** Member ride volume peaks mid-week (**Tuesday through Thursday**), reflecting standard work and school commuting patterns. Conversely, casual ridership spikes heavily from **Friday through Sunday**.
* **Interpretation:** The weekend surge confirms that casual users treat the service as an activity or weekend amenity rather than a daily utility.
<img src="Rides by day of the week.png" alt="Rides by Day of Week" width="600">

### 3. Geographical Hotspots: Tourism vs. Transit Hubs (Geographic Map)
* **Insight:** Casual rides heavily cluster around iconic Chicago tourist and recreational landmarks, led by **Navy Pier** and **DuSable Lake Shore Drive**. Members cluster more evenly around residential and commercial transit hubs.
* **Interpretation:** Marketing teams can precisely target physical and digital ad spend where casual riders naturally congregate during peak leisure hours.
<img src="Top 20 Start Stations.png" alt="Top 20 Start Stations" width="600">

## 📈 Interactive Dashboard & Visualizations
You can explore the fully interactive Tableau dashboard containing these charts and regional breakdowns here:
👉 **[View Live Dashboard on Tableau Public](https://public.tableau.com/views/cyclisticdataanalysischarts/CyclisticBike-ShareMembervs_CasualUsageTrends?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)**

---

## 5. 💡 Strategic Recommendations  
Based on the data-driven insights, the marketing department should execute the following initiatives to convert casual riders:

1. **Geo-Targeted Digital Campaigns:** Deploy weekend-focused mobile ads around Navy Pier, Millennium Park, and Lake Shore Drive            highlighting the financial breakdown of annual savings.
2. **In-App Threshold Prompts:** Introduce automated pop-up prompts in the app for casual riders whose trip duration exceeds a certain      threshold, showing how much money, they would have saved with an annual membership on that single longer ride.
3. **Summer/Weekend Pass Tiers:** Create a specialized promotional membership tier that bridges the gap for casual weekend riders,          easing them into a long-term subscription model.

---

## 📁 Repository Structure
```text
├── sql/
│   ├── average ride length
│   ├── check for duplicates
│   ├── cleaning and transformation
│   ├── impossible trip times
|   ├── missing station data
│   └── union_all
└── README.md
