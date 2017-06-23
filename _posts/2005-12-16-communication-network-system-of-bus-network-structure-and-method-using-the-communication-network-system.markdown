---

title: Communication network system of bus network structure and method using the communication network system
abstract: Disclosed is a communication network system in a bus network structure, the system including: a broker processing a message routing; a connector; and a plurality of services connected to the broker via the connector, wherein: the service is a communicable terminal node and each of the plurality of services is connected to the broker via one connector, the connector is a module for mediating a connection between the service and the broker, each connector connected to only one broker, and the broker is a module for setting up a routing path or the connection with the connector, and to process the message routing, all brokers connected to each other in a full mesh topology.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08346892&OS=08346892&RS=08346892
owner: NHN Corporation
number: 08346892
owner_city: Seongnam-si
owner_country: KR
publication_date: 20051216
---
This application is a U.S. National Phase Application of International Application PCT Application No. PCT KR2005 004348 filed on Dec. 16 2005 which claims the benefit of priority from Korean Patent Application No. 10 2004 0107496 filed on Dec. 17 2004. The disclosures of International Application PCT Application No. PCT KR2005 004348 and Korean Patent Application No. 10 2004 0107496 are incorporated herein by reference.

The present invention relates to a communication network system in a bus network structure and a data transmitting receiving method using the same and more particularly to a communication network system and a data transmitting receiving method using the same in which a bus network structure connects at least one service contained in one process to a broker processing a message routing via one connector and connects all brokers of a network to each other in a full mesh topology and a connection structure between services is simplified via the bus network structure.

In the conventional art all game servers providing game service are connected to each other in a mesh topology. is a diagram illustrating network connections between game servers according to the conventional art.

According to the conventional art illustrated in every time new game servers are added there is a surprising increase in a number of connections from the viewpoint of the entire network. is a diagram illustrating network connections between game servers which may occur as a number of game servers continuously increases in the conventional art.

According to the conventional art in which game servers are connected to each other with mesh topology as described above when a number of game servers increases the connection structure thereof also becomes very complicated. As a result a game server may not be able to be extended according to an increase of game users. Also when a connection between game servers is globally extended the management thereof also becomes difficult.

The more a number of partner servers connect to one server the more the total number of connections geometrically increases. Generally in the conventional art one game server is connected to a login server a ranking server and a database server. In this instance the game server is additionally grouped with a channel list server and a notice server as one multicast group. Accordingly a substantial number of connections in the entire network greatly exceeds a number of connections between game servers. Also its management is very difficult.

Consequently a new communication network structure which can deviate from a network structure according to the conventional art connecting all game servers in a mesh topology simplify and easily manage a connection structure between servers and efficiently extend services is needed.

The present invention is conceived to solve the aforementioned problems in the conventional art and the present invention provides a communication network system and a data transmitting receiving method using the same which can simplify a connection structure between servers by using a bus network structure and support service extendibility and performance extendibility and also can easily maintain and manage the connection structure.

The present invention also provides a communication network system and a data transmitting receiving method using the same which can suggest a new communication structure that can deviate from a network structure according to the conventional art connecting all game servers in a mesh topology simplify and easily manage a connection structure between servers and efficiently extend services.

To achieve the above objectives and solve the aforementioned problems in the conventional art according to an embodiment of the present invention there is provided a communication network system including a broker processing a message routing a connector and a plurality of services connected to the broker via the connector wherein the service is a communicable terminal node and each of the plurality of services is connected to the broker via one connector the connector is a module for mediating a connection between the service and the broker each connector connected to only one broker and the broker is a module for setting up a routing path or the connection with the connector to process the message routing all brokers connected to each other in a full mesh topology.

According to an aspect of the present invention there is provided a communication network system in which the connector includes an Application Programming Interface API exposing a function provided by the connector to the service a message queue management module managing a transmitted received Message Routing Protocol MRP packet the MRP packet being a unit of data transmitted received between the connector and the broker a service pool management module registering the service in the broker or removing the service from the broker and managing the registered service a service management module managing information on the registered service and a connection management module transmitting receiving the MRP packet and managing a socket connection with the broker.

