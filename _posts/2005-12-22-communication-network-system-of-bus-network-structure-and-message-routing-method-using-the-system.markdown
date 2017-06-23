---

title: Communication network system of bus network structure and message routing method using the system
abstract: A method for processing a message routing in a communication network system having a bus network structure includes connecting a plurality of brokers in a mesh topology; connecting each of the service terminal nodes to one of the brokers via a connector; allocating a network address to each of the connected service terminal nodes; maintaining at least some of the allocated network addresses and socket addresses of the connected brokers in a routing table; and routing a message between the service terminal nodes by using information contained in the routing table. A network communication system having a bus network structure includes service terminal nodes; at least one connector connected to at least one of the service terminal nodes; and a plurality of brokers, each of the brokers having a routing table.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08321585&OS=08321585&RS=08321585
owner: NHN Corporation
number: 08321585
owner_city: Seongnam-si
owner_country: KR
publication_date: 20051222
---
This application is a U.S. National Phase Application of International Application PCT Application No. PCT KR2005 004464 filed on Dec. 22 2005 which claims the benefit of priority from Korean Patent Application No. 10 2004 0111609 filed on Dec. 24 2004. The disclosures of International Application PCT Application No. PCT KR2005 004464 and Korean Patent Application No. 10 2004 0111609 are incorporated herein by reference.

The present invention relates to a communication network system in a bus network structure and a method for processing a message routing in the communication network system. More particularly the present invention relates to a communication network system which can allocate a network address to each service maintain the network address and a socket ID of a broker connected to each service in a routing table of the broker and process a message routing between each service by using the network address and the socket ID maintained in the routing table in a communication network system having a bus network structure in which at least one service contained in one process is connected to a broker processing a message routing via one connector and all brokers of a network are connected to each other in a full mesh topology.

In the conventional art all game servers providing game service are connected to each other in a mesh topology. is a diagram illustrating network connections between game servers according to the conventional art.

According to the conventional art illustrated in every time new game servers are added there is a surprising increase in a number of connections from the viewpoint of the entire network. is a diagram illustrating network connections between game servers which may occur as a number of game servers continuously increases in the conventional art.

According to the conventional art in which game servers are connected to each other with mesh topology as described above when a number of game servers increases the connection structure thereof also becomes very complicated. As a result a game server may not be able to be extended according to an increase of game users. Also when a connection between game servers is globally extended the management thereof also becomes difficult.

The more a number of partner servers connect to one server the more the total number of connections geometrically increases. Generally in the conventional art one game server is connected to a login server a ranking server and a database server. In this instance the game server is additionally grouped with a channel list server and a notice server as one multicast group. Accordingly a substantial number of connections in the entire network greatly exceeds a number of connections between game servers. Also its management is very difficult.

Consequently a new communication network structure which can deviate from a network structure according to the conventional art connecting all game servers in a mesh topology simplify and easily manage a connection structure between servers and efficiently extend services is needed. Also a method capable of efficiently processing a message routing in the new communication network structure is needed.

The present invention is conceived to solve the aforementioned problems in the conventional art. Thus an objective of the present invention is to provide a method for efficiently processing a message routing via a routing table maintained by a broker in a new communication network system having a simplified connection structure between servers by using a bus network structure.

Another objective of the present invention is to include a network address of each service in a routing table maintained by each broker in correspondence to a socket ID of a broker connected to the each service and enable a broker to efficiently perform a message routing via a routing table in a new communication network system having a simplified connection structure between servers by using a bus network structure.

Still another objective of the present invention is to automatically inform other brokers when a routing table maintained by a particular broker is changed and to enable the other brokers to update their routing table in a new communication network system having a simplified connection structure between servers by using a bus network structure.

Yet another objective of the present invention is to embody natural load balancing by moving a proper number of connectors connected to an existing broker to an additional broker when adding the additional broker and to automatically update a routing table in a new communication network system having a simplified connection structure between servers by using a bus network structure.

Further another objective of the present invention is to quickly terminate an abnormal connection by terminating a connection of one side according to a predetermined standard when a plurality of connections is set up between brokers and to efficiently maintain a number of connections from the viewpoint of the entire network in a new communication network system having a simplified connection structure between servers by using a bus network structure.

