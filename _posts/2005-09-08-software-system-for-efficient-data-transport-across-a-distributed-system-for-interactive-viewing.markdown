---

title: Software system for efficient data transport across a distributed system for interactive viewing
abstract: The server performs the one or more operations on the graphics data to obtain resultant graphics data, and, transmits the resultant graphics data to the client system.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08035636&OS=08035636&RS=08035636
owner: Oracle America, Inc.
number: 08035636
owner_city: Redwood City
owner_country: US
publication_date: 20050908
---
This invention is related to the field computer graphics and more particularly to a system and method for communicating graphic data through a network.

Computer networks permit the distribution of computational labor across a number of computers. One computer a server may be configured to provide computational services to other computers clients . In particular a server may be specially configured to store and maintain graphics data such as scene graphs for clients. A client may send requests for graphics data to the server. The server may receive the requests and send back the requested graphics data through the network. Since the graphics data e.g. a portion of a scene graph may be voluminous and complex the client may need to be well endowed with resources such as a powerful host processor a powerful graphics accelerator and high network access bandwidth in order to render and display the graphics data with a latency that is acceptable to the user. Unfortunately many computer system are not so well endowed. There exists a need for a system and methodology of serving graphics data especially scene graph data to clients with a wide variety of processing and rendering capabilities.

In one set of embodiments a server may be configured to implement a method for communicating graphics data to clients through a network. The method may involve the following actions. The server may receive a request for graphics data from a client system through a network. The request may include client description data which describes capabilities of the client system. The server may access the requested graphics data from an augmented scene graph. The augmented scene graph may be stored in a system memory of the server.

The server may determine which one or more operations from a set of possible operations are to be performed on the graphics data based on the client description data. The set of possible operations may include 

The server may perform the one or more operations on the graphics data to obtain resultant graphics data and transmit the resultant graphics data to the client system through the network.

In some embodiments the set of possible operations may further include c culling the view limited compiled graphics data with a view frustum to obtain state sorted graphics data. In one embodiment the set of possible operations may yet further include d rendering the state sorted graphics data to obtain rendered images.

The server may generate the augmented scene graph by expanding a preexisting scene graph S. The process of expanding the scene graph S may include 

In one set of embodiments the processes of receiving accessing determining performing and transmitting are implemented as part of a graphics application programming interface API e.g. as part of a scene graph based graphics API such as Java3D .

The client description data may describe capabilities of the client system e.g. capabilities including 

In one embodiment the process of accessing the requested graphics data from the scene graph may include generating a copy of a subgraph of the scene graph specified by the request. The server may remove portions of data from said copy until 

Alternatively if the client system does not have graphics rendering support the server may remove portions of data from said copy until 

In some embodiments the resultant graphics data may include level of detail nodes. The process of transmitting the resultant graphics data may include transmitting Shape3D nodes under each level of detail node in order of lowest resolution to highest resolution. Thus the client system may immediately begin to display images corresponding to the lower resolution Shape3D and then successively refine.

Furthermore the resultant graphics data may include texture hierarchies. Thus the process of transmitting the resultant graphics data may also include transmitting layers in each texture hierarchy in order from lowest resolution to highest resolution.

The client system may render the resultant graphics to obtain images unless the resultant graphics data already are images . The client system may display the images on a display device of the client system.

The one or more operations performed on the graphics data may include a larger number of operations if the client description data indicates a user preference for speed than if the client description data indicates a user preference for image quality. The larger number of operations may serve to reduce the size of the data to facilitate faster transmission through the network and or faster processing and rendering at the client.

In another set of embodiments a server may implement a method for communicating graphics data to a plurality of clients through a network as follows. The server may receive a request for graphics data from a client system through the network. The request may include client description data. The client description data may contain values characterizing processing and graphics rendering capacities of the client system.

The server may access the requested graphics data from an augmented scene graph in response to the request.

The server may determine which one or more operations from a set of possible operations are to be performed on the graphics data based on the client description data. The set of possible operations may include 

The server may perform the one or more operations on the graphics data to obtain resultant graphics data and transmit the resultant graphics data through the network to the client system.

In some embodiments the set of possible operations may further include culling the view limited compiled graphics data with a view frustum to obtain state sorted graphics data. The set of possible operations may yet further include rendering the state sorted graphics data to obtain rendered images.

In one embodiment the server may repeat the above described processes of receiving accessing determining performing and said transmitting for each of a plurality of requests asserted by a plurality of client systems.

