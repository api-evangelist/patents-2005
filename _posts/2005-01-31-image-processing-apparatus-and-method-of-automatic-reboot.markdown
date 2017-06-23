---

title: Image processing apparatus and method of automatic reboot
abstract: An image processing apparatus is disclosed that, when falling in failures possibly being fixable by switching off/on electric power, is able to be automatically and appropriately rebooted and does not involve disagreement in counts of different counters used for management actions in the course of rebooting process. The image processing apparatus, which has hardware resources used for image formation and programs used for controlling the image formation, includes a failure detection unit to detect a rebooting failure from type A or D failures which are possibly fixable by switching off/on electric power of the image processing apparatus, and a reboot unit to reboot the hardware resources and the programs. The image processing apparatus may further include an operation halting unit to halt operations of the hardware resources and the programs when the rebooting failure is detected.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07391979&OS=07391979&RS=07391979
owner: Ricoh Company, Ltd.
number: 07391979
owner_city: Tokyo
owner_country: JP
publication_date: 20050131
---
In an image processing apparatus such as a copier for the purpose of charging or other management actions several kinds of hardware or software based counters are installed in the copier to count each printing operation. For example in the copier there may be a general counter of a controller a counter of a charging device in the controller a mechanical counter of an engine and a counter of a charging device in the engine. It is required that these counters accurately count each printing operation. If the counts are not correct charging or other management actions cannot be made appropriately.

As illustrated in in step S a notification of starting a printing job is transmitted from an application which controls copying operations to an xCS such as an Engine Control Service ECS .

In step S receiving the notification from the application the xCS notifies a system control service SCS to start a process of printing the first sheet.

In step S receiving the notification from the xCS the SCS notifies an engine to start the process of printing the first sheet.

In step S receiving the notification from SCS the engine starts to feed the first sheet and notifies the SCS that the first sheet is fed.

In step S receiving the notification from the SCS the xCS notifies the SCS to start a process of printing the second sheet.

In step S the engine starts to feed the second sheet and notifies the SCS that the second sheet is fed.

Here in order to improve printing performance the process of printing the second sheet is started while the first sheet is being fed.

In step S the engine executes printing of the first sheet and increments the count of the mechanical counter of the engine when fusing on the first sheet is completed.

In step S receiving the notification from the engine the SCS increments the count in the general counter of the controller.

In step S receiving the request from the SCS the engine increments the count in the counter of the charging device in the engine.

Afterward in step S when the first sheet is normally delivered the engine notifies the SCS of the normal delivery of the first sheet.

Similarly in step S the engine executes printing of the second sheet and increments the count of the mechanical counter of the engine when fusing on the second sheet is completed.

In step S receiving the notification from the engine the SCS increments the count in the general counter of the controller.

In step S receiving the request from the SCS the engine increments the count in the counter of the charging device in the engine.

Afterward in step S when the second sheet is normally delivered the engine notifies the SCS of the normal delivery of the second sheet.

In the above operations printing of the first sheet and the second sheet is counted by all of the general counter of the controller the counter of the charging device in the controller the mechanical counter of the engine the counter of the charging device in the engine and the counts in these counters are in agreement.

The image processing apparatus for example a copier sometimes fails due to problems in hardware software or other problems. For example there are primarily four types of failures as follows.

It should be noted that this classification is made just for convenience but does not indicate the level of gravity of the failures.

In the related art when failures of type D occur if the number of failure occurrences is less than a preset value the image processing apparatus is set to automatically reboot without operations by the users.

In steps S through S almost at the same time notifications of operation suppression are sent from the SCS to the xCS to the engine via a system resource manager SRM and to the applications and .

In step S component sections of the image processing apparatus which have received the notifications are driven to undertake operation suppression processing. The operation suppression processing is a kind of post processing for appropriately terminating processes being executed so that reboot can be executed safely. For example the operation suppression includes processing that prevents new operations by controlling an interface.

In steps S through S the component units of the image processing apparatus make responses of operation suppression.

Although the image processing apparatus in failure can be rebooted as described above the counts in the aforesaid counters which are provided for charging or other management actions are in agreement.

In step S receiving the notification from SCS the engine starts to feed the first sheet and notifies the SCS that the first sheet is fed.

In step S receiving the notification from the SCS the xCS notifies the SCS to start a process of printing the second sheet.

In step S the engine starts to feed the second sheet and notifies the SCS that the second sheet is fed.

