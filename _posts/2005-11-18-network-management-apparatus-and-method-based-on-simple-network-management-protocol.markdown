---

title: Network management apparatus and method based on simple network management protocol
abstract: An apparatus and method is provided for managing a communication device using Simple Network Management Protocol (SNMP). When a developer creates an SNMP interface header file through an application program at a compile time, an extractor generates a management information base (MIB) file and object identifier information (OIDInfo) on the basis of the interface header file. When a manager makes an SNMP request at a run time, an agent sends the OIDInfo included in the SNMP request message to an OIDInfo processor. The OIDInfo processor refers to an OIDInfo memory and delivers general message service (GMS) information to the agent. A GMS request/response process between the agent and the application program is then performed on the basis of the GMS information.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08812636&OS=08812636&RS=08812636
owner: Samsung Electronics Co., Ltd.
number: 08812636
owner_city: Suwon-si
owner_country: KR
publication_date: 20051118
---
This application claims the benefit under 35 U.S.C. 119 a of Korean Patent Application No 10 2004 0094795 entitled Network Management Apparatus and Method Based on Simple Network Management Protocol filed in the Korean Intellectual Property Office on Nov. 18 2004 the entire disclosure of which is incorporated herein by reference.

The present invention relates generally to an apparatus and method for managing a network device. More particularly the present invention relates to a network management apparatus and method for managing a communication device using Simple Network Management Protocol SNMP .

Integrated network management is difficult because of the rapid growth of networks in several past years and the advent of various heterogeneous systems. As networks scale up network device management is becoming essential in many fields.

Therefore network managers need a network framework for comprehensive management in various network environments. Due to this need the main standards organization for the Internet i.e. Internet Engineering Task Force IETF has adopted Simple Network Management Protocol SNMP corresponding to a relatively simple protocol as a standard for managing a network device based on the Internet.

In a conventional SNMP system a management system is referred to as a manager and a management target is referred to as an agent. A management information transmission network for connecting the manager to the agent is based on Transmission Control Protocol Internet Protocol TCP IP and communication using SNMP uses a command for retrieving management information a command for successively retrieving management information a command for changing and writing management information and a command for reporting an exceptional operation on the basis of a management information base MIB between the manager and the agent.

The SNMP agent is a software module placed in a management target device and has information about the MIB. This information is delivered to the SNMP manager using SNMP.

Specific information resources and so forth that are to be managed using SNMP are referred to as objects. A collection of the objects is referred to as the MIB. The format of the MIB is defined as part of the SNMP and the objects are defined using Abstract Syntax Notation One ASN. 1 .

The SNMP agent manages an MIB configured by parameters relating to a network device function. The SNMP manager obtains a specific value from MIBs provided by SNMP agents and identifies a device state or changes the value.

As described above an operation for conventionally managing a network using SNMP denotes an operation for obtaining a specific value from MIBs provided by management target devices identifying a device state and changing the value.

According to SNMP a management method can be easily used and various types of devices using TCP IP can be developed. Through various Requests For Comments RFCs a management range can be easily designated or extended and protocols can be configured simply. Among the many management protocols SNMP is widely used because it can be easily implemented.

First commands transmitted received between the SNMP manager and the SNMP agent as illustrated in will be described.

The SNMP manager and the SNMP agent of can communicate with each other using the above described messages.

A conventional development method and a conventional method for interfacing with an application program will now be described with reference to .

In step of a network manager defines an MIB to develop the SNMP agent and defines a structure used for an interface with an associated application program.

In step an MIB file is generated on the basis of the MIB defined in step . In step the network manager codes and compiles the generated MIB file thereby generating the SNMP agent .

In step the network manager determines if the MIB or interface has been corrected. If the MIB or interface has been corrected the network manager proceeds to step to define management items.

In step the network manager generates an MIB file on the basis of the management items defined in step . In step the network manager recodes and recompiles the SNMP agent on the basis of the generated MIB file.

