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

For detailed workflow, please see [data analysis](https://github.com/mehurlock94/analyzing-baltimore-salary-data-and-residency/blob/main/data-analysis-workflow.md)

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
The results of this analysis both confirmed the initial hypothesis and uncovered an additional explanation for choice to live outside the city. First, the linear regression confirmed that both time of employment and gross salary are weak and moderate predictors, respectively, of whether a department's employees live outside the city. One thing to point out is the gross income of employees would generally be expected to increase as time of employment increases. The number of temporary or part-time positions may disrupt this trend slightly, although more analysis is needed to confirm this. In general, the idea that a higher earning employee would want to live in the suburbs is expected based on [previous trends](https://grist.org/cities/no-the-rich-are-not-all-moving-to-the-city-now/). Indeed, some of the [reasons](https://www.movers.com/moving-guides/reasons-why-people-move-to-the-suburbs-from-the-city.html) people leave the city for the suburbs include cheaper living, lower crime, more room, and better schools. Surveys of Baltimore employees would be needed to confirm these claims, but it is worth noting that Baltimore suburubs are superior to the city in [education](https://www.niche.com/k12/search/best-school-districts/s/maryland/) and [crime rate](https://www.opportunityatlas.org/).

An interesting result came from the cluster analysis, to show that first responders, financial employees, and legal employees are among the those choosing to live outside the city the most frequently. While they are not the highest earners, financial employees and legal employees do make within the higher range of gross incomes, suggesting that their decision to live outside the city is, at least in part, correlated with their earnings. The more striking population is first responders, especially since recent events have sparked [debates](https://www.police1.com/law-enforcement-policies/articles/state-your-case-should-there-be-residency-requirements-for-sworn-personnel-o2OspoSS7WiN1aRv/) on whether police officers should be [required to live](https://www.usatoday.com/story/news/nation/2020/06/13/police-residency-data/5327640002/) in the city they service. As with any of these groupings, surveying employees would be the most telling information to know why first responders choose to live in adjacent counties. Potential [homogeneity](https://journals.ametsoc.org/view/journals/bams/95/2/bams-d-12-00183.1.xml) among first responders and their related lifestyles would be a good area to investigate. Another possiblity is first responders prefer to live further away to distance themselves from [traumas](https://ohsonline.com/articles/2020/01/21/mental-health-and-first-responders-how-their-jobs-can-cause-more-than-just-stress.aspx) experienced while on the job.

On the opposite end of the spectrum, those choosing to live within the city are temporary or part-time positions, transportation authority and public buildings or parks. Some are expected, as positions like [election workers](https://www.eac.gov/voters/become-poll-worker) typically come from those living within a given community. Another factor to point out is that these positions are among the lowest time of employment and gross income. As noted above, a confounding variable comes from requirements for city officials, who make up the top earners, to [live within city limits](https://www.baltimoresun.com/maryland/baltimore-city/bs-md-ci-city-council-20180312-story.html). This removes the ability for some officials to choose to live outside the city and may encourage those not required to stay as well, though this is speculative. In all cases, gathering more information on Baltimore employee preferences and lifestyles would make it possbile to build a stronger model for understanding why employees choose to live outside the city where they work.
