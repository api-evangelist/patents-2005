---

title: Automatic generation of a motion controller
abstract: A method for automatically creating a customized motion controller based on user input specifying desired characteristics of the motion controller. The method may compile the program into executable code and download the executable code to a target platform, thus enabling the target platform to function as the specified customized motion controller. User input may specify characteristics of the motion controller system such as: the target platform; the configuration of motors, sensors and I/O devices to be used; the supervisory control functions to be implemented; and the target language for the motion control program.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09285801&OS=09285801&RS=09285801
owner: National Instruments Corporation
number: 09285801
owner_city: Austin
owner_country: US
publication_date: 20050914
---
This application claims the benefit of U.S. Provisional Application No. 60 609 616 filed on Sep. 14 2004 entitled Programmatic Generation of a Motion Controller which is hereby incorporated by reference in its entirety as though fully and completely set forth herein.

This invention relates to motion controllers and more particularly to software tools allowing users to create motion control programs having user specified structure and functionality.

Dedicated motion control boards are available for performing motion control functions thus liberating host computers from the effort of performing these functions. A dedicated motion control board is typically configured to connect to a host computer one or more motor drive units and sensor devices that report the state e.g. position or velocity of the motors. Motor drive units are used to provide drive signals with sufficient voltage and current to operate the stepper and or servo motors. Dedicated motion control boards are generally not designed for user programmability and thus are fixed in their motion control architecture and components. A dedicated motion control board may allow a user to change the values of parameters and set bits to turn various features ON or OFF. However the inability to reprogram the motion control architecture or components is a severe limitation to the usefulness and cost effectiveness of dedicated motion control boards. A motion control system capable of performing motion control in a manner that is user programmable would be beneficial.

In the prior art a motion control program may be constructed manually by the user in a graphical programming environment such as LabVIEW or in a text based programming environment.

The diagram is the motion control program. The diagram may be compiled to form the motion control code.

In a text based programming environment the user may construct the motion control program by manually composing a text file or a set of text files containing statements conforming to a programming language. In particular the text file may include calls to routines in one or more predefined libraries. The routines in the predefined libraries allow the user to invoke various functions associated with supervisory control trajectory generation and control loop processing. A variety of embodiments are contemplated in order to support a corresponding variety of programming languages such as C C Java etc.

However many persons may not be sufficiently trained in the art of programming within one of the supported programming environments to successfully or efficiently complete the construction of the motion control program. Therefore an improved method is desired for creating a motion controller that does not require manual coding of the motion controller.

A motion control system may include a host computer a hardware platform motor drive units sensors and a set of I O devices. A user programmable motion control system may be created as follows. A host computer may receive user input specifying desired characteristics features functions system components and the desired motions of a physical system to be controlled by the motion controller. The desired characteristics specified by the user input may include supervisory control functions trajectory generation functions and loop processing functions. The host computer may then generate a program that realizes the desired characteristics based on the user input. The host computer may also compile the program into executable code in response to a user request for compilation. The host computer may download the executable code to the hardware platform and invoke execution of the executable code on the hardware platform in response to user requests for download and execution.

In some embodiments a method for programmatically generating a motion controller may include the steps of a receiving information from a user regarding characteristics of a desired motion controller and b generating a program where the program is executable to implement the motion controller according to said characteristics where the program is programmatically generated without direct user coding of the program.

The information from the user regarding characteristics of the motion controller may include at least one of platform type axes type motion I O devices i.e. motors and sensors functionality and additional I O devices.

In one set of embodiments the host computer may receive user inputs specifying a motion control program download executable code corresponding to the motion control program to a target platform and invoke execution of the executable code on the target platform. The target platform operates as a motion controller by executing the executable code.

The host computer may manage a graphical user interface through which the user may construct a diagram by selecting icons placing the icons in a graphical window and coupling the icons together with virtual wire connections. The user inputs are inputs defining the diagram.

Alternatively the host computer may manage a graphical user interface through which the user may construct a text file by entering textual statements conforming to a programming language. In this case the user inputs are inputs defining contents of the text file.

While the invention is susceptible to various modifications and alternative forms specific embodiments thereof are shown by way of example in the drawings and will herein be described in detail. It should be understood however that the drawings and description thereto are not intended to limit the invention to the particular form disclosed but on the contrary the invention is to cover all modifications equivalents and alternatives falling within the spirit and scope of the present invention as defined by the appended claims.

