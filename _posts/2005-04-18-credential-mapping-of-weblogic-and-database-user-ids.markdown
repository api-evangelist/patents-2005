---

title: Credential mapping of WebLogic and database user ids
abstract: A connection pool can use a credential mapper to map credentials for an application server into a credential to use with the database management system. This can allow objects such as an Enterprise Java Bean to access the database with more specific credentials than the anonymous connection pool connection user name/password.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07788497&OS=07788497&RS=07788497
owner: BEA Systems, Inc.
number: 07788497
owner_city: Redwood Shores
owner_country: US
publication_date: 20050418
---
This application claims priority to U.S. Provisional Application No. 60 643 753 entitled Credential Mapping of WebLogic and Database User Ids by Fei Luo et al. filed Jan. 13 2005.

Application servers such as the WebLogic server available from BEA Systems of San Jose Calif. allow users to do a number of functions. One of the functions that can be allowed by the application servers is to provide access to a database. In one embodiment a connection pools such as a Java Database Connectivity JDBC connection pools are provided. Such connection pools allow for a number of objects in the application server to access the database through the connection. The connection pool uses a number of connections that are already set up with the database. When a connection is needed an object at the application server uses the connection in the connection pool to connect up with the database.

In one embodiment at least one credential for the database indicates a user to a greater specificity than an anonymous connection pool ID.

Looking at the example of the Enterprise Java Bean can use connection to connect to the database . The connection can use the credential mapper to obtain a specific username and password for the database management system . Additionally the object accessing connection using the connection can obtain a different credential username and password from the credential mapper to send to the database manager system .

In the example of the thread has an Enterprise Java Bean which uses a connection to connect to the database . In this example the credential mapper can convert the credential information from the security context of the thread into the credential information for use by the database management system. A simple example uses a credential map table to map the username password from the thread into a username password for the database. Details of one implementation of a credential mapper is given in the U.S. Provisional Application No. 60 573 268 entitled TOKEN HANDLER API filed May 21 2004 incorporated herein by reference.

In one embodiment the application server uses threads which are associated with the security context such as the thread . Some of the threads can access the database using at least one credential for the database obtained from the credential mapper . The credential mapper is adapted to map at least one credential for the security context of the thread into at least one credential for the database.

The use of the credential mappers for the connection pool can be as an extension of a JDBC implementation.

A number of database manufacturers provide application programming interfaces APIs for accessing the database. A disadvantage of these APIs is that certain objects such as EJBs may not know the specific credential information to provide to the APIs. Since threads have their own associated security contexts the credential mapper can be used without needing to have the ultimate user provide an additional user name and password. For example the EJB or other object can connect to a database through the connection pool and obtain a specific username password associated with that user through the credential mapper without ever requiring the thread to independently maintain credential information for the database.

The following description gives one non limiting implementation of one embodiment. The discussion below gives one embodiment but those skilled in the art will understand that other implementations of the above described concepts can be done. Any potentially limitating language given below is to be interpreted in the context of the specific non limiting implementation and is not meant to limit the general concepts.

A database server specific identity username password can be specified in the Pool s definition. Consequently application clients that borrow and use these connections from the Pool remain anonymous to the database server. The latter is unable to perform user specific tasks like auditing access control etc.

Database vendors offer proprietary solutions to propagate client credentials over anonymous JDBC connections to solve this problem. These solutions are typically exposed through extensions to the standard JDBC API interfaces.

By virtue of the a dynamic wrapper technology applications can automatically have access to all vendor specific extensions to the JDBC API. Thus applications will be able to cast to the vendor type and invoke these extension APIs.

There exist another class of applications that do not obtain JDBC connections directly from Pools. Middle tier layers such as Oracle TopLink EJB CMP containers etc obtain the connections. WLS will be required to internally lookup the corresponding RDBMS specific identities and invoke the vendor extension APIs in this case.

Existing vendor specific APIs to set the client identities are not secure. They do not validate the identities being propagated. Hence using a new CREDENTIAL MAP would be the more secure method for applications to enable this functionality.

New configuration attribute CredentialMappingEnabled can be provided. Applications wanting to enable this feature will set this attribute to true. When this attribute is enabled the server software can internally invoke the required vendor APIs. Currently Oracle DB2 offer such extensions 

One embodiment may be implemented using a conventional general purpose or a specialized digital computer or microprocessor s programmed according to the teachings of the present disclosure as will be apparent to those skilled in the computer art. Appropriate software coding can readily be prepared by skilled programmers based on the teachings of the present disclosure as will be apparent to those skilled in the software art. The invention may also be implemented by the preparation of integrated circuits or by interconnecting an appropriate network of conventional component circuits as will be readily apparent to those skilled in the art.

One embodiment includes a computer program product which is a storage medium media having instructions stored thereon in which can be used to program a computer to perform any of the features presented herein. The storage medium can include but is not limited to any type of disk including floppy disks optical discs DVD CD ROMs micro drive and magneto optical disks ROMs Rams EPROM s EPROM s Drams Rams flash memory devices magnetic or optical cards Nan systems including molecular memory ICs or any type of media or device suitable for storing instructions and or data.

Stored on any one of the computer readable medium media the present invention includes software for controlling both the hardware of the general purpose specialized computer or microprocessor and for enabling the computer or microprocessor to interact with a human user or other mechanism utilizing the results of the present invention. Such software may include but is not limited to device drivers operating systems execution environments containers and user applications.

The foregoing description of preferred embodiments of the present invention has been provided for the purposes of illustration and description. It is not intended to be exhaustive or to limit the invention to the precise forms disclosed. Many modifications and variations will be apparent to one of ordinary skill in the relevant arts. For example steps performed in the embodiments of the invention disclosed can be performed in alternate orders certain steps can be omitted and additional steps can be added. The embodiments were chosen and described in order to best explain the principles of the invention and its practical application thereby enabling others skilled in the art to understand the invention for various embodiments and with various modifications that are suited to the particular use contemplated. It is intended that the scope of the invention be defined by the claims and their equivalents.

