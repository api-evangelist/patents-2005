---

title: System for providing secure access
abstract: A system implementing secure access to management information, the system () comprising: an open management service () including an open management application programming interface (); a managed object () generating management information; and an object interface () for (i) receiving management information from the object, (ii) converting the received management information into a format accessible to the open management service, and (iii) providing the management information to the open management service () in response to a valid request from a client (). The system further comprises an authorization component () for verifying an access code () associated with the request to determine if the client () is authorized to issue the request.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07546300&OS=07546300&RS=07546300
owner: NCR Corporation
number: 07546300
owner_city: Dayton
owner_country: US
publication_date: 20050622
---
The present invention relates to a system for providing secure access and to a secure access method. In particular the present invention relates to a system and method for providing secure access to management information in an open management system.

Open management systems are non proprietary management systems that use standard technology to allow client programs to access management information in an enterprise environment. Open management systems provide a consistent definition and structure of data including expressions for elements such as object classes properties associations and methods.

To ensure interoperability across a network comprising different types of programs and devices where these programs and devices are provided by different vendors open management systems provide an interface for requesting and for describing data about programs and devices. This interface enables administrators and software management programs to access the same type of information from many different types of devices and programs on different platforms for example different operating systems using the same commands.

This open management system interface is made publicly available to allow clients to be programmed to browse and query management information via the management system. The management information may relate to software resources such as installed programs and or hardware resources such as storage devices and memory .

It is proposed herein to use an open management system in a self service terminal SST such as a kiosk or an automated teller machine ATM .

Self service terminals are generally public access devices that are designed to allow a user to conduct a transaction or to access information in an unassisted manner and or in an unattended environment. SSTs typically include some form of tamper resistance in both hardware and software so that they are inherently resilient to faults and unauthorized access. SSTs include ATMs non cash kiosks that allow users to access information for example to view reward points on a reward card the user has present to the SST and kiosks that accept payment for services for example Web surfing kiosks photo printing kiosks kiosks that allow users to buy goods and such like . The term SST has a relatively broad meaning and may include vending machines and photocopiers.

An ATM is one type of SST and typically includes a cash dispenser for dispensing currency to a user subsequent to identifying the user and validating that the user has sufficient funds to cover the amount of currency to be dispensed.

An ATM includes a variety of different hardware devices and typically executes an operating system a run time platform to augment the operating system and one or more control programs.

The run time platform is used for i interfacing with the operating system ii providing device drivers for non standard computing devices for example cash dispenser devices and iii providing industry standard interfaces application programming interfaces APIs to the control program and any other programs executing on the ATM. These industry standard interfaces enable the control program to use standard commands i to make use of self service devices PIN pads cash dispensers and such like and ii to obtain device status and fault management information.

The control program CP typically includes a transaction processing component TPC and a management component MC .

The TPC offers a user a suite of transactions and services. The TPC provides the presentation functionality to guide the user through steps involved in a user selected transaction and provides the processing logic to lead the ATM through steps involved in performing the user selected transaction.

The management component MC records status fault and other information about the ATM and captures and handles errors to ensure that the ATM does not unexpectedly go out of service. Furthermore the MC provides supervisory functions to monitor and test operation of the devices and programs in the ATM.

To ensure that these devices and programs are operating correctly an ATM has an elaborate state of health system. This state of health system also ensures that service personnel have access to diagnostic information about how the ATM is operating. This information typically includes logs and tallies about i the operations that each device has performed ii the number of times a device has been used iii any error messages reported by a device and such like.

Different service personnel may have different levels of access to the ATM. For example there may be three types of service personnel. A first type of service personnel may only be authorized to clear media jams replenish non currency media such as receipt paper and such like. These personnel are generally referred to as first line maintenance personnel and typically do not require any tools to perform their maintenance functions. A second type of service personnel may be authorized to perform diagnostic tests on some ATM devices to reset certain logs and counters and such like. These personnel are generally referred to as second line maintenance personnel and typically carry a set of tools to help them perform their maintenance functions. A third type of service personnel may be authorized to replenish currency in the ATM. These personnel are generally referred to as currency replenishers and typically do not perform any maintenance functions.

