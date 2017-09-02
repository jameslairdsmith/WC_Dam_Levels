Cleaning Western Cape Dam Level Data
====================================

The following code is created for the purpose of extracting and cleaning
data on the dam levels in the Western Cape (WC) province of South
Africa. The data is provided by the WC provincial government.

The data is available from:
<https://web1.capetown.gov.za/web1/opendataportal/DatasetDetail?DatasetName=Dam+levels>

Load Dependencies
-----------------

    library(knitr)
    library(tidyverse)

I use knitr::kable for the rendering of the markdown tables. This makes
it easier to read in many formats, notably Github.

Reading in the Data
-------------------

    DamLevels <- read_csv("~/Google Drive/Applications/Github/WC_Dam_Levels/Data/Raw_Data.csv")

    DamLevels %>% 
      head(10) %>% 
      select(1:9) %>% 
      kable()

<table>
<thead>
<tr class="header">
<th align="left">BULK WATER STORAGE</th>
<th align="left">X2</th>
<th align="left">X3</th>
<th align="left">X4</th>
<th align="left">X5</th>
<th align="left">X6</th>
<th align="left">X7</th>
<th align="left">X8</th>
<th align="left">X9</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">NA</td>
<td align="left">58 644</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">33 517</td>
<td align="left">335</td>
<td align="left">NA</td>
<td align="left">NA</td>
</tr>
<tr class="even">
<td align="left">NA</td>
<td align="left">WEMMERSHOEK</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">STEENBRAS LOWER</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
</tr>
<tr class="odd">
<td align="left">DATE</td>
<td align="left">HEIGHT</td>
<td align="left">STORAGE</td>
<td align="left">Current</td>
<td align="left">Last Year</td>
<td align="left">HEIGHT</td>
<td align="left">STORAGE</td>
<td align="left">Current</td>
<td align="left">Last Year</td>
</tr>
<tr class="even">
<td align="left">NA</td>
<td align="left">(m)</td>
<td align="left">(Ml)</td>
<td align="left">%</td>
<td align="left">%</td>
<td align="left">(m)</td>
<td align="left">(Ml)</td>
<td align="left">%</td>
<td align="left">%</td>
</tr>
<tr class="odd">
<td align="left">01-Jan-12</td>
<td align="left">48.23</td>
<td align="left">44 621</td>
<td align="left">76.1</td>
<td align="left">NA</td>
<td align="left">20.34</td>
<td align="left">23 549</td>
<td align="left">70.3</td>
<td align="left">NA</td>
</tr>
<tr class="even">
<td align="left">02-Jan-12</td>
<td align="left">48.21</td>
<td align="left">44 571</td>
<td align="left">76</td>
<td align="left">NA</td>
<td align="left">20.31</td>
<td align="left">23 460</td>
<td align="left">70</td>
<td align="left">NA</td>
</tr>
<tr class="odd">
<td align="left">03-Jan-12</td>
<td align="left">48.17</td>
<td align="left">44 471</td>
<td align="left">75.8</td>
<td align="left">NA</td>
<td align="left">20.28</td>
<td align="left">23 372</td>
<td align="left">69.7</td>
<td align="left">NA</td>
</tr>
<tr class="even">
<td align="left">04-Jan-12</td>
<td align="left">48.13</td>
<td align="left">44 372</td>
<td align="left">75.7</td>
<td align="left">NA</td>
<td align="left">20.26</td>
<td align="left">23 313</td>
<td align="left">69.6</td>
<td align="left">NA</td>
</tr>
<tr class="odd">
<td align="left">05-Jan-12</td>
<td align="left">48.11</td>
<td align="left">44 322</td>
<td align="left">75.6</td>
<td align="left">NA</td>
<td align="left">20.23</td>
<td align="left">23 224</td>
<td align="left">69.3</td>
<td align="left">NA</td>
</tr>
<tr class="even">
<td align="left">06-Jan-12</td>
<td align="left">48.07</td>
<td align="left">44 221</td>
<td align="left">75.4</td>
<td align="left">NA</td>
<td align="left">20.2</td>
<td align="left">23 136</td>
<td align="left">69</td>
<td align="left">NA</td>
</tr>
</tbody>
</table>

