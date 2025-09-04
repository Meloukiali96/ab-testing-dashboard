# A/B Testing Dashboard | Power BI
![Dashboard Screenshot](ab_testing%20screenshot.jpg)
## 📌 Project Overview
This project analyzes the results of an A/B test comparing **Ads vs PSAs**.  
The goal was to measure which campaign performed better in terms of **conversion rates** and overall effectiveness.  
The project demonstrates skills in **Power BI, DAX, and data storytelling**.

---

Tools & Skills
- Power BI for data modeling and dashboard design
- DAX for calculated measures (Conversion Rates, Lift, Overall CR)
- Data storytelling to highlight insights for business stakeholders 

---

Dashboard Highlights
- **Overall Conversion Rate:** ~2.5% across all users  
- **Ad Group Conversion Rate:** 2.55%  
- **PSA Group Conversion Rate:** 1.79%  
- **Lift:** Ads outperformed PSAs by ~42%  
- **Insights over time:** Conversions were stronger at the start of the week  

---

Key Insights
- Ads generated **96% of all conversions** in the experiment.  
- PSAs underperformed and would need redesign or replacement.  
- Ad campaigns could be optimized further by testing creatives or targeting weaker days (midweek).  

---

Files in this Repo
- `ab_test_data.csv` → Dataset used for the analysis  
- `AB_Testing_Dashboard.pbix` → Power BI dashboard file  
- `ab_testing screenshot.jpg` → Dashboard screenshot 

---

Core DAX Measures

```DAX
Total Users = DISTINCTCOUNT(Fact[UserID])
Total Conversions = CALCULATE(DISTINCTCOUNT(Fact[UserID]), Fact[Converted] = 1)

Conversion Rate = DIVIDE([Total Conversions], [Total Users])

Ad Conversion Rate = CALCULATE([Conversion Rate], Fact[test_group] = "ad")
PSA Conversion Rate = CALCULATE([Conversion Rate], Fact[test_group] = "psa")

Lift = DIVIDE([Ad Conversion Rate] - [PSA Conversion Rate], [PSA Conversion Rate])