It is noted that any or all of the method embodiments described herein may be implemented in terms of program instructions and the program instructions may be stored on any of a wide variety of computer readable memory media. Examples of memory media include 

It is further noted that program instructions implementing any or all of the methods described herein may be transmitted through any of various transmission media or combinations thereof and thereby made available to server systems and client systems. Examples of transmission media include 

As used herein the term transmission medium includes computer networks such as local area networks or wide area networks. For example program instructions implementing one or more of the embodiments described herein may be distributed to servers and or clients through a computer network such as Internet.

It is further noted that program instructions implementing any or all of the method embodiments described herein may be stored in the memory of a computer system. A processor of set of processors of the computer system may be configured to read and execute the program instructions of the memory in order to enact the method embodiment s .

While the invention is described herein by way of example for several embodiments and illustrative drawings those skilled in the art will recognize that the invention is not limited to the embodiments or drawings described. It should be understood that the drawings and detailed description thereto are not intended to limit the invention to the particular form disclosed but on the contrary the intention is to cover all modifications equivalents and alternatives falling within the spirit and scope of the present invention as defined by the appended claims. The headings used herein are for organizational purposes only and are not meant to be used to limit the scope of the description or the claims. As used throughout this application the word may is used in a permissive sense i.e. meaning having the potential to rather than the mandatory sense i.e. meaning must . The phrase A includes B is to be interpreted as A includes B but is not limited to B .

A server and a number of clients C C . . . C N are configured for communicating through a computer network as illustrated in where Nis a positive integer. The number Nmay take any value subject to the limitations imposed by fundamental constraints such as server processing bandwidth server memory capacity network bandwidth etc.

The server may include one or more processors and memory as shown in . The memory may be configured to store program instructions and data. The one or more processors may be configured to read and execute the program instructions from the memory . The memory may include any of various kinds of random access memory RAM and read only memory ROM .

The network interface device is configured for coupling to the computer network and allows the server to communicate with other devices through the computer network. The storage devices may include devices such as hard disks compact disk CD drives digital versatile disk DVD drives floppy drives magnetic tape drives etc.

The client C k may include one or more processors and memory as shown in . The memory may be configured to store program instructions and data. The one or more processors may be configured to read and execute the program instructions from the memory . The memory may include any of various kinds of random access memory RAM and read only memory ROM .

The client C k may also include a network interface device e.g. an Ethernet card . The network interface device is configured for coupling to the computer network and allows the client to communicate with other devices through the computer network.

The client C k may also include one or more storage devices such as hard disks CD ROM drives floppy drives magnetic tape drives .

The client C k may also include a graphics accelerator or a set of graphics accelerators configured to accelerate graphics computations especially 3D graphics computations. The graphics accelerator may be configured to receive graphics data and to perform rendering computations on the graphics data in order to generate a video output stream. The video output stream may be used to drive the display device s . The display device s may include devices such as monitors projectors or head mounted displays.

It is noted that graphics accelerators may be evaluated based on certain performance features such as texture memory capacity and triangle rate capacity.

The server and the clients C C . . . C N are configured to execute software applications. Some of the software applications may be configured for client server based operation. Thus an application may include a server component configured to execute on the server and a client component configured to execute on a client. The client component interacts with the server component to accomplish desired processing operations. Furthermore the server component may be configured to interact with client components executing on a number of different clients.

The server component of an application may be referred to simply as the server application . Similarly the client component of the application may be referred to simply as the client application .

In addition the server and the clients may each be configured with a software infrastructure that performs a host of basic functions. For example each software infrastructure may include a network operating system a scene graph based graphics API i.e. a graphics API that is configured to operate using scene graphs and perhaps one or more other graphics APIs such as OpenGL and DirectX . API is an acronym for application programming interface . Java3D is an example a scene graph based graphics API.

The client applications and the server application may rely on the software infrastructures to communicate with one another.

As noted above part of the software infrastructure at the server and at each client C k may be a scene graph based graphics API. The scene graph based graphics API executing on the server may be referred to herein as the server interface . The scene graph based API executing on a client application may be referred to herein as the client interface . In one set of embodiments the scene graph based graphics API may be implemented as an extension to existing Java3D .

The server software system is configured to communicate with the client software system through the network . The operating systems and may be specially configured to facilitate this communication.

The server application may create a scene graph S. The scene graph S may be stored in server memory .

