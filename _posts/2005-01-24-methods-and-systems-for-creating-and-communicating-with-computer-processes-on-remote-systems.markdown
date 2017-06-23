---

title: Methods and systems for creating and communicating with computer processes on remote systems
abstract: An application programming interface (API) presents services of a system to applications. The API is usable with all processes, local and remote, and is transparent with respect to the location of processes. A process table stores information about processes created using the system. The process table supports centralized process control and peer-to-peer process communication and synchronization. Each process is assigned a Universally Unique Identifier (UUID) that uniquely identifies the process no matter the computing device on which it runs. A parent UUID and a group UUID may be attached to the process and used for enforcing dependencies (e.g., for halting the process and all of its child processes) and for managing arbitrary, user-defined groups, respectively. A global event is associated with each process. When a process receives this event, it performs a controlled shutdown, cleans up, and reports status.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07587725&OS=07587725&RS=07587725
owner: Microsoft Corporation
number: 07587725
owner_city: Redmond
owner_country: US
publication_date: 20050124
---
This application is a divisional application of and claims the benefit of U.S. patent application Ser. No. 09 872 257 filed Jun. 1 2001 which issued as U.S. Pat. No. 7 089 561 on Aug. 8 2006 content of which is hereby incorporated by reference.

The present invention relates generally to computer operating systems and more particularly to communications mechanisms for computer processes.

Often a process running on one computing device may need to create or communicate with a process on another device. The use of remote devices may simply be a convenience as for example when a program requires so many resources that it cannot effectively be run on one device. The work of the program may then be shared among several devices by invoking processes on the remote devices to perform pieces of the overall task. The results produced by the remote processes are collected in a central coordinating process. In other cases the use of remote devices is inherent in the nature of the work at hand. For example communications protocols cannot be fully tested on one device. A script for testing a protocol may be run on a test host device. To perform the test the script may start an application on a second device start a peer application on a third device and start an application on a fourth device to monitor the communications between the applications on the second and third devices.

Methods exist for a process running on a host computing device to create a process on a remote device. However these methods provide much less functionality for communicating with the remote process than is available for processes running locally. Often these methods only allow the host device to start the remote process receive output from it and terminate it. The termination is uncontrolled not giving the remote process a chance to clean up before exiting. Another drawback of these methods is the distinction they draw between local and remote processes. This makes it very difficult to debug a program on one device and know that it will work correctly when it is running on multiple devices.

Even for purely local processes current methods of communication are in some ways inadequate. Local processes may be limited in their ability to log ongoing status information. Termination of local processes may be as uncontrolled as for remote processes.

What is needed is a method that enhances the communications abilities of all processes and that provides the full functionality of local processes to processes on remote computing devices. The method would ideally hide the distinction between local and remote processes allowing all processes to be treated in the same manner.

The above problems and shortcomings and others are addressed by the present invention which can be understood by referring to the specification drawings and claims. The present invention provides mechanisms for creating and communicating with computer processes. An application programming interface API presents the services of the invention to applications. The API is usable with all processes local and remote and is transparent with respect to the location of processes. The invention also works with processes that do not use the API although some enhanced services are available only to processes using the API.

A process table stores information about processes created using the invention. The process table is accessible by all processes local and remote and supports centralized process control and peer to peer process communication and synchronization. Locks are used to synchronize access to the process table.

Each process is assigned a Universally Unique Identifier UUID that uniquely identifies the process no matter the computing device on which it runs. A parent UUID and a group UUID may be attached to the process and used for enforcing dependencies e.g. for waiting for or halting the process and all of its child processes and for managing arbitrary user defined groups respectively.

A global event is associated with each process. When a process receives this event it performs a controlled shutdown cleans up and reports its status. Users define other global events and assign meanings to them. Global events form a generally useful message passing mechanism.

At frequent intervals processes and process threads log heartbeat entries in the process table. If a process or thread stops updating this field then other processes can assume that this process or thread broke into the debugger. A process may log other information such as the number of its threads and the current status of the threads.

