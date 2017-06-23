---

title: Supervisor program
abstract: A supervisor program () for monitoring a self-service terminal () executing a terminal application suite () is described herein. The supervisor program () comprises: an internal interface () for communicating with the terminal application suite () to collect supervisor information and at least one supervisor utility (). Each supervisor utility () is configured to collate specific information and each utility () has an external interface () for directly communicating the collated information to a service provider () external to the terminal (). This enables the external service provider () to determine if the terminal () requires attention. A method of supervising a self-service terminal is also described.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08708226&OS=08708226&RS=08708226
owner: NCR Corporation
number: 08708226
owner_city: Duluth
owner_country: US
publication_date: 20051103
---
The present invention relates to a supervisor program. In particular the present invention relates to a supervisor program for use with a self service terminal SST such as a kiosk or an automated teller machine ATM and to an SST incorporating such a supervisor program.

Self service terminals are generally public access devices that are designed to allow a user to conduct a transaction or to access information in an unassisted manner and or in an unattended environment. SSTs typically include some form of tamper resistance in both hardware and software so that they are inherently resilient to faults and unauthorized access. SSTs include i ATMs ii non cash kiosks that allow users to access information for example to view reward points on a reward card the user has inserted into the SST print documents for example aircraft boarding cards and such like and iii kiosks that accept payment for services for example Web surfing kiosks photo printing kiosks kiosks that allow users to buy goods kiosks that dispense medication and such like . The term SST has a relatively broad meaning and may include vending machines and photocopiers.

An ATM is one type of SST and typically includes a cash dispenser for dispensing currency to a user subsequent to identifying the user and validating that the user has sufficient funds to cover the amount of currency to be dispensed.

An ATM operates under software control. Typical ATM software includes operating system software a run time platform and a control application CA although these have been listed as three separate items the run time platform and the control application may be combined into a single terminal application suite.

The operating system is typically a conventional personal computer operating system such as a Microsoft Windows NT trade mark operating system. As is well known in the art the operating system is responsible for memory process task and disk management and sends high level commands to device drivers that control devices in the ATM. The operating system may be integrated into the run time platform.

The run time platform is used for i interfacing with the operating system ii providing device drivers for non standard computing devices for example cash dispenser devices and iii providing industry standard interfaces application programming interfaces APIs to the control application and any other applications executing on the ATM. These industry standard interfaces enable the control application to make use of self service devices PIN pads cash dispensers and such like and to obtain device status and fault management information.

Typical industry standard interfaces include a CEN XFS extensions for Financial Services interface published by the European Committee for Standardization an Active XFS interface a device status management DSM interface and such like. The CEN XFS interface enables ATM peripherals such as cash dispensers card readers encrypting PIN pads and printers to interface with Windows based applications. The Active XFS interface sits on top of that is it provides an interface to the CEN XFS interface and provides a simpler mechanism for accessing the CEN XFS interface.

The control application CA includes a transaction processing component TPC and a management component MC .

The TPC offers a user a suite of transactions and services by providing the processing logic and presentation functionality through which a cardholder can perform transactions. The TPC executes XFS compliant commands which are implemented by the run time platform.

The management component MC records status fault and other information about the ATM and captures and handles errors to ensure that the ATM does not unexpectedly go out of service. Furthermore the MC provides supervisory functions to monitor the operation of the ATM and includes an industry standard communication facility to report status information and errors to a remote management station.

The MC includes a system application that allows a service engineer to access the status and fault information stored within the ATM. By accessing the status and fault information the engineer can more easily diagnose problems and determine if any action needs to be taken for example replenishment operations or maintenance tasks .

It is common for the major ATM vendors and independent ATM software providers to sell a terminal application suite that integrates the run time platform and the control application CA so that all of the functions are provided by a large monolithic application.

Providing a single software suite that does all these functions has the disadvantage that it is unlikely that any one suite has the best in class implementation of each function to be performed by that suite.