According to another aspect of the present invention there is provided a communication network system in which the broker includes a link management module maintaining and managing a connection with the connector or other brokers and transmitting receiving data with the connector or other brokers a routing information management module maintaining and managing routing information of a service registered in the broker a message division module understanding a type of data received in the link management module and dividing the received data into a simple message and a complex message according to a predetermined standard a message router receiving the simple message from the message division module obtaining location information of a destination associated with the simple message from the routing information management module and transferring the obtained location information to the link management module a message deserializer receiving the complex message from the message division module and converting the received complex message into an object a message transactor receiving the object from the message deserializer and controlling the broker by using the object a message serializer receiving the object from the message transactor processing the object into transmittable linear data and transferring the same to the link management module and an automatic configurator tracking a status of a network containing the broker and automatically adjusting the status of the broker.

According to an embodiment of the present invention there is provided a method for transmitting receiving data by using a communication network system in a bus network structure in which the communication network system includes a broker processing a message routing a connector and a plurality of services connected to the broker via the connector and the method includes the steps of connecting all brokers of the communication network system to each other in a full mesh topology the broker being a module for setting up a routing path or a connection with the connector to process the message routing connecting the connector to the broker the connector being a module for mediating the connection between the broker and at least one service contained in one process each connector connected to only one broker registering the service in the broker via the connector the service being a communicable terminal node each service connected to the broker via one connector and transmitting receiving data between the registered services via the connector and the broker.

Hereinafter a communication network system and a data transmitting receiving method using the same according to the present invention will be described in detail with reference to the accompanying drawings.

As illustrated in in the conventional art all game servers are connected to each other in a mesh topology. However in the bus network structure according to the present invention as illustrated in all servers are connected to each other in a bus structure. Accordingly the connection structure between servers is very simplified.

According to the conventional art illustrated in as illustrated in every time new game servers are added there is a surprising increase in a number of connections from the viewpoint of the entire network. On the other hand as illustrated in in the bus network structure according to the present invention each server maintains a connection with one broker. Also in the case of extending the network an intermediate connection is performed via brokers. Accordingly although a server is additionally connected a number of connections is not significantly increased from the viewpoint of the entire network. Accordingly the communication network system adopting the bus network structure of the present invention as illustrated in may easily link a new service and also may easily maintain and manage the linked service.

As illustrated in the communication network system according to the present invention includes a broker processing a message routing a connector and a plurality of services connected to the broker via the connector .

The service is a communicable terminal node. Each service is connected to the broker via one connector . Also the connector is a module for mediating a connection between the broker and the service . Each connector is connected to only one broker .

According to an embodiment of the present invention the connector and the service are contained in an identical process. Only one connector is contained in one process and at least one service is contained in one process. Namely only one connector exists for each process. Also the connector may mediate a connection between all services and the broker . In this instance all services exist in a process containing the connector .

According to the present embodiment a connector and a process are matched 1 1. Accordingly a communication network system may be unified. Also inefficient routing which may occur when connecting the services contained in different processes to the same broker via one connector may be prevented. Also complexity in transmitting receiving data may be prevented.

The broker is a module for setting up a routing path or the connection with the connector to efficiently process the message routing. The brokers are connected to each other in a full mesh topology.

In the present specification a network formed by connecting the brokers in a full mesh topology is defined as a message routing server MRS network . Accordingly the MRS network is a network service platform for efficiently transmitting receiving a message between various types of communication systems. The connector is a module for providing a programming interface for transmitting receiving a message by using the MRS network . The service utilizes the MRS network via the programming interface provided by the connector .

As illustrated in in the communication network system according to the present invention there is only one effective connection between the broker and the connector . In the case of communicating with the broker each service sequentially communicates with the broker via said only one connection.

As illustrated in various types of game related servers such as a game string server a channel list server a game server a notice server a management server a database server etc. are connected to each other via an MRS network . Each server maintains only one connection with any one of a plurality of brokers which are connected to each other in a full mesh topology.

