---

title: Playback control methods and arrangements for a DVD player
abstract: In accordance with certain aspects of the present invention, enhancements have been developed to further extend the performance of a generic DVD navigator. The methods and arrangements herein provide a mechanism that allows a player application to precisely ‘bookmark’ locations during playback, and later resume playback at the selected bookmarked locations.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07774797&OS=07774797&RS=07774797
owner: Microsoft Corporation
number: 07774797
owner_city: Redmond
owner_country: US
publication_date: 20051027
---
This application is a continuation of U.S. application Ser. No. 09 721 266 now U.S. Pat. No. 6 990 671 filed Nov. 22 2000 which is incorporated herein by reference.

This invention relates to computers and like devices and more particularly to improved playback control methods and arrangements for use between a multimedia player application and a generic media content navigator program via certain application programming interfaces APIs .

A digital versatile disc DVD player is composed of three logical units as defined in the DVD specification. The first logical unit is a DVD player application that presents an interface to the user and relays user commands to the second logical unit. The second logical unit a DVD navigator that reads and interprets the information on the DVD and controls which segments of video and audio are processed based on the user commands. The third logical unit is a DVD presentation layer that decompresses data read from the DVD and presents the corresponding audio video and subpicture streams as applicable to one or more renderers.

These logical units may be implemented in hardware and or software. By way of example in certain implementations the DVD player is implanted via a graphical user interface GUI that is displayed to a user and through which the user is able to selectively control playback etc. of the DVD using a pointing selection input device e.g. a mouse. This is usually a fairly straightforward task for system developers and allows for easy customization.

Implementing a DVD navigator on the other hand tends to be a more complex task. This is especially true for applications that seek to integrate DVD information into presentations and the like. Here each developer entity would need to provide a mechanism for reading and interpreting their DVD and interfacing with the decoder mechanism in the DVD presentation layer. Moreover the decoder mechanism in the DVD presentation layer will likely be a product of a third party making the task of authoring a DVD navigator even more difficult since the navigator must interface to many different decoder mechanisms.

Consequently there is a need for a powerful yet simplified and consistent interface that player applications can use to control the DVD navigator program.

Recognizing the potential burdens placed on application developers Microsoft Corporation in an effort to further enhance their operating system and the user s environment have developed a generic navigator component. This generic navigator component provides a standard specification compliant DVD navigator as part of Windows to help application developers avoid such possibly repetitive and difficult tasks. This generic navigator component exposes two application programming interfaces APIs that combined provide a powerful yet simplified and consistent interface that player applications can use to control the DVD navigator. The APIs have been designed to further influence the flexibility and usefulness of the underlying DVD Navigator.

In accordance with certain aspects of the present invention enhancements have been developed to further extend the performance of the generic navigator component. Of significance herein was the need for an improved user and player application environment for starting and stopping playback. With current navigators jumping to previous locations on discs is cumbersome and often unreliable. For example when a user wants to continue to watch a movie from a specific location he she must remember the location and manually navigate back to that point. Thus it would be beneficial to provide a mechanism that allows the player application to more precisely bookmark locations during playback and later resume playback that selected bookmarked locations.

The following exemplary methods and arrangements describe certain enhancements and features associated with a generic DVD navigator having APIs exposed to DVD player applications. These are referred to as the DVD navigator and DVD2 APIs. It is noted that while most of the description is directed towards a PC running the Windows operating system the various methods and arrangements are clearly applicable to other operating systems devices etc. Moreover the use of the term DVD is not meant to exclude other media formats. Thus the DVD content itself may come from a hard drive a compact disc over a network and the like.

As will be described the DVD navigator and or DVD2 API enable a player application to interactively control the playback of DVD content. The DVD2 API consists of two interfaces. The first is termed IDvdlnfo2 . The second is termed IDvdControl2 . The player application may use the IDvdlnfo2 interface to query the current state of the DVD navigator and the IDvdControl2 interface to better control playback and or to alter the DVD navigator s state.

