---

title: Self-adapting plug-in service
abstract: A self-adapting plug-in service that runs on a plurality of platforms and obviates the need to develop a different version of the plug-in service for each platform. A self-adapting plug-in service according to the present techniques includes code that generates a platform access using a common plug-in API and a translation layer that translates the platform access into a platform-specific access that is adapted one of the platforms that is running under the self-adapting plug-in service.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07433935&OS=07433935&RS=07433935
owner: Hewlett-Packard Development Company, L.P.
number: 07433935
owner_city: Houston
owner_country: US
publication_date: 20050429
---
A variety of platforms may include support for plug in services. A plug in service may be used to augment the capabilities of a platform by adding services that are not built in to the platform. For example a plug in service may be downloaded via the Internet to provide a new capability to an existing platform.

One example of a platform that supports plug in services is a services platform. A services platform may be defined as a software system that provides a set of services that pertain to a set of devices deployed in a home or business. Examples of devices that may be serviced via a services platform include computer systems printers communication devices storage devices display devices etc. Examples of a services platform include Openview and WebjetAdmin by Hewlett Packard.

A platform may conform to an interface specification that enables software developers to create plug in services that are able to run on the platform. For example an interface specification may include an application programming interface API that defines a set of methods in the platform that may be called by plug in services.

A prior plug in service that is adapted to the interface specification for one platform may not run on another platform due to differences in the interface specifications of the two platforms. For example a prior plug in service developed according to the interface specification of Openview may not run on WebJetAdmin. As a consequence a developer of a plug in service may develop a version of the plug in service for each desired platform. Unfortunately the development of multiple versions of the same plug in service may increase the cost of developing a plug in service by consuming large amounts of software development resources and by increasing development time an increasing the likelihood of software bugs.

A self adapting plug in service is disclosed that runs on a plurality of platforms and obviates the need to develop a different version of the plug in service for each platform. A self adapting plug in service according to the present techniques includes code that generates a platform access using a common plug in API and a translation layer that translates the platform access into a platform specific access that is adapted one of the platforms that is running under the self adapting plug in service.

Other features and advantages of the present invention will be apparent from the detailed description that follows.

In the example embodiment shown the self adapting plug in service may be run on a services platform in a customer site and a services platform in a customer site . The code of the self adapting plug in service generates platform accesses using the common plug in API and the translation layer translates the platform accesses into platform specific accesses that are adapted either the services platform or the services platform depending upon where the self adapting service is running.

The self adapting plug in service may be downloaded from a server to the customer site and or to the customer site via a network e.g. the Internet. Alternatively the self adapting plug in service may be installed at the customer site and or at the customer site using a storage media e.g. optical disc magnetic media etc.

The services platform runs on a computer system at the customer site and provides a set of built in services that pertain to a set of devices that are deployed in the customer site . The services platform includes a platform specific application programming interface API that enables plug in services to access the built in services .

The services platform runs on a computer system at the customer site and provides a set of built in services that pertain to a set of devices that are deployed in the customer site . The services platform includes a platform specific API that enables plug in services to access the built in services .

The services platforms and are different services platforms that provide different platform specific APIs for plug in services. For example the services platform may be Openview and the services platform may be WebJetAdmin.

The translation layer is code that translates between the common plug in API and the platform specific APIs and . A platform access generated by the code may be a call to a built in service of a services platform defined in the common plug in API . In response to the call the translation layer determines which of the services platforms or is running under the self adapting plug in service and then translates the call accordingly. For example if the self adapting plug in service is installed on the services platform then the translation layer translates the call defined in the common plug in API into an equivalent call defined in the platform specific API of the services platform . Similarly if the self adapting plug in service is installed on the services platform then the translation layer translates between the common plug in API and the platform specific API of the services platform .

The translation layer may translate a platform access from the code by performing a platform specific access using a set of semantic rules that correspond to the services platform that is running under the self adapting plug in service . For example if the self adapting plug in service is installed on the services platform then the translation layer may translate a platform access from the code by performing a platform specific access using a set of semantic rules associated with the services platform e.g. Openview or WebJetAdmin semantic rules that pertain to a particular built in service.

In an example embodiment in which the services platform is Openview and the services platform is WebJetAdmin the built in services include and Openview device discovery service an Openview remote access service and an Openview remote transport service and the built in services include a WebjetAdmin device discovery service a WebJetAdmin remote access service and a WebJetAdmin remote transport service.

The common plug in API provides a calling interface to a set of methods in the translation layer that correspond to the common built in services of an underlying services platform i.e. the device discovery service and the remote access service and the remote transport service of the above example services platforms and . An example calling interface of the common plug in API is as follows.

The argument device data is a data structure enables a call from the code to pass data parameters commands etc. to the DiscoverDevice method of the translation layer . The device data data structure includes a set of data parameters commands etc. that enables the translation layer to construct a call to any of the underlying services platforms onto which the self adapting plug in service may be installed. For example the device data data structure includes a set of data parameters commands etc. that enables the translation layer to construct a call to Openview device discovery service and to construct a call to the WebjetAdmin device discovery service.

