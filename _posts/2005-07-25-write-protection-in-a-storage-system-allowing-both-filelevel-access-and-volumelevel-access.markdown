---

title: Write protection in a storage system allowing both file-level access and volume-level access
abstract: A method for write protection in a storage system using both the “file-level WORM function” and the “block-level WORM function”. The block-level WORM function has two modes: the first mode is to prohibit both file access and block access, and the second mode is to prohibit block access only. When a user uses the file-level WORM function to prohibit write access to a file in a volume, a file access invokes the first mode of the block-level WORM function to prohibit write access to the volume where the write prohibited file resides.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07558930&OS=07558930&RS=07558930
owner: Hitachi Data Systems Corporation
number: 07558930
owner_city: Santa Clara
owner_country: US
publication_date: 20050725
---
The present invention relates to the storage system for archiving and more specifically to the Network Attached Storage NAS .

A Write Once and Read Many WORM storage is a storage that is not erasable and rewritable but can be read freely. Currently there are two types of WORM storage systems the volume level WORM storage system and the file level WORM storage system. A volume level storage system is operative to prohibit write access from host computers to a volume of information that is assembled as a data unit group such as a block for a certain period of time. The volume of information may be defined and specified as a logical device. This type of system is often used as a block level access storage system like those communicating with hosts using SCSI FCP SCSI or iSCSI protocols.

A file level WORM has a means for prohibiting write access to each file which may be considered a data unit for a certain period of time. This type of system is often used as a file level access storage system such as a network attached storage NAS system which communicates with hosts using file level access protocols like NFS CIFS etc.

Some storage systems allow both the file level access and the block level access. U.S. Pat. No. 6 779 083 discloses a storage system having a block interface e.g. Fibre channel and a file interface e.g. NFS or CIFS via Ethernet and allowing access to a volume from both the block interface and the file interface. Even if such a storage system has means for prohibiting write access to one of the files for a certain period of time the file still may be overwritten from a host connected to the block interface since the volume where the file is stored can also be accessed from the block access interface. One method for preventing write access to the file is to apply a volume level WORM function to the volume. But when the volume level WORM is applied write access to all files are prohibited including those that users want to have write access.

Therefore it would be desirable to provide a method for write protection in the system having both a block interface and a file interface.

In view of the foregoing it is an object of the present invention to provide a method for more secure data protection.

The storage system of the present invention has at least two methods for processing host accesses the file access method for processing file level access from hosts and the block access method for processing block level access from hosts. The file access method prohibits write access to a file for a certain period of time the file level WORM function and the block access method prohibits write access to a block or volume of information for a certain period of time the block level WORM function . The block level WORM function has two modes the first mode is to prohibit both file access and volume access and the second mode is to prohibit volume access only thereby permitting file access to other files in the volume.

In the storage system of the present invention when a user uses the file level WORM function to prohibit write access to a file in a block or volume a file access invokes the first mode of the block level WORM function to prohibit write access to the volume where the write prohibited file resides. Consequently the files in the volume protected by the file level WORM function can not be accessed from the block interface adapter but other files in the volume can still be accessed from the block interface adapter.

Objects and advantages of the present invention will become apparent from the following detailed description. The following description of illustrative non limiting embodiments of the invention discloses specific configurations and components. However the embodiments are merely examples of the present invention and thus the specific features described below are merely used to describe such embodiments to provide an overall understanding of the present invention. One skilled in the art readily recognizes that the present invention is not limited to the specific embodiments described below. Furthermore certain descriptions of various configurations and components of the present invention that are known to one skilled in the art are omitted for the sake of clarity and brevity.

A WORM state means that the files e.g. data units or the corresponding logical devices cannot be overwritten or deleted by users for a period of time.

A WORM state file refers to the file or data unit that cannot be overwritten or deleted by users for a period of time.

A retention period is one of the attributes of a WORM state file and WORM state volume. A WORM state file or WORM state volume cannot be overwritten or deleted until the time indicated by the retention period is passed or expires.

