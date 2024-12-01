# OLA Data Analyst Project

# Problem Statement

This project involves analyzing ride data to uncover insights for optimizing operations at OLA. The goal is to:

    1. Minimize cancellations by customers and drivers.  

    2. Enhance order volumes during weekends and match days.

    3. Maintain a balanced booking value distribution and minimize incomplete rides.

    4. Provide actionable insights via SQL queries and Power BI dashboards.

The outcomes include identifying customer behavior patterns, cancellation reasons, and revenue distribution to drive data-informed decisions.


# Steps followed 

 ## Data Analysis with SQL
### 1) Data Preparation

- Verified booking details with conditions on ride statuses, values, and ratings.
- Filtered the dataset for key metrics like cancellations, ride distances, and payment methods.
### 2) SQL Queries for Analysis

- Calculated aggregates (e.g., average ride distance, cancellation counts).
- Retrieved detailed insights, such as reasons for incomplete rides and top customers by booking count.
### 3) Sample Queries

#### 1.Retrieve successful bookings:

      Create View Successful_Bookings As
      SELECT * FROM bookings
      WHERE Booking_Status = 'Success';
#### 2.Find the average ride distance for each vehicle type:

      Create View ride_distance_for_each_vehicle As
      SELECT Vehicle_Type, AVG(Ride_Distance)
      as avg_distance FROM bookings
      GROUP BY Vehicle_Type;
#### 3.Get total number of cancelled rides by customers:
        
      Create View cancelled_rides_by_customers As
      SELECT COUNT(*) FROM bookings
      WHERE Booking_Status = 'cancelled by Customer';

#### 4. List the top 5 customers who booked the highest number of rides:
    Create View Top_5_Customers As
    SELECT Customer_ID, COUNT(Booking_ID) as total_rides
    FROM bookings
    GROUP BY Customer_ID
    ORDER BY total_rides DESC LIMIT 5;
#### 5. Get the number of rides cancelled by drivers due to personal and car-related issues:
    Create View Rides_cancelled_by_Drivers_P_C_Issues As
    SELECT COUNT(*) FROM bookings
    WHERE cancelled_Rides_by_Driver = 'Personal & Car related issue';
#### 6. Find the maximum and minimum driver ratings for Prime Sedan bookings:
    Create View Max_Min_Driver_Rating As
    SELECT MAX(Driver_Ratings) as max_rating,
    MIN(Driver_Ratings) as min_rating
    FROM bookings WHERE Vehicle_Type = 'Prime Sedan';

#### 7. Retrieve all rides where payment was made using UPI:
    Create View UPI_Payment As
    SELECT * FROM bookings
    WHERE Payment_Method = 'UPI';
#### 8. Find the average customer rating per vehicle type:
    Create View AVG_Cust_Rating As
    SELECT Vehicle_Type, AVG(Customer_Rating) as avg_customer_rating
    FROM bookings
    GROUP BY Vehicle_Type;
#### 9. Calculate the total booking value of rides completed successfully:
    Create View total_successful_ride_value As
    SELECT SUM(Booking_Value) as total_successful_ride_value
    FROM bookings
    WHERE Booking_Status = 'Success';
#### 10. List all incomplete rides along with the reason:
    Create View Incomplete_Rides_Reason As
    SELECT Booking_ID, Incomplete_Rides_Reason
    FROM bookings
    WHERE Incomplete_Rides = 'Yes';
# Power BI Dashboard Creation

- ### Data Modeling

1.Loaded data into Power BI Desktop and prepared it using Power Query Editor.

2.Applied transformations, handled null values, and optimized for analysis.

- ###  Visualization

- #### Key Metrics

1.Ride Volume Over Time: A time-series line chart for daily/weekly ride trends.

2.Booking Status Breakdown: A pie chart showing success, cancellations, and incomplete rides.

- #### Performance Metrics

1.Revenue by Payment Method: Stacked bar chart for payment method contributions.

2.Customer and Driver Ratings: Scatter plots and averages by vehicle type.

-  ### Cancellation Insights

1.Bar charts highlighting reasons for customer and driver cancellations.

- ### Ride Patterns

1.Histograms for ride distances and booking values.

- ### Interactivity

1.Added slicers for filtering by vehicle type, payment method, and customer demographics.

2.Interactive visualizations to explore data across weekends, match days, and vehicle types.


# SQL Insights
- #### Successful Rides Drive Revenue:
 
     High success rates indicate operational efficiency, but customer and driver cancellations (Query 3, 5) highlight areas needing improvement, like vehicle availability or driver support.

