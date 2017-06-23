---

title: Strategies for configuring media processing functionality using a hierarchical ordering of control parameters
abstract: Strategies for effectively discovering, selecting, configuring, and controlling components used in media processing applications are described. According to one exemplary implementation, the strategies described configure the components based on profile information, configuration information, and a hierarchical ordering of configuration parameters. The hierarchical ordering may combine different coding paradigms, where one or more high level nodes in the ordering may define configuration parameters which are common to multiple coding paradigms. In this ordering, selection of a configuration parameter may cascade down to affect lower-ranking dependent parameters in the hierarchical ordering. According to one advantage, the hierarchical ordering provides a more uniform, extensible, and problem-free approach to configuring components than unstructured approaches to configuration. Moreover, applications can utilize the hierarchical ordering at different levels of granularity.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08533597&OS=08533597&RS=08533597
owner: Microsoft Corporation
number: 08533597
owner_city: Redmond
owner_country: US
publication_date: 20050630
---
This application is a continuation in part of co pending U.S. patent application Ser. No. 10 676 722 the 722 application entitled Systems and Methods for Interfacing Media Components filed on Sep. 30 2003 and naming Glenn F. Evans et al. as inventors. The 722 application is incorporated herein by reference in its entirety.

A portion of the disclosure of this patent document contains material which is subject to copyright protection. The copyright owner has no objection to the facsimile reproduction by anyone of the patent disclosure as it appears in the Patent and Trademark Office patent files or records but otherwise reserves all copyright rights whatsoever.

Media processing applications sometimes incorporate third party components. For example a principal application may perform a high level media processing task such as DVD authoring and the high level task may in turn rely on one or more third party components to perform basic operations encompassed by the task such as compressing packetizing multiplexing and so on . An application may adopt this implementation strategy for various reasons. For example an application designer may wish to reduce the cost of the application by relying on existing third party components. Or an application designer may wish to rely on third party components rather than building such functionality into the application itself for license related reasons.

The task of selecting and configuring third party components may raise a number of challenges. First an application may have complex requirements. The pool of available components may have equally complex capabilities. It is a difficult task to match the requirements of an application with the capabilities of the components. Second it is a difficult task to ensure that the selected third party components work well together to achieve a desired end result. That is one third party component may have a set of features and configuration states which conflict with the features and configuration states of one or more other third party components. Such conflicts can produce a configuration having an inconsistent state which may cause the combination of components to perform in a suboptimal manner. Or such conflict may completely disable the combination of components. Third it is difficult to modify third party components to provide enhancements and extensions to existing configurations while still ensuring that these components consistently work with applications which may be unaware of such extensions.

The above challenges can be addressed in an ad hoc manner by a designing a custom configuration solution for each application. But this approach is problematic. For instance to avoid configuration problems this approach may require the application designer to have intimate familiarity with the media processing requirements of the application the capabilities of different components and the manner in which different components interact. This approach may also require the designer to have expert knowledge of complex algorithms used by different multimedia compression storage formats. Further this approach may also require the end user to have advanced knowledge of media processing options in order to properly interact with the application that is by inputting configuration parameters into the user interface presentations provided by the application. Any misstep by the application designer or the end user may produce an inconsistent state in the selected combination of components possibly rendering the application non functional. For example as appreciated by the present inventors the order in which configuration parameters are set is important if the parameters are not set in an appropriate order then the combination of components may be placed in an inconsistent state.

Moreover the ad hoc approach is generally not extensible meaning that it cannot be easily modified to suit variations in the application environment or the pool of available components. For instance any modification to the configuration settings may require difficult analysis and significant design modification to ensure that the changes do not produce an inconsistent state. Again this task may require expert knowledge in media processing arts.

According to another challenge the application designer may attempt to design media processing functionality that supports a wide variety of media storage formats. An application designer may address this objective by creating a complex abstraction software layer that makes different formats appear similar for user interface and configuration purposes. But this is a difficult task that adds complexity and cost to the media processing functionality. Such a cumbersome abstraction layer may also provide poor extensibility with respect to future modifications made to the application components media formats and so forth.

There is therefore an exemplary need for more satisfactory solutions for discovering selecting configuring and controlling components used in media processing applications.

This description sets forth strategies for more effectively discovering selecting configuring and controlling components used in media processing applications. According to one exemplary implementation the strategies configure the components based on profile information configuration information and a hierarchical ordering of configuration parameters. The hierarchical ordering may combine different coding paradigms. For example in one exemplary hierarchical ordering a top most node defines configuration parameters that apply to any component used in a combination of components such as any video encoder audio encoder multiplexer etc. regardless of coding paradigm. A second level of the ordering may contain a node that defines configuration parameters that apply to any video encoder regardless of coding paradigm another node that defines configuration parameters that apply to any audio encoder regardless of coding paradigm another node that defines configuration parameters that apply to any packetizer multiplexer regardless of coding paradigm and so forth. Still other subordinate layers in the hierarchical ordering may contain nodes associated with specific video encoder coding paradigms audio encoders coding paradigms and multiplexer coding paradigms and so forth. In this ordering the selection of a configuration parameter may cascade down to affect lower ranking dependent parameters in the hierarchical ordering.

According to another feature the components can be combined in a defined order wherein at least one downstream component is established prior to at least one upstream component.

The above approach has several benefits. According to one exemplary benefit the hierarchical ordering in conjunction with the use of profile information and configuration information provides a uniform approach to discovering selecting configuring and controlling media components. This approach eases the analysis burden in configuring components because it provides a well defined and consistent approach to selecting and configuring components. The approach also reduces the potential that a user or an automated mechanism will select and configure a combination of components that will produce an inconsistent state.

Further the approach offers improved versatility and extensibility over ad hoc approaches. As to versatility different applications can utilize the hierarchical ordering at different levels of granularity and configuration complexity and generality. For instance a first application may rely on the hierarchical ordering to configure a collection of components at a relatively low level of granularity setting only very general level configuration parameters. In this first application a variety of different coding paradigms can be applied to satisfy the application s requirements. On the other hand a second application may rely on the hierarchical ordering to configure a collection of components at a relatively high level of granularity that is by setting relatively detailed configuration parameters such as parameters that pertain to a specific coding paradigm . In this second application the parameters may specifically target one or more coding paradigms. In either case the applications can be configured to supply user interface presentations to the users which solicit only those fields of information that are relevant to configuring and controlling the applications. This feature helps reduce the complexity of the user interface presentations and improves the experience of the users when interacting with the applications.

As to extensibility the approach accommodates the introduction of new parameters. That is the approach allows new parameters to be integrated into the hierarchical ordering without requiring modification of the basic organization of the ordering itself.

Additional exemplary implementations and associated benefits are described in the following. It should be noted that the features described in this Summary section are intended to convey exemplary aspects of the subject matter described herein and are not intended to limit the scope of the subject matter described in the claim section.

