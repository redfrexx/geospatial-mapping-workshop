# Exercise: Lake Monster Map

Let's pretend we want to create a map for a Nature Journal article about the **distribution of sightings of lake monsters - creatures reported to live in lakes that are mainly known from folklore and typically take on the the shape of extinct or extraordinarlily large living reptiles - in the US and Canada. You want your readers to understand the relationship between the monster locations and also their location on the planet.

We'll be working with an international dataset of locations of lake monsters, the most famous of which is arguably Nessie who supposedly lives in Loch Ness in Scotland. This dataset was assembled from [Wikipedia's List of Lake Monsters](https://en.m.wikipedia.org/wiki/List_of_lake_monsters).

:::{figure} https://upload.wikimedia.org/wikipedia/commons/b/b3/Loch_Ness_Monster_Surgeon%27s_photograph.jpg
:width: 50%
Photograph showing the Loch Ness Monster, taken by Robert Kenneth Wilson in 1934. The photo was later revealed to be a hoax, but it remains one of the most famous images associated with lake monsters. Source: https://en.wikipedia.org/wiki/Loch_Ness_Monster#/media/File:Loch_Ness_Monster_Surgeon's_photograph.jpg
:::

## What story are we trying to tell?

For this map, the story we want to tell is:
- Where are these monsters reported to live in the US Great Lakes area?
- What are their names?
- For reference, what lakes and states or provinces are they in?

## Download Data

Download the data for this exercise from this [online repository](https://ucdavis.box.com/s/ozobvtvehgmsnfrizwb2darqfsoqmmgq). If you downloaded a .zip file, unzip the data to a folder you can easily find.

The data we have to work with today is:
* **Lake Monsters** (LakeMonsters.gpkg): Locations of lake monsters, Vector data set (Points)
* **Great Lakes** (Lakes_GreatLakes-Area.gpkg): Extract from the [Natural Earth Data](https://www.naturalearthdata.com/) lakes dataset for the Great Lakes and areas adjacent, Vector data set (Polygons)
* **Admin boundaries** (US_CAN_Admin1.gpkg): Extract from the [Natural Earth Data](https://www.naturalearthdata.com/) states and provinces data for the US and Canada, Vector data set (Polygons)
* **Digital Elevation Model (DEM):** (dem.tif): Represents the terrain, Raster data set

See the README.txt file that comes with the data download for more details and sources of the data.

## Setting up the QGIS project

1. Open QGIS and start a new project.

2. Set your project's projection to North America Albers Equal Area Conic (ESRI: 102008). This projection minimizes distortions for North America. If you're working on a map featuring a different area, choose a projection that fits your chosen area.

:::{figure} ./img/monsters/set_crs.mp4
Set the coordinate references system of your QGIS project
:::

:::{tip}
You can pause and play the videos by right-clicking on the video and selecting *Play* or *Pause* from the menu.
:::


3. Save your project file. Do this frequently, so you don't lose your work if QGIS crashes.

## Explore the data sets

Load all data sets mentioned above into QGIS:
- Lake Monsters
- Lakes
- Admin boundaries
- DEM

:::{figure} ./img/monsters/load_data.mp4
QGIS showing the three layers loaded. Note that the colors of the data are selected at random, so your data will probably look different.
:::

You may change the order of the layers so all of them are visible on the canvas.

:::{figure} ./img/monsters/change_order.mp4

:::

The monster data sets is a vector file. So it contains objects (monster sightings) associated with attributes. We can explore its attributes in the attribute table. Right-click on the monster layer on the left and select "Open Attribute Table". This will show you the attributes of the lake monster locations. You can see that there are columns for the name of the monster, the country it's in, and the lake it's associated with.

:::{figure} ./img/monsters/explore_data.mp4
Exploring the data in the attribute table of the lake monster layer.
:::

Explore the attributes tables of the other vector data sets (*Lakes_GreatLakes-Area* and *US_CAN_Admin1*) as well.

The dem layer is a raster data set, so it doesn't have an attribute table. You can uncheck it in the Layer panel so it is not shown in the canvas.

## Style the data

We've decided on our story and loaded up our data. Now it's time to style the data. First, let's center our view on the Great Lakes area using the zoom tool. It doesn't have to be perfect. We will adjust later.

:::{figure} ./img/monsters/ZoomToGreatLakes.png
Screenshot of the map canvas zoomed to the Great Lakes area
:::

Let's open the *Layer Styling* Panel.
1. Click the *View* menu at the top of the QGIS window
1. Choose *Panels*
1. Check *Layer Styling* - there should now be a panel on the right side of your screen.
1. Make sure the box next to *Live update* is checked. This will update the map canvas with any changes you make in the *Layer Styling* panel without you having to click an "Apply" button.

:::{figure} ./img/monsters/change_style.mp4
:::


### Administrative boundaries

Let's start with the largest background layer.  This will have a big impact on how we style the other layers and will help set the tone for how we work. We want to set the fill color to white and the border to a light gray. This will make the states recede into the background and not compete with the other layers for attention.

Open the *Layer Styling* panel,

1. Click on **Simple Fill**.
2. Set the **Fill color** to white by entering the hex color code **#ffffff** in the HTML notation box at the bottom.
3. Set the **Stroke color** to a light grey by entering the hex color code **#cbcbcb** in the HTML notation box at the bottom.

:::{figure} ./img/monsters/style_admin.mp4
:::

The stroke on the states might look a little light and might be confusing to the eye because the ocean color is the same color as the fill. Let's change the background color to make the ocean color easier for our eyes to understand:

1. On the *Project* menu, select *Properties*.
1. Select the *General* tab on the left side of the window, then click on *Background color* in the middle of the window.  Change it to the same color as the stroke of your states.  Click *OK* in the color interface and *OK* in the Options interface.

:::{figure} ./img/monsters/set_backgroundcolor.png
:::

### Lakes

Let's style the lakes layer. Select the layer (*Lakes_GreatLakes-Area*) in the **Layer Styling** panel and change the style as follows:

1. Activate the *Lakes_GreatLakes-Area* layer in the *Layer Styling* panel.
1. Click on **Simple Fill**.
1. Set the **Fill color** to gray with 75% white (25% black) - *#bfbfbf* as hex code.
1. For the **Stroke style** drop-down menu, pick **No Line**, which removes the stroke altogether.

Remember our discussion of Visual Hierarchy? The background layers - the states and the lakes - now seem to recede and demand less of our attention. This is important so we can make the monster locations stand out next.

:::{figure} ./img/monsters/Style_Lakes.png
:::


### Lake Monsters

The last layer to style is the lake monsters.

1. Activate the **LakeMonsters** layer in the *Layer Styling* panel.
1. Click on **Simple marker**.
1. Scroll down to the box that contains different marker shapes. **Choose the rounded squares.**
1. Set the **Fill color** to black **(#000000)**.

:::{figure} ./img/monsters/Style_Monsters.png
:::

Setting the points to black make them stand out well against the lighter background data.  Circles are the obvious choice for point data, but using squares for point markers rather than circles makes them stand out more. Both are good options though. In academic publications, I try to avoid shapes like stars. They might look silly, but more importantly, they are complex shapes and we're trying to avoid complexity.


[//]: # ()
[//]: # (OPTIONAL: I f you prefer icons, download an svg icon you like from svgison.com and integrate them into the map following these steps:)

[//]: # ()
[//]: # (1. In the *Layer Styling* panel, click on the drop down menu next to *Symbol layer type* and select *SVG marker*.)

[//]: # (2. Click on the *...* button next to the *SVG file* box and navigate to the location of your downloaded svg icon.  Select it and click *Open*.)

[//]: # (3. Adjust the *Size* as needed.  You may also want to adjust the *Angle* if your icon is not oriented the way you want it to be on the map.)

[//]: # (4. Note that if you use an icon, you will need to make sure it is a simple icon with a transparent background and that it will be visible at the size you need for your map.  You may also want to adjust the *Offset* options to make sure the icon is centered on the point location.)


## Labels

**About fonts:**
I like to pick a single font to work with for the whole map. I will use **Helvetica** here and show you ways to vary this single font to meet our needs. Note that my default font is some system font, so I'll need to change that for each layer. You can use whatever you like. The reason I'm using Helvetica is that 
- It's sans serrif (it has simple lines and no flourishes... compare it with Times New Roman which is a serif font), and 
- It has many variants - regular, bold, bold italic, italic, light, light italic - so it's like have 6 fonts that all go together.

Set the labels for each layer according to the following specifications. For each one, go to the *Layer Styling* panel, select the layer you want to label and click on the yellow "abc" icon to open the labeling options.

### States

Choose *Single Labels* from the drop-down menu at the top of the panel. There are 9 tabs in the labeling options panel. Hover with your mouse over each of the options to see their name. Adjust the settings for each layer as described below. 

#### Text Tab
- **Value:** *name* (this will use the column "name" from the attribute table as a label text for each state)
- **Font:** Helvetica 
- **Size:** 8 points 
- **Color:** Light grey (#cbcbcb) (same as the ocean color)

#### Formatting Tab
- **Type case:** *All Uppercase*
- **Spacing - Letter:** 1.5 (This spaces out the letters, a design choice that is fairly common with labeling large polygons)

#### Rendering Tab
- In the *Overlapping labels* section set **mode** to **"Allow overlaps without penalty"**.


:::{figure} ./img/monsters/label.mp4
:::

![./img/monsters/label.mp4](./img/monsters/label.mp4)

### Lakes

We'll used rule-based labeling with this one so we just label the big lakes. Labeling all the lakes would clutter the map. Choose *Rule-based labeling* from the drop-down list. Add a new label by clicking on the green + button at the bottom of the panel.

#### Create a new labeling rule:
- **Description:** Big Lakes
- **Filter:**  $area > 19000000000

#### Text Tab
- **Value:** *name* (this will use the column "name" from the attribute table as the label text)
- **Font:** Helvetica 
- **Style:** Italic/Oblique (traditionally, waterbodies are labeled with a slant or italic font... it's not a rule)
- **Size:** 8 points 
- **Color:** Light grey (#7f7f7f) (slightly darker or lighter than the lake color)

#### Rendering Tab
- In the *Overlapping labels* section set **mode** to **"Allow overlaps without penalty"**.

:::{figure} ./img/monsters/labels_lake.mp4
:::


### Lake Monsters

Adjust the labels for the Lake Monsters layer according to the following specifications:

Choose *Single Labels* from the drop-down menu at the top of the Styling panel in the labeling section. Like we did with the admin boundaries. 

#### Text Tab
- **Value:** *name* (this will use the column "name" from the attribute table as the label text)
- **Font:** Helvetica 
- **Style:** Bold 
- **Size:** 10 points 
- **Color:** Black (#000000)

### Formatting Tab
- **Wrap on Character:** , (comma) (When labels contain a comma, the comma is replaced by a new line character so the labels with two names print each name on its own line.)

[//]: # (- **Line height:** 0.70 line - This makes the lines closer to eachother when there are two lines in a label.)

### Rendering Tab
- In the *Overlapping labels* section set **mode** to **"Allow overlaps without penalty"**.

:::{figure} ./img/monsters/labels_monster.mp4
:::


## Designing a map

Let's assume this map is for an article in one of the Nature journals. It is important to check the publisher's specifications for figures. In our case they require:

* **Size**: 183 x <240 mm
* **Format**: .jpg
* **Other**: No divided images unless the sections are related

### 1. Create a new map layout

In QGIS, the print layout interface is where you compose your map. 

Create a new layout:
1. Project Menu -> New Print Layout
2. In the window that pops up, give your new layout a name. I'll call mine "Nature Specs" so later I'll know this layout was for my Nature submission with this data. Click *OK*.
3. A new blank layout window should now be open.

:::{figure} ./img/monsters/create_maplayout.mp4
:::

### 2. Set the page size

1. Right click anywhere on the white page in the middle of the window
1. Select *Page Properties* from the menu
1. On the panel on the right side of the screen, set the *Size* drop down to *Custom*, then set the *Width* to 183 mm and the *Height* to 240 mm for now - we'll shrink this later as needed. Note: there is a units drop down to the right of the *Width* and *Height* options.
1. Click the save button. This saves the whole project, not just the layout.


:::{figure} ./img/monsters/set_page.mp4
:::

### 3. Add a map element to the layout

You can add different elements to your map layout. You can see them on the left toolbar. Each of these elements  has properties that can be accessed by clicking on the element on the page. The properties for any given element are displayed in the right side panel. First, we will add a map element to the layout. 

1. Add the map with the *Add Map* tool. Fill up the space at the top of the page, allowing the tool to snap to the corners.

2. Since our story focuses on the Great Lakes area, adjust the map content to show this region. Use the "Move item content" tool to adjust the scale and center of the map such that the data is centered and fills up the map space. You can change the scale by scrolling with your mouse or by defining the scale in the "Item Properties" of the map element on the right. In the latter case, set it to 9000000. Make sure that you've set the coordinate reference system of the project correctly in the first step of this exercise.

After you are done adjusting the scale and center of the map, switch back to the *Select/Move item* tool.

:::{figure} ./img/monsters/center_map.mp4
:::

:::{tip}
If you're map is completely off, use the "Set Map Extent to Match Main Canvas Extent".
:::

#### 4. Adjusting the label placements

Now that we've picked a scale to render our map at, your labels may not look quite the way you want them. But we can fix this. 

1. Transfer the current scale and map center to the canvas so we can adjust the labels there. Click on the "View Current Map Extent in Main Canvas" button in the "Item Properties" of the map element. 

:::{figure} ./img/monsters/adjust_labels.mp4
:::

2. Now the scales match and we can see the effect it has on our labels. Use the **Label Toolbar** to move and rotate labels by hand to put them where you want them so they don't overlap other labels. For labels that are not fully visible in the map, you can move the labels off the map so they aren't getting cut off.

:::{figure} ./img/monsters/label_move.mp4
:::

If you get this message below, just click ok. 

:::{figure} ./img/monsters/label_message.png
:width: 80%
:::

3. When you are done, switch back to the layout window and click the *Refresh view* button. Afterward, the scale and center of the map might be shifted. Move them back as necessary. You might need to repeat this process of moving labels and readjusting the map content a few times to get everything just right.

:::{figure} ./img/monsters/refreshview.png
:::

[//]: # (Also, you may need to turn off the options related to showing labels for any labels that are misbehaving &#40;some of mine were in different places than I put them in the layout&#41;.)

4. When you are done, save the map layout. Do this frequently, so you don't lose your work if QGIS crashes.


### 5. Adding scale bar and north arrow

Finally, do we need any other elements such as scale bars and north arrow? This depends on (1) your story, (2) your audience, and (3) what other maps you have in the paper you are submitting. Is this for a North American audience? Then you probably don't need a scale bar or north arrow because the Great Lakes are a fairly recognizable area. Is it for an international audience? Maybe you need those things. Maybe I have another map that shows all of North America or the world and I've already outlined my study area in that. Then I don't need to add extra context.

#### Add scale bar

Add a scale bar in the lower left corner. Make them the same gray as the administrative boundaries. Move the IOWA or ILLINOIS labels if necessary. Alternatively you could add a white rectangle element behind the scale bar to avoid conflicts with the data around it.

:::{figure} ./img/monsters/add_scalebar.mp4
:::

#### Add north arrow

Complex compass roses are wonderful for large maps, but they are not a good choice when your space is limited.

:::{figure} ./img/monsters/add_northarrow.mp4
:::

#### Add attribution (if needed) 

Make sure to add attribution for your data and basemap. You can do this with a simple text element in the lower right corner. Use a small font size and the same gray as the administrative boundaries so it doesn't compete with the rest of the map.

In our case: 
- The administrative boundaries and lakes are from Natural Earth Data, which is in the public domain and doesn't require attribution.
- The Lake Monster data is from Wikipedia and was assembled from Michelle Tobias. So we'll add this attribution: "Data: Wikipedia's List of Lake Monsters (https://en.m.wikipedia.org/wiki/List_of_lake_monsters) assembled by Michele Tobias" by adding a label in the Map Layout. 

If you use [OpenStreetMap Data](../data_sources/osm.md) you need to add "© OpenStreetMap contributors" as attribution to your map. 


:::{figure} ./img/monsters/attribution.png
:::


### 6. Optional: Adjust the page size to fit the map

Now that all elements are in place, you may adjust the page size to fit the map better. Alternatively, you can also skip this step and specify that the map layout should be automatically cropped to the content when you export the map (see next step).

If you want to adjust the page size, do this:

1. In the "Item properties" for the map, look in the *Position and Size* section to see how high the map is. Copy that number.
1. Click off of the map so it's no longer selected.
1. Right-click on the white page space and select *Item properties* to open the properties for the map layout itself.
1. Paste the height number in the *Height* property to match our map element to the page.

### 7. Export your map

Finally, we're done with our map! (Ok, it's normal if you're now seeing a dozen things you would change, but you've got to submit that paper, so let them go!)  Let's export it!

Exporting happens in the *Print Composer*. 

1. Click the **Export as Image** button, decide where to save your map and what file type you want. 
2. The journal asks for a **.jpg file. **Give it a descriptive name** so we know what it is when we put it in the paper, for example *GreatLakeMonsters.jpg*. 
3. Once you click the *Save* button, a window will pop up asking for more parameters. Set the resolution to 300 dpi. This is sufficient for the first submission. 
4. If you activate the "Crop to content" option, the map will be cropped to the content of the map layout. In this case, you cannot adjust the width and height parameters anymore. Otherwise the whole page will be exported.

:::{figure} ./img/monsters/export.mp4
:::

### Final map 

#### Map without optimized label placement 

This is the map I made, without optimized label placement yet but with the proper attribution. 

:::{figure} ./img/monsters/GreatLakeMonsters.jpeg
:width: 80%
:::

#### Map with optimized label placement

A nicer map with optimal label placement by Dr. Michelle Tobias, who also designed this exercise. :)

:::{figure} ./img/monsters/FinishedMap.png
:width: 80%
:::

## Resources

Here are some reasources to help you refine your maps:

* [Inkscape](http://inkscape.org/) - I use this program for fixing fine details.  It's a free and open source vector illustrator program so it is similar, but not the same as Adobe Illustrator.  Export a .svg file from the QGIS print composer and open it in Inkscape to edit things like labels with super fine control.

* [QGIS Training Manual for Map Composer](https://docs.qgis.org/3.10/en/docs/training_manual/map_composer/index.html)

* [USGS Topographic Symbols](https://pubs.usgs.gov/gip/TopographicMapSymbols/topomapsymbols.pdf?utm_source=twitter&utm_medium=social&utm_term=61da4941-22fe-4c68-80b1-b4d070f25f17&utm_content=&utm_campaign=usgs)

