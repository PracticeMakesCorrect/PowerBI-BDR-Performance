This DAX formula calculates individual targets by dividing team targets by team sizes across multiple years and quarters. Includes error handling (IFERROR) and multiple nested lookups. Useful for target-setting and data normalization for sales teams.

![My Image](images/)


```dax
Indiv_Goal = IFERROR(
    SWITCH(
        Sales_Data[Created_Quarter],
        "2022-Q1",
            ROUND(
                LOOKUPVALUE(Ref_2022_Goals[Q1_Goal], Ref_2022_Goals[Goal_Team], LOOKUPVALUE(Ref_2022_Q1_Teams[Goal_Team], Ref_2022_Q1_Teams[Rep], Sales_Data[Rep]))
                / LOOKUPVALUE(Ref_2022_Team_Sizes[H1_Size], Ref_2022_Team_Sizes[Sales_Team], LOOKUPVALUE(Ref_2022_Q1_Teams[Sales_Team], Ref_2022_Q1_Teams[Rep], Sales_Data[Rep])),
                0),

        "2022-Q2",
            ROUND(
                LOOKUPVALUE(Ref_2022_Goals[Q2_Goal], Ref_2022_Goals[Goal_Team], LOOKUPVALUE(Ref_2022_Q2_Teams[Goal_Team], Ref_2022_Q2_Teams[Rep], Sales_Data[Rep]))
                / LOOKUPVALUE(Ref_2022_Team_Sizes[H1_Size], Ref_2022_Team_Sizes[Sales_Team], LOOKUPVALUE(Ref_2022_Q2_Teams[Sales_Team], Ref_2022_Q2_Teams[Rep], Sales_Data[Rep])),
                0),

        "2022-Q3",
            ROUND(
                LOOKUPVALUE(Ref_2022_Goals[Q3_Goal], Ref_2022_Goals[Goal_Team], LOOKUPVALUE(Ref_2022_Q3_Teams[Goal_Team], Ref_2022_Q3_Teams[Rep], Sales_Data[Rep]))
                / LOOKUPVALUE(Ref_2022_Team_Sizes[H2_Size], Ref_2022_Team_Sizes[Sales_Team], LOOKUPVALUE(Ref_2022_Q3_Teams[Sales_Team], Ref_2022_Q3_Teams[Rep], Sales_Data[Rep])),
                0),

        "2022-Q4",
            ROUND(
                LOOKUPVALUE(Ref_2022_Goals[Q4_Goal], Ref_2022_Goals[Goal_Team], LOOKUPVALUE(Ref_2022_Q4_Teams[Goal_Team], Ref_2022_Q4_Teams[Rep], Sales_Data[Rep]))
                / LOOKUPVALUE(Ref_2022_Team_Sizes[H2_Size], Ref_2022_Team_Sizes[Sales_Team], LOOKUPVALUE(Ref_2022_Q4_Teams[Sales_Team], Ref_2022_Q4_Teams[Rep], Sales_Data[Rep])),
                0),

        //////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

        "2023-Q1",
            ROUND(
                LOOKUPVALUE(Ref_2023_Goals[Q1_Goal], Ref_2023_Goals[Goal_Team], LOOKUPVALUE(Ref_2023_Q1_Teams[Goal_Team], Ref_2023_Q1_Teams[Rep], Sales_Data[Rep]))
                / LOOKUPVALUE(Ref_2023_Team_Sizes[Team_Size], Ref_2023_Team_Sizes[Sales_Team], LOOKUPVALUE(Ref_2023_Q1_Teams[Goal_Team], Ref_2023_Q1_Teams[Rep], Sales_Data[Rep])),
                0),

        "2023-Q2",
            ROUND(
                LOOKUPVALUE(Ref_2023_Goals[Q2_Goal], Ref_2023_Goals[Goal_Team], LOOKUPVALUE(Ref_2023_Q2_Teams[Goal_Team], Ref_2023_Q2_Teams[Rep], Sales_Data[Rep]))
                / LOOKUPVALUE(Ref_2023_Team_Sizes[Team_Size], Ref_2023_Team_Sizes[Sales_Team], LOOKUPVALUE(Ref_2023_Q2_Teams[Goal_Team], Ref_2023_Q2_Teams[Rep], Sales_Data[Rep])),
                0),

        "2023-Q3",
            ROUND(
                LOOKUPVALUE(Ref_2023_Goals[Q3_Goal], Ref_2023_Goals[Goal_Team], LOOKUPVALUE(Ref_2023_Q3_Teams[Goal_Team], Ref_2023_Q3_Teams[Rep], Sales_Data[Rep]))
                / LOOKUPVALUE(Ref_2023_Team_Sizes[Team_Size], Ref_2023_Team_Sizes[Sales_Team], LOOKUPVALUE(Ref_2023_Q3_Teams[Goal_Team], Ref_2023_Q3_Teams[Rep], Sales_Data[Rep])),
                0),

        "2023-Q4",
            ROUND(
                LOOKUPVALUE(Ref_2023_Goals[Q4_Goal], Ref_2023_Goals[Goal_Team], LOOKUPVALUE(Ref_2023_Q4_Teams[Goal_Team], Ref_2023_Q4_Teams[Rep], Sales_Data[Rep]))
                / LOOKUPVALUE(Ref_2023_Team_Sizes[Team_Size], Ref_2023_Team_Sizes[Sales_Team], LOOKUPVALUE(Ref_2023_Q4_Teams[Goal_Team], Ref_2023_Q4_Teams[Rep], Sales_Data[Rep])),
                0),

        //////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

        "2024-Q1",
            ROUND(
                LOOKUPVALUE(Ref_2024_Goals[Q1_Goal], Ref_2024_Goals[Goal_Team], LOOKUPVALUE(Ref_2024_Q1_Teams[Goal_Team], Ref_2024_Q1_Teams[Rep], Sales_Data[Rep]))
                / LOOKUPVALUE(Ref_2024_Team_Sizes[Team_Size], Ref_2024_Team_Sizes[Sales_Team], LOOKUPVALUE(Ref_2024_Q1_Teams[Goal_Team], Ref_2024_Q1_Teams[Rep], Sales_Data[Rep])),
                0),

        "2024-Q2",
            ROUND(
                LOOKUPVALUE(Ref_2024_Goals[Q2_Goal], Ref_2024_Goals[Goal_Team], LOOKUPVALUE(Ref_2024_Q2_Teams[Goal_Team], Ref_2024_Q2_Teams[Rep], Sales_Data[Rep]))
                / LOOKUPVALUE(Ref_2024_Team_Sizes[Team_Size], Ref_2024_Team_Sizes[Sales_Team], LOOKUPVALUE(Ref_2024_Q2_Teams[Goal_Team], Ref_2024_Q2_Teams[Rep], Sales_Data[Rep])),
                0),

        "2024-Q3",
            ROUND(
                LOOKUPVALUE(Ref_2024_Goals[Q3_Goal], Ref_2024_Goals[Goal_Team], LOOKUPVALUE(Ref_2024_Q3_Teams[Goal_Team], Ref_2024_Q3_Teams[Rep], Sales_Data[Rep]))
                / LOOKUPVALUE(Ref_2024_Team_Sizes[Team_Size], Ref_2024_Team_Sizes[Sales_Team], LOOKUPVALUE(Ref_2024_Q3_Teams[Goal_Team], Ref_2024_Q3_Teams[Rep], Sales_Data[Rep])),
                0),

        "2024-Q4",
            ROUND(
                LOOKUPVALUE(Ref_2024_Goals[Q4_Goal], Ref_2024_Goals[Goal_Team], LOOKUPVALUE(Ref_2024_Q4_Teams[Goal_Team], Ref_2024_Q4_Teams[Rep], Sales_Data[Rep]))
                / LOOKUPVALUE(Ref_2024_Team_Sizes[Team_Size], Ref_2024_Team_Sizes[Sales_Team], LOOKUPVALUE(Ref_2024_Q4_Teams[Goal_Team], Ref_2024_Q4_Teams[Rep], Sales_Data[Rep])),
                0)
    ),
    0
)
