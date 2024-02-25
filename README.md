# aral-station-data

Generate a JSON list of all [BP](https://www.bp.com/) Gas Stations.

# Structure

````commandline
/
    /get.py # gets all stations and automatically sorts them in /out
    /generator.py # generates the following files in /out/other: sitemap.xml, facilities.json and fuel.json
    /database.py # generates a sqlite3 file based on "stations_ARAL Tankstelle_min.json" which is used in "aral-prices"
````

## Usage

Install the dependencies with ``pip install -r requirements.txt``  
Then you can get all gas stations by running ``python3 get.py``  
The data will be in the ``/out`` folder.

# Data

The stations are divided by Brand and Country.

Directory structure:
````commandline
out/
    /all
        /stations.json # these are all BP Stations worldwide
    /brands
        /stations_BP.json # all stations with the Brand BP
        /stations_ARAL Tankstelle.json # all stations from the Brand Aral
    /countries
        /stations_DE.json # all German stations from all brands
        /stations_US.json # all stations in the US from all Brands
    /ov2 # note that there are no skipper records yet! The performance will be very bad
        /stations.ov2 # all stations
        /stations_DE.ov2 # all german stations
    /other # used in another project
````

There is always a ``_min.json`` available (e.g. `stations_min.json`) that has the whole JSON on a single line.  
Use the default file for better readability.

You can find the data [here](https://github.com/aral-preise/aral-station-data/tree/gh-pages).

There is also a README.md in the data that has basic stats.

# Data accuracy

The data may not be accurate as the script calls the [gas station locator API](https://mein.aral.de/tankstellenfinder/) and this can be prone to errors.  
  
Please note that there may be stations missing!

# Data updated

The data is updated by [this](https://github.com/aral-preise/aral-station-data/blob/main/.github/workflows/generate.yml) GitHub action.  
The version is automatically bumped by [this](https://github.com/aral-preise/aral-station-data/blob/main/.github/workflows/version.yml) GitHub action on cron '0 2 * * 1'.