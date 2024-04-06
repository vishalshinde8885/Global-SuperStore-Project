
# Global SuperStore - Dashboard

### Dashboard Link : https://app.powerbi.com/view?r=eyJrIjoiNDY5YjFjMTQtYTUxZS00NmFjLTk0NGYtMDVmOGVlOTc0NjVmIiwidCI6ImRmODY3OWNkLWE4MGUtNDVkOC05OWFjLWM4M2VkN2ZmOTVhMCJ9

## Problem Statement

This dashboard helps the Global SuperStore to understand their Sales, Orders, Products and Customers better. It helps the Superstore to know 
if their Sales and profit are going in better way or not.
Through different sales and quantity sold, they get to know their improvement area, & thus they can improve their sales by identifying these area.
It also lets them know the ship mode with duration time & regions to get less profit, thus since by using this dashboard they have identified this problem.



### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
---
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
---
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
---
- Step 4 : It was observed that in none of the columns errors & empty values were present except column named "Postal Code".
---
- Step 5 : 
- We don't required the postal code, for that we removed the postal code column.
- Added new custom column for calculating the 
     cost based on sales and profit.
- Added new columns for year,Day, Dayname,Day, of week, start of year, start of month, start of week.
---
- Step 6 :
- we select close and apply and the changes were made in dataset.
- The Model View the relationship is created based on the primary and foreign key from the table.

---
- Step 7 :
- In table view, added a new column to calculate delievered duration using the dax function,
        
        Delivered Duration = 
         DATEDIFF('Orders'[Order Date], 'Orders'[Ship Date], DAY)

---
- Step 8 : 
- In Report view started to build the visuals with introduction page for global superstore dataset.

---
- Step 9 :

- To show the KPI's(Key Performance Indicator), six card visuals are added to the canvas.
- Following Cards Visual are added calculated using DAX functions,

        Total Revenue = 
        SUMX(
        orders,
        Orders[Sales]
        )

-
        Total Profit = sumx(
        Orders,Orders[Profit])

-        Total Orders = DISTINCTCOUNT(Orders[Order ID])

-        Return Rate = DIVIDE([QuantityReturned],[Quantity Sold],"No Sales")

-        Quantity Sold = SUM(Orders[Quantity])

-        QuantityReturned = SUM(Returns[Return Quantity])

![KPI](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/96c07b25-dbfb-410c-a502-def9a6be0f0b)

---
- Step 10 : 
- A line chart was also added to the report design area representing the Revenue trending over the year, here used drill up and down to show the quarter, month and week wise revenue.
- added the page navigation button to goes on the particular report pages.
![image](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/fed04bcd-dbe3-491b-8900-ccf5c5325cc6)
- the reset button is added to show the KPI's and graph to the original set position.

- here, in line chart ,Total Revenue trended up, resulting in a 90.31% increase between Sunday, January 1, 2012 and Thursday, January 1, 2015.

![Revenue Trending](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/f2f68abb-2b98-49bd-a9a4-d1bb0a87f735)

----
 
- Step 11 : 
- Added the clustered bar chart to show order by category,
![Orders By Category](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/fdf51e24-52cb-4d83-9564-59392c7d06f1)

- added the category tooltip to show the total revenue, total orders, total profit, QuantityReturned,return rate.

![Table Top Orders](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/8bdd546f-b43b-44f9-9dd4-8c1b8bc92957)


- Step 12 : Map Visual Added to show the countries in which the orders placed.
- Added filter on the visual to select the top 10 countries by total orders.
- added slicer on this map page to select any particular country.

![Map](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/e5f79129-a08c-4ff7-9739-a8ca0179a6a0)

---
- Step 13 : In the Product details page in report view, select the one product to find out the details about that product.
- here, add Cisco Smart Phone, Full Size.
- here we added Numerical Parameter to adjust the price range between -0.1 to 0.1 in (%).
- added the line chart to see the difference between the total profit and adjusted profit over the year.
- calculated Adjusted Profit using Dax for that we added following measures,
        
        Total Cost = SUMX(Orders,Orders[Cost]+Orders[Shipping Cost])
 