Still another objective of the present invention is to suggest a new communication network structure which can deviate from a conventional network structure connecting all game servers to each other in a full mesh topology simplify a connection structure between servers and easily maintain the same and also can efficiently extend a service.

To achieve the above objectives and solve the aforementioned problems in the conventional art according to an aspect of the present invention there is provided a method for processing a message routing in a communication network system having a bus network structure wherein the communication network system includes a broker processing a message routing a connector and a plurality of services which is a communicable terminal node connected to the broker via the connector and the method includes the steps of connecting all brokers of the communication network system to each other in a full mesh topology each broker maintaining a predetermined routing table connecting the connector to the broker and setting up a connection between the service and the broker via the connector allocating a network address to the each connected service and maintaining the network address and a socket ID of a broker connected to the each service in the routing table and processing a message routing between the each service by using the network address and the socket ID maintained in the routing table.

According to an aspect of the present invention there is provided a method for processing a message routing wherein the network address is a unicast address and the step of processing a message routing between the each service includes the steps of a first broker receiving a request for transfer of a message having a destination of a unicast address from a first service connected to the first broker the first broker identifying a second broker having a socket ID corresponding to the destination by referring to the routing table and the first broker directly transferring the message to a second service corresponding to the destination when the first broker and the second broker are identical and the first broker transferring the message to the second broker and the second broker transferring the message to the second service when the first broker and the second broker are different.

According to another aspect of the present invention there is provided a method for processing a message routing further including the steps of a first broker transmitting its updated routing information to all second brokers connected to the first broker in a full mesh topology when the first broker s routing table has been updated and the second broker receiving the updated routing information to update its routing table.

According to still another aspect of the present invention there is provided a method for processing a message routing further including the steps of an additional broker setting up a connection with existing brokers connected in a full mesh topology in the communication network system in the case of adding the additional broker randomly selecting one of the existing brokers and the additional broker requesting the selected broker for a routing table receiving the routing table and reflecting the same in its own routing table.

According to another embodiment of the present invention there is provided a communication network system in a bus network structure the system including a broker processing a message routing a connector and a plurality of services connected to the broker via the connector wherein the service is a communicable terminal node and a network address uniquely identifying each service is allocated to the each service the connector is a module for mediating a connection between the service and the broker the broker is a module for setting up a routing path or a connection with the connector to process the routing message each broker is connected to each other in a full mesh topology and the broker maintains the network address and a socket ID of a broker connected to the each service in a predetermined routing table and processes a message routing between the each service by using the network address and the socket ID maintained in the routing table.

Hereinafter a communication network system and a data transmitting receiving method using the same according to the present invention will be described in detail with reference to the accompanying drawings.

As illustrated in in the conventional art all game servers are connected to each other in a mesh topology. However in the bus network structure according to the present invention as illustrated in all servers are connected to each other in a bus structure. Accordingly the connection structure between servers is very simplified.

According to the conventional art illustrated in as illustrated in every time new game servers are added there is a surprising increase in a number of connections from the viewpoint of the entire network. On the other hand as illustrated in in the bus network structure according to the present invention each server maintains a connection with one broker. Also in the case of extending the network an intermediate connection is performed via brokers. Accordingly although a server is additionally connected a number of connections is not significantly increased from the viewpoint of the entire network. Accordingly the communication network system adopting the bus network structure of the present invention as illustrated in may easily link a new service and also may easily maintain and manage the linked service.

As illustrated in the communication network system according to the present invention includes a broker processing a message routing a connector and a plurality of services connected to the broker via the connector .

The service is a communicable terminal node. Each service is connected to the broker via one connector .

In the communication network system according to the present invention a network address uniquely identifying each service is allocated to each service . In this instance the network address corresponds to a unique address value capable of identifying each service in the entire communication network system according to the present invention.

The connector is a module for mediating a connection between the broker and the service . Only one broker is connected to each connector and the service may be registered in the broker via the connector .

According to an embodiment of the present invention the connector and the service are contained in an identical process. Only one connector is contained in one process and at least one service is contained in one process. Namely only one connector exists for each process. Also the connector may mediate a connection between all services and the broker . In this instance all services exist in a process containing the connector .

