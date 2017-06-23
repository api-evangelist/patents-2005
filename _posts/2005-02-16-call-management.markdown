---

title: Call management
abstract: A personal call management system allows a user to specify how incoming telephone calls should be handled. The user can specify various parameters including modes, filters, schedules, and the like. Incoming calls are routed to a specified telephone number, or sent to voicemail, or otherwise disposed of. Users can change modes manually or can specify automatic mode selection based on time of date, day of week, location, and/or other factors.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08594298&OS=08594298&RS=08594298
owner: Avaya Inc.
number: 08594298
owner_city: Basking Ridge
owner_country: US
publication_date: 20050216
---
This application claims priority from U.S. Provisional Application No. 60 546 409 entitled Personal Call Management System filed Feb. 20 2004 the disclosure of which is incorporated herein by reference.

This application is related to U.S. patent application Ser. No. 11 060 642 entitled Dynamically Routing Telephone Calls filed on the same date herewith the disclosure of which is incorporated herein by reference.

This application is related to U.S. patent application Ser. No. 11 060 085 entitled Informing Caller of Callee Activity Mode filed on the same date herewith the disclosure of which is incorporated herein by reference.

This invention relates generally to management of communications such as telephone calls and more specifically to techniques for handling routing and configuring incoming telephone calls.

Many people callees have a multitude of telephone numbers TNs that they give out to potential callers. Typically this set of TNs includes home office and cell phone numbers. If the caller knows more than one TN for the callee the caller selects the most likely number to reach the callee and often leaves a voicemail message before trying another number. The caller is burdened with determining the most likely sequence of calls to reach the callee. This often results in one or more voicemail messages home office cell even if the caller ultimately reaches the callee. This situation slows the process of establishing a connection increases costs and reduces the probability of making a live connection due to the effort and time required of the caller. In addition multiple voicemail messages are a burden for the callee.

What is needed is a system and method that automatically handles routes and manages telephone calls so that callers do not have to guess which number to call to reach a particular individual. What is further needed is a system and method that allows a callee to specify how incoming calls are handled and that responds dynamically to real time conditions at the time a call is placed. What is further needed is additional functionality that improves the process of configuring routing and processing incoming telephone calls.

The callee is often in a much better position to know how they can be reached than the caller since the callee often knows in advance where they will be physically located home office or car and how reachable they will be. The present invention provides techniques for allowing the callee to specify how incoming calls will be handled. The user can specify call management parameters according to various factors including time of day day of week manual override caller identity caller input for example specifying whether the call is urgent called number location of callee for example using GPS cell phone tower location tower triangulation Instant Messaging presence Smart Tags or other locating technology location of caller recent phone use explicit selection using web page cell phone application dial in Interactive Voice Response IVR or other method implicit system learned adaptive understanding of the callee s call receipt desires or the like. In addition any combination of the above factors may be used.

Calls may also be sent to voicemail without ringing the user s phone based upon filtering or explicit selection. Callees may configure their routing and filtering by behavior location activity mode. Example modes are At Home At Work At Work in a Meeting Commuting and on Vacation. The selection of active mode can be made explicitly or implicitly. Explicit mode selection can include any combination of time of day and user input using cell phone web and or phone IVR. For example a cell phone may have a physical mode button or a mechanism for accessing an on screen menu from which the user can select among a number of modes. Implicit mode selection can include location information including velocity calculated from sequential position samples computer calendaring information past behavior of the user and the location of other users suppress calls while I m in the presence of the CEO . Global Positioning System GPS technology may be used to route calls based on mode the destination telephone need not be equipped with GPS detection technology. For example if the user is carrying a cell phone or other location aware device and walks into his or her office the mode may change to At Office and calls will be routed to the office phone.

Different ring types may be used based upon any combination of dialed TN calling party mode caller location callee location and or the like. For example the specific ring of a user s home office or cell phone may be selected by the system based on whether the caller is a family member or business associate filter based or whether the caller originally called the home TN or office TN dialed TN based .

The callee configures the system with mode and filter preferences in order to define how various calls should be handled. Configuration can take place via any type of user interface including a web interface phone based IVR or cell phone application. Configuration includes characterizing potential callers into groups and setting up filters for each group. Filters specify either to which phone to send the call to send it to voicemail or to give the caller a choice. The filter configuration for a group can change based on time of day explicit command from the user and or location of the user. Configuration also includes defining various activity modes during which different call management rules should be applied.

In one embodiment the system can learn adapt and extrapolate from past user behavior in order to select current mode or to place calling TN into filters. This configuration can take place automatically by the system or the system can present suggestions to the user for approval. The system can for example learn not to take calls from party A when the callee is in the presence of party B.

In one embodiment a call to any one of a callee s existing phone numbers is automatically routed to the callee at his or her designated phone. At the callee s discretion certain callers will ring through and others will automatically go to a single voicemail box or otherwise handled .

In another embodiment location information from a cell phone carried by the callee can automatically change the user s filtering and or activity mode throughout the day. For example if the callee is within 20 feet of his or her office phone the office phone is the phone that will ring for any or some selected subset of people calling the callee.

The system of the present invention provides any or all of the following features alone or in any combination 

Further features of the invention its nature and various advantages will be more apparent from the accompanying drawings and the following detailed description.

For purposes of the description herein the term callee is used to refer to an individual or entity that is being called or that may be called at some point in the future. The term user is used interchangeably with callee. 

A caller is a person who places a call to a user or attempts to place a call or potentially could place a call.

A dialed telephone number dialed TN is a number dialed by a caller. It may or may not be associated with an actual telephone device.

A mode is a callee s operational mode such as At Home At Work etc. As described below a mode can be selected explicitly by a user or implicitly according to the user s profile.

A filter is a defined scheme for identifying a subset of a user s potential callers and to treat calls from them in a distinctive way.

The present invention is now described more fully with reference to the accompanying Figures in which several embodiments of the invention are shown. The present invention may be embodied in many different forms and should not be construed as limited to the embodiments set forth herein. Rather these embodiments are provided so that this disclosure will be complete and will fully convey the invention to those skilled in the art.

For illustrative purposes the following description sets forth the invention in terms of handling a call that is placed by dialing a telephone number TN such as a North American Numbering Plan NANP number. However one skilled in the art will recognize that the techniques set forth herein can be used for handling communications that are initiated in other ways. In particular a caller can specify a callee using any type of caller identifier whether a dialed TN a text string a non NANP digit sequence or the like. The term User Address UA is used herein to denote any such mechanism for identifying a callee.

In the following description the term Delivery Telephone Number Delivery TN refers to the telephone number or UA of the device or system that terminates a call for or to a user. Delivery TNs connect to delivery devices such as a telephone a voicemail platform traditional or e mail delivery only attendant Interactive Voice Response IVR system or the like. A Dialed TN the TN that the caller dialed may or may not have the same number as one of the callee s Delivery TNs a call to the Dialed TN may or may not be connected to the device addressed by the identical Delivery TN. Thus in some cases a Dialed TN is virtual and is not the address of a physical delivery device.

As will be described in more detail below in one embodiment the present invention manages a callee s set of UAs and the real time mapping of those UAs to delivery devices. Calls placed to a UA may be routed to one or more of the delivery devices corresponding to Delivery TNs. The system uses a combination of modes filters caller selection attendant busy state and no answer state to determine whether and how a call should be routed to an appropriate delivery TN.