-        Adjusted Revenue = 
        SUMX(
        'Orders',
        Orders[Quantity]*
        [Adjusted Price]
        )

-       Adjusted Profit = [Adjusted Revenue]-[Total Cost]

- Added product metric selection field Parameter
  for the measures like total profit, total      orders,total returns,return rate,total revenue.
- Based on this field Parameter added line chart to show this measure at one time by year to calculate the Parameters.


![Product details](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/916c171e-e1af-448e-b736-e32e4c5ad076)


---

- Step 14 : Added new page in report view to show the sales performance,
- first the line and stacked column chart is added to find the top 5 region by total sales.
- Added pie chart for find out the percentage of total sales by category.
- Added ribbon chart to find the sum of sales by year and region wise.

![Sales1](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/8d21079b-5956-4ed5-b419-345dd70ca4b6)

on next page..
--> Added the Line and clustered column chart
- here we got the top % product based on total sales.

![sales 2](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/bdd43a22-c0bc-4c94-85b1-a14ed51b02b9)

---
- Step 15 :Added new page for Customer Analysis
- There are total 17K Unique Customers, showed using card.
        ![Unique customer](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/90b1e6fb-5549-4cef-a577-bce069c9f2e0)

- The Average revenue per customer is 725.95.
      ![average](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/5881566a-6374-407d-8a3c-126c5a4ddf95)
- Added Donut chart to find out the percentage and exact number of customers by country.
![Donut](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/6243eefe-e39d-4cbb-b013-b5e23f66f172)

- Added slicer for year.
-  Added line chart for field parameter such as total customer and revenue per customer by year.
![rev](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/d6eb7ee8-45ba-40b7-847b-f694c0d9bf7d)

---
- Step 16 : On other page of customer analysis,
-Added Bar chart, found out the total customers by segment.

![tcA](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/51d74823-06ce-47a5-a0a7-4c05a74aa53b)

-Added card visual , Sean Mealer is the top customer by revenue having orders 2 and revenue 23.67K. 

![top c](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/ae19dddc-5f14-4003-91c7-b16002a7dfc7)


![OR](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/135a9018-ceac-436c-af45-8ab597d1fee1)

- added stacked bar chart to calculate the total customer by ship mode and segment.

![TC by SM](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/a87fe1f0-8ec6-42a1-af86-9a46f5eabbba)

- Added a table to find the list of top 100 customers by orders. added visual level filter on this table.
![top c table](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/fdbaa1da-7706-429b-b6ea-5b50f3a9769f)

- Added the information button to show the top customer in segment at year 2015.

![info](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/d4cb9733-7378-46b3-a393-e4c818ff7eaf)


---
- Step 17 : Added new Page for Ship Mode Analysis
 - In this, Added stacked bar chart to represent the data of total profit by ship mode nad segment.
 ![SM](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/9bd04b95-8706-40d6-afac-7f5c474e9464)

 - the clustered column chart represent the data of minimum delievered duration by ship mode.
 
![Min delievered](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/c67d2a4f-8aa2-4b96-b9ab-47b2c99891a4)
 -  stacked column chart represent minimum shipping cost by ship mode and segment.
 ![image](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/c7d23348-56bb-4d3a-bdd5-05f195c22167)

 - table represent the same region,same product,same market, same ship mode, to find out the shipping cost, order priority, Quantity.


![image](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/7853ab0a-3f89-44a6-a26d-773826463d84)


---
- Step 18 - Added new page for order analysis
 - Added Ribbon Chart to represent the count of order id by year and region.
 - Added Line and stacked chart to represent the data of Maximum duaration by order priority.

 
![image](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/85ac6c13-66cc-4857-81a3-55c6fad6b38c)


 
---

- Step 19 : The report was then published to Power BI Service.
 
 
![published Image](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/47c6fbd2-48a7-4f89-aac7-2f6f7be5071a)


# Snapshot of Dashboard (Power BI Service)

![Dashboard_Power bi service](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/52e3108c-ac14-4193-89ea-3ea53d9961d5)


 
 # Report Snapshot (Power BI DESKTOP)

