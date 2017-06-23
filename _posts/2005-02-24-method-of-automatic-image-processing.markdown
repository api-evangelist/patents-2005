---

title: Method of automatic image processing
abstract: Method is disclosed for the automatic creation of images in a “van Gogh” style. The method comprises locating portions of detail in an image an utilising the areas of detail to propagate brush strokes into areas of the image having lesser details. A number of modifications are also proposed including utilising refining brush strokes to process those areas of detail in an image.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07295211&OS=07295211&RS=07295211
owner: Silverbrook Research Pty Ltd
number: 07295211
owner_city: Balmain, New South Wales
owner_country: AU
publication_date: 20050224
---
The present application is a continuation of U.S. application Ser. No. 09 112 777 filed on Jul. 10 1998 now U.S. Pat. No. 6 894 694 the entire contents of which are herein incorporated by reference.

The following Australian provisional patent applications are hereby incorporated by reference. For the purposes of location and identification U.S. patents patent applications identified by their U.S. patent patent application Ser. Nos. are listed alongside the Australian applications from which the U.S. patents patent applications claim the right of priority.

The present invention relates to an image processing method and apparatus and in particular discloses producing automatic painting effects in images.

The present invention further relates to the field of image processing and in particular to producing artistic effects in images.

Recently it has become quite popular to provide filters which produce effects on images similar to popular artistic painting styles. These filters are designed to take an image and produce a resultant secondary image which appears to be an artistic rendition of the primary image in one of the artistic styles.

One extremely popular artist in modern times was Vincent van Gogh. It is a characteristic of art works produced by this artist that the direction of brush strokes in flat areas of his paintings strongly follow the direction of edges of dominant features in the painting. For example his works entitled Road with Cypress and Star Starry Night and Portrait of Doctor Gachet are illustrative examples of this process.

It would be desirable to provide a computer algorithm which can automatically produce a van Gogh effect on an arbitrary input image.

In accordance with the first aspect of the present invention there is provided a method of automatically processing an image comprising the steps of 

locating within the image features having a high spatial variance by thresholding and skeletonising the filtered image to produce an image comprising single pixel width definition of features 

stroking the image with a series of brush strokes emanating from remaining features of the produced image in accordance with the fitted curves.

Similarly there is provided a method of automatically processing an image comprising locating within the image features having a high spatial variance and stroking the image with a series of brush strokes emanating from those areas having high spatial variance.

Preferably the step of thresholding is performed by using a threshold value of 50 of the maximum intensity value.

The preferred embodiment is preferable implemented through suitable programming of a hand held camera device such as that described in Australian Provisional Patent Application entitled Image Processing Method and Apparatus ART01 filed concurrently herewith by the present applicant the content of which is hereby specifically incorporated by cross reference.

The aforementioned patent specification discloses a camera system hereinafter known as an Artcam type camera wherein sensed images can be directly printed out by an Artcam portable camera unit. Further the aforementioned specification discloses means and methods for performing various manipulations on images captured by the camera sensing device leading to the production of various effects in any output image. The manipulations are disclosed to be highly flexible in nature and can be implemented through the insertion into the Artcam of cards having encoded thereon various instructions for the manipulation of images the cards hereinafter being known as Artcards. The Artcam further has significant onboard processing power by an Artcam Central Processor unit ACP which is interconnected to a memory device for the storage of important data and images.

In the preferred embodiment there is described an algorithm which will automatically convert a photographic image into a painted rendition of that image which replaces groups of pixels in the input image with brush strokes in the output image. The algorithm works by automatically detecting dominant edges and propagating the edge direction information into flat areas of the image so that brush strokes can be oriented in such a way as to approximate the van Gogh style. The algorithm is suitable for implementation on the aforementioned Artcam device.

Turning initially to the algorithm comprises a number of steps . These steps include an initial step of filtering the image to detect its edges . Next the edges are thresholded or skeletonised before being processed to determine the final edges . B zier curves are then fitted to the edges. Next the curves are offset and brush strokes are placed on final image . The process and is iterated until such time as the image is substantially covered by brush strokes. Subsequently final touching up of the image is performed.

Turning now to describe each step in more detail. In the first step of filtering to detect edges a Sobel 3 3 filter having co efficient sets and as illustrated in can be applied to the image. The Sobel filter is a well known filter utilised in digital image processing and its properties are fully discussed in the standard text Digital Image Processing by Gonzalez and Woods published 1992 by the Addison Wesley publishing company of Reading Mass. at pages 197 201. The Sobel derivative filter can be applied by either converting the image to greyscale before filtering or filtering each of the colour channels of an image separately and taking the maximum. The result of Sobel filtering is the production of a greyscale image indicating the per pixel edge strength of the image.

