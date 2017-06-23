---

title: Method and apparatus for modifying a platform-independent programming language build tool
abstract: One embodiment of the present invention provides a system that facilitates modifying a platform-independent programming language build tool to aid in the development and testing of smart card applications. The system operates by creating a task in the platform-independent programming language build tool that allows a user to perform functions associated with the development and testing of smart card applications. Next, the system extends the platform-independent programming language build tool interface to include the task so that the task is executable by the user. Note that making the task part of the platform-independent programming language build tool interface reduces the overhead involved in performing functions associated with developing and testing smart card applications.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09032359&OS=09032359&RS=09032359
owner: Oracle America, Inc.
number: 09032359
owner_city: Redwood Shores
owner_country: US
publication_date: 20051103
---
The present invention relates to development tools for computer software. More specifically the present invention relates to a method and an apparatus for modifying a platform independent programming language build tool.

As applications and programming languages are becoming more complex programmers are increasingly using build tools to help develop and maintain their applications. Build tools help programmers manage files and classes as well as simplifying many of the tasks programmers perform while developing applications.

However build tools are not without their limitations. Build tools often provide tasks and commands that cover basic programming language functions however they typically do not provide easy access to language extensions or third party functions that may be required for specific applications. Often when a programmer needs to utilize a function from a third party or a function that is not common for the majority of developers the programmer uses a generic build tool task and manually specifies all of the necessary information for the function in question. If an application uses these functions extensively using a generic build tool can be almost as time consuming and complex as not using a build tool.

Hence what is needed is a method for increasing the versatility of a build tool without the problems listed above.

One embodiment of the present invention provides a system that facilitates modifying a platform independent programming language build tool to aid in the development and testing of smart card applications. The system operates by creating a task in the platform independent programming language build tool that allows a user to perform functions associated with the development and testing of smart card applications. Next the system extends the platform independent programming language build tool interface to include the task so that the task is executable by the user. Note that making the task part of the platform independent programming language build tool interface reduces the overhead involved in performing functions associated with developing and testing smart card applications.

In a variation of this embodiment the platform independent programming language build tool is the Apache Ant Java build tool.

In a variation of this embodiment the task is a bridge to a predefined external task. In this variation the system passes parameters associated with the task to the predefined external task.

In a further variation the predefined external task can include a Java Card Application Protocol Data Unit APDU tool a Java Card converter tool a Java Card verification tool a Java Card CAP file generation tool a Java Card mask generation tool a Java Card script generation tool or a Java Card deployment tool.

In a variation of this embodiment extending the platform independent programming language build tool interface involves creating an Application Programming Interface API which facilitates activating the task.

TABLE 1 illustrates exemplary usage of a converter task in accordance with an embodiment of the present invention.

TABLE 2 illustrates exemplary usage of an export to text task in accordance with an embodiment of the present invention.

TABLE 3A illustrates exemplary usage of a verify CAP file task in accordance with an embodiment of the present invention.

TABLE 3B illustrates exemplary usage of a verify revision task in accordance with an embodiment of the present invention.

TABLE 3C illustrates exemplary usage of a verify export task in accordance with an embodiment of the present invention.

TABLE 4 illustrates exemplary usage of a script generation task in accordance with an embodiment of the present invention.

TABLE 5 illustrates exemplary usage of a deployment task in accordance with an embodiment of the present invention.

The following description is presented to enable any person skilled in the art to make and use the invention and is provided in the context of a particular application and its requirements. Various modifications to the disclosed embodiments will be readily apparent to those skilled in the art and the general principles defined herein may be applied to other embodiments and applications without departing from the spirit and scope of the present invention. Thus the present invention is not intended to be limited to the embodiments shown but is to be accorded the widest scope consistent with the principles and features disclosed herein.

The data structures and code described in this detailed description are typically stored on a computer readable storage medium which may be any device or medium that can store code and or data for use by a computer system. This includes but is not limited to magnetic and optical storage devices such as disk drives magnetic tape CDs compact discs and DVDs digital versatile discs or digital video discs .