It is also important to ensure that each of the three types of authorized service personnel only has access to information consistent with their level of authorization. For example only second level maintenance personnel should have access to certain highly secure information such as tamper detection information and only currency replenishers should have access to currency replenishment operations.

To provide a value added maintenance service an ATM vendor prefers to restrict access to detailed diagnostic information to service personnel associated with or approved by that vendor. It is therefore desirable to be able to restrict access to the most detailed information to those service personnel who are authorized by the ATM vendor rather than to personnel who are authorized by the ATM owner. This is relatively easy to achieve if the ATM vendor uses proprietary hardware and software however to reduce the cost of an ATM it is desirable to include as many non proprietary devices and applications as possible such as a Microsoft trade mark Windows trade mark operating system.

The Windows trade mark operating system includes an open management system referred to as Windows Management Instrumentation WMI which is proposed herein to be used to provide the state of health system in an ATM.

One disadvantage of using WMI is that it is an open management system so there is no simple way to provide a level of access control to WMI that allows an ATM vendor to include intelligent management information and to discriminate between vendor authorized and vendor unauthorized client access thereto. WMI does provide a mechanism for using Windows trade mark authentication such as domain logon credentials as an authorization mechanism but the set up and management of Windows trade mark users controlled by the ATM owner who has access to the ATM operating system not the ATM vendor.

It is among the objects of an embodiment of the present invention to obviate or mitigate the above disadvantage or other disadvantages associated with prior art open management systems and or prior art state of health systems.

According to a first aspect of the present invention there is provided a system for providing secure access to management information the system comprising an open management service including an open management application programming interface a managed object generating management information and an object interface for i receiving management information from the object ii converting the received management information into a format accessible to the open management service and iii providing the management information to the open management service in response to a valid request from a client the system further comprising an authorization component for verifying an access code associated with the request to determine if the client is authorized to issue the request.

The managed object may be hardware for example a device or software. The management information may relate to operational information such as the number of times a predetermined event has occurred status information such as the state of a sensor or such like.

Preferably the access code is provided as part of the request for management information. Conveniently the access code is provided in the IWbemContext parameter field of an IWbemServices call to Windows trade mark Management. Windows Management makes no use of the information contained within an IWbemContext parameter field but simply forwards it to the object interface.

This aspect of the present invention has the advantage that the object interface can determine whether a client application has sufficient authorization to permit the client to receive the requested information. This is a more secure method than relying on login credentials such as a password used to access the operating system as these can be circumvented by the operator of the operating system. By ensuring that a valid access code is required for each request for management information it is more difficult to circumvent this secure access system.

According to a second aspect of the present invention there is provided a method of providing secure access to management information in an open management system the method comprising receiving a request for management information from a client analyzing the request to identify an access code indicating an authorization status of the client and providing the requested management information to the open management service in the event that the authorization status satisfies a predetermined criterion.

Preferably analyzing the request further comprises identifying a specific parameter field used to convey data and reading the contents of that parameter field.

Preferably the method further comprises accessing the requested management information and providing a subset of the accessed management information in the event that the authorization status does not satisfy the predetermined criterion. This ensures that some information may be viewed by any client but other information is restricted to those clients that are authorized to view such information. When implemented in an ATM this ensures that the ATM owner can use personnel not authorized by the ATM vendor if the ATM owner so chooses. Alternatively the method further comprises providing none of the requested management information in the event that the authorization status does not satisfy the predetermined criterion. This alternative may be used if the requested management information is highly secure information.

Preferably the method further comprises providing the client with an access code for incorporating into a request for management information. This enables the access code to be incorporated automatically each time the client makes a request for management information.

Providing the client with an access code may be implemented by the client receiving an access code from a human operator and incorporating the access code into a request for management information. The access code may be input from an operator by the operator typing the access code into the system or by inserting storage media such as a diskette CDROM DVD or Flashcard and transferring the access code from the storage media to the system or by transmitting the access code from a portable device such as a portable digital assistant or a cellular radio frequency telephone in a wireless manner. The storage media may be a diagnostic media including diagnostic commands and or menus. Alternatively providing the client with an access code may be implemented by providing the system with one or more dongles or by providing software including the access code where the software is accessible by the client.

