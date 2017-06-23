---

title: Method and system for processing network data
abstract: Method and system for a network for receiving and sending network packets is provided. The system includes a host processor that executes an operating system for a host system and at least one application that runs in a context that is different from a context of the operating system; and a network adapter with a hardware device that can run a network protocol stack, wherein the application can access the network adapter directly via an application specific interface layer without using the operating system and the application designates a named memory buffer for a network connection and when data is received by the network adapter for the network connection, then the network adapter passes the received data directly to the designated named buffer.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07735099&OS=07735099&RS=07735099
owner: QLOGIC, Corporation
number: 07735099
owner_city: Aliso Viejo
owner_country: US
publication_date: 20051223
---
This application is related to the following applications incorporated herein by reference in their entirety Ser. No. 11 223 693 now U.S. Pat. No. 7 639 715 entitled Dedicated Application Interface for Network Systems filed on Sep. 9 2005 

Ser. No. 10 620 040 now U.S. Pat. No. 7 403 542 entitled Method and System for Processing Network Data Packets filed on Jul. 15 2003.

The present invention relates to network systems and more particularly to offloading host system tasks for managing network related operations.

Computer networks are commonly used today in various applications. Computer networks typically use a layered protocol structure to manage network traffic. One common model that is typically used is the ISO model that includes a physical layer a data link layer that includes a MAC layer a network layer and others.

Data received and sent to a network often needs to be processed by various network protocol layers before the data is made available to an application that requested the information. Typically a network stack places data that is received from the network in a receive buffer which are allocated by the network layer. The receive buffers are then passed between plural protocol layers until the appropriate application that requested the data is notified that the requested data is available.

Expensive and tedious copying of data commonly takes place before the application gets the data and is undesirable.

Therefore there is a need for a system and method for processing network data without multiple copy operations.

In one aspect of the present invention a system coupled to a network for receiving and sending network packets is provided. The system includes a host processor that executes an operating system for a host system and at least one application that runs in a context that is different from a context of the operating system and a network adapter with a hardware device that can run a network protocol stack wherein the application can access the network adapter directly via an application specific interface layer without using the operating system and the application designates a named memory buffer for a network connection and when data is received by the network adapter for the network connection then the network adapter passes the received data directly to the designated named buffer.

In another aspect of the present invention a method for network communication is provided. The method includes initializing a socket call wherein an application having its own context in a host computing system sends the socket call accessing a network adapter coupled to the host system wherein the network adapter processes network traffic by executing a network protocol and the application running on the host system accesses the network adapter using an application specific interface layer without using an operating system that runs on the host system sending a descriptor to the network adapter that identifies plural parameters for a network connection designating a named buffer to a network connection comparing if data received from a network is for a particular network connection and transferring the received data directly to a named buffer designated for the network connection.

In yet another aspect of the present invention a host computing system coupled to a network for receiving and transferring network packets is provided. The host computing system includes a host processor that executes an operating system and at least one application that runs in a context that is different from a context of the operating system and a network adapter with a hardware device for executing a network protocol stack for processing network traffic wherein the application can access the network adapter directly via an application specific interface layer without using the operating system and the application designates a named memory buffer for a network connection and when data is received by the network adapter for the network connection then the network adapter passes the received data directly to the designated named buffer.

In yet another aspect of the present invention a network adapter for offloading network protocol processing from a host system is provided. The network adapter includes an offload engine that offloads network protocol processing from a host processor of the host system having an operating system and at least one application that runs in a context that is different from a context of the operating system wherein the application can access the network adapter directly via an application specific interface layer without using the operating system and the application designates a named memory buffer for a network connection and when data is received by the network adapter for the network connection then the network adapter passes the received data directly to the designated named buffer.

This brief summary has been provided so that the nature of the invention may be understood quickly. A more complete understanding of the invention can be obtained by reference to the following detailed description of the preferred embodiments thereof concerning the attached drawings.

To facilitate an understanding of the preferred embodiment a top level description of common network protocols standards and the general architecture operation of a host system will be described. The specific architecture and operation of the preferred embodiment will then be described with reference to the general architecture.

