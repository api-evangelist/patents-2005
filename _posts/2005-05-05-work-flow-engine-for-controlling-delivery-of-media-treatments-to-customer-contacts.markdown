---

title: Work flow engine for controlling delivery of media treatments to customer contacts
abstract: The present invention recognizes that there is a need to enable scripts or rules within workflow engines to be more dynamic, more easily created, more easily interpreted by other software entities and moreover to enable many different media types to be provided rather than only one such as voice. The present invention addresses this by making use of new types of web-based scripting applications such as VXML and SALT. One or more new commands are added to existing workflow engines to enable them to instruct media servers to access web-based instructions. Those web-based instructions are then executed at the media server to provide additional media treatment control.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08224922&OS=08224922&RS=08224922
owner: Avaya Inc.
number: 08224922
owner_city: Basking Ridge
owner_country: US
publication_date: 20050505
---
This application relates to GB patent application number 0412727.0 filed on 8 Jun. 2004 from which the present application claims priority.

The present invention relates to workflow engines for use with customer contact systems and also to systems and methods for controlling delivery of media treatments to customer contacts.

Conventional contact centers and self service systems comprise a workflow engine which is pre configured by an administrator or operator with parameters about how incoming contacts are to be dealt with. The workflow engine comprises scripts or rules for example which are used by the overall system for determining how to treat incoming contacts. The term customer contact system is used herein to refer to both contact centers inbound outbound or mixed contact centers and self service systems.

The term self service system is used to refer to a system or application for enabling an end user or customer to make a communications contact in order to automatically receive services. Conventionally such self service systems have previously used only voice communications over the public switched telephone network PSTN although other communications types and media can be used. Examples of self service systems include an interactive voice response system IVR system a system for playing recorded announcements to a caller and a system for putting a caller on hold and offering music on hold.

The term contact center is used to refer to a system for receiving contacts and allocating those incoming contacts amongst a plurality of agent terminals for servicing. The contact can be of any suitable media type such as traditional voice calls packet based voice calls emails video calls text messages chat sessions and others. Contact centers can also be used to generate outbound contacts and in that case the contact center manages distribution of workload between the agents.

In order to provide treatments to contacts traditional contact centers and self service systems have used media servers under the control of the workflow engine. Once an administrator has decided upon a flow logic or method for treating contacts he or she has previously written a treatment script or created a set of rules to be executed by the workflow engine. This treatment script has then been executed as part of the operation of the contact center or self service system in order to control the media server and treat contacts as required.

These conventional types of workflow engine and associated scripts are restrictive and have a significant drawback in that they tend to be proprietary to vendor systems and traditionally have only managed a single media voice. Typically adding support for new commands and capabilities is cumbersome requiring updates to the Script Interpreter and Workflow Engine and finally the Media Server due to the proprietary nature of each component. This is time consuming and complex. In addition the tools available to the administrator for use in rewriting the script or rules are proprietary also. Scripts and in fact total solutions tend to be vendor specific for these reasons. These factors in combination have led to the result that workflow engine configuration has tended to be relatively static.

An object of the present invention is to provide an improved workflow engine and method which overcomes or at least mitigates one or more of the problems mentioned above.

Another object of the present invention is to provide an improved method and system for media treatment control which overcomes or at least mitigates one or more of the problems mentioned above.

The invention proposes an enhancement to existing proprietary Treatment Scripts Workflow Engines and Media Servers to enable them to invoke the next generation of standards based Media Handling Scripting language vXML CCXML SALT in an integrated fashion.

According to a first aspect of the present invention there is provided a workflow engine for use in a customer contact system to control delivery of media treatments from a media server to a customer contact said workflow engine comprising 

one or more pre specified instructions arranged to be sent to said media server in order to cause said media server to access web based instructions and execute those so providing media treatment control.

According to a second aspect of the present invention there is provided a method of operating a workflow engine in a customer contact system to control delivery of media treatments from a media server to a customer contact said method comprising the steps of 

sending one or more first instructions to said media server to cause said media server to provide media treatment to said customer contact 

sending one or more second instructions to said media server to cause said media server to access web based instructions and execute those so providing media treatment control.

According to a third aspect of the present invention there is provided a system for controlling delivery of media treatments to a customer contact associated with a customer contact system said system comprising 

wherein said workflow engine is arranged to send pre specified instructions to said media server and said media server is arranged to access web based instructions on the basis of the pre specified instructions and to execute the web based instructions in order to provide media treatment control.

According to a fourth aspect of the present invention there is provided a method of controlling delivery of media treatments to a customer contact associated with a customer contact system said method comprising the steps of 

on the basis of at least some of said instructions using said media server to access web based instructions and execute those in order to provide media treatment control.

Corresponding computer software or performing the methods of the second and fourth aspects is also provided.

Benefits and advantages of the present invention will become apparent from a consideration of the following detailed description given with reference to the accompanying drawings which specify and show preferred embodiments of the invention.

The preferred features may be combined as appropriate as would be apparent to a skilled person and may be combined with any of the aspects of the invention.

Embodiments of the present invention are described below by way of example only. These examples represent the best ways of putting the invention into practice that are currently known to the Applicant although they are not the only ways in which this could be achieved.

The contact center or self service application uses any suitable type of signalling control protocol to control an incoming call from a customer . For example to perform actions such as call answer and call transfer. Typically it uses this same signalling control protocol to instruct the media server either directly or indirectly how to treat the call. Any suitable signalling control protocol may be used such as Computer Supported Telecommunications Application CSTA S.100 ECTF Media Services API Simplified Message Desk Interface SMDI TAPI Telephony Application Programming Interface or others.

