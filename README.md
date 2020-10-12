# Looking at How to Group Different Baltimore City Government Healthcare Worker Jobs Based on Different Salary & Hiring Variables

This project serves to determine natural groupings among Baltimore City government healthcare worker employees. Being able to determine these groups is an important initial analysis tool to show how many employees are in each group, how large the group is, and how they are related. Businesses can use this information to improve their allocation of resources, productivity, and efficiency.
Number of years worked in government, annual salary (annual salary based on employment contract), gross pay (actual annual earned income), and difference between annual and gross salaries are the independent variables explored to cluster Baltimore City's healthcare workers.
This project uses Baltimore City government employee salary data. As a college resident and possibly a future healthcare employee in Baltimore City, it is interesting to see how these different factors group employees. Baltimore City can use these findings as an initial analysis about how their employees are grouped and how to improve on the allocation of salaries to bolster productivity.

# Business Question
How are different employees grouped based on number of years worked, annual salary, gross pay, and difference between annual and gross salaries?

# Data Question
How are healthcare workers grouped based on number of years worked, annual salary, gross pay, and difference between annual and gross salaries?

# Data Source
**Baltimore City Open Data:** This is a collection of publically available data on Baltimore City, which includes information and datasets on city government, services, housing & development, crime & public safety, culture & arts, finances, geography, health, neighborhoods, public works, and transportation.
This project looks at the Baltimore City Open Data's [Baltimore City Employee Salary](https://data.baltimorecity.gov/City-Government/Baltimore-City-Employees-Salaries/w28m-utix) dataset, which looks at Baltimore City employee salaries from FY2011 through FY2020.

# Data Analysis
Once the original dataset was downloaded, number of years worked ("YearsWorked") was found by subtracting "HireDate" from the end of the current fiscal year (6/30/2020) and dividing by 365. 314 rows of data were deleted to reduce the chance of skewing the results because they did not have a value in HireDate. This deletion was insignificant because there are 154,649 rows in total. The dataset was then filtered to employees with "Health" in their job title to filter the dataset to the healthcare worker population. "DiffSalary" was calculated by subtracting "GrossPay" from "AnnualSalary"
Mean and standard deviation of the independent variables ("YearsWorked", "AnnualSalary", "GrossPay", "DiffSalary") using the AVERAGE and STDEV functions. The numbers in "YearsWorked", "AnnualSalary", "GrossPay", "Diff Salary" were normalized using the STANDARDIZE function and put into the "z YearsWorked", "z AnnualSalary", "z GrossPay", "z Diff Salary" columns. An anchor table was then created using the VLOOKUP function, which contained Anchor Number, "EmployeeNum", "JobTitle", "z YearsWorked", "z AnnualSalary", "z GrossPay", "z Diff Salary". The SUMXMY2 function was used to calculate the distance squared between the first, second, third, fourth, and fifth points. Minimum distance squared and sum of minimum distance squared were calculated for each row using the MIN and SUM functions. The MATCH function was then used to calculate which row of z scores is associated with which anchor. Finally, Excel Solver was used to evaluate optimal clusters on the anchor table based on the minimum distance to each of the cluster nodes.

# Data Answer
![alt text](https://github.com/achow6/clustering-baltimore-city-salaries/blob/main/Scatter%20Plot.png)

This is a scatterplot comparison between gross pay and years worked. As an initial investigation for this cluster analysis, we can see that there are approximately five clusters, so a five-cluster analysis was conducted on the data. 

![alt text](https://github.com/achow6/clustering-baltimore-city-salaries/blob/main/Clusters.png)

This is the Solver output for the five-cluster analysis. The first cluster is characterized by employees who have not worked under the government for very long and have a much higher (above average) contract salary than actual (below average) income. There is a large gap between their contract and actual salaries.
The second cluster is represented by employees who have worked the least amount of time under the government and have a lower (below average) contract and (way below average) actual salary. There is a large gap between their contract and actual salaries, but it is smaller than the first cluster.
The third cluster is represented by employees who have worked under the government for a long time and have a high (above average) contract and (above average) actual income. Their actual income is slightly greater than their contract salary.
The fourth cluster is characterized by employees who have not worked under the government for very long and have above average contract and annual incomes. There is a large gap between their contract and actual salaries; this group actually earns much more than their contract dictates.
The fifth cluster is represented by employees who have worked under the government for the longest and have high contract and actual salaries. They also earn more than their contract dictates, but the gap is less than the one seen in the fourth cluster.

# Business Answer
This cluster analysis suggests that there are five groups within Baltimore City's healthcare workers based on number of years worked, annual salary, gross pay, and difference between annual and gross salaries. The clusters suggest that in general, employees who work for a longer time receive a higher gross salary, whereas employees who work for a shorter time receive lower/average salaries. Additional data on level of education and number of hours worked per week could be helpful in investigating more clusters or determine associations/correlations between variables. This is helpful for businesses to determine how their employees are grouped and how that could affect their productivity. With more research, this could also help businesses improve employee loyalty.

