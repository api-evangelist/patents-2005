---

title: Fault management system in multistage copy configuration
abstract: In a storage system in which a pair is configured by a remote copy, when a fault occurs in the pair, data to be lost is determined. Provided is a management computer connected to a storage system, in which the storage system includes: a primary logical volume in which data is stored and an secondary logical volume in which a replication of the data stored in the primary logical volume is stored; the primary logical volume and the secondary logical volume form a pair; the management computer comprises a data management module for managing data stored in the primary and secondary logical volumes; and the data management module obtains an event regarding the pair, determines whether the event is caused by a fault occurring in the pair, determines data made to be inconsistent by the fault in the case where the event is caused by the fault, and outputs information on the inconsistent data.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07644301&OS=07644301&RS=07644301
owner: Hitachi, Ltd.
number: 07644301
owner_city: Tokyo
owner_country: JP
publication_date: 20050315
---
The present application claims priority from Japanese application JP2004 377176 filed on Dec. 27 2004 the content of which is hereby incorporated by reference into this application.

When a fault occurs in a network composed of a plurality of apparatuses it is necessary to determine a site where the fault occurs to restore the network. However when the network increases in scale and its configuration becomes complicated it is difficult to determine the site of the fault.

JP 10 22947 A discloses a network management system for determining a site where a fault occurs by allowing a management apparatus and a management apparatus agent to monitor the status of a path on the network.

In the field of a recent data storage in order to protect data stored in a storage system data is replicated using a copy technique of a storage. According to the copy technique a logical volume in a storage system is paired with at least one logical volume in the same or another storage system. Furthermore those pairs can also be connected in a multistage. A pair configuration thus connected in a multistage is called a cascade configuration. By controlling the execution of data replication in each pair replication data at an arbitrary point can be created and saved.

In such a pair configuration because of the change in status of any pair data of another pair may be lost. For example when data is being replicated in one pair and a fault occurs in that pair the data replication is interrupted. Consequently the logical data consistency of a logical volume of a replication destination is lost.

However in each logical volume backup data at a different point from that of data stored in a logical volume of a copy source may be stored. Therefore in order to determine whether data is to be inconsistent when the status of a pair changes it is necessary to refer to the version of the data.

Furthermore there are a plurality of kinds in the normal status of a pair. Whether data is to be inconsistent when a fault occurs depends upon the status of a pair before the fault occurs.

Thus data to be inconsistent when a fault occurs cannot be determined by a conventional method of determining a fault site.

According to one embodiment of this invention there is provided a management computer connected to a storage system included in a computer system characterized in that the storage system includes a primary logical volume in which data is stored and an secondary logical volume in which a replication of the data stored in the primary logical volume is stored the primary logical volume and the secondary logical volume form a pair the management computer comprises a data management module for managing data stored in the primary and secondary logical volumes and the data management module obtains an event regarding the pair determines whether the event is caused by a fault occurring in the pair determines data made to be inconsistent by the fault in the case where the event is caused by the fault and outputs information on the inconsistent data.

According to this invention data to be inconsistent when a fault occurs in a pair is determined. Furthermore according to this invention whether inconsistent data can be restored is displayed. Furthermore this invention supports the restoration of inconsistent data.

The computer system of this embodiment is composed of a management server at least one application server and at least one storage system .

The management server and the application server are connected via a network so as to communicate with each other. The network is for example an IP network such as a LAN or a so called Internet.

The application server and the storage system are connected to each other via a storage area network SAN so as to communicate with each other. The SAN is a network dedicated to a storage and performs communications with an FC protocol an FCIP protocol or the like.

The storage system may further be connected to the management server and the like via the network so as to communicate therewith.

The management server is a computer for managing a computer system of this embodiment. The management server is composed of an input output unit a disk device a CPU a main memory a network interface I F and a bus connecting them.

The disk device is for example one hard disk drive and stores a program executed by the CPU and data required for executing the program as shown in .

The CPU is a processor for controlling the management server and executes a program stored in the disk device .

A network I F is an interface for the management server to communicate with the application server and the like via the network .

The application server is a computer for providing a file system by using the storage system and supporting transactions of a user by executing an application such as a DBMS. The application server is composed of an input output unit a network I F a CPU a main memory a disk device a data I F and a bus connecting them.

The network I F is an interface for the application server to communicate with the management server and the like via the network .

The CPU is a processor for controlling the application server and executes a program stored in the disk device .

The disk device is for example one hard disk drive and stores a program executed by the CPU and data required for executing the program as shown in .

The data I F is an interface for the application server to communicate with the storage system and the like via the SAN .

Although the configuration of the application server C is not shown it is similar to those of the application servers A and B. The computer system of this embodiment may include more application servers .

The storage system is composed of a management port a port a disk device and a disk controller for controlling them.

The management port is an interface for the storage system to communicate with the management server and the like via the network . The storage system may not be connected to the network . In the case where the storage system is not connected to the network the management port may not be provided.

The port is an interface for the storage system to communicate with the application server and the like via the SAN .

A logical volume may be composed of a plurality of hard disk drives for example RAID . In this embodiment each logical volume is assumed to be a RAID composed of a plurality of hard disk drives.

The logical volume refers to a storage region logically dealt with as one disk drive. Data used by the application server in the storage system is stored in the logical volume .

Although the configuration of the storage system C is not shown it is similar to those of the storage systems A and B. The computer system of this embodiment may include more storage systems .

Data stored in the logical volume of the storage system can be replicated copied to the logical volume of another storage system via the SAN without using the application server . Such data replication is called a remote copy. Furthermore data stored in the logical volume of the storage system can also be replicated to another logical volume of the same storage system . Such data replication is called a local copy.

As described above in the case where data is replicated between the logical volumes a combination of the logical volume of a replication source and the logical volume of a replication destination is called a pair. The logical volume of a replication source is called a primary logical volume PVOL and the logical volume of a replication destination is called a secondary logical volume SVOL .

The disk device stores at least a data management program a pair status application status management table a volume data correspondence management table and a fault detail code table . The configurations of the program and tables will be described later in detail.

At least one of the application servers connected to the storage system stores a pair management program and a pair configuration definition table .

The pair management program executes a pair operation for switching the status of a pair of the logical volumes in response to an instruction from the management server or the like.

The PAIR is a status in which the same data is stored i.e. data is duplexed in the PVOL and the SVOL as a result of data replication. When data in the PVOL of the pair in the PAIR status is updated the updated data is replicated to the SVOL by data replication local copy or remote copy . Consequently the data consistency between the PVOL and the SVOL is maintained. In the case where synchronous copy is performed the identity of the data in the PVOL and the SVOL is maintained in the PAIR status mirroring .