Turning to the drawings wherein like reference numerals refer to like elements the invention is illustrated as being implemented in a suitable computing environment. The following description is based on embodiments of the invention and should not be taken as limiting the invention with regard to alternative embodiments that are not explicitly described herein.

In the description that follows the invention is described with reference to acts and symbolic representations of operations that are performed by one or more computers unless indicated otherwise. As such it will be understood that such acts and operations which are at times referred to as being computer executed include the manipulation by the processing unit of the computer of electrical signals representing data in a structured form. This manipulation transforms the data or maintains them at locations in the memory system of the computer which reconfigures or otherwise alters the operation of the computer in a manner well understood by those skilled in the art. The data structures where data are maintained are physical locations of the memory that have particular properties defined by the format of the data. However while the invention is being described in the foregoing context it is not meant to be limiting as those of skill in the art will appreciate that various of the acts and operations described hereinafter may also be implemented in hardware.

The present invention provides services for creating and communicating with computer processes whether the processes are all running locally on one computing device or are scattered among several remote devices. Information about processes is gathered into data structures called process tables. The process tables are accessible by all processes local and remote and support centralized process control and peer to peer process communication and synchronization.

This section provides an overview of the mechanisms and capabilities of the invention and includes implementation details only when they are useful to illustrate the discussion. The following section expands on this overview by presenting in great detail an exemplary embodiment of the invention.

Each computing device runs a service called spsrv that coordinates communications among the devices. The spsrv service listens for requests coming in to a device and processes them. These requests include requests to create a process requests to provide updated status information and requests to send information to a process. The spsrv service also sends out status updates and responses to enquiries. This service generally makes communications details transparent so that an application can deal with processes regardless of the device on which they are running. Details specific to remote communications are discussed in the section below entitled Specific Considerations When Communicating with Remote Processes. 

Each computing device contains a process table that has an entry for each process running on or invoked by a process running on the computing device. The process table of computing device contains six entries. The first four entries are for Processes through which run on the device. In addition the process table contains entries for Process and which do not run locally but were invoked by Process which does run locally. Process table on computing device contains an entry for Process because that process runs locally even though the process was invoked on another device. Similarly process table on computing device contains entries for Process running locally though invoked remotely and Process running locally. Process illustrates processes running on a computing device that have nothing to do with the job run by the user of computing device . Process tables are described in greater detail with reference to . For the moment note that process tables are populated when a process is created and contain information useful for controlling and monitoring the processes.

The computing devices and of may be of any architecture. is a block diagram generally illustrating an exemplary computer system that supports the present invention. The computing device is only one example of a suitable environment and is not intended to suggest any limitation as to the scope of use or functionality of the invention. Neither should the computing device be interpreted as having any dependency or requirement relating to any one or combination of components illustrated in . The invention is operational with numerous other general purpose or special purpose computing environments or configurations. Examples of well known computing systems environments and configurations suitable for use with the invention include but are not limited to personal computers servers hand held or laptop devices multiprocessor systems microprocessor based systems set top boxes programmable consumer electronics network PCs minicomputers mainframe computers and distributed computing environments that include any of the above systems or devices. In its most basic configuration computing device typically includes at least one processing unit and memory . The memory may be volatile such as RAM non volatile such as ROM flash memory etc. or some combination of the two. This most basic configuration is illustrated in by the dashed line . The computing device may have additional features and functionality. For example computing device may include additional storage removable and non removable including but not limited to magnetic and optical disks and tape. Such additional storage is illustrated in by removable storage and non removable storage . Computer storage media include volatile and non volatile removable and non removable media implemented in any method or technology for storage of information such as computer readable instructions data structures program modules or other data. Memory removable storage and non removable storage are all examples of computer storage media. Computer storage media include but are not limited to RAM ROM EEPROM flash memory other memory technology CD ROM digital versatile disks DVD other optical storage magnetic cassettes magnetic tape magnetic disk storage other magnetic storage devices and any other media which can be used to store the desired information and which can accessed by device . Any such computer storage media may be part of device . Device may also contain communications connections that allow the device to communicate with other devices. Communications connections are examples of communications media. Communications media typically embody computer readable instructions data structures program modules or other data in a modulated data signal such as a carrier wave or other transport mechanism and include any information delivery media. The term modulated data signal means a signal that has one or more of its characteristics set or changed in such a manner as to encode information in the signal. By way of example and not limitation communications media include wired media such as wired networks including the LAN of and direct wired connections and wireless media such as acoustic RF infrared and other wireless media. The term computer readable media as used herein includes both storage media and communications media. The computing device may also have input devices such as a keyboard mouse pen voice input device touch input device etc. Output devices such as a display speakers printer etc. may also be included. All these devices are well know in the art and need not be discussed at length here.

