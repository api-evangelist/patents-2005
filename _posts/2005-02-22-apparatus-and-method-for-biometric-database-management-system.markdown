---

title: Apparatus and method for biometric database management system
abstract: A method and system for constructing a database management system for managing biometric data is disclosed. The disclosed system receives data from another database or from and enrollment process, encodes the data with an encoding plug-in, and stores the encoded data in a biometric data storage. The data may be enhanced before being stored. Incoming target data likewise is encoded using an encoding plug-in and may be pre-processed, and is sent to a matching algorithm that is either built-in or a plug-in algorithm. Further processing may occur after application of the matching algorithm. The disclosed database management system can be used not only for biometric database, but also for other similar types of data management.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07689005&OS=07689005&RS=07689005
owner: 
number: 07689005
owner_city: 
owner_country: 
publication_date: 20050222
---
This application claims the benefit of the filing date of U.S. Provisional Application Ser. No. 60 551 926 filed on Mar. 10 2004 and entitled Apparatus and Method for Biometric Database Management System. 

Data Driven Database Management System Ser. No. 11 044 698 filed Jan. 27 2005 claiming the benefit of U.S. Provisional Application Ser. No. 60 546 233 filed on Feb. 20 2004 Inventors Tianlong Chen and Jonathon Vu.

Memory Resident Database Management System and Implementation Thereof Ser. No. 10 347 678 Filed on Jan. 22 2003 Inventors Tianlong Chen Jonathan Vu.

Distributed Memory Computing Environment and Implementation Thereof application Ser. No. 10 347 677 Filed on Jan. 22 2003 Inventors Tianlong Chen Jonathan Vu Yingbin Wang.

Invariant Memory Page Pool and Implementation Thereof Ser. No. 10 425 730 Filed on Apr. 30 2003 Inventors Tianlong Chen Yingbin Wang Yinong Wei.

Central Linked List Data Structure and Methods of Use Filed Jul. 9 2002 U.S. Pat. No. 6 785 674 Inventor Jonathan Vu.

A Method and or System to Perform Automated Facial Recognition and Comparison Using Multiple 2D Facial Images Parsed from a Captured 3D Facial Image Ser. No. 10 757 144 filed on Jan. 14 2004 and claiming the benefit of U.S. Provisional Application No. 60 440 338 filed on Jan. 16 2003 Inventors Donald A. Milne III and Jonathon Vu.

Image Indexing Search and Implementation Thereof U.S. patent application Ser. No. 10 718 738 filed on Nov. 21 2003 claiming the benefit of U.S. Provisional Patent Application Ser. No. 60 454 315 filed on Mar. 14 2003 Inventors Tianlong Chen Yi Rui Yingbin Wang and Yinong Wei.

Single Computer Distributed Computing Method and Apparatus for Facial Identification Enhancement U.S. patent application Ser. No. 10 425 729 filed on Apr. 30 2003 Inventors Tianlong Chen Donald A. Milne Iii Yi Rui Yingbin Wang Jonathan Vu And Yinong Wei.

Integrated Portable Identification and Verification Device U.S. patent application Ser. No. 10 635 516 filed on Aug. 5 2003 Inventors Donald Milne III and Tianlong Chen.

The entirety of each of the aforementioned patents and applications is incorporated by reference herein.

The present invention is related to biometric database management system architecture and its implementation which can be used for fast management and searching on biometric data.

Traditionally it is common to use relational database management systems RDB to manage biometric data. Such relational database management systems are not designed specifically for biometric data and often impose unnecessary data query procedures in biometric data queries and matching requests. Such unnecessary procedures create unnecessary overhead thereby slowing the data queries and requests.

The present invention disclosed and claimed herein is a method and system for constructing a database management system for managing biometric data. However the disclosed database management system can be used not only for biometric database but also for other similar types of data management.

In an embodiment of the system a biometric database management system comprises means for encoding reference biometric data means for enhancing said reference biometric data a biometric data storage for storing said encoded reference biometric data and said enhanced encoded reference biometric data means for encoding target biometric data means for pre processing said encoded target biometric data a matching algorithm for comparing said pre processed encoded target biometric data to said reference biometric data and means for pro processing a result of said matching algorithm.

In an embodiment of the method the method for implementing a biometric database management system comprises the steps of providing a biometric data storage for storing and managing biometric data providing an enrollment process providing a searching process providing an encoding plug in interface in said enrollment process to convert a biometric data into an encoded biometric data providing an encoding plug in interface in said searching process to convert a biometric data into an encoded biometric data providing a searching algorithm management for said searching process said searching algorithm having at least functionality of one to one similarity comparing of biometric data providing configurable dataflow for said enrollment and searching processes and providing a unique ID for a set of biometric data in said biometric data storage.

Still other aspects features and advantages of the present invention are readily apparent from the following detailed description simply by illustrating preferable embodiments and implementations. The present invention is also capable of other and different embodiments and its several details can be modified in various respects all without departing from the spirit and scope of the present invention. Accordingly the drawings and descriptions are to be regarded as illustration in nature and not as restrictive.

Still referring to the Biometric Database Management provides all necessary management functionalities and interfaces to handle various biometric data or the like.