Another disadvantage is that the software transmits all status and fault information to a single communication facility which then forwards the status and fault information as appropriate.

It is among the objects of an embodiment of the present invention to obviate or mitigate the above disadvantages or other disadvantages associated with prior art self service terminal applications and or systems.

According to a first aspect of the present invention there is provided a supervisor program for monitoring a self service terminal executing a terminal application suite the supervisor program comprising an internal interface for communicating with the terminal application suite to collect supervisor information at least one supervisor utility each utility being configured to collate specific information and each utility having an external interface for directly communicating the collated information to a service provider external to the terminal to enable the external service provider to determine if the terminal requires attention.

By matching the specific information collated by a supervisor utility with information required by a service provider a dedicated supervisor utility can be provided for each service provider. By allowing the supervisor utility to contact the service provider directly the service provider can immediately address any problems reported by the supervisor utility.

It should be appreciated that the term service provider when used herein refers to an organization that dispatches people or other resources such as software to repair maintain or replenish a self service terminal.

It should be appreciated that the term directly as used herein to describe the communication between a supervisor utility and an external service provider does not mean that there cannot be any device between the supervisor utility and the external service provider. In practical embodiments there may be many routers handlers and such like that convey network traffic. However the term directly as used in this context means that there is a dedicated link between the utility and the service provider to allow the service provider to interrogate the utility and the utility to convey information to the service provider. This dedicated link may be provided by a network shared with other service providers.

Although each supervisor utility has its own interface a common structure may be provided to allow each utility to communicate via a common mechanism for example an SNMP simple network management protocol agent structure or Web Services may be used to allow all of the supervisor utilities to communicate with their respective service providers via a common internet IP network connection.

It should be appreciated that the supervisor program is separate from the terminal application suite and can be installed at a different time to installation of the terminal application suite.

As used herein the term internal interface refers to an interface between two or more software entities executing on an SST.

As used herein the term external interface refers to an interface between a software entity executing on an SST and one or more software entities executing on a device external to the SST.

The terminal application suite preferably comprises a run time platform and a control application CA .

The supervisor program may interface with the run time platform either directly or via the CA. The run time platform may incorporate an operating system or may be installed separately from an operating system.

The supervisor program may communicate with a routing agent for routing all information to a management station. This enables the management station to log all information sent from the supervisor utilities to the external service providers. This may be useful as evidence that information was sent to an external service provider in the event that the external service provider denies receiving that communication. This also provides the management station with a holistic view of the terminal. Thus the supervisor program may have two types of communication channel i a direct channel to a service provider and ii a central channel to a management station. In typical installations there may be multiple direct channels each to a different service provider but only one central channel. These channels may be implemented as distinct logical channels for example as different ports on an IP address.

Preferably the internal interface is an XFS interface allowing communication using XFS compliant commands. The particular type of internal interface used is not important provided it is an open interface used by terminal application suite vendors so that the supervisor program may communicate with the terminal application suite using standard commands.

The routing agent may be implemented by an SNMP Simple Network Management Protocol agent. Alternatively any convenient industry standard or proprietary routing agent may be used. The SNMP agent preferably routes supervisor information from the supervisor program to a management centre that collates all state of health and diagnostic information relating to that terminal.

The supervisor utilities may be implemented in a single executable file alternatively the supervisor utilities may be implemented as separate components. Each utility is preferably a concurrently executing routine for example a software agent or a software object having an agent or object interface respectively.

Preferably the supervisor utilities include one or more of the following utilities a first line maintenance utility a replenishment utility a second line maintenance utility a vendor mode utility a view of device status and state of health and a fraud manager. It will be apparent to one of skill in the art that any type of maintenance repair or replenishment operation relating to a self service terminal and triggered by a status time or fault condition in the terminal could be implemented using a supervisor utility.

The first line maintenance utility preferably receives terminal information such as counters and tallies data status data and replenishment data. This enables the first line maintenance personnel to receive information about any media jams or misfeeds occurring within the terminal.

