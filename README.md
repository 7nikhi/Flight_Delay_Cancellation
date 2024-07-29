# Flight Delay and Cancellation

### Report Link : https://app.powerbi.com/groups/me/reports/6009cbf9-c0fc-4eeb-83f0-29280ef3473b/c4a1fe2eecf613e770a5?experience=power-bi

## Problem Statement

This report helps users understand flight delays and cancellations better. It allows the users to select the best airline and airport from the report with fewer delays & cancellations. It also lets them know the average delay & departure time, with the insights gained from this report, users can choose airlines and airports that minimize departure and arrival delays by addressing the underlying factors causing these issues.

Since, the percentage of arrival delay (almost 36.5 %) of total flights & percentage of departure delay (around 37 %), thus in all they must work on improving their services. 

Also since the average arrival delay is approximately 5 minutes & departure is approximately 10 minutes, thus they must try to reduce it.


### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : During the ETL process for Flights, Airlines, and Airports data, we identified issues such as incomplete records, null values, and irrelevant information. To ensure the data is ready for analysis and reporting, we performed transformations using Power Query Editor. This optimization ensures that our data is clean, complete, and structured for effective analysis and reporting purposes.
- Step 5 : In the model view of Power BI, we have established both active and inactive relationships between the Flights table and the Airline/Airport tables. This setup enables us to utilize measures with these inactive relationships as well. This approach provides flexibility in data analysis, allowing us to apply different perspectives and filters to our calculations as needed, thereby optimizing our ability to derive insights
- Step 6 : To calculate metrics such as average arrival delay time, average departure delay time, total flights, number of arrival delays, number of departure delays, percentage of arrival delays, percentage of departure delays, and cancellation rate, we excluded null values from the "Arrival Delay" column, "Departure Delay" column as these represent less than 1% of the total data. This ensures our analysis is based on complete and reliable information for accurate insights.
- Step 7 : In the report view, under the view tab, theme was selected.
- Step 8 : The new visualizations added using the three ellipses in the report view provide users with enhanced insights into various metrics related to airlines and airports. These visuals are designed to facilitate a deeper understanding of the data, enabling users to analyze key performance indicators such as arrival and departure delays, cancellation rates, total flights, and percentages of delays. By leveraging these visuals, users can make informed decisions based on comprehensive and visually represented data, leading to more effective strategies and actions.
- Step 9 : Visual filters (Slicers) were added for four fields named "Country", "State", "City", "Airline" & "Airport".
- Step 10 : Six card visuals have been added to the canvas, each highlighting crucial metrics for airlines and airports:

           Total Flights: Shows the total number of flights recorded.
           
           Average Departure Delay (Minutes): Displays the average delay in minutes for departures.
           
           Average Arrival Delay (Minutes): Indicates the average delay in minutes for arrivals.
           
           Percentage of Arrival Delay: Represents the percentage of flights that experience arrival delays.
           
           Percentage of Departure Delay: Shows the percentage of flights that experience departure delays.
           
           Cancellation Rate: Displays the rate of flight cancellations as a percentage of total flights scheduled.

           These card visuals provide a quick snapshot of key performance indicators, allowing users to swiftly assess performance, identify trends, and make data-driven decisions to improve operational efficiency and passenger satisfaction.
           
- Step 10 : I have created bar charts, line charts, funnel charts, donut charts and map to visually represent our dataset in the report.
- Step 11 : In our dataset, certain parameters such as "diverted" and "cancelled" are represented with values of 0 and 1. A value of 1 indicates that the flight was cancelled or diverted, while a value of 0 indicates that it was not.
- Step 12 : In the report view, under the "Insert" tab, a text box has been added to the canvas with the report title "Flight Delay & Cancellation Report". Additionally, an image related to flight delays and cancellations has been inserted to visually enhance the report.
- Step 13 : For better navigation between report pages, a page navigator has been added.
- Step 14 : A hierarchy was created with levels for Country → State → City, and another hierarchy for Year → Month → Day.
- Step 15 : New measure was created to find total flights.

