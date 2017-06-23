---

title: Stream class driver for computer operating system
abstract: A stream class driver for use in a computer operating system functions together with a minidriver. The minidriver is associated with a particular design for an adapter, which is a hardware device that generates or receives streaming data. The stream class driver deals with common operating system tasks such as direct memory access, scatter/gather memory use and Plug n Play. The stream class driver is independent of the hardware design and can therefore function with any type of streaming device or external buses such as USB or IEEE 1394. the minidriver functionality is limited to only those functions required by the unique aspects of the hardware and for the minimum requirements of operation, thereby minimizing the complexity and burden of designing minidrivers for hardware devices.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07444647&OS=07444647&RS=07444647
owner: Microsoft Corporation
number: 07444647
owner_city: Redmond
owner_country: US
publication_date: 20051130
---
This application is a continuation of U.S. patent application Ser. No. 10 950 911 filed Sep. 27 2004 and entitled Stream Class Diver for Computer Operating System which is a continuation application of U.S. patent application Ser. No. 09 819 085 now U.S. Pat. No. 6 845 508 filed Jul. 27 2001 entitled Stream Class Driver for Computer Operating System which is a continuation of now abandoned U.S. patent application Ser. No. 08 994 674 filed Dec. 19 1997 and entitled Stream Class Driver for Computer Operating System all of which are incorporated herein by reference.

The present invention pertains in general to computer software operating systems and more particular to a river for a class of devices which generate or receive streaming data.

A rapidly growing area of interest in the field of computer technology is that of multimedia . This term generally refers to the concurrent use of video and audio in a computer system for a wide range of applications including business and entertainment.

The primary applications which have led to the tremendous success of personal computers have been based on the power of these computers to process numbers in complex ways such as through spreadsheets graphics word processing and data bases. However in such applications the application program works with a discrete data file and typically works with only a small part of such a data file at any one time. Multimedia applications add a major new aspect to the processing of data by personal computer. This is the requirement to manage and process a continuous stream of data as opposed to discrete data files which are typically processed by an application program. The stream of data associated with a multimedia application is generally far too large to be loaded in memory and in many cases the data is continuous with no predetermined end of the data. A further feature of multimedia streaming data is that it is sequential in nature and frequently is time dependent that is it must not only be processed in a specific sequential order it must also be processed to produce precisely times sequential events.

An example of multimedia streaming data is the output which is produced by a DVD Digital Versatile Disk apparatus. The contemporary DVD apparatus produces data using the MPEG 2 video and audio format. This output actually comprises three separate data streams which are video audio and subpicture. Each of these streams requires separate processing but the results of the processing must be time synchronized and generated at a predetermined absolute rate to obtain the desired results. Video and audio signals must be properly synchronized and timed to generate a viable multimedia presentation.

A standardized computer platform including hardware and software must be able to work a large number of independently produced multimedia adapters such as DVD players video cameras audio sources and ROM discs. Each of these products requires a separate complex driver which functions to interface application programs through the computer operating system to the specific hardware in order to process the multimedia streaming data to produce continuous outputs. However to accommodate the massive amounts of data and the extensive complex processing of this data required for a successful multimedia application the driver must be highly efficient well designed and capable of performing a wide range of functions within the operating system and functions required by the application program. With the growing complexity of operating systems and the greater demands of application programs it is very difficult for each independent producer of a hardware device particularly for multimedia to produce an efficient current and effective driver for that product. Thus there exists a need to reduce the burden of producing drivers for multimedia products.

In other areas of computer system operation such as for pointing devices for example a mouse it has been proposed to have a hardware independent driver associated with the operating system and have a hardware dependent driver provided by the hardware manufacturer for each particular device. See U.S. Pat. No. 5 465 364 entitled Method and System for Providing Device Driver Support Which is Independent of Changeable Characteristics of Devices and Operating Systems. Pointing Devices however do not have the same problems that are encountered with multimedia applications. The data rate for pointing devices is extremely low the data processing is not particularly complex and the pointing device is extremely low the data processing is not particularly complex and the pointing device is generally a support aspect of an application program in contrast to being an aspect that is a principle part of a multimedia application.

In view of the substantial problems encountered in the use of multimedia applications on personal computes and the insatiable consumer demand for greater bandwidth and data processing sophistication there is a need for a multimedia driver configuration which can efficiently handle the volume and complexity of streaming data while at the same time minimizing the burden and difficulty of driver design for the independent developers and manufacturers of multimedia products.

The present invention is a method of operation and corresponding computer program units for a stream class driver which is used in conjunction with a minidriver. The minidriver is associated with a hardware adapter which generates or receives streaming data. The operation of the stream class driver product begins with receiving of initialization data from the minidriver followed by registration of the initialization data for later use by the stream class driver. After registration the stream class driver creates a device object for the adapter. The stream class driver then sends a command to the minidriver to initialize the adapter. Next the stream class driver requests that the minidriver provide adapter stream information for all of the data streams handled by the adapter. The minidriver provides this information and the stream class driver registers the received adapter stream information. The stream class driver may then provide a command to the minidriver to turn off power to the adapter and then pages out the minidriver and subsequently awaits a data stream request.

Upon receipt of a data stream request the stream class driver pages in the minidriver to active memory. A command is generated to the minidriver to turn on power to the adapter. The stream class driver provides a data stream open command and stream structure data to the minidriver as needed to open the data stream requested a by an application program. Next the stream class driver provides a stream read or a stream write command to the minidriver. Properties and control information in a predefined data format related to the stream request are transmitted from the stream class driver to the minidriver. Upon receipt of a data stream termination command initiated by an application program the stream class driver provides a stream close command to the minidriver. Finally the stream class driver provides an uninitialization command to the minidriver for uninitializing the adapter.