In step S it is assumed that a rebooting failure occurs in the image processing apparatus. Here a rebooting failure is a failure to solve which the image processing apparatus should be rebooted.

In steps S through S the SCS sends notifications to the engine to suppress new operations and abort processes in execution.

In steps S and S almost at the same time as steps S through S the SCS sends notifications to the xCS and the applications for operation suppression.

In step S the engine attempts to abort processes as much as possible. If the process of printing the first sheet is being executed and cannot be aborted immediately the engine executes printing of the first sheet and increments the count of the mechanical counter of the engine when fusing on the first sheet is completed.

In step S upon receiving the notification from the engine the SCS increments the count in the general counter of the controller.

In step S upon receiving the request from the SCS the engine increments the count in the counter of the charging device in the engine.

Afterward in step S when the first sheet is normally delivered the engine notifies the SCS of the normal delivery of the first sheet.

At this moment however because the xCS has been in a state of operation suppression already and the interface is suppressed the notification to the application cannot be sent. For this reason the sequence cannot proceed to the operation of the application for requesting the SCS to count indicated as S by a dotted arrow and the operation of the SCS to increment the count in the counter of the charging device in the controller indicated as S by a dotted frame .

Afterward in step S the engine aborts printing of the second sheet and executes abnormal delivery of the second sheet deliver the second sheet without its being printed and notifies the SCS of the abnormal delivery of the second sheet.

As described above the first sheet is normally printed and printing of the first sheet is counted by the mechanical counter of the engine the counter of the charging device in the engine and the general counter of the controller but is not counted by the counter of the charging device in the controller hence the counts in the above counters are not in agreement.

In the related art when failures of type A occur or when failures of type D occur at a frequency higher than a preset value operations illustrated in are performed. Other methods are utilized to respond when failures of type B or C occur.

As illustrated in in step S failures of type A occur or failures of type D occur at a frequency higher than a preset value.

In step S if an automatic notification function referred to as Customer Satisfaction Service CSS in the image processing apparatus is valid an image for automatic notification is displayed on a service call SC screen SC to automatically notify a service center of the failure.

In step S if the notification is sent successfully the automatic notification image displays that the image processing apparatus is waiting for service from the service center.

In step S if transmission of the notification fails the automatic notification image displays that the service center should be contacted.

In step S if the failures of type D have occurred just occasionally that is below the preset frequency even when the automatic notification function of the image processing apparatus is valid the automatic notification is not performed and the user is urged to switch OFF ON the power.

In step S if the automatic notification function of the image processing apparatus is invalid or the image processing apparatus does not have the automatic notification function when failures of type A occur or failures of type D occur at a frequency higher than the preset value a message is displayed on the screen to urge the user to notify the service center.

In step S if the failures of type D have occurred just occasionally that is below the preset frequency a message is displayed on the screen to urge the user to switch OFF ON the power. If the failure occurs again a message is displayed on the screen to urge the user to notify the service center.

However the operations shown in as a response to failures of the image processing apparatus in the related art suffer from the following problems.

When failures of type D have occurred occasionally no matter whether the image processing apparatus has the automatic notification function or not the user is urged to switch OFF ON the power and due to this the user has to perform more operations. Because the power switch is not frequently used when making copies some users may feel inconvenienced by having to search for the power switch.

In addition as described above when failures of type D have occurred at a frequency higher than the preset value it is set that the automatic notification is performed or the user is urged to notify the service center. Among the frequently occurring failures there are some recurring failures caused by inappropriate operation of the power switch by the user which could have been avoided by otherwise appropriately switching OFF ON the power. In other words even for some less than severe failures for example failures fixable by the user without calling a service person the automatic notification or the notification by the user has to be performed.

A first specific object of the present invention is to provide an image processing apparatus and a method thereof which apparatus is able to be automatically and appropriately rebooted reset re started when falling into failures possibly fixable by switching off and on electric power.

A second specific object of the present invention is to provide an image processing apparatus and a method thereof in which apparatus disagreement in counts of different counters used for charging or other management actions does not occur when being rebooted from failures possibly fixable by switching off and on electric power.

According to a first aspect of the present invention there is provided an image processing apparatus including hardware resources used for image formation and programs used for controlling the image formation the image processing apparatus comprising a failure detection unit configured to detect a first failure of the image processing apparatus from a plurality of second failures of the image processing apparatus and a reboot unit configured to reboot the hardware resources and the programs. The image processing apparatus is rebooted when the first failure occurs. The second failures of the image processing apparatus can be recovered from by switching off and switching on electric power of the image processing apparatus.