Following DAX expression was written for the same,
        
        Total Flights = COUNTROWS(flights)
        
 A card visual was used to represent count of flights.

 ![Total Flights](https://github.com/user-attachments/assets/d43238e0-83b6-4c34-8129-201bf2ba7542)

        
 - Step 16 : New measure was created to find Average Arrival Delay.
 
 Following DAX expression was written to find Avg Arrival Delay,
 
         Avg Arrival Delay = AVERAGE(flights[ARRIVAL_DELAY])
 
 A card visual was used to represent Average Arrival Delay.
 
 ![Avg Arrival Dealy](https://github.com/user-attachments/assets/e5a36ce8-2ef0-47e2-9db4-41838cc501ed)

 
 - Step 17 : New measure was created to find Average Departure Delay.
 
 Following DAX expression was written to find Avg Departure Delay,
 
         Avg Departure Delay = AVERAGE(flights[DEPARTURE_DELAY])
         
 A card visual was used to represent Average Departure Delay.
 
 ![Avg Departure Delay](https://github.com/user-attachments/assets/7fe021d9-75cc-43ee-aeb0-519d0e1a980d)


  - Step 18 : New measure was created to find Percentage of Arrival Delay.
 
 Following DAX expression was written to find No. of Arrival Delay,
 
         No. of Arrival Delay = COUNTROWS(FILTER(flights, flights[ARRIVAL_DELAY] > 0))

 Following DAX expression was written to find Percentage of Arrival Delay,
 
         Percentage of Arrival Delay = CALCULATE([No. of Arrival Delay]/[Total Flights])
         
 A card visual was used to represent Percentage of Arrival Delay.
 
 ![Percentage of arrival delay](https://github.com/user-attachments/assets/fc5723a0-9ce1-4af7-a44b-9bda06b3b7e4)


  - Step 19 : New measure was created to find Percentage of Departure Delay.
 
 Following DAX expression was written to find No. of Departure Delay,
 
         No. of Departure Delay = COUNTROWS(FILTER(flights, flights[DEPARTURE_DELAY] > 0))

 Following DAX expression was written to find Percentage of Departure Delay,
 
         Percentage of Departure Delay = CALCULATE([No. of Departure Delay]/[Total Flights])
         
 A card visual was used to represent Percentage of Departure Delay.
 
 ![Percentage of departure delay](https://github.com/user-attachments/assets/a267fea4-4d4a-4c5a-881d-2e01d5b6b90f)

 
   - Step 20 : New measure was created to find Cancellation Rate.
 
 Following DAX expression was written to find Cancellation Rate,
 
         Cancellation Rate = DIVIDE(CALCULATE(COUNTROWS(flights), flights[CANCELLED] = 1), COUNTROWS(flights))
         
 A card visual was used to represent Cancellation Rate.
 
 ![Cancellation Rate](https://github.com/user-attachments/assets/376c9529-7dd5-40ff-a5da-7fd14e5af18c)
 
 - Step 21 : The report was then published to Power BI Service.
 
 
![Publish to power bi](https://github.com/user-attachments/assets/d005c08f-4a69-4e5f-b007-e275a8a26013)

# Snapshot of Dashboard (Power BI Service)

![Airline Power BI Service](https://github.com/user-attachments/assets/9eb34657-e317-4324-8213-17deeb0b1a60)

 
 # Report Snapshot (Power BI DESKTOP)

![Airline Power BI Desktop](https://github.com/user-attachments/assets/78795a5d-16cc-401c-a6b8-27b972c79189)

# Insights

A report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the report;

### [1]   Total Number of Flights = 5000000

### [2]   6 Airline have Departure Delay more than Average Departure Delay.

### [3]   7 Airline have Arrival Delay more than Average Arrival Delay.

### [4]   172 Airport have Departure Delay more than Average Departure Delay.

### [5]   170 Airport have Arrival Delay more than Average Arrival Delay.

### [6]   Spirit Air lines has highest average Departure Delay which is 16.70.

### [7]   Spirit Air lines has also highest average Arrival Delay which is 15.23.

### [8]   Washington Airport has highest average Departure Delay which is 29.39.

### [9]   Washington Airport has also highest average Arrival Delay which is 24.06. 
  
### [10] Average Delay
  
      a) Average delay in arrival(minutes) - 4.89
      b) Average delay in departure(minutes) - 9.78
Average delay will change if different visual filters will be applied.

 ### [11] Percentage Delay
  
      a) Percentage of Arrival Delay is 36.6%
      b) Percentage of Departure Delay is 37.2%
       
 ### [12] Cancellation Rate

      Cancellation rate is 1.4% of all flights.
 
# Snapshot of Report 

           Delay
           
           ![Airline Delay](https://github.com/user-attachments/assets/34a44597-ad68-4a70-8dcf-43b808b36d4b)

           Cancellation

           ![Airline Cancellation](https://github.com/user-attachments/assets/4e4627ab-ffeb-4f5d-9a51-689a10274c1f)

           Delay/Cancellation using Map

           ![Airline Delay_Cancellation](https://github.com/user-attachments/assets/64b8e584-fce1-44bd-94d9-b969b7e0b558)