A WORM state filesystem is a file system in which all files and directories therein cannot be overwritten or deleted by users. In other words the file system is in the WORM state. When one filesystem is stored in a single logical device the meaning of the WORM state filesystem is substantially the same as the meaning of the WORM state volume as would be understood by one skilled in the art.

The file interface adapter has an interface for communicating with client host computers using a file level access protocol e.g. NFS CIFS or the like as would be understood by one skilled in the art. In the illustrated exemplary embodiment the interface is an Ethernet interface LAN I F . Each file interface adapter also has one or more CPUs and one or more corresponding memories and and an interface between the coupled CPU s and respective memories . The storage system may have a plurality of file interface adapters

The block interface adapter has an interface for communicating with client host computers using a block level access protocol e.g. SCSI iSCSI or the like. In one embodiment the block interface adapter communicates with the client host computers using the FCP SCSI protocol and the interface is a Fiber Channel interface FC I F . In another embodiment the block interface adapter communicates with the client hosts using iSCSI protocol and the interface is an Ethernet interface. The block interface adapter also includes a CPU and a memory . The storage system may have a plurality of block interface adapters . Hereinafter both the file interface adapter and the block interface adapter are referred to as host adapters .

The storage media in the form of a disk shared memory and or cache memory provides the file and or block storage for the WORM based data. A disk adapter is operative to create one or more logical devices from a plurality of disks and comprises a CPU a memory and a Fiber Channel interface FC I F . The storage system may have a plurality of disk adapters . The shared memory is used by the file interface adapter the block interface adapter and the disk adapter to effect communication with each other. The cache memory is used to store the read data from disks or to store the write data from client hosts or to accelerate read write accesses.

An internal switch which may be a common switch or separate switches serves to connect each of the file interface adapters to the storage media. In addition console is attached to the storage system via switch to issue instructions to the storage system to define logical devices to administer and maintain the storage system or for other purposes as would be known to one skilled in the art.

As shown the file interface adapters are implemented in software and include a network filesystem module a local filesystem module a device driver and a logical device module . The file interface adapters may be coupled to logical storage devices such as dedicated device and shared device .

The network filesystem module is used to communicate with the client host s using an appropriate protocol such as the NFS or CIFS protocol. For example it may receive a file access request in accordance with the NFS or CIFS protocol and communicate with the local filesystem module to access the file systems created in the logical devices such as dedicated device or shared device .

The local filesystem module creates the file system in the logical devices such as dedicated device and shared device receives file access requests from the network filesystem module and responds to the file access requests. To access logical devices the local filesystem module issues access requests to the device driver . The local filesystem module is also operative to prohibit write access to a user specified file for a certain period of time. Users of client hosts can specify the file to which the user wants to prohibit write access and the period for write prohibition by using Application Programming Interfaces APIs .

The device driver converts an access request from the local filesystem module and accesses logical devices via the hardware interface of the type illustrated in . The access protocol used in the device driver corresponds to that used in the interface . If the interface is a Fiber Channel interface the Fiber Channel protocol is used in the device driver as well. If the interface is a proprietary interface of the vendor of the storage system the proprietary protocol is used in the device driver accordingly. In yet another exemplary embodiment the protocol is a proprietary protocol that enhances the SCSI protocol.

In one exemplary embodiment modules and comprise software stored in memory such as the memory of . A skilled artisan would appreciate that the modules could also be implemented by hardware or firmware.

The logical device module in receives access requests from the device driver via a hardware interface then issues requests to access the logical devices such as dedicated device shared device and dedicated device . The issued access requests are once stored in the shared memory . When the disk adapter detects requests in the shared memory it retrieves the requests from the shared memory and processes the requests.

The logical device module and also is operative to prohibit write access to the user specified logical volumes for a certain period of time. Users can specify the logical volume for which they want to prohibit write access from client hosts or via a Graphical User Interface GUI from the console via a Command Line Interface CLI from client hosts via APIs or by the instructions from the interface adapter