The access code may include an access or security level for example level one two or three where level three provides the most complete access to management information. The access code may also include an identifier indicating the identity of the owner of the system. This would enable an audit log to be kept to indicate which personnel accessed management information when they accessed the information and such like.

The access code is preferably encrypted to prevent anyone from tampering with the access code and increasing the security level to a level they are not entitled.

By virtue of this aspect of the present invention the client application provides an access code with every request for management information. The access code is decoded compared with a list of valid codes and access is either granted denied or partially denied.

According to a third aspect of the present invention there is provided a self service terminal comprising a plurality of modules each module having one or more managed objects associated therewith for accessing management information associated with the module and an object interface for i receiving management information from the objects ii converting the received management information into a format accessible to a management service and iii providing the management information to the management service in response to a request therefor.

Reference is first made to which is a perspective view of a self service terminal in the form of an ATM including a secure access system according to one embodiment of the invention. Reference is also made to which is a schematic diagram illustrating the ATM of and showing internal devices mounted within the ATM .

The ATM has a chassis shown in dotted line to which is pivotably coupled a plastics fascia covering an upper portion of the chassis and secured thereto by a lock mechanism . A door is hingably coupled to a lower portion of the chassis . When the fascia is unlocked and hinged open and the door is swung open an operator can gain access to devices located within the ATM .

The fascia provides a user interface to allow a user to interact with the ATM . In particular the fascia has apertures aligning with some of the devices when the fascia is pivoted to the closed position.

The fascia defines a card reader slot aligning with a card reader device a receipt printer slot aligning with a receipt printer device a display aperture aligning with a display and associated function display keys FDKs disposed as two columns each on opposing sides of the display a keypad aperture through which an encrypting keypad device protrudes and a dispenser slot aligning with a dispenser device

With the exception of the encrypting keypad the devices are all mounted within the chassis . The encrypting keypad is mounted on a shelf portion of the fascia which extends outwardly from beneath the display aperture

Referring now to the ATM also includes the following internal devices that are not directly viewed or accessed by a user during the course of a transaction. These devices include a journal printer device for creating a record of every transaction executed by the ATM a network connection device for accessing a remote authorization system not shown and a controller device in the form of a PC core for controlling the operation of the ATM including the operation of the other devices . These devices are all mounted within the chassis of the ATM .

The controller device comprises a plurality of modules including a non volatile memory storing a BIOS BIOS NVRAM a microprocessor main memory associated with the microprocessor storage space in the form of a magnetic disk drive and a display controller in the form of a graphics card.

The BIOS NVRAM microprocessor main memory disk drive and graphics card are all replaceable modules within the controller device

The display is connected to the microprocessor via the graphics card installed in the controller and one or more controller buses . The other ATM devices and to are connected to the ATM controller via the one or more controller buses

Each device and some modules within a device for example the microprocessor main memory disk drive and graphics card are managed objects. In this embodiment a managed object is a logical component for example a disk partition or a physical component for example a device within the ATM that is capable of providing management information.

Reference is now made to which is a block diagram illustrating modules within the cash dispenser device

The cash dispenser has a cassette module for holding currency to be dispensed. A pick module is provided for picking currency items banknotes from the cassette and conveying them to a transport and note thickness module . The transport module conveys the picked banknote from the pick module to a stacking wheel module . The transport module also detects the thickness of the picked banknote to determine if more than one banknote has been picked in a single operation. If more than one banknote has been picked the picked banknotes are conveyed to a purge bin instead of the stacking wheel . If only one banknote has been picked then that banknote is transported to the stacking wheel . Once all requested banknotes have been picked and transported to the stacking wheel the banknotes are stripped from the stacking wheel as a bunch and presented to an ATM customer via a presenter module . A control board is provided to control the operation of the cash dispenser and a communications module is provided to communicate with the controller device

When the ATM is booted up the microprocessor accesses the magnetic disk drive and loads the main memory with software components as will be described with reference to which is a schematic diagram illustrating how software components interact in main memory

The microprocessor loads an operating system kernel into the main memory . In this embodiment the operating system is a Windows NT trade mark operating system available from Microsoft Corporation. The operating system includes a plurality of device drivers . . . for interfacing with standard computing devices such as the magnetic disk drive the display a serial port a parallel port and such like. For clarity only two device drivers are illustrated in .

