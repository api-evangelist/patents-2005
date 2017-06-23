---

title: System and method for software component plug-in framework
abstract: The invention provides a software component plugin framework. The system described supports dynamic loading, instantiation, and unloading of interface implementations (plugin modules), together with encapsulation of these interface implementations. The many benefits provided by the invention include software reuse, interoperability and fast product development cycles.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07752637&OS=07752637&RS=07752637
owner: BEA Systems, Inc.
number: 07752637
owner_city: Redwood Shores
owner_country: US
publication_date: 20050720
---
This application is a continuation of U.S. patent application SYSTEM AND METHOD FOR SOFTWARE COMPONENT PLUG IN FRAMEWORK application Ser. No. 09 918 880 filed Jul. 31 2001 which claims the benefit of U.S. provisional application SYSTEM AND METHOD FOR SOFTWARE COMPONENT PLUG IN FRAMEWORK Application No. 60 294 467 filed May 30 2001 each of which applications are incorporated herein by reference.

A portion of the disclosure of this patent document contains material which is subject to copyright protection. The copyright owner has no objection to the facsimile reproduction by anyone of the patent document or the patent disclosure as it appears in the Patent and Trademark Office patent file or records but otherwise reserves all copyright rights whatsoever.

The invention relates generally to object component models and specifically to a system and a method for enabling plugin applications in a framework architecture.

Today s business environment has become increasingly dependent on electronic commerce or e commerce applications for their day to day operations. E commerce applications typically define such enterprise wide functions as supply chain management purchasing sales finance manufacturing enterprise resource planning and data processing. An e commerce application is typically designed to operate or run on a dedicated computer server or group of servers known collectively as an e commerce or transaction server. Such server products include the TUXEDO product from BEA Systems Inc. San Jose Calif. Weblogic Server also from BEA Systems Commerce Server from Microsoft Corporation in Redmond Wash. and both Avila and CRM from IBM Corporation Armonk N.Y.

The key requirements for such servers are that they be proven reliable and scalable so as to meet the needs of a growing organization. Some products are also designed with flexibility in mind. Particularly TUXEDO is geared towards providing a powerful and flexible end to end e commerce solution that can be used to connect and empower all users while integrating all of a corporations corporate data.

One of the primary disadvantage of such e commerce or transaction servers is that they tend to be very large applications in and of themselves. The typical e commerce server ships as a server application that must be compiled to form an engine or kernel through which client applications may then communicate. Once compiled very little can be added or modified to the server application and hence to the system without requiring a reconfiguration of this kernel.

Traditionally in order to add personalities or extensions the server kernel must be re configured and recompiled at each step. This necessitates server downtime and greatly increases the risks that errors will be introduced either during the recompile process or during the attempt to get the server running again in the shortest possible time. As shown in switching to a TUXEDO personality adding a connection module extension and then adding a security module extension may take as many as three server downtimes and kernel recompiles. Such compile problems are also encountered when adding routine server application updates and software patches. The traditional server architecture likewise does not lend itself to reuse of Module code when the server kernel is itself replaced. Much time and cost is spent re writing code for new releases of a server product that does much the same as the last version of the code. Customers who develop custom code to run with or within their server product find their code unusable with server releases of the server product. The overall result is one of redundant coding expense and wasted time.

To address this issue the inventors have concluded that it would be advantageous to break the existing application transaction server or e commerce server into a set of more manageable components. This would also address the following goals 

Allow commerce and transaction server customers to reuse their client applications with newer or future server products.

Eliminate additional steps of porting and recertifying other related server based products because of changes to the currently offered server infrastructure.

Address the needs of e commerce server customers who suffer because their server based products include bugs that have been corrected in the latest version of the server system.

Reduce the amount of code copied changed across products through componentization and encourage the reuse of software code to minimize redundant coding.

Consequently to address these goals the inventors propose an e commerce server architecture wherein a server engine component referred to herein as an engine plays a center role in providing some basic services and also a plugin mechanism that allows the customization of the engine. This customization may include well defined interfaces to the engine and call outs from the engine. Personalities are provided through plugin modules including any customizations to the engine s set of extensions.

Within the server engine dynamic linking and loading of a plugin module referred to herein as an interface implementation and encapsulation of that interface implementation occurs in such a manner that the interface implementation is totally hidden from the interface user i.e. the component acting as a client or client application .

As disclosed herein the invention provides a plugin framework that may be incorporated into or as part of an application server engine to allow dynamic customization of the engine interfaces in terms of extending them through plugin modules. These plugin modules are in turn provided by personalities and engine extensions. Application server engines that may be used with the invention include both e commerce transaction and application engines. One embodiment of the engine Plugin Framework provides the following features 

Plugin application programming interfaces APIs that act as extensions to the engine provided interfaces

Both DLL Dynamic Link Library and non DLL types of containers for plugin modules may be supported through various embodiments of the framework architecture. A system incorporating this new architecture can be visualized as a pool of software components interacting with each other through a client server relationship. As used herein a software component is considered a client when it asks for a service provided by another component and is considered a server when it provides a service being requested by another component. The set of services offered by a component is accessed through a well defined interface. A component can offer multiple sets of either interrelated or not interrelated i.e. independent from each other services through corresponding interfaces. To the client a component thus appears as a set of interfaces. The client does not care how these interfaces are actually implemented by the component. Components as used in this context of this application are thus the implementation provider for a given set of interfaces they support. A component can be removed from an application and replaced with another component so long as the new component provides an implementation for the same interface as the old component did.

When implementing such an interface architecture one of the early design decisions regarding the use of components is to decide on the medium or container for making the component available during run time. There should be a backing implementation for each interface being invoked by a client. This implementation library can be dynamically linkable if the requirement is for separating the client from the interface implementation and dynamically loadable if the requirement is to not load the component until it is actually needed. The library may be another process on the same i.e. local node or on a remote node.

Included below is a brief glossary of terms acronyms and abbreviations which will be useful in understanding the detailed description of the embodiments that follows 

 . . . indicates a token which can be replaced by a real value conforming to the syntax specified. The value between and is often replaced with a plugin specific name to retrieve plugin specific functions.

A component is a set of software modules that are bundled together and which provide implementations for a set of services specified by the corresponding interfaces.

An interface is a contract about a set of services between the requesters clients and the providers servers of the services. This contract specifies a set of functions with the associated syntactical and semantical properties for example the input output parameters and the return values etc. Components utilize a client server relationship and communicate with each other through interfaces.

