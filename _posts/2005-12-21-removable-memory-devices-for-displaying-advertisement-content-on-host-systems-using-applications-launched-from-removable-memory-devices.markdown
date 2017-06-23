---

title: Removable memory devices for displaying advertisement content on host systems using applications launched from removable memory devices
abstract: A removable memory device is provided. The device includes a plurality of re-programmable non-volatile memory cells; and a controller including a processor and a controller memory, wherein an application is launched from the removable memory device and executed on a host system when the removable memory device interfaces with the host system, and the application launches a display window on a display device, wherein the display window is controlled by the application and is used to display advertisement content that is stored in the plurality of memory cells or from a server that is accessible by the host system.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08683082&OS=08683082&RS=08683082
owner: Sandisk Technologies Inc.
number: 08683082
owner_city: Plano
owner_country: US
publication_date: 20051221
---
The present application claims priority under 35 USC 119 e to the following provisional patent application the disclosure of which is incorporated herein by reference in its entirety 

Ser. No. 60 736 336 filed on Nov. 14 2005 entitled SYSTEM AND METHOD FOR DISPLAYING ADVERTISEMENT USING FLASH MEMORY STORAGE DEVICES with Carlos J. Gonzalez Edwin J. Cuellar and Susan A. Cannon as inventors.

The present application is also related to patent application Ser. No. 11 314 844 entitled SYSTEM AND METHOD FOR DISPLAYING ADVERTISEMENT USING FLASH MEMORY STORAGE DEVICES filed on even date herewith the disclosure of which is incorporated herein by reference in its entirety.

The present invention relates to computing systems and more particularly to displaying advertisements using a flash memory storage device.

Electronic commerce is becoming commonplace with the rapid increase in the use of the Internet. Consumers continue to spend more time with computing devices for personal and business needs. The Internet today is a significant portal for advertisers who want to expose their goods and services to consumers.

Advertisers continue to push advertisements and promotional materials information jointly referred to as Ads or Ad content to consumers in various ways for example web sites that provide some service to consumers are typically funded via advertisements to the consumer. Examples include web sites that provide search services on the Internet like Google Yahoo or shopping services like Amazon and eBay or other services like free email accounts maps etc.

Ads are displayed on a user s computer when a user visits a website or clicks on a website link or when the and the website presents sponsored links in addition to the results from that search.

Efficient business organizations continue to explore different avenues by which Ads and information regarding their goods and services can reach consumers. There is a need for novel techniques by which organizations can get their Ads displayed to consumers.

In one aspect of the present invention a removable memory device is provided. The device includes a plurality of re programmable non volatile memory cells and a controller including a processor and a controller memory wherein an application is launched from the removable memory device and executed on a host system when the removable memory device interfaces with the host system and the application launches a display window on a display device wherein the display window is controlled by the application and is used to display advertisement content that is stored in the plurality of memory cells or from a server that is accessible by the host system.

In another aspect of the present invention the removable memory device includes a plurality of re programmable non volatile memory cells and a controller including a processor and a controller memory wherein an application stored in the non volatile memory cells is launched from the removable memory device and executed on a host system and the application launches a display window on a display device wherein the display window is controlled by the application and the application facilitates a secured connection between a server and the memory device so that advertisement content can be updated and displayed in real time on a display device.

In yet another aspect of the present invention a system for displaying advertisement content on a display device is provided. The system includes a host system that interfaces with a removable memory device and a server that can update an application and or advertisement content stored in a plurality of memory cells of the removable memory cells wherein the application is launched from the removable memory device and executed on the host system when the removable memory device interfaces with the host system and the application launches a display window on a display device wherein the display window is controlled by the application and is used to display the advertisement content in real time from the server when a network connection with the server is active.

This brief summary has been provided so that the nature of the invention may be understood quickly. A more complete understanding of the invention can be obtained by reference to the following detailed description of the preferred embodiments thereof in connection with the attached drawings.

In one aspect of the present invention a removable non volatile memory device may also be referred to as flash device or flash memory device is provided that stores an Advertising Client application ACA and Ad content. The ACA and or Ad content can be stored in a secured area of the flash device and or encrypted. The flash device stores adverting content that can only be accessed changed updated after proper authentication.