The DVD2 API provides several unique and novel features. For example thread based synchronization methods are provided for real time playback a playback control mechanism is provided to determine the degree of interactivity communication mechanisms are provided between the player application and the disc program playing of time ranges is supported mechanisms are provided for coordinating and handling parental level requests and for determining the minimal parental level to play a restricted segment of content and a unique disc identifier algorithm is provided which further supports the bookmarking of any location within the DVD content

With this mind attention is drawn to which depicts an exemplary DVD player . Player includes at least one player application configured to present the user with a user interface U I . Through U I the user is able to instruct player application with regard to the playback of DVD content .

As illustrated player application is provided with DVD2 API and to communicate user requests and receive feedback information respectively. DVD2 API provide access to the functions within navigator . Navigator interacts with DVD content which in addition to media information includes a program . Program defines the menus jumps etc. associated with the remaining content. Navigator includes a state associated with the playback process. Here in state for example the current user operation UOP e.g. play stop pause reverse fast forward slow motion angle etc. is stored along with the current location within the DVD content e.g. chapter time frame and certain other registers such as those that could record recent jumps UOPs.

The output of navigator includes an encoded video stream an encoded audio stream and a subpicture stream as applicable. These outputs are inputted to a decoder which is configured to decode decrypt and decompress the encoded data and output the corresponding streams to the applicable video renderer or audio renderer . Renderer causes the video information to be displayed to the user for example via a video monitor. Renderer causes the audio information to be reproduces for the listener for example via one or more speakers.

Attention is now drawn to which is a block diagram depicting an exemplary computing system suitable for use with the arrangement in .

Computing system is in this example in the form of a personal computer PC however in other examples computing system may take the form of a dedicated server s a special purpose device an appliance a handheld computing device a mobile telephone device a pager device etc.

As shown computing system includes a processing unit a system memory and a system bus . System bus links together various system components including system memory and the processing unit . System bus may be any of several types of bus structures including a memory bus or memory controller a peripheral bus and a local bus using any of a variety of bus architectures. System memory typically includes read only memory ROM and random access memory RAM . A basic input output system BIOS containing the basic routine that helps to transfer information between elements within computing system such as during start up is stored in ROM . Computing system further includes a hard disk drive for reading from and writing to a hard disk not shown a magnetic disk drive for reading from or writing to a removable magnetic disk and an optical disk drive for reading from or writing to a removable optical disk such as a CD ROM or other optical media. Hard disk drive magnetic disk drive and optical disk drive are connected to system bus by a hard disk drive interface a magnetic disk drive interface and an optical drive interface respectively. These drives and their associated computer readable media provide nonvolatile storage of computer readable instructions data structures computer programs and other data for computing system .

A number of computer programs may be stored on the hard disk magnetic disk optical disk ROM or RAM including an operating system one or more application programs other programs and program data .

A user may enter commands and information into computing system through various input devices such as a keyboard and pointing device such as a mouse . A camera microphone or other like media device capable of capturing or otherwise outputting real time data can also be included as an input device to computing system . The real time data can be input into computing system via an appropriate interface . Interface can be connected to the system bus thereby allowing real time data to be stored in RAM or one of the other data storage devices or otherwise processed.

As shown a monitor or other type of display device is also connected to the system bus via an interface such as a video adapter . In addition to the monitor computing system may also include other peripheral output devices not shown such as speakers printers etc.

Computing system may operate in a networked environment using logical connections to one or more remote computers such as a remote computer . Remote computer may be another personal computer a server a router a network PC a peer device or other common network node and typically includes many or all of the elements described above relative to computing system although only a memory storage device has been illustrated in .

The logical connections depicted in include a local area network LAN and a wide area network WAN . Such networking environments are commonplace in offices enterprise wide computer networks Intranets and the Internet.

When used in a LAN networking environment computing system is connected to the local network through a network interface or adapter . When used in a WAN networking environment computing system typically includes a modem or other means for establishing communications over the wide area network such as the Internet. Modem which may be internal or external is connected to system bus via the serial port interface .

In a networked environment computer programs depicted relative to the computing system or portions thereof may be stored in the remote memory storage device. It will be appreciated that the network connections shown are exemplary and other means of establishing a communications link between the computers may be used.

