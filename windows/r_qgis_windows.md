## Data Fest 2018   

### QGIS Processing with R Scripts

#### Windows Version

[Data and Instructions](https://projects.iq.harvard.edu/datafest2018/schedule)

Instructor:  [Lex Berman](http://www.iq.harvard.edu/people/lex-berman)

**Overview:  This session will introduce setup and use of R within QGIS.**

*NOTE:*  the instructions will be for WINDOWS machines.   On Mac OSX, R can be used **alongside** QGIS, but fails to run within the QGIS Processing scripts (from El Capitan on).

**Software:**  

QGIS: Version 2.18.15 [www.qgis.org](http://www.qgis.org)

SAGA:  Version Included with QGIS

R: Version 3.4.3  [cran-r](https://cran.r-project.org/)

RStudio: 1.1.383 [rstudio](https://www.rstudio.com/)

### setup options

1.  Install the software listed above

2.  Open RStudio to verify that the R installation is working

3.  Open QGIS Desktop 2.18

4.  Under the main menu: Processing > Options > Providers > R

5.  Note path of "R folder"  and verify this is correct on your system

6.  Make sure the Activate box is CHECKED for R

7.  Click OK for the options settings

8.  Note warnings, such as "Wrong Parameter for MSYS folder"

9.  In the settings for Processing > Options > Providers > GRASS commands  (not GRASS GIS 7 commands)  delete any paths under the *Msys folder, GRASS folder, Location of GRASS docs* options.  Make sure the GRASS Commands Activate box is UNCHECKED, then hit OK

10.  If you do not receive warnings, we are ready to test R!

### processing toolbox

1.  Open the main menu item Processing > Toolbox

2.  In the Toolbox Panel, expand the R Scripts > Tools menu tree,  you should see items for *Create new R script* and *Get R Scripts from on-line*...

3.  click on  *Get R Scripts from on-line* then *Not installed* tree.  You should see many functions and scripts that you can simply check to add to your R scripts locally.  For example, lets CHECK *Scatterplot types* and OK

4.  now you should have a new branch under R Scripts > Tools  called *Vector Processing* and under this branch you will find the function *Scatterplot types*.  If you right-click on a tool, you have opttions to EDIT, EXECUTE and DELETE the script.

5.  Now let's try the *Create new R script* tool, which opens an editor. 

6.  Go to our sample script and view the [raw content](https://github.com/vajlex/R_with_QGIS/blob/master/r_script/bird_data.rsx) then COPY the script and PASTE it into the QGIS R Script Editor

7.  Click Save As and note that the default folder is the location that is currently defined under Processing > Options > Providers > R > R User Library Folder.  give your script a filename, such as *test_script* and hit SAVE

8.  If you CLOSE the Script Editor, you will now see a new branch in the Toolbox under R Scripts called "User R Scripts" and this should contain your "test_script"

9.  Right click on the *test_script* tool and you can EDIT, EXECUTE or DELETE.  We will click on EDIT to examine the script.

10. Note that the first line in the script calls the library "data.table" and we have not INSTALLED that library in our local R instance.   Therefore we should keep in mind that you must first install any dependencies and libraries in R (or RStudio) BEFORE attempting to run the R Script in QGIS.   QGIS does not have the ability to install libraries, so we will first launch RStudio.

11.  In RStudio console, run 

    test.data.table  
    
In a fresh install, you will probably get "Error:  object 'test.data.table' not found

12.  In RStudio console, run 

    install.packages("data.table")

13.  Then run

    require(data.table)
    test.data.table
    
Now you should get some output about the data.table package

14.  Having installed our main package, return to QGIS R Script Editor.  the next issue to sort out is the location and path to our data file.   IN the sample script, the command is to set the working directory here:

    wd <- "C:/R_TEMP/data"
    
Therefore, the easiest way to proceed is to create the folder at the root of C: drive called R_TEMP and move our data folder there.  At this point you should simply grab the complete .zip archive to download from github repo, [R_with_QGIS](https://github.com/vajlex/R_with_QGIS).   Once you have the .zip uncompressed, move the "data" folder to R_TEMP.  Then the path to your data should exist.

15.  Review the test_script to understand the functions that we will run in R, then note that the final line is to write the manipulated and selected data into a new .txt file.   

16.  While in the script editor, click on the gear button to EXECUTE the script.  A console window will open.  Click RUN on the lower right to execute.   The progress of the algorithm will be noted on the console.  After running, the window will close.  Go to the working directory to see if the designated output file *fixed_birds* has been generated.

17.  If you find the *fixed_birds_data* file with content, then R has successfully run within QGIS!


### Bringing R analytical results into QGIS

1.  Now that we have generated a new .txt file using R, let's add the file to QGIS with the https://github.com/vajlex/R_with_QGIS

2.  Use the Add Delimited Text Layer button and browse to the *fixed_birds_data.txt* file.  Set the File Format to CUSTOM DELIMITERS.   Click COMMA, then TAB, then SPACE, until you find the delimiter that correctly separates the content into columns (as shown in the live PREVIEW at the bottom of the form).  In our case, it should be SPACE that correctly delimits the content. 

3.  Make sure the box for *First record has field names* is checked

3.  Next we must make sure that the correct fields have been used for the X Field and Y Field values.  In this case, QGIS has guessed that X Field = "LONGITUDE"  and Y Field = "LATITUDE".  Take a visual look at the data in the PREVIEW area to see if this looks correct.  Those values should be numbers in decimal degrees.

4.  Now we can hit OK and we will be prompted to specify the Coordinate Reference System (CRS) or Projection definition.  We can accept the default global projection in decimal degrees:  WGS 84.  Then hit OK and the data should be imported as points into QGIS

5.  In the LAYERS PANEL, right click on the layer we have imported, called "fixed_birds_data"  then ZOOM TO LAYER.   The Map View will recenter on the extent containing all the imported data.   Note that our original R Script (which eliminated any data with the STATE VALUE of OHIO) has worked properly in filtering the data, and putting the x, y values in the proper fields.

6.  In order to run further spatial analysis tasks on our data, right click on the layer *fixed_birds_data*  and SAVE AS a new ESRI SHAPEFILE, for example:   C:\R_TEMP\shape\fixed_birds.shp

7.  The new Shapefile layer will be added to the QGIS project.   Right-click on the original fixed_birds_data.txt layer and REMOVE it from the project.  Now we have brought our working data into QGIS and left the original R analysis .txt file untouched.

### Spatial Analysis in QGIS

1.  There are many geoalgorithms and cartographic tools available in QGIS.  For this case, we will just use a quick Selection and Heatmap to show you some of the potential.

2. 