As an embodiment when the image processing apparatus is printing sheets until reaching a predetermined number the first failure occurs before the number of the second failures reaches a predetermined value. Preferably the predetermined number of sheets to be printed may be 10 and the predetermined value of the number of the second failures may be 2.

As an embodiment the failure detection unit and the reboot unit may be realized as functions of a system control service that performs at least application management operational section control system message display LED display hardware resources management and interruption application control.

As an embodiment from the time when the first failure is detected to the time when the reboot process is executed even when another failure occurs that ought to be reported automatically the reboot process continues without the automatic notification about the other failure being performed.

As an embodiment operations of the hardware resources and the programs may be suppressed after the first failure is detected. Preferably the image processing apparatus stands by from the time when the hardware resources and the programs make responses to the operation suppression to the time when the reboot process is executed.

As an embodiment in the reboot process of the hardware resources and the programs sequentially an engine is reset access to a hard disk drive is halted power of the engine is switched off the power of the engine is switched on and an application is rebooted. As another embodiment in the reboot process of the hardware resources and the programs if an energy saving mode is detected the power of the engine is switched on after post processing. As another embodiment after the power of the engine is switched on sequentially access to the hard disk drive is halted and the application is rebooted.

As an embodiment when the first failure is detected an image is displayed on a screen to announce the start of a reboot process. Preferably processing conditions of post processing of the hardware resources and the programs may be displayed in the image announcing the start of the reboot process. As another embodiment information of the time up to the execution of the reboot process may be displayed in the image announcing the start of the reboot process. As another embodiment a button for initiating the immediate start of the reboot process may be displayed in the image announcing the start of the reboot process.

As an embodiment after the execution of the reboot process an image may be displayed on a screen to require a user to make confirmation.

According to a second aspect of the present invention there is provided a method of automatically rebooting an image processing apparatus including hardware resources used for image formation and programs used for controlling the image formation the method comprising the steps of detecting a first failure from a plurality of second failures of the image processing apparatus and rebooting the hardware resources and the programs when the first failure is detected. The image processing apparatus is rebooted when the first failure occurs and the second failures can be recovered from by switching off and switching on electric power of the image processing apparatus.

As an embodiment from the time when the first failure is detected to the time when the reboot process is executed even when another failure occurs that ought to be reported automatically the reboot process continues without automatic notification of the other failure being performed.

As an embodiment operations of the hardware resources and the programs are suppressed after the first failure is detected.

As an embodiment in the reboot process of the hardware resources and the programs steps of resetting an engine halting access to a hard disk drive switching off power of the engine switching on the power of the engine and rebooting an application are executed sequentially.

According to a third aspect of the present invention there is provided an image processing apparatus including hardware resources used for image formation and programs used for controlling the image formation and the image processing apparatus comprises a failure detection unit configured to detect a first failure of the image processing apparatus from a plurality of second failures of the image processing apparatus an operation halting unit configured to halt operations of the hardware resources and the programs after the first failure is detected and a reboot unit configured to reboot the hardware resources and the programs. The image processing apparatus is rebooted when the first failure occurs and the second failures of the image processing apparatus can be recovered from by switching off and switching on electric power of the image processing apparatus.

As an embodiment the image processing apparatus further comprises a controller counter provided on a side of a controller of the programs a controller charging device counter provided on the side of the controller a mechanical counter provided on a side of an engine of the hardware resources and an engine charging device counter provided on the side of the engine.

As an embodiment the halt of operations includes halt of jobs and halt of generation of new control processes. Preferably due to the halt of jobs uncompleted jobs of the programs are cancelled.

As an embodiment operations of the hardware resources and the programs are suppressed after halt of the operations and before the reboot process. Preferably the image processing apparatus stands by from the time when the hardware resources and the programs make responses to the operation suppression to the time when the reboot process is executed.

As an embodiment when the image processing apparatus is printing sheets until reaching a predetermined number the first failure occurs before the number of the second failures reaches a predetermined value. Preferably the predetermined number of sheets to be printed may be 10 and the predetermined value of the number of the second failures may be 2.

As an embodiment the failure detection unit the operation halting unit and the reboot unit may be realized as functions of a system control service that performs at least application management operational section control system massage display LED display hardware resources management and interruption application control.

As an embodiment in the reboot process of the hardware resources and the programs sequentially an engine is reset access to a hard disk drive is halted power of the engine is switched off the power of the engine is switched on and an application is rebooted.