The present invention can be implemented in symmetric or asymmetric fashion. A symmetric implementation is one in which all delivery TNs are in the set of dialed TNs otherwise the implementation is asymmetric.

Referring now to there is shown a block diagram depicting an architecture for implementing the present invention according to one embodiment.

Caller places a call via a local phone switch such as Central Office CO Mobile Switching Center MSC or Private Branch Exchange PBX . The call goes through public switched telephone network PSTN to destination switch such as CO A MSC B or PBX C. The present invention may be implemented regardless of the particular type of switches being used at the origin or destination. Destination switch queries call management module to determine where to route the call. Module checks user profile database A to obtain call management settings for users. In one embodiment external input such as callee location caller identifiers and the like is also used by module to determine where to route the call.

Module sends a response to switch indicating the desired routing for the call. The appropriate delivery device including for example home telephone A wireless telephone B office telephone C voicemail platform and or the like is given the call and the device handles the call as though it were received directly. Callee then receives the call via the selected delivery device .

In one embodiment when voicemail platform handles a call it can query module to determine whether a voicemail message should be delivered as an email attachment to email reader for receipt by callee . In another embodiment when voicemail platform handles a call it can activate an alert e.g. a flashing light a tone or an indicator on a display on any or all of delivery devices according to callee preferences as indicated in module .

In one embodiment each query from destination switch includes for example the dialed TN and the caller TN if known . One skilled in the art will recognize that other information may also be included in the query. In one embodiment in response to receiving a query module returns a destination TN which may represent a delivery device corresponding to the dialed number or another device or voicemail platform . Voicemail platform can be in the same network as destination switch or it can be accessible over PSTN .

In one embodiment voicemail platform e mail delivery query includes the dialed TN and the caller TN if known . In response module provides a delivery flag yes or no and an e mail address.

The present invention can be implemented in connection with any type of telephone system including home telephones office telephones and wireless telephones regardless of telephone equipment and regardless of telephone service provider.

Referring now to there is shown a block diagram depicting one architecture for implementing call management functionality according to the techniques of the present invention. When caller places a call to callee the call is routed to callee based on rules stored in service database A.

Caller may call a landline TN or wireless TN of callee . In the landline case illustrates post ring management of the call. Landline phone is rung by connected CO switch A in LEC . When phone goes unanswered the call is forwarded using a pre provisioned Call Forward Busy No Answer switch feature over Public Switched Telephone Network PSTN to Wireless Carrier s Mobile Switch B where it is then managed. Mobile Switch MSC B sends a query over SS7 network through one or more Signaling Transfer Points STP through signaling gateway to Application Processor B.

Application Processor B queries database A and returns a reply containing routing information that will be used by Mobile Switch B to route the call. Possible routing destinations include callee s wireless phone and carrier s voicemail platform .

In some implementations queries from Mobile Switch B may pass through the Home Location Register HLR . In a similar fashion when caller places a call to the callee s wireless phone rather than callee s wireline phone the call is routed from originating switch A through PSTN to MSC B. MSC B manages these calls pre ring before the mobile phone is rung. In some cases caller is connected to an automated attendant Interactive Voice Response or IVR not shown in .

For example if callee shares landline with a family member MSC B can be instructed to temporarily connect caller to voicemail platform in a way that causes voicemail platform to play prompts under the direction of an Application Processor not shown by way of Messaging gateway . Calls may also be managed in an Enterprise . In this case PBX queries the service for routing information and voicemail may be used in the enterprise.

In one embodiment signaling gateway database A application processor B and messaging gateway communicate with one another via Local Area Network LAN . Similarly components of enterprise communicate with one another via Local Area Network LAN . LANs and communicate with one another using Internet Protocol IP and LAN communicates with VM using IP . Gateway connects LAN to PSTN . STP communicates with signaling gateway via SS7 .

In one embodiment user profile database A stores the following information in order to specify a callee s call management settings 

According to one embodiment of the present invention call management settings described above are specified by the user via a user interface such as a website via a cell phone or PDA or by default initial setup. Configuration may be performed by a third party using an API. Mode selection can also be made directly or through an API.

The following is a description of a software based call management system configurable by the callee to route incoming calls that are originally dialed to any of the callee s managed phone numbers according to the callee s indicated preferences. For example the callee can specify that different incoming calls should be routed to any of a number of different delivery devices based on any combination of factors including for example the number the caller dialed the identity of the caller the location of the caller environmental conditions at the callee s location and real time callee and or callee input at the time the call is attempted.

In one embodiment the callee specifies such configuration options via a web based user interface that facilitates communication with call management module . Referring now to and there are shown screen shots depicting an example of a web based front end that can be used for such call management configuration. One skilled in the art will recognize that these screen shots are merely exemplary and that many different arrangements and user interface elements can be used without departing from the essential characteristics of the present invention. One skilled in the art will further recognize that the user interface need not be web based and that any other type of user interface for accepting callee configuration of the system can be used.

Referring now to there is shown a telephone setup screen . For purposes of the following description it is assumed that the user interacting with the screens is the callee however the user could be another individual who is configuring call management parameters on behalf of a callee.

The user enters a home phone number in field A mobile phone number in field B and office phone number in field C. The user can enter any number of additional phone numbers in field D and can specify descriptions for additional phone numbers via pull down menu . Other options can also be entered including 

Callers on the VIP list get special treatment. For example the system can be configured to allow calls from VIP callers to get through even when normal calls would be routed to voice mail or screening. Calls from numbers people in the user s VIP list skip through any Screen settings as their calls are considered emergency calls in the context of screening. Such a technique is referred to herein as filtering .

Link provides access to a VIP list management screen for adding editing and deleting names and numbers in the VIP list.

Referring now to there is shown a VIP list management screen according to one embodiment. List shows current VIP entries. The user can edit entries by clicking on an Edit link or delete entries by clicking on a Delete link .

After clicking on an Edit link the user can specify a name in field and one or two telephone numbers in fields A and B. Apply button applies the changes cancel button dismisses screen without applying any changes.

Referring again to the user can specify email addresses in fields for call notification emails and for receiving voicemail respectively. Buttons facilitate navigation to other screens in the call management setup application.

The user can configure call routing for each mode activity the user defines. Modes in this example are My Default At Work At Home and Commuting . The user can select which mode to define from activity menu . In field he or she can specify the name for the mode activity . Popup menus A B C allow the user to specify how calls should be handled when they are received at the home number mobile number and office number respectively. In one embodiment each popup menu allows the user to select among routing the call to a particular destination device to voicemail or to screen the call or the like.

Check box allows the user to enable a preset schedule for the mode. If check box is checked the mode will automatically be activated at the times specified in popup menus .

Check box allows the user to select whether text notification should be sent to the mobile phone when a voicemail message is received.

Check box allows the user to select whether an email message should be sent when a voicemail message is received.

Apply button applies the changes indicated by the user. Delete activity button deletes the mode activity from menu . Navigation buttons allow the user to navigate to other call setup screens.

In the example shown as depicted in the user has configured the My Default activity so that calls to home mobile or office are routed to the respective delivery devices.

