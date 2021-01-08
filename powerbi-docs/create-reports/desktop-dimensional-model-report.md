---
title: "Tutorial: From dimensional model to stunning report in Power BI Desktop"
description: Add a page filter, visualization filter, or report filter to a report in Power BI
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 01/07/2021
LocalizationGroup: Reports
---
# Tutorial: From dimensional model to stunning report in Power BI Desktop 

In this tutorial, you start with a dimensional model and build a beautiful report from start to finish in 20 minutes.

You work at AdventureWorks and your manager wants to see a report on your latest sales figures. They have requested an executive summary of: 

- Which day had the most sales in February 2019? 
- Which country is the company seeing the most success in? 
- Which product category and reseller business types should the company continue to invest in? 

Using our sample AdventureWorks sales workbook (link to workbook), we can build this report in no time. Here’s what the final report will look like. 

Graphical user interface, application

Description automatically generated

Let’s get started! 

In this tutorial, you'll learn how to: 

- Download sample data two different ways 
- Prepare your data with a few transformations 
- Build a report with a title, three visuals, and a slicer 
- Publish your report to the Power BI service so you can share it with your colleagues 

## Prerequisites 

- Before you start, you need to [download Power BI Desktop](../fundamentals/desktop-get-the-desktop.md). 
- If you're planning to publish your report to the Power BI service and you aren't signed up yet, [sign up for a free trial](../fundamentals/service-self-service-signup-for-power-bi.md). 

## Get data: Download the sample 

1. Download the AdventureWorks Sales sample Excel workbook from ____. 

1. Open Power BI Desktop. 

1. In the **Data** section of the **Home** ribbon, select **Excel**. 

1. Navigate to where you saved the sample workbook, and select **Open**. 

## Prepare your data 

In the Navigator pane, you have the option to *transform* or *load* the data. The Navigator provides a preview of your data so you can verify that you have the correct range of data. Numeric data types are italicized. In this tutorial, we're going to transform the data before loading.

Select all tables, and choose **Transform Data**. Make sure not to select the sheets (labeled *_data*). 

Graphical user interface, table

Description automatically generated 

Check that the data types of the columns match those in the following table. To make any changes, select a query, then select one or more columns. On the **Home** tab, select **Data Type**, then select the appropriate data type from the table. 

Graphical user interface, application, table, Excel

Description automatically generated 

|Query  |Column  |Data type  |
|---------|---------|---------|
|Customer  |  CustomerKey | Whole Number |
|Date | DateKey |    Whole Number     |
|     | Date | Date      |
|     | MonthKey  | Whole Number |
|Product  | ProductKey | Whole Number  | 
|     | Standard Cost | Decimal Number  | 
|     | List Price | Decimal Number  | 
|Reseller  | ResellerKey | Whole Number  | 
|Sales   | SalesOrderLineKey | Whole Number  | 
|     | ResellerKey  | Whole Number  | 
|     | CustomerKey | Whole Number  | 
|     | ProductKey  | Whole Number  | 
|     | OrderDateKey | Whole Number  | 
|     | DueDateKey  | Whole Number  | 
|     | ShipDateKey | Whole Number  | 
|     | SalesTerritoryKey | Whole Number  | 
|     | Order Quantity   | Whole Number  | 
|     | Unit Price  | Decimal Number  | 
|     | Extended Amount  | Decimal Number  | 
|     | Unit Price Discount Pct | Percentage  | 
|     | Product Standard Cost | Decimal Number  | 
|     | Total Product Cost | Decimal Number  | 
|     | Sales Amount | Decimal Number  | 
| SalesTerritory  | SalesTerritoryKey | Whole Number  | 
|  SalesOrder   |  SalesOrderLineKey | Whole Number  | 

Back on the **Home** tab, select **Close & Apply**. 

Graphical user interface, application, table, Word

Description automatically generated 

## Model your data 

The data you loaded is almost ready for reporting. Let’s inspect the data model and make some changes. 

Select **Model View** on the left. 

Screenshot of Model View icon. 

You see your data model. It should look like the following image, with boxes for each table. 

