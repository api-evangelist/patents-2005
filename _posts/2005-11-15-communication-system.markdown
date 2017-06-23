---

title: Communication system
abstract: A communication system for linking users to control instruments. A user may send a first creation command from a user interface and establish a communication channel linking the command interpreter and the control instrument independent of the interface bus standard or interface hardware driver type. The communication system also includes providing a common communication interface between the user and the control instrument in an array-based programming environment. Embodiments provide a concise and powerful communication system for communicating with control instruments independent of the various types of supported interface bus standards, communication protocols, and driver types.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07823168&OS=07823168&RS=07823168
owner: The MathWorks, Inc.
number: 07823168
owner_city: Natick
owner_country: US
publication_date: 20051115
---
This application is a continuation application of U.S. patent application Ser. No. 09 954 872 filed Sep. 18 2001 now U.S. Pat. No. 6 993 772. The contents of the aforementioned applications are hereby incorporated by reference.

In typical instrumentation systems a computer communicates with control instruments such as oscilloscopes and function generators that can obtain data about dynamic real world systems under test. Users can model simulate or analyze data by establishing a communication channel to the control instruments. Users connect the computer to the control instruments through various interface options such as Serial General Purpose Interface Bus GPIB or Virtual Machine Environment Extended for Instrumentation VXI .

Users typically use a software driver having a distinct API provided by a manufacturer of an interface hardware to establish a communication channel with a particular control instrument. The software driver includes a library of executable functions that a computer program may call to establish the communication channel or to reconfigure the communication channel.

According to one aspect of the invention a method includes receiving a first creation command from a user interface and establishing a communication channel linking the command interpreter and the control instrument independent of the interface bus or interface hardware driver type. The method also includes providing a common communication interface between the user and the control instrument.

One or more of the following features may also be included. A user may establish a second communication channel linking the command interpreter to a second control instrument. The method may further include having a first and a second communication interface. The interfaces associated with the first and second communication channels may be of different types. The different types of communication interfaces include any of the supported interface types such as Serial General Purpose Interface Bus GPIB Virtual Machine Environment Extended for Instrumentation VXI or General Purpose Interface Bus Virtual Machine Environment Extended for Instrumentation GPIB VXI .

The communication interface type of at least one communication channel is the Virtual Instrument Software Architecture VISA protocol.

The method further includes selecting the first control instrument having a particular type of communication interface from a group of instrument interfaces having a first driver that includes the first type of communication interface and selecting the second control instrument from a group of instrument interfaces having a second driver that includes the second type of communication interface.

The user may establish the first communication channel with the first control instrument using a first instantiation command based on a first syntax. Similarly the second communication channel can also be established using a second instantiation based on the same first syntax.

In response to an interpreter command the method may further include creating a first and a second instrument object having properties associated with the first and the second communication channel respectively. The first instrument object may have a read function for receiving data from the first communication channel as well as a write function for transmitting data through the first communication channel in response to the command interpreter.

The user may also create an object array in response to an array creation command. The object array includes as elements a first and a second instrument object. The user may change the properties of the first and second communication channels by changing properties of the object array.

Prior to establishing a communication channel the method may also include detecting an available interface on a detected interface for the first communication channel and displaying the configuration of the first communication channel in response to the command interpreter to display the properties of the first instrument object.

In certain embodiments the common interface includes a command interpreter having an instrument engine operating in an array based environment. The routine may also generate timer events and event handling operations. Additionally the routine may further provide for restoring objects to the array based environment buffering data between the interface hardware and the user interface creating record files for data transfer validating parameters byte swapping and configuring object properties among others.

As yet another feature the method may establish the first communication channel by linking a compilation means to the first control instrument. The compilation means compiles a user program to a stand alone executable file when the command for compilation is received.

According to another aspect of the invention a system includes a user interface adapted to receive a first creation command a command interpreter a first control instrument and a first communication channel linking the command interpreter and the first control instrument. The system further includes a common communication interface for communicating with the first instrument.

One or more of the following features may also be included. The system may include a second control instrument and a second communication channel.

The user may establish the first and the second communication channels in the system using various supported types of communication interfaces such as Serial General Purpose Interface Bus GPIB Virtual Machine Environment eXtended for Instrumentation VXI or GPIB VXI.

The first and second communication channels may also conform to different communication protocols. The system may include control instruments having an interface selected from a group of instrument interfaces supplied by different types of drivers.