According to the present embodiment a connector and a process are matched 1 1. Accordingly a communication network system may be unified. Also inefficient routing which may occur when connecting the services contained in different processes to the same broker via one connector may be prevented. Also complexity in transmitting receiving data may be prevented.

The broker is a module for setting up a routing path or the connection with the connector to efficiently process the message routing. The brokers are connected to each other in a full mesh topology.

In the present specification a network formed by connecting the brokers in a full mesh topology is defined as a message routing server MRS network . Accordingly the MRS network is a network service platform for efficiently transmitting receiving a message between various types of communication systems. The connector is a module for providing a programming interface for transmitting receiving a message by using the MRS network . The service utilizes the MRS network via the programming interface provided by the connector .

As illustrated in in the communication network system according to the present invention there is only one effective connection between the broker and the connector . In the case of communicating with the broker each service sequentially communicates with the broker via said only one connection.

Only one connection should be set up between brokers connected to each other in a full mesh topology in the MRS network . If a plurality of brokers simultaneously requests a connection and a plurality of connections is set up this may cause a problem.

According to an embodiment of the present invention when a first broker and a second broker request a connection to each other at the same time and a plurality of connections is set up between the first broker and the second broker each IP address of the first broker and the second broker is compared. Which one connection will be terminated among a plurality of connections may be determined on the basis of the comparison. For this a method of determining the each IP address as a DWORD value of 4 bytes and terminating a connection requested by the broker corresponding to an IP address having a smaller value may be utilized.

According to the present embodiment it is possible to quickly terminate an abnormal connection and efficiently maintain a proper number of connections from the viewpoint of the entire network by terminating a connection of one side according to an explicit standard when a plurality of connections is set up between brokers .

As described above the broker functions to set up a routing path to efficiently process a message routing. For this all brokers in the MRS network maintain a routing table for the message routing.

Also the broker may set up a connection with the service via the connector connected to the broker receive a service registration request from the service and include routing information of the corresponding service in its routing table.

As described later in the present invention a network address is allocated to the each service and the allocated network address may uniquely identify the service in the entire network. In this instance a routing table may make a network address of each service correspond to a socket ID socket address of a broker connected to the each service and include the network address and the socket ID.

Also the broker in the MRS network processes a message routing between the each service by using a network address of the each service and a socket ID socket address of the broker connected to the each service which are maintained in its routing table.

As illustrated in various types of game related servers such as a game string server a channel list server a game server a notice server a management server a database server etc. are connected to each other via an MRS network . Each server maintains only one connection with any one of a plurality of brokers which are connected to each other in a full mesh topology.

In the conventional art all game related servers are connected to each other in a full mesh topology. Accordingly the more a number of partner servers connected to one server the more the total number of connections geometrically increases. On the other hand according to the present invention as illustrated in each server maintains a connection with only one broker. Also in the case of extending the network an intermediate connection is performed via brokers. Accordingly although a server is additionally connected a number of connections is not significantly increased in the viewpoint of the entire network.

In the present specification the structure of the message will be described based on a data type which is widely used in Windows rather than an octet notation as a data type for defining a field of each message. In this case Windows data type and octet notation is mapped such as BYTE octet 8 WORD octet 16 and DWORD octet 32 .

Messages used in the communication network system according to the present invention are grouped into MRMSGHeader and MRCMPHeader. Each message is divided into fields of which one is a common field containing MRHeader and remaining fields are specified fields of each message.

MRHeader is message header information that all messages exchanged in the communication network system according to the present invention should contain as a common field. An MRHeader message may not be used alone. The MRHeader message must be transmitted received after inserting a valid value in a protocol type field and appending additional message information to the MRHeader.

A transferred message in the MRMSGHeader format has a structure for transferring a payload value designated by a service between a plurality of services connected to an MRS network.

In this case a source address and a destination address are described in the message transmitted received in the structure of MRMSGHeader. The source address is an address of a transmitter transmitting a message and the destination address is an address of a receiver receiving the message. Also the MRS network tries routing on the basis of connection information and the destination address. Each field will be described in Table 2 below.

A transferred message in the format of MRCMPHeader is a message defined for transmitting receiving a signal between a connector and a broker and between brokers. In this instance the connector and the broker are subsystems of the communication network system according to the present invention. Each field will be described in Table 3 below.

