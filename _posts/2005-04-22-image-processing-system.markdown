---

title: Image processing system
abstract: An image processing system including an image processing device and a control device which controls data transfer to said image processing device is provided. When the control device is connected to the image processing device via the network, the control device encrypts the decrypted data and transfers the encrypted data to the image processing device via the network, and when the control device is connected to the image processing device via a leased cable, the control device transfers the decrypted data to the image processing device via the cable.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08184311&OS=08184311&RS=08184311
owner: Canon Kabushiki Kaisha
number: 08184311
owner_city: Tokyo
owner_country: JP
publication_date: 20050422
---
The present invention relates to an image processing system and more particularly to a technique of ensuring the integrity of data in transferring data to an image processing device.

A printer which prints upon reception of a print job via a network from a host terminal is commonly known as a network printer. In an environment in which a print job is transferred via a network the integrity of confidential information contained in the print job must be secured. Examples of a general method of securing the integrity of confidential information are as follows.

First when a print job containing confidential information is to be transmitted to a print node a host computer encrypts the print job and then transmits it to the print node. The print node decrypts the encrypted print job and prints it see e.g. Japanese Patent Laid Open No. 2004 086894 .

Second a print node temporarily stores a print job transmitted from a host computer and only when the print node authenticates the user by using an IC card or the like permits printing see e.g. Japanese Patent Laid Open No. 2001 188664 .

As a means for implementing the first method a printer itself directly comprises a function for decrypting encrypted data. In addition a control device may be arranged on the input stage of the printer and equipped with a decryption function. In this later case the printer does not need to include a decryption function and instead a conventional printer can be advantageously used.

In association with this Japanese Patent Laid Open No. 2001 159960 discloses a form in which a printer is connected to a set top box installed in the subscriber s house or the like in a two way communication system capable of using the Internet service. This reference discloses a technique of transferring print data to the set top box via a network only after confirming that the concerned communication channel is a secured one. This technique ensures the integrity of print data between the print data transfer source and the set top box.

At the same time it is required to maintain a certain degree of freedom in the network configuration so as to cope with various user environments and user requests. In light of this the system should allow the selection of either a configuration in which a control device and a printer having a function for decrypting encrypted data are directly connected by a cable or a configuration in which they are connected via a network such as a LAN.

When a printer does not include any function for decrypting encrypted data unencrypted data shall be transferred from the control device to the printer by directly connecting the control device and printer with a cable. This direct connection prevents any leakage of confidential information that could otherwise occur in a network configuration. Even when a printer has a function for decrypting encrypted data the processing load of data encryption and decryption may be reduced by directly connecting the control device and the printer with a cable.

On the other hand when a control device and a printer are connected via a network the integrity of the transmitted print data must be ensured differently. Japanese Patent Laid Open No. 2001 159960 described above assumes the configuration in which a printer and a set top box serving as a control device are directly connected with a cable. Thus Japanese Patent Laid Open No. 2001 159960 does not consider the integrity of the transmitted print data between the set top box and the printer when they are connected via a network.

In view of the above problems in the conventional art the present invention has an object to ensure the integrity of data transmitted between an image processing device and a control device in consideration of their connection configuration by exploiting the characteristic of the connection configuration in a system having the image processing device and the control device which controls data transfer to the image processing device.

In one aspect of the present invention a control device which controls data transfer to an image processing device includes a first connection unit configured to connect a network a second connection unit configured to connect a cable designed for data transfer wherein the cable is different from the network means for receiving encrypted data from an external device via the network means for decrypting the received encrypted data and means for when the connection to the image processing device uses the network encrypting the decrypted data and transferring the encrypted data to the image processing device via the network and when the connection to the image processing device uses the cable transferring the decrypted data to the image processing device via the cable.

The above and other objects and features of the present invention will appear more fully hereinafter from a consideration of the following description taken in connection with the accompanying drawings wherein one example is illustrated by way of example.

Preferred embodiments of the present invention will be described in detail in accordance with the accompanying drawings. The present invention is not limited by the disclosure of the embodiments and all combinations of the features described in the embodiments are not always indispensable to solving means of the present invention.

An image processing system is comprised of an image processing device and control device . The image processing device is a so called multi function peripheral having the functions of a printer image input document filing document transmission reception image conversion and the like. The control device provides an extended function to the image processing device . In this sense the control device will be called an extended control device . The image processing device and extended control device are respectively connected to a LAN communicate with another network node via the LAN and also communicate with each other via the LAN .

The image processing device and extended control device are configured so that they can also communicate via a local interface I F instead of communication via the LAN in the local I F is illustrated with a broken line to represent that the image processing device and extended control device are not connected by the local I F . The local I F complies with e.g. USB or IEEE1394. The user in general the network administrator or system administrator can select either one of the two connection configurations in advance. The local I F is preferably adopted particularly in the use of a conventional image processing device having no decryption module.

A client personal computer PC is a personal use information processing device is located on the user s desk in most cases and executes various application programs. The client PC is connected to the LAN utilizes services provided by another network node and provides services to another network node. The client PC functions as a host computer for the image processing system and thus will be called a host computer hereinafter.

A server computer is a large scale information processing device is connected to the LAN and mainly provides services to another network node via the LAN .

A printer is a peripheral device corresponding to a network is connected to the LAN and provides services of the image processing device to another network node via the LAN .

A router is a network node for connecting networks to each other and connects the LAN to a wide area network such as the Internet or a virtual private network.

As described above the image processing device provides various basic image processing functions such as a printer image input document filing document transmission reception and image conversion.

A reader image input device optically reads a document image and converts it into image data. The reader is made up of a scanner unit having a function of scanning a document and a document feed unit having a function of conveying a document paper sheet.

A printer image output device conveys a print paper sheet prints image data as a visible image on the print paper sheet and delivers the print paper sheet outside the device. The printer is made up of a feed unit having a plurality of types of print paper cassettes a marking unit having a function of transferring and fixing image data onto a print paper sheet and a delivery unit having a function of sorting and stapling a printed paper sheet and outputting it outside the device.

A control unit is electrically connected to the reader and printer and is also connected to the LAN . The control unit provides a copying function of controlling the reader to scan image data of a document and controlling the printer to output image data on a print paper sheet. The control unit also provides a scanner function of converting image data read by the reader into code data and transmitting the code data to a host computer not shown via the LAN and a printer function of converting code data received from the host computer via the LAN into image data and outputting the image data to the printer .

