---

title: Hardware accelerator for an object-oriented programming language
abstract: An apparatus and method are provided including a hardware accelerator capable of being interfaced with a processor for accelerating the execution of an application written utilizing an object-oriented programming language. Such object-oriented programming language may include Java and/or C++.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09098297&OS=09098297&RS=09098297
owner: NVIDIA Corporation
number: 09098297
owner_city: Santa Clara
owner_country: US
publication_date: 20050614
---
The present application is a continuation of U.S. application Ser. No. 09 886 167 filed Jun. 20 2001 now issued U.S. Pat. No. 6 983 357 which is a continuation of U.S. application Ser. No. 08 965 540 filed Nov. 6 1997 now issued U.S. Pat. No. 6 330 659 which claims benefit of U.S. Provisional Application No. 60 045 951 filed May 8 1997 which are incorporated herein by reference in their entirety for all purposes.

The invention relates to object oriented programming languages. More particularly the invention relates to a hardware accelerator for an object oriented programming language.

Object oriented programming OOP is the name of a class of programming languages and techniques based on the concept of an object . An object is a self contained component which has a specific role in a program. OOP languages include C and the Java language developed by Sun Microsystems Inc. For the purposes of discussion only the OOP language described herein is Java.

An OOP defines classes of objects. A class is a prototype for an object or a set of objects which share a common structure and behavior. An object also referred to as an instance is a specific representation of a class. Each instance of a class is distinguished by its particular attributes. These attributes are defined by instance variables . The types and names of these instance variables are defined in the class. However the values of the instance variables are set and changed in the object.

The behavior of a class determines how an instance of that class operates. The behavior of a class is determined by a set of routines referred to as methods that is associated with the class. An operation on an object is performed using a method. Methods are common to all instances of a particular class.

Classes are hierarchically arranged. Each class in the hierarchy may have a class above it in the hierarchy referred to as a superclass or a class below it referred to as a subclass . Subclasses inherit attributes and behavior from their superclasses. Thus a subclass does not have to redefine a behavior that is defined in a superclass but can inherit the methods and variables from the superclass.

In an OOP procedure calls are described in terms of message passing. A message names a method and may optionally include other arguments. When a message is sent to an object the object s class is searched for the method named therein to determine how to perform the requested operation on the given object. If the method is not defined for the object s class the object s superclass is searched. This procedure is continued up through the class hierarchy until either the method definition is found or there is no higher superclass to search.

The arrangement of arguments for a procedure call is determined by a calling convention. The calling convention determines the particular order in which arguments are pushed onto a stack or entered in registers as well as who is responsible for removing the arguments.

The calling conventions or interface by which an application accesses an operating system and other services is referred to as the Application Programming Interface API . In Java the core Java API defines the minimal set of functionality that must be supported for a platform to be considered Java compliant.

Java supports independent programs referred to as applications and dependent programs referred to as applets. Java applets are programs that are transmitted over an electronic network and executed by an application provided on a receiving device. Examples of such electronic networks include the Internet and a local area network system referred to herein as an intranet. Receiving devices include computers personal data assistants and Internet capable telephones.

For purposes of discussion herein a Java applet will be assumed to be transmitted over the Internet to a receiving computer for display in a World Wide Web Web page. A Java application is a standalone program that does not need to be executed by an application such as a Web browser provided on the receiving computer.

Java is a platform independent language that can run on any Java compliant computer system. The Java development environment includes a Java compiler and a Java interpreter. The Java compiler generates bytecodes from a Java program. Java bytecodes are machine instructions that are not platform specific.

A platform specific bytecode interpreter is used to execute the Java program. This bytecode interpreter is called the Java virtual machine. For applets the bytecode interpreter is built into a Java enabled Web browser. The Java virtual machine and its supporting code are together referred to as the Java runtime system.

The Java virtual machine includes a bytecode instruction set a set of registers an area for storing methods a stack and a garbage collected heap. The Java virtual machine registers temporarily hold the data representing the machine s state. The registers affect the machine s operation and are updated after each bytecode is executed. The method area stores the Java bytecodes that implement most of the methods in the Java system.

The stack is used to supply parameters to both bytecodes and methods and to receive back their results. The stack frame contains the local variables for the method call its execution environment and its operand stack.