In the case of designating a source address and a destination address to transmit receive data using an MRS network the present invention utilizes a new address system according to the present invention not an IP address. The MRS network supports three types of addresses which are unicast anycast and multicast to identify a particular service. Each address is in the form of a cast type and an address in any one of the three address types and has the length of 16 bytes.

In the case of an online game a plurality of service instances interacts and communications between the service instances also increase. However in the conventional art a network address is not allocated to the service instances. Namely one process having an identical network address contains many service instances and processes a large number of communications between service instances.

Accordingly the present invention utilizes a new address system allocates a single network address to each service instance and efficiently processes a communication between service instances. In this case a game server does not need to distribute messages to each of a plurality of game centers. Accordingly management cost may be significantly reduced.

For this the present invention allocates a network address uniquely identifying each service to the same. Also the network address is defined as a unique address value capable of identifying the each service in the entire network system according to the present invention.

In the present invention data is transmitted received between services registered in an MRS network via a connector and a broker on the basis of the network address.

Also the present invention supports three types of addresses which are unicast anycast and multicast.

A communication network system according to the present invention may register a service in a broker via a connector by using a unicast address which is a network address allocated to each service. Also the communication network system may make at least one portion of the registered services join an anycast group or a multicast group according to a function of a corresponding service and transmit receive data between the registered service and the service registered in the anycast group or the multicast group. Namely in the present invention data may be transmitted or received from a unicast address of a source transmitting a message to an anycast address of a destination receiving the message.

For this a connector of the communication network system according to the present invention may function to register services in a broker and to make at least one portion of the registered services join an anycast group or a multicast group according to a function of a corresponding service. A broker in an MRS network may function to route a message received from a particular service and transmit receive data between the service and a registered service in the anycast group or the multicast group. Also the broker is registered with a unicast address of each service and also with the anycast address or the multicast address of the service registered in the anycast address or the multicast address.

As an example when a service A providing a GOSTOP game service is generated a connector may initially register a unicast address of the service A in a broker and subsequently make the service A join a multicast group associated with providing of the GOSTOP game service. When a service B transmits a packet asking how many users are using a game with respect to GOSTOP game services a broker may receives the packet and transmit the same to the service A and a multicast address of all the services registered in the multicast group. The service A receives a response to the query via the broker.

As described above in the present invention each service may be grouped into an anycast or multicast group according to its properties. The grouping may be performed by using a unicast address which is a unique network address allocated to each service. Accordingly the grouped service may be a service operating in a physically separated server.

In a cast type is the type of an address and has one value from among CT UNICAST CT MULTICAST and CT ANYCAST.

A unicast address is a network address which is allocated to each service and also a unique address capable of identifying all the services using an MRS network. Also the unicast address is in the form of a server name and an instance ID. In this instance the server name identifies a server activating a particular service in the entire network of the communication network system according to the present invention. The instance ID uniquely identifies a corresponding service in the same server.

A server name is a unique value of 11 bytes indicating a computer hardware server in which a service using the MRS network is activated. A server name may be a unique value of 11 bytes identifying a server in which a service is activated within the entire network.

The instance ID is a unique identifier identifying a service in the same server. A reserved value is allocated to the instance ID with respect to a portion of services and a dynamically generated value in the server is allocated to the instance ID with respect to the rest of the services.

As an example values of 1 to 65535 are reserved for when a service requires a fixed unicast address. Values after 65536 may be dynamically allocated and used within the server. In this instance the service requiring a fixed unicast address may include a service that continuously operates from starting to termination of the communication network system according to the present invention thereof.

The multicast address and anycast addresses simply utilize a 15 byte length value. Accordingly the multicast and anycast addresses may be readily set up and utilized between services. This value should be a unique value in the entire network and also known in advance.

Examples of using an MRS network according to the present invention may include 1 the case of a service accessing the MRS network to utilize a function of other services and 2 the case of a service accessing the MRS network to provide a function of processing a matter requested from other services.

As an example of 1 the case of a service accessing the MRS network to use a function of other services there may be a service sending a request to a login server to confirm user login information and receiving a response thereto. The service for utilizing a function provided by other services operates as shown below via a connector which is a module for mediating the MRS network and the service.

