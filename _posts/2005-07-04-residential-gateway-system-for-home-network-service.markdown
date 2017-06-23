---

title: Residential gateway system for home network service
abstract: Disclosed herein is a Residential Gateway (RG) system for home network service. The RG system receives various supplementary services through a Home Network Serving Node (HNSN) that provides home network service. The system includes an Open Service Gateway initiative (OSGi) framework, an RG agent, a virtual Universal Plug and Play (UPnP) device, and a Java virtual machine. The RG agent is installed on the OSGi framework and implemented in bundle form. The UPnP device is registered on the OSGi framework by the RG agent. The Java virtual machine is ported by the RG agent to hardware on which an operating system is installed.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08699501&OS=08699501&RS=08699501
owner: SK Telecom Co., Ltd.
number: 08699501
owner_city: Seoul
owner_country: KR
publication_date: 20050704
---
This application is the National Phase application of International Application No. PCT KR2005 00002106 filed Jul. 4 2005 which designates the United States and was published in English. This application in its entirety is incorporated herein by reference.

The present invention relates in general to a residential gateway system for home network service and more particularly to a residential gateway system for providing home network service on the basis of Open Service Gateway initiative and Universal Plug and Play.

Currently various types of home networking middleware intelligent information appliances and residential gateways based on various wired wireless network technologies in a home networking market and various development environments exist due to different hardware platforms Operating Systems OSs and network protocols.

Home networking middleware such as Java Intelligent Network Infra structure JINI Home Wide Web HWW Home Audio Video interoperability HAVi or Universal Plug and Play UPnP has purposes of communication and control between intelligent information appliances and a Residential Gateway RG operates as a gateway that dynamically transfers services which are separately provided by various service providers to a home network.

In these environments efforts are being made to make use of a dynamic service management function in conjunction with a control function for intelligent information appliances through home networking middleware and a representative example as shown in is the interoperable model of Open Service Gateway initiative OSGi based home networking middleware. That is it is desired to provide a integration type model for the two functions by developing a service bundle for home networking and installing it on an OSGi framework.

OSGi aims to integrate various network standards and technologies for internal networks and external networks like a single system by defining a standard for dynamic service management through Application Program Interfaces APIs having consistent form and providing a framework that is a java based platform independent service environment.

When the various network standards and technologies of OSGi based internal and external networks are combined like a single system a demand for a RG standard may increase. However sufficient standardization work for the RG has not been performed.

Meanwhile control devices which are capable of integrally managing devices home appliances that use various communication protocols and are dispersed in home are also being developed. That is home network control devices which are capable of supporting all communication protocols such as International Electrical and Electronics Engineering IEEE 1394 Universal Serial Bus USB Infrared Data Association IrDA X 10 and Lonworks are being developed.

However the standardization of the interoperable protocol for a Home Network Serving Node hereinafter referred to as an HNSN which functions as a central server provided for home networking and home automation and RGs installed in homes have not been conducted.

Accordingly the present invention has been made keeping in mind the above problems occurring in the prior art and an object of the present invention is to provide a RG system which is capable of integrally managing controlling and monitoring all devices connected to an OSGi and UPnP based home network.

First all devices which are connected to a home network through an OSGi based residential gateway can be integrally managed and detailed information about these devices can be acquired.

Second a standard for an OSGi based RG is presented so that various high quality home network services can be provided and at the same time the extension of devices and services can be facilitated.

Third a UPnP based RG system can be established so that devices in the home network can be controlled from outside the home network and remotely monitored and controlled using only a browser.

The present invention provides a Residential Gateway RG system for home network service the system receiving various supplementary services through a Home Network Serving Node HNSN that provides home network service the system including an OSGi framework an RG agent installed on the OSGi framework and implemented in bundle form a virtual UPnP device registered on the OSGi framework by the RG agent and a java virtual machine ported by the RG agent on hardware on which an operating system is installed.

In addition the present invention provides an RG system for home network service including an OSGi framework an RG agent installed on the OSGi framework and implemented in bundle form and UPnP device service registered on the OSGi framework by the RG agent.

