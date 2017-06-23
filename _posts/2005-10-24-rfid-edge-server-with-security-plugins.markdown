---

title: RFID edge server with security plug-ins
abstract: An RFID edge server using an application server allows for improvements in an RFID system.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07394377&OS=07394377&RS=07394377
owner: BEA Systems, Inc.
number: 07394377
owner_city: San Jose
owner_country: US
publication_date: 20051024
---
This application claims priority to U.S. Provisional Application No. 60 710 243 entitled RFID Edge Server by Ashok Banerjee filed Aug. 22 2005 and U.S. Provisional Application No. 60 721 023 entitled RFID Edge Server with Security Plug Ins and WSRM by Ashok Banerjee filed Sep. 27 2005.

The present invention relates to Radio Frequency Identification RFID technology. Radio Frequency Identification technology is becoming more and more important especially to manage supply chains.

Radio Frequency Identification technology can allow for the tracking of objects using RFID tags and RFID readers. RFID readers can interrogate the RFID tags using radio waves. The RFID tag typically includes an antenna and a microchip that stores a response code. The majority of RFID tags use a silicon microchip to store a unique serial number such as an electronic product code EPC and usually some additional information. The reader can pass the response code to a computer system to track the objects.

There are two main categories of RFID systems passive and active systems. Passive RFID tags do not have a transmitter but simply reflect back energy to the reader. Active tags have their own transmitter and power source such as a battery. Active RFID systems are typically used for a tracking large items since the active RFID tags are relatively expensive.

Because passive RFID tags do not use a power source and transmitter they tend to be cheaper than the active RFID tags. Retailers and manufacturers are adding the passive tags to items in the supply chain. RFID systems can significantly reduce the cost of managing inventory.

Passive RFID tags allow for the possibility of tracking of cartons of materials as they enter and exit entry points of a warehouses and stores. As the passive RFID tags become cheaper ultimately individual packages can have their own RFID tags and thus the inventory can be tracked very precisely. Additionally since the RFID technology does not rely on line of sight operation a shopping cart full of goods with RFID tags can be scanned without requiring the goods to be removed from the cart.

In one embodiment RFID tags can be used to implement an electronic product code EPC . The EPC is a unique number used to identify specific objects in the supply chain. EPC information services EPCIS can enable users to exchange EPC related data with trading partners throughout the EPC network.

The RFID edge server can be used to provide RFID reader management filtering commissioning and connectivity. As disclosed below in one embodiment the RFID edge server can include application server such as a J2EE application server. J2EE applications servers can run J2EE applications. J2EE applications can be made up of components. A J2EE component can be a self contained functional software unit that is assembled into a J2EE application with its related classes and files and that communicates with other components. The J2EE specification defines the following J2EE components 

J2EE components can be written in the Java programming language and can be compiled in the same way as any program in the language. In one embodiment The difference between J2EE components and standard Java classes is that J2EE components are assembled into a J2EE application are verified to be well formed and in compliance with the J2EE specification and are deployed to production where they are run and managed by the J2EE server.

In one embodiment the application server is the WebLogic Server available from BEA Systems Inc. of San Jose Calif.

The application server can run a RFID edge server infrastructure itself as a J2EE application. RFID edge server application can include J2EE components and be packaged in an archive file such as a Java Archive JAR file or a Web Archive WAR file.

The use of an application server at the RFID edge server can provide a number of advantages. The application server components can include 

The RFID edge server can provide for RFID data filtering and business rules. The RFID edge server can work with a variety of RFID readers. Applications can interact with an RFID edge server through an Application Level Events ALE interface. ALE can provide a way for developers to define high level events that are needed by specific customer enterprise applications. Enterprise applications receive incoming data in formats designed for easy integration and can obtain RFID data without requiring programmers to interact directly with RFID readers or to perform any low level real time processing or scheduling.