In order for the manager to interface with the application programs the agent must know structure and destination information. When a conventional tool for developing the SNMP agent is used objects corresponding to the management items must be implemented using a structure used in the application programs .

In the conventional method for developing the SNMP agent an MIB is designed such that characteristics of a device can be reflected. Content of the designed MIB determines a development range of the SNMP agent a role of the application programs for performing a management function within the device an interface method between the SNMP agent and the application programs and so on.

A conventional tool is used to effectively develop the SNMP protocol. The development of the SNMP agent using the tool is facilitated when the SNMP agent has necessary data. However the development of the SNMP agent is difficult and complex because MIB objects have different structures when an MIB object value is obtained through an interface with the application programs .

The SNMP manager accesses management items managed in the different application programs within a device through the SNMP agent . These management items are expressed by the MIB and differ according to device characteristics. This MIB cannot be perfectly defined at the time of initial development.

Because the SNMP agent is conventionally developed on the basis of the above described MIB different SNMP agents must be developed for devices. Items to be managed in an identical device can be frequently changed added or deleted. When a change is made the SNMP agent needs to be corrected.

Since the SNMP agent must be corrected and recompiled whenever the MIB is changed added or deleted in the above described environment a great deal of time and effort is required for the development.

Accordingly a need exists for an effective and efficient system and method for managing a communication device using Simple Network Management Protocol SNMP .

Embodiments of the present invention are provided to substantially solve the above and other problems and provide a network management apparatus and method based on Simple Network Management Protocol SNMP that generate a management information base MIB file and an object identifier information file in real time in a network management system.

Embodiments of the present invention provide a Simple Network Management Protocol SNMP management apparatus and method for controlling the operation of devices suitable for changes occurring in a network comprising a network management system.

Embodiments of the present invention provide a Simple Network Management Protocol SNMP management apparatus and method for operating devices comprising a network management system according to a standard.

In accordance with an object of the present invention an apparatus is provided for generating a management information base MIB file for managing a communication device using Simple Network Management Protocol SNMP at a compile time and an object identifier information OIDInfo file for communication between an SNMP agent and an application program. The apparatus comprises a header file memory for storing a header file created by the application program to manage an SNMP device an extractor for reading the header file from the header file memory and creating an MIB file and an OIDInfo file for exchanging a message between the SNMP agent and the application program an MIB file memory for storing the MIB file created by the extractor and an OIDInfo memory for storing the OIDInfo file created by the extractor.

In accordance with another object of the present invention a method is provided for generating a management information base MIB file for managing a communication device using Simple Network Management Protocol SNMP at a compile time and an object identifier information OIDInfo file for communication between an SNMP agent and an application program. The method comprises the steps of creating an SNMP interface header file in an application program receiving a changed management item reading the SNMP interface header file and generating an MIB file and an OIDInfo file and storing the MIB file and the OIDInfo file.

In accordance with another object of the present invention a method is provided for performing a run time operation for receiving a Simple Network Management Protocol SNMP request message including a management item from a manager for managing a communication device using SNMP and making a response of a result of processing the management item. The method comprises the steps of receiving the SNMP request message for requesting data of the result of processing the management item from the manager in an agent sending object identifier information OIDInfo included in the SNMP request message from the agent to an OIDInfo processor sending information for communication between the agent and an application program storing the management item data requested by the manager from the OIDInfo processor to the agent on a basis of the OIDInfo communicating with the application program in the agent on a basis of the communication information received from the OIDInfo processor and receiving the result of processing the management item requested by the manager from the application program and sending the received result of processing the management item from the agent to the manager.

In accordance with another object of the present invention an apparatus is provided for managing a communication device using Simple Network Management Protocol SNMP to perform a run time operation for receiving an SNMP request message including a management item from a manager for managing the communication device using SNMP and making a response of a result of processing the management item. The apparatus comprises an application program for performing an operation for requesting the management item an object identifier information OIDInfo processing means for providing information for communicating with the application program when receiving predetermined OIDInfo mapped to the management item and an agent for sending to the OIDInfo processing means the OIDInfo mapped to the management item when receiving the SNMP request message from the manager obtaining the information for communication with the application program receiving a result of processing the management item from the application program and sending the processing result to the manager.

