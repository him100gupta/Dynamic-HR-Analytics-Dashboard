## DAX
Custom DAX measures are utilized to provide precise and insightful KPIs, as well as to format charts, ensuring they remain dynamic and responsive.

### Custom DAX measures for KPIs: -

+ Total Employees
``` SQL
Total Employees = COUNT(HR_Analytics[EmployeeCount])
```

+ Average Age
``` SQL
Average Age = AVERAGE(HR_Analytics[Age]) 
```

+ Average Tenure
``` SQL
Average years at company = AVERAGE(HR_Analytics[YearsAtCompany])
```

+ Attrition
``` SQL
Attrition = CALCULATE(COUNTROWS(HR_Analytics), HR_Analytics[Attrition] = 1)
```

+ Attrition Rate
``` SQL
Attrition Rate = DIVIDE([Attrition], [Total Employees])
```

+ Average Salary
``` SQL
Average salary = AVERAGE(HR_Analytics[MonthlyIncome])
```

+ Average Overtime
``` SQL
Employee with overtime = (COUNTROWS(FILTER(HR_Analytics, HR_Analytics[OverTime] = "Yes"))/COUNTROWS(HR_Analytics))
```

+ Average Salary Hike
``` SQL
Percent salary Hike = AVERAGE(HR_Analytics[PercentSalaryHike])/ 100
```

+ Average HourlyRate
``` SQL
Average Hourly rate = AVERAGE(HR_Analytics[HourlyRate])
```

+ Average Training Time
``` SQL
Average training time = AVERAGE(HR_Analytics[TrainingTimesLastYear])
```

+ Trained Employee
``` SQL
Employee with last year training = (COUNTROWS(FILTER(HR_Analytics, HR_Analytics[TrainingTimesLastYear] > 0)) / COUNTROWS(HR_Analytics))
```

+ Employee Promotion
``` SQL
Perntage of employess promoted = (COUNTROWS(FILTER(HR_Analytics, HR_Analytics[YearsSinceLastPromotion] > 0)) / COUNTROWS(HR_Analytics))
```

+ Job Satisfaction
``` SQL
Average job satisfaction rating = AVERAGE(HR_Analytics[JobSatisfaction])
```
### Custom DAX measures for conditional formatting: -

+ Job Rating by Active employee's: - This will format the matrix to display the number of employees who rated 1-2, highlighting cases where the employee count for these ratings exceeds 20.
``` SQL
CountEmployeesByRating = 
CALCULATE( COUNT(HR_Analytics[EmpID]),VALUES(HR_Analytics[JobSatisfaction]) )
```
``` SQL
ConditionalColoring = 
IF( SELECTEDVALUE(HR_Analytics[JobSatisfaction]) IN {1, 2} && [CountEmployeesByRating] > 20,  "#FF0000", "#FFFFFF" )
```