The heap is the memory location from which newly created instances are allocated. Instances are automatically garbage collected in Java. A garbage collector is a programming function that is designed to track each instance that is created and to free the memory storing an instance after the last reference to the instance has vanished.

In Java objects classes that are intended to be reused repeatedly in different programs are stored as a class library . A set of classes that embodies an abstract design for solutions to a number of related problems is known as a framework. The core application frameworks that are stored in the Java class library include Java.Lang Java.Util Java.Applet Java.IO Java.NET and Java.AWT.

Java.Lang includes classes that add data types and system capabilities to the language itself while Java.Util contains the utility classes and simple collection classes. Java.Applet contains classes for implementing Java applets.

Java.IO contains the input and output classes for writing to and reading from streams such as standard input and output. Java.IO also includes the input and output classes for handling files.

Java.NET contains classes for networking support. Such classes include those for connecting and retrieving files in accordance with such standard Web protocols as for example TCP IP and IP and for creating sockets such as those used in UNIX applications.

The Java Abstract Windowing Toolkit Java.AWT provides classes and behavior for creating graphical user interface GUI based applets and applications. The Java.AWT can be used for example to draw to the screen create windows buttons menu bars slider bars and other user interface elements. Java.AWT can also be used to manage user input such as mouse clicks and keystrokes.

Object oriented software frameworks are generally implemented using the computer s Random Access Memory RAM Read Only Memory ROM or Virtual Memory VM . When a Java application or applet is started on for example a computer one of the first operations performed is the creation of the GUI.

However because a software based implementation is being used a significant percentage of the processing capacity of the computer operating system can be required to actually generate and display the GUI. Therefore the processing of other instructions by the operating system can be slowed dramatically while GUI elements are being rendered on a display device. Further if mouse or keyboard events are generated while a display is updating the Java runtime may enter a kind of deadlock where update events are being generated at the same time the system is trying to process backlogged mouse and keyboard events. Eventually the runtime system cannot catch up and process all events within a reasonable time frame. To an end user the program appears to stop working apparently refusing further commands and input.

Java is a multiprocess multithreaded system. Thus it supports a plurality of programs or processes executing simultaneously each within its own address space. A thread is a sequence of code executing within one of these processes. Therefore the Java programming environment and runtime system both have a multithreaded architecture.

In a multithreaded program such as Java a single thread running a Java program may be blocked until for example a window is drawn. Additionally any other thread that is dependant on that single thread can also be blocked. Blocking can restrict or delay for example information transmitted over a network. Blocking as such is defined as the capability for a Java thread to wait for a task to complete before resuming execution.

It is often desirable to run Java programs as a part of an embedded environment for example to run Java applications and applets on a device such as an Internet capable telephone. However Java code and a fast Java bytecode processor are required to render the device Java compliant. This can significantly increase the costs of manufacturing and operating the device.

It would therefore be an advantage to provide a method and apparatus for reducing performance degradation. It would be yet another advantage if such method and apparatus permitted the efficient use of object oriented programs in both embedded and desktop environments.

The invention provides a method and apparatus for accelerating an object oriented programming language. The preferred embodiment of the invention is configured for use with a Java compliant processor with the Java programming language and standard Java object based frameworks. However alternative embodiments of the invention are adapted for use with any object oriented programming language. Alternative embodiments of the invention are also adapted for use with other object based frameworks such as Apple Computer s Open Step framework or Microsoft s object based AFC library.

The invention provides a hardware accelerator that contains functionality to implement one or more Java application frameworks. In the presently preferred embodiment of the invention the accelerator is constructed as part of an application specific integrated circuit ASIC . The accelerator includes a hardware object management system that manages instances as well as the states of values assigned to the instances.

The preferred embodiment of the invention implements the Java Abstract Windowing Toolkit AWT Java.NET and Java Input Output application frameworks. Additional Java frameworks can also be supported by the invention if required.

The Java runtime system manages both the hardware object management system and a software object management system. The software object management system can be implemented entirely in software or in both software and hardware.

Instances and methods of supported Java application framework classes that are executed by a Java program are offloaded to the hardware object management system. Thus in the preferred embodiment of the invention the central processing unit CPU can continue processing instructions while the hardware object management system manages Java.AWT and Java.NET requests.