Application Level Events ALE defines an interface through which an application could indicate exactly what information it wants from the raw stream of RFID reads. Through ALE an application can specify a number of things 

A request of this kind may be made in an on demand mode where the reads are performed in response to an application request or as a standing request where data is sent to the application periodically without further request.

An RFID application can make a high level request for data through the ALE interface and the hardware or software on the other side of the ALE interface fulfills the request. ALE shields applications from low level implementation detail.

Another benefit for end users is that ALE facilitates sharing RFID data among many applications simultaneously. Different applications may make requests through the ALE interface without requiring those applications to have knowledge of each other. If two applications request data from the same reader the implementation of ALE mediates those requests and makes sure that each application receives the data it needs. Using ALE each RFID can interact with a number of applications rather than be just a dedicated peripheral for a specific application.

The EPC Information Service EPCIS is a specification for a standard interface for accessing EPC related information. Because an Electronic Product Code EPC gives each object a unique serial number each individual object can be tracked independently and fine grained real time information about each individual object can be collected stored and acted upon. EPC Information Services are a way for supply chain partners to share and exchange information efficiently because a standard interface allows trading partners to use the same functions or methods for querying data across the supply chain leading to reduced times integrating with partners if everyone uses the same interface even though they may store the information in different types of underlying databases.

EPC Information Service is a technical specification for a data communication interface. EPC Information Services are designed to support both on demand polling access and a push model supporting standing queries. Depending on how the security for each individual EPCIS implementation is configured you might be granted the right to define your own standing queries or you might only have the option of subscribing to an existing query which was pre defined by the owner or provider of a particular EPCIS service.

The EPC Information Service lies at the top layer of the EPC Network technology stack. EPCIS can allow business logic to be mixed with read events coming from RFID readers. The layers underneath EPCIS e.g. Filtering Collection ALE Reader Protocol etc. can be primarily concerned with simple triples of data Reader Tag EPC timestamp . EPCIS allows for higher level meanings to be stored or accessed involving business processes and business transactions.

The EPCIS interface can be implemented as an EPCIS server. In terms of implementing an EPC Information Service you can choose to either host your own EPCIS interface coupled to your existing databases for serial level data or subscribe to a technology solution provider hosting a managed EPCIS service.

Trading partners may be able to find an EPCIS by using the Object Name Service ONS doing a lookup based on the EPC of your products. Serial level pointers can also be stored securely within registries called Discovery Services. Discovery Service registries can be updated by each custodian on handover with serial level EPC lookup.

The RFID edge server can have a TCP IP socket for each of the RFID readers or each active RFID readers. One way of connecting the RFID edge server with the RFID readers and is to have a dedicated thread for monitoring each socket. In one embodiment the number of RFID readers n can be quite large. It is feasible for large warehouses to have over a hundred RFID readers. For this reason the RFID edge server can be input output I O constrained. Each of the access threads needs to access a CPU and other Operating System Resources which require a certain amount of setup for each access thread. The switching between a large number of threads can limit the number of RFID readers that can be associated with an RFID edge server.

As shown in in one embodiment the RFID edge server is associated with multiple RFID readers and . RFID edge server can include an application server to run applications such as the RFID edge server application . The RFID edge server can have TPC IP socket connections and with multiple RFID readers and . The RFID edge server can have fewer access threads for the RFID readers than there are socket connections.

Each data access thread can be used to service multiple sockets. In one embodiment at least some of the access threads are written in a non Java language. For example the access thread can be written in code that is native to the machine.

The operating system for the machine running the application server can be such that it will provide TPC IP socket information to access thread which can then be provided to the application server for use by the RFID edge server application . Alternately the operation for the machine can allow the application server to obtain the low level control of the TPC IP sockets using the access thread .

In one embodiment the RFID readers and are connected to the RFID edge server through the local network . The TPC IP protocol can be used for interconnecting between the RFID edge server and RFID readers and .

