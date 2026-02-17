# What-Ive-Fixed-On-My-Second-SQL-SSMS-Project.

At 14 years old, I successfully completed a full SQL data-cleaning project on an online_sales_dataset. I improved the dataset by fixing missing values, correcting inconsistent customer inputs, validating incorrect entries, and making the data safer for analysis.

1. Replacing Missing Values
I handled missing warehouse location values by replacing NULL with 0, ensuring empty locations wouldn’t cause problems in reports:
Used ISNULL() to convert missing values into '0'
2. Selecting the First Valid Value
To prevent missing discount values from affecting calculations, I used COALESCE() to automatically choose the first non-empty value:
Missing discounts default to 0
3. Fixing Customer Input Errors
Customers often enter extra spaces in their country names, so I cleaned these entries using:
TRIM() to remove unwanted whitespace
4. Counting Discounts Per Customer
I analyzed customer order behavior by counting discounts per customer:
Used COUNT() with GROUP BY CustomerID to group identical customers together
5. Adding Real-Time Timestamps
To support order tracking and timestamping, I retrieved the current system date using:
GETDATE()

6. Converting Shipping Costs Into Whole Numbers
To standardize shipping cost values, I converted decimals into integers:
CAST(ShippingCost AS int)
7. Checking Column Data Types
To avoid conversion and query errors, I inspected all column datatypes with:
INFORMATION_SCHEMA.COLUMNS
8. Measuring Time Since Orders Were Placed
I calculated how many days ago each customer placed an order using:
DATEDIFF(day, InvoiceDate, GETDATE())
9. Attempting Invoice Date Conversion
I attempted to convert InvoiceDate into a proper date datatype to improve compatibility with date functions:
ALTER TABLE ... ALTER COLUMN
(This attempt helped identify datatype limitations in the dataset.)
10. Finding the Last Day of Each Order Month
To support monthly analysis, I extracted the final day of the month for each invoice:
EOMONTH(InvoiceDate)
11. Validating Date Entries
To ensure invoice dates were legitimate and not random text, I used:
TRY_CONVERT(DATE, InvoiceDate)
12. Safely Converting Text to Numbers
To prevent crashes from invalid numeric data, I used safe conversion functions:
TRY_CAST(Quantity AS INT)
13. Detecting Invalid Numeric Value
I located rows where letters were mistakenly entered into numeric fields using:
ISNUMERIC(CustomerID) = 0
14. Standardizing Unit Prices
To simplify pricing analysis, I converted decimal unit prices into whole numbers:
CAST(UnitPrice AS int)
15. Preventing Divide-by-Zero Errors
To stop calculations from breaking, I safely handled division using:
NULLIF() to avoid dividing by zero
16. Formatting Dates for Readability
I converted invoice dates into a human-friendly format:
CONVERT(VARCHAR, InvoiceDate, 101) → MM/DD/YY
17. Standardizing Stock Codes
To ensure stock codes worked regardless of capitalization, I normalized them using:
UPPER(StockCode)