An operation unit is connected to the control unit formed from a liquid crystal touch panel and provides a user interface for operating an image input output system.

The extended control device is made up of a control device main body and operation unit . The extended control device preferably comprises an IC card reader used for user authentication. The control device main body is formed from e.g. a hardware architecture equivalent to a well known personal computer and can execute general software including a general purpose operating system various device drivers and various application programs. The operation unit provides a user interface for allowing the user to operate the extended control device . The IC card reader is a peripheral device provided to a general personal computer.

The image processing device and extended control device are connected to each other via the LAN and can communicate with each other. The local interface is an optional interface for providing a dedicated communication channel between the image processing device and the extended control device and is implemented by a USB or dedicated bus.

As shown in the extended control device is set behind the image processing device . Reference numeral denotes an operation unit of the extended control device . The operation unit is e.g. a liquid crystal display covered with a transparent touch panel on the surface and is electrically connected to the extended control device . The IC card reader is an I O device electrically connected to the extended control device . The operation unit and IC card reader of the extended control device are set on a dedicated stand so that the user who stands in front of the image processing device can easily operate them.

The CPU and bus controller control the overall operation of the control unit and the CPU runs on the basis of a program loaded from a ROM via a ROM I F . This program also describes an operation of interpreting PDL Page Description Language code data received from a host computer and rasterizing the PDL code data into raster image data and is processed by software. The bus controller controls transfer of data input output from each I F and performs arbitration upon bus contention and control of DMA data transfer.

A DRAM is connected to the main controller via a DRAM I F and is used as a work area for operating the CPU and an area for storing image data.

A Codec compresses raster image data stored in the DRAM by a format such as MH MR MMR JBIG JPEG and decompresses compressed stored code data into raster image data. An SRAM is used as a temporary work area for the Codec . The Codec is connected to the main controller via an I F and data transfer with the DRAM is controlled as DMA transfer by the bus controller .

A graphic processor performs processes such as image rotation variable magnification processing and gamut mapping.

A connector is connected to the main controller via an external communication I F controller and connects the main controller to the LAN . A connector is connected to the main controller via a local I F controller and connects the local I F .

A general purpose high speed bus connects an I O controller and an expansion connector for connecting an expansion board. The general purpose high speed bus is generally a PCI bus.

The I O controller is equipped with a start stop synchronization serial communication controller for two channels that transmits receives control commands to from the CPUs of the reader and printer . The I O controller is connected to external I F circuits and via an I O bus .

A panel I F is connected to an LCD controller and formed from an I F for display on the liquid crystal screen of the operation unit and a key input I F for inputs from hard keys and touch panel keys.

The operation unit comprises a liquid crystal display a touch panel input device adhered onto the liquid crystal display and a plurality of hard keys. A signal input from the touch panel or hard key is transmitted to the CPU via the panel I F described above and the liquid crystal display displays image data sent from a panel I F . The liquid crystal display displays functions and image data in the operation of the image processing device .

A real time clock module updates and saves a date and time managed within the device and is backed up by a backup battery .

An E IDE interface connects an external storage device. The embodiment uses the I F to connect a hard disk drive store image data in a hard disk and load image data from the hard disk .

Connectors and are respectively connected to the reader and printer and made up of start stop synchronization serial I Fs and and video I Fs and .

The scanner I F is connected to the reader via the connector and the main controller via a scanner bus . The scanner I F has a function of performing a predetermined process for an image received from the reader and also has a function of outputting to the scanner bus a control signal generated on the basis of a video control signal sent from the reader .

The printer I F is connected to the printer via the connector and the main controller via a printer bus . The printer I F has a function of performing a predetermined process for image data output from the main controller and outputting the image data to the printer and also has a function of outputting to the printer bus a control signal generated on the basis of a video control signal sent from the printer .

Transfer of raster image data rasterized in the DRAM to the printer is controlled by the bus controller and the raster image data is DMA transferred to the printer via the printer bus and video I F .

Software processed by the controller incorporated in the image processing device is adopted as so called firmware and executed by the CPU .

A real time OS is a real time operating system and provides running software with various resource management services and frameworks optimized for control of a built in system. Various resource management services and frameworks provided by the real time OS include multitask management thread management of substantially parallel operating a plurality of processes by managing a plurality of execution contexts of CPU processes inter task communication for implementing synchronization and data exchange between tasks memory management interrupt management various device drivers and protocol stacks implementing various protocol processes for a local interface network communication and the like.

A file system is a mechanism for storing data in a storage device such as a hard disk or memory. The file system is used to spool jobs processed by the image processing device controller and save various data.

A job device control module controls hardware of the image processing device and controls a job which uses basic functions print scan communication image conversion and the like provided mainly by hardware of the image processing device .

A management module manages the operation of the controller for example controls an internal state associated with the operation of the image processing device controller .

A control API is an application programming interface which allows built in applications on a layer higher than the control API to utilize services provided by software modules on a layer lower than the control API .

A network service allows an external network node such as the host computer to utilize the basic functions of the device by converting network protocols between the network service and the control API . The network service comprises a network server function equipped with various protocols LPR NetWare SMB PAP IPP and the like especially for network printing and makes it possible to issue a print job from an external network node such as the host computer .

The network service provides a secure network connection implemented by a technique such as encryption. The network service also provides a mechanism of easily tunneling an unsecure TCP connection by using IETF Secure Shell secsh or SSH . An example of the internal configuration of the network service will be explained in detail with reference to .

A built in application logic presentation interface and built in application UI form a built in application. By using the basic functions of the control API the built in application implements advanced functions such as copy image scan document transmission reception and document filing in addition to the basic functions of the image processing device . The built in application logic corresponds to the business logic of the built in application. The presentation interface is an interface arranged to separate the business logic of the built in application from presentation logic. The built in application UI corresponds to the presentation logic of the built in application and performs display of a graphical user interface GUI and control of an input in order to allow the user to operate the built in application. The built in application UI provides a local user interface on the operation unit of the image processing device and also provides a Web application implemented using a markup language such as HTML and a Web technique such as HTTP. The user can remote control the image processing device by connecting the Web application from a Web browser running on the host computer or the like. The presentation layer of the built in application installed as the Web application will be called a remote UI.