Graphical user interface, application

Description automatically generated 

 

This model is a typical star schema as you might see from data warehouses: It resembles a star. The center of the star is a Fact table and the surrounding tables are called Dimension tables, which are related to the Fact table with relationships. The Fact table contains numerical information about sales transactions, such as Sales Amount and Product Standard Cost. The Dimensions provide context so you can, among other things, analyze: 

- what Product was sold 
- to which Customer 
- by which Reseller 
- in which Sales Territory  

If you look closely, you notice that all Dimension tables are related to the Fact with a Relationship, except for the Date table. Let’s add some relationships to Date now. Drag the DateKey from the Date table to OrderDateKey on the Sales table. You've created a so-called "one-to-many" relationship from Date to Sales, as indicated by the **1** and the asterisk ***** (many) at the two ends of the line.  

The relationship is "one-to-many" because we have one or more Sales orders for a given Date. If we had a maximum of one Sales order for each date, the relationship would be "one-to-one". The little arrow in the middle of the line indicates the "cross-filtering direction." It indicates that you can use values from the Date table to filter the Sales table, so the relationship allows you to analyze when a Sales order was placed.  

Graphical user interface, text, application

Description automatically generated 

The Sales table contains more information about dates related to Sales orders, such as Due Date and Ship Date. Let’s add two more relationships to the Date table by dragging: 

- DateKey to DueDateKey 
- DateKey to ShipDateKey 
    
Graphical user interface, application

Description automatically generated 

You notice that the first relationship, on OrderDateKey, is active, shown by the continuous line. The other two are inactive, shown by the dashed line. Power BI uses the active relationship by default to relate Sales and Date. Hence, a sum of SalesAmount is calculated by Order Date, not Due Date or Ship Date. You can influence this behavior. See later in this tutorial. 

The typical star schema contains several keys that hold the relationships between Facts and Dimensions. Normally we don't want to use any key columns in our reports. Let’s hide the key columns from view, so the Fields List shows fewer fields, and the data model is easier to use. 

Go over all tables and hide any column whose name ends with *Key*: 

Select the **Eye** icon next to the column and choose **Hide in report view**.

You can also select the **Eye** icon next to the column in the Properties pane.

 

Hidden fields have this icon, an eye with a line through it. 

 
Hide these fields.

|Table  |Column  |
|---------|---------|
|Customer  | CustomerKey |
|Date     | DateKey |
|     | MonthKey |
|Product     | ProductKey  |
|Reseller   | ResellerKey  |
|Sales     | CustomerKey  |
|     | DueDateKey |
|     | OrderDateKey |
|     | ProductKey |
|     | ResellerKey        |
|     | SalesOrderLineKey        |
|     | SalesTerritoryKey        |
|     | ShipDateKey        |
| SalesOrder    | SalesOrderLineKey |
| SalesTerritory  | SalesTerritoryKey |
|     |         |
|     |         |
|     |         |


Your data model should now look like this data model, with relationships between Sales and all the other tables, and all the key fields hidden: 

Graphical user interface, application

Description automatically generated 

Now that our data model is easier to consume because of the hidden columns, we can add a couple of *hierarchies* to make the model even easier to use. Hierarchies enable easier navigation of groupings. For example, cities are in a State or Province, which is in a Country or Region. 

Create the following hierarchies. Right-click the highest level, or the least granular, field in the hierarchy and choose **Create hierarchy**. In the Properties pane, set the Name of the hierarchy and set the levels. Then **Apply Level Changes**. 

Graphical user interface, text, application

Description automatically generated 

You can also use the Properties pane to rename levels in a hierarchy after you added them as you need to do for the Year and Quarter level of the Fiscal hierarchy in the Date table. 

 

TABLE 

HIERARCHY NAME 

LEVELS 

CUSTOMER 

Geography 

Country-Region 

State-Province 

City 

Postal Code 

Customer 

DATE 

Fiscal 

Year (Fiscal Year) 

Quarter (Fiscal Quarter) 

Month 

Date 

PRODUCT 

Products 

Category 

Subcategory 

