---

title: System and method for filter content pushed to client device
abstract: A system and method are provided for filtering data be pushed from a server to a communication device in accordance with a set of predefined rules. Data to be pushed to the communication device is received at the server. A content filter engine is used to determine at the server whether the data meets criteria established by the set of predefined rules, the set of predefined rules having been established by a user of the communication device via a user interface. The data is transmitted to the communication device only if the data is not filtered by the set of predefine rules.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07752272&OS=07752272&RS=07752272
owner: Research In Motion Limited
number: 07752272
owner_city: Waterloo
owner_country: CA
publication_date: 20050111
---
The present invention relates generally to a system and method for filtering data pushed to a client device and specifically to a server side personal data filter for filtering data in accordance with user specified parameters.

Access to information has led to the success of the wireless communication device industry. Handheld wireless devices have successfully introduced portable devices that enable users to have wireless access to features such as electronic mail e mail and the Internet.

Referring to a communication infrastructure is illustrated generally by numeral . The communication infrastructure comprises a plurality of communication devices a communication network a gateway and a plurality of backend services .

The communication devices include any wired or wireless device such as a desktop computer a laptop or mobile computer a smart phone a personal digital assistant such as a Blackberry by Research in Motion for example and the like. The communication devices are in communication with the gateway via the communication network . Accordingly the communication network may include several components such as a wireless network a relay a corporate server and or a mobile data server MDS for relaying messages between the devices and the gateway . The gateway is further in communication with a plurality of the backend servers . The types of backend servers and their corresponding links will be apparent to a person of ordinary skill in the art.

In the present embodiment the MDS provides a platform for mobile applications running on wireless packet data networks by providing a secure gateway between the wireless network and corporate intranets and the Internet. Further in the present embodiment the MDS operates as part of the corporate server . An example of a corporate server is the Blackberry Enterprise Server provide by Research in Motion. The corporate server provides functions for enabling wireless applications including network connectivity encryption data transcoding and push support.

Further the MDS provides communication protocols such Hypertext Transfer Protocol HTTP and Transfer Communication Protocol Internet Protocol TCP IP connections from communication devices to corporate intranets or the Internet. Typically standard protocols are used to minimize the need to learn or apply new connectivity techniques and allow new or existing corporate applications to be extended easily to the communication devices . However it will be appreciated that proprietary protocols may also be used.

The MDS performs the necessary address translation to route data between the communication device and IP networks so the details of addressing between various networks need not be addressed by application developers.

The MDS supports multiple networks and communication devices which enables an organization to deploy and manage its data applications on a single consistent architecture.

The corporate server provides a secure private connection between the enterprise and the communication device . Using encryption algorithms such as Triple Data Encryption Standard DES symmetric key encryption data flowing between the handheld and the corporate network is fully encrypted. Typically data is not decrypted at any intermediate point.

Further the corporate server maintains information about communication device users in the enterprise. Thus for example push applications can send corporate data to specific users even when they change device subscriber identity module SIM cards or networks.

As part of the corporate server the MDS uses the same secure architecture. Accordingly standard HTTP can be used to access a corporate intranet but sensitive corporate data remains confidential.

As an HTTP proxy and transformation engine the corporate server can convert and process data that passes between communication device applications and a content server. Using MDS plug in transcoders can be written to perform custom filtering that delivers content to wireless devices in an efficient and appropriate format.

Lastly the communication devices can remain continuously connected to the wireless network. Therefore data can be sent without users having to request it explicitly. This push capability enables wireless enterprise applications that may increase users productivity and make efficient use of the network.

Typically the corporate server is responsible for sending new email messages to users communication devices automatically while the MDS enables a software developer to write push applications that send new corporate content and alerts to specific users communication devices . Therefore information can be delivered to the communication devices as it becomes available and users do not have to initiate data exchange and download.

However one problem faced by most if not all of the users of such devices is the limitation and or cost of bandwidth. Communication across the wireless network can be both slow and costly. Further another problem is the appropriateness of pushed and pulled content. That is content having no business relevance that is transferred to the communication device often consumes significant resources including network resources server resource and human resources. Accordingly there is a need for a system and method that limits occupying these resources unnecessarily.

In accordance with an aspect of the present invention there is provided a system for filtering data to be pushed from a server to a communication device in accordance with a set of predefined rules the system comprising a personal content filter database for storing the set of predefined rules the set of predefined rules comprising user defined rules received from an associated user via a user interface on the communication device and a content filter engine for implementing the set of predefined rules by preventing restricted information from being transmitted to the communication device.

In accordance with an aspect of the present invention there is provided a method for filtering data be pushed from a server to a communication device in accordance with a set of predefined rules the method comprising the steps of receiving the data to be pushed to the communication device at the server using a content filter engine to determine at the server whether the data meets criteria established by the set of predefined rules the set of predefined rules having been established by a user of the communication device via a user interface and transmitting the data to the communication device only if the data is not filtered by the set of predefine rules.