A built in Java environment is an interpreter environment configured mainly by a Java virtual machine. The built in Java environment is configured so that instruction string data described by Java byte codes are read and linked in execution and the Java virtual machine sequentially reads interprets and executes the instructions. This can ensure expandability and flexibility capable of dynamically adding and exchanging small part of software on firmware which is entirely statically coupled to a single load module including the real time OS. A Java native interface JNI provides Java class libraries so configured as to allow a Java program to utilize resources and services of firmware native system including the real time OS and job device control API. The basic part of the Java environment is constructed by well known Java 2 Platform and Micro Edition.

A built in application logic in the image processing device can be controlled from presentation logic implemented by an application in the system of the extended control device .

The image processing device has a flag for controlling whether to cooperate with the extended control device and the flag is stored in a nonvolatile memory not shown or the like.

A network driver is connected to the LAN controls the external communication I F controller and exchanges data via the LAN . A network communication controller controls a network communication protocol such as TCP IP and exchanges data. An encrypted data communication unit performs encrypted data communication by a predetermined encrypted data communication protocol. Communication data to be exchanged is encrypted decrypted by an encryption decryption processor .

A print application executes the function e.g. printing of a printing device. A device controller generates a control command and control data and comprehensively controls the printer .

The screen is a touch panel and each displayed function is executed by touching the frame of the function. A copy mode key is touched to perform copying operation. When the copy mode key is touched a copy mode window is displayed. An extended function key is touched to enter a mode for double sided copying overlay copying move binding margin setting frame erase setting and the like.

Reference numeral denotes a status line which displays a message representing the status of the device and print information. In copying stands by.

An image mode key is touched to enter a setting mode for hatching shading trimming and masking for a copied image. A user mode key enables registration of a mode memory and setting of a standard mode window. An application zoom key is touched to enter a mode in which a document is magnified independently in the X and Y directions and the mode of a zoom program which calculates a variable magnification ratio from the document size and copy size. An M1 key M2 key and M3 key are keys touched to invoke registered mode memories.

An option key sets an optional function such as a film projector in order to directly copy a film. A sorter key sets sorting non sorting and grouping. A mixed document key is touched to set documents of A4 and A3 sizes or documents of B5 and B4 sizes at once on a document feeder.

An equal magnification key is touched to set the copying magnification ratio to 100 . A reduction key and enlargement key are touched for reduction enlargement to a regular size. A paper selection key is touched to select a copying paper sheet. Density keys and are used to copy data at a high density every time the key is touched and at a low density every time the key is touched. A density display key changes its display left and right every time the density keys and are touched. An AE key is touched when a document whose background is dark like newspaper is copied by automatic density adjustment. A HiFi key is touched to copy a document whose halftone density is high like a photographic document. A character emphasis key is touched to emphasize a character in copying a character document.

Reference numeral denotes a log key which is touched to display log information of printed jobs. For example information on the end time user name file name and print count of a print job is displayed. Reference numeral denotes a printer selection key which is touched to select a receiving side copying machine in remote copying or cascade copying.

A guide key is touched when the function of a given key is unknown and the description of the key is displayed. A fax key is touched to perform fax and a Box key is touched to display a Box function. A printer key is touched to change the printing density or refer to detailed printout information of PDL data from a remote host computer.

A main CPU is a central processing unit which controls the whole extended control device and executes programs stored in a ROM and hard disk unit . A network interface is an interface for connecting the extended control device to the LAN . Software executed by the CPU can exchange data in two ways with the image processing device or another computer via the LAN .

A memory is generally a volatile storage for saving instructions executed by the CPU data and the like. The ROM is a read only storage for saving programs data and the like for basic hardware control. The hard disk unit is generally a nonvolatile storage for saving programs executed by the CPU calculated data and the like. The hard disk unit stores a boot program activation program a program which starts execution operation of hardware or software a plurality of applications edit files user files network management programs and the like.

A display interface is a controller used to connect a display unit for displaying the internal state of the extended control device the execution state and the like. A keyboard interface and mouse interface can connect to the extended control device an input device for allowing the user to input data and instructions.

A peripheral device interface contains specifications such as USB RS 232C serial and IEEE1394 and connects the IC card reader operation unit and local I F . As described above the IC card reader is used for user authentication to specify the user. The operation unit is made up of a liquid crystal display and a transparent sheet like touch panel adhered onto the surface of the liquid crystal display . The touch panel is a pointing device similar to a mouse. Software executed by the CPU can detect as coordinate data a position on the display that is pointed by the user on the touch panel . The touch panel is driven by the peripheral device interface . The liquid crystal display displays the internal state of the extended control device the execution state and the like. Software executed by the CPU can draw a graphical user interface on the liquid crystal display . The liquid crystal display is driven by the display interface .

Blocks in correspond to software program modules executed by the CPU of the extended control device .

An application corresponds to various applications executed by the extended control device main body .

An API is an application program interface for interfacing the application with software in the image processing device controller .

A printer driver is a module which enables the application to print. In order to realize printing the printer driver interfaces as a client installed in accordance with a print service protocol with the network service of the image processing device .

A scanner driver is a module which enables the application to scan an image. In order to realize scan the scanner driver interfaces with the control API as a client installed in accordance with a protocol corresponding to the control API in the image processing device .

A job device control interface is a module which enables the application to perform basic job control and device control. In order to realize basic job control and device control the job device control interface interfaces with the control API as a client installed in accordance with a protocol corresponding to the control API in the image processing device .

A presentation extension interface is a module which enables the application to extend the built in application UI in the image processing device . This module interfaces with the presentation interface as a client installed in accordance with a protocol corresponding to the presentation interface . With an API provided by this module the application in the extended control device can incorporate presentation logic i.e. application UI corresponding to the application UI built in the image processing device . Depending on installation of the application a function not provided to the built in application UI can be extended or customized.

A built in application extension interface is a module which enables the application to customize the built in application logic in the image processing device . This module is a client installed in accordance with a protocol corresponding to a plug in interface not shown incorporated in the built in application logic and interfaces with the built in application logic . With an API provided by this module the application in the extended control device can incorporate a plug in for replacing or extending part of the business logic of the application built in the image processing device .

An image job control interface is a module which enables the application to perform particularly a high speed image process. This module is a client installed in accordance with a protocol corresponding to the internal API of the job device control module. By a combination with image transfer via the local interface this module achieves an increase in the speed of a job for exchanging an image or document between the extended control device and the image processing device .