The same numbers are used throughout the disclosure and figures to reference like components and features. Series numbers refer to features originally found in series numbers refer to features originally found in series numbers refer to features originally found in and so on.

This description sets forth exemplary strategies for discovering selecting configuring and controlling components for use in a media processing application.

As to terminology the term component refers to any unit designed to process information. A component can be implemented as a hardware unit software unit or a unit that comprises a combination of hardware and software. A component may comprise a single part such as a single piece of hardware and or software that is purchasable as a unit or it can comprise a combination of multiple such parts. In one case a component can be provided by a third party provider meaning that the entity which supplies the main media processing application is different than the entity which provides the component . In another case the component can be supplied by the same entity that provides the main media processing application.

The term media information refers to any data represented in electronic form that can be consumed by a user. The media information can include any information that conveys audio and or video information such as audio resources e.g. music spoken word subject matter etc. still picture resources e.g. digital photographs etc. moving picture resources e.g. audio visual television media programs movies etc. and so on.

The term media processing application refers to an application for processing media information to achieve any end result. One example of a media processing application is a DVD authoring application.

The term component module refers to a group of one or more components that are used in a media processing application. For example a codec grouping which combines encoders packetizers and a multiplexer is one example of a component module.

The term coding paradigm refers very broadly to a set of rules that apply to the interpretation creation and control of data. For a particular paradigm the rules may be promulgated by a standards organization by a commercial entity or some other source. For example MPEG Moving Picture Experts Group e.g. MPEG2 or ISO IEC 13818 defines one coding paradigm. SMPTE VC1 Society of Motion Picture Television Engineers standard VC1 also referred to as WMV or Windows Media Video defines another coding paradigm and so forth.

Generally any of the functions described with reference to the figures can be implemented using software firmware e.g. fixed logic circuitry manual processing or a combination of these implementations. The term logic module or functionality as used herein generally represents software firmware or a combination of software and firmware. For instance in the case of a software implementation the term logic module or functionality represents program code or declarative content that performs specified tasks when executed on a processing device or devices e.g. CPU or CPUs . The program code can be stored in one or more computer readable memory devices. More generally the illustrated separation of logic modules and functionality into distinct units may reflect an actual physical grouping and allocation of such software and or hardware or can correspond to a conceptual allocation of different tasks performed by a single software program and or hardware unit. The illustrated logic modules and functionality can be located at a single site e.g. as implemented by a processing device or can be distributed over plural locations.

Section A presents an overview of an exemplary system for creating a combination of components a configuration module for use in a media processing application. Section A also sets forth an exemplary manner of operation of the system.

Section B describes one exemplary component module that can be created using the system of Section A.

Section C describes an exemplary hierarchical organization of configuration parameters that can be used to create the component module of section B.

Section D describes an exemplary computer environment for implementing aspects of the system of Section A.

Section E constitutes a first appendix which forms an integral part of this disclosure setting forth an exemplary collection of configuration parameters that can be used to populate the hierarchical ordering of control parameters described in Section C.

Section F constitutes a second appendix which forms an integral part of this disclosure setting forth an exemplary program listing of a codecapi.h module that can be used to implement aspects of the configuration strategies.

The system includes a media processing application or just application for brevity for performing a media processing operation such as DVD authoring etc. . To perform its function the application may rely on a collection of components drawn from a pool of available components . As previously described the components can represent hardware units software units hybrid units implemented in both hardware and software and so forth. The components can be provided by the same entity which provides the application or by a different third party entity.

Broadly stated the components receive input media information video and or audio information provide some kind of transformation of the input information to provide transformed information and then output the transformed information. Exemplary kinds of components include various types of video encoders various types of audio encoders various types of packetizers and multiplexers and so forth. A video encoder refers to any kind of unit which transforms video information from one form to another. The video encoder may for instance compress the video information scale the video information change its color space and so forth. Similarly an audio encoder refers to any kind of unit which transforms audio information from one form to another. A packetizer refers to a unit which breaks video or audio information into packets having a defined size. Typically packets include headers and payloads the headers contain metadata which describes features of the information stored in the payloads such as timing related information associated with the information stored in the payloads. A multiplexer is a device which combines two or more signals into a composite signal. For example a multiplexer can receive a stream of video information and a stream of audio information and produce an output that comprises interleaved packets of video and audio information. The components can include yet other kinds of units not mentioned above.

Interface functionality allows the application to interact with the components . One function that the interface functionality can perform is to handle the registry of components . In performing this function the interface functionality records salient information e.g. metadata regarding new components added to the pool of available components . Another function that the interface functionality performs is to discover the available components and in particular to determine the components which are available that can perform one or more tasks required by the application . In performing this function the interface functionality can compare the requirements of the application with the capabilities of the components and select a group of components which satisfy the requirements. Another function that the interface functionality performs is to configure the selected components. In performing this function the interface functionality can set various parameters that govern the manner in which the selected components operate. According to another function the interface functionality can control the operation of the selected group of components collectively forming a component module and can monitor its operation. In performing this function the interface functionality can collect statistical information regarding the operation of the component module. The interface functionality can use this statistical information to improve the performance of the application . The following discussion provides more details regarding the above identified functions and other aspects of the interface functionality .

In terms of physical implementation the application and interface functionality can be implemented as two respective logic modules implemented in hardware and or software provided by a computing device. For example the application can be implemented as an application program and the interface functionality can be implemented as an application programming interface API . provides one illustrative example of a computing environment that can be used to implement the application and the interface functionality . In another exemplary implementation the application and the interface functionality can be implemented using two separate units. For example one or more features of the interface functionality can be implemented as a detachable card which is communicatively coupled to a computer device which implements the application . Still further implementation permutations are possible.

The components can likewise represent hardware and or software units which are physically implemented by the same mechanism which implements the application and or interface functionality . For example the components may represent software units which are executed by the same computer device which implements the application and or the interface functionality . Alternatively one or more of the components can be implemented by a unit such as a detachable card which is separate from but communicatively coupled to the device which implements the application and or interface functionality . Still further implementation permutations are possible.

In any event the interface functionality can include management logic for performing all the prescribed tasks assigned to the interface functionality . These tasks include at least the above identified operations such as registering components discovering components selecting components which match the requirements of the application configuring the components monitoring the operation of the components and so forth.

The interface functionality also includes a profile store . The profile store stores profiles. A profile specifies configuration information that can be used to select and configure a group of components to perform a prescribed task. For example a DVD profile can contain parameters used to configure a pipeline to produce a DVD compliant output stream. The profile can contain name information which identifies the profile encoder mux packetizer parameters and media type descriptions valid ranges associated with the operation of the component module to be built a list of capabilities to filter candidate components by a list of critical configuration parameters and so forth. The application can use a profile stored in the profile store to provide pre canned instructions to create a desired component module. For instance supposing that the application needs to perform function X it can identify in the profile store a profile Pwhich specifies how to create and configure a component module to perform function X. Actual creation of the component module comprises carrying out the instructions in the profile.

