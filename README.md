# User-Engagement-Analysis-PowerBI

# **User Engagement Dashboard - Power BI Mini Project**  
**📊 A Complete Analysis Report**  

---

## **📌 Table of Contents**  
1. [Project Overview](#-project-overview)  
2. [Dataset Used](#-dataset-used)  
3. [Tools & Technologies](#-tools--technologies)  
4. [Workflow](#-workflow)  
5. [Key Metrics & DAX Formulas](#-key-metrics--dax-formulas)  
6. [Insights & Outcomes](#-insights--outcomes)  
7. [Dashboard Screenshots & Analysis](#-dashboard-screenshots--analysis)  
8. [Future Improvements](#-future-improvements)  

---

## **🚀 Project Overview**  
This project analyzes **user engagement** data to track:  
✔ **Daily Active Users (DAU)**  
✔ **Retention Rates**  
✔ **Device & Segment Trends**  
✔ **Geographical Performance**  

**Business Goal**: Improve user retention and engagement by identifying behavioral patterns.  

---

## **📂 Dataset Used**  
### **Source**: Custom-generated Excel file  
### **Table Name**: `users`  
### **Attributes (Columns)**  
| Column | Description | Data Type |
|--------|-------------|-----------|
| `user_id` | Unique user identifier | Text |
| `date` | Date of activity | Date |
| `login_count` | Number of logins per day | Integer |
| `time_spent_minutes` | Session duration | Integer |
| `pages_visited` | Pages viewed per session | Integer |
| `actions_taken` | Clicks/downloads | Integer |
| `user_segment` | Free, Premium, Trial | Text |
| `device_type` | Mobile, Desktop, Tablet | Text |
| `country` | User location | Text |

---

## **🛠 Tools & Technologies**  
- **Power BI Desktop** (Data modeling, DAX, visualizations)  
- **Excel** (Data generation)  

---

## **🔧 Workflow**  
### **1. Data Preparation**  
- Created a mock dataset in Excel with **1,000+ rows**.  
- Structured columns to reflect real-world user behavior.  

### **2. Power BI Implementation**  
1. **Data Import**: Loaded Excel into Power BI.  
2. **Data Cleaning**:  
   - Ensured `date` was in correct format.  
   - Removed duplicates (if any).  
3. **Data Modeling**:  
   - Created a **date table** for time intelligence.  
   - Established relationships (if multiple tables existed).  
4. **DAX Measures**: Added calculations (see below).  
5. **Visualizations**: Built interactive dashboards.  

---

## **📊 Key Metrics & DAX Formulas**  
### **1. Daily Active Users (DAU)**  
```dax
DAU = DISTINCTCOUNT(users[user_id])
```
- **Purpose**: Counts unique users per day.  

### **2. Retention Rate**  
```dax
Retention Rate = 
VAR TotalUsers = DISTINCTCOUNT(users[user_id])
VAR ReturningUsers = CALCULATE(
    DISTINCTCOUNT(users[user_id]),
    users[login_count] > 1
)
RETURN DIVIDE(ReturningUsers, TotalUsers, 0)
```
- **Purpose**: Measures % of users who returned.  

### **3. Avg Session Duration**  
```dax
Avg Session Time = AVERAGE(users[time_spent_minutes])
```
- **Purpose**: Tracks engagement depth.  

### **4. Total Logins**  
```dax
Total Logins = SUM(users[login_count])
```
- **Purpose**: Aggregates login activity.  

---

## **🔍 Insights & Outcomes**  
### **1. User Segmentation**  
- **Free users dominated (38%)**, followed by Trial (37%) and Premium (25%).  
- **Premium users** had **longer sessions** (157.95 avg logins vs. 132.72 for Free).  

### **2. Device Trends**  
- **Mobile** had the highest logins (~100+), likely due to convenience.  
- **Desktop** users showed higher retention (data suggests deeper engagement).  

### **3. Geographical Analysis**  
- **India** had the highest retention (22.79%), followed by Germany (22.65%).  
- **USA** showed moderate engagement (19.82%).  

### **4. Time-Based Patterns**  
- **Peak logins** occurred on **Day 3** (177.31 avg), dipping on Day 4 (125.54).  
- **Weekends** saw increased activity (Day 6-7).  

---

## **📸 Dashboard Screenshots & Analysis**  
![User engagement dashboard](https://github.com/user-attachments/assets/dd38f9d7-b60c-43d1-ace3-c1c6c92f2e50)
 

### **1. DAU by Segment (Pie Chart)**  
- Free: 38%  
- Trial: 37%  
- Premium: 25%  

### **2. Retention by Country**  
- **Top**: India (22.79%)  
- **Bottom**: UK (16.46%)  

### **3. Login Count by Device**  
- **Mobile**: 100+  
- **Tablet**: ~70  
- **Desktop**: ~65  

### **4. Summary Table**  
| User Segment | Day 1 | Day 7 | Total |  
|-------------|-------|-------|-------|  
| Free        | 250   | 145   | 132.72|  
| Premium     | 133   | 131   | 157.95|  
| Trial       | 112   | 175   | 146.42|  

---

## **🚀 Future Improvements**  
1. **Add SQL Integration**: Connect to a live database (e.g., PostgreSQL).  
2. **Advanced DAX**: Implement rolling averages (`DATESINPERIOD`).  
3. **Drill-Through Pages**: Let users click into specific segments.  
4. **User Journey Analysis**: Track paths from login → conversion.  

---