The SUSPEND is a status in which data replication is stopped as a result of a pair operation SPRIT described later. Even if the data in the PVOL of the pair in the SUSPEND status is updated the updated data is not replicated to the SVOL. Therefore in the PVOL and the SVOL of the pair in the SUSPEND status different data may be stored.

The COPY and the REVERSE COPY are statuses in which data replication for switching the SUSPEND status to the PAIR status is being performed i.e. status in which data replication has been started and has not been completed . The COPY is a status in which data replication from the PVOL to the SVOL is performed. The REVERSE COPY is a status in which data replication from the SVOL to the PVOL is performed.

The ERROR is a status in which data replication is stopped as a result of the occurrence of a fault. Herein the fault refers to for example a network fault occurring in the SAN or a fault occurring in the storage system . In the pair in the ERROR status similar to in the SUSPEND status data replication is not performed. Therefore the ERROR status is also called a SUSPEND ERROR . Thus in the PVOL and the SVOL of the pair in the ERROR status different data may be stored.

The pair management program performs three pair operations SPLIT RESYNC and REVERSE RESYNC . The REVERSE RESYNC is also called RESTORE .

When the RESYNC is performed in the pair in the SUSPEND status the pair is placed in the COPY status and the data in the PVOL is replicated to the SVOL. When the replication is completed the pair is placed in the PAIR status.

As described later in the case where the degree of a fault occurring in a pair is small the RESYNC can be performed in the pair in the ERROR status SUSPEND ERROR status . The result of the execution is the same as that obtained when the RESYNC is performed in the pair in the SUSPEND status. More specifically the pair in the ERROR status in which the RESYNC is performed is placed in the COPY status and the data in the PVOL is replicated to the SVOL. When the replication is completed the pair is placed in the PAIR status.

When the RESTORE is performed in the pair in the SUSPEND status the pair is placed in the REVERSE COPY status and the data in the SVOL is replicated to the PVOL. When the replication is completed the pair is placed in the PAIR status.

The pair management program may detect that the status of a pair has been changed and notify the management server of the change. Specifically when another software performs a pair operation and a fault occurs in a pair as well as when the pair management program performs a pair operation the pair management program notifies the management server that the status of the pair has been changed and of the changed status of the pair.

The storage system may directly notify the management server of the change in the status of the pair via the management port .

The pair management program may further detect that the status of an application has been changed and notify the management server of the change. Specifically the pair management program detects that an application has been staticized in other words an application has been made to be quiescent or a staticized application has been destaticized with respect to any of the logical volumes and notifies the management server that the status of the application has been changed and the changed status of the application.

The pair configuration definition table includes information regarding a pair to which each logical volume in the storage system to which the application server is connected belongs. The pair configuration definition table will be described later in detail referring to .

The pair management program and the pair configuration definition table may be stored in the disk device of the management server . In this case the pair management program performs a pair operation of the logical volume in the storage system via the management port connected to the network .

In the example shown in DKC disk controller DKC and DKC are storage systems . For example the DKC DKC and DKC may be storage systems A B and C respectively. In the SAN the application server and the like are not shown.

The DKC includes three logical volumes VOL VOL and VOL. The DKC includes three logical volumes VOL VOL and VOL. The DKC includes six logical volumes VOL VOL VOL VOL VOL and VOL.

The data in the VOL is replicated to the VOL between the DKC and the DKC. In other words the VOL and the VOL forms a pair. Herein the VOL is PVOL and the VOL is SVOL. The pair formed by the VOL and the VOL is referred to as a pair P.

The pairs P P and P form a copy group CG. The copy group refers to a collection of pairs and can be set to be a unit for a pair operation. Although a pair operation can be performed with respect to each pair a plurality of pair operations can also be performed collectively by determining a copy group. In the case where a copy group ensures data consistency in one copy group when PVOLs are updated SVOLs are updated in the order of the update of the PVOLs. For example in the case where data A not shown in the VOL is updated and then data B not shown in the VOL is updated the data A is replicated from the VOL to the VOL and then the data B is replicated from the VOL to the VOL. Thus the update order of data is maintained whereby the mutual consistency of data in a copy group is maintained.

For example a plurality of pairs regarding one instance of one application may be set to be one copy group and a plurality of pairs regarding one database may be set to be one copy group.

Similarly the VOL VOL and VOL respectively form pairs P P and P by the remote copy together with the VOL VOL and VOL. In these pairs the VOL VOL and VOL are PVOLs and the VOL VOL and VOL are SVOLs. These three pairs form a copy group CG.

Further the VOL VOL and VOL respectively form pairs P P and P by the local copy together with the VOL VOL and VOL. In these pairs the VOL VOL and VOL are PVOLs and the VOL VOL and VOL are SVOLs. These three pairs form a copy group CG.

In a copy path extending from the DKC to the DKC a PVOL side is defined as an upper stage and an SVOL side is defined as a lower stage. For example based on the pair P the pair P is in an upper stage and the pair P is in a lower stage. The pair P is adjacent to the upper stage of the pair P and the pair P is adjacent to the lower stage of the pair P. On the other hand the pair P is in the upper stage of the pair P and is not adjacent to the pair P.

Referring to the summary of this invention will be described next. Herein although only the VOL VOL VOL and VOL will be described the descriptions are also applied to another logical volume .

In the case where the pair status of all the pairs shown in are in the PAIR for example when the application server updates the data in the VOL of the DKC the update is reflected to the VOL and the VOL by the remote copy and further is reflected to the VOL by the local copy. Consequently the same data is stored in the VOL VOL VOL and VOL.

Next when the SPLIT is performed with respect to the pair P the pair status of the pair P is placed in the SUSPEND whereby the remote copy of the pair P is suspended.

Thereafter when the data in the VOL is updated the update is reflected to the VOL by the remote copy. However since the remote copy of the pair P is suspended the update is not reflected to the VOL and the VOL. Consequently the data stored in the VOL and the VOL is not the same as that stored in the VOL and the VOL.

At this time when a fault occurs in the pair P as long as the application is not suspended the logical consistency of the data stored in the VOL cannot be ensured although consistency may be kept in some cases it cannot be ensured . Since the data whose consistency is not ensured cannot be used the data in the VOL is lost.

On the other hand in the case where the pair P is normal when the RESYNC is performed with respect to the pair P the pair status is placed in the COPY and the data in the VOL is replicated to the VOL. When the replication is completed the pair status is placed in the PAIR . At this time among the data stored in the VOL before the commencement of the replication the data different from that in the VOL is lost when the data in the VOL is overwritten.

