---

title: Host based satellite positioning systems
abstract: Methods and systems consistent with the present invention provide a host based positioning system. The host based positioning system includes a tracker hardware interface that connects to a dedicated hardware space vehicle tracker. The tracker hardware interface receives positioning information from the space vehicle tracker. The host based positioning system also includes a memory that includes a GPS library having a user interface, a tracker interface, and an operating system interface. A processor runs functions provided by the interfaces.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07792639&OS=07792639&RS=07792639
owner: SiRF Technology Inc.
number: 07792639
owner_city: San Jose
owner_country: US
publication_date: 20050606
---
This application is a continuation of U.S. patent application Ser. No. 10 269 914 entitled HOST BASED SATELLITE POSITIONING SYSTEMS filed on Oct. 10 2002 that issued as U.S. Pat. No. 7 043 363 on May 9 2006 which was related to U.S. patent application Ser. No. 10 269 105 titled LAYERED HOST BASED SATELLITE POSITIONING SOLUTIONS filed on Oct. 10 2002 and U.S. patent application Ser. No. 10 269 104 titled NAVIGATION PROCESSING IN HOST BASED SATELLITE POSITIONING SOLUTIONS filed Oct. 10 2002 both of which were incorporated by reference in their entirety and which are also incorporated by reference herein.

This invention relates to satellite positioning systems. In particular this invention relates to satellite positioning systems implemented utilizing the processing power of a host in communication with a hardware tracker.

The worldwide utilization of wireless devices such as two way radios pagers portable televisions personal communication system PCS personal digital assistants PDAs cellular telephones also known a mobile phones Bluetooth satellite radio receivers and Satellite Positioning Systems SPS such as Global Positioning Systems GPS also known as NAVSTAR is growing at a rapid pace. Current trends are calling for the incorporation of SPS services into a broad range of electronic devices and systems including Personal Digital Assistants PDAs cellular telephones portable computers automobiles and the like. At the same time manufacturers constantly strive to reduce costs and produce the most cost attractive product possible for consumers.

In the past providing a SPS solution often involved expensive dedicated SPS signal reception and processing hardware as well as dedicated post processing hardware for resolving location measurements displaying location coordinates updating map displays and the like. However given the rapid growth in speed sophistication and processing power of the host microprocessors present in the host device e.g. in a cellular telephone or automobile the possibility exists for allowing the host microprocessor to bear the burden not only of running its regular applications but also to operate as part of the SPS solution. Such an approach is presented in U.S. Pat. No. 6 430 503 titled Distributed GPS Navigation System issued to Paul W. McBurney et al. the entirety of which is incorporated herein by reference.

As noted above however there is a strong push toward incorporating SPS solutions in many electronic devices designed by numerous manufacturers. Of course each device varies considerably in architecture operating system hardware interfaces and the like. Prior SPS solutions did not provide the flexibility that allowed the solutions to be adapted to a wide range of electronic devices. Instead expensive customized solutions were needed for each device thereby undesirably increasing costs and delaying the introduction of SPS services into a wide range of devices.

Therefore a need exists for implementations of SPS solutions that overcome the problems noted above and others previously experienced.

Methods and systems consistent with an invention of a host based SPS solution are disclosed. The SPS solution is implemented in a convenient library form that is flexible and extensible and that may adapt to meet the needs of many different hardware platforms. As a result a wide variety of electronic devices may incorporate SPS functionality with less expense utilizing less development time.

In one example implementation a host based SPS system may include a host processing system that connects through a tracker hardware interface to a dedicated hardware space vehicle tracker. The host processing system may also include a memory that includes a SPS library having a user interface positioning engine a tracker interface and an operating system interface. A processor in the host processing system runs the positioning engine and the functions provided by the interfaces.

The tracker hardware interface receives positioning information from the space vehicle tracker. Through functions in the tracker interface the positioning information is communicated to the positioning engine. In turn the positioning engine may determine a position and communicate the position to a user application through functions provided in the user interface.

Other apparatus systems methods features and advantages of the present invention will be or will become apparent to one with skill in the art upon examination of the following figures and detailed description. It is intended that all such additional systems methods features and advantages be included within this description be within the scope of the present invention and be protected by the accompanying claims.

Reference will now be made in detail to an implementation in accordance with methods systems and products consistent with the present invention as illustrated in the accompanying drawings. The same reference numbers may be used throughout the drawings and the following description to refer to the same or like parts.

