---

title: System and method for integrated header, state, rate and content anomaly prevention for domain name service
abstract: The present invention provides an integrated prevention of header, state, rate and content anomalies along with network policy enforcement for domain name service (DNS). A hardware-based apparatus helps identifying DNS rate-thresholds through continuous and adaptive learning. The apparatus can determine DNS header and DNS state anomalies and drop packets containing those anomalies. DNS queries and responses are inspected for known malicious contents using a Content Inspection Engine. The apparatus integrates advantageous solutions to prevent anomalous packets and enables a policy based packet filter for DNS.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07626940&OS=07626940&RS=07626940
owner: IntruGuard Devices, Inc.
number: 07626940
owner_city: Sunnyvale
owner_country: US
publication_date: 20050620
---
This is a continuation in part application of the U.S. patent application Ser. No. 11 021 637 filed Dec. 22 2004 entitled SYSTEM AND METHOD FOR INTEGRATED HEADER STATE RATE AND CONTENT ANOMALY PREVENTION WITH POLICY ENFORNCEMENT which is incorporated herein by reference. This application also relates to a co pending U.S. patent application Ser. No. 10 759 799 filed Jan. 15 2004 entitled METHOD AND APPARATUS FOR RATE BASED DENIAL OF SERVICE ATTACK DETECTION AND PREVENTION which is incorporated herein by reference.

The present invention relates generally to intrusion prevention and more particular to a system and method for the prevention of denial of service attacks on Domain Name Service DNS .

Intrusion prevention appliances have been widely available in the last few years. Published U.S. Patent Application Numbers 20030004688 20030004689 20030009699 20030014662 20030204632 20030123452 20030123447 20030097557 and 20030041266 disclose systems methods and techniques that primarily focused on content header and state anomaly based intrusion prevention. Denial of Service attack prevention systems have also been dealt in the literature. Published US Patent Application Numbers 20030076848 20030110274 and 20030070096 and 20020083175 disclose systems that prevent denial of service attacks or spoofed DNS messages.

As one skilled in the art knows internet attacks have been growing in complexity and have been more wide spread due to a variety of readily available attack toolkits. Many of the recent DoS or DDoS attacks have been on the DNS servers. By overloading the DNS servers the attackers can easily deny access to the associated web service or other related internet services. Clearly a new method and system is needed to protect DNS servers from getting flooded with unwanted and illegitimate requests. The present invention addresses this need.

While it is impossible to predict the behavior of all types of future attacks current trends in attacks lead to certain known categories of attacks viz. pre attack probes header anomalies state anomalies rate anomalies and content anomalies.

The present invention provides a single appliance that integrates solutions to these different anomalies and provides an integrated solution to the rate based denial of service attacks especially on the Domain Name Service.

The new appliance described herein provides copper and optical connectivity. A Packet Interface block interfaces with external network through a PHY and a MAC device and buffers packets until a decision has been made about them.

A Classifier interfaces with Packet interface to classifier. The Rate Anomaly Meters receive classifier output and maintain the instantaneous packet rates and compare against the thresholds set adaptively and continuously by the controlling host.

If the specific type of packets exceeds the rate threshold packets of that type or belonging to that group are discarded for a certain time period.

The anomaly engines drop packets that have header or state anomalies in different layers of protocol.

A fragment reassembly engine reassembles any fragments according to processes well known in the art. Assembled or un fragmented packets are then sent to an engine that removes any reordering issues or retransmission anomalies for TCP packets.

Ordered TCP as well as non TCP packets are then sent to relevant protocol normalization engines. The derived layers 2 3 4 and 7 header parameters and state information are then used by the Multi rule search engine to find a rule set that matches the incoming packet.

A rule matching engine drives the content inspection engine to validate if contents of the packet match any of the anomalous signatures. A Stateful sub rule traversal engine then validates if further contents of the packet meet sub signatures of the rule.

If a rule match is found it is added to the event queue corresponding to the packet. A packet may match multiple rules.