In one embodiment the system can use sockets which are serviced by multiplexed reader accessor threads. Muxer sockets can support asynchronous network I O for the upper protocol layers via a completion based contract. In one embodiment Protocol layers can implement MuxableSocket as a completion callback and register it with the muxers via SocketMuxer.register . It can then issue asynchronous read requests to the muxers via SocketMuxer.read . Under the covers muxers can perform the network input operations either asynchronously for OS which supports asynchronous IO e.g. I O completion port on Win2K or in a non blocking fashion for OS which supports non blocking I O e.g. select poll on Unix platforms or the JDK 1.4 non blocking I O API which is modeled closely after the select API or synchronously with polling. To avoid undue copying data can be read into protocol layers buffer directly . When the read operation is completed the muxer can notify the protocol layer via the completion callback MuxableSocket.dispatch . In the event of any network errors or end of file or timeout reached for the socket the muxer can notify the protocol layer via an error handler MuxableSocket.hasException endOfStream .

In one embodiment the number of access threads used is fixed. The number of or default number of access threads can be proportional to the number of CPUs of the machine running the RFID edge server. In one exemplary embodiment there are two access threads per CPU to access the sockets of the RFID readers.

In one embodiment the RFID edge server can have a RFID edge server application running which can include message filtering and boxcar code . In one embodiment messages are received by the RFID edge server. The RFID edge server application can filter away duplicate or otherwise unnecessary reports. In one embodiment the reports can be boxcarred that is multiple event reports can be combined together into a single message from the RFID edge server to the central server . This can reduce the amount of traffic between the RFID edge server and the central server and thus increase the number of RFID edge servers that can interact with the central server . The boxcarred reports can include data from messages provided by the RFID readers and . The central server can unboxcar the messages. A boxcarring protocol at the RFID edge servers and at the central servers that ensures the correct boxcarring and unboxcarring of the messages.

One embodiment of the present invention is a method wherein at the RFID edge server messages are received from RFID readers and . The messages are filtered at the RFID edge server . Event reports can be boxcarred which can include the data from the messages and sent to the central server .

A computer readable media including code adapted to do the above method can also be used. This code can be part of the RFID edge server application running on the application server of the RFID edge server .

An RFID edge server can be associated with multiple RFID readers and . The RFID edge server can include an application server adapted to receive an RFID software package as an archive file . The application server can open an archive file to install the RFID software into the application server . In one embodiment the archive file is a J2EE standard archive file such as a JAR file Java Archive .

The Java Archive JAR file format can enable the bundling of multiple files into a single archive file. Typically a JAR file will contain the class files and auxiliary resources associated with applets and applications. The JAR file format can provide many benefits 

The RFID edge server application archive can be provided from a website which can be downloaded into the application server of the RFID edge server . The archive file can include large number of other files such as classes and binaries needed to run an RFID edge server application. The RFID edge server archive can make it easier to obtain and maintain the RFID software .

One embodiment of the present invention is a method wherein at the RFID edge server RFID software packaged in an archive file is received. At the RFID edge server the archive file can be opened to install the RFID software into the application server . A computer readable medium implementing this method can also be used.

On embodiment of the present invention is a method including at an EPCIS server receiving EPCIS software packaged into an archive file and opening the archive file to install the EPCIS software into the application server . Additionally the present invention can comprise a computer readable medium including code adapted to do the steps of the method.

Additionally store and forward messaging can operate in as part of a transaction in which case the message is stored after forwarding until any transaction including the message completes. In one embodiment the transactional messaging uses a two phase commit such as with XA messaging to ensure that either all updates are done or all the updates are rolled back.

In one embodiment store and forward messaging is implemented using a JMS server . In one embodiment the JMS server operates in a transactional manner and transactions involving the messages can be rolledback.

The Java Message Service is a Java API that allows applications to create send receive and read messages. The JMS API defines a common set of interfaces and associated semantics that allow programs written in the Java programming language to communicate with other messaging implementations.

