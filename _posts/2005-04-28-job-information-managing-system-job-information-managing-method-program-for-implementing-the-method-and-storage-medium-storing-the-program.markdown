---

title: Job information managing system, job information managing method, program for implementing the method, and storage medium storing the program
abstract: A job information managing system which can improve convenience in managing and using management codes and improve user-friendliness and convenience in printing management using the management codes. A client computer generates a job for a printer and generates job information on the job. A server computer acquires the job information from the client computer and manages the job information. The client computer creates a label in association with a plurality of management codes for managing job information. The created label is sent to the server computer and stored in association with the plurality of management codes.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07636174&OS=07636174&RS=07636174
owner: Canon Kabushiki Kaisha
number: 07636174
owner_city: 
owner_country: JP
publication_date: 20050428
---
The present invention relates to a job information managing system a job information managing method a program for implementing the method and a storage medium storing the program.

Conventionally there has been developed a job information managing system comprised of an information processing apparatus which generates a job an image processing apparatus which executes the job and a job information managing apparatus which acquires and manages job information on the job executed by the image processing apparatus refer to Japanese Laid Open Patent Publication Kokai No. 2001 282475 for example .

In the job information managing system the job information managing apparatus counts or totalizes the numbers of prints sheet sizes sheet types and so forth with respect to individual users based on acquired job information and displays the usage status with respect to individual users. Also the job information managing apparatus defines properties such as department and division divides users into groups according to the properties tabulates the usage status with respect to the individual properties and displays the tabulation result in tabular or graphic form.

However there may be a case where merely tabulating and displaying the usage status with respect to individual users or properties such as department and division to which the users belong are not almighty. For example in a law firm in general printing expenses are totalized with respect to individual services and hence it is necessary to re totalize printing expenses with respect to the individual services from the result of totalization of printing expenses with respect to individual users who have performed printing. Also a user who has performed printing for a certain service does not always engage in the service and hence even by referring to information on the user who has performed printing it is difficult to determine which service corresponds to the printing. For this reason properties called management codes are defined on a service by service basis so that usage status such as the number of prints sheet size and sheet type can be managed with respect to individual services.

However in the above job information managing system which manages usage status using management codes it is troublesome to manage and use management codes in the case where a large number of management codes are required. For example in the case where hundreds of or thousands of management codes are defined a desired management code must be selected from among the hundreds of or thousands of management codes so as to assign the management code to job information. Therefore satisfactory user friendliness cannot be realized.

It is an object of the present invention to provide a job information managing system and a job information managing method which can improve convenience in managing and using management codes and improve user friendliness and convenience in printing management using the management codes a program for implementing the method and a storage medium storing the program.

To attain the above object in a first aspect of the present invention there is provided a job information managing system comprising at least one image processing apparatus at least one information processing apparatus that generates a job for the image processing apparatus and generates job information on the job and a job information managing apparatus that acquires the job information from the information processing apparatus and manages the job information wherein the information processing apparatus comprises a creating device that creates an identifier in association with a plurality of management codes for managing the job information and a sending device that sends the identifier created by the creating device to the job information managing apparatus and wherein the job information managing apparatus comprises a storage device that stores the sent identifier in association with the plurality of management codes.

With the arrangement of the first aspect of the present invention the information processing apparatus creates a label in association with a plurality of management codes for managing job information and sends the created label in association with the plurality of management codes to the job information managing apparatus and the job information managing apparatus stores the sent label in association with the plurality of management codes. As a result it is possible to improve convenience in managing and using management codes and to improve user friendliness and convenience in printing management using the management codes.

Preferably the information processing apparatus comprises a designating device responsive to input of the identifier or the management codes to designate the plurality of management codes for the job information and the sending device of the information processing apparatus sends the job information and the designated plurality of management codes to the job information managing apparatus the storage device of the job information managing apparatus stores the job information and the designated plurality of management codes in association with each other and the job information managing apparatus comprises a counting device that counts the job information with respect to each of the plurality of management codes.

Preferably the management codes are used for counting system usage charges including charges for job processes including printing processes usage rights for the management codes being settable for specific users so as to permit the users to count the system usage charges using the management codes.

To attain the above object in a second aspect of the present invention there is provided a job information managing method of acquiring and managing job information on a job to be output from an information processing apparatus to an image processing apparatus comprising a storing step of storing an identifier in association with a plurality of management codes for managing the job information.

To attain the above object in a third aspect of the present invention there is provided a job information managing program executable by a computer to acquire and manage job information on a job to be output from an information processing apparatus to an image processing apparatus comprising a storing module for storing an identifier in association with a plurality of management codes for managing the job information.

