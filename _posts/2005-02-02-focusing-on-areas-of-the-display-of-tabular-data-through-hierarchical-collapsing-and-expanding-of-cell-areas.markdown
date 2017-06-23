---

title: Focusing on areas of the display of tabular data through hierarchical collapsing and expanding of cell areas
abstract: A method, apparatus and program product for focusing the display of tabular data wherein the display has multiple rows and columns of cells. A computer running a tabular data application includes a display for displaying the tabular data. The tabular data application includes a routine for defining a user defined area in the tabular data display in a focused display. The routine places indicators at the top, bottom, right side and left side of the focused display. The indicators may be one of an expand indicator or a collapse indicator. A movable cursor in the tabular data display is used to select at least one of the indicators for focusing the display. The routine in the tabular data application expands or collapses the display of tabular data to give a focused display. The expanding or collapsing of the display is determined by whether the selected indicator is an expand indicator or a collapse indicator.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08296646&OS=08296646&RS=08296646
owner: International Business Machines Corporation
number: 08296646
owner_city: Armonk
owner_country: US
publication_date: 20050202
---
This invention relates to computer tabular data and more particularly related to focusing of areas of spreadsheets through hierarchical collapsing of cells.

Selected rows or columns of adjacent cells in computer tabular data such as a spreadsheet can be hidden to allow a user to reduce the amount of information that might be distracting. The prior art before the present invention is limited in its ability to allow the user to focus on arbitrary regions of data in the spreadsheet.

U.S. Pat. No. 5 255 356 issued Oct. 19 1993 to Michelman et al. for METHOD FOR HIDING AND SHOWING SPREADSHEET CELLS discloses a method for hiding and showing spreadsheet cells of a worksheet being displayed on a computer system display means.

U.S. Pat. No. 5 450 538 issued Sep. 12 1995 to Glaser et al. for GRAPHICAL USER INTERFACE CONTROL FOR EXPANSION AND RE SIZING OF DATA FIELDS IN FORMS discloses a computer interface system employing a menu graphical user interface for the entry of text data in a data store receiving user inputs for controlling the graphical user interface.

U.S. Pat. No. 5 950 168 issued Sep. 7 1999 to Simborg et al. for COLLAPSIBLE FLOWSHEET FOR DISPLAYING PATIENT INFORMATION IN AN ELECTRONIC MEDICAL RECORD discloses a user interface which presents patient data on a computer display to a health care provider as a flowsheet including an array of category labels with indications of whether the category is in a collapsed state or an expanded state.

U.S. Pat. No. 6 084 585 issued Jul. 4 2000 to Kraft et al. for SYSTEM FOR DIRECTLY ACCESSING FIELDS ON ELECTRONIC FORMS discloses a computer system which provides a graphical user interface to assist a user in completing electronic forms.

U.S. Pat. No. 6 115 759 issued Sep. 5 2000 to Sugimura et al. for SYSTEM FOR DISPLAYING DESIRED PORTIONS OF A SPREADSHEET ON A DISPLAY SCREEN BY ADJOINING THE DESIRED PORTIONS WITHOUT THE NEED FOR INCREASING THE MEMORY CAPACITY discloses a data processing apparatus having a spreadsheet data storing section for storing spreadsheet data a spreadsheet creating section for creating a spreadsheet consisting of at least one row and at least one column and a display section for displaying the spreadsheet on a screen. The data processing apparatus includes an inputting section for designating a row or a column to be subjected to a non display operation a non display controlling section for removing row or column data in the non display operation and controlling the display section to display a modified spreadsheet by moving rows or columns previously located adjacent to the removed row or column into adjoining relation.

U.S. Pat. No. 6 438 565 B1 issued Aug. 20 2002 to Ammirato et al. for SYSTEM AND METHODS FOR IMPROVED SCENARIO MANAGEMENT IN AN ELECTRONIC SPREADSHEET discloses an electronic spreadsheet including a scenario manager having a preferred interface and method for creating and managing various versions or scenarios of a spreadsheet model. Methods are provided for specifying an area of the model to track and capture various versions of the base model.

U.S. Pat. No. 6 711 715 B1 issued Mar. 23 2004 to Grealish for METHOD AND SYSTEM FOR EFFICIENT STORAGE AND RESTORATION OF DISPLAY STATE DATA discloses storage and restoration of display state data for a display object having a display state that can be altered by display state changes made to other display objects in a hierarchical data structure where the display state of the display object being stored has more than on superior display object.

U.S. Patent Application Publication Number US 2003 0188256 A1 published Oct. 2 2003 by Augeglia et al. for SYSTEM AND METHOD IN AN ELECTRONIC SPREADSHEET FOR COPYING AND POSTING DISPLAYED ELEMENTS OF A RANGE CELLS and US 2003 0188257 A1 US 2003 0188258 A1 and US 2003 188259 A1 published Oct. 2 2003 by Aureglia et al. for SYSTEM AND METHOD IN AN ELECTRONIC SPREADSHEET FOR DISPLAYING AND OR HIDING RANGE OF CELLS all disclose a method system and computer program for copying and pasting in an electronic multidimensional spreadsheet displayed elements of a source range of cells onto a destination range of cells the source range of cells including one or more elements displayed on a user interface and one or more hidden elements the elements being contiguous and aligned along a given spreadsheet dimension.