In one exemplary embodiment the logical device module is a software program stored in the memory and is executed by the CPU in . A skilled artisan would appreciate that the logical device module could also be implemented by hardware or firmware.

A logical device module in the block interface adapter is similar to the logical device module . The one difference is that the logical device module receives I O requests from the device driver and the logical device module receives I O requests from client hosts

In one embodiment the logical device module is a software program stored in the memory and is executed by the CPU in . A skilled artisan would appreciate that the module could also be implemented by hardware or firmware.

In the exemplary embodiment illustrated in the device driver the local filesystem module and the network filesystem module are executed in the CPU of and the logical device module is executed in another CPU . A skilled artisan would appreciate that as an alternative the logical device module the device driver the local filesystem module and the network filesystem module can be executed in the same CPU.

The disk adapter in creates one or more logical devices from a plurality of disks . The operation of the disk adapter is well known and the description thereof is omitted. An example of the relation between logical devices 0 3 and disks is presented in . The storage system constructs a RAID Redundant Arrays of Inexpensive Disks from a plurality of disks and creates logical devices 0 3. Each logical device has its unique identification number called logical device number. As shown in logical devices whose logical device numbers are 0 1 2 and 3 are created in the RAID group.

The local filesystem module creates a data structure or file system in a logical device to store files. shows a file system according to one exemplary embodiment of the present application. As shown there are three kinds of regions in the file system a metadata region a directory entry region and a data region . The directory entry region is used to store directory name or file name information. Data of each file is stored in the data region .

The metadata region is a set of attribute information of each file which comprises a superblock a block bitmap and i node tables . Each i node table includes elements through . The i node number is a unique number assigned to a particular node in storage that contains a file and the file type and size identify relevant information about the file. Last access time and last modified time provide relevant historical information about the file and are used for a variety of administrative tasks as would be known in the art. As subsequently explained an access permission parameter indicates whether write access to the file is permitted in general. Also among these elements a retention flag and a retention period are used to store the file attributes related to the WORM state. The retention flag is used to indicate whether the file associated with the i node is in the WORM state and the retention period value is used to identify the related retention period. The combination of the retention flag and the retention period parameter defines whether a file cannot be overwritten or deleted by anyone before the retention period expires. A pointer directs further access to another specified storage location.

Conventional file systems have access permission information which indicates whether the file can be written and is called the write permission bit. The difference between the write permission bit and the retention flag is that the write permission bit can be changed by the owner of the file whenever desired but no one can change the retention flag until the retention period expires.

Device access to the information stored in a file system for example is initiated by an I O request issued by a driver device in the case of a file access by client host and by client host directly in the case of a block access. Each I O request issued by the client host or the driver device includes the identification information of the logical device and the location information in the logical device where the client host or the driver device wants to access. In FCP SCSI used by the client host a World Wide Name WWN is used as the identification information and Logical Block Address LBA is used as the location information. The driver device in the file interface adapter uses a Target ID T ID and LBA for the device identification information and location information respectively.

In the column for configuration information CONF each logical device has a value 0 or 1. When the value is 1 the storage system does not allow users to access certain changes of the configuration of the logical device. When the value is 0 user access is permitted.

In the column TARGET ID the device identification information WWN or T ID is stored. When the value of MODE is 1 write accesses from only the block interface adapter are allowed and the WWN is stored. When the value of MODE is 2 write accesses from only the file interface adapter are allowed and T ID is stored. When the value of MODE is 0 like LDEV since write accesses to the logical device from both the file interface adapter and the block interface adapter are allowed both WWN and T ID are stored. The client hosts access the logical device using WWN and the client hosts access the logical device via the device driver using T ID.

A logical unit number is stored for each logical device in the column LUN . When client hosts or access the logical device LUN is specified in addition to WWN or T ID.

Either 0 or 1 is stored in the access permission column PERM . When the value is 0 the write access to the logical volume is not prohibited. When the value is 1 the write access to the logical device is prohibited until the time that is specified in the column RETENTION . As discussed above when the value in the column PERM is 1 the file is in the WORM state.

