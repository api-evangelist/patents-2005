---

title: API for network discovery
abstract: Discovery of a network to which a device is in communication and classifying the network is disclosed. The network may be classified as a network already known or a new network signature may be created where the network signature is made up of a network id, a link id and a hop id.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07590762&OS=07590762&RS=07590762
owner: Microsoft Corporation
number: 07590762
owner_city: Redmond
owner_country: US
publication_date: 20051207
---
Historically operating systems have communicated network status and associated system settings with the network adapters in the computer. For example the system would report that Local Area Connection 1 or Wireless Connection 1 is connected and firewall settings could be set per adapter. Network adapter types are a complicated concept and require users to understand networking concepts in order to understand status. In addition as the number of network adapter types increases it becomes increasingly likely that a computer will connect to the same network over multiple adapters. Moreover a network adapter is likely to be used to connect to multiple networks and system settings that are appropriate from one network may not be correct for another network. Typical users care about what they are connected to not how they are connected and many system settings should be based upon the network to which the computer is connected not how they are connected.

Discovery of a network to which a device is in communication and classifying the network is disclosed. The network may be classified as a network already known or a new network signature may be created where the network signature is made up of a network id a link id and a hop id. The discovery may use APIs created to assist the network discovery process. User interfaces to assist users with network connections also are described.

Although the following text sets forth a detailed description of numerous different embodiments it should be understood that the legal scope of the description is defined by the words of the claims set forth at the end of this patent. The detailed description is to be construed as exemplary only and does not describe every possible embodiment since describing every possible embodiment would be impractical if not impossible. Numerous alternative embodiments could be implemented using either current technology or technology developed after the filing date of this patent which would still fall within the scope of the claims.

It should also be understood that unless a term is expressly defined in this patent using the sentence As used herein the term        is hereby defined to mean . . . or a similar sentence there is no intent to limit the meaning of that term either expressly or by implication beyond its plain or ordinary meaning and such term should not be interpreted to be limited in scope based on any statement made in any section of this patent other than the language of the claims . To the extent that any term recited in the claims at the end of this patent is referred to in this patent in a manner consistent with a single meaning that is done for sake of clarity only so as to not confuse the reader and it is not intended that such claim term by limited by implication or otherwise to that single meaning. Finally unless a claim element is defined by reciting the word means and a function without the recital of any structure it is not intended that the scope of any claim element be interpreted based on the application of 35 U.S.C. 112 sixth paragraph.

The steps of the claimed method and apparatus are operational with numerous other general purpose or special purpose computing system environments or configurations. Examples of well known computing systems environments and or configurations that may be suitable for use with the methods or apparatus of the claims include but are not limited to personal computers server computers hand held or laptop devices multiprocessor systems microprocessor based systems set top boxes programmable consumer electronics network PCs minicomputers mainframe computers distributed computing environments that include any of the above systems or devices and the like.

The steps of the claimed method and apparatus may be described in the general context of computer executable instructions such as program modules being executed by a computer. Generally program modules include routines programs objects components data structures etc. that perform particular tasks or implement particular abstract data types. The methods and apparatus may also be practiced in distributed computing environments where tasks are performed by remote processing devices that are linked through a communications network. In a distributed computing environment program modules may be located in both local and remote computer storage media including memory storage devices.

With reference to an exemplary system for implementing the steps of the claimed method and apparatus includes a general purpose computing device in the form of a computer . Components of computer may include but are not limited to a processing unit a system memory and a system bus that couples various system components including the system memory to the processing unit . The system bus may be any of several types of bus structures including a memory bus or memory controller a peripheral bus and a local bus using any of a variety of bus architectures. By way of example and not limitation such architectures include Industry Standard Architecture ISA bus Micro Channel Architecture MCA bus Enhanced ISA EISA bus Video Electronics Standards Association VESA local bus and Peripheral Component Interconnect PCI bus also known as Mezzanine bus.