After all the rules matches have been performed a decision multiplexer picks the highest priority rule match and informs the MAC interface whether to let the packet through or to drop the packet. Allowed packets are then sent out.

An object of the present invention is to provide a high rate hardware based integrated system and method of preventing network packets across the packets having

Another object of the system is to provide a DNS classifier that is capable of classifying TCP and UDP based DNS packets and components of DNS protocol headers.

Still further object of the system is to provide a DNS Rate Anomaly Engine capable of continuously calculating the traffic rate on classified DNS parameters and estimating the traffic rate thresholds adaptively and thus determining the threshold violations on domain name service parameters such as queries and responses.

Another object of the system is to provide a DNS State Anomaly Engine that can selectively drop excessive packets during rate based floods.

Yet another object of the system is to provide a DNS State Anomaly Engine that can validate DNS responses and that can drop them if there is no previous corresponding query associated with them.

Still another object of the system is to provide a DNS State Anomaly Engine that can drop certain DNS queries that are coming within the Time to Live period during DNS query floods from the same sources to the same destinations.

Another object of the system to use cached response if available rather than letting the query go to the Domain Name Server during DNS query floods.

Still another object of the system is to provide a method to determine any known content patterns of intrusion in domain name service protocol packets.

Still another object of the invention is to provide a method to determine any known policy violations on domain name service.

Still further objects and advantages of the present invention will become apparent to one skilled in the art upon reading and understanding the preferred embodiments described below with reference to the following drawings.

The present invention provides an integrated intrusion prevention solution for DNS related attacks. A single hardware based appliance integrates a plurality of mechanisms to prevent different anomalies and enables a policy based packet filter.

Network inbound packets enter the apparatus and exit as cleansed inbound packets . Similarly network outbound packets enter the apparatus and exit as cleansed outbound packets . The dropped packets make the difference between packets at ingress and at egress. For the purpose of forensic analysis these dropped packets are routed to two forensic ports viz. the Dropped Inbound Packets and the Dropped Outbound Packets .

Packets entering the system are buffered in the Packet Interface block . A copy of these packets is passed to the Classifier which passes on the header and other relevant information over the Classification bus to the subsequent blocks for decision making. The Packet Interface block receives a multiplexed decision about each packet buffered within and either allows the packets or drops the packets. The drop packets are optionally copied to the forensic ports and .

The decision making operation of determining which packets need to be dropped is handled by the four major blocks viz. the Header and State Anomaly Prevention the Rate Anomaly and Reconnaissance Prevention the Content Anomaly Prevention and the Policy Lookup Engine . They send the results to the Decision Multiplexer via the Decision bus .

A controlling host uses the Host Interface to read the controlling parameter and set the parameters of different blocks via the Host Interface Bus . The controlling host also reads events related to policy violations and anomalies. In some embodiments these events are subsequently logged and or analyzed.

The Header Anomaly Prevention block within prevents packets that have layers 2 3 4 and 7 header anomalies according to protocols under consideration. For example in an exemplary embodiment of this invention layer 3 header anomaly prevention looks for packets that are marked IPV4 packets in layer 2 header but do not have version 4 in the IP header. Similarly besides other anomalies layer 4 header anomaly prevention block looks for TCP packets that have illegal flag combinations such as SYN and FIN set together. In an exemplary embodiment of this invention the layer 7 header anomaly prevention block looks for anomalous behavior such as non DNS traffic destined for port .

The State Anomaly Prevention block within prevents packets that violate standard state transitions in protocols. In an exemplary embodiment of this invention the layer 4 state anomaly prevention block prevents packets that do not belong to any established connection and have ACK bit on in the TCP flags. In an exemplary embodiment of this invention the layer 7 state anomaly prevention block can optionally prevent DNS response packets that are arriving without the corresponding DNS query.

The Continuous and Adaptive Rate Anomaly Prevention block within prevents instantaneous rate anomaly as detected through continuous and adaptive learning. In an exemplary embodiment of this invention rate anomalies at network layers 2 3 4 and 7 are to be detected and prevented by this block. In an exemplary embodiment of this invention DNS Query rate anomaly is prevented by detecting DNS Query packets exceeding their adaptively learnt threshold in a given direction.

