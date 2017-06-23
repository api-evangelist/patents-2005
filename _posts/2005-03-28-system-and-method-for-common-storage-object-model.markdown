---

title: System and method for common storage object model
abstract: A system and method for common storage object model is provided. In one aspect, one or more classes representing respective one or more storage devices are provided. One or more plugin modules are operable to discover and provision one or more storage devices connected to a storage network using the one or more classes. A wrapper module is operable to handle selecting and loading of the one or more plugin modules.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07801931&OS=07801931&RS=07801931
owner: Computer Associates Think, Inc.
number: 07801931
owner_city: Islandia
owner_country: US
publication_date: 20050328
---
This application is a Continuation of U.S. Ser. No. 10 889 715 filed on Jul. 12 2004 now abandoned and claims the benefit of U.S. Provisional Application No. 60 486 509 entitled COMMON STORAGE OBJECT MODEL filed on Jul. 11 2003 the entire disclosure of which is incorporated herein by reference.

A frequently occurring task for many providers of computer services is adding support of a new device into an existing application. Most of the time such a task requires a massive development effort and even redesigning and or rebuilding the whole application. Accordingly a common storage object model is provided.

A system and method for common storage object model is provided. The system in one aspect includes one or more classes representing respective one or more storage devices. One or more plugin modules are operable to discover and provision one or more storage devices connected to a storage network using the one or more classes. A wrapper module is operable to handle selecting and loading of the one or more plugin modules.

The method in one aspect includes providing one or more classes to represent respective one or more storage devices providing one or more plugin modules operable to discover and provision one or more storage devices connected to a storage network using the one or more classes and providing a wrapper module operable to handle selecting and loading of the one or more plugin modules.

Further features as well as the structure and operation of various embodiments are described in detail below with reference to the accompanying drawings. In the drawings like reference numbers indicate identical or functionally similar elements.

CA Common Storage Object Model is an object model that describes both the physical and the logical elements of an enterprise storage environment and relationships among these elements in a hierarchical and or relational object model.

In one embodiment each element is represented as a class which has attributes and methods. The objects and properties in the model are gathered by looking at different vendor APIs and storage device platforms. Thus the model provides a unique vendor independent data representation which permits to query and handle data from different set of devices. The data is represented in a single format making it easy to support more devices and integrate components within company s storage applications.

The design also supports multiple views of the same resources without duplication by associating different classes or entities. For example a volume on a host can be correlated to the device volumes it is constructed of.

With the class hierarchy and the extra property attributes of each class new features or device specific features can be added without altering the application which is using the model. Objects and methods can be easily added as needed by the changing storage environment.

Common storage object model in one embodiment comprises a collection of classes of storage entities. Each storage entity physical logical is represented as a class with attributes and methods. Relationships among the entities are represented as attributes and or references. The common storage object model of the present disclosure may be provided as a C dll data link library module which exports these classes which may be used by plugins and consumers.

For each supported storage device plugins may be written which may use a mechanism available for that device Vendor Specific API s Industry Standards such as CIM SMIS Bluefin etc. to discover and populate the object model for that device. Consumer applications may use the CSM and the plugins to retrieve and consume the storage data extracted from the devices.

In one embodiment plugin functionality is handled by a wrapper library which handles dynamic loading of the libraries therefore no code changes are needed to add a new library device support. Consumer application may use the wrapper to load the appropriate plugins have the object model populated by the plugins and then use the data retrieved according to their needs.

The common storage object model CSM comprises a set of classes that model the physical and logical elements of enterprise storage environment and the relationships among these elements. and illustrate the set of classes. In one embodiment all classes have a common ancestor and each instance of a class has a unique identity. To capture vendor specific properties and behavior it is possible to extend the CSM classes through inheritance. Each class that will be added to CSM in future will be able to work with existing applications because of polymorphic behavior of the classes.