Model 

Product 

RESELLER 

Geography 

Country-Region 

State-Province 

City 

Postal Code 

Reseller 

SALESORDER 

Sales Orders 

Sales Order 

Sales Order Line 

SALESTERRITORY 

Sales Territories 

Group 

Country 

Region 

 

Your data model should now look like this: 

 

Graphical user interface, application

Description automatically generated 

To finish up our modeling, lets rename the following tables using the Properties pane: 

OLD TABLE NAME 

NEW TABLE NAME 

SALESTERRITORY 

Sales Territory 

SALESORDER 

Sales Order 

 

Your final data model should look like this: 

Graphical user interface, application

Description automatically generated 

Extra credit: Write a measure in DAX 

Writing measures in the DAX formula language is super powerful for data modeling. There's lots to learn about DAX in the Power BI documentation. For now, let's write a basic measure that calculates the total sales amount by due date on the sales order instead of the default order date. 

Select Data View on the left. 

Graphical user interface, application, Word

Description automatically generated 

Select the Sales table in the Fields list: 

Graphical user interface, application

Description automatically generated 

On the Home ribbon, select New Measure. 

Type this measure to calculate the total sales amount by due date on the sales order instead of the default order date: 
Sales Amount by Due Date = CALCULATE(SUM(Sales[Sales Amount]), USERELATIONSHIP(Sales[DueDateKey],'Date'[DateKey]))  

Select the check mark to commit: 

 

Build your report 

Now that you’ve modeled your data, it is time to create your report. Go to the Report View and in the Fields pane on the right, you see the fields in the data model you created. 

Let’s build the final report, one visual at a time. 

 

Visual 1: Add a title 

On the Insert ribbon, select Text Box. Type "Executive Summary – Sales Report". 

Select the text you typed. Set the font size to 20 and bold. 

Graphical user interface, text, application, Word

Description automatically generated 

In the Visualizations pane, toggle the Background to Off. 

Resize the box to fit on one line. 

Visual 2: Sales Amount by Date 

Now, you create a line chart to see which month and year had the highest Sales Amount. 

From the Fields pane, drag the Sales Amount field from the Sales table to a blank area on the report canvas. By default, Power BI displays a column chart with one column, Sales Amount. 

Drag the Month field from the Fiscal hierarchy in the Date table and drop it on the column chart: 

Chart, bar chart

Description automatically generated 

In the Fields section of the Visualizations pane, remove the Year and Quarter: 

 

 

In the Visualizations pane, change the visualization type to Area Chart. 

Graphical user interface, application, Word

Description automatically generated 

If you added the DAX measure in the extra credit above, add it to Values as well. Open the Format pane, open Data colors and change the color of Sales Amount by Due Date to more contrasting color such as red: 

Graphical user interface, application

Description automatically generated 

As you can see here Sales Amount by Due Date trails slightly behind the Sales Amount, which proofs that it uses the relationship between Sales and Date that uses DueDateKey. 

 

Visual 3: Order Quantity by Reseller Country 

Create a map to see Resellers in which Country have the highest Order Quantity Amount. 

From the Fields pane, drag the Country-Region field from the Reseller table to a blank area on your report canvas to create a map. 

Drag the Order Quantity from the Sales table and drop it on the map. Make sure Country-Region is in the Location well and Order Quantity in the Size well. 
Graphical user interface, application

Description automatically generated 

Visual 4: Sales Amount by Product Category and Reseller Business type 

Create a column chart to investigate which products are sold by what type of reseller business. 

Drag the two charts you've created to be side by side in the top half of the canvas. Save some room on the left side of the canvas. 

Select a blank area in the lower half of your report canvas. 

In the Fields pane, select Sales Amount from Sales, Product Category from Product and Business Type from Reseller. 

Power BI automatically creates a clustered column chart. Change the visualization to a Matrix: 

 Graphical user interface, application

Description automatically generated 

With the matrix still selected, filter out Business Type [Not Applicable] by setting the following Filter: 

Graphical user interface, text, application

Description automatically generated 

Drag the matrix so it's wide enough to fill the space under the two upper charts. 