Similarly the argument remoteaccess data is a data structure enables a call from the code to pass data parameters commands etc. to the RemoteAccess method of the translation layer and the argument remotetransport data is a data structure enables a call from the code to pass data parameters commands etc. to the RemoteTransport method of the translation layer . The remoteaccess data and RemoteTransport data structures include data parameters commands etc. that enables the translation layer to construct a corresponding call to any of the underlying services platforms onto which the self adapting plug in service may be installed.

As shown the code generates a call DiscoverDevice device data to the translation layer using the common plug in API . The translation layer translates the call DiscoverDevice device data into a call Openview DiscoverDevice arg1 arg2 ..argx to the Openview device discovery service using the platform specific API . The translation layer constructs the Openview DiscoverDevice arg1 arg2 . . . argx call by determining that the self adapting plug in service is running on Openview and extracting the arguments arg1 arg2 . . . argx from the device data data structure according to the Openview platform specific API . Similarly the code generates a call RemoteAccess remoteaccess data to the translation layer using the common plug in API and the translation layer translates it into a call Openview RemoteAccess arg1 arg2 . . . argx to the Openview remote access service using the platform specific API and the code generates a call RemoteTransport remotetransport data to the translation layer using the common plug in API and the translation layer translates it into a call Openview RemoteTransport arg1 arg2 . . . argx to the Openview remote transport service using the platform specific API .

At step the installer program for the self adapting plug in service is run on the computer system . The installer program may run automatically after download or may instigated by a user.

At step the installer program determines which services platforms are installed on the computer system . The installer program may detect a services platform by finding files associated with the services platform in a directory of the computer system . For example the installer program may find Openview and or WebjetAdmin files in a directory of the computer system . Alternatively the installer program may detect a services platform by examining a registry of the operating system of the computer system . For example a registry may indicate that Openview and or WebJetAdmin is installed on the computer system .

At step the installer program generates a prompt for installing the self adapting plug in service onto one of the detected services platform. For example if more than one services platform was detected at step then at step a prompt is generated that enables selection of one of them e.g. either Openview or WebjetAdmin for the installation. If only one services platform was detected at step then at step a prompt may be generated that enables verification of the self adapting plug in service installation. The prompt at step may be answered by a user or may be automatically answered as part of the installation.

At step the installer program passes an identifier to the self adapting plug in service that identifies which services platform was selected at step . The translation layer of the self adapting plug in service uses the identifier when translating platform accesses to a services platform by the code .

The built in service is a device communication service that enables communication with devices at a customer site. The built in service provides server to device communications data gathering and administration. In one embodiment the built in service includes device simple network management protocol SNMP printer management language PML protocol printer job language PJL protocol and service location protocol SLP .

The built in service is a common platform service a user interface service and a console management service. The common platform service can gather data reflecting what is displayed on a user interface of the services platform .

The built in service is a device discovery service. A set of device discovery methods are employed through the services platform to locate devices on a network at a customer site of the services platform . The device discovery methods include multicasting service location protocol discovery SNMP range ping discovery ARP table discovery and directed network broadcasting discovery.

The built in service is a remote access service. Remote access is provided from remote clients through the self adapting plug in service and the services platform for the purposes of command and control of servers at the remote site. These access techniques include VPN secure shell and HTTP data brokering.

The built in service is a remote transport service. Data is collected and transported by the self adapting plug in service through the services platform . These remote transports include HTTP S SMTP and secure SMTP.

Table 1 shows the common plug in API presented to the self adapting plug in service and the platform specific API for the services platform in the above example embodiment.

One example a semantic rule pertaining a services platform is parsing of returned data. The data return structures for each of the elements may be somewhat different for each services platform. Thus the self adapting plug in service return data structures are formed to accommodate the various data elements of each services platform. Specific parsing rules for each services platform are then utilized as part of the common plug in API.

Another example a semantic rule pertaining a services platform is processing time for actions which may vary depending upon the platform specific API call. For example transaction time out rules are different for the snmpGetBlock method on WebJetAdmin as compared to OpenView. Thus transactional logic retries etc. may different for each services platform and may specified in a translation layer.

Another example a semantic rule pertaining a services platform is the availability of API elements in each services platform. For example a services platform may not support all of the common plug in API elements. For example getDeviceConsuleGroup is not supported when the a self adapting plug in service is hosted in OpenView but is when hosted in WebJetAdmin. Thus a translation layer may be provided with information on the supported APIs for each services platform and adapts accordingly.

While the above description focuses on embodiments in which a self adapting plug in service runs on services platforms the present techniques are applicable to plug in services to any platforms that have a substantial commonality in built in services. Once a translation layer to the common services of a set of platforms according to a common plug in API then any plug in service may be developed using that common plug in API and may then run on any of the platforms in conjunction with the translation layer.

The present techniques may be applied to services residing on JetDirect network cards in Hewlett Packard printers. JetDirect includes have a number of services available e.g. SNMP agents secure sransports such as https and secure shell IPSec for data link layer data encryption which could be used along with remote access and remote transport of data and device discovery capabilities in the form of multicasting.

The present techniques may be applied to printer drivers which include services such as printer discovery graphics text rendering low level OS graphics APIs and translating application data to printer languages such as PCL and Postscript

The foregoing detailed description of the present invention is provided for the purposes of illustration and is not intended to be exhaustive or to limit the invention to the precise embodiment disclosed. Accordingly the scope of the present invention is defined by the appended claims.