In one embodiment the common ancestor class provides three methods for all the objects Clone Equal and GetExtraProperty . Clone creates an instance of the object and Equal compares the object to another instance to see if they are equal. These two methods can be overwritten in the child classes to function more precisely for instances of each child class. GetExtraProperty makes it possible for consumer applications to handle device specific properties in the plugins without any code changes in the application. This method returns the property name its type and the corresponding value.

Class CABase is the common parent of every other class in the object model. CABase provides a unique object ID an object name and an object state for each instance of the child classes. CABase also provides two methods Clone and Equal . These two methods can be redefined in each child class to function more precisely for instances of that child class.

Class CAObjectContainer is a list template. This list is designed to contain instances of CABase or any child of CABase. CAObjectContainer itself is a subclass of CABase and this makes it possible to have list of lists.

Class CAStorageSubSystem models a storage disk array. This class contains the basic information about a disk array. CAStorageSubSystem provides methods to handle the physical and logical components of a disk array. CAStorageSubSystem contains one or more instances of CAEnclosure one or more instances of CARaidGroup and one or more instances of CALogicalDevices . CAStorageSubSystem is a subclass of CABase .

Class CAEnclosure represents an enclosure inside of a storage subsystem. An enclosure is a gathering of storage processors spindles ports fans and power supplies. CAEnclosure has one or more instances of CASpindle one or more instances of CAStorageProcessor one or more instances of CANPort one or more instances of CAPowerSupply and one or more instances of CAFan . Each instance of CAEnclosure is in association with one instance of CAStorageSubSystem . Class CAEnclosure is a subclass of CABase .

Class CAFan represents a fan in an enclosure. Each instance of CAFan is in association with one instance of CAEnclosure . CAFan is a subclass of CABase .

Class CAPowerSupply represents a power supply in an enclosure. Each instance of CAPowerSupply is in association with one instance of CAEnclosure . CAPowerSupply is a subclass of CABase .

Class CASpindle represents a physical disk spindle in an enclosure. Each instance of CASpindle is in association with one instance of CAEnclosure can be in association with one instance of CARaidGroup and can be in association with one instance of CALogicalDevice . Each instance of CASpindle can have one or more instances of CASpindleExtent . CASpindle is a subclass of CABase .

Class CAPhysicalExtent is an abstract class. It represents a chunk of a bigger entity. This class is a super class for CASpindleExtent and CARaidExtent . CAPhysicalExtent is a subclass of CABase .

Class CASpindleExtent represents a part of CASpindle . An instance of CASpindleExtent is in association with one instance of CASpindle . An instance of CASpindleExtent can be in association with one instance of CALogicalDevice . CASpindleExtent existence depends on CASpindle . CASpindleExtent is a subclass of CAPhysicalExtent .

Class CARaidGroup represents a raid group. An instance of CARaidGroup has one or more instances of CASpindle or one or more instances of CASpindleExtent . Each instance of CARaidGroup is in association with one instance of CAStorageSubSystem . An instance of CARaidGroup can have one or more instances of CARaidExtent . An instance of CARaidGroup can be in association with one or more instances of CALogicalDevice .

Class CARaidExtent represents a part of CARaidGroup . An instance of CARaidExtent is in association with one instance of CARaidGroup . An instance of CARaidExtent can be in association with one instance of CALogicalDevice . CARaidExtent existence depends on CARaidGroup . CARaidExtent is a subclass of CAPhysicalExtent .

Class CALogicalDevice models a logical device that is created out of a raid group or using a spindle a part of a spindle or a part of a raid group. CALogicalDevice represents the logical device inside the disk array. An instance of CALogicalDevice can be in association with one and only one instance of CASpindleExtent CARaidExtent CASpindle or CARaidGroup . Each instance of CALogicalDevice is in association with an instance of CAStorageSubSystem . An instance of CALogicalDevice can be in association with one or many instances of CADeviceLun . CALogicalDevice is a subclass of CABase .

Class CALun is an abstract class. It represents a LUN. Class CALun is used as a super class for CADeviceLun and CAPhysicalVolume . CALun is a subclass of CABase .