Preferably the job information managing program comprises a designating module for designating the plurality of management codes for the job information when the identifier or the plurality of management cods are input and a second storing module for storing the job information and the designated plurality of management codes in association with each other and a counting module for counting the job information with respect to each of the plurality of management codes.

To attain the above object in a fourth aspect of the present invention there is provided a storage medium storing a job information managing program according to any of claims to .

To attain the above object in a fifth aspect of the present invention there is provided a job information managing apparatus that acquires job information on a job to be output from an information processing apparatus and manages the job information comprising a storage device that stores an identifier in association with a plurality of management codes for managing the job information.

To attain the above object in a sixth aspect of the present invention there is provided an information processing apparatus that generates a job for an image processing apparatus generates job information on the job and sends the generated job information to a job information managing apparatus that manages the job information comprising a creating device that creates an identifier in association with a plurality of management codes for managing the job information and a sending device that sends the created identifier to the job information managing apparatus.

To attain the above object in a seventh aspect of the present invention there is provided a computer executable program applied to a job information management system comprising a job information managing apparatus that counts job information by specifying counting units using a plurality of management codes and at least one information processing apparatus connected to the job information managing apparatus comprising an acquiring module for acquiring an identifier associated with the plurality of management codes stored in the job information managing apparatus an updating module for updating the management codes with which the identifier acquired by the acquiring module is associated and a transfer module for transferring the identifier updated by the updating module to store the identifier in the job information managing apparatus.

To attain the above object in an eighth aspect of the present invention there is provided a computer executable program applied to a job information management system comprising a job information managing apparatus that counts job information by specifying counting units using a plurality of management codes and at least one information processing apparatus connected to the job information managing apparatus comprising a managing module for managing a plurality of management codes and an identifier used for counting of the job information in association with each other and a display control module for displaying a selection screen for prompting determination as to whether the plurality of management codes managed by the managing module are to be designated or the identifier managed by the managing module is to be designated when counting the job information.

Preferably the display control module displays the selection screen in response to a printing instruction.

The above and other objects features and advantages of the invention will become more apparent from the following detailed description taken in conjunction with the accompanying drawings.

The present invention will now be described in detail with reference to the drawings showing a preferred embodiment thereof.

The job information managing system in is comprised of client computers to which are operated by users a server computer which manages components of the job information managing system and image processing apparatuses implemented by printers to a facsimile machine FAX a copying machine and a multi function printer MFP . These components are connected to each other via a local area network hereinafter simply referred to as the network constructed based on e.g. Ethernet registered trademark such that they can communicate with each other.

It should be noted that there is no difference in hardware configuration between the client computers to and the server computer . The client computers to execute a job account client program described later and the server computer executes a job account server program described later. In the following description the client computers to will be generically referred to as client computer unless otherwise specified.

Also it should be noted that the server computer is managed by an administrator and hence users who use the client computer and others do not have to be aware of the presence of the server computer .

It should be noted that the above mentioned arrangement of the job information managing system is merely an example and the present invention is not limited to this insofar as the job information managing system according to the present embodiment is comprised of at least one client computer at least one server computer and at least one image processing apparatus. Although three client computers to be used by users are shown in a plurality of other computers may be connected to the network and they do not have to be connected to printers.

It should be noted that various kinds of image processing apparatuses can be envisaged as an image processing apparatus constituting the job information managing system in the present embodiment a description will be given of the printers to for example.

The printer has a function of printing according to data received from the client computer but does not have a function of outputting job information on a job executed by the printer to an external apparatus.

The printer has not only the above function of the printer but also a function of notifying job information such as the total number of discharged pages relating to a job to the client computer upon completion of the job.

The printer has a function of storing job information in an internal memory after printing and outputting the job information in accordance with a request from the server computer .

The server computer acquires job logs described later from the client computer via the network selects a specific job log in accordance with a request from a person who would like to review the job log and carries out e.g. counting or totalization by unit time device user and so forth.

Although in the present embodiment it is assumed that TCP IP is used as a protocol for the network any other protocols may be used insofar as they can realize functions described below.

As shown in the client computer has an application a hook module a GDI a printer driver a spooler a transmission reception module and a job account client program .

The application operates on an operating system not shown. The hook module and the job account client program are installed into the client computer . The GDI is a sub system included in the operating system for performing graphic drawing.

The printer driver is a program that is prepared by a printer manufacturer according to printers such as the printers to controlled by the client computer for mediating between the printers to and the application . The spooler is a temporary storage area reserved by the printer driver . The transmission reception module is included in the operating system. The job account client program is executed by a CPU of the client computer .