The first and second communication channels may be established in response to first and second instantiation commands respectively according to a first syntax.

The system may further include first and second configuration commands according to a second syntax for changing the configuration between each of the communication channels with their corresponding control instruments.

The system may further include first and second instrument objects associated with the first and second communication channels. The system may also include an object array having as elements the first and second instrument objects. The user may change the properties of the communication channels in response to the interpreter command to change properties of the object array.

The first instrument object may include a read function for receiving data and a write function for transmitting data through the communication channel in response to the interpreter command.

Prior to establishing a communication channel the system may also include means for detecting an available interface on a detected interface for the first communication channel and means for displaying the configuration of the first communication channel in response to the interpreter command to display the properties of the first instrument object.

According to another aspect of the invention a system for communicating with control instruments includes means for receiving a creation command from a user means for establishing a communication channel means for providing a common communication interface for communicating with control instruments and means for creating an object array having properties including a first and a second instrument object as elements of the object array.

According to yet another aspect of the invention a method includes instantiating an instrument object establishing a communication channel linking the control instrument to the instrument object writing and reading data between the control instrument and the instrument object and disconnecting the instrument object from the control instrument in response to a close function call.

The system allows a user to simplify communication with control instruments independent of the various types of interface bus standards communication protocols or types of interface hardware.

Using only one common communication interface allows users to easily set up configure and change the properties of communication channels linked to various control instruments. In this manner the system is a powerful concise mechanism that allows users to easily and quickly communicate with control instruments without laboriously learning the details of different hardware interfaces having a distinct. Application Program Interface API or driver modules. The common communication interface operates across different drivers different hardware protocols and different hardware bus standards.

Furthermore the instrument object arrays provide a powerful programming tool for users to interact with the control instruments by allowing access to complex operations without laborious user programming. A user can easily gain access to properties and data from various types of instruments using only one object array which is a vector of objects. Thus the user can easily configure an object s properties manipulate it and control the behavior of the control instruments.

Moreover the user communicates to objects of different types by using greatly simplified functions to perform complex programming operations. Therefore the user is required to have neither extensive nor detailed knowledge of hardware to benefit from using object array features in communicating with various control instruments.

The details of one or more embodiments of the invention are set forth in the accompanying drawings and the description below.

Computer further includes a processor for executing the user s commands entered by the user . Computer includes an interface hardware which is typically a separate circuit board that allows the computer to use certain kinds of peripheral devices such as each of control instruments . Each interface hardware is associated with different types of interface bus standard types such as Serial General Purpose Interface Bus GPIB Virtual Machine Environment eXtensions for Instrumentation VXI or General Purpose Interface Bus Virtual Machine Environment Extended for Instrumentation GPIB VXI . Various supported interface bus standards may be used and are not limited to those shown by exemplification in the embodiments herein. For example supported bus standard interfaces include TCP IP Transmission Control Protocol Internet Protocol UDP User Datagram Protocol VISA TCP IP USB Universal Serial Bus USB USB 2.0 IrDA standard InfraRed Data Association FireWire PXI PCI Extensions for Instrumentation VXI Parallel Port and Centronics parallel interface.

Interface hardware includes a corresponding software driver having a distinct Application Programming Interface API to link the control instruments to the computer .

Interface hardware contains one or more ports to link peripheral instruments such as control instruments to computer . For example three physical ports are shown in association with interface hardware . In turn ports connect to control instruments . For example one port individually connects through a physical connection such as cable or wire to one of the corresponding control instruments . One of the control instruments may be further connected to a system under test. System may include systems under control test and measurement equipment such as analyzers test systems calibrators data acquisition systems counter timers meters oscilloscopes DMMs generators power supplies scanners and switches and sources. Thus system relates to any system having data transfer capabilities.

User may send a list of requests or commands to processor from the GUI to establish a communication channel between the computer and the control instruments . The user does so by writing a user program which resides in memory of computer . The user program may be associated with the syntax of for example any interpreted programming environment. An interpreted programming environment may be any proprietary program that performs mathematical computations for modeling simulation graphics or data analysis related to control instruments among many others. An example of an interpreted programming environment is MATLAB from MathWorks Inc. of Natick Mass.