In embodiments using a replenishment utility the replenishment utility may be interconnected to a replenishment service provider via a dedicated interface. The replenishment service provider may receive information about counters and tallies logs settlement data and replenishment data.

The dedicated interface may implement a client server communication architecture. The dedicated interface may utilize push technologies.

Web Services are self contained self describing modular applications that can be published accessed and invoked across the Web. A Web Service performs a function. Once a Web Service is deployed other applications and other Web Services can discover and invoke the deployed service.

A Web Service is described using a description language called WSDL Web Services Description Language so that once a program accesses a WSDL description of a Web Service the program has everything it needs to make use of that Web Service.

Conveniently SOAP simple object access protocol is used to package requests for Web Services and responses from Web Services.

The dedicated interface may use a predefined port on an IP network and may use HTTP hyper text transfer protocol to communicate SOAP packets.

Using Web Services or an SNMP structure enables the replenishment service provider to contact the replenishment utility directly to determine the amount of media remaining in the terminal and or the amount of media presented to users. The media may be currency valuable documents such as blank tickets receipt paper or such like.

One advantage of using Web Services is that a single open interface can be developed for use with each supervisor utility but each service provider can develop its own Web based programs for accessing these Web Services. This enables each service provider to create its own programs for accessing the supervisor utility thereby easing problems associated with integrating such programs into the service provider s enterprise architecture.

In some embodiments a plurality of replenishment utilities may be used one for currency one for tickets and such like. Each replenishment utility may communicate with a different replenishment service provider.

The second line maintenance utility may be interconnected to a technician service provider via a dedicated interface such as a Web Services interface . This enables the technician service provider to dispatch a technician to the terminal in the event of a failure of one of the devices within the terminal without having to await a request from the management centre.

The second line utility may provide information about counters and tallies status data diagnostic self test data logs including hardware inventories software inventories and device information and replenishment data. Hardware inventories include identification of terminal part numbers. Software inventories include identification of installed components and revision levels. Device information includes firmware levels and part numbers.

The management centre may gather supervisor information from the terminal application suite including the control application the run time platform and devices mounted within the terminal . Thus the management centre may collate all supervisor information from the terminal but does not have to request service providers to assist the terminal as each supervisor utility communicates directly with one or more of the service providers.

By virtue of this aspect of the present invention a supervisor program is provided that informs a management centre of status information including any problems within a terminal and also informs an appropriate remote service provider directly thereby reducing the time taken to obtain assistance.

Furthermore this aspect of the invention allows a supervisor program to be used with any run time platform and control application provided the platform and application comply with the internal open interface. This enables an organization to use a single type of supervisor program in multiple terminals where some of the terminals execute a run time platform and CA provided by one vendor and other terminals execute a platform and CA provided by a different vendor. This ensures that a best in class supervisor program can be selected.

Having supervisor utilities that can communicate directly with service providers facilitates efficient outsourcing of terminal monitoring maintenance and replenishment operations.

According to a second aspect of the present invention there is provided a method of supervising a self service terminal executing a terminal application suite the method comprising communicating with the self service terminal application suite via an internal interface to collect supervisor information in at least one supervisor utility and communicating the collected supervisor information directly to a service provider external to the terminal so that the external service provider can remotely monitory the status of the terminal.

The method may include the further step of communicating the collected supervisor information to a remote management centre via a routing agent. Thus information from multiple supervisor utilities may be communicated to the remote management centre while each supervisor utility transmits its own information to a dedicated service provider.

According to a third aspect of the present invention there is provided a self service terminal supervisory system comprising a self service terminal and a plurality of service providers at locations external to the terminal the terminal comprising a supervisor program including a first interface to a terminal application suite and a plurality of supervisor utilities the supervisor utilities having a second interface directly accessible to each of the external service providers to enable each external service provider to obtain direct access to supervisor information collated by the supervisor program.

