---

title: Telephone system that notifies caller of called party's state
abstract: A telephone system that has the ability to provide a caller with additional information (beyond a busy signal or a ring tone) concerning the called party when the called party's line is busy: The called party can control the amount and type of additional information provided to the calling party. In one embodiment, when the called party is notified that someone is trying to place a call (by a mechanism such as by conventional caller ID) the called party has the option of providing the calling party with a variety of different information, such as whether or not the called party is on a conference call and the number (and name if available) of the party to whom the called party is speaking.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07933397&OS=07933397&RS=07933397
owner: Cisco Technology, Inc.
number: 07933397
owner_city: San Jose
owner_country: US
publication_date: 20050825
---
There are a great many different types of telephone systems in widespread use. For example there are conventional telephone systems generally referred to as Plain Old Telephone Service POTS systems. There are cellular telephone systems that provide connections by various radio frequency protocols. Other modern telephone systems utilize Voice Over Internet Protocol VOIP technology. The specific preferred embodiments described herein related to VoIP systems however it should be understood that other embodiments are possible using other types of telephone systems 

In general there are two types of telephone calls. In the first and most common situation there is a single calling party and a single called party. In the second type of call generally referred to as a conference call a number of parties are connected together.

Calls other than conference calls have a single calling party and a single called party. In the simplest situation if a call is placed to a telephone that is busy with a first call the calling party merely receives a busy signal and no indication concerning the first call is given to the calling party. Features such as call waiting and caller ID provide the called party with an indication that someone is trying to reach them. However the calling party is given no significant information other than a ring tone or a busy signal.

Voices over IP VOIP telephones are gaining popularity. There are many different varieties of VOIP telephones commercially available. Many VOIP telephones include a display that includes soft keys . Soft keys are keys that can be programmed to provide a variety of functions. The embodiments of the invention described below utilize such soft keys. However it should be understood that the soft keys are merely one mechanism for sending signals from a handset to the device controlling the handset. A wide variety of other such mechanisms are available.

When a call is placed over any type of telephone system the user who places the call and the users who is called are provided with various information. For example if the called telephone is busy a busy signal is generally sent to the party that placed the call. In other systems when a called telephone is busy the calling party is connected to a voice mail system. A party who calls a line that is busy may hear a busy signal or hear various types of messages but such a caller is not given information abut the call that is in progress.

The embodiments described below provide a system that has the ability to provide a caller with additional information beyond a busy signal a ring tone or a pre configured voice message concerning the called party. The called party can control the amount and type of additional information provided to the calling party.

In one embodiment when the called party is notified that someone is trying to place a call by a mechanism such as by conventional caller ID the called party has the option of providing the calling party with a variety of different information such as whether or not the called party is on a conference call and the number and name if available of the party to whom the called party is speaking. The amount and type of information provided to a calling party can be pre established in a profile.

Several preferred embodiments of the present invention will now be described with reference to the accompanying drawings. Various other embodiments of the invention are also possible and practical. This invention may be embodied in many different forms and the invention should not be construed as being limited to the embodiments set forth herein.

The figures listed above illustrate the preferred embodiments of the invention and the operation of such embodiments. In the figures the size of the boxes is not intended to represent the size of the various physical components. In situations where an element appears in multiple figures the same reference numeral is used to denote the same element in each of the multiple figures.

Only those parts of the various units are shown and described which are necessary to convey an understanding of the embodiment to those skilled in the art. Those parts and elements not shown are conventional and known in the art.

It is noted that telephone calls are placed to particular telephone numbers that is to particular telephones and not to specific individuals. However to facilitate the explanation of the applicant s invention herein the term called party will be used to mean a particular telephone with a particular telephone number. That is as used herein the term called party does not refer to an individual instead it refers to a particular telephone and the user of that particular telephone

An overall diagram of a first embodiment of the invention is shown in . This first embodiment consists of a VoIP system with several users A B C D etc. Each of the users A B C D etc. has a handset namely handsets A B C D etc. The four handsets A B C and D are connected to a single Internet Protocol Private Branch Exchange IP PBX system .

