Cleaning Western Cape Dam Level Data
====================================

The following code is created for the purpose of extracting and cleaning
data on the dam levels in the Western Cape (WC) province of South
Africa. The data is provided by the WC provincial government.

The data is available from:
<https://web1.capetown.gov.za/web1/opendataportal/DatasetDetail?DatasetName=Dam+levels>

Load Dependencies
-----------------

    library(readr)
    library(magrittr)

Reading in the Data
-------------------

    DamLevels <- read_csv("~/Google Drive/Applications/Github/WC_Dam_Levels/Data/Raw_Data.csv")

    ## Warning: Missing column names filled in: 'X2' [2], 'X3' [3], 'X4' [4],
    ## 'X5' [5], 'X6' [6], 'X7' [7], 'X8' [8], 'X9' [9], 'X10' [10], 'X11' [11],
    ## 'X12' [12], 'X13' [13], 'X14' [14], 'X15' [15], 'X16' [16], 'X17' [17],
    ## 'X18' [18], 'X19' [19], 'X20' [20], 'X21' [21], 'X22' [22], 'X23' [23],
    ## 'X24' [24], 'X25' [25], 'X26' [26], 'X27' [27], 'X28' [28], 'X29' [29],
    ## 'X30' [30], 'X31' [31], 'X32' [32], 'X33' [33], 'X34' [34], 'X35' [35],
    ## 'X36' [36], 'X37' [37], 'X38' [38], 'X39' [39], 'X40' [40], 'X41' [41],
    ## 'X42' [42], 'X43' [43], 'X44' [44], 'X45' [45], 'X46' [46], 'X47' [47],
    ## 'X48' [48], 'X49' [49], 'X50' [50], 'X51' [51], 'X52' [52], 'X53' [53],
    ## 'X54' [54], 'X55' [55], 'X56' [56], 'X57' [57], 'X58' [58], 'X59' [59],
    ## 'X60' [60], 'X61' [61]

    ## Parsed with column specification:
    ## cols(
    ##   .default = col_character()
    ## )

    ## See spec(...) for full column specifications.

    DamLevels %>% 
      head(20)

    ## # A tibble: 20 x 61
    ##    `BULK WATER STORAGE`          X2      X3      X4        X5
    ##                   <chr>       <chr>   <chr>   <chr>     <chr>
    ##  1                 <NA>      58 644    <NA>    <NA>      <NA>
    ##  2                 <NA> WEMMERSHOEK    <NA>    <NA>      <NA>
    ##  3                 DATE      HEIGHT STORAGE Current Last Year
    ##  4                 <NA>         (m)    (Ml)       %         %
    ##  5            01-Jan-12       48.23  44 621    76.1      <NA>
    ##  6            02-Jan-12       48.21  44 571      76      <NA>
    ##  7            03-Jan-12       48.17  44 471    75.8      <NA>
    ##  8            04-Jan-12       48.13  44 372    75.7      <NA>
    ##  9            05-Jan-12       48.11  44 322    75.6      <NA>
    ## 10            06-Jan-12       48.07  44 221    75.4      <NA>
    ## 11            07-Jan-12       48.01  44 074    75.2      <NA>
    ## 12            08-Jan-12       47.97  43 973      75      <NA>
    ## 13            09-Jan-12       47.91  43 826    74.7      <NA>
    ## 14            10-Jan-12       47.88  43 752    74.6      <NA>
    ## 15            11-Jan-12       47.84  43 654    74.4      <NA>
    ## 16            12-Jan-12       47.82  43 605    74.4      <NA>
    ## 17            13-Jan-12       47.77  43 483    74.1      <NA>
    ## 18            14-Jan-12       47.74  43 409      74      <NA>
    ## 19            15-Jan-12       47.71  43 336    73.9      <NA>
    ## 20            16-Jan-12       47.71  43 336    73.9      <NA>
    ## # ... with 56 more variables: X6 <chr>, X7 <chr>, X8 <chr>, X9 <chr>,
    ## #   X10 <chr>, X11 <chr>, X12 <chr>, X13 <chr>, X14 <chr>, X15 <chr>,
    ## #   X16 <chr>, X17 <chr>, X18 <chr>, X19 <chr>, X20 <chr>, X21 <chr>,
    ## #   X22 <chr>, X23 <chr>, X24 <chr>, X25 <chr>, X26 <chr>, X27 <chr>,
    ## #   X28 <chr>, X29 <chr>, X30 <chr>, X31 <chr>, X32 <chr>, X33 <chr>,
    ## #   X34 <chr>, X35 <chr>, X36 <chr>, X37 <chr>, X38 <chr>, X39 <chr>,
    ## #   X40 <chr>, X41 <chr>, X42 <chr>, X43 <chr>, X44 <chr>, X45 <chr>,
    ## #   X46 <chr>, X47 <chr>, X48 <chr>, X49 <chr>, X50 <chr>, X51 <chr>,
    ## #   X52 <chr>, X53 <chr>, X54 <chr>, X55 <chr>, X56 <chr>, X57 <chr>,
    ## #   X58 <chr>, X59 <chr>, X60 <chr>, X61 <chr>

