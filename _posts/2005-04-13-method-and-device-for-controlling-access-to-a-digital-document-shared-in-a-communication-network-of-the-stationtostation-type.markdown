---

title: Method and device for controlling access to a digital document shared in a communication network of the station-to-station type
abstract: The invention relates to a central server stations controlling access to a collection of digital data created by a client station. The server station receives, from the client station, a request to validate a collection of digital data, where the request contains the collection which has a collection identifier and for each data item belonging to the collection, a data identifier designating said data item, and at least one representation of said data item, the representation being chosen depending on said data item and on the collection identifier. For each data identifier received, a representation of the data item is locally obtained depending on the data item and on the collection identifier of the received collection associated with the collection. A comparison is made between the received representation and the obtained local representation and, in a case where the comparison results in a match, the digital data item to be shared is validated.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07845000&OS=07845000&RS=07845000
owner: Canon Kabushiki Kaisha
number: 07845000
owner_city: Tokyo
owner_country: JP
publication_date: 20050413
---
The present invention relates to the control of access to a shared document in a communication network of the station to station or distributed type commonly referred to as the peer to peer topology type.

During the past few years station to station networks have become an alternative to the client server networks which have become widespread up to the present time. This is because through their distributed architecture station to station networks make it possible to share a large number of digital data between a large number of users without for all that requiring an expensive infrastructure.

In practice in a station to station network each station fulfills the role of client and server. Thus each station can request data or a digital document from any other station in the network and the exchange of data can take place directly from one station to another.

Hereinafter the term document or digital data applies both to images or digital videos or to digital text files or the like.

This means that the digital data received by a client station can then be served to other users by said client station.

The digital data accessed by many persons can therefore be replicated on several machines and served by more servers.

The system therefore adapts all alone to demand and the communication storage costs are distributed between all the servers.

On the other hand in a conventional client server system the data are served by a single server or by a set of machines fixed in advance.

The capacity of these conventional servers must be sized in advance which results either in oversizings the cost of the server is then too high or undersizings the data are not served sufficiently rapidly .

Another advantage of the station to station system is that the digital data are served directly from the machines of the users.

However station to station networks are unstable. This is because the client devices and consequently the server devices connect to each other and disconnect from each other periodically on the network thus making the presence of the data very haphazard. In addition the addresses of the client and or server devices are unpredictable and liable to be different at each connection.

As a result access to the contents in a communication network of the station to station type still constitutes a significant difficulty since the latency for obtaining the data is no longer simply due to the time necessary for recovering the data as in the conventional client server topology but also the search time for a server device having these data available.

According to the topology of the station to station network concerned this search phase may be not insignificant.

In the context of the invention the context is more precisely adopted of a communication system exchanging digital data by means of digital containers of these data.

For example the digital data are digital photographs images which can be represented in hierarchical storage format with multiple representations in terms of resolution and memory size .

A digital container of such data is for example a collection of digital photographs that is to say a container of references to these images where various sub parts or representations can be situated on different machines in the network.

The majority of station to station data exchange systems are intended for exchanging public data the whole world can access a shared data item.

The present invention is preferentially concerned with a particular context where the data exchanged are personal. It is a case for example of images or videos which a person wishes to share with his friends or family that is to say a restricted number of users. The data are then not public.

In this context it is necessary to have a system for restricting access to the data. A list of documents and an associated access list are grouped together in the collection. When sharing the collection is sent to all the addressees. Each one decides to accept the collection or not. If the addressee accepts the collection this supplements the local access list of the client machine for each of the documents contained. Likewise for the creator of the collection the new collection supplements the local access lists.

The control of access to the data from the client machines is based on the trust of a person who is sharing a personal data item with regard to an addressee who has received this data item the server of the addressee must in dealing with access to his machine and the validity of the requests comply with the restrictions proposed by the creator of the data. However the destination can apply a different limitation of access to the data which he has received.

