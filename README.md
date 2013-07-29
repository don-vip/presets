# JOSM presets for Camp mapping

This preset can be used to map a refugee camp in Open Street Map. 

The presets have been organised to match sectors as known by humanitarian workers. 

Note that ``` addr:postcode ``` is used to register the Addressing systems as used in UNHCR registration database. This will facilitate export and join with aggregated refugee profile information.

Administrative levels within the camp are recorded at 2 levels:

For level 1 (Camp sectors or modules)
``` 
                <key key="place" value="suburb"/>
                <key key="admin_level" value="8"/>
                <key key="boundary" value="administrative"/>
                <key key="refugee" value="yes"/>
``` 
For level 2 (Camp blocks or communities)
``` 
                <key key="place" value="neighbourhood"/>
                <key key="admin_level" value="9"/>
                <key key="boundary" value="administrative"/>
                <key key="refugee" value="yes"/>
``` 

![ScreenShot](https://github.com/unhcr/presets/blob/master/screenshot.png)


# JOSM (OSM editor) basic editing guide


## 1: Create an account
OpenStreetMap.org: https://www.openstreetmap.org/user/new
Note: you will need to provide a working email address to activate your account. 
Identify the organisation you are working with in your user name this will facilitate further audit trail.


## 2: Download and run JOSM windows installer
Download link: http://josm.openstreetmap.de/download/windows/josm-setup.exe
Save this file on your desktop, and run the installer.
It should put JOSM in your start menu list of programs and open JOSM when finished installing.
If JOSM is not able to start you may need to download Java Runtime Environment (free) from: http://java.com


## 3: Setup JOSM 

Username
Open Edit -> Preferences and select Connection Settings (2nd icon from top).
Enter your username and password 

Set JOSM to Geographic Coordinates and WGS 84 
Open Edit -> Preferences and select Map setting (Grid Icon, 3rd icon from top). 
Select the Map Projection tab.
Set the “Display Coordinates” to Decimal Degrees 
Set the “Projection Method” to WGS 84 Geographic 

Install Plugins 
Open Edit -> Preferences and select Configure available plug ins (Outlet icon) 
Click on the Download List button and choose: 
	* Walking Papers (walkingpapers)
 	* WMS (wmsplugin)
Click Okay and the plugins should download (Note: okay button may be hidden at bottom of screen)
Restart JOSM 

Load the camp mapping presets 
Open Edit -> Preferences and select Map setting 
Select the Tagging Presets tab and Click NEW 
	* LAUNCH the file chooser to select a Preset file (XML)  
	* Navigate to the camp mapping Presets File in your file system
	* Click OK and Close preferences.
	* Restart JOSM See work-around in annex in case of problems

Optional: Start JOSM with more memory
This may be needed if you want to edit large OSM files
Command prompt for JOSM installed using windows installer:
	* Open a command prompt by going to the start menu and typing 'cmd' in the search/run window
	* Paste one of these commands:
		On a 32 bit machine: java -jar -Xmx512M "C:/Program Files/JOSM/josm-tested.jar"
		On a 64 bit machine (HOT Laptop): java -jar -Xmx512M "C:/Program Files (x86)/JOSM/josm-tested.jar"

Note: Removing the preferences file if JOSM has errors
If JOSM ever experiences an error when starting up it may be necessary to delete your preferences file
This will require re-doing the steps from above
To delete the preferences file:
Open an explorer window and type %APPDATA% in the location bar and press enter.
You should find a folder called JOSM. Alternatively, try to search for the term JOSM or browse the usual folders, that contain program settings.
 
## 4: Working with real OSM features in JOSM

### 4-1: Download, explore and change the visual display of OSM raw data

Download  editable OSM data
Click the download button to download actual OSM raw editable data. 
Zoom out with the scroll wheel and browse around the world until you find Haiti
Point mouse pointer where you wish to zoom
Right click to drag map
Try selecting the magnifying glass tool from left bar to zoom to a box
Choose a little piece of data relevant to your Haiti Area Of Interest (AOI) or somewhere else. You should not load more than ~ 1 square km. 

Explore the Data 
Zoom into a few downloaded map features like a road or building footprint 
Left click to select a feature and make it active 
Notice the information panels that show the attributes (properties) and geometries (nodes,ways,relations) 
Notice for building footprints and roads that you can both highlight the line/polygon and its individual nodes 
Try selecting and dragging a node.
    * Don’t worry you can move it and then select Edit > Undo (ctrl-z)
Click the Show Authors button (5th from bottom), and then select different map features to see who was the person to last edit the feature. 
Turn off any background layers (right-click add/hide) 

Optional: Customize the visual display of features 
Change the color of layers in the table of layers
Enhance the look of lines and text by choosing Edit > Preferences > Display Settings (first icon)
Click the “OSM Data” tab and check the box for “smooth map graphics”
Try clicking View > Wireframe View to have a more stark coloring 

### 4-2: Load surveyed data with GPS, Walking paper and imagery in JOSM to support your editing

Loading GPX data
    * OSM can leverage the GPX format (XML-based GPS Exchange Format) by providing an easy system for uploading and publishing GPS traces that can then be traced from (OSM encourages tracing in order to clean up GPS data). GPX is a common format of data coming from GPS units, storing coordinate data (waypoints, tracks, and routes) and is supported by many GPS data processing tools. GPS Babel can be used as a GPS data format translator (http://www.gpsbabel.org/)
    * Click File Open a file and navigate to the GPX files resulting from your GPS surveys.
    * Contribute GPX files (tracks and points) to OSM.
    ** From JOSM this requires installing the “DirectUpload” plugin
    ** You can also upload GPX data directly to the OpenStreetMap.org site 

Loading field papers
    * Create an atlas fitting your area of interest on the field paper web site (http://fieldpapers.org/). 
    * Survey with the paper map (annotation, correcting mistakes, drawing new features). 
    * Scan and upload the annotated map on the field paper web site  
    * In JOSM, walking paper Menu and copy/ paste the URL produced by the WP web site at the end of the upload process

Loading imagery for tracing or quality control of GPX based edits
Open Edit -> preferences and select WMS Plugin Preferences

    *  Upper windows lists the WMS resources activated in JOSM
    *  Lower window lists easy activable WMS resources for JOSM
    *  Check details of the best available imagery for tracing in Haiti on the Imagery section of the WikiProject Haiti:
    *  http://wiki.openstreetmap.org/wiki/WikiProject_Haiti/Imagery_and_data_sources
    *  Hit the ADD button and copy/ paste the Name and URL of a WMS resource to your AOI 

The WMS resources is now active in your editing session 
JOSM -> WMS -> newly added WMS resources to have it as a background support image 
    * It can be used for tracing
    * When the geometric accuracy of the WMS is greater than the GPS, the WMS can be used to run quality control of the edits in conjunction with Walking Papers
Optional: Custom Tile urls can also be added using the SlippyMap plugin, see:
    * http://wiki.openstreetmap.org/wiki/JOSM/Plugins/SlippyMap#Custom_tile_URLS

Issue with automatic proxy configuration may hapen. The way we fixed this can be:

 1.  Go to ```  http://wpad/wpad.dat ```  on the computer
 2.  Open the resulting wpad.dat file in a text editor
 3.  Read the proxy setting out of the file
 4.  Open JOSM
 5.  Go to Preferences
 6.  Go to Connection settings
 7.  Go to Proxy settings Tab
 8.  Change to "manually configure a HTTP proxy
 9.  Enter proxy settings from wpad.dat file
   

### 4-3: Focused editing of OSM data

Modifying existing attributes of features:  
Attribution of features in OSM is based on a tag structure composed of a key (Highway) and its associated values (primary, secondary, tertiary).
To modify an attribute of an OSM feature:
*  select the line feature, see on the right panel the key and value of the tag you want to edit
*  double-click the row or hit the edit button and change to an appropriate value 

Adding attributes to existing features 
Click the “Add” button to enter the key and its associated value of the tag to be created
*  In the pop-up type the key of your tag which should appear in the pick list (note, all keys should be lowercase)
*  Then press tab to move to the value field and type the actual name of the feature

Adding attributes to existing features using the Presets  
From the Preset menu, navigate to the relevant preset and in the associated pop up key in values or select values from drop down menus and apply.  

Modifying the geometry of existing feature 
Changing Position:
*  You may want to adjust the position of point (a water point), area (a camp) or line
*  To do this simply select & drag the feature.
Splitting a linear feature:
*  Suppose you have a road selected and it extends for a long distance over which the name changes.
*  If you want to add two names this may require “splitting the way”.
*  To do this select one of the nodes in the way, then choose Tools > Split Way 

Creating new point/ line/ area features 
Hit the Draw Node tool from the tool box (2nd tool from the top)  
* To create a point: double click a point at the relevant location. 
* To create a line: draw the line, creating intermediary points (nodes); double click at the end of the segment to be created to complete the process. 
* To create a polygon (area): draw the line, creating intermediary points (nodes); double click at the end of the polygone to be created to complete the process. 
Add attributes to the created geometries repeating the steps of the adding new attributes section.

## 5: OSM support resources 

Generic OSM support resources.
* OSM Beginner's Guide
http://wiki.openstreetmap.org/wiki/Beginners%27_Guide
* Map Making Overview
http://wiki.openstreetmap.org/wiki/Map_Making_Overview
* JOSM Introduction
http://wiki.openstreetmap.org/wiki/Josm
* Potlatch Introduction
http://wiki.openstreetmap.org/wiki/Potlatch
* Potlatch Getting Started video
http://www.youtube.com/watch?v=Oio1jY8WNig
* Editing Roads in Potlatch
http://www.youtube.com/watch?v=D6pBBK1SHh0
* Editing Camp in Potlatch
http://www.youtube.com/watch?v=Oio1jY8WNig
* Using presets in Potlatch
http://www.youtube.com/watch?v=YAnt2RSaEEA&fmt=18

#  Create a large ready-to-print city map

MapOSMatic is a web application to generate maps of cities or towns, including index of streets, from OpenStreetMap data.
Such map can be used for notice board within the camp
Access the servcie here: http://www.maposmatic.org/