DVD2 API simplifies application authoring adds functionality and solves many difficult synchronization issues common to DVD player applications development. Basically a common DVD API helps discourage proprietary single use monolithic DVD solutions that serve only as standalone DVD player applications. It also allows various applications such as presentation programs DVD players games or interactive learning programs to add DVD support without having to know which DVD decoder or DVD hardware support is on the user s system. Historically custom DVD solutions tend to be very hardware dependent and have limited upgrade options for users.

As will be described in greater detail below DVD2 API adds flexible synchronization mechanisms for the application to know the completion status of requests made to the DVD Navigator . The new command completion notification allows the application to concurrently perform other tasks and be informed of the status of a previous request. Previous DVD APIs assumed that either the application would be blocked until the request was completed or would not send any notification to the application. Applications now have the option of receiving a synchronization object that they can use to wait on or are notified about completion events.

The synchronization mechanism also returns the status of the request that indicates whether it succeeded or returns the reason an error code for its failure. Previous DVD APIs would appear to successfully execute requests that would later fail due to changed state when the DVD Navigator actually started processing them. At that point there was no way to propagate the error indication back to the player application . The new mechanism also notifies the player application of every request that is cancelled or overridden by the disc s program or by further user actions.

Current DVD APIs use predefined behaviors that dictate how a command interacts with the current display. When a player application issues a new request it pre empts and cancels any content video or audio that is being played. Alternatively the APIs semantics dictate that the current presentation completes before the new content is presented which forces the user to wait before he she can request another action. Interactive applications such as DVD players and games may require the first behavior instant effect but other applications such as a slideshow may require the second behavior complete the current presentation . Since these two options are mutually exclusive predefined API s semantics cannot accommodate both. DVD2 API allows player application to indicate the desired behavior via flags and also how it interacts with the synchronization mechanism.

DVD navigator is configured to simulate a virtual CPU that uses an execution state in the form of a set of memory registers see . Previous DVD APIs allowed applications to read the contents of the registers. DVD2 API also allows player application to also change the contents of the memory registers. The combined read write functionality allows player application to essentially communicate with program as illustrated in .

The read and write methods works in such a way that they can also be used for synchronization. By way of example with read write functionality player application can implement controlled unlocking or restricted access to all or portions of DVD content . With controlled unlocking the user may be restricted from viewing portions of the disc until player application sets specific memory registers. Player application could receive this information from the content s author the user another program a website or the like. For example depicts the use of a code being written to registers by player application and being read by program . If the code is correct then portion of DVD content can be played back.

In certain implementations DVD2 API contains a simplified naming scheme for the potential user operations suggested in the DVD specification Annex J. The DVD2 API uses less DVD jargon and features a more intuitive naming scheme. The user operation names proposed in the DVD specification are unclear and can lead to incorrect usage or under utilization by application programs. The names now suggest their usage instead of an abstract label. Also time codes are now returned in a simple integer format instead of the awkward BCD coding.

Some previous DVD APIs failed to correctly handle minimum parental level branching by having the DVD navigator send an error event indicating that the branch always failed see . The player application then had to increase the parental level and restart the movie from the beginning. If the branch fails the player application would need to stop the playback to enter the STOP domain to change the parental level. It can only continue by restarting the movie.

To the contrary DVD2 API has a mode that pauses navigator and lets player application respond to the parental level increase request before the navigator continues. If the increase request is granted the playback continues without requiring the user to start the movie from the beginning. The DVD specification only states that the navigator should pause until it knows whether the request succeeded or failed. It does not describe a mechanism to accomplish this task and suggests that the Navigator calls the Temporary Parental Level Change feature built into the player 4.6.4.1 V14 197 .

Nor does the DVD specification describe any mechanism to allow the user to play multi segment parent level branches see e.g. . As such previous DVD APIs did not provide a mechanism that allowed the user to play multi segment or multiple branch parent level branches if no branches were permitted at the current user level. In the past the navigator only notified the application that the playback has stopped since no branch was available for the current parental level.

To the contrary navigator and DVD2 API compute the minimum level required to play the block and return this value along with a playback stopped notification. The application can then notify the user of the required parental level that is required to continue playing DVD content . Thus the user no longer has to guess the required level through trial and error having to restart the movie on each try.