As an embodiment when the first failure is detected an image is displayed on a screen to announce the start of an automatic reboot process. Preferably processing conditions of post processing of the hardware resources and the programs may be displayed in the image announcing the start of the automatic reboot process. Preferably information of the time up to the execution of the reboot process may be displayed in the image announcing the start of the automatic reboot process. Preferably a button for initiating the immediate start of the reboot process may be displayed in the image announcing the start of the automatic reboot process.

As another embodiment after the execution of the reboot process an image may be displayed on a screen to require a user to make confirmation.

According to a fourth aspect of the present invention there is provided a method of automatically rebooting an image processing apparatus including hardware resources used for image formation and programs used for controlling the image formation and the method comprises the steps of detecting a first failure from a plurality of second failures of the image processing apparatus the image processing apparatus being rebooted when the first failure occurs said second failures able to be recovered from by switching off and switching on electric power of the image processing apparatus halting operations of the hardware resources and the programs after the first failure is detected and rebooting the hardware resources and the programs when the first failure is detected. Preferably the step of halting the operations includes a step of halting jobs and halting generation of new control processes. Preferably due to the step of halting jobs uncompleted jobs of the programs are cancelled.

According to the present invention when coping with failures of the image processing apparatus that can possibly be recovered from by switching off and re switching on electric power an image processing apparatus can be automatically and appropriately rebooted without operations by a user.

In addition when coping with failures of the image processing apparatus that can possibly be recovered from by switching off and re switching on electric power it is possible to provide an image processing apparatus free from disagreement in counts of different counters used for charging or other management actions.

These and other objects features and advantages of the present invention will become more apparent from the following detailed description of preferred embodiments given with reference to the accompanying drawings.

Below preferred embodiments of the present invention are explained with reference to the accompanying drawings.

As illustrated in the image processing apparatus includes a software group an image processing apparatus activator and hardware resources .

The image processing apparatus activator operates first when power of the image processing apparatus is switched on to activate an application layer and a platform layer . For example the image processing apparatus activator reads programs related to the application layer and the platform layer from a hard disk device abbreviated to be HDD below transfers the programs to a portion of a memory and starts up the programs.

The hardware resources include a scanner a plotter and other hardware such as an ADF Auto Document Feeder .

The software group includes the application layer and the platform layer activated on an operating system abbreviated to be OS below such as UNIX a registered trade mark . The application layer includes programs that provide user services for image formation by a printer a copier a facsimile machine a scanner and the like. Specifically the application layer includes a printer application for use of a printer a copier application for use of a copier a facsimile machine application for use of a facsimile machine and a scanner application for use of a scanner.

The platform layer includes a control service layer a system resource manager abbreviated to be SRM below and a handler layer . The control service layer interprets requests from the application layer and generates a request for acquiring the hardware resources . The system resource manager SRM manages one or more hardware resources to arbitrate requests from the control service layer . The handler layer manages the hardware resources in accordance with an acquisition request from the system resource manager .

The control service layer includes one or more service modules such as a network control service NCS a delivery control service DCS an operational panel control service OCS a facsimile control service FCS an engine control service ECS a memory control service MCS a user information control service UCS and a system control service SCS .

In addition the platform layer includes an API Application Programming Interface which is capable of receiving a request from the application layer by using functions defined beforehand. The OS executes processes related to software included in the application layer and the platform layer in parallel.

The process of NCS provides services commonly available to applications required by the network I O and distributes data received from a network by using various protocols or acts as a relay to transform data from the applications to the network. For example NCS controls data communications with a network device connected to the network by HTTP Hyper Text Transfer Protocol using httpd Hyper Text Transfer Protocol Daemon .

The process of OCS controls an operational panel which functions as an information transmitter between an operator and a main body control process.

The process of FCS provides APIs for facsimile transmission to and reception from the application layer by using a PSTN or an ISDN for registration or citation of various facsimile data stored in a memory for backup use for reading facsimile and for printing a received facsimile.

The process of MCS controls for example allocation and release of a memory and utilization of the HDD.

The process of SCS performs for example application management operational section control system massage display LED display hardware resources management and interruption application control.

The process of SRM together with SCS performs system control and management of the hardware resources for example in accordance with an acquisition request from an upper layer utilizing the scanner the plotter and other hardware and controls execution of them.

