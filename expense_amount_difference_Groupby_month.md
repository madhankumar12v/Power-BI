### If you want to calculate only the expense amount difference without the percentage, you can modify the formula as follows:

```
Expense Diff =
IF(
    ISFILTERED('Sheet1'[Date]),
    ERROR("Time intelligence quick measures can only be grouped or filtered by the Power BI-provided date hierarchy or primary date column."),
    VAR __PREV_MONTH =
        CALCULATE(
            SUM('Sheet1'[Expense]),
            DATEADD('Sheet1'[Date].[Date], -1, MONTH)
        )
    RETURN
        SUM('Sheet1'[Expense]) - __PREV_MONTH
)

```
* In this modified formula, the variable __PREV_MONTH calculates the sum of expenses for the previous month using the CALCULATE and DATEADD functions.

* The RETURN statement calculates the expense amount difference by subtracting the previous month's expense total from the current month's expense total using the SUM function.

* The result will be the difference in expense amounts between the current month and the previous month.
