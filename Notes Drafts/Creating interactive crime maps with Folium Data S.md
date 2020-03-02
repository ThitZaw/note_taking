# Creating interactive crime maps with Folium – Data Science Blog by Domino

Created By: Thit Zaw
Last Edited: Feb 13, 2020 11:03 PM
URL: https://blog.dominodatalab.com/creating-interactive-crime-maps-with-folium/

*You can see this Domino project [here](https://try.dominodatalab.com/u/joshpoduska/crimemaps/overview).*

I get very excited about a nice map. But when it comes to creating maps in Python, I have struggled to find the right library in the ever changing jungle of Python libraries. After some research I discovered [Folium](https://github.com/python-visualization/folium), which makes it easy to create [Leaflet](http://leafletjs.com/) maps in Python. This blog post outlines how I used Folium to visualize a data set about crime in San Francisco. I then describe a how to use Domino to turn this Python code into a self-service reporting tool.

Folium is a powerful Python library that helps you create several types of Leaflet maps. The fact that the Folium results are interactive makes this library very useful for dashboard building. To get an idea, just zoom/click around on the next map to get an impression. The [Folium github](https://github.com/python-visualization/folium) contains many other examples.

By default, Folium creates a map in a separate HTML file. In case you use Jupyter (like myself), you might prefer to get inline maps. [This Jupyter example](https://try.dominodatalab.com/u/joshpoduska/crimemaps/view/examples.ipynb) shows how to display maps inline.

For this example I needed some interesting data that contains locations. I decided to use [SFPD incident data from SF OpenData](https://data.sfgov.org/Public-Safety/Police-Department-Incident-Reports-Historical-2003/tmnf-yvry). Use the Export function (select csv) to download the entire dataset.

![Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/SFPD-Dataset-Image-Aug-2019.png](Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/SFPD-Dataset-Image-Aug-2019.png)

The [Jupyter notebook](https://try.dominodatalab.com/u/joshpoduska/crimemaps/overview) contains only a few lines of code. It loads the incident file into a pandas dataframe, selects the first 1000 records to speed things up a little, and creates an inline map containing an interactive map with markers based on the resulting dataset.

[Untitled](Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/Untitled%20Database.csv)

When running this, it creates a map with location markers that are clustered (`clustered_marker = True`) if close together. The tileset used in here is OpenStreetMap (which is default). Folium can be used with other tilesets like Mapbox or Cloudmade too.

![Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/1000recordsmap.png](Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/1000recordsmap.png)

You save a map as an html file by using `map.create_map(path='map.html')` instead of `display(map)`

Well, that was fun! But this might not be an ideal visualization to compare maps with each other. Lucky for us, there is also a way to create a choropleth map thanks to Folium.

> A choropleth map (from Greek χώρο (“area/region”) + πλήθος (“multitude”)) is a thematic map in which areas are shaded or patterned in proportion to the measurement of the statistical variable being displayed on the map, such as population density or per-capita income.

To create a choropleth, we need a geojson file to create the areas/boundaries that match the San Francisco police districts in the data file. With a Google search on “sfpd districts geojson” I found a government open data website with a Shapefile that almost matches my needs.

The next step is to convert the Shapefile into a geojson file. The easiest way is to use an [ogr2ogr web client](http://ogre.adc4gis.com/). Select the downloaded zip file and put `crs:84` in the Target SRS field. Save the result as sfpddistricts.geojson and upload the file to your Domino project.

The additional Python code to create a choropleth is as follows. Note that I used the whole dataset instead of the 1000 records used earlier. Because the choropleth is based on the aggregated counts, the speed isn’t suffering from large datasets.

[Untitled](Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/Untitled%20Database%201.csv)

It creates a choropleth map like below with a legend in the upper right corner. [Color Brewer](http://colorbrewer2.org/) color schemes are built-in and added like `fill_color = 'YlOrRd'`. The aggregated counts are stored in a separate json file (`crimedata2.to_json('crimeagg.json')`) which is later used as data source during the creation of the map.

![Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/choromap.png](Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/choromap.png)

## Building a self-service reporting tool

The crime incident data is much richer than just locations and districts. It also contains variables like categories, dates and times. This creates the opportunity to, for instance, get better insights in specific sorts of incidents. To avoid making maps for all combinations of variables, I used Domino’s “Launcher” feature to let others create their own maps based on their parameters.

![Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/Launcher-crimemap-try.png](Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/Launcher-crimemap-try.png)

A Launcher in Domino is a self-service web form that lets non-technical users run your script. To create one, we just need to specify what parameters to expose through the web form.

My launcher will have two parameters: 1. “Dayofweek” is a multi-select list and contains all the days of the week. 2. “Category” is a select menu with all the incident categories that are in the data.

Out of laziness, I decide to create a little script to create the list of categories that occur in the data.

![Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/Running-script-crimemaps.png](Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/Running-script-crimemaps.png)

I copy paste the result of the second cell into the Allowed Values field in the newly created launcher.

The script that handles the launcher requests is [main.py](https://try.dominodatalab.com/u/joshpoduska/crimemaps/view/main.py). This next bit of code handles the user input and uses it to filter the dataset:

[Untitled](Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/Untitled%20Database%202.csv)

Now that we have category and description information, why not use it as a popup for the markers? Just add `popup=each[1]['Category'] + ": " + each[1]['Descript']` to the parameters of the marker placement function. Main.py contains both the marker map code and the choropleth code.

Now we can create maps using the launcher. The following (static) map shows the drugs and narcotics related incidents in the weekends (Saturday & Sunday). Zooming in on the created map will make the clusters split. The blue markers refer to individual incidents. It is probably no surprise to see that most drug related incidents take place in and near the Tenderloin area.

![Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/mapdrugweekend.png](Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/mapdrugweekend.png)

It also creates a choropleth map like this one, telling a story similar to the map with markers.

![Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/mapchorodrugweekend.png](Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/mapchorodrugweekend.png)

## Bonus: comparing maps

Now that we have created the code and launcher like this, we can use the Domino comparison feature to put multiple maps side by side.

I had two separate runs from the launcher, one with burglaries in the weekend and one during weekdays. Both runs succeeded. The next step is to select both runs and hit compare at the top.

![Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/Compare-1.png](Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/Compare-1.png)

A page will open which contains a comparison of both runs. The nice part is that it will put the maps next to each other. This way we can easily see that, in case of our example, burglaries seem more evenly spread over San Francisco in weekends than during weekdays.

![Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/Compare-2.png](Creating%20interactive%20crime%20maps%20with%20Folium%20Data%20S/Compare-2.png)

So there we have it, a pretty easy way to create and compare maps. I didn’t find very shocking crime incident trends, yet. So feel free to share your most interesting finds in the comments.

*Domino note: This popular post was updated in August 2019 to reflect technical changes.*