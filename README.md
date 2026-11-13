
# Healthcare Data Analysis and Insights

## 1. Problem Statement

The healthcare industry generates vast amounts of data daily, providing valuable insights for healthcare providers and policymakers to improve patient care, allocate resources effectively, and manage healthcare costs. This project aims to analyze a comprehensive healthcare dataset comprising medical examinations, hospitalization details, and customer profiles to extract insights into patient health profiles, medical histories, and healthcare costs. By exploring relationships between various health metrics, identifying trends, and visualizing key patterns, the project aims to deliver actionable insights to healthcare stakeholders for informed decision-making through rigorous data cleaning, transformation, exploration, and analysis.

## 2. Dataset Description

The project uses three datasets:

### 2.1 Medical Examinations

Contains patient medical information:

- Customer ID
- BMI
- HBA1C
- Heart Issues
- Any Transplants
- Cancer History
- NumberOfMajorSurgeries
- Smoker

### 2.2 Hospitalization Details

Contains hospitalization-related information:

- Customer ID
- Year
- Month
- Date
- Children
- Charges
- Hospital Tier
- City Tier
- State ID

### 2.3 Customer Names

Contains customer identification and the original Names column.

### 2.4 Final Consolidated Dataset

The three datasets were combined into a worksheet named `Healthcare`, using Customer ID as the common identifier.

The final dataset contains **2,335 records and 17 columns**:

1. Customer ID
2. First Name
3. BMI
4. HBA1C
5. Heart Issues
6. Any Transplants
7. Cancer History
8. NumberOfMajorSurgeries
9. Smoker
10. Weight Status
11. Diabetes Status
12. Date of Birth
13. Charges
14. Hospital Tier
15. City Tier
16. State ID
17. Age

## 3. Data Preprocessing

Data preprocessing was performed in Microsoft Excel to improve the quality, consistency, and reliability of the healthcare dataset.

The preprocessing activities included:

- Identifying missing values represented by `?`.
- Handling missing Month and Year values.
- Identifying the most frequently occurring values in Smoker, Hospital Tier, and City Tier.
- Inspecting and correcting invalid State ID entries.
- Splitting customer names into Title, First Name, and Last Name.
- Converting NumberOfMajorSurgeries into numerical data.
- Checking inconsistencies in Heart Issues and Smoker.
- Creating Weight Status categories based on BMI.
- Creating Diabetes Status categories based on HBA1C.
- Combining Year, Month, and Date into Date of Birth.
- Calculating Age using 8 June 2023 as the reference date.
- Formatting Charges as currency ($).

## 4. Exploratory Data Analysis

Exploratory Data Analysis was performed using PivotTables, PivotCharts, doughnut charts, column charts, and scatter plots.

### 4.1 Cancer History Among Smokers and Non-Smokers

Analyzed the distribution of cancer history among smokers and non-smokers using Customer ID counts and a doughnut chart.

### 4.2 Total Major Surgeries and Average HBA1C by Transplant History

Compared the total number of major surgeries and average HBA1C between patients with and without a history of transplants.

| Transplant History | Total Major Surgeries | Average HBA1C |
|---|---:|---:|
| No | 1,417 | 6.6704 |
| Yes | 162 | 5.1876 |
| Total | 1,579 | 6.5799 |

A doughnut chart was used to present this analysis in the workbook.

### 4.3 Average Healthcare Charges by Weight Status and Diabetes Status

Analyzed average healthcare charges across different Weight Status and Diabetes Status categories using a column chart.

### 4.4 Average Charges by Hospital Tier Within Different States

Compared average healthcare charges across different Hospital Tiers within different State IDs using a clustered column chart.

### 4.5 Relationship Between Age and BMI

Examined the relationship between Age and BMI using a scatter plot and linear trendline.

- R-squared value: 0.0157

### 4.6 Relationship Between Age and HBA1C

Examined the relationship between Age and HBA1C using a scatter plot and trendline.

### 4.7 Relationship Between Age and Healthcare Charges

Examined the relationship between Age and Charges using a scatter plot and linear trendline.

