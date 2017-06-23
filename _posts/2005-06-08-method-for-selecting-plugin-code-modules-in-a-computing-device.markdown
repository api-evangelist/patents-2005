---

title: Method for selecting plug-in code modules in a computing device
abstract: A plug-in for execution by an application on a computing device is selected by arranging for a server to iterate through available plug-ins, asking each plug-in in succession if it can better match the criteria required by the application than the previous plug-in. The plug-in having the closest match to the criteria is then executed by the application.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08225296&OS=08225296&RS=08225296
owner: Nokia Corporation
number: 08225296
owner_city: 
owner_country: FI
publication_date: 20050608
---
This application claims the priority of PCT GB2005 002250 filed on Jun. 8 2005 and GB 0413060.5 filed on Jun. 9 2004 the entire contents of which are hereby incorporated in total by reference.

The present invention relates to a method of operating a computing device and in particular to a method of operating such a device for enabling the device to resolve which out of a number of plug ins is the best fit to the attributes specified by a requesting application on the device.

The term computing device as used herein is to be expansively construed to cover any form of computing device and includes data recording devices of any form factor computers of any type or form including hand held and personal computers and communication devices of any form factor including mobile phones smart phones communicators which combine communications image recording and or playback and computing functionality within a single device and other forms of wireless and wired information devices.

A plug in can be defined as a replaceable item of executable code that provides specific services to a loosely coupled application that can load or invoke the plug in at run time. Plug ins are commonly loaded as dynamic link libraries DLLs or similar type of modules which execute within the same process space as the application which invokes them though they can also be spawned and run as separate processes.

Plug ins are widely used in many operating systems and by many applications. The main advantages of this technology are 

This technology is familiar to most users of computing devices through the widespread incorporation of plug ins in web browsers such as Microsoft Internet Explorer and Netscape which was the subject of U.S. Pat. No. 5 838 906 commonly known as the Eolas patent . As well as being the basis for running Java applets inside browsers the most common manifestation of the use of plug ins is that browser applications rely on them to render certain types of content. The use of plug ins in relation to multimedia files is particularly widespread.

Because plug ins are by definition inherently independent of the applications that load them it is necessary for all systems that use plug in technology to provide mechanisms by which applications are made aware of available plug ins and are advised of the method for loading or invoking them.

Early mechanisms such as those used by Windows applications depending solely on OLE technology from Microsoft required hard coded links to the plug in names and locations. This is regarded as unsatisfactory because it permits only plug in replacement and requires the host application to be updated to permit the addition of extra plug in components.

Subsequent mechanisms store names and locations of plug ins in a registry or plug in database this is considered superior to the hard coding of names as it is both flexible and extensible. For maximum flexibility and to enable the same plug ins to be used by different applications such registries or databases are typically system wide rather than application specific. It is therefore common for one or more intermediate layers to be provided between applications and their plug ins which provide common services including 

Microsoft s Component Object Model COM is one well known method of doing this whereby the operating system provides an intermediate layer which locates the plug in module in a registry handles the instantiation and then redirects calls from the application to the plug in instance. COM was developed so that software manufacturers could plug new accessories into existing applications without requiring a rebuild of the existing application. COM components should therefore be designed as interchangeable plug ins whether the COM component is a local in process DLL or a remote server executable.

WO 00 67114 in the name of Sun Microsystems describes A System and Method for discovering and binding a program object by which an intermediate layer uses a registry to discover and instantiate a plug in and then returns a reference to the instance back to the application in order that it may communicate with it directly.

System wide mechanisms such as these are often combined with less generic intermediate levels such as application specific plug in managers or specialized servers which allow plug ins to be used to service multiple simultaneous applications.

One concern with the current technology is that where there are a number of plug in candidates the choice of which plug in is the most suitable can be a highly technical process which requires potentially complex decision making intelligence or algorithms in order to arrive at the optimal selection.

Any approach based on the intermediate making such decisions would require it to maintain possibly complex state information and be party to specialized information. Depending on how generic the intermediaries are this could result in unnecessarily bloated code owing to the inclusion of routines for all types of existing plug ins. Architecturally this is at odds with the role of generic service layers which should restrict themselves to providing common services such as locating and instantiating plug ins. Thus all types of intermediaries are likely to prove inadequate for dealing with new types of plug ins which may not have been known about at the time the intermediate layer was written.

One specific case which illustrates these concerns is the implementation of Location Based Services LBS on a wireless information device such as a mobile telephone. LBS includes location based information location sensitive billing emergency services and location tracking. All of these features depend on the mobile phone being able to tell where it is positioning . However there are many different ways of obtaining positioning information. The most widely recognized system uses Global Positioning System GPS . There are also alternative technologies in use many of which are network based such as cell triangulation. It is also known that the available method for obtaining positioning information will expand in the future for instance the European Galileo project will eventually provided an alternative to GPS.