In one embodiment a message such as message A is sent to the central server and the RFID edge server maintains a copy of message A until an acknowledgment from the central server or a determination that a transaction including the Message A is completed.

In one embodiment of the present invention a method wherein a RFID edge server receives data from multiple RFID readers and . At the RFID reader store and forwarding of messages including at least some of the data is done to the central server . A computer readable medium implementing such a method can be used.

The JMX administration can be used to manage resources related to the RFID edge server. Java Management Extensions JMX can use managed beans or MBeans. An MBean is a managed Java object similar to a JavaBean that follows the design patterns set forth in the instrumentation level of the JMX specification. An MBean can represent a device an application or any resource that needs to be managed. MBeans expose a management interface a set of readable and or writable attributes and a set of invokable operations along with a self description. The management interface does not change throughout the life of an MBean instance. MBeans can also emit notifications when certain defined events occur.

The JMX administration can use MBeans to set configuration for the RFID edge server. An administration server at the RFID edge server can be used to set the configuration of the RFID edge server. The administration server can be run on the application server. An administration console can be used to manage the RFID edge server . The administration console can include a graphical interface for determining and setting the state and configuration of the RFID edge server.

The RFID edge server of claim wherein the JMX administration can be used to manage the connections with the multiple RFID readers. The JMX administration can be used to manage the RFID edge server remotely.

The J2EE Connector Java connector architecture defines a standard architecture for connecting the J2EE platform to heterogeneous Enterprise Information Systems EIS systems. Examples of EIS systems include ERP mainframe transaction processing database systems and legacy applications not written in the Java programming language. The J2EE Connector Java connector architecture defines a set of scalable secure and transactional mechanisms to enable the integration of EISs with application servers and enterprise applications.

The J2EE Connector architecture enables an EIS vendor to provide a standard resource adapter for its EIS. The resource adapter plugs into an application server providing connectivity between the EIS the application server and the enterprise application. An EIS vendor needs to provide just one standard resource adapter which has the capability to plug in to any application server that supports the J2EE Connector architecture.

Multiple resource adapters that is one resource adapter per type of EIS are pluggable into an application server. This capability enables application components deployed on the application server to access the underlying EIS systems.

The Java connector can connect to ERP software at another location. RFID edge server also communicates with an EPCIS server.

Device management functions of the RFID edge server can include Health Monitoring Diagnostics Fault Management Tag Activity Monitoring Performance Analysis Analytics to determine underperforming components Maintenance Upgrades Version Control Firmware Software upgrades Provisioning Configuration and Web based configuration.

1 Scalability RFID systems can have hundreds of RFID readers each reading data hundreds of times a second. This can cause CPU utilization network bandwidth and or data repository constraints. A number of features can help this problem including Thread Multiplexing Non blocking IO Eliminating duplicates through ALE Boxcarring packets and Handling data storage at the Enterprise Application Integration EAI layer.

2 Availability Availability of the system can be improved by reducing dependency on the database at the edge and ensuring availability of integration server layer. In one embodiment a file system and not a database is used at the RFID edge server. A database can be used at an integration layer such as at a central server. Load balancers can be used as well as high availability messaging through clustered JMS servers. A clustered database can be used to back the integration server layer.

3 Security Administration should be secure to prevent readers from being turned off and items being stolen. The administrative interface can be protected by authentication authorization audit and potentially over SSL Secure Socket Layer . This SSL handshake can be very CPU intensive. Alternately the entire stack reader edge server can be wrapped in a firewall to enable perimeter authorization. The RFID system security can be plugable to 3party security providers.

4 Interoperability Interoperability can include interoperability with packaged applications and with readers Support for standards based JCA Adapters. Reader abstraction layer at the edge that readily facilitates device drivers additions and updates.

