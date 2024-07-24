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

![Snap_1](https://user-images.githubusercontent.com/102996550/174089602-ab834a6b-62ce-4b62-8922-a1d241ec240e.jpg)

        
- Step 15 : New measure was created to find total count of customers.

Following DAX expression was written for the same,
        
        Count of Customers = COUNT(airline_passenger_satisfaction[ID])
        
A card visual was used to represent count of customers.

![Snap_Count](https://user-images.githubusercontent.com/102996550/174090154-424dc1a4-3ff7-41f8-9617-17a2fb205825.jpg)

        
 - Step 16 : New measure was created to find  % of customers,
 
 Following DAX expression was written to find % of customers,
 
         % Customers = (DIVIDE(airline_passenger_satisfaction[Count of Customers], 129880)*100)
 
 A card visual was used to represent this perecntage.
 
 Snap of % of customers who preferred business class
 
 ![Snap_Percentage](https://user-images.githubusercontent.com/102996550/174090653-da02feb4-4775-4a95-affb-a211ca985d07.jpg)

 
 - Step 17 : New measure was created to calculate total distance travelled by flights & a card visual was used to represent total distance.
 
 Following DAX expression was written to find total distance,
 
         Total Distance Travelled = SUM(airline_passenger_satisfaction[Flight Distance])
    
 A card visual was used to represent this total distance.
 
 
 ![Snap_3](https://user-images.githubusercontent.com/102996550/174091618-bf770d6c-34c6-44d4-9f5e-49583a6d5f68.jpg)
 
 - Step 18 : The report was then published to Power BI Service.
 
 
![Publish_Message](https://user-images.githubusercontent.com/102996550/174094520-3a845196-97e6-4d44-8760-34a64abc3e77.jpg)

# Snapshot of Dashboard (Power BI Service)

![dashboard_snapo](https://user-images.githubusercontent.com/102996550/174096257-11f1aae5-203d-44fc-bfca-25d37faf3237.jpg)

 
 # Report Snapshot (Power BI DESKTOP)

 
![Dashboard_upload](https://user-images.githubusercontent.com/102996550/174074051-4f08287a-0568-4fdf-8ac9-6762e0d8fa94.jpg)

# Insights

A single page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

### [1] Total Number of Customers = 129880

   Number of satisfied Customers (Male) = 28159 (21.68 %)

   Number of satisfied Customers (Female) = 28269 (21.76 %)

   Number of neutral/unsatisfied customers (Male) = 35822 (27.58 %)

   Number of neutral/unsatisfied customers (Female) = 37630 (28.97 %)


           thus, higher number of customers are neutral/unsatisfied.
           
### [2] Average Ratings

    a) Baggage Handling - 3.63/5
    b) Check-in Service - 3.31/5
    c) Cleanliness - 3.29/5
    d) Ease of online booking - 2.88/5
    e) Food & Drink - 3.21/5
    f) In-flight Entertainment - 3.36/5
    g) In-flight service - 3.64/5
    h) In-flight Wifi service - 2.81/5
    i) Leg room service - 3.37/5
    j) On-board service - 3.38/5
    k) Online boarding - 3.33/5
    l) Seat comfort - 3.44/5
    m) Departure & arrival convenience - 3.22/5
  
  while calculating average rating, null values have been ignored as they were not relevant for some customers. 
  
  These ratings will change if different visual filters will be applied.  
  
  ### [3] Average Delay 
  
      a) Average delay in arrival(minutes) - 15.09
      b) Average delay in departure(minutes) - 14.71
Average delay will change if different visual filters will be applied.

 ### [4] Some other insights
 
 ### Class
 
 1.1) 47.87 % customers travelled by Business class.
 
 1.2) 44.89 % customers travelled by Economy class.
 
 1.3) 7.25 % customers travelled by Economy plus class.
 
         thus, maximum customers travelled by Business class.
 
 ### Age Group
 
 2.1)  21.69 % customers belong to '0-25' age group.
 
 2.2)  52.44 % customers belong to '25-50' age group.
 
 2.3)  25.57 % customers belong to '50-75' age group.
 
 2.4)  0.31 % customers belong to '75-100' age group.
 
         thus, maximum customers belong to '25-50' age group.
         
### Customer Type

3.1) 18.31 % customers have customer type 'First time'.

3.2) 81.69 % customers have customer type 'returning'.
       
       thus, more customers have customer type 'returning'.

### Type of travel

4.1) 69.06 % customers have travel type 'Business'.

4.2) 30.94 % customers have travel type 'Personal'.

        thus, more customers have travel type 'Business'.