The data is not in a tidy form and so requires cleaning.

Dates
-----

A logical place to begin is with the date column as all the dam levels
are aligned to it in wide format.

    DamLevelsDate<-DamLevels[5:nrow(DamLevels),1]    # The dates begin in the 5th row

    DamLevelsDate %>% 
      head(10) %>% 
      kable()

BULK WATER STORAGE
------------------

01-Jan-12  
02-Jan-12  
03-Jan-12  
04-Jan-12  
05-Jan-12  
06-Jan-12  
07-Jan-12  
08-Jan-12  
09-Jan-12  
10-Jan-12

The dates are parsed in as a character column at the outset. In order to
parse the strings into a date format, I make use of the lubridate
package.

    library(lubridate)

    DamLevelsDateClean <- DamLevelsDate %>% 
      rename(Date=`BULK WATER STORAGE`) %>%     # I rename the column to remove the full caps.
      mutate(Date=dmy(Date))

    DamLevelsDateClean %>% 
      cbind(DamLevelsDate) %>% 
      head(10) %>% 
      kable()

<table>
<thead>
<tr class="header">
<th align="left">Date</th>
<th align="left">BULK WATER STORAGE</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">2012-01-01</td>
<td align="left">01-Jan-12</td>
</tr>
<tr class="even">
<td align="left">2012-01-02</td>
<td align="left">02-Jan-12</td>
</tr>
<tr class="odd">
<td align="left">2012-01-03</td>
<td align="left">03-Jan-12</td>
</tr>
<tr class="even">
<td align="left">2012-01-04</td>
<td align="left">04-Jan-12</td>
</tr>
<tr class="odd">
<td align="left">2012-01-05</td>
<td align="left">05-Jan-12</td>
</tr>
<tr class="even">
<td align="left">2012-01-06</td>
<td align="left">06-Jan-12</td>
</tr>
<tr class="odd">
<td align="left">2012-01-07</td>
<td align="left">07-Jan-12</td>
</tr>
<tr class="even">
<td align="left">2012-01-08</td>
<td align="left">08-Jan-12</td>
</tr>
<tr class="odd">
<td align="left">2012-01-09</td>
<td align="left">09-Jan-12</td>
</tr>
<tr class="even">
<td align="left">2012-01-10</td>
<td align="left">10-Jan-12</td>
</tr>
</tbody>
</table>

The measurements are taken exactly one day apart. In the process of
conducting the analysis however I found that there were some anomalies
in the progression of the dates.

To check this, I perform some transformations on the data using dplyr.
In particular I check to make sure that each date is exactly one day
away from the date immediately above it.

    DamLevelsDateClean %>% 
      mutate(initnum=1:nrow(DamLevelsDateClean)) %>% # I specify a new column of the initial row numbers for reference.
      mutate(DamLevelsDateLag=lag(DamLevelsDateClean$Date)) %>%   
      mutate(Diff=DamLevelsDateLag-Date) %>%  
      arrange(Diff)  %>% 
      head(10) %>% 
      kable()

<table>
<thead>
<tr class="header">
<th align="left">Date</th>
<th align="right">initnum</th>
<th align="left">DamLevelsDateLag</th>
<th align="left">Diff</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">2020-05-21</td>
<td align="right">1968</td>
<td align="left">2019-05-20</td>
<td align="left">-367 days</td>
</tr>
<tr class="even">
<td align="left">2018-05-19</td>
<td align="right">1966</td>
<td align="left">2017-05-18</td>
<td align="left">-366 days</td>
</tr>
<tr class="odd">
<td align="left">2019-05-20</td>
<td align="right">1967</td>
<td align="left">2018-05-19</td>
<td align="left">-366 days</td>
</tr>
<tr class="even">
<td align="left">2021-05-22</td>
<td align="right">1969</td>
<td align="left">2020-05-21</td>
<td align="left">-366 days</td>
</tr>
<tr class="odd">
<td align="left">2017-08-08</td>
<td align="right">1955</td>
<td align="left">2017-05-07</td>
<td align="left">-93 days</td>
</tr>
<tr class="even">
<td align="left">2012-01-02</td>
<td align="right">2</td>
<td align="left">2012-01-01</td>
<td align="left">-1 days</td>
</tr>
<tr class="odd">
<td align="left">2012-01-03</td>
<td align="right">3</td>
<td align="left">2012-01-02</td>
<td align="left">-1 days</td>
</tr>
<tr class="even">
<td align="left">2012-01-04</td>
<td align="right">4</td>
<td align="left">2012-01-03</td>
<td align="left">-1 days</td>
</tr>
<tr class="odd">
<td align="left">2012-01-05</td>
<td align="right">5</td>
<td align="left">2012-01-04</td>
<td align="left">-1 days</td>
</tr>
<tr class="even">
<td align="left">2012-01-06</td>
<td align="right">6</td>
<td align="left">2012-01-05</td>
<td align="left">-1 days</td>
</tr>
</tbody>
</table>

