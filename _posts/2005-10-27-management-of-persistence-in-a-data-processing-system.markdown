---

title: Management of persistence in a data processing system
abstract: A user is enabled to specify policy information for use by a persistence manager in determining how to persist information relating to a data item so as achieve a desired level of reliability. The user is permitted to specify at least two behavior requirements to be associated with information to be persisted. The first behavior requirement is specifiable for a first system state, and the second behavior state is specifiable for a second system state. The behavior requirements are interpretable by the persistence manager to determine a persistence behavior necessary to conform with the policy information.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08983922&OS=08983922&RS=08983922
owner: International Business Machines Corporation
number: 08983922
owner_city: Armonk
owner_country: US
publication_date: 20051027
---
The present invention relates to transactional systems such as messaging or database systems and more particularly to transactional systems which persist data in order to guarantee data integrity in for example the event of a system failure.

Each operation will at some point in time be written by the persistence manager through the storage interface to persistent store e.g. log at layer . When a commit associated with a set of operations a transaction is finally confirmed as having been forced to the persistent store all operations comprising the transaction are also in persistent storage and the system can guarantee to the application that it is possible to recover that set of operations in the event of a system failure. In other words whilst the persistence manager is permitted a degree of flexibility about hardening the persistence records describing the operations comprising a transaction all such operations must be on disk by the time the commit is hardened. At this point the system returns control to the application and processing can continue. Note as shown in transactions may be identified by a transaction id tid to .

Forcing data to persistent storage is however an expensive process in terms of time and processing power.

The idea of an asynchronous commit is therefore known see for example the www site IP.com000031629D. This means that as far as an application is concerned its request has happened but in reality the system may force or persist appropriate data to disk at a later time.

IDE disks for example provide an option such that under certain circumstances if asked to force data to storage such forcing is not immediately but is done asynchronously.

The www site raxco.be pages info SuperSpeed Cache supercache.htm discloses a lazy write system in which a write flush is performed once every second. This is used to improve performance for write intensive applications.

Asynchronous forcing can however result in consistency problems. If the system fails prior to a force it is not then possible to be sure of the state of the persistent storage.

In the messaging world it is also possible for the requirements for forcing data to persistent storage to be relaxed. For example a message may be designated as semi persistent . This means that upon controlled shutdown the system guarantees not too lose data but does not make the same guarantees upon system failure.

All of the above solutions are however predefined by the disk or middleware designer. Customers are not provided with any flexibility. There may be certain circumstances under which a customer is prepared to accept a particular degree of risk which is appropriate to the kind of environment that they are operating in e.g. reliability may be sacrificed for speed.

According to a first aspect the invention provides a method for a data processing system comprising enabling a user to specify policy information for use by a persistence manager in determining how to persist information relating to a data item so as achieve a desired level of reliability the enabling step comprising permitting the user to specify at least two behavior requirements to be associated with information to be persisted a first behavior requirement being specifiable for a first system state and a second behavior state being specifiable for a second system state the behavior requirements being interpretable by the persistence manager to determine a persistence behavior necessary to conform with the policy information.

In a preferred embodiment a user is permitted to specify one or more behavior requirements to be associated with information to be persisted.

Preferably at least one behavior requirement is that transactional integrity should be maintained for a set of operations on one or more data items having such a behavior requirement associated therewith.

In one embodiment the data processing system is a messaging system and the information relating to a data item is a message. In this embodiment it is possible for a user to specify delivery requirements for a message dependent upon a system operational state e.g. at most once message delivery whilst the system is at state A and exactly once delivery whilst the system is at state B. Operational states may be by way of example normal running controlled shutdown system failure system chosen checkpoint administrator chosen checkpoint.

Preferably a user is able to specify the interaction between two types of policy information both being applicable to the same information.

According to a second aspect there is provided a method for a persistence manager to persist data comprising receiving a request to persist information relating to a data item reading policy information in order to determine how to persist the information so as achieve a desired level of reliability the policy information specifying a first behavior requirement specifiable for a first system state and a second behavior requirement specifiable for a second system state interpreting behavior requirements in order to determine a persistence behavior necessary to conform with the policy information read persisting the information relating to the data item accordingly.

Preferably it is possible to determine that more than one type of policy information is applicable to the data item to be persisted in which case differences are preferably resolved to determine what persistence behavior is appropriate.

