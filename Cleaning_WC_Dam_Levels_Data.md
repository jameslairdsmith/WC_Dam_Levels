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

To combine the data, I bind the Date column to the storage columns.

    StorageWide<-cbind(DamLevelsDateClean,StorageWide)
    StorageWide %>% 
      head(20)

    ##          Date Wemmershoek Steenbras Lower Steenbras Upper Voelvlei
    ## 1  2012-01-01      44 621          23 549          29 620  124 100
    ## 2  2012-01-02      44 571          23 460          29 620  123 812
    ## 3  2012-01-03      44 471          23 372          29 570  123 237
    ## 4  2012-01-04      44 372          23 313          29 620  122 520
    ## 5  2012-01-05      44 322          23 224          29 317  121 947
    ## 6  2012-01-06      44 221          23 136          29 545  121 374
    ## 7  2012-01-07      44 074          23 047          29 495  121 232
    ## 8  2012-01-08      43 973          23 047          29 242  121 232
    ## 9  2012-01-09      43 826          22 988          29 646  120 233
    ## 10 2012-01-10      43 752          22 900          29 595  119 805
    ## 11 2012-01-11      43 654          22 870          29 595  117 960
    ## 12 2012-01-12      43 605          22 812          30 003  119 094
    ## 13 2012-01-13      43 483          22 725          29 773  118 527
    ## 14 2012-01-14      43 409          22 667          30 182  117 818
    ## 15 2012-01-15      43 336          22 552          30 156  117 818
    ## 16 2012-01-16      43 336          22 465          30 156  117 111
    ## 17 2012-01-17      43 140          22 407          29 545  115 700
    ## 18 2012-01-18      43 042          22 320          29 292  114 997
    ## 19 2012-01-19      42 969          22 175          29 141  114 576
    ## 20 2012-01-20      42 872          22 089          29 066  114 016
    ##    Hely-Hutchinson Woodhead Victoria Alexandra De Villiers Kleinplaats
    ## 1              763    742.8        0      99.9       196.5       336.6
    ## 2              763    742.8        0      99.2       196.5       336.6
    ## 3              773    745.4        0      98.7       197.3       336.6
    ## 4              794    749.6        0      99.2       197.8       334.2
    ## 5              797    749.6        0      98.9         198       330.6
    ## 6              798    737.7        0      98.5       198.5       330.6
    ## 7              801    727.7        0      97.7       198.5       330.6
    ## 8              801    717.2        0      97.3       198.3       330.6
    ## 9              801    703.5        0      96.8       197.8       328.3
    ## 10             802    691.5        0      95.8       198.3       325.9
    ## 11             804    677.7        0      95.4       198.5       325.9
    ## 12             804    666.7        0      95.1       198.5       323.6
    ## 13             804    653.8        0      94.4       198.3       321.2
    ## 14             802    642.4        0      93.9         198       320.1
    ## 15             808    631.7        0      93.2       198.8       316.6
    ## 16             811    620.2        0      92.8       198.5       316.6
    ## 17             811    606.8        0      92.3       198.8       316.6
    ## 18             802    604.6        0      91.6       195.7       316.6
    ## 19             794    601.8        0      90.9       192.8       316.6
    ## 20             781    600.3        0      90.4       189.6       316.6
    ##    Lewis Gay Theewaterskloof Berg River
    ## 1      128.3         357 963    115 930
    ## 2      128.3         356 677    114 850
    ## 3      128.3         355 394    114 280
    ## 4      128.3         353 687    113 770
    ## 5      128.3         351 135    113 410
    ## 6      128.3         349 863    113 100
    ## 7      128.3         348 594    113 100
    ## 8      128.3         347 327    113 100
    ## 9      127.2         345 643    113 100
    ## 10     127.2         343 963    111 780
    ## 11     127.2         342 706    111 370
    ## 12       125         341 452    111 370
    ## 13       125         340 617    110 570
    ## 14     123.9         338 951    110 570
    ## 15     117.6         337 705    110 570
    ## 16       114         336 461    109 460
    ## 17     112.5         333 981    109 060
    ## 18     112.5         333 157    108 650
    ## 19     112.5         332 334    108 340
    ## 20     112.5         330 282    107 990

Convert the Data to Long Form
-----------------------------

    library(reshape2)

    ## 
    ## Attaching package: 'reshape2'

    ## The following object is masked from 'package:tidyr':
    ## 
    ##     smiths

    StorageLong<-StorageWide %>% 
      melt(measure.vars = 2:ncol(StorageWide),variable.name = "Dam",value.name = "Storage") %>% 
      mutate(Storage=as.double(str_replace(Storage," ","")))

    ## Warning in evalq(as.double(str_replace(Storage, " ", "")), <environment>):
    ## NAs introduced by coercion

    StorageLong %>% 
      head(20)

    ##          Date         Dam Storage
    ## 1  2012-01-01 Wemmershoek   44621
    ## 2  2012-01-02 Wemmershoek   44571
    ## 3  2012-01-03 Wemmershoek   44471
    ## 4  2012-01-04 Wemmershoek   44372
    ## 5  2012-01-05 Wemmershoek   44322
    ## 6  2012-01-06 Wemmershoek   44221
    ## 7  2012-01-07 Wemmershoek   44074
    ## 8  2012-01-08 Wemmershoek   43973
    ## 9  2012-01-09 Wemmershoek   43826
    ## 10 2012-01-10 Wemmershoek   43752
    ## 11 2012-01-11 Wemmershoek   43654
    ## 12 2012-01-12 Wemmershoek   43605
    ## 13 2012-01-13 Wemmershoek   43483
    ## 14 2012-01-14 Wemmershoek   43409
    ## 15 2012-01-15 Wemmershoek   43336
    ## 16 2012-01-16 Wemmershoek   43336
    ## 17 2012-01-17 Wemmershoek   43140
    ## 18 2012-01-18 Wemmershoek   43042
    ## 19 2012-01-19 Wemmershoek   42969
    ## 20 2012-01-20 Wemmershoek   42872

Extracting Capacity
-------------------

    seq<-seq(2,50,4)
    Capacities<-DamLevels[1:2,seq]
    Capacities<-data.frame(t(Capacities))

    Capacities<-Capacities %>% 
      rename(Capacity=X1,Dam=X2) %>% 
      mutate(Capacity=as.double(str_replace(Capacity," ",""))) %>% 
      mutate(Dam=str_to_title(Dam))
    Capacities  

    ##    Capacity             Dam
    ## 1     58644     Wemmershoek
    ## 2     33517 Steenbras Lower
    ## 3     31767 Steenbras Upper
    ## 4    164095     Vo<cb>Lvlei
    ## 5       925 Hely-Hutchinson
    ## 6       955        Woodhead
    ## 7       128        Victoria
    ## 8       134       Alexandra
    ## 9       242     De Villiers
    ## 10     1301     Kleinplaats
    ## 11      168       Lewis Gay
    ## 12   480188 Theewaterskloof
    ## 13   130010      Berg River

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