As is well known in the art the operating system kernel is responsible for memory process task and disk management and includes routines for implementing these functions.

The operating system includes an open management service in the form of a Windows trade mark WMI service .

The operating system also includes a registry and a plurality of standard providers . Although there are many standard providers for clarity only three are shown in . These standard providers are supplied by Microsoft with the Windows trade mark NT operating system and interface with standard PC devices and components such as the registry main memory a USB port and such like . Providers expose a rich set of instrumentation information for the devices and components they are associated with.

The microprocessor also loads a run time platform into the main memory . In this embodiment the runtime platform is a set of APTRA trade mark XFS components available from NCR Corporation 1700 S. Patterson Blvd. Dayton Ohio 45479 U.S.A. The run time platform provides a range of programming facilities specific to self service terminal devices and services.

One function of the run time platform is to enhance the operating system so that the operating system and run time platform together provide high level access to all of the devices including both standard computing devices via the operating system and non standard computing devices via the run time platform . Thus the combination of the run time platform and the operating system can be viewed as providing a complete ATM operating system.

The platform comprises a plurality of self service device drivers . . . that interface with self service specific devices. Although only two device drivers are shown there are many device drivers in the platform one for each self service specific device such as the card reader the receipt printer the FDKs the encrypting keypad and the cash dispenser . Furthermore there are many more devices in an ATM than those described herein for example there are more standard computing devices such as serial ports and a parallel port there are also more self service devices such as a rear operator panel. These devices are not discussed herein because they are not essential to an understanding of the invention.

The platform also includes support files not shown for use with the self service drivers to allow each device to operate. For each self service device the driver and any associated support files enable that device to be operated tested maintained and configured. The platform also includes drivers to facilitate encrypted communication between the devices for example between the card reader and the controller between the printer and the controller and such like.

If a new device is to be added to the ATM then a corresponding driver and any associated support files are also added. Thus the platform provides the environment needed for the ATM s self service devices to be operated and maintained.

In general there is at least one provider for each managed object but there may be more than one provider for each object.

The microprocessor also loads a control program CP into the main memory . The CP comprises a transaction processing component TPC and a management component MC . The management component also includes an access control AC sequence which is described in more detail below.

The CP interfaces with the platform via an open financial interface and an open management interface . The open financial interface is a standard interface for making use of self service devices referred to herein as a CEN XFS API . This CEN XFS interface is used to instruct the devices to perform operations. The open management interface is an API application programming interface in the Windows trade mark operating system implementing WMI. The WMI interface is used to obtain management information including device status and fault data.

The TPC provides processing logic and presentation information to allow a customer to execute a transaction at the ATM by controlling the presentation of screens to an ATM customer to guide a customer through a transaction.

The term screen is used herein to denote the graphics text controls such as menu options and such like that are presented on an SST display the term screen as used herein does not refer to the hardware that is the display that presents the graphics text controls and such like. Typically when a transaction is being entered at an SST a series of screens are presented in succession on the SST display the next screen displayed being dependent on a customer entry or activity relating to the current screen. For example a first screen may request a customer to insert a card once a card has been inserted a second screen may invite the customer to enter his her PIN once the final digit of the PIN has been entered a third screen may invite the customer to select a transaction and so on.

The TPC also provides processing logic and presentation information typically presented on a rear operator panel which is not shown in the drawings to allow maintenance personnel such as technicians or replenishers from a service organization to execute replenishment or diagnostic operations at the ATM . The TPC controls the presentation of information to an ATM service engineer to guide the engineer through a replenishment or diagnostic operation.

The management component MC performs device management functions. The MC records information relating to the status and operation of the ATM . For example the MC records when an ATM customer is using the ATM and when a maintenance person or other authorized person is replenishing maintaining or diagnosing the ATM .

The MC also provides an operator not an ATM customer but a maintenance person such as a service engineer or other authorized person with access to functions required to configure diagnose and maintain the ATM .

The CP is a management program that accesses management information from managed objects using the WMI service .

