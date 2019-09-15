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

### Releases per Year, splitted by Genre

168,735 albums in full-length CD or vinyl selection of which 46,025 were identified as duplicates (same name, band and year) and dropped

<table border="0">
 <tr>
    <td>

All genre tags that were at least one year among the top ten:

Genre Tag     | Count
------------- | -------------
Death         | 35,129
Black         | 30,920
Heavy         | 24,529
Thrash        | 21,914
Rock          | 12,538
Power         | 12,529
Doom          | 11,534
Melodic       | 11,249
Progressive   | 11,248
Hard          |  6,524
Gothic        |  4,536
Speed         |  4,567
Groove        |  1,737
Symphonic     |  1,601
Brutal        |  1,401
Folk          |  3,544
Sludge        |  1,089
Stoner        |    843
Atmospheric   |    613
Hardcore      |  2,136
Crossover     |  1,891
Punk          |  1,874
NWOBHM        |  1,566
Psychedelic   |   784
Pop           |   412
Various       |   376
Glam          |   224
Blues         |    68
Gospel        |    10
never in top ten| 54,627  
</td>
    <td>


Fraction of the release per year of every sub-genre 
  <img src="https://raw.githubusercontent.com/garbersc/ma-scraper/master/pics/outputGenreSplits.png" width="300" />  
    </td>
 </tr>
</table>

#### and some inerpretation

## Types of Releases

When looking for all releases I got 487,000 and removed 123,710 as duplicates

<table border="0">
 <tr>
    <td>

Types of all releases:

Type           | Count
---------------|------
Full-length    | 237,335
Demo           |  88,321
EP             |  71,847
Single         |  32,775
Split          |  21,480
Compilation    |  18,875
Live album     |   9,531
Video          |   4,789
Boxed set      |   1,162
Collaboration  |     696
Split video    |     179  
</td>
    <td>



Releases per year splitted by release type  
  <img src="https://raw.githubusercontent.com/garbersc/ma-scraper/master/pics/TypesPerYear.png" width="300" />  
    </td>
 </tr>
</table>



## Formats of Releases

<table border="0">
 <tr>
    <td>

Formats of all releases:

Format                   | Count
-------------------------|------
CD                       |   218,003
Digital                  |   106,624
Cassette                 |    87,117
12" vinyl                |    34,846
7" vinyl                 |    14,683
other (i.e. multi disc)	 |    25,727  
</td>
    <td>



Releases per year splitted by release format  
  <img src="https://raw.githubusercontent.com/garbersc/ma-scraper/master/pics/FormatsPerYear.png" width="300" />  
    </td>
 </tr>
</table>



## Formats splitted by Types

Releases per year splitted by release format for full-length | Releases per year splitted by release format for EPs  
:--:|:--:
![FullLength](https://raw.githubusercontent.com/garbersc/ma-scraper/master/pics/FormatsOfFull-length.png) | ![EP](https://raw.githubusercontent.com/garbersc/ma-scraper/master/pics/FormatsOfEP.png)

Releases per year splitted by release format for Singles | Releases per year splitted by release format for Demos 
:--:|:--:
![Single](https://raw.githubusercontent.com/garbersc/ma-scraper/master/pics/FormatsOfSingle.png) | ![Demos](https://raw.githubusercontent.com/garbersc/ma-scraper/master/pics/FormatsOfDemos.png)

Releases per year splitted by release format for Splits |
:--:|:--:
![Split](https://raw.githubusercontent.com/garbersc/ma-scraper/master/pics/FormatsOfSplit.png) |


