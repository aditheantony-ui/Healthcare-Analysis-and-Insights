
# Healthcare Data Analysis and Insights

## 1. Problem Statement

The healthcare industry generates vast amounts of data daily, providing valuable insights for healthcare providers and policymakers to improve patient care, allocate resources effectively, and manage healthcare costs. This project aims to analyze a comprehensive healthcare dataset comprising medical examinations, hospitalization details, and customer profiles to extract insights into patient health profiles, medical histories, and healthcare costs. By exploring relationships between various health metrics, identifying trends, and visualizing key patterns, the project aims to deliver actionable insights to healthcare stakeholders for informed decision-making through rigorous data cleaning, transformation, exploration, and analysis.

## 2. Dataset Description

The project uses three datasets obtained for the healthcare analysis.

### 2.1 Medical Examinations

Contains patient medical information, including:

- Customer ID
- BMI
- HBA1C
- Heart Issues
- Any Transplants
- Cancer History
- NumberOfMajorSurgeries
- Smoker

### 2.2 Hospitalization Details

Contains hospitalization and patient-related information, including:

- Customer ID
- Year
- Month
- Date
- Charges
- Hospital Tier
- City Tier
- State ID

### 2.3 Customer Names

Contains customer identification and name information.

### 2.4 Final Healthcare Dataset

The three datasets were consolidated into a single worksheet named `Healthcare`, using Customer ID as the common identifier.

The final dataset contains 2,335 records and the following 17 columns:

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

Data preprocessing was performed to improve the quality, consistency, and reliability of the healthcare dataset.

The preprocessing activities included:

- Identifying missing values represented by `?`.
- Handling missing Month and Year values.
- Identifying the most frequently occurring values in Smoker, Hospital Tier, and City Tier.
- Handling missing or invalid State ID values.
- Splitting customer names into Title, First Name, and Last Name.
- Converting NumberOfMajorSurgeries into numerical data.
- Checking inconsistencies in Heart Issues and Smoker.
- Creating Weight Status categories based on BMI.
- Creating Diabetes Status categories based on HBA1C.
- Combining Year, Month, and Date into Date of Birth.
- Calculating patient Age using 8 June 2023 as the reference date.
- Formatting Charges as currency ($).

## 4. Exploratory Data Analysis

Exploratory Data Analysis was conducted to identify patterns, distributions, and relationships within the healthcare dataset.

### 4.1 Cancer History Among Smokers and Non-Smokers

Analyzed the distribution of cancer history among smokers and non-smokers using patient counts and a doughnut chart.

### 4.2 Total Major Surgeries and Average HBA1C by Transplant History

Compared the total number of major surgeries and average HBA1C between patients with and without a history of transplants.

| Transplant History | Total Major Surgeries | Average HBA1C |
|---|---:|---:|
| No | 1,417 | 6.6704 |
| Yes | 162 | 5.1876 |
| Total | 1,579 | 6.5799 |

### 4.3 Average Healthcare Charges by Weight Status and Diabetes Status

Analyzed how average healthcare charges vary across different Weight Status and Diabetes Status categories using a column chart.

### 4.4 Average Charges by Hospital Tier Within Different States

Compared average healthcare charges for each Hospital Tier across different State IDs using a clustered column chart.

### 4.5 Relationship Between Age and BMI

Examined the relationship between patient Age and BMI using a scatter plot and linear trendline.

- R-squared value: 0.0157

### 4.6 Relationship Between Age and HBA1C

Examined the relationship between patient Age and HBA1C using a scatter plot and trendline.

### 4.7 Relationship Between Age and Healthcare Charges

Analyzed the relationship between patient Age and healthcare Charges using a scatter plot and linear trendline.

- R-squared value: 0.0211

## 5. Project Execution Steps

The project was carried out using Microsoft Excel. The following steps describe the operations performed to complete the assignment.

### 5.1 Data Cleaning

**Step 1: Identify Missing Values**

- Opened the Medical Examinations table.
- Checked every column for missing values represented by `?`.
- Used COUNTIF to count missing values in each column.
- Repeated the process for the Hospitalization Details table.
- Identified 17 missing values across the two datasets.

**Step 2: Handle Missing Month and Year Values**

- Identified missing entries in the Month column.
- Replaced missing Month values with `Sep`.
- Calculated the average of the available Year values.
- Rounded the average to the nearest integer.
- Used the rounded average to fill missing Year entries.

**Step 3: Determine the Mode of Smoker, Hospital Tier, and City Tier**