The application includes an image processing application which captures and processes images a word processor application which creates document data and so forth.

The job log merge module collects various logs relating to various processing from the hook module printer driver spooler and transmission reception module . The job log sending module transmits the logs which have been collected by the job log merge module as a merge log to a job account server program described later.

The job account server program is comprised of a job receiving module a job log merge module a job log recording module a job log counting module a job ID generating module an unprocessed object database DB . The functions of and relationship between these modules will be described later.

In the client computer when a printing instruction is issued to the application the application carries out GDI calls for drawing. The hook module hooks monitors and recognizes the GDI calls and stores information such as what parameters were used for which GDI calls and the number of GDI calls. The hook module counts e.g. APIs Application Programming Interfaces which carry out page feed or sheet discharge to acquire information such as the number of sheets to be discharged or the number of pages in a job issued by the application creates a hook log in based on the information and sends the hook log to the job account client program .

The hook module can change document names according to predetermined criteria. A description of document names and a process for changing them will be given later.

As shown in the hook log includes a job ID an application name the number of logical pages a document name and so forth. The job ID is an identifier which is acquired from the GDI upon a GDI call and uniquely designates a print job.

Referring again to the printer driver converts the GDI call into print data which can be interpreted by a printer according to print settings and sends the print data to the spooler . Also the printer driver creates a driver log in based on information extracted from the print data obtained by the conversion and sends the driver log to the job account client program .

As shown in the driver log includes the job ID the sheet size of print data included in the job N up information information indicative of the number of physical pages information indicative of double sided one sided printing and so forth. The sheet size N up information number of physical pages and double sided one sided printing information are acquired from print settings made in the printer driver during printing. The N up information is indicative of the number of logical pages allotted to one sheet. The number of physical pages means the number of pages in the case where one side of a sheet to be output in printing is counted as 1.

Taking an example where the number of logical pages is 4 and the N up information is indicative of 2 the number of physical pages is 2. When the physical pages are printed on both sides of a sheet one sheet is output and discharged. That is the first and second pages of the logical pages are printed on one side of a sheet and the third and fourth pages of logical pages are printed on the reverse side of the sheet.

Referring again to the job account client program periodically monitors the spooler when there is a job spooled by the spooler information indicative of the number of sheets to be discharged or the number of pages in the job is acquired via an API Application Program Interface of the OS and an API log in is created based on the information and sent to the job account client program .

As shown in the API log is comprised of the job ID the owner s name of the job user name and a spool data size.

Referring again to the transmission reception module communicates with one of the printers to which is designated by the application and sends the print data to the printer if the printer is ready to receive the print data. On this occasion by using e.g. a command according to Printer Job Language registered trademark produced by Hewlett Packard Co. it is possible to acquire the number of pages discharged in the job after the printer completes discharge of all the pages in the job. The transmission reception module creates a monitor log in based on job information such as the number of pages received from the printer and sends the monitor log to the job account client program .

As shown in the monitor log includes the job ID. In the case where print data is sent to the printer the monitor log further includes the number of discharged pages and the number of discharged sheets not shown.

In each of the hook log the driver log the API log and the monitor log there is provided an area where flag information indicative of whether the concerned job has already been processed or not and information indicative of a log type.

The job log merge module merges the hook log the driver log the API log and the monitor log normally the job log merge module sends a merge log in to the job log sending module each time a merging process is completed.

As shown in the merge log is comprised of the items included in the hook log the driver log the API log and the monitor log.

It should be noted that the job log sending module sends a merge log to the job log receiving module periodically or in response to a request from the job log receiving module . On this occasion the job log sending module may control the transmission reception module provided by the OS so that the merge log can be sent to the job log receiving module . It should be noted that the job account client program may allot priorities to the hook log the driver log the API log and the monitor log and send any of these logs to the job account server program according to the priorities.

The job log receiving module acquires the merge log sent from the job log sending module and stores the same. Also in the case where a printer which executes a job has a function of storing job information that is it is the printer the job log receiving module defines a protocol for communication with the printer and communicates with the same so as to acquire job information as an apparatus log directly from the printer . Specifically the job log receiving module periodically polls the printer and if there is any information which has not been acquired yet the job log receiving module acquires the job information as an apparatus log shown in . The apparatus log is stored in a RAM or a HD of the printer . Because of the limited storage capacity of the RAM or the HD it is not desirable that all the pieces of information such as a document name sent from the transmission reception module to a printer are stored as the apparatus log.