Computing systems and devices to communicate via networks currently uses various protocols standards.

Transmission Control Protocol Internet Protocol TCP IP TCP is a standard network protocol incorporated herein by reference in its entirety that provides connection oriented reliable byte stream service. This means that two nodes establish a logical connection before sending data and that TCP maintains state information regarding the data transfer. Reliable means that data is delivered in the same order that it was sent. A byte stream service means that TCP views data to be sent as a continuous data stream that is sent in any way it sees fit and delivers it to the remote node as a byte stream.

IP layer standard protocol incorporated herein by reference in its entirety provides a datagram service whose function is to enable routing of data through various network subnets. Each of these subnets could be a different physical link such as Ethernet ATM etc. IP layer is also responsible for fragmentation of the transmit data to match a local link s MTU. IP layer can fragment data at the source node or at any intervening router between the source and destination node.

A complete description of the TCP IP protocol suite is provided in TCP IP Illustrated Vol. 1 by W. Richard Stevens and Volume 2 by Gary R. Wright and W. Richard Stevens published by Addison Wesley Professional Computing Series that is incorporated herein by reference in its entirety.

iSCSI Protocol Internet SCSI iSCSI as defined by the Internet Engineering Task Force IETF maps the standard SCSI protocol on top of the TCP IP protocol. iSCSI incorporated herein by reference in its entirety is based on Small Computer Systems Interface SCSI which enables host computer systems to perform block data input output I O operations with a variety of peripheral devices including disk and tape devices optical storage devices as well as printers and scanners. The iSCSI and TCP IP protocol suite consist of 4 protocol layers the application layer of which iSCSI is one application the transport layer TCP the network layer IP and the link layer i.e. Ethernet .

A traditional SCSI connection between a host system and peripheral device is through parallel cabling and is limited by distance and device support constraints. For storage applications iSCSI was developed to take advantage of network architectures based on Ethernet standards. iSCSI leverages the SCSI protocol over established networked infrastructures and defines the means for enabling block storage applications over TCP.

The iSCSI architecture is based on a client server model. Typically the client is a host system such as a file server that issues a read or write command. The server may be a disk array that responds to the client request. Typically the client is an initiator that initiates a read or write command and a disk array is a target that accepts a read or write command and performs the requested operation.

In a typical iSCSI exchange an initiator sends a read or write command to a target. For a read operation the target sends the requested data to the initiator. For a write command the target sends a Ready to Transfer Protocol Data Unit PDU informing the initiator that the target is ready to accept the write data. The initiator then sends the write data to the target. Once the data is transferred the exchange enters the response phase. The target then sends a response PDU to the initiator with the status of the operation. Once the initiator receives this response the exchange is complete. The use of TCP guarantees the delivery of the PDUs.

Typically logical units are in the target process commands. Commands are sent by the host system in Command Descriptor Blocks CDB . A CDB is sent to a specific logical unit for example the CDB may include a command to read a specific number of data blocks. The target s logical unit transfers the requested data block to the initiator terminating with a status message indicating completion of the request. iSCSI encapsulates CDB transactions between initiators and targets over TCP IP networks.

RDMA Remote Direct Memory Access RDMA is a standard upper layer protocol incorporated herein by reference in its entirety that assists one computer to directly place information in another computer s memory with minimal demands on memory bus bandwidth and CPU processing overhead. RDMA over TCP IP defines the interoperable protocols to support RDMA operations over standard TCP IP networks. A network interface card or adapter that can offload TCP IP protocol processing and support RDMA over TCP IP may be referred to as an RNIC.

NFS This is a client server application that allows users to access shared files using an interface Virtual File System .

UDP A is a connectionless protocol that runs on top of the IP layer . UDP A provides fewer error recovery services compared to TCP and is commonly used for broadcast type messages.

TOE executes the TCP IP protocol stack or any other protocol stack . Furthermore TOE is used to connect host system to another host system or peripheral device not shown via a network connection A.

Host memory is coupled to the CPU via a system bus or a local memory bus not shown . The host memory is used to provide CPU access to data and or program information that is stored in host memory at execution time. Typically the host memory is composed of random access memory RAM circuits. A computing system with the CPU and main memory is often referred to as a host system.