Furthermore since the pair status of the pair P is in the PAIR the update of the VOL is reflected to the VOL. Consequently among the data stored in the VOL the data different from that in the VOL is lost when the data in the VOL is overwritten.

Furthermore in the case where a fault occurs in the pair P when the pair status is in the COPY and replication of data is suspended the consistency of the data stored in the VOL is not ensured. Therefore the data in the VOL is lost more specifically the data in the VOL is to be inconsistent .

Furthermore since the pair status of the pair P is in the PAIR the update of the VOL is reflected to the VOL. In other words the data whose consistency is not ensured is replicated from the VOL to the VOL. Consequently the data in the VOL is also lost.

When a pair status is changed by a fault or a pair operation the data management program of this invention determines data to be inconsistent or data to be overwritten by the change and notifies a user of the data.

The pair status application status management table includes information for managing data in the logical volume and is referred to by the data management program .

In a PVOL and a SVOL are names of a PVOL and an SVOL forming each pair. In the PVOL and the SVOL VOL VOL and the like are described.

A copy group name is a name of a copy group to which each pair belongs. In the copy group name CG and the like are described.

A pair status is a pair status of each pair. In the pair status the PAIR SUSPEND COPY or ERROR is described. In the example shown in the pair statuses of the pairs P P and P are in the SUSPEND and the pair statuses of the other pairs are in the PAIR . This shows that in the remote copy or the local copy is performed in the pairs belonging to the copy groups CG and CG and the remote copy of the pairs belonging to the copy group CG is suspended.

The application shows a pair including the logical volume in which the application is performed by the application server i.e. which receives data I O directly from the application server . In the example shown in since the application server using the DKC performs an application O is described with respect to the pairs including the VOL VOL and VOL.

A static flag shows whether an application is staticized. Staticization refers to the suspension of direct or indirect data access I O from the application server to the logical volume . When the application is staticized O is described with respect to the pairs directly providing the application. It should be noted that only the pairs in which O is described in the application are targeted for description.

The volume data correspondence management table includes information for managing data in the logical volume and is referred to by the data management program .

A data name is a name for identifying data to be stored in each logical volume . The data is identified for example based on an application by which the data is created the application server performing the application and the name of an instance.

In the example shown in the data in the VOLs to are created by the application of SQL server of the application server called HOST and the instance name is SQL instance . The HOST is a name of the application server using the DKC.

The VOLs to are replications of the VOLs to . Therefore the data names of the VOLs to are the same as those of the VOLs to . This also applies to the VOLs to and the VOLs to . In the case where an instance name is changed or the like the data name in the upper stage is not necessarily matched with that in the lower stage.

An application staticized time is a time when the application is staticized with respect to each logical volume . In the VOLs to and the VOLs to are not staticized in other words data write processing to each of these logical volumes is not suspended so the LATEST is described in the application staticized time . On the other hand since the VOLs to and the VOLs to are staticized in other words data write processing to each of these logical volumes is suspended a staticized time 0 00 on May 10th 2004 in the example shown in is described in the application staticized time .

The data name and the application staticized time can be used as an identifier of data. In other words the contents of data with the same data name and the same application staticized time are the same.

A backup ID is an identifier of backup. The value of the backup ID is given when the application is staticized with respect to each logical volume . The same backup ID is given to the logical volumes having the same data name and the same application staticized time . On the other hand different backup IDs are given to the logical volumes in which at least one of the data name and the application staticized time is different. In the VOLs to and the VOLs to are not staticized so the backup ID is vacant. On the other hand since the VOLs to and the VOLs to are staticized a backup ID BID in the example shown in given when they are staticized is described in the backup ID .

Data can also be identified uniquely based on a combination of the data name and the application staticized time in place of the backup ID so the backup ID is not necessary.

The application volume corresponds to the logical volume that receives data I O from the application server among the logical volumes in a copy path including each logical volume .

The copy path refers to a sequence of pairs connected in a cascade shape. For example in the P P and P connected in a cascade shape correspond to one copy path.

In the VOL VOL VOL and VOL belong to the same copy path. Among these logical volumes the VOL receives data I O from the application server . Therefore the application volume of the VOL is the VOL . Similarly the application volume of the VOL and the VOL is also the VOL.

On the other hand the application volume of the VOL VOL and VOL is the VOL. Furthermore the application volume of the VOL VOL and VOL is the VOL.

The volume data correspondence management table may include information on a mount point with respect to each logical volume .

In a volume is a name of a logical volume included in the DKC. In the example shown in in the volume the VOL VOL and VOL are described.

A copy group name is a name of a copy group to which each logical volume belongs. In the example shown in CG is described in the copy group name of the VOL to VOL.

A pair name is a name of a pair to which each logical volume belongs. In the example shown in the P P and P are described respectively in the pair name of the VOL VOL and VOL.

The pair configuration definition table of the application server using the DKC and the DKC is not shown. However in the pair configuration definition table of the application server the names of the logical volumes included in the DKC or the DKC and the name of a copy group and a pair to which they belong are described.

The pair configuration definition table is referred to when the management server creates the pair status application status management table and the volume data correspondence management table and when these tables are updated to the latest contents.

Herein the case where the pair status is changed includes the case where a fault occurs in a pair and the case where a user allows the pair management program to perform a pair operation.

As the precondition for performing the processing in it is necessary that the contents of the pair status application status management table and the volume data correspondence management table are latest. Specifically the management server obtains information related to the contents of these tables from each application server and updates these tables. Alternatively the user may operate the input output unit of the management server to update these tables. This update may be performed before or after a request for monitoring a pair status is received from the user.

In this embodiment as described later in detail when the pair status or the application status is changed the processing shown in or is performed. Consequently the contents of the pair status application status management table and the volume data correspondence management table are updated to latest values. Thus according to this embodiment the latest values are always stored in these tables.

Upon receiving a request for monitoring a pair status from the user the data management program starts monitoring a pair status . Then the data management program waits for a pair status change event . Specifically the data management program waits for the reception of a notification of a change in pair status from the pair management program in the application server .

When obtaining a pair status change event i.e. receiving a notification of a change in pair status the data management program determines whether the pair status after the change is in the ERROR .

In the step when the data management program determines that the changed pair status is in the ERROR a fault occurs in a pair whose pair status has been changed. Therefore the data management program then determines data made to be inconsistent by the fault occurring in the pair . At this time the pair status before the occurrence of the fault in the pair the pair status of each pair in a copy path including the pair in which the fault occurs and an application status are referred to. The procedure of processing in the step will be described later in detail with reference to .

Next the data management program outputs information on data determined in the step i.e. data made to be inconsistent by the fault . Specifically the data management program outputs information such as the name identifier of the data the application staticized time thereof the name identifier of a storage system in which the data is stored and the like is output from the input output unit of the management server . The information output at this time will be described later in detail with reference to .