Information in the column RETENTION indicate the period when the logical device is not allowed to be written. Until the time specified in the column RETENTION is reached the logical device module or does not allow write access to the logical volume from client hosts or . As mentioned above the time shown in the column RETENTION is called the retention period. Rather than a specified date and time the retention period may be identified as a specific time duration or other measure of time as would be understood by one skilled in the art.

When the value in the column MODE is 0 or 2 write accesses to the logical device from the file interface adapter are allowed and the value in the configuration column CONF is 1 the value in the column RETENTION is set even if the value in the column PERM is 0. In this status the latest retention periods of all the WORM state files are stored.

The file system configuration table is stored in the memory . Columns and are for the TARGET ID T ID and the logical unit number LUN of the logical device containing the file system.

The column DEV FILE is for the device filename of the logical device. The local filesystem module uses the device filename to issue an access request to the logical device.

The column PERM is similar to the column PERM in . Either 0 or 1 is stored in the column. The local filesystem module can set the file state into the WORM state using the retention flag . The local filesystem module can also set or change the state of an entire file system to a WORM state i.e. all files and directories in the file system are prohibited from being updated deleted. When the value is 1 the local filesystem module prohibits any write access to the file system until the time specified in the column RETENTION . When the value is 0 the local filesystem module allows write access to the file system.

When at least one of the files in the file system is set to the WORM state the local filesystem module stores a value 1 in the column PERM . When no file is in the WORM state a value 0 is stored in the column PERM .

The column RETENTION shows the period when the logical device is not allowed to be written. Until the time specified in the column RETENTION the local filesystem module does not allow any write access to the file system.

When the value in column PERM is 1 the latest retention periods of all the WORM state files are stored in the column RETERNTION .

In one embodiment the values in the column RETENTION and in the column RETENTION are set independently. It is possible that the value in the column RETENTION is earlier than the value in the column RETENTION . In this case the write access to all files and directories in the file system is prohibited before the retention period that is stored in the column RETENTION . After the retention period that is stored in the RETENTION the local filesystem module allows updating files in the file system except the files whose retention flag is set and whose retention period is later than current time.

At step the local filesystem module issues a read request to the logical device module via the driver device to read the i node of the specified file. If a copy of the i node exists in the memory the process is not executed. Otherwise after receiving the data block of i node from the device driver the process proceeds to step .

At step the local filesystem module checks whether the value of the retention flag which is. copied from the logical device to the memory is 1. If yes the file is already in the WORM state. The process then terminates returning an error to the user.

If the value of the retention flag is 0 the local filesystem module sets the retention flag field of the specified file to 1 and sets the retention period field of the specified file. At this point these fields are not reflected to the logical device.

At step the local filesystem module issues a write request with the updated i node information to update the i node of the file. After the driver device returns an acknowledgement of the write request the process proceeds to step .

At step it is determined whether the retention period to be set to the specified file by the user is later than the latest retention period currently set in one of the files in the file system. This can be done by comparing the retention period specified by the user with the RETENTION in the file system configuration table . If the retention period specified by the user is not later than the time in RETENTION the process ends. If the retention period specified by the user is later than the time in the RETENTION the local filesystem module issues a request to change the mode of the logical device to the WORM state at step . As discussed below the logical device module then performs steps to set the mode of the logical device to the WORM state. When the logical device module returns a completion signal the process ends.

At step when receiving the read request issued by the local filesystem module at step the logical device module reads i node data from the logical device and returns the i node data to the local filesystem module . The location information of the i node is sent from the local filesystem module with the read request which includes T ID LUN and LBA.

At step when receiving the write request issued by the local filesystem module at step the logical device module writes data to the logical device specified by the user.

From step to step the logical device module sets the mode of the logical device to the WORM state when it receives the request from the local filesystem module . The request contains the retention period. In one embodiment the format of the request is a proprietary format. Alternatively the format may be the enhanced format of the MODE SELECT command in the SCSI protocol.

