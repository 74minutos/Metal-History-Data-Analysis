The original scraper is not working at the moment. The README is not fully updated with all addition yet and the code is not cleaned at the moment.

[original scraper](https://github.com/jonchar/ma-scraper) by @jonchar  
[analysis on metal-archives data by him](https://jonchar.net/notebooks/MA-Exploratory-Analysis/)  
[jump to analysis](https://garbersc.github.io/ma-scraper/#analysis)  

# Metal Archives Scraper

URL: http://www.metal-archives.com/

This script uses requests to retrieve the data and pandas to collect it before
saving in \*.csv format.

## Scraping band names alphabetically

Band names can be found alphabetically on the site. The tables they are
presented in are loaded via AJAX requests that return data in JSON format.
The script `MA_scraper.py` retrieves the alphabetical list of band names
along with the other information in the table (Country, Genre, & Status).

* The maximum number of band names returned is 500, it can be set by
`iDisplayLength`.

* The starting point in the alphabetical list for a given letter is set by
`iDisplayStart`.

* Every JSON response contains a field `sEcho`, which if left blank in the URL
request will result in invalid JSON being returned, so `sEcho` is set to 0 in
order to avoid this.

## Approach

The script collects the data in chunks of 500 bands at a time starting with
bands whose names start with a number and then alphabetically. If the response
does not contain valid JSON, the script will retry up to 10 times.

## Output

The collected information is then stored in a \*.csv file with the following
column headers and data types:

* `'NameLink'`: HTML snippet containing band name and link to corresponding
band page on Metal Archives (HTML string)

* `'Country'`: Country of origin (string)

* `'Genre'`: Description of band genre (string, terms not standardized)

* `'Status'`: HTML snippet describing band status (HTML string, active / split-up / changed
name / on hold / unknown / disputed)

Total number of bands may vary as the site is regularly updated.
Check [their stats page](http://www.metal-archives.com/stats) for a current
number.

# Analysis
what was the idea and why this is cool
- [ ] may come

## Enzyclopedia Metallum: The Metal Archives
describe MA, were the data comes from and what 'features' include

## Releases

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
<table border="0">
 <tr>
    <td>Lorem ipsum ...</td>
    <td>
    Lorem ipsum ...
    </td>
 </tr>
</table>


### Releases per Year, splitted by Genre

168735 albums in full-length CD or vinyl selection of which 46025 were identified as duplicates (same name, band and year) and dropped

<table border="0">
 <tr>
    <td>

All genre tags that were at least one year among the top ten:

Genre Tag     | Count
------------- | -------------
Death         | 35129
Black         | 30920
Heavy         | 24529
Thrash        | 21914
Rock          | 12538
Power         | 12529
Doom          | 11534
Melodic       | 11249
Progressive   | 11248
Hard          |  6524
Gothic        |  4536
Speed         |  4567
Groove        |  1737
Symphonic     |  1601
Brutal        |  1401
Folk          |  3544
Sludge        |  1089
Stoner        |   843
Atmospheric   |   613
Hardcore      |  2136
Crossover     |  1891
Punk          |  1874
NWOBHM        |  1566
Psychedelic   |   784
Pop           |   412
Various       |   376
Glam          |   224
Blues         |    68
Gospel        |    10
never in top ten| 54627  
</td>
    <td>


Fraction of the release per year of every sub-genre 
  <img src="https://raw.githubusercontent.com/garbersc/ma-scraper/master/pics/outputGenreSplits.png" width="500" />  
    </td>
 </tr>
</table>

Fraction of the release per year of every sub-genre  
![RealeasesPerGenre](https://raw.githubusercontent.com/garbersc/ma-scraper/master/pics/outputGenreSplits.png) 

#### and some inerpretation

## Types of Releases

When looking for all releases I got 487000 and removed 123710 as duplicates

Types of all releases:

Type           | Count
---------------|------
Full-length    | 237335
Demo           |  88321
EP             |  71847
Single         |  32775
Split          |  21480
Compilation    |  18875
Live album     |   9531
Video          |   4789
Boxed set      |   1162
Collaboration  |    696
Split video    |    179

Releases per year splitted by release type  
![Types](https://raw.githubusercontent.com/garbersc/ma-scraper/master/pics/TypesPerYear.png)


## Formats of Releases
Formats of all releases:

Format                   | Count
-------------------------|------
CD                       |          218003
Digital                  |          106624
Cassette                 |           87117
12" vinyl                |           34846
7" vinyl                 |           14683
other (i.e. multi disc)	 |	   25727

Releases per year splitted by release format  
![Formats](https://raw.githubusercontent.com/garbersc/ma-scraper/master/pics/FormatsPerYear.png)


## Formats splitted by Types

Releases per year splitted by release format for full-length  
![FullLength](https://raw.githubusercontent.com/garbersc/ma-scraper/master/pics/FormatsOfFull-length.png)

Releases per year splitted by release format for EPs  
![EP](https://raw.githubusercontent.com/garbersc/ma-scraper/master/pics/FormatsOfEP.png)

Releases per year splitted by release format for Singles  
![Single](https://raw.githubusercontent.com/garbersc/ma-scraper/master/pics/FormatsOfSingle.png)

Releases per year splitted by release format for Demos 
![Demos](https://raw.githubusercontent.com/garbersc/ma-scraper/master/pics/FormatsOfDemos.png)

Releases per year splitted by release format for Splits
![Split](https://raw.githubusercontent.com/garbersc/ma-scraper/master/pics/FormatsOfSplit.png)


