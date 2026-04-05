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

<img width="634" height="242" alt="duplicate remove" src="https://github.com/user-attachments/assets/931d7303-11f3-42e1-b499-1d19813dbdaa" />


### 3. Validation Helper Columns
Helper columns were created to support data quality checks, including:

- `Customer_ID_checker`
- `Customer_Name_check`
- `Age_checker`

These columns were used to identify:
- repeated customer IDs
- customer-ID-style values stored in the name field
- unrealistic age values
  
<img width="491" height="354" alt="customer_id checker_manuly" src="https://github.com/user-attachments/assets/123ba296-c608-4ff0-8752-e737388d6ec8" />



<img width="407" height="157" alt="customer_name_checker" src="https://github.com/user-attachments/assets/8715d57a-98d3-4e97-9ce0-738689de818e" />




<img width="447" height="29" alt="aGE CHECKER" src="https://github.com/user-attachments/assets/04c51ef0-c74e-40e0-887d-c3e7bc71a43f" />


### 4. Repeated Customer ID Review
Repeated customer IDs were filtered and reviewed separately to distinguish exact duplicates from records requiring business confirmation. A separate review file was created for these unresolved cases.

<img width="755" height="368" alt="customer id repeated to be asked" src="https://github.com/user-attachments/assets/fbc2cf51-8ca2-4bed-94d8-01f305141fbf" />


### 5. Customer Name Validation
A checker was applied to identify records where customer IDs appeared in the `Customer_Name` field instead of actual customer names. This process identified **10 suspicious name records** requiring further review or correction.

### 6. Text Cleaning
The `TRIM()` function was used to remove extra spaces from text fields, while `PROPER()` was also applied where needed to improve text consistency.

Example formulas used:

```excel
=TRIM(B2)
=PROPER(H2)
```

<img width="629" height="199" alt="trim to remove space" src="https://github.com/user-attachments/assets/13cb6f3d-fa54-4529-b04e-86d530aa72bb" />

<img width="605" height="287" alt="replace inproper value" src="https://github.com/user-attachments/assets/5a76bd92-ff0e-4548-81d9-e222039fda34" />



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

<img width="468" height="323" alt="date_formatt_1" src="https://github.com/user-attachments/assets/3a7ec929-069e-445b-84cf-53577c676dd0" />

<img width="431" height="333" alt="date_formatt_2" src="https://github.com/user-attachments/assets/fb86e120-d2e6-4eac-bc57-21dec684b954" />


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
