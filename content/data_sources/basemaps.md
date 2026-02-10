# Basemaps

Base maps are important for providing context to your maps. They can help to orient the reader and provide a reference for the location of the features you are mapping. There are different types of basemaps available, including:

- **Administrative boundaries:** These basemaps show the political boundaries of countries, states, and other administrative units. 
- **Infrastructure:** These basemaps show roads, buildings, and other features of the built environment. 
- **Topographic maps:** These basemaps show the physical features of the landscape, such as elevation, rivers, and vegetation.
- **Satellite or aerial imagery:** These basemaps show the Earth's surface as captured by satellites. They can provide detailed information about land use, vegetation, and other features of the landscape.


:::{figure} ../img/basemaps/esri_vectortilebasemaps.png
Basemaps provided by [ESRI](https://livingatlas.arcgis.com/en/browse/#d=1&cont=true&categories=Vector+Tiles) 
:::


## 1. Base maps from administrative boundaries


### 1.1. Download administrative boundaries

When creating the lake monster map, we used a simple basemap that only shows the administrative boundaries of the area. This was sufficient for our purposes, as we wanted to focus on the features of the lake monster rather than the details of the landscape.

You can create similar map for your study area by downloading administrative boundaries from a source such as 

- [Natural Earth](https://www.naturalearthdata.com/): good for visualisation, boundaries are simplified for better use with small scale maps, e.g. country borders
- [GADM](https://gadm.org/): good for analysis, boundaries are not simplified and at different levels (e.g. country, state, county, municipality, etc.) 
- [Project Linework](https://www.projectlinework.org/): for more artistic looking boundaries at small scales 

These sources provide shapefiles of administrative boundaries at different levels (e.g., country borders, state borders, etc.) that you can load into QGIS and use as a basemap for your project.


:::{figure} ../img/studyarea/Study_area_HD.png
:width: 70%
Map showing the location of Heidelberg, Germany, with administrative boundaries as basemap.
:::

A more elaborate example can be found on Wikipedia which provides nice maps using administrative boundaries as base maps.

:::{figure} https://upload.wikimedia.org/wikipedia/commons/f/ff/Base_Map_of_the_Netherlands.png
:width: 50%
Base Map of the Netherlands showing administrative boundaries as basemap. Source: https://commons.wikimedia.org/wiki/File:Base_Map_of_the_Netherlands.png
:::

### 1.2. Creating a map of your study area based on administrative boundaries

In order to style a certain country differently than the others, you need to extract it and save it in another data set. 

1. Load the administrative boundaries shapefile into QGIS.
2. Use the "Select Features by area or single Click" tool to select the country you want to style differently. Export the selected features as a new data set. It will be added as a new layer in QGIS. 

:::{figure} ../img/studyarea/studyarea_extract_country.mov
Select and export country as new data set in QGIS. It 
:::

3. The extracted data set is added as a new layer in QGIS. So now you can style it differently than the other countries. 

:::{figure} ../img/studyarea/studyarea_style.mov
Style the country so that it stands out from the other countries in QGIS.
:::

You can do this with any other vector data set as well. 


## 2. Base maps from web services

Administrative boundaries only give political context. In some cases, you might want to add more details about the landscape, such as roads, buildings, land use, etc. You can do this by adding basemaps from web services. These basemaps are provided by different providers (e.g. OpenStreetMap, Google Maps, etc.).

Using these services, you don't need to download the data. QGIS does this while rendering the map.

Here is how to add basemaps in QGIS:

1. Install the XZY Tiles Basemap Downloader plugin in QGIS.

:::{figure} ../img/basemaps/xyz_installplugin.mov
Install the XYZ Tiles Basemap Downloader plugin in QGIS
:::

2. Click on the "XYZ Tiles Basemap Downloader" icon in the toolbar to load the basemaps. You only need to do this once after installing the plugin.  

:::{figure} ../img/basemaps/xyz_start.png
Load the basemaps using the XYZ Tiles Basemap Downloader plugin in QGIS
:::

3. Restart QGIS. Save your project first, otherwise you might lose your work. 

4. Open the browser panel on the left. If it is not there yet, you can activate it in the menu (View -> Panels -> Browser). Navigate to the XYZ Tiles section and you should see a list of basemaps that you can add to your project.

:::{figure} ../img/basemaps/xyz_load.mov
Navigate to the XYZ Tiles section and load a layer
:::

Explore the different basemaps and add the one that you like to your project by double-clicking on it. You can adjust the transparency of the basemap layer in the "Layer Styling" panel to better visualize your other layers on top of it.

:::{caution}
**Add attribution of the basemap to your map if the licence requires it**, i.e., the name of the basemap and who provides it. You can usually find the attribution information in the terms of use for the basemap.
:::

The appearance (colors, etc.) of these basemaps cannot be edited. For more advanced editing options you can use other providers such as MapBox or MapTiler. But these require a user account. 





