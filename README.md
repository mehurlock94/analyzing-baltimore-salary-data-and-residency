# Analyzing Baltimore employee data relative to permanent residency

## Background
In recent years, Baltimore has seen its fair share of [corruption](https://www.npr.org/2020/02/27/809929622/ex-baltimore-mayor-to-be-sentenced-for-healthy-holly-children-s-book-scheme), which has caused many departments of the city government to come under fire. A noteable current initiative, [project Baltimore](https://foxbaltimore.com/news/project-baltimore), seeks to identify shortcomings and deception within Baltimore schools. One effort to reduce malfeasance, is to require select, typically high ranking, city officials to [reside within city limits](https://www.baltimoresun.com/maryland/baltimore-city/bs-md-ci-city-council-20180312-story.html). While officials will never publicly report their opinions, one might assume that once one earns enough money, they will seek living situations outside the city in an effort to escape [Baltimore crime](https://www.baltimorecountymd.gov/departments/police/crimestats/). 

This analysis seeks to identify trends amongst individuals who elect to live outside the city. Using [publicly-available](https://data.baltimorecity.gov/) city employee data, the decision to make home beyond city limits is weighed against key factors like lenght of employment and base salary.

## Business Question
__Does increased income of city employees lead them to live outside of city limits?__

## Data Question - Open Data
All data from this analysis comes from the [Opportunity Atlas Project](https://www.opportunityatlas.org/) organized by tract. Files were downloaded for each location and combined into the files here:

- [Employee Salaries](https://github.com/mehurlock94/analyzing-baltimore-salary-data-and-residency/blob/main/Baltimore_Employee_Salaries.csv)
- [Employee Permanent Residencies](https://github.com/mehurlock94/analyzing-baltimore-salary-data-and-residency/blob/main/Baltimore_City_Employee_Residency_by_Agency.csv)

For detailed workflow, please see [data analysis](https://github.com/mehurlock94/analyzing-baltimore-salary-data-and-residency/blob/main/data-analysis-workflow)

## Data Question - Analysis
Microsoft Excel was used to answer the following:
1. __Do higher earnings correlate with the choice to live outside of Baltimore city limits?__ Employeed data included city agency, time of employment, salary, gross income, and percent of employees within that agency living outside of city limits.
2. __Are there professions which are more prone to living outside of city limits?__ Use heat mapping to identify professions that most often elect to live outside city limits.
3. __Are there logical groupings to the professions that live outside the city?__ Cluster analysis on employee data to see where there is overlap in characteristics, then qualitatively summarize professions.

## Data Answer
__Do higher earnings correlate with the choice to live outside of Baltimore city limits?__
![error](https://github.com/mehurlock94/analyzing-baltimore-salary-data-and-residency/blob/main/MLR_balt_employees.png)

A multiple linear regression analysis of employeed data, showed that both time of employment and gross income are significant predictors (p<0.05) of the percetages of employees choosing to live outside the city. However, the intercept likewise carries a fair amount of significance, indicating that other variables, not analyzed here, are contributing to the decision to leave the city. To get an isolated look at each variable, simple linear regression (SLR) was performed on plots using time of employment and gross salary as the independent variable.

![error](https://github.com/mehurlock94/analyzing-baltimore-salary-data-and-residency/blob/main/Balt_time_living.png)

SLR between average time as a city employee and living location shows a weak correlation (R-squared = 0.0296). The slope of the line indicates that one year of employment (365 days) will lead to a 0.9% decrease in number of employees living in the city. 

![error](https://github.com/mehurlock94/analyzing-baltimore-salary-data-and-residency/blob/main/Balt_income_living.png)

SLR between average employee gross income and living location shows a stronger but moderate correlation (R-squared = 0.3824). The slope of the line indicates that a $1,000 increase in gross income results in a 0.4% decrease in the number of employees living in the city.

__Are there professions which are more prone to living outside of city limits?__
![error](https://github.com/mehurlock94/analyzing-baltimore-salary-data-and-residency/blob/main/Balt_dept_heat_map.png)

While time of employment and income are predictors of whether an emplyee chooses to live in the city, their weak R-squared values suggest that other factors influence this decision. To visualize this, a heat map was generated to identify departments with the highest and lowest percentage of employees living within the city. 

![error](https://github.com/mehurlock94/analyzing-baltimore-salary-data-and-residency/blob/main/Balt_dept_heat_map_top_hits.png)

This analysis revealed the top three departments to live in the city are summer crossing guard, general crossing guard, and elections officials. These are all part-time or temporary positions. The bottom three departments to live in the city are the police department, the comptroller (audits), and the fire department. The connection between these professions is less clear, but their average time of employment ranks in the mid-range and their average gross salary are among the highest (see below).

__Are there logical groupings to the professions that live outside the city?__
![error](https://github.com/mehurlock94/analyzing-baltimore-salary-data-and-residency/blob/main/Balt_dep_cluster_heat_map.png)

To better understand how departments group, a cluster analysis was used analyzing time of employment, average salary, average gross income, percentage of employees within the city, and total number of emplyees. From this analysis, Cluster #2 (Anchor = Fire Department) and Cluster #3 (Anchor = States Attorneys Office) had the lowest number of employees that live within city limits. For Cluster #2, the departments are DPW-Water & Waste Water, Fire Department, and Police Department. These professions can generally be referred to as trade jobs and first responders. This outcome is consistent with the previous analysis to identify departments with the lowest number of individuals within the city. For Cluster #3, the professions are either financial or legal in nature. Neither grouping contains the highest paying jobs, though their average gross salaries are among the upper range. Cluster #5 (Anchor = R&P-Parks) has the highest prevalence of employees residing in the city and is among the lowest in both time of employment and gross income. While the professions are variant, they can be generally summarized under transportation authority, public buildings or parks, and part-time or temporary employment. Finally, Cluster #1 demonstrates that the highest paying departments are in the mid-range of departments which reside within the city.

## Data Interpretation