In the conventional art all game related servers are connected to each other in a full mesh topology. Accordingly the more a number of partner servers connected to one server the more the total number of connections geometrically increases. On the other hand according to the present invention as illustrated in each server maintains a connection with only one broker. Also in the case of extending the network an intermediate connection is performed via brokers. Accordingly although a server is additionally connected a number of connections is not significantly increased in the viewpoint of the entire network.

In the present specification the structure of the message will be described based on a data type which is widely used in windows rather than an octet notation as a data type for defining a field of each message. In this case windows data type and octet notation is mapped such as BYTE octet 8 WORD octet 16 and DWORD octet 32 .

Messages used in the communication network system according to the present invention are grouped into MRMSGHeader and MRCMPHeader. Each message is divided into fields of which one is a common field containing MRHeader and remaining fields are specified fields of each message.

MRHeader is message header information that all messages exchanged in the communication network system according to the present invention should contain as a common field. An MRHeader message may not be used alone. The MRHeader message must be transmitted received after inserting a valid value in a protocol type field and appending additional message information to the MRHeader.

A transferred message in the MRMSGHeader format has a structure for transferring a payload value designated by a service between a plurality of services connected to an MRS network.

In this case a source address and a destination address are described in the message transmitted received in the format of MRMSGHeader. The source address is an address of a transmitter transmitting a message and the destination address is an address of a receiver receiving the message. Also the MRS network tries routing on the basis of connection information and the destination address. Each field will be described in Table 2 below.

A transferred message in the format of MRCMPHeader is a message defined for transmitting receiving a signal between a connector and a broker and between brokers. In this instance the connector and the broker are subsystems of the communication network system according to the present invention. Each field win be described in Table 3 below.

In the case of designating a source address and a destination address to transmit receive data using an MRS network the present invention utilizes a new address system according to the present invention not an IP address. The MRS network supports three types of addresses which are unicast anycast and multicast to identify a particular service. Each address is in the form of a cast type and an address in any one of the three address types and has the length of 16 bytes.

In the case of an online game a plurality of service instances interacts and communications between the service instances also increase. However in the conventional art a network address is not allocated to the service instances. Namely one process having an identical network address contains many service instances and processes a large number of communications between service instances.

Accordingly the present invention utilizes a new address system allocates a single address to each service instance and efficiently processes a communication between service instances. In this case a game server does not need to distribute messages to each of a plurality of game centers. Accordingly management cost may be significantly reduced.

Also the present invention supports three types of addresses such as unicast anycast and multicast. Accordingly anycast or multicast may be applied to group instances operating in physically separated servers as one anycast or multicast group.

In a cast type is the type of an address and has one value from among CT UNICAST CT MULTICAST and CT ANYCAST.

The unicast address is a unique address capable of identifying all services using an MRS network. Also the unicast address is in the form of a server name and an instance ID. In this instance the server name identifies a server activating a particular service in the entire network. The instance ID uniquely identifies a corresponding service in the same server.

The server name is a unique value of 11 bytes indicating a computer hardware server in which a service using the MRS network is activated. A server name may be a unique value of 11 bytes identifying a server in which a service is activated within the entire network.

The instance ID is a unique identifier identifying a service in the same server. As an example values of 1 to 65535 are reserved for when a fixed unicast address is required. Values after 65536 may be dynamically allocated and used within the server.

The multicast address and anycast addresses simply utilize a 15 byte length value. Accordingly the multicast and anycast addresses may be readily set up and utilized between services. This value should be a unique value in the entire network and also known in advance.

Examples of using an MRS network according to the present invention may include 1 the case of a service accessing the MRS network to utilize a function of other services and 2 the case of a service accessing the MRS network to provide a function of processing a matter requested from other services.

As an example of 1 the case of a service accessing the MRS network to use a function of other services there may be a service sending a request to a login server to confirm user login information and receiving a response thereto. The service for utilizing a function provided by other services operates as shown below via a connector which is a module for mediating the MRS network and the service.