The interface functionality also includes a component capability store . The capability store stores capability lists. Each capability list describes the capabilities of a component such as the characteristics of the components its operating limitations and so forth. The application finds satisfactory components by comparing the requirements specified in a selected profile with the component capabilities advertised in the component capability store .

In one exemplary implementation different elements of the profiles capability lists and configuration parameters can be identified using appropriate identifiers such as GUIDs. For example each distinct capability of a component can be identified with a different GUID. These GUID identifiers help manage and locate desired components. For example a profile may specify one or more GUIDS enabling the management logic to determine whether there are any components which satisfy the features associated with the GUIDs by determining if there are matching GUIDs in the component capability store .

Although not shown in the interface functionality can also include a store for storing a hierarchical listing of configuration parameters used to configure a component module in the manner to be described below .

In step of the procedure the management logic receives a request to perform a task which will require the use of a component module.

In step the management logic locates a profile in the profile store associated with the desired task. As mentioned above the located profile describes how to create and configure a component module that will perform the desired task.

In step the management logic can find the component or components in the pool of available components which can perform the selected profile. As mentioned above this can be performed by matching the requirements of the profile with the attributes specified in the component capability store . In one case this matching procedure can have at least two phases. In a first phase the management logic can identify components for which there is an express one to one match between specified application requirements and component capabilities. If all the requirements are not met in the first phase in a second phase the management logic can re examine any component for which there is no express match but which might nevertheless possess the features necessary to satisfy the application requirements. For example an application requirement might state find a component that has property Y. The first pass examines the component capability store to determine whether there are any components which expressly state that they have the desired property. Some components may expressly state that they do not have this feature. These components are excluded from the search. But other components might not advertise that they have the desired feature but may nonetheless still possess this feature. In the second phase the management logic will attempt to satisfy unmet requirements by re examining any component which does not expressly conflict the application s requirements.

In step the management logic constructs the component module which will perform the desired task using the components selected in step . The component module is created in a specific manner e.g. by adding components in a specified order and setting configuration parameters in a specified order. This restraint helps reduce the possibility that the component module will be placed in an inconsistent state. As previously described an inconsistent state is a state in which one component includes settings or requirements which conflict with the settings or requirements of another component or components . An inconsistent state may impair the performance of the application or completely disable the application .

Although not shown in after the component module is created the procedure can monitor the performance of the component module. This is useful in order to collect statistical information regarding the operation of the component module so as to improve the performance of the component module and so forth. The interface functionality can collect performance data by registering one or more events upon the occurrence a registered event during the operation of the component module the interface functionality can log the event for use in forming statistics.

In one exemplary implementation in performing the above operations the potential candidate components can be enumerated and pre filtered without actually creating an instance of each component. This feature makes the processing described above more efficient.

The origin may represent an original capture device which first produces the information. For example the origin may represent a video camera which captures audio visual information. Alternatively the origin may represent any kind of source of pre recorded information such as audio visual information retrieved from a file a disk a tape a digital network and so forth. The destination may likewise have different connotations depending on different implementations. In one case the destination may represent a storage that is used to receive the transformed information produced by the component module . In another case the destination may represent an output device such as any kind of audio visual output device for presenting the transformed information. A television is one such output device. In another case the destination may represent some target site coupled to a digital network. These are merely representative examples of possible origins and destinations .

The specific combination of components shown in performs an operation in which video information and audio information are encoded and then this encoded information is broken up into packets which are interleaved together to form a final output result. More specifically the source information received form the origin may include two components video information and audio information . A video encoder encodes the video information while an audio encoder encodes the audio information . Encoding can comprise transforming the information in any way such as by compressing the information changing the color space of the information and so forth.

A video packetizer receives the output of the video encoder and breaks this output up into a series of video packets. An audio packetizer receives the output of the audio encoder and breaks this output up into a series of audio packets. As described above each packet can include header information and payload information. The header information contains metadata which describes the payload information. For example the header information may include timestamp information which describes the timing at which the information contained in the payload was captured received or otherwise subjected to some identified processing. shows the packetizers as forming discrete units which are coupled to the output of the encoders . This is one possibility. In another case however the packetizers can be integrated into the respective encoders . In another case the packetizers can be integrated in the multiplexer .

The multiplexer itself receives the output of the packetizers and combines the packetized video information with the packetized audio information into a single stream of information. The multiplexer can perform this combination by interleaving the video information with the audio information according to a defined format. The component module then forwards the interleaved stream to the destination .

To repeat the composition of the component module shown in is merely exemplary. Other arrangements are possible.

According to one exemplary implementation the interface functionality creates the component module in a predefined order so as to reduce the possibility of producing an inconsistent state. Generally the build process proceeds by constructing the pipeline topology from the multiplexer to the encoders. The following presents an overview of an exemplary build order 

In one case the pipeline is constructed using a profile. The following exemplary list of operations describes one way of creating the component module using the profile 

One general feature of the exemplary approach described above is that a component can be configured and then logically connected to a downstream component. By virtue of this feature it is possible to effectively address in a structured manner many conflicts and ambiguities that may occur in the course of component configuration. For example a typical problem occurs when the source image size does not match the image size specified for a particular encoding task. For instance DVD movies are typically compressed at a resolution of 720 480 pixels. If the source content is at 1920 1080 pixels then it may be unclear which component in a combination of components should scale e.g. shrink the image to the appropriate size. By configuring the output resolution setting on the encoder the encoder can choose to scale down the input content if possible. If the encoder is unable to scale down the image resolution then this component can indicate e.g. by connection failure to the entity building the topology that the image source needs to scale down the size of the image. If that option fails then the entity can create a generic image processing object to reduce the size of the image.

In general the parameters shown in define a collection of nodes. The nodes form a tree of parameters where each node may have one or more child nodes and each child node may have in turn one or more of its own child nodes and so forth. The parameters become increasingly more detailed as the tree is traversed from top to bottom. For example one or more top level nodes define a collection of parameters which may apply to a wide variety of components and coding paradigms. In this sense these parameters define component agnostic and coding paradigm agnostic settings. On the other hand lower level parameters may more narrowly pertain to specific components and or coding paradigms.

One general characteristic of the ordering is top down configuration dependence. According to this characteristic a change in a top level parameter in the ordering may affect lower ranking dependent parameters if they exist . In another words if a change is made to a parent parameter then the interface functionality may propagate this change down the ordering to make complementary changes to child parameters grandchild parameters and so forth. For example a user may select a parameter associated with a relatively high level node. This parameter may create a conflict with pre existing child node parameters requiring a change to be made to the child node parameters to rectify this conflict. In some cases rectifying a conflict may require disabling one or more components or features of components that serve no useful function after a change has been made to a top level parameter.