The services of the present invention are presented to applications by means of an Application Programming Interface API . The API can be used with all processes local and remote and is transparent with respect to the location of a process. The API returns sensible values if a request fails because of a network problem and does not falter if remote devices are unavailable. If a process uses the API then the process is called a WINDOWS Test Technologies WTT based process. The name WTT is of only historical interest and the invention is not limited to use in the testing field or to use with Microsoft s WINDOWS operating systems. The invention works with any combination of WTT based and non WTT based processes although some enhanced services are available only to WTT based processes. For purposes of this discussion the services provided by the API are roughly divided into four major categories of communications tasks creating processes monitoring processes waiting for processes and sending signals to processes especially termination signals.

Using the API applications can create new processes and run them either on the local computing device or on a remote device. Each process is tagged by a Universally Unique Identifier UUID that uniquely identifies the process no matter the computing device on which it resides. In addition a parent UUID and a group UUID may be assigned to the process and used for enforcing dependencies e.g. for signaling the process and all of its child processes and for managing arbitrary user defined groups respectively. The process table stores information about processes created on the computing device whether the process runs locally on the device or runs remotely. The process table is created as a memory mapped file and is visible to all processes on the device. A global event is associated with each process created via the API and is used for process control and signaling.

Because a process table is accessible to all processes on the computing device mechanisms exist for coordinating access to the table. One mechanism involves software locks both for the entire table and for each individual row. For example a process updating its heartbeat time can lock access to its row while it writes the current time into the Heartbeat Time field. When a process is created or deleted the entire process table is locked so that a row can be added or deleted without interference.

At frequent intervals for each process a monitor thread logs heartbeat entries in the Heartbeat Time field in the local process table. Each thread in a process updates a local heartbeat and the monitor thread keeps track of these local heartbeats updating the heartbeat field in the local process table if all the threads are updating their local heartbeats. If any thread deadlocks and stops updating its local heartbeat the monitor thread detects this logs the fact and either breaks into the debugger or marks the process as requiring assistance. When an application wants to monitor the heartbeat of a process the application begins by looking up the entry for the process in the process table on the computing device on which the application is running. The application reads the Target Device field to see where the process is running. Then if the target device is the local device the application reads the Heartbeat Time field in the local process table. Otherwise the target device is distinct from the local device and the application sends a request to the spsrv service running on the target device asking it to send the value of the Heartbeat Time of the process. For example if Process in wants to know whether Process is still running normally that is to say is still logging heartbeats Process would consult Process Table on its local computing device . Reading the entry for Process Process discovers that Process is running remotely on computing device . See . Process formulates a request and sends it to the computing device . That device reads its process table and reports to Process that the Heartbeat Time field of Process currently reads 14 24 56 . Process compares that heartbeat time adjusted if necessary for time zone differences to its local clock and decides whether Process is running or has broken into the debugger.