An interpreted programming environment includes a program referred to as a command interpreter that executes other programs. In contrast with a compiler that translates source code into machine code and stores the machine code output in a file for later execution the command interpreter analyzes statements in the user program each time it is executed and then performs the desired action. Thus the command interpreter processes the user program analyzes the meaning of each statement of the user program and sends the corresponding desired action to the common interface adaptor .

The user program coupled with the command interpreter is shown as a communication module . The communication module may also include in lieu of a command interpreter a compiler not shown for generating a stand alone executable file. The compiler is used as an intermediate step in the translation of the user program code to an non interpreted language. In other words the user would generate a program in a programmatic environment and then compile the program through the compiler. This would in turn result in a stand alone executable file that may be run independently from the user program . In other embodiments the user program may be otherwise modified for execution in other operating environments.

A common interface adaptor is an interface for communicating with various drivers having distinct APIs which in turn communicate with the different types of interface hardware . In particular the common interface adaptor connects the command interpreter to a driver causing the transfer of data and functions between the interpreter and the driver . Driver includes a software program that extends an operating system to support a peripheral device such as interface hardware of control instrument .

Driver interfaces with Serial port interface standards such as RS 232 which are widely used in Windows from Microsoft Corporation SUN from Sun Microsystems Inc. and MAC from Apple Computer Inc. Operating Systems.

Driver is also compatible with General Purpose Interface Bus GPIB known as IEEE 488.1 a standard hardware interface connection commonly used in the test and measurement industry. The GPIB interface hardware provides a corresponding software driver specific to the particular GPIB interface hardware used by a control instrument .

Furthermore driver may be a VISA driver. A VISA driver may be used with different interface bus standard types. One difference between VISA drivers and other types of drivers such as a GPIB driver is that a VISA driver allows the interface hardware to communicate using a common VISA API.

Driver can support peripheral devices such as interface hardware of any control instruments ultimately linking the user to system under test through the communication module the common interface adaptor and one of the control instruments . Driver may support various types of communication interfaces as described above.

Referring now to two processes associated with the communication system are illustrated. In order for the user to communicate with control instruments the communication system executes a programming process and an operating process . The programming process is distinct from the operating process both residing within computer of .

In the programming process the user interacts with the GUI which in turn sends and receives data from the command interpreter . The command interpreter interacts with the common interface adaptor . In short the user s requests to the command interpreter and the command interpreter s interaction with the common interface adaptor describe the programming process .

In the operating process the common interface adaptor of the programming process links to driver which in turn interfaces the interface hardware to the common interface adaptor . The common interface adaptor sends the translated user commands sent by the command interpreter to the driver . Driver processes the commands and operates the interface hardware . The driver also communicates with the interface hardware transferring data from the interface hardware to the common interface adaptor . Accordingly the operating process causes the common interface adaptor to be linked to one of the control instruments .

To better understand the invention it is helpful to clarify the general meanings of certain terms used in connection with the object oriented systems and features described hereinafter. An example object oriented language is JAVA from Sun Microsystems Inc. The JAVA programming paradigm environment is a platform independent abstracted computing model that permits one to create executable program code that is capable of running on a variety of operating systems.

An object class is a set of data attributes and functional capabilities routines encapsulated into a single logical function.

Different objects may be differentiated from other instances of the same object class by their attribute values such as the object properties and its data members and not by their routines capabilities . The term object is often used by itself to refer loosely to either an object class or an object instance the difference being understood in context.

 Attributes or properties are data elements of object classes that are expressed through particular values in object instances.

 Inheritance represents a specialization of an object class in which the specialized class shares all of the attributes and routines of the parent classes.

Here an instrument object refers to an object that provides a gateway to the instrument s capabilities and allows the user to control the behavior of the control instrument .

The instrument object also refers to an instance of a particular object class such as GPIB Serial and VISA. In particular an instrument object includes functions that are inherited by the Serial GPIB and VISA objects. A serial object contains functions that are unique to communicating with a serial port instrument. Similarly a GPIB object includes functions that are unique to communicating with a GPIB capable instrument and a VISA object has functions that are unique to communicating with instruments using the VISA standard or protocol. An instrument object has functions common across all of these different instrument objects.

An instrument object may be associated with any communication channel established between a command interpreter and a control instrument. Referring to the user may generate an instrument object in response to instantiation commands also referred to as an interpreter command. 