A so called hybrid station to station system has the particularity of comprising a permanent server also referred to as a central server which can serve for registering users and controlling the connection of the client machines of these users.

For the purpose of increasing the availability of the digital data on the station to station network and thus promoting the broadcast service quality the central server can also store locally and temporarily limited versions of personal digital data.

The Applicant has posed the problem for itself of supplying access control as well as control of the sharing and distribution of the personal documents on the central server of a hybrid station to station network.

It relates in particular to an access control applicable to a permanent central storage server of a hybrid station to station network and independent of a particular user.

Thus it relates to a method of controlling access to a collection of digital data created by a client station the method being implemented on a central server station in a communication network of the hybrid station to station type.

E receiving from the client station a request to validate a collection designated by a collection identifier and comprising for each data item belonging to the collection a data identifier designating said data item and at least one chosen representation of said data item 

E for each data identifier thus received locally obtaining a representation of the data item associated with the said collection and

E comparing the representation thus received with the local representation and in the case of positive comparison validating said digital data item to be shared.

Such a method according to the invention thus makes it possible to ensure that the client station sending the validation request does indeed possess all the digital data in the collection to be shared on its machine and therefore that it does indeed have access to these digital data.

According to one embodiment of the invention the validation step E is followed by a step E of calculating a signature of said collection of digital data in the case of positive validation of each of the digital data belonging to the collection.

In practice the step E of calculating the signature of the collection is followed by a step E of sending this signature to the client station.

Thus the client station will easily be able to prove subsequently to any other client station in the network that the collection which it is sharing is valid.

According to another embodiment each collection of digital data is stored locally in response to a positive validation of each digital data item to be shared issuing from step E .

In this way the central server stores only valid collections which can be shared in the P2P network according to the control of the access rights set up.

According to yet another embodiment the step E of obtaining the representation of the data item associated with the collection comprises the following steps 

In the case of a negative local search at the end of step a the method also comprises the step E consisting of seeking a version of the digital data item identified by a data identifier on the network and step E consisting of locally storing said version thus obtained from a client station.

Thus the central server is ensured of locally storing versions of digital data referenced by the collections currently being validated. In addition by virtue of steps b and c the central server can verify the presence on the sending client station of the validation request and the integrity of the versions of the data referenced by the collection.

In practice the method also comprises a step of verifying the identity of the client station sending the validation request established by means of a chosen authentication function.

According to one characteristic of the invention in the case of negative comparison at step E the following steps are provided for 

In addition in the case of positive verification at the end of step 3 the step is provided consisting of obtaining a representation of said data item associated with said collection and the step consisting of inserting the representation of the data item thus obtained in the collection.

According to one important characteristic of the invention the method also comprises prior to step E the following steps relating to the creation of a collection of digital data on a client station intended to be validated by a server station in a communication network of the hybrid station to station type 

In the case of negative obtaining at the end of step E provision is made for seeking a collection identifier corresponding to a collection containing the data identifier and the identifier for the client station sending the validation request and substituting the collection identifier thus found for the representation of said digital data item.

The collection document intended to be validated by the central server is thus created according to a method compatible with the validation steps according to the invention implemented by the central server and mentioned above.

According to another embodiment the access control method also comprises a method of checking the integrity of a digital data item forming part of a collection of digital data created by a distant client station by means of a method mentioned above the integrity check method being implemented on another client station in a communication network of the hybrid station to station type characterized in that it comprises the following steps 

Another object of the present invention is a device for controlling access to a collection of digital data created by a client station belonging to a communication network of the hybrid station to station type.

Another object of the present invention is an information medium which can be read by a computer system possibly totally or partially removable in particular a CD ROM or magnetic medium such as a hard disk or a floppy disk or a transmissible medium such as an electrical or optical signal characterized in that it comprises instructions of a computer program permitting the implementation of a processing method of the type described above where this program is loaded into and executed by a computer system.

Finally an object of the present invention is a computer program stored on an information medium said program containing instructions permitting the implementation of a processing method of the type described above when this program is loaded into and executed by a computer system.