In a further aspect of the present invention the stream class driver can open additional data streams for either reading or writing streaming data concurrently with the first data stream.

The present invention includes a stream class driver for use in a computer operating system. The purpose of this stream class driver is to make the writing of hardware drivers minidrivers for streaming devices much simpler. The functions performed by the minidriver are limited to those functions which are unique or necessary for the associated hardware while the stream class driver performs all of the functions which are not dependent upon the particular hardware implemented.

The principal terms used in describing the functions data structures commands and other aspects of the present invention are defined as follows 

2. ActiveMovie A cross platform API developed by Microsoft Corporation for developers of multimedia applications that provide a user mode connection and stream architecture to support high quality digital video high fidelity audio and special effects now termed Direct Show. 

4. API Application Programming Interface A set of routines that an applications program uses to request and carry out lower level services performed by a computer operating system.

5. CSA Connection and Streaming Architecture A functional specification produced by Microsoft Corporation defining an architecture and interface for application programs using streaming data and synchronization tasks. This is kernel mode streaming in WDM.

6. DLL Dynamic Link Library An API routine that user mode applications access through ordinary procedure calls.

9. EISA Extended Industry Standard Architecture a 32 bit bus configuration developed as an extension of ISA.

10. Filter An entity which performs a specified function and includes a collection of related connection points called pins.

11. GUID Globally Unique Identifier. A quantity which is unique and includes a current date time and a sequence number and which is used to allow any party to create an identifier which will not overlap other identifiers similarly created.

15. IRQ Interrupt Request A method by which a device can request to be serviced by the device s software driver.

16. ISA Industry Standard Architecture legacy bus configuration for original personal computer design.

19. Kernel Mode The processor mode which allows full unprotected access to the system. A driver or thread running in kernel mode has access to system memory and hardware.

20. Minidriver A hardware specific DLL that uses a class driver to accomplish most actions through functional calls and provides only device specific controls.

22. PCI Peripheral Component Interconnect A high performance 32 bit or 64 bit bus designed to be used with devices that have high bandwidth requirements such as the display subsystem.

25. Plug and Play PnP An enumerator standard for automatically detecting and recognizing installed hardware as defined by Microsoft Corporation.

27. USB Universal Serial Bus A bidirectional isochronous dynamically attachable serial interface for adding peripheral devices such as game controllers serial and parallel ports and input device on a single bus.

29. VxD Virtual Device Driver A device driver that runs at the privileged ring 0 protected Mode of the microprocessor.

30. WDM Windows 32 Driver Model a 32 bit driver model based on the Windows NT driver model that is designed to provide a common architecture of I O services and binary compatible device drivers for both Windows NT and Windows operating system for specific classes of drivers.

31. Windows NT Driver Model The layered device driver model used under the Windows NT operating system see Inside Windows NT by Helen Custer Microsoft Press 1993 .

32. Windows NT Refers to the Microsoft Corporation Windows NT Version 4.0 operating system including any add on capabilities and any later versions of the operating system.

The operating environment of the present invention is illustrated in . This drawing shows selected hardware and software within a personal computer system which is preferably a system using an Intel Corporation x86 microprocessor and a Microsoft Corporation operating system such as Windows NT. The present invention is used within the illustrated environment for supporting a multimedia application such as an application program . The present invention is directed to a stream class driver which is preferably included within an operating system . The application program interacts with the operating system through an application programming interface API . The operating system includes the conventional features and operating aspects not illustrated which are well known in the industry. A system bus driver is a part of the operating system and is used to provide communication through a bus such as PCI bus used with personal computers.

The upper edge of a stream class driver of the present invention is accessed through a CSA interface which is defined in Windows Driver Model Connection and Streaming Architecture Design Notes and Reference published by Microsoft Corporation. This document which is incorporated herein by reference is a part of the MEMPHIS designated operating system documentation entitled Windows 98 Developer s Release Device Driver Kit DDK .

CSA interface is further defined in U.S. patent application Ser. No. 08 825 957 filed Apr. 4 1997 entitled Method and Computer Program Product for Reducing Inter Buffer Data Transfers Between Separate Processing Components which is incorporated herein by reference.

The class driver can be embodied in a computer readable medium such as magnetic disk optical disk or magnetic tape.

The lower edge connection the stream class driver is defined by a stream class driver minidriver interface which is specified in detail herein and in the attached appendices.

A minidriver communicates through the interface with the stream class driver . Minidriver is a unique design corresponding to the hardware adapter . The adapter is preferably a device that generates or consumes steaming data such as used in a multimedia application. An example of the adapter is a DVD player which produced digital audio and video streams for a motion picture.

Minidriver is a hardware specific DLL that uses the class driver to accomplish most actions through function calls and provides only device specific controls. The minidriver registers each adapter such as with the class driver and the class driver creates a device object to represent each adapter that it registered. This process is described in more detail below. Minidriver uses the class driver s device object to make system calls.

The adapter is connected to transmit and receive commands and to transmit and receive data through the bus . In a typical implementation the application program is a multimedia application that uses streaming data provided by the adapter through the bus .

Operating system aspect includes the minidriver which is unique to the adapter but when implemented with a particular computer system becomes a part of the operating system of that computer.

The internal interface between the class driver and the minidriver is primarily a set of function calls between these drivers. The class driver controls the request flow calling the minidriver when access to the adapter hardware is necessary. The class driver is responsible for multiprocessor and interrupt synchronization. Once both the class driver and the minidriver are initialized the minidriver is passive and is called only by the class driver . Most of the function calls from the minidriver to the class driver are low level service requests.