The Reconnaissance Prevention block within prevents reconnaissance recon activities. In an exemplary embodiment of this invention as an example one of the recon prevention schemes is implemented utilizing a port scan counter.

The Content Anomaly Prevention block prevents packets that match known signature of attacks in the application content of the packet. In an exemplary embodiment of this invention these rules consist of signatures in the packet anywhere or within specifically parsed areas of the packets such as a DNS protocol payload. In an exemplary embodiment of this invention the Content Anomaly Block looks for a string CD 80 E8 D7 FF FF FF bin sh to determine a DNS Exploit called named overflow . In another exemplary embodiment of this invention necessary packet normalization for accurate content inspection is supplemented with processing such as fragment reassembly TCP assembly reordering retransmission removal etc. The purpose of such normalization is to send normalized packets for content inspection.

The Policy Lookup engine prevents packets that violate the network policies set by an administrator. In an exemplary embodiment the policies are set by the administrator and include rules that allow or deny packets based on interface source IP address destination IP address IPV4 or IPV6 protocol source port destination port and or ICMP type and code. In an exemplary embodiment for DNS protocols policies are available for a user to allow or deny packets with specific DNS parameters such as queries responses or specific values of QDCount ANCount NSCount ARCount etc.

The Decision Multiplexer block receives decisions from decision making blocks and over the Decision bus combines them as a single decision and forwards them to the Packet Interface block .

The controlling host can read the control registers and set them to manage the functionality of different components. The controlling host can periodically read the maximum packet rates of different types of packets to come up with an adaptive threshold and program them using the Host Interface Block . The Host Interface Block accesses other blocks through the Host Interface Bus . The controlling host can also read the statistics related to packets being dropped due to anomalies or policy violation. The controlling host can then use this data for logging and analysis. In an exemplary embodiment the controlling host can read the maximum packet rates for DNS Query packets or response packets in two directions and set the adaptive thresholds for them through the Host Interface Block .

The Classifier is further illustrated in detail through the Layer 2 Classifier the Layer 3 Classifier the Fragment Reassembly Engine the TCP Reorder Processing and Retransmission Removal Engine the Layer 4 Classifier the Layer 7 Classifier and the Protocol Normalization Engine .

The Layer 2 Classifier receives frames from Packet Interface and classifies packets based on their layer 2 characteristics. It parses the layer 2 headers and passes that information to subsequent logic blocks over the Classification Bus . In an exemplary embodiment of this invention this block can parse Ethernet frames and IEEE 802.2 3 frames and can determine ARP RARP Broadcast Multicast non IP VLAN tagged frames and double encapsulated VLAN tagged frames.

The Layer 3 Classifier receives packet data as well as layer 2 classifier information from the Layer 2 Classifier . It extracts the layer 3 header information in IPV4 and IPV6 headers and passes it on to the subsequent logic over the Classification Bus . In some embodiments of this invention the Classifier parses IPV4 and IPV6 packets and determines properties such as TOS IP Options fragmentation and protocol.

The Fragment Reassembly Engine receives layer 3 header information from the Layer 3 Classifier as well as the packet data. In cases where the Layer 3 Classifier informs that this packet is a fragmented packet the Fragment Reassembly Engine requests the Packet Interface Block to hold the packet. It also informs subsequent blocks not to inspect especially tagged fragmented packets as they are not yet assembled. It stores the information about fragments in its internal data structures related to reassembly. Packets that are not fragmented are passed through. A timeout based mechanism is then used to wait until all the fragments that belong together have been received. An ager based mechanism periodically wakes up and determines whether some fragments are over age and discards them from memory.

Once the Fragment Reassembly Engine determines that all fragments corresponding to one datagram are in order and do not violate any fragmentation related anomalies it requests the Packet Interface Engine to re release them in order. These packets are then passed through the subsequent blocks in order for further inspection. The Fragment Reassembly Engine therefore guarantees that blocks subsequent to it always receive datagram fragments in order.