Initially when starting a process a programming interface is initialized to transmit receive data between the service and a connector. After registering a unicast address of the service in the MRS network the service sends a request message to other services and receives a response message therefrom. Also in the case of completing the use of the function provided by other services the unicast address of the service is removed from the MRS network. When ending the process the programming interface is also terminated.

As an example of 2 the case of a service accessing the MRS network to provide a function of processing a matter requested from other services there may be a service providing a database reference function and a service providing a user s login information or location information. The service for providing a particular function to other services operates as shown below via a connector which is a module for mediating the MRS network and the service.

Initially when starting a process a programming interface is initialized to transmit receive data between the service and a connector. After registering a unicast address of the service in the MRS network the service joins an anycast or multicast address with respect to a function to be provided. Also the service receives a request message from other services and sends a response message thereto. Also in the case of completing providing of the particular function to another service the service leaves the joined anycast or multicast address. The unicast address of the service is removed from the MRS network. When ending the process the programming interface is also terminated.

As described above in the present invention a connector may cause a service to register a unicast address thereof in an MRS network and join an anycast or multicast address according to a function to be provided and also cause the service to leave the joined anycast or multicast address in the case of termination of the service.

Hereinafter a data transmitting receiving method supported in an MRS network according to the present invention will be described.

As illustrated in the MRS network according to the present invention may transmit data from a unicast address of a source to a unicast address of a destination. Also all unicast addresses registered in the MRS network may receive data from a unicast address of a physically separated area. As described above to transmit or receive unicast data the unicast address of the source is registered in the MRS network. Also the unicast address of the destination registered in the MRS network is known.

As illustrated in the MRS network according to the present invention may transmit data from a unicast address of a source to a multicast address of a destination. When an address of the destination is a multicast address the MRS network transmits data to all unicast addresses joined in the multicast address. illustrates a process of transmitting data from S of a unicast address to S and S of a multicast address. As described above to transmit multicast data the unicast address of the source is registered in the MRS network. Also the multicast address of the destination joined in the MRS network is known.

As S and S in in order to receive desired data transmitted to a multicast address the unicast address registered in the MRS network has to be joined in the multicast address. When a joining procedure is completed data transmitted to the joined multicast address may be received.

As illustrated in the MRS network according to the present invention may transmit data from a unicast address of a source to a multicast address of a destination. When an address of the destination is an anycast address data is transmitted by selecting any one of unicast addresses joined in the anycast address. As described above to transmit anycast data the unicast address of the source is registered in the MRS network. Also the anycast address of the destination joined in the MRS network is known.

According to an embodiment of the present invention a broker in an MRS network receiving an anycast address operates in the case of having a unicast address directly connected to the broker among unicast addresses joined in the anycast address to transmit data to the unicast address. Also in the case of not having a unicast address directly connected to the broker the broker may randomly select an address to receive data via other brokers connected in a full mesh topology.

Referring to according to the present embodiment a broker CS receives the anycast address from S and transmits data to S which is directly connected to the broker CS among S S and S joined in the anycast address. In this case a routing length may be significantly reduced.

If S is a service not joined in the anycast address according to the present embodiment the broker CS receives the anycast address from S and transmits data to S which is an anycast address connected to other broker CS or to S which is also an anycast address connected to other broker CS. This is illustrated in .

According to the present embodiment fast routing becomes possible by processing anycast data as described above. Also natural load balancing may be embodied without an L switch.

As S S and S in to receive desired data transmitted to an anycast address a unicast address registered in the MRS network has to be joined in the anycast address. When a joining procedure is completed data transmitted to the joined anycast address may be received.

Hereinafter an operation process of a service a connector and a broker which are subsystems of a communication network system according to the present invention will be described with reference to .

In step S a service transmits a service registration message to a connector. In step S the connector analyzes the service registration message to check whether the same is a pre registered service. In step S in the case of the service not pre registered the connector transfers the service registration message to a broker.