Specifically the process of SRM determines whether the acquired hardware resources are available or not namely whether the acquired hardware resources are being used by other acquisition requests. If the acquired hardware resources are available the process of SRM notifies the upper layer that the acquired hardware resources are available. In addition in response to the acquisition request from the upper layer the process of SRM performs scheduling in order to utilize the hardware resources and directly executes the requested process for example paper conveyance and image capturing memory allocation file generation and so on.

The handler includes a facsimile controller unit handler FCUH for controlling a facsimile controller unit FCU which is described below and an image memory handler IMH for controlling allocation of the memory to processes and the allocated memory. SRM and FCUH request processing by the hardware resources by using an engine interface I F which is capable of transmitting a request for processing to the hardware resources by using functions defined beforehand.

As illustrated in the image processing apparatus includes a controller board an operational panel a facsimile controller unit FCU and an engine . The facsimile controller unit includes a unit in compliance with a G3 standard and a unit in compliance with a G4 standard.

The controller board includes a CPU an ASIC application specific integrated circuit a HDD a system memory MEM P a local memory MEM C a NorthBridge abbreviated as NB below a SouthBridge abbreviated as SB below a Network Interface Card NIC a USB device and IEEE 1394 device and a Centronics device .

The operational panel is connected to the ASIC of the controller board . In addition the SB NIC USB device IEEE 1394 device and the Centronics device are connected to the NB through a PCI bus.

In the controller board the MEM C and the HDD are connected to the ASIC and the CPU and the ASIC are connected through the NB of a CPU chipset. Hence if the CPU and the ASIC are connected through the NB the controller board operates even when the interface of the CPU is not open.

The ASIC and the NB are not connected through the PCI bus but are connected through an AGP Accelerated Graphics Port . Because the ASIC and the NB execute and control one or more processes which constitute the application layer and the platform layer shown in by connecting the ASIC and the NB through the AGP instead of the PCI bus performance degradation is preventable.

The CPU controls the whole image processing apparatus . The CPU starts up and executes the NCS DCS OCS FCS ECS MCS UCS SCS SRM FCUH and IMH shown in as respective processes on the OS and starts up and executes the printer application the copier application the facsimile machine application and the scanner application included in the application layer .

The NB is a bridge for connecting the CPU the MEM P the SB and the ASIC . The MEM P is used as an image memory of the image processing apparatus . The SB is a bridge for connecting the NB with the PCI bus and peripheral devices. The MEM C is used as a copier image buffer and a code buffer.

The ASIC includes integrated circuits IC which have hardware elements for image processing and are specifically used for processing images.

As illustrated in the SCS includes a failure detection unit that detects failures of the image processing apparatus of type A and type D as described above a log writing unit that writes information of the detected failures into a log and a rebooting failure detection unit that detects a rebooting failure of the image processing apparatus among the failures of type D which can highly possibly be recovered from by switching off on the electric power of the image processing apparatus .

Here a rebooting failure indicates that the image processing apparatus needs to be rebooted when the rebooting failure occurs.

Preferably the rebooting failure occurs before the number of occurrence of the type D failures reaches a predetermined value when the image processing apparatus is printing sheets until reaching a predetermined number.

For example the rebooting failure occurs before the number of the failures of type D reaches 2 when a count of a general counter for counting the number of the printing sheets increases toward 10 that is the first failure of type D may be detected as a rebooting failure.

Further the SCS includes an image display controller that displays an image to announce an automatic notification process and an automatic reboot process when failures occurs and an automatic notification controller that automatically notifies a service center of the failure by using NRS New Remote Service when failures of type A or type D occur at a predetermined frequency for example the failures of type D have occurred twice when the count of the general counter for counting the number of the printing sheets increases to 10. The NRS is a diagnosis service utilizing the aforesaid CSS or a network.

Further the SCS includes an operation suppression controller that performs controls to suppress operations of the hardware resources of the image processing apparatus such as an engine or the programs software group after the rebooting failure is detected and before the reboot process starts. For example the operation suppression may include suppression of new operations suppression of communications between processes and suppression of access to the HDD.

Further the SCS includes a reboot execution controller for rebooting that is resetting an engine of the image processing apparatus or programs in a series.

In an energy saving mode detection unit is for detecting an energy saving mode of the image processing apparatus .

In step S in case of a failure of type A or when the failure of type D is not a rebooting failure for example the failure of type D occurs for the second time when the count of the general counter for counting the number of the printing sheets increases toward 10 if the image processing apparatus has an automatic notification function given by the CSS Customer Satisfaction Service or NRS and if the function is valid an image for automatic notification is displayed on a screen to automatically notify a service center of the failure.