To accomplish interface hardware driver type and interface bus standard independence the user generates an instrument object associated with a particular communication channel linking the command interpreter to the control instruments . The user generates a creation command at the GUI to generate the instrument object.

The command interpreter processes and forwards the creation command to the appropriate type of common interface adaptor selected based on the input arguments specified in the creation command. One task of the common interface adaptor is to translate the information passed between the command interpreter and the driver associated with the instrument object. Thus the common interface adaptor allows a programming environment to be wholly independent of the type of interface hardware driver and interface bus standard.

The GPIB common interface adaptor communicates with the GPIB interface hardware. Generally each GPIB card which has a unique API requires a common interface adaptor . Since each unique driver adopts its own syntax for communicating with a GPIB interface hardware a common interface adaptor is added to translate the functions passed between the command interpreter and the corresponding driver . Although the adaptor is written using the C programming language any suitable programming language may be used.

For example a National Instruments hereinafter NI driver may have a command called ibwrt for writing ASCII data to NI interface hardware. An Agilent Technologies hereinafter Agilent driver has a similar command called hpibwrt that writes ASCII data to Agilent interface hardware.

However the command interpreter uses a writeHardwareAscii function to write ASCII data to the interface hardware. The NI common interface adaptor translates the writeHardwareAscii function to ibwrt. The Agilent common interface adaptor translates the writeHardwareAscii function to hpibwrt.

Similarly the VISA protocol requires its own common interface adaptor. In order to communicate with a control instrument using the VISA standard the command interpreter relies on the particular corresponding type of VISA software driver. The VISA software driver uses the appropriate commands for communicating with different control instruments . Similar to a GPIB common interface adaptor a VISA common interface adaptor translates the commands and requests sent from the command interpreter to the corresponding VISA driver.

Referring again to the command interpreter a Java Native Interface layer hereinafter JNI layer developed by Sun Microsystems Inc. and the common interface adaptor implement the common communication interface . Furthermore an array based environment and an instrument engine are also shown.

The array based environment includes functions used by the user to create an instrument object through function calls as well as to configure an instrument object s properties and to connect the instrument object with one of the control instruments .

The instrument engine is responsible for passing data and information from the user to the driver and back using function calls defined in the array based environment . The instrument engine takes the data either from the user or from the driver and formats it into the format that the driver or the user requested. How the data is sent and read to and from the driver depends upon the type of the driver . The user defines the driver type when the user creates an instrument object. To this end the common interface adaptor makes the communication between the instrument engine and the driver possible.

In certain embodiments the instrument engine is written in the JAVA programming language whereas the common interface adaptor is written in the C programming language. When the instrument engine communicates with the common interface adaptor the JNI layer enables this communication.

The JNI layer is a standard programming interface for writing JAVA native functions and embedding the Java virtual machine into native applications. The primary goal of the JNI layer is binary compatibility of native process libraries across all Java virtual machine implementations on a given platform. By writing programs using the JNI layer Java code can operate with applications and libraries written in other languages such as C .

For example the JNI layer can transfer data between the Java and the C programming layers. In particular the JNI layer is used because the instrument engine is written in JAVA whereas the common interface adaptor is written in the C programming language. With other programming languages different programming interfaces may be used.

When establishing a communication channel with a serial type interface hardware the instrument engine is not required to connect to a common interface adaptor. Rather the connection between the instrument engine and the serial interface is handled by an object class and interface library such as a JAVA package.

Where the JAVA programming language is used JAVA interfaces and classes are grouped into a JAVA package. In certain embodiments by using a JAVA package the user can easily access ready made interfaces classes fields constructors and functions. Therefore the instrument engine may use the functions provided in such packages to communicate with a control instrument connected to a serial port. Thus the object class and interface library may be replaced by any suitable programming package or library.

For non serial types of interfaces the following example illustrates how the user may send commands and data between the array based environment and the instrument engine and back. Referring to the commands described in this example demonstrate a process also referred to as an instrument session which the user initiates. This example shows a typical session that a user may initiate.

First user may generate a GPIB object that uses a NI driver by instantiating an instrument object in this case a GPIB object using the following instantiating function call 

The array based environment s GPIB constructor calls the instrument engine GPIB constructor. The instrument engine constructor verifies that a NI GPIB common interface adaptor exists first argument . The instrument engine constructor also configures the instrument object s properties to correspond to the constructor arguments i.e. BoardIndex 0 and PrimaryAddress 1 second and third arguments respectively . Thus prior to establishing a first communication channel with the control instrument the user detects an available interface for establishing the communication by the appropriate instantiation functions.