The invention stores application framework classes as libraries in a shared memory. However each supported application framework is managed separately. A request is distributed to the hardware controller for the particular application framework and the shared memory is accessed as necessary.

A software stub is provided as an interface between the hardware object management system and the CPU. The software stub can be modified or replaced to permit the invention to be used with any compatible OOP language.

The hardware object management system includes an Input Output request queue for receiving and storing object requests. When a task processor allocates memory for an object it is removed from the queue. An active object list tracks the number of reference counts in the Java virtual machine to an instance. When the number of reference counts to an instance is zero the memory storing the object is deallocated by a Java garbage collector.

In the presently preferred embodiment of the invention the Java.AWT hardware implementation contains a windowing view system and a rendering engine. A graphic Java program is structured as a hierarchy of nested containers and components. Containers manage collections of visual objects called components. Components represent visual functionality that is displayed on the screen such as menu bars buttons editable text areas and text fields. Containers themselves may be hierarchically nested within one another and may maintain a parent child relationship with another Container. For a given application there is one container view at the top of the view hierarchy that is represented by a Window AWT.Frame object. AWT.Frame defines a window native to a particular platform i.e. Windows or Solaris .

In addition containers can also be thought of as special case components that have the ability to contain other components that have the ability to contain other components. This is because functionally the Container class is a subclass of Component. A Panel is a Container that can be displayed ion a screen within an application or applet. A Frame is a Window with a title and menu bar and is yet another type of Component Container object. The shared class behavior that all of these classes have allow them to share various characteristics and integrate well together. The Java.AWT hardware implementation leverages these shared functionalities between different component object variations by optimizing messaging and increasing container display efficiency.

Containers are Java.AWT components that can contain other components including other containers. A panel is a container that can be displayed on screen such as a applet. A frame is a window that has such features as a title and a menu bar.

The windowing view system includes a general graphics controller for creating frames and components and for passing data to the rendering engine a window manager for managing the frames a layout manager for managing container hierarchies within a frame and a component manager for managing component hierarchies within a container.

The Java.NET hardware implementation contains a windowing view system and a connectivity engine. The windowing view system includes a network controller that contains microcode for Java.NET framework equivalencies. A network query mechanism performs DNS lookups and reports results to the network controller a socket manager manages sockets in use by applications and a stream manager for shuttles input and output data through a link supported by network protocols.

The invention therefore provides a hardware implementation for reducing blocking by co processing instructions of a supported application framework. Java processing is thereby accelerated.

The invention provides a method and apparatus for accelerating an object oriented programming language. The preferred embodiment of the invention is optimized for use with the Java programming language developed by Sun Microsystems Inc and with the Java Application Program Interface. However the invention is readily adapted for use with any object oriented programming language such as C or even C for a program that was written in Object Oriented Style. Thus the following discussion is provided for purposes of example and not as a limitation on the scope of the invention.

Similarly an implementation which is interconnected with the Java accelerator may employ a different application framework or set of application frameworks unconnected with Sun s Java APIS.

While the preferred embodiment of the invention is adapted for use in data transmission over the Internet the invention is equally applicable to other wide area or local area networks. Additionally while the preferred embodiment is used with a desktop computer the invention can also be used with other devices including network servers personal data assistants fax machines and Internet capable telephones.

The display screens and configuration of the graphical user interface described below are provided in accordance with the presently preferred embodiment of the invention. However one skilled in the art will appreciate that such display screens and graphical user interfaces are readily modified to meet the requirements of alternative embodiments of the invention. The following discussion is therefore provided for purposes of example and not as a limitation on the scope of the invention.

A part of the Java Accelerator s memory see is predesignated to hold object descriptors and parameters. These object spaces are all of equal size but the format of each depends on the type of object assigned to them. At the start of each object descriptor there is a status byte that indicates whether that particular object space is in use.

Upon initialization designators are indicated as being free. Software can then begin to create objects using the following steps 

The hardware object manager also works in the situation where object IDs are provided by the host system and not returned by the hardware. In this case the first provided object ID is stored in a base reference register and associated with the first free object location. Each subsequent object request has its ID compared with the reference register. The offset determines the actual object location in memory. If that particular record is already in use then the next free object location is used. A predefined reference field is included with each object record to indicate what offset it is associated. Offsets are performed in a modulo fashion such that memory locations wrap around to the beginning again when the offset is greater than the allotted memory space. This system also works for situations where the system provided object ID is a greater number of bits than the hardware object ID.