The IP PBX system is connected to a call response server by means of an API. It should be understood that most practical IP PBX systems have many more than four users however only four representative users are shown in for convenience and simplicity of illustration and explanation.

The IP PBX shown in is connected to a wide area network WAN that could for example be the Internet. Alternatively network could. be a local area network LAN . In a typical situation many other users only a few of which are shown are also connected to the Internet by other IP PBXs. The first embodiment will focus on the users A B C and D that are connected to the same IP PBX . Other embodiments will focus on users that are connected to different IP PBX systems.

Consider as a first example a situation where users A B and C are involved in a conference call and while the conference call is in progress user D tries to place a call to user A. In a conventional system user D would receive a busy signal and possibly be re directed to a voice mail system. In some conventional systems. that have a user ID feature user A would be notified that D is trying to place a call and user A would have the option to put the conference call on hold and pick up the call from user D. However even in such a system if user A does not choose to pick up the call user D would either receive a busy signal or be directed to a voice mail system.

In contrast to the above described conventional response with the first embodiment shown here when user A receives an indication via called ID that user D is trying to place a call to user A user A would have available several options described below. It should be noted that the options listed below are for a first relatively simplified embodiment. Other embodiments described later have other options available. In this simplified embodiment the options available to a called party A when party A is involved in a conference call and party A receives a call from party D and are 

As is conventional the IP PBX consists of a combination of call processing software and a server platform on which the software operates. For convenience of reference herein the combination of call processing software and the server on which such software is operating will be referred to as a IP PBX.

As a specific example the call processing software in the IP PBX can include a program referred to in technical literature as the Cisco CallManager. The Cisco CallManager is a software call processing system that runs on various server platforms such as those listed below. There is a publicly available book Entitled Cisco CallManager Fundamentals A Cisco AVVID Solution by John Alexander Chris Pearce Anne Smith and Delon Whetten published by Cisco Press ISBN 1587050080 July 2001. The above referenced book describes the Cisco CallManager program.

The server on which the call processing software operates can for example be server platforms such as the Media Convergence Servers MCS models 7815 1000 7825 1133 or 7835 1266 commercially marketed by Cisco Systems.

The IP PBX includes a conventional call agent that sets up calls between various parties and a program that can display and receive signals from soft keys on the display . The call setup program and the soft key management program are indicated in by the box . The call setup program sets up calls in a conventional manner. Likewise the soft key management program manages the setup and sensing of the soft keys in a conventional manner. The signals from the soft keys are sent to the call response server that provides responses or which pushes information to the calling party.

IP PBX has an application programming interface an API that provides detailed information on every call that is being handled by the IP PBX . Conventional commercially available call management programs that have such an interface available. Two such interfaces that are in use are the JAVA Telephone API JTAPI and the Computer Telephony Integration CTI interface.

The soft key management software in the IP PBX can also accept and transfer to call response server via the API numbers that a user punches into the keypad on the handset which indicate the length of time the user expects a call to last.

The API in the IP PBX provides the following information to the call response server for each call being handled 

The API on the IP PBX can accept an audio message from the call response server and transfer such messages to a calling telephone. The API on the IP PBX API can also accept text messages from the call response server and transfer such messages to the display of a calling party s handset. T is noted that the text messages are provided to the IP PBX on an XML interface. Interfaces such as JTAPI TAPI and CTI are generally used for control information.

The call response server includes a conventional CPU and memory. A program in the call response server performs the functions described below. The call response server includes a profile memory A. At setup time a profile is established for each telephone line for each handset if each handset only has one line . The profile indicates how the calls to the particular line are to be handled. That is what options the user has available and what information should be provided to the caller for each option. The details of the actual programming that performs each of the described steps is conventional.

Most of the steps and functions shown in are performed by caller response server under control of a program located in caller response server . The operation begins when the information provided by IP PBX indicates that the line of a called party is busy as indicated by block .

The IP PBX provides the called party with an indication of the identity of the calling party as indicated by block . This is done by a conventional caller ID function.

