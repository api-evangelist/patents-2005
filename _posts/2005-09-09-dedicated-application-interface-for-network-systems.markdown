---

title: Dedicated application interface for network systems
abstract: Method and system for receiving and sending network packets from a network is provided. The system includes, a host processor that executes an operating system for a host system and at least one application that runs in a context that is different from a context of the operating system; and a network adapter with a hardware device that can run a network protocol stack, wherein the application can access the network adapter directly via an application specific interface layer without using the operating system.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07639715&OS=07639715&RS=07639715
owner: QLOGIC, Corporation
number: 07639715
owner_city: Aliso Viejo
owner_country: US
publication_date: 20050909
---
This patent application is related to the following U.S. patent applications the disclosures of which are incorporated herein by reference in their entirety Ser. No. 11 222 594 entitled METHOD AND SYSTEM FOR MEMORY VALIDATION filed on even date herewith and Ser. No. 10 620 040 entitled Method and System for Processing Network Data Packets filed on Jul. 15 2003.

The present invention relates to network systems and more particularly to offloading host system operating tasks for managing network related operations.

Computer networks are commonly used today in various applications. Computer networks typically use a layered protocol structure to manage network traffic. One common model that is typically used is the ISO model that includes a physical layer a data link layer that includes a MAC layer a network layer and others.

Various protocols standards are currently used by computing systems and devices to communicate via networks. The following provides an introduction of some of the standards protocols 

Transmission Control Procotol Internet Protocol TPC IP TCP is a standard network protocol incorporated herein by reference in its entirety that provides connection oriented reliable byte stream service. This means that two nodes establish a logical connection before sending data and that TCP maintains state information regarding the data transfer. Reliable means that data is delivered in the same order that it was sent. A byte stream service means that TCP views data to be sent as a continuous data stream that is sent in any way it sees fit and delivers it to the remote node as a byte stream.

The IP standard protocol incorporated herein by reference in its entirety provides a datagram service whose function is to enable routing of data through various network subnets. Each of these subnets could be a different physical link such as Ethernet ATM etc. IP is also responsible for fragmentation of the transmit data to match a local link s MTU. IP can fragment data at the source node or at any intervening router between the source and destination node.

A complete description of the TCP IP protocol suite is provided in TCP IP Illustrated Vol. 1 by W. Richard Stevens and Volume 2 by Gary R. Wright and W. Richard Stevens published by Addison Wesley Professional Computing Series that is incorporated herein by reference in its entirety.

iSCSI Protocol Internet SCSI iSCSI as defined by the Internet Engineering Task Force IETF maps the standard SCSI protocol on top of the TCP IP protocol. iSCSI incorporated herein by reference in its entirety is based on Small Computer Systems Interface SCSI which enables host computer systems to perform block data input output I O operations with a variety of peripheral devices including disk and tape devices optical storage devices as well as printers and scanners. The iSCSI and TCP IP protocol suite consist of 4 protocol layers the application layer of which iSCSI is one application the transport layer TCP the network layer IP and the link layer i.e. Ethernet .

A traditional SCSI connection between a host system and peripheral device is through parallel cabling and is limited by distance and device support constraints. For storage applications iSCSI was developed to take advantage of network architectures based on Ethernet standards. iSCSI leverages the SCSI protocol over established networked infrastructures and defines the means for enabling block storage applications over TCP.

The iSCSI architecture is based on a client server model. Typically the client is a host system such as a file server that issues a read or write command. The server may be a disk array that responds to the client request. Typically the client is an initiator that initiates a read or write command and a disk array is a target that accepts a read or write command and performs the requested operation.

In a typical iSCSI exchange an initiator sends a read or write command to a target. For a read operation the target sends the requested data to the initiator. For a write command the target sends a Ready to Transfer Protocol Data Unit PDU informing the initiator that the target is ready to accept the write data. The initiator then sends the write data to the target. Once the data is transferred the exchange enters the response phase. The target then sends a response PDU to the initiator with the status of the operation. Once the initiator receives this response the exchange is complete. The use of TCP guarantees the delivery of the PDUs.