Additionally DVD2 API extends the functionality of the DVD Annex J specification and previous DVD APIs. The DVD Annex J specification only specifies actions to perform. It does not specify how player application finds out information about the disc or the DVD navigator s state . Here new disc and navigation state query functionality is provided.

Unlike previous DVD APIs DVD2 API does not require the application writer to already have a ready copy of the DVD specification to use it e.g. due to the incomplete description of the data returned by the API . The data returned by the methods to get the textual information the title attributes audio attributes and subpicture attributes is documented so that application developers can get the necessary information from the new API and the associated documentation.

DVD2 API also allows the application to query the attributes of arbitrary title indices instead of just the current title index. DVD2 API also returns the audio stream s Karaoke information so that intelligent Karaoke applications can be implemented. DVD2 API also returns the capabilities of decoder so the application can present configuration options to the user like frame stepping in both direction smooth rewind and fast forward etc. or intelligently alter the user interface. New control functionality is also provided. For example DVD2 API allows player application to play ranges of chapters or ranges of times to select specific menu buttons just not relative buttons and allows the user to select buttons using a mouse location. It also supports the getting setting of bookmark objects and the ability to query a calculated current unique disc ID.

To better understand the synchronization mechanism of the DVD2 API and the associated navigator with the application the following sections examine various exemplarily modes of operation and point out some of the benefits and shortcomings. Essentially there are four modes of operation along with certain other variations thereto. The initial four modes are illustrated in . Each of these modes may be supported by the various methods and arrangements in accordance with the present invention.

A don t care mode or model is depicted in wherein player application sends a request to navigator without caring about what the result if any there is and or when the request is completed. An example might be a jump to location request a show menu request etc. Here player application essentially assumes that the requested operation has been completed.

In an event mode or model is illustrated. Here player application is provided notice upon a generic event sent by the navigator when the request is completed . One drawback to this model is that player application may have made more than one request and would not be able to tell the events apart.

An improvement is provided in . Here rather than having an event provide notice to player application navigator generates an object that can then be used by player application to track the status of the request. This provides player application with the ability to conduct instance tracking.

In yet another improvement as illustrated in navigator can generate an object that can be used for tracking and also a subsequent event. In this manner player application can use the objects to tell events apart. Therefore this model supports multiple instance tracking.

Before describing further details of these various models and the DVD2 API the deficiencies of a blocking only API or a non blocking only API will be described. One variation is depicted in . Here player application sends a request to navigator via DVD2 API of course . The player application must wait for a result message from navigator . One drawback to this model is that U I will probably be frozen while player application waits.

One way to solve the frozen U I problem is to provide a worker program such as is depicted in . Here the worker program receives the request and forwards it to navigator and then itself waits for the result message. Once the worker receives the result message then it is forwarded to player application . While this may free up U I it may be difficult to manage several workers operating simultaneously.

In contrast a non blocking API is equivalent to the don t care mode. There is no direct feedback on the status or result of an operation. The application must infer the status from changes in the playback time changes menu changes etc . However due to variation in disc content and structure this approach is very unreliable and error prone. With this mind the following sections provide additional details into the use of DVD2 API 

All of the IDVDControl methods in previous DVD APIs run asynchronously to the application a non blocking only model . Thus when an application calls a method the navigator performs preliminary verifications and then immediately returns a result. However in the meantime the state of the DVD Navigator may have changed and the request may fail when the DVD Navigator actually begins to execute the command.

One solution is to change the semantics of the DVD API to ensure that methods do not return until all requests complete. But to retain the asynchronous behavior applications must create separate execution paths e.g. helper threads to manage DVD API calls as descried above in a blocking only model . Multithreaded programming models always complicate application development especially simple scriptable interfaces.

Therefore to solve this problem the DVD2 API creates associated synchronization command objects. The command object allows the application to synchronize and to learn about the command s status. Each API method is extended with two extra arguments. The general form of a DVD2 API command is 

Wherein ppObject is an argument used to return a synchronization COM Component Object Model object to application and dwFlags is the set of flags passed to the method to determine the behavior and usage of the synchronization object. These are a bit wise union of the available pre defined flags.

