---

title: Abstracted metadata policy component and related architecture
abstract: A method and architecture for reading and updating metadata. A policy component is arranged to receive a request to read or update metadata that may include metadata from a plurality of standards. Each metadata format potentially includes a field corresponding to the request. The policy component determines which fields to read or update in satisfying the request by consulting a repository. The repository includes mappings that map information included in the request (e.g., a path) to locations in the metadata corresponding to the request. The policy component uses the locations to read or update the metadata.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07548927&OS=07548927&RS=07548927
owner: Microsoft Corporation
number: 07548927
owner_city: Redmond
owner_country: US
publication_date: 20050421
---
Files may have metadata associated therewith. Metadata is information about a file that helps describe the file but is independent of the file itself For example metadata may include information about a file such as author title manager company category comments creation date and any other data about the file. Some metadata applies to almost all files while other metadata is specific to the type of file. For example most files have author and subject as metadata while image files may also include shutter speed camera model equipment make metering mode and the like. Typically the metadata is not needed to display the file but in some cases it is. For example metadata for an image may include width height and bit depth This metadata may be needed to properly display the image.

Some files have metadata of various standards associated with or embedded in them. For example an image file may be associated with Exchangeable Image File Format EXIF International Press Telecommunications Council IPTC and Extensible Metadata Platform XMP metadata. Each type of metadata associated with a file may or may not have various pieces of information about the file e.g. author create date and so forth .

What is needed is a method and system for reading the various pieces of information contained in various metadata schemas that are associated with a file and determining which metadata entry should take priority and updating the metadata to keep it consistent across the multiple schemas.

Briefly the present invention provides a method and architecture for reading and updating metadata. A policy component is arranged to receive a request to read or update metadata that may include metadata from a plurality of standards. Each metadata format potentially includes a field corresponding to the request. The policy component determines which fields to read or update in satisfying the request by consulting a repository. The repository includes mappings that map information included in the request e.g. a path to locations in the metadata corresponding to the request. The policy component uses the locations to read or update the metadata.

Other aspects will become apparent from the following detailed description when taken in conjunction with the drawings in which 

The invention is operational with numerous other general purpose or special purpose computing system environments or configurations. Examples of well known computing systems environments and or configurations that may be suitable for use with the invention include but are not limited to personal computers server computers hand held or laptop devices multiprocessor systems microcontroller based systems set top boxes programmable consumer electronics network PCs minicomputers mainframe computers distributed computing environments that include any of the above systems or devices and the like.

The invention may be described in the general context of computer executable instructions such as program modules being executed by a computer. Generally program modules include routines programs objects components data structures and so forth which perform particular tasks or implement particular abstract data types. The invention may also be practiced in distributed computing environments where tasks are performed by remote processing devices that are linked through a communications network. In a distributed computing environment program modules may be located in both local and remote computer storage media including memory storage devices.

With reference to an exemplary system for implementing the invention includes a general purpose computing device in the form of a computer . Components of the computer may include but are not limited to a processing unit a system memory and a system bus that couples various system components including the system memory to the processing unit . The system bus may be any of several types of bus structures including a memory bus or memory controller a peripheral bus and a local bus using any of a variety of bus architectures. By way of example and not limitation such architectures include Industry Standard Architecture ISA bus Micro Channel Architecture MCA bus Enhanced ISA EISA bus Video Electronics Standards Association VESA local bus Peripheral Component Interconnect PCI bus also known as Mezzanine bus PCI Express PCI E bus and accelerated graphics port AGP bus.

Computer typically includes a variety of computer readable media. Computer readable media can be any available media that can be accessed by the computer and includes both volatile and nonvolatile media and removable and non removable media. By way of example and not limitation computer readable media may comprise computer storage media and communication media. Computer storage media includes both volatile and nonvolatile removable and non removable media implemented in any method or technology for storage of information such as computer readable instructions data structures program modules or other data. Computer storage media includes but is not limited to RAM ROM EEPROM flash memory or other memory technology CD ROM digital versatile disks DVD or other optical disk storage magnetic cassettes magnetic tape magnetic disk storage or other magnetic storage devices or any other medium which can be used to store the desired information and which can accessed by the computer . Communication media typically embodies computer readable instructions data structures program modules or other data in a modulated data signal such as a carrier wave or other transport mechanism and includes any information delivery media. The term modulated data signal means a signal that has one or more of its characteristics set or changed in such a manner as to encode information in the signal. By way of example and not limitation communication media includes wired media such as a wired network or direct wired connection and wireless media such as acoustic RF infrared and other wireless media. Combinations of the any of the above should also be included within the scope of computer readable media.