A general purpose operating system OS is an operating system for the extended control device . Unlike the real time OS the general purpose OS has been developed as software for providing the cornerstone of mainly an information processing device and computer. Examples of the general purpose OS are Windows Mac OS Solaris Linux FreeBSD NetBSD and OpenBSD. The general purpose OS abstracts various hardware and software resources of the extended control device and allows higher order software to easily efficiently utilize them.

The general purpose OS provides the following mechanisms a multiprocess mechanism and thread mechanism which substantially parallel execute a plurality of processes by managing a plurality of execution contexts of CPU processes inter process communication and inter thread communication which implement synchronization and data exchange between processes and between threads memory management and interrupt management which are protected for each process various device drivers and protocol stacks implementing various protocol processes for a local interface network communication and the like.

It should be noted that many device drivers for general computer peripheral devices which are commercially available comply with general purpose OSs. This is because computer peripheral devices are generally developed for general purpose information processing devices such as a personal computer in which a general purpose OS runs. By adopting a general purpose OS hardware and device drivers for various computer peripheral devices on the market can be directly or relatively easily diverted to the extended control device . The extended control device is an accessory added to compensate the expandability and flexibility of the image processing device . The purpose of the extended control device is more efficiently achieved by employing not only a hardware configuration equivalent to a general purpose image processing device but also a general purpose OS for software.

An extended control device platform is software library framework runtime module and the like serving as a cornerstone which provides the software operating environment of the extended control device . The extended control device platform includes a utility library framework and runtime modules which are prepared to be able to easily construct in the extended control device an application for cooperating with an application built in the image processing device .

A system application is formed from utility applications which are normally installed in the extended control device and help the user to utilize and manage an extended image processing system.

A user land application is formed from applications for providing the user with an extended function of the extended image processing system. Each of applications classified into the user land application can be installed and added or uninstalled and deleted. An application can also be so controlled as to be activated only when the user purchases not only the entity of the application program but also the license to execute the application program.

An MFP integrated application is a user land application corresponding to the built in application of the image processing device and allows the extended control device to use advanced functions and basic functions provided by the image processing device . The MFP integrated application interfaces with the built in application of the image processing device via the presentation extension interface and built in application extension interface . The MFP integrated application can provide the same functionality and user interface as those of the built in application of the image processing device and can also extend and provide the functionality and user interface. The MFP integrated application contains and integrates application components to .

The copy component is an application component corresponding to a copying function as one function of the built in application of the image processing device .

The box component is an application component corresponding to a document filing function as one function of the built in application of the image processing device .

The transmission component is an application component corresponding to a document transmission reception function as one function of the built in application of the image processing device .

The portal component is an application component which provides a portal site for easily invoking a frequently used function and routine process in accordance with user s preferences. The portal component combines the settings of operation parameters and a series of operations into macros throughout the application components of the MFP integrated application and provides a user interface capable of freely arranging customized buttons for executing a plurality of macros.

The main body job monitor component is an application component for referring to the status of a job in progress within the image processing device and the log of a completed job.

The device management component is an application component which provides a user interface for managing hardware of the image processing device .

A memory medium operation component is a user land application for operating various removable storages e.g. memory cards represented by a magneto optical medium drive USB storage smart card and Compact Flash connected as peripheral devices to the extended control device . The memory medium operation component can transfer a document stored in a memory medium to the image processing device to print transmit or file the document and receive an image scanned or received document or a filed document by the image processing device to store the document in a memory medium.

A encrypted data secure printing component is a user land application which provides a secure printing function of receiving an encrypted print request from the host computer temporarily storing the encrypted request and only when the operation is performed by an authenticated user and user authentication is successful decrypting the request and causing the image processing device to actually print.

A browser component is a user land application which provides a browsing function for the Web and the like on the operation unit of the extended control device .

Reference numerals and are other user land applications. As described above the user land application can be flexibly added deleted activated and inactivated.

Software modules packages classified as the system application of the extended control device include the following utility programs runtime modules and the like.

A function key panel is formed from a framework and container for arranging function menus software keys and the like on the desktop of the display of the operation unit of the extended control device. Arrangeable function keys are as follows for example default system keys e.g. log out key shutdown key counter confirmation key remaining heat key system status key system setting key and screen keyboard invoke key application context keys e.g. guide key application setting key and application status key whose operations are switched in accordance with a selected application and current application addition keys e.g. keys prepared by developing and arranging part of a unique menu in an application which are added and arranged by a selected application to help its operation.

The look feel of the key layout can be customized personalized in accordance with user s preferences. The look feel of the function key panel is switched in synchronism with the theme of the whole system. For example when a theme such as high contrast or reverse is selected the display of the function key panel is so switched as to reflect the characteristic of the theme. The function key panel allows arranging not only software keys and menus but also application components such as the clock and mail incoming flag. In the use status of a given user the function key panel provides keys user mode keyboard operation panel guide about and reset .

The key user mode instructs a currently selected application to open an environment setting dialog or activates a system environment setting program serving as one of system applications.

The key operation panel designates activation of an operation panel emulator serving as one of system applications.

The key guide instructs a currently selected application to display an on line manual in accordance with the operating status of the application by using help serving as one of system applications.

The key about instructs a currently selected application to display application information such as the version development source and copyright or displays the version and copyright information of each module associated with the entire system.

The key reset instructs a currently selected application to cancel a series of operations executed halfway by the user and roll back to a preceding check box corresponding to the current status. For example when the user touches the reset key while inputting a character string to a text input field the character string during input is cleared. When the user touches the reset key during kana kanji conversion of a character string a conversion candidate selected state is canceled and the character string returns to kana. When the user touches the reset key while changing a setting value in a dialog for setting the operating parameters of an image processing job the setting during change is canceled and returns to the initial value.

The screen keyboard is a software keyboard for emulating a physical full keyboard and the operability is optimized to operate the touch panel with a finger. The screen keyboard emulates the physical keyboard at a system level as low as possible i.e. the screen keyboard is so configured as to eliminate the necessity for discrimination from the physical keyboard at almost all system levels in consideration of a case in which a physical keyboard is optionally connected to the extended control device . By covering the front surface of the display of the screen keyboard the operability of an application serving as an input destination decreases. However the screen keyboard is so devised as not to obstruct the input and for example switching between display and non display and movement of the display position can be operated easily with a finger. The resolution of the screen keyboard is independently adjusted to prevent excessive downsizing of the keytop which is undesirable for operation with a finger as the resolution of the display further increases. The screen keyboard is targeted for internationalization and an input language or the like is switched for a destination local to which the extended control device is shipped.