Computer typically includes a variety of computer readable media. Computer readable media can be any available media that can be accessed by computer and includes both volatile and nonvolatile media removable and non removable media. By way of example and not limitation computer readable media may comprise computer storage media and communication media. Computer storage media includes both volatile and nonvolatile removable and non removable media implemented in any method or technology for storage of information such as computer readable instructions data structures program modules or other data. Computer storage media includes but is not limited to RAM ROM EEPROM flash memory or other memory technology CD ROM digital versatile disks DVD or other optical disk storage magnetic cassettes magnetic tape magnetic disk storage or other magnetic storage devices or any other medium which can be used to store the desired information and which can accessed by computer . Communication media typically embodies computer readable instructions data structures program modules or other data in a modulated data signal such as a carrier wave or other transport mechanism and includes any information delivery media. The term modulated data signal means a signal that has one or more of its characteristics set or changed in such a manner as to encode information in the signal. By way of example and not limitation communication media includes wired media such as a wired network or direct wired connection and wireless media such as acoustic RF infrared and other wireless media. Combinations of the any of the above should also be included within the scope of computer readable media.

The system memory includes computer storage media in the form of volatile and or nonvolatile memory such as read only memory ROM and random access memory RAM . A basic input output system BIOS containing the basic routines that help to transfer information between elements within computer such as during start up is typically stored in ROM . RAM typically contains data and or program modules that are immediately accessible to and or presently being operated on by processing unit . By way of example and not limitation illustrates operating system application programs other program modules and program data .

The computer may also include other removable non removable volatile nonvolatile computer storage media. By way of example only illustrates a hard disk drive that reads from or writes to non removable nonvolatile magnetic media a magnetic disk drive that reads from or writes to a removable nonvolatile magnetic disk and an optical disk drive that reads from or writes to a removable nonvolatile optical disk such as a CD ROM or other optical media. Other removable non removable volatile nonvolatile computer storage media that can be used in the exemplary operating environment include but are not limited to magnetic tape cassettes flash memory cards digital versatile disks digital video tape solid state RAM solid state ROM and the like. The hard disk drive is typically connected to the system bus through a non removable memory interface such as interface and magnetic disk drive and optical disk drive are typically connected to the system bus by a removable memory interface such as interface .

The drives and their associated computer storage media discussed above and illustrated in provide storage of computer readable instructions data structures program modules and other data for the computer . In for example hard disk drive is illustrated as storing operating system application programs other program modules and program data . Note that these components can either be the same as or different from operating system application programs other program modules and program data . Operating system application programs other program modules and program data are given different numbers here to illustrate that at a minimum they are different copies. A user may enter commands and information into the computer through input devices such as a keyboard and pointing device commonly referred to as a mouse trackball or touch pad. Other input devices not shown may include a microphone joystick game pad satellite dish scanner or the like. These and other input devices are often connected to the processing unit through a user input interface that is coupled to the system bus but may be connected by other interface and bus structures such as a parallel port game port or a universal serial bus USB . A monitor or other type of display device is also connected to the system bus via an interface such as a video interface . In addition to the monitor computers may also include other peripheral output devices such as speakers and printer which may be connected through an output peripheral interface .

The computer may operate in a networked environment using logical connections to one or more remote computers such as a remote computer . The remote computer may be a personal computer a server a router a network PC a peer device or other common network node and typically includes many or all of the elements described above relative to the computer although only a memory storage device has been illustrated in . The logical connections depicted in include a local area network LAN and a wide area network WAN but may also include other networks. Such networking environments are commonplace in offices enterprise wide computer networks intranets and the Internet.

When used in a LAN networking environment the computer is connected to the LAN through a network interface or adapter . When used in a WAN networking environment the computer typically includes a modem or other means for establishing communications over the WAN such as the Internet. The modem which may be internal or external may be connected to the system bus via the user input interface or other appropriate mechanism. In a networked environment program modules depicted relative to the computer or portions thereof may be stored in the remote memory storage device. By way of example and not limitation illustrates remote application programs as residing on memory device . It will be appreciated that the network connections shown are exemplary and other means of establishing a communications link between the computers may be used.

