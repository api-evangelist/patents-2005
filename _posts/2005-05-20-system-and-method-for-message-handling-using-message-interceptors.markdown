---

title: System and method for message handling using message interceptors
abstract: A system including an interception service that serves as a discovery mechanism and framework for carriers to connect to processors. The system allows for message handling using message interceptors, comprising one or more message carriers for receiving and handling messages; one or more message processors for processing messages; and an interception service that registers interception points in the message carriers for allowing message processors to access the message.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07606855&OS=07606855&RS=07606855
owner: Bea Systems, Inc.
number: 07606855
owner_city: Redwood Shores
owner_country: US
publication_date: 20050520
---
This application claims priority from provisional application entitled SYSTEM AND METHOD FOR MESSAGING HANDLING USING MESSAGE INTERCEPTORS Application No. 60 573 208 filed May 21 2004 by Shean Chang and incorporated herein by reference.

A portion of the disclosure of this patent document contains material which is subject to copyright protection. The copyright owner has no objection to the facsimile reproduction by anyone of the patent document or the patent disclosure as it appears in the Patent and Trademark Office patent file or records but otherwise reserves all copyright rights whatsoever.

The invention is related generally to application servers and messaging systems and specifically to a system and method for message handling using message interceptors.

In an application server environment a message broker is a configurable intermediary that can process messages and make high level decisions about how they should be handled. Message brokers support routing filtering transforming duplicating and various other simple operations on messages. Message brokers are connected to normal processing paths by either being the explicit destination for a message or by intercepting messages intended for some other destination.

What is desirable is a means for taking responsibility off of the carriers and processors. One approach is to put a message broker interception code into the proper processing paths. However a better approach would be to separate the notion of interception from the description of processing. The only existing standard that is similar to this is JAX RPC handler chains. However while JAX RPC handler chains describe the processing of messages they do not offer a flexible means of registering message carriers with message processors.

In accordance with an embodiment of the invention an interception service serves as a discovery mechanism and framework for carriers to connect to processors. If desired a separate feature can be built that implements handler chains on top of the interception service as a type of processor.

Interception is the insertion of processing code in the normal flow of control of a program. This inserted code is given the power to supersede the standard processing or to complement it. As described herein an interception service for message handling elements of the WebLogic Server WLS is described. Other types of application server may use and benefit from the feature. There are four goals driving this design loose coupling extensibility dynamic manageability and minimality of performance impact.

In accordance with an embodiment the system includes the Message Interception Service interception service as well as the framework that it provides to those who are making messages available to be intercepted these are termed Message Carriers or for convenience carriers and those who are processing these messages termed Message Processors or simply processors .

The central premise guiding the feature is taking responsibility off of the carriers and processors. With that in mind the guiding principles in defining the interception service are as follows loose coupling between processors and carriers extensibility to support new carriers or processors over time manageability to support monitoring and configuration without special code in either and minimal performance impact so that the carriers can continue to function without fear that enabling interception will cripple their performance.

Interception Point The abstract notion of a place in the code where a carrier makes messages available to be intercepted.

Message broker An intermediary that gives administrative control to message routing and transformation.

JAX RPC Handler A java interface. javax.xml.rpc.handler.Handler that describes message processing functions for SOAP

JAX RPC Handler Chain Handlers are run in an ordered list described by javax.xml.rpc.handler.HandlerChain.

The interception service is an administrable table of associations between interception points and processors. It is also a table of processor information. As such the interception service provides a framework for the behavior of carriers and processors with respect to interception.

The interception service is designed to be administered through static method calls which add remove and modify associations and processor information. While these calls can and should be made by various elements of the system a part of the system is dedicated to storing interception service configuration information termed the Interception Service Configurator ISC . The configuration information can be passed through dynamic deployment of modules. This specification will not discuss the use of modules at the present time instead the focus will be on what runtime and configuration information will be available.

The interception service allows processors and interception points to be named and the administrator to choose which to connect to which.

In accordance with an embodiment there are seven operations provided by the interception service Interception Point Description Interception Point Registration Processor Type Registration Processor Registration Interception Point Processor Association Run Time Control and Interception.

There is one interception service on each server for example Weblogic Server . It is assumed however that all interception service instances across the cluster will be configured uniformly.

Each interception point type may have a different naming scheme. Through the registerInterceptionPointNameDescription method the carrier informs the interception service about the naming scheme of the interception points that it will register. The description includes information for each part of the name a name a validation function and the number of acceptable values for the name if the name can only take on a limited number of values this is useful information to the interception service .