5 Integration Layer The Global view is difficult to support due to different readers and edge server formats. Complex event composition is costly and not suitable at CPU intensive edge transformation and duplicate elimination . The RFID edge server need not be designed to integrate with other components of an integrated software platform. A unifying EAI layer can be used to compose and correlate events from different sets of RFID infrastructure. Clustered integration servers can be used to absorb the load of complex event composition. The EAI product can be fully integrated with Business Process Management BPM and Portal.

6 Administration Different administration consoles from different components can prevent a centralized administration. RFID components can integrate with existing management vendors HP Openview Tivoli and can support protocols like SNMP JMX.

7 Messaging Once RFID becomes mission critical there can be a need to ensure messages are sent once and only once. The JMX embodiment can support exactly once semantics. Transaction can guarantee on message enqueue dequeue. The RFID edge server can provide asynchronous JMS support.

The security framework can also provide an API for connecting to security plugins and that can allow third party security to operate using the known features and user interface. The security plugin can be code internal to the RFID edge server or can be code external to the RFID edge server . The security framework translates the security selections from a security plugin to security for the RFID edge server application . The security framework and thus any of the security plugins and can have default settings for the RFID edge server application .

The Security Framework can provide end to end application security covering J2EE and non J2EE components of an application hosted on an application server.

Integration with existing security solutions is greatly simplified. The Security Framework can separate application business logic from the security code. Security services including security business rules can be provided by the infrastructure and don t have to be coded in the application. A user interface for security administration can be provided out of the box.

A built in dynamic security rules engine can makes it easy to implement dynamic business rules for security policies and does not require any downtime to update these rules. It can allow mapping company business rules to security policies in distributed deployments providing easy customization of application security to business requirements.

With an API such as an open Security Service Provider Interface SSPI the framework can allow third party security solutions on the market to plug in and provide their security services to applications running on the application server and also enables adding custom extensions.

Single Sign On can be automatically available to applications on the application server without any additional programming.

The Security Framework can provide interfaces to other products J2EE containers and customer applications and delegates requests to the appropriate security plug in. Default security plug ins can perform the following functions out of the box 

Authentication Can authenticate verify and map security tokens to an internal format for security support. Can support delegated username password and certificate authentication with the application server and HTTP certificate authentication via the standard service provided in a Web server.

Authorization Can enforce authorization policies for resources taking business policies into consideration. Can support role based authorization in which access is based on job function and business rules.

Auditing Can Audit all security actions in support of non repudiation. Provides a customizable set of data for auditing security events such as failed login attempts authentication requests rejected digital certificates and invalid roles.

Public key infrastructure Can support standard public key encryption for data or digital signatures or when electronic authentication of a client s identity is required.

Credential mapping Can map a user s authentication credentials to those required for legacy applications so that the legacy application gets the necessary credential information.

Role mapping Can map roles to users or groups based on policy. Can determine the appropriate set of roles granted to an application server user or group for a resource.

The security plug in scheme can be based on a set of Security Service Provider Interfaces SPIs for the plug in points. The Security SPIs can be used by customers or third party vendors to develop security plug ins for the WebLogic Server environment. Security SPIs can be available for authentication authorization auditing credential mapping role mapping and the public key infrastructure supporting the Java standard Key Store for encrypted storage of public and private encryption keys .

An open interface based security architecture allows use of existing security products while taking advantage of new security technologies available in the marketplace. With this architecture a security installation can support security vendors full value propositions not just a subset. A user s choice of security products can be mixed and matched to create complete custom security solutions. In fact the application server can run more than one security plug in for a given function and users can set constraints that govern which product or protocol will be used in a given situation.

As users integrate new solutions or modify existing ones administrators can set security policy for each security plug in using a built in menu driven policy tool. Security policy can govern authorization the rules and constraints for accessing resources or assuming roles. More than one security plug in can run concurrently as part of a migration or transition scheme and set security policy accordingly. An Adjudicator function can resolve any conflicts in interpretation when making authorization decisions.

