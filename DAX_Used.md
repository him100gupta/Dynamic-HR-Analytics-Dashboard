## DAX
Custom DAX measures are utilized to provide precise and insightful KPIs, as well as to format charts, ensuring they remain dynamic and responsive.

### Custom DAX measures for KPIs: -

+ Total Employees
``` SQL
Total Employees = COUNT(HR_Analytics[EmployeeCount]) ```

+ Average Age
``` SQL
Average Age = AVERAGE(HR_Analytics[Age]) 