In addition to its heartbeat a process may log other information including the number of its threads the current status of the threads console output log file output etc. An application wishing to monitor this output can use the same techniques described above with respect to heartbeats. The application can also obtain ongoing status information by requesting that a copy of new information written by the process be sent to the application as it is written. Using parent and group UUIDs an application can monitor all of the processes in a dependency list or in a user defined process group.

A process may wait for other processes to achieve a specified status for example to complete their initialization or to terminate. The API provides a function that waits until the processes achieve the status or until a timeout period elapses. The function checks the heartbeat of all WTT based processes and if a process is not logging heartbeats then the process may be assumed to have broken into the debugger. Using the processes in as an example assume that Process calls the API function to wait for Processes and to complete their initialization. Because Processes and run on remote computing devices the API function sends a wait request to those remote devices. Each device waits on the processes local to it and then reports the results to Process . For each process in the wait list the returned status may be Completed Initialization Still Initializing or Heartbeat Stopped. Using UUIDs in the same manner as in process monitoring a process can wait for all of the processes in a dependency list or in a user defined process group. Note that because non WTT based processes do not update their Heartbeat Time field it cannot be assumed that these processes broke into the debugger.

When a job is divided into discrete processes the processes often need to communicate among themselves to coordinate the tasks they perform. The API provides a generally useful signaling mechanism for this purpose in the form of Global Events. As an example one particular event is the Controlled Shutdown. When a WTT based process receives this event it releases the resources it is using reports its status and performs a controlled shutdown. Users may define other Global Events and assign meanings to them. When a process receives an event it responds in a fashion appropriate to the event s meaning. However if a process receives an event it does not understand it may terminate in an uncontrolled fashion. A process may use parent and group UUIDs to send an event to groups of processes.

The services provided by the invention as described in the previous section are presented again in this section but with more attention paid to the details of an exemplary API. In its specific details this embodiment is oriented towards use with Microsoft s WINDOWS operating system but the principles are applicable to other environments. This section begins by describing the fundamental data structures used in this embodiment.

The variable types TCHAR and Tstring are used in the definitions below to provide source code compatibility between Unicode and non Unicode machines. If the parameter  UNICODE is defined during the build then TCHAR is defined to be the Unicode s basic wide character type wchar t otherwise it becomes the standard ASCII 8 bit signed char. Similarly Tstring is a string of TCHARs and becomes either the Unicode wide string wstring or ASCII string. 

By associating a group GUID with a set of processes processes can communicate with all the processes in the set. This is similar to a process group in Windows NT or Unix.

Defines information relating to a process. WTTGetProcessListInfo returns this information. A pointer to this structure is passed as an input parameter to WTTOpenProcess. An application receives a handle to a process by calling WTTOpenProcess and can use that handle to monitor the process even if the process was not created by the application.

Holds information about a thread including the Thread Identifier and a list of comments. Comments may be pushed onto the stack and the most recent comment may be popped off the stack and examined.

This structure is opaque to the user and is used as a handle for future operations. This process specific handle may be replaced by WTTHANDLE.

This data structure is opaque to the user and is used as a handle for future operations. This handle is capable of handling objects no matter their type whether processes events mutexes etc. For WINDOWS implementations this handle is similar to the handles used by Win32 processes.

Having presented the data structures used in this implementation the following describes the function calls provided by the API.

Create a process whether WTT based or not. The user s input parameters are passed in as part of the WTTPROCESSPARAM structure. The returned structure pointer pHWTTProcess is opaque and is used in future calls. If UserName and Password are specified as part of the input structure then the process is created with the logon credentials of the specified user.

The call is basically asynchronous in nature and returns as soon as possible after the process is successfully created or with a meaningful error value explaining why the process creation failed.

Points to a structure of type WTTPROCESSPARAM which contains the input parameters. Some of the fields in this structure are appropriately updated to store output values. For example if the passed in GUID is NIL see Note on UUIDs below then the newly created GUID is stored when the function returns.

The following flags are supported in the WTTPROCESSPARAM structure s dwCreateProcessFlags field CREATE NEW CONSOLE CREATE NEW PROCESS and DETACHED PROCESS.