This proves not to be the case. By some error, a few of the dates appear
to be in the future. I managed to correct these by inspection.

    DamLevelsDateClean[1966,1]<-ymd("2017-05-19")
    DamLevelsDateClean[1967,1]<-ymd("2017-05-20")
    DamLevelsDateClean[1968,1]<-ymd("2017-05-21")
    DamLevelsDateClean[1969,1]<-ymd("2017-05-22")
    DamLevelsDateClean[1955,1]<-ymd("2017-05-08")

    DamLevelsDateClean %>% 
      mutate(initnum=1:nrow(DamLevelsDate)) %>%   
      mutate(DamLevelsDateLag=lag(DamLevelsDateClean$Date)) %>%   
      mutate(Diff=DamLevelsDateLag-Date) %>%  
      arrange(Diff)  %>% 
      head(10) %>% 
      kable()

<table>
<thead>
<tr class="header">
<th align="left">Date</th>
<th align="right">initnum</th>
<th align="left">DamLevelsDateLag</th>
<th align="left">Diff</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">2012-01-02</td>
<td align="right">2</td>
<td align="left">2012-01-01</td>
<td align="left">-1 days</td>
</tr>
<tr class="even">
<td align="left">2012-01-03</td>
<td align="right">3</td>
<td align="left">2012-01-02</td>
<td align="left">-1 days</td>
</tr>
<tr class="odd">
<td align="left">2012-01-04</td>
<td align="right">4</td>
<td align="left">2012-01-03</td>
<td align="left">-1 days</td>
</tr>
<tr class="even">
<td align="left">2012-01-05</td>
<td align="right">5</td>
<td align="left">2012-01-04</td>
<td align="left">-1 days</td>
</tr>
<tr class="odd">
<td align="left">2012-01-06</td>
<td align="right">6</td>
<td align="left">2012-01-05</td>
<td align="left">-1 days</td>
</tr>
<tr class="even">
<td align="left">2012-01-07</td>
<td align="right">7</td>
<td align="left">2012-01-06</td>
<td align="left">-1 days</td>
</tr>
<tr class="odd">
<td align="left">2012-01-08</td>
<td align="right">8</td>
<td align="left">2012-01-07</td>
<td align="left">-1 days</td>
</tr>
<tr class="even">
<td align="left">2012-01-09</td>
<td align="right">9</td>
<td align="left">2012-01-08</td>
<td align="left">-1 days</td>
</tr>
<tr class="odd">
<td align="left">2012-01-10</td>
<td align="right">10</td>
<td align="left">2012-01-09</td>
<td align="left">-1 days</td>
</tr>
<tr class="even">
<td align="left">2012-01-11</td>
<td align="right">11</td>
<td align="left">2012-01-10</td>
<td align="left">-1 days</td>
</tr>
</tbody>
</table>

Extracting Dam Names
--------------------

The names of the various dams are given above the various columns and
can be extracted in sequence. They are also changed to title case by
means of the stringr package.

    library(stringr)

    seq<-seq(2,50,4)
    Dams<-DamLevels[2,seq]    # The dam mnames are in the second row
    Dams<-as.character(Dams)
    Dams<-str_to_title(Dams)
    Dams[4]<-"Voelvlei"   

    Dams %>% 
      kable()