The Fragment Reassembly Engine also determines whether there are fragmentation related anomalies and if so marks those packets as invalid and informs the decision to the Decision Multiplexer over the Decision Bus . The techniques necessary to achieve fragment assembly as well as fragmentation related anomaly prevention are well known to those skilled in the art and thus are not further described herein. The allowed assembled packets leave as original unmodified packets with their own packet ID but they leave the Fragment Reassembly Engine in order so that subsequent blocks can inspect the content in order.

The Layer 4 Classifier similarly parses the layer 4 information from packets that are guaranteed to be in order with respect to fragmentation. In an exemplary embodiment this classifier looks at TCP UDP ICMP IPSec ESP and IPSec AH headers. This information is passed to the subsequent blocks over the Classification Bus . In an exemplary embodiment of this invention this classifier can parse layer 4 information such as TCP Options TCP ports UDP Ports ICMP types codes TCP flags sequence numbers ACK numbers etc. Packets that are anomalous are dropped.

The TCP Reordering Processing and Retransmission Removal Engine receives classified packets from the Layer 4 Classifier . It only monitors TCP packets and it passes the rest further to subsequent blocks for further inspection. It creates connection states in memory tables and ensures that packets follow well known TCP state transitions. Packets that are anomalous are dropped through a decision sent over the Decision Bus to the Decision Multiplexer . Preferably this block further checks whether the packet s TCP sequence number is in order and within the receiver s window. Packets that are outside the window are dropped through the Decision Multiplexer . Packets that are in order and not retransmissions are passed through.

For all packets within the window that have not been acknowledged yet a CRC based checksum is saved as part of the state for the connection. It requests subsequent blocks not to inspect the packets which are out of order. It holds data structure related to such packets in memory. For every such packet stored in memory a self generated ACK is sent to the sender to facilitate quicker reordering. A timeout based mechanism is then used to wait until expected sequence number arrives for the connection. An ager based mechanism periodically wakes up and determines whether some packets are over age and discards them from memory. The ordered packets are then passed through the subsequent blocks in order for further inspection. This way the subsequent blocks can always assume that TCP packets will always be in order.

The TCP Reordering Processing and Retransmission Removal Engine also determines whether there are retransmission related anomalies and if so marks those packets as invalid and informs the decision to the Decision Multiplexer over the Decision Bus . Retransmission anomalies are determined using the stored CRC based checksum. Retransmitted packets that are equal or larger than the previous transmission can be determined to be anomalous through a CRC comparison. Retransmissions that are smaller than earlier transmission are discarded. The techniques necessary to achieve TCP reordering as well as retransmission related anomaly prevention are well known to those skilled in the art and thus are not further described herein. The allowed ordered packets leave as original unmodified packets with their own packet ID but they leave the engine in order so that subsequent blocks can inspect the content in order.

The Layer 7 Classifier receives ordered fragments of IP datagrams ordered TCP packets specially flagged TCP retransmissions and other packets and parses layer 7 header information. In an exemplary embodiment of this invention this block parses headers of protocols such as FTP HTTP TELNET DNS SMTP POP RPC etc. It does so using stateful parsing techniques well known to those aware of the art.

In an embodiment of this invention the FTP classifier within determines the commands and replies being used in the FTP packets. Commands parsed include USER PASS ACCT CWD CDUP SMNT REIN QUIT PORT PASV TYPE STRU MODE RETR STOR STOU APPE ALLO REST RNFR RNTO ABOR DELE RMD MKD PWD LIST NLST SITE SYST STAT HELP NOOP. 3 digit reply codes are parsed as well and grouped as positive and negative.

In an embodiment of this invention the HTTP classifier within determines the requests and replies being used in the HTTP packets. Requests are parsed as Method Request URI Request Header Fields and HTTP Version. The Method is further classified as OPTIONS GET HEAD POST PUT DELETE TRACE CONNECT and extension methods. The request URI is isolated and passed further. Request Header Fields such as Accept Charset Accept Encoding Accept Language Authorization Expect From Host If Match If Modified Since If None Match If Range If Unmodified Since Max Forwards Proxy Authorization Range Referer TE User Agent. 3 digit status codes are parsed as well and grouped as positive and negative.