Typically logical units in the target process commands. Commands are sent by the host system in Command Descriptor Blocks CDB . A CDB is sent to a specific logical unit for example the CDB may include a command to read a specific number of data blocks. The target s logical unit transfers the requested data block to the initiator terminating with a status message indicating completion of the request. iSCSI encapsulates CDB transactions between initiators and targets over TCP IP networks.

There has been a need to offload TCP IP protocol stack processing from a host computer system to a network adapter. A network adapter that executes the TCP IP protocol stack is called a TOE TCP Offload Engine .

Most TOE devices provide a single physical interface to a host processor CPU . Applications that run on the host side are allocated memory locations. In most environments for example Windows Linux and others the memory locations on the host side used to access the TOE interface is controlled by the operating system. This is inefficient because the operating system context to receive and send data on behalf of the application is different from the context of the application. Hence context switching between the application and the operating system is used by conventional systems to process network traffic. This can result in latencies and network bandwidth degradation and hence is undesirable.

Therefore there is a need for a system and method that will allow plural applications running on a host system to efficiently access an adapter to communicate with a network.

In one aspect of the present invention a system coupled to a network is provided. The system includes a host processor that executes an operating system for a host system and at least one application that runs in a context that is different from a context of the operating system and a network adapter with a hardware device that can run a network protocol stack wherein the application can access the network adapter directly via an application specific interface layer without using the operating system.

In another aspect of the present invention a method for network communications is provided. The method includes initializing a socket call wherein an application having it s own context in a host computing system sends the socket call and accessing a network adapter coupled to the host system wherein the network adapter processes network traffic by executing a network protocol and the application running on the host system accesses the network adapter using an application specific interface layer without using an operating system that runs on the host system.

In another aspect of the present invention a host computing system coupled to a network for receiving and transferring network packets is provided. The host computing system includes a host processor that executes an operating system and at least one application that runs in a context that is different from a context of the operating system and a network adapter with a hardware device for executing a network protocol stack for processing network traffic wherein the application can access the network adapter directly via an application specific interface layer without using the operating system.

In yet another aspect of the present invention a network adapter for offloading network protocol processing from a host system is provided. The network adapter includes an offload engine that offloads network protocol processing from a host processor of the host system having an operating system and at least one application that runs in a context that is different from a context of the operating system wherein the application can access the network adapter directly via an application specific interface layer without using the operating system.

This brief summary has been provided so that the nature of the invention may be understood quickly. A more complete understanding of the invention can be obtained by reference to the following detailed description of the preferred embodiments thereof concerning the attached drawings.

To facilitate an understanding of the preferred embodiment the general architecture and operation of a host system will be described. The specific architecture and operation of the preferred embodiment will then be described with reference to the general architecture.

Host memory is coupled to the CPU via a system bus or a local memory bus not shown . The host memory is used to provide CPU access to data and or program information that is stored in host memory at execution time. Typically the host memory is composed of random access memory RAM circuits. A computing system with the CPU and main memory is often referred to as a host system.

In host memory specific locations for example A and B may be allocated to specific applications for example and in .

System includes a network adapter having a TCP IP accelerator module or chip or system or engine TOE that is used to connect host system to another host system or peripheral device not shown via a network connection A.

TOE provides assistance to improve the speed of iSCSI read and write transactions as well as a full implementation of a TCP IP protocol. TOE also includes an embedded Ethernet MAC to connect a PCI based host to a LAN not shown .

In conventional systems a host CPU for example executes the network protocol stack in software to process network packets. Conventional TOE engines also provide only a partial solution because they cannot handle exceptions for example TCP IP exceptions .

In the configuration shown in CPU does not have to execute a network protocol stack in software because TOE can perform that entire function. TOE can establish and maintain a network connection to process network traffic. Details of a TOE are provided in co pending patent application Ser. No. 10 620 040 filed on Jul. 15 2003 incorporated herein by reference in its entirety.

The present invention provides an offloaded implementation of a full network protocol stack for example a TCP IP stack . Application Programming Interfaces APIs to this protocol stack are made available to allow host software to take advantage of the offloaded protocol stack for network applications.