In addition the present invention provides a UPnP based RG system for home network service the RG system including an HNSN connected to a mobile network to control devices and transfer control statuses of the devices and a home gateway connected to the HNSN through a network and connected to the devices wherein the home gateway comprises a Web server and a UPnP proxy that detect devices connected and disconnected to and from the home gateway and create a device list Web document receive a remote control signal which is generated by a user from the HNSN and perform control transmit a response message regarding the control and monitor event generation by the devices.

The construction and operation of an embodiment of the present invention are described in detail with reference to the accompanying drawings below.

The HNSN operates in conjunction with Personal Computers PCs or SK Virtual Machine VM or Wireless Application Protocol WAP mobile phone terminals connected to a network from which home network service can be received and functions as a central server for providing the home network service.

The RG is connected to the HNSN through the network or the Internet to receive various supplementary services. In particular the RG performs functions such as the control and monitoring of home devices the updating and rebooting of RG SoftWare S W and the control of gateway home network device using the Web service of a registration gateway and the setting of a network.

The local network may be constructed from for example a UPnP network and a Recommended Standard RS 485 control network that is a kind of Power Line Communication PLC and is connected to different types of home network devices UPnP cameras PCs Web PADs illumination devices crime prevention devices and the like to share information or control various functions.

Linux version 2.4.18 is used for the OS cvm 1.0.1 which satisfies J2ME CDC that is the java virtual machine of Sun Co. is used for the java virtual machine and the 4DAgent of 4DHomeNet is used for the OSGi framework .

Instead of a UPnP bundle the virtual UPnP device performs a UPnP protocol on the local network like an actual UPnP device.

The RG agent which is an agent that operates in conjunction with the HNSN is a bundle that uses the OSGi framework .

The HMS UI is a bundle that supports a graphic interface and the OAM is a kind of network management bundle that undertakes the operation management and maintenance of a network.

The devices such as PCs or Web PADs and UPnP devices which are connected to the RG operate in conjunction with HNSN though an RG H interface and the RG provides functions such as the registration and authentification of the RG periodic RG keep alive message transfer the controlling and monitoring of devices connected to the RG the rebooting of the RG and the updating of bundles.

The RG D0 interface which is an interface for network devices connected to the home IP network of the RG supports standard UPnP.

The RG D1 interface is collectively connected to RS 485 devices by a Control box C box connected with the RS 485 devices and is connected to the RG through an RS 232 interface. The interface between the C box and the RG is the RG D1.

An RG U interface which is UI that allows a user to directly control the home devices of Web PADs in home and the like is an interface that provides general Web service.

An RG O interface and an RG J interface are the internal interfaces of the RG. The RG J interface is an API that enables the java virtual machine to be ported to the hardware on which the OS is installed and the RG O interface which is an API between the OSGi framework and the bundles and provides an API that satisfies the standard of OSGi R and also provides an API for a service provider or preparing a virtual device.

The RG HNSN interface is a protocol in which an RG registration and authentification function and a keep alive function for RG management are added to a UPnP protocol having discovery description control and event functions for devices in an IP based home network and are then applied to a Wide Area Network WAN .

An RG side agent responsible for communication between the HNSN and the RG is the RG agent . The RG agent operates on an OSGi framework because it is implemented as an OSGi bundle. Furthermore since the HNSN and the RG agent perform communication through protocols such as a Simple Service Discovery Protocol SSDP a Hypertext Transfer Protocol HTTP a Simple Object Access Protocol SOAP and a General Event Notification Architecture GENA the RG agent implements the respective protocols.

The RG agent acts as a connection link between the RG and the HNSN registers the RG or periodically transmits an RG heart beat and informs the termination of the RG connection at the time of completion. Furthermore the RG agent manages a list of devices that are currently connected to the RG and allows the list to be transferred when the HNSN request it. Furthermore the RG agent transmits update information to the HNSN when the list of devices is updated.