At block if a matching network signature is not found the method may create a new profile for the new network signature. The default name for a new network profile may be the DNS suffix of the network. If the DNS suffix is already the name of another network profile then sequential numbering will be included in the name of the new network profile i.e. microsoft.com microsoft.com 2 microsoft.com 3 etc. . The default icon for the profile will be a generic network profile icon. At block if a matching network signature is found the method may merge the new network signature with the found network signature. At block if a network signature is recognized by the device at block the method may update the network signature status. By updating network signature status the method may update whether a network signature was connected or not or whether a network signature was authenticated or not.

A network signature may be a network ID a link ID and a hop ID. The network ID may be a unique ID corresponding to a site for example Microsoft.com. Of the network link and hop IDs the network ID is the least specific. A link ID may be a unique ID corresponding to a subnet for example a MAC gateway address. This ID is more specific than the network ID but less specific than the hop ID. A hop ID may be a unique ID corresponding to a segment for example a specific access point. Of the network link and hop IDs the hop ID is the most specific. A managed network may be a network with a domain controller and an unmanaged network may be a network without a domain controller. The following are several examples of the method.

Abby and her neighbor purchase identical routers and simply plug them into power and their cable modems. Abby connects her laptop to her home network and the first network profile is automatically created. Some time later Abby visits her neighbor and decides to connect her laptop to her neighbor s network. After she connects the neighbor s network is identified as a different network and assigned a new profile.

Abby typically connects her laptop to her home network via 802.11. Today however she plans to transfer some very large files so she decides to connect to her home network via Ethernet. After she connects Windows reports that she is connected to the same network profile as when she is connected via 802.11.

Ed s corporation has a campus with multiple buildings and many wireless access points. Though Ed uses his laptop in most of these buildings and therefore connects to many access points he is always shown as connected to the same network profile. Additionally if he VPNs into work from home he is shown as connected to the same network profile.

Patrick frequently uses his laptop at work and at home. He configures his laptop so that it automatically switches the default printer based upon the network profile to which it is currently connected. When at work the default printer automatically switches to be the printer in his office. When at home the default printer automatically switches to be the printer in his study even if he is also VPNed into work.

Patrick almost always has his laptop with him and he connects to multiple networks. On some networks he wants to interact with other computers and devices on the network so he chooses to open the discovery ports in Windows Firewall when connected to these networks. Patrick however uses other networks simply for Internet access and wants to maximize his security on these networks so he chooses to close the discovery ports in Windows Firewall when connected to these networks.

Scenario 1 When the laptop is connected to internet through an Internet Service Provider at home a network profile Home is created by the Network Profile Service. 

Scenario 2 When the laptop is connected to corporate network another network profile Work is created by the Network Profile Service. Home network profile remains inactive.

Scenario 3 When laptop is connected to network at home through the ISP Work network profile remains inactive. However when a VPN connection is established to the corporate network Work network profile also becomes active.

The Network Profile Manager may be a singleton COM object which monitors network connectivity by registering with the Network Location Awareness NLA service provides network change notifications to interested clients and exposes a set of APIs for Network Profile Management such as Network Profile Management UIs .

The Network Profile Enumerator may be a COM object that provides an interface to enable enumeration of available connected and saved Network Profiles such as those in store .

The Network Profile may be a COM object that represents a network on the system. For example Abby s Network Home Network etc.

The Network Signature Enumerator may be the COM object that provides an interface to enumerate network signatures.

The Network Signature may be a COM object that provides an interface to represent a network signature.

The architecture for the method may be illustrated in . The network profiles management user interface may be divided into three largely independent components 

According to the method there may be a property page for each network profile. This property page may a few functions 

