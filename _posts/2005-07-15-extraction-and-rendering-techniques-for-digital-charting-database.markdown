---

title: Extraction and rendering techniques for digital charting database
abstract: Disclosed is a method for extracting and rendering data from digital charting databases. The software method integrates and combines bathymetric/topographic data from several sources into a stream of three-dimensional data points, creating a triangle surface mesh, and dividing it into pieces along arbitrary lines to create regularly sized and shaped areas for efficient storing and rendering. The method works by forming an initial triangle mesh of the area and then refining the mesh by incrementally adding each point to the mesh, until a full mesh representation is achieved. The large single file is then broken down into discrete geographic regions, and the region data is converted into a standard file format for viewing and/or processing.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07463258&OS=07463258&RS=07463258
owner: The United States of America as represented by the Secretary of the Navy
number: 07463258
owner_city: Washington
owner_country: US
publication_date: 20050715
---
The invention described herein may be manufactured and used by or for the Government of the United States of America for governmental purposes without the payment of any royalties thereon or therefor.

The present invention relates to a general purpose methodology for extracting and rendering data from digital charting databases and more particularly to a method for integrating and combining bathymetric topographic data from several sources operating on ordinary desktop personal computers.

A necessary prerequisite to display a 3 dimensional 3 D tactical picture is the ability to access bottom terrain data and render those data in real time. For example any submarine based tactical system must access information from the submarine s combat control system CCS databases. An onboard bathymetry database used in support of the Common Tactical Picture CTP is the NIMA product Digital Nautical Chart DNC . The DNC is an unclassified vector based digital database containing maritime features essential for safe marine navigation. The database consists of a portfolio of approximately 5000 nautical charts that provide global marine navigation between 84 North latitude and 81 South latitude and supports a variety of Geographic Information System GIS applications. NIMA has produced the DNC to support worldwide navigation requirements of the U.S. Navy and U.S. Coast Guard.

In addition to bathymetry the DNC database contains nautical features consisting of points lines and polygons. These features have been collected individually and assembled to support its use by GIS and other scientific applications.

The size of both modeled and measured data in the DNC database presents a challenge to computer s ability to extract the data and visualize it at interactive speed. Older methods of visualization relied on heavy post processing of the data into image files that could be played back as movies or plotted and studied for future use. These methods were slow and failed to fully exploit the information value of the data. There are varied efforts underway to progress toward interactive visualization. For example tools exist for comparing multivariate data sets to imagery data sets in both geographic and multivariate feature space. An example tool supports various input data formats allows visualization in three data spaces active querying with text output in two data spaces selection of areas and manual classification in two data spaces. Still graphics systems of mid end workstations often cannot render the geometry fast enough to be interactive.

U.S. Pat. No. 6 515 663 to Hung et al. describes a method and apparatus for the efficient rendering of a three dimensional object on a flat screen in stereo 3 D such that the left and right eyes can view two different images i.e. the same object from slightly different viewpoints making the image appear to extend out of the screen and into real three dimensional space.

U.S. Pat. No. 6 556 194 to Shiono describes a method of combining partial descriptions of a three dimensional object obtained from different perspectives and merging that data into a single complete description of that object valid from all perspectives. The method defines shape vectors using ranges and directions from the surface points. The various sets of shape vectors from differing perspectives are then merged through vector arithmetic yielding a single unified shape vector description of the object.

U.S. Pat. No. 6 563 500 to Kim et al describes a method and apparatus for the efficient coding and decoding of a 3 D triangle mesh dataset for the purpose of transmission. The method attempts to speed transmission by coding to allow the receiving end to begin mesh reconstruction before the entire dataset is received and also allowing partial reconstruction even if there is lost data. The method basically consists of taking a complete 3 D mesh dataset splitting it into chunks encoding it sending it receiving it decoding it and recombining it. The mesh is split along natural fault lines as opposed to arbitrary division lines chosen to make the pieces regular in size and shape.

U.S. Pat. No. 6 606 089 to Margadant describes a method of visualizing spatially resolved data by means of a superposition of texture maps. The method involves taking sampled three dimensional data loading it as texture maps a two dimensional surface that is wrapped around a three dimensional object giving the 3 D object a surface texture similar to that of the 2 D surface analogous to applying wallpaper paint or veneer to a real object and then allowing the graphics rendering hardware to superpose these maps to rapidly create a pictorial representation of the data . The method avoids rendering a complete mesh description of the object and instead rapidly generates pictures of the data.

None of the foregoing approaches are well suited for DNC data which requires direct read software that provides for display without data manipulation. The present invention finds that direct read is possible by extraction of all information including both navigational and bathymetric information generated from the DNC database and generating a three dimensional triangle mesh description of sampled data. The present system as will be disclosed integrates and combines bathymetric topographic data from several sources operating on ordinary desktop personal computers saving development time and associated expenses in addition to providing for widespread portability.

It is therefore a primary object of the present invention to provide a method for integrating and combining bathymetric topographic data from several sources operating on ordinary desktop personal computers.

It is a further object of the present invention to provide a methodology for integrating and overlapping bathymetry topographic data points into a regularly sized rendering tile in which the data points are not overlapping but are accurately representing the sampling density of the extracted data points.

It is a still further object of the present invention to provide a method for extracting and rendering data from digital charting databases as described above by constructing a library that can easily be modified to accommodate other data sets both in situ and archival.