The RG agent sends a registration message to the HNSN when the RG agent registers the RG on the HNSN. In this case the RG agent sends connection information and an RG ID password. The HNSN performs authentification using the RG ID password and stores the connection information of the RG and sends an OK response when the authentification has been successfully performed.

When the RG agent is successfully registered the RG agent transfers the heart beat of the RG to the HNSN by periodically typically at one minute interval sending the current IP information of the RG along with alive messages to the HNSN so that the RG agent allows the IP information of the RG to be managed.

3 Graceful bye function function of when the RG terminates informing the HNSN of the termination of the RG and of performing termination 

When the RG agent terminates normally or is rebooted the RG agent sends a bye message to the HNSN thus allowing the HNSN to manage the status information of the RG .

4 Connected device list maintenance function a function of managing a list of devices currently connected to the RG and transmitting the list to the HNSN 

When a request from the HNSN exists the RG agent transmits a list of the home devices connected to the RG .

5 New device notification function a function of detecting newly connected devices updating the list of the devices and notifying the HNSN of the detection of new devices 

When the RG detects that new home devices are connected to it the RG agent sends information about newly attached devices to the HNSN and updates the list of the devices.

The RG agent periodically reports the current status of the RG to the HNSN and acts as a proxy for devices that are installed in the home and connected to the RG .

When the RG agent receives device control commands from the HNSN the RG agent discovers and control corresponding devices. Thereafter the RG agent transmits the results of the control to the HNSN .

Querying to check the status of devices is processed in the same manner as in the device control function. When the HNSN transmits query instructions to the RG agent the RG agent checks the status of corresponding devices and transmits status values to the HNSN .

3 Device event subscription unsubscription function the HNSN applying and canceling the event subscription of devices 

The HNSN may subscribe to the events of a specific device. For the subscription to events the subscription to events is requested to the RG agent . The subscription to events may be cancelled when the subscription of events is not necessary any more.

4 Device event notification function transmitting events which are generated by devices to the HNSN that has requested the event subscription of the devices 

When an event is generated due to variation in the status of a certain device the RG agent transmits an event message to the HNSN that has requested the event subscription.

The UPnP collects the information about devices and controls the devices using protocols such as HTTP SSDP GENA and SOAP which are currently used based on Transmission Control Protocol TCP IP technology.

The HNSN and the RG agent transmit requests such as M SEARCH and NOTIFY to each other using SSDP UDP.

This is a request that is mainly transmitted to the RG agent by the HNSN and is used when the HNSN intends to acquire the list of home devices connected to the RG . Commonly M SEARCH is requested when the RG agent performs registration or a user makes a new change to the list of home devices of the RG through the HNSN UI. When the RG receives the request the RG checks currently connected home devices and responses to the request of the HNSN with the Web Uniform Resource Locators URLs of description files that describe respective devices inserted into the location header of a HTTP OK of the HNSN for the respective devices.

When the RG agent requests registration from HNSN and the HNSN responds to the request the RG agent transmits a list of devices detected by the RG agent to the HNSN using SSDP NOTIFY. Even in this case the RG agent transmits the URLs of the description files of the respective devices which are inserted into the location header similarly to the response of the M SEARCH.

This is used when the HNSN downloads an XML file from the description URL transmitted by the RG agent using SSDP.

This is used in two cases namely the case in which the RG agent is a control point device and the case in which the RG agent is a proxy device.

Assuming that the RG knows basically connection information about the HNSN the RG first requests registration from the SOAP port of the HNSN after the RG is booted and an engine is executed. The HNSN performs authentification and completes the registration by sending an OK response if the authentification is successful. The HNSN sends a 500 error response if authentification fails or errors exist. The RG waits for a predetermined time and then attempts registration again when the RG receives the 500 error response.

The RG periodically requests Alive to the HNSN thereafter when the registration is successful. The periodic Alive request is to notify the HNSN of any abnormality of the RG in the case in which the RG is abnormally operated or abruptly powered down. Furthermore when the RG has a flexible IP and the IP of the RG changes the periodic Alive request allows the HNSN to manage a changed IP.