The ACA is preferably launched from the flash device either when the device interfaces with a host system or as a result of user activity. The ACA launches an Ad window or POP Up Ads where Ad content is showed to the user.

To facilitate an understanding of the preferred embodiment the general architecture and operation of a computing system non volatile memory storage device will first be described. The specific architecture and operation of the preferred embodiment will then be described with reference to the general architecture.

Computer includes a computer readable memory medium such as a hard disk for storing readable data. Besides other programs disk can store application programs including web browsers by which computer connects to the Internet.

According to one aspect of the present invention computer can also access a computer readable non volatile memory device for example a removable flash memory device that stores data files Ad content application program files for example the ACA and computer executable process steps embodying the present invention or the like via a flash memory receptacle interface . A CD ROM or CD R W read write interface not shown may also be provided with computer to access application program files audio files and data files stored on a CD ROM.

A modem an integrated services digital network ISDN connection or the like also provides computer with a network for example the Internet connection . The network connection allows computer to download data files audio files movies video application program files and conduct on line E commerce transactions.

It is noteworthy that the present invention is not limited to the architecture. For example notebook or laptop computers handheld devices including without limitation personal digital assistants PDAs cell phones and other common host platforms set top boxes or any other system capable of running computer executable process steps as described below may be used to implement the various aspects of the present invention.

Host system connects to a computer network not shown via network interface A and through network connection . One such network is the Internet that allows host system to download applications code documents and others electronic information.

Read only memory ROM is provided to store invariant instruction sequences such as start up instruction sequences or basic Input output operating system BIOS sequences.

Input Output I O devices A for example a keyboard a pointing device mouse a monitor a modem and the like are also provided an example of which is shown in .

Host system is coupled to a flash memory device that includes a controller module may also be referred to as memory controller or controller and solid state memory modules shown as Memory Module and Memory Module N . Controller module interfaces with host system via a bus interface or directly via system bus B or another peripheral bus not shown .

There are currently many different flash memory cards that are commercially available examples being the CompactFlash CF the MultiMediaCard MMC Secure Digital SD miniSD Memory Stick SmartMedia and TransFlash cards. Although each of these cards has a unique mechanical and or electrical interface according to its standardized specifications for example The Universal Serial Bus USB specification based interface incorporated herein by reference in its entirety the flash memory included in each is very similar. These cards are all available from SanDisk Corporation assignee of the present application. SanDisk also provides a line of flash drives under its Cruzer trademark which are hand held memory systems in small packages that have a Universal Serial Bus USB plug for connecting with a host by plugging into the host s USB receptacle. Each of these memory cards and flash drives includes controllers that interface with the host and control operation of the flash memory within them.

Host systems that use such memory cards and flash drives are many and varied. They include personal computers PCs laptop and other portable computers cellular telephones personal digital assistants PDAs digital still cameras digital movie cameras and portable audio players. The host typically includes a built in receptacle for example for one or more types of memory cards or flash drives but some require adapters into which a memory card is plugged.

A NAND architecture of the memory cell arrays is currently preferred although other architectures such as NOR can also be used instead. Examples of NAND flash memories and their operation as part of a memory system may be had by reference to U.S. Pat. Nos. 5 570 315 5 774 397 6 046 935 6 373 746 6 456 528 6 522 580 6 771 536 and 6 781 877 and United States patent application publication no. 2003 0147278.

A host interface interfaces with host system while a flash interface interfaces with memory modules .

The process steps according to one aspect of the present invention may be performed using the Internet. The following provides a brief description of the Internet.

The Internet connects plural computers world wide through well known protocols for example Transmission Control Protocol TCP Internet Protocol IP into a vast network. Information on the Internet is stored world wide as computer files mostly written in the Hypertext Mark Up Language HTML . Other mark up languages e.g. Extensible Markup Language XML as published by W3C Consortium Version 1 Second Edition October 2000 W3C may also be used. The collection of all such publicly available computer files is known as the World Wide Web WWW .

