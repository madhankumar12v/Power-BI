## Reference Notes:

#### 1.Measure column

#### 2.Calculated Column

#### 3.SUM vs SUMX

#### 4.Creating DAX Measure Tables

#### 5.Creating Folders and SubFolders

#### 6.Measures as Filter (Ex:Switch(SelectedValue(columnName)),value1,Result1,value2,Result2,....else)

#### 7.Calculated Function (syntax:Calculate(Expression,[Filter1,[filter2,...]]) 
    
- Boolean Filter Expression
  
Ex:Calculate(sum(columnName)),KeepFilters(ColumnName="Furniture")

- Table Filter Expression
  
Ex1:Calculate(sum(columnName)),Filter(TableName,T.ColumnName="Furniture")
Ex2:Calculate(sum(columnName)),KeepFilters(ColumnName="Furniture")&&ColumnName[Date]=ColumnName[Date]

- Filter Modification Function 
  
Syntax:Divide(Numerator,Denominator,AlternateResult)
  
Ex1:Divide(sum[ColumnName],Calculate(sum[ColumnName]),All[ColumnName]),0)


### 8.UserRelationShip:
 syntax: Calculate(Expression,[Filter1],...)
  
       Count([ColumnName])
  
	   UserRelationShip[ColumnName1],[ColumnName2]

  Ex: No of Shipment=Calculate(Count[ColumnName]),UserRelationShip[ColumnName1],[ColumnName2]

### 9.Calendar:
  
syntax: Calendar(Start Date,End Date)
  
Ex: Calendar(Date(Year,Month,Day),Date(Year,Month,Day))

### 10.LOOKUPVALUE:(Multiple Condition)
  
syntax: LOOKUPVALUE(result_ColumnName,Search_ColumnName1,Search_Value1,
Search_ColumnName2,Search_Value2,AlternateResult)

### 11.Related:(One Condition)
  
Syntax: Related(Result Column)

- WithOut Variables
  
ISBLANK[ColumnName]
  
IF(Expression,ResultIfTrue,ResultIfFalse)
  
Syntax: IF(ISBLANK(SUM[ColumnName]),0,SUM[ColumnName])

- With Variables

  Example:
sales_with_variable=
var Sales = SUM([ColumnName])

Return
IF(ISBLANK(sales),0,sales)

### 12.All 
Its Remove Both Visual and Outside Filter
syntax: ALL(ColumnName or TableName)

### 13.ALLSELECTED
Its Remove Only Visual Filter
Syntax: ALLSELECTED(ColumnName or TableName)

### 14.ALLEXCEPT
Its Applied Only Specified Columns
Syntax: ALLEXCEPT(TableName,ColumnName)

### 15.Concatenate (notes:Use formula or Use & symbol)
It concatenates two strings
strings can include text or numbers
  
Syntax: Concatenate(text1,text2)

### 16.Concatenatex
Concatenates the result of an expression evaluated for each row in a table
  
Syntax: CONCATENATE(table,expression,delimiter)

- with Duplicates
  
Ex2: Concatenatex(TableName,ColumnName,"delimiter",orderby ColumnName,ASC)

- WithOut Duplicates:
  
Ex1:Concatenatex(Values(TableName),ColumnName,"delimiter",orderby ColumnName,ASC)
  
Syntax:Values(ColumnName or TableName)

### 17.SYNC Slicer
### 18.Cross highlighting/Filtering
### 19.how to disable cross highlighting/Filtering

### 20.SAMEPERIODLASTYEAR
Ex1:
  last year sales=CALCULATE(SUM(ColumnName),SAMEPERIODLASTYEAR(columnName))

OR 

  Ex2:
  Growth %=
  
  Var current_year_sales=SUM(ColumnName)
  
  Var last_year_sales=CALCULATE(SUM(ColumnName)),SAMEPERIODLASTYEAR(ColumnName)
  
  Return
  
  DIVIDE(current_year_sales-last_year_sales,last_year_sales,0)

### 21.dateadd
Syntax: DATEADD(Dates,NumberOfIntervals,Interval)