Alternatively all names independent of interception point type may simply be a triple interception point type location and name.

When the carrier reaches a point in its execution where it is aware of an impending interception point it registers the existence of that interception point with the interception service via the registerInterceptionPoint call that it provides. It is returned a handle through which it calls the interception service which in turn calls the processor and with which it can unregister.

When a processor framework like the message broker boots it registers its processor type with the interception service through the registerProcessorType call. It also specifies a factory with which processor instances can be created by the interception service.

When configuration information is available about processors for example when the ISC boots the interception service is called to add to the list of configured processors through the addProcessor method. The interception service in turn invokes the particular processor type s processor factory in order to get a processor for runtime use. If the particular processor type is not yet registered this act will be deferred until registration. However a handle is returned to the caller in either case.

The basis of the interception service is a table of associations between names of interception points and names of processors. The interception service provides calls such as addAssociation through which an association can be added to the table removeAssociation through which an association can be removed from the table and getAssociationHandle and getAssociationHandles through which an individual association can be found or the complete set of associations can be enumerated.

When a carrier reaches an interception point its job is to call the interception service to reach any processors that may be associated with this particular interception point.

In the non optimized view of this it creates an object that implements the MessageContext interface from the JAX RPC standard javax.xml.rpc.handler.MessageContext and calls a process method of the handle that the interception service provided during registration. This will invoke the corresponding process method of the associated processor if one exists.

This can be optimized somewhat by querying the interception service before creating the MessageContext to see if there is an association configured for this interception point. This would save the possibly superfluous creation of the MessageContext.

The interception service is configured as a set of interception point processor associations. The table of associations can be searched and modified from outside the interception service. Further it is possible to enable and disable individual associations dynamically. Lastly any modifications to this table should be transparent to the carriers and processors excepting that processors may request to be informed of changes to its associations see Processor Awareness .

The interception service supports a registration mechanism for processors. Each registration must use a unique name. A handle is returned with which the processor can determine the interception points with which it is associated. A processor may deregister using the handle as well.

When a processor misbehaves e.g. throws a runtime exception the interception service will forcibly shutdown the offending processor. The processor will be informed of this event through the invocation of its on Shutdown method. It is assumed that the processor will inform the administrative software of this occurrence and that it will respond accordingly. It may choose to simply reenable the processor by removing and adding it.

The interception service makes it possible for external modules to see whether an association has a processor that is in the shutdown state i.e. has been shutdown but has not been reenabled .

The processor may specify a method to be invoked to be notified about changes to the state of its associations. There are two events currently which are considered to be state changes when the number of associated interception points goes from nonzero to zero and when the number of associated interception points goes from zero to nonzero. This is useful since processors may free or allocate resources when these events occur.

An interception point must follow the naming scheme that is described by its interception point type. The interception service verifies that this is so and otherwise throws an exception.

It is expected that a carrier will register with the same interception point name multiple times. Each registration may or may not return the same handle.

A particular interception point name may only occur once in the table of associations of the interception service. An attempt to add an association with the same interception point name as an existing association will throw an exception.

Each processor must register with a unique name. An attempt to register a processor with the same name as a processor which has already registered will cause an exception.

Interception point processing is deemed as necessary for the proper functioning of the carrier. If there is an association configured for an interception point yet no corresponding processor has registered or the processor has unregistered or been shutdown an InterceptionServiceException is thrown to the carrier when it attempts to invoke its associated processor. In other words a carrier cannot function without its associated processor.

The Interception Service needs certain guarantees from the processor for proper behavior. It needs to know that processor shutdown notification and processor state change notification calls will return promptly. The Interception Service provides similar guarantees to its callers. All administrative calls may be assumed to be of short duration. This includes adding and removing association registering and unregistering interception points and registering and unregistering processors.

The interception framework gives the processor the ability to say to the carrier that it has processed the message and that the carrier should not continue its processing. This is communicated via the return code of the process method. The interception service is not really involved in this it is merely specified here that the carrier should interpret the return code as described.

When it reaches an interception point the carrier may be at a point in its processing where it cannot allow the destination of its message to be superseded. A call process only is provided by the interception service and by the processor which only gives the processor the ability to read and write the message but does not give the processor the opportunity to tell the carrier whether or not to allow the message to continue along its current path.