- R-squared value: 0.0211

## 5. Project Execution Steps and Methods Used

The following procedures describe the actual work performed in the Excel workbooks.

### 5.1 Data Cleaning

**Step 1: Identifying Missing Values**

- Checked each column in the Medical Examinations table for missing values represented by `?`.
- Repeated the process for the Hospitalization Details table.
- Used COUNTIF to count missing values in the individual columns.
- Identified a total of 17 missing values across both tables.

**Step 2: Handling Missing Month and Year**

- Replaced missing Month values with `Sep`.
- Calculated the average of the available Year values.
- Used ROUND to round the average to the nearest integer.
- Filled missing Year values using the rounded average.

**Step 3: Finding the Most Frequently Occurring Values**

- Examined the Smoker, Hospital Tier, and City Tier columns.
- Used PivotTables and frequency counts to identify the most frequently occurring values.
- Used the mode values to fill missing entries.
- The mode for Smoker was `No`.
- The mode used for Hospital Tier and City Tier was `tier - 2`.

**Step 4: Cleaning State ID**

- Applied filters to inspect the State ID column.
- Used FILTER with ISNUMBER and VALUE to identify numeric-looking entries.
- Used COUNTIF to check the occurrence of `1983`.
- Identified two incorrect occurrences of `1983`.
- Replaced these entries with `Unknown`.

**Step 5: Inspecting Hospital Tier and City Tier**

- Applied Excel filters and Number Filters to inspect unusual numeric or year-like values.
- Used COUNTIF to check the frequency of unusual entries.
- Verified the values before applying the mode for missing entries.

### 5.2 Data Transformation

**Step 6: Splitting Customer Names**

Used Excel formulas to separate the original Names column into Title, First Name, and Last Name.

**Title:**

```excel
=TRIM(MID(B2,FIND(",",B2)+1,FIND(" ",TRIM(MID(B2,FIND(",",B2)+1,99))&" ")-1))
```

**First Name:**

```excel
=TRIM(LEFT(TRIM(MID(SUBSTITUTE(B2,CHAR(160)," "),FIND(".",SUBSTITUTE(B2,CHAR(160)," "))+1,99)),FIND(" ",TRIM(MID(SUBSTITUTE(B2,CHAR(160)," "),FIND(".",SUBSTITUTE(B2,CHAR(160)," "))+1,99))&" ")-1))
```

**Last Name:**

```excel
=TRIM(LEFT(SUBSTITUTE(B2,CHAR(160)," "),FIND(",",SUBSTITUTE(B2,CHAR(160)," "))-1))
```

First Name was retained in the final Healthcare dataset.

**Step 7: Converting NumberOfMajorSurgeries**

- Inspected the NumberOfMajorSurgeries column.
- Identified non-numeric representations.
- Replaced non-numeric representations with meaningful numerical values.
- Prepared the column for numerical analysis.

**Step 8: Checking Inconsistencies**

- Inspected Heart Issues and Smoker using Excel filters.
- Checked inconsistent categorical entries and capitalization.
- Standardized equivalent values.

**Step 9: Creating Weight Status**

Created a new column named `Weight Status` using BMI:

| BMI | Weight Status |
|---|---|
| Below 18.5 | Underweight |
| 18.5–24.9 | Normal Weight |
| 25.0–29.9 | Overweight |
| 30.0 and Above | Obesity |

Formula used in the Medical Examinations worksheet:

```excel
=IF(B2<18.5,"Underweight",IF(B2<25,"Normal Weight",IF(B2<30,"Overweight","Obesity")))
```

**Step 10: Creating Diabetes Status**

Created a new column named `Diabetes Status` using HBA1C:

| HBA1C | Diabetes Status |
|---|---|
| Below 5.7 | Normal |
| 5.7–6.4 | Prediabetes |
| 6.5 and Above | Diabetes |

Formula used in the Medical Examinations worksheet:

```excel
=IF(C2<5.7,"Normal",IF(C2<6.5,"Prediabetes","Diabetes"))
```

**Step 11: Creating Date of Birth**