With this architecture the engine can be further visualized as shown in as a pool of software components interacting with each other through a client server relationship. A component is considered a client when it invokes a service provided by another Component and a server when it provides a service being invoked by another component. The set of services offered by each server component can be accessed through a well defined interface . A server component can offer multiple sets of services through the corresponding interfaces which may be interrelated or not interrelated independent from each other .

An interface is a binding point between a client component and the server component. The client component need not know how these interfaces are implemented by a server component. In other words the server component backing the interface is totally transparent to the client component. This means that an implementation a plugin of an interface can be replaced by other plugins at run time without impacting the client application code.

To a client an interface may for example be a C language data type structure of which every member is a function pointer pointing to the plugin functions implementing the services defined by the corresponding interface. An interface is thus only a formal specification of a set of services until it and its corresponding implementations or plugins is registered and subsequently realized. As such an interface has to be realized before its services can be invoked. The interface realization process consists of locating the specified implementation loading it into the caller s address space and populating an internal table of pointers with the addresses of the plugin functions implementing the services defined by the corresponding interface.

One method of defining an interface is to use a standard specification such as the Object Management Group s hereinafter referred to as OMG Interface Definition Language hereinafter referred to as IDL or a subset of it. However one can alternatively use any language which supports a structure record or an equivalent type of data structure with double indirection support e.g. the struct command used in C or C . The method of actually defining an interface is not necessary for an understanding of the present invention and can be left to the interface developer.

The interface developer is however expected to provide the following software modules which are then linked by the clients and or the plugins of that interface prior to run time 

Header Files Both the client applications and the plugins use header files to define interfaces function prototypes of the interface functions and the macros for the invocations of various interface functions. These header files are included into the client application and the plugin s source code.

Client stub files The client application uses client stub files for invoking the interface functions. A client stub defines an interface as a set of language specific data types and routines one for each function method that is part of the interface. These client stubs are compiled and linked into the client application.

Plugin skeleton files A plugin uses the plugin skeleton files to map client invocations of interface functions to the actual function implementations in the interface implementation i.e. the plugin .

In one embodiment of the invention every interface has a name that serves as the compile time type in the code that uses that interface. These programmatic types are defined in header files provided by the interface developer.

The programmatic name for an interface is only a compile time type used within the application source code. Each interface also has a unique run time identifier with the following syntax 

It will be evident to one skilled in the art that the particular variable names and syntaxes given here are for exemplary purposes and that the invention is not limited to the specific syntax described herein.

In accordance with one embodiment there is one universal namespace for recording s in the engine PIF. Each is unique within this namespace. In addition to every interface may also have a version associated with it specified as two numbers a and a . The combination of an together with a version uniquely identifies a particular version of an interface.

Versions are used to indicate compatibility among interfaces and particularly between releases of the same interface. A change implies a different interface. Different major versions of an interface are not expected to be compatible with respect to each other. However the same s but different s of an interface should be compatible in the sense that a version with higher should be downward compatible with the version with lower . Both the and the can be given by a numeric string representing a number between 0 and 256.

Each engine s personality and extension has a unique . An should be unique within a component which owns it. The component provider who may be a third party vendor or developer is responsible for assigning s s and s to the interfaces which they provide.

In accordance with an embodiment of the invention every implementation of a supported interface has a unique implementation ID implId with respect to the interface it is implementing. This implementation ID has the following syntax 

There is one universal namespace for recording s in the engine PIF. Each is unique within this namespace.

Interface version compatibility is an important issue between an interface requested or invoked by a particular caller and the interface implementation or plugin which backs or realizes the interface. In accordance with one embodiment oft the invention every interface has a version number that can be specified in terms of major and minor version numbers. A plugin is an implementation of a specific version of an interface. The following rules apply with regard to version compatibility between the interface being realized and the plugin being considered to back the interface during the realization process the processing of  epif realize function 

Each plugin has a run time knowledge of the version of the interface for which it is providing an implementation. If the major version number of the interface which the caller is attempting to realize and the major version number of the interface which the specified plugin implements are different then the interface and the plugin are not compatible and in this case the realization of the interface fails.

If the major version number of the interface the caller is attempting to realize and the major version number of the interface which the plugin specified implements are the same then the following subset of rules apply 

An interface with a higher minor version number is downward compatible in terms of functionality and function signatures with interfaces with lower minor version number and identical .

An interface with a lower minor version number and identical is a subset of an interface with a higher minor version number.

During the realization process the backing plugin i.e. the one which is realizing the interface must have a minor version number which is equal or higher than the minor version number of the interface being realized. Otherwise the interface and the plugin are not compatible.

The Vtbl returned by a plugin implementing an interface with a higher minor version number is allowed to grow only in a downward compatible way in terms of both size and content with the Vtbl of a plugin implementing the same interface but with a lower minor version number. The term Vtbl used herein takes its common meaning and is a term known to one skilled in the art.

The rules described above are given to illustrate a particular embodiment of the invention and particularly version numbers used within that embodiment. It will be evident to one skilled in the art that other rules can be substituted for or added to those shown above while remaining within the spirit and scope of the invention.

PIF profiles provide a way of associating a PIF client the caller of a PIF external interface function whether it is an application process or a system process with a set of PIF related attributes during run time. A PIF client may want to use its own implementation for a specific interface or it may want to realize a different implementation.

PIF profiles are identified by unique profile identifiers called s. The syntax of a is specified below.

There is one universal namespace for s in the engine PIF. Each is unique in this namespace. The PIF can be configured to always search the profile specified by an EV PIF PROFILE environment variable in or before it searches for the default system wide profile. A group of clients may be associated with the same profile and consequently refer to the same set of interface implementation object attributes. A PIF client may be associated with an existing PIF profile by setting the EV PIF PROFILE environment variable to the desired .

The PIF needs to locate the necessary plugin container which can be a DLL which contains the specified plugin in order to load it into the registry Therefore it needs to know its image path and also other attributes about the interfaces and the interface implementations it is dealing with. To accomplish this an embodiment of the invention uses a persistent storage based data repository for storing this kind of information. The PIF does not require a particular structuring for the persistent storage based plugin related information. Instead the PIF describes this plugin information and specifies a set of command utilities for registering and unregistering plugins and for querying and or updating the stored plugin information. Within this document the data repository that is used for storing PIF related information is referred to as the registry . In the registry interfaces and interface implementations are identified by s and s respectively.

