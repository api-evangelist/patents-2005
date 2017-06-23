---

title: Processing of messages to be transmitted over communication networks
abstract: The invention relates to processing, at a transmitting entity, messages to be transferred between a transmitting entity and a receiving entity. The method comprises: obtaining a message to be transferred to the receiving entity, defining a substantially unique identifier at least for one part of the message to be transferred, conditionally replacing said part of the message to be transferred with said substantially unique identifier, and forwarding the message for transfer to the receiving entity. Further the invention relates to processing, at a receiving entity, messages transferred between a transmitting entity and a receiving entity The method comprises: receiving a message transferred from the transmitting entity, the message comprising a substantially unique identifier as a substitute of a part of the message, and retrieving said substituted part of the message on the basis of said substantially unique identifier.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08150927&OS=08150927&RS=08150927
owner: 
number: 08150927
owner_city: 
owner_country: 
publication_date: 20051118
---
The invention relates to processing of messages that are to be transmitted over communication networks and particularly to such processing of e mails.

E mail traffic is one of the rapidly growing applications in mobile radio communication networks. E mails are downloaded to laptops or mobile terminals or other radio wireless communication devices through mobile communication networks.

Because available bandwidth is typically limited in mobile communication networks handling of large e mails and or e mails with attachments for example over 20 kB often leads to poor user experience due to long periods of time needed for downloading and sending e mails. Furthermore the user is often billed according to the amount of transferred data. Therefore it would be beneficial for the user to be able to minimise the amount of data that is transferred.

In the following terminology that is used for describing such methods is briefly discussed. This terminology will be adhered to in the rest of this document.

Currently optimisation is used only for downloading e mails whereas in sending of e mails only compression is currently used. Compression may be and often is used also for downloading e mails in addition to or instead of optimisation.

Two alternative setups are shown for the mobile terminal. In the first one the mobile terminal comprises an e mail client and an e mail proxy client that is connected to the e mail server and communicates with the e mail server by using POP IMAP or SMTP protocol. The e mail proxy and the e mail proxy client communicate with each other over the mobile radio network by using a proprietary e mail proxy protocol which protocol is configured to optimise the transfer of e mails to the e mail proxy client. The e mail proxy compresses e mail messages and the e mail proxy client decompresses them in the mobile terminal and provides them onwards to the e mail client . In addition to this the e mail proxy may optimise the emails to be downloaded by removing attachments from the e mails or replacing them with HTTP URIs HyperTexts Transfer Protocol Uniform Resource Identifier for allowing the user of the mobile terminal to download the attachments later.

E mails are sent from the mobile terminal through the e mail proxy client. The e mail proxy client compresses the messages and sends them in compressed form to the e mail proxy which decompresses them and sends them onwards to the email server in decompressed form.

In the second mobile terminal setup the mobile terminal comprises only an e mail client . Herein the e mail client communicates directly with the e mail proxy by using POP IMAP or SMTP protocol.

The disadvantage of the currently used solutions is that sent e mails are only compressed and not optimised. Further the web interface that is needed for optimising e mail downloads is not optimal. For example the e mail messages are not saved for offline use and a considerable amount of additional data needs to be sent for establishing the web interface www pages images etc. .

An object of the present invention is to provide a new solution for processing of messages that are to be transmitted between a transmitting entity and a receiving entity at least partially over communication networks.

One of the basic ideas of the invention is to replace parts of messages by substantially unique identifiers before transferring the messages over a communication network or a part of a communication network wherein may be a mobile network or a fixed line network. Thereby the amount of data to be transferred over the communication network can be reduced. This substantially unique identifier can then be used for retrieving the omitted part of the message in the receiving end.

According to a first aspect of the invention there is provided a method for processing messages to be transferred between a transmitting entity and a receiving entity at least partially over a communication network wherein the method comprises 

conditionally replacing said part of the message to be transferred with said substantially unique identifier and

According to a second aspect of the invention there is provided a method for processing messages transferred between a transmitting entity and a receiving entity at least partially over a communication network wherein the method comprises 