Combined Year, Month, and Date using DATE, MATCH, and TEXT.

Formula used in the Hospitalization Details worksheet:

```excel
=TEXT(DATE(B2,MATCH(C2,{"Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec"},0),D2),"dd-mmm-yyyy")
```

The resulting date was formatted as `DD-MMM-YYYY`.

**Step 12: Calculating Age**

Calculated each customer's age using 8 June 2023 as the reference date.

Formula used:

```excel
=DATEDIF(J2,DATE(2023,6,8),"Y")
```

**Step 13: Formatting Charges**

Applied dollar currency formatting to the Charges column.

### 5.3 Data Integration Using VLOOKUP

**Step 14: Creating the Healthcare Worksheet**

- Created a worksheet named `Healthcare`.
- Used Customer ID as the common identifier.
- Retrieved First Name from Customer Names.
- Retrieved medical information from Medical Examinations.
- Retrieved hospitalization information from Hospitalization Details.
- Used exact-match VLOOKUP formulas with `FALSE`.
- Consolidated the required fields into 17 columns and 2,335 records.

**First Name – Customer Names**

```excel
=VLOOKUP($A2,'Customer Names'!$A:$E,4,FALSE)
```

**Medical Examination Fields**

The following VLOOKUP formulas were used to retrieve the medical information:

**BMI:**

```excel
=VLOOKUP($A2,'Medical Examinations'!$A:$J,2,FALSE)
```

**HBA1C:**

```excel
=VLOOKUP($A2,'Medical Examinations'!$A:$J,3,FALSE)
```

**Heart Issues:**

```excel
=VLOOKUP($A2,'Medical Examinations'!$A:$J,4,FALSE)
```

**Any Transplants:**

```excel
=VLOOKUP($A2,'Medical Examinations'!$A:$J,5,FALSE)
```

**Cancer History:**

```excel
=VLOOKUP($A2,'Medical Examinations'!$A:$J,6,FALSE)
```

**NumberOfMajorSurgeries:**

```excel
=VLOOKUP($A2,'Medical Examinations'!$A:$J,7,FALSE)
```

**Smoker:**

```excel
=VLOOKUP($A2,'Medical Examinations'!$A:$J,8,FALSE)
```

**Weight Status:**

```excel
=VLOOKUP($A2,'Medical Examinations'!$A:$J,9,FALSE)
```

**Diabetes Status:**

```excel
=VLOOKUP($A2,'Medical Examinations'!$A:$J,10,FALSE)
```

**Date of Birth – Hospitalization Details**

```excel
=VLOOKUP($A2,'Hospitalisation Details'!$A:$K,10,FALSE)
```

**Charges – Hospitalization Details**

```excel
=VLOOKUP("Id"&(2336-ROWS($M$2:M2)),'Hospitalisation Details'!$A:$K,6,FALSE)
```

**Hospital Tier:**

```excel
=VLOOKUP("Id"&(2336-ROWS($N$2:N2)),'Hospitalisation Details'!$A:$K,7,FALSE)
```

**City Tier:**

```excel
=VLOOKUP("Id"&(2336-ROWS($O$2:O2)),'Hospitalisation Details'!$A:$K,8,FALSE)
```

**State ID:**

```excel
=VLOOKUP("Id"&(2336-ROWS($P$2:P2)),'Hospitalisation Details'!$A:$K,9,FALSE)
```

**Age:**

```excel
=VLOOKUP("Id"&(2336-ROWS($Q$2:Q2)),'Hospitalisation Details'!$A:$K,11,FALSE)
```

The ROWS-based lookup formulas were used for hospitalization fields to generate the required Customer ID lookup sequence.

### 5.4 PivotTables and Charts

**Step 15: Cancer History Among Smokers and Non-Smokers**

- Created a PivotTable using Smoker and Cancer History.
- Added Customer ID to Values and selected Count.
- Compared cancer history across smoker categories.
- Created a doughnut chart.

**Step 16: Total Major Surgeries and Average HBA1C by Transplant History**