It is a still further object of the present invention to provide a method as described above which is capable of use by the general public as well as the military because it is designed to work with both classified and unclassified bathymetric topographic databases for oceanography terrain mapping and even mapping of extraterrestrial bodies etc.

These and other objects of the present invention are accomplished by a method for extracting and rendering data from digital charting databases. The method is preferably implemented in software form generally by integrating and combining bathymetric topographic data from several sources into a stream of three dimensional data points creating a triangle surface mesh and dividing it into pieces along arbitrary lines to create regularly sized and shaped areas for efficient storing and rendering. The method works by forming an initial triangle mesh of the area and then refining the mesh by incrementally adding each point to the mesh until a full mesh representation is achieved. The large single mesh is then broken down into discrete geographic regions and the region data is converted into a standard file format for viewing and or processing.

The present invention is a method for extracting and rendering data from digital charting databases. The method is readily implemented in software form for use on a conventional computer workstation with an appropriate operating system. The computer workstation may be for example a conventional personal computer with standard internal components e.g. a microprocessor with peripheral chipset mounted on an appropriate motherboard . Of course other more or less powerful computer systems can be used but it is suggested that the computer system meet the minimum system requirements for intense video applications such as gaming. The user interface is preferably a conventional color monitor and standard input devices such as a keyboard and mouse. The operating system is preferably LINUX 9.0 based or another operating adaptive and known to those skilled in the art. The software of the present invention may be compressed onto one or more installation disks and may be loaded onto a computer system as described above using conventional installation macros such as those provided with the aforementioned operating systems.

At step the data from DATA..N is combined into a single stream of three dimensional data points. This entails combining the data points and sorting all points by the x or y coordinate.

At step the combined and sorted data from DATA.N is connected in triangles forming an initial triangle mesh of the area. This artificial starting mesh comprises a single triangle that completely bounds the input data. The triangle mesh is refined by incrementally adding each streaming point from step to the mesh until a full mesh representation is achieved. Next at step the large file data is rendered into chunks e.g. broken down into geographic regions of a predetermined fixed size.

Finally at step the rendered data is converted to a standard file format such as Open Inventor or other known format for visualization.

The software imports three dimensional coordinate data from one or multiple sources including the DNC database and others. Consequently the collective data can have gaps and overlaps. More data provides additional detail.

The data from multiple sources is converted to x y and z coordinate data and is combined into one large file for processing.

The combined single file data is connected into a triangle mesh surface in order to make an artificial starting mesh consisting of a single triangle that completely bounds the input data. This can be done using the following algorithm 

1st. The combined data is sorted by the coordinates of the largest dimension x y or z so that triangles can be created along a moving front. illustrates a combined datafile in which the largest dimension is X. This data would be sorted along the X axis which reduces the number of calculations. For the purposes of this function the Y and Z dimensions are ignored.

2nd. Calculate an encompassing triangle by creating virtual vertices A B and C as shown in . An exemplary set of code for performing this function may be written in Borland Turbo C and is provided as follows 

4th. Beginning with point and for each point moving inward along X perform the following substeps. Remove triangles from consideration if the point s X coordinate is greater than the sum of the x coordinate of the center of the triangle s circumcircle the radius of the circumcircle. The circumcircle is a triangle s circumscribed circle i.e. the unique circle that passes through each of the triangles three virtual vertices A B and C. The center of the circumcircle is called the circumcenter and the circle s radius R is called the circumradius.

b. Make a list of triangles which include the point . These would be the triangle with vertices A B and C in .

c. Make list of triangles whose circumcircle includes point but do not contain point themselves these triangles will be used in step f . No triangle meets this criteria.

e. Construct new triangles by drawing lines between the point and the vertices of the removed triangles. shows this in the basic case.

f. Tentatively remove all bordering triangles whose circumcircles include the point the triangles found in step c .

h. Test for overlap of the newly created triangles by seeing if the constructed line crosses a previously drawn line.

5th. Move on to the next point point . and show the continuation of this process. Upon completion of the process is obtained.

6th. Remove all triangles joined to virtual points e.g. A B and C . From points A B and C are removed along with all connecting lines resulting in .

Creation of the triangular mesh per steps above creates a large file that must be broken down into geographic region. This is accomplished with the following substeps.

The files are then converted into a standard file format. For the uses of this invention the standard format is OPEN INVENTOR or comparable system known to those skilled in the art an object oriented 3 D toolkit offering a comprehensive solution to interactive graphics programming problems. The format presents a programming model based on a 3 D scene database that simplifies graphics programming.

The above described method for integrating and combining bathymetric topographic data from several sources into a regularly sized rendering tile in which the data points are not overlapping but are accurately representing the sampling density of the extracted data points constructs a library that can easily be modified to accommodate other data sets both in situ and archival. The method works with both classified and unclassified bathymetric topographic databases for oceanography terrain mapping and even mapping of extraterrestrial bodies etc.

Having now fully set forth the preferred embodiment and certain modifications of the concept underlying the present invention various other embodiments as well as certain variations and modifications of the embodiments herein shown and described will obviously occur to those skilled in the art upon becoming familiar with said underlying concept. It is to be understood therefore that the invention may be practiced otherwise than as specifically set forth in the appended claims.