The detailed description for the specific embodiment of the present invention presented herein includes the description in the appendices that follow. These are 

The operating system functional operation begins at a start point . Next step is performed to power up the system and perform the conventional self tests which are well known in the personal computer industry.

After the system has been powered up and the operating system initialization process is performed step is executed in which an enumerator such as Plug n Play detects the attached adapter . When the adapter has been detected the Plug n Play enumerator in step loads into memory the minidriver for the detected adapter . In step the Plug n Play initiates the minidriver DriverEntry routine as describe in Appendix II.

Further referring to the next functional step carried out is performed by the minidriver in step . In this step the minidriver calls the class driver function StreamClassRegisterAdapter. See Appendix I The minidriver further collects and passes the data structure termed HW INITIALIZATION DATA. This data structure is described in detail in Appendix II.

From step control is transferred to step which is performed by the stream class driver . Within step the initialization data provided in the HW INITIZLIZATION DATA structure is registered that is it is recorded in memory for use by the class driver . Next in step the stream class driver creates a device object corresponding to the adapter . The minidriver will not create a device object but instead will share the class driver device object as needed. Only one device object is created per adapter.

In step the stream class driver calls the minidriver to initialize the adapter . This is done by calling the minidriver s function HWReceivePacket with the command SRB INITIALIZE DEVICE. See Appendix IV .

In step the minidriver initializes the adapter hardware by performing the required setup and loading in the adapter any code required for operation of the hardware.

In step control is returned to the streaming class driver which calls the minidriver for stream information. This is done with the command SRB GET STREAM INFO Appendix IV which is sent to the minidriver function HWReceivePacket.

Upon receipt of the SRB GET STREAM INFO command the minidriver in step builds a hardware stream descriptor for all streams that are supported by the adaptor . This information is returned to the class driver . In step the streaming class driver registers the hardware stream descriptor in memory for future use.

Next in step the stream class driver generates a power off command which is transmitted to the minidriver for the adapter . See Appendix IV In general the operating system with driver will turn off power to the adapter whenever it is not being used especially for battery powered computers.

The minidriver receives the power off command in step and turns off power to the adapter . In many systems particularly portable computer systems the adapter is a device which uses a relatively substantial amount of electrical power. By disabling the adapter when not in use system power will be conserved.

Control is returned to the stream class driver in step wherein the driver pages out the minidriver program so that it is no longer stored in active memory thus freeing resources for use by the application program operating system or other active applications. The device object is preferably closed by closing its file handle prior to paging out the minidriver . Finally the class driver enters state to wait for a stream request which requires use of the adapter .

Upon completion of the steps shown in the computer system multimedia subsystem has been initialized and set to be ready to use the adapter for streaming data when needed.

Referring to there is shown a series of interrelated operations carried out by the operating system class driver and minidriver after the multimedia subsystem has been initialized as shown in . These operations are carried out to initiate and terminate a data stream request. A stream request is generated by the operating system in response to the application program . The data stream request is provided to the stream class driver which responds in step to page in the minidriver . This step loads the minidriver into active memory. If the device object has been closed it is opened prior to paging in the minidriver. If the minidriver has not been paged out step is not needed.

In step the stream driver sends a power on command to the minidriver for the adapter . This command is received by the minidriver and in step it turns on power to the adapter by transmitting appropriate commands to the adapter through the bus . Steps and are not needed if power has not been terminated to the adapter .

In step the driver calls the minidriver function HWReceivePacket with the command SRB OPEN STREAM Appendix IV and further provides a data structure HW STREAM OBJECT. See Appendix III This data structure provides the information needed by the adapter and minidriver to service a stream command which will be received from the application program .

Upon receipt of the stream open command the minidriver performs step to activate the adapter and open the specified stream. For the described example wherein the adapter is a DVD the specified stream could be the video stream. For other streams such as audio a new stream request would need to be generated through the operating system by the application program .

When the step has been confirmed the class driver sends either a stream read SRB READ DATA or a stream write SRB WRITE DATA command to the minidriver function ReceiveDataPacket as specified in the HW STREAM OBJECT for the selected stream. The minidriver receives and stores the read or write command at step .

In step the class driver sets properties and other control information for the selected stream by passing the appropriate stream request block SRB to the minidriver s ReceiveControlPacket function as specified in the HW STREAM OBJECT for the selected stream.

At step the minidriver sets the properties and control information received for the selected data stream so that the data stream transfer proceeds as requested by the application program . At this point the minidriver is responsible for the streaming data request until it notifies the class driver that the request has been completed.

In state the class driver waits for receipt of a stream termination command while the streaming data transfer proceeds between adapter and application program .

When the application program has completed use of the specified data stream a stream termination command is generated by the operating system and transferred to the class driver at step . In this step the stream class driver calls the minidriver and sends a stream close command SRB CLOSE STREAM to the minidriver s HWReceivePacket function. In response to this command the minidriver at step closes the specified stream. The transfer of data for the current stream is completed at an end state . After step the class driver may optionally close the device object page out the minidriver and turn power off to the adapter .

When the operating system detects at step that the adapter has been disabled by the user physically removed or the system is being shut down control is transferred to the driver at step in which the driver calls the minidriver and sends an uninitialization command SRB UNINITIALIZE DEVICE. In step the minidriver performs the actions needed to uninitialize the adapt . The actions required are dependent upon the particular design of the adapter and will vary from one manufacturer to the next. After the adapter has been uninitlized the minidriver operation terminates at the end state .