Smart card contains a computational engine which includes circuitry for performing computational operations. Smart card also contains a number of different types of memory including random access memory RAM electrically erasable programmable read only memory EEPROM and read only memory ROM .

In general RAM can include any type of volatile random access memory EEPROM can include any type of writeable non volatile memory such as EEPROM flash memory or magnetic memory and ROM can include any type of read only memory.

RAM is used to store various data items and data structures such as a system stack . System stack is described in more detail below with reference to .

ROM includes a virtual machine such as the JAVA virtual machine developed by SUN Microsystems Inc. of Santa Clara Calif. Note that applications written in a platform independent programming language such as the JAVA programming language can be executed on virtual machine . Also note that in one embodiment of the present invention smart card is a Java Card .

ROM also contains a number of applications and which provide services for clients accessing smart card . Other applications such as application can be located in EEPROM . Yet other applications not illustrated may be located in both ROM and EEPROM .

ROM may also include a card manager which contains code for managing the execution of applications on smart card . For example suppose a platform independent programming language build tool wishes to access a service provided by one of the applications on smart card . Note that platform independent programming language build tool may access a service provided by one of the applications directly or through a third party set of tools such as the Java Card tools in the Java Card reference implementation. Platform independent programming language build tool first communicates with card manager step A . Card manager puts platform independent programming language build tool in contact with an application step B . This allows platform independent programming language build tool to communicate directly with application step C . Note that card manager can also delete objects from memory. This object deletion process is described in more detail below with reference to .

EEPROM contains a number of objects which are accessed by applications . More specifically application accesses object application accesses objects and and application accesses object . Other objects that have become unlinked are not referenced by any application. It is desirable to delete these unreferenced objects to free up memory space in EEPROM . The process of deleting these unreferenced objects is described in more detail below with reference to .

One embodiment of the present invention provides a system for implementing modifying a platform independent programming language build tool to aid in the development and testing of smart card applications such as applications . presents a flowchart illustrating the process of modifying a platform independent programming language build tool in accordance with an embodiment of the present invention.

The system starts by creating a task in the platform independent programming language build tool that allows a user to perform functions associated with the development and testing of smart card applications step . Next the system extends the platform independent programming language build tool interface to include the task so that the task is executable by the user step . Note that making the task part of the platform independent programming language build tool interface reduces the overhead involved in performing functions associated with the development and testing of smart card applications. This allows the programmer to work directly with tasks within the platform independent programming language build tool without having to perform the work included in maintaining external tasks and links.

The following is an implementation of Apache Ant tasks for Java Card tools in accordance with one embodiment of the present invention. Apache Ant is a Java based build tool that is extended using Java classes and is configured through XML based configuration files. see http ant.apache.org Because Apache Ant uses Java classes and XML configuration files the build files themselves are platform independent. These Apache Ant tasks are basically designed to enhance user experience with the Java card tools and enable user to incorporate usage of Java card tools in their builds more easily and seamlessly.

The Java Card reference implementation comes with suite of Java Card tools to help developers develop verify and test their Java Card applications. But to use these tools in an Apache Ant build requires using a standard Java Ant task. This makes using Java Card tools in an Apache Ant build very cumbersome and error prone.

Java Card Ant tasks are designed to enhance user experience with Java Card tools and enable users to use Java Card tools in their Apache Ant builds more easily and seamlessly. Java Card Ant tasks are also designed to take care of some of the manual steps such as editing of script files for CAP download required to run some of the tools.

ConverterTask This task is used to enable usage of the Java card converter to create CAP files Java Card Applet JCA files and Export EXP files 

VerifyRevTask This task is used to verify binary compatibility between two versions of an export file 

ScriptgenTask This task is used to generate Application Protocol Data Unit APDU script files for download in cref and