Initially when starting a process a programming interface is initialized to transmit receive data between the service and a connector. After registering a unicast address which is a network address of the service in the MRS network the service sends a request message to other services and receives a response message therefrom. Also in the case of completing the use of the function provided by other services the unicast address of the service is removed from the MRS network. When ending the process the programming interface is also terminated.

As an example of 2 the case of a service accessing the MRS network to provide a function of processing a matter requested from other services there may be a service providing a database reference function and a service providing a user s login information or location information. The service for providing a particular function to other services operates as shown below via a connector which is a module for mediating the MRS network and the service.

Initially when starting a process a programming interface is initialized to transmit receive data between the service and a connector. After registering a unicast address of the service in the MRS network the service joins an anycast or multicast group with respect to a function to be provided. Also the service receives a request message from other services and sends a response message thereto. Also in the case of completing providing of the particular function to another service the service leaves the joined anycast or multicast group. The unicast address of the service is removed from the MRS network. When ending the process the programming interface is also terminated.

As described above in the present invention a connector may register a unicast address of a service in an MRS network and make the service join an anycast or multicast group according to a function of the service and leave the service from the joined anycast or multicast group in the case of termination of the service.

Hereinafter a message routing method supported in an MRS network according to the present invention will be described.

All brokers of an MRS network according to the present invention maintain their routing table to process a message routing. A unicast address allocated to each service and a socket ID socket address of a broker connected to each service correspond to each other and are maintained in the routing table. The broker processes a message routing between each service by using the unicast address of the service and the socket ID of the broker maintained in the routing table.

Referring to in a routing table maintained by each broker each unicast address of services S and S may be maintained in correspondence to cs4.platform.nhncorp.com or 221.148.17.54 which is a socket ID of broker CS. Also each unicast address of services S and S may be maintained in correspondence to cs8.platform.nhncorp.com or 221.148.17.51 which is a socket ID of broker CS. Also each unicast address of services S and S may be maintained in correspondence to cs6.platform.nhncorp.com or 221.148.17.55 which is a socket ID of broker CS.

As an example in when the broker CS receives a request for transfer of a message having a destination as a unicast address from the service S connected to the broker CS the broker CS identifies a broker having a socket ID corresponding to the destination by referring to its routing table.

When the destination is the service S the broker CS directly transfers the message to the service S corresponding to the destination by not using another broker. This is because the service S is maintained in the routing table in correspondence to the socket ID of the broker CS.

Also when the destination is the service S the broker CS transfers the message to the broker CS and the broker CS transfers the message to the service S corresponding to the destination. This is because the service S is maintained in the routing table in correspondence to the socket ID of the CS.

In it is assumed that S is a service not registered in an anycast or multicast group S S and S are services registered in the anycast group and S and S are services registered in the multicast group.

A broker in an MRS network according to the present invention maintains a unicast address of each service and a socket ID of a broker connected to each service in its routing table. Also the broker may further include a multicast address of a service registered in a multicast group in its routing table. In this case the routing table maintains the multicast address in correspondence to a socket ID of a broker connected to each service.

As an example in when the broker CS receives a request for transfer of a message having a destination for a multicast address from the service S connected to the broker CS the broker CS identifies at least one broker having a socket ID corresponding to the destination by referring to its routing table.

In this case brokers CS and CS having a socket ID corresponding to services S and S registered in the multicast group are identified by using the routing table. The broker CS transfers the message to the brokers CS and CS. Accordingly the broker CS transfers the message to the service S connected to the broker CS and the broker CS transfers the message to the service S connected to the broker CS.

When service S not illustrated registered in the multicast group is connected to the broker CS the broker CS may identify a socket ID corresponding to the service S as its socket ID by referring to its routing table and transfer the message to service S without going via other brokers.

A broker in an MRS network according to the present invention maintains a unicast address of each service and a socket ID of a broker connected to each service in its routing table. Also the broker may further include an anycast address of a service registered in an anycast group in its routing table. In this case the routing table maintains the anycast address in correspondence to a socket ID of a broker connected to each service.

As an example when the broker CS receives a request for transfer of a message having a destination as an anycast address from the service S connected to the broker CS the broker CS identifies at least one broker having a socket ID corresponding to the destination by referring to its routing table and selects one of the at least one broker.