In step S if the notification is sent successfully the automatic notification image displays that the image processing apparatus is waiting for service from the service center.

Or as in step S the automatic notification image displays that service will be provided on the next service day because it is outside service hours.

In step S if transmission of the notification fails the automatic notification image displays that the user should contact the service center.

In step S if the failure of type D is a rebooting failure for example the failure of type D occurs for the first time even when the automatic notification function of the image processing apparatus is valid the automatic notification is not performed but an image is displayed on the screen to announce the start of an automatic reboot process.

What is displayed in this image may include for example a message indicating that data of the processes being executed may be deleted due to the reboot and it is necessary to run the processes again or procession conditions of post processing of the hardware resources and the programs related to the automatic reboot process the time up to execution of the automatic reboot process or a button for initiating an immediate start of the automatic reboot process.

Here the post processing of the hardware resources and the programs related to the automatic reboot process is processing for appropriately executing the automatic reboot process for example for preventing sheets from being left in the engine or preventing troubles with the HDD.

As the time up to execution of the automatic reboot process for example a waiting period of 30 seconds may be set after the post processing is completed and the automatic reboot process becomes executable. The reason for the waiting period is that when the post processing is completed in a short time the image for announcing the start of the automatic reboot process can be displayed for only a short time and the user cannot recognize the message in the image.

The button for initiating an immediate start of the automatic reboot process is provided for the purpose of quickly executing the automatic reboot process without the waiting period so as to accelerate recovery of the image processing apparatus .

In step S when the waiting period displayed in the image for announcing start of the automatic reboot process elapses the automatic reboot process is executed.

In step S the user is notified of completion of the automatic reboot process and an image is displayed on the screen to require the user to make confirmation.

In step S after the user pushes a confirmation button the display returns back to the usual display condition.

In step S if the user pushes the button for an immediate start of the automatic reboot process the automatic reboot process is executed without the waiting period. Then as in step S the display returns back to the usual display condition.

In this case step S is omitted that is it is not necessary to display an image to notify the user of completion of the automatic reboot process and to require the user to make confirmation.

In step S if the automatic notification function of the image processing apparatus is invalid or the image processing apparatus does not have the automatic notification function in case of a failure of type A or when the failure of type D is not a rebooting failure an image is displayed on the screen to show that the user should contact the service center.

In step S if the failure of type D is a rebooting failure an image the same as that in step S is displayed on the screen to announce the start of an automatic reboot process.

In step S when a preset waiting period elapses the automatic reboot process is executed. Then as in step S the user is notified of completion of the automatic reboot process and the confirmation image is displayed on the screen to require the user to make confirmation. Then as in step S after the user pushes a confirmation button the display returns back to the usual display condition.

In step S if the user pushes the button for an immediate start of the automatic reboot process the automatic reboot process is executed without the waiting period. Then as in step S the display returns back to the usual display condition.

According to the above operations the image processing apparatus is capable of automatic and appropriate reboot without operations by users when dealing with failures which can possibly be recovered from by switching off on the electric power without the necessity of automatic notification to a service center.

In the same reference numbers as in are assigned to the OCS operation panel control service and the SCS system control service . Further in for convenience it is assumed that the SCS also includes functions of the SRM system resource manager .

In addition in applications respectively correspond to the printer application the copier application the facsimile machine application and the scanner application illustrated in and an engine corresponds to the hardware resources in an xCS corresponds to processes in the control service layer such as the NCS DCS FCS ECS MCS and UCS .

As illustrated in in step S a rebooting failure occurs in the image processing apparatus . For example the failure is of type D and occurs for the first time and the SCS detects this failure.

In steps S through S notifications of operation suppression are sent from the SCS to the xCS the applications and the engine almost at the same time.

In steps S through S the component sections of the image processing apparatus which have received the notifications are driven to undertake operation suppression processing and send responses to the SCS . For example the SCS sets a timeout period of 3 minutes for receiving the responses from the component sections.

The operation suppression processing is a kind of post processing for appropriately terminating processes being executed so that rebooting can be executed safely. For example the operation suppression includes processing that prevents new operations by controlling an interface.

In step S the SCS requests the OCS to stop communications of an operational section driver but no response is obtained as being blocked in functions.

In step S the SCS notifies a user of completion of the automatic reboot process and displays an image to require the user to make confirmation.

As described above by suppressing operations of the component sections so as to abort those processes being executed and halt the interface the reboot process can be executed rapidly without residual sheets troubles with the HDD or data remnants.

