
[![image](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DBishal13/Data-Engineering-and-Vizualization/blob/main/code/Data%20Engineering%20Notebook.ipynb)
## Data engineering

This notebook describes downloading and preparing United States presidential election data. You will address missing values, reformat data types, and restructure the format of a table.

***

## Load and prepare data

You will use ArcPy, ArcGIS API for Python, and a Pandas data frame to download and prepare the election data. First, you will import these modules to use them. Then, you will create a variable for the United States county election data and use this variable to read the data into a Pandas data frame.

* Import needed modules

* Read data into Python

## Handle missing data 
The election data includes records that are missing data in the FIPS field. This missing data is referred to as null values. You will identify how many rows have null values and create a new data frame that does not include them.

## Explore and handle data types

Reviewing your data shows that the FIPS field is considered a numeric field instead of a string. As a result, leading zeroes in the FIPS values have been removed. The resulting FIPS values only have four characters instead of five. You will determine how many records are missing leading zeroes and add or append the missing zero.

## Reformat the table structure

Currently, each record in the table corresponds to a candidate and their votes in a county. We reformatted the table so each record corresponds to each county, with fields showing the votes for different candidates in that election year. 
It is possible to do this using the [Pivot Table geoprocessing tool](https://pro.arcgis.com/en/pro-app/tool-reference/data-management/pivot-table.htm) or Excel pivot tables, but Python may make it easier to automate and share.

## Calculate additional columns

You will use the values from the updated table to add additional columns of information, such as the number of votes for a non-major party, the percentage of voters for each party, and so on. Each column is referred to as an attribute of the dataset.

* Calculate an attribute for the total votes for non-major party

* Calculate additional attributes

## Geoenable the data

You will eventually use this data in a spatial analysis. This means that the data needs to include location information to determine where the data is located on a map. You will geo-enable the data using County data that has already been geocoded. Geocoded data is location data that has been assigned a street address.

There are various resources that you can use to find geo-enabled data. [ArcGIS Living Atlas of the World](https://livingatlas.arcgis.com) is an authoritative source provided by Esri. Each record in your election data represents information for a county, so you will use a Living Atlas dataset that represents county geometry. This dataset has been downloaded and added to your project.


The county geometry dataset includes various attributes. You will simplify the data frame only to include the needed attributes. The Total_cvap_est attribute represents the total population in each county of voting age for 2016.

***

## Join the data

You have a data frame with election data ('df_out') and a spatially-enabled data frame of the county geometry data ('counties_df'). You will merge these datasets into one. 

The resulting data frame includes the attributes from your election data and the specified attributes from the county geometry data. The SHAPE field represents the county geometry and is used to locate each record, or feature, on the map.

***

## Query and calculate attributes

Because you have the voting age population for 2016, you can now calculate the average voter participation (voter turnout) for 2016. 

You will calculate a new field named voter turnout using field operators in Pandas. The operations will apply to all values across the columns. 

***

## Validate the data

Before you continue with other data preparation, you should ensure the output data has been successfully created. 

First, you will validate the values for voter turnout. You will remove null values, and because these values represent a fraction (total votes divided by voting age population), you will confirm that the values range between 0 and 1.

The describe function indicates voter turnout values over one, indicating a turnout above 100%. You can go ahead and investigate by asking for these records.

Four counties with deficient populations resulted in voter turnout values above 100%. You could remove these records from the data or do additional research to identify the source of this issue. 

***

## Update validated data

After reviewing the Census Bureau voting age population data for 2016, you determined that these counties have a low voting age population with a fairly high margin of error. This may be the reason why these counties have a voter turnout rate higher than 100%. You will recalculate the voter turnout field for these counties using the upper range of their margin of error: 
- San Juan County, Colorado: 574
- Harding County, New Mexico: 562
- Loving County, Texas: 86
- McMullen County, Texas: 566

**Note: This information was extracted from this [table](https://data.census.gov/cedsci/table?q=voting%20age%20population%202016&g=0500000US08111,35021,48301,48311&hidePreview=true&table=DP05&tid=ACSDP5Y2016.DP05&t=Age%20and%20Sex&y=2016&lastDisplayedRow=6&vintage=2016&mode=&moe=true).**

To confirm that this correction addressed the issue, you will again query for counties with a voter turnout value above 100%.

No records are returned, indicating that there are no counties with a turnout value above 100%. Well done! You have cleaned the data. Next, you will convert the dataframe to a permanent dataset called a feature class. Feature classes are stored in an ArcGIS Pro file geodatabase.

***

## Convert data frames to feature classes

You will use the ArcGIS API for Python, imported at the beginning of this script, to export the spatially-enabled data frame to a feature class.


## Correct for missing data

The feature class needs a county in South Dakota. You'll be able to correct this issue by exploring the data further.

The county geometry dataset identifies the missing county as Oglala Lakota County. By searching online for this county, you determine that Oglala Lakota County changed its county name and FIPS in 2015. It was originally Shannon County with a FIPS of 46113 and is now Oglala Lakota County with a FIPS of 46102. You will search the election data for the current FIPS to find the missing data.

There is the issue! The data has the correct name (Oglala Lakota) but the wrong FIPS (46113). You will correct this data issue.

With the corrected FIPS value for Oglala Lakota County, you can now rejoin the geometry, recalculate the voting turnout field, and recreate the feature class. 

You will export the data frame to a feature class that you can visualize and analyze in ArcGIS Pro. 