In an embodiment of this invention the TELNET classifier within determines the telnet commands. The commands classified are SE NOP Data Mark Break Interrupt Process Abort Output Are you there Erase character Erase line Go ahead SB WILL Won t Do Don t and IAC.

In an embodiment of this invention the TELNET classifier within determines the telnet commands. The commands classified are SE NOP Data Mark Break Interrupt Process Abort Output Are you there Erase character Erase line Go ahead SB WILL Won t Do Don t and IAC.

In an embodiment of this invention the DNS classifier within parses the DNS queries. The parser breaks the DNS message into Header Question Answer Authority and Additional sections. The header is further parsed to determine whether the message is a query response or some other code. The Question section is further parsed as QNAME QTYPE and QCLASS. The Answer section is further classified as resource record RR consisting of Domain Name Type Class TTL and Resource data length.

In an embodiment of this invention the SMTP classifier within parses the SMTP commands and replies. The commands are further parsed as EHLO HELO MAIL RCPT DATA RSET VRFY EXPN HELP NOOP and QUIT. Replies are further decoded as positive and negative.

In an embodiment of this invention the POP classifier within parses the POP commands and responses. The commands are further parsed as USER PASS APOP QUIT STAT LIST RETR DELE NOOP RSET TOP UIDL and QUIT. Responses are further decoded as positive and negative.

In an embodiment of this invention the RPC classifier within parses the RPC message. The message is parsed as transaction id followed by the call or reply. The call is further parsed as RPC version program number version number procedure and the rest of the call body. The reply is further parsed as accepted or denied.

Protocol Normalization Engine receives classified packets and normalizes the parsed data so that it can be inspected for content anomalies. In a preferred embodiment of the invention the normalization is done for URI portion of the within HTTP. The normalizations include Hex encoding Double Percent Hex encoding Double Nibble Hex Encoding First Nibble Hex Encoding Second Nibble Hex Encoding UTF 8 Encoding UTF 8 Bare Byte Encoding Unicode Microsoft U encoding Alt Unicode Double encode IIS Flip Slash White space etc. In a preferred embodiment of this invention the normalization is done for RPC records by consolidating records broken into more than one record fragment into a single record fragment. In a preferred embodiment of this invention the TELNET protocol normalization removes negotiation sequences. This normalization prunes negotiation code by copying all non negotiation data from the packet. In a preferred embodiment of this invention the TELNET normalization is also performed on the FTP packets.

The Continuous and Adaptive Rate Anomaly block within is further illustrated in the Layer 2 Rate Anomaly Meters the Layer 3 Rate Anomaly Meters the Layer 4 Rate Anomaly Meters and the Layer 7 Rate Anomaly Meters . The meters and continuously and adaptively determine rate thresholds for layers 2 3 and 4 network parameters and determine whether flood is occurring for any of the parameters. A controlling host uses the Host Interface to learn the rate and set the threshold. All the meters support a two way communication with the host through the Host Interface Bus . The above referenced co pending U.S. patent application Ser. No. 10 759 799 entitled METHOD AND APPARATUS FOR RATE BASED DENIAL OF SERVICE ATTACK DETECTION AND PREVENTION discusses in detail how rate based denial of service attacks can be prevented using a continuous and adaptive learning approach for layers 2 3 and 4 based attacks.

The Layer 7 Rate Anomaly Meters continuously and adaptively determine rate thresholds for layer 7 network parameters and determine whether flood is occurring for any of the parameters. In an exemplary embodiment the apparatus can detect and prevent application layer floods such as HTTP Request Type Floods HTTP Failure Floods FTP Request Floods FTP Failure Floods DNS Query Floods DNS Response Floods.

According to the invention a DNS Query Rate Anomaly Meter prevents DNS query transactions from being used more often than the previously observed threshold. The Host Interface Bus is used to inform the controlling host via the Host Interface of the continuous rates being learnt so that the controlling host can adaptively set the thresholds for layer 7 Rate Anomaly Meters .

