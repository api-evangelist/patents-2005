---

title: Method and network structure for moving a call leg
abstract: Disclosed herein is a method and a network structure for moving a call leg, and implementing a call leg move with the network structure. The method includes creating a call leg moving interface and its method interface reference parameters, which are used to move a call leg from an original call to a destination call. The interface reference parameters are an identifier of a call leg to be moved and a destination call identifier. The method further includes, if an application wants to move the call leg, determining the interface reference parameters according to the call leg and the destination call, and invoking the call leg moving interface to move the call leg from the original call to the destination call with the interface reference parameters. In this manner, the disclosed method provides a simple, convenient, easy to implement and spread interface to the application to move the call leg from one call to another.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07711099&OS=07711099&RS=07711099
owner: Huawei Technologies Co., Ltd.
number: 07711099
owner_city: Shenzhen
owner_country: CN
publication_date: 20051222
---
This is a continuation of International Application No. PCT CN2004 000515 which was filed on May 21 2004 and which in turn claimed the benefit of Chinese Patent Application No. 03137492.1 which was filed on Jun. 25 2003 the entire disclosures of which are hereby incorporated herein by reference.

The present invention relates generally to call moving technology in a telecommunication system and more particularly to a method and network structure for moving a call leg.

In a telecommunication system based on actual requirements there is a multiparty call mode. In this mode a call has three or more call parties and each party is referred to as a call leg. A call leg communicates with other call legs that belong to the same call. During communication based on requirements a call leg may need to move from one call to another and then communicate with call legs of another call.

In current technologies an application server encapsulates and makes abstracts of the underlying telecommunication network capabilities to provide a simple and open service capacity interface to applications and the application services are created through the open service capacity interface. For the multiparty call situation mentioned above current technology such as Parlay OSA API provides only creating leg and releasing leg methods that cannot move a leg from one call to another directly. With this technology when a leg of one call wants to move to another call the only way to proceed is first release from the original call to terminate the connection with the original call and then create the leg in the destination call to connect with the destination call. While in this way a call leg can be moved from one call to another for the user using this leg to communicate the call leg must create a new connection with the destination call after the release from the original call. Not only is this approach complex but also during the call move the user communication is interrupted so as to interfere the continuity of communication and data and states in the original call are changed so as to lose some important information. This is undesirable for services that need communication continuity such as a charging service.

As described above current technology cannot implement a call leg move from one call to another without terminating the communication of this leg.

In accordance with one aspect of the disclosure a method is useful for implementing a call leg move and may include the following steps 

 A creating a call leg moving interface and its method interface reference parameters which are used to move a call leg from an original call to a destination call where the interface reference parameters are an identifier of a call leg to be moved and a destination call identifier and 

 B if an application wants to move the call leg to be moved determining the interface reference parameters according to the call leg and destination call and invoking the call leg moving interface to move the call leg from the original call to the destination call with the interface reference parameters.

 B1 an application notifying the original call that the call leg is being moved to a destination call 

 B2 the original call breaking resource occupied by the call leg changing an original call identifier to the destination call identifier through setting the call message of the call leg and sending a call leg move request to the destination call and 

 B3 having received the call leg move request sent from the original call the destination call determining whether its resource is enough and if it is enough the destination call allocating resource to the leg in which case the call leg move is successful and otherwise it is not successful.

After step B3 the method may further include the destination call notifying the application about a call leg move result.

In some cases step B may include notifying a user terminal corresponding to the call leg to be moved that the call leg is moving to the destination call.

Changing the original call identifier to the destination call identifier through setting the call message of the call leg in step B2 may include keeping unchanged at least a media type a charging policy and terminal information in the call message.

Moving the call leg in step B may include maintaining the call leg in a suspending state in the original call.

In accordance with another aspect of the disclosure a network structure is useful for a call leg move that includes a telecommunication network a capability abstracting layer and an application layer. The capability abstracting layer abstracts capabilities of the telecommunication network into independent functions and each independent function provides a corresponding interface to the application layer. Through invoking interfaces the application layer can provide services that are implemented by the independent functions. The capability abstracting layer includes both a call leg moving function and a call leg moving interface provided to the application layer with at least two parameters an identifier of a call leg to be moved and a destination call identifier.

In some cases the call leg moving interface is a newly added interface to Parlay OSA API with at least two parameters namely the identifier of the call leg to be moved and the destination identifier.

In some cases the call leg moving interface is a newly added open interface with at least two parameters namely the identifier of the call leg to be moved and the destination call identifier.

The call leg moving interface may further include one out parameter for showing a result of call leg move e.g. true or false.