European Patent Application EP 1 256 890 A2 published Nov. 13 2002 for Vosheli for SYSTEMS AND METHODS PROVIDING DYNAMIC SPREADSHEET FUNCTIONALITY discloses a system and method for supporting and or enabling the creation of dynamic reports and or data presentations in connection with a spreadsheet based formatting and calculation capabilities. The disclosed system and method generally include an electronic spreadsheet having a plurality of cells that are arrayed in a defined number of columns and rows a database in communication with the electronic spreadsheet and an expansion formula that functions to control retrieval of data from the database and automatically varies expands at least one of the defined number of columns and rows to accommodate the data retrieval.

An article by Torres SPREADSHEET DATA VISUALIZATION Research Disclosure n334 02 92 February 1992 discusses techniques to enhance processing of spreadsheet or deficiencies including the spreadsheet to be oriented along different axes in order to see the data from different perspectives and to allow temporary hide remove add of rows and columns as well as zoom in out.

The shortcomings of the prior art are overcome and additional advantages are provided through the provision of a system to allow a user to focus on arbitrary regions of relevant data. The user hierarchically hides sections of data over arbitrary two dimension regions of the spreadsheet. This is especially useful within a large spreadsheet of numbers or images.

The present invention provides a system and method for focusing on relevant information by selectively collapsing the irrelevant cells. This may be done manually or automatically based on selection of relevant cells for exposing only the highlighted cells of interest.

The present invention provides a system and method wherein the user drags a cursor over a cell that has collapsible neighbors. The system and method further includes icons indicating the direction of collapsing. After a collapse operation is complete a visual representation allowing the user to expand the cells. These indicators may take the form of plus or minus icons directional arrows ellipsis or other graphic icons to indicate the two possible operations of collapsing and expanding regions of interest.

System and computer program products corresponding to the above summarized methods are also described and claimed herein.

Additional features and advantages are realized through the techniques of the present invention. Other embodiments and aspects of the invention are described in detail herein and are considered a part of the claimed invention. For a better understanding of the invention with advantages and features refer to the description and to the drawings.

The detailed description explains the preferred embodiments of the invention together with advantages and features by way of example with reference to the drawings.

In a simple manual two dimension collapse is illustrated. The user collapses the neighbors to the selected area first in the horizontal direction steps and and then in the vertical direction step and . In this operation and icons show when the user can expand and collapse the hidden cells. A manual two dimension collapse operation of four user actions is shown at steps and . illustrates a simple automatic two dimension collapse operation one action from step to step . The automatic two dimension collapse operation may be entered for example by accessing a menu or by a specific combination of keystrokes as desired.

It will be understood that the illustrated technique may also be used for three dimensional data such as for spreadsheets in a cube.

At the process collapses unhighlighted cells to the left top as shown at . At the process collapses unhighlighted cells to the right bottom as shown at . At a check is made to determine if any interior cells are to be collapsed. The automatic collapse of interior cells can be set as a user preference. If the check at is yes. The unhighlighted interior cells are collapsed at as shown at and ends at . If the check at is no the routine ends at as shown at .

At the routine determines the bounds of the highlighted region. At the left cells are collapsed. At the right cells are collapsed. At the top cells are collapsed. At the bottom cells are collapsed. A check is made at to determine if interior cell are to be collapsed as determined by the preferences indicated by the user. If the check at is no the routine ends at . If the check at is yes at the routine collapses the unhighlighted horizontal cells. At the routine collapses the unhighlighted vertical cells.

It will be understood that the focus module expands the display by doing an expand operation instead of a collapse operation by changing the collapse operation with an expand operation as discussed in the .

Although the embodiment disclosed is spreadsheet specific it will be understood that the invention may be used with any other tabular forms of data and is not limited to spreadsheet applications alone.

The capabilities of the present invention can be implemented in software firmware hardware or some combination thereof.

As one example one or more aspects of the present invention can be included in an article of manufacture e.g. one or more computer program products having for instance computer usable media. The media has embodied therein for instance computer readable program code means for providing and facilitating the capabilities of the present invention. The article of manufacture can be included as a part of a computer system or sold separately.

Additionally at least one program storage device readable by a machine tangibly embodying at least one program of instructions executable by the machine to perform the capabilities of the present invention can be provided.

The flow diagrams depicted herein are just examples. There may be many variations to these diagrams or the steps or operations described therein without departing from the spirit of the invention. For instance the steps may be performed in a differing order or steps may be added deleted or modified. All of these variations are considered a part of the claimed invention.

While the preferred embodiment to the invention has been described it will be understood that those skilled in the art both now and in the future may make various improvements and enhancements which fall within the scope of the claims which follow. These claims should be construed to maintain the proper protection for the invention first described.