Class CADeviceLun represents a LUN on a disk array that is exported and ready to be used by a host. Each instance of CADeviceLun is associated with one instance of CALogicalDevice . Each instance of CADeviceLun is associated with one instance of CANPort . An instance of CADeviceLun can participate in an association with one instance of CALunMask and two instances of CANPort one as Target and one as Initiator . An instance of CADeviceLun can be associated with one instance of CAPhysicalVolume . CADeviceLun is a subclass of CALun .

Class CAPhysicalVolume represents a LUN that is in use by a host and acts as a physical volume on the host. An instance of CAPhysicalVolume is in association with one instance of CADeviceLun . Instances of CAPhysicalVolume can be associated with one or more instances of CAHBAPort . An instance of CAPhysicalVolume is in association with one instance of CAHost . An instance of CAPhysicalVolume can have one or more instances of CAPhysicalPartition . CAPhysicalVolume is a subclass of CALun .

Class CAStorageProcessor represents a storage processor in an enclosure. An instance of CAStorageProcessor can have one instance of CANPort . Each instance of CAStorageProcessor is associated with one instance of CAEnclosure . CAStorageProcessor is a subclass of CABase .

Class CANPort represents a fiber channel port in an enclosure. An instance of CANPort can be associated with one instance of CAStorageProcessor . An instance of CANPort can be associated with one or more instances of CADeviceLun . Each instance of CANPort can participate as a Target or an Initiator in an association with instances of CALunMask and CADeviceLun . Each instance of CANPort is associated with one instance of CAEnclosure . CANPort is the super class of CAHBAPort and subclass of CABase .

Class CAHBAPort models a fiber channel port on a host bus adapter. Each instance of CAHBAPort can be associated with one instance of CAHBA . Instances of CAHBAPort can be associated with one or more instances of CAPhysicalVolume . CAHBAPort is a subclass of CANPort .

Class CAHBA represents a host bus adapter in a host. An instance of CAHBA can have one or more instances of CAHBAPort . CAHBA is a subclass of CABase .

Class CALunMask represents a mask defined for a device LUN. An instance of CALunMask is associated with one instance of CADeviceLun and two instances of CANPort one as Target and one as Initiator . The existence of CALunMask depends on this association. CALunMask is a subclass of CABase .

Class CAHost represents a host. Each instance of CAHost can have one or more instances of CANetworkAddress one or more instances of CAPhysicalVolume or more instances of CALogicalVolume and one or more instances of CAHba . CAHost is a subclass of CABase .

Class CANetworkAddress represents a network address. An instance of CALunMask is associated with one instance of CAHost . CANetworkAddress is a subclass of CABase .

Class CAPhysicalPartition models a part of CAPhysicalVolume . Each instance of CAPhysicalPartition is associated with one instance of CAPhysicalVolume . An instance of CAPhysicalPartition can be associated with one instance of CAPartitionGroup . CAPhysicalPartition is a subclass of CABase .

Class CAPartitionGroup represents a group of CAPhysicalPartitions . Each instance of CAPartitionGroup is associated with one or more instances of CAPhysicalPartition . An instance of CAPartitionGroup can be associated with one instance of CALogicalVolume . CAPartitionGroup is a subclass of CABase .

CALogicalVolume represents a volume on the host that has been created using partitions of a CAPhysicalVolume . Each instance of CALogicalVolume is associated with one instance of CAHost . An instance of CALogicalVolume is associated with one or more instances of CAPartitionGroup . CAPhysicalPartition is a subclass of CABase .

In one embodiment the interface is based on a data collection algorithm which is based on object enumeration using for example the same semantic as objects are enumerated in Windows that is the paradigm of GetFirst and GetNext kind of methods. In this paradigm object enumeration is executed while getting the first object and looping until an EOF is not signaled. This paradigm also implies that objects are enumerated inside the context of their super parent object. Thus Enclosures are enumerated inside the StorageSubSystem object and Disks are enumerated inside Enclosures etc.