<table>
<tbody>
<tr class="odd">
<td align="left">Wemmershoek</td>
</tr>
<tr class="even">
<td align="left">Steenbras Lower</td>
</tr>
<tr class="odd">
<td align="left">Steenbras Upper</td>
</tr>
<tr class="even">
<td align="left">Voelvlei</td>
</tr>
<tr class="odd">
<td align="left">Hely-Hutchinson</td>
</tr>
<tr class="even">
<td align="left">Woodhead</td>
</tr>
<tr class="odd">
<td align="left">Victoria</td>
</tr>
<tr class="even">
<td align="left">Alexandra</td>
</tr>
<tr class="odd">
<td align="left">De Villiers</td>
</tr>
<tr class="even">
<td align="left">Kleinplaats</td>
</tr>
<tr class="odd">
<td align="left">Lewis Gay</td>
</tr>
<tr class="even">
<td align="left">Theewaterskloof</td>
</tr>
<tr class="odd">
<td align="left">Berg River</td>
</tr>
</tbody>
</table>

The name of Voelvlei dam usually contains a special character, which
causes problems in various rendering envrioments. For simplicity it is
replaced with the plain text version.

Extracting the Storage Data
---------------------------

Each column represents a dam. The columns are evenly spaced and so can
be extracted using a seq. The dam names (above) are used as the new
column names.

    seq<-seq(3,51,4)

    StorageWide<-DamLevels[5:nrow(DamLevels),seq]
    colnames(StorageWide)<-Dams

    StorageWide %>% 
      head(10) %>% 
      kable()

<table>
<thead>
<tr class="header">
<th align="left">Wemmershoek</th>
<th align="left">Steenbras Lower</th>
<th align="left">Steenbras Upper</th>
<th align="left">Voelvlei</th>
<th align="left">Hely-Hutchinson</th>
<th align="left">Woodhead</th>
<th align="left">Victoria</th>
<th align="left">Alexandra</th>
<th align="left">De Villiers</th>
<th align="left">Kleinplaats</th>
<th align="left">Lewis Gay</th>
<th align="left">Theewaterskloof</th>
<th align="left">Berg River</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">44 621</td>
<td align="left">23 549</td>
<td align="left">29 620</td>
<td align="left">124 100</td>
<td align="left">763</td>
<td align="left">742.8</td>
<td align="left">0</td>
<td align="left">99.9</td>
<td align="left">196.5</td>
<td align="left">336.6</td>
<td align="left">128.3</td>
<td align="left">357 963</td>
<td align="left">115 930</td>
</tr>
<tr class="even">
<td align="left">44 571</td>
<td align="left">23 460</td>
<td align="left">29 620</td>
<td align="left">123 812</td>
<td align="left">763</td>
<td align="left">742.8</td>
<td align="left">0</td>
<td align="left">99.2</td>
<td align="left">196.5</td>
<td align="left">336.6</td>
<td align="left">128.3</td>
<td align="left">356 677</td>
<td align="left">114 850</td>
</tr>
<tr class="odd">
<td align="left">44 471</td>
<td align="left">23 372</td>
<td align="left">29 570</td>
<td align="left">123 237</td>
<td align="left">773</td>
<td align="left">745.4</td>
<td align="left">0</td>
<td align="left">98.7</td>
<td align="left">197.3</td>
<td align="left">336.6</td>
<td align="left">128.3</td>
<td align="left">355 394</td>
<td align="left">114 280</td>
</tr>
<tr class="even">
<td align="left">44 372</td>
<td align="left">23 313</td>
<td align="left">29 620</td>
<td align="left">122 520</td>
<td align="left">794</td>
<td align="left">749.6</td>
<td align="left">0</td>
<td align="left">99.2</td>
<td align="left">197.8</td>
<td align="left">334.2</td>
<td align="left">128.3</td>
<td align="left">353 687</td>
<td align="left">113 770</td>
</tr>
<tr class="odd">
<td align="left">44 322</td>
<td align="left">23 224</td>
<td align="left">29 317</td>
<td align="left">121 947</td>
<td align="left">797</td>
<td align="left">749.6</td>
<td align="left">0</td>
<td align="left">98.9</td>
<td align="left">198</td>
<td align="left">330.6</td>
<td align="left">128.3</td>
<td align="left">351 135</td>
<td align="left">113 410</td>
</tr>
<tr class="even">
<td align="left">44 221</td>
<td align="left">23 136</td>
<td align="left">29 545</td>
<td align="left">121 374</td>
<td align="left">798</td>
<td align="left">737.7</td>
<td align="left">0</td>
<td align="left">98.5</td>
<td align="left">198.5</td>
<td align="left">330.6</td>
<td align="left">128.3</td>
<td align="left">349 863</td>
<td align="left">113 100</td>
</tr>
<tr class="odd">
<td align="left">44 074</td>
<td align="left">23 047</td>
<td align="left">29 495</td>
<td align="left">121 232</td>
<td align="left">801</td>
<td align="left">727.7</td>
<td align="left">0</td>
<td align="left">97.7</td>
<td align="left">198.5</td>
<td align="left">330.6</td>
<td align="left">128.3</td>
<td align="left">348 594</td>
<td align="left">113 100</td>
</tr>
<tr class="even">
<td align="left">43 973</td>
<td align="left">23 047</td>
<td align="left">29 242</td>
<td align="left">121 232</td>
<td align="left">801</td>
<td align="left">717.2</td>
<td align="left">0</td>
<td align="left">97.3</td>
<td align="left">198.3</td>
<td align="left">330.6</td>
<td align="left">128.3</td>
<td align="left">347 327</td>
<td align="left">113 100</td>
</tr>
<tr class="odd">
<td align="left">43 826</td>
<td align="left">22 988</td>
<td align="left">29 646</td>
<td align="left">120 233</td>
<td align="left">801</td>
<td align="left">703.5</td>
<td align="left">0</td>
<td align="left">96.8</td>
<td align="left">197.8</td>
<td align="left">328.3</td>
<td align="left">127.2</td>
<td align="left">345 643</td>
<td align="left">113 100</td>
</tr>
<tr class="even">
<td align="left">43 752</td>
<td align="left">22 900</td>
<td align="left">29 595</td>
<td align="left">119 805</td>
<td align="left">802</td>
<td align="left">691.5</td>
<td align="left">0</td>
<td align="left">95.8</td>
<td align="left">198.3</td>
<td align="left">325.9</td>
<td align="left">127.2</td>
<td align="left">343 963</td>
<td align="left">111 780</td>
</tr>
</tbody>
</table>