In conventional systems a host CPU for example executes the network protocol stack in software to process network packets. Conventional TOE engines also provide only a partial solution because they cannot handle exceptions for example TCP IP exceptions .

In the configuration shown in CPU does not have to execute a network protocol stack in software because TOE can perform that entire function. TOE can establish and maintain a network connection to process network traffic. Details of a TOE are provided in patent application Ser. No. 10 620 040 now U.S. Pat. No. 7 403 542 entitled Method and System for Processing Network Data Packets filed on Jul. 15 2003 incorporated herein by reference in its entirety.

The present invention provides an offloaded implementation of a full network protocol stack for example a TCP IP stack . Application Programming Interfaces APIs to this protocol stack are made available to allow host software to take advantage of the offloaded protocol stack for network applications.

It is noteworthy that the present invention is not limited to any particular protocol or standard. Although the figures and the foregoing examples are based on offloading TCP IP protocol and illustrate iSCSI transactions in one aspect of the present invention adapter may include an offload engine that can process any network protocol stack for example the SPX IPX protocol for any transaction.

Adapter according to the present invention can be used for both initiator and target applications i.e. can be used on a host bus adapter or with a redundant array of inexpensive disks RAID controller . As shown in RAID controller is coupled to plural storage devices for example and .

Adapter may be on a PCI development board with a Field Programmable gate Array FPGA . The chip may also be integrated into an Application Specific Integrated Circuit ASIC with an embedded serialize de serializer SERDES not shown and internal programmable random access memory RAM .

System includes an embedded processor that is used to process SCSI requests into iSCSI exchanges to transfer SCSI based data. Processor also generates completion messages for host . The term processor in this context is intended to include any hardware state machine that can perform the intended function.

iSCSI processor includes hardware state machines firmware which synchronizes incoming byte streams from TCP finds iSCSI PDU boundaries sends data to host via SCSI direct memory access engine module SDE .

System also includes network operation processors NOPs that include plural state machines for different network protocols for example TCP IP UDP RDMA NFS and Ethernet for processing traffic entering and leaving system . The state machines handle most of the data transfer without host CPU involvement.

Local memory interface is used by various system components to access external memory in this illustration RAM .

Encryption de cryption engine is used to encrypt de crypt data while data is moved in and out of host using system . Standard encryption de cryption techniques may be used.

Two DMA engines or modules are used by NOPs to move data to and from host . Inbound DMA module is used to move data from system i.e. from local memory to host memory. Buffer queue manager maintains small and large buffers that are used by Inbound DMA engine . Outbound DMA engine is used to move data from host memory to system for transmission to the network.

SCSI DMA Engine SDE provides iSCSI processor with a DMA channel from Local RAM to Host memory. SDE includes a byte packer function that takes unaligned or less than 8 byte buffers and packs them into 8 byte words before sending them to Host .

System also includes request queue managers the term manager and module are used interchangeably throughout this specification and that are used to pass commands to chip to perform a specific operation. SCSI request queue manager is used for initiating SCSI based transfers while module is used for TCP IP Ethernet or any other protocol standard.

Completion queue managers and are used to send completion messages to host . These messages are generated to report status of inbound i.e. from the network to system and then to host to outbound i.e. from host to the network via system transfers. SCSI completion manager handles SCSI completion messages while non SCSI messages are handled by module .

Register interface provides host access to plural system status and control registers as well as a channel to access local memory .

PCI PCI X interface block and PCI interface provide a PCI PCI X interface between host and system . BIOS Read only memory is also provided to store invariant instruction sequences such as start up instruction sequences or basic input output operating system BIOS sequences instructions.

Interface receives data commands from the host operating system kernel via a TOE driver library may be referred to as library . Library allows the operating system to interface with TOE engine via interface .

Plural applications shown as and run on host system in their individual contexts shown as A A and A . Each application is assigned space in system memory shown as A and B . Each application for example has a special TOE driver library may also be referred to as a module for example and that allows an application to interface directly with the TOE . Adapter is made available to each application based on program code that runs within an application s context.

