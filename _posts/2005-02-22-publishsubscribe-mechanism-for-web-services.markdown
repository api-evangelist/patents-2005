---

title: Publish/subscribe mechanism for web services
abstract: A method for managing events in a web service environment is provided. A request for a subscription to desired events in an event class in an associated catalog namespace of a catalog repository is received from a subscribing application. The subscription request includes an event filter to select the desired events from a plurality of events described by the event class. An event which is received from a web evens source and described by the event class is processed through the event filter. If the received event matches the event filter, the received event is forwarded to the subscribing application through an event listener associated with the subscribing application.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07958515&OS=07958515&RS=07958515
owner: Computer Associates Think, Inc.
number: 07958515
owner_city: Islandia
owner_country: US
publication_date: 20050222
---
This application is a Rule 1.53 b continuation and claims the priority of application Ser. No. 10 851 620 filed May 21 2004 now abandoned which claims the benefit of U.S. provisional application 60 473 323 filed May 23 2003 and entitled A PUBLISH SUBSCRIBE MECHANISM FOR WEB SERVICES which is incorporated in its entirety herein by reference.

This application relates to web services. In particular the application relates to a publish subscribe mechanism for web services.

The World Wide Web is widely recognized as a vast source of information. However the Internet and the web are not merely an information source. The web is rapidly becoming a preferred medium for application software and web services are emerging as the next generation platform for distributed application software.

Web services are web software typically self contained self describing and modular that can be located and invoked across the web. Web services may perform functions ranging from simple requests to complex business processes. Once a web service is deployed other applications and other web services typically can discover and invoke the deployed service. Web service platforms enable application software to communicate synchronously or asynchronously over standard Internet protocols such as HTTP HyperText Transfer Protocol SOAP Simple Object Access Protocol UDDI Universal Description Discovery and Integration etc. Web Services Description Language WSDL is an XML extensible Markup Language language that may be used to describe a web service and specify a manner of communicating with the web service. The specification is often referred to as a WSDL contract .

The term event specific to the context of computer technology or the web means a change or notification of change in condition or state within a system. An event may be triggered by user operation through an interactive device for example a keystroke a mouse button click words spoken through a speech interface etc. or by operation of software.

Software platforms sometimes provide a publish subscribe mechanism which can be used by application software to raise publish events or express interest subscribe in events which may be published by other application software. While use of the Internet and web services is proliferating a publish subscribe mechanism for web services to manage events over the web is still lacking.

The term event as used herein should be construed in a manner consistent with its conventional meaning in a computer art or web context and or to include a data object corresponding to the conventionally known event.

The subject application provides a method for managing events in a web service environment. In one embodiment the method includes receiving from a subscribing application a request for a subscription to desired events in an event class the subscription request including an event filter to select the desired events from a plurality of events described by the event class registering an event listener associated with the subscribing application processing through the event filter an event which is received from an event source and is described by the event class and notifying the subscribing application of the received event through the registered event listener if the received event matches the event filter.

The application also provides an apparatus for managing events in a web service environment. In one embodiment the apparatus includes a catalog repository and a publish subscribe web service. The catalog repository includes one or more catalog namespaces. The publish subscribe web service includes a subscription management component and an event processing component. The subscription management component receives from a subscribing application a request for a subscription to desired events in an event class in a catalog namespace of the catalog repository. The subscription request includes an event filter to select the desired events from a plurality of events described by the event class. The subscription management component registers an event listener associated with the subscribing application. The event processing component processes an event which is received from an event source and if the received event is described by the event class and matches the event filter forwards the received event to the subscribing application through the registered event listener.

The methods and apparatus of the present disclosure may be embodied in a program of instructions executable by a machine such as a computer or computer system which is stored in a storage medium or transmitted in one or more segments in a transmission medium.

The present disclosure provides tools in the form of methods apparatus and system for managing events in a web service environment including a publish subscribe mechanism for web services.

There are many types of systems in a distributed applications environment that can use a publish subscribe service. presents a high level view of an exemplary system referred to below as CAM in which agents technology is used to collect information for the applications. CAM system includes a number of agents through and some management applications through connected through network .

The system management applications may include for example enterprise management security storage data management portal intelligence add on etc. The applications process information collected through the agents and make system management decisions either automatically or with help of a human operator. The decisions may be mapped to actions performed by the agents.

