---

title: Scalable object recognition architecture
abstract: A method of processing received objects in a rendering system determines whether a detection scheme which already has grouped objects exits. The rendering system has a plurality of detection schemes, with each detection schemes having an associated object group type. If such a detection scheme does not exist and a previously received object has been stored, then the method determines in descending priority order whether one of the detection schemes is operative to group the received object with the previously received object. If it is determined that none of the detection schemes is operative to group the received object with the previously received object, then the previously received object is output for rendering the received object is stored. If it is determined that one of the detection schemes is operative to group the received object with the previously received object, then the received object is grouped with the previously received object.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07145578&OS=07145578&RS=07145578
owner: Canon Kabushiki Kaisha
number: 07145578
owner_city: Tokyo
owner_country: JP
publication_date: 20050303
---
The present invention relates generally to the management of objects in an object rendering system and in particular to the management of graphical object detection schemes within the object rendering system.

Rendering is a process by which graphic objects are converted to pixels. The rendering is performed by a graphics rendering system which receives the graphic objects from an application program as graphic commands. Graphics rendering systems typically use a painters algorithm style of rendering where each graphic object is drawn onto a frame buffer as the graphic object arrives. Other graphics rendering systems use a 2 stage approach where the graphics rendering system in a first stage converts all incoming graphic objects into some intermediate format for the page and in a second stage renders a scanline at a time from the intermediate format.

No matter the type of graphics rendering system efficiency problems are suffered due to the nature of some of the graphic commands received from the application programs. For example a common drawing application program passes a gradient fill to the graphics rendering system as a group of adjacent overlapping rectangles each with a slightly different flat colour thereby giving the impression of a smooth gradient fill. Although true to the nature of the original object the graphic objects are abundant with redundant data.

In an attempt to reduce the above inefficiencies it has been proposed to detect simple graphic objects that may be combined into more complex graphic objects and combining such graphic objects into object groups thereby removing redundant data and reducing the number of raster operations. An object group in this context is used to describe a group of one or more objects that may be combined to form a more efficient set of object s specific to the graphics rendering system. The combined object s may be more complex than the group of single objects but the graphics rendering system may be able to handle the object group s more efficiently. Single objects may be classified as an object group if such single objects are transformed into a format more desirable to the graphics rendering system than the format in which the objects were originally represented.

Object group detection schemes are typically used for determining whether or not the objects are able to be grouped to form a more efficient desirable set of objects. System designers specifically tailor detection schemes to detect and correct these object inefficiencies. The corrected graphic object data although most likely more complex than the original would be optimised for the specific graphics rendering system thus improving the rendering efficiency of such a system.

Each detection scheme detects and combines a different grouping of graphic objects to form a complex graphic object. Due to the fact that detection schemes often use one or more of the same objects conflict amongst detection schemes typically occurs when the rendering system includes multiple detection schemes.

It is an object of the present invention to substantially overcome or at least ameliorate one or more disadvantages of existing arrangements.

The present invention operates to eliminate the need for detection schemes of a graphics rendering system to communicate with each other.

According to an aspect of the present invention there is provided a method of processing a received object in a rendering system said rendering system having a plurality of detection schemes each detection scheme being operative to group objects to form an associated object group said method comprising the steps of 

determining in descending priority order whether one of said detection schemes is operative to group said received object with a previously received ungrouped object 

outputting for rendering said previously received ungrouped object if it is determined that none of said detection schemes is operative to group said received object with said previously received ungrouped object and

grouping said received object with said previously received ungrouped object if it is determined that one of said detection schemes is operative to group said received object with said previously received ungrouped object.

According to another aspect of the present invention there is provided a method of processing a received object in a rendering system said rendering system having at least one detection scheme each detection scheme being operative to group objects to form an associated object group and one of said detection schemes having associated grouped objects said method comprising the steps of 

determining whether said detection scheme having associated grouped objects is operative to group said received object with said grouped objects 

outputting for rendering said grouped objects if it is determined that said detection scheme having associated grouped objects is not operative to group said received object with said grouped objects and

grouping said received object with said grouped objects if it is determined that said detection scheme having associated grouped objects is operative to group said received object with said grouped objects.

According to another aspect of the present invention there is provided a rendering system for implementing any one of the aforementioned methods.

According to yet another aspect of the present invention there is provided a computer program product including a computer readable medium having recorded thereon a computer program for implementing any one of the methods described above.

Where reference is made in any one or more of the accompanying drawings to steps and or features which have the same reference numerals those steps and or features have for the purposes of this description the same function s or operation s unless the contrary intention appears.

