---

title: TCP time stamp processing in hardware based TCP offload
abstract: A method for sending/receiving a TCP segment is provided. The sending process includes, determining if a TCP port can be offloaded; saving a host system's time stamp value; replacing a host system's time stamp value with a TCP offload engine (“TOE”) adapter's time stamp value; and sending the TCP segment via the TOE adapter. The receiving process includes verifying if a TCP port is being offloaded by a host system to the TOE adpter; retrieving the host system's time stamp value; and inserting the host system's time stamp value in the received TCP segment before the forwarding the received TCP segment to the host system.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07420991&OS=07420991&RS=07420991
owner: QLOGIC, Corporation
number: 07420991
owner_city: Aliso Viejo
owner_country: US
publication_date: 20050401
---
This application is a continuation in part of patent application Ser. No. 10 620 076 filed on Jul. 15 2003 now abandoned the disclosure of which is incorporated herein by reference in their entirety.

The present invention relates to computer networks and more particularly to processing network data packets.

Conventional computer systems typically include several functional components. These components may include a central processing unit CPU main memory input output I O devices and storage devices for example disk driver tape drives referred to herein as storage device .

In conventional systems the main memory is coupled to the CPU via a system bus or a local memory bus. The main memory is used to provide the CPU access to data and or program information that is stored in main memory at execution time. Typically the main memory is composed of random access memory RAM circuits. A computer system with the CPU and main memory is often referred to as a host system.

Computer networking is common today. Network computing allows users to share information regardless of where they are located. Network computing has also increased the use of mass storage devices that can store data. Such storage devices often have to interface with networks to exchange commands and or read and write data. Storage controllers are used to facilitate interaction between storage systems and computing systems.

Traditionally storage controllers e.g. disk array controllers tape library controllers have supported the SCSI 3 protocol and have been attached to computers by a Small Computer System Interface SCSI parallel bus or Fibre Channel. Internet SCSI iSCSI standard as defined by the Internet Engineering Task Force IETF maps the standard SCSI protocol on top of the TCP IP protocol to overcome the physical limitations of SCSI.

Networks are generally defined as having layers of protocol. The iSCSI and TCP IP protocol suite consist of four protocol layers the application layer of which iSCSI is one application the transport layer TCP the network layer IP and the link layer i.e. Ethernet .

TCP is a network protocol that provides connection oriented reliable byte stream service. Two network nodes establish a logical connection before sending data and TCP maintains state information regarding the data transfer. A byte stream service means that the TCP protocol views data to be sent as a continuous data stream. shows a block diagram of TCP data encapsulated in an IP datagram. shows a block diagram of a standard TCP header.

Each byte of data sent using a TCP connection is tagged with a sequence number. Each TCP segment header contains the sequence number of the first byte of data in the segment. This sequence number is incremented for each byte of data sent so that when the next segment is to be sent the sequence number is again for the first byte of data for that segment. The sequence numbering is used to determine when data is lost during delivery and needs to be retransmitted.

A data packet receiver keeps track of the sequence numbers and knows the next sequence number when a new segment arrives. If the sequence number in the segment is not the expected one the receiver knows that the segment has arrived out of order. This could be because the network reordered the segments or a segment was lost. Typically TCP handles both of these cases.

Typically when a TCP segment is received on a node an acknowledgement ACK packet is returned to acknowledge reception of the packet. To help reduce the number of segments on a network TCP may delay the delivery of an ACK packet.

A TCP header can include various flag bits for example ACK flag denotes that the acknowledgement number is valid SYN flag denotes synchronize sequence number to initiate a connection FIN flag indicates that the packet sender has finished sending data and RST flag resets a connection.

The standard TCP protocol provides a time stamp option where a sender of a packet places a time stamp. The time stamp is established during the initial phase of a TCP connection. The time stamp allows a receiver to avoid receiving old TCP segments and then considering them to be a part of an existing data segment.

Most conventional solutions for controlling communications between storage controllers and networks are via the software based Open Systems Interconnection OSI model. The iSCSI protocol with the TCP IP protocol stack running in software requires a large amount of computing power especially at current 1 giga bits per second 1 Gbps and future 10 Gbps network link processing rates.

Hardware solutions as disclosed in the co pending patent application Ser. No. 10 620 076 offload the TCP stack processing to a hardware state machine based system or TCP Offload Engine TOE Adapter . However the hardware solution has time stamp migration problems from a host s TCP IP time stamp to the TOE adapter s time stamp during connection offload and upload especially when the initial TCP connection is established by the host TCP IP stack and then offloaded to the TOE adapter. The offloading in this context means that the TOE adapter processes the TCP IP stack in hardware using state machines instead of the software stack implementation in the host system. The host and the adapter time stamps vary and if the time stamp is not properly handled a TCP packet is not processed.

