---

title: Process for securing the access to the resources of an information handling system (I.H.S.)
abstract: A process for securing the access to the resources of an Information Handling System (I.H.S.) in accordance with the present invention which involves the steps of:


url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07877614&OS=07877614&RS=07877614
owner: MOBILEGOV France, S.A.R.L.
number: 07877614
owner_city: Sophia Antipolis
owner_country: FR
publication_date: 20051201
---
The invention relates to Information Handling telecommunications and more particularly to a process and apparatus for securing access to an Information Handling System IHS 

The constant progress of the communication systems and technology particularly with the explosion of the Internet and intranet networks has resulted in the development of an era of information and services. Nowadays computers and more generally the Information Handling Systems I.H.S. such as the desktop computers the laptop computers and any type of hand held or portable systems can be used for accessing a wide variety of transactions or services wherever the user or the customer of the new information era is.

This clearly raises the problem of the security of access to the source of information and more generally to the transaction and services.

In the new world of information exemplified by the development of the Internet and intranet networks security issues are becoming more and more critical.

Some techniques are already known for solving at least partly the problem of security of access to sensitive databases and more generally to any Information Handling System.

One of the first techniques which was used was the combination of the well known user id and password which guarantees up to a certain extent that a user trying to access a predetermined system is an authorized user. Any user having neither user id nor the corresponding password will be considered as an unauthorized user and the access to the resource will be denied. While such a system has shown great efficiency in the past it now shows to be clearly insufficient in the more recent systems.

The combination of the user identifier and the password was improved by the use of a specific smart card reader. In a more sophisticated way the logon procedure is replaced or completed by the simultaneous use of a secure smart card reader in order to enable a remote system to make sure that the supposed user is the one who owns the authentication smart card. Clearly such a solution is a significant improvement brought to the security of the system but it does not prevent any unauthorized modification or setting to the configuration of the system requesting access to the service.

More sophisticated systems were developed based on the use of biometric identification or even the checking of some parameters internal to the user configuration such as the Internet Protocol I.P. address of the customer home or office when the latter tries a connection to a remote system. Such systems provide partial solutions to some security issues but do not provide an overall solution which can be used for a wide variety of IHS systems based on multiple configurations which encompasses as well as the user data and the internal configuration of the system.

No solution guarantees that the system has not been modified. Simple modifications like adding devices such as USB data storage or replacing a biometric reader by another device may be harmful as they allow bypassing of applications security.

Clearly there is still a need for a global solution for improving security in computers and more generally IHS systems based on a wide variety of machines and their various configurations.

It is an object of the present invention to improve security in the access of an Information Handling System I.H.S. 

It is another object of the present invention to provide a process which is applicable to a wide variety of computers and machines opened to different components and configurations which significantly improves security brought to the access to a network or to a local service.

These and other objects are achieved by the process for securing the access to the resources of an Information Handling System I.H.S. in accordance with the present invention which involves the steps of 

The invention significantly increases the security of the system by involving two successive qualification and validation processes. The qualification process involves the generation of an encrypted signature which encompasses selected components of the hardware and software configuration of the machine for the purpose of generating a reference signature. In this way the process becomes available for a great number of machines and configurations. Once generated the second validation process uses the reference signature as a comparison element for the purpose of guaranteeing that no changes in the configuration were brought to the machine.

In one preferred embodiment the system qualification file process is characterized in that the system qualification file is organized under a structured form listing a set of generic components associated with component presence parameters CPP defining whether the presence of the component is mandatory prohibited or optional.

Preferably the qualification process is used for checking conformity of every component identified with the system with the corresponding Component Presence Parameter CPP .

In one embodiment during the qualification process a system qualification file is created which is selected among a set of predefined templates corresponding to different levels of security or different applications.

Preferably the system qualification file SQF comprises for each generic component being listed a set of fields which receives Component Identification Data CID identifying the component and Component Contextual Data CCD for storing data retrieved by the component.