In the example shown as depicted in the user has configured the At Work activity so that calls to home are sent to voicemail and calls to both mobile and office are sent to the office. This mode is scheduled to be active from 9 am through 5 pm every workday. Check box has been activated so that text notification will be sent when voicemail is received.

In the example shown as depicted in the user has configured the Commuting activity so that calls to home are screened to the mobile phone and calls to mobile or office are connected to the mobile phone. A message is played to the caller The person you are trying to contact is currently unavailable if this is an emergency press 1 otherwise press 2 to leave a message. If the caller presses 1 he or she is connected to the mobile device. If he or she presses 2 he or she is connected to the voicemail platform.

After setup is complete the user can view a summary of his or her Call Management settings. Referring now to there is shown an example of a call management summary screen according to one embodiment. A summary of settings is shown with Edit buttons allowing the user to return to a screen for changing settings. The user can select which mode is active by clicking on one of radio buttons . Apply button applies the changes.

In one embodiment the user can select among modes by other means as well. Referring now to there is shown an example of a user interface for selecting among modes via a mobile phone handset .

In one embodiment the system of the present invention activates different modes depending on any of explicit selection time of day and or day of week location of the callee detected for example by GPS positioning or by noting that the user has used a particular phone recently or by explicit user indication of location . In one embodiment scheduled modes are automatically active during scheduled times. In one embodiment scheduling can be turned on or off from the handset or from the website.

Based on the user specified configuration options described above a call routing matrix can be constructed. Referring now to there is shown an example of a call routing matrix according to one embodiment. Matrix summarizes call handling preferences according to callee mode and caller identity. Each row in matrix represents a mode and each column represents a filter option a particular caller or caller group . Current mode is also shown.

In the example shown matrix provides input fields for specifying additional call routing configuration options. For example pull down menus allow the user to schedule certain modes and or to specify how mode activation can be automatically handled based on location or other factors. Pull down menus allow the user to switch manually to a desired mode. Link allows the user to access additional edit options.

In one embodiment any or all of the summary information and input fields of can be shown in the context of other types of user interfaces including for example an interface for a PDA or cell phone screen.

When a call is made to callee module directs the call based on any combination of the following factors call routing rules as specified above currently active mode caller identification or lack thereof called telephone number mode and caller or callee input as described above. In one embodiment call routing may also be determined by the system based on routing decisions the user has made in the past. Thus the present invention can use intelligent call management algorithms including for example collaborative filtering based on the behavior of a set of users to learn about users preferences without requiring explicit selection.

For example if the system recognizes that at a given location calls to all users are almost never answered it can automatically route calls to callees in that location to voicemail while sending a SMS notification to the callee. Examples of locations where such a situation may occur are a movie theater and a lecture hall. The system can determine these location behaviors empirically for example based on system usage. Alternatively the system can use a database of location classifications to extrapolate a user s behavior or set of user s collaborative behavior from one location to another location of similar classification.

In one embodiment call handling is accomplished as follows. When a call is placed to one of a user s managed telephone numbers a database query is made before the call is completed. The result of the database query causes the call to complete to the originally dialed device device associated with the managed telephone number to be redirected to another delivery device which may or may not also be in the set of managed telephone numbers or to be redirected to the system handling the user s voicemail. The call routing is thus performed in a manner that is seamless to both the caller and the callee.

In one embodiment the system of the present invention implements rule based routing based on the data stored in database A.

Rules are implemented in a manner that resembles operands. For any given call management situation only one rule is executed so as to definitively dispose of the call.

The rules are created by program logic on a web server and in database A when callee configures his or her account. When a managed call is handled by the system of the present invention a determination is made as to which single rule is to be executed by the switch. If more than one callee shares the managed phone line managed TN a single rule is identified for each callee and returned to the querying server telephone server Signaling Application Processor etc. . That server causes the caller to be asked which user they are calling. For example Press 1 for Joe Press 2 for Jane After that selection is made by the caller the appropriate call routing rule is executed. If only a single user is associated with a managed TN the rule for that user is executed without need for caller interaction. Accordingly in one embodiment database A stores a representation of a chart for a particular callee the chart sets forth a set of rules. Each rule is qualified by any or all of the following 

Associated with each rule is an action or more than one action also referred to as op codes. Examples include 

In one embodiment database A includes a representation of a number of rules each including any or all of the above.

As discussed herein callee modes can be based on explicit selection or on location or by a schedule or by other predetermined conditions. In one embodiment certain modes may expire automatically after a defined period of time then the callee returns to a default mode or previous mode.

In one embodiment the schema and indexing of the table is designed to facilitate rapid lookup during call handling operation. When the system of the present invention receives notification from a switch LEC MSC PBX etc. that a call has been placed to an managed telephone number managed TN the system of the present invention does the following 

For each user associated with the managed TN the instruction part of the selected rule is returned. This instruction part consists of an opcode and some operands. These are opcodeID deliveryDeviceID1 deliveryDeviceID2 and 2 notification options callNotifyEmailOption and callNotifySMSOption. The deliverDeviceIDs reference telephone numbers stored elsewhere in the database. When the rule instruction is returned by the database to the querying server telephone numbers are returned instead of deliveryDeviceIDs.

When the user is identified by the Platform on caller selection in the case of multiple users on a managed TN the associated rule instruction or op code is executed.

Referring now to there is shown a table containing an example set of rules for a callee including a set of op codes. callNotifyEmailOption and callNotifySMSOption are notification options which if set to Y cause the system of the present invention to send a call notification to callee using an address stored elsewhere.

The following is an example of a set of op codes for use by the system of the present invention. One skilled in the art will recognize that many other types of op codes can also be used. The op code CONNECT DIALED DEVICE is transformed to CONNECT by database logic before being returned to the querying server telephone server using information available at call time specifically the called number . The op code CONNECT INTERNAL VM is transformed to VOICEMAIL if the voicemail access number stored in the database is handled by the same telephone server that is making the database query this direct internal connection saves the resources required to place an additional call.

In one embodiment voicemail platform and other enhanced services can be provided by any provider and need not be associated with the provider of module . A user can have any number of voicemail repositories though many users will find it convenient to direct all voicemail calls to a single voicemail repository. Thus the user may select a voicemail service and repository provided by one of the carriers that the user is using for telephone service. Alternatively the user may select voicemail service from a third party provider that is not associated with any of the user s phones.

In one embodiment when initially signing up for call management services such as those provided by the present invention the user can select a voicemail service provider from a list of available providers.

Then when call management configuration specifies that a call should go to voicemail module directs the call to the appropriate voicemail access phone number. In one embodiment unanswered calls busy or no answer after four rings are also routed to the appropriate voicemail access phone number.

In one embodiment other enhanced services such as call notification via e mail SMS message Stutter Dial Tone and the like or integrated call logging one list of incoming calls across all of a user s managed phones can be provided independently of the user s telecom carriers.

In one embodiment the system of the present invention performs real time mapping and rule selection on call by call basis. Thus inputs are evaluated at the time the call comes in so as to select the rule based on the most up to date information. Thus the present invention ensures that calls are correctly routed based on the most current sources of information and settings.

As described above the call management system of the present invention allows a user callee to control how they are reached by phone. When one of the user s telephone numbers is dialed the call is routed pursuant to the desire of the user. Thus incoming calls may be routed for example to the phone at the callee s current location or to voicemail if they consider themselves unavailable for phone calls .