The job log merge module merges the merge log in and the apparatus log in sent from the job account client program to generate a final log in . As shown in the final log is comprised of the items included in the merge log and the apparatus log.

The job log recording module receives the final log from the job log merge module and refers to the unprocessed object DB . If the received final log is subjected to processing the job log recording module stores the received final log in e.g. a HD of the server computer . The job log counting module is responsive to an instruction from a person who reviews to carry out counting of the number of print pages per unit time the number of print pages for each owner and so forth.

The ID generating module issues a client ID for uniquely identifying the client computer . The client ID is set as a four digit character string aaaa aaab . . . zzzy and zzzz each digit of which may assume 26 values i.e. to in accordance with a request from the hook module . Here a new document name is created using a combination of a client ID and a job ID but the job account server program may issue a new unified document name unique to the entire system.

Although in the present embodiment it is assumed that in the client computer four logs i.e. the hook log the driver log the API log and the monitor log are created for one print job these four logs should not necessarily be created. For example if the application directly sends print data to the spooler the hook log and the driver log are not created. If no protocol is prescribed for communication between the printer driver and the job account client program the job account client program cannot acquire the driver log. If a printer which executes a job does not have the function of notifying the number of discharged pages to the transmission reception module as is the case with the printer the transmission reception module cannot acquire information on the number of discharged pages in the monitor log.

In the present embodiment logs are acquired in a plurality of processes relating to a print job and therefore even if it is impossible to acquire logs in part of the processes logs can be finally acquired with a high probability.

In the job information managing system constructed as described above whether logs as job information acquired from the client computer the printer and so forth should be recorded or not is determined according to the process of generation of the logs and only logs which should be recorded are recorded in the server computer .

A description will now be given of the hardware configuration of the computers in the job information managing system according to the embodiment of the present invention.

The client computer in is comprised of a CPU Central Processing Unit a ROM Read Only Memory a RAM Random Access Memory a CD ROM drive for reading a CD ROM a KBC Keyboard Controller a display controller a HD Hard Disk and a communication unit which are connected to each other via a system bus .

The CPU controls the overall operation of the client computer and carries out computations and others. The ROM is a storage area which stores e.g. information on a system starting program. The RAM is a data storage area on which no usage restrictions are imposed. The KBC sends data input from a keyboard not shown to the CPU . The display controller controls display on a CRT a liquid crystal display or the like. The HD stores programs and data and refers to or loads the programs and the data into the RAM as the need arises during execution of programs. The communication unit is used for communication with other computers and image processing apparatuses connected to the network .

The communication unit is controlled by the transmission reception module the job log sending module and so forth in .

Software modules such as the application hook module GDI printer driver transmission reception module and job account client program in the operating system communication control programs and so forth are loaded from the HD and the ROM into the RAM and executed by the CPU .

It should be noted that in place of or in addition to the HD another storage device such as a nonvolatile memory may be provided.

The server computer is basically identical in construction with the client computer and therefore component elements of the server computer are designated by reference numerals to not shown with hundreds digits thereof being 2 and last two digits corresponding to those of the reference numerals to designating the component elements of the client computer in . Specifically the server computer is comprised of a CPU a ROM a RAM a CD ROM drive for reading a CD ROM a KBC a display controller a HD and a communication unit which are connected to each other via a system bus .

The computers of the printers to are identical in hardware configuration and therefore a description will now be given of the printer for example.

The controller controls the entire printer . The print engine carries out a printing operation and an image reading operation under the control of the controller . The communication unit communicates with the client computers to and the server computer . The operation unit carries out a setting operation interactively with a user.

The controller is comprised of a CPU Central Processing Unit a ROM Read Only Memory a RAM Random Access Memory a HD Hard Disk which are connected to each other via a system bus .

The CPU controls the overall operation of the printer and carries out e.g. computations. The ROM includes a data storage area upon which no usage restrictions are imposed. The HD includes a storage area which reserves programs and data which may be rewritable even after power supply to the printer is turned off.

The RAM includes a storage area in which an operating system and programs for communication control engine control and so forth are loaded and executed.

As shown in in the server computer a main I O program an operating system and applications are loaded into the RAM so that they can be executed. In the RAM of the server computer associated data generated by execution of the applications is additionally stored and a working area for operation of other programs is also prepared.

The software configuration of the server computer as shown in can be realized by externally installing the job account server program . The job account server program can be downloaded via a network such as the Internet or installed from a portable and removable storage medium.