The invention can be used for securing a transaction in a communication session between a system and a remote server. In that case preferably the reference qualification signature is stored within the server which increases the security.

Alternatively the invention can be used locally by storing the reference qualification signature on a stand alone computer and therefore the two successive qualification validation processes permit securing the access to the resources of the system.

Typically components such as a GPS receiver or biometric sensors can be used for increasing the level of security of the transaction.

The process and apparatus will be more particularly described in reference to which illustrates a basic structure of a system for embodying the present invention.

Generally speaking the system may be any Information Handling System or device which is equipped with processing resources. This clearly includes without any limitation desktop computers portable computers and laptops hand held or pocket PC s also known as Personal Digital Assistant P.D.A. and even the latest mobile phones equipped with processing resources.

In addition to the motherboard the system further includes a set of external devices such as the traditional main devices i.e. the well known display keyboard mouse equipment and some storage facilities hard disks floppy disks CDROM or DVD ROM drives etc. . The system may further includes secondary devices attached to the motherboard via appropriate I O ports i.e. a printer a scanner video and photo equipment communication devices Bluetooth WIFI Infrared telephony GSM GPRS modem and even more specialized devices such as a radio frequency identification RFID reader a Smart Card reader a biometric reader and more generally any other equipment which is likely to be a source of information.

System is operated under the control of software code which is organized in low level code the known Basic Input Output System BIOS code cooperating with the Operating System O.S. and higher level code including special software components and applications. In the preferred embodiment of the invention system is operated under the well known WINDOWS operating system marketed by MICROSOFT Corp. A hand held computer can be equipped with the WINDOWS CE Trademark of Microsoft Comp. operating system designed for pocket PCs. Clearly those skilled in the art will adapt the invention to any alternate operating system such as LINUX or PalmOS for instance.

Considering now more particularly the information which system may access through its general purpose and more specialized devices it can be seen that system is given access via interface to a wide range of information such as contextual or environmental information as well as user related information . Environment information may be without any limitation information regarding Global Positioning System G.P.S. the date and the time the relevant temperature of the room wherein the system is being operated the phone line number provided by the modem adapter the Media Access Control MAC IP address assigned by the network adapter and so on. User related information may include data such as biometric data PIN code login password ID card or any personal information provided by the user.

As it is illustrated in the system is viewed as a set of hardware and software components which are combined together in order to provide the user with an access to some resources or the completion of a given transaction for instance with a not known remote server .

The invention achieves high security in transaction or any service by systemically performing prior to any transaction a complete authentication procedure which includes both a qualification and a validation procedure.

During both the qualification and the validation procedures all the components forming part of the hardware or software equipment of the system being authenticated are identified checked and validated as will be described hereinafter with details.

Every component within system is identified registered and validated prior to the transaction or prior to accessing any secured service. In the frame of the subject invention a component is understood to encompass hardware and software elements which are constituents of the system. More precisely a component is a constitutive element of a system. It can be a built in card motherboard network adapter card a microprocessor chip a memory chip a hard disk and so on. More generally a peripheral device such as a biometric reader and a software component or application program is considered to be a component.

In the preferred embodiment of the invention every component is associated to component data which includes without limitation Component Identification Data CID and Component Contextual Data CCD .

Component Identification Data CID is an identifier which uniquely identifies the component itself. Clearly it can be any unique alphanumerical string which identifies the corresponding component be it hardware or software.

It should be noticed that in the technical field of computers it is common practice to the product manufacturers and to the providers of individual parts to assign references which individually identify one particular element. For instance each processor has a unique serial number each installed software under Windows for example or software component such as Active X has a Globally Unique Identifier GUID and or a ClaSs IDentifier CLSID . For the software GUID CLSID there could be no collision between two identifiers as they are built up to be unique in an OS. For the hardware components a Computer ID could be created by concatenating the identifier of the manufacturer the identifier of the model and the serial number of the component itself. Clearly those skilled in the art will adapt the invention to any alternate operating system such as LINUX.

