# Fleet-Performance-Dashboard
AI-powered Power BI dashboard for fleet performance &amp; delivery efficiency
# 🚚 Fleet Performance & Delivery Efficiency Dashboard

## 📌 Project Overview
This project demonstrates the use of **Power BI with AI-powered visuals** to analyze fleet performance for a logistics company.  
The dashboard provides insights into **on-time deliveries, fuel efficiency, and cost per kilometer**, enabling better decision-making for route optimization and fleet management.

---

## 📂 Dataset
Two tables were used:
- **Trip_Data**
  - Trip_ID, Vehicle_ID, Driver_ID, Origin, Destination, Distance_km, Fuel_Consumed_L, Delivery_Status, Delivery_Date, Fuel_Cost_Fixed, Estimated Delivery Time (hrs)
- **Vehicle_Master**
  - Vehicle_ID, Vehicle_Type, Capacity_kg, Maintenance_Cost

---

## 🔧 Data Preparation
- Missing fuel consumption values handled using **mean imputation**.  
- Created a **relationship** between `Trip_Data` and `Vehicle_Master` using `Vehicle_ID`.  
- Added calculated columns:
  - **Estimated Delivery Time (hrs)** = `Distance_km ÷ 40`  
  - **Fuel_Cost_Fixed** = 100  

---

## 📊 DAX Measures
1. **Fuel Efficiency**
   ```DAX
   Fuel_Efficiency =
   SUM(Trip_Data[Distance_km]) /
   SUM(Trip_Data[Fuel_Consumed_L])

2. **On-Time Delivery %**
   ```DAX
   OnTime_Delivery_Percent =
   DIVIDE(
      CALCULATE(
          COUNT(Trip_Data[Trip_ID]),
          Trip_Data[Delivery_Status] = "On-Time"
      ),
      COUNT(Trip_Data[Trip_ID])
   )
   
3. **Cost per km**
   ```DAX
   Cost_per_km =
   DIVIDE(
      SUMX(
          Trip_Data,
          Trip_Data[Fuel_Cost_Fixed] +
          RELATED(Vehicle_Master[Maintenance_Cost])
      ),
       SUM(Trip_Data[Distance_km])
   )

4. **Average Delivery Time**
   ```DAX
      Avg_Delivery_Time =
      AVERAGE(Trip_Data[Estimated Delivery Time (hrs)])

---

## 📈 Visualizations
- Line Chart → Fuel Efficiency trend by Delivery Date
- Bar Chart → On-Time Delivery % by Destination
- Pie Chart → Vehicle Type vs Average Maintenance Cost
- Cards → Avg. Delivery Time, Avg. Cost per km

---

## 🤖 AI-Powered Visuals
- Q&A Visual → “Average Cost per km by vehicle type?”
- Key Influencers → Delivery Status explained by Distance, Vehicle Type, Driver_ID
- Decomposition Tree → Cost per km explained by Vehicle Type, Maintenance Cost, Distance

---

## 🔑 Key Insights from the Dashboard
1. **Fuel Efficiency Trends**
     - The fleet achieved an average fuel efficiency of 11.52 km/L.
     - Efficiency varied across dates, showing opportunities to optimize routes and reduce fuel consumption.

2. **Delivery Performance**
     - Only 60% of deliveries were on-time, with certain destinations (like Pune and Bangalore) performing better than others.
     - Driver analysis revealed that Driver D03 was 1.83x more likely to deliver on time compared to others.

3. **Cost Analysis**
     - The average cost per km was ₹18.03, but vehicle type comparisons showed differences:
             Trucks: ₹21.58/km
             Vans: ₹18.89/km
             Mini-Trucks: ₹22.79/km
      - This highlights that Vans are the most cost-efficient option for deliveries.

---

## 📷 Dashboard Preview

<img width="1361" height="788" alt="image" src="https://github.com/user-attachments/assets/dadabefa-f5cb-4cfa-b6c7-7e84626441bd" />

## 👩‍💻 Author
Shareena Beevi  
Aspiring Data Analyst

#PowerBI #DataAnalytics #Logistics #Dashboard #AI