When an application for example wants to establish a network connection the application directly places a call via its own specific interface module for example for application without using the operating system kernel . Adapter establishes the connection and interfaces with the application directly through the application specific TOE driver for example . In one aspect of the present invention the operating system kernel is not involved with an application establishing a network connection.

A socket descriptor provides TOE with connection information. A socket descriptor may include the following information Source MAC Address source in this context means the device system from where a data packet originates Destination MAC Address destination address in this context means the address of the device system location where a packet is destined VLAN Tag Virtual Local Area Network Identifier Destination IP address Source IP address Destination port Source port IP user protocol type for example TCP or UDP Socket Reference Number a number that is used by TOE and the TOE Driver Next Socket Descriptor pointer address of next Socket Descriptor Previous Socket Descriptor pointer address of previous Socket Descriptor Named Buffer Descriptor List Head pointer a pointer to the beginning of Named Buffer Descriptor List described below Named Buffer Descriptor List Tail pointer a pointer to the end of the Named Buffer Descriptor List described below Segment List Head pointer a pointer to the beginning of Segment List described below and Segment List Tail pointer a pointer to the end of Segment List described below .

When TOE receives a socket descriptor from host driver then a connection is established if a descriptor specifies a connection oriented protocol for example TCP . As data is received TOE stores the data in buflets in RAM . The term buflet as used herein throughout this specification means a unit of memory i.e. page block or cell used for storing data.

TOE processes the network headers and verifies the appropriate checksums. TOE matches a received datagram with a socket. If a match is found then data is moved directly to the first available buffer linked to the corresponding socket descriptor.

In the case of an IP UDP datagram after data is placed in the buffer the buffer is returned to the TOE driver. Multiple receive buffers may be submitted by an application so that all received datagrams can be placed in the assigned buffers.

For a TCP segment after the segment payload is copied to the assigned buffers the buffer is returned to the TOE driver. Multiple receive buffers may be submitted by an application so that all received segments can be placed in the assigned buffers. Depending upon the size of the assigned buffer data from plural TCP segments can be placed in the assigned buffer before the assigned buffer is returned to the TOE driver application.

Turning in detail to a TCP segment or a UDP IP datagram collectively referred to as data without limitation is received by TOE S. In step S processor looks for a socket descriptor for the received data. In step S if a socket descriptor is not found then in step S data is sent to an anonymous buffer in Host Memory . Anonymous Buffers in Host Memory are allocated by the TOE driver for example and assigned to TOE for passing Ethernet packets to the TOE driver for processing by the Host Networking Stack. In step S TOE grants control of the anonymous buffer to the TOE Driver for example . In step S an interrupt is generated for the TOE driver and the process ends in step S.

If a socket descriptor is found in step S then adapter links the received segment to the socket descriptor S. In step S adapter determines if a named buffer is available. The named buffer in this context is a buffer s that is designated allocated to a particular application. If a named buffer is not available then the buflet containing the segment is linked to the corresponding Socket Descriptors list of received segments and the process ends in step S.

A named buffer descriptor is used by TOE to manage named buffers. The descriptor includes a Timeout value that can be set by an application which determines the time a buffer is available for a connection a Named Buffer Descriptor Reference Number a handle that is used TOE to move information to a named buffer a Total Byte Count value a Socket Descriptor Reference Number Next Named Buffer Descriptor pointer address of next Named Buffer Descriptor Previous Named Buffer Descriptor pointer address of previous Named Buffer Descriptor Number of header Byte written to buffer for UDP based connections and a Host Memory Descriptor pointer address of memory containing address and size of the host memory pages that comprise the named buffer .

A segment buflet header is used by TOE to manage buflets in local memory . The header includes a Link to next Buflet if segment consists of more than one buflet this field points to next buflet a Byte Offset value for the first Data byte of the segment Number of data bytes in a segment Offset to MAC Header Offset to IP header Offset to IP Payload and Link to next Segment.

Turning back to if a named buffer is available then in step S adapter schedules the segment for delivery to the named buffer. Depending on the type of data the appropriate DMA engine is used to transfer the segment to the named buffer.