- Created a PivotTable using Any Transplants.
- Added NumberOfMajorSurgeries to Values and selected Sum.
- Added HBA1C to Values and selected Average.
- Created a doughnut chart to present the comparison.

**Step 17: Average Charges by Weight Status and Diabetes Status**

- Created a PivotTable.
- Grouped data by Weight Status and Diabetes Status.
- Added Charges to Values.
- Changed the calculation to Average.
- Created a column chart.

**Step 18: Average Charges by Hospital Tier Across States**

- Created a PivotTable.
- Grouped data by State ID and Hospital Tier.
- Added Charges to Values.
- Changed the calculation to Average.
- Created a clustered column chart.

**Step 19: Age Correlation Analysis**

Created three separate scatter plots:

1. Age vs BMI
2. Age vs HBA1C
3. Age vs Healthcare Charges

For each scatter plot:

- Selected Age as the X-axis.
- Selected the corresponding numerical variable as the Y-axis.
- Inserted a scatter chart.
- Added a linear trendline.
- Displayed the R-squared value where configured.

### 5.5 Interactive Dashboard Creation

**Step 20: Creating the Dashboard Worksheet**

- Created a worksheet named `Healthcare Dashboard`.
- Moved it to the first worksheet position.
- Added the title `HEALTHCARE ANALYTICS DASHBOARD`.
- Added the subtitle `Patient Demographics, Medical Conditions & Healthcare Cost Analysis`.

**Step 21: Adding Charts and KPI Cards**

- Copied the analysis charts into the dashboard.
- Arranged the charts for clear presentation.
- Created a Total Patients KPI card.
- Displayed the total patient count of 2,335.

**Step 22: Adding Interactive Slicers**

- Inserted a Weight Status slicer.
- Inserted a Diabetes Status slicer.
- Opened Report Connections.
- Connected the slicers to compatible PivotTables, including Healthcare Charges and Total Major Surgeries.
- Tested the slicers to confirm interactive filtering.

## 6. Excel Formulas and Functions Reference

The following functions and methods were used throughout the project.

| Formula / Function / Method | Application |
|---|---|
| COUNTIF | Counted missing values and checked the frequency of State ID entries |
| AVERAGE | Calculated average Year and other numerical measures |
| ROUND | Rounded the average Year |
| TRIM | Removed unnecessary spaces from customer names |
| MID | Extracted text from customer names |
| FIND | Located commas, spaces, and periods in names |
| LEFT | Extracted first and last names |
| SUBSTITUTE | Replaced non-breaking spaces |
| CHAR | Identified non-breaking spaces using CHAR(160) |
| IF | Created Weight Status and Diabetes Status categories |
| TEXT | Formatted the combined Date of Birth |
| DATE | Combined Year, Month, and Date |
| MATCH | Converted month abbreviations into month numbers |
| DATEDIF | Calculated patient age |
| VLOOKUP | Integrated information from all three source datasets |
| ROWS | Generated the hospitalization Customer ID lookup sequence |
| FILTER | Inspected numeric-looking State ID entries |
| ISNUMBER | Checked numeric values |
| VALUE | Converted numeric text into numbers |
| SUM | Calculated total major surgeries |
| COUNTA | Counted patient records |
| PivotTables | Summarized healthcare data and identified frequent values |
| Sorting and Filtering | Inspected missing, inconsistent, and unusual entries |
| Text to Columns | Separated customer names |
| Doughnut Charts | Visualized cancer history and transplant analysis |
| Column Charts | Compared healthcare charges |
| Clustered Column Charts | Compared hospital tiers across states |
| Scatter Plots | Examined relationships between Age and other numerical variables |
| Trendlines | Examined overall data patterns |
| R-squared | Evaluated the linear relationship shown by scatter plots |
| Slicers | Enabled interactive dashboard filtering |

### Tools Used

- Microsoft Excel
- Excel Formulas and Functions
- VLOOKUP
- PivotTables and PivotCharts
- Excel Filters and Sorting
- Text Extraction Functions
- Doughnut Charts
- Column Charts
- Clustered Column Charts
- Scatter Plots and Trendlines
- Interactive Slicers
- Dashboard Development
