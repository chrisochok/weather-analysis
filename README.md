# Data Engineer Test_Green Flag

ASSUMPTIONS:
Upon reviewing schema statistics:
 1. The 'ObservationDate' field should be a 'date' attribute so was coerced to 'datetime' from 'str' data type for querying accuracy.
 2. Some 'NaN' values were identified in the following numeric fields and have been imputted with zeros - [WindGust - 151411, Visibility - 26493, Pressure - 14820].
 3. 27760 'NaN' values were identified in the 'Country' field. These were replaced with empty strings.
 4. "The converted data should be queryable to answer the following question." - it's assumed that this statement refers to converting data file to parquet columnar store before further analysis.


> weather.py
```
  This script reads in the weather data (194697 rows by 15 columns) and coverts into parquet data format. Performs minor transformations as detailed above, then answers the following questions (grouped into python functions):

  a. Which data was the hottest day?
  b. Temperature on that day
  c. Region was the hottest day
```
> test_weather.py
```
  Test suite that independently tests small units of codes within the weather.py file.
```
> file_path_sample.py
```
  Small sample python module that hides/ supplies local file path for the .csv files. Note: Rename file_path_sample.py to file_path.py
```

Repro steps via cli:

* Clone the repository using Terminal/CLI.
  ```
  $ mkdir weather
  $ cd weather
  $ git clone https://github.com/Chrisochok/weather_analysis.git
  ```
* Refactor file_path_sample.py to file_path.py, and
* Set the file_path to your csv files location.
* Navigate to the folder containing weather.py & test_weather.py files i.e. one level up from ~/Desktop/weather/data
```
  $ pwd `to check that you are in the right location`
  $ cd ~/Desktop/weather/
```
* Install `pandas` and `fastparquet` modules and dependencies (if you do not have these installed)
  On Windows:
```
  $ pip install pandas
  $ pip install fastparquet
```
  On Mac:
```
  $ pip3 install pandas
  $ pip3 install fastparquet
```
* Run test_weather.py script ( the tests should fail at this stage )
```
  $ python3 -m unittest weather.py
```
* Run weather.py script
```
  $ python3 weather.py
```
* Now run test_weather.py once more
```
  $ python3 -m unittest weather.py
```
* Alternatively run scripts directly from your favourite IDE.