The RG requests Bye to the HNSN upon being normally powered down by a user or a manager. The HNSN changes the status information of the RG to Power down upon receiving the Bye and sends an OK response. The RG terminates completely upon receiving the OK response.

This sets authorities that are capable of accessing to the RG and controlling and monitoring devices connected to the RG .

This acquires authorities that are capable of accessing to the RG set on the HNSN RG and controlling and monitoring devices connected to the RG .

When it is desired to perform control query on one device that belongs to a list of devices connected to the RG set on the HNSN the HNSN transmits a SOAP Request to the RG agent and receives result status information as a response.

When it is desired that the HNSN control a specific device a Control SOAP Request for controlling the device is transmitted to the RG agent and the RG agent controls the actual device and then transmits a Control SOAP Response containing resulting values to the HNSN .

When it is desired that the HNSN know the status information of the specific device a Query SOAP Request for performing querying the status information of the device is transmitted to the RG agent and the RG agent reads the current status information of the actual device and then transmits a Query SOAP Response containing the status information to the HNSN .

This is used when the HNSN applies for or cancels event subscription to monitor a specific device connected to the RG and makes known events generated by the device.

This is used when it is desired that HNSN subscribe to the events of a specific device of the RG . The RG agent has stored the Subscription of the HNSN and processes it when the events are generated from the corresponding device. Thereafter the RG agent transmits a GENA Notify Request containing the event to the HNSN .

This is used when it is desired that the HNSN cancel the event subscription of a specific device of the RG . The RG agent deletes the stored subscription of the HNSN and does not transmit a Notify Request to the HNSN even when the corresponding device generates the events later.

When the subscription of the HNSN to a device has been stored in the RG and the device generates events the RG transmits the Notify Request containing event details to the HNSN .

With reference to the internal structure of the RG is described below. Relationships between the RG agent and the OSGi framework the UPnP bundle and the UPnP device services are described.

The RG agent is implemented in bundle form installed on the OSGi framework hereinafter referred to as a framework and is a typical bundle application that can be driven by a bundle activator. The RG agent fetches and uses packages provided by other bundles and acquires and uses services registered by other bundles.

The RG agent fetches the UPnP device service that has been registered on the framework and constructs a list of devices and monitors the registration and registration cancellations and changes of the UPnP device service in real time by registering a service monitor on the framework . Thereafter UPnP event listener service which is capable of listening to the events generated by the UPnP device service is registered on the framework so that the events of a specific device can be subscribed to.

Although the RG agent and the UPnP bundle are not directly related to each other they are indirectly related to each other through the framework . The UPnP event listener service which is registered on the framework by the RG agent is managed by the UPnP bundle and events generated from the UPnP event listener service are collected by the UPnP bundle and are then transferred to the corresponding UPnP event listener.

Devices which are transmitted to the HNSN by the RG agent are UPnP device services rather than physical devices connected to the actual RG . To implement UPnP device services is to perform communication using physical devices and interfaces.

The UPnP device services are classified into two types. One is for directly registering the UPnP device service on the framework in a bundle and the other is for allowing the UPnP bundle to detect actual UPnP devices which are connected with the RG and exist on the local network using the UPnP protocol prepare UPnP device service and register the UPnP device service on the framework . The former performs the UPnP protocol on the local network instead of the UPnP bundle like the actual UPnP device which is called a virtual UPnP device.

The RG agent recognizes the two types of UPnP device services as UPnP device service without distinguishing them and transmits the list of devices to the HNSN upon receiving device list transmission request from the HNSN . Thereafter when the registration or registration cancellation of the UPnP device services are make known through the service listener registered on the framework the RG agent updates the list of devices which is transmitted to the HNSN through SSDP Notify Alive or SSDP Notify Byebye in real time.

The RG agent calls the API of managed UPnP device service upon receiving a device control and status query request from the HNSN . Thereafter the RG agent transmits returned values to the HNSN as a response. In the case in which the API of the UPnP device service is called and the UPnP device service corresponds to the actual UPnP device that exist on the local network the UPnP bundle transmits SOAP messages to the actual UPnP device and receives and returns responses. In the case in which the UPnP device service corresponds to the virtual UPnP device the UPnP bundle actually controls physical devices to which the implementation of the UPnP device services is connected and receives and returns responses.