The object returned must be released by the application. By returning a pre incremented COM object the life of the object can be correctly maintained. A variation on the interface also extends the original interface by including two methods that allow the application to wait on the start and end occurance along with other changes in the system 

The special return code VFW E DVD CMD CANCELLED is returned by the initial DVD API method by the IDvdCmd WaitForStart or IDvdCmd WaitForEnd or along with the event indication that the command was pre empted and is no longer valid.

As described above player application can determine the commencement and completion of the command by any of the following using the command object directly using no command objects listening to command related events using a combination of events and objects to aid in tracking multiple instances of a command.

By passing an IDvdCmd pointer to the command the Navigator will allocate and return a new IDvdCmd object. Calling the interface method IDvdCmd WaitForStart will block until the command begins and IDvdCmd WaitForEnd waits until the command completes. If the command has been cancelled then the Navigator will return VFW E COMMAND CANCELLED. After the application is done with the object it must call Release to free the COM object. A NULL pointer passed to the DVD API indicates that no command object should be returned to the application and the command execution should continue in the standard asynchronous mode.

The other two methods GetStartHandle and GetEndHandle return a system specific synchonization object that allows the application to wait for other requests disc I O user interface changes semaphore changes unblocking threads communications with other processes etc to be processed while it wait for the start or end events to occurs. Then the application calls the WaitForStart or WaitForEnd methods to retrieve the result. An example in the Microsoft Windows API 

Instead of managing an object the application can simply specify the DVD CMD FLAG Block flag with a null object pointer. The command will not return until it has either completed or was cancelled. The API will emulate a synchronous behavior. For example 

If an application only needs to synchronize one command or does not differentiate between command instances no synchronization object is needed and only events are required. A NULL object pointer is passed to the DVD API method and the 1Param1 value sent with the event will always be set to 0.

By specifying both objects and the DVD CMD FLAG SendEvents flag an application can track different commands. The DVD2 API call will return an object that the application can use for later reference. When the event notification is sent the DVD2 API generates a unique identifier or cookie 1Param1 for each event that the application can map back to an IDvdCmd object. The cookie approach ensures that applications will not leak memory if they miss an event and allows the DVD Navigator to verify the validity of the object.

The DVD2 API method IDvdlnfo2 GetCmdFromEvent 1Param1 maps the cookie into a command object pointer. The application must call the COM Release method on the returned pointer after it has finished processing each of these events. When the application is completely finished with the message usually after receiving an END event it must call Release on the global command pointer that it saved.

The following illustrative examples show how synchronization can be accomplished using the IDvdControl2 interface 

For clarity some of the examples refer to the following utility function used to map the 1Param1 value from EC DVD CMD events into an IDvdCmd object 

Previous DVD API commands assumed that on any change of content player application wanted to truncate the current content presentation and it switched to the new content. The improved DVD2 API commands extend the command object mechanism with the following flags 

Here the . . .  Flush flag indicates that the presentation of the current content should be immediately truncated so that new content can start to be displayed like before . The absence of the flag indicates that the current content presentation should end first. The . . .   . . . Rendered flags change the semantics of the start and end of each command. By default the command starts and ends once it has been processed. The new flags indicate that the start and end occur when the results of the change of content have been processed and presented respectively.

DVD2 API permits player applications not only to read the DVD Navigator s general purpose registers the GPRMs but also allows them to set the GPRMs using 

The combined read write functionality allows DVD applications to communicate with the program on the disc and can implement controlled unlocking or restricted access to the content. The application can use GetAlIGPRMs to read the current state and set a specific register using SetGPRM.

The SetGPRM method can also be used to synchronize the application and the DVD Navigator s virtual CPU. The SetGPRM method is executed only during the periods when the DVD Navigator is allowed to process user commands the Presentation and Still phases 3.3.6.1 V13 28 . Navigation command execution is considered to be atomic. So setting the GPRM is postponed until these phases occur. The application can use the command object and event mechanism to ensure coordination. The command object s event mechanism is serialized with event notifications such as domain changes or changes to system registers . The application can call SetGPRM and wait until the command completion event is received and then wait for an event indicating a change the DVD navigator s state possibly a domain change .