The instrument session includes establishing a first communication channel linking the instrument object or alternatively the first instrument object to the control instrument. The function call is 

The array based environment s fopen function calls the instrument engine s fopen function which in turn invokes the NI common interface adaptor s create function. The NI common interface adaptor s create function communicates directly with the driver made by NI which communicates with the GPIB interface hardware not shown and establishes the connection with one of the control instruments .

The user may control the behavior of the control instruments by writing and reading information through the following read and write function calls 

The array based environment s fprintf function passes the string IDN to the instrument engine s fprintf function. The instrument engine takes the string IDN and passes it to the NI common interface adaptor s write function as an argument. This function writes the string to the instrument through the NI GPIB driver .

The array based environment s fscanf function notifies the instrument engine that data should be available from the instrument . The instrument engine calls the NI common interface adaptor s read function that queries the driver for any available data which in turn queries the instrument . If data is available the data is returned to the instrument engine which then returns the data to the user . If no data is available an error code is passed back to the instrument engine . The function of the instrument engine invokes the NI common interface adaptor to translate and pass the error message to the user .

Finally the user may close the instrument session by disconnecting the instrument object from one of the control instruments with the fclose g function call.

The instantiation of the different types of instrument objects as well as a comprehensive list of their properties and functions can be found in the 112 2000 . which is incorporated herein by reference.

However the user may perform or require the execution of more complex operations such as implementing timer events event handling restoring the object to the array based environment log data to disk parameter validation data type casting buffering of data byte swapping property configuration and translation of error codes.

For instance the instrument engine includes routines for generating timer events and event handling. Implementing timer events involves using events and callbacks. For example while the instrument object is connected to an instrument events can be used to display a message display and analyze data or perform any other callback. Therefore an instrument session also supports event based acquisition that allows callbacks to be generated into the array based environment when a specified event occurs. To this end each instrument object includes a set of callback properties. When an event is generated the callback associated with the event is executed. For example in a MATLAB environment the GPIB timer event type has TimerAction and TimerPeriod as its associated callback properties. Accordingly a timer event is generated when the time specified by the TimerPeriod property passes. Time is measured relative to when the object is connected to the instrument .

The instrument engine also includes routines for restoring the object to the array based environment . Object storage and retrieval allows serial port GPIB or VISA objects for example to be saved and reloaded to and from a memory location such as memory . This allows an instrument object to be recreated in the array based environment from a previous user session in the array based environment . When saving an instrument object any data that may be in the instrument object s input or output buffer is not saved. Data in the object s input buffer can be read into the array based environment and saved separately. Upon loading the value of any read only property is restored to default values.

The instrument engine also provides routines for finding an instrument object which has been created but whose handle or reference has been lost. When an instrument object is created the object is stored in the instrument engine . The user can create as many references or handles as desired to this object. If the user loses the reference to the instrument object the instrument engine routines are able to restore the instrument object from the instrument engine back to the array based environment. The user has the ability to restore all instrument objects in this manner from the instrument engine or the user can specify a set of properties and property values that the instrument object to be restored must have.

Routines are also provided for buffering data to be sent to the interface hardware and buffering data read from the interface hardware . Buffering data to be sent to the interface hardware is performed using an output buffer. An output buffer is computer memory allocated by the instrument object to store data that is to be written to the instrument . The flow of data from the user to the instrument proceeds as follows 1 the data specified by a write function is sent to the output buffer and 2 the data in the output buffer is sent to the instrument . In some embodiments one property specifies the maximum number of bytes that you can store in the output buffer. Another property indicates the number of bytes currently in the output buffer.

On the other hand an input buffer includes memory allocated by the instrument object to store data that is to be read from the instrument . In this case the flow of data from the instrument to the user would follow these steps 1 data read from the instrument is stored in the input buffer and 2 the data in the input buffer is returned to the variable specified by the read function. Data from consecutive reads are automatically appended in the input buffer.