On the other hand in the step in the case where the data management program determines that the changed pair status is not in the ERROR the pair status has been changed by the execution of a pair operation in the pair. Therefore the data management program determines the correspondence relationship between the logical volume changed by the pair operation and the data stored in the logical volume . At this time the pair status before the execution of the pair operation the pair status of each pair in a copy path including the pair in which the pair operation is executed and the application status thereof are referred to. The procedure of processing in the step will be described later in detail with reference to .

After performing the step or the data management program updates the contents of the pair status application status management table and the volume data correspondence management table so that they are matched with the changed pair status . The procedure of the update will be described later in detail with reference to .

Next the data management program determines whether to complete the monitoring of a pair status . Specifically the data management program determines for example whether the user has input an instruction of completing the monitoring of a pair status.

In the step in the case where the data management program determines not to complete the monitoring of a pair status the data management program returns to the step so as to continue to monitor a pair status.

On the other hand in the step in the case where the data management program determines to complete the monitoring of a pair status the data management program completes the monitoring of a pair status whereby the processing in is completed.

As described above according to the processing in when a pair status is changed the processing of determining data to be inconsistent or data to be overwritten is performed with the detection of the change as a trigger. Therefore even in the case where a fault occurs in a pair or a pair status is changed by another application program or the like as well as when the user performs a pair operation using the pair management program the processing shown in is performed and data to be inconsistent or data to be overwritten is determined.

The relationship among a pair in which a fault occurs the pair status of the pair and the data made to be inconsistent by the fault will be described later in detail with reference to .

Among the information on the data to be inconsistent an output information type represents the kind of information to be output and includes a data name an application staticized time and a storage system name .

The data name further includes an application server name an application name and an instance name . In the case where the application is a file system the data name includes the application server name a file system name not shown and a mount point not shown . The data name may include other information for identifying data to be inconsistent. The storage system name is classified into a local and a remote .

A content corresponds to the output information type . In the example shown in data to be inconsistent is the data in the VOLs to shown in . Thus the content of the data name is the same as that of the data name of the logical volume thereof. Specifically the application server name is HOST1 the application name is SQL server and the instance name is SQL instance 01 .

Similarly the content of the application staticized time is LATEST in the same way as in the application staticized time shown in .

The content of the storage system name is a name identifier of the storage system in which data to be inconsistent is stored. Herein one row corresponds to one logical volume in which data to be inconsistent is stored.

The storage system name is classified into the local and the remote . The local is the storage system in which a logical volume used directly for an application by the application server is stored and the remote is the storage system different from the storage system in which the logical volume used directly for an application is stored. The remote may be connected by the remote copy in a plurality of stages.

In the example shown in the DKC is used for an application by the application server so the storage system name of the DKC is classified into the local . The DKC and the DKC are not used for the application by the application server so the storage system name of the DKC and the DKC is classified into the remote .

According to the data to be inconsistent is not stored in the DKC. Therefore the content of the local is vacant.

According to the data to be inconsistent is stored in the DKC. Therefore the content of the remote is an identifier of the DKC. Specifically in the content the name identifier of the storage system including the logical volume in which the data to be inconsistent is stored is described.

 Abc13468 192.16.1.1 is an identifier of the DKC. REMOTE COPY shows that the data stored in the DKC is replicated from another storage system DKC in this case by the remote copy.

The information on the data to be inconsistent may be output from the input output unit as text data. Alternatively for example the information may be output together with the drawings such as a figure showing a configuration of a computer system and the like.

When the processing in is started the data management program determines whether the pair status immediately before the occurrence of a fault is in the COPY PAIR or SUSPEND . Specifically the data management program refers to the pair status of the pair status application status management table with respect to the pair in which the fault occurs.

In the case where the data management program determines that the pair status immediately before the occurrence of a fault is in the SUSPEND the consistency of the data in the SVOL of the pair is not lost by the fault. Therefore the data management program determines that the data is not inconsistent and completes the processing.

On the other hand in the case where the data management program determines that the pair status immediately before the occurrence of a fault is in the COPY the consistency of the data in the SVOL of the pair is lost by the fault. Therefore the process proceeds to a step .

On the other hand in the case where the data management program determines that the pair status immediately before the occurrence of a fault is in the PAIR the consistency of the data in the SVOL of the pair may be lost by the fault.

Therefore the data management program then determines whether data has been written in the pair in which the fault has occurred or there is a possibility that data has been written . The reason for this is as follows. When data is written in the pair in which the fault has occurred there is a possibility that the consistency of the data in the SVOL of the pair may be lost.

In the step the data management program determines whether a pair whose pair status is in the COPY is present in the upper stage of the pair in which the fault has occurred. Specifically the data management program refers to the pair status of the pair status application status management table with respect to all the pairs in the upper stage of the pair in which the fault has occurred. Then the data management program determines that a pair whose pair status is in the COPY is present in the upper stage of the pair in which the fault has occurred the data management program determines whether the pair status of all the pairs between the pair whose pair status is in the COPY and the pair in which the fault has occurred is in the PAIR .

Consequently in the case where a pair whose pair status is in the COPY is present in the upper stage of the pair in which the fault has occurred and the pair status of all the pairs between the pair whose pair status is in the COPY and the pair in which the fault has occurred is in the PAIR the determination result in the step is Yes . In this case data is written in the pair in which the fault has occurred or there is a possibility that data may be written therein so there is a possibility that the consistency of the data may have been lost. Therefore the process proceeds to the step .

On the other hand in the case where a pair whose pair status is in the COPY is not present in the upper stage of the pair in which the fault has occurred the determination result in the step is No . Furthermore even in the case where a pair whose pair status is in the COPY is present in the upper stage of the pair in which the fault has occurred and the pair status of at least one pair between the pair whose pair status is in the COPY and the pair in which the fault has occurred is not in the PAIR the determination result in the step is No . In this case there is no possibility that data is written in the pair in which the fault has occurred. Therefore the data management program determines that the consistency of the data is not lost i.e. the data is not inconsistent and completes the processing.

In the step the data management program determines whether the pair in which the fault has occurred is synchronized with the application volume . Specifically the data management program determines whether the pair status of all the pairs present between the PVOL of the pair in which the fault has occurred and the application volume in a copy path including the PVOL is in the PAIR .

In the case where the data management program determines that the pair status of all the pairs is not in the PAIR i.e. at least one pair in the SUSPEND is present the pair in which the fault has occurred is not synchronized with the application volume . In this case the consistency of the data in the SVOL of the pair in which the fault has occurred is not lost by the fault. Therefore the data management program determines that the data is not inconsistent and completes the processing.