The operation panel emulator is a software panel for emulating the physical operation panel of the image processing device . The operation panel emulator emulates by software a start key stop key ten key pad and the like which form the operation panel. Key codes generated upon touching various key components are mapped to key codes generated by a physical keyboard connected as an option to the extended control device . For example when a key of the ten key pad is touched a key code of the physical full keyboard that corresponds to each key is generated. The GUI of the operation panel emulator is displayed in response to a request from an application and can also be displayed by explicit operation of the user. The operation panel emulator has a plurality of modes in order to select a difference dependent on the model of the image processing device . For example when the image processing device is a fax compatible device the operation panel emulator runs in a mode having fax keys e.g. and . When an application invokes the operation panel emulator display non display of each key can be selected from the application.

An icon box is a system application for switching a current application. The icon box provides the presentation logic of an application selection list for prompting the user to select a user land application to be operated at the point. The icon box lists and displays icon images and or application names and when the user selects an application the current application is switched to the selected application. The application name can be displayed by either a text or image. The text is targeted for localization in conjunction with the internationalization framework. The resources of the icon images and application names are resources contained in user land application modules. The user can edit the display order of icons and the look feel can be switched in synchronism with the theme. The icon box itself is the selector of an application and is not a launcher. By providing the delayed activation mechanism of lifecycle management an application can be so registered as to be activated only when it is selected first. Functions such as forced termination and alert display may be added for each application.

An installer is used to install various software programs which form the extended control device . Software to be installed includes the modules of a user land application system application library driver and extended control device platform. A software module to be installed can be supplied from a local file system such as a removable medium and can also be supplied via a network.

An updater is a system application for updating various software programs which form the extended control device . Software to be updated is identical to software to be installed by the installer . A software module to be updated can be supplied from a local file system including a removable medium and can also be supplied via a network. The updater also has a function of detecting via a network update of an updater present in a server and if the updater has been updated prompting the user to update the updater.

A counter reference program is a system application for referring to a counter value. The counter reference program can refer to both the counter of the image processing device and the counter of the extended control device that counts the use of an application.

An antivirus program is a system application which prevents and detects infection of a virus and repairs the system upon infection.

The system environment setting program is a system application for referring to and editing various environment setting items preference and property of system software and hardware of the extended control device . The system environment setting program is a container capable of plugging in a plurality of components and various environment setting items are processed by components for setting them in accordance with the category. Depending on a setting target setting item access is properly controlled so that for example only the system administrator can refer to or set the system environment setting program.

A theme is a system application which provides a mechanism for unitarily setting customized items preferences of each application while maintaining the uniformity. For example when the user designates as a theme the entire tone setting or component display size setting in accordance with the user s preferences or physical feature various applications run in an operation mode complying with the theme.

An activation application selection program is a system application which controls activation and stop of an application for each user. The user can select an application from a list of applications installed in the system and change the application to an execution state. Whether execution is actually permitted is based on the user authority. The user can also select an application from running applications and change the application to a stop state. The system administrator can perform settings common to all users.

A log in dialog is a system application corresponding to a log in mechanism. The log in dialog interacts with the user necessary to start a user session in which the user utilizes the extended image processing system. In the necessary dialog the system demands of the user the entry of information domain name user name and password necessary for user authentication. The entry of the user name can be set to be more easily selected from a user list in addition to text input. Especially in an operation of allowing a guest user user not required to be authenticated to manipulate the system log in operation by the guest user can be facilitated. The setting of the log in method is changed by the system administrator user. Since the log in dialog comprises a user interface displayed when the user does not log in during a system session other than a user session a function of performing management operation shutdown or the like of the system session or a function of displaying the state of the image processing device may be added. To perform user authentication based on an IC card smart card or biometric authentication at the start of a user session the log in dialog can be replaced with the implementation of a dedicated log in dialog the implementation of the log in mechanism can also be replaced similarly .

A user management program is a system application for managing a user who utilizes the extended image processing system and managing the user authority.

An address book is a system application for connecting a directory service inside or outside the system and editing directory information. The address book includes destination information but is not limited to this and the attributes of various entities such as the user organization device and service are processed as directory information.

A status ticker is a system application for displaying status information and messages notified by the system and application. The status ticker can display a text icon image and the like. The status ticker also performs priority based arbitration and time division display for a plurality of parallel message display requests. The message display of the status ticker corresponds to various display effects by an animation and the like.

A system status monitor is a system application for monitoring a system status and application status associated with both hardware and software of the extended control device . The system status monitor also allows confirming information on the versions and copyrights of various modules which form the extended image processing system .

A log viewer is a system application for referring to and managing pieces of log information of the systems and built in applications of the extended control device and image processing device .

A system setup program is a utility system application for assisting an initial setup procedure in installing the extended image processing system a replacement procedure in replacing the image processing device with a new model and a recovery procedure when the system of the extended control device is destroyed owing to any trouble and need to be recovered.

A backup program is a system application for saving data stored in the hard disks and nonvolatile memories of the extended control device and image processing device to a secure storage means e.g. a removable medium external storage or network storage connected to the extended control device and restoring the moved data.

A screen saver is a system application for controlling display so as to prevent burn in of the display when the user does not use the operation unit of the extended control device . The screen saver can also play back an animation which shows convenient use of the extended image processing system . Also the screen saver can display alarm information such as shortage of paper in the image processing device display a virtual bulletin board describing a message e.g. announcement of the date and time of a periodic maintenance set by the system administrator or the like and acquire and display the latest information e.g. weather forecast or news from the server via a network. In an operation form in which a plurality of users alternately log in and use the extended control device the screen saver performs an auto log out process for automatically logging out for a user who forgot to log out and left the device.

A help system is a system application for displaying a document which explains e.g. how to use the overall extended image processing system and assisting each user land application in displaying the guide document. The help system has a portal function of integrating as the whole system guide document contents supplied by respective modules such as a system module and application module. An application program can instruct the help system to present to the user an arbitrary portion in contents. The application can therefore present optimal information to the user in accordance with the operation status. The help system is configured as a Web application can display a guide document on the operation unit of the extended control device and can also display a guide document on a Web browser running in the host computer or the like.