Both the interface and the implementations backing it have an associated set of attributes. In addition an implementation is always associated with the interface it implements. Given a particular interface there may be multiple implementations for that interface. An interface identifier is an attribute of an interface implementation identifying the interface this particular interface implementation implements. An implementation identifier is an attribute of an interface it is associated with the implementation.

In object oriented terminology the registry may be considered a persistent store for PIF related objects and their associated attributes. These PIF related objects and their attributes are described in table 1 table 2 and table 3. Table 1 lists some interface objects table 2 implementation objects and table 3 profile objects. It will be evident to one skilled in the art that other objects can be stored within the registry to supplement or replace those shown while remaining within the spirit and scope of the invention.

Before an interface implementation can be used i.e. before it can be realized it must be installed in the system and registered within the registry. Unregistration and or uninstallation of the interface implementation is required to later remove all the relevant information from the registry. To accomplish these tasks the PIF provides the following command utilities 

The functions epifreg epifunreg epifregedt and the other functions described below are given these function names for purposes of illustration. It will be evident to one skilled in the art that the invention is not limited to using the specific functions described herein.

In one embodiment of the invention a dynamically loadable library DLL is used as the component server or container. Implementations of the interfaces plugins are contained inside DLLs. In accordance with one embodiment a DLL may contain only one plugin although their embodiments may support multiple plugin DLL s. A plugin may not span over multiple DLLs. A DLL may contain multiple plugins which may or may not be for the same interface. A DLL may contain a derived plugin which implements only a subset of the functions which make up the corresponding interface and which inherits the implementation of the remaining functions of the interface from another plugin.

The PIF provides the following functions or services for loading and unloading a DLL to and from the caller s address space and for getting the address of a function in a loaded DLL 

 e dl unload is used for unloading a dynamically loadable library DLL module from the calling process address space. This function also decrements a reference count associated with the specified library.

 e dl geffuncaddr is used for getting the address of an exported dynamically loadable library DLL function given a function name.

These functions can be provided as a library tailored to each desired or supported personality. For example for use with TUXEDO the functions may be provided through a TUXEDO standard libgp library.

 e pif dupref for incrementing the reference count associated with an instance of a plugin which can be used for lifetime control or for duplicating a plugin instance.

 e pif release for decrementing the reference count associated with an instance of a plugin used for lifetime control.

 e pif interception seq for getting the ordered sequence of interface pointers of the plugin instances in the fanout type interception sequence.

Following the registration process the registry thus contains a list of all current implementations. When a client application makes a request to use an implementation they must realize the interface. This is performed through an  e pif realize routine. Other routines such as  e pif getinfo allow the client application to get additional information about the interface. A call to realize the interface is passed to a kernel portability layer . The kernel portability layer allows the PIF itself to be independent of the operating system layer . The PIF translates the realize request from the client into a series of function requests to the kernel portability layer to load the appropriate implementation container. The PIF also issues requests to the appropriate container to instantiate a particular implementation and later passes requests to release that implementation .

For an interface to be useful an interface has to have a language binding an implementation and a well defined set of rules for interaction between the client and the implementation of the interface. This set of rules comprises the interface realization protocol. The interface realization protocol encompasses rules governing client invocation virtual function tables plugin instantiation and reference counting. In accordance with an embodiment of the invention the client of any particular interface must have a handle pointer to a newly created instantiation of a plugin backing the interface before it can invoke any of the functions of the interface. It acquires this handle for the interface by invoking the  e pif realize function an example of which is shown in listing 1 TM32U is used to refer to an unsigned integer variable other variable types can be used 

The pointer to the implementation id implementation id pointer hereinafter referred to as pImplId can be specified as either an or a or NULL. If pImplId is specified as NULL then the of the default implementation defined in the registry database Defaultimpl attribute is used instead. This default implementation is searched according to the search rules associated with the registry database such as for example the first client s caller s profile and then the system wide profile for the interface ids.

The interface realization in this example involves only a single implementation with no inheritance and is further described in . In a calling application caller uses the PIF to realize an implementation plugin A . The dashed lines in the Figure indicate the invocation sequence and the handles returned to various components during the realization of an interface. The solid lines in indicate the relationships among the data structures involved in interface realization. The caller issues a request to the PIF to realize an interface. The PIF uses this request information and the information stored in the registry to send an instantiate request to a plugin A . The PIF uses the information stored within the plugins Vtbl private data store and per instance data structure to create a proxy Vtbl . A pointer to the proxy Vtbl is then returned to the caller. The caller uses this pointer to thereafter communicate with the interface and the implementation. Each of these processes is described in further detail below.

As shown in the handle returned ip is a pointer to a data structure in memory called a Proxy Virtual Function Table Proxy Vtbl . In one embodiment the Virtual Function Table Vtbl is a C struct of function pointers pointing to the actual functions comprising the implementation for the interface being realized. Every plugin is required to maintain e.g. allocating a memory block and populating it its own Vtbl. Plugins are also responsible for managing per instance private data and plugin wide struct  e pif plugin info data structure. The PIF is responsible for presenting to a client a realized interface as a C struct of which the members are pointers to functions implementing the function signatures which the interface specifies.

As part of interface realization process the PIF loads the container or DLL containing the target plugin for backing the interface and then invokes function of the plugin if it is available and registered. Otherwise it invokes a DLL wide  ec pif instantiate function to instantiate an instance of the plugin. Both  ec pif instantiate and functions have the same function signature. Given a pointer to an and a pointer to an they instantiate a plugin and return three handles the address of the plugin s Vtbl the address of the plugin instance specific private data and the address of the plugin s  e pif plugin info structure.

The e pif plugin info structure contains information relevant to the implementation of the interface. In particular an EF PIF SINGLETON flag indicates to the PIF that the implementation is a singleton . When a singleton implementation is instantiated new calls to instantiate the implementation result in a reference to the first plugin instance. The PIF may use this singleton indication to optimize reference handling for other  e pif realize calls to this implementation since the PIF is not required to call the  ec pif instantiate function . If a particular implementation turns off this indication then the PIF will always call the  ec pif instantiate function every time the client realizes the implementation. Realization of a non singleton plugin always results in a new plugin instance.

