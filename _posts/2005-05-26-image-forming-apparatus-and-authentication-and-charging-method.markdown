---

title: Image forming apparatus and authentication and charging method
abstract: An image forming apparatus having a hardware resource used in image forming processing and an application executing the image forming processing, and performing authentication relating to the execution of the image forming processing is disclosed. The image forming apparatus includes a character string display part and a type character string display part. The character string display part displays a character string that does not include the type of the image forming processing, and prompts the authentication. The type character string display part displays the type of the image forming processing.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07835019&OS=07835019&RS=07835019
owner: Ricoh Company, Ltd.
number: 07835019
owner_city: Tokyo
owner_country: JP
publication_date: 20050526
---
The present invention relates to an image forming apparatus performing authentication and charging and a method of performing the authentication and charging.

In recent years image forming apparatuses containing the functions of apparatuses such as a facsimile machine a printer a copier and a scanner in a single housing have been known. These image forming apparatuses have a display part a printing part an image obtaining part and four types of applications corresponding to a facsimile machine a printer a copier and a scanner provided in a single housing and operate as a facsimile machine a printer a copier and a scanner by switching the applications.

The image forming apparatuses having these functions are often used by an unspecified number of users at for instance convenience stores. In this case charging and authentication are required. A description is given with reference to of three types of screens displayed in such a case. These screens are displayed when a user intends to make a full color copy.

The screen illustrated in is displayed when a user code is required for user authentication. As illustrated a message reading IN CASE OF USING FULL COLOR ENTER USER CODE WITH NUMERIC KEYPAD AND PRESS KEY. CHANGE FOR OTHER COLOR MODES WITH SELECTION KEY. is displayed on this screen.

The screen illustrated in is displayed when a key counter key card or user code is required for user authentication. As illustrated a message reading IN CASE OF USING FULL COLOR SET KEY COUNTER OR KEY CARD OR ENTER USER CODE WITH NUMERIC KEYPAD AND PRESS KEY. is displayed on this screen.

The screen illustrated in is displayed when a key counter or key card and a user code are required for user authentication. As illustrated a message reading IN CASE OF USING FULL COLOR SET KEY COUNTER OR KEY CARD ENTER USER CODE WITH NUMERIC KEYPAD AND PRESS KEY. is displayed on this screen.

A function such as full color and a combination of authentication devices such as a user code and a key counter are embedded in the character strings displayed on the above described screens. Accordingly when a new authentication or charging method is added in the case of for instance restricting a new function or supporting a new authentication method it is necessary to re create the screen thus increasing man hours for correction.

Accordingly it is a general object of the present invention to provide an image forming apparatus and an authentication and charging method in which the above described disadvantage is eliminated.

A more specific object of the present invention is to provide an image forming apparatus and an authentication and charging method capable of reducing man hours for correction in the case of adding a new authentication or charging method.

The above objects of the present invention are achieved by an image forming apparatus having a hardware resource used in image forming processing and an application executing the image forming processing the image forming apparatus performing authentication relating to the execution of the image forming processing the image forming apparatus including a character string display part configured to display a character string prompting the authentication the character string excluding a type of the image forming processing and a type character string display part configured to display the type of the image forming processing.

The above objects of the present invention are also achieved by an authentication and charging method in an image forming apparatus having a hardware resource used in image forming processing and an application executing the image forming processing the image forming apparatus performing authentication relating to the execution of the image forming processing the authentication and charging method including the steps of a displaying a character string prompting the authentication the character string excluding a type of the image forming processing and b displaying the type of the image forming processing.

According to the present invention an image forming apparatus and an authentication and charging method that are capable of reducing man hours for correction in the case of adding a new authentication or charging method are provided.

A description is given with reference to the accompanying drawings of an embodiment of the present invention.

In the following description an authentication and charging device refers collectively to an authentication device and a charging device. When there is no particular need to refer collectively to the authentication device and the charging device they are referred to separately.

A description is given with reference to of a program installed in an MFP MultiFunction Product which is an apparatus having multiple functions. Referring to the MFP includes a program group and hardware resources .

When the MFP is turned on the MFP starts an application layer and a controller layer in the program group . For instance the MFP reads out the programs of the application layers and the controller layers from a hard disk drive HDD transfers the read out programs to a memory area and starts the programs. The hardware resources include a scanner engine a plotter engine a facsimile control unit FCU an SRAM and the HDD .

The program group includes the application layer and the controller layer which are activated on an operating system OS such as UNIX . The application layer includes programs executing processing characteristic of respective user services related to image formation by a printer a copier a facsimile machine and a scanner and a driver group .

The application layer includes a printer application which is an application for a printer a copy application which is an application for a copier a FAX application which is an application for a facsimile machine a scanner application which is an application for a scanner and a network filing application . The application layer further includes an SDK Software Development Kit application and a VAS Virtual Application Service .

The controller layer includes a control service layer a system resource manager SRM and a handler layer . The control service layer interprets a processing request from the application layer and generates a request to obtain a hardware resource a hardware resource obtaining request . The SRM manages one or more hardware resources and arbitrates between hardware resource obtaining requests from the control service layer . The handler layer manages hardware resources in accordance with a hardware resource obtaining request from the SRM .

The control service layer is configured to include one or more service modules such as a network control service NCS a delivery control service DCS an engine control service ECS a memory control service MCS a user information control service UCS a system control service SCS and a certification and charge control service CCS .