However in the course of the automatic reboot process or the automatic notification process other failures may happen.

In an index X represents cases in which the response is made under the conditions that the automatic notification is made when a failure of type A occurs or when the failure of type D occurs but it is not a rebooting failure for example the failure of type D occurs for the second time when the count of a general counter for counting the number of the printing sheets increases toward 10 .

Meanwhile an index Y represents cases corresponding to the operations shown in and that is with the problems in the above cases X being eliminated.

Inspecting pattern and pattern in in pattern the automatic reboot process is started because of the first time failure of type D afterward when the second time failure of type D occurs in cases X the automatic reboot process is aborted and the automatic notification process is started.

However in this case because of control of suppression of operations of the component sections which is performed at the beginning of the reboot process the automatic notification function given by NRS does not work hence the automatic notification process cannot be executed successfully. In addition once transferring to the automatic notification process the count indicating the frequency of the type D failure is cleared thus if the type D failure happens again after the unsuccessful automatic notification the type D failure otherwise counted as the third one is treated as the first one and the automatic reboot process is executed again resulting in repeated execution of the automatic reboot process.

On the other hand in the pattern the second time failure is of type A because of operation suppression control similarly the automatic notification process cannot be executed successfully. Furthermore because the image processing apparatus is in a SP mode special mode the failure cannot be recovered from without a failure fixing operation by a service person just like failures of a fusing section. Hence after manual reboot the same failure of type A occurs.

In a usual way as in step S the automatic reboot process is executed and as in step S after a confirmation image is displayed on the screen the process is completed.

However if a failure of type A or type D occurs in the course of the process as in step S as in step S the automatic notification is performed when the automatic notification function is invalid an image for a service call is displayed on the screen and the process stops at a state of waiting for the power to be switched off on.

Due to this problem in the cases Y when other failures happen after the automatic reboot process is started information of the failure is written only in a log and execution of the automatic reboot process continues.

Then in step S another failure of type A or type D occurs in the course of the automatic reboot process.

In step S even when another failure of type A or type D occurs only the information of the failure is written in a log.

After the automatic reboot process is executed usually a confirmation image is displayed on the screen and then the automatic reboot process is completed as in step S.

If a failure which ought to be automatically reported occurs before step S for example in case of the failure of a fusing section a type A failure occurs surely as in step S automatic notification is performed when the automatic notification function is invalid an image for a service call SC is displayed on the screen as in step S. In this way appropriate operations are carried out according to the contents of the failures.

In order to reduce power consumption an image processing apparatus is often set to be in the energy saving mode. illustrates an automatic rebooting process when a rebooting failure occurs during the transition to the energy saving mode.

As illustrated in in step S a rebooting failure occurs in the image processing apparatus . For example the failure is of type D and occurs for the first time and the SCS detects this failure.

In steps S through S notifications of operation suppression are sent from the SCS to the xCS and the applications almost at the same time. The SCS does not send the notification of operation suppression to the engine because the SCS detected that the engine is substantially in a resting state due to transition to the energy saving mode.

In steps S through S the component sections of the image processing apparatus which have received the notifications are driven to undertake operation suppression processing and send responses to the SCS . For example the SCS sets a timeout period of 3 minutes for receiving the responses from the component sections.

The operation suppression processing is a kind of post processing for appropriately terminating processes being executed so that reboot can be executed safely. For example the operation suppression includes processing that prevents new operations by controlling an interface.

In step S because the engine is substantially in a resting state due to transition to the energy saving mode the SCS does not request to reset the engine nor switch off the power of the engine .

In step S the SCS notifies a user of completion of the automatic reboot process and displays an image to require the user to make confirmation.

In this way it is possible to appropriately carry out the reboot process even when the image processing apparatus is transiting to the energy saving mode.

The image processing apparatus of the present embodiment has the same configuration as illustrated in and . Below the same reference numbers are assigned to the same elements as in the first embodiment and overlapping descriptions are omitted.

The configuration shown in is basically the same as that in except that an operation abortion controller is included.

Specifically the SCS includes an automatic notification controller that automatically notifies a service center of the failure by using NRS New Remote Service when failures of type A or type D occur at a predetermined frequency for example the failures of type D have occurred twice when the count of the general counter for counting the number of the printing sheets increases to . The NRS is a diagnosis service utilizing the aforesaid CSS or a network.

Further the SCS includes an operation abortion controller that performs controls to abort operations of the hardware resources of the image processing apparatus such as an engine or the programs software group after the rebooting failure is detected and before the reboot process starts. For example the operation abortion may include abortion of jobs abortion of generation of new process control or others.