Other types of objects may exhibit this same functionality. A Button Object for instance likely references a string object which may in itself be more than 30 bytes. In this case a Button Object would point to a String Object which would in turn point to another String Object with each object measuring 30 bytes in length. This shows how Combined Object Entry Lists function.

Objects see are handled in small blocks with the invention. The objects always look the same in terms of their size and footprint. What distinguishes one instance from another on the active object list is its data structure or instance variables.

Instances may be either simple or complex. They may contain 8 16 32 bit integers or single bit boolean values. They may also contain object reference IDs to other objects.

Take the case of a Container object. After a request for a Container object has been placed on the Input Output Request Queue JExpress takes the request and creates a fixed size block of memory to store variables related to the Container instance. After several Component objects are created they may be added to the Container. If a LayoutManager is assigned to manage objects assigned to a Container this is done accordingly. In the case of a Container BorderLayout association five possible components may be added directly to the Container. The Borderlayout object is then given references to a maximum of five north south east west and center components so that it knows how to draw and update these objects at later points in time.

The Active Object List contains a list of possibly many 30 byte blocks each denoting an active instance of a particular type of object.

Each type of object has a structure associated with it as shown in the three object instance diagrams below.

All instantiated objects contain flags which describe the type of object the a method selector for the runtime system and the framework the object belongs to BorderLayout instances in addition contain a pointer to the container that uses them to layout a set of components possible object references to it s components in the north south east and west and a value determining the space to leave in pixels between components when drawing them.

Container objects contain the number of enclosed components a reference to a component object which holds the Container s inherited instance values and a reference to the first container object in a linked list of Component objects

Component objects contain a type value denoting if they should draw a button or handle events from a button slider textfield or other type of widget. They also contain a link to the next component available in the Container.

These object definitions map directly into C structures which are managed by the framework note these are preliminary structs that will both change and will be optimized .

The object definitions outlined herein along with others not defined herein are used to create instances and maintain unique instance values. Without use of these data structures the 30 byte blocks in the Active Object List would have no meaning. These object structs are used to identify set and access values within particular object instances. The runtime system uses the collection of object instances to make method execution meaningful for a given set of data.

A method descriptor in the descriptor struct for an object may be specified so that the object may be transmitted to the low level framebuffer implementation. The smart framebuffer can then take the struct and interpret a command such as a resize or redraw in a meaningful way. At this time Graphics and Component objects have their structs forwarded to the smart framebuffer.

The Java runtime system includes the Java virtual machine together with its supporting code. The Java runtime system parses instantiation and method calls. In the preferred embodiment of the invention the Java runtime system manages two instance managers a hardware object management system and a software object management system . However in alternative embodiments of the invention the Java runtime system manages more than two instance managers.

The hardware object management system contains functionality to support Java application frameworks. In the presently preferred embodiment of the invention the hardware object management system implements the Java Abstract Windowing Toolkit AWT and Java.NET application frameworks. The Java Input Output application framework not shown is also implemented to support the Java.NET functions. The hardware object management system can readily be adapted to support additional Java frameworks as needed. The invention therefore provides a Java application framework hardware implementation that functions as an accelerator for the CPU.

The hardware object management system manages instances as well as the states of values assigned to the instances. In the presently preferred embodiment of the invention the hardware object management system is wholly implemented in gates and can have associated external random access memory RAM .

In this embodiment the hardware object management system is constructed as part of an applications specific integrated circuit ASIC . It should be appreciated that while the preferred embodiment of the invention is discussed in connection with a gate level implementation and with an ASIC the actual hardware implementation of the invention is considered to be a matter of choice to one skilled in the art.

The software object management system can be implemented entirely in software. However in alternative embodiments of the invention the software object management system is implemented using both software and hardware components. An example of a software object management system is the computer system s memory manager.

Instances and methods of supported Java application framework classes that are executed by a Java program are offloaded to the hardware object management system. Thus in the preferred embodiment of the invention the CPU can continue processing instructions while the hardware object management system manages Java.AWT and Java.NET requests.