The following patent applications are hereby incorporated by reference in their entirety as though fully and completely set forth herein 

U.S. patent application Ser. No. 09 518 492 titled System and Method for Programmatically Creating a Graphical Program and filed on Mar. 3 2000 whose inventors are Ram Kudukoli Robert Dye Melanie Jensen and Yumiko Kawachi.

U.S. patent application Ser. No. 09 745 023 titled System and Method for Programmatically Generating a Graphical Program in Response to Program Information filed on Dec. 20 2000 invented by Kudukoli et al. is.

U.S. patent application Ser. No. 09 886 455 titled System and Method for Programmatically Generating a Graphical Program in Response to User Input filed on Jun. 20 2001 invented by Washington et al.

U.S. Patent Application publication number 20020129333 U.S. patent application Ser. No. 10 051 268 titled System and Method for Programmatically Generating a Graphical Program Based on a Sequence of Motion Control Machine Vision and Data Acquisition DAQ Operations filed on Jan. 18 2002 and invented by Chandhoke et al.

U.S. Patent Application Publication Number 20050049724 U.S. patent application Ser. No. 10 653 532 titled Re configurable Motion Controller Drive filed on Sep. 2 2003 invented by Chandhoke et al.

U.S. Patent Application Publication Number 20020191023 U.S. patent application Ser. No. 10 051 474 titled System And Method For Graphically Creating A Sequence Of Motion Control Operations published on Dec. 19 2002 and filed on Jan. 18 2002 invented by Chandhoke et al.

A motion control system may include a host computer a controller platform one or more drive units one or more motors one or more sensors and one or more I O devices as suggested in .

The controller platform may be connected to or in communication with the host computer the drive units the sensors and the I O devices .

The drive units may be configured to provide drive signals to the motors in response to signals received from the controller platform and sensors .

Sensors may provide feedback signals to the controller platform about the state of the motors and or of the physical systems driven by the motors. For example sensors may provide measurements of the angular position or velocity of each motor and or measurements of the linear position or velocity of the physical systems driven by the motors. Sensors may include quadrature encoders.

The feedback signals or some subset of the feedback signals may also be provided to the drive units .

The controller platform may include a processor memory host interface drive interface sensor interface and I O interface as illustrated in . The memory may include any of various kinds of RAM and any of various kinds of ROM. The processor is configured to execute programs stored in the memory . The programs may include a real time operating system and motion control code. By executing the motion control code the processor causes the controller platform to serve the function of a motion controller.

The sensor interface may include analog to digital A D converters to support the use of analog sensors.

The I O interface may include A D converters and digital to analog D A converters to support the use of analog input and output devices respectively.

The controller platform may also include one or more digital signal processors DSPs i.e. integrated circuits specialized for performing signal processing computations. In this case the motion control code may include code executable by the processor and code executable by the one or more DSPs.

In some embodiments the controller platform may include a field programmable gate array FPGA . In these embodiments at least a portion of the motion control code may be downloaded to the FPGA to provide the FPGA with at least some motion controller intelligence.

The controller platform may be realized by any of various systems or devices. For example in one set of embodiments the controller platform may be any one of the following hardware platforms developed and marketed by National Instruments Corporation 

In one embodiment of the motion control system the host computer couples to the drive units without an intervening controller platform i.e. controller platform is omitted. In this case the host computer performs the motion control function.

The I O devices may include input devices output devices and devices capable of both input and output. The identity of the I O devices will depend on the physical systems being controlled and the application the user intends to realize. The I O devices may include digital and or analog devices.

As illustrated in the host computer executes software that is operable to receive high level user input specifying desired functionality of a motion controller. The high level user input may include information indicating desired functionality of the motion controller as discussed in greater detail below as indicated in step . The high level user input may also include selecting a target controller platform from a set of supported platforms as indicated in step .

In response to the high level user input the software operates to automatically construct a motion controller program from fundamental functional units as indicated in step . The motion controller may be automatically constructed in a graphical programming environment such as LabVIEW or in a text based programming environment such as C C or Java.

In response to execution of the motion control code the target controller platform functions as a motion controller.

In one set of embodiments the set of supported platforms includes the National Instruments platforms listed above.