receiving at the receiving entity a message transferred from the transmitting entity the message comprising a substantially unique identifier as a substitute of a part of the message and

retrieving said substituted part of the message on the basis of said substantially unique identifier.

According to a third aspect of the invention there is provided a transmitting entity according to claim .

According to a fourth aspect of the invention there is provided a receiving entity according to claim .

According to a second aspect of the invention there is provided a computer program for a transmitting entity according to claim .

According to a second aspect of the invention there is provided a computer program for a receiving entity according to claim .

Dependent claims contain embodiments of the invention. The subject matter contained in dependent claims relating to a particular aspect of the invention is also applicable to other aspects of the invention.

The invention suits well for accelerating e mail transmission but it can be used also in connection with transferring any other messages or content that can be divided into more than one part such as messages comprising distinctive files and or distinctively viewable content. Such other messages may be for example Multimedia Messaging Service MMS messages or other downloadable content such as mobile Java games. Further in addition to optimising downloading of e mails or other messages the invention can be used for optimising sending of e mails or other messages from a mobile terminal.

The methods of the invention may be used even though there would not be a specific need to accelerate the data transmission. For example if the user is billed by the amount of transferred data the user is most likely happy if the amount of transferred data is reduced.

A solution according to another embodiment of the invention provides extra benefits in situations wherein

The functionality provided by the invention resides for example in any suitable location system between any suitable receiving entity and transmitting entity. The receiving entity and transmitting entity may be for example an e mail client and an e mail server respectively. Alternatively the receiving entity may be an e mail server while the transmitting entity is an e mail client. Furthermore instead of e mail clients and servers the receiving and transmitting entities may be some other communicating parties such as for example a mobile terminal and an MMSC Multimedia Messaging Service Center .

In an embodiment of the invention the path between the receiving entity and the transmitting entity may comprise one or more slow speed links a low bandwidth network . Herein slow means that the link causes significant delays to the message transfer that is the message content size divided by the link speed is large for example over 20 seconds and the user must wait for the content to be delivered. Nevertheless the invention is not restricted only to such low bandwidth networks.

The implementation of the invention may be an e mail proxy arrangement comprising an e mail proxy in the network side and an e mail proxy client residing in the user s device. That is the setup may correspond to the setup shown in only the functionality of the e mail proxy and the e mail proxy client need to be modified according to the invention. Herein it must be noted that in connection with the invention the Internet operator s intranet shown in may be also some other network such as for example a corporate LAN Local Area Network or some other setting.

The optimisation provided by the invention is based on defining substantially unique identifiers such as hash values checksums calculated by means of for example cyclical checksum algorithm or differences in relation certain auxiliary data for some parts of messages that are to be sent over a communication network. The auxiliary data may be for example a base attachment or a base message that is presumably available in the receiving end. Further the auxiliary data may be selected such that it is at least partially similar with the message part relating to which the difference is calculated. In order to reduce the amount of data whose suitability for difference calculation is tested the auxiliary data may be selected among a limited set of data such as data stored in cache.

Still another alternative is to define the substantially unique identifier on the basis of name size type time stamp or specific information in the files for example headers file author meta data described in a metadata identifier of the message part or on the basis of some suitable combination of these. The substantially unique identifier is such that it identifies a message part or content reasonably accurately. That is there is no need to have 100 accuracy if the identifier is accurate enough for the purposes of the application domain.

These substantially unique identifiers can be used to replace some parts of messages for example e mail or MMS messages that the user of a mobile terminal is sending. This optimised message is then sent over the communication network which may be for example a mobile network or some other low bandwidth network. After the message has been transferred the omitted parts of the message may be retrieved on the basis of the substantially unique identifiers and messages with contents corresponding to the original parts are forwarded to the recipients of the messages.

Nevertheless it must be noted that according to the invention replacing the message parts with the substantially unique identifier is conditional. For example if the use of the substantially unique identifier would result in a larger amount of data than the original message part then there may be no reason to conduct the replacing.