The use of the hierarchical ordering shown in has numerous benefits. According to one benefit the application can configure the component module at various levels of granularity depending on the demands of the application. For example one application can allow a user to configure the component module or can automatically configure the component module at a relatively high level setting only general parameters relevant to certain broad aspects of the operation of the component module . On the other hand another application can allow a user to configure the component module or can automatically configure the component module at a relatively detailed level setting a number of format specific parameters that serve to fine tune the operation of the component module . This variable grained approach is advantageous because it does not burden the user by requiring the user to specify a host of parameters which have no bearing on performance features that the user considers important. To repeat regardless of the level of detail in which an application configures a component module it draws from the same stock ordering essentially exposing different depths of the ordering in configuring the component module.

According to another general benefit the strong ordering shown in helps reduce the potential that the component module will be configured in a manner that will produce an inconsistent state. In one exemplary implementation parameters should be generally defined in a top down manner in which the user makes top level parameter selections prior to lower level parameter selections. In those cases where the user is permitted to make configuration choices the application can tailor the user interface presentations as selection progresses that is by removing selection options that no longer pertain to a prevailing state of a configuration operation.

According to another benefit the ordering shown in represents a standardized approach to configuring component modules. Such standardization produces a highly extensible design approach. Namely the ordering permits new configuration parameters to be orderly added to the tree and out of date configuration parameters to be removed from the tree without requiring detailed re engineering of the configuration strategy as a whole. New configuration parameters are added to the existing order at an appropriate location in the tree based on the classification of the new parameters.

With the above introduction further details will be provided below regarding exemplary nodes within the ordering . Section E below provides yet more detailed information regarding the parameters shown in .

To begin with a top level node represents parameters that apply to any component within the component module including encoders packetizers multiplexers and so forth . This node also represents parameters that can apply to any coding paradigm used by the components. The parameters associated with this node are therefore relatively basic and general purpose in nature.

At the next level node represents parameters that apply to any kind of video encoder regardless of the coding paradigm used by the video encoder. Node represents parameters that apply to any kind of audio encoder regardless of the coding paradigm used by the audio encoder. Node represents parameters that can apply to any packetizer and or multiplexer regardless of coding paradigm. Note that the packetizers and multiplexer may represent distinct components in the component module or the packetizers may be combined with the encoders or the multiplexer at this level of explanation however the packetizers and multiplexers are lumped together as a single topic of explication. 

At the next level in the hierarchical ordering nodes and represent parameters that pertain to broad classes of defined video coding paradigms. Nodes and represent parameters that pertain to broad classes of audio coding paradigms. Although only two video coding paradigms and two audio coding paradigms are shown in the reader will appreciate that the ordering can include additional coding paradigms.

At the next level nodes and represent parameters that pertain to two particular species of the general video coding paradigm associated with node . Nodes and represent parameters that pertain to two particular species of the general audio coding paradigm associated with node . Although only two video coding paradigm species and two audio coding paradigm species are shown in the reader will appreciate that the ordering can include additional coding paradigm species. Moreover there can be yet further levels in the ordering not shown in .

In the next level node represents MPEG Moving Picture Experts Group parameters that are specifically associated with the MPEG coding paradigm. Node represents SMPTE VC1 Society of Motion Picture Television Engineers standard VC1 also referred to as WMV or Windows Media Video parameters that are specifically associated with the WMV coding paradigm. Node represents AC3 Audio Coding Revision 3 parameters that are specifically associated with the AC3 coding paradigm. Node represents WMA Windows Media Audio parameters that are associated with the WMA coding paradigm.

In the next level nodes and represent two specific MPEG coding paradigms for processing video information namely the MPEG1 standard ISO IEC 11172 and the MPEG2 standard ISO IEC 13818 . Although not shown the hierarchical ordering can also incorporate a node corresponding to the H.264 standard MPEG 4 Part 10 ISO IEC 14496 10 Advanced Video Coding AVC as well as other formats.

Once again the nodes shown in may represent a sampling of a more encompassing tree of configuration nodes not shown . In other words the ordering can encompass more nodes not shown associated with additional kinds of components coding paradigms and so forth.

In step the interface logic receives the user s selection of a parameter that has at least one child parameter dependent thereon. Or step may indicate the receipt of an automatic selection of a parameter.

In step the interface logic determines whether the high level change requires any complementary changes to made in dependent lower level parameters and if so makes those changes. If appropriate step can involve notifying the user of the need to make certain selections and receiving input from the user to reflect the user s choices.

As described above certain aspects of the system shown in can be implemented using a computer device. For example certain aspects of the application interface functionality and components can be implemented by a computing device. In another implementation one or more aspects of the system can be implemented by a separate device such as a processing card which interacts with the computer device. In any event shows an exemplary computer environment which can implement aspects of the system shown in .

The computing environment includes a general purpose or sever type computer and a display device . However the computing environment can include other kinds of computing equipment. For example although not shown the computer environment can include hand held or laptop devices set top boxes game consoles etc. Further shows elements of the computer environment grouped together to facilitate discussion. However the computing environment can employ a distributed processing configuration. In a distributed computing environment computing resources can be physically dispersed throughout the environment.

Exemplary computer includes one or more processors or processing units a system memory and a bus . The bus connects various system components together. For instance the bus connects the processor to the system memory . The bus can be implemented using any kind of bus structure or combination of bus structures including a memory bus or memory controller a peripheral bus an accelerated graphics port and a processor or local bus using any of a variety of bus architectures.

Computer can also include a variety of computer readable media including a variety of types of volatile and non volatile media each of which can be removable or non removable. For example system memory includes computer readable media in the form of volatile memory such as random access memory RAM and non volatile memory such as read only memory ROM . ROM includes an input output system BIOS that contains the basic routines that help to transfer information between elements within computer such as during start up. RAM typically contains data and or program modules in a form that can be quickly accessed by processing unit .

Other kinds of computer storage media include a hard disk drive for reading from and writing to a non removable non volatile magnetic media a magnetic disk drive for reading from and writing to a removable non volatile magnetic disk e.g. a floppy disk and an optical disk drive for reading from and or writing to a removable non volatile optical disk such as a CD ROM DVD ROM or other optical media. The hard disk drive magnetic disk drive and optical disk drive are each connected to the system bus by one or more data media interfaces . Alternatively the hard disk drive magnetic disk drive and optical disk drive can be connected to the system bus by a SCSI interface not shown or other coupling mechanism. Although not shown the computer can include other types of computer readable media such as magnetic cassettes or other magnetic storage devices flash memory cards CD ROM digital versatile disks DVD or other optical storage electrically erasable programmable read only memory EEPROM etc.