One such way to accomplish disc to application communication is illustrated by the following pseudocode 

One such way to accomplish application to disc communication is illustrated by the following pseudocode 

Even though the DVD specification does not suggest any data retrieval methods the DVD2 APIs do provide this capability. The following is a list of methods provided 

With this method applications such as video editing programs and games can accurately playback arbitrary portions of the content. Combined with the command object mechanism any application like slideshow presentation video games interludes or kiosks can be implemented using a single DVD2 API command.

AcceptParentalLevelChange BOOL bAccept Please refer to the following Minimum parental level branching section.

According to the DVD specification section 4.6.4.1 pV 14 197 when the DVD Navigator encounters a SetTmpPML set temporary parental management level command it should request permission from the application call the Temporary Parental level Change feature built into the player to temporarily raise the current level. If the parental level change is allowed the Navigator raises the parental level and branches to the restricted piece of content. Otherwise it continues with the next command.

Under the semantics of the previous DVD API when the DVD navigator executes a SetTmpPML instruction it only sends a PARENTAL LEVEL TOO LOW event to the application. It immediately continues on executing the next command as if the parental level change failed. The application receives the event stops the playback displays a user interface to change the parental level and then restarts the movie from the beginning. According to the DVD specification the Navigator is allowed to alter the parental level only when it is in the STOP Domain. As a result since the navigator does not pause at the change it must stop the playback.

With DVD2 API for example the following sequence may occur. The application notifies the API of the availability of the parental level change feature by calling the method 

When the DVD Navigator encounters a SetTmpPML instruction it sends a PARENTAL LEVEL TOO LOW event to the application. The application is expected to display some user interface to let the user increase the parental level. The DVD Navigator blocks until the application responds by calling IDVDControl2 AcceptParentalLevelChange with TRUE or FALSE and then proceeds accordingly without having to stop the playback.

The DVD specification Section 4.1.4.1 V14 22 describes a scheme for selecting different program chains usually different possible segments of content based on the current parental level. For example at a certain point in the video different versions of a scene could be available and are automatically selected by the navigator based on the parental level e.g. segments intended for PG R rated or children .

For each title the PTL MAI table maps the current parental level into a 16 bit mask. During playback the DVD Navigator obtains the current parental bit mask from the PTL MAI table. The parental bit mask is used when the Navigator encounters a parental block a collection of program chains in which each program chain has an exclusive parental bit mask . The Navigator searches each PTLID FLD in the VTS PGCI SRP Section 4.2.3 V14 62 for a program chain with a bit mask that shares common bits with the current parental bit mask.

If no program chain partially matches the current bit mask previous versions of the DVD Navigator would halt the playback and send a DVD ERROR LowParentalLevel event to the application.

To help the user certain exemplary implementations of DVD2 API uses the following algorithm to compute the minimum required parental level that would let the user continue 

The index i is returned along with the DVD ERROR LowParentalLevel event. The application can use the index to suggest a possible parental level setting to the user.

DVD navigator is configured to allow a player application to encode and store the current state of the DVD playback into an abstract object referred to a bookmark containing a persistent block of data. depicts exemplary bookmarking functionality.

To further abstract and simplify the usage DVD2 API is configured to save restore and query the state information contained in the bookmark. Player application can query information in the bookmark using the navigator and save it for later use. Player application can later resume playback by instructing the DVD navigator to restore the DVD playback state contained in the bookmark. Restoring bookmarks allows the player application to start playing from any arbitrary location and any number of them for a DVD content . The bookmarks can be stored either in short term memory storage or long term storage for example a hard drive and can be restored even after player application and or the PC has been shutdown and restarted. The bookmark not only contains the state of the DVD navigator such as internal register values playback location playback state but also the information about the current disc content being played and the user s settings. Player application can use this extra information to intelligently select the appropriate bookmark from previously saved ones that can be played for a particular disc usually the disc being played for example. Bookmarks can be also be shared between users and between various applications