In one embodiment a caller can identify a callee to be called by some identifier other than the telephone number in other words an identifier that is not in conformity with the North American Numbering Plan NANP for telephone numbers . Thus in essence the caller attempts to call a person rather than a telephone number in fact the callee may not even be aware of the callee s telephone number.

For example the caller may initiate a call via a web interface PDA interface cell phone interface or by some other means. The caller may select or enter the callee s name or email address or may even click on a link on a web page to attempt to reach the callee. The caller s action causes module to perform a database lookup and to initiate a telephone call to callee according to the current mode and callee preferences as described above. Thus in this embodiment calls are routed in a similar manner as above but the caller has identified the callee by means other than the telephone number.

In one embodiment the callee can specify that calls initiated by identifying the callee by some mechanism other than telephone number are handled differently than calls initiated by dialing a telephone number. Thus for example a call initiated by selecting a name from a web page might go to voicemail while calls initiated by dialing a telephone number might be routed to the callee s wireless phone. Such a mechanism can be implemented for example by providing one or more additional pull down menus in the screen shown in allowing selection of actions to be taken if the callee is called using alternative identifying means.

Referring now to there is shown a block diagram depicting an architecture for implementing callee identification by means other than telephone numbers according to one embodiment.

A caller places a call for example via computer that is running a voice communication application. The caller identifies the callee by some means other than entering a NANP telephone number for example by entering the callee s e mail address. The application running on computer contacts call management configuration storage and routing module to determine how to route the call. Based on callee preferences routing module causes the call to be routed to another computer or to a NANP device such as telephone A connected to PSTN via an IP PSTN gateway . In one embodiment the call is routed from computer to gateway or to computer via the Internet .

In one embodiment non NANP calls can be placed using Voice over Internet Protocol VoIP . These calls can be initiated using Session Initiation Protocol SIP . To re route a SIP call call management module can be registered with a network SoftSwitch to handle the callee s VoIP telephone calls. When a call is placed to the callee VoIP phone or computer acting as a VoIP phone the SoftSwitch sends an Invite message to call management module . Call management module responds with a redirection message that causes the SoftSwitch to either complete the call as originally directed or to terminate the call on another device VoIP SIP phone PSTN phone or voicemail platform .

In one embodiment the present invention provides distinctive ring tones based on any of a number of factors including which number was dialed caller identification or the like.

Call management screen as described above in connection with can be enhanced in one embodiment by adding user interface elements that allow the user to specify different types of call notification depending on certain conditions. The notification can be for example a distinctive ring on the delivery device or a distinctive Instant Message notification on a computer. A user may specify that calls routed from his or her office phone ring to his or her home phone using an alternate short ring cycle distinctive ring while other calls use the standard ring. In one implementation the ring type can be controlled by routing the call to one of two phone numbers associated with the telephone line using a standard LEC Local Exchange Carrier distinctive ring feature.

In one implementation the ring type on a mobile phone may be modified in real time immediately before the system routes a call to that phone by sending a Short Message Service SMS message or other data message to a software application running on the phone. The software application changes the phone ring type according to instructions sent in the SMS message.

In one embodiment the present invention uses an alternative communications path such as short message service SMS email instant messaging or the like to let the callee know who is calling. The message to the callee can include additional information about the call including how it was routed where the caller is located caller s telephone number caller s name from the user s directory or from other sources such as a CNAM database number dialed by the caller and the time of the call and the like.

In one embodiment the callee can specify which incoming calls should include such notification and what type of communications path mechanism should be used. E mail notification of calls may also be configured. The content of the notification may include the caller s telephone number the caller s name from the user s directory or from other sources such as a CNAM database the number dialed by the caller and the time of the call. In alternative embodiments other types of information may be included.

In one embodiment when Call management module receives a query from a telecom switch or PBX C it dips User profile database B to determine how to respond to the query. Information returned from database B includes a callee notification configuration. This information includes how to send notification to callee and in what format to send it. In the case of e mail notification Call management module formats an e mail message and sends that message over the Internet through an mail SMTP server.

In one embodiment the present invention can convert telephone calls into email messages SMS messages instant messages or other types of communications.

Referring now to call management screen is enhanced in one embodiment by adding user interface elements that allow the user to specify that certain telephone calls depending on any of the factors discussed above should be converted to other types of communications. Specifically as shown in menu A includes a send to voicemail option that allows the callee to specify that while at work calls to his or her home number should be sent to voicemail. The system can further be configured to convert the voicemail to an email message or to attach it to an email message and send it to the callee s work email address. Content of the communication can include additional information about the call including how it was routed where the caller is located caller s telephone number caller s name from the user s directory or from other sources such as a CNAM database number dialed by the caller and the time of the call and the like. In one embodiment this information about the call and the caller is compiled from information passed in the query to the Call management module combined with derived information for example a directory lookup of the caller s name based on the calling telephone number and independent information such as the time the call was processed by the system.

In one embodiment voicemail platform queries module to determine whether to deliver a voicemail message using e mail. Module obtains profile information from database A. This determination is made based on user preference as a function of any or all of mode callee and dialed telephone number.

In one embodiment the present invention facilitates mapping of different phone numbers to different modes. For a single callee several telephone numbers can be established for example one for important calls one for business calls one or more disposable numbers and the like. Such an arrangement allows the callee to better manage his or her calls by giving out the appropriate number from the set of telephone numbers depending on the situation. The various telephone numbers need not have any correlation to actual physical locations or telephones.

Referring now to there is shown an example of call management screen wherein calls to different phone numbers are handled differently. In this example when the user has selected the High Priority mode only calls to the mobile phone will ring through. Calls placed to home and office phones will be routed directly to voicemail. Thus the user can give out the mobile phone number to those callers whom the user deems most important.

In one embodiment a disposable telephone number valid for a limited time period can be offered. Calls made to temporary disposable telephone numbers are routed to one of the user s delivery devices or to voicemail depending on the user s stated preferences. The assignment of a temporary number can be made dynamically from a pool of available numbers. The number may remain valid for a single call for a brief time period or for a long time period.

One example of the use of a temporary telephone number is as a contact number for people communicating using Internet Chat. A temporary number can be provided as a public number for a user allowing that user to give the telephone number to another person to make a single call. The user s actual delivery device telephone numbers remain private. After use the telephone number is suspended for some period of time and then returned to the pool of available temporary telephone numbers.

In another embodiment a temporary address number is given to the user along with a common access number. After calling a common access number for example a toll free number the caller enters the temporary address number a sequence of digits . The call is then routed to the appropriate user s delivery device or voicemail. The system generates a temporary address number for example a unique digit string that is valid for a limited time. During that time when a caller calls the common access number it is answered by a telephone server not shown . The telephone server queries User profile database A. Database A treats the temporary address number as a managed address for purposes of determining the routing rule to pass to the telephone server. The telephone server executes the routing rule which results in sending the call to a telephone voicemail or some other call handling device.

In a shared line situation where a subset of the members of a family have wireless phones the present invention can split off calls for those with other phones wireless or office as defined in the configuration profile.

In one embodiment potential callers can see mode information for callees. In one embodiment callees can choose whether or not to make such information available to potential callers. Additionally callees can choose to make such information available only to some potential callers if desired.