Generally the above identified computer readable media provide non volatile storage of computer readable instructions data structures program modules and other data for use by computer . For instance the readable media can store the operating system application specific functionality including functionality for implementing aspects of the application other program modules and program data . One or more of the above identified computer readable media can also implement aspects of the interface functionality and the components . In cases were one or more of the components represent hardware units not shown in these units can interact with the components shown in through appropriate coupling interfaces such as coupling mechanisms associated with processing cards .

The computer environment can include a variety of input devices. For instance the computer environment includes the keyboard and a pointing device e.g. a mouse for entering commands and information into computer . The computer environment can include other input devices not illustrated such as a microphone joystick game pad satellite dish serial port scanner card reading devices digital or video camera etc. Input output interfaces couple the input devices to the processing unit . More generally input devices can be coupled to the computer through any kind of interface and bus structures such as a parallel port serial port game port universal serial bus USB port etc.

The computer environment also includes the display device . A video adapter couples the display device to the bus . In addition to the display device the computer environment can include other output peripheral devices such as speakers not shown a printer not shown etc.

Computer operates in a networked environment using logical connections to one or more remote computers such as a remote computing device . The remote computing device can comprise any kind of computer equipment including a general purpose personal computer portable computer a server etc. Remote computing device can include all of the features discussed above with respect to computer or some subset thereof.

Any type of network can be used to couple the computer with remote computing device such as the WAN of a LAN etc. The computer couples to the network via network interface e.g. the interface shown in which can utilize broadband connectivity modem connectivity DSL connectivity or other connection strategy. Although not illustrated the computing environment can provide wireless communication functionality for connecting computer with remote computing device e.g. via modulated radio signals modulated infrared signals etc. .

This section provides additional information regarding one exemplary implementation of the ordering of parameters introduced in the context of and associated topics.

By way of preliminary remarks the configuration parameters can be identified using GUIDs. A GUID value is encoded as a string e.g. 08bdf183 f2f2 4c80 ba86 0fd5257561c9 . But in other implementations the configuration parameters can be identified using other kinds of identifiers.

In most cases the names assigned to the parameters and attributes reflect the respective roles served by the parameters and attributes. Thus many of the parameters and attributes are self explanatory based on the assigned names themselves.

The common parameters identify a set of parameters that are common to all encoders packetizers and multiplexers etc. and which apply to all coding paradigms. Exemplary common parameters are described below.

An AVEncCommonFormatConstraint configuration parameter identifies for the encoder a target format for parameter legalization. Exemplary settings associated with this configuration parameter include 

An AVEncCodecType configuration parameter indicates the types of coding schemes supported by a component. This configuration parameter can specify the following exemplary types 

An AVEncCommonRateControlMode configuration parameter describes the rate control mode to be used e.g. constant bit rate CBR variable bit rate VBR or quality mode. This parameter can specify the following exemplary settings 

RateQuality indicates that compression is driven by a quality target controlled by CommonQuality identifying a threshold quality to be maintained in the encoding operation.

An AVEncCommonLowLatency configuration parameter indicates that the output stream should be structured to have a low decoding latency. For example in video this setting limits the GOP structures that are allowed in an encoder to facilitate quick switches. For example it is normally prudent in MPEG processing to start the presentation of information at a key frame rather than a difference frame e.g. a B or P frame. This requirement however imposes a delay because the encoder must wait for a key frame to start presenting the information. A low latency mode modifies the presentation of information such that it accommodates quick switches e.g. by presenting only key frames etc. .

An AVEncCommonMultipassMode configuration parameter indicates a number of passes supported by the encoder. More specifically the encoder can process information in multiple passes. Often for instance the encoder applies a first pass to collect statistical parameters that provide information regarding the nature of the encoding task and then the encoder applies a second pass to rebalance and better optimize the processing based on the statistical parameters collected in the first pass. With the AVEncCommonMultipassMode configuration parameter users can select a number of passes within an available range. AVEncCommonPassStart described below is used to select which pass is active.

An AVEncCommonPassEnd configuration parameter ends the pass by writing TRUE . Writing FALSE aborts the multi pass operation.

An AVEncCommonRealTime configuration parameter informs the encoder that the application requires real time performance. This parameter can specify the following exemplary settings 

An AVEncCommonQuality parameter if available controls the quality during non bit rate constrained encoding. This parameter can specify the following exemplary settings 

An AVEncCommonQualityVsSpeed configuration parameter defines quality verses speed tradeoff considerations. This parameter can specify the following exemplary settings 

An AVEncCommonMeanBitRate configuration parameter specifies an average long term bit rate target for CBR or VBR rate control modes. This parameter supports media processing functionality that has only a restricted set of allowed bit rates such as MPEG1 audio.

An AVEncCommonMeanBitRateInterval configuration parameter indicates the interval that an average bit rate is specified over e.g. 100 ns units . For two pass VBR a value of 0 specifies the entire content. For a single pass CBR a value of 0 specifies that the component can choose the interval e.g. 0.5 sec .

An AVEncCommonMaxBitRate configuration parameter specifies a maximum bit rate and applies to CBR or VBR rate control modes.

An AVEncCommonMinBitRate configuration parameter specifies a minimum bit rate and applies to CBR or VBR rate control modes. A forced minimum bit rate can be achieved by increasing the quality. One use of this parameter is to prevent the encoder from compressing certain information to the point where the media processing functionality emits no output data which has the tendency to stall the media processing functionality . This can happen for example when an encoder compresses a black image. The minimum bit rate parameter prevents the encoder from reducing its output to zero and thereby reduces the potential of such stalls.

An AVEncCommonBufferSize configuration parameter specifies the size of the buffer to be used during encoding. This parameter applies to CBR or PeakVBR rate control modes. For MPEG this parameter defines the VBV buffer size.

An AVEncCommonBufferInLevel configuration parameter specifies an initial level of the buffer to support concatenation of streams. This parameter applies to CBR or PeakVBR rate control modes. For MPEG video this parameter defines the initial VBV buffer level.

An AVEncCommonBufferOutLevel configuration parameter specifies a level of the buffer at the end of an encoding operation to support concatenation of streams. This parameter applies to CBR or PeakVBR rate control modes. For MPEG video this parameter defines the VBV buffer level at the end of the encoding operation. In general one use of the AVEncCommonBufferInLevel and AVEncCommonBufferOutLevel configuration parameters is to facilitate video editing operations e.g. by better controlling the amount of information that is passed into and pulled out of the buffer during a video editing operation.