The present invention applies to any mono or multiresolution digital document. The description which follows describes the method of the invention relying on the example of multiresolution data but this is proposed only for the reasons of optimization of resources which is not directly related to the invention this is because the right of access to a document or to a sub part of a document is managed in the same way. The description is based on an example of an optimum system where the central server stores only low resolution versions small memory size of the digital data.

The system for which gives an overall view is composed of several entities connected in a network. The network such as the Internet allows client server architecture communications where each client station periodically accesses a central server station . Peer to peer connections amongst the client stations of the users are also made in order to exchange the data to be shared and this independently of the server. The users connect to the network with different methods for example high speed modems of the DSL type low speed or cable but also from mobile telephone sets for example of the GSM type. The network can just as well be a private local network LAN . The central server can also be composed of several servers coupled together and accessible from a single network address.

The client terminals or stations can communicate directly or by means of the central server . Each server can for example be a device as described in and comprise in particular a volatile data storage device referred to as a cache memory which may contain long life data such as images but also more volatile data such as address lists and a man machine interface which affords interaction with an administrator of this server.

The terminals can also be a device as described in but also a digital assistant or a photographic apparatus or a portable telephone. These appliances can be connected to various peripherals such as for example a digital camera or a scanner or any other image acquisition or storage means supplying multimedia data.

The computer appliances central server can execute an application computer software containing the algorithms of the invention. Each server comprises a display interface which may correspond to an Internet browser coupled to a Web server . The Web server is a conventional server such as Apache or Microsoft IIS executing software modules peculiar to the invention. According to another possibility the software and server are a single entity. The central server is also composed of a storage device such as a hard disk on which the data to be stored temporarily will be stored in particular the thumbnails relating to the digital photographs to be shared and a database containing unique identifiers of the various entities of the global system in particular the identifiers of the users images .

An apparatus implementing the invention is for example a microcomputer or a workstation. This apparatus is connected to various peripherals such as for example any image storage means connected to a graphics card and supplying multimedia data to the apparatus.

The communication bus affords communication and interoperability between the various elements included in the microcomputer or connected to it. The representation of the bus is not limiting and in particular the central unit is able to communicate instructions to any element of the microcomputer directly or by means of another element of the microcomputer .

The executable code of each program enabling the programmable apparatus to implement the processes according to the invention can be stored for example on the hard disk or in read only memory .

According to a variant the floppy disk can contain data as well as the executable code of the aforementioned programs which once read by the apparatus will be stored on the hard disk .

In a second variant the executable code of the programs can be received by means of the communication network via the interface in order to be stored in an identical fashion to that described previously.

The floppy disks can be replaced by any information medium such as for example a compact disk CD ROM or a memory card. In general terms an information storage means which can be read by a computer or by a microprocessor integrated or not into the apparatus possibly removable is adapted to store one or more programs whose execution enables the method according to the invention to be implemented.

In more general terms the program or programs can be loaded in one of the storage means of the apparatus before being executed.

The central unit controls and directs the execution of the instructions or portions of software code of the program or programs according to the invention instructions which are stored on the hard disk or in the read only memory or in the other aforementioned storage elements. On powering up the program or programs which are stored in a non volatile memory for example the hard disk or the read only memory are transferred into the random access memory RAM which then contains the executable code of the program or programs according to the invention as well as registers for storing the variables and parameters necessary for implementing the invention.

It should be noted that the communication apparatus comprising the device according to the invention can also be a programmed apparatus.

This apparatus then contains the code of the computer program or programs for example fixed in an application specific integrated circuit ASIC .

With reference to a collection list of identifiers of the images to be shared is a set of references on media contents image video sound with metadata. By extension a collection can contain collections referred to as sub collections .

In the description which follows the case is adopted of the sharing of a collection of digital images by an archiving system in a network of the peer to peer type.