At step the logical device module receives the request issued by the local filesystem module at step to set the mode of the logical device to the WORM state and changes the value of the CONF in the corresponding logical device to 1.

At step the logical device module checks if the specified logical device is accessible from both the block interface adapter and the file interface adapter . The check can be carried out by examining the corresponding row of the logical device configuration information . If the logical device is accessible from both host adapters two sets of TARGET ID and LUN are defined in the logical device. For example in the first row the element in two sets of TARGET ID and LUN are defined in LDEV zero. If the logical device is accessible from both host adapters the process proceeds to step . Otherwise the process proceeds to step .

At step the logical device module changes the value of the field PERM in the corresponding logical device into 1 and puts the retention period in the field RETENTION . Only the field of PERM and RETENTION that are used for the block interface adapter e.g. the row where WWN is set in the TARGET ID field are updated. When the PERM and the RETENTION fields are already set i.e. when one or more files in the logical device have already been set to the WORM state the process compares the retention period currently set in the RETENTION field with the new retention period received at step and updates the RETENTION field if the new retention period is later than the current retention period. If the new retention period is earlier than the current retention period in the RETENTION the value of the RETENTION is not updated.

At step the logical device module sets the RETENTION of the file interface. Again if the retention period received from the local filesystem module is not later than the current RETENTION the RETENTION field is not updated.

At step a completion signal is returned to the local filesystem module advising that the change in has been accomplished.

At step the local filesystem module compares the new retention period received from the user and the RETENTIONI and RETENTION that are then currently stored in the file system configuration table in . If the newly received retention period is later than the RETENTIONI and the RETENTION the process proceeds to step . Otherwise the process terminates.

At step the local filesystem module issues a request to change the mode of the logical device to the WORM state. As discussed below the logical device module then performs steps to set the mode of the logical device to the WORM state. When a completion signal is returned from the logical device module to the local filesystem module the process ends.

At step the logical device module checks the logical device configuration information and decides whether the retention period is already set in the specified logical device. If it is set the process proceeds to step . Otherwise the process proceeds to step .

At step it is determined whether the retention period newly received from the local filesystem module is later than the retention period currently set in the RETENTION field in the corresponding logical device. If so the process proceeds to step . Otherwise the process proceeds to step . At step the logical device module . sets the PERM field in the logical device to 1 and sets the retention time into the RETENTION field. At step a completion signal is returned to the local filesystem module .

At step the local filesystem module checks as to whether the current time is later than the retention period of the designated file. If the current time is not later than the retention period the process terminates. Otherwise the process proceeds to step .

At step the local filesystem module resets the retention flag and the retention period of the file according to the user s request.

At step the local filesystem module checks if there are still other WORM state files in the file system. If other WORM state files exist the process skips to step . Otherwise the process proceeds to step .

At step the local filesystem module resets PERM and RETENTION in the file system configuration table .

At step the local filesystem module checks if the file system is in WORM state i.e. whether the PERMI in the file system configuration table is 1. If yes since the process does not need to change the state of the logical volume at this point the process ends. Otherwise the process proceeds to step .

At step the local filesystem module issues a request to the logical device module to reset the mode of the logical device. As discussed below the logical device module resets the mode of the logical device at steps and . When the completion signal is returned from the logical device module to the local filesystem module the process ends.

At step the logical device module checks the logical device configuration information to see if the current time is later than the retention period of the designated logical volume. If the current time is not later than the retention period the process skips to step . Otherwise the process proceeds to step . At step the logical device module sets the CONF into 0 and the RETENTION PERIOD in the logical device configuration information is deleted. At step the process returns a completion signal to the local filesystem module .

At step the local filesystem module checks if the current time is later than the RETENTION of the designated file system logical volume . If the current time is not later than the RETENTION the process terminates. Otherwise the process proceeds to step .