Those skilled in the art will recognize that a plug in design for implementing LBS which allows an application to use any method for obtaining positioning information would be highly appropriate and provide significant benefits. This is because 

However the above techniques for obtaining position have significantly different characteristics such as accuracy power required cost to the user and the time taken to obtain a positioning fix. The choice of which one to invoke is therefore a complex one which is dependent on a number of factors. No intermediate layer for invoking plug ins would be capable of taking all these into account. In the worst case an inability to make a sensible decision on how to obtain positioning information would result in the use of a simple last fit mechanism whereby the most recently installed matching plug in that conforms to the appropriate API is instantiated.

It is therefore apparent that there is currently no flexible and extensible way of automatically determining which plug in should be used in situations where a device has multiple plug ins available each of which could perform a particular task but in a sufficiently different manner to make it advantageous to choose a particular plug in for a particular circumstance.

Accordingly it is an object of the present invention to provide an improved method for selecting plug ins in a computing device.

According to a first aspect of the present invention as shown in there is provided a method for enabling a software application running on a computing device to cause the most suitable code module from a set of code modules to be executed the method comprising

According to a second aspect of the present invention there is provided a computing device arranged to operate in accordance with the method of the first aspect.

According to a third aspect of the present invention there is provided an operating system for causing a computing device according to the second aspect to operate in accordance with a method of the first aspect.

The Symbian OS operating system for mobile phones produced by Symbian Software Ltd of London has made extensive use of plug ins since its first release in 1997. While these plug ins have traditionally been based around polymorphic DLLs which are loaded by the type of intermediate layer described above an increasing number are proposed to be implemented as executables running in their own process space. This invention can be applied to either type of plug in.

While the invention described here describes how to solve the problem outlined above in the context of LBS it will readily be appreciated by those skilled in the art that the principles underlying the invention are equally applicable to any situation where a choice between possible plug ins needs to be made. Hence the case of LBS is used for illustrative purposes only and is not to be construed as restricting the scope or applicability of the invention in other areas. Likewise the Symbian OS operating system as described herein is also used for illustrative purposes only and is also not to be construed as restricting the scope or applicability of the invention in relation to other operating systems as will be apparent to persons familiar with this art.

The Location Based Services positioning sub system in the Symbian OS operating system employs a client server framework architecture to allow multiple clients applications to retrieve periodic updates of the device location from multiple location technologies.

This architecture comprises a singleton location server that is technology independent and which is accessed through a consistent application program interface API which provides a technology independent abstraction layer suitable for any of the methods described earlier.

The server manages access to location technology specific modules. These modules are implemented as plug ins which can be added to or removed from the operating system dynamically and which are detected and used by the location server without the client applications needing to know.

When a client connects to the location server it can offer a criteria object to specify desired or required properties of the location technology to be used. These criteria objects are specified in the abstraction API and allow Quality of Service QoS parameters such as horizontal accuracy vertical accuracy or time to first fix to be specified. Other parameters of potential interest to the application can also be specified such as cost and power consumption.

With the present invention as shown in the location server iterates through the available plug ins asking each one in succession if it can better match the criteria specified by the client than the previous plug in. The location server itself is unaware of how the resolution of better worse is being carried out from plug in to plug in.

The approach described within this application is based on each plug in being capable of carrying out a deterministic calculation of a score reflecting how well the plug in fits the specified QoS criteria. The calculation employs the current values of attributes such as time to next fix which will be known to each plug in. The calculation is deterministic and each plug in follows the same rules to ensure a fair and correct decision is always arrived at. Many different algorithms or methods for the final selection are possible such as 

The first of these methods requires some limited decision making by the server component the second is a true devolution of decision making such that the server is not involved at all. However this invention is not restricted to these two methods and will work with any algorithm that those skilled in the art may devise.

The invention relies on plug ins behaving correctly when calculating their score i.e. following the published rules for the deterministic calculation . This is not considered a deficiency of the principles involved and imposes no extra risk since an application in all cases has to trust that the plug ins it invokes will be well behaved. But if it is decided that plug ins should not all be trusted blindly it is still possible to check the behaviour of each one at a suitable point such as when the plug in is installed tested verified or signed. Alternatively applications may perform dynamic checking of the behaviour of a plug in at runtime by a watchdog or other mechanism.

This invention specifies a method and apparatus enabling the resolution of which out of a set of available plug in plug ins is the best fit to a set of desirable properties specified by a requesting application.

The members of the set of plug ins are each asked to carry out a deterministic calculation of how well they conform to the set of desired properties and then return the result as a numeric score.

This enables the selection of the most suitable module without the need for explicit intervention by or decision making intelligence in any other part of the software controlling the apparatus.

Although the present invention has been described with reference to particular embodiments it will be appreciated that modifications may be effected whilst remaining within the scope of the present invention as defined by the appended claims.