Thus hereinafter the term multiresolution image will be given both to digital images with a multiresolution format such as the JPEG2000 format for example and single resolution digital images for example the jpeg format in this second case the concept of multiresolution is supported by the construction of independent files corresponding to different resolutions obtained from one and the same high resolution image file.

Each object corresponding to a digital image is identified by a data identifier created on the machine of the user. This data identifier is assigned by the client application even if it is not connected to the network. One solution consists of producing random numbers locally. Optionally these data identifiers can be unique in order to facilitate searches on the network. Tools well known to persons skilled in the art make it possible to generate data identifiers with a minute probability of duplication.

Images will likewise be defined by a data identifier by the application of the client as soon as a new image is added to a collection if the image is copied from an existing collection it will preserve the original data identifier . However a thumbnail has the same data identifier as an image. In order to precisely determine an object image or thumbnail the data identifier must be associated with a data typing the majority of the time this typing is implicit according to the requests sent over the network in the case of downloading the image is requested whilst the thumbnail is useful for simple display .

Each user also has a unique user identifier supplied by the central server during the process of registering the user. This property is useful for reducing to the minimum the risk of multiple registrations for the same user. In the preferred embodiment by purchasing the client software the purchaser registers his software and establishes with the central server an account which identifies this user. This account identified by the user identifier serves for a connection of the client either by the standard software or by an Internet browser.

The creation of a collection without right of access by a user does not come under the invention. There exist well known methods in the state of the art which deal with images and their association with image containers. For example the user can copy an image from the graphical interface of the operating system of his computer and deposit it in the graphical interface of the computer software implementing the invention. The user can structure his images collections and sub collections so as to finally to record each collection created in the form of a list of image identifiers of sub collections. Each collection can possibly comprise one or more metadata of small memory size for example a thumbnail representing the whole of the collection.

A user creates a collection C with addressees step E described with reference to . This collection C is then sent to the central server in a message . This message is for example formatted in XML mark up language such as SOAP and transported by the HTTP communication protocol in a request of the POST type.

In response to this validation request the central server validates the collection in accordance with step E the substeps of which are described with reference to . Where applicable the central server seeks the thumbnails which it is lacking locally.

A series of messages follows in order to send to the central server the thumbnails requested step E . These messages are for example HTTP PUT messages. Each message comprises a reference to the collection Cl the data identifier of the thumbnail and the thumbnail itself.

In practice it is a case of verifying the access rights for each file received and storing them in the local cache.

When all the thumbnails have been transmitted by the client station the latter can then request that a signature for the collection C be created for it step E . The message of the same type as then serves as a communication medium for obtaining the signature from the central server . The client station can thus update the signature field of the collection C and send the collection C to the addressees entered in the user identifier fields of the collection C. One alternative consists for the client station of sending a simple notification to the addressees indicating that the collection C is now available also on the central server.

Step E relating to the verification of the presence of all the image files in the local cache and the creation and sending of the signature of the collection and executed by the server is described with reference to .

In a first step E the collection headers are created the user enters a title the identifier of the author the date of creation are filled in. A new collection identifier is created.

The user next selects a list of images. It may be a case of images situated in collections already shared or new images of the user step E .

For each image step E the client obtains step E a data identifier it may be a case of the identifier of the image in the collection where it was selected or a new identifier if it is a case of a new image. A new identifier can be created by taking for example a random number with sufficient size to have a very small probability of obtaining the same identifier several times.

For each image it is necessary to create a unique representation for the current collection. Two types of representation are envisaged according to the possibility of obtaining locally or not a version of the current image.

In the case where a version of the image processed is present locally it is possible first of all to create a representation in the form of a signature of a version of the image. It is preferable to use a small version of the image in order to preserve acceptable performance during processing. For example the signature is a check sum of the thumbnail or a signature obtained by a hashing algorithm known in the state of the art e.g. MD5 applied to the thumbnail. The important thing is that this signature be created from a physical data item of the image which only a possessor of this image can obtain e.g. the data identifier is not sufficient since ill intentioned users could invent image identifiers without having these images in order to recover them fraudulently .