Next the resultant per pixel edge strength image is thresholded so as to produce a corresponding thresholded binary image. The threshold value can be varied however a value of 50 of the maximum intensity value is suitable. For each pixel in the edge strength image the pixel is compared with the threshold and if it is greater than the threshold a one is output and if it is less than the threshold a zero is output. The result of this process is to produce a threshold edge map.

Next the thresholded edge map is skeletonised at step of . The process for skeletonising an image is fully set out in the aforementioned reference text at pages 491 494 and in other standard texts. The process of skeletonisation produces a thinned skeletonised edge map maintaining a substantial number of characteristics of the thresholded edge map.

In a next step the edges of the skeletonised edge map are determined to yield a data structure which comprises a list of further lists of points within the image. Preferably only edges having a length greater than a predetermined minimum are retained in the list.

As the skeletonised image contains only single pixel width edges possibly with multiple branches the following algorithm expressed as a C code fragment sets out one method of determining or identifying the points which belong to each contiguous edge in the skeletonised image. It breaks branching edges into separate edges and chooses to continue along the edge in the direction which minimises the curvature of each branch ie. at a branch point it favours following the branch which induces the least curvature. The code is as follows 

The result of utilising this algorithmic component on the skeletonised edgemap is to produce a list of edges having at least a predetermined size. A suitable size was found to be a length of 20 pixel elements.

In the next step of B zier curves are fitted to each of the edge lists derived from step . For each list of edges a piece wise B zier curve is fitted to the corresponding list of points. A suitable algorithm for fitting the piece wise B zier curve is Schneider s curve fitting algorithm as set out in Schneider P. J. An Algorithm for Automatically Fitting Digitised Curves in Glassner A. S. Ed. Graphics Gems Academic Press 1990. This algorithm provides quick convergence to a good fit which aims only for geometric continuity and not parametric continuity. Schneider s algorithm is recursive such that if the fit is poor is sub divides the curve at the point of maximum error and fits the curves to the two halves separately. Next an estimate of the tangent at the split point is derived using only the two points on either side of the split point. For dense point sets this tends to amplify the local noise. An improved quality of curve fitting can be alternatively undertaken by using points further away from the split point as the basis for the tangent.

In the next steps of the curves are offset from the primary curve list by half a desired brush stroke width . The offsetting occurring on both sides of the primary curve list with the result being two curves approximately one stroke width apart from one another which run parallel to and on either side of the original primary curve.

The following algorithm is utilized to generate a piece wise B zier curves which are approximately parallel to a specified piece wise B zier curves and includes the steps.

iii. Evaluate selected points on each curve segment making up the piece wise curve and offset them by the specified offset value. Append the offset points to the point list and their corresponding tangents to the tangent list. This process is described below with reference to and

iv. Fit a piece wise B zier curve to the resultant point list. Rather than estimating tangents during the curve fitting process use the exact tangents associated with the offset points. Offset each curve segment as follows 

i. Evaluate the curve value normalised tangent and normalised normal normalised to the size of the image for a set of evenly spaced parameter value between and including 0.0 and 1.0 eg. a spacing of 0.25 .

v. Append the surviving points to the point list and append their corresponding tangents to the tangent list. Only append the point associated with parameter value 1.0 if the segment in question is the last in the piece wise curve otherwise it will duplicate the point associated with parameter value 0.0 of the next segment.

1. Firstly for a set of evenly spaced parameter values on the B zier curve between and including 0.0 and 1.0 for each parameter value Pn the curve value a normalised tangent and normalised normal are calculated.

3. Next a line segment from the point to a point which is at the end of the scaled normal is calculated.

4. Next the line segment is checked against corresponding line segments for all other points on the curve eg. . If any two line segments intersect one of the points is discarded.

5. The surviving points are appended to the point list and their corresponding tangents are appended to the tangent list. The point associated with the parameter value 1.0 is appended only if the segment in question is the last in the piece wise curve segment. Otherwise it will duplicate the point associated with the parameter value 0.0 of the next segment.

Turning to the end result of the offset of curves in accordance with step of is to produce for a series of B zier curve segments C C etc. Firstly a series of parametrically spaced points P P. Next the normalisation points N N are produced corresponding through to point of for each of the points P P. Next the resultant piece wise B zier curve segment is produced by utilising the points in N N. This process is then repeated for the opposite curve comprising the points N N and curve . This process is then repeated for each of the subsequent piece wise curves C etc. The result is the two curves of being substantially parallel to one another and having a spaced apart width of approximately one brush stroke.