Whenever instances and methods in the hardware implemented Java application framework classes are being executed by a Java program the instances and methods are offloaded to the hardware object management system. Thus in the preferred embodiment of the invention the hardware object management system manages the Java.AWT and Java.NET requests of threads running on the Java virtual machine. The CPU is thereby available to continue processing instructions and threads that are not dependant upon the offloaded instances and methods while the hardware object management system manages the Java.AWT and Java.NET requests.

Application framework classes intended to be repeatedly reused in different programs are stored in the Java Class Library . Such classes can include those of the Java.AWT Java.NET Java.Lang Java.IO and Java.Util application frameworks.

The application framework classes are stored as libraries in a shared memory. However each supported application framework is managed separately. A request is distributed to the hardware controller for the particular application framework and the shared memory is accessed as necessary.

Classes and behavior for performing network operations such as establishing a socket connection are implemented by the Java.NET accelerator . The Java.NET accelerator is provided with an interface to a network TCP IP stack . The Java.NET accelerator includes a hardware implementation of both Java.NET networking objects and Java.IO input output related objects. This is because networking necessarily implies the input and output of data. The incorporation of both frameworks into hardware allows significant reduction of redundant software coding.

In one example of an implementation of the Java.NET accelerator the Java.IO hardware implementation is used to handle data input and output during a socket connection. In the Java.NET accelerator Java.NET and Java.IO application framework classes are bound together through inheritance. Thus classes in one framework can inherit functionality in another framework and then add to it.

The Java.AWT accelerator implements the classes methods i.e. behavior of the Abstract Windowing Toolkit. The Java Abstract Windowing Toolkit Java.AWT provides classes and behavior for creating graphical user interface GUI based applets and applications. Such classes include the Java.AWT class and any associated rendering tools for example a two dimensional rendering engine .

The Java.AWT accelerator can be used to draw to the screen create windows buttons menu bars slider bars and other user interface elements and can also be used to manage such user input as mouse clicks and keystrokes. Thus the Java.AWT accelerator is provided with an interface to such devices as the computer display framebuffer keyboard and mouse.

In the preferred embodiment of the invention the hardware object management system is also cast into the ASIC to manage instances and the states of values assigned to the instances. For example the hardware object management system stores data to track whether a button is pushed. The hardware object management system also stores data indicating the relationship among objects such as that the button is a part of a particular window. This information is stored in the shared memory.

Software stubs are provided as an interface between each accelerator and the CPU running the Java virtual machine. Thus the Java.NET accelerator has associated Java.NET software stubs and Java.IO software stubs while the Java.AWT accelerator has associated Java.AWT software stubs . The software stubs covering the hardware components of the invention can be modified or replaced to permit the invention to be used with any compatible OOP language.

The Java compliant host CPU runs a Java virtual machine for example from read only memory ROM storage . A Java applet or application that is transmitted to the invention through the physical transport is then directed through the physical transport interface to the host CPU. AWT command decoders and NET command decoder are used to convert the binary input information to output elements represented by the binary code.

The applet or application is stored in the memory as bytecodes. A GUI must be created to display the applet or application. Thus when a Java program is initially run from the memory a call is made to the function libraries stored in ROM directing that a GUI display be generated.

Such call is directed by means of the hardware object management system and the software stub to the appropriate Java application framework accelerator. When for example a Java.AWT window is requested the Java.AWT accelerator creates a window object. The graphics command generator is then requested to direct the graphics controller to actually draw the window on the display .

The Java.NET accelerator can include e mail and web browser application engines . Thus for example a JPEG or GIF image can be downloaded from the Internet using the invention. The image is then directed through the Network TCP IP stack to a JPEG GIF decoder and then to a frame buffer managed by a frame buffer manager . Thus the invention uses a hardware implementation to accelerate the display of a graphical image downloaded from a network connection.

The memory controller arbitrator serves as an interface between the host CPU and the shared main memory . The memory controller arbitrator allocates and manages system memory among the various components of the invention. This memory management includes the allocation of memory to for example the Java.AWT accelerator or providing the CPU with the memory location of an object created by the invention.