While a streaming data request is being processed the streaming adapter may generate interrupts. When an interrupt is detected the class driver will call the minidriver interrupt service routine as described in Appendix II. All of the minidriver functions are synchronized with the adapter ISR. This is done to make the minidriver nonreentrant. Nonreentrancy is accomplished by masking off the IRQ of the adapter and all lower priority IRQs when code is being executed in any of the minidriver routines. When a thread is executing in the minidriver no calls will be made to any other function within the minidriver including the ISR. This nonreentrancy holds true even on multiprocessor systems making the minidriver very easy to write.

Due to routine synchronization and request serialization the minidriver is multiprocessor safe and nonreentrant for low to medium end hardware. The processing described above has correct file operation synchronization. For example stream and adapter opens are correctly serialized without having the minidrver implement mutexes semaphores or events. All low level buffer management is handled by the class driver . This includes allocation of DMA adapter object as necessary mapping of buffers and building scatter gather list of for DMA and locking and flushing buffers appropriately in DMA versus PIO cases. All IOCTL parameter validation is performed by the class driver . All requests are timed by the class driver with a watchdog timer.

A particular advantage for the class driver of the present invention is that it can work with a wide variety of streaming hardware devices such as MPEG video capture USB audio and video and IEEE 1394 audio and video.

In summary a driver configuration for streaming data includes a stream class driver for performing system operations which are independent of the streaming data adapter and a minidriver which performs a minimum set of functions that are dependent upon the specific hardware design implemented for the adapter. As a result the minidriver design is greatly simplified and can be more easily implemented for each of a large number of streaming class devices.

Although one embodiment of the invention has been illustrated in the accompanying drawings and described in the foregoing Detailed Description it will be understood that the invention is not limited to the embodiment disclosed but is capable of numerous rearrangements modifications and substitutions without departing from the scope of the invention.

Each of the following functions can be called by the minidriver at any time except in the following instances 

The TimerRoutine function called in the StreamClassScheduleTimer routine informs the class driver that the minidriver needs to be called back at a certain time in the future. This is a one shot timer that must be rescheduled each time it is called. The format of the minidriver s timer procedure is as follows 

The StreamClassRegisterAdapter routine is called by the minidriver from its DriverEntry routine the minidriver s initial entry point.

Contains the parameter value with which the operating system called the adapter minidriver s initialization routine. This parameter is the driver object.

Contains the parameter value with which the operating system called the adapter minidriver s initialization routine.

The StreamClassDeviceNotification routine notifies the stream class driver of device specific status changes.

The StreamClassStreamNotification routine notifies the class driver of stream specific status changes.

This PriorityRoutine function in the StreamClassCallAtNewPriority routine informs the class driver that the minidriver needs to be called back at a lower priority. Note that this function cannot be called if the minidriver has set the TurnOffSynchronization Boolean for the adapter. This service should be used if a significant number of processor instructions must be executed from ISR request or other entry points in the minidriver. The format of the minidrivers priority callback routine is as follows 

The StreamClassGetPhysicalAddress routine is used to translate a virtual address into a physical address range that can be used directly by adapters through busmaster DMA.

Supplies the virtual address to be translated. The SRB is required if the address came from the DataBuffer field of a STREAM REQUEST BLOCK.

The StreamClassGetPhysicalAddress routine returns the length in bytes of the physical memory segment.

The StreamClassGetPhysicalAddress routine can be used to build a scatter gather list for DMA data transfers that span physical data pages. The returned length indicates the length in bytes of the physical segment. Note that the length returned can be longer than the length of the data buffers specified in the SRB and that no locking probing mapping or flushing of these physical addresses is necessary. All these operations are performed by the stream class.

An SRB is not required if the VirtualAddress is not of type PerRequestExtension. This function can only be called to translate an extension address if BusMasterDma is specified in HW INITIALIZATION DATA.

The StreamClassAbortOutstandingRequests routine is used to abort all outstanding requests to a particular stream or the entire device. If the StreamObject parameter is not zero all outstanding requests to the specified stream should be aborted by the class driver. If the StreamObject parameter is zero all outstanding requests to the device and all streams should be aborted. The Status parameter indicates with what status each request should be aborted.

The class driver automatically sets a ReadyForNextStreamDataRequest ReadyForNextStreamControlRequest and or ReadyForNextDeviceRequest for each request it aborts depending on the type of requests it aborted.

The StreamClassQueryMasterClock routine allows slave streams to read the current value of the master clock or the stream time.

Contains the handle for the master clock that was passed to the minidriver through SRB INDICATE MASTER CLOCK

Pointer to the procedure within the minidriver to be called back when the requested time is retrieved from the master clock.

When this procedure is called by the stream class the TimeContext field points to a structure. The structure supplies the minidriver with the requested clock time.

The StreamClassGetDmaBuffer routine provides the minidriver with a pointer to the DMA buffer to the mindriver if the minidriver specified a DMA buffer size in the HW INITIALIZATION DATA structure.

The StreamClassRegisterFilterWithNoKSPins routine is used to register filters with DirectShow that have no kernel streaming pins and therefore do not stream in kernel mode.

Contains an array of Boolean values indicating pin direction for each pin length of the array is PinCount . Output pins are TRUE input pins are FALSE.

Optionally contains an array of GUIDs indicating pin categories. The length of the array is PinCount.

The StreamClassRegisterFilterWithNoKSPins routine returns NTSTATUS SUCCESS if the registry key is created.

The StreamClassRegisterFilterWithNoKSPins routine is typically used for TvTuners Crossbars and similar components. On exit a new binary registry key FilterData is created that contains the Mediums and optionally the Categories for each pin on the filter.