Reference is first made to which is a perspective view of a self service terminal in the form of an ATM executing a supervisor program according to one embodiment of the invention. Reference is also made to which is a schematic diagram illustrating the ATM of and showing internal devices mounted within the ATM .

The ATM has a chassis shown in dotted line to which is pivotably coupled a plastic fascia covering an upper portion of the chassis and secured thereto by a lock mechanism . A door is hingably coupled to a lower portion of the chassis . When the fascia is unlocked and hinged open and the door is swung open an operator can gain access to devices located within the ATM .

The fascia provides a user interface to allow a user to interact with the ATM . In particular the fascia has apertures aligning with devices when the fascia is pivoted to the closed position.

The fascia defines a card reader slot aligning with a card reader device a receipt printer slot aligning with a receipt printer device a display aperture aligning with a display and associated function display keys FDKs disposed as two columns each on opposing sides of the display a keypad aperture through which an encrypting keypad device protrudes and a dispenser slot aligning with a dispenser device

With the exception of the encrypting keypad the devices are all mounted within the chassis . The encrypting keypad is mounted on a shelf portion of the fascia which extends outwardly from beneath the display aperture

Referring now to the ATM also includes the following internal devices that are not directly viewed or accessed by a user during the course of a transaction. These devices include a journal printer device for creating a record of every transaction executed by the ATM a network connection device for accessing a remote authorization system not shown and a controller device in the form of a PC core for controlling the operation of the ATM including the operation of the other devices . These devices are all mounted within the chassis of the ATM .

The controller comprises a BIOS stored in non volatile memory a microprocessor associated main memory storage space in the form of a magnetic disk drive and a display controller in the form of a graphics card.

The BIOS microprocessor main memory disk drive and graphics card are all replaceable modules within the controller device

The display is connected to the microprocessor via the graphics card installed in the controller and one or more internal controller buses . The other ATM devices and to are connected to the ATM controller via a device bus and the one or more internal controller buses .

When the ATM is booted up the microprocessor accesses the magnetic disk drive and loads the main memory with software components as will be described with reference to which is a schematic diagram illustrating how software components interact in main memory .

The microprocessor loads an operating system kernel into the main memory . In this embodiment the operating system is a Windows NT trade mark operating system available from Microsoft Corporation. The operating system includes a plurality of device drivers . . . for interfacing with standard computing devices such as the magnetic disk drive the display a serial port a parallel port and such like. As is well known in the art the operating system kernel is responsible for memory process task and disk management and includes routines for implementing these functions.

The microprocessor also loads a run time platform into the main memory . In this embodiment the runtime platform is a set of APTRA trade mark XFS components available from NCR Corporation 1700 S. Patterson Blvd. Dayton Ohio 45479 U.S.A. The run time platform provides a range of programming facilities specific to self service terminal devices and services.

One function of the run time platform is to enhance the operating system so that the operating system and run time platform together provide high level access to all of the devices including both standard computing devices via the operating system and non standard computing devices via the run time platform . Thus the combination of the run time platform and the operating system can be viewed as providing a complete ATM operating system.

The platform comprises a plurality of self service device drivers . . . that interface with self service specific devices. Although only three device drivers are shown there are many device drivers in the platform one for each self service specific device such as the card reader the receipt printer the FDKs the encrypting keypad and the cash dispenser . Furthermore there are many more devices in an ATM than those described herein for example there are more standard computing devices such as serial ports and a parallel port there are also more self service devices such as a rear operator panel. These devices are not discussed herein because they are not essential to an understanding of the invention.

The platform also includes support files not shown for use with the self service drivers to allow each device to operate. For each self service device the driver and any associated support files enable that device to be operated tested maintained and configured. The platform also includes drivers to facilitate encrypted communication between the devices for example between the card reader and the controller between the printer and the controller and such like.