The security framework can support any choice of vendors and protocols because it separates the details of the security system from application code simplifying application maintenance and management. Changing security system components or policies need not entail modifying applications. This unified architecture makes it easy to integrate best of breed security solutions and to replace components of a security system with the latest technologies from third party vendors or from a development staff. The ability to swap in new security plug ins and technologies as needed reduces the total cost of ownership and maximizes the return on investment in security technologies.

The security framework can organize users into users and groups that take on roles according to defined security policies. Users can be organized into groups. Groups can be used to represent organizational boundaries as well as to simplify administration. Each application user and group is mapped to a role dynamically during application execution when authorization is needed.

Roles and policies can determine access to system resources and permitted behaviors. User roles can be registered by an administrator using the built in menu driven security policy tool embedded in the BEA supplied Authorization plug in. The security policy tool s interface can reflects business concepts not programming concepts and allows an administrator to create simple prose based rules for dynamically assigning roles and calculating access privileges. Application developers are freed from having to write application code to implement complex business policies because the policy tool separates the tasks of business policy creation and application creation.

The roles that a user can be assigned to are determined by policies defined by the administrator on behalf of the company. Since policies reflect business security rules a company s management can set security policies rather than the software development staff. Security policies can easily be changed with changes in business conditions.

The role and policy based security scheme can replaces the previous scheme of users groups and access control lists ACLs and can offers clear advantages for ease of administration and ease of adaptability as security requirements change. Using roles and policies for authorization permits dynamic computation of access status for each resource for each user or group.

WSRM can be used to send messages in a service oriented architecture SOA system such as an SOA system using a service bus and service registry.

In one embodiment the RFID edge server outbound notifications are transmitted using Web Service Reliable Messaging WSRM . WSRM is an open specification for ensuring reliable message delivery for Web services. WSRM can send messages using the Simple Object Access Protocol SOAP . SOAP is a simple XML based protocol to let applications exchange information over HTTP. HTTP messages are often allowed through firewalls so WSRM can allow reliable messaging in a format that can pass through most firewalls In one embodiment WSRM utilizes a transactional messaging system in the implementation.

Reliability can include the ability to guarantee message delivery to users with a chosen level of protocol capability and Quality of Service QOS . Again the users can be either other WS protocols e.g. WS Security WS Distributed Management WS Notifications etc or Application layer user information messages which are exchanged between the end points of the connection.

To facilitate WS Reliability SOAP based Reliable Messaging Processors RMPs in the sender and in the receiver endpoints can be used. For example both the RFID edge server and the central sever can have RMPs. The RMPs can work together to ensure that messages are delivered in a reliable manner over a connection that may be inherently unreliable. The sender and receiver RMPs can operate on newly defined SOAP headers that are transmitted as either self contained messages or they can be attached to other WS protocol messages or user data messages all of which are SOAP XML encoded . Fault messages may extend to the SOAP message body.

The users can determine the level of WS Reliability. Reliability may include one or more reliable messaging protocol capability for the delivery of WS messages

The users of the WS Reliability protocol may agree upon any or all of the above message delivery capabilities. Different users or applications may choose different protocol capabilities which are conveyed to the RMP sender and receiver prior to initiating communications. Alternatively the receiver RMP can determine the protocol capability via explicit parameter values sent in each reliable message request.

For purposes of the WSRM TC QOS can be defined as the ability to determine at least some of the following aspects 

The WSRM specification can define extensions to SOAP Headers. It is assumed that the payload user information is specified using a WSDL description fault messages may also use the payload to convey fault code information .

In the Reliable Messaging Model the sender node can send a message to the receiver node i.e. intermediaries are assumed to be transparent in the WS Reliability specification . Upon receipt of the message and at the appropriate time the receiver node sends back an Acknowledgment message or Fault message to the sender node.

There are three ways for the receiver to send back an Acknowledgment message or a Fault message to the sender. These are referred to as the RM Reply patterns which are defined as follows 