The computer module includes at least one processor unit a memory unit a storage device which typically includes a hard disk drive and a floppy disk drive and a number of input output I O interfaces. The input output I O interfaces include a video interface that couples to the video display an I O interface for the keyboard and mouse and an interface for the printer . The components to of the computer module communicate via an interconnected bus .

An operating system executing within the computer system performs basic tasks such as recognizing input from the keyboard and mouse sending output to the display screen and printer keeping track of files and directories on the storage device and controlling the hard disk drive and a floppy disk drive . The operating system also provides a software platform on top of which application programs execute.

When a document is to be rendered on the output device or the application program passes each page of the document as a series of graphic commands to a graphics interface services GIS layer provided by the native operating system of the computer system . The graphic commands describe the graphic objects of the page. The GIS layer is generally an application programming interface providing a rich set of graphics functionality to all application programs.

The GIS layer provides graphic objects to a device driver in a format that the GIS layer judges the device driver would process most efficiently and at a resolution of the output device or . In fact the GIS layer mediates between the application program and the output device or thereby enabling the device driver to support a much smaller set of functionality such as drawing rectangular blocks of image data and filling simple regions with flat color.

The device driver also known as a graphics rendering system renders the graphics objects received from the GIS layer . Rendering is the process by which the graphics objects received from the GIS layer are converted to pixels by the device driver . The pixels are sent to the output device or . Whilst the application program and the graphics interface services are formed by software the device driver may be performed in software hardware or a combination thereof.

In the preferred implementation the process of rendering by the graphics rendering system is effected by instructions in software that are carried out by the processor of the general purpose computer . The software may be stored in a computer readable medium including the storage device for example. A computer readable medium having such software or computer program recorded on it is a computer program product.

The graphics rendering system includes a graphics object buffer a number N of object detection schemes through N and a rendering module all of which are preferably effected by instructions executed by the processor . The operation of the graphics rendering system and its components through N and is described below with reference to and also by way of example with reference to .

Before describing the graphics rendering system according to the present disclosure and in an attempt to better illustrate the conflict that occurs amongst detection schemes when the rendering system includes multiple detection schemes where the detection schemes use one or more of the same objects shows a graphics rendering system with two detection schemes and and a vertical time axis . Each detection scheme or combines simple graphics objects into a graphics object group of a different type. Detection scheme combines multiple rectangle objects that adjoin each other into a single rectangle object. Detection scheme combines non adjoining rectangle objects into a single object consisting of multiple rectangles. shows the graphical relationship between rectangular input objects and .

Referring again to when input object is received by the graphics rendering system both detection schemes and detect object as a simple object that may be used to form their respective graphics object groups. This results in the detection schemes and both maintaining a reference to object .

However when input object a rectangle object adjoined to input object is received by the graphics rendering system only detection scheme is able to combine input object with input object because objects and are adjoining. Unless detection scheme has knowledge that detection scheme has combined input objects and detection scheme may output object which is not an efficient output of grouped graphics objects within graphics rendering system . So each detection scheme or has to communicate with other detection schemes to ensure that an input object is rendered only once either as a simple object by itself or as part of a graphics object group.

The requirement that each detection scheme communicates with one another greatly reduces the ease at which new detection schemes may be implemented. As more detection schemes are added to the graphics rendering system communication protocols typically grow in complexity which has the adverse effect of reducing execution speed and increasing software complexity within the graphics rendering system . Accordingly the cost of implementing a new object group detection scheme is increased.

Detection scheme detects multiple rectangle objects that adjoin each other and combines them into a single rectangular object. Detection scheme detects non adjoining rectangle objects and combines them into a single object consisting of multiple rectangles.

Detection scheme has higher priority than detection scheme because detection scheme produces an object group which requires less memory resources for storage and therefore can be more effectively rendered. The rendering effectiveness of a detection scheme which affects its relative priority is determined by the amount of reduction in graphics rendering system resources such as memory required to render the object group as compared to rendering each simple graphics object used to form the object group.

Rendering effectiveness is not the only factor affecting detection scheme priority. In an alternative implementation other factors may be used to determine detection scheme priority such as detection complexity object group complexity resources needed for detection etc. In yet another implementation totally random detection scheme priorities that are not dependent on any property of the detection schemes themselves may be used.

A detection scheme is considered to be active if it has detected one or more graphics objects but has not yet completed an object group formed by the detection scheme. At most one detection scheme may be active at any point in time.

Each detection scheme has two callback functions associated thereto A recognise callback function and a flush callback function. A detection scheme responds to the recognise callback function by reporting on its detection status by sending a status flag which may have one of the following meanings 

