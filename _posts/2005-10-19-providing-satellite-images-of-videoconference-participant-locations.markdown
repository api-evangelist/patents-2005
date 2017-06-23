---

title: Providing satellite images of videoconference participant locations
abstract: A videoconferencing method having corresponding apparatus and computer programs comprises receiving exchanging audiovisual data for a videoconference with a videoconference server; identifying a physical location of a videoconference client; and either sending an indicator of the location to the server, which obtains physical location video data for the location comprising satellite photographs of the location and sends the data to other videoconference clients, or obtaining the data and sending the data to the server, which sends the data to other videoconference clients in the videoconference.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07633517&OS=07633517&RS=07633517
owner: Seiko Epson Corporation
number: 07633517
owner_city: Tokyo
owner_country: JP
publication_date: 20051019
---
The present invention relates generally to videoconferencing. More particularly the present invention relates to providing satellite images of videoconference participant locations.

In general in one aspect the invention features a videoconferencing method for a videoconference client the method comprising receiving first audiovisual data for a videoconference from a videoconference server sending second audiovisual data for the videoconference to the videoconference server identifying a physical location of the videoconference client and performing at least one of sending an indicator of the physical location to the videoconference server wherein the videoconference server obtains physical location video data for the physical location the physical location video data comprising a plurality of satellite photographs of the physical location and wherein the videoconference server sends the physical location video data to one or more others of the videoconference clients in the videoconference or obtaining the physical location video data for the physical location and sending the physical location video data to the videoconference server wherein the videoconference server sends the physical location video data to the one or more others of the videoconference clients in the videoconference.

In some embodiments the physical location video data represents a moving picture of the respective physical location shown at increasing magnification. In some embodiments the physical location video data further comprises a plurality of graphic images of the respective physical location. Some embodiments comprise an apparatus to perform the method. Some embodiments comprise a computer program for performing the method.

In general in one aspect the invention features a videoconferencing method for a videoconference client the method comprising receiving first audiovisual data for a videoconference sending second audiovisual data for the videoconference and

performing at least one of receiving an indicator of a physical location of one or more others of the videoconference clients in the videoconference obtaining physical location video data for each of the physical locations the physical location video data comprising a plurality of satellite photographs of the respective physical location and displaying the physical location video data or receiving the physical location video data for the physical locations of the one or more others of the videoconference clients in the videoconference and displaying the physical location video data.

In some embodiments the physical location video data represents a moving picture of the respective physical location shown at increasing magnification. In some embodiments the physical location video data further comprises a plurality of graphic images of the respective physical location. Some embodiments comprise displaying the physical location video data for the one or more others of the videoconference clients automatically when the one or more others of the videoconference clients join the videoconference. Some embodiments comprise an apparatus to perform the method. Some embodiments comprise a computer program for performing the method.

In general in one aspect the invention features a videoconferencing method comprising receiving audiovisual data from each of a plurality of videoconference clients sending the audiovisual data received from each of the videoconference clients to others of the videoconference clients identifying a physical location of at least one of the videoconference clients obtaining physical location video data for each of the physical locations the physical location video data comprising a plurality of satellite photographs of the respective physical location and sending the physical location video data to one or more of the videoconference clients.

In some embodiments the physical location video data represents a moving picture of the respective physical location shown at increasing magnification. In some embodiments the physical location video data further comprises a plurality of graphic images of the respective physical location. Some embodiments comprise receiving an indicator of each physical location from respective ones of the videoconference clients. Some embodiments comprise sending the physical location video data for physical location of one of the videoconference clients automatically when the one of the videoconference clients joins the videoconference. Some embodiments comprise an apparatus to perform the method. Some embodiments comprise a computer program for performing the method.

The details of one or more implementations are set forth in the accompanying drawings and the description below. Other features will be apparent from the description and drawings and from the claims.

The leading digit s of each reference numeral used in this specification indicates the number of the drawing in which the reference numeral first appears.

Embodiments of the present invention provide videoconferencing systems videoconference clients and videoconference servers that provide satellite images of videoconference client physical locations to the videoconference clients. The satellite photographic images for a physical location are preferably provided in the form of physical location video data representing a moving picture of the physical location shown at increasing magnification and can be combined with graphical images text and the like to provide further information. The videoconference system preferably obtains the images text and the like from a satellite image provider. While embodiments of the present invention are described in terms of a client server paradigm other embodiments operate according to other paradigms such as peer to peer paradigms and the like.

Each videoconference client identifies a physical location such as a street address latitude and longitude or the like associated with the videoconference client step . For example each videoconference client prompts a user to enter the address obtains the address automatically from a Lightweight Directory Access Protocol LDAP directory or the like.

Each videoconference client then automatically obtains physical location video data for the physical location from satellite image server step . The physical location video data preferably comprises a plurality of satellite photographs of the physical location. The physical location video data preferably represents a moving picture of the respective physical location shown at increasing magnification.

