Mean Population Elevation in the Continental USA
================
Daniel Moul
2020-10-23

<br>

The continental United States has vast flat plains and long mountain
ranges. But what do people experience? They don’t live at the the
extreme highest and lowest elevations. What do people experience? One
way to answer this question is find the average elevation of the
population of the USA. We can approximate the answer by doing the
following:

1.  Calculate the mean elevation of each county
2.  Get the population of each county
3.  Calculate a weighted mean elevation for the country based on the
    above

<br>

## 1\. Get mean elevation of each county

We can approximate the mean elevation of each county using the
‘populated places’ data set from the USGS [Populated
Places](https://geonames.usgs.gov/docs/stategaz/POP_PLACES.zip) topical
gazetteer from GNIS. Most counties have more than 10 populated places,
and we can average them to get an approximation for the mean elevation
of the county.

<table class="table table-striped table-condensed table-responsive" style="width: auto !important; margin-left: auto; margin-right: auto;">

<caption>

Example data from USGS ‘Populated Places’ data set with calculated mean
elevation per county

</caption>

<thead>

<tr>

<th style="text-align:left;">

state\_alpha

</th>

<th style="text-align:left;">

state\_numeric

</th>

<th style="text-align:left;">

county\_name

</th>

<th style="text-align:left;">

county\_numeric

</th>

<th style="text-align:right;">

n\_poplulated\_places

</th>

<th style="text-align:right;">

mean\_elev\_in\_m

</th>

<th style="text-align:right;">

mean\_elev\_in\_ft

</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

AL

</td>

<td style="text-align:left;">

01

</td>

<td style="text-align:left;">

Limestone

</td>

<td style="text-align:left;">

083

</td>

<td style="text-align:right;">

132

</td>

<td style="text-align:right;">

214

</td>

<td style="text-align:right;">

703

</td>

</tr>

<tr>

<td style="text-align:left;">

CO

</td>

<td style="text-align:left;">

08

</td>

<td style="text-align:left;">

Logan

</td>

<td style="text-align:left;">

075

</td>

<td style="text-align:right;">

27

</td>

<td style="text-align:right;">

1233

</td>

<td style="text-align:right;">

4044

</td>

</tr>

<tr>

<td style="text-align:left;">

IN

</td>

<td style="text-align:left;">

18

</td>

<td style="text-align:left;">

Gibson

</td>

<td style="text-align:left;">

051

</td>

<td style="text-align:right;">

36

</td>

<td style="text-align:right;">

137

</td>

<td style="text-align:right;">

448

</td>

</tr>

<tr>

<td style="text-align:left;">

KY

</td>

<td style="text-align:left;">

21

</td>

<td style="text-align:left;">

Adair

</td>

<td style="text-align:left;">

001

</td>

<td style="text-align:right;">

64

</td>

<td style="text-align:right;">

264

</td>

<td style="text-align:right;">

866

</td>

</tr>

<tr>

<td style="text-align:left;">

MS

</td>

<td style="text-align:left;">

28

</td>

<td style="text-align:left;">

Tate

</td>

<td style="text-align:left;">

137

</td>

<td style="text-align:right;">

30

</td>

<td style="text-align:right;">

98

</td>

<td style="text-align:right;">

320

</td>

</tr>

<tr>

<td style="text-align:left;">

ND

</td>

<td style="text-align:left;">

38

</td>

<td style="text-align:left;">

Rolette

</td>

<td style="text-align:left;">

079

</td>

<td style="text-align:right;">

14

</td>

<td style="text-align:right;">

546

</td>

<td style="text-align:right;">

1790

</td>

</tr>

<tr>

<td style="text-align:left;">

OH

</td>

<td style="text-align:left;">

39

</td>

<td style="text-align:left;">

Mercer

</td>

<td style="text-align:left;">

107

</td>

<td style="text-align:right;">

69

</td>

<td style="text-align:right;">

272

</td>

<td style="text-align:right;">

893

</td>

</tr>

<tr>

<td style="text-align:left;">

SD

</td>

<td style="text-align:left;">

46

</td>

<td style="text-align:left;">

Tripp

</td>

<td style="text-align:left;">

123

</td>

<td style="text-align:right;">

11

</td>

<td style="text-align:right;">

637

</td>

<td style="text-align:right;">

2091

</td>

</tr>

<tr>

<td style="text-align:left;">

TX

</td>

<td style="text-align:left;">

48

</td>

<td style="text-align:left;">

Borden

</td>

<td style="text-align:left;">

033

</td>

<td style="text-align:right;">

3

</td>

<td style="text-align:right;">

861

</td>

<td style="text-align:right;">

2826

</td>

</tr>

<tr>

<td style="text-align:left;">

TX

</td>

<td style="text-align:left;">

48

</td>

<td style="text-align:left;">

Moore

</td>

<td style="text-align:left;">

341

</td>

<td style="text-align:right;">

15

</td>

<td style="text-align:right;">

1102

</td>

<td style="text-align:right;">

3616

</td>

</tr>

</tbody>

</table>

<br>

<img src="mean-population-elevation_files/figure-gfm/unnamed-chunk-6-1.png" width="100%" />

<br>

## 2\. Get population by county

I downloaded county-level population estimates from ACS 2014-2018 via
the Census Bureau’s Planning Database at
<https://www.census.gov/topics/research/guidance/planning-databases.2020.html>

<br>

<img src="mean-population-elevation_files/figure-gfm/unnamed-chunk-10-1.png" width="100%" />

<br>

## 3\. The answer

The average elevation of the population of the USA is 856 ft, which is a
weighted mean based on county population. Compare that to the simple
average of county elevation: 1302 ft. It seems reasonable to me that
weighted mean is lower elevation than the simple mean, since there are
more people near the coasts in higher-density counties than in the
middle of the country and in mountainous areas.

Note that counties in Alaska and Hawaii were included when calculating
the mean, however they are not included in the plot below.

<br>

<img src="mean-population-elevation_files/figure-gfm/unnamed-chunk-13-1.png" width="100%" />

<br>

Most people live in the green counties (below 1000 ft elevation).

<br>

<img src="mean-population-elevation_files/figure-gfm/unnamed-chunk-14-1.png" width="100%" />

<br>

<br>

Three states (AZ, CA, CO) have a range of more than a mile in elevation
between the lowest and highest mean county elevations.

<br>

<img src="mean-population-elevation_files/figure-gfm/unnamed-chunk-16-1.png" width="100%" />

<br>

## 4\. Notes

Can we rely on the population mean elevation calculated based on
“populated places?” Yes, because (1) 94% of the counties have more
than 10 populated places ; and (2) those with less are mostly sparsely
populated ranching and farming areas in a band from Texas to North
Dakota where it’s relatively flat.

<br>

<img src="mean-population-elevation_files/figure-gfm/unnamed-chunk-18-1.png" width="100%" />

<br>

<img src="mean-population-elevation_files/figure-gfm/unnamed-chunk-19-1.png" width="100%" />

<br> <br>

(end of document)