Combine the Data
----------------

To combine the data, I bind the date column to the storage columns.

    StorageWide<-cbind(DamLevelsDateClean,StorageWide)

    StorageWide %>% 
      head(10) %>% 
      kable()

<table>
<thead>
<tr class="header">
<th align="left">Date</th>
<th align="left">Wemmershoek</th>
<th align="left">Steenbras Lower</th>
<th align="left">Steenbras Upper</th>
<th align="left">Voelvlei</th>
<th align="left">Hely-Hutchinson</th>
<th align="left">Woodhead</th>
<th align="left">Victoria</th>
<th align="left">Alexandra</th>
<th align="left">De Villiers</th>
<th align="left">Kleinplaats</th>
<th align="left">Lewis Gay</th>
<th align="left">Theewaterskloof</th>
<th align="left">Berg River</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">2012-01-01</td>
<td align="left">44 621</td>
<td align="left">23 549</td>
<td align="left">29 620</td>
<td align="left">124 100</td>
<td align="left">763</td>
<td align="left">742.8</td>
<td align="left">0</td>
<td align="left">99.9</td>
<td align="left">196.5</td>
<td align="left">336.6</td>
<td align="left">128.3</td>
<td align="left">357 963</td>
<td align="left">115 930</td>
</tr>
<tr class="even">
<td align="left">2012-01-02</td>
<td align="left">44 571</td>
<td align="left">23 460</td>
<td align="left">29 620</td>
<td align="left">123 812</td>
<td align="left">763</td>
<td align="left">742.8</td>
<td align="left">0</td>
<td align="left">99.2</td>
<td align="left">196.5</td>
<td align="left">336.6</td>
<td align="left">128.3</td>
<td align="left">356 677</td>
<td align="left">114 850</td>
</tr>
<tr class="odd">
<td align="left">2012-01-03</td>
<td align="left">44 471</td>
<td align="left">23 372</td>
<td align="left">29 570</td>
<td align="left">123 237</td>
<td align="left">773</td>
<td align="left">745.4</td>
<td align="left">0</td>
<td align="left">98.7</td>
<td align="left">197.3</td>
<td align="left">336.6</td>
<td align="left">128.3</td>
<td align="left">355 394</td>
<td align="left">114 280</td>
</tr>
<tr class="even">
<td align="left">2012-01-04</td>
<td align="left">44 372</td>
<td align="left">23 313</td>
<td align="left">29 620</td>
<td align="left">122 520</td>
<td align="left">794</td>
<td align="left">749.6</td>
<td align="left">0</td>
<td align="left">99.2</td>
<td align="left">197.8</td>
<td align="left">334.2</td>
<td align="left">128.3</td>
<td align="left">353 687</td>
<td align="left">113 770</td>
</tr>
<tr class="odd">
<td align="left">2012-01-05</td>
<td align="left">44 322</td>
<td align="left">23 224</td>
<td align="left">29 317</td>
<td align="left">121 947</td>
<td align="left">797</td>
<td align="left">749.6</td>
<td align="left">0</td>
<td align="left">98.9</td>
<td align="left">198</td>
<td align="left">330.6</td>
<td align="left">128.3</td>
<td align="left">351 135</td>
<td align="left">113 410</td>
</tr>
<tr class="even">
<td align="left">2012-01-06</td>
<td align="left">44 221</td>
<td align="left">23 136</td>
<td align="left">29 545</td>
<td align="left">121 374</td>
<td align="left">798</td>
<td align="left">737.7</td>
<td align="left">0</td>
<td align="left">98.5</td>
<td align="left">198.5</td>
<td align="left">330.6</td>
<td align="left">128.3</td>
<td align="left">349 863</td>
<td align="left">113 100</td>
</tr>
<tr class="odd">
<td align="left">2012-01-07</td>
<td align="left">44 074</td>
<td align="left">23 047</td>
<td align="left">29 495</td>
<td align="left">121 232</td>
<td align="left">801</td>
<td align="left">727.7</td>
<td align="left">0</td>
<td align="left">97.7</td>
<td align="left">198.5</td>
<td align="left">330.6</td>
<td align="left">128.3</td>
<td align="left">348 594</td>
<td align="left">113 100</td>
</tr>
<tr class="even">
<td align="left">2012-01-08</td>
<td align="left">43 973</td>
<td align="left">23 047</td>
<td align="left">29 242</td>
<td align="left">121 232</td>
<td align="left">801</td>
<td align="left">717.2</td>
<td align="left">0</td>
<td align="left">97.3</td>
<td align="left">198.3</td>
<td align="left">330.6</td>
<td align="left">128.3</td>
<td align="left">347 327</td>
<td align="left">113 100</td>
</tr>
<tr class="odd">
<td align="left">2012-01-09</td>
<td align="left">43 826</td>
<td align="left">22 988</td>
<td align="left">29 646</td>
<td align="left">120 233</td>
<td align="left">801</td>
<td align="left">703.5</td>
<td align="left">0</td>
<td align="left">96.8</td>
<td align="left">197.8</td>
<td align="left">328.3</td>
<td align="left">127.2</td>
<td align="left">345 643</td>
<td align="left">113 100</td>
</tr>
<tr class="even">
<td align="left">2012-01-10</td>
<td align="left">43 752</td>
<td align="left">22 900</td>
<td align="left">29 595</td>
<td align="left">119 805</td>
<td align="left">802</td>
<td align="left">691.5</td>
<td align="left">0</td>
<td align="left">95.8</td>
<td align="left">198.3</td>
<td align="left">325.9</td>
<td align="left">127.2</td>
<td align="left">343 963</td>
<td align="left">111 780</td>
</tr>
</tbody>
</table>