The controller layer is configured to have a GW API which makes it possible to receive a processing request from the application layer by a predefined function. The OS executes the programs of the application layer and the controller layer in parallel as processes.

The process of the NCS provides commonly usable services to applications requiring a network I O. The process of the NCS performs arbitration in distributing data received in accordance with respective protocols from the network side to applications and transmitting data from applications to the network side.

For instance the NCS controls data communications with a network apparatus connected via a network based on HTTP HyperText Transfer Protocol using httpd HyperText Transfer Protocol Daemon .

The process of the DCS controls delivery of stored documents. The process of the ECS controls engines such as the scanner engine and the plotter engine . The process of the MCS performs memory control such as obtaining and releasing memory and using the HDD . The process of the UCS manages user information.

The process of the SCS performs processing such as application management control of an operations part system screen display LED display hardware resources management and interruption application control.

The process of the SRM together with the SCS performs system control and hardware resources management. For instance the process of the SRM performs arbitration and controls execution in accordance with a hardware resource obtaining request from the upper layer using the hardware resources such as the scanner engine and the plotter engine .

Specifically the process of the SRM determines whether a hardware resource requested to be obtained is usable. If the hardware resource requested to be obtained is usable the process of the SRM notifies the upper layer that the hardware resource requested to be obtained is usable. Further the process of the SRM performs scheduling for using a hardware resource in response to a hardware resource obtaining request from the upper layer. For instance the process of the SRM directly implements the contents of requests for paper conveyance and an imaging operation by a printer engine for memory reservation for file generation etc.

The handler layer includes a facsimile control unit handler FCUH and an image memory handler IMH . The FCUH manages the FCU . The IMH allocates memory to processes and manages the allocated memory. The SRM and the FCUH make it possible to transmit a processing request to a hardware resource with a predefined function and make the processing request using an engine I F for which a PCI bus is employed.

With the above described software each application gives the CCS an instruction to display or not display a below described authentication screen notifies the CCS of an authentication setting and notifies the CCS of a charging setting. Receiving the authentication setting notice the CCS returns an authentication state corresponding to the contents of the setting. The SCS controls screen display. The SRM gives an instruction on timing of charging accompanying process execution. The USC obtains information on users in an address book and provides the information to the CCS . The NCS obtains network authentication information.

The controller board includes a CPU an ASIC the HDD a local memory MEM C a system memory MEM P a Northbridge NB a Southbridge SB an NIC Network Interface Card a USB device an IEEE 1394 device and a Centronics device .

The operations panel is connected to the ASIC of the controller board . The SB the NIC the USB device the IEEE 1394 device and the Centronics device are connected to the NB through a PCI bus.

The FCU the scanner engine and the plotter engine are connected to the ASIC of the controller board through a PCI bus.

The controller board has the local memory and the HDD connected to the ASIC and has the CPU and the ASIC connected to each other through the NB of the CPU chipset. Thus connecting the CPU and the ASIC through the NB makes it possible to cope with the case where the interface of the CPU is not open to the public.

The ASIC and the NB are connected via not a PCI bus but an AGP Accelerated Graphics Port . Thus in order to execute and control one or more processes forming the application layer and the controller layer of the ASIC and the NB are connected via not a low speed PCI bus but the AGP thereby preventing a decrease in performance.

The CPU controls the entire MFP . The CPU causes the NCS the DCS the ECS the MCS the UCS the CCS the SCS the SRM the FCUH and the IMH to be activated as processes on the OS and executed. Further the CPU causes the printer application the copy application the FAX application the scanner application the network filing application and the SDK application forming the application layer to be activated and executed.

The NB is a bridge for connecting the CPU the system memory the SB and the ASIC . The system memory is used as a drawing memory for the MFP . The local memory is used as a copy image buffer and a code buffer. The system memory and the local memory correspond to the SRAM of . The SB is a bridge for connecting the NB to a PCI bus and peripheral devices.

The ASIC is an IC for image processing including a hardware element for image processing. The HDD is storage for image data document data programs font data and forms. The operations panel is an operations part receiving input operations from and displaying information to a user.

An authentication and charging device is added to the above described hardware configuration as required. According to this embodiment a key card a coin rack a multifunction MF key card and a key counter each of which corresponds to an authentication and charging part may be employed as the authentication and charging device.

Next a detailed description is given of the CCS . The CCS achieves the same function as the authentication charging user restriction function conventionally performed by the SCS. The CCS issues information on a usable function an unusable function corresponding to an authenticated individual hereinafter restriction information as a result of role based access personal authentication by a user logon for supporting increased security. The CCS can be expanded easily at the time of introducing a new authentication or charging method.

The CCS main thread which is the interface of applications and other modules manages authentication manages charging and creates screens. The created screens are displayed on the operations panel . The operations panel and the CCS correspond to a character string display part a type character string display part and an authentication information input part.

Next a description is given of the authentication and charging module group . The authentication and charging module group includes a personal authentication thread a key counter thread an external charging device thread and a user code thread which are authentication and charging modules. The authentication and charging module group manages authentication manages charging and creates screens according to an authentication method. These authentication and charging modules are provided for corresponding authentication and charging devices but are basically threads of the same configuration. Each authentication and charging module is caused to operate based on an instruction indicating designating the authentication and charging module as a thread to operate which is described in detail below.

The personal authentication thread performs basic authentication NT authentication and LDAP authentication. The user code thread performs authentication using a user code. The key counter thread corresponds to the case of using a key counter as the authentication and charging device.