The parts of the message for which the substantially unique identifiers are defined may be for example MIME parts of MIME multipart message. MIME multipart is specified in Network Working Group standard RFC 2387 The MIME Multi part Related Content type August 1998. 

The optimisation according to the invention can be used equally for optimising messages that are downloaded to mobile terminals or some other user devices. It must be noted that the invention may be used in connection with other optimisation mechanisms or on it s own.

According to an embodiment of the invention the system is configured to select the parts of message which are optimised by means of a hash value or some other identifier on the basis of the type or size of the parts of message. It is possible for example that parts that are smaller than certain size limit are not optimised. In an alternative setting parts of a type which can be easily compressed are not optimised whereas parts of a type which cannot be significantly compressed are optimised and then possibly compressed. As an example text files can be easily compressed but JPEG and MP3 files cannot be compressed significantly.

In the following in connection with various details of the invention will be discussed in connection with a system comprising an e mail client and an e mail proxy client in a user s device and an e mail proxy and an e mail server in the fixed line network. The e mail proxy client and the e mail proxy communicate with each other at least partially over a communication network which may be a network having limited bandwidth such as a mobile network. In addition to e mails these examples may be adapted also to other types of messages.

First a download request destined to the e mail server is sent form the e mail client. This request goes through the e mail proxy client and the e mail proxy. The e mail server responds to the download request with the e mail messages .

In step the e mail proxy calculates MD5 hash or similar for each attachment and stores them with reference to the original attachment. These hashes and respective references to the original documents are then maintained in the e mail proxy for future use. The e mail proxy also compares the calculated hash es to the ones that have been stored for the e mail client or e mail proxy client in question.

On the basis of this comparison the e mail proxy conditionally attaches the hashes to the e mail messages before sending them to the e mail proxy client.

In an alternative implementation the e mail proxy is lazy and does not compare the calculated hash to the previous hashes but always replaces the attachments with respective hashes before sending the messages to the e mail proxy client.

Then the e mail proxy sends the message accompanied with attachments and related hashes to the e mail proxy client. In step the e mail proxy client stores new hashes and optionally new attachments received from the e mail proxy. Then the e mail proxy client retrieves the substituted attachments on the basis of the hashes in step .

Then the e mail proxy client reconstructs the original e mail message s on the basis of the retrieved attachments in step . After the reconstruction the email proxy client sends the reconstructed e mail message s to the e mail client.

In an implementation according to an embodiment of the invention the e mail proxy and the e mail proxy client communicate with each other by using a proprietary protocol. In that case it is possible to embed the hashes or information about the hashes in packet headers of the proprietary protocol so that the receiving entity is able to identify in which messages some parts are replaced by hashes. Another option for notifying the receiving entity of the replaced message parts is to define a new MIME part. This new MIME part is used for replacing the omitted MIME part. The hash may be conveyed in the new MIME part or alternatively the hash may be included in the headers of the new MIME part whereby the actual MIME part may be empty. Other substantially unique identifiers may be conveyed in the same way. A still further possibility is to include the information about replaced message parts into an HTTP header.

First an email message with attachments is sent from the e mail client. The e mail proxy client residing in the user s device captures the e mail and calculates MD5 hash or similar for each attachment and stores them with reference to the original attachment in step . These hashes and respective references to the original documents are then maintained in the e mail proxy client for future use.

The e mail proxy client may also compare the calculated hash es to the ones that have been stored before. On the basis of this comparing the e mail proxy conditionally attaches the hashes to the e mail messages before sending them onwards over the mobile network to the e mail proxy.

In an alternative implementation the e mail proxy client is lazy and does not compare the calculated hash to the previous hashes but always replaces the attachments with respective hashes before sending the messages to the e mail proxy.

Then the e mail proxy client sends the optimised message possibly accompanied with attachments and related hashes to the e mail proxy. In step the e mail proxy retrieves the substituted attachments on the basis of the hashes.