In accordance with yet another aspect of the disclosure a method and network structure generally provide a call leg moving interface to an application layer. When an application wants to move a call leg it invokes the call leg moving interface to implement the call leg move. When a call leg is moved to another call the communication of this leg is not terminated for the reason of the call leg move thereby providing continuous communication service. As a result the data and states in the original call are maintained so communication continuity in the original call can be maintained. This result is beneficial for services with continuity requirements such as continuously charging etc.

The disclosed method and network structure generally provide a simple convenient easy to implement and easy to spread service for call leg moves from one call to another.

The disclosed method and network structure will now be described more fully hereinafter with reference to the accompanying drawings in which preferred embodiments thereof are shown. The disclosed method and network structure may however be embodied in many different forms and should not be construed as limited to the embodiments set forth herein. Rather these embodiments are provided so that this disclosure will be thorough and complete and will fully convey the scope of the invention to those skilled in the art. Like numbers refer to like elements throughout.

Disclosed herein is a method and network structure that generally provide an open interface for call leg moving to applications. Through the open interface an application implements some services with relational function including call leg moving service such as call hold and call moving etc.

Each independent function includes some small functions. In the disclosed method and network structure a call leg moving function is newly added in capability abstracting layer and the call leg moving interface corresponding to the call leg moving function and its parameters are added. The call leg moving interface is used to provide newly added call leg moving function to application layer. The parameters of the call leg moving interface at least include the interface reference parameters which are the call leg identifier to be moved and the destination call identifier to be moved to. The interface reference parameters further include one output parameter for showing the moving result. Referring to in this embodiment the call leg moving function is one part of the whole call control function.

In this embodiment a call leg moving interface may be implemented by defining a new IrpMultiPartyCall open interface. The IrpMultiPartyCall interface has one movelegmethod with two parameters destCall in IpMultiPartyCall and legID TpCallLegIdentifier. The call leg moving function is implemented by this IrpMultiPartyCall interface where the destCall in IpMultiPartyCall which is the interface reference of the destination call that the call leg will be moved to is the identifier of the destination call and the legID TpCallLegIdentifier which is the identifier of the call leg to be moved includes an ID and an interface reference of the call leg. The IrpMultiPartyCall interface further has output parameter which is a Boolean value in this embodiment. After the IrpMultiPartyCall interface is invoked this output parameter is used for showing the result of call leg move. When it is a true value it shows that the call leg move is successful. When it is a false value it shows that the call leg move failed.

In other embodiments of the disclosed method and network structure the call leg moving function can be added to an existing interface that may be implemented as follows.

In the Parlay API multiparty call the call leg moving function is added to the IpMultiPartyCall interface in order to implement making a call leg move from one call to another. The IpMultiPartyCall interface includes a moveleg method with parameters destCall in IpMultiPartyCall and legID in TpCallLegIdentifier. The destCall in IpMultiPartyCall which is the interface reference of the destination call that the call leg will be moved to is used as identifier of the destination call. The legID TpCallLegIdentifier which is the identifier of the call leg to be moved includes an ID and an interface reference of the call leg. Also the IpMultiPartyCall interface further has a output parameter which is a Boolean value in this embodiment. After the IrpMultiPartycall interface is invoked this output parameter is used for showing the result of call leg move. When it is a true value it shows that the call leg move is successful. When it is a false value it shows that the call leg move failed.

Step creates a call leg moving interface and its parameters for moving a call leg from the original call to a destination call. The parameters at least include the interface reference parameters which are the call leg identifier to be moved and the destination call identifier to be moved to. The parameters further include an output parameter which is used to show the result of the call leg move.

In step when an application wants to move a call leg the interface reference parameters are decided according to the call leg to be moved and the destination call that the call leg will be moved to and the application invokes the call leg moving interface with the interface reference parameters. And then the connection between the call leg and the original call is broken by the call leg moving interface and the voice channel resource occupied by the call leg in the original call is released. Later a voice channel resource in the destination call is allocated to the call leg and the call leg is moved to the destination call. Finally a result of the call leg move is returned to the application.

In step the application notifies the original call that a call leg will be moved to the destination call.

In step the original call breaks the voice channel resource occupied by the call leg. The original call identifier in the call message is changed to the destination call identifier and then a call leg move request is sent to the destination call where the call messages at least include the call identifier the media type the charging policy and the terminal information. Changing the belonging of the leg is implemented by changing the call identifier of the call messages. In this embodiment the media type the charging policy and the terminal information are kept unchanged.