The StreamClassGetNextEvent routine retrieves the first or next event from the event queue. If the CurrentEvent parameter is a NULL then the routine will return the first event.

Contains an optional GUID specifier that indicates the event to retrieve. A NULL value indicates a wildcard.

Contains an optional item specifier that indicates the item within a set of events as specified by the EventGuid member to return. A value of 1 indicates a wildcard.

Points to an event previously returned by the StreamClassGetNextEvent routine. The routine will return the next event of the specified type following CurrentEvent in the queue. A NULL value indicates that the first event of the specified type is to be returned.

The StreamClassGetNextEvent routine returns the first or next event of the specified type if successful or NULL if no event is found.

The StreamClassReadWriteConfig routine returns or sets the configuration information from the parent from the device. The routine is commonly used to retrieve or set PCI information when the minidriver is controlling a PCI card. The routine must be called at Passive Level.

Indicates if the action is a read or write. If set to TRUE the configuration information is read. If set to FALSE configuration information is written.

Indicates the buffer to write the configuration information into or from which to read the information. The buffer is normally a stack buffer a local variable within the calling routine or the information could be read directly into the HW device extension.

The StreamClassReadWriteConfig routine returns TRUE if the read or write was successful or it returns FALSE if unsuccessful.

The StreamClassReadWriteConfig routine can only be called at Passive level. Drivers using stream class synchronization must use a callback from to access this routine.

The StreamClassQueryMasterClockSync routine synchronously retrieves the current master clock time. This routine must be used at Dispatch or Passive level. If the caller is running at a raised IRQL using stream class synchronization with a hardware interrupt it should use the asynchronous version of this service or use a callback from StreamClassCallAtNewPriority.

The StreamClassQueryMasterClockSync routine returns the time specified in the Function member of the TimeContext structure if successful or an error if it is unsuccessful.

The following functions are supplied by the minidriver and are called by the class driver . All these routines except for the completion and setup routine run to completion and are executed serially. This means that no two of these routines execute at the same time with the same device extension. Because these routines are running at an elevated interrupt request level potentially blocking other processors they should execute as quickly as possible.

When the class driver receives a request to be processed by the hardware adapter associated with the minidriver the class driver calls the minidriver s setup routine. The setup routine may allocate memory necessary to process the request. The request is queued by the class driver . The class driver then calls the minidriver s start routine to begin the request processing. After this call the minidriver is responsible for the request until it notifies the class driver that the request has completed.

As the request is processed the adapter will generate interrupts. When an interrupt is detected the class driver calls the associated minidriver s interrupt service routine ISR . After the request has completed the minidriver notifies the class driver of the completion.

Every kernel mode driver including minidrivers has to expose a routine named . This routine initializes various driver data structures including the key structure and prepares the environment for all the other driver components.

The minidriver allocates its stack and then initializes the other fields. All of the fields must be initialized. The DriverEntry should then call StreamClassRegisterAdapter. The adapter minidriver s initialization routine should return the status value returned by

Supplies a second context value with which the adapter minidriver should call StreamClassRegisterAdapter.

The HW INITIALIZATION DATA structure is the hardware initialization data structure. This structure is used in the DriverEntry routine and is passed between minidriver initialization and stream class initialization.

Points to the adapter mini driver s receive device data packet routine. This is the entry point for receiving an SRB request from the stream class driver to the adapter.

Points to the adapter minidriver s cancel packet routine. This routine is called when an outstanding stream or adapter based request needs to be canceled. This routine is called only under extreme circumstances such as when an upper layer is attempting to recover and data packets are considered lost.

Points to the adapter minidriver s request time out handler. This routine is called when a stream or adapter based packet times out. The time out is not necessarily an error and it is up to the minidriver to determine what to do with the packet that times out.

Contains the size in bytes required by the adapter minidriver for its device extension. This storage is used by the adapter minidriver to hold peradapter information. A pointer to this storage is supplied with every call to the adapter minidriver. This data is initialized to zero by the class driver.

Contains the number of bytes of extra workspace needed for each stream information structure by the minidriver.

Contains the number of bytes of workspace needed for each instance extension. Normally set to zero except for hardware that can support multiple instances of the reported streams on the same adapter.

Indicates that the memory pointers passed to the minidriver may be used for direct Bus Master DMA access. If the minidriver uses a translation buffer to ensure minimum DMA size or correct buffer alignment this value should be set to FALSE.

Indicates that the DMA engine can access only the lower 24 bits of the 32 bit address space. This should only be set to TRUE if the minidriver will be doing DMA directly to the buffer and not through a double buffer scenario.

Specifies the alignment requirement of the buffers. For example if the DMA engine requires the buffers to be quadword aligned then four should be specified. Note that many data types such as DVD MPEG will be either byte aligned or word aligned so DMA hardware should be designed to support it.

If this field is set to FALSE the minidriver cannot be reentered. Therefore if the minidriver uses a DISPATCH or lower priority callback routine the minidriver must disable any interrupts that it might receive. If an interrupt controlled by the driver is received while code in the minidriver is running at DISPATCH or lower priority the interrupt is lost. If an interrupt is received while at HIGH priority it is queued until the currently executing code is finished.

Specifies the size of the single contiguous region of physical memory that the driver needs at hardware initialization time. The memory is returned to the driver when the driver makes the StreamClassGetDmaBuffer call. It is important to use as little physical buffer as possible here as this is locked physical memory that is not available to the system even when the streaming class minidriver is not in use.