If a new device is to be added to the ATM then a corresponding driver and any associated support files are also added. Thus the platform provides the environment needed for the ATM s self service devices to be operated and maintained.

The microprocessor also loads a control application CA into the main memory . The CA provides transaction processing functions for customers and for maintenance personnel and device management functions.

For clarity and to aid understanding the control application is represented in as comprising two logical parts a transaction processing part for implementing transaction processing functions and a management part for implementing device management functions. Each of these parts comprises a plurality of objects each object performing a predetermined function. However it should be appreciated that the particular structure used to implement these functions is a matter of design choice for example the control application may be implemented as a single monolithic program or as a set of discrete objects that can interact with one another.

The transaction processing part includes a customer transaction processing object an operation transaction processing object and a session manager object .

The management part includes a transaction management object a device management object and a system application object .

In this embodiment objects in the transaction processing part interact with objects in the management part either directly via an object interface or indirectly via an open interface to the platform .

The open interface is a standard interface for making use of self service devices referred to herein as a CEN XFS API . This CEN XFS interface is used to instruct the devices to perform operations and is also used to obtain device status and fault management information.

The customer transaction object provides processing logic and presentation information to allow a customer to execute a transaction at the ATM . The customer transaction object controls the presentation of screens to an ATM customer to guide a customer through a transaction.

The term screen is used herein to denote the graphics text controls such as menu options and such like that are presented on an SST display the term screen as used herein does not refer to the hardware that is the display that presents the graphics text controls and such like. Typically when a transaction is being entered at an SST a series of screens are presented in succession on the SST display the next screen displayed being dependent on a customer entry or activity relating to the current screen. For example a first screen may request a customer to insert a card once a card has been inserted a second screen may invite the customer to enter his her PIN once the final digit of the PIN has been entered a third screen may invite the customer to select a transaction and so on.

The operation transaction object provides processing logic and presentation information typically presented on a rear operator panel which is not shown in the drawings to allow maintenance personnel such as technicians or replenishers from a service provider to execute replenishment or diagnostic operations at the ATM . The operation transaction object controls the presentation of information to an ATM service engineer to guide the engineer through a replenishment or diagnostic operation.

The session object provides persistence throughout a consecutive sequence of interactions. For an ATM transaction a session may cover the duration of a transaction from a customer entering a card into the ATM card reader slot to the customer concluding a transaction at that ATM for example by retrieving the card or dispensed cash. A session may also cover the duration of a replenishment or diagnostic operation performed by a maintenance person the duration of a request from the ATM to a third party information provider such as a CRM database or advertisement provider or such like.

In the management part the transaction management object records information relating to the status and operation of the customer transaction object and the operation transaction object . For example the transaction management object records when the customer transaction object is active and the current state and or screen of the customer transaction object . Similarly the transaction management object records when the operation transaction object is active that is when a maintenance person or other authorized person is replenishing maintaining or diagnosing the ATM and the current state and or screen the operation transaction object is in. The transaction management object also records any regular data sent by the transaction objects to indicate that these objects are operating normally sometimes referred to as a heartbeat . The transaction management object also records significant events of the customer or operation transaction objects . These significant events include when the customer transaction object is out of service.

In the management part the device management object collates status and fault information from the devices via the run time platform and operating system and makes this information available to the system application object .

The system application object provides an operator not an ATM customer but a maintenance person such as a service engineer or other authorized person with access to functions required to configure diagnose and maintain the ATM . The following seven system application functions in addition to some others are available from the system application via the operation transaction processing object 

These seven functions are implemented by accessing the device management object and are explained in more detail below.

Some self service devices are able to clear themselves when instructed to do so for example a card reader and a receipt printer. These operations are referred to herein as maintenance operations and can be performed by a maintenance person implementing the maintenance function from the system application .

Typically each self service device is able to perform one or more tests on itself to determine if it is operating correctly. This is referred to herein as a device self test and can be initiated via the system application .

