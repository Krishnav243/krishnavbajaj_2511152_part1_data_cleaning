# Cleaning Log

## Part 1: Business Data Cleaning, Validation & Excel Reporting

### Dataset Information

| Item                            | Count |
| ------------------------------- | ----- |
| Original Records                | 934   |
| Final Cleaned Records           | 913   |
| Exact Duplicate Records Removed | 21    |

---

## Issues Identified

### Missing Values

* Missing Region Values: 26
* Missing Ship Mode Values: 22
* Missing Discount Values: 18

### Duplicate Records

* Exact Duplicate Records: 21
* Duplicate Order ID Occurrences: 63

### Discount Issues

* Negative Discount Values: 16
* Percentage-Based Discount Values: 8

### Date Issues

* Multiple date formats found in order_date and ship_date fields.
* Ship date earlier than order date identified in several records.
* Date standardization required before analysis.

### Text Formatting Issues

* Inconsistent capitalization in text fields.
* Extra spaces found in category, sub_category, and ship_mode fields.
* Formatting inconsistencies affecting pivot table grouping.

---

## Cleaning Actions Performed

### Text Standardization

The following fields were cleaned and standardized:

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

* Removed leading and trailing spaces using TRIM.
* Standardized text capitalization.
* Corrected formatting inconsistencies.
* Standardized category, sub-category, and ship mode values for consistent reporting.

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
* Flagged records where ship_date occurred before order_date.

---

### Duplicate Handling

Actions performed:

* Identified exact duplicate rows.
* Removed 21 exact duplicate records.
* Identified duplicate Order IDs.
* Retained duplicate Order IDs for business review.
* Flagged duplicate Order IDs for further investigation.

---

### Discount Validation

Actions performed:

* Replaced missing discount values with 0.
* Converted percentage-format discount values into decimal format.
* Flagged negative discount values as Invalid.

---

## Calculated Columns Created

* cleaned_discount
* calculated_sales
* calculated_profit
* profit_margin
* shipping_delay_days
* order_month
* order_year
* data_quality_flag

### Calculation Logic

Calculated Sales = Quantity × Unit Price × (1 − Discount)

Calculated Profit = Calculated Sales − Cost

Profit Margin = Calculated Profit ÷ Calculated Sales

Shipping Delay Days = Ship Date − Order Date

---

## Business Rules Applied

### Missing Region

Missing values were replaced with "Unknown".

### Missing Ship Mode

Missing values were replaced with "Unknown".

### Missing Discount

Missing values were replaced with 0 only when other sales fields were valid.

### Negative Discounts

Negative discount values were flagged as Invalid.

### Invalid Shipping Records

Records with ship_date earlier than order_date were flagged as Invalid.

### Cancelled Orders

Cancelled orders were excluded from completed sales reporting.

### Failed Payments

Failed payment records were excluded from completed sales reporting.

### Refunded Orders

Refunded orders were retained and reported separately for business review.

---

## Records Removed

| Record Type             | Count |
| ----------------------- | ----- |
| Exact Duplicate Records | 21    |

---

## Records Flagged

| Issue                    | Count |
| ------------------------ | ----- |
| Duplicate Order IDs      | 63    |
| Invalid Discount Records | 16    |
| Invalid Shipping Records | 93    |

---

## Assumptions Made

* Missing Region values were treated as Unknown.
* Missing Ship Mode values were treated as Unknown.
* Missing Discount values were treated as 0 when other sales fields were available.
* Duplicate Order IDs may represent valid business transactions and therefore were not automatically removed.
* Flagged records were retained for reporting transparency.

---

## Limitations

* Duplicate Order IDs require further business verification.
* Flagged shipping records require manual review.
* Business validation decisions were based on available dataset information.

---
## Screenshots

### Raw Dataset Preview

![Raw Dataset](screenshots/raw_data_preview.png)

---

### Cleaned Dataset Preview

![Cleaned Dataset](screenshots/cleaned_data_preview.png)

---

### Sales and Profit by Region

![Sales and Profit by Region](screenshots/pivot_summary_1.png)

---

### Sales and Profit by Category and Sub-Category

![Category Analysis](screenshots/pivot_summary_2.png)




## Final Outcome

The dataset was successfully cleaned, validated, and prepared for business reporting. Missing values, duplicate records, text-format inconsistencies, discount issues, and date-related issues were identified and addressed. The final dataset is suitable for pivot analysis, reporting, dashboard creation, and business decision-making.