The Network Profiles Folder may be the central place for managing network profiles. It may allow the user to rename profile and launch Network Profile Property pages. It may be an implementation of IShellFolder interface and other Shell extension related interfaces to provide features like context menu and drag and drop. It may have a list view showing the information from Network Profile Services.

The Network Status and Options Page may be the central place for viewing the status of the user session s overall network connectivity launching relevant tasks and linking to the various components for managing network configuration. This fold may be implemented by using the call processing language CPL framework and hosting a network mini map provided by netmap.dll .

In Profile Manager CProfileMgr may be a base class for the Network profile property pages the Network profiles folder and the Network status and options page to inherit and may be responsible for getting and setting properties to from the Network Profile Services . This class may also provide functions for getting profile list signature list icon list . . . etc. The Network Profile Services may provide network profile and signature data and notifications. The Netshell.dll may host the Connection Status and Property pages that the method needs to launch. The Netmap.dll may provide the network mini map implementation that the method may host in the Status and Options folder component. The Network Communications Services Interface NCSI Network Profile Services may provide the state of a profile whether it is connected or not. But it may not distinguish whether it has Internet connectivity or just local connectivity as NCSI may help in that regard. NCSI may be built into NLA. The Netman.dll may provide the network connection data icon provided by netshell dll .

The programming model may be a COM based interface that supports automation. The clients may connect to the Network Profile Service by instantiating a Profile Manager object. Through the Profile Manager object the clients may enumerate or register for change notifications. The COM APIs fall into the following classes.

The Network Profile Service may detect the presence of a network by registering with NLA . Whenever a network connection is established or its state changes the Network Profile Service may get a notification from NLA . NLA may provide a unique signature identifying the network interface along with some characteristics of the network interface

Network Profile Service may use NLA API to parse the NLA signature in terms of its underlying components which may be NetworkID LinkID and HopID. The NetworkID and possibly the LinkID may be used to determine if it is a new network or an existing network. Other characteristics provided by NLA may help determine if the network is managed or unmanaged.

As described in relation to network profiles may reflect the network environment to which a computer is connected. The profiles may consist of one or more network signatures. If a signature is detected that doesn t already exist in a profile or cannot be merged into an existing profile then Network Profile Service may create a new network profile. However if the new signature is already part of a network profile then the status of the network profile may be updated to reflect the change in the state.

The Network Profile Service may use the registry to save all the information about network profiles and specific pieces of NLA signatures. During the boot process it may initialize its internal data structures by reloading the information from the registry.

Though network profiles are visible to all users Network Profile Service may ensure that the state of a network profile is correctly reflected to users of different session. To do this the Network Profile may takes into account the compartment id of the networks. For example if a user makes a VPN connection the network profile containing the network signature corresponding to the VPN connection may appear connected to the only user that made the VPN connection. The network profile may appear disconnected to the rest of the users. Additionally the notification of the connection may be sent to only those applications that are running in the context of the user of the active VPN connection.

The method may also expose application programming interfaces APIs to assist using the new functionality. The Network Profiles Service will expose APIs that provide the following functionality 

The method may also provide notifications of the following events to components that register to receive the notifications 

The interface may be implemented by a singleton COM object. It may provide a set of methods to perform network profile management functions. The following is a description of various tasks that may be supported by this interface.

CreateNetworkProfile method may create a new network profile with the specified name and returns a pointer to INetworkProfile interface pointer on success.

EnumNetworkProfiles may return an interface to enumerate Network Profiles that are connected disconnected or all. NP ENUM PROFILE flag may control the type of network profiles to enumerate.

NP ENUM NETWORK PROFILE CONNECTED may cause the enumerator to return network profiles that are connected at the time the IEnumNetworkProfile enumerator is instantiated. cOnce IEnumNetworkProfile enumerator interface is returned to the caller the list of connected network profiles may be locked for that instance of the enumerator. If a network profile becomes disconnected during the enumeration the network profile may not be dropped from the list of this enumerator. If a new network profile is created by the network profile service during the enumeration then it may not be included in the enumeration.