ERROR SUCCESS if the process is successfully created else Win32 error. In the latter case the returned handle is NOT valid.

This function assigns a GUID to the process that uniquely identifies the process no matter the device on which it runs. Then the function locks access to the process table and finds an empty slot in the table. Assigning the slot to the new process this function stores in the slot the initial data for the process including its GUID Parent GUID Group GUID etc. The parent of the process updates the heartbeat field and writes a zero value into the HB field. This makes it possible for the WTTWaitForMultipleObjects function to detect a DEBUG BREAK that occurs before the creation of the Global Event.

If the process is to run on a remote device then the parameters of the call are marshaled over the network and sent to the remote target device. The process is then created locally on the target device.

Once the new process starts its status in the process table the dwProcStatus field is automatically updated.

Send a signal to the processes in a set. The set may include both WTT based and non WTT based processes. The global event handle is set for each process. One currently defined signal is terminate the process. On receipt of that signal a process cleans up after itself and performs a controlled stop. Sending a terminate signal is similar to sending a kill signal.

The set of processes to signal. This is an array of WTTHANDLEs for WTTProcesses as returned by the WTTCreateProcess and WTTOpenProcess functions.

Attempt a controlled stop by signaling the event associated with the process. It is the responsibility of non WTT based processes to check the global event.

This terminates all processes in a process tree. For every process in the process tree internal process APIs are recursively used to terminate the children. The process table is searched to find all the descendents so that they can be signaled.

For non WTT based processes the standard global event handle is signaled. If a non WTT based process does not clean up within an acceptable period of time after being sent a WTT SIGNAL PROCESS signal then the calling process can send a WTT TERMINATE PROCESS signal.

Wait for processes in a set to achieve a specified status but stop waiting if a timeout period expires. The function checks the heartbeats of all WTT based processes and if a process is not logging heartbeats then it is assumed to have broken into the debugger. This function is often used to wait for processes to terminate. In that case the different possible scenarios on returning from this function are as follows 

A debug break cannot be declared for a non WTT based process because this type of process does not log heartbeats.

TRUE means wait for all processes in the set. FALSE means wait for the first process to achieve the specified status.

The function timeout period. The function waits no longer than this before returning. If a process does not achieve the specified status e.g. terminated during this period of time its status is returned as WAIT TIMEOUT.

If a process has not logged a heartbeat during this period then the process is declared to have broken into the debugger. The value of this parameter may be smaller than the value of dwTimeoutInSeconds. A value of INFINITE is also possible which effectively ignores heartbeats.

If fWaitAll is TRUE then the value of this parameter should be the maximum of the debug timeout values of all the processes in the monitored set.

The type of status to wait for. These values cannot be combined. Many more statuses are possible the following are currently implemented 

The address to receive the first failure status of the array or NULL if this information is not desired . This field is meaningful only if the return value is ERROR SUCCESS and if fWaitAll is FALSE.

The address to receive the index corresponding to the summary status or NULL if this information is not desired .

WAIT TIMEOUT if the timeout expires before all the processes achieve the specified status. In this case pdwSummaryIndex and pdwSummaryStatus are undefined.

WTT ERROR DEBUG BREAK if a process breaks into the debugger. pdwSummaryStatus contains WTT ERROR DEBUG BREAK and the index of that process in the phWTTProcess array is returned in pdwSummaryIndex. There could be several processes in such a state in which case pdwSummaryIndex points to the first one.

When processes in the set run on a distributed set of computing devices there may be one thread per process or one per computing device which the overall thread monitors.

For non WTT based processes dwLastHBUpdateTime is the time the process was created and is not updated. No debug break can be declared for these processes.

Query the status of a process that was launched by the WTTCreateProcess function. After reviewing the information returned WTTFreeProcessInfo is called to release the memory allocated by this function.