Windows NT trade mark records entries relating to software operations for example a time out or a failure in accessing an object device operations and communication operations for example failure to receive an expected response to a message . These entries are referred to herein as event logs and the system application allows the operator or engineer to view these event logs search and filter these event logs and copy these event logs to a diskette or print them out.

A service tally provides a list of the times at which a service has been requested for a particular device since the tally was last reset. Typically only service engineers can reset a tally. In this context a service relates to software used to access functionality provided by a self service device for example dispense cash is a service associated with the cash dispenser device . This allows the customer transaction processing object to be able to issue a dispense cash request to the platform together with the amount to be dispensed and the platform provides the low level commands required to instruct the cash dispenser to dispense the amount of cash requested.

Care should be taken to distinguish between two different uses of the word service herein. The first use relates to software or an interface providing functionality to the control application or some other application. The second use relates to repair replacement replenishment cleaning or such like operations performed by a service engineer. It should be clear from the context which particular meaning is intended.

The device status list displays a list of all the devices having states that require attention. For example a cash dispenser device may have a currency cassette that requires replenishment. The following information is provided for each device state requiring attention device name this is the name of the device that requires attention description this is a short description of the problem attention this shows whether the state requires attention now or will require attention soon user category this specifies what type of user is able to deal with the state for example a service engineer or an operator who clears media jams . Typically a service engineer will be authorized to perform more operations than an operator. An operator may only be allowed to clear jams in a printer replenish a printer with printable media and such like.

The device status list includes replenishment states where a consumable item such as currency or a paper roll for a printer needs replaced and fault states where a fault exists such as a paper jam in a printer that needs to be cleared .

The device servicing function enables a service engineer to service in the sense of repair replace replenish clean or such like a device even if that device does not report that it requires servicing. Once the service engineer has performed the service the device servicing function automatically tests the serviced device to ensure that it is operating correctly. One example of a device servicing action may be emptying a purge bin.

The self service device configuration function allows an operator or engineer to display and set hardware and software parameters such as the language used alarms and such like. A service engineer can also use the self service configuration function to set a printer active to allow the device status list event logs service tallies or such like to be printed by the ATM .

These seven system application functions operate by sending requests and receiving responses via the object interface between the operation transaction processing object and the system application .

The management part includes fault handling capabilities to cope with any faults or exceptions thereby ensuring that the ATM does not suddenly go out of service for example during a transaction. In particular the fault handler capability of the management part deals with critical errors such as processor exceptions and memory protection violations operating system exceptions device exceptions kernel level exceptions catastrophic software problems persistent failures and power failures.

An ATM SNMP agent handler is instantiated in main memory to manage certain communications with software entities external to the ATM as will be described in more detail below.

The ATM SNMP agent handler also communicates with a plurality of sub agents one of which is an application and device sub agent to direct agent requests to an appropriate sub agent and to forward agent responses to an external software entity.

The application and device sub agent receives fault and status information from the platform and the control application and conveys this received information to a remote management centre illustrated in and described with reference to below .

At this point reference will also be made to which is a block diagram illustrating a system including the ATM .

In the ATM is coupled to an IP network in the form of a private intranet. The remote management centre introduced with reference to is also connected to the ATM via the IP network . A first line maintenance organization a second line maintenance organization and a currency replenishment organization are also connected to the ATM via the IP network . Each of these organizations to is coupled to the IP network by an external SNMP agent manager to located within each respective organization. These organizations are service providers for the ATM .

Referring again to the final part of the initialization procedure is for the microprocessor to load a supervisor program into the main memory .

The supervisor program interfaces with the CA via an open interface labeled API in . In this embodiment the open interface is an ActiveX interface. The supervisor program also interfaces with the platform via an XFS interface labeled XFS in .

The supervisor program is shown in more detail in which is a schematic diagram illustrating components within the supervisor program .

The supervisor program comprises three supervisor utilities . Each supervisor utility is a sub agent that communicates with the ATM SNMP agent handler .