Such identifiers are particularly used for permitting the different drivers corresponding to the different devices to be installed within a given operating system for instance the Windows type operating system.

The invention takes advantage of the already existing identifiers for improving security and authentication in the transactions and access to information handling systems.

In addition to Component Identification Data the Component data further includes Component Contextual Data CCD which does not identify the component itself but are the data returned by the component when it is used. For instance the CCD is the GPS coordinates on a specific request provided by a GPS device component. CID and CDD data may be combined for creating a complex contextual identification reference which will be used for authorizing or denying the access to the system .

This complex identification is used in a secured authentication process which involves two successive qualification and validation processes which substantially increase the security of access to the transaction or to the service. The first qualification process permits the generation of a Reference Qualification Signature RQS which is a snapshot of the authorized configuration of the system covering both the component identifiers and possibly the contextual data provided by some components which signature is used in a subsequent validation process for the purpose of authorizing or denying access to a transaction or to a service.

It can be seen that the invention can be used for a wide variety of systems and for a wide variety of applications including financial legal or economic applications involving access to sensitive data. In particular it can be used in two different contexts by securing a remote transaction between system and a distant server or even locally by securing the use of system .

The Qualification process is initiated with a step which consists of the installation of a so called Qualifying agent which is installed within system . The setup of Qualifying agent can be achieved from different conventional ways from a media as a CDROM or a floppy disk or via a downloaded transfer through a secure https internet connection for example . When system is operated under a Windows NT or Windows 2000 type operating system it should be noticed that the administrative rights are required for achieving installation of the Qualifying Agent. For the more critical applications it will be useful to reserve the execution of the Qualifying process described below only to specialized staff having administrative rights over the computer or system .

The Qualification process then proceeds with a step where a so called System Qualification File SQF is created which in the preferred embodiment takes the form of a extended Markup Language XML file which is ideally stored in a secured and temporary area of the system for example in the memory or on the hard disk .

The SQF file presents a structured organization which allows storage of the data corresponding to the different components detected within system which includes the Component Identification Data CID and possibly the Component Contextual Data CCD which can be returned by one or more particular components. All of the information will be combined in a same file which will be encrypted for the purpose of generating a reference qualifying signature providing enhanced security to the system.

The System Qualification File SQF is arranged as a template for an extended Markup Language XML file which is structured to provide space available for receiving for every generic type of component the CID and the CCD of the actual component detected and identified within the system. Preferably the SQF file comprises upon its creation so called Component Presence Parameters CPP which are predefined parameters associated with generic types of components such as hard disk motherboard etc. which will be used for securing more particularly both the Qualification and the Validation process and thus advantageously increasing the efficiency of the authentication process. The CPP parameters can be one of the following 

Mandatory the corresponding component must be present within the system to permit full execution of the Qualification or the Validation process

Optional the component can be present or not. Its presence does not influence the execution of the Qualification or the Validation process

Prohibited the component cannot be present. Detection of the presence of the component will stop the execution of the Qualification or the Validation process.

More preferably the SQF file is created by selecting one particular file among a set of predefined templates which correspond to different sets of profiles or different levels of security or qualification or even to different applications which can be secured by the authentication process. That permits organizing different levels of qualifications with different configurations of components which will be detected tracked and checked by means of their corresponding CPP parameters.

Preferably a four level classification is organized by means of four distinctive templates for the SQF file as follows 

For clarity s sake there will now be detailed three examples of SQF files corresponding to three different sets of qualifications.

The first example which is indicated below corresponds to one profile wherein the motherboard the CPU and the RAM cannot be changed once the qualifying process is completed TOFILL replaced with CID in the Fill Up Component Identifier data step .