Process information is stored in a WTTHANDLE structure. The handle could have been obtained either by a call to WTTCreateProcess or by a call to WTTOpenProcess after a call to WTTGetProcessListInfo .

Additionally this could have a value of NULL. In that case the information returned pertains to the process that called this function. This is useful when a non WTT based process wishes to get GUID information about itself which it can then use to open a handle to the Global Event.

This stores information about the process being queried. The information includes the threads present the stack of thread comments for each thread a list of log files that this process monitors and a list of variations completed by the process.

The data returned are stored in the form of simple link lists or stacks. Small routines are provided to return the size traverse and list the contents of the lists or stacks.

For non WTT based process a list of thread identifiers the module name the type of the process and the current state of the process are returned. The current state of the process may not be very accurate because non WTT based processes do not log heartbeats.

The macro GET PROC STATUS pWTTProcessinfo dwProcStatus returns a string corresponding to the process status.

Release the memory allocated within the WTTPROCESSINFO structure during a WTTGetProcessInfo function call.

Pointer to a pointer to a structure containing information about a process returned by a call to WTTGetProcessInfo.

ERROR SUCCESS if the allocated memory is successfully released else Win32 error. The pointer to the WTTPROCESSINFO structure is not defined after a call to this function.

Get the process list from the target machine s process table. The information returned varies depending upon the values specified in dwFlags. Memory allocation is done within the function call itself. WTTFreeProcessListInfo is called to release the memory after reviewing the information returned.

TRUE means remote entries should be resolved. In that case extra heartbeat related information is retrieved for processes initiated by WTTCreateProcess on the computing device specified by pszMachine. A query is made to that remote device.

During the marshaling of parameters to a remote device pszMachine is marshaled into the szTargetMachine field of the buffer.

This function needs to carefully check to see if a process actually exists. If the entry for a particular process is present in the .ini file but not present in the process table then the process no longer exists. There is a problem however because there may be entries in the process table for processes that have exited. This happens only if a WTT based process is killed with a forced kill signal. Even doing an OpenProcess on the process identifier PID is not a foolproof check as the PID could have been recycled. The solution is to use the Phandle pointer in the process table on the local machine where the process was instantiated to wait on the Process Handle with a timeout of zero. If the process is gone then Phandle is signaled immediately.

When returning the list of process information allocate space for one more than the total number of entries returned. The last entry is a NULL NIL for GUIDs and ZERO for DWORDS.

Retrieve a copy of output as it is added to a log file. The effect is that of a distributed tail f command. A callback allows this function to return asynchronously.

This structure contains the log information. It includes the UNC path of the log file. If this pointer is NULL then the first log file is used as specified in the .ini file.

The number of bytes to be retrieved. If this is set to the value WTTPROCESS FULL LOGSIZE then entire log files are retrieved.

Register a callback function with the spsrv service to retrieve data the tail of the log file asynchronously.

This structure contains the log information. It includes the UNC path of the log file. If this pointer is NULL then cancel all tail logs for the process identified by the pWTTProcInfo parameter.

A pointer to the element in the array retrieved by WTTGetProcessListInfo that concerns the process of interest.

The handle has information like the GUID of the process the name of the device on which the process runs etc. Once the handle is received it is more efficient to store its information in a local process table and to then call WTTCloseHandle to release the memory.

Close a WTT process handle. This releases the memory allocated by the WTTOpenProcess call. The local process table entry created for the process is marked as invalid.

The functions WTTTailLog and WTTConsoleOutput use callback functions to allow them to return asynchronously. The structure of the callback function is as follows 

UUIDs also called GUIDs provide unique designations of objects such as processes interfaces manager entry point vectors and client objects. In practice these identifiers need only be unique within the context of their use that is within the set of communicating computing devices. Because techniques already exist for making the identifiers truly unique those techniques are used here.

An array of eight elements. The first two elements of the array contain the third group of four hexadecimal digits of the UUID. The remaining six elements contain the final twelve hexadecimal digits of the UUID.

