# Kickstarter Analysis

## Project Overview

Analysis was previously preformed to help a playwrite named Louise launch her Kickstarter campaign to fund her production *Fever*. Louse's campaign neared its goal quickly after launching. She has asked for more information on how campaigns similar to her's fared, specifically with regard to their launch date and the funding goal of the campaign.

### Purpose

This project was performed to investigate the possible relationship between the outcome of a Kickstarter campaign with respect to either its launch date or its fundraising goal.

 In order to provide relevant results, the campaigns included must be similar to Louise's. Since her campaign is a theatrical production, campaigns included in the analysis should fall into this category.
## Analysis and Challenges

### The Data Set

The data utilized in this analysis consisted of 4114 Kickstarter campaigns and relavent descriptive and numerical information about them. 

Examples of included information:
- Campaign Name
- Fundraising Goal
- Outcome of the campaign
- Parent and Subcategory
- Launch and End Dates

Microsoft Excel was used to perform the Analysis.

### Analysis of Outcomes Based on Launch Date

To explore this relationship the data first needed to be refined. The data set contains campaigns with Launch dates in different years. To allow a more granular look, the year needed to be extracted from the existing date.

This was done useing YEAR() function. For example:

     =YEAR(6/22/2015)
would return the value 2015.

After extracting the year of each launch into a seperate column, a Pivot Table was created to relate the specific data of interest.

The rows were filled with the Launch Date, specifically the month. The columns hold the Outcomes with the values representing the number of each Outcome in a particular Month.

Using a Filter on the Columns, "Live" was excluded as an outcome. Parent Category and Years were added as Filters. For this analysis, Parent Category was filtered to "Theatre".

From this table, a Pivot Chart was created to visualize the relationship between the month a campaign with Parent Category of "Theatre" was launched and whether it was successful, failed, or canceled. A line chart was chosen to clearly represent the counts of the three outcomes over time, shown below.

![Outcomes vs Launch Date Chart](/Resources/Theatre_Outcomes_vs_Launch.png)

### Analysis of Outcomes Based on Goals

A new worksheet was created to collect data extracted from the original Kickstarter worksheet. One way to view this relationship is by finding the percentage of each Outcome that falls within a set range of Fundraising Goals. As an example, the percentage of campagins that Failed with a Fundraising Goal between $25000 and $29999. To accomplish this, the rows of the sheet were broken up into Goal ranges and the columns represent the count of each outcome in that range. Additionally, to comform with the initial question, only campaigns with the Subcategory of "Play" were considered.

To find the number of campains that would within these limits, the COUNTIFS() function was used. A representative use from the worksheet:

     =COUNTIFS(Kickstarter!$F:$F,"=successful",Kickstarter!$D:$D,">=10000",Kickstarter!$R:$R,"=plays",Kickstarter!$D:$D,"<=14999")

The formula above uses COUNTIFS() to count the number of times all of these critera are met at the same index in the specified range. Each range references the worksheet Kickstarter that holds the data set. This particular statement counts campaigns with a successful Outcome with a Goal between 10000 and 14999 and a Subcategory of plays.

Slightly modified versions were used to populate counts for the Outcomes (live excluded). To check for errors a COUNTIFS() was used with only Outcome and the Subcategory to ensure the total for each Outcome was correct. The SUM() Function was then applied to find the total number of campaigns within each fundraising Goal bracket.

Using the Total for each Goal bracket, the percentage was calculated by dividing the counted number by the total and formating the results as a percentage.

     =B3/E3 and (CTRL+SHIFT+%)
     =(388)/(534) and (CTRL+SHIFT+%)


 Which yields 73 percent.

 To visualize this relationship a line chart was created displaying the percentage part of each Goal bracket made up by each outcome, this chart is shown below.
 
 ![Outcomes vs Goals Chart](/Resources/Outcomes_vs_Goals.png)

### Challenges and Difficulties Encountered

A principle difficulty encounted during the second analysis was an inconsistency in the counting of the failed campaigns with COUNTIFS(). This was resolved by determining what the total count of failed play campaigns should be and reviewing the formulas that had been entered. This led to the discovery of several serious typos that altered the meaning of the COUNTIFS() function but did not cause it to return an error.

A potential difficulty in the first analysis is correctly formatting the rows of the pivot table. Useing the Date Launched column presents multiple options for display. It is advantageous to choose months for readability given the table can be filtered by year. Moreover, the Pivot Chart would not be as readable without the rows in months.
## Results

### Outcome vs Lauch Date

Viewing all years, there is a clear spike in successful outcomes for theatre campagns started in May. Likewise there is a spike in October for the number that fail, however, it is still lower than the number of successful campaigns. The only time the number of successful and fail campaigns are nearly the same is when launched in December.

Generally, Kickstarter Campaigns in the Theatre Parent Category appear to be Successful more often than not in every month except December. May has the largest difference between successful and failed but it also is the month with the highed number of Launched campaigns.

Launching in May could hold the best outcome, but it is a more crowded field. While October still has more successful Launches than failures, the peak suggests against launching in October. The number of cancelled campaigns is consistent throughout the year.

### Outcomes vs Goals

In the Subcategory plays, no campaigns were canceled. This results the line representing successful in the percentage share of each Goal bracket being a mirror image of failed.

Successful play campaigns represent a larger percentage when the Goal is up to $19,999 and between $35,000 and $45,000.

The rate at which the percentage failed play campaigns increases after $1,000 before slowing after $9,999. This suggests that a goal of less that $9,999 may lead to a successful outcome in a larger proportion of campaigns.

### Limitations of the Dataset

This dataset represents a general view of Kickstarter campaigns. The data of interest is only a subset, a larger sample would produce a larger subset and allow for stronger conclusions.

Multiple contries are represented in the data. It has not been explored whether or not the Kickstarter usage habits varies between each of these nations. Some of the data used for the analysis is not derived from the country where it is to be applied.

The manner in which the data was obtained is unspecified and it is unclear if it reprents a general subset of the Kickstarter Campaign population.

### Further Inquiry

- It may be useful to create a table to break the Outcome vs. Launch data into Subcategories to explore if different types of theatre campaigns differ in optimal Launch Date. A chart of the same form that was created for the broader theatre data would provide visual insight into the specific play Sub Category Outcomes.
- Louise's production has a comparitivley small goal when compared to larger goals for campaigns in the play Sub Category. A chart focused on goals up to $10,000 with smaller brackets may provide new insignt that is more specific to the purpose of this analysis.