Then the e mail proxy reconstructs the original e mail message on the basis of the retrieved attachments in step . After the reconstruction the email proxy sends the reconstructed e mail message to the recipient.

If the proxy or the e mail server does not have the attachment the e mail proxy sends a request for missing attachments or differences to the e mail proxy client. In step the e mail proxy client selects a base attachment based on name type date size etc. that is presumably found in the e mail proxy or e mail server and calculates a bytewise difference between the base attachment and the original attachment. This process may be executed several times in order to gain the minimum difference. 

Then the e mail proxy client sends the hash of the base attachment and the difference between the base attachment and the original attachment to the e mail proxy. In some implementation it may suffice to send only the difference. In that case the recipient may for example try to build the original attachment by combining the difference with a predefined set of files for example files stored in cache and see if any of the combinations results in sensible file. The e mail proxy may also compress the difference before sending the message to the e mail proxy client. If a suitable base attachment is not found the e mail proxy client may send the original attachment.

In step the e mail proxy retrieves the base attachment on the basis of the hash sent by the e mail proxy client. The attachment may be fetched from the e mail server. Then the base attachment is patched with the difference in order to create the original attachment in step . After this the original e mail message is reconstructed on the basis of the patched attachment in step and the email proxy sends the reconstructed e mail message to the recipient.

If the hash of the original attachment is not found in the previous hashes the e mail proxy tries to find a suitable base attachment for calculating a difference between the base attachment and the original attachment in step . The base attachments should be such that it is available for the e mail proxy client. If a suitable base attachment is found the e mail proxy calculates the difference between the base attachment and the original attachment.

Then the e mail proxy sends the e mail message s accompanied with attachments differences and related hashes to the email proxy client. If a difference is used a hash value relating to the base attachment is sent to the e mail proxy client.

In step the e mail proxy client stores new hashes and optionally new attachments received from the e mail proxy. Then the e mail proxy client retrieves the substituted attachments or base attachments on the basis of the hashes in step .

Then the e mail proxy client reconstructs the original e mail message s on the basis of the retrieved attachments and patched base attachments in step . After the reconstruction the email proxy client sends the reconstructed e mail message s to the e mail client.

It must be noted that illustrate only examples and that any details of one example may be combined with the details of the other examples.

Any hash algorithm that produces substantially unique hash values may be used in connection with the invention. Nevertheless also other substantially unique identifiers may be used. For example in case of a cyclical checksum based substantially unique identifier the algorithm may work as follows the transmitting end calculates the cyclical checksum for a file to be transferred so that first a checksum is calculated for a window of width w w is smaller than the file size . Then the window is moved forward by a delta d and the checksum is again calculated from for a window of width w. This is continued until the end of the file and thereby a set of checksums is obtained. This set of checksums is then sent to the receiving end instead of the original file and the receiving end compares the checksums it received with cyclical checksums calculated for various files available in the receiving end. If a large number of checksums are identical for two files it may be concluded that the files are similar or similar enough for the purposes of the embodiment of the invention .

Further any e mail protocol such as POP IMAP SMTP and MAPI Messaging Application Programming Interface may be employed in connection with between an e mail client and an e mail proxy client and between an e mail proxy and an e mail server. The protocols that are used may be different in the terminal and in the server network.

The functionality of a system according to the invention may be configurable for example based on attachment type size user preferences mobile terminal processing power network conditions etc. Moreover text contained in messages can be handled in the same way as the handling of attachments discussed above. The implementations employing differentiation are beneficial for example in cases where e mail messages are replied to forwarded or bounced.

The user device comprises a processing unit and a memory coupled to the processing unit . The memory comprises an e mail client software and an e mail proxy client software executable in the processing unit . The network entity comprises a processing unit and a memory coupled to the processing unit . The memory comprises an e mail proxy software executable in the processing unit . The user device and the network entity are connected to each other at least partially over mobile network. The network entity is further connected to an e mail server over a fixed line network.

The processing unit controls in accordance with the e mail proxy client software the user device to process a message which is generated by means of the e mail client software and which is intended to be transferred to the e mail server over the mobile network and or a message which has been transferred from the network entity over the mobile network.