Further the SCS includes an operation suppression controller that performs controls to suppress operations of an engine or the programs after receiving a response indicating operation abortion. For example the operation suppression may include suppression of new operations suppression of communications between processes and suppression of access to the HDD.

As illustrated in in step S a rebooting failure occurs in the image processing apparatus . For example the failure is of type D occurs for the first time and the SCS detects this failure.

In steps S through S notifications of operation abortion are sent from the SCS to the xCS the applications and the engine via the SRM almost at the same time.

In steps S and S when the operation abortion processing is completed responses indicating operation abortion are sent to the SCS .

In steps S and S the engine is in a state not allowing new process control and sends a response indicating operation abortion to the SCS .

Then in steps S through S the SCS sends notifications of operation suppression to the xCS the applications and the engine via the SRM almost at the same time.

In step S the component sections of the image processing apparatus which have received the notifications are driven to undertake operation suppression processing. The operation suppression processing is a kind of post processing for appropriately terminating processes being executed so that rebooting can be executed safely. For example the operation suppression includes processing that prevents new operations by controlling an interface.

In steps S through S the SCS receives the responses from the component sections of the image processing apparatus.

In step S the SCS notifies a user of completion of the automatic reboot process and displays an image to require the user to make confirmation.

As illustrated in in step S a notification of starting a printing job is transmitted from the application to the xCS .

In step S receiving the notification from the application the xCS notifies the SCS to start a process of printing the first sheet.

In step S receiving the notification from the xCS the SCS notifies the engine to start the process of printing the first sheet.

In step S receiving the notification from SCS the engine starts to feed the first sheet and notifies the SCS that the first sheet is fed.

In step S receiving the notification from the SCS the xCS notifies the SCS to start a process of printing the second sheet.

In step S the engine starts to feed the second sheet and notifies the SCS that the second sheet is fed.

Next similarly in step S the xCS notifies the SCS to cancel the process of printing the second sheet.

In step S the engine attempts to cancel processes as much as possible. Assuming that the process of printing the first sheet is being executed and hence cannot be aborted immediately the engine executes printing of the first sheet and increments the count of the mechanical counter of the engine when fusing on the first sheet is completed.

In step S upon receiving the notification from the engine the SCS increments the count in the general counter of the controller.

In step S upon receiving the request from the SCS the engine increments the count in the counter of the charging device in the engine.

Afterward in step S when the first sheet is normally delivered the engine notifies the SCS of the normal delivery of the first sheet.

At this moment because of the operation abortion processing instead of the operation suppression processing the interface is not suppressed and the notification can be normally sent to the application .

Afterward In step S the engine cancels the process of printing the second sheet performs abnormal sheet delivery of the second sheet delivers the second sheet without its being printed and notifies the SCS of the abnormal delivery of the second sheet.

In step S because abortion of processes related to successive printing jobs is completed the xCS notifies the application of job completion.

In steps S S the SCS waits for responses indicating operation abortion from other components for example a time out period may be put on and starts the operation suppression process.

As described above once the first sheet is normally printed the engine mechanical counter the engine charging device counter the controller general counter of the and the controller charging device counter count the printing operation of the first sheet and increment counts of these counters correctly hence the counts in these counters are not in agreement and disagreement as in the related art does not occur.

In in steps S through S notifications of operation suppression are sent from the SCS to the xCS the applications and the engine .

In steps S through S the component sections of the image processing apparatus which have received the notifications are driven to undertake operation suppression processing and send responses to the SCS . For example the SCS sets a timeout period of 3 minutes for receiving the responses from the component sections.

The operation suppression processing is a kind of post processing for appropriately terminating processes being executed so that rebooting can be executed safely.

In step S the SCS requests the OCS to stop communications of an operational section driver but no response is obtained as being blocked in functions.

As described above by suppressing operations of the component sections so as to abort those processes being executed and halt the interface the reboot process can be executed rapidly without residual sheets troubles with the HDD or data remnants.

While the present invention has been described with reference to specific embodiments chosen for purpose of illustration it should be apparent that the invention is not limited to these embodiments but numerous modifications could be made thereto by those skilled in the art without departing from the basic concept and scope of the invention.

This patent application is based on Japanese Priority Patent Applications No. 2004 027232 filed on Feb. 3 2004 and No. 2004 033953 filed on Feb. 10 2004 the entire contents of which are hereby incorporated by reference.