A number of types of communications may take place between the agents and the management applications . For example streams of system status messages may flow from the agents to the management applications. In addition there may be streams of control messages flowing back from the management applications to the agents.

A control message typically has a well defined source and a well defined destination. Therefore it can be delivered using a traditional one to one request and or reply protocol for example RPC Remote Procedure Call mechanisms such as IIOP Internet Inter ORB Protocol Java RMI Remote Method Invocation COM Component Object Model or SOAP RPC .

Status messages sent by agents typically are caused by changes in the environment for example events and are therefore asynchronous by nature. In addition an agent sending a message is generally decoupled from the management applications and rarely knows the applications receiving the message. There can be many management applications receiving messages from a single agent. Therefore the sending of status messages is typically an asynchronous one to many type of messaging which generally cannot be carried over a traditional RPC link. Instead a publish subscribe mechanism is used.

The architecture of a publish subscribe framework for the CAM system is shown in . Publish subscribe framework includes a messaging hub and runtime services .

The messaging hub includes a store and forward messaging mechanism that provides asynchronous and synchronous APIs Application Program Interfaces for sending and receiving messages. Events may be delivered from agents to the messaging hub and then from the messaging hub to event subscribers such as an event console an object repository an application etc. In addition the messaging hub implements event advertising routing and filtering functions.

Runtime services form the engine room of the framework to scale extend and perform to the demands of the system. In addition to publish subscribe services runtime services may also provide other services such as cache management catalog management for example object mapping etc.

Other frameworks similar to the CAM publish subscribe framework are also conventionally known. Many of the frameworks use conventional proprietary messaging platforms for example such as MSMQ from Microsoft or MQSeries from IBM to send and receive messages. The conventional messaging platforms may provide a capability of sending messages over HTTP. For example a SOAP request can be sent typically as a message through one of the conventional messaging platforms via HTTP tunneling 

However an application that sends messages via HTTP tunneling through a conventional messaging platform misses a main benefit of web services i.e. interoperability. Interoperability means two or more software work together without requiring significant alterations and with the interface between the software being transparent to the end user. For example interoperability may include exchanging data files between the software. In addition a software having interoperability which is written for one computer platform can run without modification on other platforms.

In order to send a SOAP message from for example a wireless device through one of the conventional messaging platforms the client side library of the conventional proprietary platform generally must already be deployed on the wireless device. Therefore conventional messaging platforms allow only limited interoperability and a publish subscribe framework based on a conventional messaging platform is significantly limited in a heterogeneous environment.

It is desirable to have a publish subscribe framework available as a web service and for client applications to be able to locate and invoke the publish subscribe service with help of ubiquitous Internet protocols such as HTTP SOAP and UDDI in order to render the framework more suitable for use by web services 

Some exemplary embodiments of methods and apparatus for managing events in a web service environment are described below.

An apparatus for managing events in a web service environment according to one embodiment includes a catalog repository and a publish subscribe web service . The catalog repository includes one or more catalog namespaces. The publish subscribe web service includes a subscription management component and an event processing component . The subscription management component receives from a subscribing application a request for a subscription to desired events in an event class in a catalog namespace of the catalog repository . The subscription request includes an event filter to select the desired events from a plurality of events described by the event class. The subscription management component registers an event listener associated with the subscribing application. The event processing component processes an event which is received from an event source and if the received event is described by the event class and matches the event filter forwards the received event to or notifies the subscribing application through the registered event listener.

The apparatus may optionally further comprise an event gateway. The event processing component receives the event through the event gateway from a web event source over the Internet through an Internet protocol and forwards the received event through a local messaging protocol to a local subscriber if the received event matches an event filter included in a subscription request of the local subscriber.

A method for managing events in a web service environment according to one embodiment includes receiving from a subscribing application a request for a subscription to desired events in an event class in an associated catalog namespace of a catalog repository step S the subscription request including an event filter to select the desired events from a plurality of events described by the event class registering an event listener associated with the subscribing application step S processing through the event filter an event which is received from an event source and is described by the event class step S and notifying the subscribing application of the received event through the registered event listener step S if the received event matches the event filter step S Yes . The method is preferably implemented through a web service. The event listener may identify an endpoint of the subscribing application. The event filter may be a query defined on the event class.

The subscribing application may be a web application for example in a conventional client server configuration . Alternatively the application may be locally resident on a computing platform which provides web access and or network access.