- #### Ride Preferences by Vehicle Type: 
     Premium vehicles like Prime Sedan show higher ratings and longer distances (Query 2, 6, 8), while budget options need better service optimization.

- #### Top Customers Are Key:
   The top 5 customers (Query 4) significantly boost bookings, emphasizing the need for loyalty programs or personalized benefits.

- #### Digital Payment Dominance: 
  UPI payments (Query 7) are widely used, signaling a strong preference for seamless digital transactions.

- #### Cancellation Insights: 
  Personal and car-related driver cancellations (Query 5) underline the need for robust vehicle maintenance and driver backup plans.

- #### Revenue Opportunities: 
  Successful bookings (Query 9) are the backbone of earnings; increasing their share through incentives and improved processes can boost profitability.

- #### Ratings Reflect Quality:
  High driver and customer ratings for premium vehicles point to quality service (Query 6, 8), while lower ratings for budget options need attention.

- #### Incomplete Rides Analysis:
  Incomplete rides (Query 10) reveal actionable gaps like driver unavailability or communication failures.
           
# Snapshot of Power BI Report
## Key Visuals
#### 1.Revenue by Payment Method
- Highlights UPI and credit cards as the preferred modes.
#### 2.Ride Volume Trends
- Weekends and match days show peak ride volumes.
#### 3.Cancellation Reasons
- Customer issues: 45% due to changed plans.
- Driver issues: 60% due to vehicle unavailability.


## Snapshot of Dashboard OVERALL (Power BI)
![Screenshot (717)](https://github.com/user-attachments/assets/22590462-7f7f-4b87-99db-2c13ef635cda)
 ## Snapshot of Dashboard Vehicle Type (Power BI)
![Screenshot (719)](https://github.com/user-attachments/assets/5afe287c-8f97-4269-957d-fd7bc23f8ebd)

## Snapshot of Dashboard REVENUE (Power BI)

![Screenshot (720)](https://github.com/user-attachments/assets/c8ffb24c-dbf4-4468-86ef-d533a4eea313)

 
## Snapshot of Dashboard CANCELLATION (Power BI)

 
![Screenshot (721)](https://github.com/user-attachments/assets/c5f7e522-2975-499a-8837-941849abb0ad)


## Snapshot of Dashboard RATINGS (Power BI)

![Screenshot (723)](https://github.com/user-attachments/assets/7c6a8c67-c749-435a-9f87-07b0103ffd6c)

# Insights

Five page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

## 1. Overall
- #### Ride Volume Over Time:
  1. Ride volume shows periodic fluctuations, with a noticeable increase toward the end of the month.
  2. A steady trend in ride volume is observed, with fluctuations possibly linked to demand patterns, such as weekends or peak hours.

- #### Booking Status Breakdown:
  1. Successful bookings dominate at 62.17%, showing efficient operations.
  2. Driver cancellations (17.8%) outpace customer cancellations (10.06%), suggesting potential driver-related operational issues.
  3. "Driver Not Found" constitutes 9.96%, indicating a possible gap in driver availability during high-demand periods.
  
## 2. Vehicle Type
- ####  Top 5 Vehicle Types by Ride Distance:
The top-performing vehicle types account for the majority of long-distance rides, catering primarily to intercity or extended travel needs.

## 3. Revenue

- ####  Revenue by Payment Method:
  1. A clear distribution of revenue by payment (approx 70%-80%methods), such as UPI, Cash, or Credit Card, reveals customer preferences.

  2. Digital payment methods might dominate, reflecting growing adoption of cashless transactions.
- #### Top 5 Customers by Total Booking Value:
  
  A small percentage of customers (10%-15%) significantly contribute to overall revenue, suggesting the importance of retaining high-value users through loyalty programs.
- #### Ride Distance Distribution Per Day:
  Most rides fall within a specific distance range, while a few outliers suggest occasional long-distance rides.
### 4. Cancellation
- #### Cancelled Rides Reasons (Customer):
   - 40–50% of cancellations are due to "Change of Plans" or "Long Wait Times."
- #### Cancelled Rides Reasons (Drivers):
   - Drivers cite reasons like "Unreachable Locations" for 30–40% of cancellations.
### 5. Ratings
- Driver Ratings Distribution:
   
   Majority of drivers receive 4+ stars, while 5–10% fall below average, needing performance improvement.
- Customer Ratings:
  
   Average customer ratings remain consistently high (3.9 - 4.0 stars on average).
- Customer vs. Driver Ratings:
  
  A positive correlation exists between customer and driver ratings, reflecting mutually beneficial interactions.