OBJECT COLLECTED The new object has been collected as part of the detection scheme s object group part of the detection scheme s object group and also completed the detection scheme s object group and

OBJECT COLLECT FAILED The new object cannot be collected as part of the detection scheme s object group.

In an alternative implementation the OBJECT COLLECTED COMPLETE status flag may be omitted from the recognise callback function since OBJECT COLLECT FAILED may be used to flush a previously completed object group when a new input object is received by the graphics rendering system .

The flush callback function causes the detection scheme to output its object group to rendering module for rendering if there is a complete or incomplete object group or does nothing if the detection scheme is not active.

An alternative implementation may implement the flush callback such that a complete or incomplete object group is output to either the rendering module or as a new input object into graphics rendering system for further detection.

The graphics rendering system is aware of the basic properties that make graphic objects suitable for detection by each detection scheme. The object s type for example a flat colour object or an image object and whether the rendering context has changed are examples of the basic properties used to determine whether a graphics object is suitable for detection by each detection scheme. So each input graphics object to graphics rendering system is pre processed to determine whether the object satisfies the basic properties that would make that input graphics object suitable for any detection scheme. A graphics object that satisfies the basic properties of a detection scheme can potentially be detected by that scheme but it is not guaranteed that the graphics object will form part of the detection scheme s object group.

An alternative implementation may choose not to pre process objects for detection suitability because unsuitable objects will be rejected by the recognise callback function of the detection schemes. Another alternative implementation could be for each detection scheme to provide an is suitable callback function thereby allowing graphics rendering system to use the is suitable callback function to pre process and determine whether graphic objects are suitable for detection by each detection scheme rather than graphics rendering system being aware of the basic properties that make graphic objects suitable for detection by each detection scheme.

Yet another alternative implementation can further pre process an input object before determining its suitability for object detection by merging any clipping objects with the input object. This will simplify the drawing path of the input object which may make the input object more suitable for object detection.

When the graphics rendering system receives input object which is a rectangle either of the detection schemes or can detect object and use such a rectangular object to form its respective object group. However graphics rendering system does not pass input object to either detection scheme or but stores the input object in the graphics object buffer along with its associated data such as colour drawing path etc .

When the graphics rendering system receives input object rectangle the input object rectangle stored in graphic object buffer is passed to detection scheme which has priority over detection scheme via the recognise callback function along with input object rectangle . Since detection scheme collects adjoining rectangles into a single rectangle object and input objects and adjoin each other detection scheme forms an object group from the rectangles and returns status OBJECT COLLECTED and becomes active.

Input objects and are not passed to the detection scheme because only one scheme may be active at any point in time. An alternative implementation may choose to store more than one object in the graphics object buffer before passing input objects to detection schemes and .

When graphics rendering system receives the next input object which is also a rectangle detection scheme is already active so input object rectangle is given directly to detection scheme via the recognise callback function. However input object is not accepted by detection scheme as part of the active object group . Because the new object cannot be collected as part of the active object group detection scheme returns a stutus OBJECT COLLECT FAILED causing the active object group to being output to the rendering module by the flush callback function while input object is stored in graphics object buffer .

An alternative implementation may choose to not store input object in graphics object buffer but output object to rendering module after the active object group .

When graphics rendering system receives input object which is another rectangle both input objects and are given to detection scheme only for object detection via the recognise callback function because detection scheme has the highest priority. However detection scheme is unable to form an object group from input objects and because objects and even though they are rectangles do not adjoin each other. Accordingly the recognise callback function returns status OBJECT COLLECT FAILED. Graphics rendering system responds by passing input objects and to detection scheme . Since detection scheme is able to form an object group from non adjoining rectangle objects input objects and form an object group and detection scheme becomes active.

The process continues by graphics rendering system receiving input object . Input object is passed directly to the active detection scheme being active using the recognise callback function. Since input object is a non adjoining rectangle from input objects and input object is accepted as part of the object group formed from input objects and . Accordingly the recognise callback function returns status OBJECT COLLECTED and detection scheme remains active with object group .

Graphics rendering system next receives input object which is a rectangle that adjoins both input objects and . The active detection scheme is unable to accept input object as part of the object group and the recognise callback function of detection scheme returns status OBJECT COLLECT FAILED. In response to the status OBJECT COLLECT FAILED the flush callback function is issued and the object group formed from input objects and is output for rendering to rendering module . Also input object is stored in graphics object buffer .

Finally the graphics rendering system receives the last input object which is a circle. A circle is not detectable by either of the detection schemes or . This results in the input object rectangle stored in the graphics object buffer to be output to the rendering module followed by the input object circle .

