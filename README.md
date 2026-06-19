# Part 1: Business Data Cleaning, Validation & Excel Reporting

## Project Overview

This project focuses on cleaning, validating, and preparing retail sales order data for business reporting and analysis. The raw dataset contained missing values, duplicate records, inconsistent text formatting, mixed date formats, discount-related issues, and business rule violations. The objective was to create a clean and analysis-ready dataset while documenting all data quality issues and cleaning decisions.

---

## Dataset Description

The dataset contains order-level retail sales information including:

* Order details
* Customer information
* Product categories
* Regional information
* Shipping information
* Sales and profit data
* Payment and order status details

The raw dataset was provided in Excel format and cleaned using Microsoft Excel.

---

## Tools Used

* Microsoft Excel
* Pivot Tables
* Excel Functions (TRIM, PROPER, IF, YEAR, MONTH, etc.)
* Conditional Formatting
* Data Validation Techniques

---

## Data Cleaning Activities Performed

### Text Standardization

The following fields were reviewed and standardized:

* customer_name
* segment
* region
* state
* city
* category
* sub_category
* ship_mode
* payment_status
* order_status

Actions performed:

* Removed extra spaces.
* Corrected capitalization inconsistencies.
* Standardized category names.
* Standardized sub-category names.
* Standardized ship mode values.
* Improved consistency across all reporting fields.

---

### Missing Value Handling

| Field     | Action Taken                           |
| --------- | -------------------------------------- |
| Region    | Missing values replaced with "Unknown" |
| Ship Mode | Missing values replaced with "Unknown" |
| Discount  | Missing values replaced with 0         |

---

### Date Standardization

Actions performed:

* Reviewed order_date and ship_date fields.
* Standardized all dates to DD/MM/YYYY format.
* Created shipping_delay_days column.
* Created order_month column.
* Created order_year column.
* Identified and flagged invalid shipping records.

---

### Duplicate Handling

Actions performed:

* Identified exact duplicate records.
* Removed duplicate rows after validation.
* Flagged duplicate Order IDs for business review.

---

### Discount Validation

Actions performed:

* Replaced missing discount values with 0.
* Converted percentage-based discount values into decimal format.
* Flagged negative discount values as invalid.

---

## Business Rules Applied

* Missing Region values were replaced with "Unknown".
* Missing Ship Mode values were replaced with "Unknown".
* Missing Discount values were replaced with 0 when valid.
* Negative discounts were flagged as invalid.
* Ship dates earlier than order dates were flagged as invalid shipping records.
* Cancelled orders were excluded from completed sales reporting.
* Failed payment records were excluded from completed sales reporting.
* Refunded orders were reported separately for review.

---

## Data Quality Summary

| Issue                           | Count |
| ------------------------------- | ----- |
| Original Records                | 934   |
| Final Cleaned Records           | 913   |
| Exact Duplicate Records Removed | 21    |
| Missing Region Values Fixed     | 26    |
| Missing Ship Mode Values Fixed  | 22    |
| Missing Discount Values Fixed   | 18    |
| Invalid Discount Records        | 16    |
| Duplicate Order ID Occurrences  | 63    |
| Invalid Shipping Records        | 93    |

---

## Calculated Columns Created

The following calculated fields were added:

* cleaned_discount
* calculated_sales
* calculated_profit
* profit_margin
* shipping_delay_days
* order_month
* order_year
* data_quality_flag

---

## Pivot Analysis Performed

The following business reports were created using Pivot Tables:

### 1. Sales and Profit by Region

Analysis of total sales and profit generated across regions.

### 2. Sales and Profit by Category and Sub-Category

Comparison of sales and profitability across product categories.

### 3. Order Count by Ship Mode

Distribution of orders by shipping method.

### 4. Profit Margin by Customer Segment

Comparison of average profit margin across customer segments.

### 5. Order Status Analysis by Region

Review of cancelled, refunded, and completed orders by region.

### 6. Monthly Sales Trend

Analysis of sales performance across months.

---

## Key Business Insights

* South region generated the highest sales among all regions.
* Technology and Furniture categories contributed significantly to revenue.
* Small Business customers achieved the highest average profit margin.
* Several records contained invalid shipping dates and required review.
* Data quality improvements increased consistency and reporting reliability.

---

## Assumptions

* Missing Region values were treated as Unknown.
* Missing Ship Mode values were treated as Unknown.
* Missing Discount values were treated as 0 when other sales fields were valid.
* Duplicate Order IDs may represent valid business transactions and were retained for review.

---

## Limitations

* Duplicate Order IDs require further business validation.
* Invalid shipping records require manual review.
* Business decisions were based solely on the provided dataset.

---

## Repository Structure

```text
part1_data_cleaning/
├── data/
│   ├── raw_orders.xlsx
│   └── cleaned_orders.xlsx
├── outputs/
│   ├── data_quality_report.xlsx
│   ├── pivot_summary.xlsx
│   └── cleaning_log.md
├── screenshots/
│   ├── raw_data_preview.png
│   ├── cleaned_data_preview.png
│   ├── pivot_summary_1.png
│   └── pivot_summary_2.png
└── README.md
```

---

## Screenshots Included

* Raw Dataset Preview
* Cleaned Dataset Preview
* Sales and Profit by Region Pivot Summary
* Sales and Profit by Category and Sub-Category Pivot Summary

---

## Conclusion

The dataset was successfully cleaned, validated, and transformed into an analysis-ready format. Data quality issues were identified, documented, and resolved using Excel-based techniques and business validation rules. The final dataset supports accurate reporting, pivot analysis, and business decision-making.