As mentioned above the workflow engine comprises scripts rules or equivalents which are pre configured by an administrator in order to specify how incoming contacts are to be treated. The workflow engine interprets the script s or rules and issues appropriate signalling control messages to the media server in order to treat contacts. That is the workflow engine is can be considered the master of the call and it directs the call flow at a high level. For example the workflow engine determines whether to play a recorded announcement to start an IVR session or to play music while the customer waits for the next service.

In some cases the call server and media server exchange collected digit information from scripted exchanges with the customer . This information is returned to the workflow engine and used in determining the next step of the call flow.

The present invention recognises that there is a need to enable scripts or rules within workflow engines to be more dynamic more easily created more easily interpreted by other software entities and moreover to enable many different media types to be provided rather than only one such as voice.

The present invention addresses this by making use of new types of web based applications. For example VXML voice extendible mark up language as specified by the world wide web consortium W3C and SALT being developed by an industry consortium led by Microsoft trade mark . These web based applications typically reside in web servers and are either addressed by specific http URLs or are embedded parts of standard web pages.

That is information flow in different media types such as voice video text etc rather than the mono modal operation provided by the prior art architectures illustrated in .

A problem then arises in how to enable these web based applications to be used in conjunction with existing contact center and self service architectures such as those illustrated in without the need for major changes to the architecture or existing contact center and self service equipment. The present invention achieves this by using a web enabled media server in place of conventional media server and by making improvements to the workflow engine .

As shown the media server is in communication with a web server . That is the media server is now web enabled in order to interact with web server and retrieve web centric media services pages from the web server . This is done using http or any other suitable communications protocol. The web server comprises a web based application such as vXML or SALT.

In addition the media server comprises a suitable interpreter for interpreting web pages downloaded from the web server . Once interpreted these downloaded web pages provide instructions or information about what media treatments to deliver to the customer .

In this way it is no longer necessary to rely wholly on the workflow engine script or rule base as specifying the manner in which media treatments are effected. Consider the situation in which an administrator requires to change the media treatment control. He or she is able to use web based tools to create suitable web pages at the web server . The workflow engine is then arranged to send instructions to the media server to download specified web pages comprising vXML or other web based instructions and once downloaded to execute those. In this way the administrator does not need to completely rewrite or update the existing proprietary scripts or rules at the workflow engine itself. By simple addition of one command enhancement the ability to invoke execution of a vXML or other next generation script the administrator gains all the benefits of being able to use web based tools to form the web pages containing the vXML or other web centric scripts. All the other advantages mentioned above of using web based applications are also reaped without the need for any major changes at the contact center or self service system.

The instructions sent by the workflow engine to the media server can be of any suitable type. For example new commands variations of existing commands or control data. The workflow engine is effectively providing a primary workflow or master workflow which is then supplemented by any web based scripts that it specifies should be used. The workflow engine decides primarily on the basis of existing logic within the workflow engine what the high level treatment flow is and when and what media treatment should be given for a call at any point in time.

However instead of simply invoking legacy commands as illustrated in the workflow engine is opened to be able to pass data to the media server such that the media server is directed to retrieve and execute web based scripts which are provisioned separately but in complement to the workflow script .

In a first embodiment the workflow engine is arranged to direct messages to a messaging bus such as SIP messaging bus . This changes the workflow engine architecture but not the nature of the workflow scripts. Legacy technical knowledge of the workflow engine scripting environment is thus leveraged. The messaging bus represents a change over the system of and is preferably standards based. In this embodiment changes to the workflow engine interpreter are made.

In a second embodiment the workflow engine is arranged to use existing messages for communication with the media server which have capability to support generic data e.g. stringified data or application to application data sharing . In this way the workflow engine does not create a unique message sequence over a defined protocol for invoking vXML instead it simply delivers call attached data to an endpoint which can convert this data to a voiceXML invocation which can be handed to the Media Server. In this case no changes are required to the workflow engine interpreter although changes to an external interpreter are required.

In an embodiment of the invention the workflow engine has knowledge of the effects the web based instructions will have on media treatment control. However this is not essential the workflow engine can also have little or no knowledge of the effects the web based instructions will have. In that case the web based instructions themselves are more complex to enable more of the burden of media treatment control to be taken away from the workflow engine. In this way the workflow administrator can make design choices as to how the media treatment control is to be shared between the workflow engine and the web based scripts and how this is to be implemented.

As mentioned above the instructions sent by the workflow engine to the media server can be of any suitable type. For example addition of one new command to a legacy workflow engine for example the addition of a giveVXML command effectively introduces all the power of web centric dynamic scripts to the workflow administrator. It is not essential for the workflow administrator to be knowledgeable about the web centric scripts because he or she can rely on a web centric developer to provide this capability. In this way the workflow administrator can continue to define exactly how media treatments should be controlled and continue to use his or her existing expertise about the legacy workflow script environment but at the same time increase the flexibility and power of his or her legacy solution architecture by seamlessly introducing web centric media services.

Another advantage is that when it is required to upgrade the customer contact system to deal with other media types such as video or web collaboration then the existing workflow engine can still be used. Previously this would only have been possible by upgrading the workflow engine as well. Now it is possible to use the web centric scripts to provide the control needed for the new media types.

The embodiments described herein are particularly advantageous when used in conjunction with a session initiation protocol SIP enabled customer contact system. For example a SIP enabled contact center as described in earlier U.S. patent application Ser. No. 10 743 971 filed on Dec. 23 2003 which is also assigned to Nortel Networks Limited. The whole contents of that earlier application are incorporated herein by reference. SIP as a protocol is advantageous for use with the present invention in that 