The bookmarking abstract data type is comprised of two aspects 1 the actual bookmark itself and 2 the API calls used to save restore and query information contained in the bookmark. In accordance with certain exemplary implementations bookmark contains at least the following information a substantially unique disc identifier the address of the current video object unit VOBU being displayed section 5.1.1 of the DVD specification the loop count and shuffle history Section 3.3.3.2 of the DVD specification the current DVD resume information outlined in section 3.3.3.2 of the DVD specification the current DVD general parameter GPRM and system parameter SPRM values sections 4.6.1.1 and 4.6.1.2 and the current domain and phase section 3.3.3 and 3.3.6 . In certain further implementations the bookmark also includes versioning and integrity information. The bookmark can be packaged as an abstract object or as a block of binary data for storage.

To provide such bookmarking techniques DVD2 API in certain exemplary implementations supports the following methods 

Application pseudocode to implement storing the current location or to implement power saving functionality i.e. the ability to save the computer s state to enter a low power state that can be restored 

The current DVD specification has a built in unique identifier on each disc DVD unique identifier . However applications must assume that the disc authors correctly implemented the identifier unfortunately this not always so.

Many applications need a unique tag to identify a DVD disc such as when a user swaps DVD discs the playback system needs to decide if it has a new disc. If it has a new disc then it must reset the playback otherwise it can continue without interrupting the user s viewing. If it does not have the ability to differentiate discs it must always reset. A unique identifier see would provide the ability to differentiate different discs not different exact copies however .

A unique identifier also lets applications verify the compatibility of stored information with a particular DVD disc. Applications cannot successfully use cached information with the wrong disc. For example when a user attempts to recall a saved location on the disc using a bookmark the DVD navigator can ensure the data s compatibility by comparing the unique identifier stored in the bookmark with the unique identifier of the current disc. Playback only continues if the identifiers match.

Unique identifiers allow applications to associate additional information with the disc by using the unique identifier as an index into a database. For example even though the DVD specification supports textual information on the disc it is rarely used. A web based database of the disc s title and contents can be stored and retrieved by an application after it computes the identifier on the disc.

The current built in unique identifier on the DVD disc is inadequate. First the identifier is relatively large in size 32 bytes it relies on the disc author to ensure that it is actually unique and a central entity must assign ranges of identifiers to disc authors to ensure that the uniqueness is maintained between companies.

Other conventional unique identifier algorithms do not produce unique identifiers for a large numbers of discs. Here the probability that two discs are assigned the same identifier grows exponentially as the total number of DVD discs increases. With the expected growth trends in DVD discs many unique identifier routines will be inadequate. Moreover these algorithms often do not have known and or provable properties. Without known properties it is impossible to state the effectiveness or suitability of the identifiers produced.

In accordance with certain exemplary implementations of the present invention a unique identifier is generated by computing a 64 bit CRC of a concatenated or otherwise arranged binary representation of the file header and the file contents of various files in the DVD s VIDEO TS directory. This is capability is further illustrated in .

The 64 bit CRC is computed using an irreducible polynomial in the field GF 2 . An example polynomial is 

The polynomial is generated by finding an exponent n such that x 1 has an irreducible prime factor of degree 64.

The actual CRC value is computed in certain examples by concatenating all of the binary data into a single block bits bto b assigning each bit bto the coefficient xin a polynomial then computing the remainder after dividing by the polynomial P 

For each filename in the list the following structure is filled out and added to the CRC all data fields are in LSB first 

If present the first 65536 bytes of the file VIDEO TS VIDEO TS.IFO are read and added to the CRC. If the IFO file is less than 65536 then the entire file is added.

If present the first 65536 bytes of the file VIDEO TS VTS01 O.IFO are read and added to the CRC. If the IFO file is less than 65536 then the entire file is added.

Although some preferred implementations of the various methods and arrangements of the present invention have been illustrated in the accompanying Drawings and described in the foregoing Detailed Description it will be understood that the invention is not limited to the exemplary implementations disclosed but is capable of numerous rearrangements modifications and substitutions without departing from the spirit of the invention as set forth and defined by the following claims. Additionally each of the references identified above is expressly incorporated in their entirety herein by reference and for all purposes.