A thread that contains a class or method of one of the supported Java application frameworks is directed to the invention through the hardware object management system. Thus in the preferred embodiment of the invention the hardware object management system manages the Java.AWT and Java.NET requests of threads running on the Java virtual machine. Therefore while the hardware object management system manages the Java.AWT and Java.NET requests the CPU is able to continue processing threads and instructions that are not dependent thereon.

The hardware object management system includes an Input Output request queue for receiving and storing object requests. Such requests can include 

When a task processor allocates memory to an object for example by creating a new container object the object is removed from the queue. An active object list stores a list of instances . In use flags are provided to indicate the number of reference counts in the Java virtual machine to an instance.

When the number of reference counts to an instance is zero the memory storing the object is deallocated by a Java garbage collector not shown . The active object list will also indicate that the particular instance is not in use .

The status of an object is stored in a status listing . The status can include indicating that the object is in use or that the memory storing the object has been deallocated .

The Java virtual machine sends data to and receives data from the invention using a set of commands tasks . The Java programming language relies primarily on low level objects. Therefore the low level register includes objects that are essential to Java implementation.

In one embodiment of the invention only the low level implementation is implemented. This embodiment has greatly reduced size and memory requirements and is of advantage for use in embedded systems.

Low level functionality includes elementary windowing control image rendering font control and event handling. Low level objects supported by the preferred embodiment of the invention include 

The high level register provides secondary functionality that can be optionally implemented in hardware. Such high level functionality includes standard GUI widgets GUI layout behavior and media control objects. High level objects supported by the preferred embodiment of the invention include 

Because the invention represents entire application frameworks in hardware the invention eliminates the need for a significant amount of code. For example some parts of an OOP application framework can be made available for use by a custom application while other parts are hidden for exclusive use by the application framework. However in a hardware implementation it is not necessary to hide such framework parts. It is more useful to eliminate redundant coding and to implement only those functions that are publicly accessible to software stubs that activate tasks within the hardware gate arrays.

Thus many objects and classes of Java application frameworks care eliminated in the invention. An example of an eliminated class is the Sun Microsystems Inc. Java.NET.SocketInputStream class. This class inherits from Java.IO.FileInputStream and adds only a minimal amount of functionality to the original baseclass. Thus the invention can eliminate such a redundant class without causing a significant loss of functionality.

Object requests are received and stored pending processing in the Input Output request queue . The task processor then directs each request to a hardware AWT accelerator . The accelerator includes a windowing view system and a rendering engine .

The windowing view system includes a window manager for managing frames that are generated by the invention. The layout manager manages the hierarchies of containers within each frame while the component manager manages the components within each container.

The windowing view system also includes a general graphics controller for creating frames and components and for passing data to the rendering engine. The microcode for the hardware equivalencies of the Java.AWT application framework is implemented in the general graphics controller. Object method requests are made and are executed appropriately by the other components of the windowing view system and by the rendering engine.

The rendering engine creates the requested objects using rendering tools such as an image renderer a polygon renderer and a font renderer . One skilled in the art will readily appreciate that the types of rendering tools included with the rendering engine can be varied according to the particular requirements of the supported application framework.

The image renderer receives and decompresses image data. The image is then rendered within a given component of a display. The polygon renderer provides acceleration for rendering vector based images. Predefined drawing types such as for drawing arcs lines ovals polygons and rectangles can be supported. The font renderer manages requests for displaying text.

The Window Server Windowing System see exists at the furthest point away from the Java Virtual Machine. Relying on commands forwarded onto it from the Object Execution Mechanism i.e. the runtime it never directly receives commands from the software layer. As such the Window server has no direct interface from the software level.

This is roughly equivalent to the way that Java operates on a PC. Typically peer objects are created to map requests from the Java processor to compiled resources outside the runtime. For Windows 95 NT or any other modern OS this means making calls to the standard windowing system either C or Assembly code.

The compiled code used in these operating systems thus generates the primitives necessary to perform system level windowing requests. Windows are managed on a screen and standard buttons sliders and other OS based UI widgets are often utilized to simplify coding increase performance and provide a user interface that matches that of the host OS itself. In Sun s JDK this is called using a peer interface employing a set of software based class stubs which map functionality between Java objects and compiled native code.