The external charging device thread corresponds to the case of using a key card a coin rack or an MF key card as the authentication and charging device.

Next a description is given of the I O module inputting and outputting information on charging and authentication. The I O module includes an internal in apparatus address book I O thread an NT server I O thread an LDAP server I O thread an external charging device I O thread an MF key card I O thread and a key counter I O thread . The I O module communicates with the modules of the application layer and the control service layer and the authentication and charging devices so as to receive the authentication state of each device and issue an authentication request.

The internal address book I O thread performs communications regarding an internal in apparatus address book. The internal address book refers to information on user addresses obtained through the UCS . The NT server I O thread communicates with a server performing the above described NT authentication. The LDAP server I O thread communicates with a server performing the above described LDAP authentication.

The external charging device I O thread communicates with an external charging device key card coin rack. The external charging device key card coin rack refers to a device for the case of using the MFP employing a key card or coin rack. The MF key card I O thread communicates with an MF key card charging device. The MF key card has a variety of functions in addition to those of the key card. The key counter I O thread communicates with a key counter.

The thread configuration of the CCS is as described above. Next a description is given with reference to of an operation of each CCM as a designated thread.

At the CCM generation stage an authentication method for operating as a designated CCM is selected. Thereafter the CCM obtains a parameter from the authentication and charging device data table . The authentication and charging device data table includes a user code parameter a key card parameter a key counter parameter an MF key card parameter and a coin rack parameter. These parameters are information on the above described authentication and charging devices.

Next the CCM obtains common parameters from the CCM control parameters . The common parameters include an authentication parameter a charging parameter a restriction information fixing part parameter and an I O to be used.

The charging management the authentication management and the screen control are generated in correspondence to the parameters. The charging management manages and executes charging. The authentication management receives authentication information and reports authentication. Further the authentication management responds to an authentication inquiry from the screen control . The screen control receives a key event from the operations panel and performs screen drawing and key event issuance corresponding to the key event. When information is determined by the key event the screen control sends an inquiry to the authentication management .

Next a description is given with reference to of a basic authentication sequence. is a sequence diagram illustrating processing performed among an application the CCS an authentication and charging device the ECS and the SRM .

In step S of the application makes usage registration with the CCS . The usage registration which is a request for registration of the application for using the CCS is normally made at the time of activation of the application . This notice is given in order for the application to request information on authentication and charging necessary for a function to be performed by the application . For instance notice is given that the copy application requests authentication and charging setting information regarding copying and a document box in order to perform processing using a document box module.

After being notified of the usage registration request in step S if the authentication and charging device is unusable because of for instance disconnection in step S the CCS notifies the application of an authentication failure AUTHENTICATION NG . If the authentication and charging device is usable in step S the CCS notifies the application of an authentication success AUTHENTICATION OK .

In step S the CCS notifies the application of authentication necessity non necessity information which gives notice of a type of authentication required in performing a function. For instance notice is given that a restriction by AUTHENTICATION METHOD is imposed on the monochrome function of a copier. A description is given below of authentication methods such as AUTHENTICATION METHOD .

Next in step S the CCS notifies the application of charging necessity non necessity information which gives notice of a type of charging required in performing a function. For instance notice is given that it is necessary to execute charging by AUTHENTICATION METHOD in the case of performing monochrome printing by a copier.

In step based on the above described information the application requests the CCS to display an authentication screen and the CCS displays the screen. This display operation corresponds to the step of displaying a character string the step of displaying a type character string and the step of inputting authentication information.

This notification of step S is performed when the application intends to perform a function but an authentication state necessary for performing the function is not AUTHENTICATION OK in order to display a message to that effect on the operations panel and prompt a user to give an instruction to obtain authentication.

For instance if the copy application intends to perform monochrome printing but the authentication state of AUTHENTICATION METHOD is not OK the request is made in order to request the CCS to display a usage restriction screen corresponding to AUTHENTICATION METHOD .

In step S the authentication and charging device notifies the CCS of the state of the authentication and charging device . Then in step S the CCS notifies the application of AUTHENTICATION OK.

Being notified of AUTHENTICATION OK in step S the application requests the CCS to erase the authentication screen and the CCS erases the screen.

In the application job execution is started and in step S a job is passed to the ECS in order to cause various engines to operate. At this point if notice is given in step S that charging is required the ECS is also notified of below described charging information as job information. With respect to charging unrelated to this job exceptionally the CCS may be directly instructed to execute charging.

In step S the ECS notifies the SRM of a process. If charging is required in step S the SRM instructs the CCS to execute charging. In step S the CCS notifies the authentication and charging device of an instruction to execute charging.

The basic authentication sequence is as described above. A description is given below of a detailed sequence. Next a description is given of the charging information. The charging information includes an authentication method number a parameter for engine control information as to whether to check the state of connection of a charging device information as to whether counting is incremental additive or decremental subtractive information as to whether to count with a key counter or a key card and user ID information.

Next a description is given with reference to of the interchange among the application the CCS and an SCS SRM . is a diagram illustrating the details of data contents in the sequence diagram of . First in step S of the SCS SRM transmits an authentication setting notification request to the CCS . Next in step S the CCS transmits an authentication setting notice to the application . Thereafter in step S the CCS transmits an authentication setting notification completion response to the SCS SRM .

