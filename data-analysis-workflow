# This document outlines the workflow of data collection and analysis in Excel for Mini Project #3, labeled analyzing-baltimore-salary-data-and-residency

Raw data for this project were taken from the Baltimore Open Data [hub](https://data.baltimorecity.gov/). Both datasets, [listed here](https://github.com/mehurlock94/analyzing-baltimore-salary-data-and-residency/blob/main/README.md), are indexed primarily by agency.

## Cleaning datasets
Baltimore salary data was downloaded from excel and includes employee name, position, agency, date of employment, salary and gross income. The date of employment within this file was not logged in a format to easily do calculations in excel, so the Excel "Text to Columns" feature was used to separate key values, delimited by spaces and "(". The year, month and day were they summarized into a start time using the "date" function. Since many employees have worked in Baltimore for several years, only data pertaining to fiscal year 2020 were used for analysis.

Baltimore employee living location (henceforth referred to as "location")  is summarized by agency and reports the total number of employees and the number living within each county in Maryland. For simplicity, the data was summarized by those living within the city and those living within another county. Since the location data is organized by agency, the salary data was summarized using the "averageifs" function, selecting for agency and fiscal year 2020. This was performed to find the average time of employment, salary, and gross income for each agency. Since the labels for agencies were not congruent between the FY2020 data and the location data, the Excel "Advanced Filter" feature was used to extract all unique agency values from the FY2020 and manually matched to the agencies in the location data. Agencies present in the salary data but not in the location data were removed.

Modified spreadsheets are as follows:
- [Salary data with time of employement added](https://github.com/mehurlock94/analyzing-baltimore-salary-data-and-residency/blob/main/Baltimore_Employee_Salaries_with_Time.xlsx)
- [Data analysis file](https://github.com/mehurlock94/analyzing-baltimore-salary-data-and-residency/blob/main/Baltimore_Employee_Salaries_Manipulated.xlsx)

## Multiple Linear Regression
MLR was conducted on the full FY2020 dataset, using the percentage of employees living in a location as the dependent variable, and the time of employement, salary, and gross income as the independent variables. The output is listed as "MLR_living_location" within the [Data analysis file](https://github.com/mehurlock94/analyzing-baltimore-salary-data-and-residency/blob/main/Baltimore_Employee_Salaries_Manipulated.xlsx)
Data were imported into Excel and filtered based on two locations: 
1. Baltimore, MD
1. Sussex County, DE

A [previous analysis](https://github.com/mehurlock94/comparing-baltimore-lewes-social-status/blob/main/README.md) investigated similar properties specific to Lewes, DE. The differences between Baltimore and Lewes were subsequently assumed to have many confounding variables, so the scope for Delaware was expanded to Sussex County to better align total population and to better diversify demographics. Data from Baltimore locations were processed to include only locations which exist within Baltimore city limits. Some data points were designated as Baltimore, MD but truly occurred outside these boundaries. With the locations filtered, datasets for individual variables obtained from Opportunity Atlas were matched to the filtered list using the VLOOKUP Excel function. The raw data compiled for analysis are included [here](https://github.com/mehurlock94/comparing-baltimore-sussex-county-teen-birth-economic-outcomes/blob/main/balt_sussex_raw_data.xlsx). The Excel file with manupulated data is inlcuded [here](https://github.com/mehurlock94/comparing-baltimore-sussex-county-teen-birth-economic-outcomes/blob/main/comparing_balt_sussex_teen_birth_economic_outcomes_data.xlsx)

## Multiple Linear Regression
For each location, multiple linear regression was performed using the regression tool within the Microsoft Excel Data Analysis Toolpack. The independent variables analyzed were Teen Birth Rate, Fraction Married, Median rent, and Single Parent Frequency with the dependent variable being Poverty Rate. For both locations, the F-value for the MLR was significant (F<1E-6). For each variable, a p-value below 0.05 was taken to be significant. Significant variables were considered for analysis via simple linear regression.

## Simple Linear Regression
Simple linear regression was performed to compare teen birth rate vs. single parent frequency and to compare single parent frequency vs. poverty rate using the SLOPE, INTERCEPT, and RSQ functions in excel. The values were likewise plotted on a scatterplot and fitted with a line representing the simple linear regression. Since the spread for each dataset was moderate to severe (the highest R-squared value was .533), outliers were not considered, as it is expected that several would have qualified using two standard errors from predicted values as a criteria. The Slope, Intercept and R-squared value for each location and comparison were summarized in a table.

All tables and plots were organized into figures within the main [README.md](https://github.com/mehurlock94/comparing-baltimore-sussex-county-teen-birth-economic-outcomes/blob/main/README.md)

