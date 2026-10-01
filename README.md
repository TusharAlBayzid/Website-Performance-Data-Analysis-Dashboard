# 📊 Website Performance Data Analysis Dashboard

🚀 **Project Overview**  
This project is an end-to-end, interactive **Website Performance & Traffic Analytics Dashboard** developed in **Microsoft Power BI**. Using a real-world dataset of **3,182+ hourly web analytics records**, this project transforms raw, unstructured website traffic logs into actionable marketing and user-behavior insights. It empowers stakeholders and digital marketing teams to evaluate acquisition channels, monitor user retention, identify peak traffic hours, and optimize marketing ROI through dynamic visual storytelling.

---

## 🛠️ Technical Challenges & Solutions

During the data extraction, transformation, and loading (ETL) as well as the dashboard development phase, several real-world technical challenges were systematically resolved to ensure 100% data accuracy and a clean user interface:

**1. Unstructured Header Rows & Object Data Type Formatting**
*   **Problem:** The raw dataset contained metadata noise (`# ----`) in the primary header row, pushing the actual column names into the first data row. Consequently, all numerical metrics (`Users`, `Sessions`, `Engagement rate`) were misclassified as text/object strings.
*   **Solution:** Utilized **Power Query Editor** to promote the first valid row as headers (`Use First Row as Headers`), standardized verbose column names (e.g., renaming `Session primary channel group (Default channel group)` to `channel group`), and explicitly cast all quantitative columns into `Whole Number` and `Decimal Number` data types.

**2. Parsing Non-Standard Concatenated Timestamps (`YYYYMMDDHH`)**
*   **Problem:** The timestamp column (`Date + hour`) was stored as a 10-digit continuous integer/text string (e.g., `2024041623`), which Power BI could not natively recognize as a valid `Date/Time` hierarchy or separate into hourly buckets.
*   **Solution:** Extracted the last 2 characters in Power Query to engineer a dedicated **`Hour`** column (`0` to `23`) for hourly heatmap analysis. Next, engineered a custom `DateHour` column using a Power Query **M-Language `#datetime()` formula** (`Text.Start`, `Text.Middle`, and `Text.End`) to parse the year, month, day, and hour into a true `Date/Time` format.

**3. Feature Engineering for Non-Engaged Sessions**
*   **Problem:** The dataset provided `Sessions` and `Engaged sessions`, but lacked a direct metric to evaluate bounce/non-engaged traffic across marketing channels.
*   **Solution:** Created a custom calculated column in Power Query (`[Non-Engaged] = [Sessions] - [Engaged sessions]`), enabling direct side-by-side proportion analysis between engaged and unengaged user visits.

**4. Resolving Axis Scale Disparity & Visual Clutter in Time-Series Charts**
*   **Problem:** Plotting `Average of Sessions` (ranging from `20` to `120`) and `Average of Engagement rate` (ranging from `0.0` to `1.0`) on a single Y-axis caused the engagement rate line to flatten completely along the bottom axis. Furthermore, plotting 700+ hourly data points created severe visual noise.
*   **Solution:** Mapped `Average of Engagement rate` to a **Secondary Y-axis** and configured the **Date Hierarchy** with smooth line interpolation and zoom sliders, transforming a cluttered hourly chart into a clean, executive-ready trend comparison.

---

## 📈 Dashboard Pages & Visual Breakdown

This single-page, highly interactive dashboard contains **7 core analytical visuals**, seamlessly integrated for dynamic cross-filtering:

1.  **Total Users by Channel (Donut Chart):** Provides an immediate high-level snapshot of total user acquisition (**133K Total Users**) segmented by marketing channels. It highlights that **Organic Social (~48K users, 35.65%)** and **Direct (~30K users, 22.51%)** are the primary traffic drivers, whereas *Email* and *Organic Video* bring the lowest volume.
2.  **Average Engagement Time by Channel (Horizontal Bar Chart):** Evaluates content effectiveness by measuring how long users stay active per session (`Average` aggregation). Reveals a critical business insight: although **Organic Video (~180 sec)**, **Referral (~93 sec)**, and **Email (~73 sec)** bring fewer visitors, they retain user attention significantly longer than high-volume social channels.
3.  **Engagement Rate Distribution by Channel (Multi-Metric Column Chart):** Compares the **Median**, **Minimum**, and **Maximum** engagement rates across all traffic sources to illustrate data spread and consistency. **Referral (`~0.67` median)** and **Organic Search (`~0.60` median)** emerge as the most reliable, high-performing channels.
4.  **Traffic by Hour and Channel (Conditional Formatting Matrix / Heatmap):** A 24-hour (`0` to `23`) color-coded heatmap (`YlGnBu` gradient) pinpointing exact peak traffic windows. Identifies that **Organic Social** peaks at **Midnight (Hour 0 with 3,917 sessions)** and **7:00 PM – 8:00 PM (Hours 19–20)**, while **Referral** traffic peaks at **11:00 AM (Hour 11 with 1,790 sessions)**—vital for scheduling ad campaigns.
5.  **Engaged vs Non-Engaged Sessions (100% Stacked Smooth Area Chart):** Visualizes the ratio of meaningful interactions versus unengaged visits across channels. Highlights that while *Organic Social* and *Referral* maintain strong engagement ratios, the **Direct** channel suffers from a higher proportion of non-engaged sessions, signaling a need for landing-page optimization.
6.  **Sessions and Users Over Time (Dual-Series Line Chart):** Tracks hourly and daily fluctuations of total `Sessions` (blue) alongside unique `Users` (magenta) throughout April and May, pinpointing peak traffic surges between **April 16 and April 20**.
7.  **Engagement Rate vs Sessions Over Time (Dual-Axis Trend Chart):** Analyzes the correlation between traffic volume (`Average of Sessions`) and traffic quality (`Average of Engagement rate`) from April to May, demonstrating how overall engagement efficiency scales alongside monthly traffic growth.

---

## 📁 Repository Contents

*   `Website_Performance_Analysis_Project.pbix` : The fully functional Power BI dashboard containing the cleaned data model, custom Power Query steps, and interactive visuals.
*   `Website Data Analysis with Python.xlsx` : The raw dataset used for this project.
*   `Website Performance Data Analysis Dashboard.png` : A high-resolution image preview of the completed dashboard.
*   `Website Performance Data Analysis Dashboard.pdf` : A static PDF export of the complete report for quick executive review.

---

## 👨‍💻 Author

**Bayzid Mostak**<br>
*Data Analyst & Visualization Expert*

*   [LinkedIn] https://www.linkedin.com/in/bayzid-mostak-data-analyst/
*   [GitHub] https://github.com/TusharAlBayzid
*   Note: Download the `.pbix` file and open it in Power BI Desktop to experience the fully interactive cross-filtering capabilities of this dashboard.