In step the broker adds routing information of the service having transmitted the service registration message to its routing table. Also in step the broker transmits the routing information to other brokers. In step other brokers update its routing information by using the received routing information.

As described above in the present invention a broker in the case of updating its routing table may transmit the updated routing information to other brokers constructing the MRS network and cause other brokers to maintain latest routing information at all times.

In step a service transmits a service cancellation message to a connector. In step the connector analyzes the service cancellation message to check whether the same is a final cancellation. In step in the case of the final cancellation the connector transfers the service cancellation message to a broker.

In step S the broker deletes routing information of the service having transmitted the service cancellation message from its routing table and updates its routing table. In step S the broker notifies other brokers of deletion of the routing information. In step S other brokers receive the notice detect deletion of the routing information and update their own routing table.

In step S a service that wants to utilize a particular service transfers a connection message to a connector and sets up a virtual connection with the connector. In this case an address of a desired service is designated.

In step S the service transmits a message by using a programming interface of the connector. In step S the connector adds a Message Routing Protocol MRP Header according to MRP to the message transmitted from the service and transmits a corresponding message to a broker connected to the connector. In this instance MRP is used in the MRS network. In step S the broker searches for a destination of the message received from the connector. In step S the broker transmits the message to a corresponding broker or a corresponding connector.

In step S the broker receives a message from another broker. In step S the broker searches for a destination of the received message. In step S the broker transmits the message to a corresponding connector. In step S the connector removes the MRP Header from the transmitted message and searches for a destination address and instance of the transmitted message. In step S the message is transmitted to a corresponding service and the corresponding service receives the message.

In a communication network system according to the present invention messages transferred to a broker via a connector through the aforementioned process are transparently transmitted received to other brokers or connectors. Also in the communication network system a message transferred by a particular service may be transparently transmitted received via a routing path between brokers provided in the routing path.

In step S an additional broker is waiting for other brokers to be connected first. In step S the broker is connected to other brokers that are being implemented. In step S brokers connected to the additional broker add the same to their broker list and update the same. In the same manner in step S the additional broker is connected to other brokers that are being implemented. In step S broker lists of the other brokers are also updated. As described above broker lists of all brokers that are being implemented in the MRS network may be updated.

In step S the additional broker is connected to all brokers that are being implemented and randomly selects any one of the brokers. In step S the additional broker requests the selected broker for a routing table and in step S receives the same. In step S the additional broker reflects the received routing table to its routing table. In step S the additional broker notifies other brokers that the additional broker itself is ready for a connection with a connector.

In step S a broker receives the notice and counts a number of re setup connectors to be moved to the new broker among its connectors connected to the broker and selects the same number of connectors as the counted number. Also in step S the broker having received the notice notifies all connectors connected to the broker itself that the new broker has been connected. In step S all connectors having received the notice add the new broker to a broker list recording brokers connected to the broker itself.

In step S a message informing to re setup a connection with the new broker is transferred to the selected re setup connectors. In step S the connectors having received the message are connected to the new broker and transfer a service registration message with respect to services connected to the connectors to the new broker.

The steps of S to S may be performed with respect to all brokers that are being implemented in the MRS network. Also through the aforementioned process a certain portion of connectors connected to a broker that is being implemented and services connected to the connectors may be moved to the additional broker in the MRS network. Accordingly load may be efficiently distributed between brokers.

In step S a broker to be normally terminated sets itself so that a connector may no longer connect to the broker. In step S the broker to be normally terminated notifies other brokers that the broker will be terminated. In step S the terminating broker and other brokers having received the notice notifies the same to connectors connected to the other brokers.

In step S the terminating broker transmits a message to connectors connected to the terminating broker. In this instance the message is about re setup of connectors informing the connectors to move to other broker. In step S connectors having received the message are connected to another broker and transmit a service registration message with respect to services connected to the connectors.

In step S the newly connected broker of connectors from the terminating broker soon updates its routing information and transmits the updated routing information to the terminating broker and other brokers.

In step S the terminating broker updates its routing table by using the transmitted routing information and checks whether the terminating broker s connection with the connector is still included in the routing table of the broker. If not the connection is terminated in step S.