A set of a device and attribute information such as DEVICE ATTRIBUTE INFORMATION corresponds to an authentication method and is the contents of the notification of the authentication necessity non necessity information of step S of . Further a set of a device and count target information such as DEVICE COUNT TARGET INFORMATION is the contents of the notification of the charging necessity non necessity information of step S of . Further the attribute information is the contents of a below described authentication method details notice.

Receiving the authentication setting notice in step S the application performs determination by the attribute information. Further in step S the application determines the authentication state and based on the determination of step S in step S the application transmits an authentication screen display request to the CCS . In step S the CCS transmits an authentication screen display notice to the SCS SRM . The SCS SRM gives an instruction to perform drawing and in step S the SCS SRM transmits an authentication screen preparation request to the CCS . The CCS changes a screen attribute and in step S the CCS transmits an authentication screen preparation completion response to the SCS SRM . Then the SCS SRM performs screen drawing.

Further in step S the SCS SRM transmits an external charging state notice to the CCS . Receiving the external charging state notice in step S the CCS notifies the application of an external charging state as an authentication state.

DEVICE DEVICE etc. shown in are IDs used for convenience in order to distinguish between authentication methods and do not represent specific types of authentication and charging devices. The specific types of authentication and charging devices are abstracted and the abstracted types are represented by the attribute information in .

Next a description is given using the tables of of an example of authentication performed with the above described configuration. These tables show authentication methods representing types of authentication and remarks corresponding to the authentication methods.

Next a description is given of the notification of an authentication setting to each application described with reference to . As described above the CCS notifies each application of an authentication setting based on an SP UP setting the authentication setting showing which authentication method is required in order to perform a function. The SP UP setting shows the contents of a setting provided by a service person giving a maintenance check of the MFP and or by a user. The setting contents are for instance that key counter authentication is required for monochrome copy printing or that key counter authentication and user code authentication are required for color copy printing.

Here the authentication setting of which the application is notified reports only information on a function requiring authentication. In addition to authentication restrictions on the function include those accompanying a user logon. However restriction information that has no direct relation to authentication is not reported as an authentication setting but is separately reported as a function restriction. The function restriction refers to a restriction on the function due to a user s individual situation which is OK as an authentication state.

Based on the SP UP setting the CCS notifies the application registered therewith registered application of a function by function authentication setting. A description is given with reference to of an example of the authentication setting. shows functions requiring authentication and authentication methods corresponding to the functions. For instance it is possible to perform full color printing by performing authentication with AUTHENTICATION METHOD or AUTHENTICATION METHOD . AUTHENTICATION METHOD or AUTHENTICATION METHOD shows that authentication is performed by selecting one of the two authentication methods of AUTHENTICATION METHOD and AUTHENTICATION METHOD . This selection is performed by the application.

In order to make the type of authentication device transparent to the application a specific authentication method name such as a user code or key counter is not presented but an abstract name such as AUTHENTICATION METHOD or AUTHENTICATION METHOD is presented as described above. When there is a change in the SP UP setting the authentication method is changed and the registered application is notified of the change. Specifically the values set by UP include a personal authentication method local NT LDAP user code no authentication the presence or absence of user code authentication the presence or absence of key counter authentication and the presence or absence of external charging device authentication. Specifically the values set by SP include the type of external charging device addition type key card MF key card .

As illustrated in the CCS notifies each application of an authentication state reported from the corresponding authentication device . The CCS stores information necessary for authentication received from each authentication device as a received authentication state. The CCS transmits authentication OK NG information to any of the applications requiring the authentication of the corresponding authentication device in order to perform its function. As described above it is determined based on the SP UP setting information which authentication method is required in order to perform the function.

Next a description is given of an authentication screen. The CCS generates an authentication screen corresponding to the usage restriction state of the MFP . The generated screen is displayed based on the instruction of the application. The authentication screen may be for instance a charging method authentication request screen requesting insertion of a key card or a user logon screen.

The CCS which thus generates an authentication screen does not have a screen that is directly aware of the action of the application or the type of a restricted function. This is because having a screen that is directly aware of the action of the application or the type of a restricted function would cause the CCS to have a corresponding screen every time an application or a new function restriction is added thus significantly reducing the extensibility of the CCS .

A description is given below with reference to the drawings of authentication screens generated by the CCS . is a diagram illustrating a screen for performing authentication for full color copying with one of a coin rack key counter and user code.

The screen of shows a fixed message display column a function display column an authentication button and a cancellation button cancel . A character string displayed in the fixed message display column corresponds to a character string displayed by a character string display part. A character string displayed in the function display column corresponds to a character string displayed by a type character string display part. The authentication button corresponds to an input object.

Thus providing the fixed message display column and the function display column separately makes it possible to specify character strings displayed in the columns and independent of each other. Further the character strings displayed in the fixed message display column and the function display column have no such relationship that a change of one affects the other. Accordingly it is easy to replace the character strings displayed in the columns and .

A description is given of the fixed message display column . As illustrated in text reading IN CASE OF USING FOLLOWING FUNCTION REMOVE ONE OF RESTRICTIONS. is displayed in the fixed message display column. Thus by using FOLLOWING FUNCTION it is possible to display a character string that does not include the type of image forming processing. Further text displayed in the fixed message display column is a character string prompting the type of authentication to be selected.

Next a description is given of the function display column . The function display column displays a character string FULL COLOR in the case of corresponding to a function name specified by the application. Thus the CCS prepares a column for displaying a character string specified by the application and displays the specified character string in the column.

Next a description is given of the authentication button . The authentication button displays an authentication button corresponding to a function. In the case of three authentication buttons are displayed. If authentication may be performed with a single type of authentication one authentication button is displayed.