On the other hand in the case where the data management program determines that the pair status of all the pairs is in the PAIR the pair in which the fault has occurred is synchronized with the application volume . In this case the consistency of the data in the SVOL of the pair in which the fault has occurred may be lost by the fault.

Therefore the data management program determines whether the application has been staticized . Specifically the data management program refers to the static flag of the pair status application status management table with respect to the application volume of the pair in which the fault has occurred.

In the case where the data management program determines that the application has been staticized the consistency of the data in the SVOL of the pair in which the fault has occurred is not lost by the fault. Therefore the data management program determines that the data is not inconsistent and completes the processing.

On the other hand in the case where the data management program determines that the application has not been staticized there is a possibility that the consistency of the data in the SVOL of the pair in which the fault has occurred may have been lost by the fault. Since the data whose consistency is not ensured cannot be used the data in the SVOL of the pair in which the fault has occurred is inconsistent .

Therefore the data management program then determines whether the data in another logical volume is inconsistent by the fault. First the SVOL of the pair in which the fault has occurred is assumed to be the logical volume search target volume first targeted for a search . Furthermore the search target volume is registered in a target list not shown . Herein the target list is a list of the logical volume in which data is inconsistent by a fault.

Next among the pairs adjacent to the lower stage of the search target volume a pair whose pair status is neither in the PAIR nor in the COPY is assumed to have been searched .

Then the data management program determines whether an unsearched pair is present in the pairs adjacent to the lower stage of the search target volume .

In the case where the data management program determines that an unsearched pair is present in the pairs adjacent to the lower stage of the search target volume the consistency of the data in the SVOL of the unsearched pair is lost. Therefore the SVOL of the unsearched pair is set to be a new search target volume and the SVOL is added to the target list . Then the unsearched pair is set to have been searched and the process returns to the step .

On the other hand in the step in the case where an unsearched pair is not present in the pairs adjacent to the lower stage of the search target volume the logical volume in which data is inconsistent is not present any more in the lower stage of the search target volume.

Therefore next the data management program determines whether the search target volume is an initial search target volume see the step or an unsearched pair is present .

In the case where the search target volume is not an initial search target volume and an unsearched pair is present an unsearched pair remains in the lower stage of the first search target volume. Therefore the pair whose search target volume is an SVOL is set to have been searched. Then the logical volume adjacent to the upper stage of the search target volume i.e. the PVOL of the pair whose search target volume is an SVOL is set to be a new search target volume and the process returns to the step .

On the other hand in the step in the case where the search target volume is an initial search target volume see the step or an unsearched pair is not present the search for all the pairs in the lower stage of the initial search target volume has been completed.

Therefore next information on the logical volume registered in the target list is output whereby the processing is completed. Specifically information shown in is output with respect to the logical volume registered in the target list.

In the above processing shown in a depth first search is used for the search the steps to of the logical volume . However even when another search method such as a breadth first search is used this invention can be carried out.

By performing the processing in the correspondence relationship between the logical volume and the data to be stored in the logical volume is determined.

When the processing in is started the data management program determines whether the pair status immediately before being changed is in the COPY PAIR or SUSPEND with respect to a pair whose pair status has been changed .

In the case where the data management program determines that the pair status immediately before being changed is in the PAIR the changed pair status is in the SUSPEND . Thus the change in the pair status into the SUSPEND is notified . In this case data is not overwritten in an SVOL of the pair. In other words the data stored in the SVOL immediately before the pair status has been changed is the same as the data stored in the SVOL immediately after the pair status has been changed. Therefore the correspondence relationship between the logical volume and the data does not change . Thus it is confirmed that there is no data to be overwritten whereby the processing is completed.

On the other hand in the step in the case where the data management program determines that the pair status immediately before being changed is in the SUSPEND the changed pair status is in the COPY or PAIR . Thus the change in the pair status into the COPY or the PAIR is notified .

If the data stored in the PVOL and SVOL of the pair immediately before the pair status has been changed are the same data replication is not performed and the PAIR status is obtained immediately. In this case the data replication is not performed so the correspondence relationship between the logical volume and the data does not change . In other words the data stored in the SVOL immediately before the pair status has been changed is the same as the data stored in the SVOL immediately after the pair status has been changed. Thus it is confirmed that there is no data to be overwritten whereby the processing is completed.

On the other hand if the data stored in the PVOL and the SVOL of the pair are not the same the COPY status is obtained and data replication is performed. Thereafter the PAIR status is obtained. In this case although the data replication is performed the data stored in the SVOL is not confirmed until the data replication is completed. Therefore at a time when the SUSPEND status has been changed to the COPY status it is confirmed that there is no data to be overwritten whereby the processing is completed.

On the other hand in the step in the case where the data management program determines that the pair status immediately before being changed is in the COPY the changed pair status is in the PAIR . Thus the change in the pair status into the PAIR is notified . Then the processing for determining data to be overwritten is started.

Initially data stored in a pair whose pair status has been changed hereinafter referred to as a status changed pair is determined . Specifically the data management program refers to the data name the application staticized time the backup ID and the like in the volume data correspondence management table with respect to the status changed pair.

Then the status changed pair is assumed to be an initial search target pair . Furthermore the SVOL of the status changed pair is registered in an overwrite target volume list not shown . Herein the overwrite target volume list is a list of the logical volume in which data is overwritten by a change in pair status.

In other words as a result of the change in pair status it is determined that the correspondence relationship between the logical volume and the data changes in the SVOL. Specifically as a result that the data in the PVOL is overwritten onto the SVOL the data stored in the SVOL becomes the same as the data stored in the PVOL.

Then the data management program determines whether an unsearched pair is present in the pairs adjacent to the lower stage of the search target pair .

In the case where the data management program determines that there is an unsearched pair among the logical volumes in which data is overwritten by the change in pair status there may be those which are not registered in the overwrite target volume in the lower stage of the search target pair.

Therefore next the unsearched pair adjacent to the lower stage of the search target pair is set to be a new search target pair .

Then the data management program determines whether the pair status of the newly set search target pair is in the PAIR or the SUSPEND .

In the case where the data management program determines that the pair status is in the SUSPEND data replication is not performed in the search target pair. Thus data is not overwritten onto the SVOL of the search target pair. Furthermore there is no logical volume in which data is overwritten in the lower stage of the search target pair. Therefore the search target pair is set to have been searched and the process returns to the step .

On the other hand in the step in the case where the data management program determines that the pair status is in the PAIR the data replication is performed in the search target pair. Thus data is overwritten onto the SVOL of the search target pair. Therefore the SVOL is added to the overwrite target volume list .