DeployCAPTask This task given a CAP file downloads the CAP file in the Java card c reference cref and saves the resulting EEPROM image in an output EEPROM file.

Note that all task classes inherit from JavaCardTaskBase class which is responsible for setting command line options that are common between all Java card tools. Each task class has set methods for each command line option parameter and an execute method which is called by Apache Ant to start the task.

All of the tasks take a certain number of parameters provided through an Apache Ant script. For details on which of these parameters are required and which are optional please refer to Java card user s guide.

The converter task is used to invoke the Java card converter to create JCA CAP and EXP files from an input package. Following is a list of converter options that can be used from within an Apache Ant script 

noverify The verifier is not invoked to verify the generated CAP file. This option can be specified by putting noverify true in the conversion target in the Apache Ant Task 

Appletnameaid This is a nested element since there can be more than one applets in a package. The values that are required for this element are appletName which is the fully qualified name of the applet class and the AID of the applet and

ConfigFile If parameters to the converter are supplied in a config file this parameter must be supplied since this provides a fully qualified path to the config file.

TABLE 1 illustrates exemplary usage of a converter task in accordance with an embodiment of the present invention.

The Exp2Text task converts an export file into a human readable text file. Parameters that are input to this task are 

classdir Root directory for input. This is the directory where the system will look for the export file 

TABLE 2 illustrates exemplary usage of an export to text task in accordance with an embodiment of the present invention.

Verifier tasks are implemented as three different classes which are VerifyCAPTask VerifyRevTask and VerifyExpTask. All these classes inherit from the base verifierTask class which is used to set command line options parameters that are common to all the three tasks. Since multiple Export files can be mentioned on the verifier command line export file name had to be a nested value in the task which is why class ExportFileName has been declared to set export file names. Command line parameters that are common between all the verifier tasks iclude the following 

nowarn Sets no warn option in the verifier so that the verifier doesn t throw any warning messages and

The VerifyCAP task is used to verify CAP files. Command line parameters and options that can be set for this task are as follows 

ExportFileName Required This is a configured value and must be declared as illustrated in the following example.

TABLE 3A illustrates exemplary usage of a verify CAP file task in accordance with an embodiment of the present invention.

The VerifyRev task is used to verify binary compatibility between two different versions of an export file. This task only takes export files as arguments. This class only implements the execute method since it only requires two export files on the command line handled in the super class .

TABLE 3B illustrates exemplary usage of a verify revision task in accordance with an embodiment of the present invention.

The VerifyExp task verifies an export file. This class also implements the execute method only which is responsible for executing the task. Export file input is handled by the super class.

TABLE 3C illustrates exemplary usage of a verify export task in accordance with an embodiment of the present invention.

The Scriptgen task is used to convert a CAP file into a script file for download in cref. Parameters required for this are 

NoBeginEnd This flag tells Scriptgen that CAP begin and CAP end APDUs are not to be included in the output file 

FooterFile This is the name of the footer file and path to the footer file which is to be appended to the script which can be used to create applet instances etc. .

TABLE 4 illustrates exemplary usage of a script generation task in accordance with an embodiment of the present invention.

The DeployCap task is responsible for taking a CAP file downloading it into cref and creating a resulting cref EEPROM image containing the downloaded CAP file . This also facilitates 1 downloading CAP files in cref since it hides the steps of using scriptgen to generate script files 2 starting cref with proper parameters and 3 running APDUTool to download the script file in to cref. Parameters required for this task are 

TABLE 5 illustrates exemplary usage of a deployment task in accordance with an embodiment of the present invention.

The foregoing descriptions of embodiments of the present invention have been presented for purposes of illustration and description only. They are not intended to be exhaustive or to limit the present invention to the forms disclosed. Accordingly many modifications and variations will be apparent to practitioners skilled in the art. Additionally the above disclosure is not intended to limit the present invention. The scope of the present invention is defined by the appended claims.

