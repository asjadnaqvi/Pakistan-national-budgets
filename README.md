# Pakistan Budgets

The interactive visualizations can be viewed here: 

*   [2024-25](https://public.flourish.studio/visualisation/18741763/) 
*  [2023-24](https://public.flourish.studio/visualisation/14291446/) 


and the partial data files can be downloaded here:

*   [2023 - 2024](./2023_2024)
*   [2024 - 2025](./2024_2025)


## Background

This repository scrapes data from federal budgets that are released as PDFs by the [Ministry of Finance, Government of Pakistan](https://www.finance.gov.pk/)

Individual budget files are in their respective folders. 

Note that numbers are added up from the lowest `ID6` category. If the lowest category is missing in the published budgets, then this will be automatically missing from the tables. These entries are relatively few though and are updated as the budget files are revised. 

Also note that actual spending can be different than the allocated amount. This can be checked in budget files which also provide allocation and revised numbers for *(N-1)* fiscal year.

*Disclaimer*: The files are generated using pattern recognition scripts which had to be fine tuned over several iterations. The files can contain errors. If you come across data issues, then please report them as soon as possible. This is a hobby project to improve my data scraping skills. Therefore, if you intend to use this data for research and policy work, please double check the original source files. Also note that budget files are intermittently updated so the data might only reflect the version downloaded at the time of scraping the data. A full cleaning is possible but this requires a proper fully-funded project. 




## Description of the variables

| Variable | Type | Description | 
| --- | --- | --- |
| `fund` | num | Name of the fund e.g. current expenditure, capital expenditure, consolidated funds etc. | 
| `ministry_name` | str | Ministry name | 
| `division_name` | str | Name of the division | 
| `ID1_name` | str | Name of the first level  | 
| `ID2_name` | str | Name of the second level   | 
| `ID3_name` | str | Name of the third level   | 
| `ID4_name` | str | Name of the fourth level   | 
| `ID5_name` | str | Name of the fifth level   | 
| `ID6_name` | str | Name of the sixth (lowest) level   | 
| `posts_<N-1>` | num | The number of posts (jobs) in year **N-1**.  | 
| `posts_<N>` | num | The number of posts (jobs) in year **N**.  | 
| `budget_<N-1>` | num | The value in PKR of item `ID6` in fiscal year **N-1**. | 
| `budget_<N-1>_revised` | num | The value in PKR of item `ID6` revised in fiscal year **N-1**. | 
| `budget_<N>` | num | The value in PKR of item `ID6` in fiscal year **N**. | 




## Change log
* 20 Jul 2024: Budgets for FY2023 and FY2024 added. Previous years removed due to a cleaning issue. Might be added later.
* 03 Jul 2022: Budget for the year 2022-2023 added.
* 07 Jul 2021: Budget for the year 2020-2021 added. Fund categories added. Minor fixes to categories. In order to merge the different budget years, a careful look at the sub-categories are needed. Especially if the category IDs are changing over time. 
* 06 Jul 2021: The format of the budgets have changed after they were approved in the Assembly. They no longer contain information on the previous year. I have redone 2021-22 budgets and have added the names of the ministries and the Demand for grant categories. This should give a better overall picture. The visualization for 2021-22 budget has also been upgraded. 2020-21 files have been removed for now and will be added back once the files are updated.
* 28 Jun 2021: Documentation added for the tables in the markdown. Page description improved considerably.
* 26 Jun 2021: Budget for 2021-2022 is scrapped from PDFs. The scripts are improved to weed out the errors in data matching. Some `1D6` categories were being skipped since the columns were messed up. The other main issues was that entries with single columns were not being assigned to the correct column. While most fit a generic pattern, not all might end up in the correct column. This was the bulk of the fine tuning. These should be extremely few and should ONLY matter if analyzing the data at the highest level of disaggregation, i.e. `ID6`. Please report these if you find them.
* Jul 2020: Budget for 2020-2021 is scrapped from PDFs. The core scripts are put in place to sort and order the table entries. 