A typical satellite positioning system SPS system has approximately 12 satellites that may be visible at any one time to a wireless device. SPS means any system utilizing satellites and or land based communications devices for providing or enabling the determination of a location of the wireless device on the earth for example but not limited to the global positioning system GPS known as NAVSTAR GLONASS LORAN Shoran Decca or TACAN. Although many of the interface functions below make reference to GPS those functions are not limited to use with GPS but generally are equally applicable in other SPS environments.

An operating system e.g. Windows CE QNX Palm OS UNIX Linux Windows 2000 NT XP or the like runs in the memory . As will be explained in more detail below a user program communicates with a SPS library and the operating system . The user program thereby receives position information from the GPS library and may also communicate commands to the SPS library. The user program may be any program that utilizes positioning information including as examples a mapping program course charter location aid and the like.

The host connects through the hardware tracker interface and the interface connection to the tracker hardware . The hardware tracker interface may be virtually any type of data transfer interface as examples a serial parallel compact flash PC Card or network interface . The interface connection may then be as examples a serial cable parallel cable or network cable and may optionally be wireless. In one implementation the hardware tracker interface is an RS232 port running at 38 400 bps N 8 1 that communicates up to 2 KB of data per second between the host and the tracker hardware .

In other implementations the tracker hardware as illustrated by the reference numeral is more closely incorporated into the host . Thus rather than connecting to the host through the interface connection for example the tracker hardware may be directly coupled to the host address data and control buses. As will be explained in more detail below the host receives and processes navigation information from the hardware tracker in order to provide the user programs with position information.

Although aspects of the present invention are depicted as being stored in memory one skilled in the art will appreciate that all or part of systems and methods consistent with the present invention may be stored on or read from other machine readable media for example secondary storage devices such as hard disks floppy disks and CD ROMs a signal received from a network or other forms of ROM or RAM either currently known or later developed. Further although specific components of positioning system are described one skilled in the art will appreciate that a positioning system suitable for use with methods systems and articles of manufacture consistent with the present invention may contain additional or different components. For example the CPU may be a microprocessor microcontroller application specific integrated circuit ASIC discrete or a combination of other types of circuits acting as a central processing unit. The memory may be RAM DRAM SDRAM or any other type of read writeable memory.

Turning next to that figure shows one example of an implementation of the tracker hardware . The tracker hardware acquires and tracks SPS satellites and sends raw measurement data to the host for position calculation. To that end the tracker hardware includes an antenna for receiving SPS satellite signals and a radio frequency RF filter for passing the signals to the RF interface circuit . The RF interface circuit processes the signals produces 2 bit Inphase and Quadrature I Q signals and recovers SPS clocks. The RF interface circuit provides the I Q signals and SPS clocks to the location processing circuit for digital processing. A reference frequency source e.g. a crystal oscillator provides a reference clock for the RF interface circuit while the optional real time clock RTC source provides a reference clock for the location processing circuit .

The tracker hardware may be implemented with components available from SiRF Technology Inc. of San Jose Calif. For example the RF interface circuit may be implemented as a GRF2i LP integrated circuit. The location processing circuit may be implemented as examples as a GSP2t integrated circuit or GSP2e integrated circuit. The tracker hardware minimizes the overhead on the host and operating system by keeping low the maximum transmission rate of raw measurements to the host e.g. one measurement per second .

With regard next to that figure shows a detailed block diagram of a hardware and software diagram for the positioning system . The memory in the host includes a SPS library user programs e.g. map displaying map matching dead reckoning and route calculation programs and the operating system which may be a multi threaded operating system . The SPS library includes a positioning engine a user interface a tracker interface and an operating system interface . The user tasks implement device drivers or link directly to the user programs as examples.

In addition to the hardware tracker persistent storage and a real time clock may optionally be provided. The persistent storage may be as examples 2 KB of Flash memory battery backed up RAM or a disk drive. The SPS library may use the RTC in the host the RTC or may operate without an RTC.

The user interface is called by the user programs to start and configure the positioning system. The positioning engine calls a function provide by the user program e.g. GPS Output to deliver positioning messages e.g. position updates and other synchronous and asynchronous data to the user program . The tracker interface provides for communication between the tracker hardware and the host and to that end may load and call the operating system serial communication drivers. The operating system interface calls operating system functions for task scheduling and synchronization RTC access and storage access.

When information is received the user program processes the information for example to display or update a map step . If the program continues to run step processing returns to step . Otherwise the program stops the positioning engine step and terminates. The positioning engine runs separately and when new positioning information is available creates a message for the program step and sends the message to the program step . Tables 1 5 below show exemplary function calls.

Below one exemplary implementation of the user interface tracker interface and an operating system interface is set forth. Table 6 shows which functions and messages are associated with each interface while Tables 7 10 set forth files and data types used or referred to in the follow description.