A document viewer is a system application for displaying document data of various formats such as a text image and application specific format. Examples of the displayed document format are a text a document described by a markup language such as HTML XML or SGML an image of JPEG PNG TIFF or JBIG a document of a page description language such as LIPS or PostScript a document of PDF or the like a program accompanied with display such as Macromdia Flash Sun Java or Applet an animation and document data based on proprietary formats specific to various application programs such as a wordprocessor presentation and spreadsheet. Part or all of a document processed by the document viewer can undergo printing scanning transmission reception filing and the like by the image processing device .

A file operation program is a system application for operating file systems constructed in various storage means incorporated in or connected to the extended control device a file system of the image processing device and network shared file systems provided by the server computer and host computer via a network.

A document management program is a document management system installed in the extended control device . The document management program provides a function of implementing storage search and management of various document data by using the file system of the extended control device the database management system of an external server and the like.

A system session management package manages the configuration and setting of the whole system in order to manage the sessions of the entire system from boot up to shutdown of the extended control device . The system session management package also manages the lifecycle of daemon services system application and user application installed as resident applications .

A power control package manages power control such as power saving setting of the extended control device . The power control package manages hardware systems e.g. WakeOn LAN and ACPI and BIOS setting.

A user session management package manages log in sessions by the user from log in to log out. The user session management package manages the lifecycle of console applications system application and user application running during a log in session by the user . The user session management package assists the log in session management mechanism of a Web application.

A log in mechanism allows the user to start a user session and specifies the user by user management and user authentication packages. For the purpose of integration into a user environment a log in mechanism which satisfies each need can be plugged in. For example log in mechanisms based on user authentication using an IC card smart card and biometric authentication can be integrated.

An access control package manages for each user and a group to which the user belongs the access authorities of various resources which form the image processing system .

A user management authentication package manages a user account which uses the system and specifies identifies the user. What you have authentication based on an IC card smart card and what you are authentication based on biometric authentication can be utilized in addition to what you know authentication based on a password.

A directory service cooperation package assign to an external directory service user management user authentication or directory information management of the extended control device .

A directory is a local directory service of the extended control device and manages information on the user and various resources. The managed information includes the attributes of all entities managed by the directory service and the relationship between entities. For example entities managed by a directory service such as NDS are a user printer file server and the like. Management targets are resources in the system of the extended control device and resources in the image processing device .

An application lifecycle management package manages the lifecycles installation update uninstallation activation interruption and stop of a system application and user application.

A license management package manages the license of each application in the extended control device .

An application counter counts the use amount of each application installed in the extended control device and the use amount of a system resource accompanying the use of the application. The application counter can count not only for the total system but also for each user.

An environment setting management package is a database which holds the environment settings preference property and configuration of the whole system and respective applications. The environment setting management package manages user independent common settings and settings specific to each user.

A resource management package helps structurize and manage various resources localizable character string icon image sound plug in GUI description auxiliary data and the like which form an application.

A personalized framework provides a framework for reflecting the user s preferences horizontally on the application specific settings of a plurality of applications. The personalized framework implements a theme for example when the tone of the entire screen is selected the tone of each application is synchronized with the selected tone and user specific general purpose environment settings POP server information or the like referred to commonly by a plurality of applications.

A user assistance package is a mechanism of registering and managing documentation guide help manual tutorial and the like of the whole system and applications of the extended control device and assisting the user in using the system and applications.

An input package processes an input event from the user. Event input sources from the user in the interaction between the user and the system of the extended control device are a physical keyboard the hard keys of the operation unit a pointing device e.g. mouse a screen keyboard the emulator of the operation unit and screen function keys on the function key panel. The input package also performs a process associated with an input method input means or front end processor for inputting characters of each language .

A status message management package accepts and manages a status or message asserted by each application. The status message management package provides a mechanism which allows the user or another application to acquire the status or message. For example the status ticker acquires the message.

A logging package provides a mechanism of recording the log of each application. A status in which an application transmits a message to application status message management and part of the message are automatically logged. The logging package processes not only a log for the end user but also a log for debugging an application by the developer.

A window manager is implemented in cooperation with the window manager of the native general purpose OS optimized for the extended control device and is independent of the OS. The window manager controls display and overlapping of GUI windows opened by various applications. The window manager provides a window title menu and slider which can be easily operated with a finger.

A GUI tool kit includes a GUI framework GUI components and runtime modules which design the look feel for the system of the extended control device .

A sound package controls presentation of information to the user by the system and applications with a tap sound alarm sound and the like. The library of sound data designed for the system of the extended control device is prepared. Sound setting is targeted to personalization.

A secure communication channel provides a secure network connection implemented by a technique such as cryptography. The secure communication channel also provides a mechanism of easily tunneling an unsecure TCP connection by using IETF Secure Shell secsh or SSH .

A secure file system provides a secure file system and is implemented by a technique such as cryptography.

A key management package provides a mechanism of securely managing a key necessary for various cryptographic processes.

An image processing package provides a mechanism for various image processes. The image processing package also provides a distributed imaging mechanism of allowing the application of the extended control device to utilize as a distributed service a dedicated image processing function using image processing hardware or the like incorporated in the image processing device . OCR and block selection techniques are also treated as part of the image process.

A presentation extension interface provides a communication mechanism from presentation logic implemented by an application in the system of the extended control device to the business logic of a built in application in the image processing device .

A built in application extension interface is implemented by an application protocol and a framework for converting the business logic of a built in application in the image processing device into a distributed component.

A job device control interface is a primitive interface which provides a universal control model common throughout the product series of the image processing device . The job device control interface allows the application of the system of the extended control device to control the device function of the image processing device . The job device control interface cannot interface software in the extended control device and a built in application layer in the image processing device .

An image job control interface is a high level interface for performing at a high speed a process accompanied with image transfer e.g. printing or scanning by the image processing device . The image job control interface allows an application in the system of the extended control device to utilize the device function of the main body of the image processing device . The interface cannot interface with a built in application layer in the main body of the image processing device .

A printer driver is a mechanism of issuing a print job fax transmission job document file storage job from the application of the extended control device to the image processing device by using a print framework provided by the native general purpose OS .

A scanner driver is a mechanism of issuing a pull scan job from the application of the extended control device to the image processing device and acquiring a scanned image by using an image scan framework provide by the native general purpose OS .