The data is not in a tidy form and so requires cleaning.

Dates
=====

It is logical to begin with the DATE column and join it to the remaining
columns afterwards.

    DamLevelsDate<-DamLevels[5:nrow(DamLevels),1]
    DamLevelsDate %>% 
      head(20)

    ## # A tibble: 20 x 1
    ##    `BULK WATER STORAGE`
    ##                   <chr>
    ##  1            01-Jan-12
    ##  2            02-Jan-12
    ##  3            03-Jan-12
    ##  4            04-Jan-12
    ##  5            05-Jan-12
    ##  6            06-Jan-12
    ##  7            07-Jan-12
    ##  8            08-Jan-12
    ##  9            09-Jan-12
    ## 10            10-Jan-12
    ## 11            11-Jan-12
    ## 12            12-Jan-12
    ## 13            13-Jan-12
    ## 14            14-Jan-12
    ## 15            15-Jan-12
    ## 16            16-Jan-12
    ## 17            17-Jan-12
    ## 18            18-Jan-12
    ## 19            19-Jan-12
    ## 20            20-Jan-12

As can be seen the dates are parsed in as a character column at the
outset. In order to parse the strings into a date format, I make use of
the lubridate package.

    library(lubridate)

    ## 
    ## Attaching package: 'lubridate'

    ## The following object is masked from 'package:base':
    ## 
    ##     date

    colnames(DamLevelsDate)<-c("Date")    # I rename the column to remove the all caps.
    DamLevelsDate$Date<-dmy(DamLevelsDate$Date)

    DamLevelsDate %>% 
      head(20)

    ## # A tibble: 20 x 1
    ##          Date
    ##        <date>
    ##  1 2012-01-01
    ##  2 2012-01-02
    ##  3 2012-01-03
    ##  4 2012-01-04
    ##  5 2012-01-05
    ##  6 2012-01-06
    ##  7 2012-01-07
    ##  8 2012-01-08
    ##  9 2012-01-09
    ## 10 2012-01-10
    ## 11 2012-01-11
    ## 12 2012-01-12
    ## 13 2012-01-13
    ## 14 2012-01-14
    ## 15 2012-01-15
    ## 16 2012-01-16
    ## 17 2012-01-17
    ## 18 2012-01-18
    ## 19 2012-01-19
    ## 20 2012-01-20

