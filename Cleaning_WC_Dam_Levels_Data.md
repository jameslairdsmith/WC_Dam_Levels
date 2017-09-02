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
    library(knitr)

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
      head(20) %>% 
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
<th align="left">X10</th>
<th align="left">X11</th>
<th align="left">X12</th>
<th align="left">X13</th>
<th align="left">X14</th>
<th align="left">X15</th>
<th align="left">X16</th>
<th align="left">X17</th>
<th align="left">X18</th>
<th align="left">X19</th>
<th align="left">X20</th>
<th align="left">X21</th>
<th align="left">X22</th>
<th align="left">X23</th>
<th align="left">X24</th>
<th align="left">X25</th>
<th align="left">X26</th>
<th align="left">X27</th>
<th align="left">X28</th>
<th align="left">X29</th>
<th align="left">X30</th>
<th align="left">X31</th>
<th align="left">X32</th>
<th align="left">X33</th>
<th align="left">X34</th>
<th align="left">X35</th>
<th align="left">X36</th>
<th align="left">X37</th>
<th align="left">X38</th>
<th align="left">X39</th>
<th align="left">X40</th>
<th align="left">X41</th>
<th align="left">X42</th>
<th align="left">X43</th>
<th align="left">X44</th>
<th align="left">X45</th>
<th align="left">X46</th>
<th align="left">X47</th>
<th align="left">X48</th>
<th align="left">X49</th>
<th align="left">X50</th>
<th align="left">X51</th>
<th align="left">X52</th>
<th align="left">X53</th>
<th align="left">X54</th>
<th align="left">X55</th>
<th align="left">X56</th>
<th align="left">X57</th>
<th align="left">X58</th>
<th align="left">X59</th>
<th align="left">X60</th>
<th align="left">X61</th>
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
<td align="left">31 767</td>
<td align="left">318</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">164 095</td>
<td align="left">1 641</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">925</td>
<td align="left">9</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">955</td>
<td align="left">10</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">128</td>
<td align="left">1</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">134</td>
<td align="left">1</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">242</td>
<td align="left">2</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">1 301</td>
<td align="left">13</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">168</td>
<td align="left">2</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">480 188</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">130 010</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">898 221</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">451</td>
<td align="left">NA</td>
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
<td align="left">STEENBRAS UPPER</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">VO<cb>LVLEI</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">HELY-HUTCHINSON</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">WOODHEAD</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">VICTORIA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">ALEXANDRA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">DE VILLIERS</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">KLEINPLAATS</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">LEWIS GAY</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">THEEWATERSKLOOF</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">BERG RIVER</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">TOTAL STORED - BIG 6</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">LAND-en ZEEZICHT</td>
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
<td align="left">HEIGHT</td>
<td align="left">STORAGE</td>
<td align="left">Current</td>
<td align="left">Last Year</td>
<td align="left">HEIGHT</td>
<td align="left">STORAGE</td>
<td align="left">Current</td>
<td align="left">Last Year</td>
<td align="left">HEIGHT</td>
<td align="left">STORAGE</td>
<td align="left">Current</td>
<td align="left">Last Year</td>
<td align="left">HEIGHT</td>
<td align="left">STORAGE</td>
<td align="left">Current</td>
<td align="left">Last Year</td>
<td align="left">HEIGHT</td>
<td align="left">STORAGE</td>
<td align="left">Current</td>
<td align="left">Last Year</td>
<td align="left">HEIGHT</td>
<td align="left">STORAGE</td>
<td align="left">Current</td>
<td align="left">Last Year</td>
<td align="left">HEIGHT</td>
<td align="left">STORAGE</td>
<td align="left">Current</td>
<td align="left">Last Year</td>
<td align="left">HEIGHT</td>
<td align="left">STORAGE</td>
<td align="left">Current</td>
<td align="left">Last Year</td>
<td align="left">HEIGHT</td>
<td align="left">STORAGE</td>
<td align="left">Current</td>
<td align="left">Last Year</td>
<td align="left">HEIGHT</td>
<td align="left">STORAGE</td>
<td align="left">Current</td>
<td align="left">Last Year</td>
<td align="left">HEIGHT</td>
<td align="left">STORAGE</td>
<td align="left">Current</td>
<td align="left">Last Year</td>
<td align="left">STORAGE</td>
<td align="left">Current</td>
<td align="left">Last Year</td>
<td align="left">NA</td>
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
<td align="left">(m)</td>
<td align="left">(Ml)</td>
<td align="left">%</td>
<td align="left">%</td>
<td align="left">(m)</td>
<td align="left">(Ml)</td>
<td align="left">%</td>
<td align="left">%</td>
<td align="left">(m)</td>
<td align="left">(Ml)</td>
<td align="left">%</td>
<td align="left">%</td>
<td align="left">(m)</td>
<td align="left">(Ml)</td>
<td align="left">%</td>
<td align="left">%</td>
<td align="left">(m)</td>
<td align="left">(Ml)</td>
<td align="left">%</td>
<td align="left">%</td>
<td align="left">(m)</td>
<td align="left">(Ml)</td>
<td align="left">%</td>
<td align="left">%</td>
<td align="left">(m)</td>
<td align="left">(Ml)</td>
<td align="left">%</td>
<td align="left">%</td>
<td align="left">(m)</td>
<td align="left">(Ml)</td>
<td align="left">%</td>
<td align="left">%</td>
<td align="left">(m)</td>
<td align="left">(Ml)</td>
<td align="left">%</td>
<td align="left">%</td>
<td align="left">(m)</td>
<td align="left">(Ml)</td>
<td align="left">%</td>
<td align="left">%</td>
<td align="left">(m)</td>
<td align="left">(Ml)</td>
<td align="left">%</td>
<td align="left">%</td>
<td align="left">(Ml)</td>
<td align="left">%</td>
<td align="left">%</td>
<td align="left">NA</td>
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
<td align="left">24.17</td>
<td align="left">29 620</td>
<td align="left">93.2</td>
<td align="left">NA</td>
<td align="left">14.99</td>
<td align="left">124 100</td>
<td align="left">75.6</td>
<td align="left">NA</td>
<td align="left">14.17</td>
<td align="left">763</td>
<td align="left">82.5</td>
<td align="left">NA</td>
<td align="left">35.3</td>
<td align="left">742.8</td>
<td align="left">77.8</td>
<td align="left">NA</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">NA</td>
<td align="left">10.64</td>
<td align="left">99.9</td>
<td align="left">74.4</td>
<td align="left">NA</td>
<td align="left">26.28</td>
<td align="left">196.5</td>
<td align="left">81</td>
<td align="left">NA</td>
<td align="left">6.15</td>
<td align="left">336.6</td>
<td align="left">25.9</td>
<td align="left">NA</td>
<td align="left">13.9</td>
<td align="left">128.3</td>
<td align="left">76.4</td>
<td align="left">NA</td>
<td align="left">24.83</td>
<td align="left">357 963</td>
<td align="left">74.5</td>
<td align="left">NA</td>
<td align="left">39.33</td>
<td align="left">115 930</td>
<td align="left">89.2</td>
<td align="left">NA</td>
<td align="left">695 783</td>
<td align="left">77.46</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
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
<td align="left">24.17</td>
<td align="left">29 620</td>
<td align="left">93.2</td>
<td align="left">NA</td>
<td align="left">14.97</td>
<td align="left">123 812</td>
<td align="left">75.5</td>
<td align="left">NA</td>
<td align="left">14.17</td>
<td align="left">763</td>
<td align="left">82.5</td>
<td align="left">NA</td>
<td align="left">35.3</td>
<td align="left">742.8</td>
<td align="left">77.8</td>
<td align="left">NA</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">NA</td>
<td align="left">10.61</td>
<td align="left">99.2</td>
<td align="left">73.9</td>
<td align="left">NA</td>
<td align="left">26.28</td>
<td align="left">196.5</td>
<td align="left">81</td>
<td align="left">NA</td>
<td align="left">6.15</td>
<td align="left">336.6</td>
<td align="left">25.9</td>
<td align="left">NA</td>
<td align="left">13.9</td>
<td align="left">128.3</td>
<td align="left">76.4</td>
<td align="left">NA</td>
<td align="left">24.8</td>
<td align="left">356 677</td>
<td align="left">74.3</td>
<td align="left">NA</td>
<td align="left">39.12</td>
<td align="left">114 850</td>
<td align="left">88.3</td>
<td align="left">NA</td>
<td align="left">692 990</td>
<td align="left">77.15</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
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
<td align="left">24.15</td>
<td align="left">29 570</td>
<td align="left">93.1</td>
<td align="left">NA</td>
<td align="left">14.93</td>
<td align="left">123 237</td>
<td align="left">75.1</td>
<td align="left">NA</td>
<td align="left">14.24</td>
<td align="left">773</td>
<td align="left">83.6</td>
<td align="left">NA</td>
<td align="left">35.33</td>
<td align="left">745.4</td>
<td align="left">78.1</td>
<td align="left">NA</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">NA</td>
<td align="left">10.59</td>
<td align="left">98.7</td>
<td align="left">73.5</td>
<td align="left">NA</td>
<td align="left">26.31</td>
<td align="left">197.3</td>
<td align="left">81.4</td>
<td align="left">NA</td>
<td align="left">6.15</td>
<td align="left">336.6</td>
<td align="left">25.9</td>
<td align="left">NA</td>
<td align="left">13.9</td>
<td align="left">128.3</td>
<td align="left">76.4</td>
<td align="left">NA</td>
<td align="left">24.77</td>
<td align="left">355 394</td>
<td align="left">74</td>
<td align="left">NA</td>
<td align="left">39.01</td>
<td align="left">114 280</td>
<td align="left">87.9</td>
<td align="left">NA</td>
<td align="left">690 324</td>
<td align="left">76.85</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
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
<td align="left">24.17</td>
<td align="left">29 620</td>
<td align="left">93.2</td>
<td align="left">NA</td>
<td align="left">14.88</td>
<td align="left">122 520</td>
<td align="left">74.7</td>
<td align="left">NA</td>
<td align="left">14.38</td>
<td align="left">794</td>
<td align="left">85.8</td>
<td align="left">NA</td>
<td align="left">35.38</td>
<td align="left">749.6</td>
<td align="left">78.5</td>
<td align="left">NA</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">NA</td>
<td align="left">10.61</td>
<td align="left">99.2</td>
<td align="left">73.9</td>
<td align="left">NA</td>
<td align="left">26.33</td>
<td align="left">197.8</td>
<td align="left">81.6</td>
<td align="left">NA</td>
<td align="left">6.13</td>
<td align="left">334.2</td>
<td align="left">25.7</td>
<td align="left">NA</td>
<td align="left">13.9</td>
<td align="left">128.3</td>
<td align="left">76.4</td>
<td align="left">NA</td>
<td align="left">24.73</td>
<td align="left">353 687</td>
<td align="left">73.7</td>
<td align="left">NA</td>
<td align="left">38.91</td>
<td align="left">113 770</td>
<td align="left">87.5</td>
<td align="left">NA</td>
<td align="left">687 282</td>
<td align="left">76.52</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
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
<td align="left">24.05</td>
<td align="left">29 317</td>
<td align="left">92.3</td>
<td align="left">NA</td>
<td align="left">14.84</td>
<td align="left">121 947</td>
<td align="left">74.3</td>
<td align="left">NA</td>
<td align="left">14.4</td>
<td align="left">797</td>
<td align="left">86.1</td>
<td align="left">NA</td>
<td align="left">35.38</td>
<td align="left">749.6</td>
<td align="left">78.5</td>
<td align="left">NA</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">NA</td>
<td align="left">10.6</td>
<td align="left">98.9</td>
<td align="left">73.7</td>
<td align="left">NA</td>
<td align="left">26.34</td>
<td align="left">198</td>
<td align="left">81.7</td>
<td align="left">NA</td>
<td align="left">6.1</td>
<td align="left">330.6</td>
<td align="left">25.4</td>
<td align="left">NA</td>
<td align="left">13.9</td>
<td align="left">128.3</td>
<td align="left">76.4</td>
<td align="left">NA</td>
<td align="left">24.67</td>
<td align="left">351 135</td>
<td align="left">73.1</td>
<td align="left">NA</td>
<td align="left">38.84</td>
<td align="left">113 410</td>
<td align="left">87.2</td>
<td align="left">NA</td>
<td align="left">683 355</td>
<td align="left">76.08</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
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
<td align="left">24.14</td>
<td align="left">29 545</td>
<td align="left">93</td>
<td align="left">NA</td>
<td align="left">14.8</td>
<td align="left">121 374</td>
<td align="left">74</td>
<td align="left">NA</td>
<td align="left">14.41</td>
<td align="left">798</td>
<td align="left">86.3</td>
<td align="left">NA</td>
<td align="left">35.24</td>
<td align="left">737.7</td>
<td align="left">77.3</td>
<td align="left">NA</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">NA</td>
<td align="left">10.58</td>
<td align="left">98.5</td>
<td align="left">73.3</td>
<td align="left">NA</td>
<td align="left">26.36</td>
<td align="left">198.5</td>
<td align="left">81.9</td>
<td align="left">NA</td>
<td align="left">6.1</td>
<td align="left">330.6</td>
<td align="left">25.4</td>
<td align="left">NA</td>
<td align="left">13.9</td>
<td align="left">128.3</td>
<td align="left">76.4</td>
<td align="left">NA</td>
<td align="left">24.64</td>
<td align="left">349 863</td>
<td align="left">72.9</td>
<td align="left">NA</td>
<td align="left">38.78</td>
<td align="left">113 100</td>
<td align="left">87</td>
<td align="left">NA</td>
<td align="left">681 239</td>
<td align="left">75.84</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
</tr>
<tr class="odd">
<td align="left">07-Jan-12</td>
<td align="left">48.01</td>
<td align="left">44 074</td>
<td align="left">75.2</td>
<td align="left">NA</td>
<td align="left">20.17</td>
<td align="left">23 047</td>
<td align="left">68.8</td>
<td align="left">NA</td>
<td align="left">24.12</td>
<td align="left">29 495</td>
<td align="left">92.8</td>
<td align="left">NA</td>
<td align="left">14.79</td>
<td align="left">121 232</td>
<td align="left">73.9</td>
<td align="left">NA</td>
<td align="left">14.43</td>
<td align="left">801</td>
<td align="left">86.6</td>
<td align="left">NA</td>
<td align="left">35.12</td>
<td align="left">727.7</td>
<td align="left">76.2</td>
<td align="left">NA</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">NA</td>
<td align="left">10.55</td>
<td align="left">97.7</td>
<td align="left">72.8</td>
<td align="left">NA</td>
<td align="left">26.36</td>
<td align="left">198.5</td>
<td align="left">81.9</td>
<td align="left">NA</td>
<td align="left">6.1</td>
<td align="left">330.6</td>
<td align="left">25.4</td>
<td align="left">NA</td>
<td align="left">13.9</td>
<td align="left">128.3</td>
<td align="left">76.4</td>
<td align="left">NA</td>
<td align="left">24.61</td>
<td align="left">348 594</td>
<td align="left">72.6</td>
<td align="left">NA</td>
<td align="left">38.78</td>
<td align="left">113 100</td>
<td align="left">87</td>
<td align="left">NA</td>
<td align="left">679 542</td>
<td align="left">75.65</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
</tr>
<tr class="even">
<td align="left">08-Jan-12</td>
<td align="left">47.97</td>
<td align="left">43 973</td>
<td align="left">75</td>
<td align="left">NA</td>
<td align="left">20.17</td>
<td align="left">23 047</td>
<td align="left">68.8</td>
<td align="left">NA</td>
<td align="left">24.02</td>
<td align="left">29 242</td>
<td align="left">92.1</td>
<td align="left">NA</td>
<td align="left">14.79</td>
<td align="left">121 232</td>
<td align="left">73.9</td>
<td align="left">NA</td>
<td align="left">14.43</td>
<td align="left">801</td>
<td align="left">86.6</td>
<td align="left">NA</td>
<td align="left">34.99</td>
<td align="left">717.2</td>
<td align="left">75.1</td>
<td align="left">NA</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">NA</td>
<td align="left">10.53</td>
<td align="left">97.3</td>
<td align="left">72.5</td>
<td align="left">NA</td>
<td align="left">26.35</td>
<td align="left">198.3</td>
<td align="left">81.8</td>
<td align="left">NA</td>
<td align="left">6.1</td>
<td align="left">330.6</td>
<td align="left">25.4</td>
<td align="left">NA</td>
<td align="left">13.9</td>
<td align="left">128.3</td>
<td align="left">76.4</td>
<td align="left">NA</td>
<td align="left">24.58</td>
<td align="left">347 327</td>
<td align="left">72.3</td>
<td align="left">NA</td>
<td align="left">38.78</td>
<td align="left">113 100</td>
<td align="left">87</td>
<td align="left">NA</td>
<td align="left">677 921</td>
<td align="left">75.47</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
</tr>
<tr class="odd">
<td align="left">09-Jan-12</td>
<td align="left">47.91</td>
<td align="left">43 826</td>
<td align="left">74.7</td>
<td align="left">NA</td>
<td align="left">20.15</td>
<td align="left">22 988</td>
<td align="left">68.6</td>
<td align="left">NA</td>
<td align="left">24.18</td>
<td align="left">29 646</td>
<td align="left">93.3</td>
<td align="left">NA</td>
<td align="left">14.72</td>
<td align="left">120 233</td>
<td align="left">73.3</td>
<td align="left">NA</td>
<td align="left">14.43</td>
<td align="left">801</td>
<td align="left">86.6</td>
<td align="left">NA</td>
<td align="left">34.82</td>
<td align="left">703.5</td>
<td align="left">73.7</td>
<td align="left">NA</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">NA</td>
<td align="left">10.51</td>
<td align="left">96.8</td>
<td align="left">72.1</td>
<td align="left">NA</td>
<td align="left">26.33</td>
<td align="left">197.8</td>
<td align="left">81.6</td>
<td align="left">NA</td>
<td align="left">6.08</td>
<td align="left">328.3</td>
<td align="left">25.2</td>
<td align="left">NA</td>
<td align="left">13.86</td>
<td align="left">127.2</td>
<td align="left">75.7</td>
<td align="left">NA</td>
<td align="left">24.54</td>
<td align="left">345 643</td>
<td align="left">72</td>
<td align="left">NA</td>
<td align="left">38.78</td>
<td align="left">113 100</td>
<td align="left">87</td>
<td align="left">NA</td>
<td align="left">675 436</td>
<td align="left">75.2</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
</tr>
<tr class="even">
<td align="left">10-Jan-12</td>
<td align="left">47.88</td>
<td align="left">43 752</td>
<td align="left">74.6</td>
<td align="left">NA</td>
<td align="left">20.12</td>
<td align="left">22 900</td>
<td align="left">68.3</td>
<td align="left">NA</td>
<td align="left">24.16</td>
<td align="left">29 595</td>
<td align="left">93.2</td>
<td align="left">NA</td>
<td align="left">14.69</td>
<td align="left">119 805</td>
<td align="left">73</td>
<td align="left">NA</td>
<td align="left">14.44</td>
<td align="left">802</td>
<td align="left">86.8</td>
<td align="left">NA</td>
<td align="left">34.67</td>
<td align="left">691.5</td>
<td align="left">72.4</td>
<td align="left">NA</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">NA</td>
<td align="left">10.47</td>
<td align="left">95.8</td>
<td align="left">71.4</td>
<td align="left">NA</td>
<td align="left">26.35</td>
<td align="left">198.3</td>
<td align="left">81.8</td>
<td align="left">NA</td>
<td align="left">6.06</td>
<td align="left">325.9</td>
<td align="left">25.1</td>
<td align="left">NA</td>
<td align="left">13.86</td>
<td align="left">127.2</td>
<td align="left">75.7</td>
<td align="left">NA</td>
<td align="left">24.5</td>
<td align="left">343 963</td>
<td align="left">71.6</td>
<td align="left">NA</td>
<td align="left">38.52</td>
<td align="left">111 780</td>
<td align="left">86</td>
<td align="left">NA</td>
<td align="left">671 795</td>
<td align="left">74.79</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
</tr>
<tr class="odd">
<td align="left">11-Jan-12</td>
<td align="left">47.84</td>
<td align="left">43 654</td>
<td align="left">74.4</td>
<td align="left">NA</td>
<td align="left">20.11</td>
<td align="left">22 870</td>
<td align="left">68.2</td>
<td align="left">NA</td>
<td align="left">24.16</td>
<td align="left">29 595</td>
<td align="left">93.2</td>
<td align="left">NA</td>
<td align="left">14.56</td>
<td align="left">117 960</td>
<td align="left">71.9</td>
<td align="left">NA</td>
<td align="left">14.45</td>
<td align="left">804</td>
<td align="left">86.9</td>
<td align="left">NA</td>
<td align="left">34.49</td>
<td align="left">677.7</td>
<td align="left">71</td>
<td align="left">NA</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">NA</td>
<td align="left">10.45</td>
<td align="left">95.4</td>
<td align="left">71</td>
<td align="left">NA</td>
<td align="left">26.36</td>
<td align="left">198.5</td>
<td align="left">81.9</td>
<td align="left">NA</td>
<td align="left">6.06</td>
<td align="left">325.9</td>
<td align="left">25.1</td>
<td align="left">NA</td>
<td align="left">13.86</td>
<td align="left">127.2</td>
<td align="left">75.7</td>
<td align="left">NA</td>
<td align="left">24.47</td>
<td align="left">342 706</td>
<td align="left">71.4</td>
<td align="left">NA</td>
<td align="left">38.44</td>
<td align="left">111 370</td>
<td align="left">85.7</td>
<td align="left">NA</td>
<td align="left">668 155</td>
<td align="left">74.39</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
</tr>
<tr class="even">
<td align="left">12-Jan-12</td>
<td align="left">47.82</td>
<td align="left">43 605</td>
<td align="left">74.4</td>
<td align="left">NA</td>
<td align="left">20.09</td>
<td align="left">22 812</td>
<td align="left">68.1</td>
<td align="left">NA</td>
<td align="left">24.32</td>
<td align="left">30 003</td>
<td align="left">94.4</td>
<td align="left">NA</td>
<td align="left">14.64</td>
<td align="left">119 094</td>
<td align="left">72.6</td>
<td align="left">NA</td>
<td align="left">14.45</td>
<td align="left">804</td>
<td align="left">86.9</td>
<td align="left">NA</td>
<td align="left">34.35</td>
<td align="left">666.7</td>
<td align="left">69.8</td>
<td align="left">NA</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">NA</td>
<td align="left">10.44</td>
<td align="left">95.1</td>
<td align="left">70.9</td>
<td align="left">NA</td>
<td align="left">26.36</td>
<td align="left">198.5</td>
<td align="left">81.9</td>
<td align="left">NA</td>
<td align="left">6.04</td>
<td align="left">323.6</td>
<td align="left">24.9</td>
<td align="left">NA</td>
<td align="left">13.78</td>
<td align="left">125</td>
<td align="left">74.4</td>
<td align="left">NA</td>
<td align="left">24.44</td>
<td align="left">341 452</td>
<td align="left">71.1</td>
<td align="left">NA</td>
<td align="left">37.44</td>
<td align="left">111 370</td>
<td align="left">85.7</td>
<td align="left">NA</td>
<td align="left">668 336</td>
<td align="left">74.41</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
</tr>
<tr class="odd">
<td align="left">13-Jan-12</td>
<td align="left">47.77</td>
<td align="left">43 483</td>
<td align="left">74.1</td>
<td align="left">NA</td>
<td align="left">20.06</td>
<td align="left">22 725</td>
<td align="left">67.8</td>
<td align="left">NA</td>
<td align="left">24.23</td>
<td align="left">29 773</td>
<td align="left">93.7</td>
<td align="left">NA</td>
<td align="left">14.6</td>
<td align="left">118 527</td>
<td align="left">72.2</td>
<td align="left">NA</td>
<td align="left">14.45</td>
<td align="left">804</td>
<td align="left">86.9</td>
<td align="left">NA</td>
<td align="left">34.18</td>
<td align="left">653.8</td>
<td align="left">68.5</td>
<td align="left">NA</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">NA</td>
<td align="left">10.41</td>
<td align="left">94.4</td>
<td align="left">70.3</td>
<td align="left">NA</td>
<td align="left">26.35</td>
<td align="left">198.3</td>
<td align="left">81.8</td>
<td align="left">NA</td>
<td align="left">6.02</td>
<td align="left">321.2</td>
<td align="left">24.7</td>
<td align="left">NA</td>
<td align="left">13.78</td>
<td align="left">125</td>
<td align="left">74.4</td>
<td align="left">NA</td>
<td align="left">24.42</td>
<td align="left">340 617</td>
<td align="left">70.9</td>
<td align="left">NA</td>
<td align="left">38.28</td>
<td align="left">110 570</td>
<td align="left">85</td>
<td align="left">NA</td>
<td align="left">665 695</td>
<td align="left">74.11</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
</tr>
<tr class="even">
<td align="left">14-Jan-12</td>
<td align="left">47.74</td>
<td align="left">43 409</td>
<td align="left">74</td>
<td align="left">NA</td>
<td align="left">20.04</td>
<td align="left">22 667</td>
<td align="left">67.6</td>
<td align="left">NA</td>
<td align="left">24.39</td>
<td align="left">30 182</td>
<td align="left">95</td>
<td align="left">NA</td>
<td align="left">14.55</td>
<td align="left">117 818</td>
<td align="left">71.8</td>
<td align="left">NA</td>
<td align="left">14.44</td>
<td align="left">802</td>
<td align="left">86.8</td>
<td align="left">NA</td>
<td align="left">34.03</td>
<td align="left">642.4</td>
<td align="left">67.3</td>
<td align="left">NA</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">NA</td>
<td align="left">10.39</td>
<td align="left">93.9</td>
<td align="left">70</td>
<td align="left">NA</td>
<td align="left">26.34</td>
<td align="left">198</td>
<td align="left">81.7</td>
<td align="left">NA</td>
<td align="left">6.01</td>
<td align="left">320.1</td>
<td align="left">24.6</td>
<td align="left">NA</td>
<td align="left">13.74</td>
<td align="left">123.9</td>
<td align="left">73.8</td>
<td align="left">NA</td>
<td align="left">24.38</td>
<td align="left">338 951</td>
<td align="left">70.6</td>
<td align="left">NA</td>
<td align="left">38.28</td>
<td align="left">110 570</td>
<td align="left">85</td>
<td align="left">NA</td>
<td align="left">663 597</td>
<td align="left">73.88</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
</tr>
<tr class="odd">
<td align="left">15-Jan-12</td>
<td align="left">47.71</td>
<td align="left">43 336</td>
<td align="left">73.9</td>
<td align="left">NA</td>
<td align="left">20</td>
<td align="left">22 552</td>
<td align="left">67.3</td>
<td align="left">NA</td>
<td align="left">24.38</td>
<td align="left">30 156</td>
<td align="left">94.9</td>
<td align="left">NA</td>
<td align="left">14.55</td>
<td align="left">117 818</td>
<td align="left">71.8</td>
<td align="left">NA</td>
<td align="left">14.48</td>
<td align="left">808</td>
<td align="left">87.4</td>
<td align="left">NA</td>
<td align="left">33.89</td>
<td align="left">631.7</td>
<td align="left">66.2</td>
<td align="left">NA</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">NA</td>
<td align="left">10.36</td>
<td align="left">93.2</td>
<td align="left">69.4</td>
<td align="left">NA</td>
<td align="left">26.37</td>
<td align="left">198.8</td>
<td align="left">82</td>
<td align="left">NA</td>
<td align="left">5.98</td>
<td align="left">316.6</td>
<td align="left">24.3</td>
<td align="left">NA</td>
<td align="left">13.5</td>
<td align="left">117.6</td>
<td align="left">70</td>
<td align="left">NA</td>
<td align="left">24.35</td>
<td align="left">337 705</td>
<td align="left">70.3</td>
<td align="left">NA</td>
<td align="left">38.28</td>
<td align="left">110 570</td>
<td align="left">85</td>
<td align="left">NA</td>
<td align="left">662 137</td>
<td align="left">73.72</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
</tr>
<tr class="even">
<td align="left">16-Jan-12</td>
<td align="left">47.71</td>
<td align="left">43 336</td>
<td align="left">73.9</td>
<td align="left">NA</td>
<td align="left">19.97</td>
<td align="left">22 465</td>
<td align="left">67</td>
<td align="left">NA</td>
<td align="left">24.38</td>
<td align="left">30 156</td>
<td align="left">94.9</td>
<td align="left">NA</td>
<td align="left">14.5</td>
<td align="left">117 111</td>
<td align="left">71.4</td>
<td align="left">NA</td>
<td align="left">14.5</td>
<td align="left">811</td>
<td align="left">87.7</td>
<td align="left">NA</td>
<td align="left">33.74</td>
<td align="left">620.2</td>
<td align="left">64.9</td>
<td align="left">NA</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">NA</td>
<td align="left">10.34</td>
<td align="left">92.8</td>
<td align="left">69.1</td>
<td align="left">NA</td>
<td align="left">26.36</td>
<td align="left">198.5</td>
<td align="left">81.9</td>
<td align="left">NA</td>
<td align="left">5.98</td>
<td align="left">316.6</td>
<td align="left">24.3</td>
<td align="left">NA</td>
<td align="left">13.36</td>
<td align="left">114</td>
<td align="left">67.9</td>
<td align="left">NA</td>
<td align="left">24.32</td>
<td align="left">336 461</td>
<td align="left">70.1</td>
<td align="left">NA</td>
<td align="left">38.06</td>
<td align="left">109 460</td>
<td align="left">84.2</td>
<td align="left">NA</td>
<td align="left">658 989</td>
<td align="left">73.37</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
<td align="left">NA</td>
</tr>
</tbody>
</table>

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

    #write.csv(file = "/Users/jameslairdsmith/Google Drive/Applications/Github/WC_Dam_Levels/Clean_WC_Dam_Levels.csv",StorageLong)