An AVEncCommonStreamEndHandling configuration parameter specifies the manner in which a stream is encoded upon its termination. For example a stream end event may truncate information that is being presented. The AVEncCommonStreamEndHandling configuration parameter defines how the encoder handles this truncation e.g. by permitting an incomplete truncation or by fixing up the truncation such that the encoder is allowed to encode data up to a more graceful termination point. More specifically this parameter can specify the following exemplary settings 

An AVEncStatCommonCompletedPasses configuration parameter indicates a completed number of passes. This parameter is therefore meaningful for multi pass encoding operations.

An AVEncVideoOutputFrameRate configuration parameter specifies an output frame rate defined by a numerator denominator ratio specifying frames second. This parameter can specify the following exemplary settings 

An AVEncVideoOutputFrameRateConversion configuration parameter provides output frame rate conversion control if the input frame rate does not match the desired output frame rate. This parameter can specify the following exemplary settings 

An AVEncVideoPixelAspectRatio control parameter defines a PixelAspectRatio width height. This parameter can specify the following exemplary settings 

An AVEncVideoForceSourceScanType configuration parameter indicates the nature of the output. This parameter can specify the following exemplary settings 

An AVEncVideoNoOfFieldsToEncode configuration parameter defines a number of fields to encode. This is to support telecine modes. The value 0 specifies no limit.

An AVEncVideoNoOfFieldsToSkip configuration parameter defines a number of fields to skip prior to encoding.

An AVEncVideoEncodeDimensionconfiguration parameter specifies the spatial dimensions of the coded stream if less than the connected input source. This parameter can be used for cropping.

An AVEncVideoEncodeOffsetOrigin configuration parameter operates in conjunction with AVEncVideoEncodeDimension. This parameter specifies the start top left offset position of the coded image for cropping purposes.

An AVEncVideoDisplayDimension configuration parameter specifies the desired display dimension of the coded stream during decode.

An AVEncVideoOutputScanType configuration setting specifies the manner in which the encoder is to interlace the output. This parameter can specify the following exemplary settings 

An AVEncVideolnverseTelecineEnable configuration parameter enables internal inverse telecine when processing interlaced input. For external telecine control output scantype can be set to same as input. 

An AVEncVideolnverseTelecineThresholdLinear configuration parameter specifies a linear range that controls a level at which the encoder considers a video field redundant and thereby can be treated as a film frame. This parameter is useful for performing inverse telecine from analog sources. This parameter can specify the following exemplary boundary settings 

An AVEncVideoSourceFilmContent configuration parameter provides a hint to the encoder as to the video source type with regard to film content. This parameter can specify the following exemplary settings 

An AVEncVideoSourcelsBW configuration parameter indicates whether the video source contains color. This parameter can specify the following exemplary settings 

An AVEncVideoFieldSwap Bool configuration parameter reverses the interlaced fields in the video source image. This parameter can specify the following exemplary settings 

AVEncVideohiputChromaResolution and AVEncVideoutputChromaResolution configuration parameters specify the chroma subsampling structure. These parameters can specify the following exemplary settings 

AVEncVideoInputChromaSubsampling and AVEncVideoOutputChromaSubsampling configuration parameters specify the chroma subsampling structure used to describe the relationship of the chroma to the luma data. These parameters can specify the following exemplary settings 

AVEncVideohnputColor Primaries and AVEncVideoOutputColor Primaries configuration parameters specify the color primaries for output and default for input if not given . These parameters can specify the following exemplary settings 

AVEncVideoInputColorTransferFunction and AVEncVideoOutputColorTransferFunction configuration parameters specify the transfer parameter variation of gamma used to code data. These parameters can specify the following exemplary settings 

AVEncVideoInputColorTransferMatrix and AVEncVideoOutputColorTransferMatrix configuration parameters specify the conversion matrix used to convert from RGB to YCbCr. These parameters can specify the following exemplary settings 

AVEncVideoInputColorLighting and AVEncVideoOutputColorLighting configuration parameters specify the intended lighting conditions on the input if not specified and output data. These parameters can specify the following exemplary settings 

AVEncVideoInputColor NominalRange and AVEncVideoOutputColor NominalRange configuration parameters specify the nominal range that 0 to 1 is mapped to for RGB formats such as 0 to 255 or 16 to 235 . These parameters can specify the following exemplary settings 

An AVEncInputVideoSystem configuration parameter specifies the video system of the content. This parameter can specify the following exemplary settings 

An AVEncVideoHeaderDropFrame configuration parameter specifies the setting of the drop frame flag in the GOP Header.

An AVEncVideoHeaderHours configuration parameter specifies the starting hours in the GOP header e.g. 0 to 59.

An AVEncVideoHeaderMinutes configuration parameter specifies the starting minutes in the GOP header e.g. 0 to 59.

An AVEncVideoHeaderSeconds configuration parameter specifies the starting seconds in the GOP header e.g. 0 to 59.

An AVEncVideoHeaderFrames configuration parameter specifies the starting frames in the GOP header e.g. 0 to 24 or 0 to 29 or 0 to 23 for film.

An AVEncVideoDefaultUpperFieldDominant configuration parameter sets the field dominance of the input video.

An AVEncVideoCBRMotionTradeoff configuration parameter indicates the tradeoff between motion and still images when performing CBR encoding. This parameter can specify the following exemplary settings 

An AVEncVideoCodedVideoAccessUnitSize configuration parameter specifies access unit size and is used for still image applications in VBR rate control .

An AVEncStatVideoOutputFrameRate configuration parameter specifies the average frame rate in frames per second of video content. This value can be obtained after the completion of encoding.

An AVEncStatVideoCodedFrames configuration parameter specifies the number of video frames encoded by the media processing functionality. This value is equal to AVEncStatVideoTotalFrames minus any frames that were dropped due to bit rate constraints or end of stream handling issues.

An AVEncStatVideoTotalFrames configuration parameter specifies the number of video frames passed to the media processing functionality.

An AVEncAudioInputChannelCount configuration parameter specifies the total number of audio input channels to be coded.

An AVEncAudioChannelConfig configuration parameter specifies the number of coded channels. This parameter can specify the number of coded channels as follows 

An AVEncAudioIntervalToEncode configuration parameter specifies the audio interval to encode. The value 0 specifies that no limit applies.

An AVEncAudioIntervalToSkip configuration parameter specifies an audio interval to skip used in conjunction with IntervalEncode to perform range encodings .

An AVEncAudioMapDestChannel0 configuration parameter specifies the destination channel 0 mapping to source channel zero based mapping.

An AVEncAudioMapDestChannel1 configuration parameter specifies the destination channel 1 mapping to source channel zero based mapping.

An AVEncAudioMapDestChannel2 configuration parameter specifies the destination channel 2 mapping to source channel zero based mapping.

An AVEncAudioMapDestChannel3 configuration parameter specifies the destination channel 3 mapping to source channel zero based mapping.

