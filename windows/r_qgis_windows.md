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

5.  Now let's try the *Create new R script* tool, which opens an editor.  We can go to our sample script and view the [raw content]() 