Next a series of brush strokes are placed into the output image along the curves. The strokes are oriented in accordance with the curve tangent direction. Each brush stroke is defined to have a foot print which defines where it may not overlap with other brush strokes. A brush stroke may only be placed along the curve if its foot print does not conflict with the foot prints already present in the output image. Any curves that do not have any brush strokes placed along them are discarded and the process of steps and are iterated in a slightly modified form until no curves are left. The slightly modified form of step is to offset the curves by one brush stroke in the outward direction rather than the half brush stroke necessary when offsetting curves from the curve C of .

It has been found by utilisation of the above method that the result produced consists of a series of brush strokes which emanate from objects of interest within the image.

Subsequent to covering the image with brush strokes of a given size further processing steps can be undertaken with smaller and smaller brush strokes and increasing derivative threshold levels so as to more accurately brush stroke important features in the image. Such a technique is similar to that used by van Gogh in certain portions of his images where details are required.

It would be appreciated by a person skilled in the art that numerous variations and or modifications may be made to the present invention as shown in the specific embodiment without departing from the spirit or scope of the invention as broadly described. The present embodiment is therefore to be considered in all respects to be illustrative and not restrictive.

The embodiments of the invention use an ink jet printer type device. Of course many different devices could be used. However presently popular ink jet printing technologies are unlikely to be suitable.

The most significant problem with thermal ink jet is power consumption. This is approximately 100 times that required for high speed and stems from the energy inefficient means of drop ejection. This involves the rapid boiling of water to produce a vapor bubble which expels the ink. Water has a very high heat capacity and must be superheated in thermal ink jet applications. This leads to an efficiency of around 0.02 from electricity input to drop momentum and increased surface area out.

The most significant problem with piezoelectric ink jet is size and cost. Piezoelectric crystals have a very small deflection at reasonable drive voltages and therefore require a large area for each nozzle. Also each piezoelectric actuator must be connected to its drive circuit on a separate substrate. This is not a significant problem at the current limit of around 300 nozzles per printhead but is a major impediment to the fabrication of pagewidth printheads with 19 200 nozzles.

Ideally the ink jet technologies used meet the stringent requirements of in camera digital color printing and other high quality high speed low cost printing applications. To meet the requirements of digital photography new ink jet technologies have been created. The target features include 

All of these features can be met or exceeded by the ink jet systems described below with differing levels of difficulty. Forty five different ink jet technologies have been developed by the Assignee to give a wide range of choices for high volume manufacture. These technologies form part of separate applications assigned to the present Assignee as set out in the table under the heading Cross References to Related Applications.

The ink jet designs shown here are suitable for a wide range of digital printing systems from battery powered one time use digital cameras through to desktop and network printers and through to commercial printing systems.

For ease of manufacture using standard process equipment the printhead is designed to be a monolithic 0.5 micron CMOS chip with MEMS post processing. For color photographic applications the printhead is 100 mm long with a width which depends upon the ink jet type. The smallest printhead designed is IJ38 which is 0.35 mm wide giving a chip area of 35 square mm. The printheads each contain 19 200 nozzles plus data and control circuitry.

Ink is supplied to the back of the printhead by injection molded plastic ink channels. The molding requires 50 micron features which can be created using a lithographically micromachined insert in a standard injection molding tool. Ink flows through holes etched through the wafer to the nozzle chambers fabricated on the front surface of the wafer. The printhead is connected to the camera circuitry by tape automated bonding.

Eleven important characteristics of the fundamental operation of individual ink jet nozzles have been identified. These characteristics are largely orthogonal and so can be elucidated as an eleven dimensional matrix. Most of the eleven axes of this matrix include entries developed by the present assignee.

The complete eleven dimensional table represented by these axes contains 36.9 billion possible configurations of ink jet nozzle. While not all of the possible combinations result in a viable ink jet technology many million configurations are viable. It is clearly impractical to elucidate all of the possible configurations. Instead certain ink jet types have been investigated in detail. These are designated IJ01 to IJ45 above which matches the docket numbers in the table under the heading Cross References to Related Applications.

Other ink jet configurations can readily be derived from these forty five examples by substituting alternative configurations along one or more of the 11 axes. Most of the IJ01 to IJ45 examples can be made into ink jet print heads printheads with characteristics superior to any currently available ink jet technology.

Where there are prior art examples known to the inventor one or more of these examples are listed in the examples column of the tables below. The IJ01 to IJ45 series are also listed in the examples column. In some cases print technology may be listed more than once in a table where it shares characteristics with more than one entry.

Suitable applications for the ink jet technologies include Home printers Office network printers Short run digital printers Commercial print systems Fabric printers Pocket printers Internet WWW printers Video printers Medical imaging Wide format printers Notebook PC printers Fax machines Industrial printing systems Photocopiers Photographic minilabs etc.

The information associated with the aforementioned 11 dimensional matrix are set out in the following tables.