Supervisor utility provides dedicated information to the first line maintenance organization . Supervisor utility provides dedicated information to the second line maintenance organization . Similarly supervisor utility provides dedicated information to the currency replenishment organization .

Each of these three utilities can access the management part particularly the device management object to retrieve relevant information. For each utility relevant information is information that can be used to determine if the dedicated organization needs to take any action to maintain the ATM in working order.

As an example sub agent monitors certain devices and modules within those devices to determine if a first line maintenance person needs to take any action. A first line maintenance person can generally perform operations that do not require any tools such as clearing misfeeds replacing rolls of paper in printers and such like. Typically the sub agent obtains status information from the receipt printer and the journal printer . This status information includes details of the amount of media paper remaining within each printer details of how many print operations have been performed and such like.

Sub agent provides dedicated information to the second line maintenance organization and monitors every device within the ATM and all modules within those devices because the second line maintenance person needs to be able to fix any problem that arises within the ATM .

Sub agent provides dedicated information to the currency replenishment organization and monitors the currency dispenser to determine if the ATM needs more currency.

Referring again to each external SNMP agent manager interfaces with an enterprise application . The enterprise application such as conveys information received by the respective external SNMP agent manager to individuals or automated processes within the organization . Similarly the enterprise application allows individuals or software entities within the organization to send requests to the ATM via the external SNMP agent manager . The external SNMP agent manager conveys this request to the ATM SNMP agent handler which routes this request to the sub agent dedicated to the organization . The sub agent receives this request via the interface component and conveys it to the processing component

The processing component in each sub agent is able to generate a trap to indicate a status change or a fault and the interface component conveys this trap to the dedicated organization. This feature of generating a trap is provided in accordance with the SNMP standard.

The processing component within each sub agent is able to access status and fault information stored in the device management object for those devices that require management by the organization to which that sub agent is dedicated. Thus each sub agent has a view of the status and fault information from a set of devices .

The ATM SNMP agent handler conveys all status and fault information from the ATM which may be transmitted from the application and device sub agent the first line maintenance sub agent the second line maintenance sub agent or the replenishment sub agent to the remote management centre . This ensures that the remote management centre receives all the status and fault information sent to the organizations to .

When the ATM is in use if a paper misfeed occurs within the receipt printer then the device management object records this status change and notifies the appropriate sub agents. One mode of operation may only notify the first line maintenance sub agent . Another mode of operation may notify both the first and second line maintenance sub agents . A third mode of operation may notify the first line maintenance sub agent first and then the second line maintenance sub agent only if a first line maintenance person has not cleared the misfeed within a predetermined time period.

If there is a print head failure while the ATM is in use the second line maintenance organization will receive a trap from its dedicated sub agent . A person or a software entity within the organization will be notified of this event via the enterprise application and will dispatch a maintenance person to repair the ATM .

If the amount of currency stored within the dispenser falls below a predetermined level while the ATM is in use the currency replenishment organization will receive a trap from its dedicated sub agent . A person or software entity within this organization will be notified of this event via the enterprise application and will dispatch a cash in transit vehicle to replenish the ATM with currency.

It will now be appreciated that this embodiment of the present invention allows different organizations to manage an ATM and to receive status and fault information directly from the ATM being managed.

Various modifications may be made to the above described embodiment within the scope of the present invention for example in other embodiments the supervisor utility may comprise more or fewer than three supervisor utilities.

In other embodiments Windows trade mark Management Instrumentation WMI may be used to manage data collation. WMI is a component of the Microsoft trade mark Windows trade mark operating system and is the Microsoft trade mark implementation of Web Based Enterprise Management WBEM which is an industry initiative to develop a standard technology for accessing management information in an enterprise environment. WMI uses the Common Information Model CIM industry standard to represent systems applications networks devices and other managed components.

In other embodiments different supervisor utility structures may be used for example Web Services may be used instead of or in addition to an SNMP agent structure.

