# Looking at How to Group Different Baltimore City Government Healthcare Worker Jobs Based on Different Salary & Hiring Variables

This project serves to determine natural groupings among Baltimore City government healthcare worker employees. Being able to determine these groups is an important initial analysis tool to show how many employees are in each group, how large the group is, and how they are related. Businesses and Baltimore City Government can use cluster information to improve their allocation of resources, productivity, and efficiency.

Baltimore City government has a history of [high employee turnover rates](https://www.baltimoresun.com/maryland/baltimore-city/bs-md-ci-commissioner-turnover-20180119-story.html). High turnover rates often [negatively affect the productivity and efficiency of the institution and is often caused by lack of recognition (i.e. lack of overtime pay)](https://smallbusiness.chron.com/causes-effects-high-low-staff-turnover-33939.html). Baltimore City can use these findings as an initial analysis about how their employees are grouped and how to improve on the allocation of salaries to bolster productivity and improve turnover rates.

This project uses Baltimore City government employee salary data. As a college resident and possibly a future healthcare employee in Baltimore City, it is interesting to see how these different factors group employees. Number of years worked in government, annual salary (annual salary based on employment contract), gross pay (actual annual earned income), and difference between annual and gross salaries are the independent variables explored to cluster Baltimore City's healthcare workers.

# Business Question
How can different employees be grouped based on number of years worked, annual salary, gross pay, and difference between annual and gross salaries?

# Data Question
How are healthcare workers grouped based on number of years worked, annual salary, gross pay, and difference between annual and gross salaries?

# Data Source
**Baltimore City Open Data:** This is a collection of publically available data on Baltimore City, which includes information and datasets on city government, services, housing & development, crime & public safety, culture & arts, finances, geography, health, neighborhoods, public works, and transportation.
This project looks at the Baltimore City Open Data's [Baltimore City Employee Salary](https://data.baltimorecity.gov/City-Government/Baltimore-City-Employees-Salaries/w28m-utix) dataset, which looks at Baltimore City employee salaries from FY2011 through FY2020.

# Step-by-Step Data Analysis
1. Number of years worked ("YearsWorked") was found by subtracting "HireDate" from the end of the current fiscal year (6/30/2020) and dividing by 365
2. 314 rows of data were deleted to reduce the chance of skewing the results because they did not have a value in HireDate. This deletion was insignificant because there are 154,649 rows in total
3. Dataset was then filtered to employees with "Health" in their job title to filter the dataset to the healthcare worker population
4. "DiffSalary" was calculated by subtracting "GrossPay" from "AnnualSalary"
5. Scatterplots comparing two variables at a time were created to visually determine approximately how many clusters exist in the dataset
6. Mean and standard deviation of the independent variables ("YearsWorked", "AnnualSalary", "GrossPay", "DiffSalary") using the AVERAGE and STDEV functions
7. "YearsWorked", "AnnualSalary", "GrossPay", "Diff Salary" were normalized using the STANDARDIZE function and put into the "z YearsWorked", "z AnnualSalary", "z GrossPay", "z Diff Salary" columns
8. An anchor table was created using the VLOOKUP function, which contained Anchor Number, "EmployeeNum", "JobTitle", "z YearsWorked", "z AnnualSalary", "z GrossPay", "z Diff Salary"
9. SUMXMY2 function was used to calculate the distance squared between the first, second, third, fourth, and fifth points
10. Minimum distance squared and sum of minimum distance squared were calculated for each row using the MIN and SUM functions
11. MATCH function was then used to calculate which row of z scores is associated with which anchor
12. Excel Solver was used to evaluate optimal clusters on the anchor table based on the minimum distance to each of the cluster nodes

# Data Answer
![alt text](https://github.com/achow6/clustering-baltimore-city-salaries/blob/main/Scatter%20Plot.png)

During the data analysis process, scatterplots were created (i.e. comparing YearWorked to Annual Salary and comparing YearsWorked and GrossPay) as an initial investigation into the dataset for this cluster analysis. This is an example of one of the scatterplot comparisons. It compares gross pay and years worked. All of the scatterplots generally exhibited five similar clusters, so a five-cluster analysis was conducted.

![alt text](https://github.com/achow6/clustering-baltimore-city-salaries/blob/main/Clusters.png)

This is the Solver output for the five-cluster analysis. 

The first cluster is the smallest (748 individuals) and is characterized by employees who have not worked under the government for very long and have a much higher (above average) contract salary than actual (below average) income. There is a large gap between their contract and actual salaries.

The second cluster is represented by 2,961 employees who have worked the least amount of time under the government and have a lower (below average) contract and (way below average) actual salary. There is a large gap between their contract and actual salaries, but it is smaller than the first cluster.

The third cluster is represented by 2,993 employees who have worked under the government for a long time and have a high (above average) contract and (above average) actual income. Their actual income is slightly greater than their contract salary.

The fourth cluster is characterized by 1,078 employees who have not worked under the government for very long and have above average contract and annual incomes. There is a large gap between their contract and actual salaries; this group actually earns much more than their contract dictates.

The fifth cluster is the largest (3001 individuals) and is represented by employees who have worked under the government for the longest and have high contract and actual salaries. They also earn more than their contract dictates, but the gap is less than the one seen in the fourth cluster.

# Business Answer
This cluster analysis suggests that there are five groups within Baltimore City's healthcare workers based on number of years worked, annual salary, gross pay, and difference between annual and gross salaries. The analysis suggests that in general, clusters of employees who work for a longer time receive a higher gross salary, whereas clusters of employees who work for a shorter time receive lower/average salaries. Additional research is needed to determine if there is an association between years worked and salary.

Additional data on level of education and number of hours worked per week (part/full time) could be helpful in investigating more clusters or determine associations between variables. This is helpful for businesses to determine how their employees are grouped and how that could affect their productivity. With more research, this could also help them determine how to allocate their resources (salary) and improve employee loyalty.

For Baltimore City government, specifically, this data shows how their healthcare workers could be grouped under the variables investigated in this project. With additional research on additional variables, such as education, number of hours worked per week (part/full time), and specific job titles (doctor, nurse, etc), these clusters can be refined and could change the groupings of these healthcare workers. Using these groupings as an initial analysis, Baltimore City government could perform additional analysis (linear regression, correlation calculations, etc), to determine associations and correlations, which could help determine where and how to allocate resources (salary) and improve employee loyalty.