For example as shown in the job account server program is installed by causing the CD ROM drive of the server computer to read information on the CD ROM . In this case as shown in volume information directory information an execution file and an associated data file are recorded in a storage area of the CD ROM . The execution file includes an install program for the job account server program .

When the CD ROM is set in the CD ROM drive the execution file is executed under the control of the operating system and the main I O program and e.g. program modules and associated data for realizing the job account server program are read out from the CD ROM and stored in the HD . The program modules for realizing the job account server program include the modules to in .

It goes without saying that the storage medium should not be limited to a CD ROM but may be a DVD a FD or the like.

As shown in according to a predetermined apparatus management protocol the hook module determines whether or not the printer has an apparatus log by referring to information acquired from the printer which is to perform printing step S . If the printer does not have an apparatus log the process is immediately terminated. On the other hand if the printer has an apparatus log the hook module determines whether or not a client ID as identification information which is issued by the ID generating module so as to enable the client computer to be uniquely identified has been acquired from the ID generating module step S .

If it is determined in the step S that the hook module has not yet acquired the client ID the hook module communicates with the ID generating module to acquire the client ID from the ID generating module step S and the process proceeds to a step S. On the other hand if the hook module has already acquired the client ID the process proceeds to the step S without executing the step S.

In the step S an in client computer job ID which uniquely identifies a job within a client computer is created. It is assumed here that numerals 0001 to 9999 are sequentially issued.

Then the hook module combines the client ID acquired from the ID generating module with the created in client computer job ID to create a new document name as new identification information which is uniquely defined within the job information managing system step S . The hook module stores the original document name which has been sent from the application in an item original document name in the hook log step S and replaces the document name by the new document name step S and terminates the process.

As a result the new document name is sent to the GDI and subsequent processing is performed by the printer driver spooler transmission reception module and printer using the new document name.

The reason why the new document name is created is that in merging job information acquired from a printer it is difficult to use a job ID as it is as a key for merging. For example since part of the specifications of a job information managing process is not publicly known in many cases a server computer A developed by a company A cannot acquires a job ID from a printer B developed by a company B. Specifically in many cases no job ID is not included in job information acquired from a printer which is not adapted to an unexpected job information managing process and hence the job information cannot be merged for use. However in many cases a document name which is created by an OS or applications of a client computer and sent to a printer can be acquired as job information.

Therefore it can be envisaged that a document name which can be managed by a client computer and acquired as a job information key from a printer in place of a job ID is used as identification information. However using the conventional document name as it is raises a problem. In general a document name which can be managed by an OS or an application of a client computer is comprised of nine or more characters and according to an OS which is ordinarily used a document name comprised of up to 255 characters may be given but a printer can manage a document name comprised of eight or less characters and a document name which can be used in a job information managing process is usually comprised of eight or less characters. For this reason there may be a case where different document names comprised of eight or more characters given by an OS or an application of a client computer are regarded as the same document name comprised of eight characters in a printer which is very confusing.

To solve this problem a client ID issued by a server computer and a job ID issued by a client computer are combined to be used as a document name. As a result a new document name comprised of eight characters uniquely defined in a system which is managed by a server computer and is comprised of client computers and printers is created to be used for identification of a job in place of a job ID. Once a new document name has been created in a client computer this new document name can be used as a job identifier in printers client computers and server computer.

A description will now be given of the operation of the job log merge module of the client computer .

The log merge module receives logs such as a hook log driver log API log and monitor log records contents thereof in e.g. the HD and executes the present process at predetermined regular time intervals to carry out merging for each job to create a merge log.

As shown in the job log merge module determines whether or not there is any monitor log with a processed flag thereof not being YES i.e. any monitor log which has not yet been processed step S . If there is no unprocessed monitor log the process is immediately terminated and on the other hand if there is any unprocessed monitor log the process proceeds to a step S.

In the step S the unprocessed monitor log is copied to another temporary storage area and assumed as a log A and a job ID is acquired from the log A step S .

Then search is carried out for a hook log a driver log and an API log corresponding to the acquired job ID to determine whether or not there is any log which has not been subjected to merging i.e. whether or not there is any unprocessed log step S . If there is no unprocessed log the process is terminated and if there is any unprocessed log the process proceeds to a step S.

In the step S a log which has the same job ID as a job ID referred to as N for the convenience of explanation of the unprocessed log is searched for through the hook log the driver log and the API log to determine whether there is any log having the same job ID as N. If there are a plurality of unprocessed logs job IDs in the unprocessed logs A are sequentially identified as N in order from the smallest one.

If it is determined in the step S that there is no log which has the same job ID as N an item type in the unprocessed log A is set as merge to make a mark indicating that merging has been completed step S and then the step S and the subsequent steps are executed again.