The present invention may be used on a PCI development board with a Field Programmable gate Array FPGA . The chip may also be integrated into an Application Specific Integrated Circuit ASIC with an embedded serialize de serializer SERDES not shown and internal programmable random access memory RAM .

It is noteworthy that the present invention is not limited to any particular protocol or standard. Although the figures and the foregoing examples are based on offloading TCP IP protocol and illustrate iSCSI transactions in one aspect of the present invention adapter may include an offload engine that can process any network protocol stack for example the SPX IPX protocol for any transaction.

Adapter according to the present invention can be used for both initiator and target applications i.e. can be used on a host bus adapter or with a redundant array of inexpensive disks RAID controller . As shown in RAID controller is coupled to plural storage devices for example and .

System includes an embedded processor that is used to process SCSI requests into iSCSI exchanges to transfer SCSI based data. Processor also generates completion messages for host .

iSCSI processor includes hardware state machines firmware which synchronizes incoming byte streams from TCP finds iSCSI PDU boundaries sends data to host via SCSI direct memory access engine module SDE .

System also includes network operation processors NOPs that include plural state machines for different network protocols for example TCP IP and Ethernet for both traffic entering and leaving system . The state machines handle most of the data transfer without host CPU involvement. Local memory interface is used by various system components to access external memory in this illustration RAM .

Encryption de cryption engine is used to encrypt de crypt data while data is moved in and out of host using system . Standard encryption de cryption techniques may be used.

Two DMA engines or modules are used by NOPs to move data to and from host . Inbound DMA module is used to move data from system i.e. from local memory to host memory. Buffer queue manager maintains small and large buffers that are used by Inbound DMA engine . Outbound DMA engine is used to move data from host memory to system for transmission to the network.

SCSI DMA Engine SDE provides iSCSI processor with a DMA channel from Local RAM to Host memory. SDE includes a byte packer function that takes unaligned or less than 8 byte buffers and packs them into 8 byte words before sending them to Host .

System also includes request queue managers the term manager and module are used interchangeably throughout this specification and that are used to pass commands to chip to perform a specific operation. SCSI request queue manager is used for initiating SCSI based transfers while module is used for TCP IP Ethernet or any other protocol standard.

Completion queue managers and are used to send completion messages to host . These messages are generated to report status of inbound i.e. from the network to system and then to host to outbound i.e. from host to the network via system transfers. SCSI completion manager handles SCSI completion messages while non SCSI messages are handled by module .

Register interface provides host access to plural system status and control registers as well as a channel to access local memory .

PCI PCI X interface block and PCI interface provide a PCI PCI X interface between host and system . BIOS Read only memory is also provided to store invariant instruction sequences such as start up instruction sequences or basic input output operating system BIOS sequences instructions.

Interface receives data commands from the host operating system via a TOE driver library may be referred to as library . Library allows the operating system to interface with TOE engine via interface .

Plural applications shown as and run on host system in their individual contexts shown as A A and A . Each application is assigned space in system memory shown as A and B . Each application for example has a special TOE driver library may also be referred to as a module for example and that allows an application to interface directly with the TOE engine . Adapter is made available to each application based on program code that runs within an application s context.

When an application for example wants to establish a network connection the application directly places a call via its own specific interface module for example for application without using the operating system . Adapter establishes the connection and interfaces with the application directly through the application specific TOE driver for example . In one aspect of the present invention the operating system is not involved with an application establishing a network connection.

In step S the TOE driver for example associated with the application sends a command to the TOE engine . Typically this command is sent by the operating system but because of the distributed architecture of an application can directly send the command.

In step S adapter initializes the network connection. In one aspect the network connection is a TCP IP connection.

In step S the connection is established and in step S data is transferred by adapter to the appropriate memory allocated for a particular application. This data transfer occurs without using operating system .

It is noteworthy that the adaptive aspects of the present invention are not limited to any particular operating system for example Windows or Linux or to any particular network protocol for example TCP IP .

Although the present invention has been described with reference to specific embodiments these embodiments are illustrative only and not limiting. Many other applications and embodiments of the present invention will be apparent in light of this disclosure and the following claims.