The system memory includes computer storage media in the form of volatile and or nonvolatile memory such as read only memory ROM and random access memory RAM . A basic input output system BIOS containing the basic routines that help to transfer information between elements within computer such as during start up is typically stored in ROM . RAM typically contains data and or program modules that are immediately accessible to and or presently being operated on by processing unit . By way of example and not limitation illustrates operating system application programs other program modules and program data .

The computer may also include other removable non removable volatile nonvolatile computer storage media. By way of example only illustrates a hard disk drive that reads from or writes to non removable nonvolatile magnetic media a magnetic disk drive that reads from or writes to a removable nonvolatile magnetic disk and an optical disk drive that reads from or writes to a removable nonvolatile optical disk such as a CD ROM or other optical media. Other removable non removable volatile nonvolatile computer storage media that can be used in the exemplary operating environment include but are not limited to magnetic tape cassettes flash memory cards digital versatile disks digital video tape solid state RAM solid state ROM and the like. The hard disk drive is typically connected to the system bus through a non removable memory interface such as interface and magnetic disk drive and optical disk drive are typically connected to the system bus by a removable memory interface such as interface .

The drives and their associated computer storage media discussed above and illustrated in provide storage of computer readable instructions data structures program modules and other data for the computer . In for example hard disk drive is illustrated as storing operating system application programs other program modules and program . Note that these components can either be the same as or different from operating system application programs other program modules and program data . Operating system application programs other program modules and program data are given different numbers herein to illustrate that at a minimum they are different copies. A user may enter commands and information into the computer through input devices such as a keyboard and pointing device commonly referred to as a mouse trackball or touch pad. Other input devices not shown may include a microphone joystick game pad satellite dish scanner a touch sensitive screen of a handheld PC or other writing tablet or the like. These and other input devices are often connected to the processing unit through a user input interface that is coupled to the system bus but may be connected by other interface and bus structures such as a parallel port game port or a universal serial bus USB . A monitor or other type of display device is also connected to the system bus via an interface such as a video interface . In addition to the monitor computers may also include other peripheral output devices such as speakers and printer which may be connected through an output peripheral interface .

The computer may operate in a networked environment using logical connections to one or more remote computers such as a remote computer . The remote computer may be a personal computer a server a router a network PC a peer device or other common network node and typically includes many or all of the elements described above relative to the computer although only a memory storage device has been illustrated in . The logical connections depicted in include a local area network LAN and a wide area network WAN but may also include other networks. Such networking environments are commonplace in offices enterprise wide computer networks intranets and the Internet.

When used in a LAN networking environment the computer is connected to the LAN through a network interface or adapter . When used in a WAN networking environment the computer typically includes a modem or other means for establishing communications over the WAN such as the Internet. The modem which may be internal or external may be connected to the system bus via the user input interface or other appropriate mechanism. In a networked environment program modules depicted relative to the computer or portions thereof may be stored in the remote memory storage device. By way of example and not limitation illustrates remote application programs as residing on memory device . It will be appreciated that the network connections shown are exemplary and other means of establishing a communications link between the computers may be used.

Each of the components and may comprise code that executes on or hardware associated with a computer such as the computer system of and may comprise a conventional application program an operating system component or utility a control an application programming interface API a hardware device a combination of the above and so forth.

In one embodiment the requesting component instantiates a query reader or writer by communicating with the codecs component as described in more detail in conjunction with . The requesting component may then use the query reader or writer to obtain or update metadata associated with a file such as an image file.

The policy component may use rules and other data from the rules database to determine how to read and write metadata as described in more detail below.

The rules database comprises a repository into which rules may be stored and accessed regarding reading and writing metadata. The rules database may include a mapping that maps a non fully qualified path defined below to one or more fully qualified paths defined below . Thus for example author may map to ifd 315 in an IFD type of metadata and may also map to iptc artist in an IPTC type of metadata.

The mappings included in the rules database may be fixed or updateable e.g. through system updates user modification new component installation and so forth . In an update additional metadata types may be mapped to the rules database .

The rules database may include rules that indicate which metadata has priority when reading a metadata field. For example if file has EXIF metadata and IPTC metadata associated with it the rules may indicate that the EXIF metadata should be returned in response to requests for certain metadata fields and that the IPTC metadata should be returned in response to requests for other metadata fields.

The rules database may also include rules that indicate what should happen on a write to metadata. In one embodiment the rules may specify that all metadata associated with a non fully qualified path is updated. For example if a file is associated with EXIF and IPTC metadata the rules may specify that the EXIF IPTC XMP and any other metadata associated with the path that is specified by the rules be updated created and or deleted hereinafter collectively referred to as updated .