An AVEncAudioMapDestChannel4 configuration parameter specifies the destination channel 4 mapping to source channel zero based mapping.

An AVEncAudioMapDestChannel5 configuration parameter specifies the destination channel 5 mapping to source channel zero based mapping.

An AVEncAudioMapDestChannel6 configuration parameters specifies the destination channel 6 mapping to source channel zero based mapping

An AVEncAudioMapDestChannel7 specifies the destination channel 7 mapping to source channel zero based mapping.

An AVEncAudioInputContent configuration parameter provides a hint to the encoder that the content is either voice or music. This parameter can specify the number of coded channels as follows 

An AVEncStatAudioPeakPCMValue configuration parameter specifies the highest volume level occurring in audio content. This value can be obtained upon the completion of encoding.

An AVEncStatAudioAveragePCMValue configuration parameter specifies the average volume level occurring in audio content. This value can be obtained upon the completion of encoding.

An AVEncStatAudioAverageBPS configuration parameter specifies the average bits per second for quality based VBR audio. This value is also available after encoding.

An AVEncMPVGOPSize configuration parameter specifies the maximum distance in pictures from one GOP header to the next GOP header.

An AVEncMPVGOPOpen configuration parameter specifies whether the encoder produce closed GOPs. This parameter can specify the following exemplary settings 

An AVEncMPVDefaultBPictureCount configuration parameter specifies the default number of consecutive B pictures to be used between key frames I P . The encoder uses this as a hint to the default GOP structure.

An AVEncMPVProfile configuration parameter specifies the profile e.g. MP. This parameter can specify the following exemplary settings 

An AVEncMPVLevel configuration parameter specifies the level e.g. ML. This parameter can specify the following exemplary settings 

An AVEncMPVFrameFieldMode specifies the coding mode of a picture. Specifying field mode will produce an MPEG picture for each source image field. Specifying frame mode will produce a single MPEG picture for each field pair. This parameter can specify the following exemplary settings 

An AVEncMPVAddSeqEndCode configuration parameter specifies that a sequence end code should be added at the end of the stream. This parameter can specify the following exemplary settings 

An AVEncMPVUseConcealmentMotionVectors configuration parameter specifies the use of error concealment motion vectors namely 0 off and 1 on.

An AVEncMPVSceneDetection configuration parameter specifies the way in which scene detection should be handled by the encoder with regard to GOP structures and bit allocation. This parameter can specify the following exemplary settings 

An AVEncMPVGenerateHeaderSeqExt configuration parameter specifies that sequence extension headers are generated namely 0 no header and 1 generate header.

An AVEncMPVGenerateHeaderSeqDispExt configuration parameter specifies that sequence display extension headers are generated namely 0 no header and 1 generate header.

An AVEncMPVGenerateHeaderPicExt configuration parameter specifies that picture extension headers are generated namely 0 no header and generate header.

An AVEncMPVGenerateHeaderPicDispExt configuration parameter specifies that picture display extension headers are generated namely 0 no header 1 generate header.

An AVEncMPVGenerateHeaderSeqScaleExt configuration parameter specifies that sequence scaleable headers are generated namely 0 no header and generate header.

An AVEncMPVScanPattern configuration parameter specifies the macroblock scan pattern. This parameter can specify the following exemplary settings 

An AVEncMPVIntraDCPrecision configuration parameter specifies the DC Precision in bits e.g. 8 11 is the usual range . The value 0 indicates that the encoder automatically selects.

An AVEncMPVQScaleType configuration parameter specifies the quantizer scale behavior. This parameter can specify the following exemplary settings 

An AVEncMPVIntraVLCTable configuration parameter specifies the use of an alternate VLC table instead of a standard MPEG1 table. This parameter can specify the following exemplary settings 

An AVEncMPVQuantMatrixIntra configuration parameter specifies intra matrix coefficients used by the encoder.

An AVEncMPVQuantMatrixNonIntra configuration parameter specifies non intra matrix coefficients used by the encoder.

An AVEncMPVQuantMatrixChromaIntra configuration parameter specifies chroma intra matrix coefficients used by the encoder.

An AVEncMPVQuantMatrixChromaNonIntra configuration parameter specifies chroma non intra matrix coefficients used by the encoder.

An AVEncMPALayer configuration parameter specifies the coding layer to be used. This parameter can specify the following exemplary settings 

An AVEncMPACodingMode configuration parameter specifies the coding mode. This parameter can specify the following exemplary settings 

An AVEncDDService configuration parameter specifies the service provided by the bit stream. This parameter can specify the following exemplary settings 

An AVEncDDDialogNormalization configuration parameter specifies the dialog normalization level in dB.

An AVEncDDCentreDownMixLevel configuration parameter specifies the center down mix level in dB e.g. 30 dB 45 dB 60 dB 

An AVEncDDSurroundDowrMixLevel configuration parameter specifies the surround down mix level in dB e.g. 30 dB 45 dB 60 dB 

An AVEncDDSurroundMode configuration parameter specifies the surround mode. This parameter can specify the following exemplary settings 

An AVEncDDProductionInfoExists configuration parameter specifies that the audio production information is present in the stream.

An AVEncDDProductionRoomType configuration parameter specifies the room type in the audio production information. This parameter can specify the following exemplary settings 

An AVEncDDProductionMixLevel configuration parameter specifies the mix level in the audio production information in dB.

An AVEncDDOriginalBitstream configuration parameter specifies whether the content is copied or original.

An AVEncDDChannelBWLowpassFilter configuration parameter enables low pass filtering on each channel with an automatically specified bandwidth.

An AVEncDDLFELowpassFilter configuration parameter enables 120 Hz low pass filtering on the LFE input channel.

An AVEncDDSurround90DegreeePhaseShift configuration parameter specifies a 90 degree phase shift on the surround input channels.

An AVEncDDSurround3dBAttenuation configuration parameter specifies a 3 dB attenuation on the surround input channels.

An AVEncDDDynamicRangeCompressionControl configuration parameter specifies a dynamic range compression profile applied to the input channels. This parameter can specify the following exemplary settings 

An AVEncDDSurroundExMode configuration parameter specifies the Ex surround coding mode. This parameter can specify the following exemplary settings 

An AVEncDDPreferredStereoDownMixMode configuration parameter specifies the preferred stereo down mix mode. This parameter can specify the following exemplary settings 

An AVEncDDLtRtCenterMixLv1 x10 configuration parameter specifies the LtRt center mix level x10 e.g. one of 15 0 15 30 45 50 999.

An AVEncDDLtRtSurroundMixLv1 x10 configuration parameter specifies the LtRt surround mix level x10 e.g. one of 15 0 15 30 45 50 999.

An AVEncDDLoRoCenterMixLv1 x10 configuration parameter specifies the LoRo center mix level x10 e.g. one of 15 0 15 30 45 50 999.

