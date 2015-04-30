# Plotting density of census tracts by distance to a point

##  Get the data!

The shapefiles, which contain the land area (used for density) as well as a lat/long combination, are found on the [Census website](ftp://ftp2.census.gov/geo/tiger/TIGER2014/TRACT/)

To download all of them at once, run:
```bash wget -m ftp://ftp2.census.gov/geo/tiger/TIGER2014/TRACT/```
And the zip files will be downloaded in a nested folder. 

To unzip all of the data files at once, run:
```bash find ./ -name \*.zip -exec unzip {} \;```

This unsips ```.dbf``` files, which are a type of database file that can be converted to ```.csv``` using ```csvkit``` and the function ```in2csv``` with a ```-f dbf``` flag.
```bash find ./ -name \*.dbf -exec in2csv -f dbf {} \; > file.csv```

So ```file.csv``` has some repeating lines, but those get ignored when we merge the file with data about population.

The population data came from the [Minnesota Population Center](https://www.nhgis.org/), which allows for historical data and geographies to be downloaded, although it does require creating an account. I downloaded this file and saved it as ```population.csv```

## Analysis in notebook form:

The ipython notebook [0. Data prep](http://nbviewer.ipython.org/github/cwang912/density_plots/blob/master/0.%20Data%20prep.ipynb) details the cleaning and merging of the two data sets.

The ipython notebook [1. Distance vs. Density plots](http://nbviewer.ipython.org/github/cwang912/density_plots/blob/master/1.%20Density%20vs.%20distance%20plots.ipynb) details the plotting. Future work will attempt to fit a model to the data or allow for user input.