Therefore what is needed is a process and system that can handle the time stamp migration issues between a host system and a TOE adapter.

In one aspect a method for sending a TCP segment is provided. The sending method includes determining if a TCP port can be offloaded saving a host system s time stamp value replacing a host system s time stamp value with a TCP offload engine TOE adapter s time stamp value and sending the TCP segment via the TOE adapter.

In another aspect a method for receiving a TCP segment is provided. The method includes verifying if a TCP port is being offloaded by a host system to the TOE adpter retrieving the host system s time stamp value and inserting the host system s time stamp value in the received TCP segment before the forwarding the received TCP segment to the host system.

A system for exchanging TCP segments is provided. The system includes a server having an adapter for sending and receiving TCP segments and a host system having a TCP offload TOE adapter for processing a TCP IP stack in hardware wherein if a TCP port can be offloaded then the host system s time stamp value is saved and the host system s time stamp value is replaced with a TOE adapter s time stamp value before a TCP segment is sent via the TOE adapter.

This brief summary has been provided so that the nature of the invention may be understood quickly. A more complete understanding of the invention can be obtained by reference to the following detailed description of the preferred embodiments thereof concerning the attached drawings.

To facilitate an understanding of the preferred embodiment the general architecture and operation of a host system will be described. The specific architecture and operation of the preferred embodiment will then be described with reference to the general architecture.

TOE adapter includes a hardware implementation of a full network protocol stack. Application Programming Interfaces APIs to this protocol stack are made available to allow host software to take advantage of the hardware acceleration for straight network applications.

TOE adapter may also be based on a PCI development board with a Field Programmable gate Array FPGA or integrated into an Application Specific Integrated Circuit ASIC with an embedded serialize de serializer SERDES and internal programmable RAM.

Host includes a central processing unit CPU that is coupled to a system bus . CPU may be an Intel based microprocessor or any other type of processor and executes computer executable process steps. Storage media stores operating system program files application program files and other files. Some of these files are stored using an installation program. For example CPU executes computer executable process steps of an installation program so that CPU can properly execute the application program.

A random access main memory RAM also interfaces to computer bus to provide CPU with access to memory. When executing stored computer executable process steps CPU stores and executes the process steps out of RAM . Read only memory ROM is provided to store invariant instruction sequences such as start up instruction sequences or basic input output operating system BIOS sequences.

An I O device s interface allows host system to use various input output devices and peripherals. It is noteworthy that interface may have plural components to interface with plural devices. TOE adapter interface interfaces CPU with TOE adapter .

TOE Adapter includes a TCP Offload stack for processing TCP segments. The aforementioned patent application describes how TOE adapter processes the TCP segments via hardware. MAC layer interfaces with lower kernel interface when host TCP IP stack processes network packets.

In step S host referred to as client in the figures sends SYN packet with a host assigned time stamp. In step S server sends SYN ACK packet. In step S host sends an ACK packet using a host time stamp. In step S host sends a duplicate ACK using TOE adapter time stamp. The duplicate ACK is sent to open a TCP window. This occurs after the decision is made to offload the TCP IP stack processing.

In step S in response to step S server sends an ACK packet still using the host time stamp. In step S host sends 128 bytes of data using TOE adapter time stamp. Server drops this packet. In step S server sends an ACK packet still using the host time stamp and in step S server drops the packet that is sent from host .

If the port can be offloaded in step S then in step S the host TCP IP time stamp is stored. This stamp may be stored at any memory location that is accessible to CPU . In step S TOE adapter s time stamp is obtained from the TOE adapter and host s time stamp is replaced by TOE adapter s time stamp.

In step S the TCP window is zeroed out a checksum is generated in step S and the SYN segment is sent via TOE adapter in step S.

In step S a new TCP checksum is generated and the TCP segment is forwarded to the host. This allows the host to process the TCP segment.

If the port is offloaded in step S then in step S host inserts the TOE adapter s time stamp in the TCP header. The TCP window is zeroed out in step S and a new checksum is generated in step S. The ACK segment is then sent out in step S via adapter . The TCP connection is then offloaded to TOE adapter .

In one aspect time stamp differences between TOE adapter and host are efficiently managed to reduce the risk of packets being dropped.

Although the present invention has been described with reference to specific embodiments these embodiments are illustrative only and not limiting. Many other applications and embodiments of the present invention is apparent in light of this disclosure.