The minidriver can contain routines that will 5e called by the class driver. The function prototypes are contained in the minidrivers header file. Following is a complete list of routines 

The PHW RECEIVE DEVICE SRB routine is the entry point for sending device specific SRBs to the minidriver.

The PHW RECEIVE DEVICE SRB routine is called when the initial device request is received and after each subsequent ReadyForNextDeviceRequest notification is received for this type. After this call the adapter minidriver owns the request and is expected to complete it. The request should be completed asynchronously through interrupt based or timer based polling if the request could potentially take more than a few microseconds to complete. The mini driver should never poll ports waiting for a lengthy request to complete.

The TimeoutCounter and TimeoutOriginal fields are used to time the request. The class driver will set both of these fields to a nonzero value before the request is received by the minidriver and will then begin counting down the TimeoutCounter field until it reaches zero. When it reaches zero the minidriver s time out handler will be called. If the minidriver queues a request for a long time it should set the TimeoutCounter to zero to turn off the timer. Once the request is dequeued it should set the TimeoutCounter field to the value in TimeoutOriginal.

When a request times out and the time out handler is called the minidriver should normally reset its hardware abort this request and issue a ReadyForNextStreamDataRequest ReadyForNextStreamControlRequest or ReadyForNextDeviceRequest depending on the type of request. Alternatively the minidriver may reset its hardware and call StreamClassAbortOutstandingRequests which will abort all outstanding requests on a particular stream or device. Minidrivers that set the TurnOff Synchronization Boolean should first verify that the request is still in their queues before taking action upon it.

The PHW CANCEL SRB routine is usually called when the minidriver should normally abort a request with STATUS CANCELLED. It should then issue a ReadyForNextStreamDataRequest ReadyForNextStreamControlRequest or ReadyForNextDeviceRequest depending on the type of request. Minidrivers that set the TurnOff Synchronization Boolean will not receive this call. Alternately StreamClassAbortAllRequests can be called to abort all requests on a specific stream or the device.

The PHW INTERRUPT routine is called when the adapter hardware generates an interrupt. This routine must clear the interrupt on the adapter before it returns.

The PHW INTERRUPT routine returns FALSE if the adapter is not interrupting or TRUE if the adapter is interrupting.

The PHW RESET ADAPTER routine is called by the class driver when it determines that the streaming adapter needs to be reset.

The PHW RESET ADAPTER routine returns TRUE if the adapter was successfully reset or FALSE if the reset attempt failed.

For multifunction cards all functions should be reset on this call as appropriate. This function may be called even if the minidriver is not ready for another request.

The following routines are used to access or change the stream object created when an SRB is requested 

The PHW RECEIVE STREAM DATA SRB routine is the entry point for receiving data transfer SRBs to an opened stream. The pointer to this routine is filled into the HW STREAM OBJECT structure during the SRB OPEN STREAM call.

A separate entry point in the HW STREAM OBJECT structure can be used for each stream if required by the minidriver. The PHW RECEIVE STREAM DATA SRB routine is called when the initial data request for an opened stream is received and after each subsequent ReadyForNextStreamDataRequest notification is received for this type.

After this call the adapter minidriver owns the request and is expected to complete it. The request should be completed asynchronously through interrupt based or timer based polling if the request can potentially take more than a few microseconds to complete.

The PHW RECEIVE STREAM CONTROL SRB routine is the entry point for receiving nondata transfer such as SRB SET DEVICE STATE SRBs to an opened stream. The pointer to this routine is filled into the HW STREAM OBJECT structure during the SRB OPEN STREAM call defined later . A separate entry point can be used for each stream if desired by the minidriver.

The PHW RECEIVE STREAM CONTROL SRB routine is called when the initial control request for an opened stream is received and after each subsequent ReadyForNextStreamControlRequest notification is received for this type. After this call the adapter minidriver owns the request and is expected to complete it. The request should be completed asynchronously through interrupt based or timer based polling if the request could potentially take more than a few microseconds to complete. The minidriver should never poll ports waiting for a lengthy request to complete.

The streaming header information is contained in several structures. The HW STREAM HEADER structure is the primary structure and is followed in memory by one or more HW STREAM INFORMATION structures. These structures then make up the HW STREAM DESCRIPTOR structure.

The following structures are used to report which stream types and properties are supported by the minidriver.

The HW STREAM HEADER structure reports which stream types and properties are supported by the minidriver. It is used in conjunction with the HW STREAM INFORMATION structure.

Indicates the number of HW STREAM INFORMATION structures that follow the HW STREAM HEADER structure. The first of these packets is constructed by the mini driver immediately adjacent to the HW STREAM HEADER structure.

Indicates the number of property sets supported by the device which is the number of array entries specified by the pointer below. For more information on property sets see Kernel Streaming Reference in the WDM DDK documentation.

Points to the topology structure. At a minimum the categories information must be filled in with at least one category GUID. See the WDM Kernel Streaming documentation for more information on this structure.

The HW STREAM INFORMATION structure indicates what streams are supported. The stream represented by the first HW STREAM INFORMATION structure is designated Stream Zero.

Indicates the number of instances of this stream that are supported by the adapter. For example if this stream information is for an MPEG 2 PES video data stream and the minidriver supports two of them this value would be set to two.

Indicates whether the data is accessible by the class driver. The minidriver should be set to TRUE for any stream that accepts data from the class driver or can return data to the class driver. Streams such as an NTSC output that go to a monitor would not be accessible to the class driver so the Boolean should be set to false.

Provides a pointer to the following variable length structure which contains GUIDs specifying what type of data is represented by this stream.