The subscription request may also include an endpoint of the subscribing application and the received event is forwarded to the endpoint if the received event matches the event filter. The subscription request may further Include a a name of the event class which describes the desired events and b a path of the catalog namespace in which the event class is defined. The subscribing application may determine a the name of the event class which describes the desired events and b the path of the catalog namespace in which the event class is defined by retrieving a handle to the event class from the catalog repository. Thus a subscribing application can easily locate and invoke the subscribe service. The method may further comprise receiving a subscription request from a local subscriber and notifying the local subscriber of the received event through a local messaging protocol if the received event matches the event filter.

The method may further comprise defining the event class in a schema of the associated catalog namespace of the catalog repository to advertise the plurality of events described by the event class.

The method may further comprise receiving the event from the web event source over the Internet through an Internet protocol. The subscribing application may be notified of the received event over the Internet through an Internet protocol. The method may further comprise decoding the received event creating an event object associated with the received event as a member of the event class describing the received event and broadcasting the event object through registered event listeners to subscribing applications. Alternatively the web event source may create the event object and either forward the event object or a handle to the event object to the web service.

A software application deployed on the web can easily raise an event by simply posting for example a SOAP message to an HTTP endpoint associated with the event class.

A web service which incorporates a publish subscribe framework according to one embodiment of the present disclosure is outlined below.

An event management mechanism with a publish subscribe framework as described herein may be integrated in for example an enterprise management portal system . The system provides through a portal distributed services including one or more enterprise management applications such as network and system management automated operations management IT information technology resource management database management web infrastructure management application management etc. A common services component of the system is included to enable integration efficient management a consistent administration interface and ease of use of the management applications. The common services include runtime services which perform an array of services to support the distributed nature of the system including catalog management object caching and event services. The common services include an event management facility with a straightforward API application programming interface that can be used to advertise available event types subscribe for events and to raise events in namespaces corresponding to various information providers.

Each application etc. in which accesses the web service has an associated instance of the runtime services in . Each instance of the runtime services can connect to a catalog repository that contains meta data describing data events and services offered by various information providers. An agent a relational database a file system folder an application etc. are all examples of information providers.

Meta data information stored in the catalog is structured as a collection of namespaces. A catalog namespace contains a schema and a collection of other namespaces. The schema of a namespace consists of classes that describe events objects and services available from the corresponding information provider.

A fragment of a catalog namespace tree is portrayed in which shows a few exemplary catalog namespaces. One of the namespaces the one that is expanded in corresponds to a file system provider. The schema of the namespace contains four classes. One of the classes describes the type of objects located in the namespaces. The name of the class is File . The remaining three classes describe the types of events that can be inserted in the namespace. The names of the classes are self explanatory. Each of the event classes may have several properties describing events.

If an information provider for example in wishes to advertise its events in a certain namespace it can create one or more event classes in the schema of that namespace through the associated instance of the runtime services. This information is stored in the catalog and can be examined by any application for example etc. that has sufficient security privileges.

An application for example etc. can subscribe to events described by an event class and originating in a namespace by specifying the path of the namespace and the name of the event class. For example the application can retrieve a handle to the namespace from the catalog and create an event filter through the associated instance of the runtime services. The event filter may be a query defined on the event class. The subscribing application registers the event filter and an object that implements an event listener interface with the associated instance of the runtime services. The subscription process is illustrated by the following exemplary code fragment 

An event listener object implements the event listener interface which may be defined for example as follows 

When an event matching the filter is detected by the runtime system the handleEvent method of the listener object which receives the event object as an argument is invoked.

An application sending an event may first create an event object and then use the raise method of the runtime services to broadcast this event to listeners such as exemplified by the following code fragment 

The runtime services ensure that remote and local listeners are notified. For example events may propagate events between instances of the common services runtime system.

There are several ways to encode information in the body of a SOAP message. For example it can be encoded either as an RPC call or as an XML document. The style of encoding may be controlled by a switch in a WSDL contract for the service. The body of a SOAP message sent to an operation which is encoded as an RPC call may be declared as follows 

The body of a message sent to an operation which is encoded and interpreted as an XML document may be declared as follows 

There are strict rules governing how parameters of an RPC request are to be encoded in the body of a SOAP message. Document style encoding on the other hand is very non restrictive and allows virtually any type of XML documents. When flexibility or extensibility is desired document style encoding is generally preferred.