The process performed by the graphics rendering system for each input object passed thereto by the GIS layer is now described in detail with reference to . The steps of process are affected by software loaded into memory and executed by the processor .

The graphics rendering system starts process in step where new objects to be rendered are input into graphics rendering system from the GIS layer . Step pre processes object data received in step by examining object properties such as object type and object colour to filter out input objects that are not suitable for object group detection. That is input objects not groupable by any of the detection schemes through N are filtered out or rejected. If an input object is rejected in step then step follows where any input object stored by graphics object buffer or object group stored by an active detection scheme is output to rendering module by the flush callback function followed by the rejected input object. Process then continues to step where process returns.

In the case where it is determined in step that the input object is suitable for detection process continues to step where the current state of object detection in graphics rendering system is determined.

If there are no active detection schemes and no objects stored in graphics object buffer then the state is NO OBJECT and process continues to step where the new object is stored in the graphics object buffer . Process then continues to step where process returns.

In the case where it is determined in step that there is one object stored in the graphics object buffer then the state is STORED OBJECT and the process continues to step where graphics rendering system determines whether more detection schemes exist. If there is at least one detection scheme left in the list of detection schemes then process continues to step where both the new object and the object stored in the graphics object buffer are passed to a next detection scheme of graphics rendering system with the recognise callback function. The next detection scheme used in step is the scheme that has the highest priority in the list of detection schemes available in the rendering system .

Process then continues to step where the status returned by the recognise callback function of step is checked. If the status returned by the recognise callback function indicates a new object group has been formed that is the returned value is OBJECT COLLECTED then process continues to step where process returns.

If step receives a status indicating that a new object group has been formed and the object group is complete that is the returned value is OBJECT COLLECTED COMPLETE then step is executed to flush the completed object group to rendering module . Process then continues to step where process returns.

If step receives a status that indicates the detection scheme failed to form an object group between the object in graphic object buffer and the object received in step that is the value returned by the recognise callback function is OBJECT COLLECT FAILED then process returns to step until all possible detection schemes in graphics rendering system have been exhausted at which point process proceeds to step .

In step the input object stored by graphics object buffer is output to the rendering module and the input object received in step is stored into graphics object buffer . Process then continues to step where process returns.

Referring again to step if it is determined that there is an active detection scheme then the current state is SCHEME ACTIVE and the process continues to step where the input object received in step is passed to the active detection scheme with the recognise callback function. Process then proceeds to step where the return value of the recognise callback function in step is checked.

If the return value is OBJECT COLLECTED COMPLETE that is an existing object group is complete then step is executed to call the flush callback function of the active detection scheme to output the completed object group to rendering module . Process then continues to step where process returns.

If step receives status OBJECT COLLECTED that is the input object received at step has been accepted as part of the active detection scheme s object group then step is executed for process to return.

If step receives status OBJECT COLLECT FAILED that is the detection scheme failed to add the input object received at step to the active detection scheme s object group then step will call the flush callback function of the active detection scheme to output the active detection scheme s object group to rendering module and then store the object received in step into graphics object buffer . Process then continues to step where process returns.

Process transits from state NO OBJECT to state STORED OBJECT if graphics rendering system receives a new input object from the GIS layer and the new input object is deemed to be suitable for detection in step . Process remains in state NO OBJECT if the input object received by graphics rendering system is rejected in step .

Process transits from state STORED OBJECT to state NO OBJECT if the input object received by graphics rendering system is rejected by step . Process remains in state STORED OBJECT if the input object received by graphics rendering system is suitable for object detection but cannot form an object group with the input object stored in graphics object buffer . Process transits from state OBJECT STORED to state SCHEME ACTIVE if the input object received by the graphics rendering system is suitable for object detection and forms an object group with the input object stored in the graphics object buffer .

Process transits from state SCHEME ACTIVE to state NO OBJECT if the input object received by graphics rendering system is either rejected in step or the recognise callback function in step returned status OBJECT COLLECTED COMPLETE. Process remains in state SCHEME ACTIVE if the status returned in step is OBJECT COLLECTED. Process transits from state SCHEME ACTIVE to state STORED OBJECT if the input object received by the graphics rendering system is considered suitable for object detection in step but step returns OBJECT COLLECT FAILED.

As can be seen from the above description by eliminating the need for detection schemes through N to communicate with each other and by providing a well defined interface and framework in which to implement object detection schemes through N new detection schemes may be implemented with no knowledge of other pre existing detection schemes through N in the graphics rendering system .

The foregoing describes only some embodiments of the present invention and modifications and or changes can be made thereto without departing from the scope and spirit of the invention the embodiments being illustrative and not restrictive.