The instrument engine further provides routines for creating a record file. The record file is an ASCII file that contains a record of one or more instrument control sessions. Data transferred between the array based environment and the instrument and any events that may have occurred can be saved to a text file also referred to as a record file. A compact and detailed record file may be created. A compact record file contains a description of the data that was sent between the array based environment and the instrument a description of the events which occurred the number of values written to the instrument the number of values read from the instrument the data type of the values and event information. A detailed record file contains the same information as the compact record file along with the actual data that was transferred between the array based environment and the instrument .

ASCII data sent between the array based environment and the instrument is stored as text in the record file.

 This is described above Binary data with precision given by uchar schar u int8 u int16 or u int32 is recorded as hexadecimal values. For instance if the decimal value 255 is read from the instrument as a 16 bit integer the hexadecimal value 00FF is saved in the record file. Single and double precision floating point numbers are recorded as decimal values using the g format and as hexadecimal values using the format specified by the IEEE Standards 754 1985 for Binary Floating Point Arithmetic.

Moreover recording information to disk provides a permanent record of the instrument control session and provides an easy way to debug user program . The instrument engine provides the capability to perform the above identified complex operations and features. In communicating with the instrument these complex operations are encapsulated into simpler function calls once the user has created one instrument object.

By way of illustration shows how the user may use the common communication interface of by establishing two or more communication channels. The common communication interface is shown in association with drivers and .

The user establishes a first communication channel . This is done in response to a first creation command not shown . The first communication channel links the common communication interface to the first control instrument . Subsequently the user may open a second communication channel in response to a second creation command not shown . The second communication channel links the common communication interface to the second control instrument . The first and second communication channels may be supported simultaneously so that a user has access to and can control both communication channels and at the same time.

Interface hardware may support GPIB VXI or Serial interfaces and different types of interface hardware may supply the driver with its own unique API. Interface hardware has ports and supporting the different types of interface buses attached to the control instruments and .

After establishing the first communication channel the user may open second communication channel using the same interface hardware . However the user is not limited to using interface hardware . The second communication channel may be established using a different interface hardware in this case interface hardware . This communication channel is shown as communication channel . In this example driver and interface hardware are used to connect the common communication interface to the control instrument via a physical port .

Therefore user may establish various communication channels linking the common communication interface specifically the command interpreter of to the control instruments independent of the type of interface bus standard type and interface hardware type.

Describing the driver interchangeability feature of the common communication interface a first interface driver hardware type may supply the driver and interface hardware whereas a second interface driver hardware type may supply the driver and interface hardware . Moreover the interface bus standards implemented in ports and may be of various different types. But irrespective of the different types of interface driver hardware and the type of interface bus standard used the communication system exposes only one common communication interface to the user . This way communication with any and all control instruments is facilitated.

When the user establishes the first communication channel the user does so through a particular type of communication interface such as Serial GPIB VXI or GPIB VXI. Similarly the user establishes a second communication channel through a different type of communication interface. Thus the first and the second communication interfaces may include respectively interfaces of a first and second type.

Furthermore the first communication channel is consistent with a particular type of communication protocol provided by the first interface driver hardware type. In other words a first interface hardware would provide a consistent and compatible driver namely in the form of a first communication protocol necessary for establishing the first communication channel .

In the same vein the user would establish the second communication channel through a second communication protocol provided by a second interface hardware .

When the instrument engine handles more than one communication channels the array based environment of the common communication interface is a powerful tool. The array based environment can simplify the communication with a control instrument in significant ways. Objects of different classes or of the same class may be combined into one object array. For example the user may generate an object array of only Serial port objects or an array of Serial port and GPIB objects. An object array is defined as a collection of identically typed objects namely an array of instrument objects merely distinguished by their indices or subscripts. For example 

Many array based functions allow the user to operate on an array of instrument objects i.e. fopen fclose and stopasync. An array of instrument objects is generated by concatenating different instrument objects similar to creating an array of variables by concatenating the variables together. The user creates an object array in response to an array creation command to the command interpreter.

 using one call the EOSMode property of g and v can be configured to the same value set x EOSMode read 

No restrictions or limitations exist on the use of object arrays. In particular the user may create as many instrument objects as required or needed without limitations concerning the number of objects in an object array. Moreover array objects may use any instrument object of any particular interface hardware having a corresponding and unique API.

Although the invention preferably relates to instrumentation control other fields of application especially in the broad sector of communication systems are within the scope of the invention. Thus a number of embodiments of the invention have been described. Accordingly it will be understood that various modifications may be made without departing from the scope of what is presented in the following claims.