Still referring to the BDBS provides a set of Encoding related interfaces and . Among them the plug in Encode interface is to encode the incoming data normally an image to an encoded template which is normal for biometric data. For some special biometric data this Encode interface can be a do nothing procedure. A plug in interface is an Application Programming Interface that provides for a user to compile and link to the database or provide a dynamically linked library such as a .DLL library file in Windows environment. Such a dynamically linked library is the most preferable method. When multiple biometric data is involved one different such plug in may be required for each different biometric data type. A separate Pre encoding process is provided for any pre processing before encoding which normally includes image quality enhancement and the like. And this Pre encoding process can be configurable and a plug in or built in or a do nothing procedure. Built in means that it is provided directly by the BDBS whereas Plug in means that the actual functionality is provided by the user of the BDBS.

Still referring to the BDBS provides a Pro encoding processing function which will at least provide functionality such as indexing of the biometric data. As an option a user can provide the indexing functionally to replace the built in indexation interface . A user can configure the BDBS to allow biometric data sources and to follow two different dataflow routes route without Enhancement processing or route with Enhancement processing . Either way the BDBS will put the encoded biometric data into the Biometric Data Storage . As an option the Enhancement processing procedure can be a built in or plug in or combination of built in and plug in. It is preferably a built in functional procedure so the database management knows how data is stored inside the Biometric Data Storage .

Still referring to the BDBS will provide several different and configurable ways to handle matching procedures which are shown in the right portion of the diagram.

Still referring to as similar with the enrollment procedures the BDBS provides a plug in interface for encoding the incoming target biometric data and a configurable Pre encoding process plug in . This Encoding plug in must provide the same encoding functionality as the Encoding plug in but it preferably should not include any other functionality such as indexing .

Still referring to the BDBS provides another plug in interface the Matching Algorithm Plug in that provides one or multiple matching algorithms to handle matching comparisons between an incoming target and internal stored biometric data. The output of the matching algorithms should at least provide numerical output or other meaningful similarity scores such similarity scores preferably better be scaled into 0 to 100 numbers but it may not be true for some biometric data.

Still referring to the BDBS provides three more processing functional blocks referred to as Pre Matching Processing Built in Matching Algorithm and Pro Matching Processing . Both Pre Matching Processing and Pro Matching processing can be either built in or plug in procedures to the BDBS. The Pre or Pro refers to before or after the matching procedure either by the Plug in Matching algorithm or the Built in Matching algorithm . As an example such pre matching processing can calculate the index or index group before the actual matching algorithm which will decrease the number of actual matching processes needed and therefore is faster. Also as an example of the multiple biometric data types or multiple similarity scores generated by matching algorithms the pro matching processing procedure can be a list of similarity scores or a combined or called fused similarity score such as a similarity score from a group voting procedure as indicated in the patent application METHOD AND APPARATUS FOR FACIAL IDENTIFICATION ENHANCEMENT filed on Aug. 7 2003 with Ser. No. 10 635 565 by Tianlong Chen etc.

Still referring to the dataflow from the Incoming Target to the final result can be configurable such that data can go through path with pre matching processing or path without Pre matching processing go through path with plug in matching algorithm or go through path with built in matching algorithm and go through path with or path without Pro matching processing . That is either Pre matching processing or Pro matching processing can be enabled or disabled by configuration.

Still referring to the plug in or built in Matching Algorithms Pre Matching Processing and Pro Matching Processing can all access the Biometric Data Storage via paths and .

Still referring to in order for the plug in Matching Algorithm interface to access the Biometric Data Storage correctly a set of functions will be provided to user to hide an internal data storage format to protect database integrity. Such a set of functions should include at least read of one unit of stored biometric data.

Still referring to the encoded biometric data from Incoming Target can be stored into the Biometric Data Storage via path or indirectly into the Biometric Data Storage through paths and .

Still referring to in order to process the biometric data fast not all information related to a person will be stored in the BDBS. The other information can best be stored other types of database such as relational database. Therefore in the BDBS each person or identity of a set of biometric data should have a unique ID to be used to retrieve such other information from other databases.

Still referring to since the biometric data normally is a binary string or a set of numeric data the indexing or indexing group calculation in the pro encoding processing can be a neural network indexing procedure which can provide better and balanced categorization. Other indexing schemes may be used such as the scheme disclosed in the patent application Image Indexing Search and Implementation Thereof filed by Tianlong Chen etc. with Ser. No. 10 718 738. Normally without indexing or an indexing group the sequential searching meaning searching one after another through Biometric Data Storage will take a much longer time than an indexed search. But as a configurable option user can make a sequential searching also through the BDBS.

In the case of facial recognition the pre encoding process may include a procedure to generate a set of 2D morphed images or reconstructed 3D models from a given incoming image called parent image normally belonging to one person or one identity then in the internal data storage each morphed image in the set will not only have same unique ID for the parent image but also may have its own sub ID.

Still referring to to provide faster biometric retrieval speed the whole Biometric Database Management System can be built as an in memory database which can utilize the DMCE capability disclosed in the patent application Distributed Memory Computing Environment and Implementation Thereof application Ser. No. 10 347 677. Such capability includes the use of a virtual address referred to as a DMCE virtual address. 

The foregoing description of the preferred embodiment of the invention has been presented for purposes of illustration and description. It is not intended to be exhaustive or to limit the invention to the precise form disclosed and modifications and variations are possible in light of the above teachings or may be acquired from practice of the invention. The embodiments were chosen and described in order to explain the principles of the invention and its practical application to enable one skilled in the art to utilize the invention in various embodiments as are suited to the particular use contemplated. It is intended that the scope of the invention be defined by the claims appended hereto and their equivalents. The entirety of each of the aforementioned documents is incorporated by reference herein.