In step having received the call leg move request from the original call the destination call determines whether there is enough voice channel resource to allocate a voice channel to the call leg. If there is a voice channel is allocated to the call leg and the call leg move is successful. Otherwise the call leg move failed.

In step based on the result of step the destination call will notify the result to the original call and then the original call will notify the application.

It can be seen from the description above that the call leg moving method may proceed as follows break the voice channel resource occupied by the call leg in the original call change messages related to the original call to messages related to the destination call then allocate voice channel resource in the destination call to the call leg which makes that the call leg can communicate with other call legs in the destination call. In this embodiment while the call leg is moved the call leg state and data in the original call are kept unchanged and the call leg is in a suspended state in the original call so as to hold this call leg in the original call. At step it is informed to the user terminal corresponding to the call leg that the call leg will be moved to the destination call in order that the user terminal can understand its call environment in time.

Two pre conditions are satisfied to implement the call leg moving function. First the call leg breaks connection of the resource having been allocated by the original call. Secondly the destination call is created before the call leg moves to it.

In a multiparty chat service on a Web page is used to describe an application detail in accordance with one embodiment.

A Web multiparty chat service provides a Web page through which multiparty calls can be created and all current calls and the call parties in each call can be seen and managed.

As shown on the left side of in the call before a call leg is moved out the user with identifier has communicated 9 minutes and is at the connection state. The user with identifier has communicated 2 minutes and is at the connection state. The user with identifier has communicated 3 minutes and is at the connection state. The user with identifier has communicated 5 minutes and is at the connection state. In the call before a call leg is moved in the user with identifier has communicated 5 minutes and is at the connection state. The user with identifier has communicated 2 minutes and is at the connection state and the user with identifier has communicated 5 minutes and is at the connection state.

During the call when user or other authenticated persons drag the user call leg from the call to the call it is equivalent that user or other authenticated persons send out a call leg move request and then the application will invoke the call leg moving interface to perform the call leg move.

As shown in the right side of after the call leg has been moved the user in the call is at a hold state and its call leg is suspended so it cannot communicate with the other three users in the call but its call messages are kept unchanged in the call . The user is connected to the call and can communicate with the user or .

When the user has finished the communication in the call it can be returned to the call and communicates with users or continuously because its call messages such as the media type and the charging information are kept unchanged during departure.

When the call leg of the user in the call is at a suspended state it can be released at any time. This means that the user is disconnected with the call. Later if the user wants to join the call again user should create the connection again.

In steps user A invokes service application on a Web page and initiates a multiparty call request. The application creates a multiparty call with the call identifier MPCC Call and then according to the calling number set by user A the MPCC Call creates a call leg with the identifier callLeg for user A.

In steps user B invokes service application on a Web page and initiates another multiparty call request on a Web page. The application creates a multiparty call with the call identifier MPCC Call and then according to the calling number set by user B the MPCC Call creates a call leg with the identifier callLeg for user B.

In steps while the call is in progress user A drags the callLeg from MPCC Call to MPCC Call on the Web page and then the Application notifies MPCC Call that callLeg needs to be moved to MPCC Call.

In steps after having received the move leg notification MPCC Call obtains the call leg to be moved according to the legID in TpCallLegIdentifier and notifies user of callLeg that the call leg will be moved from MPCC Call to MPCC Call. Then MPCC Call breaks the resource of callLeg allocated by MPCC Call. From now on callLeg is suspended and cannot communicate with other parties of MPCC Call.

In step MPCC Call notifies callLeg to update its call message. Those messages related to MPCC Call are changed to messages related to MPCC Call such as call identifier and the media resource channel etc. Other messages such as media type charging policy terminal information etc. are kept unchanged.

In step MPCC Call obtains the destination call MPCC Call that the call leg callLeg will be moved to according to the destCall in IpMultiPartyCall and then MPCC Call notifies MPCC Call the callLeg to be joined to MPCC Call and transfers the call leg identifier to MPCC Call.

In steps after having received the move leg request from MPCC Call MPCC Call allocates resource to callLeg and will report the allocation result i.e. true or false to MPCC Call. If the resource allocation is successful callLeg can communicate with other legs in MPCC Call. Whether the resource allocation is successful depends on whether there are enough resources in MPCC Call and whether MPCC Call accepts the callLeg.

In step after having received the result from MPCC Call MPCC Call determines whether the call leg move is successful. If it is successful MPCC Call will return a true value to the application and otherwise a false value.

Although a number of embodiments of the disclosed method and network structure are described above it is apparent that various modifications and changes can be made within the spirit and scope of the present invention.