The invention loosely uses the ideas of peers. However the peer implementation is provided totally at a gate level implementation and is only accessible from other ASIC based functionality i.e. hard coded Java objects . Doing this makes sense from a number of perspectives. First peer based drawing types can be swapped out easily at the register definition level allowing custom or multiple UI implementations to be created. Secondly peers in ASICS can be compartmentalized appropriately into different sections of hardware as is appropriate. That is a difference between hardware and software. In software you build logical functional groupings while in ASICs you build for efficiency and reduced gatecount.

In software we can group object based functionality logically in a way that is orderly. All of the view based objects can pretty much go in one place . . . one framework. In hardware it is necessary to split things up. One could build an object representation at the Window server for every UI object. However it turns out this is neither efficient nor necessary.

Necessity dictates that if possible elegance should be sacrificed for minimum gatecount making the scenario in a more attractive design.

Note that in this implementation of the Windowing System there are only a few objects that might be comparable to standard Java peer objects. They are quite different than peers in a software only Java implementation because they support a more abstracted set of functionalities. A software implementation might assign a peer to every UI object i.e. Button Slider TextComponent etc whereas the invention employs a single Component peer that handles all Component related drawing requests.

The rendering engine then encapsulates all of the actual drawing code and provides renderers handlers for of interpreting Frame Graphics Component and String instances. The rendering engine typically accessed these instances by either memory reference or via a fixed size stream of data 30 bytes . The instance contains a command byte instructing the rendering engine which method to execute with regard to the object.

When the rendering engine receives an instance it first decodes the type of object that is being sent into one of the four objects supported. Once the object type is known the reference is passed down to the decoder for that particular object type. The execution method e.g. Component paint is determined and the method executed.

For a Component paint the object is further queried to find out the type of component to be displayed. Currently the component section of the rendering engine knows how to render the types of view based widgets shown on .

Once the rendering engine is aware of the type of component it is to draw the instance is queried for information such as the location of and dimensions of the widget. The component is then rendered on the display.

Because objects are quite small it is impossible to transmit strings within component instances. It is the case that the fixed size of an instance in the invention may be 30 bytes which could be smaller than the size of a string itself.

For this reason strings or at least references to strings are sent previous to sending actual components to the rendering engine.

Strings are accumulated by the rendering engine. Either a stream or a reference to a fixed byte object containing string information is typically sent to the rendering engine. This string may be followed by another fixed block which contains another string. Subsequent transmissions are concatenated onto the end of a string until a component instance arrives. Once the component arrives the accumulated string is associated with it and the component is then rendered with its string. The concatenation is necessary especially in the case of a textfield which may have very large strings.

Note that in final ASIC form the concatenation process see consists of accumulated pointers to fixed blocks containing the string to render instead a concatenated string itself. This is necessary because some components may have very large text contents such as the TextArea which on traditional Java may be 32 kilobytes or larger. A TextArea is essentially a text editor object. Scaled down versions of the invention might have arbitrarily assign a maximum number of text characters allowed to guarantee efficient use on devices with small memory footprints.

Once the component is rendered with it s string the string itself is set to null in preparation for the next string component combination.

Graphics instances are different than component instances. Graphics instances are responsible for drawing low level primitives where components may drive this or even hundreds of primitives including lines filled areas and text in order to draw something like an editable TextArea. The graphics object supports general types of primitives drawing. The types of rendering shown on are supported by the graphics object in the rendering engine.

The graphics peer implementation in the rendering engine looks fairly complicated but is actually much simpler than the component peer. Graphics supplies very low level drawing while components usually combine a set of graphics drawing behavior into a single macro as described in the preceding paragraph.

Frames are relatively straightforward in terms of what they do. This being a sort of frame peer implementation it draws windows on the screen of a specific type. The window display type may change depending on the implementation and may support multiple personality types as is the case overall with the rendering engine.

Generally a frame has a title bar an icon image and a cursor type associated with it. Frames behave in the same way that components and graphics do but are drawn behind the UI that they contain.

Frames are a type of container in the standard Java implementation. However because this is something like a frame peer it has no direct relationship with any other objects. As far as the rendering engine is concerned a window is just a special object with a macro that draws a specific set of lines and so forth. It acts very similar to the way a component behaves at this level.

In the first object request in the input output request queue is to create a frame object . When the frame object is created it is added to the active object list. The next object request to create an event object is then moved to the top of the input output request queue. When the event object is created it is also added to the active object list.

