---

title: Null-packet transmission from inside a firewall to open a communication window for an outside transmitter
abstract: A high-bandwidth direct communication path between two clients is used for voice or video calls over the Internet. An opening or a window in a firewall is made for the direct path by sending a null packet out from inside the firewall. The null packet can be a UDP packet directed to a UDP port of the other client. Initially, each client makes a TCP connection to port  of an external manager. Each client registers its UDP port number with the external manager. A call request from one client to the external manager results in a message from the external manager to the other client. The other client then creates the window in its firewall by transmitting the null UDP packet. Then the external manager is notified and tells the calling client to begin sending UDP packets directly to the other client through the firewall window.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08079072&OS=08079072&RS=08079072
owner: Google Inc.
number: 08079072
owner_city: Mountain View
owner_country: US
publication_date: 20050622
---
This application is a Continuation of U.S. application Ser. No. 09 682 084 filed Jul. 18 2001 now U.S. Pat. No. 6 978 383.

This invention relates to computer network communication software and more particularly to opening communications windows in firewalls.

The Internet enables communication among distant computers and local networks. Electronic mail web browsing instant messaging and video and audio streaming are common today. Using the Internet to complete telephone calls is possible using voice over Internet Protocol VoIP technology. Video messages may also be exchanged using enhancements to VoIP technology.

To protect local computers and networks from unauthorized use or even outright attack various security measures can be taken. A barrier between a local network and the Internet is often employed. This barrier is known as a firewall since it protects internal networks from the ravages of the open Internet.

 Firewall is a generic term that describes an array of different technologies for securing computer networks. Some common Firewall technologies are Packet Filters Proxy Servers Network Address Translation Port Address Translation and Application Protocol Filtering. Firewalls can be implemented in routers special firewall appliances and bastion hosts at the connection point of two or more computer networks. Personal firewalls are a software application running on a personal computer.

Firewalls can operate on different levels of the network. is a reference diagram for the Open Systems Interconnection OSI network model. Packets passing through a firewall can be filtered by examining their IP addresses TCP ports protocols states or other header criteria at network layer or transport layer .

Dynamic or stateful packet filters can operate on most of the layers. Only specifically configured traffic is allowed through the firewall such as web browser traffic that uses Transport Control Protocol TCP on port . All traffic from outside the firewall can be blocked except when a connection is opened from within the firewall. A temporary return path opening or window is created through the firewall for each connection initiated from the local network within the firewall. This window closes when the connection is closed.

For User Datagram Protocol UDP the temporary return path is closed when no traffic has flowed through the Dynamic Packet Filter for a configurable time period. Some firewalls allow traffic flowing in either direction to reset the timer while others allow only outbound packets to reset the timer.

Proxy servers can operate on layers or application layer . Clients behind the firewall connect to the proxy server which then makes another connection to the final server. Application protocol filtering can also operate on layer . Presentation layer and session layer are between the sockets of layer and the TCP connections of layer . Data link layer encapsulates the data into the actual packets or frames transmitted over the physical layer .

Firewalls can interfere with some Internet applications even preventing their use across firewalls. For example VoIP applications can be blocked by firewalls. illustrates how a firewall can block UDP packets for a VoIP application. Personal computer PC is protected by firewall while server or PC is directly connected to Internet .

Voice call applications prefer to use UDP rather than TCP to stream audio using less bandwidth. Separate ports can be used for each direction of the audio stream. For example audio from the user at PC can be sent over Internet to port of PC using the UDP protocol. Datagrams can pass through firewall since they originate from within inside firewall .

The reverse direction audio stream is sent from PC to a different port of PC . However when PC attempts to stream audio back to PC firewall blocks the UDP datagrams. Firewall sees these UDP datagrams as coming from Internet without a request from within PC the firewall. Firewall blocks these UDP datagrams assuming that they are unauthorized and possibly an attack on the local network.

While some firewalls such as personal firewalls can be configured to allow the incoming packets to enter from the outside Internet most firewalls cannot be configured by ordinary users. While some standard application traffic may be able to pass through firewalls such as web traffic using TCP to port other kinds of traffic such as UDP packets and for other arbitrary ports is often unconditionally blocked.

What is desired is a method for opening a window in a firewall to allow entry of audio or video streams originating from outside the firewall. A program that can open a firewall window is desired. Opening of firewalls for UDP datagrams or packets is especially desired to allow VoIP to operate across firewalls.

