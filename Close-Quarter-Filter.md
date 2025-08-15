This DAX formula dynamically determines the current fiscal quarter using TODAY() and LOOKUPVALUE, then calculates a filter for the next four quarters with FILTER and SELECTCOLUMNS. Good for future-proofing a slicer. 


![My Image](images/)


```dax
Last4ClosedQuarters = 
VAR CQ = TODAY()
VAR CQ_Formatted = 
    VAR QuarterStart = STARTOFQUARTER(CQ)
    VAR LastClosedQuarterStart = 
        IF(
            CQ >= QuarterStart,
            STARTOFQUARTER(DATEADD(CQ, -3, MONTH)),
            QuarterStart
        )
    RETURN
        FORMAT(LastClosedQuarterStart, "YYYY") & "-Q" & QUARTER(LastClosedQuarterStart)
VAR QTR_NUM = 
    LOOKUPVALUE(
        FQ_FY_CLOSE_FILTER[FQ_Count],
        FQ_FY_CLOSE_FILTER[FQ],
        CQ_Formatted
    )
VAR FQ_VALUES = 
    DISTINCT(
        SELECTCOLUMNS(
            FILTER(
                FQ_FY_CLOSE_FILTER,
                FQ_FY_CLOSE_FILTER[FQ_Count] >= QTR_NUM - 3 &&
                FQ_FY_CLOSE_FILTER[FQ_Count] <= QTR_NUM
            ),
            "FQ",
            FQ_FY_CLOSE_FILTER[FQ]
        )
    )
VAR OUTPUT = FQ_VALUES
RETURN
    OUTPUT