In one embodiment a potential caller can see mode information by keying in the phone number of the callee in a cell phone or other device or by selecting the callee from a directory or by some other means. In one embodiment when appropriate the calling device queries the system of the present invention to obtain a description of the callee s current mode. A representation of that mode is displayed the potential caller who can then decide whether or not to attempt to complete the call.

In this context a callee s mode information is a label that reflects the callee s desire ability or propensity to accept any or certain types of phone calls. User B s mode can be presented to User A before and or after User A places a call to User B.

If mode information is presented to User A before a call is placed to User B User A can use knowledge of User B s mode in deciding whether or not to initiate a call to User B. If mode information is presented to User A after a call is placed to User B User A can use that knowledge as context for discussion with User B if the call is picked up by User B or for understanding why the call was not picked up by User B.

The displayed mode may be set explicitly by that callee or it may be a function of the callee s mode in other words the callee may specify that the displayed mode not be the same as the actual mode. All inputs used to determine mode can also be used to algorithmically determine the user s mode. User A may learn of User B s mode by viewing an address book entry on a client device mobile phone or other device by selecting a show mode soft key on a client device or by some other means on the client device. User A may also learn of User B s mode after calling User B.

Callee mode information can be determined when another user queries for it or it can be determined periodically by the system. If the mode is determined periodically it can be stored and made available for query or it can be pushed to the client devices of all users who have access to the information.

Referring now to there is shown an example of a cell phone display wherein a current activity mode Home for a callee is displayed. This display would be shown for example after the user of the cell phone had keyed in the telephone number of the callee on keypad or after he or she had selected the callee s name from an on screen list or directory .

In one embodiment the display of the mode indicates whether the callee is at home at work on vacation or the like. In another embodiment additional information can be displayed such as the callee s activity mode schedule an indication of when the current mode will change and what the next mode will be forwarding information such as substitute telephone number or any combination thereof. The callee can specify what kind of information is displayed and can indicate that different kinds of information be made available to different callers or depending on other factors.

In one embodiment the system of the present invention is implemented as follows. First a call being made is intercepted as follows 

Then a database dip is performed to determine how to dispose of the call. Disposition options are let it complete forward it elsewhere or send it to voicemail. The database dip is performed on a specialized database or mirror. Interfaces to the database include AIN WIN CAMEL to an SCP via SS7 or XML via the Internet.

Database dips may be made directly or through a partner that runs the SS7 network as a front end to the database either by contacting the database in real time pull or hosting a mirror of the database push .

Referring now to there is shown an example of a detailed architecture for implementing the present invention according to one embodiment. For illustrative purposes the wireless network shown is a GSM network. CDMA and other wireless protocols are also supported. For illustrative purposes a redundant centralized configuration is shown in the example of . However one skilled in the art will recognize that the invention can also be implemented using for example a geographically distributed architecture.

SS7 Network provides the SS7 connectivity between service platform and Wireless Carrier Network . Such a network may be provided for example by a wireless telephone company such as Verizon. One skilled in the art will recognize that other mechanisms for connecting components and can be used.

Enterprise Network connects to the service platform using Internet protocol IP . ILEC SS7 Network is used to turn message waiting on and off on landline phones. Elements in and are optional components that need not be included in order to practice the present invention.

In the embodiment shown in when a call addressed to a managed telephone number is received by MSC MSC sends a query containing the called TN and calling TN to Application Processor SCP using a TCAP message over the Signaling System 7 SS7 . This message travels over one or more Service Transfer Points STP in SS7 network and through Signaling Gateway where its format is converted to SCCP User Adaptation Layer SUA . Alternatively the query can travel over Internet Protocol IP network from MSC through Edge SS7 Gateway to Application Processor SCP using the SIGTRAN protocol.

The Application Processor acts as an Intelligent Networking Service Control Point SCP . SCP queries the Database to determine how to handle the call. In some cases for example if the managed TN is shared among multiple users caller is prompted to enter a digit to select the desired callee or to select the callee by other means . To do this SCP establishes a session and responds to MSC instructing it to temporarily connect the call to Application Processor Intelligent Peripheral IP through VoiceXML gateway over PSTN or using VoIP.

When Application Processor IP receives a call it communicates with Application Processor SCP over Internet Protocol to determine which voice prompt to play to caller . The response from SCP is used to select and retrieve the voice prompt from Prompt store . That prompt is played to caller . Caller s selection made for example with the Dual Tone Multi Frequency DTMF signal from a key press on a conventional telephone is detected and forwarded to SCP . Application processor SCP uses the caller s selection to determine how to dispose of the call. Instructions for call disposition are sent to MSC .

MSC disconnects the call to Application processor IP and forwards the call to the desired delivery TN. Callee can be notified of unanswered call events by the system. Desired call event information is sent from database to Notification Server which can notify callee in various ways including sending an Short Message Service SMS message to callee s mobile phone via SMS Gateway.

An enterprise telephone station attached to a Private Branch Exchange PBX can be managed by the system. When a call destined to a station is received by PBX PBX sends a query to Application Processor SCP over Application Programming Interface API . The response from the query instructs PBX as to how to dispose of the call.

Voicemail messages may be interchanged between Wireless Carrier Voicemail platform and Enterprise Voicemail platform using VPIM Gateway .

In one embodiment call routing also referred to as vectoring is accomplished by forwarding from destination switches connected to the originally dialed TN in a Central Office CO A or Mobile Switching Center MSC B or by forwarding from Private Branch Exchanges PBX C controlling dialed office telephones.

In one embodiment Advanced Intelligent Network AIN technology is used in COA. Advanced Intelligent Network AIN is a telephone network architecture that separates service logic from switching equipment allowing new services to be added without having to redesign switches to support new services.

In another embodiment Wireless Intelligent Network WIN Customized Applications for Mobile network Enhanced Logic CAMEL or other technology is used in MSC B to implement the call management functionality described herein.

Referring now to there is shown an example of an architecture for implementing the present invention by integrating with a wireless carrier using WIN or CAMEL.

The implementation shown in manages landline wireless and office telephones using the wireless carrier Mobile Switching Center switch MSC B. Calls placed to Home phone A of callee are initiated by any phone A B C and are routed over PSTN to Central Office CO A associated with called home phone A. If Home phone A is busy or not answered the call is forwarded to MSC B where the call is managed.

Calls placed to the user s office phone C are managed by MSC B if the callee s public TN published TN is forwarded by PBX C to MSC B and Office phone C is associated with a hidden TN. In this fashion calls destined to the callee s Office phone C arrive at MSC B where they can be managed and potentially forwarded to the actual office phone using the private TN.

Upon receipt of a call for a managed TN MSC B queries SCP inside Call Management Module using a WIN or CAMEL trigger over SS7. SCP in this figure includes a service database and database logic which determines how the call should be handled by MSC B.

If the managed TN is shared by multiple users a prompt is played to caller so that caller can select the callee he or she is trying to reach. The spoken name of each user is originally stored in the Master copy of prompts and periodically copied to a mirror data store at MSC B. MSC B uses the local copy of the prompts to ask caller to select a callee for example Press 1 for Joe. Press 2 for Mary and the like . The selection is sent to SCP which replies to MSC B with instructions for completing the call. Depending on the instructions MSC B may forward the call to the callee s Wireless phone B Office phone C or to a voicemail platform not shown in or the like. In this example the call would not be forwarded to Home phone A because phone A is already known to be busy or not answered. The service database can be configured with a computer through a Website or through telephone Interactive Voice Response IVR system .