A flawed configuration may cause a processor whose only function is to make such decisions to be called in this way. It is assumed that the processor will throw an exception which will cause the interception service to shut down the processor as described above.

The interception framework defines exceptions of two types one that indicates a problem that is not related to the particular message being processed and one that indicates a problem that is related to the message. Further the exception may indicate whether the problem is perceived to be of short or long duration.

The interception service must gather statistics for each association that is configured. It should keep track of the number of times the processor is invoked as well as the number of times that the processor supersedes the original destination of the message.

Due to the nature of interception the statistics may indicate something slightly different than expected. For a JMS example if a transaction is rolled back then a consumer side processor may see the same message twice and the statistics will reflect that occurrence. Therefore the number of messages intercepted may be different than the number of messages received by JMS as reported by JMS.

The interception service will provide logging that will note each time a processor registers as well as each time an association is added or removed.

While MBeans which correspond to the management interfaces of the interception service are mostly straightforward there is one type of MBean which requires more explanation. As described above the interception service allows different interception point types to have different naming schemes. Therefore there needs to be a different MBean for associations with each of the different interception point types. The following section discuss the carriers for example JMS and Web Services relationships to the interception service.

The following example illustrates an initialization and running of the interception service in which there is just one carrier JMS and all processors are part of the message broker. Further this example assumes that all processors and associations are configured through the ISC.

After boot the message broker comes up first. It merely calls a hard coded line which tells the interception service its name message broker and its processor factory.

Next the ISC reads its Mbeans. In this example these MBeans identify one processor and one association. The processor is of type message broker with name Route Through Chicago Office and has the associated configuration information that the message broker needs. The interception service configurator calls the interception service to describe this processor. The interception service in turn calls the processor s factory to create a processor. Next the ISC adds its one configured association to the interception service. Let us assume that this association is the following pair the multipart name of the interception point is S1 Q1 Incoming and the name of the processor is Route Through Chicago Office .

Next JMS starts. It calls the interception service to describe its naming scheme. Its naming scheme is that it has a server name which can take on any value a destination name which can take on any value and a location which can be either incoming or outgoing . That is it for now.

Next let us assume that a JMS producer starts JMS registers an interception point with the name S2 Q2 incoming . Let us assume that a consumer comes up next and JMS registers the name S1 Q1 outgoing . The reader will notice that neither of these interception points actually has a processor associated with it. So when JMS receives a message from the previously mentioned producer it asks the interception service if there are any processors associated with this particular point. Since there is no processor associated with this name JMS simply continues its processing.

Finally another producer starts which has the interception point named S1 Q1 incoming . When a message is received by the JMS server through this producer the interception service will now have an associated processor. So the JMS code creates a MessageContext and calls the interception service to process the message. The interception service in turn calls the processor to process it unless it has unregistered in that millisecond in which case it will just return true. The processor may return true or false if it returns false this indicates that JMS should not continue along its course true indicates that JMS should continue .

2. Total count of messages which the processor has allowed to continue along its path the number which have been superseded can be derived of course 

In accordance with an embodiment it must be possible to activate and deactivate an association. As described above an inactive association is functionally equivalent with respect to interception to there being no association configured.

In accordance with an embodiment the interception service configuration can configure processors with metadata.

The present invention may be conveniently implemented using a conventional general purpose or a specialized digital computer or microprocessor programmed according to the teachings of the present disclosure. Appropriate software coding can readily be prepared by skilled programmers based on the teachings of the present disclosure as will be apparent to those skilled in the software art.

In some embodiments the present invention includes a computer program product which is a storage medium media having instructions stored thereon in which can be used to program a computer to perform any of the processes of the present invention. The storage medium can include but is not limited to any type of disk including floppy disks optical discs DVD CD ROMs microdrive and magneto optical disks ROMs RAMs EPROMs EEPROMs DRAMs VRAMs flash memory devices magnetic or optical cards nanosystems including molecular memory ICs or any type of media or device suitable for storing instructions and or data.

The foregoing description of the present invention has been provided for the purposes of illustration and description. It is not intended to be exhaustive or to limit the invention to the precise forms disclosed. The embodiments were chosen and described in order to best explain the principles of the invention and its practical application thereby enabling others skilled in the art to understand the invention for various embodiments and with various modifications that are suited to the particular use contemplated. It is intended that the scope of the invention be defined by the following claims and their equivalence.

