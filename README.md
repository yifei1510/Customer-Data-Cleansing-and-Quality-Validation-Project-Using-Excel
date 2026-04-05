# Customer Data Cleansing and Quality Validation Project Using Excel

## Executive Summary

This Excel data cleaning project cleaned and validated a raw customer dataset by resolving duplicate rows, repeated customer IDs, invalid name entries, inconsistent category values, mixed date formats, extra spaces, and missing data. The dataset was reduced from **999 raw rows** to **430 cleaned rows and 8 columns**, including the removal of **511 fully blank rows (51.2%)**, improving overall data quality and reporting readiness.

Using **Remove Duplicates, Find and Replace, Filters, and Excel formulas such as `TRIM()`, `PROPER()`**, the project standardised key fields, validated suspicious records, and separated **50 repeated records across 19 customer IDs** for further review, representing **5.0% of the raw dataset**. The final dataset is analysis-ready and can be directly imported into tools such as **Power BI, Excel, SQL, and other reporting platforms**.

**Cleaned Dataset Link:**  
[View the cleaned dataset](https://app.powerbi.com/groups/me/reports/864c22eb-ed0a-457e-a5ff-ec9c762b95fc/17275c38c6ba3b5cf624?experience=power-bi)


## Business Problem

The raw dataset was not suitable for direct reporting or analysis because it contained multiple data quality issues that could distort business outputs and reduce confidence in the results.

### Key issues identified

1. The raw file contained **999 rows**, but **511 rows** were fully blank.
2. Some customer IDs appeared multiple times and could not be removed automatically without further review.
3. Several values in the `Customer_Name` field were actually customer IDs instead of names.
4. `Gender` included inconsistent labels such as `M`, `F`, `Female`, `female`, `MALE`, and `MAlE`.
5. `Marital_Status` contained inconsistent values such as `Single`, `Marrd`, and `Sungle`.
6. `Purchase_Date` used mixed date formats with both `/` and `-`.
7. Text fields contained extra spaces that could affect filtering, matching, and summarisation.
8. Missing values were present in fields such as `Age`, `Amount`, and `Location`.
9. Some repeated customer IDs contained conflicting details and required manual review before any final decision.

Without cleaning, these issues would lead to inaccurate summaries, poor data consistency, unreliable reporting, and weak analytical outputs.

---

## Methodology

A structured Excel-based workflow was used to clean, validate, and review the dataset.

### 1. Initial Data Review
The raw file was reviewed to identify blank rows, duplicate records, invalid text patterns, inconsistent categories, mixed date formats, and missing values.

### 2. Duplicate Removal
Exact duplicate rows were removed using **Data > Remove Duplicates** to reduce obvious redundancy in the dataset.

### 3. Validation Helper Columns
Helper columns were created to support data quality checks, including:

- `Customer_ID_checker`
- `Customer_Name_check`
- `Age_checker`

These columns were used to identify:
- repeated customer IDs
- customer-ID-style values stored in the name field
- unrealistic age values

### 4. Repeated Customer ID Review
Repeated customer IDs were filtered and reviewed separately to distinguish exact duplicates from records requiring business confirmation. A separate review file was created for these unresolved cases.

### 5. Customer Name Validation
A checker was applied to identify records where customer IDs appeared in the `Customer_Name` field instead of actual customer names. This process identified **10 suspicious name records** requiring further review or correction.

### 6. Text Cleaning
The `TRIM()` function was used to remove extra spaces from text fields, while `PROPER()` was also applied where needed to improve text consistency.

Example formulas used:

```excel
=TRIM(B2)
=PROPER(H2)
```

### 7. Standardising Inconsistent Values

The Find and Replace feature was used to standardise inconsistent categorical values, including:

M / F → Male / Female
Marrd → Married
Sungle → Single

This reduced Gender from 9 inconsistent labels to 2 standard categories, and reduced Marital_Status from 4 raw labels to 2 clean categories.

### 8. Age Validation

A validation formula was used to flag unrealistic age values:

```excel
=OR(C2<0,C2>100)
```
This supported logical validation at record level.

### 9. Date Standardisation

Mixed date formats in Purchase_Date were standardised using Text to Columns and Excel date formatting tools.

This improved consistency for sorting, grouping, and future time-based analysis.

### 10. Missing Value Review

Missing values were reviewed based on the business meaning of each field rather than being mechanically replaced with a single default value. This helped avoid introducing misleading information into fields such as Age, Amount, and Location.

### 11. Final Dataset Review

After cleaning, the output was reviewed to ensure improved consistency across key fields and to keep unresolved exception records separate from the final working file.

## Skills
- Microsoft Excel
- Data Cleaning
- Data Validation
- Data Quality Review
- Duplicate Detection
- Helper Column Design
- Text Standardisation
- Date Standardisation
- Missing Value Review
- Exception Handling
- Record-Level Validation
- Find and Replace
- Filters and Sorting
- Text to Columns
- Excel Functions (TRIM, PROPER, OR)
- Manual Review of Suspicious Records

## Results & Business Recommendation

### Results

The project produced a cleaner and more structured dataset that is more suitable for validation, filtering, reporting, and downstream analysis.

### Quantified outcomes
- Reviewed 999 raw rows
- Identified 511 fully blank rows, representing 51.2% of the raw file
- Reduced the dataset to 430 cleaned rows
- Achieved an 11.9% reduction from the 488 non-blank source rows
- Standardised Gender from 9 inconsistent labels to 2 clean categories
- Standardised Marital_Status from 4 raw labels to 2 clean categories
- Standardised Location into 4 consistent categories
- Identified 10 suspicious records where customer IDs appeared in the Customer_Name field
- Separated 50 repeated records across 19 customer IDs into a review file for confirmation

### Business value
- Reduced data noise by removing exact duplicates and blank rows.
- Improved category consistency for filtering and reporting.
- Increased confidence in customer-level records by isolating suspicious entries.
- Improved date and text consistency to support downstream analysis.
- Created a structured exception-handling process instead of making unsupported assumptions during cleaning.

## Business Recommendation

- Repeated customer IDs should be reviewed before deletion, as they may represent conflicting or business-valid repeated
  records.
- Validation helper columns should be used early in the cleaning process to identify suspicious patterns systematically.
- Categorical fields should be standardised before building pivot tables, charts, or dashboards.
- Missing values should be reviewed based on field meaning rather than filled mechanically.
- Exception records should be stored separately for stakeholder confirmation when the correct value cannot be verified from
  the source data.

## Next Steps

- Confirm the 50 repeated records across 19 customer IDs with the relevant stakeholder or source owner.
- Complete manual correction of records where IDs were entered in the Customer_Name field instead of customer names.
- Perform a final review of the cleaned CSV to remove any remaining blank or unresolved rows.
- Use the cleaned dataset to create pivot tables, summary analysis, or dashboard visuals.
- Extend this workflow in future projects using Power Query or SQL to demonstrate scalable data cleaning capability on
  larger datasets.