The invention is a computer product and a method for managing communication between users over a network when at least one user is connected to a network through a firewall. The product includes applications running on the users devices and an external manager application. The invention includes a provision for communication between the external manager and users over a channel which can pass through a firewall. User applications provide registration information including communication channel information to the external manager application at a time before communication between users is initiated. One user application requests communication with another user application by communicating the request to the external manager application. The external manager application provides the user applications with instructions to initiate and accept communications through a firewall on the communications channels registered with the external manager application such that the user applications use the instructions to establish communications with one another through a firewall.

In one aspect of the invention the network is the Internet. In one version the communication channel information includes IP address and port data.

In a preferred embodiment the communication channel between the users and the external manager is TCP IP protocol on a port accepted by a firewall and the communication channel between the users is UDP. In a version of this embodiment the type of communication between the users is VoIP.

The present invention relates to an improvement in voice over Internet Protocol VoIP through firewalls. The following description is presented to enable one of ordinary skill in the art to make and use the invention as provided in the context of a particular application and its requirements. Various modifications to the preferred embodiment will be apparent to those with skill in the art and the general principles defined herein may be applied to other embodiments. Therefore the present invention is not intended to be limited to the particular embodiments shown and described but is to be accorded the widest scope consistent with the principles and novel features herein disclosed.

External manager is on a server accessible from Internet . External manager can be accessed through a web site that PC and PC each connect to. Since web browsers use the Transport Control Protocol TCP and port firewalls are configured by default to allow incoming TCP packets to and from port although perhaps only when PC or PC first send a packet out to external manager and thus initiate a TCP connection from within the firewall.

A communication program such as VoIP prefers to make a direct connection using UDP between PC and PC . This reduces latency and thus optimizes voice quality. However firewalls do not allow UDP connections to be initiated from outside the firewall. Since TCP connections to external manager are allowed PC and PC first connect to external manager . External manager registers each PC by storing addresses and ports for the PCs in directory table . Keep alive messages are used to maintain the TCP connection.

When PC attempts to initiate a call to PC PC uses TCP port to send the call request to external manager . External manager then searches for the address and port information for PC in directory table . This information is used to send a message from external manager to PC .

PC can open a connection when registering and then periodically send a keep alive packet to external manager to maintain the connection.

Once PC receives the message from external manager it opens a window in firewall . External manager then notifies PC that it can now use this window to send UDP packets back to PC . The message from external manager specified the port to use for the window which is UDP port in this example. Since PC sends out a UDP packet over port from within firewall firewall creates an entry in its filter tables to allow UDP packets to pass through port to PC from Internet . The address of PC can also be also checked for incoming packets by firewall .

A window in firewall is opened when PC sends the first UDP packets to PC . Thus windows are opened in both firewalls . External manager acts as a third party message passing service telling both PC s which UDP port to use.

When requested by external manager PC and PC open windows in their firewalls for a port specified by external manager . In this example UDP port is used on PC while UDP port is used by PC . PC is instructed by external manager to send a UDP packet from its port to port on PC . This opens a window in firewall for incoming packets to UDP port from an external port .

UDP packets are streamed between PC port and PC port through the firewall openings. Since UDP is more efficient at transferring voice data than TCP a higher bandwidth is available for the call. UDP is more efficient than TCP because there is no 3 way handshake to establish a TCP connection in fact there is no formal connection no check for losses no re transmission and a lower packet header overhead. A direct connection is made for the voice traffic even though external manager is used to initiate the call.

Likewise PC registers with external manager by opening a TCP connection to port and sending its local UDP port . The UDP ports can be arbitrary ports and are sent along with other configuration information. Using arbitrary UDP ports allows for greater configuration flexibility and avoidance of conflicts with other programs running on a PC that may use UDP ports.

Since a TCP connection to port is made to external manager these request packets can pass through any local firewalls that protect PC or PC . As long as the PC s can browse the web which uses TCP the PC s can access external manager . Reply packets from external manager can also pass through the firewalls through windows that are automatically set up by the firewall when the PC first connects with external manager . For the most restrictive firewalls PCs could use port but many firewalls allow other arbitrary TCP ports to be used such as TCP port for PC and TCP port for PC .

When the user at PC wishes to communicate with the user at PC a call setup request is sent to external manager . The same TCP ports are used in the same connection as the registration. In this example the call request is contained in packet or packets that are sent to TCP port from port of PC . The call request from PC identifies PC as the called party.

External manager searches its directory table for more information on the called party PC and finds its IP address and TCP port . External manager sends a call notification request to this port of PC using a TCP connection. This call notification includes the UDP port of the calling party port as well as its IP address. The request may include other information or commands such as a command to open a window in its firewall .

PC may need to periodically open a new TCP connection to external manager to allow the request from external manager to pass through its firewall . For example PC can send a TCP packet every minute to external manager . Less restrictive firewalls may not require the periodic packet transmission from inside firewall .