An object remains active until the objects Java Virtual Machine garbage collector reference count decreases to zero. See above . Additionally objects can contain references to each other as necessary. For example the relationships among a window a button within the window and text displayed on the button are indicated by such references.

The windowing view system also includes a layout manager and a component manager . The layout manager belongs to is referenced by a frame and performs the functions of 

Many redundant support objects are eliminated in the Java.NET accelerator without causing any loss of networking functionality.

Java.NET object requests are received and stored pending processing in the Input Output request queue . The task processor then directs each request to a hardware NET accelerator . The accelerator includes a networking system and a connectivity engine . The connectivity engine executes a request to establish maintain or terminate a network connection for example using such network protocols as IP TCP IP and UDP .

Microcode for the Java.NET accelerator is implemented in the Network Controller . The windowing view system also includes a network query mechanism a socket manager and a stream manager .

The network controller can operate either synchronously or asynchronously. The network query mechanism performs DNS lookups and reports the results to the network controller.

The socket manager manages sockets that are in use by applications. This management includes opening and closing the socket connections. The socket manager also determines the container that an event occurred in and notifies the container to update if necessary. When requested socket status is transferred to the network controller.

The stream manager shuttles character stream based input and output over the TCP IP or UDP link. The stream manager offers a choice of input output streams that differ for an application s use. Additionally when requested the stream manager transfers buffers to the network controller.

Although the invention is described herein with reference to the preferred embodiment one skilled in the art will readily appreciate that other applications may be substituted for those set forth herein without departing from the spirit and scope of the present invention.

For example in the preferred embodiment of the invention only one hardware object management system is required on the ASIC for any number of supported application frameworks. However in alternative embodiments multiple hardware object management systems are provided. For example a separate hardware component such as an ASIC can be provided for each supported application framework with each hardware component having a dedicated hardware object management system.

The invention can be formed as a part of a computer system or can be formed as a part of an insertable device such as a PCI card.

One skilled in the art will readily be able to construct the hardware and software required for the invention using well known programming techniques and equipment.

Appendices A L attached hereto and incorporated as a part of this application further describe the features functions and structure of the invention.

Appendix A is a logic description according to one embodiment of the invention. Appendix A details an example of the objects parameter lists and local variables that presently need to be implemented for the invention to be Java.NET compliant. Appendix A is a list of objects methods and variables that have been used to build one embodiment of the invention. References to dependencies in Appendix A denote the objects upon which the said object is dependent. Similarly references to Exceptions are Exception classes upon which the said object is dependent.

Appendix B is a list of the Register Set for the Java.NET accelerator according to one embodiment of the invention. The processor sends data to and retrieves data from the invention using this Register Set.

Appendix C is an exemplary High Level Command Set for the Java.NET accelerator according to one embodiment of the invention. This High Level Command Set provides object based functionality in hardware that allows the Java.NET codebase to be consolidated into silicon.

Appendix D is an exemplary list of an Low Level System Service Interface Description for the Java.NET accelerator according to one embodiment of the invention.

Appendix E is an exemplary list of method equivalencies for the High Level System Services of the Java.NET accelerator according to one embodiment of the invention.

Appendix F is an exemplary list of Java.IO method equivalencies for the High Level System Services of the Java.NET accelerator according to one embodiment of the invention.

Appendix G is an exemplary list of General OutputStream Stream based Object and Object method equivalencies for the Java.NET accelerator according to one embodiment of the invention.

Appendix H is an exemplary list of codes used for Exception Errors in the Java.NET accelerator according to one embodiment of the invention. Many operations including function calls in the invention or Java.NET method calls can result in exception errors. This is because requests related to sending and receiving data over socket connections can fail for a variety of reasons. Several types of exception errors can occur within the Java.NET and Java.IO application frameworks. The invention can support these exception errors by making return values available to the software layer that exists on top of the hardware component. Thus error checking and handling can take place.

Appendix I is an example of a Low Level Implementation API for the Java.AWT accelerator according to one embodiment of the invention.

Appendix J is an example of a High Level Implementation API for the Java.AWT accelerator according to one embodiment of the invention.

Appendix K is an exemplary explanation of the Object oriented Java.AWT accelerator according to one embodiment of the invention.