If it is determined in the step S that there is a log which has the same job ID as N this log is assumed as a log B and it is determined whether or not there is any item that is included in the log B but is not included in the log A step S . If there is no item that is included in the log B but is not included in the log A an item type in the log A is set as merge to make a mark indicating that merging has been completed step S and the step S and the subsequent steps are executed again.

If it is determined in the step S that there is any item which is included in the log B but is not included in the log A this item is added to the log A to create a merge log step S and a processed flag of the merge log is set to YES to make a mark indicating that merging has been completed step S . Then the step S and the subsequent steps are executed again.

In the present process the job log merge module identifies the earliest start time and the latest finish time among start times and finish times indicated by entries of start time information and finish time information included in each of the hook log driver log API log and monitor log and merges and stores them as a merge log.

In the present process logs are merged using a job ID as a key but a document data name or a new document data name may be used as the key.

As shown in the job log merge module determines whether or not there is any unprocessed merge log step S . If there is any unprocessed merge log it is determined whether or not the printer has an apparatus log step S . If the printer has an apparatus log it is determined whether there is an apparatus log including the same document name as in the unprocessed merge log step S .

If it is determined in the step S that there is an apparatus log including the same document name as in the unprocessed merge log the number of discharged pages and the number of discharged sheets in the apparatus log are caused to overwrite the merge log or are added to the merge log step S and the original document name is replaced by the document name step S for example document name 2001 annual report original document name abcd0001 as shown in .

Then the original document name in the merge log is erased to be a final log step S and the final log is sent to the job log recording module step S followed by termination of the process.

If it is determined in the step S that there is no unprocessed merge log or if it is determined in the step S that there is no apparatus log including the same document name as in the unprocessed merge log the process is immediately terminated.

If it is determined in the step S that the printer has no apparatus log the step S is executed to terminate the process.

As shown in the server computer checks the type of an event that has occurred step S and carries out a client communicating process step S a management code registering process step S a management code usage right setting process step S a label registering process step S a label usage right setting process step S or a process for registering the above mentioned job information step S according to the type of the event and terminates the process.

In the client communicating process the server computer communicates with the client computer . In the management code registering process the server computer registers management codes shown in described later . In the management code usage right setting process the server computer defines usage rights for the management codes with respect to individual users . In the label registering process the server computer registers labels in described later . In the label usage right setting process the server computer defines usage rights for the labels .

In the management codes are defined in three classes groups . For example in the first class management codes A A A A . . . and usage rights for the respective management codes i.e. information indicative of users who can use the management codes are stored. A plurality of users can be set for one management code and all the set users have a usage right for the management code. Similarly management codes B B B . . . and usage rights therefor are stored in the second class and management codes C C C . . . and usage rights therefor are stored in the third class.

The management codes defined in the three classes are used in combination one management code per class. For example a combination of the management codes A B and C is used for a certain job. Specifically to classify service and client information in e.g. a law firm classes of management codes are grouped into client first class matter second class and sub matter third class and management codes are defined in each class as below.

Sub matter Divorce Traffic Accident Injury Theft Succession of Property Finance Patent Infringement Copyright . . .

Expenses for printing operations can be charged in units classified according to service contents e.g. Mr. Suzuki Civil Affairs Succession of Property and Midori Trading Co. Ltd. Legal Work Patent Infringement .

In the labels as identifiers are defined for management code groups each comprised of a plurality of management codes and used to facilitate designation of management codes for managing usage status.

For example in a label L is defined for a management code group comprised of the management codes A B and C and usage rights are set for users and . Similarly a label L is defined for a management code group comprised of the management codes A B and C and a label L is defined for a management code group comprised of the management codes A B and C.

As shown in when a management code list screen is called YES to a step S the server computer displays a management code list screen of step S . When the user designates a class of management codes to be registered in a combobox of the management code list screen step S the server computer displays a management code list comprised of names of management code registered in the designated class step S . In First Class Client is selected in the combobox and management code names such as Midori Trading Co. Ltd. are displayed in the management code list .

Then when Register management code is selected from a menu not shown on the management code list screen YES to a step S the server computer displays a management code input dialogue of step S . When the user inputs a management code into an edit box of the management code input dialogue step S and presses an OK button step S the server computer registers the input management code step S and terminates the process.

As shown in when the management code list screen is called YES to a step S the server computer displays the management code list screen of step S . When the user designates a class of management codes to be registered in the combobox of the management code list screen step S the server computer displays the management code list comprised of registered management code names in the designated class.