A scene graph contains a description of a scene including geometric data and attribute information such as texture and material properties . Scene graphs and their use in rendering 3D virtual worlds are well known to graphics programmers and especially to users of Java3D .

The server interface may expand the scene graph S e.g. during an initialization phase into an augmented scene graph S . In particular the server interface may generate the augmented scene graph S by expanding 

Thus the geometric object or objects corresponding to the Shape3D node X will be represented at two or more different resolutions. Resolution may be measured in terms of number of vertices or number of triangles. 

The lossy geometric compression algorithm may be realized by any various known algorithms. For example the techniques described in one or more of the following articles may be used to implement the lossy geometric compression 

In some embodiments an LOD node may itself perform steps 2 and 3 . In Java3D nodes may include program code.

There is no requirement that all Shape3D nodes in the scene graph S be expanded. In one set of embodiments the server application or client application may specify which Shape3D nodes in the scene graph S are to be expanded. For example each Shape3D node in the scene graph S may include an expansion control bit. The server application may set the expansion control bit of a Shape3D node equal to one if the Shape3D node is to be expanded and to zero if not. The server interface may check the expansion control bit of each Shape3D node to determine if the node should be expanded.

The server interface may expand a texture object Y into a hierarchy of texture information e.g. a mipmap by applying a lossy texture compression algorithm to the texture object Y one or more times. The hierarchy may include the texture object Y as its highest resolution level. The hierarchy also includes one or more levels at lower resolutions. Thus the original texture object Y will be represented at two or more different resolutions.

There is no requirement that all texture object nodes in the scene graph S be expanded. In one set of embodiments the server application or client application may specify which texture objects in the scene graph S are to be expanded. For example each texture object in the scene graph S may include an expansion control bit. The server application may set the expansion control bit of a texture object equal to one if the texture object is to be expanded and to zero if not. The server interface may check the expansion control bit of each texture object to determine if it should be expanded.

The nodes of a scene graph may be classified as leaf nodes or group nodes. Group nodes can have zero or more children. Leaf nodes have no children.

For each group node G in the augmented scene graph S let Sdenote the subgraph of S whose root is the group node G. In other words the subgraph Sincludes the group node G and everything under the group node G.

Let MAXdenote the subgraph that would be obtained from subgraph Sby removing from each LOD node of the subgraph Sall but the highest resolution Shape3D node and by removing from each texture hierarchy of the subgraph Sall but the highest resolution level.

Let MINdenote the subgraph that would be obtained from subgraph Sby removing from each LOD node of the subgraph Sall but the lowest resolution Shape3D node and by removing from each texture hierarchy of the subgraph Sall but the lowest resolution level.

The server interface may traverse the augmented scene graph S e.g. during an initialization phase in order to perform the following computations. For each group node G in the augmented scene graph S the server interface may compute 

The maximum vertex count is defined as the sum of a the number of vertices in each unexpanded Shape3D node of the subgraph Sand b the number of vertices in the Shape3D node of maximum resolution underneath each LOD node in the subgraph S. In other words the maximum vertex count corresponds to the number of vertices in the subgraph MAX.

The minimum vertex count is defined as the sum of a the number of vertices in each unexpanded Shape3D node of the subgraph Sand b the number of vertices in the Shape3D node of minimum resolution underneath each LOD node in the subgraph S. In other words the minimum vertex count corresponds to the number of vertices in the subgraph MIN.

The maximum texture size is defined as the sum of a the size of each unexpanded texture object of the subgraph Sand b the size of the texture object of maximum resolution from each texture hierarchy in the subgraph S. In other words the maximum texture size corresponds to a sum of the sizes of texture objects in the subgraph MAX.

The minimum texture size is defined as the sum of a the size of each unexpanded texture object of the subgraph Sand b the size of the texture object of minimum resolution from each texture hierarchy in the subgraph S. In other words the minimum texture size corresponds to a sum of the sizes of texture objects in the subgraph MIN.

The maximum memory footprint is defined as the size of the subgraph MAX i.e. the number of bytes or words required to store the subgraph MAXin memory.

The minimum memory footprint is defined as the size of the subgraph MIN i.e. the number bytes or words required to store the subgraph MINin memory.