The user or GPS interface includes a GPS control interface and a GPS communication interface. The GPS control Interface functions allow a user program to start and stop the GPS engine using the functions shown in Table 11.

The GPS communication interface functions allow a user program to send and receive messages to and from the GPS engine using the functions shown in Table 12.

GPS Start initializes and starts positioning engine threads and communication interface. This function should be called by user programs to start GPS activity.

The GPS Stop function stops the positioning engine threads and communication interface. This function should be called by the user program to stop GPS activity.

The GPS Output function retrieves a message from positioning engine. There are no return values. The function is called by the positioning engine whenever any message is sent out. This function is implemented by the user program and statically linked with the GPS library.

The GPS Input function sends a command to the GPS engine. The function may be called by the client program to send a command to the GPS receiver.

The GPS communication interface messages are exchanged between the GPS client e.g. a user program and positioning or GPS engine via the user interface input and output functions.

The GPS NAV MEASURED NAVIGATION output message provides ECEF position velocity GPS time and position status information. The message is outputted periodically at 1 Hz rate.

The GPS NAV MEASURED TRACKER output message provides satellite status azimuth elevation and C No information. The message is outputted periodically at 1 Hz rate.

The GPS NAV SW VERSION output message provides a positioning engine software version string. Message is sent as a reply to the GPS NAV POLL SW VERSION input message.

The GPS NAV CLOCK STATUS output message provides current GPS clock status information. Message is outputted periodically at 1 Hz rate or on demand as a reply to GPS NAV POLL CLOCK STATUS input message.

The GPS ADC ODOMETER DATA output message provides ADC odometer and GPIO lines state from tracker. Message is outputted periodically at 1 or 10 Hz rate depending on setting used in GPS Start function.

In one implementation the Voltage formula is Uin V Vref adcX avg 8192 16384 where Vref 2.55V and adcX avg is a measurement value from message above. The analog to digital converter may for example take measurements at 50 Hz rate and the reported value adcX avg may be an average of the last 5 samples.

The GPS NAV COMPLETE output message is sent at the end of the navigation cycle to confirm that the GPS engine has finished a position computation cycle with or without success . In one implementation this message is outputted at 1 Hz rate.

The GPS NAV INITIALIZE input message performs GPS engine re initialization. Message should be used to perform factory cold warm or hot restart.

In one implementation the navigation engine will initiate restart within one second and a default clock offset value is 96250 Hz. When the actual clock offset is unknown a value of 96250 Hz should be used. However if the real clock offset is far from a specified value a longer TTFF will be observed.

The software version string may be returned for example in a GPS NAV SW VERSION output message via GPS Output function.

The GPS NAV POLL CLOCK STATUS input message asks for the current GPS clock status of the GPS library.

The clock status data may be returned in GPS NAV CLOCK STATUS output message via GPS Output function.

The Operating System Interface functions are operating system dependent and are implemented in the open source format available from SiRF Technology Inc. The functions include Thread mutex and semaphore functions. Permanent storage and RTC functions may be available depending on hardware availability.

The OS Thread Create function uses an appropriate operating system service to create a thread. The function is called by the GPS engine at the startup to create all desired threads.

The OS Thread Delete function uses appropriate OS service to stop a thread and or to wait for thread to gracefully stop. Function is called by the GPS engine from GPS Stop to stop all SiRFNav threads.

The OS Thread Sleep function uses appropriate OS service to suspend a thread for a given number of milliseconds. Function is called by the GPS engine to suspend current thread temporarily.

The OS Mutex Create function uses an operating system service to create a Mutex mutually exclusive object or OS specific equivalent such as a software critical section. This function is called by the GPS engine at the startup to create all desired mutexes.

The OS Mutex Delete function uses an operating system service to delete a Mutex object. The function is called by the GPS engine at the stopping procedure to delete all used mutexes.

The OS Mutex Enter function uses an operating system service to obtain a Mutex object. This function is called by the GPS engine just before entering into a critical section.

The OS Mutex Exit function uses appropriate OS service to release a Mutex object. Function is called by the GPS engine just after leaving from a critical section.

The OS Semaphore Create function uses an operating system service to create a Semaphore object. The function is called by the GPS engine at the startup to create all desired semaphores.

The OS Semaphore Delete function uses an operating system service to delete a Semaphore object. The function is called by the GPS engine at the stopping procedure to delete all used semaphores.

The OS Semaphore Wait function uses an operating system service to wait for Semaphore object. Function is called by the GPS threads to wait for events.

The OS Semaphore Release function uses appropriate OS service to release a Semaphore object. The function is called by the GPS engine to schedule other thread.