According to a third aspect there is provided apparatus for a data processing system comprising an enabling component for enabling a user to specify policy information for use by a persistence manager in determining how to persist information relating to a data item so as achieve a desired level of reliability the enabling component comprising a first permitting component for permitting the user to specify at least two behavior requirements to be associated with information to be persisted a first behavior requirement being specifiable for a first system state and a second behavior state being specifiable for a second system state the behavior requirements being interpretable by the persistence manager to determine a persistence behavior necessary to conform with the policy information.

According to a fourth aspect there is provided apparatus for a persistence manager to persist data comprising a receiving component for receiving a request to persist information relating to a data item a reading component for reading policy information in order to determine how to persist the information so as achieve a desired level of reliability the policy information specifying a first behavior requirement specifiable for a first system state and a second behavior requirement specifiable for a second system state an interpreting component for interpreting behavior requirements in order to determine a persistence behavior necessary to conform with the policy information read a persisting component for persisting the information relating to the data item accordingly.

Due to the frequently significant cost of interaction by a transactional data processing system with a persistent store it is not always possible to achieve adequate performance by synchronous use of such a store. This is true in for example a system in which new data items are short lived and the throughput is high such as a messaging system. In such an environment it may be acceptable to trade some transactionality for increased performance. There is a risk that entire but not partial transactions may be lost in the case of failures. Nevertheless depending on the type of data being processed by the system this is a risk that a user may be willing to accept in order to improve the throughput of the system.

In accordance with a preferred embodiment it is now possible for a user customer to define the behavior that is acceptable under adverse conditions i.e. well defined bad behavior in the light of failures system shutdowns and the like.

In messaging and other transactional systems today customers can request various qualities of service including various levels of persistence and reliability. For example IBM s WebSphere MQ gives some per message control so that persistent messages will not be lost but non persistent ones may be and transaction control so that all operations within a transaction will atomically succeed or fail. The meaning of such qualities of service is however pre defined.

The emphasis is typically on the provision of ever greater reliability. However there are also more low value micro transactions being processed. System users might well given the option therefore choose to take a calculated risk of incorrect answers in failure and certain other cases.

Thus in accordance with the preferred embodiment a user is permitted to define various levels of reliability in the event of operational states such as 

Other operational states could also be defined such as immediate shutdown . In certain circumstances operational states may inherit properties from other operational states. For example immediate shutdown may be seen to have the same effect as system failure .

Another example of state is a time click at regular time intervals where there is calculated risk of failure between an operation and the next time click. This can happen with lazy writing being flushed at regular intervals time clicks . Please see the http www site raxco.be pages info SuperSpeed Cache supercache.htm. Note that the prior art assures that the system is in a specified state if failure happens after that flush following an operation but does not indicate that a user may specify and control the state for failure before that flush.

Application has the ability to associate policy information with a message message type or transaction and this policy information is then used by the system to determine how the system persists requests from the application which relate to a particular message. Such policy information is preferably defined at layer three by a system administrator during system setup. Such defined policies are then preferably exposed to higher layers e.g. layer for their use. As alluded to above a policy may for example refer to a particular message to a message type or to a particular transaction. A policy may also be associated with a queue. Thus information defined at level is also preferably exposed at layer .

The request is received by the message processor and a policy for the message being PUT is determined step . The policy may be based on policy information obtained from policy information at the same time as step . also illustrates that the namespace contains policy information as discussed with reference to .

If a policy is obtained from policy information information regarding the policy is preferably transmitted with the message.

Thus when the message is received at step an appropriate processing policy can be retrieved from the request itself.

As briefly mentioned above however policy information may also be associated with a particular queue. Such policy information is preferably specified by the queue s administrator at queue definition time. also shows a sample queue persistence policy . The policy shown in the figure is As Connection which indicates that the policy defined by policy information should be used. However it is possible for a queue s administrator to specify an overriding policy. For example an administrator may decide that a particular persistence policy is appropriate irrespective of the policy specified at layer . This decision could be based on the queue administrator s knowledge of the purpose of the queue in question.

Alternatively policy information could be derived from the message being put by application of a business rule. For example a business rule which increases the level of persistence for messages of higher monetary value. A pointer to such business rule information is preferably held in layer see but is defined at layer .

Once the message processor has determined the policy the persistence policy that will be applied to the message that message is put to queue with an indication of the policy that should be applied by a persistence manager at layer as illustrated at step of .

At step persistence manager determines how and when to write to persistent storage in order to ensure conformance with the appropriate policy.