Indicates the number of property array entries specified by the following pointer. See Kernel Mode Streaming Reference in the WDM DDK documentation for more information on property sets.

Indicates what function is required. The following functions are defined. Note that each of the times returned must be in 100 ns units.

This section describes the format of the SRB. The SRB contains information necessary for the minidriver to process data and control requests. There are SRB commands specific to the driver and adapter and SRB commands specific to each stream supported by the adapter .

The PORT CONFIGURATION INFORMATION structure contains the configuration information necessary to initialize the adapter.

Indicates the length of the PORT CONFIGURATION INFORMATION structure as returned by sizeof. Since this structure may grow in later releases the adapter minidriver should check that the length is greater than or equal to the length expected. This field is always initialized.

Contains the adapter minidriver s adapter data storage. This storage is initialized to zero before this call is made.

Contains the device object associated with this adapter. The minidriver can save this pointer in its device extension if it needs to call system services.

Indicates that the system I O bus number on which the adapter resides. This number is zero for machines with only one I O bus. This field is always initialized by the class driver.

Indicates the bus interrupt request level. This level corresponds to the IRQL on PCI ISA and MCA buses. The uninitialized value is zero.

Indicates the bus vector returned by the adapter. This is used for systems that have I O buses that use interrupt vectors. For ISA MCA and EISA I O buses this field is unused. The uninitialized value is zero.

Indicates whether this adapter uses level or latched type interrupts. This value is always initialized.

Indicates the DMA channel used by the adapter. The un initialized value is 0XFFFFFFFF. This field is normally only used for ISA DMA Bus master cards.

Supplies a pointer to an array of ACCESS RANGE structures. The number of elements is indicated by the NumberOfAccessRanges field. The driver should fill in each structure for the adapter. The uninitialized values for the structures are zero.

AccessRanges will be NULL if NumberOfAccessRanges is zero. See Comments for information on the structure used to define access ranges.

Contains the size of the stream descriptor structure that is filled in by the minidriver in the SRB GET STREAM INFO command defined later in this document . The minidriver should fill in this size to be equal to the size of the HW STREAM HEADER Structure plus the sizes of each of the variable length HW STREAM INFORMATION structures needed by the minidriver.

The ACCESS RANGE structure is used to define access ranges for the AccessRanges value. These ranges indicate to the system which ports and memory address are being used by the card.

Indicates the length in bytes or number of ports of the range. This value should indicate the range actually decoded by the adapter.

Indicates the size of this packet Filled in by the stream class. The minidriver should verify that the size of the structure it expects is less than or equal to the value in this element.

Indicates the number of the stream to be opened. The number corresponds with the location of the stream s HW STREAM INFORMATION structure in the information returned by SRB GET STREAM INFO defined earlier.

The minidriver fills in the vector to its HW RECEIVE STREAM DATA SRB routine as defined in this document.

The minidriver fills in the vector to its HW RECEIVE STREAM CONTROL SRB routine as defined in this document.

If set to TRUE indicates the minidriver will use DMA to transfer data directly from the data packets for this stream type. If the device has to double buffer data into a DMA buffer but does not actually use DMA from or to the user buffers directly this should be set to FALSE. Note that both the DMA and PIO values can be set if necessary.

Indicates that the minidriver will use PIO to transfer data for this stream type. This means that the processor needs to touch some or all of the data in the data packets to transfer it to the device. Note that both the DMA and PIO values can be set if necessary.

The HW STREAM REQUEST BLOCK structure is the basis for all SRBs. The structure contains information necessary for the minidriver to process data and control requests. There are SRB commands specific to the adapter and commands specific to each stream supported by the adapter.

Indicates the number of seconds until the request is timed out by the class driver. The class driver sets both the TimeoutCounter and the TimeoutOriginal to nonzero values when the request is received by the minidriver and then begins counting down the TimeoutCounter until it reaches zero. A setting of zero indicates that the request is not timed.

Indicates a buffer pointing to an array of scatter gather elements. This array of elements can be used by the minidriver to use DMA directly to or from host memory. Note that no locking probing mapping or flushing of these physical addresses is necessary all these operations are performed by the stream class. See the Comments section for information on the structure used for each element in the scatter gather array.

The fields PhysicalScatterGatherList and NumberOfPhysicalElements are filled in only if the minidriver has indicated DMA support in the STREAM OBJECT structure.

SRB command codes are used in the HW STREAM REQUEST BLOCK and are used to provide information to the class drivers. SRB commands can be either stream specific or device instance specific.

The SRB INITIAIIZE DEVICE command is sent by the class driver when an adapter needs to be initialized. The PORT CONFIGURATION INFORMATION structure which contains parameters necessary to initialize the adapter is passed in through the CommandData. ConfigInfo field of the SRB by the class driver.

The PORT CONFIGURATION INFORMATION structure is partially initialized by the class driver before the SRB INITIALIZE DEVICE function is called. The specific fields initialized depend on the adapter mini driver and the information available to the class driver. All uninitialized fields are set to a well known value as defined in the following text. All relevant fields should be updated by the adapter minidriver.

The fields required to find and set up the adapter IRQ port address and so on must have been filled in by the class driver. If not the minidriver should return with STATUS NO SUCH DEVICE.

The SRB UNINITIALIZE DEVICE command is sent by the class driver when the adapter needs to be uninitialized. The minidriver should deallocate any system resources it allocated aside from those allocated through the class driver such as the uncached extension IRQs and so on that will be automatically deallocated by the class driver. The minidriver should permanently disable adapter interrupts on this call if possible.