The method of the runtime services which is used to subscribe for events is static in nature. Therefore it can be safely mapped to an operation with RPC encoding.

The raise method on the other hand is dynamic. Event objects passed to this method are defined by classes stored in the catalog repository. Since it is difficult to recompile an application each time a new event class is added to the catalog document style encoding is preferably used for the raise operation.

Multiple events may be encoded as part of a single SOAP message in order to reduce the number of network roundtrips. Each event is mapped to an XML element. The name of this element corresponds to the name of the class describing the event. Different namespaces in the catalog may contain event classes with identical names. Names of event elements may be qualified by placing them in different XML namespaces. The URL of an XML namespace containing the name of an event element may be derived from the path of the namespace containing the corresponding event class. The mapping is very simple. If the path of a namespace is Root File System Provider then the URL of the corresponding XML namespace is http ccs.ca.com Root File System Provider . Properties of event objects are mapped to elements nested in the event element. Property values are encoded as strings. The original type of a property is indicated in the value of the xsi type attribute.

A portion of the public subscribe service for processing events submitted over SOAP HTTP by external applications may be implemented as a servlet extending the JAXMServlet class defined in JAXM one of the standard Java APIs for web services. The onMessage method of this servlet can be written as follows 

With help of a servlet capable of processing events encoded as SOAP messages an event gateway may be provided to allow applications located outside of a company firewall to send events to subscribers deployed on the internal company network . When an outside application submits a SOAP message to the gateway these subscribers receive for example CAM MSMQ or JMS Java Message Service messages. Thus events can be received over SOAP HTTP and translated to events in the common services runtime system.

In addition the publish subscribe service may be adapted to forward events received from the common services runtime system to external web based event subscribers such as by implementing an event listener class as shown below 

Accordingly web based applications can use the publish subscribe service to send and receive events. In addition the publish subscribe service can play the role of a gateway translating event messages between SOAP HTTP and messaging protocols used on local networks such as MSMQ JMS or CAM .

As described above RPC encoding may be used for the subscribe operation of the service. In addition a WSDL contract may be defined for this operation. Once the contract is ready a WSDL compiler can be used to generate client side and server side stubs for automatic encoding and decoding of SOAP messages.

A WSDL document may be written in XML and consist of many interrelated sections. Most web services development kits are capable of generating a WSDL contract from an interface defined in a conventional programming language such as Java or C . The following subscription management interface defined in Java takes advantage of this capability 

An application can subscribe for events from the publish subscribe service by submitting one or more subscription objects. Each subscription object carries a number of properties such as the following examples an endpoint at which the application is listening for events e.g. http myapp.org 8080 listener the path of a namespace in the catalog e.g. Root File System Provider the name of an event class defined in this namespace e.g. FileCreatedEvent a query expression used to filter events e.g. path like .doc .

Once the communication stubs are generated with a WSDL compiler the IEventManager interface for the subscription management service can be implemented as follows 

When a subscription request arrives from a web client its endpoint may be used to create a new event listener object. The listener object and the event filter provided as part of the subscription request may then be registered with the common services runtime system. When an event matching the subscription criteria occurs in the runtime system the handleEvent method of the event listener is invoked by the event manager. The method encodes the event in SOAP XML and posts it to the endpoint provided by the subscriber.

A publish subscribe web service according to the subject application can be used by applications deployed on the Internet for example to subscribe for send and receive events using ubiquitous Internet protocols. In addition the service can work as a gateway between SOAP HTTP and traditional messaging protocols such as JMS MSMQ MQSeries and others. The publish subscribe service can be used in a large number of applications which use asynchronous one to many messaging for example system monitoring and management information replication instant messaging peer to peer computing and others. The service may be implemented as an extension of an existing publish subscribe framework with help of an off the shelf web services development kit.

The above specific embodiments are illustrative and many variations can be introduced on these embodiments without departing from the spirit of the disclosure or from the scope of the appended claims.

For example the following variations may be introduced event objects may be encoded in SOAP event objects encoded in SOAP may be sent over a protocol other than HTTP events may be sent directly from producer to consumer while bypassing the broker other event filtering mechanism may be used etc.

Elements and or features of different illustrative embodiments may be combined with each other and or substituted for each other within the scope of this disclosure and appended claims.