In other words as a result of the change in pair status it is determined that the correspondence relationship between the logical volume and the data changes in the SVOL. Specifically as a result that the data in the PVOL is overwritten onto the SVOL the data stored in the SVOL becomes the same as the data stored in the PVOL.

On the other hand in the step in the case where the data management program determines that there is no unsearched pair among the logical volumes in which data is overwritten by the change in pair status those which are present in the lower stage of the search target pair have been all registered in the overwrite target volume list.

In the case where it is determined that the search target pair is not a status changed pair among the logical volumes in which data is overwritten by the change in pair status those which are not registered in the overwrite target volume list may be present in the lower stage of the status changed pair. Therefore the pair adjacent to the upper stage of the search target pair is set to be a new search target pair whereby the process returns to the step .

On the other hand in the case where it is determined that the search target pair is a status changed pair the logical volumes in which data is overwritten by the change in pair status have been all registered in the overwrite target volume list. Therefore the data to be overwritten and the logical volume in which the data is stored are confirmed whereby the processing is completed.

When the table update processing is started first the pair status of the pair status application status management table is updated with respect to a pair whose pair status has been changed .

Next it is determined whether there is data made to be inconsistent by a fault or data overwritten by a change in pair status . Specifically in the case where a fault occurs in a pair it is determined whether there is data made to be inconsistent by the fault with reference to the result of the processing in . In the case where a pair operation is performed it is determined whether there is data overwritten by the change of the pair status with reference to the result of the processing in .

In the case where it is determined that there is no data made to be inconsistent by the fault and no data overwritten by the change in the pair status in the step the processing is completed.

On the other hand in the step in the case where it is determined that there is data made to be inconsistent by the fault or the data overwritten by the change in the pair status the volume data correspondence management table is updated . Specifically the values of the data name the application staticized time the backup ID and the application volume of the logical volume in which data has been overwritten are updated to the same values as those of the logical volume of a replication source of data to be updated.

In the description of the detailed description will be omitted with respect to the portions common to those of the processing performed by the data management program when a pair status is changed in .

The change in an application status includes staticization of an application and cancel of staticization i.e. destaticization of an application. When an application is staticized the application server does not write data in the logical volume . On the other hand when the staticization of an application is cancelled the application server can write data in the logical volume . When the application server overwrites data in the logical volume old data stored in the logical volume is lost.

The processing in is started when the user requests the management server to monitor a pair status and an application status.

Upon receiving a request for monitoring a pair status and an application status from the user the data management program starts monitoring these statuses . Then the data management program waits for a pair status change event or an application status change event . More specifically the data management program waits for receiving a notification of a pair status change or an application status change from the pair management program of the application server .

Upon receiving a pair status change event or an application status change event the data management program then determines whether a pair status has been changed to the ERROR .

In the case where it is determined that the pair status has been changed to the ERROR in the step a fault occurs in a pair whose pair status has been changed. Therefore the data management program then determines data made to be inconsistent by the fault occurring in the pair . The procedure of the processing in the step is as described in .

Next the data management program outputs information regarding data i.e. data made to be inconsistent by a fault determined in the step . The information output at this time is as described in .

Next the data management program updates the contents of the pair status application status management table and the volume data correspondence management table so that they are matched with the changed pair status . The procedure of the update is as described in .

Next the data management program determines whether to complete the monitoring of a pair status and an application status . More specifically for example the data management program determines whether the user inputs an instruction of completing the monitoring of a pair status and an application status.

In the step in the case of determining not to complete the monitoring of a pair status and an application status the data management program returns to the step so as to continue the monitoring.

On the other hand in the step in the case of determining to complete the monitoring of a pair status and an application status the data management program completes the monitoring of a pair status .

On the other hand in the step in the case of determining that the pair status has not been changed to the ERROR a pair operation has been performed in the pair or the application status has been changed. When the pair operation has been performed the pair status has been changed. Consequently the correspondence relationship between the logical volume and the data may be changed. Furthermore even when the application status has been changed the correspondence relationship between the logical volume and the data may be changed. Therefore next the data management program determines the correspondence relationship between the logical volume and the data . The procedure of the processing in the step will be described later in detail see . When the step is completed the process proceeds to the step .

As described above according to the processing in when a pair status or an application status is changed the processing of determining data to be inconsistent or data to be overwritten is performed with the detection of the change as a trigger. Therefore in the case where a fault occurs in a pair or a pair status or an application status is changed by another application or the like as well as in the case where the user performs a pair operation using the pair management program or the like or updates an application status the processing in is performed and the data to be inconsistent or the data to be overwritten is determined.

When the processing in is started the data management program determines which of an application status and a pair status has been changed .

In the case of determining that the pair status has been changed the data management program performs the processing of determining data to be overwritten by the change in the pair status . This processing has been described in so the description thereof will be omitted here.

On the other hand in the case of determining that the application status has been changed next the data management program then determines whether an application has been staticized or the application staticization has been cancelled . In the case where the application staticization has been performed data is not lost by overwrite so the process proceeds to a step .

On the other hand in the case where the application staticization has been cancelled data may be lost by overwrite. Therefore next the logical volume used directly for an application i.e. the logical volume directly accessed by the application server is set to be the logical volume to be first targeted for a search search target volume . Furthermore the search target volume is registered in the overwrite target volume list. The overwrite target volume list is the same as that described in . Furthermore the data to be stored in the search target volume is assumed to be the data to be overwritten.

Furthermore the data in the logical volume in the lower stage of the search target volume may be lost by overwrite. More specifically the data in the logical volume connected by at least one pair whose pair status is in the PAIR in the lower stage of the search target volume is lost by overwrite. In order to determine the logical volume in the lower stage in which data is overwritten the logical volume in the lower stage of the search target volume starts being searched for.

Next it is determined whether there is an SVOL that forms a pair with the search target volume and has not been searched .

In the case where there is an SVOL that forms a pair with the search target volume and has not been searched the search for the logical volume in the lower stage of the search target volume has not been completed. Therefore next it is determined whether the pair status of the pair formed by the search target volume and the unsearched SVOL is in the PAIR or SUSPEND .

In the case where the pair status is in the SUSPEND data is not overwritten on the SVOL. Therefore the SVOL is set to have been searched and in order to check another SVOL the process returns to the step . At this time data is not overwritten even on the logical volume in the lower stage of the SVOL. Therefore it is not necessary to conduct a search for the logical volume in the lower stage of the SVOL.

On the other hand in the case where the pair status is in the PAIR in the step data is overwritten on the SVOL. Therefore the SVOL is added to an overwrite target volume list .

Next the search target volume is set to have been searched and the SVOL is set as a new search target volume thereafter the process returns to the step .