A window in firewall must be opened to allow incoming UDP packets from PC to pass through firewall to PC . A null UDP packet is transmitted from PC to PC to open window in firewall . The null packet is sent from UDP port of PC to UDP port of PC . Since the packet originates from within firewall it is allowed to pass through firewall to the Internet.

Firewall typically stores the IP addresses and UDP ports of PC and PC and the protocol used UDP in a table. This table is consulted when an incoming packet is received from the Internet. When the incoming packet s protocol source and destination IP addresses and ports match an entry in the table the packet is allowed to pass through the firewall. Otherwise the packet is rejected and prevented from entering the local network. Thus an opening or window through the firewall is created when a table entry is stored. The table entry allows for a reply from the external Internet to the outgoing packet.

Other kinds of firewalls may store other information such as the originating application on PC a data link media access controller or Ethernet address. This alternate information can be used for matching packets or communications at different OSI levels from outside the firewall.

The null UDP packet from PC thus creates an entry in the table of firewall . This entry creates window allowing UDP packets to be transferred back and forth directly between PC and PC .

The UDP packet from PC is prevented from reaching PC since it is blocked by firewall as an un requested UDP packet from the outside Internet. Since the UDP packet is discarded by the other firewall it does not contain any important information. Ideally a null packet is used that contains no data. This minimizes the packet size and reduces bandwidth waste. Of course if firewall is permissive or absent the null packet can reach PC . Then PC simply discards the null packet.

Once the null packet has been sent by PC through firewall PC notifies external manager that window has been created. This firewall open reply is sent to TCP port of external manager from TCP port of PC . TCP port traffic can easily pass through firewall since it appears to be web browser traffic. The HTTP protocol may be used for the entire connection to satisfy restrictive application level firewalls.

External manager sends a reply to PC indicating that PC is now ready to stream UDP packets. The reply can contain the UDP port that PC uses port . This reply is sent from TCP port of external manager to TCP port of PC and can pass through firewall as it appears to be standard web traffic.

PC can now initiate a direct connection with PC using high bandwidth UDP packets. Such a direct UDP connection is ideal for multi media data such as audio voice video and binary data formats.

PC sends its first UDP packet from its port to port of PC . Since this UDP packet originates from the local network within firewall firewall opens window such as by creating a table entry that includes ports and and the address of PC .

This first UDP packet passes through window of firewall to the Internet where it is routed to firewall . Since the packet s ports and addresses match the table entry for window firewall allows the UDP packet to pass through window to the local network where it is routed to PC . Thus window opened by the null packet from PC is already set up before incoming packets arrive from PC .

Additional UDP packets can be sent from PC to PC over this path. Windows remain open for some time. Timers may close windows after some period of time with no packet flow or no outgoing packets from inside the firewall. However for most active 2 way communications packets occur with a frequency sufficient to maintain windows .

PC also sends UDP packets along this path using window in firewall to reach PC from outside firewall . Since these packets originate from inside firewall they are allowed to pass through and keep window open by resetting the packet timer. A field in the firewall table entry can be used to store the timer value.

The external manager sends a command to client B that tells client B to transmit a null packet to open a window in his firewall step . The destination port of the null packet is port A of client A which was provided by client A during registration. Client B then transmits a null packet to client A step . The firewall stores an entry for the outgoing packet causing a communication window to be opened for replies from client A.

Client B sends a message to the external manager confirming that the null packet has been sent step The firewall window should now be open ready to receive incoming packets from client A.

The external manager sends a message to client A step telling client A that the firewall should now be open. Client A can now go ahead and start direct communication with client B through the firewall opening. As client A begins this direct communication step an opening is created in any firewall protecting client A. Preferably UDP packets are used for the direct communication although other protocols could be used. Enhancements and extensions to UDP and derivatives of it may also be used as may similar high speed protocols.

Telephony Audio Services Interface TASI is a development environment that provides an application programming interface API for using library features or functions called by application . TASI can have a variety of services such as call control detecting placing and terminating calls between clients and audio stream control and formatting.

Interchange services corresponds to the OSI model transport layer. Interchange services provides packet transport using IP packets. Communication sockets in Windows socket sub system can be opened by Interchange services to send and receive IP packets containing audio or video data to a remote client over the Internet. Of course socket sub systems other than Windows can be substituted.

Multi function resource can be implemented in hardware or software or both. Multi function resource provides a host based software layer that performs a variety of functions. Multi function resource can perform digital signal processor DSP functions such as voice compression echo cancellation bad frame interpolation for late or lost packets silence compression voice activity detection and comfort noise generation. In addition multi function resource provides the ability for playing wave files on multimedia subsystem . Multi function resource has three main subsystems the voice compression subsystem the packetization subsystem and the voice quality subsystem.