The architecture of is set up to provide the functionality of the present invention using one or more of the following steps 

Home phone A is provisioned to forward to cell phone TN on Busy or No Answer. Alternatively one or both of the following techniques can be used 

Office phone C is provisioned in PBX C to forward to cell phone TN on Busy or No Answer or office phone forwarding variable or BNA can be dynamically configured based upon mode and or filter.

A switch in MSC B connects to cell phone B or redirects to another phone C A or voicemail based upon mode and filters.

If the call is unanswered it is forwarded to the cell phone switch. In the case of fixed forwarding or ported home number all calls go to MSC B before ringing home phone A.

If home phone A is shared a switch in MSC B can play attendant prompts to allow caller to select one of multiple users via IVR.

The switch in MSC B can connect to cell phone B or redirect to another phone A C or voicemail based upon mode and filters.

A switch in MSC B connects to cell phone B or redirect to another phone A C or voicemail based upon mode and filters.

Attendant prompts especially personalized greetings and names may be recorded at a central site and distributed to each of the MSCs B through data mirroring. An SSP at MSC B can use an Intelligent Peripheral located at MSC B or centrally to play attendant prompts.

In one embodiment Advanced Intelligent Network AIN functionality at destination switch can be used to perform filtering and or play attendant prompts before ringing home phone A. When caller selects the callee he or she is trying to reach the call can be forwarded to home phone A possibly using distinctive ringing to identify the desired user the call can be sent to another phone including a cell phone B or office phone C the call can be routed to a voicemail platform or the call can be routed to another service. In one embodiment callee can specify filters that allow certain callers skip the attendant or to be handled differently than other callers. Adding a caller to a filter list can take place at any time including after a call is completed or before or during a conversation or at any time using a configuration tool such as described above. In one embodiment the web based user interface displays a log of incoming callers call times the user the caller selected along with the controls necessary to add remove callers to from filters.

Referring now to there is shown another embodiment of the present invention wherein the functionality described above is implemented using Dynamic Number Portability DNP substituting the Alternate TN at the Origin and or Gateway switch.

Caller places a call on any of the following a residential inter company or inter carrier wireless phone A an Intra carrier wireless phone B or an intra company phone C. is Central office CO switch A is associated with phone A. Mobile switching center switch B is associated with phone B.

Public Switch Telephone Network PSTN carries calls among CO switch A Voicemail VM platform and CO switch A. SS7 network carries Non Call path Associated Signaling NCAS between switch A or B and call management module .

Voicemail VM platform is a potential destination for calls that is capable of recording caller s voice message. CO switch A is a land line central office switch associated with home residential telephone delivery device A. Mobile switching center MSC switch B is connected to wireless mobile telephone delivery device B. Private branch exchange PBX C is connected to an office telephone station C.

In one embodiment callee configures the service of the present invention for example using a computer or wireless phone software application . Examples of screen shots of such an application are shown in and .

In one embodiment Call Management Module includes Service Control Point SCP that accepts queries from switches A B A and PBXC and returns call routing information. PCM Mode Filter and Redirect logic and PCM Attendant logic A are software programs associated with SCP .

Data store contains master copies of user spoken names for use in prompting caller to select from multiple users who share a managed home telephone.

In one embodiment web configuration interface generates the website with which callee configures the service.

In one embodiment callee can use telephone Interactive Voice Response IVR server to configure services.

In one embodiment call management is performed by doing a lookup at origin switch A or B associated with caller s telephone line A or B or PBX C for example using Dynamic Number Portability DNP . Thus the call is redirected before it leaves originating switch . An advantage of such an implementation is that it reduces system wide telecom costs and eliminates potential calling loops that may take place if different systems such as PBXs control redirection for overlapping subsets of a user s phones.

DNP need not be implemented in all networks to be effective at reducing costs associated with re routing calls to alternate telephone numbers.

In one embodiment DNP is implemented using universal switch CO and MSC participation and or PBX participation to redirect intra company calls to a user s office phone. In one embodiment DNP is also implemented at international gateway switches so that calls can be routed vectored when entering a particular service area.

In another embodiment DNP is implemented at the call originating device for example when calls are transported without going thought telecom switches. Such a technique can also be used for devices that use PSTN . Such devices include a computer that places calls using IP telephony a wireless carrier s cell phone or a peer to peer switch less cell phone. The call originating device performs a DNP database dip to receive the substitute TN and other call control information such as TN to call if the substitute TN is not answered.

When caller dials a TN switch A or B determines the dialed TN is a user TN optional step . If so then a DNP dip is performed passing Dialed TN and Calling Party TN Calling Party Blocked CID Flag and a switch identifier for location determination used in some cases for substitute TN selection . Returned from the dip is Substitute Telephone Number STN Busy Telephone Number BTN No Answer Telephone Number NATN No Answer Ring Count or time delay and billing entity number which may be a switch ID of user .

Switch A or B calls the STN. If it is busy the call is connected to BTN. If it is not answered after No Answer Ring Count rings the call is connected to NATN. The STN can be a delivery device wireline or wireless phone or another device such as an attendant IVR service.

In addition destination switch A B or another destination switch for the delivery device may act as an attendant service. An attendant service can redirect the call present caller with options such as attempt connection or go to voicemail or allow caller to select which callee he or she is calling from a list of options or provide screening choices to callee . For example an attendant can call callee and let him or her know who is on the phone and present callee with call completion options.

The use of BTN and NATN also allows LECs to pull back a call destined to a wireless carrier. In this way they can allow their customers to have a single voicemail box possibly on the LEC network. This scheme enables a leave a message for a person not for each of their places service. DNP also enables a wireline carrier to allow its customer to hide a wireless TN behind a wireline TN.

Inclusion of BTN and NATN in the returned DNP information also allows the owner of origin switch A B to provide a voice messaging option to their customers the callers. Such a service could be implemented for example by dialing 11 or other prefix code or access TN before a 10 digit number. If callee is a DNP user and has a BTN and NATN then caller is connected to voicemail directly. If BTN and NATN is not present then the 11 service can connect the call directly or inform caller that the voice messaging option is not available. This scheme enables a leave a message for a person without the risk of talking to them service.

In one embodiment a BTN and NATN returned in a DNP dip may differ depending on the switch making the dip. The DNP dip includes switch ID that can be mapped to location inside the DNP system. DNP can dynamically substitute local access numbers. This can be done for example to minimize the access charges in a voicemail network. In one embodiment the BTN and NATN are not typically configured directly by the user. Instead the user selects a third party VM provider and that provider supplies access numbers.

In one embodiment attendant greetings are a function of filters and modes. For example when caller dials callee s home TN caller might receive a different personalized greeting based upon callee s current mode I m commuting right now please leave a message and I ll return your call when I reach my destination or I m at work today please press 1 to connect to my office phone. 

Also in one embodiment modes and or filters can be used to select ringing modes loud soft vibrate etc. and or ring tones Ring ring you have a call etc. on a cell phone or other phone as described in more detail above.

The following is a set of operational steps that are used to implement the functionality of the present invention using DNP according to one embodiment 