Throughout the drawings like reference numerals will be understood to refer to like parts components and structures.

Exemplary embodiments of the present invention will now be described in detail herein below with reference to the accompanying drawings. In the following description detailed descriptions of functions and configurations incorporated herein that are well known to those skilled in the art are omitted for clarity and conciseness.

In embodiments of the present invention a Simple Network Management Protocol SNMP agent comprises four parts as illustrated in .

The SNMP agent comprises an agent for processing an SNMP message and performing an interface with application programs and an object identifier information OIDInfo processor for processing OIDInfo corresponding to a library with information for creating a general message service GMS necessary for communication between the application programs and the agent .

The SNMP agent further comprises an extractor for transferring information for creating a GMS message and a management information base MIB to an OIDInfo memory of and a header file memory for storing an SNMP interface header file used for communication with an application program information to be managed by an application program of and GMS information.

The OIDInfo processor provides a number of functions. First when OIDInfo about management items is input from the agent the OIDInfo processor retrieves GMS information corresponding to information for communication between the agent and the application program from the OIDInfo memory storing an OIDInfo data file and provides the GMS information to the agent . Here the information for communication comprises information about a port number a message format a communication type a payload structure and so on for communication between the agent and the application program . In an exemplary embodiment of the present invention it is assumed that the interface between the agent and the application program is the GMS however the present invention is not limited thereto. Alternatively other interfaces may be used.

First the agent is used for processing the SNMP protocol with the manager and transmits receives a GMS message for communication with an application program for actually maintaining and managing management items. When a network manager sends an SNMP request message including a protocol data unit PDU based on various preset formats to request an management item of a network device in which the agent operates using the manager an OID mapped to the management item included in the SNMP request message is sent to the OIDInfo processor . Then the agent receives from the OIDInfo processor GMS information corresponding to information about a port number a format and a payload structure for communicating with the application program . The agent communicates with the application program using the GMS information and receives a result of processing the management item from the application program . Upon receiving the result of processing the management item from the application program the agent sends data of the result of processing the management item to the manger through an SNMP response message.

Second the agent is further used in obtaining OIDInfo from the OIDInfo processor and sending a trap PDU to the manager when receiving a notification trap message from the application program .

To access the management item the OIDInfo processor reads from the OIDInfo memory an OIDInfo file storing information necessary to send a message to and receive a message from the application program . The OIDInfo processor retrieves the OIDInfo file and delivers GMS information to the agent . The OIDInfo memory stores OIDInfo library application programming interfaces APIs and OIDInfo data files. The OIDInfo library APIs and the OIDInfo data files are provided from the extractor .

The extractor is used in generating an MIB file from an SNMP interface header file defined as the management item in the application program generating an OIDInfo file required by the OIDInfo processor and storing the MIB file and the OIDInfo file in the OIDInfo memory .

The SNMP interface header file is a file in which a message identifier ID a port number a message structure and so on are defined such that the agent can obtain information managed in the application program . The SNMP interface header file is defined in the application program and is stored in the header file memory .

An exemplary operation of the SNMP agent at the compile time will now be described with reference to and .

A basic structure for creating an OIDInfo data file with information about a GMS message to be sent to the application program and a process for generating OIDInfo data based on the structure in the extractor will now be described.

Using the above described method the extractor is used in generating data from the header file memory . The agent uses an OIDInfo library capable of retrieving necessary information through an OIDInfo file and uses the information about the GMS message to be sent to the application program .

The compile operation of the SNMP agent will now be described in greater detail with reference to . illustrates an exemplary process for generating a data file in the extractor of the SNMP agent at the compile time in accordance with an embodiment of the present invention.