In this case brokers CS CS and CS having a socket ID corresponding to services S S and S registered in the anycast group are identified by using the routing table. The broker CS selects one of the identified brokers CS CS and CS.

According to an embodiment of the present invention when a broker in an MRS network receives anycast data having a destination as an anycast address from a unicast address of a service corresponding to a source the broker may select a service having a minimum routing distance for transmission of the anycast data and transmit the anycast data to the selected service.

In the present embodiment a broker in an MRS network having received anycast data may operate to transmit the anycast data to a service when the service is directly connected to the broker among services registered in an anycast group. Also when a directly connected service does not exist the broker may randomly select a service to transmit anycast data via other brokers connected to the broker in a full mesh topology.

Namely a broker in an MRS network having received anycast data may select a service to transmit the anycast data when the services registered via a connector directly connected to the broker exist. However when the registered service does not exist the broker may randomly select one of a plurality of services registered in the anycast group and transmit anycast data to the selected service.

According to the present embodiment a routing distance is remarkably shortened by processing anycast data as described above. Accordingly routing may be performed quickly. Also natural load balancing may be embodied while not using an L4 switch.

Hereinafter an operation process of a service a connector and a broker which are subsystems of a communication network system according to the present invention will be described with reference to .

In step S a service transmits a service registration message to a connector. In step S the connector analyzes the service registration message to check whether the same is a pre registered service. In step S in the case of the service not pre registered the connector transfers the service registration message to a broker.

In step the broker adds routing information of the service having transmitted the service registration message to its routing table. Also in step the broker transmits the routing information to other brokers. In step other brokers update their routing information by using the received routing information.

As described above in the present invention a broker in the case of updating its routing table transmits the updated routing information to other brokers in an MRS network connected to each other in a full mesh topology. The brokers having received the updated routing information update their routing table. As a result all the brokers in the MRS network may maintain latest routing information at all times.

In step a service transmits a service cancellation message to a connector. In step the connector analyzes the service cancellation message to check whether the same is a final cancellation. In step in the case of the final cancellation the connector transfers the service cancellation message to a broker.

In step S the broker deletes routing information of the service having transmitted the service cancellation message from its routing table and updates its routing table. In step S the broker notifies other brokers of deletion of the routing information. In step S other brokers receive the notice detect deletion of the routing information and update their own routing table.

In step S a service that wants to utilize a particular service transfers a connection message to a connector and sets up a virtual connection with the connector. In this case an address of a desired service is designated.

In step S the service transmits a message by using a programming interface of the connector. In step S the connector adds a Message Routing Protocol MRP Header according to MRP to the message transmitted from the service and transmits a corresponding message to a broker connected to the connector. In this instance MRP is used in the MRS network. In step S the broker searches for a destination of the message received from the connector. In step S the broker transmits the message to a corresponding broker or a corresponding connector.

In step S the broker receives a message from another broker. In step S the broker searches for a destination of the received message. In step S the broker transmits the message to a corresponding connector. In step S the connector removes the MRP Header from the transmitted message and searches for a destination address and instance of the transmitted message. In step S the message is transmitted to a corresponding service and the corresponding service receives the message.

In a communication network system according to the present invention messages transferred to a broker via a connector through the aforementioned process are transparently transmitted received to other brokers or connectors. Also in the communication network system a message transferred by a particular service may be transparently transmitted received via a routing path between brokers provided in the routing path.

In step S an additional broker to be newly added is waiting for existing brokers to be connected first. In step S the additional broker sets up a connection with the existing brokers that are being implemented. In step S the existing brokers connected to the additional broker add the same to their broker list recording other brokers connected to the existing brokers and update the broker list. In the same manner in step S the additional broker sets up a connection with other existing brokers that are being implemented. In step S broker lists of the other existing brokers are also updated. As described above broker lists of all brokers that are being implemented in the MRS network may be updated.

In step S the additional broker is connected to all the existing brokers that are being implemented and randomly selects any one of the existing brokers. In step S the additional broker requests the selected broker for a routing table thereof and in step S receives the same. In step S the additional broker reflects the received routing table in its routing table. In step S the additional broker notifies other existing brokers that the additional broker itself is ready for a connection with a connector.