In this first example the motherboard the CPU and the RAM are defined to be mandatory and the field TOFILL will be replaced by the individual data extracted during detection of the components.

The second example shows a situation where no smartcard is allowed to be connected to the system since the CPP parameter is set to prohibited which prohibits the presence of such a component during the qualification or the validation processes.

In the third example below there is shown a profile which is more accurate on later modifications and offers a new level of security since it stores in a data section the data provided by the GPS component. It can be seen that the geographical x y coordinates provided by a GPS component are retrieved from that component and stored within the System Qualification File. To increase the level of security the GPS component is assigned a mandatory CPP parameter and the SQF file contains a section with attributes which define some predefined geographical ranges already contained in the file.

Clearly the three examples which are discussed above should be only considered for illustration purposes without any limitation in order to demonstrate the great versatility and the wide possibilities offered by the process of the invention.

Referring back to one sees that when the SQF file is created from one predefined template discussed above the process proceeds with a step which is an entering point for a loop based on steps which is used for detecting tracking and registering the different components which can be detected within system in accordance with the structure of the SQF file which was created in step .

For each component being considered within step the process refers to the QSF and extracts thereof if any the corresponding Component Presence Parameter CPP from the QSF. That value is read in a step .

Then in a step the process checks the conformity of the system with the CPP parameter corresponding to the component being considered. This is achieved by detection of the list of components existing in the system and comparing the list with the contents of the XML structure of the SQF file.

Those skilled in the art can use different methods and processes available for determining the particular components which are present within system . In one embodiment the qualifying process extracts system information directly from the SMBIOS tables or interrogates the Distributed Management Interface DMI or Windows Management Instrumentation WMI as known from Microsoft. As known by those skilled in the art the DMI interface is an Application Programming Interface API that consists of a set of routines that are called for accessing the information stored within the BIOS layer. Basic information relating to the DMI programming interface can be found at the address http www.dmff.org spec html.

By using the DMI or WMI interface or by accessing directly the SMBIOS level the Qualifying process accesses the different tables contained in the System Management BIOS SMBIOS for the purpose of reporting comprehensive information regarding the user s preferred software configuration and required for completing a request for transaction. Such information includes the type of processor the type of chipset the number of hard disk drives the particular graphic card being used the serial number of the display the reference of the operating system and so on.

Below there is illustrated the determination from the API known from Windows of the identification of the hard disk of system 

Similarly the process may access the BIOS level to determine the different components such as follows 

Those are only examples showing how easy it is to gather valuable information regarding the different components forming a system and to derive the CID and CCD information which are to be introduced within the SQF file.

Referring back to one sees that if conformity is not satisfied in step then the process proceeds to a step which interrupts the qualification process. Clearly this means that system will be considered as being a NON QUALIFIED system which can be used for normal or routines tasks but certainly not for accessing sensitive or critical information or transactions. This is a great advantage of the process of the invention which permits modifications to be brought to one computer for instance by plugging some external devices and continuing to use the system for normal and routine tasks. Conversely when the system is applied for qualification the system will have to be in a predefined condition including hardware and software configuration to allow completion of the qualification process and the creation of the reference signature which will be discussed below.

If conformity is satisfied then the process proceeds to a step where the information associated with the corresponding component i.e. the Component Identification Data CID and the Component Contextual Data CCD retrieved from the component is precisely introduced at the appropriate location field FILLIN within the XML structure of the SQF file. If one component is a biometric captor then the CID will identify the captor while the CCD may consist for instance of a raw bitmap image of a fingerprint of the user. It consequently integrates user data into the gathered information inside the qualifying protocol file template. Similarly should one component be a GPS receiver the qualifying process reads the receiver hardware identifiers CID and the GPS data provided by the receiver CCD and such information is stored within the XML structure of the SQF file.

The process then proceeds with a step where the next component in the template of the SQF file will be considered and the process goes back to entry point .