The WWW is a multimedia enabled hypertext system used for navigating the Internet and is made up of hundreds of thousands of web pages with images and text and video files which can be displayed on a computer monitor. Each web page can have connections to other pages which may be located on any computer connected to the Internet.

A typical Internet user uses a client program called a Web Browser to connect to the Internet. A user can connect to the Internet via a proprietary network or an Internet Service Provider. The web browser may run on any computer connected to the Internet. Currently various browsers are available of which two prominent browsers are Netscape Navigator and Microsoft Internet Explorer.

The Web Browser receives and sends requests to a web server and acquires information from the WWW. A web server is a program that upon receipt of a request sends the requested data to the requesting user. A standard naming convention known as Uniform Resource Locator URL has been adopted to represent hypermedia links and links to network services. Most files or services can be represented with a URL.

URLs enable Web Browsers to go directly to any file held on any WWW server. Information from the WWW is accessed using well known protocols including the Hypertext Transport Protocol HTTP the Wide Area Information Service WAIS and the File Transport Protocol FTP over TCP IP protocol. The transfer format for standard WWW pages is Hypertext Transfer Protocol HTTP .

It is noteworthy that the present invention is not limited to any particular type of network protocol standard. Any standard proprietary network methodology may be used to implement the adaptive aspects of the present invention. For example the Simple Object Access Protocol SOAP an XML based messaging protocol incorporated herein by reference in its entirety may be used to implement the adaptive aspects of the present invention.

Flash device re configures the computer screen and opens up a section of the computer screen to allow room for the Ads to be displayed.

Remote server is operationally coupled to plural content provider systems and . Content provider systems can be controlled by advertisers or other third parties. Content provider systems and are used to update download advertising content to server and or flash device .

Server can communicate with flash device securely in various ways. One way to communicate is by establishing a cryptographic connection directly between flash device and server with host serving only to facilitate the communication. Another way is by establishing cryptographic communication between server and host and then establishing communication between host and the flash device .

FIG. IE shows yet another block diagram of system A where flash device interfaces with host system via a USB interface. Flash device conforms to the USB specification i.e. can be accessed via a USB interface and appears to host having plural Logical Units LUNs of storage space and each LUN may appear to be of a different class of storage device. For example flash device may appear to have both a standard Mass Storage Class volume LUN A which imitates the behavior of a small computer system interface SCSI Hard Disk Drive and a multimedia card MMC Class volume which imitates the behavior of a CD ROM LUN B .

Host system having its own operating system views LUN A as a mass storage device for storing data and other information and LUN B as a CD ROM that can store an auto run application code for launching an application for example ACA A . Hidden area C is secured and is not available without proper authentication.

Host system interfaces with flash device via interface B. Standard USB based application programming interface API may be used for reading or writing data while proprietary APIs may be used to access hidden area C.

In one aspect of the present invention ACA A is stored in a secured area for example E of flash device and may be encrypted to reduce the risks of hacking i.e. attempts for unauthorized access to the system .

In one aspect protected or secured area means an area that is read only or accessible only by the appropriately authenticated entity host program etc. In the case of USB devices with a CD ROM volume the program may be stored in the CD ROM volume LUN B which is read only .

In another aspect of the present invention memory controller executes and launches ACA A when flash device is engaged with computing system . ACA A is automatically launched when the host system detects the presence of flash device . Memory controller may also aid computing system A in launching ACA A from flash device .

If the host system does not support the auto launch mechanism then ACA A can be launched manually by the user. ACA A can be embedded within a flash device menu that allows a user to start programs that are stored in flash device . In this case a user has to launch ACA A in order to access flash device storage and or other functionality.

It is noteworthy even for manual launch of ACA A the advertiser content provider controls what information and how it is presented to the user. For example an advertiser can have 2 or more programs that run randomly or in sequence.

Referring back to flash device stores advertising content shown as AD AD . . . ADn in segment area E. Ad content can include text search results multi media content an application or a computer game.

In one aspect memory area E is secured so that access to Ad content is restricted. Access to Ad content is provided to content providers after appropriate authentication only. Ad content can also be encrypted for additional security.