In step S existing brokers receive the notice and count a number of re setup connectors to be moved to the additional broker among connectors connected to the existing brokers and select the same number of connectors as the counted number. In this instance when a number of connectors connected to the existing broker exceeds an average number of connections obtained by dividing a number of connections between all connectors and brokers existing in the entire network by the total number of brokers existing brokers may select an excess number of connectors as re setup connectors.

Also in step S each of the existing brokers having received the notice notifies all connectors connected to the broker itself that the additional broker has been connected. In step S each of the connectors having received the notice adds the additional broker to its broker list recording brokers connected to the connector itself.

In step S a message informing to re setup a connection with the additional broker is transferred to the selected re setup connectors. In step S the connectors having received the message are connected to the additional broker and transfer a service registration message with respect to services connected to the connectors to the additional broker.

Also as connections between the additional broker and the selected re setup connectors are completed routing tables of the additional broker and the existing brokers are all updated.

The steps of S to S may be performed with respect to all brokers that are being implemented in the MRS network. Also through the aforementioned process a certain portion of connectors connected to brokers that are being implemented and services connected to the connectors may be moved to an additional broker in the MRS network. Accordingly load may be efficiently distributed between brokers.

In step S a broker to be normally terminated sets itself so that a connector may no longer connect to the broker. In step S the broker to be normally terminated notifies other brokers that the broker will be terminated. In step S the terminating broker and other brokers having received the notice notifies the same to connectors connected to the other brokers.

In step S the terminating broker transmits a message to connectors connected to the terminating broker. In this instance the message is about re setup of connectors informing the connectors to move to other broker. In step S connectors having received the message are connected to another broker and transmit a service registration message with respect to services connected to the connectors.

In step S the newly connected broker of connectors from the terminating broker soon updates its routing information and transmits the updated routing information to the terminating broker and other brokers.

In step S the terminating broker updates its routing table by using the transmitted routing information and checks whether the terminating broker s connection with the connector is still included in the routing table of the broker. If not the connection is terminated in step S.

In step S the terminating broker checks whether a predetermined time has passed from a point in time when a message about re setup of connectors informing the connectors to move to other broker is transmitted to the connectors connected to the terminating broker. In step S in the case of having connectors connected to the terminating broker even after the certain time the terminating broker terminates all connections with the connectors and terminates the broker itself.

In step S a broker is abnormally terminated. In this case in step S another broker detects abnormal termination of the broker. In step S another broker readjusts its maximum capacity.

A maximum number of connectors connectable to one broker as an example 50 is the broker s maximum capacity. In the case of another broker detecting abnormal termination of a broker the another broker may increase its maximum number of connectors connectable to one broker to 60 and operate to enable connectors connected to the abnormally terminated broker to quickly move to other brokers and be connected thereto. In this case a service disconnection time may be significantly reduced.

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

According to the present invention there is provided a method for efficiently processing a message routing via a routing table maintained by a broker in a new communication network system having a simplified connection structure between servers by using a bus network structure.

Also according to the present invention it is possible to include a network address of each service in a routing table maintained by each broker in correspondence to a socket ID of a broker connected to the each service and enable a broker to efficiently perform a message routing via a routing table in a new communication network system having a simplified connection structure between servers by using a bus network structure.

Also according to the present invention it is possible to automatically inform other brokers when a routing table maintained by a particular broker is changed and to enable the other brokers to update their routing table in a new communication network system having a simplified connection structure between servers by using a bus network structure.

Also according to the present invention it is possible to embody natural load balancing by moving a proper number of connectors connected to an existing broker to an additional broker when adding an additional broker and to automatically update a routing table in a new communication network system having a simplified connection structure between servers by using a bus network structure.

Also according to the present invention it is possible to quickly terminate an abnormal connection by terminating a connection of one side according to a predetermined standard when a plurality of connections is set up between brokers and to efficiently maintain a number of connections from the viewpoint of the entire network in a new communication network system having a simplified connection structure between servers by using a bus network structure.

Also according to the present invention it is possible to suggest a new communication network structure which can deviate from a conventional network structure connecting all game servers to each other in a full mesh topology simplify a connection structure between servers and easily maintain the same and also can efficiently extend a service.