In step S the terminating broker checks whether a predetermined time has passed from a point in time when a message about re setup of connectors informing the connectors to move to other broker is transmitted to the connectors connected to the terminating broker. In step S in the case of having connectors connected to the terminating broker even after the certain time the terminating broker terminates all connections with the connectors and terminates the broker itself.

In step S a broker is abnormally terminated. In this case in step S another broker detects abnormal termination of the broker. In step S another broker readjusts its maximum capacity.

A maximum number of connectors connectable to one broker as an example 50 is the broker s maximum capacity. In the case of another broker detecting abnormal determination of a broker another broker may increase its maximum number of connectors connectable to one broker to 60 and operate to enable connectors connected to the abnormally terminated broker to quickly move to other brokers and be connected thereto. In this case a service disconnection time may be significantly reduced.

In step S another broker having detected abnormal termination of the broker updates its routing information and notifies other brokers to update their routing table. In step S other brokers are notified of the abnormal termination of the broker and cause their connectors to update their broker list.

In step S a broker is abnormally terminated. In this case in step S a connector connected to the broker detects that the broker connected to the connector is abnormally terminated. In step S the connector deletes the abnormally terminated broker from its broker list.

In step S the connector having deleted the abnormally terminated broker from its broker list randomly selects any one of other brokers from its broker list. In step S the connector is connected to the selected broker. In step S the connector registers all services connected to the connector itself to the selected broker.

In step S the broker with the newly added services transmits its updated routing information to other brokers and notifies the same that the services are registered.

Hereinafter a structure of a connector which is a subsystem of a communication network system according to the present invention and a function of each component will be described.

As illustrated in a connector includes an API a message queue management module a service pool management module a service management module and a connection management module .

The API is an Application Programming Interface which exposes a function of the connector to a service connected to the connector . A system that wants to utilize an MRS network according to the present invention uses the API and transmits receives data.

As illustrated in according to an embodiment of the present invention a connector and a service are contained in an identical process. Only one connector may be contained in one process and at least one service may be contained in one process. Namely one connector is contained in each process and the connector may mediate a connection between all services connected to the connector and the broker constructing an MRS network.

According to the present embodiment a communication network system may be unified by matching a connector and a process 1 1. Also inefficient routing may be prevented. In this instance the inefficient routing occurs when connecting services contained in different processes to the same broker via one connector. Also complexity in transmitting receiving data may be prevented.

As illustrated in at least one service contained in one process may be connected to an MRS network via one connector . In this case a connection and data transmitting receiving between services and the connector may be performed via the API .

Namely to transmit receive data by using the MRS network the service may not directly set up a connection with the MRS network to transmit receive data. The service transmits receives data by using the API provided from the connector . As a result the API receives a request for registration or cancellation of a service and a request for transmission of data to the broker from the service.

The connector is a module for providing the API . Also the connector is loaded in each process using the MRS network and functions to transmit receive a message to the MRS network with respect to all services generated in a corresponding process.

The message queue management module functions to manage an MRP packet used in the MRS network according to the present invention. In this instance the MRP packet is a unit of data transmitted received between the connector and the broker .

As illustrated in the message queue management module may include a transmission queue and a receiving queue .

In this instance the transmission queue functions to manage an MRP packet to be transmitted to the broker and the receiving queue functions to manage an MRP packet received from the broker .

The service pool management module functions to register a service in the broker or remove the service from the broker and to manage the registered service. The service management module functions to manage information on the registered service.

As illustrated in the service management module may include a receiving message queue a receiving buffer queue and a completion queue .

In this instance the receiving message queue functions to manage a received message from the broker . The receiving buffer queue functions to manage a receiving buffer registered by the service. The completion queue functions to manage completed results with respect to input output requested from the service.

The connection management module functions to transmit receive an MRP packet and manage a socket connection with the broker .

As illustrated in the connection management module may include a message transmission module and a connection control module .