An inter application communication package provides a communication mechanism between processes and between threads of software running in the extended control device . Since the general purpose OS of the extended control device provides an independent memory space which is protected to each process running in the extended control device communication between applications running as different processes requires a special mechanism. The inter application communication package implements a transport layer of inter process communication by using mechanisms such as a shared memory pipe and socket provided by the general purpose OS . An application protocol layer of inter process communication is based on exchange of XML based messages using the XML protocol SOAP and a tool kit framework and engine which assist treatment of the XML protocol are provided. The inter application communication package also includes a framework for assisting construction of a distributed system by a plurality of software programs which are distributed at a plurality of nodes and cooperate with each other via a network like the extended control device and image processing device and the extended control device and an external system. Some frameworks are based on the XML protocol independent of a programming language and some frameworks are based on RMI which is a Java distributed object technique.

A macro scripting package is a macro mechanism of combining a series of software processes into a single process by a technique such as end user programming scripting or example learning user operation is so recorded as to be reproduced . With the macro scripting package the user can combine a series of processes in a single application into a macro and can also register and utilize a combination of processes of applications as a macro such as a routine job.

An execution scheduling package is a mechanism of automatically executing a desired process in synchronism with scheduled time execution similar to cron as a UNIX utility the event of a system session e.g. boot up or shutdown or the event of a user session e.g. log in or log out .

A Web server is a service of exchanging data with a request source in response to a request based on a well known network protocol HTTP or more secured HTTPS .

An application server cooperates with the Web server to provide an operating environment for a Web application which dynamically exchanges data with a client. The application server transfers as a request an HTTP request message received by the Web server to a proper application corresponding to the request message receives a response from the application on the basis of the processing result of the application and sends back the response as a corresponding HTTP response message to the request source of the original HTTP request. The application server includes a template engine for dynamically generating a message by using a combination of a template and a program based on the template language in order to efficiently develop and operate a Web application. The application server comprises an application framework based on an MVC Model View Controller architecture in order to efficiently develop and operate a Web application.

A SOAP engine is used to facilitate development of a processor which processes a well known XML protocol. The SOAP engine is so configured as to be synchronized with the application server . The SOAP engine processes a SOAP request message sent from a SOAP client and transfers the message to appropriate software for processing a message. After the software for processing a message completes a proper process and returns the message the SOAP engine generates a SOAP response message corresponding to the return and sends it back to the requesting SOAP client.

An XML took kit assists software programs in the extended control device in executing processes such as interpretation generation and conversion of XML and various markup languages defined as applications of XML.

The basic part of a Java platform is constructed by a Java platform well known as Java 2 Platform Standard Edition or Java 2 Runtime Environment.

The display monitor is an LCD touch panel having a resolution of 1 024 dots 768 dots. An application display area is set around the center of the window and a plurality of windows starting from a copy window are superposed at the same size as shown in . When viewed from the user only one front window is seemed to move. An icon box on the left end of the window corresponds to the above described window switching means. An application name and icon are displayed in each window in one to one correspondence and when many available applications exist and cannot fall within the window they can be scrolled and displayed.

By touching an arbitrary icon on the icon box a corresponding window is displayed in the application display area. A function key panel at the top of the window provides a set of function buttons commonly used by the extended operation unit . By touching each button another application such as an application guide screen keyboard to be described later or operation panel emulator can be activated. Further the key code of a reset key or the like can be transmitted to another application.

The screen keyboard enables character input via an LCD touch panel. The layout can be changed to a 101 key keyboard 106 key keyboard or the like in accordance with keyboard setting.

The operation panel emulator enables inputs similar to inputs from the ten key pad start key and stop key of the hardware operation unit of the image processing device .

The host computer comprises a CPU which processes a document containing a figure image character table including spreadsheet and the like on the basis of a document processing program or the like that is stored in a ROM or hard disk HD or supplied from a floppy disk drive FD . The CPU comprehensively controls devices connected to a system bus .

Reference numeral denotes a RAM which functions as a main memory work area and the like for the CPU . Reference numeral denotes a keyboard controller KBC which controls instruction inputs from a keyboard KB pointing device not shown and the like. Reference numeral denotes a CRT controller CRTC which controls display of a CRT display CRT . Reference numeral denotes a disk controller DKC which controls the hard disk HD and floppy disk drive FD storing a boot program various application programs font data user files edit files printer control command generation programs to be referred to as printer drivers hereinafter and the like. Reference numeral denotes a network interface card NIC which exchanges data in two ways with a network device via the LAN . Reference numeral denotes a controller PIO which controls a peripheral device is connected to an IC card reader writer CARD and reads writes information of an IC card.

A software configuration for implementing a encrypted data secure printing function installed in the host computer will be explained with reference to .

An application is an application program such as a wordprocessor spreadsheet program or Internet browser.

A printer driver converts data created by the application into print data of a printer control language interpretable by the image processing device and generates print job data containing print data.

An encryption engine encrypts print job data and generates the first secret key as the first encryption key for encrypting data.

A user interface opens various registered windows and executes various data processes on the basis of commands designated with a mouse cursor not shown or the like on a CRT . In executing printing the user opens a window associated with print setting and performs setting of a printer and setting of a printing method for a printer driver including selection of a printing mode.

A card manager controls access to an IC card encrypts and decrypts the first secret key and acquires a serial number or the like.

In the host computer when the application designates execution of printing the printer driver creates print job data. The created print job data is sent to the encryption engine . The encryption engine receives the print job data encrypts it with the first secret key encrypts the first secret key with the public key of the IC card and sends back the encrypted print job data and first secret key to the printer driver . The printer driver receives the encrypted print job data and first secret key and outputs them to the spooler .

An example of the encrypted data secure printing component of the extended control device will be explained. is a block diagram showing an example of the internal configuration of the encrypted data secure printing component .

A printing application is an LPD module which receives an encrypted print job. The received print job is saved as a save job in the hard disk unit while the job is kept encrypted.

An analyzer is a module for analyzing the print job and acquiring a job name job owner name encryption method encrypted first secret key and the like.

A storage management unit is a module for managing as a job list job information of the save job stored in the hard disk unit .

A decryption unit is a module for decrypting with the received first secret key the encrypted print job transferred from the job management unit . The decryption unit sequentially transfers decrypted parts to a transmission unit .

The transmission unit is a module for transmitting the print job decrypted by the decryption unit to the image processing device .

A encrypted data secure printing API undertakes the main process of encrypted data secure printing and the following process is performed using this API.