The cancellation button is a button for erasing a displayed screen. Operational specifications at the time of the pressing of the cancellation button are left up to the discretion of the application that has given an instruction to display the button . Therefore at the time of requesting display of a restriction screen the application is caused to specify the presence or absence of a button a character string to be displayed in the button and an event type to be reported to the application at the time of pressing the button.

In addition it is left up to the discretion of the application whether to display an authentication screen accompanying a function restriction. In this case specifications may be such that the brightness of the selection key of the restricted function is reduced by half or that the authentication screen itself is not displayed. The CCS gives no instruction as to the specifications.

The effects of pressing down a button on the authentication screen are left up to the discretion of the application. For instance if a restriction accompanying authentication is imposed on a duplex function effects such as switching to a single side mode by pressing down a button on the authentication screen returning to the original screen without changing a setting and resetting a job are left up to the discretion of the application. At this point a key event is transmitted to the application. Accordingly a key event number is specified by the application in advance.

The basic contents of screens are as described above. A description is given below of authentication screens. illustrates a screen for the case where the authentication device is a coin rack. In the case of a coin rack the fixed message display column the function display column and a job reset button RESET JOB are displayed on the screen. The job reset button is a button for resetting a job.

A username is put in the username entry column and thereafter is entered by pressing an entry button ENTER . A password is put in the password entry column and thereafter is entered by pressing an entry button ENTER . After entering the username and password a logon is made with the logon button . In the case of a logon failure this screen can be erased with the cancellation button .

The user code entry column the username entry column and the password entry column are objects of an input entry column form.

The above described screens are example authentication screens. Thus on the authentication screen the name of a restricted function can be specified separately so that only the function name is replaced when a new combination of authentication methods is generated.

In the case of combination authentication screens corresponding to authentication methods are successively displayed on the screen. For instance when the first authentication is performed with a user code and the next authentication is performed with a coin rack or key counter first the authentication screen with a user code illustrated in is displayed and if the authentication is OK an authentication screen illustrated in is displayed. The authentication screen illustrated in is a screen for performing authentication with one of a coin rack and a key counter.

As described above the CCS generates a screen based on an instruction from the application. However the application does not request an authentication screen to be generated if authentication has been completed. For instance it is assumed that the relationship between the function and authentication is as shown in and that the authentication state is as shown in .

The table of shows the authentication states of various types of authentication indicating with respect to each authentication type whether the user is authenticated with the authentication type. The information shown in this table is retained by the CCS and reported to the application.

The application determines based on this table whether to display a screen. In this case the table of indicates that the user is authenticated with AUTHENTICATION METHOD and AUTHENTICATION METHOD . Accordingly execution of the functions other than monochrome printing shown in requires no authentication. This is indicated by showing functions and authentication states required for execution of the functions. Based on the table shown in the application determines whether to instruct the CCS to generate a screen.

Next a description is given of a usable function. In principle the authentication setting reported by the CCS is a setting for reporting lack of authentication. In the case of role based access a user logon use of the MFP may be restricted because of the function restriction attributes of individual users although the authentication state is OK.

In executing a restricted function the MFP according to this embodiment which is a system that only displays the fact that the function is restricted and requires no new authentication at the time of having an authentication result is designed so that each application receiving the authentication result displays a screen.

Accordingly at the time of reporting the authentication result AUTHENTICATION OK NG the CCS also reports a usable function which is described below using a specific example.

First a description is given with reference to of a system setting. The system setting is the basic setting of authentication in the MFP . A table showing a system setting shown in indicates that authentication is performed with a local address book for a personal authentication setting that authentication is performed with a key card for a full color function FULL COLOR that authentication is performed with a key card or key counter for a monochrome function MONOCHROME and that no setting is provided for a two color function TWO COLOR and a single color function SINGLE COLOR .

Thus the authentication methods are reported to the application not by their specific contents but by their respective numbers. Accordingly the CCS manages the details of the specific contents of the authentication methods. shows the details of the specific contents of authentication methods managed by the CCS .

Next a description is given of authentication in which an individual is identified. In the authentication in which an individual is identified an authenticated user may have limited access to functions. shows the contents of a setting for a user who has logged on a logged on user . The contents of the setting include a user setting with respect to the items of user attribute functions such as a color function and authorization to execute a copy application.

In the case of the user attribute is GENERAL a general user the color function and the two color function are NO unusable the monochrome function and the single color function are YES usable and the authorization to execute a copy application is YES authorized .

Thus when a user logs on the CCS sets the authentication state of AUTHENTICATION METHOD whose authentication method is a logon to OK and reports the usable functions of the logged on user separately from the authentication setting notice.

Based on the usable functions the authentication setting and the authentication state the application determines which function is executable. shows the determination results. According to the single color function and the copy application function are executable. In this determination a function is determined to be non executable if the authentication state is NG or the function is unusable. Accordingly for instance the monochrome function which is usable is determined to be non executable because the state of authentication with AUTHENTICATION METHOD or AUTHENTICATION METHOD is not OK.

If a user makes an attempt to execute a non executable function screen display is performed in accordance with the following rule at the time of the execution.

First in the case of newly requiring authentication the application transmits a request to display an authentication screen to the CCS . If the usage of a function is restricted for a reason other than authentication the application itself displays the fact that the function is restricted. This display is performed by for instance reducing button brightness by half or displaying a message to that effect. The display manner is determined by the application.