The Recon Prevention sub block within is further illustrated in the Layer 3 Recon Prevention sub block within and the Layer 4 Recon Prevention sub block within . The Layer 3 Recon Prevention sub block within prevents reconnaissance activity at layer 3. In an exemplary embodiment of this invention this block prevents IP address scanning using information received from the layer 3 classifier and determines whether a single source is connecting to many IP addresses within a short interval. In another embodiment of this invention this block prevents dark address scanning using information received from the layer 3 classifier and determines whether a source is scanning unused IP address ranges.

The Layer 4 Recon Prevention sub block within prevents reconnaissance activity at layer 4. In an exemplary embodiment of this invention this block prevents port scanning using information received from the layer 3 and layer 4 classifiers and determines whether a single source is connecting to many layer 4 TCP UDP ports within a short interval.

The Header and State Anomaly Prevention block within is further illustrated in the Layer 2 Anomaly Engine the Layer 3 Anomaly Engine the Layer 4 Anomaly Engine and the Layer 7 Anomaly Engine . The Engines and receive corresponding classifier outputs over the Classification Bus and determine whether the header has any anomaly or whether the state transition due to header values leads to anomalies. The packets determined to be anomalous are dropped via a decision sent over the Decision Bus to the Decision Multiplexer .

In some embodiments the Layer 3 Anomaly Engine detects and prevents IPV4 packets that have one or more of the following anomalies 

In some embodiments the Layer 3 Anomaly Engine detects and prevents IPV6 packets that have one or more of the following anomalies 

In some embodiments the Layer 3 Anomaly Engine also prevents fragmented packets that have over assembly related anomalies as detected by Fragment Assembly Engine .

In some embodiments the Layer 4 Anomaly Engine detects and prevents TCP packets that have one or more of the following anomalies 

In some embodiments the Layer 4 State Anomaly Engine detects and prevents UDP packets that have one or more of the following anomalies 

In some embodiments the Layer 4 State Anomaly Engine detects and prevents TCP packets that violate valid state transitions that are expected by standard TCP state machines. For this purpose it receives information from the Layer 4 Classifier and the TCP Reorder Processing and Retransmission Removal Engine . Packets that are outside the receiver s window as maintained by the state table are also dropped for being anomalous. Retransmitted packets that are determined by the Retransmission Removal engine to be different from the original transmission are also dropped by the Layer 4 State Anomaly Engine .

In some embodiments the Layer 7 Anomaly Engine prevents state transition anomalies at layer 7 protocols such as HTTP e.g. the GET keyword for request method must be followed by a URI. Similarly the FTP protocol Anomaly Engine within can identify requests that are within the allowed requests as defined in the RFC. In an exemplary embodiment of this invention the DNS anomaly engine can prevent a DNS response without an associated DNS query. It can prevent DNS queries during rate floods that are coming from the same source within the TTL period of previous valid DNS response.

The Content Anomaly Prevention block is further illustrated via its sub components Multi Rule Search Engine Rule Matching Engine Stateful Sub rule Traversal Engine Event Queuing Engine and Content Inspection Engine . The Multi rule Search Engine gets classification information from the Classification Bus . Part of this information viz. Interface Source IP Address Destination IP Address Protocol Source Port and Destination Port is used to first search through a search engine to determine whether the packet violates any policies. If so the packet is dropped through a decision conveyed over the Decision Bus to the Decision Multiplexer .

If the search matches certain rules and requires further content inspection the Rule Matching Engine sends the assembled ordered normalized data to the Content Inspection Engine . An external host loads the contents of the BRAM SRAM and DRAM of the Content Inspection Engine with necessary signatures corresponding to the rule sets through the Host Interface over the Host Interface Bus .

The Content Inspection Engine can start the initial state at a specific point where the last match for the previous packet had occurred. This helps in statefully matching the strings across packets.

