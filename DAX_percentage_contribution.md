### To calculate the percentage contribution of each category in relation to the total expenses, you can use the following DAX formula:

```
Category Contribution % =
IF (
    ISFILTERED ( 'Sheet1'[Date] ),
    ERROR ( "Time intelligence quick measures can only be grouped or filtered by the Power BI-provided date hierarchy or primary date column." ),
    VAR TotalExpenses =
        CALCULATE ( SUM ( 'Sheet1'[Expense] ), ALL ( 'Sheet1'[Category] ) )
    RETURN
        DIVIDE ( SUM ( 'Sheet1'[Expense] ), TotalExpenses )
)

```
### Here's how the formula works:

* It checks if the 'Date' column is filtered using ISFILTERED('Sheet1'[Date]). If it is filtered, an error message is returned to ensure the formula is only applied when the 'Date' column is not filtered.

* It calculates the total expenses across all categories using the CALCULATE and ALL functions. The ALL function removes any filtering applied to the 'Category' column.

* It returns the percentage contribution of each category by dividing the sum of expenses for each category by the total expenses (DIVIDE(SUM('Sheet1'[Expense]), TotalExpenses)).

* This formula calculates the percentage contribution of each category in relation to the total expenses in the 'Sheet1' table.
