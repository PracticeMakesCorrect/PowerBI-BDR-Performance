This DAX formula finds the person who manages each rep depending on the fiscal quarter. This is useful for keeping track of reps changing teams so that when one filtes to a particular fiscal quarter and manager, the reps shown are always correct. 


![My Image](images/Manager-Hierarchy.PNG)


```dax
Team_Lead_Structure = 
VAR CurrentRep = Sales_Performance_Overview[Rep_Name]
VAR CurrentFiscalPeriod = Sales_Performance_Overview[Fiscal_Period]
VAR CurrentYear = LEFT(CurrentFiscalPeriod, 4)
VAR CurrentQuarter = RIGHT(CurrentFiscalPeriod, 2)
VAR TeamLead = 
    CALCULATE(
        SELECTEDVALUE(Org_Chart[Team_Lead]),
        Org_Chart[Year] = CurrentYear,
        Org_Chart[Quarter] = CurrentQuarter,
        Org_Chart[Rep_ID] = CurrentRep
    )
RETURN
    TeamLead