The SRB GET STREAM INFO command is sent by the class driver to retrieve information about the streams supported by the minidriver s hardware. When the minidriver receives this command the minidriver builds the HW STREAM HEADER structure followed by one or more HW STREAM INFORMATION structures in the buffer provided by the class driver and pointed to by CommandData.StreamBuffer. The size of this buffer is indicated by the minidriver in the StreamDescriptorSize field in the PORT CONFIGURATION INFORMATION structure.

The SRB OPEN STREAM command is sent by the class driver to open a stream. The stream to be opened is specified by the HW STREAM OBJECT which is pointed to by the StreamObject field in the SRB. The CommandData.OpenFormat field may point to additional format information about the stream being opened.

When the minidriver receives the SRB OPEN STREAM command the minidriver should determine if the specified stream is able to be opened at this time. If the stream can be opened the HW STREAM OBJECT structure is updated by the minidriver and STATUS SUCCESS is returned. If the number of instances specified as stream are already opened or the hardware resources to open this stream are otherwise unavailable the minidriver should return an appropriate error status.

The SRB CLOSE STREAM command is sent by the class driver to close a a previously opened stream. The stream to be closed is specified by the HW STREAM OBJECT structure referenced by the StreamObject field in the SRB. If the stream is successfully closed by the minidriver STATUS SUCCESS should be returned. Otherwise an appropriate error status should be returned.

The SRB OPEN DEVICE INSTANCE command is sent by the class driver to open an instance of the adapter. Most adapters do not support instancing so the InstanceExtensionSize field in the HW INITIALIZATION DATA structure should be set to zero and should never receive this command.

If the minidriver supports device instancing this command will be sent by the class driver each time a new instance of the adapter is opened. For example a DSP decoder that can allocate n number of instances of the streams specified. The HwInstanceExtension field in the SRB should then be set to the minidriver s per instance workspace by the class driver.

The SRB CLOSE DEVICE INSTANCE command is sent by the class driver to close a previously opened instance of the adapter.

The SRB GET DEVICE PROPERTY command controls the changing of property values for the device. For more information on property sets see Kernel Mode Streaming Reference in the WDM DDK Documentation.

The SRB SET DEVICE PROPERTY command controls the changing of property values for the device. For more information on property sets see Kernel Mode Streaming Reference in the WDM DDK Documentation.

The SRB UNKNOWN DEVICE COMMAND command indicates that the IRP function is unknown to the class driver.

The SRB PAGING OUT DRIVER command indicates that the driver is to be paged out. It is only sent if enabled in the registry. Adapter interrupts should be disabled and a STATUS SUCCESS should be returned.

Stream specific command codes are defined for a previously opened stream. The StreamObject field in the SRB specifies the stream on which to carry out the specified command.

The SRB READ DATA command is issued to read one or more blocks of data to or from the specified stream.

The Command Data. DataBufferArray field points to one or more KSSTREAM HEADER structures as defined in the following text.

The number of KSSTREAM HEADER structures pointed to by the CommandData. DataBufferArray field is indicated by the NumberOfBuffers field in the SRB.

The SRB WRITE DATA command is issued to write one or more blocks of data to or from the specified stream.

The CommandData.DataBufferArray field points to one or more KSSTREAM HEADER structures as defined in the following text.

The number of KSSTREAM HEADER structures pointed to by the CommandData.DataBufferArray field is indicated by the NumberOfBuffers field in the SRB.

The SRB SET STREAM STATE command controls the state of the specified stream. The CommandData.StreamState field in the SRB is set by the class driver to one of the following states 

The minidriver should set the stream to the specified state and return STATUS SUCCESS if successful. An appropriate error code should be returned if the operation fails.

The SRB GET STREAM PROPERTY command controls the changing of property set values for the stream. For more information on property sets see Kernel Mode Streaming Reference.

The SRB SET STREAM PROPERTY command controls the changing of property set values for the stream. For more information on property sets see Kernel Mode Streaming Reference.

The SRB OPEN MASTER CLOCK command indicates that the stream referenced by the stream object in the SRB has been chosen to be the master clock. The HwClockObject in the HW STREAM OBJECT must have been filled in correctly for a particular stream to be chosen as the master clock.

The CommandData.MasterClockHandle field points to the handle of the master clock which the minidriver should retain.

The SRB CLOSE MASTER CLOCK command indicates that the stream referenced by the stream object in the SRB is no longer the master clock.

The SRB INDICATE MASTER CLOCK command gives the handle to the master clock to slave streams. If the handle is zero this stream is treated as free running by the minidriver. Also until the minidriver receives this function for a particular stream the minidriver should assume that the stream is free running. The minidriver can use this handle to read the current master clock value using StreamClassQueryMasterClock defined in this document. Note that if the handle passed into this function for a slave pin is the same as the handle passed into the minidriver through SRB OPEN MASTER ClOCK the minidriver can read the time from the master clock directly since it controls the master and the slave. This is not necessary but is an optimization.

The CommandData. MasterClockHandle field points to the handle for the master clock which the minidriver should retain. If this handle is zero this indicates to the minidriver that this stream is now free running and cannot slave to a master clock.

The SRB PROPOSE DATA FORMAT command queries the minidriver to determine if the minidriver can change the format of a particular stream. If the minidriver is able to switch the stream to the specified format. STATUS SUCCESS is returned. Note that this function only proposes a new format but does not change it.

If the minidriver is able to accept the new format the class driver at some later time may send the minidriver a format change which is indicated by an OptionsFlags flag in a KSSTREAM HEADER structure.

The SRB UNKNOWN STREAM COMMAND command indicates that the IRP function is unknown to the class driver. The function is then passed down the next driver in the stack.