NP ENUM NETWORK PROFILE DISCONNECTED may cause the enumerator to return network profiles that are disconnected at the time the IEnumNetworkProfile enumerator is instantiated. Once IEnumNetworkProfile enumerator interface is returned to the caller the list of disconnected network profiles may be locked for that instance of the enumerator. If a network profile becomes connected during the enumeration the network profile may not be dropped from the list of this instance of enumerator. If a new network profile is created by the network profile service during the enumeration then it may not be included in the enumeration.

NP ENUM NETWORK PROFILE ALL may cause the enumerator to return all the network profiles that are in the system irrespective of their state. If a new network profile is created by the network profile service during the enumeration then it may be included in the enumeration list. The caller may have to reset the point of enumeration if it is already at the end to get the newly created network profile.

In all types of enumeration if a network profile is deleted it may be removed from the enumerator s list.

A connected or managed network profile may not be deleted. The function may fail if it is called on a connected or managed network profile. Once a network profile is deleted the only method that may successfully work on INetworkProfile interface is GetId. All other methods may fail with error code E UNEXPECTED.

An active network signature may not be deleted. The function may fail if it is called on an active signature. Once a network signature is deleted the only method that may successfully work on INetworkSignature interface is GetId. All other methods may fail with error code E UNEXPECTED.

IEnumNetworkProfile may be a standard enumerator for network profiles. It may enumerate connected disconnected or all network profiles.

IEnumNetworkSignature may be a standard enumerator for NLA signatures. It may enumerate connected or active disconnected or all network signatures within a profile. The interface may be obtained from INetworkProfile interface.

GetName may return the name of the network profile. The caller may be responsible for releasing the memory pointed to by ppszProfileName by calling CoTaskMemFree.

The name of the network file may be MAX PROFILE NAME LEN long. Two may have the same name. So it may not bw recommended to use the name to identify a network profile. The name may be required to not contain tab characters.

GetDescription may return a description string for the network profile. The caller may be responsible for releasing the memory pointed to by ppszDescription by calling CoTaskMemFree 

GetId may return a unique identifier of a network profile. The caller may be responsible for allocating the buffer pointed to by pguidProfileId and should be large enough to hold a GUID.

GetIcon may return the icon of a network profile in base64 encoded format. The caller may be responsible for releasing the memory pointed to by ppIconData using CoTaskMemFree function.

SetIcon may set a new icon for a network profile. pIconData may contain the icon bitmap in base64 encoded format.

GetTimeCreated may return in FILETIME format the local date and time when the network profile was created and connected.

If the network profile has never been connected the pdwLowDateTimeConnected and pdwHighDateTimeConnected may be zero.

NP PROFILE STATE CONNECTED may mean that at least one of the NLA signatures in the network profile is active.

NP PROFILE STATE DISCONNECTED may mean that none of the NLA signatures in the network profile is active.

GetInterfaces may return an array of interface guids of all the connected network signatures in the network profile. If the network profile is not connected i.e. none of its network signatures is connected pdwCount may be set to zero and ppIntefaces may be set to NULL. The caller may be responsible for releasing memory of each element of the array as well as the array buffer pointed to by ppInterface.

EnumNetworkSignatures may return an NLA signature enumerator that enumerates signatures within the profile.

NP ENUM NETWORK SIGNATURE CONNECTED may return an enumerator for connected or active NLA signatures. Once IEnumNetworkSignature interface is returned to the caller the list of connected network signatures may be locked for that instance of the enumerator. If a network signature becomes disconnected during the enumeration the network signature may not be dropped from the list of this instance of the enumerator. If a new network signature is created by the network profile service during the enumeration then it may not be included in the enumeration.

NP ENUM NETWORK SIGNATURE DISCONNECTED may returns an enumerator for disconnected NLA signatures. Once IEnumNetworkSignature interface is returned to the caller the list of disconnected network signatures may be locked for that instance of the enumerator. If a network signature becomes connected during the enumeration the network signature may not be dropped from the list of this instance of the enumerator. If a new network signature is created by the network profile service during the enumeration then it may not be included in the enumeration.