The processing unit controls in accordance with the e mail proxy software the network entity to process a message which is received from the e mail server and which is intended to be transferred to the user device over the mobile network and or a message which has been transferred from the user device over the mobile network and which is destined to the e mail server .

It must be noted that also other implementations are possible. For example the email proxy client having functionality according to the invention may be bundled with an e mail program for example by using an separately installed extension API Application Programming Interface or through integration. The email proxy client may be bundled also with other network related software such as VPN clients dialers personal firewalls etc.

The e mail proxy having functionality according to the invention can be bundled with any other performance enhancing proxy for example with an optimising HTTP proxy. Furthermore the e mail proxy client can be bundled with any other performance enhancing proxy client. It is also possible to implement the e mail proxy in connection with an e mail server.

In an embodiment of the invention the e mail proxy or some other network entity according to the invention may be configured to remove a hash or some other substantially unique identifier from the maintained previous identifiers if the respective attachment or some other part of a message is not anymore available to the e mail proxy for example because it has disappeared from the e mail server. Messages in the e mail server are usually deleted through the e mail proxy. Thus the e mail proxy may be set to delete a hash when respective message is deleted from the e mail server. Nevertheless the user may delete attachments or messages from the e mail server also through some other interface. In order to cope with such a situation the e mail proxy may be set to synchronise the hashes it maintains with the data in the e mail server for example during idle times.

The information the e mail proxy and or e mail proxy client maintain in relation to the parts of previous messages may be a reference to the respective data stored into some other location. Alternatively the e mail proxy and or e mail proxy client may store copies of the attachments or other parts of messages themselves. Further for the purposes of retrieving a substituted attachment the e mail proxy may be set to employ attachments stored in a plurality of e mail boxes in the e mail server instead of just the attachments that are stored in the e mail box of the respective user.

The e mail proxy may be configured to store user credentials for the users earlier or to pick them up and store them when e mails of a particular user are retrieved. Credentials may be stored per user or per attachment.

Furthermore the MMSC element is connected to a database . The database may be integral part of the MMSC element such as the storage in which the MMSC temporarily stores MMS messages that are transferred between transmitting and receiving mobile terminals. As is well known to persons skilled in the art the operation of the MMSC is based on a store and forward principle. Alternatively the database may be a separate element.

Now according to an embodiment of the invention the mobile terminal first sends an MMS message including an attachment such as a photograph to the mobile terminal . To accomplish this the mobile terminal sends to the MMSC an MMS message comprising the attachment and an id which is a substantially unique identifier of the attachment. MMSC element stores the attachment together with the id into the database and forwards the MMS message including the attachment to the recipient mobile terminal .

Then the mobile terminal sends another MMS message to the mobile terminal . This MMS message includes the same attachment as the MMS message sent to the mobile terminal . Now the mobile terminal is controlled to notice that attachment has already been sent to the MMSC element. Therefore the mobile terminal sends to the MMSC element an MMS message wherein the attachment has been replaced by the respective id. MMSC element then retrieves the attachment from the database on the basis of the id and forwards the MMS message including the attachment to the recipient mobile terminal .

This example suits well for example to situations in which a user sends the same MMS message to multiple recipients. By means of the implementation discussed above the attachments needs to be sent to the MMSC element only once even though multiple messages comprising the attachment are transferred though the MMSC element.

It must be noted that this is only one example of an MMS implementation and that other options are possible. For example optimisation between the message transmission from the MMSC element to the recipient mobile terminals and is also possible.

Particular implementations and embodiments of the invention have been described especially in connection to e mail implementations. It is clear to a person skilled in the art that the invention is not restricted to details of the embodiments presented above but that it can be implemented in other embodiments using equivalent means without deviating from the characteristics of the invention. Thereby for example the details described in connection with e mail messages can be employed also in connection with any other suitable messages such as MMS messages or messages comprising Java content. The scope of the invention is only restricted by the attached patent claims.