Once the Rule Matching Engine determines via the Content Inspection Engine that the packet matches at least one of the signatures it needs to statefully walk through all the optional sub signatures within the rule. The statefulness is required because the signatures may be split across fragmented packets or reordered packets. For this purpose the state of the last match where it was left is kept in the memory for the specific connection.

Once all signatures are found to be present in the packet the rule is said to be matched. Such a match is denoted as an event. This event is queued against the packet s ID in the Event Queuing Engine .

A packet may match multiple such events. A priority scheme within the Event Queuing Engine picks the highest priority event from the determined events for the packet and informs the corresponding decision to the Decision Multiplexer over the Decision Bus .

Blocks such as and inform of their decision whether to drop the packet or not to the Decision Multiplexer .

In an exemplary embodiment the DNS classifier classifies all DNS packets over TCP or UDP by parsing them in detail. The DNS Classifier identifies TCP UDP DNS packets based on destination port it classifies them into DNS queries and responses identifies Question and Answer Resource Records RRs Authority RR fields and Additional RR fields.

In an exemplary embodiment the DNS Rate Anomaly Meter detects rate anomalies for the following DNS packets 

The rate anomaly determination is done using continuous learning of rates which are passed to the host through the Host Interface . The host sets adaptive thresholds for the above floods.

The DNS Header Anomaly Engine takes classified data from the DNS Classifier and determines well known anomalies such as following 

The DNS State Anomaly Engine takes classified data from the DNS Classifier and maintains statefulness in the state transitions. In an embodiment the following state transition anomalies are determined 

The Multi rule Search Engine Rule Matching Engine Stateful Sub rule Traversal Engine Event Queuing Engine and Content Inspection Engine work on the data received from the classifiers including DNS Classifier to determine content anomalies through searching patterns of known intrusions on DNS service.

Flowchart illustrates DNS parsing over User Datagram Protocol UDP . This is performed within the DNS Classifier . If a UDP packet has a source or destination port equal to 53 it is considered for further parsing. All other packets are ignored by this block and are marked OK. Based on the positions the Transaction ID XID QDCount ANCount NSCount and ARCount are extracted per RFC. If the packet turns out to be a DNS query it is parsed as a query otherwise it is parsed as a response. This is further illustrated in .

Flowchart illustrates DNS parsing over Transmission Control Protocol TCP . This is performed within the DNS Classifier . TCP state for the connection is queried and if the TCP connection has destination port equal to 53 it is considered for further parsing. All other packets are ignored by this block and are marked OK. Only connections that are established will have data in the layer 7. Until the connection establishment the packets are ignored for further layer 7 parsing. Length is determined for the DNS packet based on the RFC. Based on the positions the Transaction ID XID QDCount ANCount NSCount and ARCount are extracted per RFC. If the packet turns out to be a DNS query it is parsed as a query otherwise it is parsed as a response. This is further illustrated in .

Every DNS packet has questions and resource records RRs illustrates via two flowcharts and the parsing of Questions and RRs done within the DNS Classifier . Flowchart illustrates how Questions are parsed and flowchart illustrates how RRs are parsed.

Flowchart shows how the QDCount determined by the classifier is used. If it is non zero questions are present. For QDCount times the questions are parsed. For every question the QName Qtype and QClass are parsed and passed on to further meters and engines.

Flowchart shows how the ANCount NSCount and ARCount determined by the classifier are used. If they are non zero RRs are present. For the corresponding count times the resource records are parsed. For every resource record the Type Class RDLength and RData are parsed and passed on to further meters and engines.

During the above parsing within the DNS Classifier some of the information generated is useful for determining header anomalies mentioned earlier. That information is passed on to DNS Header Anomaly Engine .

DNS State Anomaly Engine consists of a Packet Processing Engine a Memory Interface a Host Interface Processor an Ager and three memory based tables viz. State Machine Table TTL Table and Query Response Cache Table .

The Packet Processing Engine interfaces with Classifiers including the DNS Classifier on one end and the Decision Multiplexer on the other end. It decides whether a given packet should be allowed or dropped based on state of the system and several other factors discussed below.