NP ENUM NETWORK SIGNATURE ALL may returns an enumerator for all NLA signatures. If a new network signature is created by the network profile service during the enumeration then it may be included in the enumeration list. The caller may have to reset the point of enumeration if it is already at the end to get the newly created network signature.

In all types of enumeration if a network signature is deleted it may be removed from the enumerator s list.

GetId may return a unique identifier of a network signature. The caller may be responsible for releasing the memory pointed to by ppszSignatureId by calling CoTaskMemFree.

GetDescription may return a description string for the network signature. The caller may be responsible for releasing the memory pointed to by ppszDescription by calling CoTaskMemFree 

The description of a network profile may be MAX SIGNATURE DESC LEN. The default description of a newly created network signature may be the DNS suffix of the network identified by the network signature.

GetInterfaces may return an array of interface guids of a network signature. If the signature is not connected the function may return NULL in ppInterfaces and pdwCount is set to zero. The caller may be responsible for releasing memory of each element of the array as well as the array buffer pointed to by ppInterface.

CLSID CNetworkProfileManager may implement a connection point for notifications of changes in network profiles and network signatures. Below may be a description of the sink interface for various notifications. The callback methods of the sink interface of a client may or may not receive all the events on the same thread. However until the callback method has returned the client may not receive another event.

INotifyNetworkProfileEvents may be a sink interface that a client will implement to get network profile related events.

OnNetworkProfleAdded method may be called when a new network profile is added. pProfile is a pointer to the new network profile interface. The client may be responsible for releasing pProfile interface.

An OnNetworkProfleDeleted method may be called when a network profile is deleted. pguidProfile may identify the network profile that has been deleted.

A OnNetworkProfleConnected method may be called when a disconnected network profile is connected. pguidProfile may identify the network profile that has connected.

A OnNetworkProfleDisconnected method is called when a connected network profile may be disconnected. pguidProfile may identify the network profile that has disconnected.

OnNetworkProflePropertyChange method may be called when one or more properties of the network profile change. pguidprofile may identify the network profile.

A OnNetworkSignatreAdded method may be called when a new network signature is added. pguidProfile may identify the network profile containing the network signature and pSignature may be the interface representing the network signature. The client may be responsible for releasing pSignature interface.

A OnNetworkSignatreDeleted method may be called when a network signature is deleted. pguidProfile may identify the network profile containing the network signature and pszSignatureId may be the id of the network signature.

A OnNetworkSignatreConnected method may be called when a network signature is connected. pguidProfile identifies the network profile containing the network signature and pszSignatureId may be the id of the network signature.

OnNetworkSignatreDisconnected method may be called when a network signature is disconnected. pguidProfile may identify the network profile containing the network signature and pszSignatureId may be the id of the network signature.

A OnNetworkSignaturePropertyChange method may be called when one or more properties of a network signature change. pszSignatureId may identify the network signature.

Other APIs may also be used. The functionality may be similar to the APIs previously discussed with some changes to the specific calls. Some examples follow.

The following table illustrates what kind of notification may be communicated to a client when an event occurs. Sometimes a single event may trigger more than one type of notification. In such cases the notifications may be reported in the order listed. The notifications may be sent to only those users who are affected by the event. Network Profile Service may take into account the compartment of the network signature associated with the event and notifies only those user sessions that belong this compartment.

The status tab may be the first and default tab for the network profile property pages. This tab may have two sections in order from top to bottom 

At the top left corner of the status tab the network profile s small 32 32 pixels for example icon may be shown. To the right of this icon may be a text box populated with the friendly name for the network profile. The user may change the name of the network profile in place.