The term Interface Lifetime Control is used herein to refer to the mechanism and the set of rules which are used to determine when to unload the container or DLL which contains the implementations of the interfaces that are currently in use. One of the goals of the invention is to make the caller or client immune to replacement of an interface s current implementation by another implementation. To the client a component is the interfaces it supports. In most cases the client does not know anything about the actual implementation of the interface provided by the component. Thus the client can not directly control the lifetime of a DLL since different parts of a program may refer to different interfaces and or multiple instantiations of the same interface supported by the DLL. In practice a client will not want to unload the DLL when it is finished with one interface but still using another interface. Determining when to release a DLL gets increasingly complicated with an increase in the complexity of the client application program. The PIF can be used to manage this lifecycle.

To accomplish this the PIF provides two functions namely  e pif dupref and  e pif release which can be invoked by PIF s clients for plugin lifetime control purposes. The PIF maintains a reference count for each plugin instance. When a client gets an interface pointer the corresponding reference count is incremented by calling the  e pif dupref function of the interface. When the client is finished using an interface the reference count is decremented by calling the  e pif release function of the interface. When all the reference counts of all the interfaces supported by a DLL falls to 0 the DLL is unloaded from memory.

In addition to these two functions provided by the PIF plugins may provide an implementation of the  ec pif destroy function. The PIF invokes this function when the reference count for a plugin falls to 0. Effective use of a reference counting scheme imposes some rules on the parties involved which are as follows 

Every implementation of an interface should provide the  ec pif copy function in support of the PIF s e pif dupref function. In one embodiment when the  e pif dupref function is called with a EF PIF DEEP COPY flag and the plugin is not a singleton the PIF calls the plugin s ec pif copy function to obtain a copy of the private data of the plugin instance. Then the PIF creates a new instance of the implementation.

Each plugin container DLL also provides a  ec pif instantiate for instantiating a plugin which the container contains. This function is invoked by the PIF during realization of an interface if the selected plugin does not provide its own function and does not set the value of its registry attribute EntryFunc to the name of its function.

When calling member functions the caller must include the interface pointer to the plugin instance which is returned from the corresponding  epif realize function as the first parameter. In accordance with an embodiment of the invention every plugin of a defined interface is required to obey the following rules 

The PIF allows one interface implementation to inherit the implementation of a subset of interface methods or functions from another interface implementation within the same interface. This inheritance relationship between any two interface implementations of the same interface is specified with an InheritsFrom attribute. The InheritsFrom attribute is an attribute of the plugin which is inheriting and the value of this attribute identifies the interface implementation inherited from. This attribute takes an as its value.

The PIF may support single or multiple inheritance. With single inheritance the implementation that is inherited from may in turn inherit from another interface implementation by setting its InheritsFrom attribute to the of the plugin it is inheriting from.

The memory layout of the interface realization through implementation inheritance is described in . As shown in dashed lines indicate the invocation sequence and the handles returned to various components during the realization of an interface solid lines indicate the relationships among the data structures involved in interface realization. As before a calling client issues a request to the PIF to realize an interface. The PIF uses the information in the request and in the registry to send an instantiate request to plugin A . Information from plugin A s vtable private data store and per instance data structure is used to populate part of the proxy vtable . This allows plugin A to fulfill a subset of the interface functions. The remaining interface functions are provided by a derived plugin B . Derived plugin B provides information from its Vtbl private data store and per instance data structure to populate the remaining functions in the proxy Vtbl. The caller then uses a pointer as before to communicate with the interface and the backing implementation via the proxy vtable. The following rules apply to the interface realization process 

All of the plugins involved in the implementation inheritance or in the inheritance sequence should have a major version number that is equal to that of the interface being realized.

At least one of the plugins involved in the implementation inheritance should have a minor version number that is equal to or higher than that of the interface being realized.

The minor version number of the derived plugin the final output of implementation inheritance process is that of the plugin with the highest minor version number among all the plugins involved in the implementation inheritance process.

If any of the above rules are violated during the inheritance process then the interface realization process may fail and an EE PIF VERSION MISMATCH error value returned to the caller of  e pif realize .

The specific rules described above are give for purposes of illustrating a specific embodiment of the invention and to demonstrate the flexibility of the PIF system. These rules need not be implemented in whole or in part in order to operate the invention and other rules may be substituted for those described above while remaining within the spirit and scope of the invention.

The PIF may also support interface inheritance the process of which operates similarly to that shown for plugin inheritance.

Interceptors provide a flexible means of adding services to a system. They allow the binding between the client and the target objects to be extended and specialized to reflect the mutual requirements of both. Interceptors can be logically thought of as being interposed in the invocation and response code paths between the client application making a request and the implementation of the object on which the request is made. As such interceptors are the functions or methods of the configured interface implementations or plugins which provide the services being interposed.

In one embodiment of the invention the engine supports two types of interceptors Fanout type interceptors and Stack type interceptors. Interceptors are specified with a pair of attributes namely InterceptionType and InterceptionSeq. These attributes are associated with an interface implementation . The InterceptionType attribute specifies the type of interception either Fanout or STACK while the InterceptionSeq attribute defines an interception sequence.

An InterceptionSeq attribute specifies the intercepting plugins and their interception order. In one embodiment its value is a comma separated ordered set of s describing the order of the plugins whose methods are invoked in the order specified when the functions of the corresponding interface are called. Wherever a verb of the interface is referred to in a code path the corresponding functions of the interface implementations specified in the data field of InterceptionSeq value are invoked in the order specified.

Fanout type interception is illustrated in . As depicted in Fanout type interception can be implemented totally independently from the PIF. The PIF does not need to be aware of its existence and as far as the PIF is concerned the interception sequence is no more than a group of plugins comprising the interception sequence specified with the InterceptionSeq attribute. In this approach however the Fanout plugin needs to know how to access the registry to get the value of the corresponding InterceptionSeq attribute. This can be accomplished by exposing the registry application programming interface API or by using the PIF s help to support access by the Fanout type interceptors.

In one embodiment the PIF may provide the necessary support with  ec pif instantiate and  epif interception seq functions. Referring again to in this model of interception the calling client or caller invokes the methods of plugin A but is not aware of the intercepting plugins . During the instantiation of plugin A the intercepting plugins as specified by the InterceptionSeq attribute of plugin A are also instantiated by the PIF and the sequence of ordered addresses of these instances of the intercepting plugins is passed to plugin A via  ec pif instantiate . Subsequent method invocations by the client or interface caller results in invocation of the corresponding methods of intercepting plugins in the order specified by the InterceptionSeq attribute.