As indicated by block the IP PBX detects whether or not the called party has pressed any soft keys. Note that the system can be programmed to give the called party several options. That is various soft keys can be available to the called party. The program for displaying soft keys is conventional. In the specific example shown in the user is provided with four soft keys that have the following functions.

It should be understood that the above four options are merely representative of the information that can be provided to the calling party at the request of the called party. These are the options specified in the profile in memory A of the particular called party line.

If the called party does not press any of the soft keys there is a default operation that is pre set that takes place as indicated by block . This can be established at system set up time.

As indicated by block the information about the call is provided to the call response server . The call response server interrogates the called parties profile in memory A to determine the particular options selected by the particular called party. From the information received and from the options that have been established when the system was set up the call information server determines the appropriate message for the calling party as indicated by block . As indicated by block the message is provided to the IP PBX. Finally as indicated by block the appropriate information is displayed on the display of the appropriate handset of the calling party or alternatively a machine generated voice message is provided to the calling party.

In alternate embodiments the system could be setup to have an option whereby a caller who is connected to the same IP PBX would always receive the name of the person to whom a called party is talking. Alternatively the same could be programmed so that selected callers would always receive the name of the person to whom the called party is speaking.

The profile for each user can be established in a number of ways. In the simplest embodiment all users have a single profile. That is calls to all users are handled in the same manner. In another embodiment each user is free to set up and change a profile from a web like interface to the call response server. In still another embodiment a system administrator is responsible for setting up a profile for each user and only the system administrator can change profiles. The profile can specify options such as which calling parties or classes of calling parties should be given the name of the person to whom a called party is speaking which calling parties or class of calling parties should be given merely a busy tone which names should never be given to the calling parties.

In one option the called party can use the keypad to enter a number to inform the calling party how long the called party expects to be busy. In another option if the called party is on a conference call other sources such as meeting schedules are searched to automatically determine the expected length of the call.

The process of notifying a called party is relatively simple if the called party and the calling party s handsets are connected to the same IP PBX. In such a situation messages to the calling party generated by the response server merely pass through the IP PBX to the calling party.

In a situation were the calling party is connected to a different IP PBX than is the called party or in a situation where the called party is connects to a IP PBX and the calling party is connected to a POTS type PBX the call setup program in the IP PBX must be modified to the extent that it can transfer voice messages back to the called party. In one embodiment such communication is accomplished as follows When a call arrives at the called party s IP PBX a separate channel is established between the called and the calling call agents. This channel is used to send verbal or control messages to the calling party.

When a call is set up using one of the conventional protocols such as SIP a channel is established between the calling PBX and the called PBX. This channel can be used to send messages back to the calling party.

It is noted that the term called party line is used herein to mean an individual telephone line to a particular user such as the line user A in . A called party line is a telephone line with a particular telephone number.

A wide variety of alternative embodiments are possible. For example in one embodiment when a called party is engaged in a conference call the server that is handling the conference call is interrogated to determine information such as the other parties on the call and the expected time duration of the conference call. The appropriate parts of this information are then transmitted to a calling party as specified by the called parties profile.

In still another embodiment a server that stores the called party s schedule is interrogated to obtain information. Selected information about the called party s schedule is provided to the calling party in accordance with a profile previously established by the called party.

In another embodiment when a called party is in a do not disturb mode the system can interrogate the called party s IP PBX to determine how long the party has been in this mode and this information can be provided to the calling party.

Certain embodiments of the disclosed technology may include a non transitory tangible computer readable storage medium storing instructions that when executed by a processor may direct the processor or other components of a computer system to perform any of the methods described herein. A non transitory tangible computer readable storage medium as used herein may include for example volatile and or non volatile memory e.g. random access memory RAM and read only memory ROM or other storage devices or media such as hard disk drives flash memory memory sticks or thumb drives compact discs CDs digital video discs DVDs floppy disks tapes and optical storage devices.

While the invention has been shown and described with respect to preferred embodiments thereof it should be understood that various changes in form and detail can be made without departing from the spirit and scope of the invention. The scope of the invention is limited only by the appended claims.