Convert the Data to Long Form
-----------------------------

The data is still in wide form and so needs to be converted to long
form. I do this using the reshape2 package.

The data from the storage column is still in character format and stil
contains spaces. These are removed and the data is converted to double
format.

    library(reshape2)

    StorageLong<-StorageWide %>% 
      melt(measure.vars = 2:ncol(StorageWide),variable.name = "Dam",value.name = "Storage") %>% 
      mutate(Storage=as.double(str_replace(Storage," ","")))

    StorageLong %>% 
      head(10) %>% 
      kable()

<table>
<thead>
<tr class="header">
<th align="left">Date</th>
<th align="left">Dam</th>
<th align="right">Storage</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">2012-01-01</td>
<td align="left">Wemmershoek</td>
<td align="right">44621</td>
</tr>
<tr class="even">
<td align="left">2012-01-02</td>
<td align="left">Wemmershoek</td>
<td align="right">44571</td>
</tr>
<tr class="odd">
<td align="left">2012-01-03</td>
<td align="left">Wemmershoek</td>
<td align="right">44471</td>
</tr>
<tr class="even">
<td align="left">2012-01-04</td>
<td align="left">Wemmershoek</td>
<td align="right">44372</td>
</tr>
<tr class="odd">
<td align="left">2012-01-05</td>
<td align="left">Wemmershoek</td>
<td align="right">44322</td>
</tr>
<tr class="even">
<td align="left">2012-01-06</td>
<td align="left">Wemmershoek</td>
<td align="right">44221</td>
</tr>
<tr class="odd">
<td align="left">2012-01-07</td>
<td align="left">Wemmershoek</td>
<td align="right">44074</td>
</tr>
<tr class="even">
<td align="left">2012-01-08</td>
<td align="left">Wemmershoek</td>
<td align="right">43973</td>
</tr>
<tr class="odd">
<td align="left">2012-01-09</td>
<td align="left">Wemmershoek</td>
<td align="right">43826</td>
</tr>
<tr class="even">
<td align="left">2012-01-10</td>
<td align="left">Wemmershoek</td>
<td align="right">43752</td>
</tr>
<tr class="odd">
<td align="left">##Extracting</td>
<td align="left">Capacity</td>
<td align="right"></td>
</tr>
</tbody>
</table>

