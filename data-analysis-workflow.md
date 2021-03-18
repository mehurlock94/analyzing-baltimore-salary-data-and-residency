# This document outlines the workflow of data collection and analysis in Excel for Mini Project #3, labeled analyzing-baltimore-salary-data-and-residency

Raw data for this project were taken from the Baltimore Open Data [hub](https://data.baltimorecity.gov/). Both datasets, [listed here](https://github.com/mehurlock94/analyzing-baltimore-salary-data-and-residency/blob/main/README.md), are indexed primarily by agency.

## Cleaning datasets
Baltimore salary data was downloaded from excel and includes employee name, position, agency, date of employment, salary and gross income. The date of employment within this file was not logged in a format to easily do calculations in excel, so the Excel "Text to Columns" feature was used to separate key values, delimited by spaces and "(". The year, month and day were they summarized into a start time using the "date" function. Since many employees have worked in Baltimore for several years, only data pertaining to fiscal year 2020 were used for analysis.

Baltimore employee living location (henceforth referred to as "location")  is summarized by agency and reports the total number of employees and the number living within each county in Maryland. For simplicity, the data was summarized by those living within the city and those living within another county. Since the location data is organized by agency, the salary data was summarized using the "averageifs" function, selecting for agency and fiscal year 2020. This was performed to find the average time of employment, salary, and gross income for each agency. Since the labels for agencies were not congruent between the FY2020 data and the location data, the Excel "Advanced Filter" feature was used to extract all unique agency values from the FY2020 and manually matched to the agencies in the location data. Agencies present in the salary data but not in the location data were removed.

Modified spreadsheets are as follows:
- [Salary data with time of employement added](https://github.com/mehurlock94/analyzing-baltimore-salary-data-and-residency/blob/main/Baltimore_Employee_Salaries_with_Time.xlsx)
- [Data analysis file](https://github.com/mehurlock94/analyzing-baltimore-salary-data-and-residency/blob/main/Baltimore_Employee_Salaries_Manipulated.xlsx)

## Multiple Linear Regression
MLR was conducted on the full FY2020 dataset, using the percentage of employees living in a location as the dependent variable, and the time of employement, salary, and gross income as the independent variables. The output is listed as "MLR_living_location" within the [Data analysis file](https://github.com/mehurlock94/analyzing-baltimore-salary-data-and-residency/blob/main/Baltimore_Employee_Salaries_Manipulated.xlsx).

## Plot Generation
The average time of employment, salary, gross income, and percent living in Baltimore were organized by the agency names found within the locations dataset. Scatterplots were generated using time of employment and gross income on respective x-axes and percent living in Baltimore on the y-axes. Equations for the line of best fit and R-squared values are displayed on the charts.

## Heat Map of Living Location
To identify the agencies with the highest and lowest amounts of employees living within the city, a heat map for percent living in Baltimore was generated using conditional formatting. Sorting was avoided to maintain the alphabetical order of agency names. The lowest percentages of employees living in Baltimore are tagged red and the highest percentages tagged green. The conditional formatting adjusts colors based on their location within the range of values.

## Cluster Analysis
Agencies were clustered based on average time of employment, average salary, average gross income, percent living in Baltimore, and the total number of employees. Agencies were retroactively matched with their anchors using VLOOKUP. Each agency's average time of employment, gross income, and percent living in Baltimore were also compiled, using agency name as an index. Each metric was analyzed using heat mapping to observe trends in variables as they pertain to the clusters.