Case 1 Caller Dials a PSTN TN from Landline Phone Connected to CO Switch or Wireless Phone Connected to MSC Switch 

Origin switch optionally determines if the TN is managed by DNP. In one embodiment this information is pushed from a database not shown within SCP to the carrier periodically. In one embodiment if this data is pushed to the carrier the carrier uses an in network SCP with an affiliated database mirror of the data within SCP to query for call routing information. This step minimizes out of network SS7 traffic. This check to see if a user has DNP can be performed on an in network LEC or wireless carrier database that is anticipated periodically for example every 15 minutes. In one embodiment if the user has DNP service a DNP dip to a DNP database is done to get current data.

If the TN is managed by DNP or if previous step was not performed a DNP dip is performed typically using Transaction Capabilities Application Part TCAP messaging carried on Signaling System 7 SS7 . In one embodiment the following information is passed to DNP database for example via TCAP message from switch A or B to Service Control Point SCP 

In one embodiment the following information is returned from DNP database for example via TCAP message from SCP to SSP 

Using TN Extension a DNP dip is performed for example using XML over HTTP. In one embodiment the following information is passed to DNP database 

In one embodiment DNP is implemented with a master database and a distributed network of mirrored databases in multiple geographically disparate locations. When a DNP dip is performed over SS7 network Global Title Translation GTT is used to find the active or best database SCP to query. SS7 network may be provided by a third party.

In one embodiment DNP dips are only performed for dialed TNs of users of the DNP service. A pre qualification database may be hosted by the LEC within its own network. Such an implementation causes DNP dip traffic to grow gracefully over time. In the event of a system failure the default action is to complete the call to the original dialed number if possible. The pre qualification database may be updated at a frequency much lower than the update of the active DNP databases.

The present invention can be implemented in many different architectures and can operate regardless of whether call routing takes place at the origin switch or the destination switch or at a gateway switch. Thus in one embodiment call routing takes place at an origin switch. Alternatively call routing can take place at any other switch along the call path. In one embodiment multiple routings can take place at different points along the call path. A DNP dip can be made at any point in order to obtain information for the call routing operation. In one embodiment multiple DNP dips may occur as requested by multiple switches. In another embodiment a flag may be set to indicate that a DNP dip has already occurred for the call so that additional unnecessary dips can be avoided.

Referring now to there is shown an example of an architecture for in network and out of network call routing using an implementation of the present invention. Two cases are contrasted 

When caller A belonging to network dials callee at dialed TN A handled by switch AB origin switch AA re routes the call to Alternate TN B via switch AC.

When caller B not belonging to network dials callee at dialed TN A gateway switch re routes the call to Alternate TN B via switch AC.

When caller B not belonging to network dials callee at dialed TN A if gateway switch or any other switch does not re route the call callee s destination switch AC can e route the call to the Alternate TN B.

With DNP origin switch forwards calls on behalf of caller . Callee is not necessarily a customer of the owner of origin switch . Thus in one embodiment the present invention uses DNP and includes a charge transfer sub system.

According to this embodiment billing records are moved from origin switch to an entity which can bill the customer. The billing record can be forwarded to the switch of the dialed number. Callee should be charged the cost as if the call was forwarded from the switch associated with the originally dialed TN to the forwarded number.

In one embodiment the present invention provides automatic and or preconfigured redirection of telephone calls in case of emergency or disaster.

In the event a disaster such as an earthquake destroys one or more of the user s delivery devices or makes them unavailable to the user the user may use screen to cause their calls to be routed to an out of area delivery device telephone . If desired an Emergency mode may be predefined for this purpose. In one embodiment the Emergency mode is automatically selected if the system of the present invention detects or is informed that a set of telephone numbers is no longer reachable.

If damage to a telephone switch causes the system to be unable to route calls destined for managed telephone numbers handled by the switch in one embodiment queries are performed by the origin switch rather than the destination switch. In one embodiment origin switch based redirection is performed at all times rather than just during unusual situations. In one embodiment the system detects switch failure for a set of managed telephone numbers attached to a switch by monitoring the health of the switch for example by querying the switch on a regular basis. If there is no response the switch is presumed to be unavailable and all users with managed telephone numbers attached to that switch are automatically placed into the Emergency mode.

DNP can be used to creating a disaster resilient phone network. In the event phone service is lost in a region from one phone line to a building to a city calls destined into that region can be rapidly rerouted to alternate locations. A disaster recovery service can be pre configured according to the techniques of the present invention that when the customer signals that a disaster occurred or when such a condition is detected by other means all managed TNs are routed vectored to the corresponding substitute TNs.

Referring now to there is shown a block diagram depicting an architecture for implementing a disaster resilient DNP architecture according to one embodiment of the present invention.

Mirror copies of Master DNP Database are provided. A backup set of Call Management servers are located at a geographically dispersed location. Switches A and B can either contain a mirror copy of DNP database to be dipped locally or they can dip a DNP database outside the carrier s network using TCAP messages over SS7 network .

These queries and the responses typically travel through one or more Service Transfer Points . In one embodiment STPs are implemented in cross connected pairs for high reliability paired with SS7 Interfaces .

Service Control Point also implemented in redundant pairs dips locally mirrored copy of DNP database . This database dip can be performed on primary Call Management module or on a backup set of Call Management servers referred to as mirror . Any number of mirrors can be provided.

Configuration Interface Server is implemented for example as a web server that hosts a website that allows callee to configure his or her service using computer .

In addition DNP can be used to facilitate traffic analysis in order to identify terrorist human networks through calling patterns of known or suspected terrorist or other enemies of the state. With the addition of location information on a per call basis or periodic update coordinated attacks can be detected in real time by looking for suspicious predefined usage pattern. Referring again to a traffic analysis component could look for suspicious patterns of telephone usage. For example component could look for multiple calls to multiple airport gates 2 linked calls from 3 airport gates within a given time period. If this event is detected an alert can be forwarded to the appropriate governmental agency.

In many households the home TN is shared among multiple residents. In one embodiment if caller calls a callee s shared home phone A caller is presented with a choice of which resident they would like to contact. This choice may be given before the phone rings or alternatively only if the phone is unanswered busy or no answer . The call may be redirected per filters profile parameters settings and mode after caller makes a selection.

In another implementation each user who shares a home phone line has his or her own personal telephone number PTN . This PTN may be a permanent TN given to a callee or it can be temporary. A set of such PTNs is configured to all point to the same home phone line A.

Without DNP each of these aliased TNs rings the same phone line. Such a personal TN can be used by a person wherever they reside within the DNP service area.

With DNP callee can decide if calls to his or her personal TN ring the common home line A or another phone line cell phone B office phone C dorm phone vacation home phone or the like . In this implementation callee may have a lifetime TN that will always reach them as long as they are within the area served by DNP for example the area served by the North American Numbering Plan . An additional TN may be dedicated to the location of a phone line. For example caller could dial PTN 1 for a user X PTN 2 for user Y or TN 3 for the residential phone line home of X and Y. This location TN would typically be given out for location based services such as pizza delivery.

Information for filters based on calling TN can be extracted batch or real time from the callee s address book. This address book may be stored on the user s computer a different server such as a Microsoft Exchange server or a web based address book.

DNP allows third party companies to offer application services to customers involving the control of common carrier voice devices.

