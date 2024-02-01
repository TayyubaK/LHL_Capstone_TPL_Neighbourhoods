# LHL Capstone - Profile of Library Use by Toronto Neighbourhoods

The Toronto Public Library network is a city service comprising of 100 physical branches spread out within the 158 neighbourhoods of Toronto. Libraries allow borrowing of physical and electronic materials, but can also be a hub for community programs and resources.

During COVID-19 access to physical branches was restricted, and recently, in late 2023 the Toronto Public Library faced a major cybersecurity incident. The purpose of this analysis is to take a look at how libraries are faring before, during, and after the challenges, and how they're being used in Toronto.


## Project/Goals
Use data analysis techinques to explore, wrangle, and create user-friendly informative visuals about the use of Toronto libraries. 

### Tech Stack
* Excel
* Python
* Jupyter Notebooks
* Tableau

## Process
### Step 1 - Data Acquisition

Datasets were obtained from the Toronto city’s [Open Data Portal](https://open.toronto.ca/catalogue/)
* [Neighbourhood Profiles (2021)](https://open.toronto.ca/dataset/neighbourhood-profiles/) – sourced from a number of Census tables released by Statistics Canada 
* [Neighbourhoods GeoJSON file (June 2022)](https://open.toronto.ca/dataset/neighbourhoods/)
* [Library Branch General Information (2023)](https://open.toronto.ca/dataset/library-branch-general-information/)
* [Library Workstation Usage (2012-2022)](https://open.toronto.ca/dataset/library-workstation-usage/) 
* [Library Visits (2012-2022)](https://open.toronto.ca/dataset/library-visits/) 
* [Library Circulation (2012-2022)](https://open.toronto.ca/dataset/library-circulation/) 
* [Library Card Registrations (2012-2022)](https://open.toronto.ca/dataset/library-card-registrations/) 

Dataset from the Toronto Police Public Safety Data Portal
* [Neighbourhood Crime Rates Open Data (2014-2023)](https://data.torontopolice.on.ca/datasets/ea0cfecdb1de416884e6b0bf08a9e195_0/explore)

### Step 2 - Data Exploration/Wrangling
Excel
* Preliminary view of data
* Spot checks on files as they were modified/cleaned

Jupyter Notebooks
* Cleaned and modified layout of data tables (layouts for use in regression model are differnt then table layout for Tableau)
    * Branch-level statistics were aggregated to neighbourhood-level 
* Created a regression model with backward selection for visits in 2019 against neighbourhood crime statistics, neighbourhood demographics (education, employement, income), and other library usage measures. No meaningful statistically significant relationship was found.

Tableau
* Loaded tables and created joins/relationships
* Created visualizations to show library locations, neighbourhood incomes and library size/year of establishment, library usage trends, neighbourhood-level and branch-level KPI measures (visits, registrations, workstation use (sessions), and circulations)

## Results
* Based on 2019 data, no statistical significance between visits to library and crime statistics or neighbourhood demographics (education, employment, income).
* Toronto has many libraries that were established in their current location decades ago. The Yorkville library in the Annex neighbourhood has been in its present site since 1907!
* Considering median income for all Toronto neighbourhoods, most libraries are located in neighbourhoods on the lower half of the income scale.
* Overall library usage measures show a negative trend from 2012-2022. 
    * However, if you limit the data to 2012-2019 (before COVID), the downward trend for visits, circulation, and sessions existed beforehand as well, although less severely. Registrations (new library cards issued) had a positive trend.
    * Looking at post-COVID recovery (2021-2022), all 4 measures show a positive trend. However, the incline for circulations (checkouts of physical and electronic media) is not as steep. It could be worth looking into what is impacting this measure.

## Challenges 
* Not all neighbourhoods have a physical library branch. Merging neighbourhood-level data and branch-level data initially caused issues with some neighbourhoods dropping off. Even knowing which neighbourhoods have no branches is useful information. This was addressed to a degree with sourcing the filter from the neighbourhood-level data.
* Scope creep - originally neighbourhood crime stats were cleaned and reviewed as well. However the dataset was very large and did not add more to the question about libraries. Ultimately the dataset was not used for visualizations.
* The best table layouts for regression model building were different than what was best for Tableau. Separate data wrangling was required for each purpose.
* Datasets were for different levels of granularity and for different time intervals. Data manipulation required careful consideration of data integrity and time period compatibility between datasets.

![Data_Matrix](https://github.com/TayyubaK/LHL_Capstone_TPL_Neighbourhoods/assets/143013434/d604d41e-e82f-47cb-9142-589d9655a02b)

## Future Goals
* Create postgreSQL database with normalized tables - would make it easier to drill up/down, make custom tables
* Rework Tableau layout with added neighbourhood demographic information and different drill-up/drill-down interactivity.
* Explore classification models instead of regression models. Perhaps neighbourhood classification has an impact on library usage measurements.
* Explore relationships between crime statistics and neighbourhoods as the dataset has already been cleaned.