In some embodiments the set of supported platforms may include the host computer itself. If the host computer is selected as the target controller platform it is assumed that the host computer couples to the drive unit without an external controller platform intervening. Thus the motion control program is compiled into motion control code for execution by the host computer .

The motion control program may include modules for supervisory control trajectory generation and control loop processing. The functionality of each of these modules may be defined by the user in the programming environment.

The trajectory generation module may generate points along one or more user specified trajectories in response to trajectory control commands asserted by the supervisory control module .

The control loop processing module generates control signals for the drive units based on a command signals asserted by supervisory control module b a stream of set points generated by the trajectory generation module and c feedback signal data from sensors or derived from signals supplied by the sensors .

As noted above many persons may not be sufficiently trained in the art of programming within one of the supported programming environments to successfully or efficiently complete the construction of the motion control program. Furthermore even if a person is sufficiently trained he she may not desire to expend the time required to construct the motion control program. Thus in one set of embodiments the host computer may be configured to execute a software assistant that automates the process of constructing the motion control program. The software assistant is designed to perform automatic creation of the customized motion control program without requiring the above prior art manual user input that has been traditionally required to create a program.

In response to execution of the software assistant the host computer may perform the following steps as illustrated in .

In steps the host computer e.g software executing on the host computer operates to receive user input specifying desired functionality and or capabilities of the motion control program or motion controller . For example the software may present a graphical user interface GUI that guides the user in entering information that specifies desired capabilities of the motion control program.

In step the host computer receives and stores user input selecting a target platform from a displayed list of supported platforms such as PXI CVS CFP or CRIO .

In step the host computer receives and stores user input specifying the motors and sensors to be used in the motion control system. For example the user input may represent selections from a first displayed list of supported motors and a second displayed list of supported sensors. As another example the user input may specify a set of electrical characteristics for each motor and each sensor.

In step the host computer receives and stores user input specifying the I O devices to be used in the motion control system. For example the user input may represent selections from displayed lists of supported I O devices according to their various kinds. As another example the user input may specify a set of electrical characteristics for each I O device.

In step the host computer receives and stores user input selecting the supervisory control functions to be implemented by the motion control program. For example the user input may specify selections from displayed lists of supervisory control functions.

In step the host computer receives and stores user input selecting a target programming language from a displayed list of supported languages for the motion control program. In one embodiment the supported languages include LabVIEW C CVI and .NET.

Note that there is considerable flexibility in the order of input steps through and the order indicated by is suggestive not mandatory.

In step the host computer or software automatically generates a motion control program in the target programming language based on the user input received in steps through . The program generation step may involve a selecting subprograms from predefined libraries based on the user inputs and b integrating the selected subprograms to form the motion control program. Note that the term automatically as used herein refers to a software program creating the motion control program based on high level user input such as that received in steps through . In other words the term automatically as used herein does not include the type of manual creation of a program such as manual selection and manual interconnection of blocks to create a graphical program or manual entry of textual code as in the prior art. Rather the automatic creation of the motion control program may in one embodiment only require the user to provide high level information regarding desired functionality and capabilities and does not require the user to provide manual or direct user input to actually specify or code the code of the motion control program. For more information on automatic creation of programs please see the applications incorporated by reference above.

In step the host computer compiles the motion control program into motion control code executable by the target controller platform.

In step the host computer may invoke execution of the motion control code on the target controller platform.

One embodiment of host computer is illustrated in . Host computer may include at least one central processing unit CPU which couples to host bus . The CPU may be realized by any of various types of processor. For example CPU may be an x86 processor e.g. a Pentium class processor a PowerPC processor or a RISC processor from the SPARC family.

A memory medium typically including RAM and referred to as main memory is coupled to the host bus by means of a memory controller . The main memory may store program instructions executable by the CPU . The main memory may also store operating system software as well as other software for operation of host computer .

The host bus may be coupled to an expansion bus by means of a bus controller also referred to herein as bus bridge logic . The expansion bus may be a PCI Peripheral Component Interconnect expansion bus although busses of other types can be used. The expansion bus may include slots to support communication with various devices such as the controller platform video display card hard drive controller and I O devices not shown such as a keyboard mouse and speakers.

Numerous variations and modifications will become apparent to those skilled in the art once the above disclosure is fully appreciated. It is intended that the following claims be interpreted to embrace all such variations and modifications.