The Memory Interface allows controlled shared and prioritized access to a high speed memory to the Packet Processing Engine the Host Interface Processor and the Ager .

The Host Interface Processor allows the controlling host to control the parameters within the Packet Processing Engine and read the statistics as well as initialize and manage the memory tables and .

The Ager is capable of performing a timer based aging of the memory tables and . This is further described below.

Table 1 describes the memory table . The key components of the table include a tuple consisting of Source IP the Transaction ID XID and the Source Port SPORT .

The DNS TTL Table shown in Table 2 is indexed using a tuple consisting of the Source IP Destination IP DIP Record Type and the CRC of name. This tuple can subsequently be used during rate based floods to validate another query coming form the same source to the same destination for the same record during the time to live TTL period.

The DNS Query Response Cache Table shown in Table 3 is indexed using a tuple consisting of the Name Type and Class in response. This tuple can subsequently be used during rate based floods to provide a response from the cache corresponding to a matching query coming for the same record. This avoids overloading the DNS server during the flood.

Preferably all three tables are implemented using hashed indexes and collision pointers. Those skilled in the art can easily appreciate such implementations. Therefore they are not further described herein in details.

The Ager comprises a background process that runs every second. The background process periodically reads the above three tables. For every entry it compares the time out value with the free running second tick counter. If the time out is over the entry is deleted. This ensures that stale entries do not populate the table. In some embodiments the Ager also collects statistics related to entries in the tables and sends them to host through the Host Interface Processor .

If the corresponding query is not found and the setting for state anomalies prevents passage of such packets the packet is dropped through a decision passed through the Decision Bus to Decision Multiplexer .

If the response is not an error response an entry is added into the DNS TTL table Table 2 and the response is added into the DNS Query Response Cache table Table 3 for subsequent use.

First the SIP DIP record type and CRC of name are used to find the corresponding tuple in Table 2. If the corresponding query is found and the setting for TTL state anomalies prevents passage of such packets the packet is dropped through a decision passed through the Decision Bus to Decision Multiplexer . If the anomalies are allowed the packet is forwarded.

If the query is not found in the TTL table the same source has not requested the same query during the TTL period and hence the response can be provided from the cache if it is present there. A search is made through the cache in Table 3. If the query is not present in the cache the query is forwarded further to the destination.

The methods described above lead to the reduction of queries and responses reaching the DNS servers and thus advantageously reduce the load on the DNS servers during rate based floods.

Although the present invention and its advantages have been described in detail it should be understood that the present invention is not limited to or defined by what is shown or discussed herein.

Moreover as one skilled in the art will appreciate any digital computer systems can be configured or otherwise programmed to implement the methods and apparatuses disclosed herein and to the extent that a particular digital computer system is configured to implement the methods and apparatuses of this invention it is within the scope and spirit of the present invention. Once a digital computer system is programmed to perform particular functions pursuant to computer executable instructions from program software that implements the present invention it in effect becomes a special purpose computer particular to the present invention. The techniques necessary to achieve this are well known to those skilled in the art and thus are not further described herein.

Computer executable instructions implementing the methods and techniques of the present invention can be distributed to users on a computer readable medium and are often copied onto a hard disk or other storage medium. When such a program of instructions is to be executed it is usually loaded into the random access memory of the computer thereby configuring the computer to act in accordance with the techniques disclosed herein. All these operations are well known to those skilled in the art and thus are not further described herein. The term computer readable medium encompasses distribution media intermediate storage media execution memory of a computer and any other medium or device capable of storing for later reading by a computer a computer program implementing the present invention.

Accordingly drawings tables and description disclosed herein illustrate technologies related to the invention show examples of the invention and provide examples of using the invention and are not to be construed as limiting the present invention. Known methods techniques or systems may be discussed without giving details so to avoid obscuring the principles of the invention. As it will be appreciated by one of ordinary skill in the art the present invention can be implemented modified or otherwise altered without departing from the principles and spirit of the present invention. Therefore the scope of the present invention should be determined by the following claims and their legal equivalents.