The OS Storage Open function uses an operating system or BIOS service to open a non volatile storage system. The function is called by the GPS engine at the startup to open a storage.

The OS Storage Close function uses appropriate OS or BIOS service to close a non volatile storage system. The function is called by the GPS engine at the shut down procedure to close a storage.

The OS Storage Write function uses appropriate OS or BIOS service to write given words to a non volatile storage system battery backed RAM file system etc. . The function is called by the GPS engine periodically for example every 30 seconds to save time position and ephemeris information. That information is used later to speed up the GPS start procedure e.g. for hot or warm starts .

The OS Storage WriteAll function uses an operating system or BIOS service to write a GPS data structure to a nonvolatile storage system. The function is called by the GPS engine periodically for example every 30 seconds to save time position and ephemeris information. That information is used later to speed up the GPS start procedure hot or warm starts 

The OS Storage Read function uses an operating system or BIOS service to read GPS data structure from a nonvolatile storage system. The function is called by the GPS engine at the startup to retrieve time position and ephemeris information. This information is used to speed up the GPS start procedure e.g. for hot or warm starts .

The OS RTC Read function uses an operating system or BIOS service to read a real time clock information from the host s RTC. The function is called periodically by the GPS engine.

The tracker communication interface functions allow messages to be sent and received between the tracker hardware and the user programs and position library.

The GPS COMM TRK Create function uses an OS or BIOS service to create a tracker communication handle. The function is called by the GPS engine at the startup to create a communication handle.

The GPS COMM TRK Delete function uses an OS or BIOS service to delete a tracker communication handle. The function is called by the GPS engine at the stopping procedure to delete a communication handler.

The GPS COMM TRK Open function uses an OS or BIOS service to open and configure a tracker communication port. The function is called by the GPS engine at the startup.

The GPS COMM TRK Reopen function uses an OS or BIOS service to re open a tracker communication port. The function is called by the GPS engine after coming back from a power suspend mode. When power suspend mode is not required then the function may return GPS SUCCESS only.

The GPS COMM TRK Close function uses an OS or BIOS service to close a tracker communication port. The function is called by the GPS engine at the stopping procedure to close the port.

The GPS COMM TRK Wait function uses an OS or BIOS services to wait for data from a tracker communication port. The function is called by the GPS engine to wait for the tracker data.

The GPS COMM TRK Read function uses appropriate OS or BIOS services to read data from a tracker communication port. The function is called by the GPS engine to read tracker data.

The GPS COMM TRK Write function uses appropriate OS or BIOS services to write data to the tracker communication port. The function is called by the GPS engine to send commands to the tracker hardware.

Turning next to that figure shows a block diagram of the cooperation between threads tasks and hardware in one implementation of a host based GPS solution. In particular the tracker hardware communicates through a serial driver for example the Windows CE serial driver . The serial driver communicates and cooperates with a file system for example the Windows CE file system which includes input buffers and output buffers for the communications that will occur.

The receive manager and navigation thread removes messages destined for the GPS library from the positioning engine queue and also places messages destined for the user programs on the user interface queue . The messages for the GPS library are processed by the tasks including the NavPeriodicTask . A set of shared buffers control flags completion flags and the like are maintained by the GPS library. Finally it is noted that the COM interface provides a set of control functions .

Turning next to that figure illustrates one execution schedule for the receive manager thread and the NavPeriodicTask . In the schedule the NavPeriodicTask runs as a low priority background thread while the receiver manager and navigation thread run in one normal priority thread.

With regard to that figure shows a synchronization diagram . The synchronization diagram illustrates the timing and interaction between the threads and tasks shown in .

With reference to receive manager RxM and navigation Nav run sequentially in one loop that waits for new data from Tracker Interface TRK IF Receiver before each iteration. Either RxM or Nav may signals NavPeriodicTask to proceed with one iteration of its loop unless NavPeriodicTask already performing its task in which case it will finish the task and skip one loop .

The RxM and Nav thread may wait on a Critical Section when writing data to the UI Queue or when sending data to Tracker . There will typically be a thread running while RxM Nav are waiting. In one implementation NavPeriodicTasks runs at smaller priority than the other tasks and it will not run as long as any other thread is running. In an alternative implementation NavPeriodicTasks runs at normal priority but does not present a conflict as long as RxM Nav have sufficient priority to consume data generated by NavPeriodicTasks .