At step the local filesystem module checks as to whether at least one of the files in the filesystem is still in the WORM state e.g. by checking if the PERM in the file system configuration table is still 1. If it is since the process does not need to change the state of the logical volume at this point the process ends. Otherwise the process proceeds to step .

At step the local filesystem module issues a request to reset the mode of the logical device. As discussed below the logical device module resets the mode of the logical device at step . When the completion signal is returned from the logical device module to the local file system this process ends. At step the logical device module sets the CONF into 0 and the RETENTION PERIOD in the logical device configuration information is deleted. At step the process returns completion signal to the local filesystem module .

A skilled artisan would appreciated that other operation such as defining logical devices from disks can also be included.

At step the logical device module or receives a request and parameters for device mapping un mapping. The parameters include 

At step the process checks whether the request is for mapping the logical device to a host adapter or for un mapping the logical device from a host adapter. If the request is for mapping the logical device the process proceeds to step . If for unmapping the process proceeds to step .

At step the process checks whether the logical device is already assigned to any other host adapter. If yes the process proceeds to step . Otherwise the process goes to step .

At step the process checks if the CONF of the other host adapter is 0. If the value of the CONF is 0 the other host adapter is not in the WORM state and the process proceeds to step . If the value of the CONF is 1 the other host adapter is in the WORM state and the process terminates and returns error information to the requester.

At step the process un maps the logical device from the specified host adapter. In one embodiment the process deletes the corresponding entry in the logical device configuration table .

At step the process assigns theological device to the specified host adapter. In one embodiment the process adds the corresponding entry in the logical device configuration table .

From step to step the process decides whether the PERM field of the host adapter assigned at step should be set to 1. The rules are as follows 

Specifically at step the process checks if the logical device is already assigned to host adapters other than the one assigned at step . If yes the process proceeds to step . Otherwise the process ends.

At step the process checks if the assigning request is to assign the logical device to the file interface adapter or to the block interface adapter . If the request is to assign the logical device to the file interface adapter the process proceeds to step . Otherwise the process proceeds to step .

At step it is decided whether the CONF of the logical device is 1or if the PERM of the host adapters found already assigned to the logical device at step is 1. If yes the process proceeds to step . Otherwise the process ends.

At step the process checks if the CONF field of the logical device is 1. If it is 1 the process proceeds to step . Otherwise the process proceeds to step .

At step the process checks if the PERM of the file interface adapter found already assigned at step is 0. If it is 0 the process ends. Otherwise the process proceeds to step .

In addition according to the rules mentioned above if the logical device is already mapped to one or more block interface adapters but is not mapped to any file interface adapters the RETENTION field of the host adapter assigned at step is set at step to the same value as that of the block interface adapters . If the logical device is already mapped to one or more block interface adapters and is also mapped to one or more file interface adapters the RETENTION field of the host adapter assigned at step is set at step to the same value as that of file interface adapters

This invention is used for information systems accommodating a plurality of different kinds of host access methods such as file access and block access and which is used for archiving data securely. When two kinds of host access methods are allowed the volume that is used by NAS accessed via the file interface adapter can be shared by the client hosts via Fiber Channel SAN and the data in the volume can be backed up via Fiber Channel SAN to a tape device see . This contributes to the workload reduction of the CPU of the file interface adapter or client hosts but it has risks that the data in the volume is erroneously or maliciously overwritten from client hosts . In this invention when users set the state of the file or file system via the file interface adapter into the WORM state since the volume where the file or file system reside becomes inaccessible from client hosts via Fiber Channel SAN the storage system is advantageous in both the workload reduction of file interface adapter or client hosts and the data security.

This invention can also be applied to other storage system having a different configuration from the storage system in . For example the storage system in does not have file interface adapter but has a NAS gateway in which the network filesystem module the local filesystem module and driver reside. This invention can also be applied to the combination of the storage system shown in and the storage system shown in .

While the invention has been described in detail above with reference to some embodiments variations within the scope and spirit of the invention will be apparent to those of ordinary skill in the art. Thus the invention should be considered as limited only by the scope of the appended claims.