- Examined the Smoker, Hospital Tier, and City Tier columns.
- Created PivotTables to count the frequency of each distinct value.
- Sorted the frequency counts in descending order.
- Identified the most frequently occurring value (mode) for each column.
- Used the identified modes to fill missing entries.
- The mode for Smoker was `No`.

**Step 4: Handle Missing State ID Values**

- Applied filters to inspect the State ID column.
- Checked for missing, invalid, and unusual entries.
- Used COUNTIF, FILTER, ISNUMBER, and VALUE to inspect the values.
- Replaced identified invalid State ID entries with `Unknown`.

### 5.2 Data Transformation

**Step 5: Split the Customer Names Column**

- Opened the Customer Names table.
- Selected the Names column.
- Used Data → Text to Columns in Excel.
- Split the names into three columns: Title, First Name, and Last Name.
- Retained First Name for the final consolidated dataset.

**Step 6: Convert NumberOfMajorSurgeries into Numerical Data**

- Inspected the NumberOfMajorSurgeries column.
- Identified non-numeric characters and representations.
- Replaced non-numeric representations with their corresponding meaningful numerical values.
- Ensured the column contained numerical data suitable for calculations.

**Step 7: Check Inconsistencies in Heart Issues and Smoker**

- Applied filters to inspect the Heart Issues and Smoker columns.
- Checked for inconsistent labels and capitalization.
- Standardized equivalent categorical values.

**Step 8: Create Weight Status**

Created a new column named `Weight Status` based on BMI:

| BMI | Weight Status |
|---|---|
| Below 18.5 | Underweight |
| 18.5–24.9 | Normal Weight |
| 25.0–29.9 | Overweight |
| 30.0 and Above | Obesity |

**Step 9: Create Diabetes Status**

Created a new column named `Diabetes Status` based on HBA1C:

| HBA1C | Diabetes Status |
|---|---|
| Below 5.7 | Normal |
| 5.7–6.4 | Prediabetes |
| 6.5 and Above | Diabetes |

**Step 10: Create Date of Birth**

- Combined Year, Month, and Date from the Hospitalization Details table.
- Created a new column named Date of Birth.
- Applied the custom date format `DD-MMM-YYYY`.

**Step 11: Calculate Age**

- Used 8 June 2023 as the dataset collection date.
- Calculated the age of each customer using Date of Birth.

**Step 12: Format Charges**

- Selected the Charges column.
- Applied currency formatting using the dollar ($) symbol.

### 5.3 Data Integration Using VLOOKUP

**Step 13: Create the Healthcare Worksheet**

- Created a new worksheet named `Healthcare`.
- Used Customer ID as the common column across all three datasets.
- Used VLOOKUP to retrieve the required information from Medical Examinations, Hospitalization Details, and Customer Names.
- Combined the retrieved information into one consolidated worksheet.
- Retained all 17 columns specified in the assignment.
- Verified the final dataset containing 2,335 records.

### 5.4 Data Analysis and Visualization

**Step 14: Cancer History Among Smokers and Non-Smokers**

- Created a PivotTable using Smoker and Cancer History.
- Added Customer ID to the Values area.
- Set the calculation to Count.
- Inserted a doughnut chart to visualize the distribution.

**Step 15: Major Surgeries and HBA1C by Transplant History**

- Created a PivotTable using Any Transplants.
- Added NumberOfMajorSurgeries to Values and selected Sum.
- Added HBA1C to Values and selected Average.
- Inserted a chart to compare patients with and without transplant history.

**Step 16: Average Charges by Weight Status and Diabetes Status**

- Created a PivotTable.
- Added Weight Status and Diabetes Status as categories.
- Added Charges to Values.
- Changed the summary calculation to Average.
- Inserted a column chart.

**Step 17: Average Charges by Hospital Tier Within State**

- Created a PivotTable.
- Added State ID and Hospital Tier as categories.
- Added Charges to Values.
- Changed the summary calculation to Average.
- Inserted a clustered column chart.

**Step 18: Age vs BMI**

- Selected Age as the X-axis and BMI as the Y-axis.
- Inserted a scatter plot.
- Added a linear trendline.
- Displayed the R-squared value.

**Step 19: Age vs HBA1C**

- Selected Age as the X-axis and HBA1C as the Y-axis.
- Inserted a scatter plot.
- Added a trendline to examine the relationship.

**Step 20: Age vs Healthcare Charges**

- Selected Age as the X-axis and Charges as the Y-axis.
- Inserted a scatter plot.
- Added a linear trendline.
- Displayed the R-squared value.

### 5.5 Dashboard Creation

**Step 21: Create the Healthcare Dashboard Worksheet**