The RxM and Nav thread runs the RxM control task that maintains a state machine for the Rx and manages the state machine transitions based on current state. The RxM communicates with the tracker hardware through the tracker interface. It both sends data and commands to the tracker hardware to pace it through initial acquisition and tracking of SPS satellites and receives data and status messages from the receiver with raw SPS satellite tracking data. The primary purpose of the RxM task is to manage and control the operation of the tracker hardware . It also preprocesses the raw tracker data and submits the processed data to the Navigation Processing Task. The RxM gets scheduled or called by the Nav Task once the tracker hardware starts tracking.

The NavPeriodicTasks thread is a pseudo task that performs miscellaneous support operations for the RxM and Nav tasks. Its functions include determining and performing updates to the satellite state tables and generating new visible SPS satellite list when new ephemeris data is collected or whenever it is requested.

The Nav Processor Thread performs position velocity and time computations based on the RxM generated individual SPS satellite data. This makes use of the functionality offered through the navigation library in optimally computing the navigation position data. The computed navigation data is made available to the Data Forwarding thread. At the beginning of each iteration the Nav Processor calls or schedules the RxM task to run and then it performs navigation computations and generates the user position velocity and time data. Based on the computation results if pre selected error thresholds are exceeded the Nav Processor may send commands to the receiver either directly or through the RxM to force the receiver to reset.

The I O Reader thread and Tracker Interface Receiver sends data to queues as shown in . In addition data length error checks may be performed with error counts logged in a global variable. Erroneous message bytes will be reported to the user program through debug messages.

Note that in some implementations the I O Writer thread is not used. Instead its role may been taken by TRK IF whose methods are invoked from the RxM Nav thread and SendPassThruDataToTracker . TRK IF writes directly to the serial port. All I O functions will be grouped into one class . In WinCE buffering is performed on the File System level which allows TRK IF to return quickly upon sending data. On Nucleus additional buffering may be provided.

The DataForwarderThread reads from the UI Queue and calls the user program s ICallBack interface for each binary message to be sent. If the UI queue s Semaphore is still signaled after Callback returns the DataForwarderThread may continue piping data until the UI queue is empty. In one implementation the UI Queue is not locked while Callback is being executed which allows other threads to run while waiting for Callback to return. Client Callback typically puts data in internal storage for another thread to use. Generally one Callback is called at a time. The UI Queue is prioritized and it will put pass thru messages before all others in the queue.

The SendPassThruDataToTracker function is an API call for sending pass thru messages from the user program to the tracker hardware . Note that the pass through control function may be implemented as a filter to enable or disable pass thru messages.

A Shutdown may be performed by purging all queues and I O. For example 300 ms enough for RxM Nav to complete may then be given for threads to complete. Although some threads may not complete in that time such as the DataForwarderThread that may be waiting for Callback to return and NavPeriodicTask for which there may or may not be a provision to interrupt long term calculations. Regardless threads which do not complete on time are terminated.

The following synchronization objects may be used a Semaphore and Critical Section in UI Queue for triggering UI output a Semaphore and Critical Section in Trk2Nav Queue for triggering Nav update a Positioning Navigation Library sync flag from NavPeriodTasks to RxM and Nav and a shutdown semaphore and flag. Note that the Critical Section s in the Tracker Interface are for protecting access to the serial port.

Queues may have the following API and features Constructor destructor void GetBuffer int priority long size to obtain a pre allocated buffer for Put void Put to queues the buffer with specified priority void BeginGet to waits until data ready or shutdown void EndGet void Remove void Purge to cancel all BeginGet calls an internal Semaphore for notifying BeginGet when data is ready and an internal Critical Section.

With regard to error checking all queue overruns I O errors timeouts and COM errors may optionally be reported to client packaged in debug messages UI queue overruns will be reported as an error to user program Tracker message time outs may be handled by Nav and Trk2Nav Queue overruns may be signaled to RxM and Nav.

It is further noted that the Windows registry may provide a mechanism for configuring thread priorities that may for example be set once at startup and remain unchanged during execution I O buffer sizes and queue sizes. Note that the SetupComm function may be used to increase the size of existing WinCE I O buffers. Doing so prevents input data loss under stress conditions. This may also be configurable through registry and default values may be chosen to accommodate several seconds of I O e.g. 4 kb for input and 1 kb for output .

The foregoing description of an implementation of the invention has been presented for purposes of illustration and description. It is not exhaustive and does not limit the invention to the precise form disclosed. Modifications and variations are possible in light of the above teachings or may be acquired from practicing of the invention. For example the described implementation includes software but the present invention may be implemented as a combination of hardware and software or in hardware alone. Note also that the implementation may vary between systems. The invention may be implemented with both object oriented and non object oriented programming systems. The claims and their equivalents define the scope of the invention.