Data on the capacities of the various dams line the top two rows of the
dataset. They are evenly spaced and so can also be extracted by means of
a sequence.

    seq<-seq(2,50,4)
    Capacities<-DamLevels[1:2,seq]
    Capacities<-data.frame(t(Capacities),stringsAsFactors = F)
    Capacities[4,2]<-c("Voelvlei")


    Capacities<-Capacities %>% 
      rename(Capacity=X1,Dam=X2) %>% 
      mutate(Capacity=as.double(str_replace(Capacity," ",""))) %>% 
      mutate(Dam=str_to_title(Dam))

    Capacities  %>% 
      kable()

<table>
<thead>
<tr class="header">
<th align="right">Capacity</th>
<th align="left">Dam</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="right">58644</td>
<td align="left">Wemmershoek</td>
</tr>
<tr class="even">
<td align="right">33517</td>
<td align="left">Steenbras Lower</td>
</tr>
<tr class="odd">
<td align="right">31767</td>
<td align="left">Steenbras Upper</td>
</tr>
<tr class="even">
<td align="right">164095</td>
<td align="left">Voelvlei</td>
</tr>
<tr class="odd">
<td align="right">925</td>
<td align="left">Hely-Hutchinson</td>
</tr>
<tr class="even">
<td align="right">955</td>
<td align="left">Woodhead</td>
</tr>
<tr class="odd">
<td align="right">128</td>
<td align="left">Victoria</td>
</tr>
<tr class="even">
<td align="right">134</td>
<td align="left">Alexandra</td>
</tr>
<tr class="odd">
<td align="right">242</td>
<td align="left">De Villiers</td>
</tr>
<tr class="even">
<td align="right">1301</td>
<td align="left">Kleinplaats</td>
</tr>
<tr class="odd">
<td align="right">168</td>
<td align="left">Lewis Gay</td>
</tr>
<tr class="even">
<td align="right">480188</td>
<td align="left">Theewaterskloof</td>
</tr>
<tr class="odd">
<td align="right">130010</td>
<td align="left">Berg River</td>
</tr>
</tbody>
</table>

Calculate total

    TotalCapacity<-Capacities %>% 
      summarise(sum(Capacity)) %>% 
      as.numeric()

    TotalCapacity

    ## [1] 902074

