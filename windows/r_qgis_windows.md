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

15.  