These three reply patterns provide the users with flexibility to send reliable request response or one way SOAP messages Callback and Polling patterns . Callback is important for one way request message patterns and for batching of acknowledgements and fault messages.

Additionally polling enables reliable message delivery to extend beyond the firewall which might otherwise block external reliable messages from reaching the intended recipient. Polling makes it possible to use the WS Reliability protocol even when a firewall prevents 3rd parties from initiating messages or requests.

Three types of message delivery capabilities are defined in the WS Reliability protocol. One or more of these protocol capabilities may be used with each of the RM Reply patterns. The selection is dependent on prior end user agreements or explicitly inferred by the receiver RMP from request messages.

This is to successfully deliver a message from a sender RMP to a receiver RMP without failure if this is not possible to report the failure to the sender s application. To realize guaranteed delivery the message is persisted i.e. stored in the sender RMP until delivery to the receiver is acknowledged or until the ultimate failure is reported to it s requester. There is a requirement on the underlying transport protocol that the message MUST be transported without corruption. If message persistence is lost for any reason it is no longer possible to guarantee message delivery. Since the reliability of message persistence is a property of the system implementation the conditions under which guaranteed message delivery holds is also a property of the system implementation.

A number of conditions may result in transmission of duplicate message s e.g. temporary downtime of the sender or receiver a routing problem between the sender and receiver etc. In order to provide at most once semantics the ultimate RMP receiver can eliminate duplicate messages and never present them to the user. Messages with the same Message Identifier value can be treated as duplicates and not delivered to the application.

Some applications will expect to receive a sequence of messages from the same sender in the same order those messages were sent. Although there are often means to enforce this at the Application layer this is not always possible or practical. In such cases the Reliable Messaging layer is required to guarantee the message order. WRSM defines a model to meet this requirement.

When the sender application sends three messages and with Guaranteed Message Ordering the receiver s RMP can guarantee that message order when it makes those messages available to the receiver s application the user . When a receiver s RMP receives messages and the receiver s RMP can make message available to the application but it persists message until message is received. When receiver s RMP receives message it can then makes message and available to the application in that order.

One embodiment may be implemented using a conventional general purpose or a specialized digital computer or microprocessor s programmed according to the teachings of the present disclosure as will be apparent to those skilled in the computer art. Appropriate software coding can readily be prepared by skilled programmers based on the teachings of the present disclosure as will be apparent to those skilled in the software art. The invention may also be implemented by the preparation of integrated circuits or by interconnecting an appropriate network of conventional component circuits as will be readily apparent to those skilled in the art.

One embodiment includes a computer program product which is a storage medium media having instructions stored thereon in which can be used to program a computer to perform any of the features presented herein. The storage medium can include but is not limited to any type of disk including floppy disks optical discs DVD CD ROMs micro drive and magneto optical disks ROMs Rams EPROM s EPROM s Drams Rams flash memory devices magnetic or optical cards Nano systems including molecular memory ICs or any type of media or device suitable for storing instructions and or data.

Stored on any one of the computer readable medium media the present invention includes software for controlling both the hardware of the general purpose specialized computer or microprocessor and for enabling the computer or microprocessor to interact with a human user or other mechanism utilizing the results of the present invention. Such software may include but is not limited to device drivers operating systems execution environments containers and user applications.

The foregoing description of preferred embodiments of the present invention has been provided for the purposes of illustration and description. It is not intended to be exhaustive or to limit the invention to the precise forms disclosed. Many modifications and variations will be apparent to one of ordinary skill in the relevant arts. For example steps performed in the embodiments of the invention disclosed can be performed in alternate orders certain steps can be omitted and additional steps can be added. The embodiments were chosen and described in order to best explain the principles of the invention and its practical application thereby enabling others skilled in the art to understand the invention for various embodiments and with various modifications that are suited to the particular use contemplated. It is intended that the scope of the invention be defined by the claims and their equivalents.