The physical location video data optionally further comprises graphic images of the respective physical location. For example the video can begin with views of the Earth from outer space followed by a series of maps followed by the satellite photographs all shown at a steady rate of increasing magnification to convey an effect of approaching the physical location from above.

Satellite image server can be part of videoconference server and can even reside on the same physical device but is preferably operated by a satellite image provider that provides an application programming interface API for videoconference server .

Videoconference clients preferably obtain the physical location video data before the first videoconference and store the physical location video data for use in each videoconference as described in detail below. Alternatively videoconference clients obtain the physical location video data at the beginning of each videoconference.

Each videoconference client sends the physical location video data to videoconference server step which receives the physical location video data step and then sends the physical location video data to one or more others of videoconference clients step . Preferably each videoconference client compresses the physical location video data prior to transmission and decompresses the video data on reception according to conventional techniques. In some embodiments videoconference server stores the physical location video data either compressed or not for use in future videoconferences.

Videoconference clients receive the physical location video data step and decompress the physical location video data if necessary. Videoconference clients then display the physical location video data step . Preferably the physical location video data of the physical location of a videoconference client is displayed automatically as that videoconference client joins the current videoconference. In addition a user can view the physical location video data at any time by manipulating a graphical user interface. Users can view the physical location video data for any videoconference client including the user s videoconference client .

Preferably the physical location video data simply replaces the video portion of the regular videoconference audiovisual data which continues to be received uninterrupted but is not displayed. In other embodiments the physical location video data is shown in a separate window concurrently with the video portion of the regular videoconference audiovisual data.

Each videoconference client identifies a physical location such as a street address latitude and longitude or the like associated with the videoconference client step . For example each videoconference client prompts a user to enter the address or obtains the address automatically from a Lightweight Directory Access Protocol LDAP directory or the like.

Each videoconference client then automatically sends an indicator of the physical location to videoconference server step . The indicator can be the street address or some other indicator of the physical location.

Videoconference server receives the indicator of the physical location of videoconference client step and obtains physical location video data for the physical location step as described above with reference to .

Videoconference server sends the physical location video data to other videoconference clients in the videoconference step . Preferably videoconference server compresses the physical location video data prior to transmission and videoconference clients decompress the video data on reception according to conventional techniques. In some embodiments videoconference server stores the physical location video data either compressed or not for use in future videoconferences.

Videoconference clients receive the physical location video data step and decompress the physical location video data if necessary. Videoconference clients then display the physical location video data step as described above.

Each videoconference client identifies a physical location such as a street address latitude and longitude or the like associated with the videoconference client step . For example each videoconference client prompts a user to enter the address or obtains the address automatically from a Lightweight Directory Access Protocol LDAP directory or the like.

Each videoconference client then automatically sends an indicator of the physical location to videoconference server step . The indicator can be the street address or some other indicator of the physical location.

Videoconference server receives the indicators of the physical locations of videoconference clients step and sends the indicators of the physical location of each videoconference client in a videoconference to the other videoconference clients in the videoconference step .

Each videoconference client in a videoconference receives the indicators of the physical locations of the other videoconference clients in the videoconference step and obtains the corresponding physical location video data step as described above with reference to . Videoconference clients then display the physical location video data step as described above.

The invention can be implemented in digital electronic circuitry or in computer hardware firmware software or in combinations of them. Apparatus of the invention can be implemented in a computer program product tangibly embodied in a machine readable storage device for execution by a programmable processor and

method steps of the invention can be performed by a programmable processor executing a program of instructions to perform functions of the invention by operating on input data and generating output. The invention can be implemented advantageously in one or more computer programs that are executable on a programmable system including at least one programmable processor coupled to receive data and instructions from and to transmit data and instructions to a data storage system at least one input device and at least one output device. Each computer program can be implemented in a high level procedural or object oriented programming language or in assembly or machine language if desired and in any case the language can be a compiled or interpreted language. Suitable processors include by way of example both general and special purpose microprocessors.

Generally a processor will receive instructions and data from a read only memory and or a random access memory. Generally a computer will include one or more mass storage devices for storing data files such devices include magnetic disks such as internal hard disks and removable disks magneto optical disks and optical disks.

Storage devices suitable for tangibly embodying computer program instructions and data include all forms of non volatile memory including by way of example semiconductor memory devices such as EPROM EEPROM and flash memory devices magnetic disks such as internal hard disks and removable disks magneto optical disks and CD ROM disks. Any of the foregoing can be supplemented by or incorporated in ASICs application specific integrated circuits .

A number of implementations of the invention have been described. Nevertheless it will be understood that various modifications may be made without departing from the spirit and scope of the invention. Accordingly other implementations are within the scope of the following claims.