In this instance the message transmission module functions to load an MRP packet to be transmitted from the message queue management module and transmit the same to the broker and to transfer an MRP packet received from the broker to the message queue management module . Also the connection control module functions to process a control message between the connector and the broker and control a connection therebetween.

Hereinafter a structure of a broker which is another subsystem of a communication network system according to the present invention and a function of each component will be described.

As illustrated in a broker may include a link management module a routing information management module a message division module a message router a message deserializer a message transactor a message serializer and an automatic configurator .

The link management module functions to maintain and manage a connection with a connector or other broker and also to transmit receive data with the connector or other broker.

The routing information management module functions to maintain and manage routing information of a service registered in the broker . Also the routing information management module may maintain a connection pool including connection information with a connector connected to the broker or other brokers.

The message division module functions to understand a type of data received in the link management module and divide the received data into a simple message and a complex message according to a predetermined standard.

The message router functions to receive the simple message from the message division module obtain location information of a destination associated with the simple message from the routing information management module and transfer the obtained location information to the link management module .

The message deserializer functions to receive the complex message from the message division module and convert the received complex message into an object.

The message transactor functions to receive the object from the message deserializer and control the broker by using the object.

The message serializer functions to receive the object from the message transactor process the object into transmittable linear data and transfer the same to the link management module .

The automatic configurator functions to track a status of a network containing the broker and automatically adjust the status of the broker .

As illustrated in the link management module may include an OS socket subsystem a link accepter a data receiving module a data transmission module and a link agent .

The OS socket subsystem functions as interface for transmitting receiving data with a connector connected to the broker or other broker.

The link accepter functions to receive a connection request from the connector connected to the broker or other broker via the OS socket subsystem and record connection information according to the connection request in the connection pool maintained by the routing information management module .

The data receiving module functions to receive data from the connector connected to the broker or other brokers and transfer the data to the message division module .

The data transmission module functions to receive processed data from the message serializer and transmit the processed data to the connector connected to the broker or other brokers.

The link agent functions to attempt a connection with the connector connected to the broker or another broker via the OS socket subsystem according to a request from the data transmission module and in the case of a successful connection update the connection pool maintained by the routing information management module by using connection information.

Also the data transmission module may check whether a connection with another broker or a connector associated with a destination of data to be transmitted is set up by referring to the connection pool. In the case the connection not set up the data transmission module may operate to attempt data transmission after requesting the link agent to set up a connection with a connector connected to the broker or another broker.

The method for transmitting receiving data in a communication network according to the present invention includes computer readable media including program instructions to implement various operations embodied by a computer. The media may also include alone or in combination with the program instructions data files data structures tables and the like. The media and program instructions may be those specially designed and constructed for the purposes of the present invention or they may be of the kind well known and available to those having skill in the computer software arts. Examples of computer readable media include magnetic media such as hard disks floppy disks and magnetic tape optical media such as CD ROM disks magneto optical media such as floptical disks and hardware devices that are specially configured to store and perform program instructions such as read only memory devices ROM and random access memory RAM . The media may also be a transmission medium such as optical or metallic lines wave guides etc. including a carrier wave transmitting signals specifying the program instructions data structures etc. Examples of program instructions include both machine code such as produced by a compiler and files containing higher level code that may be executed by the computer using an interpreter. The described hardware devices may be configured to act as one or more software modules in order to perform the operations of the present invention.

Although a few embodiments of the present invention have been shown and described the present invention is not limited to the described embodiments. Instead it would be appreciated by those skilled in the art that changes may be made to these embodiments without departing from the principles and spirit of the invention the scope of which is defined by the claims and their equivalents.

A communication network system and a data transmitting receiving method using the same according to the present invention can simplify a connection structure between servers via a bus network structure and support service extendibility and performance extendibility and also can easily maintain and manage the connection structure.

Also a communication network system and a data transmitting receiving method using the same according to the present invention can suggest a new communication structure that can deviate from a network structure according to the conventional art connecting all game servers in a full mesh topology simplify and easily manage a connection structure between servers and efficiently extend services.