On the other hand in the step in the case where there is no SVOL that forms a pair with a search target volume and has not been searched the search for the logical volume in the lower stage of the search target volume has been completed. Therefore next it is determined whether the search target volume is the logical volume to be directly used for an application .

In the case where the search target volume is not the logical volume to be directly used for an application an unsearched logical volume may remain. Therefore in order to search for the unsearched logical volume the search target volume is set to have been searched and the logical volume adjacent to the upper stage of the logical volume is set as a new search target volume thereafter the process returns to the step .

On the other hand in the case where the search target volume is the logical volume to be used directly for an application the search for the logical volume has been completed. Therefore data to be overwritten and an overwrite target volume are confirmed and the processing is completed.

When the table update processing is started first the pair status application status management table is updated . More specifically in the case where a pair status is changed the pair status of the pair status application status management table is updated with respect to the pair whose pair status has been changed. In the case where an application status is changed the application of the pair status application status management table is updated with respect to the application whose application status has been changed.

Next it is determined whether there is data made to be inconsistent by a fault or data overwritten by the change in the pair status or the change in the application status . More specifically in the case where a fault occurs in a pair the result of the processing in is referred to whereby it is determined whether there is data made to be inconsistent by a fault. In the case where a pair operation is performed the result of the processing in is referred to whereby it is determined whether there is overwritten data. In the case where an application status is changed the result of the processing in is referred to whereby it is determined whether there is overwritten data.

In the step in the case where it is determined that there is neither inconsistent data nor overwritten data the processing is completed.

On the other hand in the step in the case where there is inconsistent data or overwritten data the volume data correspondence management table is updated . More specifically the values of the data name the application staticized time the backup ID and the application volume of the logical volume in which data has been overwritten are updated to the same values as those of the logical volume of a replication source of data to be overwritten.

In steps to are respectively the same as the steps to in . Furthermore steps and are respectively the same as the steps and .

As the precondition for performing the processing in it is necessary that the contents of the pair status application status management table and the volume data correspondence management table be the latest.

Upon receiving a request for monitoring of a pair status from the user the data management program starts monitoring a pair status . Then the data management program waits for a pair status change event .

Upon obtaining the pair status change event i.e. receiving a notification of a pair status change the data management program determines whether the changed pair status is in the ERROR .

In the step in the case where it is determined that the changed pair status is in the ERROR a fault occurs in a pair whose pair status has been changed. Therefore next the data management program determines data made to be inconsistent by the fault occurring in the pair . The procedure of the processing in the step is as shown in .

On the other hand in the step in the case where it is determined that the changed pair status is not in the ERROR a pair operation is performed in the pair. Therefore the data management program determines the correspondence relationship between the logical volume changed by the pair operation and data . The procedure of the processing in the step is as shown in .

After performing the step or the data management program updates the contents of the pair status application status management table and the volume data correspondence management table so that they are matched with the changed pair status . The procedure of the update is as shown in .

Next the data management program outputs information on the data i.e. data made to be inconsistent by a fault determined in the step . The information output at this time is as shown in .

Next the data management program determines whether the logical volume in which consistent data which can recover the data made to be inconsistent by the fault occurring in the pair is stored is present in a copy path .

More specifically the data management program refers to the information output in the step and the volume data correspondence management table . Then the data management program determines whether there is the volume in which the value of the data name is the same as the content of the data name and in which the value of the application staticized time is the same as the content of the application staticized time . In the case where there is the volume in which they are the same the consistent data which can recover the data made to be inconsistent by the fault occurring in the pair is stored in the logical volume corresponding to the volume .

In the step in the case where the data management program determines that the logical volume in which the consistent data which can recover the data made to be inconsistent by the fault occurring in the pair is stored is present in a copy path the data management program notifies the management server that the inconsistent data can be restored by using the data in the logical volume . At this time in the input output unit of the management server the logical volume in which the inconsistent data is stored and the logical volume in which the consistent data which can recover the inconsistent data is stored may be shown see .

The user can restore the inconsistent data based on the information including the information shown in notified in the step .

On the other hand in the step in the case where the data management program determines that the logical volume in which the consistent data which can recover the data made to be inconsistent by the fault occurring in the pair is stored is not present in the copy path the data management program notifies the management server that the consistent data which can recover the inconsistent data is not present .

After performing the step or the data management program determines whether to complete the monitoring of a pair status .

In the step in the case where the data management program determines not to complete the monitoring of a pair status the data management program returns to the step so as to continue monitoring a pair status.

On the other hand in the step in the case of determining to complete the monitoring of the pair status the data management program completes the monitoring of a pair status whereby the processing in is completed.

The screen display is for example output from a screen display not shown of the input output unit of the management server .

The VOL and the VOL form a pair P. In the pair P the VOL is a PVOL the VOL is an SVOL and the pair status is in the SUSPEND .

The VOL and the VOL form a pair P. In the pair P the VOL is a PVOL the VOL is an SVOL and the pair status is in the SUSPEND .

The VOL and the VOL form a pair P. In the pair P the VOL is a PVOL the VOL is an SVOL and the pair status is in the SUSPEND .

The VOL and the VOL form a pair P. In the pair P the VOL is a PVOL the VOL is an SVOL and the pair status is in the COPY .

The VOL and the VOL form a pair P. In the pair P the VOL is a PVOL the VOL is an SVOL and the pair status is in the SUSPEND .

The VOL and the VOL form a pair P. In the pair P the VOL is a PVOL the VOL is an SVOL and the pair status is in the PAIR .

The origin of an arrow displaying each pair is on the PVOL side and the tip end thereof is on the SVOL side.

In the pairs P and P are those which are formed by the remote copy and the pairs P P P and P are those which are formed by the local copy.

Since the pair status of the pair P is in the COPY data replication is being performed in the pair P. In other words in the VOL a part of data i.e. BID of the VOL is replicated.

Since the pair status of the pair P is in the PAIR the data in the VOL is reflected on the VOL. In other words a part of the data i.e. BID of the VOL is replicated even in the VOL.

On the other hand the data BID stored in the VOL is not influenced by the fault of the pair P. Therefore the data BID of the VOL is also present even after the fault has occurred in the pair P.

In the example shown in data made to be inconsistent by a pair fault i.e. data BID of the VOL and the VOL is displayed in reverse video outline . Furthermore in the case where the consistent data which can recover the inconsistent data is present in the copy path that data i.e. data BID of the VOL is displayed in italicized letters.