Given that client invokes method X of plugin A denoted as in method X of plugin A invokes method Xs of the intercepting plugins in the Fanout order specified by the InterceptionSeq attribute of plugin A as follows 

The sequenced method invocation stops with the first method returning failure condition and the status returned to the client.

All of the plugins involved in the interception implement the same interface i.e. their corresponding methods have the same signatures.

No intercepting plugin in a Fanout type interception sequence is allowed to be a Fanout type plugin or a stack type plugin.

The specific rules described above are give for purposes of illustrating a specific embodiment of the invention and to demonstrate the flexibility of the PIF system. These rules need not be implemented in whole or in part in order to operate the invention and other rules may be substituted for those described above while remaining within the spirit and scope of the invention.

Stack type interception is illustrated in . In the Stack type interception model shown in the client invokes the methods of plugin A but is not aware of the intercepting plugins . The PIF is responsible for loading and instantiating the intercepting plugins as specified by the relevant InterceptionSeq attribute in addition to plugin A during interface realization and for building and maintaining the interception sequence.

Subsequent invocations of methods of plugin A by the client interface caller result in invocations of the corresponding methods of intercepting plugins in the order specified by the InterceptionSeq attribute. During the realization of an interface involving stack type interception sequence the PIF passes the interface pointer to the next plugin in the interception sequence via function of each plugin in the sequence.

Given that client invokes method X of plugin A shown as in method Xs of the intercepting plugins are invoked in the order specified by the InterceptionSeq attribute of plugin A as follows 

As with the Fanout type interceptors with Stack interceptors all of the plugins involved in the interception implement the same interface i.e. their corresponding methods have the same signatures.

Sequenced method invocation stops with the first method returning failure condition and this status returned to the client.

All the plugins involved in a stack type interception sequence are required to be stack type plugins except that the last intercepting plugin in the sequence is allowed to be a non intercepting neither Fanout type nor Stack type plugin.

The specific rules described above are give for purposes of illustrating a specific embodiment of the invention and to demonstrate the flexibility of the PIF system. These rules need not be implemented in whole or in part in order to operate the invention and other rules may be substituted for those described above while remaining within the spirit and scope of the invention.

In one embodiment of the invention the PIF can serialize calls to a particular implementation s  ec pif instantiate  ec pif copy and  ec pif destroy function and make use of separate processing threads. This can contribute greatly to the overall performance of the system.

The following section illustrates various functions that are used with the PIF system to register implementations and to realize interfaces. It will be evident to one skilled in the art that additional or alternative functions can be used within the spirit and scope of the invention.

The  e dl load function maps the specified executable module into the address space of the calling process.

The  e dl unload function unloads the specified library from the address space of the calling process. After this call the specified handle is no longer valid wherein 

The  e dl getfuncaddr function returns the address of the specified exported dynamic link library DLL function 

The  e dl geffuncaddr function returns the address of the specified exported dynamically loadable library DLL function in pfa wherein 

The  e dl addref increments the reference count of the DLL specified by dllhandle. It should be called for every new copy of a pointer to an instant of a plugin wherein 

The  ec pif instantiate function is a container wide default plugin instance instantiate function invoked by the Plugin Framework PIF during the realization of an interface i.e. as a result of a client invoking  e pif realize . It is implemented by a plugin implementer and is invoked only if plugin specific instantiate function is not available. If a plugin specific function is provided then this function is invoked rather than the DLL wide  ec pif instantiate function. The plugin specific function has the same function signature as that of  ec pif instantiate function wherein 

The  ec pif instantiate function given a pointer to an version of the interface and a pointer to an instantiates a plugin implementing the interface being realized and returns a set of handles about the plugin and the instance of the plugin being instantiated in a memory block pointed to by pI. The version specifies the version of the interface whose is pointed to by pIId.

The pInterceptionData points to a in core data structure of data type struct e pif interception data defined as follows 

The pointer pI points to a memory block of data type struct e pif instance handles defined as follows 

In the pInterceptionData structure the pVtbl contains the address of the Vtbl of the plugin being instantiated. The pPrivData contains the address of the private data of the instance of the plugin being created. pPluginInfo contains the address of the memory block of type struct  e pif plugin info containing plugin information specific to the plugin being instantiated. It is the responsibility of the plugin to populate the fields of this structure. The struct  epif plugin info is declared as follows 

The  e pif plugin info structure contains information relevant to the implementation of the interface. The m flags field defines flags set by the implementation and interpreted by the PIF. In one embodiment of the invention the following flags are defined 

EF PIF CONCURRENCYAWARE signal that the implementation whether it is a derived implementation or a head of a Fanout or STACK type interception sequence is concurrency aware

The EF PIF SINGLETON flag is a hint to the Plugin Framework to indicate whether the implementation is a singleton. When a singleton implementation is instantiated new calls to instantiate the implementation result in a reference to the first plugin instance. The PIF can use this hint to optimize reference handling for other  e pif realize calls to this implementation in that the Plugin Framework is not required to call the  ec pif instantiate function .

The flags specified by m flags field are not mutually exclusive. EF PIF QUERY is one example of such a flag. When it is set  ec pif instantiate populates pVtbl and pPluginInfo fields of struct  e pif instance handles pointed to by pI without instantiating the plugin.

The  e pif realize function realizes an interface specified by pIId and version by instantiating the interface implementation specified by pImplId. The client of an interface should have a pointer to newly created instantiation of a plugin backing the interface before it invokes any function of the interface. It acquires this handle for the interface by invoking the  e pif realize function.

If pImplId is specified as NULL then the default implementation DefaultImpl for the interface is loaded to back the interface. If no default implementation for the interface is set then a registered implementation with the equal major version number to that of the interface being realized and the highest minor version number is loaded to back the interface subject to the version control rules specified below 

The major version number of the target plugin should match the major version number of the interface. Otherwise the interface being realized and the target implementation are not compatible.

The minor version number of the target plugin should be equal to or higher than that of the interface being realized. Otherwise the interface and the target implementation may not be compatible.

If the target implementation is inheriting from other plugins all of the plugins in the inheritance sequence should have a major version number equal to that of the interface being realized.

If the target implementation is inheriting from other plugins at least one of the plugins in the inheritance sequence should have a minor version number that is equal to or higher than that of the interface being realized.