For implementations based on Microsoft s WINDOWS operating systems the following standard Win32 functions are used to create compare and manipulate UUIDs. Other implementation platforms provide similar functions.

A suitable infrastructure is provided for tagging and monitoring non WTT based processes. Every non WTT based process created by the WTTCreateProcess function is given a WTT created GUID for tagging. The GUID is stored in the WTT based process handle for future tracking purposes.

A Global Event handle is present for every non WTT based process. The naming structure of this handle is Event and it is present on the device on which the process is created. When a non WTT based process is created it has the option of waiting on this event handle and performing a clean shutdown if requested.

Central to the implementation of this API is the process table. The process table has row level exclusive locks and a global process table lock that over rides the row level locks.

Considering all these a global lock mutex is needed whenever a write affects the entire process table as in cases a b and f above. A row level exclusive lock is needed after acquiring the global process table when updating process specific information as in cases c d and e above.

While the invention is useful when all processes run on the same computing device it is also designed for the case when some processes run remotely. This section discusses specific considerations that come into play when the API supports remote processes.

PWTTPROCESSINFO contains a field called szDestMachine that holds the value of the target device on which the process runs. If the value is NULL then the call is local. If not the command and its parameters are sent to the target device and the results are piped back to the originating device. All calls are synchronous in nature. So if the target device crashes during the period of passing the command an appropriate error is returned.

The need to pass by value argues for using Remote Procedure Calls RPC as a message passing paradigm. On the other hand if all input parameters to a call are based on parameters passed only by value then interfaces function tables for the call can be set up and the spsrv service used to handle the commands on the remote device. Another consideration is that if 32 bit based machines communicate with IA64 cluster machines then RPC is very useful as it takes care of architectural differences. RPC interfaces are flexible in terms of marshaling both pointer based and value based parameters.

Every time a new API call is made a new GUID may be generated on the device that initiated the call. This GUID is used to track the call. The GUID is sent with the call to the target device. The target device keeps track of the GUID. If the target device crashes then the target device after re booting calls back its parent device with the knowledge of the GUID of the last call and the name or IP address of the parent device.

For every process created on a particular device a .ini file is created in the windir WTTbin GUID directory. For non WINDOWS implementations a similar directory is used. This directory stores information about the process its threads and its stack comments. The files store information more persistently than can memory and prevent having to use memory for ever changing bulky data. A process is free to update the information in its file whenever the thread comments are updated. If a query about the state of a process is made and if the process no longer has an entry in the process table but a .ini file exists then the status of the process is updated to ERROR SERVICE NOT ACTIVE. Due to the presence of multiple threads possibly operating simultaneously on this file synchronization is important. A cleanup routine removes .ini files three or more days old. This is the structure of a .ini file 

For marshaling parameters for a function call the spsrv service has a function table that is used to form the receive and send stubs for the spsrv service running on the remote device. To form the stub for receiving data the buffer is as generic and as flexible as possible. It identifies the function determines the number of parameters and sets a fixed order of parameters depending on the function. The following structure is used. It is marshaled into a byte buffer sent out the socket and un marshaled on the other end. When the call completes the same procedure gets the returned value of the call.

The output buffer for most calls contains the following information information in HWTTPROCESS marshaled as  M HWTTPROCESS dwSummaryStatus and dwSummaryIndex. Variable length data are put at the end of the buffer. For WTTGetProcessListInfo a list is formed of entries containing information about the processes of interest. The information carried back is as follows a list of threads present including their thread identifiers a list of comments on a per thread basis and a list of variations completed by the process. The data structures useful for marshaling this data are as follows 

In view of the many possible embodiments to which the principles of this invention may be applied it should be recognized that the embodiments described herein with respect to the drawing figures are meant to be illustrative only and should not be taken as limiting the scope of invention. Therefore the invention as described herein contemplates all such embodiments as may come within the scope of the following claims and equivalents thereof.