A function usage restriction is issued as a parameter when the authentication state becomes OK with an authentication method. When different function usage restrictions are issued in multiple authentication methods the application determines whether the function is usable based on the AND operation result of the function usage restrictions. Since the AND condition is employed the function is determined to be unusable if any of the function usage restrictions indicates that the function is unusable.

Next a description is given of notifying the application of a charging method. Based on the SP UP setting the CCS notifies each application which charging method setting charging setting is required to execute a function. For instance the CCS notifies the application that charging to a key counter is necessary for monochrome copy printing or that charging to a key counter and a user code is necessary for color copy printing.

This charging setting notification is performed as follows. As described above at the time of activation of the system the application is registered with the CCS and the CCS notifies the registered application of a function by function charging method setting.

A description is given with reference to of an example of this charging setting reported to the application. The table of shows functions requiring charging and their respective charging methods. For instance shows that the charging method is AUTHENTICATION METHOD OR AUTHENTICATION METHOD in the case of the full color function FULL COLOR . In the case of the charging method is indicated by an authentication method. This is because the authentication method specified as a charging method is part of the method reported in the authentication setting in this case and because authentication is automatically required for execution of charging in this case since authentication with a corresponding charging device should always be completed in order to execute charging. If the charging method and the authentication method are different another name such as CHARGING METHOD is used.

Thus in order to make the type of a charging device transparent to the application a specific authentication method name such as a user code or key counter is not presented but the charging method is indicated by an abstract name such as AUTHENTICATION METHOD or AUTHENTICATION METHOD .

It is also possible to assign multiple authentication methods to a single function. In this case the application employs as a charging method one of the authentication methods with which the user is authenticated first. In some applications the usage priorities of authentication devices are determined. Accordingly in the case of such applications the CCS which abstracts authentication device types determines the priorities and notifies the applications of the determined priorities.

When the SP UP setting is changed updated the CCS notifies each registered application of a charging setting corresponding to the updated SP UP setting.

Next a description is given with reference to of the operation of performing counting with respect to a charging device. In step S of the CCS notifies the application of the charging method of each mode. In step S the application determines the charging method and passes a job to the ECS .

If it is possible to use multiple authentication methods as charging methods the application or the ECS gives an instruction to execute charging with one of the authentication methods whose authentication is completed first. In step S the ECS passes a process to the SCS SRM . A count instruction request is added to the process information of the process. In step S the SCS SRM passes the process to the CCS . In step S the CCS performs counting with appropriate timing with a charging method added to the process information.

If charging to AUTHENTICATION METHOD is set with the application being notified of this charging setting the CCS which internally retains an authentication method correlation table shown in executes charging to AUTHENTICATION METHOD .

The authentication method correlation table shown in correlates charging method types with their corresponding entities. By this authentication method correlation table an authentication method entity corresponding to an authentication method can be obtained by referring to an address indicated by a pointer corresponding to the authentication method in the authentication method correlation table.

A description is given of the internal data of the CCS and their management. shows a usage registration list. The usage registration list which is a list of usage registration information composed of a requester a client ID and necessary application information retains information on registrants.

In the usage registration information the requestor is an application requesting its registration the client ID is an ID assigned to the requester and the necessary application information is application information required by the requester.

This usage registration information is created when the application is registered. shows the case where the requestors are the copy printer and scanner applications.

Next a description is given with reference to of an authentication and charging setting list. The authentication and charging setting list which is a list of authentication and charging setting information composed of a function name and a method name correlates the function name with the corresponding authentication method required for the function. The authentication and charging setting list is created based on an initial setting and an SP setting and is updated when power is turned on or the contents of a setting are changed.

Next a description is given with reference to of a method table. The method table which is composed of a method name and a real device REAL DEVICE and REAL DEVICE correlates an authentication method with a corresponding entity. For instance the table of shows that REAL DEVICE of AUTHENTICATION METHOD is a key counter and REAL DEVICE of AUTHENTICATION METHOD is a user code. This method table is also created based on an initial setting and an SP setting and updated when power is turned on or the contents of a setting are changed. The method table is correlated with the method name of the authentication and charging setting list or B .

Next a description is given with reference to of a real device management list. The real device management list which is a list of real device management information composed of a real device name a CCM name authentication type information and a state shows real device related information. Each real device name may have multiple values states set in the STATE column of the real device management list as in the case of a key card.

The real device management list is created based on an initial setting and an SP setting and is updated when power is turned on or the contents of a setting are changed. Further the real device management list may also be changed by a state notice from a CCM. The real device management information is correlated with REAL DEVICE and REAL DEVICE of the method table of .

Of the above described data the lists other than the authentication method correlation table and the method table are data that are created when needed. Accordingly reserving memory every time a list is created consumes fewer resources. In this case the data may be managed by chaining the reserved memory areas.

Next a description is given with reference to the sequence diagram of of the operation from service registration by the CCS to display of an authentication screen.

In step S of the CCS is activated to make service registration with the SCS SRM . After the registration in step S the CCS receives a system setting notice. At this point if the OCS is ready in step S the OCS notifies the SCS SRM that the OCS is ready OCS READY . In step S the OCS is notified that the OCS is ready OCS READY by the SCS SRM .

A root handle for creating a system screen is set in OCS READY. When the CCS is notified of OCS READY the CCS creates windows and items used in the authentication screen. Most of the windows and items are created at this time.