In another embodiment the rules may specify that only existing metadata associated with a path is updated. For example if a file is associated with EXIF and IPTC metadata the rules may specify that the EXIF and IPTC metadata be updated in response to a request update metadata associated with a path.

In another embodiment the rules may specify that only metadata of one type be updated in response to a request to update metadata associated with a path and that other metadata fields of other metadata types that are associated with the path be deleted. For example if a file is associated with EXIF and IPTC metadata the rules may specify that the EXIF metadata be updated and the IPTC metadata be deleted in response to a request to update metadata associated with a path.

Furthermore the rules may also specify that all the requirements of a particular metadata type be complied with in updating a metadata field. For example a specification for XMP metadata may require that certain other fields be updated in whenever a certain part of the XMP metadata is updated.

The components and and the rules database may reside on the same computer or may be distributed over two or more computers.

The decoder may include code and or hardware that enables it to read data written in a particular format e.g. XMP EXIF IPTC and the like . The query reader may navigate the underlying metadata included in the data to obtain fields of the metadata. Similarly the encoder may include code and or hardware that enables it to write data of a particular format while the query writer may navigate the underlying metadata included in the data to update fields in the metadata.

The query reader and query writer may expose an interface that allows a component to request a field in the metadata. In one embodiment this interface allows the component to specify a path to the field in a fully qualified or non fully qualified manner. For example the component may pass a string such as ifd exif 150. The symbol may specify the root of the metadata while ifd may specify an image file directory block. The term exif indicates that the metadata is formatted in EXIF format. The last part of the string e.g. 150 may comprise a tag that identifies a field in the EXIF metadata. A path starting with a is sometimes referred to as a fully qualified path while a path that does not start with a is sometimes referred to as a non fully qualified path.

The IFD metadata may include pointers or indexes into the metadata elements e.g. the EXIF metadata the XMP metadata the other metadata and other portions of the IFD metadata .

Returning to if a path is sent to query reader or the query writer that is not a fully qualified path e.g. does not start with the query reader or writer as the case may be passes the path to the policy component . For example if the component requests to read or write to a metadata field associated with a non fully qualified path of Author the query reader or writer passes the path to the policy component .

The policy component may then find the appropriate metadata field or fields and return the data associated with one field e.g. if the request is to obtain a metadata field associated with the non fully qualified path or update one or more fields e.g. if the request is to update metadata fields associated with the non fully qualified path .

At block a decoder and query reader are instantiated if they do not exist . For example referring to the requesting component may instantiate the decoder by calling the codecs component and then instantiate the query reader of by calling the decoder .

At block the component requests information from the query reader and passes a path thereto. At block the query reader determines if the path is a fully qualified path and if so processing branches to block . If the path is a non fully qualified path processing branches to block .

At block the query reader parses the path to obtain the information as described in more detail in conjunction with .

At block the information is obtained from the policy component as described in more detail in conjunction with .

At block the query reader returns the information that either it found or that the policy component found.

At block the policy component receives the request which includes the non fully qualified path. At block the policy component obtains a list of locations in the metadata mapped to the path. The policy component may do this by consulting a rules database and obtaining a list of possible locations therefrom. This list of possible locations may include an entry for each type of metadata the policy component understands. For example in response to a request including a non fully qualified path of author the following locations which are fully qualified paths may be obtained 

At block the first location is selected. At block the policy component calls the query reader. Other decoders may be instantiated if needed to interpret metadata indicated by the location.

At block a determination is made as to whether the field is included in the container. If the field is included in the container the actions continue at block otherwise the actions continue at block .

At block a determination is made as to whether the last location of the list has been reached. If not the actions continue at block otherwise the actions continue at block .

At block the next location of the list is obtained. Then the actions associated with blocks and are repeated. The actions associated with blocks continue until the field is found or all locations have been searched and the field is not found.

At block the information from the field is obtained. At block the information is returned to the query reader.

At block an encoder and query writer are instantiated if they do not exist . For example referring to the requesting component instantiates the encoder by calling the codecs component and then instantiates the query writer of by calling the encoder .

At block the component requests that a field be updated by passing a path and value to the query writer. At block the query reader determines if the path is a fully qualified path and if so the actions continue at block . If the path is a non fully qualified path processing branches to block .

At block the query writer parses the path and updates a field with the value as described in more detail in conjunction with .

At block the policy component receives the request which includes the non fully qualified path. At block the policy component obtains a list of locations in the metadata mapped to the path. The policy component may do this by consulting a rules database and obtaining a list of possible locations therefrom. This list of possible locations may include an entry for each type of metadata the policy component is able to interpret.

At block the first location is selected. At block the policy component may call a query writer if needed to update fields in the metadata. Other encoders and query writers may be instantiated if needed to update fields in the metadata indicated by the location. In another embodiment the field in the metadata is updated only if it already exists in the metadata.