Thus the persistence manager permits an administrator to define different delivery requirements for each of the possible operational states. The persistence manager then uses the knowledge held in table to determine the overall least strict behavior required to achieve the delivery requirement specified for each operational state.

To take the example above Normal Running requires that the message is delivered exactly once . From table it is determined that there is no strict persistence requirement necessary in order to achieve exactly once delivery during normal running see entry . To achieve exactly once delivery upon controlled shutdown it is necessary to record committed PUTs and GETs prior to shutdown see entry . Finally to achieve at most once delivery should the system fail it is necessary to record any committed GETs synchronously entry . Thus in order achieve all of above delivery requirements it is necessary to record committed GETs synchronously and to record committed PUTs prior to shutdown.

Thus as indicated above policy information and queue policy information may refer to the individual operational states and desired delivery requirements for each of those states. However in order to simplify things the administrator is able to specify policy names thus creating actual policies and to associate these with sets of delivery requirements. Policies are defined by the administrator at layer but exposed by the system for use at layer and or .

In the preferred embodiment three policies are defined by the user i.e. the administrator or customer programmer rather than the middleware or system designer for 

The definition of each policy is received and held in table of . For each policy the administrator is able to define a message delivery requirement for each of the three operational states of the system which are normal running controlled shutdown and failure . Thus in order to guarantee assured delivery a message must be delivered exactly once irrespective of the operational state. An administrator may of course create additional policies and fill in their details as required.

It should therefore now be apparent that the persistence manager uses the knowledge it holds in table and the information entered by the administrator into table regarding delivery requirements to determine the appropriate persistence behavior for each policy e.g. to complete the logging behavior column of table .

Such an approach provides for a very flexible system. The persistence behavior column may be generated in a generation step at system setup or may be determined dynamically at runtime. The former is a less processor intensive approach and is therefore preferable.

Note the delivery requirement options are preferably provided to the administrator as a list from which the appropriate choice may be selected and entered into table .

In another embodiment the administrator is also provided with a list of operational states from which they may select. Table holds information about the persistence behavior necessary to achieve the appropriate delivery requirement for each of the possible operational states. The administrator s selections are then used to build table .

Thus the system described above provides the administrator with a great deal of flexibility. However given the many delivery options for even a single situation the option set within the system is likely to be huge. One way to manage this is for an administrator to choose certain collections deemed likely to be useful to give these collections names and to pre define the required persistence behavior.

Note in accordance with the preferred embodiment each data item in the persistent store resolves to a reliability level policy . This is provided as an attribute of the data item. Other attributes include a data item id and a name. When a message or data item is put or inserted into the persistent store for the first time the reliability level is provided with the data item in accordance with defined policy information. When a data item is updated or deleted from the persistent store then the reliability level is already associated with the data item as an attribute.

It may be in some circumstances that reliability policies are effectively changed as a result of the operation being performed on a data item for example during update and delete.

It should also be appreciated that policies may be picked up for each message operation and some decisions made based on these independent operations but that in other cases a global decision is made based on many separate policies and determinations. For example very strong transactional requirements associated with one operation may force higher persistence requirements on another operation than that operation would have had in isolation.

Note the preferred embodiment has been described in terms of policy information. This could be taken to imply that it must be specified by a system administrator. However this is not the case. Instead such information could be defined in the application programming interface API by a customer programmer. What is important however is that the reliability levels and their meaning at each system operational state is not pre defined. A customer is provided with the flexibility to specify their own meaning for each reliability level. In other words the customer is able to specify how much of a risk he or she is willing to accept in different situations. Thus in this instance the use of the phrase policy information is intended to encompass information defined by an administrator or by a system programmer but not by a middleware designer or programmer.

Note that although the specification has described three levels of reliability which are assured reliable and unreliable other levels are of course possible. For example a user such as an administrator or API programmer could specify that whatever happens irrespective of how often persisting to storage occurs transactionality must be maintained meaning that a transaction either completes properly or it is rolled back. This is achieved by ensuring that where a set of operations are involved in a transaction these are all forced before logging the operation COMMIT TRANSACTION. This is standard and natural behavior where operations are written in the order in which they are received. In this disclosure where operations may in general be reordered for efficiency it is a limitation of degree of which the system may choose.

Please also note that although the invention has been described in terms of messaging the invention is equally applicable to other transactional systems such as for example database systems.