If pImplId is specified and EF PIF EXACT MATCH flag is set then the plugin specified by pImplId is loaded subject to version control rules as specified above. If it is not registered i.e. not found then this function fails and returns an EE PIF NOT REGISTERED error value is returned.

If pImplId is specified but not registered or found and the EF PIF EXACT MATCH flag is not set then the system attempts to locate the default implementation for the interface. If the default implementation is not compatible or not found then the system will attempt to locate a compatible implementation with the highest minor version equal to or greater than the value specified in the version argument. If a compatible implementation does not exist then the function fails returning an EE PIF NOT REGISTERED error. The specified plugin is then located according to the search rules associated with the registry such as for example first the client s caller s profile and then the system wide profile for the interface ids.

The data point to data passed to the plugin from the caller and datalen specifies the length of the buffer pointed to by data.

The  e pif dupref function increments the reference count associated with a loaded plugin instance or duplicates a plugin instance 

The  e pif dupref increments the reference count of the plugin instance pointed to by pI and duplicates the address of the plugin instance into ppdup. It should be called for every new copy of a pointer to an instant of a plugin.

The flag may include EF PIF DEEP COPY which if specified causes the Plugin Framework to create a duplicate copy of the instance specified by pI and return an interface pointer to the duplicate copy into ppdup. The duplicate instance has its own memory block for its private data if such exists life control and unique interface pointer.

The  e pif release decrements the reference count of the plugin instance pointed to by interface pointer pI. If the reference count of the specified plugin instance falls to 0 then the plugin instance is destroyed.

The  e pif is compatible function checks if a specified interface version is supported by a plugin instance 

The  e pif iscompatible checks to see if the plugin instance specified by pI is compatible with the interface version specified by version.

The  e pif interception seq function returns an ordered sequence of addresses of the instances of the plugins in the interception sequence 

There may be only one plugin in the sequence Regardless the  e pif interception seq returns the addresses of the instances of the intercepting plugins in the calling sequence relative to the plugin instance specified by pI into an in core data structure of data type struct  e pif interception data pointed to by ppInterceptionData.

If the caller is a fan out type plugin then n ordered sequence of the addresses of the Fanout intercepting plugin instances which make up the interception sequence for the Fanout plugin is returned into an array fanout interception seq. The fanout interception seq len variable specifies the number of addresses in this array.

In the case of stack type intercepting plugins the address of the next plugin instance in the calling sequence is returned into next ip. If the plugin instance specified by pI is the last plugin instance in the interception sequence then a NULL is returned in next ip.

The  e pif this returns the address of the private data area of the plugin instance specified by pI. The pVtbl handle points to the plugin specific Vtbl. This is the same Vtbl whose address is returned from function during the creation of the instance of the plugin.

The  e pif getinfo gets information about a plugin instance specified by pI. This information is returned into the  e pif plugin info public structure pointed to by pInfo 

The m flags field defines flags set by the implementation and interpreted by the PIF and include EF PIF SINGLETON EF PIF STACK EF PIF FANOUT and EF PIF CONCURRENCYAWARE all of which are described in further detail above. Concurrency awareness always imply composite behavior if the plugin is a derived plugin or a head of an interception sequence then this means that all of the plugins involved in the composition are concurrency aware and that if one of the components does not support concurrency then the composition is not concurrency aware. Consequently in this case the concurrency aware flag is not returned.

The flags argument specifies optional flags for example the EF PIF DETAILEDINFO flag. If it is specified  e pif getinfo returns detailed information about the plugin specified. If the plugin specified is a derived implementation then the information about all the implementations involving in the derivation of the plugin are returned starting from the most derived implementation. If the plugin specified is the head of a Fanout type or STACK type interception sequence then the information about all the plugins involved in the interception sequence is returned starting from the plugin specified head of interception sequence followed by the intercepting plugins left to right in case of Fanout type and top down in case of STACK type.

The  ec pif destroy releases the plugin instance specific system resources specified by pIhandles. The pIhandles points to a memory block of data type struct  e pif instance handles defined as follows 

The pInterceptionData points to an in core data structure of data type struct epif interception data defined above while the pIhandles points to a memory block of data type struct  e pif instance handles also defined above .

The pVtbl is a pointer containing the address of the Vtbl of the plugin instance whose private data are being duplicated. pPrivData is a pointer containing the address of the plugin instance private data. If no private data are used by the plugin instance then NULL is returned. The ppluginInfo pointer contains the address of the memory block of type struct  e pif plugin info containing plugin instance specific information which is declared as follows 

The  e pif plugin info structure contains information relevant to the implementation of the interface. The m flags field defines flags set by the implementation and interpreted by the PIF. Flags may include EF PIF SINGLETON EF PIF STACK EF PIF FANOUT and EF PIF CONCURRENCYAWARE all of which are described in further detail above.

The epifreg function can take a variety of options as indicated above wherein the options have the following meaning 

The epifunreg command unregisters the specified plugin. The p option specifies the implementation identifier of the plugin to be unregistered. If this option is used alone then the plugin s data stored in the Plugin Framework is unregistered including the data stored in all of the existing profiles . The o option can be optionally used to specify that the information about the plugin should be removed from the specified profileId. This command does not remove the data about the related plugin s interface which can be removed with the epifregedt command.

The epifregedt function edits the attributes of implementations interfaces and profiles stored in the Plugin Framework registry 

The Plugin Framework searches the specified profile in the registry for the specified interface and or implementation object data. The or can be specified as to indicate that the edit operation applies to all existing profiles or interface implementation ids respectively. SYSTEM is the for the default system wide profile.

The a option is used to specify the attributes involved in the editing operation on the specified object. The AttrName is the name of an attribute of the edited object and AttrValue is the value assigned to this attribute. Some attributes can be used to narrow the scope of the particular editing operation such as a set create or delete .

This section provides a sample code illustration demonstrating how to construct a PIF compliant client application and a corresponding plugin. The following files are shown merely for demonstration purposes to better illustrate the invention. It will be evident to one skilled in the art that the procedures used may be extended to apply to more complex situations and applications and that the invention is not limited to the C language examples give below.

The plugin can be defined in a metalanguage format using a plugin wizard or similar tool. The metalanguage defines the plugin operations and also such variables as the plugin name the interface name and the interface version number.