Of course the server interface does not need to extract MINand MAXfrom subgraph Sin order to compute the above maximum and minimum values. Instead the server interface may compute all the maximum and minimum values by accumulating the respective sums in a single traversal of the subgraph S. For example in one embodiment when the traversal encounters an LOD node only the child Shape3D node of maximum resolution contributes to the maximum vertex count and only the child Shape3D node of minimum resolution contributes to the minimum vertex count. Similarly in that same embodiment when the traversal encounters a texture hierarchy only the highest resolution level contributes to the maximum texture size and only the lowest resolution level contributes to the minimum texture size.

During an execution phase the client interface executing on one of the client systems C C . . . C N may send a request for graphics data to the server interface in response to a client request. As illustrated in the request for graphics data may include client description data .

In one embodiment the request for graphics data may be a request for graphics data corresponding to a specified group node G. Thus the request may include a group node identifier .

The physical constraints A may be collected when the client interface is installed on the client system and or during an initialization phase of the client interface .

The client interface may estimate the network connection bandwidth B whenever a network connection has established.

The client C k may support a graphical user interface through which a user of the client system may specify the user preferences. The user preferences may include 

In response to receiving the graphics data request corresponding to group node G from a client C the server interface may copy the subgraph Sof the augmented scene graph S and remove data from the copy X if necessary to create a subgraph T C that can be processed and rendered sufficiently fast to satisfy the client s demands as expressed by the client description data . The processing and rendering of the subgraph T C may be performed on the client and or on the server depending on the computational power of the client system and the type of graphics rendering support available at the client system.

The server interface may store the subgraph T G as a reference graph for serving other clients having similar constraints.

If the client system C has software or hardware graphics rendering support the server interface may remove data from the copy X in order to achieve the conditions that 

If the client system C does not have any graphics rendering support the server interface may remove data from the copy X in order to achieve the conditions that 

The server interface may traverse the copy X one or more times to remove data until the conditions Ak Bk and Ck are satisfied where k 1 if the client system has graphics rendering support and k 2 otherwise.

The server interface may traverse the copy X in any of various orders e.g. in a depth first order a breadth first order etc. . In some embodiments the order of node traversal may be specified by the server application .

The server interface may update the maximum values of triangle count texture size and memory footprint for the copy X after each removal of data. The traversal may be stopped early if and when the conditions Ak Bk and Ck are satisfied. If the conditions Ak Bk and Ck are not satisfied after having completed the first traversal a second traversal may be performed to

The second traversal may be stopped early if and when the conditions Ak Bk and Ck are satisfied. If the conditions Ak Bk and Ck are not satisfied after having completed the second traversal a third traversal may be performed and so forth until the conditions Ak Bk and Ck are satisfied.

The state of the copy X when the data removal process described above has completed is taken to be the subgraph T C .

In one alternative set of embodiments the server interface may traverse the copy X only once. Upon encountering in this traversal an LOD node having at least two Shape3D nodes as children the server interface may 

Furthermore upon encountering a texture hierarchy having at least two levels the server interface may 

The traversal of the copy X may be terminated early if at any time the conditions Ak Bk and Ck are satisfied. The state of the copy X when this data removal process has completed is taken to be the subgraph T C .

After having created the subgraph T C the server interface may send the subgraph T C to the client interface through the network if 

The client system may receive the subgraph T C and render the subgraph in order to generate images. The images may used to drive display device s .

In one embodiment the client system C may be declared to have a sufficiently large computational power to process the subgraph T C if the computational power is large enough to process the subgraph T C within the client frame period i.e. the reciprocal of the client s display frame rate or some predefined scalar multiple of the client frame period. Furthermore the client s network connection bandwidth may be declared to be sufficiently large to deliver the subgraph T C in a timely fashion if the client s network bandwidth is large enough to deliver the subgraph T C to the client within a maximum acceptable wait time T.

3D Shape nodes under a given LOD node of the subgraph T C may be sent to the client C in the order from lowest resolution to highest resolution. Similarly the texture layers within a given texture hierarchy of the subgraph T C may be sent to the client in the order from lowest resolution to highest resolution. This ordering strategy enables the client to quickly start displaying low resolution objects and then to successively refine the scene with higher resolution objects as time progresses.

If the client system C does not have a sufficiently large computational power to process the subgraph T C or the client s network connection bandwidth is not sufficiently large to the deliver the subgraph T C in a timely fashion the server interface may compile the subgraph T C to obtain a compiled subgraph. The compiled subgraph takes up less memory than the subgraph T C and takes less time to process than would the subgraph T C . After having generated the compiled subgraph the server interface may send the compiled subgraph to the client through the network if 