For example the encrypted data secure printing API performs filtering of the job list on the basis of the serial number of an IC card inserted into the IC card reader . The filtered job list is displayed on the liquid crystal display via a user interface .

When the user selects a job and clicks a print start button to designate the start of printing the user interface requests a card manager to decrypt the first secret key. The encrypted data secure printing API restarts the job by using the decrypted first secret key and job handle.

When the user selects a job and clicks an erase button to designate erase of the job the encrypted data secure printing API erases the job.

Depending on setting the encrypted data secure printing API can restart a job without waiting for selection of a job by the user after an IC card is inserted.

In step S encrypted print job data transmitted from the host computer is received. In step S it is determined whether reception of the print job data has ended. If YES in step S the process advances to step S if NO returns to step S to repeat the reception process.

In step S the encrypted print job data is saved as the save job in a storage device hard disk unit . In step S the print job data saved in the hard disk unit is analyzed to acquire the job name job owner name encryption method and encrypted first secret key.

In step S it is determined whether an IC card is inserted in the IC card reader . If the IC card is inserted the process advances to step S if NO returns to step S. In this manner the process does not advance to subsequent steps unless an IC card is inserted.

In step S a serial number is acquired from the IC card. In step S a job list filtered by the serial number of the IC card is displayed in a user interface window as shown in . The user can select a job to be printed from the list.

In step S it is determined whether the user has selected a print job from the job list. If YES in step S i.e. a print job has been selected the process advances to step S if NO returns to step S.

In step S it is determined whether the user has designated the start of printing of the print job selected in step S. If YES in step S i.e. the user has designated the start of printing the process advances to step S if NO returns to step S.

In step S the first secret key encrypted with the first public key of the IC card is decrypted via the IC card. The encrypted print job data is read out from the hard disk unit in step S and decrypted with the first secret key in step S.

In step S it is determined whether a logically secure communication channel has been selected for communication between the extended control device and the image processing device . The logically secure communication channel means a secure connection implemented by a technique such as cryptography. More specifically the LAN is used to connect the extended control device and image processing device and the integrity of communication is ensured by cryptography.

If a logically secure communication channel is determined in step S to have been selected the process advances to step S to encrypt the print job data with the second secret key as the second encryption key. In step S the print job data encrypted with the second secret key is transmitted to the image processing device and the process advances to step S.

If no logically secure communication channel is determined in step S to have been selected the process advances to step S to determine whether a physically secure communication channel has been selected. The physically secure communication channel means a connection which inhibits electronic eavesdropping of transmission data in normal use. More specifically the extended control device and image processing device are connected by the local I F represented by USB Universal Serial Bus or IEEE1394. Also an external communication I F not shown is prepared for the expansion connector in addition to the external communication I F and the extended control device and image processing device are connected directly i.e. physical one to one connection by Ethernet 10BASE T 100BASE TX or the like using a so called cross cable without using any HUB. If the cable between the extended control device and the image processing device is detected to be a cross cable or if the user designates the use of a cross cable the extended control device determines that a physically secure communication channel has been selected.

If a physically secure communication channel is determined in step S to have been selected the process advances to step S to directly transmit the print job data to the image processing device and to step S.

In step S it is determined whether transmission has ended. If YES in step S the process ends if NO returns to step S and is repeated.

If no physically secure communication channel is determined in step S to have been selected the process ends. That is if the selected communication channel is neither physically nor logically secure the process ends without performing any transmission process.

The embodiment of the present invention has been described in detail. A public key in an IC card is adopted to encrypt the first secret key used between the host computer and the extended control device in the above embodiment but the cryptographic method available in the present invention is not limited to this. For example encryption may use an arbitrary password input at the start of printing or a key generated from a password input.

The above embodiment is related to a process of ensuring the integrity of print job data transmitted between the host computer the extended control device and the image processing device . The print job data is data for the printing function of the image processing device and the present invention can also be applied to general data including data for respective functions document filing document transmission reception image conversion and the like implemented by the image processing device .

Note that the present invention can be implemented by supplying a software program which implements the functions of the foregoing embodiments directly or indirectly to a system or apparatus reading the supplied program code with a computer of the system or apparatus and then executing the program code. In this case so long as the system or apparatus has the functions of the program the mode of implementation need not rely upon a program.

Accordingly since the functions of the present invention are implemented by computer the program code installed in the computer also implements the present invention. In other words the claims of the present invention also cover a computer program for the purpose of implementing the functions of the present invention.

In this case so long as the system or apparatus has the functions of the program the program may be executed in any form such as an object code a program executed by an interpreter or script data supplied to an operating system.

Examples of storage media that can be used for supplying the program are a floppy disk a hard disk an optical disk a magneto optical disk a CD ROM a CD R a CD RW a magnetic tape a non volatile type memory card a ROM and a DVD a DVD ROM a DVD R and a DVD RW .

As for the method of supplying the program a client computer can be connected to a website on the Internet using a browser of the client computer and the computer program of the present invention or an automatically installable compressed file of the program can be downloaded to a recording medium such as a hard disk. Further the program of the present invention can be supplied by dividing the program code constituting the program into a plurality of files and downloading the files from different websites. In other words a WWW World Wide Web server that downloads to multiple users the program files that implement the functions of the present invention by computer is also covered by the claims of the present invention.

It is also possible to encrypt and store the program of the present invention on a storage medium such as a CD ROM distribute the storage medium to users allow users who meet certain requirements to download decryption key information from a website via the Internet and allow these users to decrypt the encrypted program by using the key information whereby the program is installed in the user computer.

Besides the cases where the aforementioned functions according to the embodiments are implemented by executing the read program by computer an operating system or the like running on the computer may perform all or a part of the actual processing so that the functions of the foregoing embodiments can be implemented by this processing.

Furthermore after the program read from the storage medium is written to a function expansion board inserted into the computer or to a memory provided in a function expansion unit connected to the computer a CPU or the like mounted on the function expansion board or function expansion unit performs all or a part of the actual processing so that the functions of the foregoing embodiments can be implemented by this processing.

As many apparently widely different embodiments of the present invention can be made without departing from the spirit and scope thereof it is to be understood that the invention is not limited to the specific embodiments thereof except as defined in the appended claims.

This application claims priority from Japanese Patent Application No. 2004 133913 filed on Apr. 28 2004 the entire contents of which are hereby incorporated by reference herein.