The following plugin description file dummy.pi is an example of a description file used to define a plugin. The plugin description may in some embodiments be created by a plugin wizard or plugin design tool. At a minimum it should contain a plugin name in this case dummy an interface name sec and an interface version number 1.2 . The plugin should also contain a number of operations in this example denoted as op op op and op . The operations define the functions the plugin will actually provide to the calling application.

The dummy.h file below is an example of a generated include or header file which is output by the plugin wizard. The header file must be included at compile time into each plugin implementation and client application. The include file provides a specification of the particular interface in which the plugin operates.

In this example the include file includes a name dummy and a data structure definition that defines the data structure for the particular interface and version number in this case sec. 1.2 . The data structure includes pointers for all of the operations supported by this particular interface and version number.

The dummy.c file below is an example of the generated skeleton template and represents the actual plugin application. The only modifications from the generated .h file is the replacement of the generated comments in each of the operation implementations with actual code and the addition of private data members to the Private data structure. The c file when compiled is used to provide the actual plugin implementation. Certain verbs such as pif destroy and pif copy are required in order for the interface to handshake successfully with a calling application. Other verbs op op op op provide the functional operations of the plugin framework.

The test.c file shown below is an example of a client application that loads and invokes operations on the plugin. The client application is written so as to call the required interface definitions specified in dummy.h . The client application must successfully realize the desired interface sec with the specified plugin. Thereafter it uses a pointer pin to refer to an implementation vtable Vtbl . The operations themselves are called through a series of put commands.

The client does not need to specify an actual implementation although it does in this example . When an implementation is not specified the client is given the default implementation for that interface.

In this section an example of a design for the function by function realization of an interface process supporting both a implementation inheritance and b no implementation inheritance cases is presented. The example design supports interface inheritance even though it may not be a requirement for all embodiments of the engine. The key aspects of this particular design are as follows 

The client is presented a realized interface as a C struct of which the member variables are the pointers to functions of an implementation that are implementing the function signatures of the interface regardless of whether the implementation backing the interface is a single implementation or a derived implementation. The client is not aware of whether the realized interface is an original interface or a composite or inherited interface and instead sees it as a single interface.

The interface method invocations pass an interface pointer to the plugin instance as the first argument.

The implementation methods may access per instance private data by invoking an  e pif this function provided by the PIF.

The realization and implementation process of this particular design embodiment is shown in . As shown in the process includes a realization phase interceptor phase load and unload phases and a rehears phase. These are discussed in further detail below.

The e pif realize function calls pif init to initialize a mutual exclusion lock routine mutex . A mutex is an abstract structure that enforces a policy of mutual exclusion. Traditionally only one process thread at a time may hold a particular mutex and threads trying to lock a held mutex will block until the mutex is unlocked. Mutexes must be exited in the opposite order in which they were entered and that they cannot be reentered before exiting.

If the registry plugin is not already realized then the process will attempt to realize it. This instance of the registry plugin can be cached for performance benefits. The count of active plugin s is incremented to reflect the new plugin and the mutex is then unlocked.

Since the process does not know when the framework will no longer be needed it keeps track of how many plugin instances are active at any given time. Whenever this count drops to zero the cached registry plugin is released. The use of cache for optimization is only useful when there will be at least one active plugin instance when other plugins are being realized. If the design model is such that only one plugin is ever active at a time then the registry plugin will be realized and released each time. A side effect of caching the registry plugin is that the underlying registry being used does not see registry changes until the registry is closed and re opened.

The process then calls the realize frontend function . If this is not successful then the mutex is locked the active plugin count is decremented. If the active count goes to zero then the registry plugin is released and the mutex unlocked.

The process continues with a realize frontend function which as a first step constructs a PIF RARGS stack using supplied arguments and calls realize internal . If realize internal finds a singleton plugin value then the corresponding singleton is returned. If realize internal finds a stack interceptor then the handle or pointer of the first plugin in the stack is returned.

If realize internal returns anything else but SUCCESS then an error is returned. If none of the above criteria are met the plugin is constructed from its components. The realize frontend function loops through each implementation and verifies the major version number while at the same time looking for both the highest minor version number and the largest Vtbl size.

A verification step ensures that the highest minor version number is greater than or equal to that requested. The size block of memory required is computed and allocated. One block of memory is allocated for the variable sized PIF CONTROL block the Proxy Vtbl the fan out interceptor array and the array of info public pointers.

The PIF CONTROL block is filled in as is the Proxy Vtbl by looping through each implementation s Vtbl and filling in empty entries in the Proxy Vtbl with non nil entries from the Vtbls.

The the filled in Proxy Vtbl is checked for empty entries and if any are found a NORESOURCE error is returned.

One of the additional arguments is an array of the PIF PINFO data structure that is declared as a local. This array is used so all the implementations making up the complete plugin can be instantiated first so that the realization process knows how big a chunk of dynamic memory to allocate. This is dependent on both the depth of implementation inheritance and on the size of the largest Vtbl within all the implementations that make up the complete plugin. Because this array is allocated before the process knows the actual depth of implementation inheritance the framework may impose an implementation restriction on the maximum depth of implementation inheritance allowed. If during the realization process this limit is reached the process will fail and an returned.

If no implementation identifier is specified then the first read of the registry is to call Getintf using the specified interface identifier and major version number of the interface. If the DefaultImpl attribute is non null then it is used as the implementation identifier.

If no implementation identifier is specified and the DefaultImpl attribute mentioned above is nil then the HighestMinorImpl attribute is looked at.

If an implementation identifier is specified or one is determined from the above steps the next step is to see if the identifier is a selector or alias by calling GetAlias . If no match is found then the implementation identifier is not an alias. If a match is found then what is now known to be an alias is used as an attribute name and it s value is read from the registry. The value of this attribute is then used as the implementation identifier but is first checked recursively to see if the alias mapped to another alias.

Using the interface identifier argument and the resultant implementation identifier a list of singleton plugins that have already been realized and have not yet been released is checked for one whose most derived implementation s info structure has the appropriate m interface id and m impl id fields. If a match is found then  pe pf dupref is called on the matching plugin and the new pointer is returned. The search for an existing matching singleton is not done when the implementation being instantiated as a base implementation.

Using the resultant implementation identifier GetImpl is called. If the implementation does not exist an error is returned unless the identifier used is the one originally specified by the caller in which case the process starts at the top as if the caller had not specified an implementation identifier.