As can be seen, measurements are taken exactly one day apart. To check
this, I perform some transformations on the data using dplyr. In
particular I check to make sure that each date is exactly one day
different from the date immediately above it.

    library(dplyr)

    ## Warning: package 'dplyr' was built under R version 3.4.1

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:lubridate':
    ## 
    ##     intersect, setdiff, union

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

    DamLevelsDate %>% 
      mutate(initnum=1:nrow(DamLevelsDate)) %>%   
      mutate(DamLevelsDateLag=lag(DamLevelsDate$Date)) %>%   
      mutate(Diff=DamLevelsDateLag-Date) %>%  
      arrange(Diff)  %>% 
      head(20)

    ## # A tibble: 20 x 4
    ##          Date initnum DamLevelsDateLag      Diff
    ##        <date>   <int>           <date>    <time>
    ##  1 2020-05-21    1968       2019-05-20 -367 days
    ##  2 2018-05-19    1966       2017-05-18 -366 days
    ##  3 2019-05-20    1967       2018-05-19 -366 days
    ##  4 2021-05-22    1969       2020-05-21 -366 days
    ##  5 2017-08-08    1955       2017-05-07  -93 days
    ##  6 2012-01-02       2       2012-01-01   -1 days
    ##  7 2012-01-03       3       2012-01-02   -1 days
    ##  8 2012-01-04       4       2012-01-03   -1 days
    ##  9 2012-01-05       5       2012-01-04   -1 days
    ## 10 2012-01-06       6       2012-01-05   -1 days
    ## 11 2012-01-07       7       2012-01-06   -1 days
    ## 12 2012-01-08       8       2012-01-07   -1 days
    ## 13 2012-01-09       9       2012-01-08   -1 days
    ## 14 2012-01-10      10       2012-01-09   -1 days
    ## 15 2012-01-11      11       2012-01-10   -1 days
    ## 16 2012-01-12      12       2012-01-11   -1 days
    ## 17 2012-01-13      13       2012-01-12   -1 days
    ## 18 2012-01-14      14       2012-01-13   -1 days
    ## 19 2012-01-15      15       2012-01-14   -1 days
    ## 20 2012-01-16      16       2012-01-15   -1 days

This proves not to be the case. By some error, a few of the dates appear
to be in the future. I managed to correct these by inspection.

    DamLevelsDate[1966,1]<-ymd("2017-05-19")
    DamLevelsDate[1967,1]<-ymd("2017-05-20")
    DamLevelsDate[1968,1]<-ymd("2017-05-21")
    DamLevelsDate[1969,1]<-ymd("2017-05-22")
    DamLevelsDate[1955,1]<-ymd("2017-05-08")

    DamLevelsDate %>% 
      mutate(initnum=1:nrow(DamLevelsDate)) %>%   
      mutate(DamLevelsDateLag=lag(DamLevelsDate$Date)) %>%   
      mutate(Diff=DamLevelsDateLag-Date) %>%  
      arrange(Diff)  %>% 
      head(20)

    ## # A tibble: 20 x 4
    ##          Date initnum DamLevelsDateLag    Diff
    ##        <date>   <int>           <date>  <time>
    ##  1 2012-01-02       2       2012-01-01 -1 days
    ##  2 2012-01-03       3       2012-01-02 -1 days
    ##  3 2012-01-04       4       2012-01-03 -1 days
    ##  4 2012-01-05       5       2012-01-04 -1 days
    ##  5 2012-01-06       6       2012-01-05 -1 days
    ##  6 2012-01-07       7       2012-01-06 -1 days
    ##  7 2012-01-08       8       2012-01-07 -1 days
    ##  8 2012-01-09       9       2012-01-08 -1 days
    ##  9 2012-01-10      10       2012-01-09 -1 days
    ## 10 2012-01-11      11       2012-01-10 -1 days
    ## 11 2012-01-12      12       2012-01-11 -1 days
    ## 12 2012-01-13      13       2012-01-12 -1 days
    ## 13 2012-01-14      14       2012-01-13 -1 days
    ## 14 2012-01-15      15       2012-01-14 -1 days
    ## 15 2012-01-16      16       2012-01-15 -1 days
    ## 16 2012-01-17      17       2012-01-16 -1 days
    ## 17 2012-01-18      18       2012-01-17 -1 days
    ## 18 2012-01-19      19       2012-01-18 -1 days
    ## 19 2012-01-20      20       2012-01-19 -1 days
    ## 20 2012-01-21      21       2012-01-20 -1 days

Extracting Dam Names
--------------------

The names of the various Dams are given above the various columns and
can be extracted in sequence. They are also changed to title case by
means of the stringr package.

    library(stringr)
    seq<-seq(2,50,4)
    Dams<-DamLevels[2,seq]
    Dams<-as.character(Dams)
    Dams<-str_to_title(Dams)
    Dams

    ##  [1] "Wemmershoek"     "Steenbras Lower" "Steenbras Upper"
    ##  [4] "Vo<cb>Lvlei"     "Hely-Hutchinson" "Woodhead"       
    ##  [7] "Victoria"        "Alexandra"       "De Villiers"    
    ## [10] "Kleinplaats"     "Lewis Gay"       "Theewaterskloof"
    ## [13] "Berg River"

