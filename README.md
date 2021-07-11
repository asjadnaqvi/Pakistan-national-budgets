## Background

This repository scrapes data from federal budgets that are released as PDFs by the [Ministry of Finance, Government of Pakistan](https://www.finance.gov.pk/)

Individual budget files are in their respective folders. 

*Note*: The files are generated using pattern recognition scripts, a lot of which had to be fine tuned. The files can contain errors. If you come across some data issues, then please report them as soon as possible.



## Description of the variables

| Variable | Type | Description | 
| --- | --- | --- |
| `year` | num | Year of the budget. E.g. 2021 represents the 2021-2022 budget. | 
| `category` | num | **Current** or **Development** budget. | 
| `ministry` | str | Ministry serial number (Greek numbers). | 
| `ministry_name` | str | Ministry name. | 
| `fund` | num | Fund category.  | 
| `dfg` | num | Demand for Grants: internal serial number. | 
| `dfg_id` | str | Demand for Grants: official serial number. | 
| `dfg_name` | str | Demand for Grants: official name. | 
| `ID1` | num | The 1st level budget category. Contains ten values.  | 
| `ID1_name` | str | The names of ID1.  | 
| `ID2` | num | The 2nd level budget category. |
| `ID2_name` | str | The names of ID2.  | 
| `ID3` | num | The 3rd level budget category. |
| `ID3_name` | str | The names of ID3.  | 
| `ID4` | num | The 4th level budget category. |
| `ID4_name` | str | The names of ID4.  | 
| `ID5` | num | The 5th level budget category. |
| `ID5_name` | str | The names of ID5.  | 
| `ID6` | num | The 6th level budget category. |
| `ID6_name` | str | The names of ID6. This is the highest disaggregated level.  | 
| `level` | num | The level of the data disaggregation for `ID6`. Level 1 is the total for the `ID6` category. Level 2 adds up to level 1. Level 3 adds up to level 2. |
| `posts_<N>` | num | The number of posts (jobs) in year **N**.  | 
| `posts_<N>_revised` | num | The number of posts (jobs) revised in fiscal year **N**.  | 
| `budget_<N>` | num | The value in PKR of item `ID6` `level` in fiscal year **N**. | 
| `budget_<N>_revised` | num | The value in PKR of item `ID6` `level` revised in fiscal year **N**. | 

*Note:* When comparing the values across the years remember to deflate them using some  inflation index.


## Interactive visualizations:

<div class="flourish-embed flourish-hierarchy" data-src="visualisation/6533369"><script src="https://public.flourish.studio/resources/embed.js"></script></div>


The interactive visualizations are made in [Flourish](https://flourish.studio/), an online dataviz platform. Since this is all open-source, the visualizations can be duplicated and edited:

**2021-2022:** https://public.flourish.studio/visualisation/6533369/

**2020-2021:** https://public.flourish.studio/visualisation/2841995/


The visualizations use `ID6` `level` 1 data.

<br />


## Change log

* 07 Jul 2021: Budget year 2020-2021 added. Fund categories added. Minor fixes to categories. In order to merge the different budget years, a careful look at the sub-categories are needed. Especially if the category IDs are changing over time. 
* 06 Jul 2021: The format of the budgets have changed after they were approved in the Assembly. They no longer contain information on the previous year. I have redone 2021-22 budgets and have added the names of the ministries and the Demand for grant categories. This should give a better overall picture. The visualization for 2021-22 budget has also been upgraded. 2020-21 files have been removed for now and will be added back once the files are updated.
* 28 Jun 2021: Documentation added for the tables in the markdown. Page description improved considerably.
* 26 Jun 2021: Budget for 2021-2022 is scrapped from PDFs. The scripts are improved to weed out the errors in data matching. Some `1D6` categories were being skipped since the columns were messed up. The other main issues was that entries with single columns were not being assigned to the correct column. While most fit a generic pattern, not all might end up in the correct column. This was the bulk of the fine tuning. These should be extremely few and should ONLY matter if analyzing the data at the highest level of disaggregation, i.e. `ID6`. Please report these if you find them.
* Jul 2020: Budget for 2020-2021 is scrapped from PDFs. The core scripts are put in place to sort and order the table entries. 