First a developer of the SNMP agent stores the SNMP interface header file defining information to be managed through the application program in the header file memory . Then the extractor reads the SNMP interface header file from the header file memory with the information to be managed creates an MIB file in which a management item is defined and stores the created MIB file in the MIB file memory . Moreover the extractor reads the SNMP interface header file from the header file memory creates an OIDInfo data file for generating a GMS message and stores the OIDInfo data file in the OIDInfo memory .

When the developer has requested a change of a management item of the SNMP agent in step the operation proceeds to step in which the application program creates the SNMP interface header file for a changed management item on the basis of information input by the developer and stores the created SNMP interface header file in the header file memory .

In step the extractor reads the SNMP interface header file and creates an MIB and an OIDInfo data file. Among the MIB and OIDInfo data file created in step the MIB is stored in the MIB file memory and the created OIDInfo data file is stored in the OIDInfo memory in step .

Communication between the agent and the application program of uses a GMS or object oriented message service interface. A payload of the GMS message as shown in comprises a type of message for supporting SNMP communication between the agent and the application program and an EM Interface header indicating the number of structures repeated in the message payload . This is described in greater detail below.

First when the manager sends an SNMP request message to the agent the agent sends OIDInfo within the SNMP request message to the OIDInfo processor . One reason why the agent sends the OIDInfo to the OIDInfo processor is that the agent requires GMS information to communicate with the application program .

The OIDInfo processor reads the GMS information on the basis of the received OID message and sends the read GMS information to the agent . Then the agent communicates with the application program on the basis of the GMS information. The agent sends to the manager a response to the SNMP request on the basis of a result of a response of the application program .

Now an exemplary operation of the components of the SNMP agent at the run time will be described with reference to .

In step the agent determines if an SNMP request has been received from the manager . If the SNMP request has been received in step the agent proceeds to step to deliver an OID included in the SNMP request message received from the manager to the OIDInfo processor .

In step the OIDInfo processor reads associated GMS information from the OIDInfo memory on the basis of received OIDInfo and delivers the GMS information to the agent . Here the GMS information comprises information about a port number a communication type a data structure and so on of the application program for communication between the agent and the application program .

In step the agent receiving the GMS information sends to the application program a request for data of a management item requested by the manager on the basis of the GMS information. In step the application program sends data about the management item through a GMS response message.

In step the agent sends an SNMP response message to the manager on the basis of the data about the management item corresponding to the response from the application program.

A set of the GMS header GMS Hdr the EM Interface header and the structure field is referred to as one row .

As described above the EM Interface header comprised of the above described four fields will now be described in greater detail. First a msgType indicates a type of a message between the agent and the application program and a rowCount indicates the number of structures repeated in the payload at the time of Get Set and Get Next operations for a table supporting a multiRowTable. At the time of a Get Bulk operation for all tables the rowCount is used for the purpose equal to that of a Max Repeat value of SNMP Get Bulk. A response is used to report an occurrence error. A structId indicates a message ID additionally used within the application program and is used as a relation ID for programmable loading data PLD .

Additionally the application program copies a transactionId and a bsmId from a header of the GMS message received from the agent creates a response message and delivers the created response message to the agent such that the agent operates normally according to the response received from the application program .

The agent allocates a memory mapped to one row inserts an index value received from the manager into the GMS payload and delivers the GMS payload to the application program .

The application program copies to the memory the row mapped to the index received from the agent in an associated table and sends a response to the agent . At this time an MsgId is set to a ResponseId associated with a predefined structure. If a failure has occurred an error value associated with the response of the EM Interface header is inserted and sent. At this time the GMS payload is resent without modification.

In the case of GetNextRequest the next row subsequent to an associated row is retrieved and delivered.

First the PreSet SetRequest message is sent from the agent to the application program . The operation of PreSetRequest is substantially the same as that of GetRequest. Upon receiving PreSetRequest the application program fixes an associated row. Upon receiving a response to PreSetRequest from the application program the agent changes an attribute value for performing SetRequest and sends SetRequest to the application program .