ACA A when triggered launches a window A . ACA A can be triggered when flash device is coupled to host system or as a result of user activity. Window A is used to display Ads on a display device connected to computing system for example monitor . Ads can be displayed real time from server or if a network connection is not available then Ads stored in memory area E are displayed offline . Window A can also be linked to a web server so that content is uploaded refreshed in real time.

Window A is controlled by ACA A and not the user. Window A is visible to the user according to the policies established by the advertiser. If Ad window A stays on top of the user display device and the user maximizes the application then the application extends to the boundaries of the Ad window A and not under. This provides a minimum display area for the Ad content.

Window A may also have a portion allocated for certain functions content so that the overall advertising system is useful for the target audience. For example window A may have an organizer planner for professionals games for kids adults helpful hints updated from server under applications C a search engine D or a link to a search engine or a combination of the foregoing. The user has the ability to customize configure window A so that the various functions content that are useful to the user are displayed. A configuration icon B allows the user to customize window A.

In another aspect the user may be given the option of selecting a set of functionality content from a menu of choices arranging and otherwise customizing the panel.

Referring back to ACA A comprises of a communication module B a display module C and an update module D. Communication module B facilitates communication between flash device and remote server . In one aspect memory controller can aid in the network connection via network interface A.

Communication module B periodically communicates with server while flash device is actively connected to computing system . In one aspect such communication is secured to thwart hacking. If flash device detects that ACA A is inactive for example by using a timeout for a period then memory controller firmware can disable the use of flash device or selectively disable certain functionality or otherwise impair device operation for example by reducing device performance.

Display module C assists in displaying Ads on a display device. Communication module B detects a network connection when established with remote server . If a remote connection is established then Ads may be displayed in window A in real time using display module C. If a network connection is not available then display module C displays Ads stored in memory area E in an off line mode.

Display module C cycles through Ad content stored in memory area E and ensures that a consumer is exposed to content for a pre determined period. This is enabled because the user cannot delete or change window A. Exposure may be measured by the amount of time an Ad is viewed by the user the number of times an Ad is exposed to the user or by the interaction of the user for example by responses to certain questions or interaction results in a game.

Display module C is also enabled to read Internet browsing data also known as cookies from computing system and transfers the cookies to a secured memory area for example E.

Communication module B interfaces with display module C and communicates the following to server the amount of time and frequency each content type is exposed to the consumer the amount of time a consumer had flash device coupled to computing system the type of files the number of files and size of files that the user was transferring to and from flash device the type of websites the user has visited and the duration of the visit. This information is then made available to content providers who can intelligently target users with relevant content information.

Advertisers can alter modify the overall Ad presentation based on user preferences or usage. The modification may be made real time if computing system is connected to server or offline.

Update module D is used to update content stored in memory area E. In one aspect Ad content is updated as a background operation while Ads are being displayed in window A. A secured channel not shown is used to update Ad content in memory area E. Data is stored in secured area E and is protected from hacking.

In one aspect of the present invention the normal functionality of flash device for example storage capacity is inhibited slowed or impaired if ACA A is not being actively used. Also the functionality of flash device is tied to the overall integrity of the ACA system A. For example if the ACA system is tampered with then flash device stops working. The connection and functionality can be recovered after the ACA system A is reinstated.

In one aspect of the present invention a user is given incremental access to flash device based on how Ads are viewed by the user. For example suppose that flash device is 2 giga bytes GB in capacity and window A is displayed for 30 seconds as default and the user is given 500 MB as the default capacity to use. When window A is displayed the user is given an option to increase the window display time in exchange for more capacity. For example a user may choose to view the Ad window for 2 minutes and in return may be given access to additional memory storage space for example 100 MB.

The business that hosts manages server benefits from the ACA system A in various ways. For example the entity can distribute flash device for free or for a nominal fee and charge Ad providers a fee per Ad or a subscription for hosting providing Ads. In another aspect of the present invention the advertiser can distribute the flash devices based on their known customer base much like direct mail goes to a target audience.

Different rates may be charged based on the frequency and number of Ads that are viewed. The entity can also obtain a certain percentage of the profit that the Ad providers make by selling goods and services.