Directly below the network profile name may be a button labeled Change icon . . . Clicking this button may open a Change icon . . . dialog on top of the property page for selecting an icon for the network profile. This dialog may include a list box of available icons. By default the network profile s current icon may be selected. The user may select another icon from the list or click a Browse . . . button. Clicking this button may open the standard File Open dialog filtered to show only Images. If the user selects an icon in the File Open dialog this icon may be added to the list in the Change icon . . . dialog and selected.

Immediately below the icon and name section on the status tab the current status of the network profile may be communicated. The status section may indicate that the network profile is in one of two possible states disconnected or connected. If the network profile is unavailable then a line reading Status Disconnected may be added to the property page. If the network profile is connected then a line reading Status Connected may be added to the property page.

Additionally a list of the network connections currently connected to the network profile may be enumerated in a listbox. Double clicking an item in the list may open the status page for the network connection on top of the network profile s property page. To the right of the listbox there may be two buttons 

This may be the second of two tabs on the network profiles property page. The tab may enumerate the signatures currently associated with the network profile and to allow the user to add delete and move signatures. The primary element on this tab may be a list of the signatures associated with the network profile contained within a listbox.

All signatures for a managed network may be collapsed into a single signature in the listbox. Each unmanaged signature may be enumerated individually in the listbox.

There may be several ways to access or enter the method such as through the Network Profiles Folder the Network Status and Options Page and the Networking Tray Icon Flyout.

The Breadcrumb Bar in the Network Profiles Folder may display the Namespace of what is currently being displayed in the Listview View.

The Wordwheel may exhibit its standard behavior in the Network Profiles Folder. When a user types in the Wordwheel the list currently being displayed in the Network Profiles Folder may be dynamically filtered to contain only those items that match what has been typed.

The tasks shown in the Taskbar may be the same regardless of whether a network profile is connected or disconnected. These tasks in order may be 

The Listview may be the largest component of the Network Profiles Folder. It may contains the list of all network profiles that the current user session has permission to access.

By default the items in a list in the Network Profiles Folder may not be grouped but may simply be listed in alphabetical order. A user however may group network profiles in the Network Profiles Folder by the following groupings 

Single clicking may select an item and the preview pane updates to show metadata for the selected item. Double clicking may select an item and the preview pane updates to show metadata for the selected item. Additionally the property page for the selected network profile may be opened in front of the Network Profiles Folder. Right clicking may select an item and the preview pane may update to show metadata for the selected item.

Hovering over an item may show a tooltip with the following information with a line break between each 

Additionally a context menu with the following options may be shown These may be standard Shell options 

When no item is selected in the Network Profile Folder s Listview view the preview pane may contain a generic network profiles icon and the number of items in the current list. When an item is selected in the Network Profile Folder s Listview view the preview pane may contain the following details about the item 

The Network Status and Options Page may be the central place for viewing the status of the user session s overall network connectivity launching relevant tasks and linking to the various components for managing network configuration. It may be implemented as a Shell Folder and as such will have some major components including a breadcrumb bar a taskbar a pagespace a DUI View and a Preview Pane. The Breadcrumb Bar may display the Namespace of what is currently being displayed in the DUI View. The Taskbar on the Network Status and Options Page may always include the following tasks 

The largest component of a Shell folder is typically the Listview View. As is the case with the Network Map this view may be replaced with a DUI view in the Network Status and Options Page. A DUI View may be used in the Network Status and Options Page in order to display the Network Mini Map.

Although the forgoing text sets forth a detailed description of numerous different embodiments it should be understood that the scope of the patent is defined by the words of the claims set forth at the end of this patent. The detailed description is to be construed as exemplary only and does not describe every possible embodiment because describing every possible embodiment would be impractical if not impossible. Numerous alternative embodiments could be implemented using either current technology or technology developed after the filing date of this patent which would still fall within the scope of the claims.

Thus many modifications and variations may be made in the techniques and structures described and illustrated herein without departing from the spirit and scope of the present claims. Accordingly it should be understood that the methods and apparatus described herein are illustrative only and are not limiting upon the scope of the claims.