In one embodiment Substitute TNs STN Delivery TNs are authenticated before they can be selected for use so as to minimize the risk of someone hijacking the calls of a user . In one embodiment this authentication process consists of the user logging in using web browser or phone IVR and entering the new number to be added to his or her palette of substitute telephone numbers STN . The user is given an authentication key such as a numeric sequence the user then calls a special access number such as a toll free number . In one embodiment the user must make this call from the STN to be added so that the user s ownership of or access to the STN can be verified via caller ID. The user keys in the authentication key. Once a number is authenticated the user can change his or her personal configuration to redirect to it at will. This process is used to populate a palette of delivery TNs available as destinations for call routing.

In one embodiment the STN or BTN or NATN returned from a DNP dip can be in turn used to dip an Electronic Numbering ENUM database to determine further user contact options including e mail address for voicemail voice message delivery.

In one embodiment a Dialed TN is dipped through the DNP database a notification message may be sent to the owner of the TN. This message can be delivered via SMS e mail Instant Message IM or the like. This message can contain any or all of the number called Dialed TN the caller s TN the caller s name using Caller Name CNAM service location from which the call was placed or other caller mode information and the like. In one embodiment a notification can be sent even if the call is not completed.

Notification may be sent to any device even if it is not associated with the call management system of the present invention. Notification may also be sent to a Delivery Device whether or not the Dialed TN or STN addresses the Delivery Device. If the Calling Party Blocked CID Flag indicates the Calling Party TN is blocked in one embodiment it is not sent in the notification pursuant to applicable regulation .

As described above in the present invention calls are routed based on various types of information parameters and preferences. One such parameter is filters in other words calls from some callers are allowed through while calls from other callers are routed to voicemail or the like .

In one embodiment such filters are also used for prioritization of calls. For example while in a commuting mode a filter that determines a caller is Friends and Family might cause the call to connect to the user s cell phone other calls might be routed to voicemail. A Telemarketer filter may cause calls to be terminated with a polite personalized no thank you message.

In such a case the Telemarketer filter would be looking for calls with masked caller ID or with suppressed Automatic Number Identification ANI . In an implementation that can distinguish between suppressed ANI and blocked caller ID a blocked caller ID call may be from a caller the user desires to talk to. That call can be marked ex post facto as being in an allowed filter even if the caller ID is never revealed to the user. In other words the system knows the Calling Party TN and can match it up with user characterizations without revealing the Calling Party TN to the User.

In some states the storage of called party number for a caller with blocked caller ID may be prohibited. One technique of allowing filtering in such cases is to use a trap door encryption algorithm as a hash function for matching. In this way any information stored could not be converted back to the TN of a caller with a blocked caller ID and would therefore comply with legal restrictions. Only one way encrypted data would be stored and matched. An alternate Telemarketer filter would filter out callers with caller IDs of toll free TN 800 866 etc which are commonly used by telemarketers.

The system may also determine if a call is a telemarketing call by looking at the pattern of calls placed by the caller. If the caller has placed a large number of calls to other users or non users within a short period of time especially if the calls are to sequential TN that caller could be deemed a telemarketer. Another way to classify a caller as a telemarketer is by accepting input from users. If multiple users report telemarketing calls from a caller then the system would record that fact to maintain a blacklist. Input from users could be received from a cell phone. A cumulative database of telemarketers TN or names can be used as a blacklist or spam list. 

DNP facilitates a personal long term TN that a user can point to any delivery TN. This TN can be retained as a user moves his or her residence throughout the numbering plan region. Thus DNP obviates the need for LNP.

In one embodiment when a client device such as cell phone detects a busy or no answer condition while attempting to place a call the device records the voicemail message and forwards it to the callee s voicemail platform or directly to the callee s client device.

Voicemail messages can be sent peer to peer and eliminate any or most voicemail infrastructure in the network. When a client device detects a busy or no answer condition a voicemail control exchange database can be queried for the spoken name and greeting of the callee and for the store and forward addressing information necessary to deliver the message to the callee s client. When the callee s client device is no longer busy call terminates or device is turned on it registers with the same database so the store and forward network can deliver the voicemail message. Voicemail messages recorded by the client can optionally be delivered to the user via email IM or MMS. Voicemail stores can be distributed in the network in a fashion similar to architecture conventionally used for e mail message stores.

In the above description for purposes of explanation numerous specific details are set forth in order to provide a thorough understanding of the invention. It will be apparent however to one skilled in the art that the invention can be practiced without these specific details. In other instances structures and devices are shown in block diagram form in order to avoid obscuring the invention.

Reference in the specification to one embodiment or an embodiment means that a particular feature structure or characteristic described in connection with the embodiment is included in at least one embodiment of the invention. The appearances of the phrase in one embodiment in various places in the specification are not necessarily all referring to the same embodiment.

Some portions of the detailed description are presented in terms of algorithms and symbolic representations of operations on data bits within a computer memory. These algorithmic descriptions and representations are the means used by those skilled in the data processing arts to most effectively convey the substance of their work to others skilled in the art. An algorithm is here and generally conceived to be a self consistent sequence of steps leading to a desired result. The steps are those requiring physical manipulations of physical quantities. Usually though not necessarily these quantities take the form of electrical or magnetic signals capable of being stored transferred combined compared and otherwise manipulated. It has proven convenient at times principally for reasons of common usage to refer to these signals as bits values elements symbols characters terms numbers or the like.

It should be borne in mind however that all of these and similar terms are to be associated with the appropriate physical quantities and are merely convenient labels applied to these quantities. Unless specifically stated otherwise as apparent from the following discussion it is appreciated that throughout the description discussions utilizing terms such as processing or computing or calculating or determining or displaying or the like refer to the action and processes of a computer system or similar electronic computing device that manipulates and transforms data represented as physical electronic quantities within the computer system s registers and memories into other data similarly represented as physical quantities within the computer system memories or registers or other such information storage transmission or display devices.

The present invention also relates to an apparatus for performing the operations herein. This apparatus may be specially constructed for the required purposes or it may comprise a general purpose computer selectively activated or reconfigured by a computer program stored in the computer. Such a computer program may be stored in a computer readable storage medium such as but is not limited to any type of disk including floppy disks optical disks CD ROMs and magnetic optical disks read only memories ROMs random access memories RAMs EPROMs EEPROMs magnetic or optical cards or any type of media suitable for storing electronic instructions and each coupled to a computer system bus.

The algorithms and modules presented herein are not inherently related to any particular computer or other apparatus. Various general purpose systems may be used with programs in accordance with the teachings herein or it may prove convenient to construct more specialized apparatuses to perform the required method steps. The required structure for a variety of these systems will appear from the description below. In addition the present invention is not described with reference to any particular programming language. It will be appreciated that a variety of programming languages may be used to implement the teachings of the invention as described herein. Furthermore as will be apparent to one of ordinary skill in the relevant art the modules features attributes methodologies and other aspects of the invention can be implemented as software hardware firmware or any combination of the three. Of course wherever a component of the present invention is implemented as software the component can be implemented as a standalone program as part of a larger program as a plurality of separate programs as a statically or dynamically linked library as a kernel loadable module as a device driver and or in every and any other way known now or in the future to those of skill in the art of computer programming. Additionally the present invention is in no way limited to implementation in any specific operating system or environment.