WMI is built on an industry standard known as the Common Interface Model CIM . CIM defines an object oriented model and meta model for defining managed entities. CIM provides a consistent definition and structure of data including expressions for elements such as object classes properties associations and methods.

The WMI service moves and stores information about managed objects and comprises a CIM object manager CIMOM and a repository

The CIMOM performs a broker function that registers all managed objects and the classes associated with those managed objects and stores this information as a mapping in the repository . This enables the CIMOM to determine what managed objects to access in response to a query received from the CP .

In addition to the mapping information the repository stores WMI related static data. This static data may include information such as the weight of each device.

Managed objects include the operating system the registry file systems devices modules in devices for example modules to driver information and such like.

The WMI service acts as a mediator between the control program and a provider . The provider may be either standard that is non proprietary or self service specific . Providers communicate with the WMI service via a COM interface. Each provider is associated with a managed object such as a device a module within the device the registry or such like . A managed object communicates with the WMI service via its dedicated provider .

The WMI service knows where to pass information because the providers register their location with the WMI service using the CIMOM as a broker . Each provider also registers its support for particular operations such as data retrieval modification deletion enumeration or query processing. The WMI service uses this provider registration information to match CP requests with the appropriate provider .

The WMI service interacts with the CP through a COM component object model interface. When a management client makes a request through the COM interface the WMI service determines whether the request involves static or dynamic data. If the request involves static data such as the name of a managed object the CIMOM retrieves the data from the repository . If the request involves dynamic data such as the amount of memory a managed object is currently using the CIMOM always passes the request on to a provider associated with the managed object.

The main purpose of the provider is to extract management information from the managed object using whatever interface the managed object presents. The extracted management information is then mapped into object classes compatible with WMI.

When a provider finishes processing a request by extracting information and then mapping the extracted information the provider returns the result object classes back to the CIMOM . In turn the CIMOM forwards the result on to a management client through the COM interface.

The CP and the providers access CIM classes via the WMI service . CIM classes are populated typically using a Managed Object Format MOF compiler and added to the WMI repository to enable them to be accessed by the CP and the providers . MOF is the language used to describe the providers and CIM classes so that the WMI service can understand their functions. For each class the MOF file contains the access level and the provider for that class.

The WMI service standard providers self service specific providers and WMI API comprise an open management system providing secure access to management information.

Reference is now also made to which is a table listing examples of statistical information available from a pick module statistics class associated with the pick module

The first column indicates the name used by a method call to retrieve information. This information may be fixed such as the caption or description of the pick module or this information may be variable such as counter information.

The second column indicates the source of the information to be retrieved which may be either the MOF or the provider . If the source of the information is the MOF then the information that is the value to be retrieved is hard coded into the pick module MOF so it is static information retrieved from the repository . If the source of the information is the provider then the pick module provider dynamically provides the value of the information.

The third column indicates if the statistical information can be reset. This only applies to the variable information that is the counters.

Some of the counters are relative indicating the number of tallies since the counter was last reset. An example of this is the BillsPicked counter row . Other counters are absolute indicating the number of tallies since the pick module was installed. An example of this is the TotalBillsPicked counter row .

Other counters listed in table are self explanatory and are listed to illustrate some of the management information that may be obtained using the open management system .

Reference is now also made to which is a table listing examples of some CIM classes that are used for obtaining management information from managed objects in ATM . These CIM classes are accessed by the CP and the providers to convey information there between.

CIM class table comprises three columns for each CIM class entry an NCR base CIM class column indicating the name of an NCR base CIM class an access level column indicating what level of access rights are required to view information from that CIM class and a description column giving a textual description of the function of the CIM class.

The NCR base CIM classes are those classes that are common to all the self service specific devices in the ATM that is these classes are available for every self service specific device in the ATM . For example there will be an NCR Dispenser class for the cash dispenser that corresponds to the NCR Device base CIM class there will also be an NCR Printer class for the receipt printer that corresponds to the NCR Device base CIM class. The non self service specific devices for example communication ports network cards and such like have different class hierarchies.

The NCR base CIM classes are defined in a base MOF file. The base MOF file includes information about the level of authorization required by that class. In this way the NCR base CIM classes define the access level for all sub classes and this access level is propagated to all sub classes and instances.