Next from the previous result associated with the collection identifier of the current collection a second signature is calculated by a hashing algorithm known in the state of the art e.g. MD5 .

This second signature is the representation which is unique for an image in a collection since it depends both on a signature of a version of the image and the collection identifier. It thus prevents copying by pirates of the elements in new collections granting them all the access rights these elements are solely valid in a single collection. In addition the use of a hash function which is non reversible does not enable any pirate to find the signature of a version of the image even knowing the representation and the collection identifier .

This representation will serve for the central server to verify the access rights of the sharer to exchange the images concerned but also subsequently for any peer client system to verify that the thumbnails which said peer system receives are valid see below .

In a variant it is possible to create and add to the collection a distinct representation for each resolution of the image this is because according to the type of image used the thumbnail is not necessarily a unique representation which can be obtained from any resolution of the image and then only the authenticity of the thumbnail and of the image version from which the thumbnail was created can alone be controlled. In this case in order to avoid downloading several resolutions of the same image the central server can decide to limit itself as described below to validating the content of a collection with regard to a single representation for example the one issuing from the thumbnail created with the high resolution version of the image the sharer is entrusted with the correct calculation of the other representations inserted in the collection.

In the case where no representation of the image to be shared is present locally it is possible to replace the representation of the collection with a collection identifier for another collection referred to again as the supplementary collection which attests to the right of access of the person to use the image. This is because there may be certain cases where the client station does not locally have images which he is authorized to see 

The data identifier and the representation obtained by one or other of the methods described above are then added to the collection in accordance with step E.

The user next gives addressees step E he can select persons in his address book or enter new names. If he has selected a name in the address book the user identifier of the user is known and is added to the list of addressees of the collection step E .

If the user enters a new name the system then interrogates the central server in order to obtain information on the addressee. If the addressee is a person recorded in the system the central server has allocated to him an identifier who can then be sent to the client station with all the associated information. The client station can then add the name in the address book. The new user identifier can then be added to the list of addressees of the collection.

In accordance with step E the collection thus created is sent to the central server . This collection is referred to as a temporary collection since it can subsequently be modified in particular by including therein the signature given by the server after validation and possibly the representations calculated from the versions of the thumbnails which the client machine lacks at the time of sharing see .

With reference to a description has been given of the functioning of the software executed on the central server when a client station requires a collection sharing and sends said collection to the central server step E for validation.

In practice the validation request comprises for each data item belonging to the collection a data identifier designating said data item and at least one chosen representation of said data item.

For example the connection to the central server is subjected to an authentication of the user user token parameter or user token in order to ensure the legality of the sharing procedure. This authentication can be carried out equally well by a Web client connection protected by SSL or by a client possessing the peer to peer software application protected SOAP messages from a pair user name pass word the central server authenticates the person and sends in response a token comprising a validity limit date and attesting to the identity of this person. This token can be sent in the form of a message or cookie for a Web connection and or in a response of the SOAP type to the software application of a peer.

By analyzing the collection received step E the central server is capable of knowing which are the new images from his data cache . The central server will use one of the methods of validating the data referenced in the collection according on the one hand to the presence of the thumbnails referenced in the collection in its cache and on the other hand according to the type of representation associated with each thumbnail.

If a thumbnail referenced in the collection by its data identifier is present in the cache it is a case of an image intended to be shared once again by the user the access rights can therefore be verified. Two cases are then distinguished according to the type of representation .

Case 1a the representation associated with the given identifier is the signature. In this case a reconstruction of the representation from the thumbnail present in the cache of the central server and the identifier of the collection is carried out for each data identifier applying the same steps as the client during the creation of the collection described above with reference to . This representation is compared with the representation entered in the collection received. A positive comparison result validates the fact that the user possesses all the known images present on the machine and therefore the fact that he has access to these images .

Case 1b for certain images in the collection the representation chosen is a collection identifier of another collection also referred to as a supplementary collection which attests to the access right of the person to use the image.