Upon receiving a normal response from the application program the agent sends to the manager a response to the Set message. If a Fail message is received from the application program the agent sends the Fail message to the manager . When the time is exceeded the agent discards a Set packet.

In the case of SetRequest a memory mapped to a row is allocated to the requested GMS payload and then the GMS payload is delivered. When the application program sends a response the agent sends only the EM Interface header .

In the case of GetBulkRequest a number of memories corresponding to a value of the rowCount Max Repeat of the EM Interface header are generated from an associated row. If the rowCount value is 0 for example the entire table is delivered.

If the agent has sent to the application program a request in which the rowCount value is 3 for example only a memory mapped to one row is allocated in relation to the payload of a requested GMS for sending an index indicating the beginning. Then the application program deletes the above described memory allocates a number of memories corresponding to a value of the rowCount copies information and sends the copied information to the agent . The memory is deleted by the agent .

To process notification preferably a preset structure must be defined and a single message ID is provided. The application program sets the msgType of the EM Interface header to EM NOTIFICATION fills a preset value of an msgId in the GMS header fills structure information in the payload and sends a message to the agent .

First an OID information header OIDInfoHdr indicates a data structure of a payload storing basic information of the OIDInfo. This structure information comprises a version and generation date of the OIDInfo a default OID an offset value for indicating the highest node of OIDTreeInfo serving as structure information of each node of an OID tree and an offset value for indicating a NotiInfoHdr used for retrieving notification information.

The OIDTreeInfo comprises tree node information and is used for a tree search. The OIDTreeInfo is used for expressing a group and expressing one node of the OIDTreeInfo associated with a scalar object and a table object. This structure comprises an ObjectID indicating an OID of an MIB a node type NodeType and four offsets.

The ObjectID indicates an OID of the current node of the MIB rather than a total OID. The NodeType is used to determine if the current node is a group object a scalar object or a table object. The offset included in the OIDTreeIOnfo comprises an offset indicating higher OIDTreeInfo and an offset indicating GMSInfo with information about the GMS and the structure.

The GMS information GMSInfo comprises GMS header information and payload information for delivering a message to the application program . This structure is divided into fields whose meanings vary with the structType and common fields. An OID is mapped to a group including a scalar or an MIB table generated using the structure and includes a common default OID or enterprise OID . A structname indicates a name created when the structure is defined. The structType is used to indicate 6 different structure types and a payloadType is a field for indicating if Set Get and Get Next are possible for multiple rows using the structure.

A requestMsgId responseMsgId and portNumber indicate GMS header information. A numberOfIndex indicates the number of structure indices. A numberOfField indicates the number of total structure fields rather than the number of attributes of an MIB table. A payloadSize indicates a total structure size for computing a size of the GMS payload. A pldRelationId indicates a relation ID of the PLD and a masterTableOffset is an offset for indicating a master table when the structType is a sub table. A nextGMSInfoOffset is a reserved field to be used later and is a field whose purpose currently is not defined. Finally a firstGMSAttInfoOffset is an offset for indicating the first GMSAttInfo indicating field information of the structure.

Fields of the GMSInfo are used for different purposes according to the structType. The requestMsgId responseMsgId and portNumber are commonly used as the GMS header information. The purposes of the nextGMSInfoOffset and firstGMSAttInfoOffset are substantially identical between all structType fields. In Table 3 by way of example the structType and the purposes of fields varying with the structType will be described.

First the purpose of each field of the GMSInfo when the structType is the scalar is shown in Table 4 by way of example.

Next the purpose of each field of the GMSInfo when the structType is the static table is shown in Table 5 by way of example.

Next the purpose of each field of the GMSInfo when the structType is the agent dynamic table is shown in Table 6 by way of example.

Next the purpose of each field of the GMSInfo when the structType is the application dynamic table is shown in Table 7 by way of example.

Next the purpose of each field of the GMSInfo when the structType is the PLD is shown in Table 8 by way of example.