Then the user selects a management code for which usage rights are to be set from the management code list and selects registered users from a menu not shown step S the server computer displays a management code usage right setting screen of step S . A user list comprised of names of users for which the selected management code has been set is displayed on the management code usage right setting screen. On the management code usage right setting screen users who can use a selected one management code are set for the code so that usage rights are defined for the code. For example in User and User are set for a management code Midori Trading Co. Ltd. .

Then when an item set user in a menu not shown on the management code usage right setting screen is pressed YES to a step S the server computer displays a user list appearing in step S . When the user selects one or more users to be set from the user list step S and presses an OK button YES to a step S the server computer sets usage rights for the selected user s step S and terminates the process.

As shown in when a label registering screen is called YES to a step S the server computer displays the label registration screen of step S . The user selects management codes of respective three classes Client Matter and Sub matter in comboboxes to on the label registering screen step S inputs a label for the selected management codes of the three classes into an edit box step S and presses an OK button YES to a step S the server computer registers the one selected label input for the selected management codes of the three classes step S and terminates the process.

As shown in when a label list screen is called YES to a step S the server computer displays the label list screen of step S . When the user selects a label for which usage rights are to be set from the label list screen and pressed an OK button step S the server computer displays a label usage right setting screen of step S .

A user list comprised of names of users set for the selected label is displayed on the label usage right setting screen. On the label usage right setting screen users who can use a selected one label are set for the label so that usage rights are defined for the label. For example in usage rights of User and User are set for a label Case M H P .

Then when the user selects an item set users from a menu not shown on the label setting screen YES to a step S the server computer displays a user list appearing in step S . When the user selects users for which usage rights are to be set from the user list step S and presses an OK button YES to a step the server computer sets usage rights for the selected users step S and terminates the process.

As shown in the client communicating process is comprised of a starting process carried out to start the client computer an in operation process carried out during operation and a terminating process carried out to terminate the process.

In the starting process the client computer inquires of the server computer whether or not the server computer has been started step S . The server computer receives the inquiry from the client computer step S and notifies the client computer that the server computer is normally operating step S .

Then the client computer receives the notification that the server computer is normally operating step and requests the server computer to send management codes and labels registered in the server computer step S . The server computer receives the management code and label sending request from the client computer step S refers to user information on the client computer and sends management codes and labels which can be used by the user to the client computer step S . The client computer receives the management codes and the labels from the server computer step S and terminates the process.

In the in operation process to register a management code newly input by the user in the case where the management code is designated during printing the client computer sends the newly input management code to the server computer step S . The server computer receives the management code newly input in the client computer step S and terminates the process. The newly input management code exists on a memory of the client computer . Also the client computer can newly define a label.

In the terminating process the client computer sends a label newly registered by the client computer and management codes corresponding to the label to the server computer step S . The server computer receives the sent label and management codes corresponding to the label and stores them in a predetermined database step S .

Then at the time of termination of the process the client computer sends a terminating notification to the server computer step S . The server computer receives the terminating notification from the client computer step S and terminates the process.

As shown in after being started the client computer connects to the server computer step S and determines whether connection with the server computer has been successful or not step S . If the connection with the server computer has not been successful the client computer performs suitable error processing step S and terminates the process.

On the other hand if the connection with the server compute has been successful the client computer acquires management codes labels and various setting information from the server computer step S . The management codes and the labels which are acquired on this occasion are those for which usage rights are given to a user who has logged in the client computer . The acquired management codes and the labels are used in inputting management codes during printing.

Then the client computer determines whether an event has occurred or not step S . If an event has occurred the type of the event is judged step S . If the event which has occurred is the label registering process the label registering process is carried out step S and server registered labels and user registered labels are merged step S . The process then returns to the step S. In the same manner as the label registering process carried out by the server computer the client computer can also register labels. In this case usage rights for the registered labels are given to a user who is currently operating the client computer i.e. a user who has logged in the client computer .

If it is determined in the step S that the event which has occurred is a printing process a printing process in described later is carried out step S and the process then returns to the step S.

If it is determined in the step S that no event has occurred the labels registered in the client computer by the user and management codes corresponding to the labels are sent to the server computer step S . The process is then terminated.

According to the process of if the event which has occurred is a label registering process the label registering process is carried out step S and labels registered in the server computer and labels registered by the user are merged step S . If no event has occurred NO to the step S the labels registered in the client computer by the user and management codes corresponding to the labels are sent to the server computer step S . This makes it more convenient to manage and use management codes and improves user friendliness and convenience in printing management using the management codes.