- Created a new worksheet named `Healthcare Dashboard`.
- Moved the dashboard worksheet to the first position.
- Added the dashboard title: `HEALTHCARE ANALYTICS DASHBOARD`.
- Added the subtitle: `Patient Demographics, Medical Conditions & Healthcare Cost Analysis`.

**Step 22: Add Charts and KPI Cards**

- Copied the analysis charts into the dashboard worksheet.
- Arranged the charts for clear presentation.
- Created a Total Patients KPI card.
- Displayed the total patient count of 2,335.

**Step 23: Add Interactive Slicers**

- Inserted a slicer for Weight Status.
- Inserted a slicer for Diabetes Status.
- Connected the slicers to compatible PivotTables and PivotCharts.
- Tested the slicers to verify interactive filtering.

## 6. Excel Formulas and Methods Used

The following Excel formulas and methods were used during data cleaning, transformation, integration, and analysis.

### 6.1 Missing Value Count

Used COUNTIF to count cells containing the literal `?` character.

```excel
=COUNTIF(A2:A2336,"~?")
```

The range should be adjusted to the relevant column in each source table.

### 6.2 Average Year Rounded to the Nearest Integer

```excel
=ROUND(AVERAGE(A2:A2336),0)
```

The range should refer to the available Year values.

### 6.3 Weight Status

```excel
=IF(C2<18.5,"Underweight",IF(C2<25,"Normal Weight",IF(C2<30,"Overweight","Obesity")))
```

### 6.4 Diabetes Status

```excel
=IF(D2<5.7,"Normal",IF(D2<6.5,"Prediabetes","Diabetes"))
```

### 6.5 Date of Birth

The DATE function can combine the Year, Month, and Date values. For a month stored as text such as `Sep`, use:

```excel
=DATE(A2,MONTH(1&B2),C2)
```

Here, A2 represents Year, B2 represents Month, and C2 represents Date. Apply the `DD-MMM-YYYY` number format.

### 6.6 Age Calculation

```excel
=DATEDIF(L2,DATE(2023,6,8),"Y")
```

### 6.7 VLOOKUP for Dataset Integration

Example: Retrieving BMI from the Medical Examinations table using Customer ID.

```excel
=VLOOKUP($A2,'Medical Examinations'!$A:$J,2,FALSE)
```

- `$A2` is the Customer ID in the Healthcare worksheet.
- `'Medical Examinations'!$A:$J` is the source lookup range.
- `2` is the column index for BMI in this example.
- `FALSE` ensures an exact match.

The column index must be changed according to the field being retrieved. The same VLOOKUP approach was used to retrieve the required fields from the other source tables.

### 6.8 Total Patient Count

```excel
=COUNTA(Healthcare!A2:A2336)
```

### 6.9 Heart Issue Patient Count

```excel
=COUNTIF(Healthcare!E2:E2336,"Yes")
```

### 6.10 Cancer Case Count

```excel
=COUNTIF(Healthcare!G2:G2336,"Yes")
```

### 6.11 Total Major Surgeries

```excel
=SUM(Healthcare!H2:H2336)
```

### 6.12 Additional Excel Functions and Methods

| Function / Method | Purpose |
|---|---|
| COUNTIF | Counted missing values and records matching conditions |
| AVERAGE | Calculated average Year, Charges, and HBA1C |
| ROUND | Rounded the average Year |
| IF | Created Weight Status and Diabetes Status categories |
| DATE | Combined date components |
| DATEDIF | Calculated patient age |
| VLOOKUP | Integrated the three datasets using Customer ID |
| FILTER | Inspected and filtered State ID values |
| ISNUMBER | Checked whether values were numeric |
| VALUE | Converted numeric text into numbers |
| COUNTA | Counted patient records |
| SUM | Calculated total major surgeries |
| PivotTables | Summarized data and identified frequently occurring values |
| Sorting | Ranked category frequencies |
| Excel Filters | Inspected missing, inconsistent, and unusual values |
| Text to Columns | Split customer names |
| PivotCharts | Visualized analytical results |
| Doughnut Charts | Compared cancer history distributions |
| Column Charts | Compared healthcare charges |
| Clustered Column Charts | Compared hospital tiers across states |
| Scatter Plots | Examined relationships between numerical variables |
| Trendlines | Examined overall data patterns |
| Slicers | Enabled interactive dashboard filtering |

### Tools and Technologies

- Microsoft Excel
- Excel Formulas and Functions
- VLOOKUP
- PivotTables and PivotCharts
- Excel Filters and Sorting
- Text to Columns
- Interactive Slicers
- Data Cleaning and Preprocessing
- Exploratory Data Analysis
- Data Visualization
- Dashboard Development