When all the components have been processed the process proceeds with a step where the System Qualification File SQF is encrypted by a cryptology algorithm such as RSA PGP and so on based on public and private keys . The particular encryption mechanism which is used is not part of the present invention and will not be further developed. Clearly those skilled in the art will adapt the invention to any known encryption algorithm.

The result of the encryption process permits derivation of a so called Reference Qualifying Signature RQS which permits the whole configuration of the system including hardware and software components CID and even contextual data CDD to be stored within the same signature.

It was described that the CID and CCD data were introduced within the template of the SQF file in order to derive one unique completed SQF file. Alternatively the originating SQF file may remain as a template and the CID and the CDD data may be stored into a separate file which results in the generation of two encrypted files a first file containing the CPP defining the level of qualification and a second file containing the CID and CDD data retrieved from all the components. But preferably the Qualification process generates one unique Reference Qualification Signature RQS based on one unique encrypted SQF file which encompasses CPP CID and CID data.

In a step the process then performs a secure transfer of the RQS signature to the remote system and the latter is then stored in a step . Preferably the RQS reference qualifying signature is sent via common secured remote protocols such as HTTPs VPN and so on . The remote server then stores the qualifying signature relatively to the system in a database or a XML file in order to be able to access to this information during a subsequent Validation process.

The Qualification process then performs in a step the removal of the Qualifyng agent from system and the Qualification process is completed.

Steps to are respectively the same as steps to . After encryption of the SQF file the process then stores the latter in a protected area of the system in a step . Then in a step the process proceeds with the suppression of the qualifying agent from the system.

Therefore the two embodiments which are respectively illustrated in and differ from one another by the fact that in one case the Reference Qualifying Signature RQS is stored within the system while in the other case it is uploaded to the remote server which certainly increases the level of the security.

It can be observed that the Qualification process which was described above substantially increases the level of the security since all the components constituting the system are carefully detected checked and their internal CID and CCD retrieved in accordance with the predefined System Qualification File SQF. In particular any system which does not fully comply with the requirements listed in the SQF file and particularly the Component Presence Parameters CPP therein defined will not be qualified to provide a secured transaction or access to the system.

This significant advantage results from the combination to the qualification process which was described above of a validation process which takes into consideration the reference signature which was previously generated.

In addition authentication of the system is substantially improved by use of the validation process which will now be described and which again will execute a complete checking of a system applying for validation prior to allowing such system to complete any transaction or to access critical data.

The validation process starts with a step where similarly to step of a validation agent is installed within the system requesting a transaction with the server or any kind of remote service.

The process then proceeds with a step where the validation agent creates a System Qualification File SQF corresponding to the level of qualification which is required from the system . Preferably the process generates a template having the same structure as the template used in step of and thus having corresponding Component Presence Parameters CPP .

The process then proceeds with a step which is an entry point of a loop used for separately processing all the components conforming to the list identified within the SQF file.

In a step the validation process extracts the CPP parameter from the template and in a step it performs a detection operation by using similar methods as those discussed above for checking conformity of the actual system to the CPP listed.

If the conformity checking fails then the validation is interrupted in a step and then access to the transaction or to the resource is denied to the user in a step .

Conversely if the conformity checking succeeds in step then the process proceeds with a step where the CID and CCD data are retrieved from the corresponding component and used for filling the SQF files.

Step is used for considering the next component within the list of generic components defined in SQF file and the process returns back to step for processing this new component.

When all the components have been processed the process then proceeds with a step which encrypts the fully completed SQF file in order to generate a Checking Signature CS therefrom.

Then the process proceeds with a step where the checking signature CS is transmitted to the remote server.

Step is an optional step where the validation agent can be removed from the system applying for validation.

Then the process proceeds with a step where a test is performed on the server in order to determine whether the checking signature CS is equal to the Reference Qualifying Signature which was computed during the Qualification process of the system and stored within the remote server.