Each row entry in CIM class table relates to a different CIM class. For example row contains a CIM class referred to as NCR Device which provides details of the device being queried. In this embodiment at least one instance of this class NCR Device exists at all times and its values persist even after an ATM reset operation is performed. Another example is row which contains a CIM class referred to as NCR DevicePart which provides information about parts or modules within a device being queried. For example if the pick module is queried then the NCR Device class would return as shown in row of NCR CashDispDevice and the NCR DevicePart class would return PickModule .

There are three access levels listed in CIM class table level and . Level allows all WMI clients such as CP to have unrestricted access to information contained within that CIM class level requires a first level of authorization level requires a higher level of authorization than level . Therefore level access is used for the most sensitive information. In this embodiment level access is restricted to service personnel approved by NCR Corporation trade mark because NCR Corporation is the vendor of the ATM in this embodiment.

Because the NCR base CIM class includes the access level indication this access level indication is propagated to all sub classes and instances of these classes. This is achieved by a using a qualifier in each sub class and instance derived from the NCR base CIM class. Furthermore access levels can be applied to classes that do not inherit from NCR base CIM classes.

The CP and the providers use an IWbemServices interface to convey an access code for validating that the CP is authorized to access management information. More information on the IWbemServices interface and on WMI in general is available from Microsoft Corporation trade mark and at http msdn.microsoft.com.

The parameter field contains an IWbemContext object which is used to convey additional information to providers . In this example an access control AC sequence is used as context values for the IWbemContext object that is the AC sequence is used by the control program to populate the IWbemContext object.

The AC sequence comprises an access level field and a client identifier field . In this embodiment there are only three different access levels to so the access level field only needs to be a two bit field however a 32 bit unsigned long VT UI4 context value is used for the access level field and the other bits are used as padding to improve security. The client identifier field is a thirty two bit field that uniquely identifies the owner of the ATM so a 32 bit unsigned long VT UI4 context value is used for the client identifier field . A third 32 bit unsigned long VT UI4 context value is used to provide a digital signature and or checksum for the first two context values to reduce the possibility of tampering with the access level field and or the client identifier field . The first two context values are encrypted using a secret algorithm and a digital signature and or checksum for the encrypted first two context values is provided as the third context value to prevent tampering for example by changing the access level . The AC sequence comprises the three encrypted context values and is stored in the CP in that form.

In this embodiment the CP has an access level coded into the access control sequence . This enables the CP to retrieve any information from the CIM classes listed in CIM class table .

The standard providers do not assess the access level of the CP . This is because the standard providers are used to obtain information about non proprietary devices and all management information associated with the non proprietary devices is made available to any client requesting the information.

The self service providers must be able to determine what access level is required to access each class to enable them to limit access to a CP having the required access level for receiving the information requested. This is achieved by adding qualifiers to each class when that class is created. Qualifiers are the generic mechanism CIM provides for incorporating additional information into classes.

In the open management system the MOF file for every object class is populated with two qualifiers a name string matching the name of the defined base class and an access level string that combines the name of the defined base class and the client CP access level required to allow the client to access information associated with that class.

The name string corresponds to the name of the NCR base CIM class listed in column of table . The access level in this embodiment is either zero one or two. When a class is derived from another class for example Dispenser TamperDetails would be derived from NCR TamperDetails then the name string qualifier of the derived class is the name of the class from which it is derived. Thus the Dispenser TamperDetails class has a name string qualifier with the text NCR TamperDetails . For each class the associated MOF file includes details of the access level and any class from which that class is derived.

Both the name string and the access level are combined and encrypted using a secret algorithm the result is then stored in the access level string as a double word value. The access level string may also be digitally signed and or checksummed. This may be used to reveal any subsequent tampering for example to reduce the access level. The contents of the access level string then serve as a signature for defining access to a class and for validating that the access level required to access that class has not been modified.

When a self service provider decrypts the access level string it compares the contents of the name string with the decrypted name from the access level string to ensure that they match. If there is no match then the name in the name string may have been changed. This may indicate that the class name has been changed to obviate the security provisions provided by the access level.