In step S adapter determines if all of the received segment data has been scheduled or DMAed for the named buffer. If all the data has been DMAed then in step S the buflet containing the segment is unlinked from the socket descriptor and re linked to the Free Buflet List B that is maintained by adapter .

If all the segment data has not been DMAed then in step SA a segment header byte count value is decreased or decremented by the amount of data that has been DMAed. In step SB a segment header byte offset value is increased or incremented by the amount of data that has been DMAed. Steps SA and SB allows TOE to maintain count of the data that has been DMAed.

In step S adapter determines if a named buffer count value has reached a threshold value. A named buffer has a threshold value that is set by the application. The threshold value determines the amount of data that can be stored in the buffer. A transfer count is maintained that determines how much data has been sent to the named buffer. If the transfer count has reached the threshold value then adapter knows that the named buffer has reached its capacity.

In step S the named buffer is returned to the TOE driver and in step S adapter determines if there are more segments linked to the socket descriptor. If yes then the process returns to step S otherwise the process ends in step S.

If the threshold value has not been reached in step S then in step S adapter determines if the segment is a TCP segment. If it is a TCP segment then in step S adapter determines if a FIN finish or RST reset bit is set in the segment. If a FIN or RST bit is set then the process moves to step S described below in detail with respect to .

If the FIN or RST bit is not set then in step S adapter determines if a PSH push or URG urgent bit is set. If a PSH or URG bit is set then the process moves to step S. If a PSH or URG bit is not set then the process ends in step S.

Named Buffer Designation In step S adapter receives named buffer information from a TOE driver for example . Plural applications using dedicated drivers are allowed to assign named buffers. In step S adapter links the named buffers to a socket descriptor that provides information regarding a connection. In step S adapter determines if any segments are linked to socket descriptors. If yes the process moves to step S . If segments are not linked to socket descriptors then the process simply waits shown as an end step SA .

Socket descriptor In step S adapter receives a socket descriptor from a TOE driver for example . In step S Adapter links the socket descriptor to a list of active sockets or active connections . As described above adapter maintains the list of active sockets in local memory . The process ends in step S.

Anonymous Buffer Links In step S adapter receives anonymous buffer information from TOE driver . Adapter to store segments that are not assigned a named buffer uses the anonymous buffers. In step S the anonymous buffers are linked to a list B of anonymous buffers that is maintained by adapter in local memory . The process ends in step S.

Socket Descriptor Delete Request In step S TOE driver e.g. sends a request to adapter to delete a socket descriptor. This may be performed if a FIN or RST bit is set in a received segment step S . In step S adapter determines if there are any named buffers linked to the socket descriptor. If yes then in step S adapter disassociates the named buffers from the socket descriptor and returns control of the named buffer to the TOE driver. The process loops back to step S until there are no named buffers linked to the socket descriptor.

In step S after all the named buffers are released adapter removes the socket descriptor from the active socket descriptor list. The removed socket descriptor is then returned to the TOE driver. Adapter maintains the list of active socket descriptors in local memory . This allows adapter to efficiently access information regarding active connections that are being maintained and handled by adapter . Thereafter the process ends in step SA.

In step S adapter determines if a named buffer is linked to the socket descriptor. If not then the process moves to step S. If the socket descriptor is linked to a named buffer then in step S the time count value in the named buffer descriptor is decreased. A timer in the Named Buffer Descriptor maintains a count S i.e. the amount of time elapsed for every connection . If a timeout has occurred then the named buffer is returned in step S. If a timeout has not occurred then the process moves to step S.

In step S adapter determines if there are some more active sockets. If yes then in step S the process moves to the next active socket descriptor. If there are no active sockets the process ends in step S.

The present invention allows multiple applications with dedicated TOE drivers to allocate buffers for network connections. The network adapter can move data directly to the named buffers that are designated by the applications. The process is efficient because minimum copying is required to move data to a designated location.

Although the present invention has been described with reference to specific embodiments these embodiments are illustrative only and not limiting. Many other applications and embodiments of the present invention will be apparent in light of this disclosure and the following claims.