In one preferred embodiment the remote server generates a temporary session ID or a time stamp on step which will be also checked in step . If the session ID has expired for example it can be for a time out reason between steps and the access will be denied. This additional procedure improves the security.

If the test succeeds then this means that the system applying for validation fully complies with all the requirements contained within the encrypted and thus protected SQF file. In particular this ensures that all the CID and the CCD including the biometric or GPS coordinates when applicable are fully compliant.

Access to the transaction or to the service is thus authorized in a step and the validation process then completes in a step which can be the end of the connection.

Conversely if the test of step fails that means that the system is not fully compliant with the requirements listed within the RQS stored within the server for instance because some internal parts of the system were changed or the user is not the registered user and thus access to the transaction or to the service is denied in a step . The process then proceeds with step which is the end of the validation process.

The validation process involves steps which are identical to steps of the validation process in the remote configuration. Indeed a validation agent is installed step for the purpose of creating a SQF file on the system step and for each component having a type listed within the SQF file the CPP parameters are read step then checked for conformity step . The CID and the contextual CDD data are then retrieved for the purpose of filling the SQF file.

When the Checking Signature CS is generated in a step then the process directly goes to a step where the Reference System Qualifying Signature is read from the local storage and compared to the checking signature in a step .

If the comparison succeeds then the process goes to a step where the access to the transaction or to the service is allowed.

Conversely if the test of step fails then the validation process proceeds with a step where access to the transaction or to the service is denied to the system .

It has been described how it becomes possible to efficiently increase security of access to a system by generating the so called reference system qualifying signature encompassing all the hardware and software components as well as the Contextual Component Data as using such signature in the validation process. This is a very advantageous deviation of the traditional signatures attached to the individual components of the known Windows operating system where the signature is used for detecting corruption of the corresponding component for the purpose of replacing any corrupted component by a new version.

In the invention the Reference system qualifying signature is not provided by the product manufacturer of the component but is automatically generated by the new qualifying process which was described above for the purpose of providing a reference which can be used within the validation process and thus secure the access to the IHS system or to the transaction.

It should be noticed that the invention which was described above can be used in a range of applications.

The invention can be directly applied to the use of a national ID card. Indeed some countries including France are reconsidering the generalization of a new type of ID card which integrates an electronic chip to contain digital biometric data of the bearer. In France in order to enable city halls to collect the biometric data of the citizens who order an ID card the government provides mobile equipment which is transported from city hall to city hall to record the information. Needless to say it is essential that this mobile equipment should not be tampered with in order to make sure that it is only used by authorized administration personnel and that recorded biometric information is not modified or unduly extracted after recording. Only approved systems and users should then be allowed to record and transmit information to the central server which controls the production of ID documents. The integrity of the whole chain should be checked and the process should be fully traceable.

More generally biometric information generalized on passports is underway. To protect the privacy of traveling citizens it is important to make sure that their biometric data are not collected unduly when they identify themselves. Therefore only qualified and fully validated systems should be used for processing such information and the integrity of the systems should be checkable.

Further judicial and police departments in Europe will soon have access to the European criminal record of all citizens. They will also access the Schengen SIS data bases. It is important to 

The invention can also be used for providing efficient warranty service by a product manufacturer. In case of rental of a computer for instance it can be of interest for the company providing the system to be sure that the system is identical when it returns from leasing with respect to the configuration it had when it was shipped to the client. When a computer or any electronic server is sold the invention provides a fast and easy way to check if the computer has been opened and modified by the customer. It definitely replaces the old and unsafe warranty sticker.

During the rental time the innovation provides a technical solution for securing unauthorized changes by remote checks. This is particularly valuable for some applications when it is desired that no unauthorized modification occurred in one computer or one system from a preconfigured predefined and registered setting. New possibilities for leasing or for commercial rental are made possible with the invention.

Another advantage of the use of the invention is the possibility to control the access to the service from the physical location of a machine.