Merge Capacities with Long Data
===============================

    StorageLong<-StorageLong %>% 
      merge(Capacities)
    StorageLong %>% 
      head(20)

    ##          Dam       Date Storage Capacity
    ## 1  Alexandra 2012-01-01    99.9      134
    ## 2  Alexandra 2012-01-02    99.2      134
    ## 3  Alexandra 2012-01-03    98.7      134
    ## 4  Alexandra 2012-01-04    99.2      134
    ## 5  Alexandra 2012-01-05    98.9      134
    ## 6  Alexandra 2012-01-06    98.5      134
    ## 7  Alexandra 2012-01-07    97.7      134
    ## 8  Alexandra 2012-01-08    97.3      134
    ## 9  Alexandra 2012-01-09    96.8      134
    ## 10 Alexandra 2012-01-10    95.8      134
    ## 11 Alexandra 2012-01-11    95.4      134
    ## 12 Alexandra 2012-01-12    95.1      134
    ## 13 Alexandra 2012-01-13    94.4      134
    ## 14 Alexandra 2012-01-14    93.9      134
    ## 15 Alexandra 2012-01-15    93.2      134
    ## 16 Alexandra 2012-01-16    92.8      134
    ## 17 Alexandra 2012-01-17    92.3      134
    ## 18 Alexandra 2012-01-18    91.6      134
    ## 19 Alexandra 2012-01-19    90.9      134
    ## 20 Alexandra 2012-01-20    90.4      134

Calculate Percentage Capacities
===============================

    StorageLong<-StorageLong %>% 
      mutate(PercentDamCapacity=Storage/Capacity) %>% 
       mutate(PercentTotalCapacity=Storage/TotalCapacity)
    StorageLong %>% 
      head(20)

    ##          Dam       Date Storage Capacity PercentDamCapacity
    ## 1  Alexandra 2012-01-01    99.9      134          0.7455224
    ## 2  Alexandra 2012-01-02    99.2      134          0.7402985
    ## 3  Alexandra 2012-01-03    98.7      134          0.7365672
    ## 4  Alexandra 2012-01-04    99.2      134          0.7402985
    ## 5  Alexandra 2012-01-05    98.9      134          0.7380597
    ## 6  Alexandra 2012-01-06    98.5      134          0.7350746
    ## 7  Alexandra 2012-01-07    97.7      134          0.7291045
    ## 8  Alexandra 2012-01-08    97.3      134          0.7261194
    ## 9  Alexandra 2012-01-09    96.8      134          0.7223881
    ## 10 Alexandra 2012-01-10    95.8      134          0.7149254
    ## 11 Alexandra 2012-01-11    95.4      134          0.7119403
    ## 12 Alexandra 2012-01-12    95.1      134          0.7097015
    ## 13 Alexandra 2012-01-13    94.4      134          0.7044776
    ## 14 Alexandra 2012-01-14    93.9      134          0.7007463
    ## 15 Alexandra 2012-01-15    93.2      134          0.6955224
    ## 16 Alexandra 2012-01-16    92.8      134          0.6925373
    ## 17 Alexandra 2012-01-17    92.3      134          0.6888060
    ## 18 Alexandra 2012-01-18    91.6      134          0.6835821
    ## 19 Alexandra 2012-01-19    90.9      134          0.6783582
    ## 20 Alexandra 2012-01-20    90.4      134          0.6746269
    ##    PercentTotalCapacity
    ## 1          0.0001107448
    ## 2          0.0001099688
    ## 3          0.0001094145
    ## 4          0.0001099688
    ## 5          0.0001096362
    ## 6          0.0001091928
    ## 7          0.0001083060
    ## 8          0.0001078625
    ## 9          0.0001073083
    ## 10         0.0001061997
    ## 11         0.0001057563
    ## 12         0.0001054237
    ## 13         0.0001046477
    ## 14         0.0001040935
    ## 15         0.0001033175
    ## 16         0.0001028740
    ## 17         0.0001023198
    ## 18         0.0001015438
    ## 19         0.0001007678
    ## 20         0.0001002135

    #write.csv(file = "/Users/jameslairdsmith/Google Drive/Applications/Github/WC_Dam_Levels/Clean_WC_Dam_Levels.csv",StorageLong)
