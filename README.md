# Coffee-Sales-Analysis

![my coffee pic](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/8f384897-5be8-4416-9121-c0dc92dcb189)

## Introduction

This project aims is to dive into coffee sales data to uncover valuable insights into sales performance over time, broken down by country, and to identify our top customers. I will be using Excel for cleaning, transforming, and visualizing the data to bring these insights to life.

## Problem Statement

The coffee sales company is grappling with understanding how well it's doing in sales across different aspects like time, location, and customer types. The data is scattered across different places, which makes it hard to find useful insights. Because of this, the company can't figure out important sales trends, which products are doing the best, or who their most valuable customers are. This lack of clarity is making it tough for the company to make smart choices, improve their marketing plans, and grow their sales. The main goal here is to gather and analyze all the coffee sales data so they can uncover these insights and start making decisions based on solid information.

## Data Source

The dataset for this analysis was obtained from a YouTube channel and is available on GitHub [HERE](https://github.com/mochen862/excel-project-coffee-sales/blob/main/coffeeOrdersData.xlsx). It includes three main tables:
- Order Table: Contains details about each order, including Order ID,	Order Date,	Customer ID,	Product ID, and	Quantity.
- Customer Table: Contains customer information such as Customer ID,	Customer Name,	Email,	Phone Number,	Address Line 1,	City,	Country, Postcode, and	Loyalty Card.
- Product Table: Contains product details including Product ID,	Coffee Type,	Roast Type,	Size,	Unit Price,	Price per 100g,	Profit

## Data Preparation

### Customer Data Integration

1. **Customer Name:** We will use the XLOOKUP function to retrieve customer names from the customer table and populate them into the order table.

   ![customer old](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/7511eeca-7689-4b5d-b5aa-24dacd5fc0b6)

```excel
=XLOOKUP(C2,customers!$A$1:$A$1001,customers!$B$1:$B$1001,,0)
```

![customer name](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/569d0563-d7a0-4729-b091-b0014c070717)


2. **Email:** Using XLOOKUP to retrieve customer emails from customer table and populate them into order table, ensuring that any missing values result in a blank cell if no email is found.

    ![email 1](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/8e66e2ee-a122-481f-a1c1-f3c57f9fefd2)

```excel
=XLOOKUP(C2, customers!$A$1:$A$1001,customers!$C$1:$C$1001,,0)
```

![email 2](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/2309bf8d-7c7e-4eb6-b1d2-60d82eb84b52) 

3. **Country:** Using XLOOKUP function to retrieve customer country information from customer table to order table

     ![country !](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/3efccea0-4414-456a-b97e-7398194b5f1b)

```excel
=XLOOKUP(C2, customers!$A$1:$A$1001,customers!$G$1:$G$1001,,0)
```

![country 2](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/011b1300-58f4-4d56-8ed3-985aa3e5247b)


### Product Data Integration

Using INDEX MATCH to integrate product details such as coffee type, roast type, size, and unit price from product table  into the order table.

![index match 1](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/a5c35f47-f364-4ad4-af00-38bb289388ca)

```excel
=INDEX(products!$A$1:$G$49,MATCH(orders!$D2,products!$A$1:$A$49,0),MATCH(orders!I$1,products!$A$1:$G$1,0))
```

![index match 2](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/720d715f-604a-4798-bb43-7805a7b23321)

### Sales Calculation

Calculating the sales value by multiplying the unit price by the quantity.

![sales 1](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/6bbdc9c9-aabb-448d-ac7a-a6237c027f3e)

```excel
=unit price * quantity [ =L2*E2 ]
```

![sales 2](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/2ac40d3c-2b37-4f34-be90-f301d93f79e5)


## Data Formatting

**Coffee Type Name:** Add a new column to represent the full name of the coffee type. Use the IF function statement to convert abbreviations in the coffee type column into their corresponding full names in this new column.

![coffee type 1](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/1fbcaa57-8b7f-4453-b9d7-3d10c4fb5fff)

```excel
=IF(I2="Rob","Robusta",IF(I2="Exc","Excelsa",IF(I2="Ara","Arabica",IF(I2="Lib","Liberica",""))))
```

![coffee type 2](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/4ac8ccf0-26b2-4584-865e-8a00d60ad44d)


**Roast Type Name:** Add a new column to display the full name of the roast type. Use the IF function to replace abbreviations from the roast type column with their corresponding full names in this new column.

![roast type 1](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/84dfd3cf-ebf2-48c3-b704-7b06e6a69db3)


```excel
=IF(J2="M","Medium",IF(J2="L","Light",IF(J2="D","Dark","")))
```

![roast type 2](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/397fc672-e683-43a7-ab86-f074500744a3)


**Order Date:** Now, format the order date column by changing the month to its abbreviation. To do this, press Ctrl+1 to open the Format Cells dialog box, then select "Custom" format and enter dd-mmm-yyyy to display the date in day-month abbreviation-year format.

![order date 1](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/f3eeb55b-4ff9-4d43-9c6b-d0fb3ff0f699)

![1_AtG-LLT_F3XozwjgAdilLg](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/4fa496f9-741f-44cc-82bb-2af5d1f37062)

![order date 2](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/d829a19e-6163-40d1-9ed2-e9a019bc7443)


**Size Column:** let's format the size column by adding 'kg' to each value. Press Ctrl+1 to open the Format Cells dialog box, select "Custom" format, enter 0.0 "kg", and then click OK.

![size](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/0903e232-0fca-48fb-b548-a3923faf14a1)


**Unit Price and Sales Column:** let's format the unit price and sales columns by adding a dollar sign ($) before each value.

![sales and unit price](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/94a30f2c-9451-4372-a54e-3e18e43ae737)


## Duplicate Removal

Removing duplicates using Excel’s built-in functionality
To check and remove duplicates, go to the "Data" tab and click on "Remove Duplicates" in the menu.


## Data Analysis

### Total Sales Over Time

We’ll start with a line graph that highlights the total sales of four coffee types—Arabica, Excelsa, Liberica, and Robusta—over the years 2019 to 2022. To make the data exploration more interactive, we'll add slicers for dates, roast type, size, and loyalty card preference. This way, you can easily filter and analyze the data to uncover hidden patterns and trends.

**Create a Pivot Table:**

- Insert a pivot table to analyze total coffee sales over time.

**Set Up the Pivot Table:**

- Drag the Order Date from the PivotTable Field list to the Rows area.
- Right-click on any cell in the Order Date column, select Group, and choose to group by Months and Years.
- Click on the Design tab, then select Report Layout and choose Show in Tabular Form. Disable both Grand Totals and Subtotals.

**Configure the Pivot Table Fields:**

Drag Coffee Type Name from the PivotTable Field list to the Columns area.
Drag Sales to the Values area.

**Format the Sales Values:**

- Click on the Sales values in the pivot table, then select Value Field Settings.
- Click on Number Format, choose Number, set No Decimal Places, and enable the 1000 Separator.

  ![over time](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/ade5799f-4d41-42c0-b086-a169d7d811f5)

**Insert a Line Chart:**

- Insert a line chart to visualize the data.
- Right-click on the field buttons in the chart and select Hide All.
  
- Format the Chart:

- Double-click on the chart to open the formatting options.
- Select Solid Fill and choose your preferred colors.
- Add a chart title: Total Sales Over Time.
- Label the vertical axis

![over time chart](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/80a6bd76-3854-4ed9-be72-3fa2566dbf5f)


### Creating and Formatting a Timeline with our chart

To help visualize our coffee sales data, we’ll create an interactive timeline chart. This will allow us to filter the data by time periods and customize the look of the timeline.

- Click on the PivotChart to select it.
- Go to the PivotChart Analyze tab.
- Click on Insert Timeline
- A dialog box will appear. Choose the order date field that we want to use for our timeline and click OK.
- Customize the Timeline Style:such as font color, size, and style to make your timeline more visually appealing and easier to read.

  ![timeline chart](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/71e0cc24-a59f-49b4-853b-50fc9ce7dbc4)


  ### Adding and Customizing Slicers with our chart

  This will create interactive slicers for our chart, allowing us to filter the data by size, loyalty card, and roast type, all with a custom, well-designed style.

  ![slicer chart](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/6a6cc0ba-27ff-4811-a2ce-19ee128f91c0)


  ### Total Sales by Country

  Next, let's create a bar chart that highlights total coffee sales in three countries known for their love of coffee: the United States, Ireland, and the United Kingdom. This chart will show us a quick overview of how much coffee each country consumes.

  ![sales by country chart](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/87a56950-cf75-4c54-b634-a86a774d0705)


  ### Top 5 Customers by Sales

  A clear and visualIZE appealing bar chart that highlights the top 5 customers based on their coffee sales, with customized formatting for clarity and impact.

  ![TOP 5 CUSTOMER](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/6dfa1859-0b10-4ba6-8a36-24a2e5d9ae01)



### Dashboard
The final dashboard includes interactive charts and slicers for dynamic data exploration. It comprises:

- Total sales over time (line chart)
- Sales by country (bar chart)
- Top 5 customers by sales (bar chart)
- Interactive timeline and slicers for filtering data

We'll create a well-organized and visualization appealing dashboard that integrates key charts and filters for analyzing coffee sales data effectively.

![Coffee Sales Dashboard](https://github.com/oluwaseuntaiwo/Coffee-Sales-Analysis/assets/145341799/c781beea-c057-4f72-9f89-c62f79829025)


## Conclusion

The coffee sales analysis project has given us valuable insights into many aspects of coffee sales performance. By merging customer and product data into the order table, we gained a better understanding of sales trends over time, regional sales distribution, and the preferences of our top customers. Visualizations like line charts and bar charts helped us interpret the data more effectively and spot important patterns. This analysis underscores how using data to guide decisions can strengthen business strategies and boost sales performance.




*Remember, data visualization isn’t just about charts and graphs; it’s about telling a story that leads to actionable insights. The interplay of different visualizations allows you to explore the data from various angles, uncovering trends and correlations.*
























  




