Thus for example CAStorageSubSystem object collects the Enclosures the Raid groups and the LUNS. CAstorageSubSystem may include the following functions 

The CEnclosure object is responsible for the collection of fans power supply and disks that belong to it. The CEnclosure may include the following functions 

The CDisk object may include GetRGInfo CRaidGroup pRaidGroup which returns a pointer to the Raid Group this disk belongs to. If this disk is a spare EOF is returned.

The CLUN object is responsible for the collection of the Extents it includes and HostLUN information if available. CLUN object may include the following functions 

The CDiskLUN object may include the functions GetDiskLunInfo GetHostsInfo GetPath to retrieve respective information.

There are more than one way of collecting data using the above methods. For example in the Extents object collect physical extents can be collected from the LUN object First and next Extent in the specific LUN or from the disk object First and next Extent in the specific disk . Those methods may be added as needed.

The CFan Cport CRaidGroup objects are information objects. They may include additional methods as needed.

The following data collection algorithm are used in one embodiment for collecting data from the devices 

In one embodiment each method may return HRESULT. If the method succeeded the returned HRESULT will be NO ERROR . Any other returned HRESULT signals an error. The actual error description may be fetched using the GetError hRes method which returns the context sensitive error description string char of that error.

In one embodiment the above interface may be implemented under a framework with specific DC sub classes. In another embodiment the above interface may be implemented with specific DC classes operating under the same interface and object structures.

Under the Framework setup the proposed classes do not implement raw data collection and the methods are defined as pure virtual functions. As such these classes can be seen as meta classes. Under this framework the data collection method using the algorithm described above is implemented. The actual raw data collection is implemented in subclasses each for a specific disk array object. Each object has its own way of getting the information for instance SYMAPI or HICommand or using CLI and so on.

This way of operation allows easy addition of new devices by simple implementing the necessary virtual functions the actual raw data collection according to the technology of the new device . The data collection itself is entirely generic capable of collection of partial information also in case a certain device does not supply all the necessary information. For instance it is possible that a device does not provide interface about its fans or it does not contain any enclosure etc.

For example class CDisk is a meta class with pure virtual methods. The class CEMDisk is subclass of Cdisk and it has EMC specific knowledge and implementation of each virtual method. Similarly the class CHDSDisk has HDS specific knowledge and implementation of each virtual method.

This implementation mechanism does not forbid specific data collection implementation for example when only a partial data collection is needed for a specific device.

In the embodiment that uses structure implementation the proposed classes are structures defining the attributes each object may have. For each device there is a separate set of implementation of the same classes under the same name in a separate executable DLL implementing the device specific raw data collection logic. In one aspect of this embodiment the data collection itself is implemented for each device separately even if they comply to the generic algorithm described above.

For each supported storage disk array a plugin is written which implements the discovery and provisioning functionalities. Plugins may use whatever mechanism of communication is available for that specific storage device in order to retrieve data and perform provisioning functions. To support a new device associated functionality in the plugin is implemented and the plugin wrapper is configured to know about this plugin. Such change does not require changes in the upper layer applications consumer applications . Some examples of plugins are HiCommand for Hitachi SymAPI for EMC Symmetrix Microsoft VDS on a Windows Server machine which could support any device with a VDS interface such as HP EVA Xiotech EMC Clariion and CIM SMIS Blufin for IBM Shark and LSILogic.

Plugin mechanism enables dynamically loading of new plugins without requiring code changes in the rest of the application. Once a new plugin is completed according to specifications that plugin is made available on the machine and the configuration file of the Plugin Wrapper modified to know about this new plugin.

Each plugin may be using a different mechanism to communicate with the specific storage device. Some plugins may be used for multiple storage devices if those devices support the same interface.

IBM Shark Plugin uses SMI S as the model and mechanism for data retrieval and storage provisioning functionalities. According to SMI S a CIM Provider server manages the storage devices and provides data retrieval and provisioning functionality for that device. All communications between the CIM Provider and CIM Client are encoded in XML and transferred over HTTP or HTTPS. IBM Shark Plugin is a CIM client that connects to IBM CIM providers to retrieve data and perform management operations.