Next the purpose of each field of the GMSInfo when the structType is the sub table is shown in Table 9 by way of example.

Field information inserted in the payload can be found when the GMSAttInfo indicated by the firstGMSAttInfoOffset are sequentially retrieved.

As the field and structure for the GMSInfo have been described a structure of the GMSAttInfo will now be described. The GMSAttInfo indicates structure field information to be inserted into a GMS payload. Elements of the GMSAttInfo indicating respective structure fields are connected to each other according to offsets. The offset value for the last GMSAttInfo is 0 .

In the order of the GMSAttInfo the GMSAttInfo indicating the index appears first and the GMSAttInfo indicating the array appears last when the structure includes the array.

Indices are arranged in order of OIDs and also values are arranged in order of OIDs. Meanings of the fields of the GMSAttInfo differ according to a structType of the GMSInfo and a fieldType of the GMSAttInfo. First the fieldType determining a type of the GMSAttInfo will be described. Exemplary purposes of fields that differ according to the fieldType are shown in Table 10 by way of example.

Fields of the GMSAttInfo when the structType is not a sub table and the fieldType is a scalar value a table value or a table and index are shown in Table 11 by way of example.

Fields of the GMSAttInfo when the structType is not a sub table and the fieldType is a table and array are shown in Table 12 by way of example.

Fields of the GMSAttInfo when the structType is not a sub table and the fieldType is an array and index are shown in Table 13 by way of example.

Fields of the GMSAttInfo when the structType is not a sub table and the fieldType is a table value are shown in Table 14 by way of example.

A NotiInfoHdr of is structure information used inside the OIDInfo processor to obtain notification information using a message ID. A method for retrieving the notification information may use one or two message IDs.

The NotiInfoHdr comprises a field indicating the number of NotiNodeInfo fields and an offset indicating the first NotiNodeInfo . A description of the fields of the NotiInfoHdr is shown in Table 15 by way of example.

The NotiNodeInfo of comprises a field for storing a message ID a notiNodeType for distinguishing a type of the NotiNodeInfo a sub NotiInfoHdrOffset for indicating a sub NotiInfoHdr and a notiInfoOffset for indicating NotiInfo with notification information.

The NotiNodeInfo is structure information used to retrieve associated notification information using a message ID. The NotiNodeInfo is arranged in the OIDInfo data file memory in order of message IDs. The OIDInfo processor can retrieve associated notification information using the NotiNodeInfo and the NotiInfoHdr .

First when one message ID is mapped to one notification information element a binary search algorithm is performed using the numberOfNotiNodeInfo and the firstNotiInfoOffset of the NotiInfoHdr. Using the algorithm associated NotiNodeInfo is searched. This is possible because the NotiNodeInfo is arranged in order of message IDs.

An SNMP notification message is created using NotiInfo indicated by a notiInfoOffset of the NotiNodeInfo .

Second when two message IDs are mapped to one notification information element the NotiNodeInfo is searched using the above described method. In this case the notiNodeType of the NotiNodeInfo is a multi notification node. The subNotiInfoHdrOffset indicates a sub NotiInfoHdr .

A substantially identical algorithm is repeated using the second message ID. Using the algorithm the NotiNodeInfo is searched. An SNMP notification message is created using the NotiInfo indicated by the notiInfoOffset of the NotiNodeInfo .

Next the NotiInfo will now be described. The NotiInfo comprises a notiInfoType for distinguishing a notification type a numberOfNotiField for indicating the number of notification structure fields defined in the SNMP interface header file and the first offset of message field information.