As shown in it is determined whether or not management codes are to be input in the client computer when carrying out printing step S . If management codes are to be input selection screens of are displayed in printing so as to prompt the user to determine whether management codes are to be designated by selecting a label or management codes are to be directly designated.

The screen of is for directly designating management codes and the screen of is for selecting a label to set management codes corresponding thereto. The screens of can be switched to each other using tab sheets. When a cursor is set to a tab sheet in using an input means such as a mouse and then a predetermined mouse button is pressed the screen of is switched to the screen of . On the other hand when the cursor is set to a tab sheet and the predetermined mouse button is pressed the screen of is switched to the screen of .

It should be noted that information indicative of whether management codes are to be input or not which is obtained in the step S is set in the server computer the information may be included in setting information loaded from the server computer by the client computer upon start.

If it is determined in the step S that management codes are to be input in printing a management code input dialogue in is displayed step S and it is determined whether or not management codes are to be input by inputting a registered label step S .

If management codes are not to be input by inputting a label the user inputs management codes of respective three classes into comboboxes to of the management code input dialogue in and presses an OK button step S . The client computer then determines whether the input management codes are new or not step S .

If the input management codes are new i.e. if the input management codes are not registered they are sent to the server computer step S . In the comboboxes to registered management codes can be selected and new management codes can be edited.

Then the input management codes and a job ID of a print job are sent to the server computer step S and a job log is sent to the server computer step S . The process is then terminated.

If it is determined in the step S that management codes are to be input by inputting a label a label is input into a combobox of a label input dialogue in to input management codes step S and the steps S and S are executed to terminate the process. In a label Case M H P is given to a set of three management codes Midori Trading Co. Ltd. Legal Work and Patent Infringement and selecting this label obtains the same effect as selection of the three management codes Midori Trading Co. Ltd. Legal Work and Patent Infringement .

According to the process of the client computer inputs a label into the combobox of the label input dialogue to input management codes step S and sends the input management codes and a job ID of a print job to the server computer step S . This improves convenience in managing and using management codes and improves user friendliness and convenience in printing management using the management codes.

It should be noted that although in the present embodiment there are management codes of three classes the present invention is not limited to this.

Further although in the present embodiment a label registered in the client computer is sent to the server computer each time a label is registered by the client computer the present invention is not limited to this but a registered label may be sent to the server computer just before the client computer is turned off.

Further although in the present embodiment usage rights for management codes and labels are set in the server computer by the management usage right setting process of it may be arranged such that usage rights for labels are not set by users but usage rights are set using a logical sum of usage rights for respective management codes.

For example a usage right for a label L is set for a logical sum User User User and User of usage rights for respective management codes in the case where the label L is defined for the following three management codes 

The above described program for specifying counting units using a plurality of management codes and counting job information used in the present invention includes a program for realizing the label registering process carried out by the client computer in . Also the program controls a process in which a plurality of management codes and a label for use in job counting are managed in association with each other and a selection screen for prompting a user to determine whether the plurality of management codes managed by the program are to be designated or the label managed by the program is to be designated is displayed when counting the job information. Further the program controls a process in which the selection screen of or is selectively displayed in response to a printing instruction from a user.

Further it is to be understood that the object of the present invention may also be accomplished by supplying a system or an apparatus with a storage medium in which a program code of software which realizes the functions of the above described embodiment is stored and causing a computer or CPU or MPU of the system or apparatus to read out and execute the program code stored in the storage medium.

In this case the program code itself read from the storage medium realizes the functions of the above described embodiment and hence the program code and a storage medium on which the program code is stored constitute the present invention.

Examples of the storage medium for supplying the program code include a floppy registered trademark disk a hard disk a magnetic optical disk a CD ROM a CD R a CD RW a DVD ROM a DVD RAM a DVD RW a DVD RW a magnetic tape a nonvolatile memory card and a ROM. Alternatively the program code may be downloaded via a network.

Further it is to be understood that the functions of the above described embodiment may be accomplished not only by executing a program code read out by a computer but also by causing an OS operating system or the like which operates on the computer to perform a part or all of the actual operations based on instructions of the program code.

Further it is to be understood that the functions of the above described embodiment may be accomplished by writing a program code read out from the storage medium into a memory provided in an expansion board inserted into a computer or a memory provided in an expansion unit connected to the computer and then causing a CPU or the like provided in the expansion board or the expansion unit to perform a part or all of the actual operations based on instructions of the program code.

This application claims priority from Japanese Patent Application No. 2004 134549 filed Apr. 28 2004 which is hereby incorporated by reference herein.