The entity can also charge third parties for exposure to advertising material that resulted from a search using search engine D or from a search within the USB drive menu A. The USB drive menu A includes an embedded Ad window and stores applications.

The user can also earn promotional points by viewing Ads through flash device . This will enable the Ad provider to develop a relationship with the user.

In one aspect of the present invention a flash device designer manufacturer supplier for example SanDisk Corp. can host and manage Ad content distribution. The flash device supplier can also sell servers and systems to advertising agencies. The supplier can charge ongoing maintenance fees. The supplier may charge a variable rate depending on the frequency of exposure to Ad content.

In another aspect of the present invention the supplier or the entity that hosts the Ad content can also charge a percentage of the profit sales price from sale of products services that are linked to the exposure of the Ad content using the ACA offline or online .

In yet another aspect of the present invention an advertising company can provide unique application features along with Ad content to encourage use of the flash device and hence result in more exposure.

In yet another aspect of the present invention when a user selects or clicks on a link provided in Ad content then the user is taken to the advertiser s web page or performs some other operation. The entity hosting the Ad content can generate revenue based on such click through action.

In another aspect an advertiser may include all of these advertising features in a product such as a USB drive with a built in MPEG 1 Audio layer MP3 player. As the user views promotional material then the program will open or unlock the features of the MP3player. As the user uses the MP3player to download music to the player they would be exposed to the Ads.

In step S after the ACA A is loaded advertising content is loaded on the flash device. In one aspect a secured memory area is used to store the advertising content so that an unauthorized user is not able to access modify delete the stored content. The advertising content can be loaded on the flash device by the flash device manufacturer the advertising content provider or downloaded using a network connection when the user attempts to use the flash device.

In step S the flash device with ACA A and advertising content is provided to the user. In one aspect the flash device is given to the user for free or for a nominal fee.

In another aspect the user is given the flash device and the user then downloads ACA A and the advertising content from server .

In step S the user operationally couples the flash device with a computing system. Various standard or proprietary receptacles connectors may be used to couple flash device . In one aspect a USB connector is used to couple flash device to a computing system for example 100 .

In step S ACA A launches an Ad window A on the computing system display device for example . In one aspect ACA A controls window A i.e. a user cannot close the window. In another aspect the user is allowed to change certain attributes of window A for example color contrast or window boundaries as long as the window continues to be displayed in the visible area of the display device. Furthermore the user may configure any additional content functionality on the advertising panel window .

In another aspect of the present invention Ads are displayed as Pop Up Ads when flash device interfaces with host system . The Pop Up window can be generated by using JavaScript or any other means. The Pop Up window duration and attributes are controlled by ACA A.

In step S computing system flash device is connected to a remote server for example . In one aspect memory controller establishes the network connection using communication module B of ACA A.

In step S server interfaces with the Ad window A through ACA A and displays content in window A. Ad content is streamed real time. Server also examines the Ad content stored in flash device .

If the Ad content stored in flash device is not current then in step S server downloads the latest Ad content to flash device . In one aspect access to flash device is secured and requires authentication. Preferably Ad content is downloaded as a background operation i.e. while the user is viewing content server downloads the content to flash device . The download allows a user to view Ad content when a network connection is not available i.e. content is displayed in step S without the network connection in step S.

The entity hosting server can generate revenue in various ways as described above. For example every time content is displayed on a user screen the content provider is charged a fee step S . The content provider may be charged a subscription fee for a certain number or unlimited number of Ads that are displayed. In another aspect the content provider pays a subscription fee and a fee based on the number of Ads that are displayed in flash device .

In another aspect in step S the user is granted incremental access to the flash device . The amount of memory is proportional to the number of Ads and or the duration of the Ads that are displayed on the user screen. For example the user is given an option to increase the default Ad window A exposure time and in return is given access to more storage space.

In one aspect of the present invention a flash device operates as an advertising application provider. This is beneficial for both the memory manufacturers and the content providers. The user also benefits because it has access to free or at a nominal fee storage space.

While the present invention is described above with respect to what is currently considered its preferred embodiments it is to be understood that the invention is not limited to that described above. To the contrary the invention is intended to cover various modifications and equivalent arrangements within the spirit and scope of the appended claims.