The client may receive the compiled subgraph and render the compiled subgraph in order to generate images. The images may be used to drive display device s .

If the client system C does not have a sufficiently large computational power to handle the compiled subgraph or the client s network connection bandwidth is not sufficiently large to deliver the compiled subgraph in a timely fashion the server interface may operate on the compiled subgraph to remove nodes that are not visible to the user based on the client s view information D e.g. the direction of gaze and virtual position of the user thereby obtaining a view limited compiled subgraph. The view limited compiled subgraph takes up less memory than the compiled subgraph and takes less time to process than would the compiled subgraph. After having generated the view limited compiled subgraph the server interface may send the view limited compiled subgraph to the client C through the network if 

The client interface may send view information updates to the server interface whenever the view information changes e.g. when the user s direction of gaze changes or when the user s virtual positions changes . The server interface may use the view information updates to generate subgraph updates. The subgraph updates may include nodes that need to be added to the view limited compiled subgraph and specifications of nodes that need to be removed from the view limited compiled subgraph.

The server interface may send the subgraph updates to the client system so that the client system may update its copy of the view limited compiled subgraph.

If the client system C does not have a sufficiently large computational power to handle the view limited compiled subgraph or the client s network connection bandwidth is not sufficiently large to deliver the view limited compiled subgraph in a timely fashion the server interface may perform view frustum culling and scene traversing on the view limited compiled subgraph in order to obtain a state sorted render graph. A specification of the view frustum may be provided as part of the client description data . The server interface may send the state sorted render graph to the client through the network if 

If the client system C does not have a sufficiently large computational power to handle the state sorted render graph or the client s network connection bandwidth is not sufficiently large to deliver the state stored render graph in a timely fashion or the client system does not have graphics rendering support the server interface may render the state sorted render graph to generate images corresponding to the client s view information. The server interface may send the images to the client.

Thus in summary the server interface may send graphics data to the client C in various formats depending on the client s capabilities as expressed by the client description data. The formats include 

High end workstations with excellent network connections typically will be able to handle format 1 . Workstations with more modest network connections may be supplied with graphics data in format 2 . Client systems with lower host computing power may be supplied with graphics data in format 3 . Client systems with insufficient computing power to process even a view limited compiled subgraph may be supplied with graphics data in format 4 . The lowest end devices e.g. mobile devices or hand held devices without graphics rendering support may be supplied with graphics data in format 5 .

Note that the time required for a given client to generate a rendered image decreases from format 1 to format 5 . If the user has declared a preference for speed over quality the server may select the smallest integer k so that the client is guaranteed to be able to render the data in format k within the display frame time and then send the data to the client using format k . If the user preference is for quality over speed then the server interface may send the data in format j instead where j is the smallest integer so that the client is guaranteed to be able to render a frame within some maximum time the user deems to be tolerable. For example for a CAD application a user may be willing to wait for an image no more than 10 seconds. Because the display frame time is less then the maximum tolerable time the integer k is greater than or equal to j.

The methodology described above simplifies the technical complications in providing 3D datasets across a distributed environment to heterogeneous clients ranging from mobile devices to powerful workstations.

In some embodiments the server interface and client interface may be implemented as a modification to the Java 3D API.

In one set of embodiments a server may be configured to implement a method for communicating graphics data to clients through a network as shown in . The method may involve the following actions.

At the server may receive a request for graphics data from a client system through a network. The request may include client description data which describes capabilities of the client system.

At the server may access the requested graphics data from an augmented scene graph. The augmented scene graph may be stored in a system memory of the server.

At the server may determine which one or more operations from a set of possible operations are to be performed on the graphics data based on the client description data. The set of possible operations may include 

At the server may perform the one or more operations on the graphics data to obtain resultant graphics data.

The server may generate the augmented scene graph by expanding a preexisting scene graph S e.g. as illustrated in the embodiment of .

In one set of embodiments the processes of receiving accessing determining performing and transmitting are implemented as part of a graphics application programming interface API e.g. as part of a scene graph based graphics API such as Java3D .

The client description data may describe capabilities of the client system e.g. capabilities including 

In some embodiments the server may determine if the client has software and or hardware graphics rendering support from rendering support information included in the client description data as indicated at of . If the client has graphics rendering support the server may remove portions of the graphics data until client constraints are met as indicated at A. If the client does not have graphics rendering support the server may remove portions of the graphics data until server constraints are met as indicated at B.