An AVEncDDLoRoSurroundMixLv1 x10 configuration parameter specifies the LoRo surround mix level x10 e.g. one of 15 0 15 30 45 50 999.

An AVEncDDAtoDConverterType configuration parameter specifies the AD Converter type used to create source content if not present in the stream . This parameter can specify the following exemplary settings 

An AVEncDDHeadphoneMode configuration parameter specifies the headphone mode. This function can specify the following exemplary settings 

An AVEncWMVKeyFrameDistance configuration parameter specifies maximum time in milliseconds between key frames in the codec output. The internal logic of the codec determines the actual location of each key frame. The distance between any two key frames may be less than the value of this property however it should never be greater.

An AVEncWMVInterlacedEncoding configuration parameter indicates whether interlaced video encoding will be used e.g. 0 off and 1 on .

An AVEncWMVDecoderComplexity configuration parameter specifies the device conformance template that is desired for use in video encoding.

An AVEncWMVHasKeyFrameBufferLevelMarker configuration parameter specifies whether the encoded video bit stream contains a buffer fullness value with every key frame e.g. 0 off and 1 insert marker 

An AVEncWMVProduceDummyFrames configuration parameter indicates whether the encoder produces dummy frame entries in the bit stream for duplicate frames. If this value is 0 the media processing functionality will not put any data in the bit stream for duplicate frames.

An AVEncStatWMVCBAvg configuration parameter specifies the resulting buffer window in milliseconds of a constrained variable bit rate VBR stream at its average bit rate.

An AVEncStatWMVCBMax configuration parameter specifies the resulting buffer window in milliseconds of a constrained variable bit rate VBR stream at its peak bit rate.

An AVEncStatWMVDecoderComplexityProfile configuration parameter specifies a device conformance template to which the encoded content conforms. This value can be obtained upon the completion of encoding.

An AVEncStatMPVSkippedEmptyFrames configuration parameter indicates the number of skipped empty frame entries in the bit stream for duplicate frames.

A subset of the common parameter IDs defined earlier also apply to the packetizer function. These are AVEncCommonTargetApplication AVEncCommonRealTime and AVEncCommonPerformance. The following parameters IDs are specific to the packetizer function.

An AVEncMP12MuxEarliestPTS configuration parameter comprises a constraint parameter from the multiplexer that specifies the earliest presentation time of the first access unit in the stream.

An AVEncMP12MuxLargestPacketSize configuration parameter comprises a constraint parameter from the multiplexer that specifies the largest packet size of the PES stream.

An AVEncMP12MuxSysSTDBufferBound configuration parameter comprises a constraint parameter from the multiplexer that specifies the buffer size bound in bytes.

An AVEncMP12PktzSTDBuffer configuration parameter specifies the size of the STD buffer BSn in bits where AVEncMP12PktzSTDBuffer AVEncMP12MuxSysSTDBufferBound .

An AVEncMP12PktzStreamID configuration parameter specifies the stream ID of the elementary source. Stream IDs may be restricted in range by MPEG specifications and DVD specifications.

An AVEncMP12PktzInitialPTS configuration parameter specifies the presentation time of the first access unit in the stream where AVEncMP12PktzInitialPTS AVEncMP12MuxEarliestPTS .

An AVEncMP12PktzPacketSize configuration parameter specifies the size of the packet in bytes where AVEncMP12PktzPacketSize AVEncMP12MuxLargestPacketSize .

An AVEncMP12PktzOriginal configuration parameter specifies that the payload is original that is not copied 

A subset of the common parameter IDs defined earlier also apply to the multiplexer function. These are AVEncCommonTargetApplication AVEncCommonRealTime and AVEncCommonPerformance. The following exemplary parameter IDs are specific to the multiplexer function.

An AVEncMP12MuxPacketOverhead configuration parameter specifies the average packet overhead in the stream

An AVEncMP12MuxEarliestPTS comprises a read only parameter that specifies the earliest presentation time of the first access unit in the stream.

An AVEncMP12MuxLargestPacketSize comprises a read only parameter that specifies the largest packet size of the PES stream.

An AVEncMP12MuxMuxRate configuration parameter specifies the multiplex rate of the overall stream in bits per second.

An AVEncMP12MuxSysRateBound configuration parameter specifies a maximum rate of any mux rate in the multiplex.

An AVEncMP12MuxTargetPacketizer configuration parameter specifies the pin index of the internal packetizer to select for control. This parameter should be set before adjusting packetizer parameters.

An AVEncMP12MuxSysFixed configuration parameter specifies that fixed bit rate is in operation and controls the way SCR increases over time. This parameter implies padding.

An AVEncMP12MuxSysCSPS configuration parameter specifies that the output stream is a constrained system parameter stream.

An AVEncMP12MuxSysVideoLock configuration parameter indicates that there is a specified constant rational relationship between the video sampling rate and the system clock.

An AVEncMP12MuxSysAudioLock configuration parameter indicates that there is a specified constant rational relationship between the audio sampling rate and system clock.

An AVEncMP12MuxDVDNavPac configuration parameter indicates that the multiplexer should generate the private DVD navigation packet stream. The multiplexer should attempt to fill in as much data as is reliably possible.

The interdependencies between the parameters require that master parameters be set before their respective dependent child parameters. Setting up parameters in the correct order ensures that the application will not become locked out of certain parameter combinations due to master slave relationships. This requirement can be met by dividing the parameters into functional groups and then setting the parameters based on their membership in the functional groups.

Consider for example the case of the MPEG video encoder parameters. The following listing identifies an exemplary order in which these parameters can be set. Other orderings are possible this being merely one possible example.

In one exemplary implementation groups of settings can be atomically set en bloc as respective groups. This can be accomplished by defining a property eAV Transaction. A component can advertise its support for transactions by supporting the property.

As a final topic the following provides an exemplary list of mappings from WMV A parameters to the parameters defined above 

The following provides an exemplary program listing of a codecapi.h module that can be used to implement aspects of the features described above.

In closing a number of features were described herein by first identifying exemplary problems that these features can address. This manner of explication does not constitute an admission that others have appreciated and or articulated the problems in the manner specified herein. Appreciation and articulation of the problems present in the relevant arts are to be understood as part of the present invention. More specifically there is no admission herein that the features described in the Background section of this disclosure constitute prior art. Further the description of a limited set of problems in the Background section does not limit the application of invention to solving only those problems it can be applied to problems and environments not expressly identified herein. Further the subject matter set forth in the Summary section and the Abstract of this disclosure do not limit the subject matter set forth in the claims.

More generally although the invention has been described in language specific to structural features and or methodological acts it is to be understood that the invention defined in the appended claims is not necessarily limited to the specific features or acts described. Rather the specific features and acts are disclosed as exemplary forms of implementing the claimed invention.

