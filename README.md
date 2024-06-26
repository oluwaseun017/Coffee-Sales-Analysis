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






