Next the NotiAttInfo corresponding to the last structure information will be descried. The NotiAttInfo indicates field information of a notification message. First a notiAttOID is a string indicating an OID of a field for giving notification. The notiAttOID indicates a full OID in the scalar and indicates a value from which an index has been excluded in the table. A notiAttName indicates a string of a field name defined in the SNMP interface header file. A notiASNType indicates a type of an attribute syntax expressed in the MIB. A notiFieldType determines an attribute type. The purposes of the other fields are varied according to the notiFieldType. A notiAttType indicates a C data type of the field. A notiAttSize indicates a field size. A notiStartOffset is an offset value for indicating a field position in structure information received from an application. A subNotiAttOffset is an offset value for indicating the NotiAttInfo for expressing an array if the current field indicates the array. A notiMaxDimensionValue indicates the maximum index value when the type is an array and index in the NotiAttInfo extended by use of the array. This means the maximum value of the array. Finally the nextNotiAttInfoOffset is an offset value for indicating the next NotiAttInfo . In the NotiAttInfo an index is placed in the head part. If multiple tables comprise notification an index is placed after a value and the next index and value are placed.

A meaning of each field differs according to the notiFieldType of the NotiAttInfo . This is shown in the following tables. A case where the notiFieldType is a scalar value is shown in Table 19 by way of example.

Next a case where the notiFieldType of the NotiAttInfo indicated by the subNotiAttInfoOffset of the NotiAttInfo is the array and index is shown in Table 23 by way of example.

Next a case where the notiFieldType of the NotiAttInfo indicated by the subNotiAttInfoOffset of the NotiAttInfo is the table value is shown in Table 24 by way of example.

In accordance with an embodiment of the present invention a method for retrieving GMS information for communication between the agent and the application program will now be described with reference to .

An OID string input from the agent is separated and changed to an OID of an integer type. Then the OIDTreeInfo is sequentially searched using a tree search algorithm according to the OID.

Then the OIDInfo memory returns the OIDTreeInfo mapped to the OID and returns the next OIDTreeInfo subsequent to the OIDTreeInfo mapped to the OID. If the desired OIDTreeInfo is searched the OIDInfo processor returns the GMSInfo indicated by the OIDTreeInfo. Then the agent creates a GMS header and a payload using the GMSInfo . When the GMS payload is created an OAM header is inserted before the payload the EM header subsequent to the OAM header is inserted to support SNMP between the agent and the application program and a structure value subsequent to the EM header is inserted. Structure field information completes a GMS PDU using the GMSAttInfo . A message is then sent to the application program .

In accordance with an embodiment of the present invention a method for retrieving notification information in the agent will now be described with reference to .

When the agent receives a trap message with a preset message ID from the application program the OIDInfo processor retrieves SNMP notification information using the message ID.

First the agent determines if the number of IDs of the received message is one or two. The agent checks a subMsgId field of the EM header . If a value of the checked field is non zero the message ID of the GMS header is used as the first message ID and the subMsgId is used as the second message ID.

Then the NotiNodeInfo is retrieved using the first message ID. The NotiNodeInfo is retrieved using the number of NotiNodeInfo fields of the NotiInfoHdr and a binary search algorithm. When the second message is provided the NotiNodeInfo is retrieved using the number of subNotiNodeInfo fields of the NotiInfoHdr indicated by the subNotiInfoHdrOffset of the NotiNodeInfo and the binary search algorithm.

The notiInfoOffset of the NotiNodeInfo indicates the NotiInfo storing notification information. An SNMP notification message is created using the NotiInfo and the NotiAttInfo . The created message is then sent to the manager .

In accordance with embodiments of the present invention the SNMP agent does not need to add a function or perform new coding and recompiling operations if the extractor generates only a new OIDInfo file even when a management target is changed or a management item is changed added or deleted. An MIB corresponding to a management item and an OIDInfo file can be automatically changed even when a structure used between the SNMP agent and the application program is added changed or deleted. Therefore the SNMP agent can be easily developed and can be used for other devices or other management targets without modification.

While the present invention has been shown and described with reference to certain exemplary embodiments thereof it will be understood by those skilled in the art that various changes in form and details may be made therein without departing from the spirit and scope of the present invention as defined by the appended claims. Accordingly the scope of the present invention is not to be limited by the above embodiments but by the following claims and equivalents thereof.