In this case the server validates the access rights from the known collection supplementary collection and then locally updates the new collection by recreating a representation representing a signature MD5 same algorithm as the client described with reference to or by recovering the signature of the thumbnail previously stored in order not to calculate it many times see below Case 2a .

If thumbnails referenced by the data identifier in the collection are not present in the cache the system must check whether the images are new. For this the server preserves the list of image identifiers which it has received coming from the clients this makes it possible to avoid the same identifier being used for several images unintentionally the data identifiers are created randomly by the clients or fraudulently a person seeks to replace an old image which has expired from the cache of the central server . This list of data identifiers used in the network can be recorded in a table in the database but also in an area of the memory of the server this area can be architectured so as to optimize the searches for identifiers . Two cases can once again be distinguished 

Case 2a if data identifiers are found in this list the previous case 1b applies. As an option the list of data identifiers can also preserve the result of the operation performed on the thumbnail checksum or MD5 hashing in which case Case 1a can be applied after calculating the signature applied to the signature of the locally known thumbnail associated with the collection identifier specific to the collection currently being validated.

Case 2b if data identifiers are not found in this list the corresponding images are considered to be new and the complete validation of the collection will occur once the central server has received all the thumbnails referenced by the collection step E detailed with reference to . This complete validation will comprise all the calculations necessary for obtaining the representation associated with each thumbnail and the comparison of the result with the representation stored in the collection received.

In the case of positive verification with regard to the validity of the collection step E the method passes to step E otherwise an error message is sent step E .

In accordance with step E the collection received possibly updated with the representations calculated by the central server thus validated is stored in a temporary area of the cache in order to be signed complete validation when all the thumbnails are received and validated.

The client station is next informed of the new procedure to be followed for concluding the validation of the collection either downloading the locally missing thumbnails step E at the end of a verification step indicating images in the collection which are not in the local cache step E Case 2b above or directly requesting a signature of the collection if all the thumbnails are already present in the cache step E .

With reference to a description has been given of the functioning of the software executed on the central server when a client station sends an image file following a collection sharing .

The user related to the client machine is authenticated the parameter user token of the request is checked in terms of content and expiry date step E .

In the case of negative authentication the method recommences with a new authentication attempt step E .

If not there is a check that the author of the collection is indeed the one who has sent the image step E .

The image received in this case a thumbnail for the requirements of sharing is recorded in the cache step E .

With reference to a description has been given of the functioning of the software executed on the central server when a client station requests the validation of the shared collection step E .

A necessary condition is that all the thumbnails be present in the cache of the central server step E .

In the negative an error message indicates that files are missing step E and it is possible to return to step E in order to request the missing images.

If the validation had not been ended at step E corresponding to the validation test calculation of the representation from the thumbnail and the collection identifier is repeated step E for the images received at step E. In a variant this validation test is directly performed for each image by the algorithm described with reference to when an image version is downloaded on the server in order to immediately eliminate any image received which is corrupted.

After having validated the collection verification of the list of images and list of addressees it is necessary to calculate a signature for the collection step E . The signature can be calculated by a conventional public key signature system an imprint of the data to be signed is calculated the author the list of images and representations and the list of addressees by an algorithm such as MD5 and then this imprint is encrypted with the private key of the central server by RSA.

The collection thus obtained and validated is definitive and can then be moved into a permanent area of the cache of the central server step E .

The signature and possibly the updates made in the collection is then sent back to the author of the collection step E .

All the station systems are able to request the public key from the central server in order to check the collections which they have received.

Thus with this key the client stations obtain the certified imprint of the collection and can compare it with an imprint created from the collection received if the comparison is identical the collection is authenticated.

Likewise the client stations can then authenticate the images which they receive from the collection. The various versions of the images are fixed and it is very easy to obtain a thumbnail from a version of the image. This thumbnail corresponding to an image received by the network can be used conjointly with the collection identifier in the same algorithm as the sharing one in order to calculate the type representation which should be identical to the value entered in the collection.