![Dashboard_Desktop](https://github.com/vishalshinde8885/Global-SuperStore-Project/assets/166035565/80c9fb61-0832-4a40-ab24-8f3863b46a22)





# Insights


A report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

### [1] Key Performance Indicator:

- Total Revenue trended up, resulting in a 90.31% increase between Sunday, January 1, 2012 and Thursday, January 1, 2015.

- Total Revenue started trending up on Sunday, January 1, 2012, rising by 90.31% (2,040,414.98) in 3 years.

- Total Revenue jumped from 2,259,450.90 to 4,299,865.87 during its steepest incline between Sunday, January 1, 2012 and Thursday, January 1, 2015.
           
### [2] Total orders and top product: 

- At 19,464, Office Supplies had the highest Total Orders and was 136.73% higher than Furniture, which had the lowest Total Orders at 8,222.
- Office Supplies had the highest Total Orders at 19,464, followed by Technology at 8,428 and Furniture at 8,222.
- Office Supplies had 19,464 Total Orders, Furniture had 8,222, and Technology had 8,428.

- The most ordered product among all categories is Binder.
- and the most returned product among all categories is label.
- the top 1 orders placed product is staples having around 222 orders.


  
  ### [3] Product Details
  
- Adjusted Profit (459.89% increase) and Total Profit (486.43% increase) both trended up between 2012 and 2015.
- Across all metrics, Adjusted Profit had the most interesting recent trend and started trending up on 2012, rising by 459.89% (8,471.79) in 3 years.
- Adjusted Profit jumped from 1,842.13 to 10,313.92 during its steepest incline between 2012 and 2015.
- Total Orders experienced the longest period of growth (+11) between 2012 and 2015.

 ### [4] Sales Performance
- At 1,731,929.67, Western Europe had the highest Total Sales and was 99.86% higher than Southern Asia, which had the lowest Total Sales at 866,572.68.
- Western Europe accounted for 29.83% of Total Sales.
- Across all 5 Region, Total Sales ranged from 866,572.68 to 1,731,929.67.
- 2015 in Region Western Europe made up 6.47% of Sum of Sales.

 ### [5] Customer Analysis Page 1:
 
- Revenue per customer trended up, resulting in a 90.31% increase between 2012 and 2015.
- Revenue per customer started trending up on 2012, rising by 90.31% (2,040,414.98) in 3 years.
- Revenue per customer jumped from 2,259,450.90 to 4,299,865.87 during its steepest incline between 2012 and 2015.
- Total Customers was highest for United States at 2501, followed by France and Mexico.
 
### [6] Customer Analysis Page 2: 

- At 8987, Consumer had the highest Total Customers and was 180.23% higher than Home Office, which had the lowest Total Customers at 3207.
- Consumer had the highest Total Customers at 8987, followed by Corporate at 5221 and Home Office at 3207.
- Corporate had 5221 Total Customers, Consumer had 8987, and Home Office had 3207.
- Standard Class in Segment Consumer made up 28.57% of Total Customers.
- Consumer had the highest average Total Customers at 2785, followed by Corporate at 1,612.50 and Home Office at 994.50. 

### [7] Ship Mode Analysis:


 - Standard Class had the highest total Sum of Profit at 890,596.02, followed by Second Class, First Class, and Same Day.
 - Consumer in Ship Mode Standard Class made up 30.70% of Sum of Profit.
 - Standard Class had the highest average Sum of Profit at 296,865.34, followed by Second Class, First Class, and Same Day.
 - At 4, Standard Class had the highest Min of Delivered Duration and was Infinity higher than Same Day, which had the lowest Min of Delivered Duration at 0.
 - Standard Class had the highest Min of Delivered Duration at 4, followed by Second Class, First Class, and Same Day.
 - Across all 4 Ship Mode, Min of Delivered Duration ranged from 0 to 4.

 ### Order Analysis: 

 - Medium and Low tied for highest Max of Delivered Duration at 7.
 - Across all 4 Order Priority, Max of Delivered Duration ranged from 3 to 7.
 - 2015 in Region Western Europe made up 9.78% of Count of Order ID.