Open source Pegasus libraries are used for the low level CIM functionality. CA CIMTool.dll contains the functionality that encapsulates the required functionality of the Pegasus libraries in a single class called CA CIMConnector. The CIM based plugins such as IBM Shark and LSILogic plugins uses customized versions of the CA CIMConnector by extending this class.

LSILogic Plugin is designed the same way as the IBM Shark plugin. The difference between LSILogic Plugin and IBM Shark Plugin is the way retrieval functions and management functions are implemented. Although both IBM CIM Provider and LSILogic CIM Provider follow SMI S but each provider interprets the specification in its own way and uses different aspects of the specification. These differences are masked for the upper layer applications.

Plugin for Hitachi Disk Arrays uses HiCommand XML Interface that is a Hitachi specific API. HiCommand Server manages Hitachi storage devices and provides discovery and management functionality to client applications via HiCommand XML interface.

EMC Symmetrix plugin uses a vendor specific API called SymAPI. In addition to the API a command line interface SymCLI is also used to implement some of the functionalities that are not available through the API.

Virtual Disk Service VDS is a new service that is part of Microsoft Windows Server 2003. VDS enables multi vendor storage devices to interoperate in Windows. VDS has application programming interfaces APIs to storage hardware and to management programs that manage the storage hardware. For the storage devices that has VDS support such as HP EVA Xiotech and EMC Clariion communication is performed via VDS with the Windows Server managing those devices to discover and manage devices that use VDS APIs.

The Plugin wrapper in one embodiment is designed to handle the plugin loading and selection thus abstracting to the upper level application the specificity of the different libraries. This library exports the same set of functions as the plugins. For example when the user makes a function call it selects the right library loads it if necessary and then calls the matching function in the plugin. A handler containing the information to select the right library is added to each function s set of parameters.

The different functions may include InitialiseStoragePlugIn InitialiseHost GetAllStorageArrays GetAllHosts releaseLibrary. For each object returned the application can call any available method. After calling the releaseLibrary the application calls again the Initialize if it wants to query the object list again. It can call as many Get function as it wants after the first Initialize . How the information is refreshed is a decision of the plugin implementer.

In one embodiment the plugin wrapper is used to provide a single library interface for all the plugins . A new library can be added for instance without changing the upper level application . The plugin exports a set of functions. In this case the exported functions are RegisterLibrary and UnRegister library.

In one embodiment the wrapper is implemented by using a configurable list of plugins where the name of the library to load is specified for each vendor device. It may also use a plain text file having an entry for the library name for each vendor device. Entry in the file may be Vendor ID product ID libraryName. 

In one embodiment an upper level application call may be handled in three different phases. The library name matching that inquiry string is examined. If there is an exact match for example in string length then the method proceeds to phase number two. Otherwise the inquiry string is added into the inquiry list for that library before going to phase number two. If there is no library matching that inquiry string then error code is returned.

In phase two at check is made to determine if the library is loaded. If it is then the method proceeds to the third phase. Otherwise an attempt is made to load the library at . If it loads then the method proceeds to the third phase. Otherwise the call is failed. At this point a call to the corresponding methods in the plugin is made and the plugin s return object is returned to the caller.

In one embodiment this library exports three different methods. HANDLE InitialiseStoragePlugIn String deviceInquiry string String ipAddress String userId String password String namespace for a storage device HANDLE InitializeHost String hostIp string userId String password for a host.

The HANDLE is an opaque data structure. It returns an integer which is the index of the library in the list of library.

The system and method of the present disclosure may be implemented and run on a general purpose computer. The embodiments described above are illustrative examples and it should not be construed that the present invention is limited to these particular embodiments. Thus various changes and modifications may be effected by one skilled in the art without departing from the spirit or scope of the invention as defined in the appended claims.