When the application is activated in step S the application makes application registration with the SCS SRM . In step S the SCS SRM transmits a system setting notice to the application .

In step S the application makes usage registration with the CCS . In step S the CCS transmits an authentication setting notice to the registered application notifying the registered application of an authentication setting.

In step S a key card transmits a chargeable state notice to the SCS SRM . In step S the SCS SRM transmits the chargeable state notice to the CCS as an external charging state. In step S the CCS transmits an authentication state notice to the application notifying the application of an authentication state.

Being notified of the authentication setting and the authentication state the application determines a function to be restricted with the authentication state of the key card and in step S the application transmits an authentication screen display request to the CCS .

Receiving the authentication screen display request the CCS retains detailed restriction information and in step S the CCS notifies the SCS SRM of the requesting application and display information relating to display of DISPLAY ON OFF an authentication screen notice . The SCS SRM retains as much display information as the number of applications. The CCS retains the detailed restriction information.

In step S the application receives OCS READY and creates an application screen. In step S the application notifies the SCS SRM that an initial screen is ready INITIAL SCREEN READY . In step S the SCS SRM transmits an operation part owner switch request to the application . In step S the application transmits an operation part owner switch response to the SCS SRM .

Immediately after completion of the operation part owner switch response in step S the SCS SRM transmits a screen preparation request to the CCS using the display information of the application retained by the SCS SRM . In response to this request the CCS selects a window to be displayed on the authentication screen selects an item to be displayed and changes the display attributes of the window and the item to OPEN or CLOSE.

The CCS does not perform drawing PAINT and in step S the CCS transmits to the SCS SRM a screen preparation completion notice in which the window handle of the window desired to be displayed is set. If a window handle is set the SCS SRM performs drawing PAINT . If a window handle is not set the SCS SRM performs no operation. In this case it is assumed that the window handle is set. Accordingly drawing is performed on the SCS side.

Next a description is given with reference to of the basic operation of authentication in the case of using an addition type external charging device. The term addition type refers to a method of adding up an amount of money in proportion to use. A key card is an example of this type of external charging device.

In step S of an external charging device transmits a state notice to the CCS . In step S the application makes usage registration with the CCS . At this point the application specifies setting information to be used for authentication and has the setting information registered with the CCS .

In step S the CCS transmits an authentication method details notice to the application . This notification is performed as many times as the number of authentication methods that may be used. A description is given below of the contents of the authentication method details notice. Based on the contents of the authentication method details notice the application stores what control each authentication method should perform.

Next in step S the CCS transmits an authentication setting notice to the application . This authentication setting notice is also transmitted as many times as the number of functions requiring authentication.

In step S the CCS transmits an authentication state notice to the application based on a state notice transmitted from the external charging device . The contents of this notification are KEY CARD NG because a key card has not been inserted in the external charging device . Here KEY CARD NG is used in this description. Actually however the name of KEY CARD is not used and the name of AUTHENTICATION METHOD X is used. Further a condition identification ID is an ID assigned to a condition in order to set conditions in the authentication method and is not determined by the contents of a condition. If the authentication method does not set a condition the condition identification ID is 0x0000 indicating nullity.

In step S the application transmits an authentication screen display request to the CCS . The application determines the authentication method from the authentication setting notice and the authentication state notice. In this case the state of the authentication method is NG. Accordingly the application requests the CCS to display an authentication screen by the notification of step S.

The CCS displays an authentication screen. Thereafter in step S the CCS receives a state notice from the external charging device being notified of insertion of a key card. As a result in step S the CCS transmits an authentication state notice to the application notifying the application of insertion of a key card.

In step S the application transmits an authentication screen display request to the CCS in order to end display of the authentication screen displayed after step S. The CCS hides the authentication screen.

When the key card is extracted in step S the external charging device transmits a state notice to the CCS notifying the CCS of extraction of the key card. In step S the CCS transmits an authentication state notice to the application notifying the application of an authentication failure AUTHENTICATION NG due to extraction of the key card. In step S the application transmits an authentication screen display request to the CCS in order to cause the CCS to display the authentication screen again. The CCS displays the authentication screen again.

A description is given of the contents of the above described authentication method details notice. The authentication method details notice reports the following seven types of parameters.

The first type of parameter indicates whether to reset a mode in execution at the time of occurrence of an authentication failure AUTHENTICATION NG . The second type of parameter indicates whether to stop reading facsimile printing and facsimile transmission at the time of occurrence of an authentication failure AUTHENTICATION NG . The third type of parameter indicates whether it is possible to obtain authentication for each color mode each paper size and each user.

The fourth type of parameter indicates whether it is possible for a user to specify the third condition on the authentication screen. The fifth type of parameter indicates whether it is possible to use obtained authentication for another operation. For instance a user code can be used for the job of the next operation unless the user code is cleared once a user is identified with the user code.

The sixth type of parameter indicates timing for canceling obtained authentication which timing may be for instance a time to shift to power saving a time of entrance into an initial setting and a time after starting execution of a function. The seventh type of parameter indicates whether the authentication method allows parallel execution of reading and printing. This type of parameter is provided in order to support a charging device such as a coin rack which requires reading and printing to be executed in synchronization with each other being prevented from advancing execution of only reading in the case of occurrence of a situation where only printing is performable at the time of execution of copying.

Next a description is given with reference to of the basic operation of authentication in the case of using a subtraction type external charging device. The term subtraction type refers to a method of subtracting an amount of money from a predetermined amount of money in proportion to use. A coin rack is an example of this type of external charging device. In this case unlike in the case of the addition type external charging device processing such as determining whether it is possible to subtract an amount of money is required thus resulting in an increase in processing.

