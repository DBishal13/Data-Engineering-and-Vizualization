
[![image](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DBishal13/Data-Engineering-and-Vizualization/blob/main/code/Data%20Engineering%20Notebook.ipynb)
## Data engineering

This notebook describes the process of downloading and preparing United States presidential election data. You will address missing values, reformat data types, and restructure the format of a table.

***

## Load and prepare data

You will use ArcPy, ArcGIS API for Python, and a Pandas data frame to download and prepare the election data. First, you will import these modules to use them. Then, you will create a variable for the United States county election data and use this variable to read the data into a Pandas data frame.

* Import needed modules

* Read data into Python

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>state</th>
      <th>state_po</th>
      <th>county</th>
      <th>FIPS</th>
      <th>office</th>
      <th>candidate</th>
      <th>party</th>
      <th>candidatevotes</th>
      <th>totalvotes</th>
      <th>version</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2016</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>Autauga</td>
      <td>1001</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>democratic</td>
      <td>5936.0</td>
      <td>24973</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2016</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>Autauga</td>
      <td>1001</td>
      <td>President</td>
      <td>Donald Trump</td>
      <td>republican</td>
      <td>18172.0</td>
      <td>24973</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>Autauga</td>
      <td>1001</td>
      <td>President</td>
      <td>Other</td>
      <td>NaN</td>
      <td>865.0</td>
      <td>24973</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2016</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>Baldwin</td>
      <td>1003</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>democratic</td>
      <td>18458.0</td>
      <td>95215</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2016</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>Baldwin</td>
      <td>1003</td>
      <td>President</td>
      <td>Donald Trump</td>
      <td>republican</td>
      <td>72883.0</td>
      <td>95215</td>
      <td>20190722</td>
    </tr>
  </tbody>
</table>
</div>

## Handle missing data 
The election data includes records that are missing data in the FIPS field. This missing data is referred to as null values. You will identify how many rows have null values and create a new data frame that does not include them.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>state</th>
      <th>state_po</th>
      <th>county</th>
      <th>FIPS</th>
      <th>office</th>
      <th>candidate</th>
      <th>party</th>
      <th>candidatevotes</th>
      <th>totalvotes</th>
      <th>version</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>9462</th>
      <td>2016</td>
      <td>Connecticut</td>
      <td>NaN</td>
      <td>Statewide writein</td>
      <td>NaN</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>democratic</td>
      <td>NaN</td>
      <td>5056</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>9463</th>
      <td>2016</td>
      <td>Maine</td>
      <td>NaN</td>
      <td>Maine UOCAVA</td>
      <td>NaN</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>democratic</td>
      <td>3017.0</td>
      <td>5056</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>9464</th>
      <td>2016</td>
      <td>Alaska</td>
      <td>NaN</td>
      <td>District 99</td>
      <td>NaN</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>democratic</td>
      <td>274.0</td>
      <td>5056</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>9465</th>
      <td>2016</td>
      <td>Rhode Island</td>
      <td>NaN</td>
      <td>Federal Precinct</td>
      <td>NaN</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>democratic</td>
      <td>637.0</td>
      <td>5056</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>9466</th>
      <td>2016</td>
      <td>Connecticut</td>
      <td>NaN</td>
      <td>Statewide writein</td>
      <td>NaN</td>
      <td>President</td>
      <td>Donald Trump</td>
      <td>republican</td>
      <td>NaN</td>
      <td>5056</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>9467</th>
      <td>2016</td>
      <td>Maine</td>
      <td>NaN</td>
      <td>Maine UOCAVA</td>
      <td>NaN</td>
      <td>President</td>
      <td>Donald Trump</td>
      <td>republican</td>
      <td>648.0</td>
      <td>5056</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>9468</th>
      <td>2016</td>
      <td>Alaska</td>
      <td>NaN</td>
      <td>District 99</td>
      <td>NaN</td>
      <td>President</td>
      <td>Donald Trump</td>
      <td>republican</td>
      <td>40.0</td>
      <td>5056</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>9469</th>
      <td>2016</td>
      <td>Rhode Island</td>
      <td>NaN</td>
      <td>Federal Precinct</td>
      <td>NaN</td>
      <td>President</td>
      <td>Donald Trump</td>
      <td>republican</td>
      <td>53.0</td>
      <td>5056</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>9470</th>
      <td>2016</td>
      <td>Connecticut</td>
      <td>NaN</td>
      <td>Statewide writein</td>
      <td>NaN</td>
      <td>President</td>
      <td>Other</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5056</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>9471</th>
      <td>2016</td>
      <td>Maine</td>
      <td>NaN</td>
      <td>Maine UOCAVA</td>
      <td>NaN</td>
      <td>President</td>
      <td>Other</td>
      <td>NaN</td>
      <td>321.0</td>
      <td>5056</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>9472</th>
      <td>2016</td>
      <td>Alaska</td>
      <td>NaN</td>
      <td>District 99</td>
      <td>NaN</td>
      <td>President</td>
      <td>Other</td>
      <td>NaN</td>
      <td>28.0</td>
      <td>5056</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>9473</th>
      <td>2016</td>
      <td>Rhode Island</td>
      <td>NaN</td>
      <td>Federal Precinct</td>
      <td>NaN</td>
      <td>President</td>
      <td>Other</td>
      <td>NaN</td>
      <td>38.0</td>
      <td>5056</td>
      <td>20190722</td>
    </tr>
  </tbody>
</table>
</div>

## Explore and handle data types

Reviewing your data shows that the FIPS field is considered a numeric field instead of a string. As a result, leading zeroes in the FIPS values have been removed. The resulting FIPS values only have four characters instead of five. You will determine how many records are missing leading zeroes and add or append the missing zero.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>state</th>
      <th>state_po</th>
      <th>county</th>
      <th>FIPS</th>
      <th>office</th>
      <th>candidate</th>
      <th>party</th>
      <th>candidatevotes</th>
      <th>totalvotes</th>
      <th>version</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2016</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>Autauga</td>
      <td>1001</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>democratic</td>
      <td>5936.0</td>
      <td>24973</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2016</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>Autauga</td>
      <td>1001</td>
      <td>President</td>
      <td>Donald Trump</td>
      <td>republican</td>
      <td>18172.0</td>
      <td>24973</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>Autauga</td>
      <td>1001</td>
      <td>President</td>
      <td>Other</td>
      <td>NaN</td>
      <td>865.0</td>
      <td>24973</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2016</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>Baldwin</td>
      <td>1003</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>democratic</td>
      <td>18458.0</td>
      <td>95215</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2016</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>Baldwin</td>
      <td>1003</td>
      <td>President</td>
      <td>Donald Trump</td>
      <td>republican</td>
      <td>72883.0</td>
      <td>95215</td>
      <td>20190722</td>
    </tr>
  </tbody>
</table>
</div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>state</th>
      <th>state_po</th>
      <th>county</th>
      <th>FIPS</th>
      <th>office</th>
      <th>candidate</th>
      <th>party</th>
      <th>candidatevotes</th>
      <th>totalvotes</th>
      <th>version</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2016</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>Autauga</td>
      <td>01001</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>democratic</td>
      <td>5936.0</td>
      <td>24973</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2016</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>Autauga</td>
      <td>01001</td>
      <td>President</td>
      <td>Donald Trump</td>
      <td>republican</td>
      <td>18172.0</td>
      <td>24973</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>Autauga</td>
      <td>01001</td>
      <td>President</td>
      <td>Other</td>
      <td>NaN</td>
      <td>865.0</td>
      <td>24973</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2016</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>Baldwin</td>
      <td>01003</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>democratic</td>
      <td>18458.0</td>
      <td>95215</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2016</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>Baldwin</td>
      <td>01003</td>
      <td>President</td>
      <td>Donald Trump</td>
      <td>republican</td>
      <td>72883.0</td>
      <td>95215</td>
      <td>20190722</td>
    </tr>
  </tbody>
</table>
</div>

## Reformat the table structure

Currently, each record in the table corresponds to a candidate and their votes in a county. You need to reformat the table so each record corresponds to each county, with fields showing the votes for different candidates in that election year. 
It is possible to do this using the [Pivot Table geoprocessing tool](https://pro.arcgis.com/en/pro-app/tool-reference/data-management/pivot-table.htm) or Excel pivot tables, but Python may make it easier to automate and share.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>FIPS</th>
      <th>year</th>
      <th>county</th>
      <th>state</th>
      <th>state_po</th>
      <th>office</th>
      <th>candidate_dem</th>
      <th>votes_dem</th>
      <th>candidate_gop</th>
      <th>votes_gop</th>
      <th>votes_total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>01001</td>
      <td>2016</td>
      <td>Autauga</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>5936.0</td>
      <td>Donald Trump</td>
      <td>18172.0</td>
      <td>24973</td>
    </tr>
    <tr>
      <th>1</th>
      <td>01003</td>
      <td>2016</td>
      <td>Baldwin</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>18458.0</td>
      <td>Donald Trump</td>
      <td>72883.0</td>
      <td>95215</td>
    </tr>
    <tr>
      <th>2</th>
      <td>01005</td>
      <td>2016</td>
      <td>Barbour</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>4871.0</td>
      <td>Donald Trump</td>
      <td>5454.0</td>
      <td>10469</td>
    </tr>
    <tr>
      <th>3</th>
      <td>01007</td>
      <td>2016</td>
      <td>Bibb</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>1874.0</td>
      <td>Donald Trump</td>
      <td>6738.0</td>
      <td>8819</td>
    </tr>
    <tr>
      <th>4</th>
      <td>01009</td>
      <td>2016</td>
      <td>Blount</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2156.0</td>
      <td>Donald Trump</td>
      <td>22859.0</td>
      <td>25588</td>
    </tr>
  </tbody>
</table>
</div>

## Calculate additional columns

You will use the values from the updated table to add additional columns of information, such as the number of votes for a non-major party, the percentage of voters for each party, and so on. Each column is referred to as an attribute of the dataset.

* Calculate an attribute for the total votes for non-major party

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>FIPS</th>
      <th>year</th>
      <th>county</th>
      <th>state</th>
      <th>state_po</th>
      <th>office</th>
      <th>candidate_dem</th>
      <th>votes_dem</th>
      <th>candidate_gop</th>
      <th>votes_gop</th>
      <th>votes_total</th>
      <th>votes_other</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>01001</td>
      <td>2016</td>
      <td>Autauga</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>5936.0</td>
      <td>Donald Trump</td>
      <td>18172.0</td>
      <td>24973</td>
      <td>865.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>01003</td>
      <td>2016</td>
      <td>Baldwin</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>18458.0</td>
      <td>Donald Trump</td>
      <td>72883.0</td>
      <td>95215</td>
      <td>3874.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>01005</td>
      <td>2016</td>
      <td>Barbour</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>4871.0</td>
      <td>Donald Trump</td>
      <td>5454.0</td>
      <td>10469</td>
      <td>144.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>01007</td>
      <td>2016</td>
      <td>Bibb</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>1874.0</td>
      <td>Donald Trump</td>
      <td>6738.0</td>
      <td>8819</td>
      <td>207.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>01009</td>
      <td>2016</td>
      <td>Blount</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2156.0</td>
      <td>Donald Trump</td>
      <td>22859.0</td>
      <td>25588</td>
      <td>573.0</td>
    </tr>
  </tbody>
</table>
</div>

* Calculate additional attributes
* 
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>FIPS</th>
      <th>year</th>
      <th>county</th>
      <th>state</th>
      <th>state_po</th>
      <th>office</th>
      <th>candidate_dem</th>
      <th>votes_dem</th>
      <th>candidate_gop</th>
      <th>votes_gop</th>
      <th>votes_total</th>
      <th>votes_other</th>
      <th>voter_share_major_party</th>
      <th>voter_share_dem</th>
      <th>voter_share_gop</th>
      <th>voter_share_other</th>
      <th>rawdiff_dem_vs_gop</th>
      <th>rawdiff_gop_vs_dem</th>
      <th>rawdiff_dem_vs_other</th>
      <th>rawdiff_gop_vs_other</th>
      <th>rawdiff_other_vs_dem</th>
      <th>rawdiff_other_vs_gop</th>
      <th>pctdiff_dem_vs_gop</th>
      <th>pctdiff_gop_vs_dem</th>
      <th>pctdiff_dem_vs_other</th>
      <th>pctdiff_gop_vs_other</th>
      <th>pctdiff_other_vs_dem</th>
      <th>pctdiff_other_vs_gop</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>01001</td>
      <td>2016</td>
      <td>Autauga</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>5936.0</td>
      <td>Donald Trump</td>
      <td>18172.0</td>
      <td>24973</td>
      <td>865.0</td>
      <td>0.965363</td>
      <td>0.237697</td>
      <td>0.727666</td>
      <td>0.034637</td>
      <td>-12236.0</td>
      <td>12236.0</td>
      <td>5071.0</td>
      <td>17307.0</td>
      <td>-5071.0</td>
      <td>-17307.0</td>
      <td>-0.489969</td>
      <td>0.489969</td>
      <td>0.203059</td>
      <td>0.693028</td>
      <td>-0.203059</td>
      <td>-0.693028</td>
    </tr>
    <tr>
      <th>1</th>
      <td>01003</td>
      <td>2016</td>
      <td>Baldwin</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>18458.0</td>
      <td>Donald Trump</td>
      <td>72883.0</td>
      <td>95215</td>
      <td>3874.0</td>
      <td>0.959313</td>
      <td>0.193856</td>
      <td>0.765457</td>
      <td>0.040687</td>
      <td>-54425.0</td>
      <td>54425.0</td>
      <td>14584.0</td>
      <td>69009.0</td>
      <td>-14584.0</td>
      <td>-69009.0</td>
      <td>-0.571601</td>
      <td>0.571601</td>
      <td>0.153169</td>
      <td>0.724770</td>
      <td>-0.153169</td>
      <td>-0.724770</td>
    </tr>
    <tr>
      <th>2</th>
      <td>01005</td>
      <td>2016</td>
      <td>Barbour</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>4871.0</td>
      <td>Donald Trump</td>
      <td>5454.0</td>
      <td>10469</td>
      <td>144.0</td>
      <td>0.986245</td>
      <td>0.465278</td>
      <td>0.520967</td>
      <td>0.013755</td>
      <td>-583.0</td>
      <td>583.0</td>
      <td>4727.0</td>
      <td>5310.0</td>
      <td>-4727.0</td>
      <td>-5310.0</td>
      <td>-0.055688</td>
      <td>0.055688</td>
      <td>0.451524</td>
      <td>0.507212</td>
      <td>-0.451524</td>
      <td>-0.507212</td>
    </tr>
    <tr>
      <th>3</th>
      <td>01007</td>
      <td>2016</td>
      <td>Bibb</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>1874.0</td>
      <td>Donald Trump</td>
      <td>6738.0</td>
      <td>8819</td>
      <td>207.0</td>
      <td>0.976528</td>
      <td>0.212496</td>
      <td>0.764032</td>
      <td>0.023472</td>
      <td>-4864.0</td>
      <td>4864.0</td>
      <td>1667.0</td>
      <td>6531.0</td>
      <td>-1667.0</td>
      <td>-6531.0</td>
      <td>-0.551536</td>
      <td>0.551536</td>
      <td>0.189024</td>
      <td>0.740560</td>
      <td>-0.189024</td>
      <td>-0.740560</td>
    </tr>
    <tr>
      <th>4</th>
      <td>01009</td>
      <td>2016</td>
      <td>Blount</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2156.0</td>
      <td>Donald Trump</td>
      <td>22859.0</td>
      <td>25588</td>
      <td>573.0</td>
      <td>0.977607</td>
      <td>0.084258</td>
      <td>0.893348</td>
      <td>0.022393</td>
      <td>-20703.0</td>
      <td>20703.0</td>
      <td>1583.0</td>
      <td>22286.0</td>
      <td>-1583.0</td>
      <td>-22286.0</td>
      <td>-0.809090</td>
      <td>0.809090</td>
      <td>0.061865</td>
      <td>0.870955</td>
      <td>-0.061865</td>
      <td>-0.870955</td>
    </tr>
  </tbody>
</table>
</div>


## Geoenable the data

You will eventually use this data in a spatial analysis. This means that the data needs to include location information to determine where the data is located on a map. You will geoenable the data using County data that has already been geocoded. Geocoded data is location data that has been assigned a street address.

There are various resources that you can use to find geoenabled data. [ArcGIS Living Atlas of the World](https://livingatlas.arcgis.com) is an authoritative source provided by Esri. Each record in your election data represents information for a county, so you will use a Living Atlas dataset that represents county geometry. This dataset has been downloaded and added to your project.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>OBJECTID</th>
      <th>COUNTYNS</th>
      <th>GEOID</th>
      <th>NAMELSAD</th>
      <th>GEONAME</th>
      <th>GEOID_1</th>
      <th>LNNUMBER</th>
      <th>Total_tot_est</th>
      <th>Total_adu_est</th>
      <th>Total_cit_est</th>
      <th>Total_cvap_est</th>
      <th>nHispLat_tot_est</th>
      <th>nHispLat_adu_est</th>
      <th>nHispLat_cit_est</th>
      <th>nHispLat_cvap_est</th>
      <th>AIAN_tot_est</th>
      <th>AIAN_adu_est</th>
      <th>AIAN_cit_est</th>
      <th>AIAN_cvap_est</th>
      <th>Asian_tot_est</th>
      <th>Asian_adu_est</th>
      <th>Asian_cit_est</th>
      <th>Asian_cvap_est</th>
      <th>BAA_tot_est</th>
      <th>BAA_adu_est</th>
      <th>BAA_cit_est</th>
      <th>BAA_cvap_est</th>
      <th>NHOPI_tot_est</th>
      <th>NHOPI_adu_est</th>
      <th>NHOPI_cit_est</th>
      <th>NHOPI_cvap_est</th>
      <th>White_tot_est</th>
      <th>White_adu_est</th>
      <th>White_cit_est</th>
      <th>White_cvap_est</th>
      <th>AIAN_W_tot_est</th>
      <th>AIAN_W_adu_est</th>
      <th>AIAN_W_cit_est</th>
      <th>AIAN_W_cvap_est</th>
      <th>Asian_W_tot_est</th>
      <th>Asian_W_adu_est</th>
      <th>Asian_W_cit_est</th>
      <th>Asian_W_cvap_est</th>
      <th>BAA_W_tot_est</th>
      <th>BAA_W_adu_est</th>
      <th>BAA_W_cit_est</th>
      <th>BAA_W_cvap_est</th>
      <th>AIAN_BAA_tot_est</th>
      <th>AIAN_BAA_adu_est</th>
      <th>AIAN_BAA_cit_est</th>
      <th>AIAN_BAA_cvap_est</th>
      <th>Rem_TOM_tot_est</th>
      <th>Rem_TOM_adu_est</th>
      <th>Rem_TOM_cit_est</th>
      <th>Rem_TOM_cvap_est</th>
      <th>HispLat_tot_est</th>
      <th>HispLat_adu_est</th>
      <th>HispLat_cit_est</th>
      <th>HispLat_cvap_est</th>
      <th>Shape__Area</th>
      <th>Shape__Length</th>
      <th>SHAPE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>00161526</td>
      <td>01001</td>
      <td>Autauga County</td>
      <td>Autauga County, Alabama</td>
      <td>05000US01001</td>
      <td>13</td>
      <td>55050</td>
      <td>41195</td>
      <td>54510</td>
      <td>40690</td>
      <td>53635</td>
      <td>40290</td>
      <td>53325</td>
      <td>40015</td>
      <td>225</td>
      <td>125</td>
      <td>225</td>
      <td>125</td>
      <td>485</td>
      <td>390</td>
      <td>340</td>
      <td>245</td>
      <td>10115</td>
      <td>7470</td>
      <td>10115</td>
      <td>7470</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
      <td>41795</td>
      <td>31835</td>
      <td>41635</td>
      <td>31705</td>
      <td>230</td>
      <td>220</td>
      <td>230</td>
      <td>220</td>
      <td>270</td>
      <td>140</td>
      <td>270</td>
      <td>140</td>
      <td>420</td>
      <td>50</td>
      <td>420</td>
      <td>50</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>90</td>
      <td>55</td>
      <td>90</td>
      <td>55</td>
      <td>1415</td>
      <td>905</td>
      <td>1185</td>
      <td>675</td>
      <td>2.208654e+09</td>
      <td>2.498864e+05</td>
      <td>{"rings": [[[-9619465, 3856529.0001000017], [-...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>00161527</td>
      <td>01003</td>
      <td>Baldwin County</td>
      <td>Baldwin County, Alabama</td>
      <td>05000US01003</td>
      <td>13</td>
      <td>199510</td>
      <td>155240</td>
      <td>195655</td>
      <td>151770</td>
      <td>190800</td>
      <td>149730</td>
      <td>188875</td>
      <td>148020</td>
      <td>1230</td>
      <td>1125</td>
      <td>1200</td>
      <td>1095</td>
      <td>1785</td>
      <td>1195</td>
      <td>1065</td>
      <td>615</td>
      <td>18500</td>
      <td>13570</td>
      <td>18245</td>
      <td>13315</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>166275</td>
      <td>132280</td>
      <td>165455</td>
      <td>131535</td>
      <td>1275</td>
      <td>795</td>
      <td>1275</td>
      <td>795</td>
      <td>590</td>
      <td>395</td>
      <td>500</td>
      <td>305</td>
      <td>1035</td>
      <td>260</td>
      <td>1035</td>
      <td>260</td>
      <td>55</td>
      <td>55</td>
      <td>55</td>
      <td>55</td>
      <td>50</td>
      <td>50</td>
      <td>45</td>
      <td>45</td>
      <td>8710</td>
      <td>5510</td>
      <td>6780</td>
      <td>3750</td>
      <td>5.671048e+09</td>
      <td>1.655940e+06</td>
      <td>{"rings": [[[-9746859, 3539643.0001000017], [-...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>00161528</td>
      <td>01005</td>
      <td>Barbour County</td>
      <td>Barbour County, Alabama</td>
      <td>05000US01005</td>
      <td>13</td>
      <td>26615</td>
      <td>20880</td>
      <td>26085</td>
      <td>20375</td>
      <td>25465</td>
      <td>20180</td>
      <td>25405</td>
      <td>20120</td>
      <td>45</td>
      <td>45</td>
      <td>45</td>
      <td>45</td>
      <td>120</td>
      <td>45</td>
      <td>110</td>
      <td>40</td>
      <td>12765</td>
      <td>9650</td>
      <td>12745</td>
      <td>9635</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>12390</td>
      <td>10340</td>
      <td>12360</td>
      <td>10310</td>
      <td>65</td>
      <td>65</td>
      <td>65</td>
      <td>65</td>
      <td>25</td>
      <td>0</td>
      <td>25</td>
      <td>0</td>
      <td>45</td>
      <td>20</td>
      <td>45</td>
      <td>15</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
      <td>1145</td>
      <td>700</td>
      <td>680</td>
      <td>250</td>
      <td>3.257902e+09</td>
      <td>3.208964e+05</td>
      <td>{"rings": [[[-9468394, 3771591.0001000017], [-...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>00161529</td>
      <td>01007</td>
      <td>Bibb County</td>
      <td>Bibb County, Alabama</td>
      <td>05000US01007</td>
      <td>13</td>
      <td>22570</td>
      <td>17815</td>
      <td>22345</td>
      <td>17590</td>
      <td>22070</td>
      <td>17440</td>
      <td>22050</td>
      <td>17415</td>
      <td>80</td>
      <td>45</td>
      <td>80</td>
      <td>45</td>
      <td>15</td>
      <td>15</td>
      <td>0</td>
      <td>0</td>
      <td>4790</td>
      <td>3875</td>
      <td>4790</td>
      <td>3875</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>16875</td>
      <td>13255</td>
      <td>16870</td>
      <td>13250</td>
      <td>65</td>
      <td>65</td>
      <td>65</td>
      <td>65</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>230</td>
      <td>170</td>
      <td>230</td>
      <td>170</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>15</td>
      <td>15</td>
      <td>15</td>
      <td>15</td>
      <td>500</td>
      <td>380</td>
      <td>295</td>
      <td>175</td>
      <td>2.311999e+09</td>
      <td>2.279184e+05</td>
      <td>{"rings": [[[-9692114, 3928124.0001000017], [-...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>00161530</td>
      <td>01009</td>
      <td>Blount County</td>
      <td>Blount County, Alabama</td>
      <td>05000US01009</td>
      <td>13</td>
      <td>57705</td>
      <td>44105</td>
      <td>55925</td>
      <td>42430</td>
      <td>52670</td>
      <td>41085</td>
      <td>52450</td>
      <td>40885</td>
      <td>170</td>
      <td>155</td>
      <td>170</td>
      <td>155</td>
      <td>90</td>
      <td>80</td>
      <td>75</td>
      <td>65</td>
      <td>905</td>
      <td>675</td>
      <td>895</td>
      <td>675</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>50710</td>
      <td>39710</td>
      <td>50580</td>
      <td>39580</td>
      <td>450</td>
      <td>360</td>
      <td>450</td>
      <td>360</td>
      <td>105</td>
      <td>75</td>
      <td>55</td>
      <td>25</td>
      <td>175</td>
      <td>25</td>
      <td>175</td>
      <td>25</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>60</td>
      <td>4</td>
      <td>45</td>
      <td>4</td>
      <td>5035</td>
      <td>3015</td>
      <td>3475</td>
      <td>1550</td>
      <td>2.456909e+09</td>
      <td>2.926429e+05</td>
      <td>{"rings": [[[-9623907, 4063676.0001000017], [-...</td>
    </tr>
  </tbody>
</table>
</div>

The county geometry dataset includes various attributes. You will simplify the dataframe to only include the attributes that you need. The Total_cvap_est attribute represents the total population in each county that are of voting age for the year 2016.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>OBJECTID</th>
      <th>GEOID</th>
      <th>GEONAME</th>
      <th>Total_cvap_est</th>
      <th>SHAPE</th>
      <th>Shape__Area</th>
      <th>Shape__Length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>01001</td>
      <td>Autauga County, Alabama</td>
      <td>40690</td>
      <td>{"rings": [[[-9619465, 3856529.0001000017], [-...</td>
      <td>2.208654e+09</td>
      <td>2.498864e+05</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>01003</td>
      <td>Baldwin County, Alabama</td>
      <td>151770</td>
      <td>{"rings": [[[-9746859, 3539643.0001000017], [-...</td>
      <td>5.671048e+09</td>
      <td>1.655940e+06</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>01005</td>
      <td>Barbour County, Alabama</td>
      <td>20375</td>
      <td>{"rings": [[[-9468394, 3771591.0001000017], [-...</td>
      <td>3.257902e+09</td>
      <td>3.208964e+05</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>01007</td>
      <td>Bibb County, Alabama</td>
      <td>17590</td>
      <td>{"rings": [[[-9692114, 3928124.0001000017], [-...</td>
      <td>2.311999e+09</td>
      <td>2.279184e+05</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>01009</td>
      <td>Blount County, Alabama</td>
      <td>42430</td>
      <td>{"rings": [[[-9623907, 4063676.0001000017], [-...</td>
      <td>2.456909e+09</td>
      <td>2.926429e+05</td>
    </tr>
  </tbody>
</table>
</div>



***

## Join the data

You have a data frame with election data ('df_out') and a spatially-enabled data frame of the county geometry data ('counties_df'). You will merge these datasets into one. 

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>FIPS</th>
      <th>year</th>
      <th>county</th>
      <th>state</th>
      <th>state_po</th>
      <th>office</th>
      <th>candidate_dem</th>
      <th>votes_dem</th>
      <th>candidate_gop</th>
      <th>votes_gop</th>
      <th>votes_total</th>
      <th>votes_other</th>
      <th>voter_share_major_party</th>
      <th>voter_share_dem</th>
      <th>voter_share_gop</th>
      <th>voter_share_other</th>
      <th>rawdiff_dem_vs_gop</th>
      <th>rawdiff_gop_vs_dem</th>
      <th>rawdiff_dem_vs_other</th>
      <th>rawdiff_gop_vs_other</th>
      <th>rawdiff_other_vs_dem</th>
      <th>rawdiff_other_vs_gop</th>
      <th>pctdiff_dem_vs_gop</th>
      <th>pctdiff_gop_vs_dem</th>
      <th>pctdiff_dem_vs_other</th>
      <th>pctdiff_gop_vs_other</th>
      <th>pctdiff_other_vs_dem</th>
      <th>pctdiff_other_vs_gop</th>
      <th>OBJECTID</th>
      <th>GEOID</th>
      <th>GEONAME</th>
      <th>Total_cvap_est</th>
      <th>SHAPE</th>
      <th>Shape__Area</th>
      <th>Shape__Length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>01001</td>
      <td>2016</td>
      <td>Autauga</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>5936.0</td>
      <td>Donald Trump</td>
      <td>18172.0</td>
      <td>24973</td>
      <td>865.0</td>
      <td>0.965363</td>
      <td>0.237697</td>
      <td>0.727666</td>
      <td>0.034637</td>
      <td>-12236.0</td>
      <td>12236.0</td>
      <td>5071.0</td>
      <td>17307.0</td>
      <td>-5071.0</td>
      <td>-17307.0</td>
      <td>-0.489969</td>
      <td>0.489969</td>
      <td>0.203059</td>
      <td>0.693028</td>
      <td>-0.203059</td>
      <td>-0.693028</td>
      <td>1.0</td>
      <td>01001</td>
      <td>Autauga County, Alabama</td>
      <td>40690.0</td>
      <td>{'rings': [[[-9619465, 3856529.0001000017], [-...</td>
      <td>2.208654e+09</td>
      <td>2.498864e+05</td>
    </tr>
    <tr>
      <th>1</th>
      <td>01003</td>
      <td>2016</td>
      <td>Baldwin</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>18458.0</td>
      <td>Donald Trump</td>
      <td>72883.0</td>
      <td>95215</td>
      <td>3874.0</td>
      <td>0.959313</td>
      <td>0.193856</td>
      <td>0.765457</td>
      <td>0.040687</td>
      <td>-54425.0</td>
      <td>54425.0</td>
      <td>14584.0</td>
      <td>69009.0</td>
      <td>-14584.0</td>
      <td>-69009.0</td>
      <td>-0.571601</td>
      <td>0.571601</td>
      <td>0.153169</td>
      <td>0.724770</td>
      <td>-0.153169</td>
      <td>-0.724770</td>
      <td>2.0</td>
      <td>01003</td>
      <td>Baldwin County, Alabama</td>
      <td>151770.0</td>
      <td>{'rings': [[[-9746859, 3539643.0001000017], [-...</td>
      <td>5.671048e+09</td>
      <td>1.655940e+06</td>
    </tr>
    <tr>
      <th>2</th>
      <td>01005</td>
      <td>2016</td>
      <td>Barbour</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>4871.0</td>
      <td>Donald Trump</td>
      <td>5454.0</td>
      <td>10469</td>
      <td>144.0</td>
      <td>0.986245</td>
      <td>0.465278</td>
      <td>0.520967</td>
      <td>0.013755</td>
      <td>-583.0</td>
      <td>583.0</td>
      <td>4727.0</td>
      <td>5310.0</td>
      <td>-4727.0</td>
      <td>-5310.0</td>
      <td>-0.055688</td>
      <td>0.055688</td>
      <td>0.451524</td>
      <td>0.507212</td>
      <td>-0.451524</td>
      <td>-0.507212</td>
      <td>3.0</td>
      <td>01005</td>
      <td>Barbour County, Alabama</td>
      <td>20375.0</td>
      <td>{'rings': [[[-9468394, 3771591.0001000017], [-...</td>
      <td>3.257902e+09</td>
      <td>3.208964e+05</td>
    </tr>
    <tr>
      <th>3</th>
      <td>01007</td>
      <td>2016</td>
      <td>Bibb</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>1874.0</td>
      <td>Donald Trump</td>
      <td>6738.0</td>
      <td>8819</td>
      <td>207.0</td>
      <td>0.976528</td>
      <td>0.212496</td>
      <td>0.764032</td>
      <td>0.023472</td>
      <td>-4864.0</td>
      <td>4864.0</td>
      <td>1667.0</td>
      <td>6531.0</td>
      <td>-1667.0</td>
      <td>-6531.0</td>
      <td>-0.551536</td>
      <td>0.551536</td>
      <td>0.189024</td>
      <td>0.740560</td>
      <td>-0.189024</td>
      <td>-0.740560</td>
      <td>4.0</td>
      <td>01007</td>
      <td>Bibb County, Alabama</td>
      <td>17590.0</td>
      <td>{'rings': [[[-9692114, 3928124.0001000017], [-...</td>
      <td>2.311999e+09</td>
      <td>2.279184e+05</td>
    </tr>
    <tr>
      <th>4</th>
      <td>01009</td>
      <td>2016</td>
      <td>Blount</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2156.0</td>
      <td>Donald Trump</td>
      <td>22859.0</td>
      <td>25588</td>
      <td>573.0</td>
      <td>0.977607</td>
      <td>0.084258</td>
      <td>0.893348</td>
      <td>0.022393</td>
      <td>-20703.0</td>
      <td>20703.0</td>
      <td>1583.0</td>
      <td>22286.0</td>
      <td>-1583.0</td>
      <td>-22286.0</td>
      <td>-0.809090</td>
      <td>0.809090</td>
      <td>0.061865</td>
      <td>0.870955</td>
      <td>-0.061865</td>
      <td>-0.870955</td>
      <td>5.0</td>
      <td>01009</td>
      <td>Blount County, Alabama</td>
      <td>42430.0</td>
      <td>{'rings': [[[-9623907, 4063676.0001000017], [-...</td>
      <td>2.456909e+09</td>
      <td>2.926429e+05</td>
    </tr>
  </tbody>
</table>
</div>

The resulting dataframe includes the attributes from your election data and the specified attributes from the county geometry data. The SHAPE field represents the county geometry and is used to locate each record, or feature, on the map.

***

## Query and calculate attributes

Because you have the voting age population for 2016, you can now calculate the average voter participation (voter turnout) for 2016. 

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>FIPS</th>
      <th>year</th>
      <th>county</th>
      <th>state</th>
      <th>state_po</th>
      <th>office</th>
      <th>candidate_dem</th>
      <th>votes_dem</th>
      <th>candidate_gop</th>
      <th>votes_gop</th>
      <th>votes_total</th>
      <th>votes_other</th>
      <th>voter_share_major_party</th>
      <th>voter_share_dem</th>
      <th>voter_share_gop</th>
      <th>voter_share_other</th>
      <th>rawdiff_dem_vs_gop</th>
      <th>rawdiff_gop_vs_dem</th>
      <th>rawdiff_dem_vs_other</th>
      <th>rawdiff_gop_vs_other</th>
      <th>rawdiff_other_vs_dem</th>
      <th>rawdiff_other_vs_gop</th>
      <th>pctdiff_dem_vs_gop</th>
      <th>pctdiff_gop_vs_dem</th>
      <th>pctdiff_dem_vs_other</th>
      <th>pctdiff_gop_vs_other</th>
      <th>pctdiff_other_vs_dem</th>
      <th>pctdiff_other_vs_gop</th>
      <th>OBJECTID</th>
      <th>GEOID</th>
      <th>GEONAME</th>
      <th>Total_cvap_est</th>
      <th>SHAPE</th>
      <th>Shape__Area</th>
      <th>Shape__Length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>01001</td>
      <td>2016</td>
      <td>Autauga</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>5936.0</td>
      <td>Donald Trump</td>
      <td>18172.0</td>
      <td>24973</td>
      <td>865.0</td>
      <td>0.965363</td>
      <td>0.237697</td>
      <td>0.727666</td>
      <td>0.034637</td>
      <td>-12236.0</td>
      <td>12236.0</td>
      <td>5071.0</td>
      <td>17307.0</td>
      <td>-5071.0</td>
      <td>-17307.0</td>
      <td>-0.489969</td>
      <td>0.489969</td>
      <td>0.203059</td>
      <td>0.693028</td>
      <td>-0.203059</td>
      <td>-0.693028</td>
      <td>1.0</td>
      <td>01001</td>
      <td>Autauga County, Alabama</td>
      <td>40690.0</td>
      <td>{'rings': [[[-9619465, 3856529.0001000017], [-...</td>
      <td>2.208654e+09</td>
      <td>2.498864e+05</td>
    </tr>
    <tr>
      <th>1</th>
      <td>01003</td>
      <td>2016</td>
      <td>Baldwin</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>18458.0</td>
      <td>Donald Trump</td>
      <td>72883.0</td>
      <td>95215</td>
      <td>3874.0</td>
      <td>0.959313</td>
      <td>0.193856</td>
      <td>0.765457</td>
      <td>0.040687</td>
      <td>-54425.0</td>
      <td>54425.0</td>
      <td>14584.0</td>
      <td>69009.0</td>
      <td>-14584.0</td>
      <td>-69009.0</td>
      <td>-0.571601</td>
      <td>0.571601</td>
      <td>0.153169</td>
      <td>0.724770</td>
      <td>-0.153169</td>
      <td>-0.724770</td>
      <td>2.0</td>
      <td>01003</td>
      <td>Baldwin County, Alabama</td>
      <td>151770.0</td>
      <td>{'rings': [[[-9746859, 3539643.0001000017], [-...</td>
      <td>5.671048e+09</td>
      <td>1.655940e+06</td>
    </tr>
    <tr>
      <th>2</th>
      <td>01005</td>
      <td>2016</td>
      <td>Barbour</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>4871.0</td>
      <td>Donald Trump</td>
      <td>5454.0</td>
      <td>10469</td>
      <td>144.0</td>
      <td>0.986245</td>
      <td>0.465278</td>
      <td>0.520967</td>
      <td>0.013755</td>
      <td>-583.0</td>
      <td>583.0</td>
      <td>4727.0</td>
      <td>5310.0</td>
      <td>-4727.0</td>
      <td>-5310.0</td>
      <td>-0.055688</td>
      <td>0.055688</td>
      <td>0.451524</td>
      <td>0.507212</td>
      <td>-0.451524</td>
      <td>-0.507212</td>
      <td>3.0</td>
      <td>01005</td>
      <td>Barbour County, Alabama</td>
      <td>20375.0</td>
      <td>{'rings': [[[-9468394, 3771591.0001000017], [-...</td>
      <td>3.257902e+09</td>
      <td>3.208964e+05</td>
    </tr>
    <tr>
      <th>3</th>
      <td>01007</td>
      <td>2016</td>
      <td>Bibb</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>1874.0</td>
      <td>Donald Trump</td>
      <td>6738.0</td>
      <td>8819</td>
      <td>207.0</td>
      <td>0.976528</td>
      <td>0.212496</td>
      <td>0.764032</td>
      <td>0.023472</td>
      <td>-4864.0</td>
      <td>4864.0</td>
      <td>1667.0</td>
      <td>6531.0</td>
      <td>-1667.0</td>
      <td>-6531.0</td>
      <td>-0.551536</td>
      <td>0.551536</td>
      <td>0.189024</td>
      <td>0.740560</td>
      <td>-0.189024</td>
      <td>-0.740560</td>
      <td>4.0</td>
      <td>01007</td>
      <td>Bibb County, Alabama</td>
      <td>17590.0</td>
      <td>{'rings': [[[-9692114, 3928124.0001000017], [-...</td>
      <td>2.311999e+09</td>
      <td>2.279184e+05</td>
    </tr>
    <tr>
      <th>4</th>
      <td>01009</td>
      <td>2016</td>
      <td>Blount</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2156.0</td>
      <td>Donald Trump</td>
      <td>22859.0</td>
      <td>25588</td>
      <td>573.0</td>
      <td>0.977607</td>
      <td>0.084258</td>
      <td>0.893348</td>
      <td>0.022393</td>
      <td>-20703.0</td>
      <td>20703.0</td>
      <td>1583.0</td>
      <td>22286.0</td>
      <td>-1583.0</td>
      <td>-22286.0</td>
      <td>-0.809090</td>
      <td>0.809090</td>
      <td>0.061865</td>
      <td>0.870955</td>
      <td>-0.061865</td>
      <td>-0.870955</td>
      <td>5.0</td>
      <td>01009</td>
      <td>Blount County, Alabama</td>
      <td>42430.0</td>
      <td>{'rings': [[[-9623907, 4063676.0001000017], [-...</td>
      <td>2.456909e+09</td>
      <td>2.926429e+05</td>
    </tr>
  </tbody>
</table>
</div>

You will calculate a new field named voter turnout using field operators in Pandas. The operations will apply to all values across the columns. 

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>FIPS</th>
      <th>year</th>
      <th>county</th>
      <th>state</th>
      <th>state_po</th>
      <th>office</th>
      <th>candidate_dem</th>
      <th>votes_dem</th>
      <th>candidate_gop</th>
      <th>votes_gop</th>
      <th>votes_total</th>
      <th>votes_other</th>
      <th>voter_share_major_party</th>
      <th>voter_share_dem</th>
      <th>voter_share_gop</th>
      <th>voter_share_other</th>
      <th>rawdiff_dem_vs_gop</th>
      <th>rawdiff_gop_vs_dem</th>
      <th>rawdiff_dem_vs_other</th>
      <th>rawdiff_gop_vs_other</th>
      <th>rawdiff_other_vs_dem</th>
      <th>rawdiff_other_vs_gop</th>
      <th>pctdiff_dem_vs_gop</th>
      <th>pctdiff_gop_vs_dem</th>
      <th>pctdiff_dem_vs_other</th>
      <th>pctdiff_gop_vs_other</th>
      <th>pctdiff_other_vs_dem</th>
      <th>pctdiff_other_vs_gop</th>
      <th>OBJECTID</th>
      <th>GEOID</th>
      <th>GEONAME</th>
      <th>Total_cvap_est</th>
      <th>SHAPE</th>
      <th>Shape__Area</th>
      <th>Shape__Length</th>
      <th>voter_turnout</th>
      <th>voter_turnout_majparty</th>
      <th>voter_turnout_dem</th>
      <th>voter_turnout_gop</th>
      <th>voter_turnout_other</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>01001</td>
      <td>2016</td>
      <td>Autauga</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>5936.0</td>
      <td>Donald Trump</td>
      <td>18172.0</td>
      <td>24973</td>
      <td>865.0</td>
      <td>0.965363</td>
      <td>0.237697</td>
      <td>0.727666</td>
      <td>0.034637</td>
      <td>-12236.0</td>
      <td>12236.0</td>
      <td>5071.0</td>
      <td>17307.0</td>
      <td>-5071.0</td>
      <td>-17307.0</td>
      <td>-0.489969</td>
      <td>0.489969</td>
      <td>0.203059</td>
      <td>0.693028</td>
      <td>-0.203059</td>
      <td>-0.693028</td>
      <td>1.0</td>
      <td>01001</td>
      <td>Autauga County, Alabama</td>
      <td>40690.0</td>
      <td>{'rings': [[[-9619465, 3856529.0001000017], [-...</td>
      <td>2.208654e+09</td>
      <td>2.498864e+05</td>
      <td>0.613738</td>
      <td>0.592480</td>
      <td>0.145884</td>
      <td>0.446596</td>
      <td>0.021258</td>
    </tr>
    <tr>
      <th>1</th>
      <td>01003</td>
      <td>2016</td>
      <td>Baldwin</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>18458.0</td>
      <td>Donald Trump</td>
      <td>72883.0</td>
      <td>95215</td>
      <td>3874.0</td>
      <td>0.959313</td>
      <td>0.193856</td>
      <td>0.765457</td>
      <td>0.040687</td>
      <td>-54425.0</td>
      <td>54425.0</td>
      <td>14584.0</td>
      <td>69009.0</td>
      <td>-14584.0</td>
      <td>-69009.0</td>
      <td>-0.571601</td>
      <td>0.571601</td>
      <td>0.153169</td>
      <td>0.724770</td>
      <td>-0.153169</td>
      <td>-0.724770</td>
      <td>2.0</td>
      <td>01003</td>
      <td>Baldwin County, Alabama</td>
      <td>151770.0</td>
      <td>{'rings': [[[-9746859, 3539643.0001000017], [-...</td>
      <td>5.671048e+09</td>
      <td>1.655940e+06</td>
      <td>0.627364</td>
      <td>0.601838</td>
      <td>0.121618</td>
      <td>0.480220</td>
      <td>0.025525</td>
    </tr>
    <tr>
      <th>2</th>
      <td>01005</td>
      <td>2016</td>
      <td>Barbour</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>4871.0</td>
      <td>Donald Trump</td>
      <td>5454.0</td>
      <td>10469</td>
      <td>144.0</td>
      <td>0.986245</td>
      <td>0.465278</td>
      <td>0.520967</td>
      <td>0.013755</td>
      <td>-583.0</td>
      <td>583.0</td>
      <td>4727.0</td>
      <td>5310.0</td>
      <td>-4727.0</td>
      <td>-5310.0</td>
      <td>-0.055688</td>
      <td>0.055688</td>
      <td>0.451524</td>
      <td>0.507212</td>
      <td>-0.451524</td>
      <td>-0.507212</td>
      <td>3.0</td>
      <td>01005</td>
      <td>Barbour County, Alabama</td>
      <td>20375.0</td>
      <td>{'rings': [[[-9468394, 3771591.0001000017], [-...</td>
      <td>3.257902e+09</td>
      <td>3.208964e+05</td>
      <td>0.513816</td>
      <td>0.506748</td>
      <td>0.239067</td>
      <td>0.267681</td>
      <td>0.007067</td>
    </tr>
    <tr>
      <th>3</th>
      <td>01007</td>
      <td>2016</td>
      <td>Bibb</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>1874.0</td>
      <td>Donald Trump</td>
      <td>6738.0</td>
      <td>8819</td>
      <td>207.0</td>
      <td>0.976528</td>
      <td>0.212496</td>
      <td>0.764032</td>
      <td>0.023472</td>
      <td>-4864.0</td>
      <td>4864.0</td>
      <td>1667.0</td>
      <td>6531.0</td>
      <td>-1667.0</td>
      <td>-6531.0</td>
      <td>-0.551536</td>
      <td>0.551536</td>
      <td>0.189024</td>
      <td>0.740560</td>
      <td>-0.189024</td>
      <td>-0.740560</td>
      <td>4.0</td>
      <td>01007</td>
      <td>Bibb County, Alabama</td>
      <td>17590.0</td>
      <td>{'rings': [[[-9692114, 3928124.0001000017], [-...</td>
      <td>2.311999e+09</td>
      <td>2.279184e+05</td>
      <td>0.501364</td>
      <td>0.489596</td>
      <td>0.106538</td>
      <td>0.383059</td>
      <td>0.011768</td>
    </tr>
    <tr>
      <th>4</th>
      <td>01009</td>
      <td>2016</td>
      <td>Blount</td>
      <td>Alabama</td>
      <td>AL</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2156.0</td>
      <td>Donald Trump</td>
      <td>22859.0</td>
      <td>25588</td>
      <td>573.0</td>
      <td>0.977607</td>
      <td>0.084258</td>
      <td>0.893348</td>
      <td>0.022393</td>
      <td>-20703.0</td>
      <td>20703.0</td>
      <td>1583.0</td>
      <td>22286.0</td>
      <td>-1583.0</td>
      <td>-22286.0</td>
      <td>-0.809090</td>
      <td>0.809090</td>
      <td>0.061865</td>
      <td>0.870955</td>
      <td>-0.061865</td>
      <td>-0.870955</td>
      <td>5.0</td>
      <td>01009</td>
      <td>Blount County, Alabama</td>
      <td>42430.0</td>
      <td>{'rings': [[[-9623907, 4063676.0001000017], [-...</td>
      <td>2.456909e+09</td>
      <td>2.926429e+05</td>
      <td>0.603064</td>
      <td>0.589559</td>
      <td>0.050813</td>
      <td>0.538746</td>
      <td>0.013505</td>
    </tr>
  </tbody>
</table>
</div>



***

## Validate the data

Before continuing with other data preparation, you should confirm that the output data has been successfully created. 

First, you will validate the values for voter turnout. You will remove null values, and because these values represent a fraction (total votes divided by voting age population), you will confirm that the values range between 0 and 1.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>FIPS</th>
      <th>year</th>
      <th>county</th>
      <th>state</th>
      <th>state_po</th>
      <th>office</th>
      <th>candidate_dem</th>
      <th>votes_dem</th>
      <th>candidate_gop</th>
      <th>votes_gop</th>
      <th>votes_total</th>
      <th>votes_other</th>
      <th>voter_share_major_party</th>
      <th>voter_share_dem</th>
      <th>voter_share_gop</th>
      <th>voter_share_other</th>
      <th>rawdiff_dem_vs_gop</th>
      <th>rawdiff_gop_vs_dem</th>
      <th>rawdiff_dem_vs_other</th>
      <th>rawdiff_gop_vs_other</th>
      <th>rawdiff_other_vs_dem</th>
      <th>rawdiff_other_vs_gop</th>
      <th>pctdiff_dem_vs_gop</th>
      <th>pctdiff_gop_vs_dem</th>
      <th>pctdiff_dem_vs_other</th>
      <th>pctdiff_gop_vs_other</th>
      <th>pctdiff_other_vs_dem</th>
      <th>pctdiff_other_vs_gop</th>
      <th>OBJECTID</th>
      <th>GEOID</th>
      <th>GEONAME</th>
      <th>Total_cvap_est</th>
      <th>SHAPE</th>
      <th>Shape__Area</th>
      <th>Shape__Length</th>
      <th>voter_turnout</th>
      <th>voter_turnout_majparty</th>
      <th>voter_turnout_dem</th>
      <th>voter_turnout_gop</th>
      <th>voter_turnout_other</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>67</th>
      <td>02701</td>
      <td>2016</td>
      <td>District 1</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2573.0</td>
      <td>Donald Trump</td>
      <td>3180.0</td>
      <td>6638</td>
      <td>885.0</td>
      <td>0.866677</td>
      <td>0.387617</td>
      <td>0.479060</td>
      <td>0.133323</td>
      <td>-607.0</td>
      <td>607.0</td>
      <td>1688.0</td>
      <td>2295.0</td>
      <td>-1688.0</td>
      <td>-2295.0</td>
      <td>-0.091443</td>
      <td>0.091443</td>
      <td>0.254293</td>
      <td>0.345737</td>
      <td>-0.254293</td>
      <td>-0.345737</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>68</th>
      <td>02702</td>
      <td>2016</td>
      <td>District 2</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>1585.0</td>
      <td>Donald Trump</td>
      <td>3188.0</td>
      <td>5492</td>
      <td>719.0</td>
      <td>0.869082</td>
      <td>0.288602</td>
      <td>0.580481</td>
      <td>0.130918</td>
      <td>-1603.0</td>
      <td>1603.0</td>
      <td>866.0</td>
      <td>2469.0</td>
      <td>-866.0</td>
      <td>-2469.0</td>
      <td>-0.291879</td>
      <td>0.291879</td>
      <td>0.157684</td>
      <td>0.449563</td>
      <td>-0.157684</td>
      <td>-0.449563</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>69</th>
      <td>02703</td>
      <td>2016</td>
      <td>District 3</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>1241.0</td>
      <td>Donald Trump</td>
      <td>5403.0</td>
      <td>7613</td>
      <td>969.0</td>
      <td>0.872718</td>
      <td>0.163011</td>
      <td>0.709707</td>
      <td>0.127282</td>
      <td>-4162.0</td>
      <td>4162.0</td>
      <td>272.0</td>
      <td>4434.0</td>
      <td>-272.0</td>
      <td>-4434.0</td>
      <td>-0.546696</td>
      <td>0.546696</td>
      <td>0.035728</td>
      <td>0.582425</td>
      <td>-0.035728</td>
      <td>-0.582425</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>70</th>
      <td>02704</td>
      <td>2016</td>
      <td>District 4</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>4162.0</td>
      <td>Donald Trump</td>
      <td>4070.0</td>
      <td>9521</td>
      <td>1289.0</td>
      <td>0.864615</td>
      <td>0.437139</td>
      <td>0.427476</td>
      <td>0.135385</td>
      <td>92.0</td>
      <td>-92.0</td>
      <td>2873.0</td>
      <td>2781.0</td>
      <td>-2873.0</td>
      <td>-2781.0</td>
      <td>0.009663</td>
      <td>-0.009663</td>
      <td>0.301754</td>
      <td>0.292091</td>
      <td>-0.301754</td>
      <td>-0.292091</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>71</th>
      <td>02705</td>
      <td>2016</td>
      <td>District 5</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>3187.0</td>
      <td>Donald Trump</td>
      <td>3683.0</td>
      <td>7906</td>
      <td>1036.0</td>
      <td>0.868960</td>
      <td>0.403112</td>
      <td>0.465849</td>
      <td>0.131040</td>
      <td>-496.0</td>
      <td>496.0</td>
      <td>2151.0</td>
      <td>2647.0</td>
      <td>-2151.0</td>
      <td>-2647.0</td>
      <td>-0.062737</td>
      <td>0.062737</td>
      <td>0.272072</td>
      <td>0.334809</td>
      <td>-0.272072</td>
      <td>-0.334809</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>72</th>
      <td>02706</td>
      <td>2016</td>
      <td>District 6</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2536.0</td>
      <td>Donald Trump</td>
      <td>4929.0</td>
      <td>8460</td>
      <td>995.0</td>
      <td>0.882388</td>
      <td>0.299764</td>
      <td>0.582624</td>
      <td>0.117612</td>
      <td>-2393.0</td>
      <td>2393.0</td>
      <td>1541.0</td>
      <td>3934.0</td>
      <td>-1541.0</td>
      <td>-3934.0</td>
      <td>-0.282861</td>
      <td>0.282861</td>
      <td>0.182151</td>
      <td>0.465012</td>
      <td>-0.182151</td>
      <td>-0.465012</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>73</th>
      <td>02707</td>
      <td>2016</td>
      <td>District 7</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>1510.0</td>
      <td>Donald Trump</td>
      <td>5935.0</td>
      <td>8294</td>
      <td>849.0</td>
      <td>0.897637</td>
      <td>0.182059</td>
      <td>0.715578</td>
      <td>0.102363</td>
      <td>-4425.0</td>
      <td>4425.0</td>
      <td>661.0</td>
      <td>5086.0</td>
      <td>-661.0</td>
      <td>-5086.0</td>
      <td>-0.533518</td>
      <td>0.533518</td>
      <td>0.079696</td>
      <td>0.613214</td>
      <td>-0.079696</td>
      <td>-0.613214</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>74</th>
      <td>02708</td>
      <td>2016</td>
      <td>District 8</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>1218.0</td>
      <td>Donald Trump</td>
      <td>6126.0</td>
      <td>8073</td>
      <td>729.0</td>
      <td>0.909699</td>
      <td>0.150873</td>
      <td>0.758826</td>
      <td>0.090301</td>
      <td>-4908.0</td>
      <td>4908.0</td>
      <td>489.0</td>
      <td>5397.0</td>
      <td>-489.0</td>
      <td>-5397.0</td>
      <td>-0.607952</td>
      <td>0.607952</td>
      <td>0.060572</td>
      <td>0.668525</td>
      <td>-0.060572</td>
      <td>-0.668525</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>75</th>
      <td>02709</td>
      <td>2016</td>
      <td>District 9</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>1843.0</td>
      <td>Donald Trump</td>
      <td>6100.0</td>
      <td>8954</td>
      <td>1011.0</td>
      <td>0.887090</td>
      <td>0.205830</td>
      <td>0.681260</td>
      <td>0.112910</td>
      <td>-4257.0</td>
      <td>4257.0</td>
      <td>832.0</td>
      <td>5089.0</td>
      <td>-832.0</td>
      <td>-5089.0</td>
      <td>-0.475430</td>
      <td>0.475430</td>
      <td>0.092919</td>
      <td>0.568349</td>
      <td>-0.092919</td>
      <td>-0.568349</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>76</th>
      <td>02710</td>
      <td>2016</td>
      <td>District 10</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>1808.0</td>
      <td>Donald Trump</td>
      <td>6255.0</td>
      <td>9040</td>
      <td>977.0</td>
      <td>0.891925</td>
      <td>0.200000</td>
      <td>0.691925</td>
      <td>0.108075</td>
      <td>-4447.0</td>
      <td>4447.0</td>
      <td>831.0</td>
      <td>5278.0</td>
      <td>-831.0</td>
      <td>-5278.0</td>
      <td>-0.491925</td>
      <td>0.491925</td>
      <td>0.091925</td>
      <td>0.583850</td>
      <td>-0.091925</td>
      <td>-0.583850</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>77</th>
      <td>02711</td>
      <td>2016</td>
      <td>District 11</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2142.0</td>
      <td>Donald Trump</td>
      <td>6444.0</td>
      <td>9689</td>
      <td>1103.0</td>
      <td>0.886160</td>
      <td>0.221075</td>
      <td>0.665084</td>
      <td>0.113840</td>
      <td>-4302.0</td>
      <td>4302.0</td>
      <td>1039.0</td>
      <td>5341.0</td>
      <td>-1039.0</td>
      <td>-5341.0</td>
      <td>-0.444009</td>
      <td>0.444009</td>
      <td>0.107235</td>
      <td>0.551244</td>
      <td>-0.107235</td>
      <td>-0.551244</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>78</th>
      <td>02712</td>
      <td>2016</td>
      <td>District 12</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>1928.0</td>
      <td>Donald Trump</td>
      <td>6629.0</td>
      <td>9543</td>
      <td>986.0</td>
      <td>0.896678</td>
      <td>0.202033</td>
      <td>0.694645</td>
      <td>0.103322</td>
      <td>-4701.0</td>
      <td>4701.0</td>
      <td>942.0</td>
      <td>5643.0</td>
      <td>-942.0</td>
      <td>-5643.0</td>
      <td>-0.492612</td>
      <td>0.492612</td>
      <td>0.098711</td>
      <td>0.591323</td>
      <td>-0.098711</td>
      <td>-0.591323</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>79</th>
      <td>02713</td>
      <td>2016</td>
      <td>District 13</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>1684.0</td>
      <td>Donald Trump</td>
      <td>4028.0</td>
      <td>6533</td>
      <td>821.0</td>
      <td>0.874330</td>
      <td>0.257768</td>
      <td>0.616562</td>
      <td>0.125670</td>
      <td>-2344.0</td>
      <td>2344.0</td>
      <td>863.0</td>
      <td>3207.0</td>
      <td>-863.0</td>
      <td>-3207.0</td>
      <td>-0.358794</td>
      <td>0.358794</td>
      <td>0.132099</td>
      <td>0.490892</td>
      <td>-0.132099</td>
      <td>-0.490892</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>80</th>
      <td>02714</td>
      <td>2016</td>
      <td>District 14</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>3043.0</td>
      <td>Donald Trump</td>
      <td>5978.0</td>
      <td>10420</td>
      <td>1399.0</td>
      <td>0.865739</td>
      <td>0.292035</td>
      <td>0.573704</td>
      <td>0.134261</td>
      <td>-2935.0</td>
      <td>2935.0</td>
      <td>1644.0</td>
      <td>4579.0</td>
      <td>-1644.0</td>
      <td>-4579.0</td>
      <td>-0.281670</td>
      <td>0.281670</td>
      <td>0.157774</td>
      <td>0.439443</td>
      <td>-0.157774</td>
      <td>-0.439443</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>81</th>
      <td>02715</td>
      <td>2016</td>
      <td>District 15</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>1828.0</td>
      <td>Donald Trump</td>
      <td>2525.0</td>
      <td>4982</td>
      <td>629.0</td>
      <td>0.873745</td>
      <td>0.366921</td>
      <td>0.506825</td>
      <td>0.126255</td>
      <td>-697.0</td>
      <td>697.0</td>
      <td>1199.0</td>
      <td>1896.0</td>
      <td>-1199.0</td>
      <td>-1896.0</td>
      <td>-0.139904</td>
      <td>0.139904</td>
      <td>0.240666</td>
      <td>0.380570</td>
      <td>-0.240666</td>
      <td>-0.380570</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>82</th>
      <td>02716</td>
      <td>2016</td>
      <td>District 16</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>3294.0</td>
      <td>Donald Trump</td>
      <td>3203.0</td>
      <td>7436</td>
      <td>939.0</td>
      <td>0.873722</td>
      <td>0.442980</td>
      <td>0.430742</td>
      <td>0.126278</td>
      <td>91.0</td>
      <td>-91.0</td>
      <td>2355.0</td>
      <td>2264.0</td>
      <td>-2355.0</td>
      <td>-2264.0</td>
      <td>0.012238</td>
      <td>-0.012238</td>
      <td>0.316703</td>
      <td>0.304465</td>
      <td>-0.316703</td>
      <td>-0.304465</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>83</th>
      <td>02717</td>
      <td>2016</td>
      <td>District 17</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>3290.0</td>
      <td>Donald Trump</td>
      <td>2618.0</td>
      <td>6788</td>
      <td>880.0</td>
      <td>0.870359</td>
      <td>0.484679</td>
      <td>0.385681</td>
      <td>0.129641</td>
      <td>672.0</td>
      <td>-672.0</td>
      <td>2410.0</td>
      <td>1738.0</td>
      <td>-2410.0</td>
      <td>-1738.0</td>
      <td>0.098998</td>
      <td>-0.098998</td>
      <td>0.355038</td>
      <td>0.256040</td>
      <td>-0.355038</td>
      <td>-0.256040</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>84</th>
      <td>02718</td>
      <td>2016</td>
      <td>District 18</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>3909.0</td>
      <td>Donald Trump</td>
      <td>2684.0</td>
      <td>7402</td>
      <td>809.0</td>
      <td>0.890705</td>
      <td>0.528101</td>
      <td>0.362605</td>
      <td>0.109295</td>
      <td>1225.0</td>
      <td>-1225.0</td>
      <td>3100.0</td>
      <td>1875.0</td>
      <td>-3100.0</td>
      <td>-1875.0</td>
      <td>0.165496</td>
      <td>-0.165496</td>
      <td>0.418806</td>
      <td>0.253310</td>
      <td>-0.418806</td>
      <td>-0.253310</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>85</th>
      <td>02719</td>
      <td>2016</td>
      <td>District 19</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2669.0</td>
      <td>Donald Trump</td>
      <td>1636.0</td>
      <td>4792</td>
      <td>487.0</td>
      <td>0.898372</td>
      <td>0.556970</td>
      <td>0.341402</td>
      <td>0.101628</td>
      <td>1033.0</td>
      <td>-1033.0</td>
      <td>2182.0</td>
      <td>1149.0</td>
      <td>-2182.0</td>
      <td>-1149.0</td>
      <td>0.215568</td>
      <td>-0.215568</td>
      <td>0.455342</td>
      <td>0.239775</td>
      <td>-0.455342</td>
      <td>-0.239775</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>86</th>
      <td>02720</td>
      <td>2016</td>
      <td>District 20</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>4151.0</td>
      <td>Donald Trump</td>
      <td>2187.0</td>
      <td>7140</td>
      <td>802.0</td>
      <td>0.887675</td>
      <td>0.581373</td>
      <td>0.306303</td>
      <td>0.112325</td>
      <td>1964.0</td>
      <td>-1964.0</td>
      <td>3349.0</td>
      <td>1385.0</td>
      <td>-3349.0</td>
      <td>-1385.0</td>
      <td>0.275070</td>
      <td>-0.275070</td>
      <td>0.469048</td>
      <td>0.193978</td>
      <td>-0.469048</td>
      <td>-0.193978</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>87</th>
      <td>02721</td>
      <td>2016</td>
      <td>District 21</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>4224.0</td>
      <td>Donald Trump</td>
      <td>3479.0</td>
      <td>8647</td>
      <td>944.0</td>
      <td>0.890829</td>
      <td>0.488493</td>
      <td>0.402336</td>
      <td>0.109171</td>
      <td>745.0</td>
      <td>-745.0</td>
      <td>3280.0</td>
      <td>2535.0</td>
      <td>-3280.0</td>
      <td>-2535.0</td>
      <td>0.086157</td>
      <td>-0.086157</td>
      <td>0.379322</td>
      <td>0.293165</td>
      <td>-0.379322</td>
      <td>-0.293165</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>88</th>
      <td>02722</td>
      <td>2016</td>
      <td>District 22</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>3270.0</td>
      <td>Donald Trump</td>
      <td>4203.0</td>
      <td>8372</td>
      <td>899.0</td>
      <td>0.892618</td>
      <td>0.390588</td>
      <td>0.502031</td>
      <td>0.107382</td>
      <td>-933.0</td>
      <td>933.0</td>
      <td>2371.0</td>
      <td>3304.0</td>
      <td>-2371.0</td>
      <td>-3304.0</td>
      <td>-0.111443</td>
      <td>0.111443</td>
      <td>0.283206</td>
      <td>0.394649</td>
      <td>-0.283206</td>
      <td>-0.394649</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>89</th>
      <td>02723</td>
      <td>2016</td>
      <td>District 23</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2894.0</td>
      <td>Donald Trump</td>
      <td>3246.0</td>
      <td>6924</td>
      <td>784.0</td>
      <td>0.886771</td>
      <td>0.417966</td>
      <td>0.468804</td>
      <td>0.113229</td>
      <td>-352.0</td>
      <td>352.0</td>
      <td>2110.0</td>
      <td>2462.0</td>
      <td>-2110.0</td>
      <td>-2462.0</td>
      <td>-0.050838</td>
      <td>0.050838</td>
      <td>0.304737</td>
      <td>0.355575</td>
      <td>-0.304737</td>
      <td>-0.355575</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>90</th>
      <td>02724</td>
      <td>2016</td>
      <td>District 24</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>3578.0</td>
      <td>Donald Trump</td>
      <td>4709.0</td>
      <td>9080</td>
      <td>793.0</td>
      <td>0.912665</td>
      <td>0.394053</td>
      <td>0.518612</td>
      <td>0.087335</td>
      <td>-1131.0</td>
      <td>1131.0</td>
      <td>2785.0</td>
      <td>3916.0</td>
      <td>-2785.0</td>
      <td>-3916.0</td>
      <td>-0.124559</td>
      <td>0.124559</td>
      <td>0.306718</td>
      <td>0.431278</td>
      <td>-0.306718</td>
      <td>-0.431278</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>91</th>
      <td>02725</td>
      <td>2016</td>
      <td>District 25</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>3378.0</td>
      <td>Donald Trump</td>
      <td>3816.0</td>
      <td>8127</td>
      <td>933.0</td>
      <td>0.885197</td>
      <td>0.415652</td>
      <td>0.469546</td>
      <td>0.114803</td>
      <td>-438.0</td>
      <td>438.0</td>
      <td>2445.0</td>
      <td>2883.0</td>
      <td>-2445.0</td>
      <td>-2883.0</td>
      <td>-0.053894</td>
      <td>0.053894</td>
      <td>0.300849</td>
      <td>0.354743</td>
      <td>-0.300849</td>
      <td>-0.354743</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>92</th>
      <td>02726</td>
      <td>2016</td>
      <td>District 26</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>3374.0</td>
      <td>Donald Trump</td>
      <td>4548.0</td>
      <td>8905</td>
      <td>983.0</td>
      <td>0.889613</td>
      <td>0.378888</td>
      <td>0.510724</td>
      <td>0.110387</td>
      <td>-1174.0</td>
      <td>1174.0</td>
      <td>2391.0</td>
      <td>3565.0</td>
      <td>-2391.0</td>
      <td>-3565.0</td>
      <td>-0.131836</td>
      <td>0.131836</td>
      <td>0.268501</td>
      <td>0.400337</td>
      <td>-0.268501</td>
      <td>-0.400337</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>93</th>
      <td>02727</td>
      <td>2016</td>
      <td>District 27</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>3729.0</td>
      <td>Donald Trump</td>
      <td>4085.0</td>
      <td>8783</td>
      <td>969.0</td>
      <td>0.889673</td>
      <td>0.424570</td>
      <td>0.465103</td>
      <td>0.110327</td>
      <td>-356.0</td>
      <td>356.0</td>
      <td>2760.0</td>
      <td>3116.0</td>
      <td>-2760.0</td>
      <td>-3116.0</td>
      <td>-0.040533</td>
      <td>0.040533</td>
      <td>0.314243</td>
      <td>0.354776</td>
      <td>-0.314243</td>
      <td>-0.354776</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>94</th>
      <td>02728</td>
      <td>2016</td>
      <td>District 28</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>4749.0</td>
      <td>Donald Trump</td>
      <td>5423.0</td>
      <td>11427</td>
      <td>1255.0</td>
      <td>0.890172</td>
      <td>0.415595</td>
      <td>0.474578</td>
      <td>0.109828</td>
      <td>-674.0</td>
      <td>674.0</td>
      <td>3494.0</td>
      <td>4168.0</td>
      <td>-3494.0</td>
      <td>-4168.0</td>
      <td>-0.058983</td>
      <td>0.058983</td>
      <td>0.305767</td>
      <td>0.364750</td>
      <td>-0.305767</td>
      <td>-0.364750</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>95</th>
      <td>02729</td>
      <td>2016</td>
      <td>District 29</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2101.0</td>
      <td>Donald Trump</td>
      <td>6347.0</td>
      <td>9394</td>
      <td>946.0</td>
      <td>0.899297</td>
      <td>0.223653</td>
      <td>0.675644</td>
      <td>0.100703</td>
      <td>-4246.0</td>
      <td>4246.0</td>
      <td>1155.0</td>
      <td>5401.0</td>
      <td>-1155.0</td>
      <td>-5401.0</td>
      <td>-0.451991</td>
      <td>0.451991</td>
      <td>0.122951</td>
      <td>0.574941</td>
      <td>-0.122951</td>
      <td>-0.574941</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>96</th>
      <td>02730</td>
      <td>2016</td>
      <td>District 30</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>1816.0</td>
      <td>Donald Trump</td>
      <td>6194.0</td>
      <td>8950</td>
      <td>940.0</td>
      <td>0.894972</td>
      <td>0.202905</td>
      <td>0.692067</td>
      <td>0.105028</td>
      <td>-4378.0</td>
      <td>4378.0</td>
      <td>876.0</td>
      <td>5254.0</td>
      <td>-876.0</td>
      <td>-5254.0</td>
      <td>-0.489162</td>
      <td>0.489162</td>
      <td>0.097877</td>
      <td>0.587039</td>
      <td>-0.097877</td>
      <td>-0.587039</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>97</th>
      <td>02731</td>
      <td>2016</td>
      <td>District 31</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>3466.0</td>
      <td>Donald Trump</td>
      <td>5617.0</td>
      <td>10182</td>
      <td>1099.0</td>
      <td>0.892064</td>
      <td>0.340405</td>
      <td>0.551660</td>
      <td>0.107936</td>
      <td>-2151.0</td>
      <td>2151.0</td>
      <td>2367.0</td>
      <td>4518.0</td>
      <td>-2367.0</td>
      <td>-4518.0</td>
      <td>-0.211255</td>
      <td>0.211255</td>
      <td>0.232469</td>
      <td>0.443724</td>
      <td>-0.232469</td>
      <td>-0.443724</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>98</th>
      <td>02732</td>
      <td>2016</td>
      <td>District 32</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2701.0</td>
      <td>Donald Trump</td>
      <td>3764.0</td>
      <td>7472</td>
      <td>1007.0</td>
      <td>0.865230</td>
      <td>0.361483</td>
      <td>0.503747</td>
      <td>0.134770</td>
      <td>-1063.0</td>
      <td>1063.0</td>
      <td>1694.0</td>
      <td>2757.0</td>
      <td>-1694.0</td>
      <td>-2757.0</td>
      <td>-0.142264</td>
      <td>0.142264</td>
      <td>0.226713</td>
      <td>0.368978</td>
      <td>-0.226713</td>
      <td>-0.368978</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>99</th>
      <td>02733</td>
      <td>2016</td>
      <td>District 33</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>5978.0</td>
      <td>Donald Trump</td>
      <td>2732.0</td>
      <td>9934</td>
      <td>1224.0</td>
      <td>0.876787</td>
      <td>0.601772</td>
      <td>0.275015</td>
      <td>0.123213</td>
      <td>3246.0</td>
      <td>-3246.0</td>
      <td>4754.0</td>
      <td>1508.0</td>
      <td>-4754.0</td>
      <td>-1508.0</td>
      <td>0.326757</td>
      <td>-0.326757</td>
      <td>0.478558</td>
      <td>0.151802</td>
      <td>-0.478558</td>
      <td>-0.151802</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>100</th>
      <td>02734</td>
      <td>2016</td>
      <td>District 34</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>4220.0</td>
      <td>Donald Trump</td>
      <td>3955.0</td>
      <td>9431</td>
      <td>1256.0</td>
      <td>0.866822</td>
      <td>0.447461</td>
      <td>0.419362</td>
      <td>0.133178</td>
      <td>265.0</td>
      <td>-265.0</td>
      <td>2964.0</td>
      <td>2699.0</td>
      <td>-2964.0</td>
      <td>-2699.0</td>
      <td>0.028099</td>
      <td>-0.028099</td>
      <td>0.314283</td>
      <td>0.286184</td>
      <td>-0.314283</td>
      <td>-0.286184</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>101</th>
      <td>02735</td>
      <td>2016</td>
      <td>District 35</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>3749.0</td>
      <td>Donald Trump</td>
      <td>4105.0</td>
      <td>9042</td>
      <td>1188.0</td>
      <td>0.868613</td>
      <td>0.414621</td>
      <td>0.453992</td>
      <td>0.131387</td>
      <td>-356.0</td>
      <td>356.0</td>
      <td>2561.0</td>
      <td>2917.0</td>
      <td>-2561.0</td>
      <td>-2917.0</td>
      <td>-0.039372</td>
      <td>0.039372</td>
      <td>0.283234</td>
      <td>0.322606</td>
      <td>-0.283234</td>
      <td>-0.322606</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>102</th>
      <td>02736</td>
      <td>2016</td>
      <td>District 36</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2693.0</td>
      <td>Donald Trump</td>
      <td>4460.0</td>
      <td>8264</td>
      <td>1111.0</td>
      <td>0.865561</td>
      <td>0.325871</td>
      <td>0.539690</td>
      <td>0.134439</td>
      <td>-1767.0</td>
      <td>1767.0</td>
      <td>1582.0</td>
      <td>3349.0</td>
      <td>-1582.0</td>
      <td>-3349.0</td>
      <td>-0.213819</td>
      <td>0.213819</td>
      <td>0.191433</td>
      <td>0.405252</td>
      <td>-0.191433</td>
      <td>-0.405252</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>103</th>
      <td>02737</td>
      <td>2016</td>
      <td>District 37</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2421.0</td>
      <td>Donald Trump</td>
      <td>1938.0</td>
      <td>5062</td>
      <td>703.0</td>
      <td>0.861122</td>
      <td>0.478269</td>
      <td>0.382853</td>
      <td>0.138878</td>
      <td>483.0</td>
      <td>-483.0</td>
      <td>1718.0</td>
      <td>1235.0</td>
      <td>-1718.0</td>
      <td>-1235.0</td>
      <td>0.095417</td>
      <td>-0.095417</td>
      <td>0.339392</td>
      <td>0.243975</td>
      <td>-0.339392</td>
      <td>-0.243975</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>104</th>
      <td>02738</td>
      <td>2016</td>
      <td>District 38</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2758.0</td>
      <td>Donald Trump</td>
      <td>1143.0</td>
      <td>5095</td>
      <td>1194.0</td>
      <td>0.765653</td>
      <td>0.541315</td>
      <td>0.224338</td>
      <td>0.234347</td>
      <td>1615.0</td>
      <td>-1615.0</td>
      <td>1564.0</td>
      <td>-51.0</td>
      <td>-1564.0</td>
      <td>51.0</td>
      <td>0.316977</td>
      <td>-0.316977</td>
      <td>0.306968</td>
      <td>-0.010010</td>
      <td>-0.306968</td>
      <td>0.010010</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>105</th>
      <td>02739</td>
      <td>2016</td>
      <td>District 39</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>3142.0</td>
      <td>Donald Trump</td>
      <td>1405.0</td>
      <td>5639</td>
      <td>1092.0</td>
      <td>0.806349</td>
      <td>0.557191</td>
      <td>0.249158</td>
      <td>0.193651</td>
      <td>1737.0</td>
      <td>-1737.0</td>
      <td>2050.0</td>
      <td>313.0</td>
      <td>-2050.0</td>
      <td>-313.0</td>
      <td>0.308033</td>
      <td>-0.308033</td>
      <td>0.363540</td>
      <td>0.055506</td>
      <td>-0.363540</td>
      <td>-0.055506</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>106</th>
      <td>02740</td>
      <td>2016</td>
      <td>District 40</td>
      <td>Alaska</td>
      <td>AK</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2338.0</td>
      <td>Donald Trump</td>
      <td>1377.0</td>
      <td>4610</td>
      <td>895.0</td>
      <td>0.805857</td>
      <td>0.507158</td>
      <td>0.298698</td>
      <td>0.194143</td>
      <td>961.0</td>
      <td>-961.0</td>
      <td>1443.0</td>
      <td>482.0</td>
      <td>-1443.0</td>
      <td>-482.0</td>
      <td>0.208460</td>
      <td>-0.208460</td>
      <td>0.313015</td>
      <td>0.104555</td>
      <td>-0.313015</td>
      <td>-0.104555</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1838</th>
      <td>36000</td>
      <td>2016</td>
      <td>Kansas City</td>
      <td>Missouri</td>
      <td>MO</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>97735.0</td>
      <td>Donald Trump</td>
      <td>24654.0</td>
      <td>128601</td>
      <td>6212.0</td>
      <td>0.951696</td>
      <td>0.759986</td>
      <td>0.191709</td>
      <td>0.048304</td>
      <td>73081.0</td>
      <td>-73081.0</td>
      <td>91523.0</td>
      <td>18442.0</td>
      <td>-91523.0</td>
      <td>-18442.0</td>
      <td>0.568277</td>
      <td>-0.568277</td>
      <td>0.711682</td>
      <td>0.143405</td>
      <td>-0.711682</td>
      <td>-0.143405</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2428</th>
      <td>46113</td>
      <td>2016</td>
      <td>Oglala Lakota</td>
      <td>South Dakota</td>
      <td>SD</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2510.0</td>
      <td>Donald Trump</td>
      <td>241.0</td>
      <td>2905</td>
      <td>154.0</td>
      <td>0.946988</td>
      <td>0.864028</td>
      <td>0.082960</td>
      <td>0.053012</td>
      <td>2269.0</td>
      <td>-2269.0</td>
      <td>2356.0</td>
      <td>87.0</td>
      <td>-2356.0</td>
      <td>-87.0</td>
      <td>0.781067</td>
      <td>-0.781067</td>
      <td>0.811015</td>
      <td>0.029948</td>
      <td>-0.811015</td>
      <td>-0.029948</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2927</th>
      <td>51515</td>
      <td>2016</td>
      <td>Bedford</td>
      <td>Virginia</td>
      <td>VA</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>NaN</td>
      <td>Donald Trump</td>
      <td>NaN</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>

The describe function indicates that there are voter turnout values over one, indicating a voter turnout above 100%. You will further investigate by querying for these records.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>FIPS</th>
      <th>year</th>
      <th>county</th>
      <th>state</th>
      <th>state_po</th>
      <th>office</th>
      <th>candidate_dem</th>
      <th>votes_dem</th>
      <th>candidate_gop</th>
      <th>votes_gop</th>
      <th>votes_total</th>
      <th>votes_other</th>
      <th>voter_share_major_party</th>
      <th>voter_share_dem</th>
      <th>voter_share_gop</th>
      <th>voter_share_other</th>
      <th>rawdiff_dem_vs_gop</th>
      <th>rawdiff_gop_vs_dem</th>
      <th>rawdiff_dem_vs_other</th>
      <th>rawdiff_gop_vs_other</th>
      <th>rawdiff_other_vs_dem</th>
      <th>rawdiff_other_vs_gop</th>
      <th>pctdiff_dem_vs_gop</th>
      <th>pctdiff_gop_vs_dem</th>
      <th>pctdiff_dem_vs_other</th>
      <th>pctdiff_gop_vs_other</th>
      <th>pctdiff_other_vs_dem</th>
      <th>pctdiff_other_vs_gop</th>
      <th>OBJECTID</th>
      <th>GEOID</th>
      <th>GEONAME</th>
      <th>Total_cvap_est</th>
      <th>SHAPE</th>
      <th>Shape__Area</th>
      <th>Shape__Length</th>
      <th>voter_turnout</th>
      <th>voter_turnout_majparty</th>
      <th>voter_turnout_dem</th>
      <th>voter_turnout_gop</th>
      <th>voter_turnout_other</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>311</th>
      <td>08111</td>
      <td>2016</td>
      <td>San Juan</td>
      <td>Colorado</td>
      <td>CO</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>265.0</td>
      <td>Donald Trump</td>
      <td>215.0</td>
      <td>506</td>
      <td>26.0</td>
      <td>0.948617</td>
      <td>0.523715</td>
      <td>0.424901</td>
      <td>0.051383</td>
      <td>50.0</td>
      <td>-50.0</td>
      <td>239.0</td>
      <td>189.0</td>
      <td>-239.0</td>
      <td>-189.0</td>
      <td>0.098814</td>
      <td>-0.098814</td>
      <td>0.472332</td>
      <td>0.373518</td>
      <td>-0.472332</td>
      <td>-0.373518</td>
      <td>301.0</td>
      <td>08111</td>
      <td>San Juan County, Colorado</td>
      <td>495.0</td>
      <td>{'rings': [[[-11964863, 4528625.000100002], [-...</td>
      <td>1.611963e+09</td>
      <td>209299.379233</td>
      <td>1.022222</td>
      <td>0.969697</td>
      <td>0.535354</td>
      <td>0.434343</td>
      <td>0.052525</td>
    </tr>
    <tr>
      <th>1816</th>
      <td>35021</td>
      <td>2016</td>
      <td>Harding</td>
      <td>New Mexico</td>
      <td>NM</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>156.0</td>
      <td>Donald Trump</td>
      <td>311.0</td>
      <td>527</td>
      <td>60.0</td>
      <td>0.886148</td>
      <td>0.296015</td>
      <td>0.590133</td>
      <td>0.113852</td>
      <td>-155.0</td>
      <td>155.0</td>
      <td>96.0</td>
      <td>251.0</td>
      <td>-96.0</td>
      <td>-251.0</td>
      <td>-0.294118</td>
      <td>0.294118</td>
      <td>0.182163</td>
      <td>0.476281</td>
      <td>-0.182163</td>
      <td>-0.476281</td>
      <td>1807.0</td>
      <td>35021</td>
      <td>Harding County, New Mexico</td>
      <td>470.0</td>
      <td>{'rings': [[[-11578210, 4330676.000100002], [-...</td>
      <td>8.400382e+09</td>
      <td>492631.196575</td>
      <td>1.121277</td>
      <td>0.993617</td>
      <td>0.331915</td>
      <td>0.661702</td>
      <td>0.127660</td>
    </tr>
    <tr>
      <th>2684</th>
      <td>48301</td>
      <td>2016</td>
      <td>Loving</td>
      <td>Texas</td>
      <td>TX</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>4.0</td>
      <td>Donald Trump</td>
      <td>58.0</td>
      <td>65</td>
      <td>3.0</td>
      <td>0.953846</td>
      <td>0.061538</td>
      <td>0.892308</td>
      <td>0.046154</td>
      <td>-54.0</td>
      <td>54.0</td>
      <td>1.0</td>
      <td>55.0</td>
      <td>-1.0</td>
      <td>-55.0</td>
      <td>-0.830769</td>
      <td>0.830769</td>
      <td>0.015385</td>
      <td>0.846154</td>
      <td>-0.015385</td>
      <td>-0.846154</td>
      <td>2674.0</td>
      <td>48301</td>
      <td>Loving County, Texas</td>
      <td>60.0</td>
      <td>{'rings': [[[-11502370, 3717641.0001000017], [...</td>
      <td>2.435674e+09</td>
      <td>254898.035389</td>
      <td>1.083333</td>
      <td>1.033333</td>
      <td>0.066667</td>
      <td>0.966667</td>
      <td>0.050000</td>
    </tr>
    <tr>
      <th>2689</th>
      <td>48311</td>
      <td>2016</td>
      <td>McMullen</td>
      <td>Texas</td>
      <td>TX</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>40.0</td>
      <td>Donald Trump</td>
      <td>454.0</td>
      <td>499</td>
      <td>5.0</td>
      <td>0.989980</td>
      <td>0.080160</td>
      <td>0.909820</td>
      <td>0.010020</td>
      <td>-414.0</td>
      <td>414.0</td>
      <td>35.0</td>
      <td>449.0</td>
      <td>-35.0</td>
      <td>-449.0</td>
      <td>-0.829659</td>
      <td>0.829659</td>
      <td>0.070140</td>
      <td>0.899800</td>
      <td>-0.070140</td>
      <td>-0.899800</td>
      <td>2679.0</td>
      <td>48311</td>
      <td>McMullen County, Texas</td>
      <td>460.0</td>
      <td>{'rings': [[[-10946606, 3326438.0001000017], [...</td>
      <td>3.882883e+09</td>
      <td>253408.774844</td>
      <td>1.084783</td>
      <td>1.073913</td>
      <td>0.086957</td>
      <td>0.986957</td>
      <td>0.010870</td>
    </tr>
  </tbody>
</table>
</div>



There are four counties with very low population that resulted in voter turnout values above 100%. You could remove these records from the data or do additional research to identify the source of this issue. 

***

## Update validated data

After reviewing the Census Bureau voting age population data for 2016, you determined that these counties have a low voting age population with a fairly high margin of error. This may be the reason why these counties have a voter turnout rate higher than 100%. You will recalculate the voter turnout field for these counties using the upper range of their margin of error: 
- San Juan County, Colorado: 574
- Harding County, New Mexico: 562
- Loving County, Texas: 86
- McMullen County, Texas: 566

**Note: This information was extracted from this [table](https://data.census.gov/cedsci/table?q=voting%20age%20population%202016&g=0500000US08111,35021,48301,48311&hidePreview=true&table=DP05&tid=ACSDP5Y2016.DP05&t=Age%20and%20Sex&y=2016&lastDisplayedRow=6&vintage=2016&mode=&moe=true).**

To confirm that this correction addressed the issue, you will again query for counties with a voter turnout value above 100%.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>FIPS</th>
      <th>year</th>
      <th>county</th>
      <th>state</th>
      <th>state_po</th>
      <th>office</th>
      <th>candidate_dem</th>
      <th>votes_dem</th>
      <th>candidate_gop</th>
      <th>votes_gop</th>
      <th>votes_total</th>
      <th>votes_other</th>
      <th>voter_share_major_party</th>
      <th>voter_share_dem</th>
      <th>voter_share_gop</th>
      <th>voter_share_other</th>
      <th>rawdiff_dem_vs_gop</th>
      <th>rawdiff_gop_vs_dem</th>
      <th>rawdiff_dem_vs_other</th>
      <th>rawdiff_gop_vs_other</th>
      <th>rawdiff_other_vs_dem</th>
      <th>rawdiff_other_vs_gop</th>
      <th>pctdiff_dem_vs_gop</th>
      <th>pctdiff_gop_vs_dem</th>
      <th>pctdiff_dem_vs_other</th>
      <th>pctdiff_gop_vs_other</th>
      <th>pctdiff_other_vs_dem</th>
      <th>pctdiff_other_vs_gop</th>
      <th>OBJECTID</th>
      <th>GEOID</th>
      <th>GEONAME</th>
      <th>Total_cvap_est</th>
      <th>SHAPE</th>
      <th>Shape__Area</th>
      <th>Shape__Length</th>
      <th>voter_turnout</th>
      <th>voter_turnout_majparty</th>
      <th>voter_turnout_dem</th>
      <th>voter_turnout_gop</th>
      <th>voter_turnout_other</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
</div>


No records are returned, indicating that there are no counties with a turnout value above 100%. Well done! You have cleaned the data. Next, you will convert the dataframe to a permanent dataset called a feature class. Feature classes are stored in an ArcGIS Pro file geodatabase.

***

## Convert data frames to feature classes

You will use the ArcGIS API for Python, imported at the beginning of this script, to export the spatially-enabled data frame to a feature class.


## Correct for missing data

The feature class is missing a county in South Dakota. You will correct this issue by further exploring the data.

The county geometry dataset identifies the missing county as Oglala Lakota County. By searching online for this county, you determine that Oglala Lakota County changed its county name and FIPS in 2015. It was originally Shannon County with a FIPS of 46113 and is now Oglala Lakota County with a FIPS of 46102. You will search the election data for the current FIPS to try to find the missing data.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>FIPS</th>
      <th>year</th>
      <th>county</th>
      <th>state</th>
      <th>state_po</th>
      <th>office</th>
      <th>candidate_dem</th>
      <th>votes_dem</th>
      <th>candidate_gop</th>
      <th>votes_gop</th>
      <th>votes_total</th>
      <th>votes_other</th>
      <th>voter_share_major_party</th>
      <th>voter_share_dem</th>
      <th>voter_share_gop</th>
      <th>voter_share_other</th>
      <th>rawdiff_dem_vs_gop</th>
      <th>rawdiff_gop_vs_dem</th>
      <th>rawdiff_dem_vs_other</th>
      <th>rawdiff_gop_vs_other</th>
      <th>rawdiff_other_vs_dem</th>
      <th>rawdiff_other_vs_gop</th>
      <th>pctdiff_dem_vs_gop</th>
      <th>pctdiff_gop_vs_dem</th>
      <th>pctdiff_dem_vs_other</th>
      <th>pctdiff_gop_vs_other</th>
      <th>pctdiff_other_vs_dem</th>
      <th>pctdiff_other_vs_gop</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
</div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>FIPS</th>
      <th>year</th>
      <th>county</th>
      <th>state</th>
      <th>state_po</th>
      <th>office</th>
      <th>candidate_dem</th>
      <th>votes_dem</th>
      <th>candidate_gop</th>
      <th>votes_gop</th>
      <th>votes_total</th>
      <th>votes_other</th>
      <th>voter_share_major_party</th>
      <th>voter_share_dem</th>
      <th>voter_share_gop</th>
      <th>voter_share_other</th>
      <th>rawdiff_dem_vs_gop</th>
      <th>rawdiff_gop_vs_dem</th>
      <th>rawdiff_dem_vs_other</th>
      <th>rawdiff_gop_vs_other</th>
      <th>rawdiff_other_vs_dem</th>
      <th>rawdiff_other_vs_gop</th>
      <th>pctdiff_dem_vs_gop</th>
      <th>pctdiff_gop_vs_dem</th>
      <th>pctdiff_dem_vs_other</th>
      <th>pctdiff_gop_vs_other</th>
      <th>pctdiff_other_vs_dem</th>
      <th>pctdiff_other_vs_gop</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2428</th>
      <td>46113</td>
      <td>2016</td>
      <td>Oglala Lakota</td>
      <td>South Dakota</td>
      <td>SD</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2510.0</td>
      <td>Donald Trump</td>
      <td>241.0</td>
      <td>2905</td>
      <td>154.0</td>
      <td>0.946988</td>
      <td>0.864028</td>
      <td>0.08296</td>
      <td>0.053012</td>
      <td>2269.0</td>
      <td>-2269.0</td>
      <td>2356.0</td>
      <td>87.0</td>
      <td>-2356.0</td>
      <td>-87.0</td>
      <td>0.781067</td>
      <td>-0.781067</td>
      <td>0.811015</td>
      <td>0.029948</td>
      <td>-0.811015</td>
      <td>-0.029948</td>
    </tr>
  </tbody>
</table>
</div>

There is the issue! The data has the correct name (Oglala Lakota) but the wrong FIPS (46113). You will correct this data issue.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>FIPS</th>
      <th>year</th>
      <th>county</th>
      <th>state</th>
      <th>state_po</th>
      <th>office</th>
      <th>candidate_dem</th>
      <th>votes_dem</th>
      <th>candidate_gop</th>
      <th>votes_gop</th>
      <th>votes_total</th>
      <th>votes_other</th>
      <th>voter_share_major_party</th>
      <th>voter_share_dem</th>
      <th>voter_share_gop</th>
      <th>voter_share_other</th>
      <th>rawdiff_dem_vs_gop</th>
      <th>rawdiff_gop_vs_dem</th>
      <th>rawdiff_dem_vs_other</th>
      <th>rawdiff_gop_vs_other</th>
      <th>rawdiff_other_vs_dem</th>
      <th>rawdiff_other_vs_gop</th>
      <th>pctdiff_dem_vs_gop</th>
      <th>pctdiff_gop_vs_dem</th>
      <th>pctdiff_dem_vs_other</th>
      <th>pctdiff_gop_vs_other</th>
      <th>pctdiff_other_vs_dem</th>
      <th>pctdiff_other_vs_gop</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2428</th>
      <td>46102</td>
      <td>2016</td>
      <td>Oglala Lakota</td>
      <td>South Dakota</td>
      <td>SD</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>2510.0</td>
      <td>Donald Trump</td>
      <td>241.0</td>
      <td>2905</td>
      <td>154.0</td>
      <td>0.946988</td>
      <td>0.864028</td>
      <td>0.08296</td>
      <td>0.053012</td>
      <td>2269.0</td>
      <td>-2269.0</td>
      <td>2356.0</td>
      <td>87.0</td>
      <td>-2356.0</td>
      <td>-87.0</td>
      <td>0.781067</td>
      <td>-0.781067</td>
      <td>0.811015</td>
      <td>0.029948</td>
      <td>-0.811015</td>
      <td>-0.029948</td>
    </tr>
  </tbody>
</table>
</div>



With the corrected FIPS value for Oglala Lakota County, you can now rejoin the geometry, recalculate the voting turnout field, and recreate the feature class. 

You will export the data frame to a feature class that you can visualize and analyze in ArcGIS Pro. 

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>state</th>
      <th>state_po</th>
      <th>county</th>
      <th>FIPS</th>
      <th>office</th>
      <th>candidate</th>
      <th>party</th>
      <th>candidatevotes</th>
      <th>totalvotes</th>
      <th>version</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>8781</th>
      <td>2016</td>
      <td>Virginia</td>
      <td>VA</td>
      <td>Bedford</td>
      <td>51515</td>
      <td>President</td>
      <td>Hillary Clinton</td>
      <td>democratic</td>
      <td>NaN</td>
      <td>0</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>8782</th>
      <td>2016</td>
      <td>Virginia</td>
      <td>VA</td>
      <td>Bedford</td>
      <td>51515</td>
      <td>President</td>
      <td>Donald Trump</td>
      <td>republican</td>
      <td>NaN</td>
      <td>0</td>
      <td>20190722</td>
    </tr>
    <tr>
      <th>8783</th>
      <td>2016</td>
      <td>Virginia</td>
      <td>VA</td>
      <td>Bedford</td>
      <td>51515</td>
      <td>President</td>
      <td>Other</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>20190722</td>
    </tr>
  </tbody>
</table>
</div>