If someone attempts to breach security by changing both the access level string and the name string then the provider can determine from the associated MOF file that the class is not actually derived from the class identified by the modified qualifier name string and prevent access to the requested information. If they take a further step to alter the actual base class defined by the MOF files then the provider will no longer function correctly since the class definition will be incorrect.

WMI does not support passing of IWbemContext objects during an event registration process or at the point of event indication. To overcome this potential hole in security this embodiment only permits event notifications that indicate what managed object should be queried by the CP thereby ensuring that a query must be made before the information is divulged.

Operation of the open management system within the ATM will now be described with reference to which is a flowchart illustrating a query made by the CP for statistical information and which illustrates pictorially.

The CP which is a WMI management client creates a request step for information. In this example the request is for statistical information from the pick module in particular the request is for the number of bills picked since a bill pick counter in the module was last reset.

The NCR base CIM class used is shown in row of table . The request takes the form IWbemServices CreateInstanceEnum BillsPicked flags pIWbemContext .

The CIMOM receives the request determines which provider should receive the request by accessing from the repository a list of the managed objects that support the function requested and conveys the request to the appropriate provider step . In this example a self service provider the dispenser provider is determined to be the appropriate recipient of the request.

The provider receives the request decrypts step the IWbemContext object from the parameter field of the IWbemServices information containing the access control sequence and then analyses step the decrypted AC sequence to determine the identification of the client management program CP and the level of authorization of the client management program.

The provider accesses the repository to obtain the access level required to receive this information step .

The provider then compares step the CP access level from the decrypted AC sequence with the required access level to determine if the CP is authorized. The provider also ensures that the name string qualifier and the access level qualifier for that class are correct and match the corresponding details in the MOF file for that class.

The access level required for this request is level as indicated in row of table so the CP does have the required level of access. However if the CP did not have the required level of access then the provider would return a result indicating that there are no instances of the class available in other words it would respond step to the CP but it would not provide the requested information.

In this example the CP does have the required access level. The provider uses proprietary commands to retrieve the information so the provider first converts the request from WMI format to the proprietary format step .

The provider uses this format to query step the pick module to obtain the value of the number of bills picked since the counter was last reset.

The pick module responds to the provider step by providing the requested information in the proprietary format.

The provider converts the requested information from the proprietary format to the WMI format step and then responds step to the CIMOM by conveying the WMI format information.

The CIMOM responds to the CP step so the CP receives the value requested which is the number of bills picked since the pick module counter was last reset.

The CP can use this information itself or can forward to some other entity either within or external to the ATM . For example the CP may provide an operator interface to allow an ATM engineer to obtain statistical information from the ATM devices and modules via the CP .

The provider also logs step the request in a file on the controller device . The provider records the client identification together with the request that was made and an indication of whether the client was authorized to make the request. This file serves as a log that can be used as an audit trail.

It will now be appreciated that this embodiment of the present invention allows an ATM vendor to limit access to sensitive data to those applications and personnel having the required access level.

Various modifications may be made to the above described embodiment within the scope of the present invention for example in other embodiments an SST other than an ATM for example a non cash kiosk may be used.

In other embodiments the format of the data structures the number of fields the number of bits in a field and such like may differ from those described in the above embodiment.

In the above embodiment keyless encryption is used to encrypt the access control object which means that the algorithm used is fixed and provides security that is similar to a client specific password scheme. This is a balance between security and operational overhead. As ATMs may not have the required infrastructure to cope with secure key management for applications an audited password based scheme is selected as a reasonable compromise. However in other embodiments more robust encryption techniques may be used such as secret key encryption public private key encryption and such like.

In the above embodiment the authorization component is implemented by the providers however in other embodiments the authorization component may be implemented by a different software routine.

In other embodiments the access codes used by a client may be centrally managed by a SST vendor. Because there is no protection against copying access codes from one SST to another which is analogous to divulging a password it is important to maintain an accurate audit trail not just for one SST but for a network of SSTs. Such an audit trail would be used to trace a particular WMI client using an access code at an SST to the original licensed user or entity associated with that access code. A database storing client identifiers and associated licensee information may be provided. The client identification codes used at each SST are logged and or reported as WMI events so that the database receives this information automatically.