The realize internal next checks the InterceptionType attribute. If this attribute indicates anything other than NoInterceptor then it calls an internal routine that handles the realization of an interceptor. This step is skipped if the implementation being realized is one that was specified in a stack Interception Sequence.

The  e dl geffuncaddr function is called using either the EntryFunc attribute or the default  ep dl instantiate . The plugin s  ep dl instantiate function is then called.

The appropriate info public structure m pinfo in the PIF PINFO struct is initialized from the corresponding implementations private info structure.  e dl unload 

The value of the ImagePath attribute is passed to  gp dl load. Then the value of the EntryFunc attribute is passed to  gp dl geffuncaddr to get the address of the plugin s instantiation routine. The instantiation routine is called with the appropriate arguments that come from those passed in to  pe pf realize and internally generated.

The realize internal checks the InheritsFrom attribute. If this attribute exists then it calls realize internal recursively with the value of the said attribute The implementation identifier specified in the InheritsFrom attribute when realized by the framework is realized as if the EF PF EXACT MATCH flag was specified.

Once control is returned to  pe pf realize from realize internal then the size of the Proxy Vtbl needed is determined and the depth of inheritance is known.

At this time the system can now check to make sure that there exists at least one implementation making up the complete plugin that implements at least the minimum minor version number requested by the caller. This check is made by looking at each implementation s  e pf plugin info data structure. If this check fails then a version mismatch error is returned.

A PIF CONTROL data structure can now be allocated. The stack local array of PIF PINFO data structures is copied to the m pi field.

The Proxy Vtbl is now also filled in. Starting with the most derived implementation and ending with the least derived implementation the following is done. For every non nil entry in the implementations static Vtbl for which there is a nil pointer at the same offset in the Proxy Vtbl the pointer from the implementations static Vtbl is copied to the Proxy Vtbl.

The Proxy Vtbl is checked to make sure there are no nil pointers. If any are found then everything is released and an error returned.

The m publicinfo field of every member of the m pi field of the PIF CONTROL structure can be initialized by simply copying the corresponding fields from each corresponding implementation s private info structure. The vector of pointers pointed to by the m publicinfo field of the PIF CONTROL structure is initialized to point to the appropriate m publicinfo fields in the array of PIF PINFO structures m pi .

Each implementation s info data structure is checked to see if the m singleton flag is set. If every implementation has this flag set then the PIF SINGLETON flag in the PIF CONTROL structure is set. If this flag is set then the PIF CONTROL structure is linked into a linked list of singleton plugins using the m nextSingleton pointer.

Clients or calling applications callers make calls to realize frontend on each implId in the sequence with rdepth 1 and the EXACT MATCH and IGNORE ISEQ flags.

The returned pointer ip is stored in the PIF RARGS structure. If it is a Fan out interception type then fanoutLen PIF RARGS is set to the sequence length. For both interception types the implementation identifiers specified in the InterceptionSeq attribute when realized by the framework are realized as if the EF PF EXACT MATCH flag was specified.

For a FAN OUT type of interceptor the realize internal function is called N times with the same arguments as the original call to  pe pf realize except for the implementation identifier argument which is replaced with the corresponding one from the sequence. N is the number of implementation identifiers in the sequence. The realize internal function is then called again this time with a sequence of pointers to the realized intercepting plugins.

For a STACK type of interceptor the realize internal function is also called N times with the same arguments as the original call to  pe pf realize. This time the sequence of implementation identifiers is traversed backwards. Additionally on each call to realize internal except the first a single pointer to the last intercepting plugin realized is passed. If the ImagePath registry attribute exists on the registry key that defined the interceptor sequence the key is treated as if it were the first plugin in the stacked interception sequence.

In the non deep copy case the reference count stored in the PIF CONTROL data structure is simply incremented and the same pointer returned.

If the PIF STACKI flag is set then  pe pf dupref is called on the next plugin in the stack. The new pointer returned is saved in the m interceptors field of the new PIF CONTROL data structure allocated. The recursion is done first because the pointer to the next plugin in the new stack is needed before any of the copy routines for any of the implementations for the current plugin are called.

If the PIF FANOUTI flag is set then  e pf dupref is called on each of the plugins in the fan out interception sequence and the returned pointers stored in the corresponding fields of the new PIF CONTROL data structure. This recursion is done first because the new sequence is needed before any of the copy routines for any of the implementations for the current plugin are called.

The new PIF CONTROL data structure is populated from the original PIF CONTROL data structure and the reference count of the new PIF CONTROL set to 1. Using the new PIF CONTROL data structure the plugin s copy routine pointed to by its  e pf plugin info data structure is called. In the case of implementation inheritance each plugin in the inheritance list has it s copy routine called.

The reference count in the PIF CONTROL data structure is decremented and if the count after being decremented is greater than zero 0 then it simply returns.

The first thing that is done when the reference count goes to 0 is to call the plugin s destroy routine so it can release any of it s resources. In the case of implementation inheritance the destroy routine of the most derived implementations are called first.

If the plugin being released is part of a stacked interceptor chain then  pe pf release is called recursively on the next plugin in the chain.

If the plugin being released is a fan out plugin then each of the corresponding intercepting plugin s is released.

If the PIF SINGLETON flag is set in the PIF CONTROL data structure then the linked list of realized singleton plugin s is checked to see if this plugin is on that list and if so it is removed from that list.

If a release flag is set then the  e pif release function is called on the next stack interceptor if any and on the sequence of fan out intercepting plugins.

The process then simply indexes through the array of PIF PINFO s in the PIF CONTROL looking for one whose pVtbl instance handle matches the passed in key. If a match is found return the corresponding pPrivData pointer is returned.

It will be evident to one skilled in the art that while some functions and routines described herein were specified as having certain characteristics features and constraints on conforming to certain rules that these rules need not be adhered to in full or in part in order to operate the invention and that the examples given are for the purposes of illustrating an embodiment of the invention.

The foregoing description of preferred embodiments of the present invention has been provided for the purposes of illustration and description. It is not intended to be exhaustive or to limit the invention to the precise forms disclosed. Obviously many modifications and variations will be apparent to the practitioner skilled in the art. The embodiments were chosen and described in order to best explain the principles of the invention and its practical application thereby enabling others skilled in the art to understand the invention for various embodiments and with various modifications that are suited to the particular use contemplated. It is intended that the scope of the invention be defined by the following claims and their equivalence.