A picture containing graphical user interface

Description automatically generated 

In the formatting pane for the matrix, open the Conditional formatting section and turn the Data bars on. Select Advanced controls and set a lighter color for the positive bar. Click OK. 

Increase the width of the Sales Amount column so it covers the whole area: 

A picture containing application

Description automatically generated 

It looks like Bikes have a higher Sales Amount overall and the Value Added Resellers sell the most, closely followed by Warehouses. For Components, the Warehouses sell more than the Value Added Resellers. 

 

Visual 5: Fiscal calendar slicer 

Slicers are a valuable tool for filtering the visuals on a report page to a specific selection. In this case, we can create a slicer to narrow in on performance for each month, quarter and year. 

In the Fields pane, select the Fiscal hierarchy from the Date table and drag it to the blank area on the left of the canvas. 

In the Visualizations pane, choose Slicer. 

Graphical user interface, application

Description automatically generated 

In the Fields section of the Visualizations pane, remove Quarter and Date so only Year and Month are left. 
 

Now if your manager asks to see data only for a specific month, you can use the slicer to switch between years or specific months each year. 

Extra credit: Format the report 

If you want to do some light formatting on this report to add more polish, here are a few easy steps. 

Theme 

On the View ribbon, change the theme to Executive. 

Graphical user interface

Description automatically generated 

Spruce up the visuals 

Make the following changes on the Format tab in the Visualizations pane. 

Screenshot of the Format tab in the Visualizations pane. 

Select Visual 2 (Sales Amount by Date). In the Title section, change Title text to "Sales Amount by Order Date" if you did not add the DAX measure. If you did, change Title text to "Sales Amount by Order Date / Due Date". Set Text size to 16 pt. Toggle Shadow to On. 

Select Visual 3 (Order Quantity by Reseller Country). In the Map styles section, change Theme to Grayscale. In the Title section, change Title text to "Order Quantity by Reseller Country" and Text size to 16 pt. Toggle Shadow to On. 

Select Visual 4 (Sales Amount by Product Category and Reseller Business Type). In the Title section, change Title text to "Sales Amount by Product Category and Reseller Business Type" and change title Text size to 16 pt. Toggle Shadow to On. 

Select Visual 5 (Fiscal calendar slicer). In the Selection controls section, toggle Show "Select all" option to On. In the Slicer header section, increase Text size to 16 pt. 

Add a background shape for the title 

On the Insert ribbon, select Shapes > Rectangle. Place it at the top of the page, and stretch it to be the width of the page and height of the title. 

In the Format shape pane, in the Line section, change Transparency to 100%. 

In the Fill section, change Fill color to Theme color 5 #6B91C9 (blue). 

On the Format tab, select Send backward > Send to back. 

Select the text in Visual 1, the title, and change the font color to White. 

Finished report 

Select "FY2019" in the slicer. 

Here's how your final polished report will look: 

Graphical user interface, application

Description automatically generated 

In summary, this report answers your manager’s top questions: 

Which day had the most sales in February 2019? 

25th of February with a sales amount of $253,915.47 

Which country is the company seeing the most success in? 

In the United States, with an order quantity of 132748. 

Which product category and reseller business types should the company continue to invest in? 

The company should continue to invest in the Bikes category and the Value Added Reseller and Warehouse reseller business. 

Save your report 

On the File menu, select Save. 

 

Publish to the Power BI service to share 

To share your report with your manager and colleagues, publish it to the Power BI service. When you share with colleagues that have a Power BI account, they can interact with your report, but can’t save changes. 

In Power BI Desktop, select Publish on the Home ribbon. 
You may need to sign in to the Power BI service. If you don't have an account yet, you can sign up for a free trial. 

Select a destination such as My workspace in the Power BI service > Select. 

Select Open 'your-file-name' in Power BI. Your completed report opens in the browser. 

Select Share at the top of the report to share your report with others. 

Next steps 

Learn more about DAX and data modeling in Power BI Desktop. 


## Next steps

More questions? [Try the Power BI Community](https://community.powerbi.com/)