Windows multimedia subsystem contains the operating system drivers and low level components that communicate with the hardware such as a sound card or audio subsystem. Speakers and a microphone or other multi media devices can be connected to the hardware controlled by multimedia subsystem .

The header has a cyclical redundancy check CRC field for error detection and a reserved field. The destination or end point identifier of the communication call connection of the other PC and the identifier of the sending PC are included. These are internal identifiers of the software that is handling the source or destination side of the call.

For null packets the payload size is set to zero since there is no data. The message ID field is set to indicate that the packet is a null packet.

When a connection is closed by a FIN packet or times out a new SYN ACK sequence is needed to open a new TCP connection. UDP packets are connection less and do not require the SYN ACK handshake. UDP is an alternative to TCP. UDP also uses IP to send a datagram over a network and is sometimes referred to as UDP IP. UDP does not provide sequencing of the packets. The application program using UDP must be able to sequence datagrams and verify the integrity of the datagrams as they are received. Network applications can save processing time with UDP since very small data units can be exchanged with little message re assembly required.

UDP provides two services not provided by the IP layer. It provides a port number to help distinguish different user requests and optionally checksum capability to verify that the data arrived intact.

PC registers with external manager by sending its UDP port in a TCP connection to port of external manager . Likewise PC registers its UDP port .

Some time later PC attempts to call PC by sending a message to port of external manager . External manager sends a message to PC with the IP address and UDP port to send the null packet to port of PC .

PC generates a null UDP packet and transmits it to port of PC . Firewall stores the addresses and UDP ports creating window for future use. Since there is no firewall protecting PC the null packet is received by PC . The null packet contains no data so it is ignored or discarded by PC .

PC then messages to port of external manager that it has sent the null packet to open the firewall. External manager sends a message to PC that communication can now be established with PC . The UDP port of PC port is also sent to PC .

PC can then begin sending UDP packets from its port to port of PC . Firewall allows these packets to pass through to PC since window has already been opened. UDP packets can be sent in the reverse direction from PC to PC using the same pair of UDP ports. Thus 2 way voice or video communication is facilitated by a direct full duplex UDP link between PCs .

Several other embodiments are contemplated by the inventors. For example other ports and protocols may be used. Separate port pairs may be used for each direction of packet flow and more than 2 client endpoints may share a packet stream. Multicasting may also be employed. Additional windows may be opened in the firewall to allow for multiple calls to different PC s. The order of the various steps may be changed and additional steps can be included. The external manager can operate on a variety of ports such as ports and . Rather than periodically send keep alive messages PC could periodically open a connection to external manager such as once every minute. A new connection could be made if some time has passed since registration. A list of several alternate UDP ports can be sent rather than a single port.

The client or PC may be a portable computing device such as a personal digital assistant PDA palm computer enhanced cell phone Internet appliance or other computing device rather than just a standard desktop or laptop PC. Operating systems other than Windows such as Linux Unix and MacOS may be used for the PC. The external manager can reside on a server that runs many applications including web server applications. Software routines may be stored on disks or other media or may be programmed as firmware or programmable logic or even converted to partial or full hardware implementations.

The invention has been described in an embodiment of two clients directly communicating with one another such as for making VoIP calls whether audio only or with video. The invention can also be applied to other peer to peer communications such as for file sharing systems. One of the two clients may act as a server rather than a peer or client.

The abstract of the disclosure is provided to comply with the rules requiring an abstract which will allow a searcher to quickly ascertain the subject matter of the technical disclosure of any patent issued from this disclosure. It is submitted with the understanding that it will not be used to interpret or limit the scope or meaning of the claims. 37 C.F.R. 1.72 b . Any advantages and benefits described may not apply to all embodiments of the invention. When the word means is recited in a claim element Applicant intends for the claim element to fall under 35 USC 112 paragraph 6. Often a label of one or more words precedes the word means . The word or words preceding the word means is a label intended to ease referencing of claims elements and is not intended to convey a structural limitation. Such means plus function claims are intended to cover not only the structures described herein for performing the function and their structural equivalents but also equivalent structures. For example although a nail and a screw have different structures they are equivalent structures since they both perform the function of fastening. Claims that do not use the word means are not intended to fall under 35 USC 112 paragraph 6. Signals are typically electronic signals but may be optical signals such as can be carried over a fiber optic line.

The foregoing description of the embodiments of the invention has been presented for the purposes of illustration and description. It is not intended to be exhaustive or to limit the invention to the precise form disclosed. Many modifications and variations are possible in light of the above teaching. It is intended that the scope of the invention be limited not by this detailed description but rather by the claims appended hereto.