Extracting the Storage Data
---------------------------

Each column represents a dam. The columns are evenly spaced and so can
be extracted using a seq. The Dam names (above) are used as the new
column names.

    seq<-seq(3,51,4)
    StorageWide<-DamLevels[5:nrow(DamLevels),seq]
    colnames(StorageWide)<-Dams
    StorageWide %>% 
      head(20)

    ## # A tibble: 20 x 13
    ##    Wemmershoek `Steenbras Lower` `Steenbras Upper` `Vo\xcbLvlei`
    ##          <chr>             <chr>             <chr>         <chr>
    ##  1      44 621            23 549            29 620       124 100
    ##  2      44 571            23 460            29 620       123 812
    ##  3      44 471            23 372            29 570       123 237
    ##  4      44 372            23 313            29 620       122 520
    ##  5      44 322            23 224            29 317       121 947
    ##  6      44 221            23 136            29 545       121 374
    ##  7      44 074            23 047            29 495       121 232
    ##  8      43 973            23 047            29 242       121 232
    ##  9      43 826            22 988            29 646       120 233
    ## 10      43 752            22 900            29 595       119 805
    ## 11      43 654            22 870            29 595       117 960
    ## 12      43 605            22 812            30 003       119 094
    ## 13      43 483            22 725            29 773       118 527
    ## 14      43 409            22 667            30 182       117 818
    ## 15      43 336            22 552            30 156       117 818
    ## 16      43 336            22 465            30 156       117 111
    ## 17      43 140            22 407            29 545       115 700
    ## 18      43 042            22 320            29 292       114 997
    ## 19      42 969            22 175            29 141       114 576
    ## 20      42 872            22 089            29 066       114 016
    ## # ... with 9 more variables: `Hely-Hutchinson` <chr>, Woodhead <chr>,
    ## #   Victoria <chr>, Alexandra <chr>, `De Villiers` <chr>,
    ## #   Kleinplaats <chr>, `Lewis Gay` <chr>, Theewaterskloof <chr>, `Berg
    ## #   River` <chr>

Combine the Data
----------------

To combine the data, I bind the Date column to the storage columns.

    StorageWide<-cbind(DamLevelsDate,StorageWide)
    StorageWide %>% 
      head(20)

    ##          Date Wemmershoek Steenbras Lower Steenbras Upper Vo<cb>Lvlei
    ## 1  2012-01-01      44 621          23 549          29 620     124 100
    ## 2  2012-01-02      44 571          23 460          29 620     123 812
    ## 3  2012-01-03      44 471          23 372          29 570     123 237
    ## 4  2012-01-04      44 372          23 313          29 620     122 520
    ## 5  2012-01-05      44 322          23 224          29 317     121 947
    ## 6  2012-01-06      44 221          23 136          29 545     121 374
    ## 7  2012-01-07      44 074          23 047          29 495     121 232
    ## 8  2012-01-08      43 973          23 047          29 242     121 232
    ## 9  2012-01-09      43 826          22 988          29 646     120 233
    ## 10 2012-01-10      43 752          22 900          29 595     119 805
    ## 11 2012-01-11      43 654          22 870          29 595     117 960
    ## 12 2012-01-12      43 605          22 812          30 003     119 094
    ## 13 2012-01-13      43 483          22 725          29 773     118 527
    ## 14 2012-01-14      43 409          22 667          30 182     117 818
    ## 15 2012-01-15      43 336          22 552          30 156     117 818
    ## 16 2012-01-16      43 336          22 465          30 156     117 111
    ## 17 2012-01-17      43 140          22 407          29 545     115 700
    ## 18 2012-01-18      43 042          22 320          29 292     114 997
    ## 19 2012-01-19      42 969          22 175          29 141     114 576
    ## 20 2012-01-20      42 872          22 089          29 066     114 016
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

    write.csv(file = "/Users/jameslairdsmith/Google Drive/Applications/Github/WC_Dam_Levels/Clean_WC_Dam_Levels.csv",StorageLong)