In step S of the external charging device transmits a state notice to the CCS . In step S the application makes usage registration with the CCS . At this point the application specifies setting information used for notification and has the setting information registered with the CCS .

In step S the CCS transmits an authentication method details notice to the application . This notification is performed as many times as the number of authentication methods that may be used. Based on the contents of the authentication method details notice the application stores what control each authentication method should perform.

Next in step S the CCS transmits an authentication setting notice to the application . This authentication setting notice is also transmitted as many times as the number of functions requiring authentication.

In step S the CCS transmits an authentication state notice to the application based on a state notice transmitted from the external charging device . The contents of this notification are KEY CARD NG because a key card has not been inserted in the external charging device . Here KEY CARD NG is used in this description. Actually however the name of KEY CARD is not used as in the above described case.

Next in step S the application notifies the CCS of an authentication condition setting. An authentication condition in this case is monochrome and A4 and its condition identification ID is 0x0001. The CCS is notified of the authentication condition because the subtraction type external charging device requires the setting of the authentication condition. The CCS stores the authentication condition of which the CCS has been notified. In step S the CCS transmits a state inquiry to the external charging device . In step S the external charging device transmits a state notice to the CCS . In step S the CCS notifies the application of the state of the external charging device of which the CCS has been notified.

Being notified of the state of the external charging device in step S the application transmits an authentication screen display request to the CCS . Receiving the request the CCS displays an authentication screen and in step S the CCS transmits an authentication state notice indicating KEY CARD OK to the application . At this point the condition identification ID is 0x0000.

As a result of insertion of a key card in step S the external charging device transmits a state notice to the CCS . In step S the CCS transmits an authentication state notice to the application . At this point the condition identification ID is 0x0001. As a result the condition is satisfied. Accordingly in step S the application transmits an authentication screen display request to the CCS . Receiving the request the CCS hides the authentication screen.

Next it is assumed that the condition of monochrome is changed to full color. In this case in step S the application notifies the CCS of an authentication condition setting in order to set the condition of full color and A4. In this case the condition identification ID is 0x0001 as in step S. If for instance a different ID of 0x0002 is used instead of 0x0001 notification is also performed when the condition of 0x0001 assigned to monochrome and A4 is satisfied.

Being notified of the authentication condition setting the CCS stores the authentication condition and in step S the CCS transmits a state inquiry to the external charging device . In step S the external charging device notifies the CCS of the state of the external charging device . In step S based on the state of which the CCS has been notified by the external charging device the CCS transmits an authentication state notice to the application . In this case the contents of the notice are KEY CARD NG.

Then in step S the application transmits an authentication screen display request to the CCS . Receiving the request the CCS displays an authentication screen. Here the key card is extracted. Accordingly in step S the external charging device transmits a state notice to the CCS . In step S the CCS notifies the application of KEY CARD NG as an authentication state notice. Then the application retransmits the authentication screen display request to the CCS and the CCS displays the authentication screen.

Next a description is given with reference to of the basic operation of authentication in a remote operation. The remote operation is for instance an operation from a PC through a network.

In step S of the external charging device having a key card inserted therein notifies the CCS of the state of the external charging device . When it is determined that the operation mode is monochrome and A4 in step S the application notifies the CCS of an authentication condition setting. The authentication condition at this point is monochrome and A4. In response to this in step S the CCS transmits an authentication state notice indicating an authentication success AUTHENTICATION OK to the application .

Being notified of AUTHENTICATION OK the application starts a job. When it is determined that the operation mode is full color and A4 in step S the application notifies the CCS of an authentication condition setting. This time the authentication condition is full color and A4 and the condition identification ID is 0x0002. In response to this in step S the CCS transmits an authentication state notice indicating an authentication success AUTHENTICATION OK to the application .

Being notified of AUTHENTICATION OK the application starts a job. When the key card is extracted in step S the external charging device transmits a state notice to the CCS . In step S the CCS transmits an authentication state notice indicating AUTHENTICATION NG to the application . The condition identification ID at this point is 0x0000. Further in step S the CCS transmits an authentication state notice indicating AUTHENTICATION NG to the application . The condition identification ID at this point is 0x0001. Further in step S the CCS transmits an authentication state notice indicating AUTHENTICATION NG to the application . The condition identification ID at this point is 0x0002.

Thus as many authentication state notices as the number of condition identification IDs are transmitted. Receiving these notices in step S the application transmits an authentication condition discard notice for discarding the condition identification ID to the CCS . The condition identification ID to be discarded at this point is 0x0002. In response to this in step S the CCS notifies the application of an authentication condition discard confirmation result to the application notifying the application of DISCARD OK indicating that the condition identification ID has been discarded.

When the key card is reinserted in step S the external charging device transmits a state notice to the CCS . In step S the CCS transmits an authentication state notice indicating an authentication success AUTHENTICATION OK to the application . The condition identification ID at this point is 0x0000. Further in step S the CCS transmits an authentication state notice indicating an authentication success AUTHENTICATION OK to the application . The condition identification ID at this point is 0x0001.

The present invention is not limited to the specifically disclosed embodiment and variations and modifications may be made without departing from the scope of the present invention.

The present application is based on Japanese Priority Patent Application No. 2004 156239 filed on May 26 2004 the entire contents of which are hereby incorporated by reference.