The user is capable of knowing that the data in the VOL and the VOL have been made to be inconsistent by the fault of the pair P with reference to the display in . Furthermore the user is capable of knowing that the consistent data which can recover the inconsistent data in the VOL and the VOL is stored in the VOL. Therefore the user can perform the processing of restoring the inconsistent data. For example by performing the RESYNC in the pair P after the fault of the pair P has been restored the data BID is replicated from the VOL to the VOL and the VOL. Consequently the inconsistent data is restored.

Next the processing of restoring inconsistent data in the case where data is made to be inconsistent by a pair fault in this embodiment will be described.

Even in the case where data is made to be inconsistent by a pair fault the inconsistent data may be restored by performing the pair operation RESYNC in the pair in which the fault has occurred. For example in when the RESYNC is performed in the pair P the data in the VOL and VOL are restored. Whether the pair operation RESYNC can be performed in the pair in which the fault has occurred is determined by the degree of the occurring fault.

As the precondition for the following processing the event of a fault must be provided with a fault detail code. The fault detail code refers to attribute information representing the degree of a fault.

In steps to are respectively the same as the steps to in . Furthermore steps and are respectively the same as the steps and . Therefore the description of those steps will be omitted.

In when a pair fault occurs data made to be inconsistent by the fault is determined and each table is updated information on the data made to be inconsistent by the fault is output . In the following description the output may be to display a display screen not shown of the input output unit of the management server to transmit the information to a predetermined address to write the information in a file not shown of a management log or the like.

Next the inconsistent data is compared with the data stored in the logical volume in the upper stage of the pair in which the fault has occurred whereby it is determined whether there is the logical volume in which the consistent data which can recover the inconsistent data is stored .

In the case where there is the logical volume in which the consistent data which can recover the inconsistent data is stored and the pair statuses of all the pairs in the copy path between the logical volume and the pair in which the fault has occurred are in the PAIR Yes is determined in the step . On the other hand in the case where there is no logical volume in which the consistent data which can recover the inconsistent data is stored or in the case where there is a pair in a status other than the PAIR in the copy path between the logical volume and the pair in which the fault has occurred No is determined in the step .

Whether there is the logical volume in which the consistent data which can recover the inconsistent data is stored is determined with reference to for example the backup ID of the volume data correspondence management table .

In the case where No is determined in the step the consistent data which can recover the inconsistent data is not present on the storage system or the inconsistent data cannot be restored by performing the RESYNC in the pair in which the fault has occurred. Therefore the data management program outputs the fact that the pair operation is not performed and proceeds to a step . In the step the data management program may output the fact that the consistent data which can recover the inconsistent data is not present on the storage system or the inconsistent data cannot be restored by performing the RESYNC in the pair in which the fault has occurred.

On the other hand in the case where Yes is determined in the step next it is determined whether the degree of the fault is low i.e. whether a pair operation RESYNC can be performed in the pair in which the fault has occurred . This determination is performed with reference to the fault detail code provided to the event of the fault and a fault detail code table . The fault detail code table will be described in detail later see .

In the step in the case where it is determined that the degree of the fault is high i.e. the pair operation RESYNC cannot be performed in the pair in which the fault has occurred the process proceeds to a step .

On the other hand in the step it is determined that the degree of the fault is low i.e. the pair operation RESYNC can be performed in the pair in which the fault has occurred next the data management program output a display for confirming whether to permit the restoration of the inconsistent data by performing the pair operation RESYNC in the pair in which the fault has occurred and waits for a response from the user .

In the step in the case where there is a response that the pair operation RESYNC is not permitted to be performed or in the case where a pair status change event is received while the data management program waits for a response from the user the process returns to the step .

On the other hand in the step in the case where there is a response that the pair operation RESYNC is permitted to be performed the pair operation RESYNC is performed in the pair in which the fault has occurred .

Next it is determined whether to complete the monitoring of a pair status . In the case where it is determined that the monitoring of a pair status is not completed the process returns to the step . In the case where it is determined that the monitoring of a pair status is completed the monitoring of a pair status is completed and the processing in is completed.

The fault detail code table is stored in the disk device of the management server and is referred to by the data management program more specifically the processing shown in . The fault detail code table associates the fault detail code with the information showing whether the pair operation RESYNC can be performed in the pair in which the fault has occurred.

The fault detail code table is composed of a fault detail code number a fault detail code and a RESYNC acceptance rejection .

The fault detail code is a code representing the degree of a fault. A fault event is provided with any of the fault detail code .

The RESYNC acceptance rejection represents whether the pair operation RESYNC can be performed with respect to each fault detail code .

In the example shown in the RESYNC acceptance rejection of the fault detail code x001 and xca0 is rejection . This shows that the fault corresponding to x001 and xca0 is serious and the pair operation RESYNC cannot be performed with respect to the pair in which these faults have occurred.

For example in the case where a fault detail code provided to an event of a fault is x001 in the step in the fault detail code table is referred to. Then since the RESYNC acceptance rejection corresponding to the fault detail code x001 is rejection it is determined that the fault is serious and the pair operation RESYNC cannot be performed.

On the other hand the RESYNC acceptance rejection of the fault detail code x002 and xc99 are both acceptance . This shows that the fault corresponding to x002 and xc99 is not serious and the pair operation RESYNC can be performed with respect to the pair in which these faults have occurred.

For example in the case where the fault detail code provided to the event of the fault is x002 in the step in the fault detail code table is referred to. Then since the RESYNC acceptance rejection corresponding to the fault detail code x002 is acceptance it is determined that the fault is not serious and the pair operation RESYNC can be performed.

According to this embodiment as described above when a pair status or an application status is changed the processing for determining data to be inconsistent or overwritten is performed with the detection of the change as a trigger. Therefore when a pair status or an application status is changed by another application program or the like as well as when a user performs a pair operation or changes an application status data to be overwritten on a logical volume by the change is determined.

Consequently the contents of a latest pair status and application status and a logical volume i.e. correspondence between the logical volume and the data can be grasped at all times.

Furthermore when a fault occurs in a pair the above mentioned latest pair status and the like are referred to whereby data made to be inconsistent by the occurring fault can be accurately determined.

Furthermore in the case where data is made to be inconsistent by the fault of the pair it is determined whether there is the consistent data which can recover the inconsistent data in any of the logical volumes. In the case where there is the consistent data which can recover the inconsistent data the location of the consistent data which can recover the inconsistent data is displayed. The user can perform the processing of restoring the inconsistent data by referring to the display.

Furthermore it is determined whether the inconsistent data can be restored by performing the pair operation RESYNC in the pair in which the fault has occurred. In the case where the data can be restored the user is inquired about whether the RESYNC is performed. In the case where the user permits the RESYNC to be performed the RESYNC is performed whereby the inconsistent data is restored.

Thus this embodiment supports the restoration of data made to be inconsistent by the fault occurring in the pair.