The UPnP Proxy of the RG is constructed so as to provide a function by which a user can remotely control home appliances only using a browser. Furthermore the UPnP Proxy is constructed such that the user can use it by connecting to the HNSN server .

The UPnP Proxy of the RG operates in conjunction with the Web server and provides various services to provide the user client remote control function. That is the UPnP Proxy discovers devices connected and disconnected to and from the home network and creates a device list Web document using information about the devices. Furthermore the UPnP Proxy directly controls the devices according to user control commands transmitted from the user and transmits response messages corresponding to the control. Furthermore when device events are generated in the home network the UPnP Proxy transmits the events to the HNSN server based on HTTP thus allowing the user to know about the generation of the events.

Furthermore the UPnP Proxy changes the device list Web document so as to be compatible with the HNSN server using the connectivity of Web documents and an existing UPnP API. Furthermore the UPnP Proxy automatically creates HTML and XML presentations based on device descriptions and service descriptions for devices that do not provide presentations.

The HNSN server includes a message creation processing module and an event message processing module . The message creation processing module receives the device descriptions and the service descriptions from the RG and stores basic information about the devices in a device information database thus providing current status information and the basic information. The event message processing module receives event messages transmitted from the Proxy and transmits the received event messages to a handler management module.

The UPnP Proxy includes the bridge and the agent and provides a remote control function to a user through interoperability between the bridge and the agent . The bridge controls and manages home network devices and the agent performs the creation conversion and transmission of content or the transmission of events to the user.

The bridge discovers and manages devices connected to the home network using the UPnP Software Development Kit SDK of Intel Co. A device management module discovers devices connected and disconnected to and from the home network and stores information about the devices in the device database . Thereafter a control processing module controls the devices according to the user s control commands and as a result transmits response messages but processes the response messages when an exceptional situations occurs. An event processing module is a module that processes events when the statuses of the devices changes and thereby generates the events. On the basis of the bridge messages defined by the bridge device UPnP forum are used and remote control protocols are used between the bridge and the agent and between the agent and the HNSN server . Accordingly the bridge performs conversion between the two protocols which are performed in a message processing protocol conversion module

The agent is provided with the message creation processing module that operates in conjunction with the message processing protocol conversion module and the message creation processing module of the HNSN server . The message creation processing module is connected with an device event registration management module an automatic presentation creation and storage module a content creation conversion unit and a client information management module and operates in conjunction with them.

A user makes a connection to the HNSN server and the HNSN server requests the list of devices from RG at step S. The agent which receives the request requests the list of devices from the bridge at step S. The list of devices is transmitted to the HNSN server using the list of devices at steps S and S.

The HNSN server fetches the device descriptions and the service descriptions from the RG using the URL information in messages according to the list of devices.

After selecting the device the user selects control information from a Web document prepared using device description and service description documents received from the RG .

The user issues device control commands according to the selection of the control information on the Web document.

The agent which has received device control messages from the HNSN server transmits the control messages to the bridge and the bridge converts the control messages into SOAP messages to transmit them to the device at steps S to S.

The HNSN server requests and fetches the device descriptions and service descriptions from the RG at steps S to S.

The HNSN server registers events for a device desired to be controlled thus allowing event messages to be received when the corresponding device generates the events at steps S to S.

When the events are generated by the device the bridge transmits the generated events to the agent and the agent transmits the received events to the HNSN server at steps S to S.

The agent transmits the message to the bridge and the bridge transmits the event registration cancellation message to the device at steps S to S. Thereafter a termination process is performed at step S.

As described above the residential gateway system for home network service according to the present invention can be applied to an OSGi and UPnP based home network service field.

From above describe details those skilled in the art will appreciate that various modifications are possible without departing from the technical spirit of the invention. Accordingly the scope of the invention must not be limited to only details of the above described embodiment but defined by the claims.