At block the field indicated by the location is updated. If the field does not exist the field may be created and set to the value otherwise the field may be updated with the value.

At block other fields may be updated in response to updating the field as described in more detail in conjunction with . These other fields may be updated to comply with a specification of the metadata that applies to the field that was updated.

At block a determination is made as to whether the the last location of the list has been reached. If so the actions continue at block otherwise the actions continue at block .

At block the next location of the list is obtained. Then the actions associated with blocks are repeated. The actions associated with blocks may repeat until the fields have been updated for all locations of the list. This essentially keeps the fields in the various metadata consistent.

At block the policy component receives the request which includes the non fully qualified path. At block the policy component obtains a list of locations in the metadata mapped to the path. The policy component may do this by consulting a rules database as described previously. The rules database may include one set of mappings for reading metadata and another set of mappings for writing metadata. Alternatively the same set of mappings may be used for reading and writing metadata.

At block the first location is selected. The mappings may be organized such that the first one listed is the field in the master metadata type. Thus in one embodiment selecting the first location selects the master field. The policy component may call a query writer if needed to update fields in the metadata. Other encoders and query writers may be instantiated if needed to update fields in the metadata indicated by the location.

At block the field indicated by the location is updated. If the field does not exist the field may be created and set to the value otherwise the field may be updated with the value.

At block other fields may be updated in response to updating the field as described in more detail in conjunction with . These other fields may be updated to comply with a specification of the metadata applying to the field that was updated.

At block a determination is made as to whether the last location of the list has been reached. If so the actions continue at block otherwise the actions continue at block .

At block the next location of the list is obtained. At block the field associated with the next location is deleted. Then the actions associated with blocks are repeated. The actions associated with blocks may be repeated each time a field is deleted at block to update other metadata in response to the deleted field in accordance with one or more metadata specifications.

At block a determination is made as to whether to update other fields in response to a field that has already been updated. For example a metadata specification may specify that one or more other fields be updated when a particular field is updated. Rules corresponding to the specification may be encoded in the rules database of for example. A policy component may obtain these rules when determining whether other fields need to be updated.

At block if other fields need to be updated the actions continue at block otherwise the actions continue at block .

In reading or updating a field the policy component may call a codecs component and pass one or more fully qualified paths thereto. In response thereto existing or newly instantiated encoder writer or decoder reader pairs may be used to read or update various metadata. is a flow diagram corresponding to block of and block of generally representing actions that may occur in reading or updating metadata via fully qualified path. At block the actions begin.

At block the first part of a fully qualified path is examined. For example if a path comprises ifd exif 150 ifd is examined. If a metadata item e.g. decoder query reader pair or encoder query writer pair exists to read or update metadata in IFD format this metadata item may then be used to traverse the metadata. Otherwise a new metadata item may be created.

At block a determination is made as to whether the examined part is the last part of the path. If so the actions continue at block otherwise the actions continue at block . For example if the selected part is 150 then processing would branch to block .

At block the field in the metadata is updated or read as requested and a success return code may be returned at block .

At block the part of the path is mapped to a metadata globally unique identifier GUID . A metadata GUID may be associated with a particular metadata type and may uniquely identify the metadata type.

At block the metadata block corresponding to the examined part of the path is found. This may be done by passing the GUID to an encoder or decoder and asking if a metadata block corresponding to the GUID exists in the container.

At block a determination is made as to whether the metadata block exists in the container. If so processing branches to block otherwise processing branches to block .

At block a failure code may be returned. In addition in cases where there is a request to create a field the metadata block may be created together with the field and a code other than failure returned.

At block a metadata block reader or writer may be created to read the metadata block corresponding to the GUID.

At block the next part of the path is examined. The actions associated with blocks and may continue until the last part of the path is examined.

A policy component may implement the following exemplary interface to update metadata by non fully qualified path e.g. pwzName 

The policy component may use the metadata block reader or writer it was initialized with to navigate the metadata hierarchy.

Although various aspects of the invention have been described in the context of images it will be recognized that the principles contained herein may also be applied to other files that have metadata associated with them without departing from the spirit or scope of the present invention.

As can be seen from the foregoing detailed description there is provided a method and system for reading the various pieces of information contained in various metadata associated with a file and determining which one takes priority and updating the metadata to keep it consistent. While the invention is susceptible to various modifications and alternative constructions certain illustrated embodiments thereof are shown in the drawings and have been described above in detail. It should be understood however that there is no intention to limit the invention to the specific forms disclosed but on the contrary the intention is to cover all modifications alternative constructions and equivalents falling within the spirit and scope of the invention.