With reference to a description is given of the steps during the reception of a request to serve an image identified by the data identifier belonging to the collection step E .

The first step consists of validating the identity of the sender of the request step E expressed by a token identifying the user user token .

If the identification token is invalid the method recommences with another authentication attempt step E .

Then it is checked whether the image having the data identifier forms part of the list of images of the collection and whether the requester forms part of the list of addressees step E .

If the local collection does not authorize the requester to obtain the image the request is refused step E .

With reference to a description is given of an example of architecture of the software based on top of the Web server.

The purpose of the architecture proposed is to offer a central server which is as light as possible in order to limit its operating cost.

The database contains information necessary for the management of the users and their profiles a user has registered at least one client software application from a client station . It also contains the most dynamic data relating to the connectivity of the peers a client can obtain the connection information IP address port access through firewall of another client identified by a unique identifier. The database contains no indication on the location of the data on the network this management is considered to be totally distributed on the network and does not form part of the invention.

The cache memory contains the shared collections and versions of the associated images. Preferably only the thumbnails and an intermediate version of low resolution are available on the server. A simple cache management policy is implemented so that the lifetime of the collections is much greater than that of the thumbnails which is itself greater than that of the medium resolutions. For example a collection can be stored for several months or years the thumbnails several months and the intermediate versions a few weeks. At the same image resolution level a policy can be applied in order to count the number of accesses to an image and to store the greatly demanded images longer. In addition the central server as well as the peers can serve the images for users not having a client machine but simple Web browsers such accesses do not favor the replication of data on the peer to peer network and can be considered in the cache policy.

The central server is the first point of entry of the peers on the network. Once a peer is connected the communications can take place in station to station mode with other connected peers. The central server will usually be interrogated subsequently for requests for information on connectivity of the machines and for validation of the collection sharing. The downloading of images from this server for a new collection will decrease as the data are replicated on the peers.

The module D provides access to the collections and to the images of the cache for the client machines and for accesses from Web browsers. It supports the algorithms in . For the purpose of improving the performance in terms of reaction time of the service of the images this module D contains no connection with the database but interacts directly with the data of the hard disk and this is the reason why a Web server is optimized.

The module C supplements the previous one in the event of a problem e.g. an image is missing and makes it possible to resolve the resolutions of the locations of the images from connections present in the cache and information on the presence of the machines in the database.

The sender requests a token from the central server through a secure SSL connection by the module A. The latter checks its identity by asking it for a password. It can then give it a token created with the private key of the central server which encodes the identity of the sender. The token serves for any server on the network or which receives a request in order to thus validate the identity by decoding the token by virtue of the public key of the central server.

Signature user id IP address date The IP address corresponds to the address visible on the network of the machine to which the user is connected.

With reference to a description has been given of the steps performed by a client station of a peer to peer network at the end of the sharing of a collection of images validated by the central server.

The client station having available the peer to peer application has received a notification of the presence of a new collection intended for it. This notification can be made from a messaging system internal to the peer to peer network or external such as electronic messaging of the e mail type. Following this notification the client station receives the shared collection or knows a location on the network for example the central server where this collection can be recovered step E .

On reception of the collection the client station must verify the validity of this collection by virtue of the field of the collection which was decrypted with the public key of the central server step E .

If the validation is correct the collection is preserved and the user can then choose images to be displayed. For each image selected by the user step E a search on the network can be made by known means of the state of the art step E . On reception of any version of an image the client station must verify the integrity of the data received from any server station in the network and no doubt unknown to the client station step E .

For this the client station applies the algorithms presented in in order to calculate the representation from the received image of the network and the identifier of the current collection.

In practice the representation is calculated from the collection identifier and the data identifier of the image thus received step E .

According to step E if this first representation thus calculated is identical to a second representation present in the current collection identification collection then the image received is recognized as authentic. In this case it is kept locally step E . Otherwise the client station attempts to seek other server stations in the network offering unmodified versions of the required image.