In one embodiment the graphics data request sent by the client system may specify a subgraph of the augmented scene graph. The process of accessing the requested graphics data from the scene graph may include generating a copy of the subgraph of the augmented scene graph specified by the request. If the client system has graphics rendering support the server may remove portions of data from said copy until 

The triangle count the texture memory capacity and the system memory amount of the client system may be determined from the client description data.

Alternatively if the client system does not have graphics rendering support the server may remove portions of data from said copy until 

In some embodiments the resultant graphics data may include level of detail nodes. Level of detail nodes are well known to graphics programmers. The process of transmitting the resultant graphics data may include transmitting Shape3D nodes under each level of detail node in order of lowest resolution to highest resolution. Thus the client system may immediately being to display images corresponding to the lower resolution Shape3D and then successively refine.

Furthermore the resultant graphics data may include texture hierarchies. Thus the process of transmitting the resultant graphics data may also include transmitting layers in each texture hierarchy in order from lowest resolution to highest resolution.

The client system may render the resultant graphics to obtain images unless the resultant graphics data already are images . The client system may display the images on a display device of the client system.

The one or more operations performed on the graphics data may include a larger number of operations if the client description data indicates a user preference for speed than if the client description data indicates a user preference for image quality. The larger number of operations may serve to reduce the size of the data to facilitate faster transmission through the network and or faster processing and rendering at the client.

In another set of embodiments a server may implement a method for communicating graphics data to a plurality of clients through a network as illustrated in .

At the server may receive a request for graphics data from a client system through the network. The request may include client description data. The client description data may contain values characterizing processing and graphics rendering capacities of the client system e.g. as variously described above.

At the server may access the requested graphics data from an augmented scene graph in response to the graphics data request.

At the server may determine which one or more operations from a set of possible operations are to be performed on the graphics data based on the client description data. The set of possible operations may include 

At the server may perform the one or more operations on the graphics data to obtain resultant graphics data.

In some embodiments the set of possible operations may further include culling the view limited compiled graphics data with a view frustum to obtain state sorted graphics data. The set of possible operations may yet further include rendering the state sorted graphics data to obtain rendered images.

In one group of embodiments the server may repeat the above described processes of receiving accessing determining performing and said transmitting for each of a plurality of graphics data requests asserted by a plurality of client systems as illustrated at of . In one embodiment the server may cache i.e. save a copy of the resultant graphics data which was generated in response to request from a first client and then serve portions of the resultant graphics data to other clients having similar constraints in response to requests from those other clients.

It is noted that any or all of the method embodiments described herein may be implemented in terms of program instructions and the program instructions may be stored on any of a wide variety of computer readable memory media. Examples of memory media include 

For example the program instructions may be distributed to customers by storing the program instructions on memory media and selling or otherwise distributing copies of the memory media.

It is further noted that program instructions implementing any or all of the methods described herein may be transmitted through any of various transmission media or combinations thereof and thereby made available to server systems and client systems. Examples of transmission media include 

As used herein the term transmission medium includes computer networks such as local area networks or wide area networks. For example program instructions implementing one or more of the embodiments described herein may be distributed to servers and or clients through a computer network such as the Internet.

It is further noted that program instructions implementing any or all of the method embodiments described herein may be stored in the memory of a computer system e.g. a computer system such as that illustrated in or in . A processor of set of processors of the computer system may be configured to read and execute the program instructions of the memory in order to enact the method embodiment s .

Various embodiments may further include receiving sending or storing instructions and or data implemented in accordance with the foregoing description upon a computer accessible medium. Generally speaking a computer accessible medium may include storage media or memory media such as magnetic or optical media e.g. disk or CD ROM volatile or non volatile media such as RAM e.g. SDRAM DDR SDRAM RDRAM SRAM etc. ROM etc. as well as transmission media or signals such as electrical electromagnetic or digital signals conveyed via a communication medium such as a network and or a wireless link.

The various methods as illustrated in the Figures and described herein represent exemplary embodiments of methods. The methods may be implemented in software hardware or a combination thereof. The order of method actions may be changed and various actions may be added reordered combined omitted modified etc.

Various modifications and changes may be made as would be obvious to a person skilled in the art having the benefit of this disclosure. It is intended that the invention embrace all such modifications and changes and accordingly the above description is to be regarded in an illustrative rather than a restrictive sense.