Referring to a corporate server environment in accordance with an embodiment of the present invention is illustrated generally by numeral . The corporate server environment includes a plurality of corporate servers . Each corporate server includes a MDS engine which provides the mobile data service. Further a content filter engine is provided for filtering data to be transmitted to the communication device . An administration user interface is provided for administering the parameters of the content filter engine which are stored in a content filter database .

Each corporate server further includes a personal data filter for filtering data transmitted to the communication device . Further an end user interface is provided for administering the parameters of the personal data filter which are stored in a personal content filter database .

The content filter engine may comprise proprietary software or a known third party solution embedded into the MDS engine . Such third party solutions include Surfcontrol s Web Filter n2h2 s Sentian and others as will be appreciated by a person of ordinary skill in the art.

In order to efficiently embed the content filter engine into the MDS engine Application Programming Interfaces APIs are developed for rule execution and administration purposes. The APIs are used to interface the rule language provided by the administration user interface and the end user interface with the rule language provided by the third party content filter engine . Therefore both the user of the communication device and an IT administrator need not use the user interface provided with the third party content filter engine .

The content filter database can store extensive lists of blocked Uniform Resource Locators URLs categorization of URLS and dynamic rules based and or keyword blocking support which is implemented by the content filter engine . Accordingly the content filter engine provides the ability for corporate control of the information transmitted to the communication device . Typically corporate controls are implemented and maintained by a company s Information Technology IT department and entered into the content filter database via the administration user interface . These controls are used to prevent certain types of information from being transmitted to the communication device in accordance with corporate policy.

Furthermore the content database provides convenient logging support of visited sites that may also be of interest to corporate IT. Therefore sites accessed frequently by many users or deemed useful for business purposes may be cached locally. Such decisions would be policy based.

Yet further the filtering concept can be extended to the communication device s user. The personal data filter provides the ability for personal filter policies to be defined and administrated by the user of each communication device . That is each user can set up and modify rules to apply only to their communication device . This functionality is provided to the user via the end user interface . The rules set up for each user are stored in the personal content filter database . The rules are applied by the personal data filter the backbone of which is provided by the content filter engine .

In the present embodiment in the case of a rule stored on the personal content filter database conflicting with a rules stored on the content filter database the latter takes precedence. This feature inhibits the user from overriding corporate policy.

Referring to a flow chart illustrating the operation of the filter in accordance with an embodiment of the invention is illustrated generally by numeral . In step the MDS receives data to be pushed to a communication device . In step the content filter engine compares the data with the rules established by the corporation and stored in the content filter database .

If the data comprises content prohibited by one of the stored rules then the method continues at step and the message is held at the MDS . The term content in this instance includes the origin of the data as well as the type of information being transmitted. Such information includes for example the file type file size context of the information and the like as will be appreciated by a person of ordinary skill in the art.

Depending on the rules this data may be discarded or sent to an alternate communication device. For example if the target communication device is a wireless handheld device the data may be sent to a personal computer associated with the wireless device instead. Yet further other rules may be provided which establish a deferred push and or a confirmation required push. For the deferred push data is deferred for a specified length of time or until a predefined time or condition is reached. At that point the data is pushed to the communication device . For the confirmation required push a message is sent to the communication device indicating to the user that data has been received as well as the reason it has not been transmitted. The user is given the option to have the data sent. Other rules will become apparent to a person of ordinary skill in the art.

If the data comprises content that is allowed the method continues at step and the personal data filter compares the data with the rules established by the user and stored in the personal content filter database .

If the data comprises content prohibited by one of the stored rules then the method continues at step and the message is held at the MDS . As previous described depending on the rules this information may be discarded or sent to an alternate communication device.

If the data comprises content that is allowed the method continues at step and the data is sent to the communication device .

The previous embodiment describes a case where there exists a corporate entity to set and implement corporate policy. However in some cases individuals not belonging to a corporate entity may subscribe to such services. Accordingly the filter applied in such cases is the personal data filter . Therefore steps and as described with reference to are skipped.

Although the content filter engine is described herein as being embedded within the MDS it may also be implemented as a standalone server coupled with the MDS as will be appreciated by a person skilled in the art. Further although the content filter database and the personal content filter database are illustrated as separate entities in they may be one and the same as will be appreciated by a person skilled in the art.

Accordingly it can be seen that the present invention provides the ability to filter data being pushed to a communication device and it can do so at the server side of the communication system. In this way general content filter authority is given to the IT administrator and personal content filter authority is given to end users to control their experience. The present invention provides the user goal of controlling the push barrage of data which is likely to grow exponentially in the years ahead.

Although preferred embodiments of the invention have been described herein it will be understood by those skilled in the art that variations may be made thereto without departing from the spirit of the invention or the scope of the appended claims.

