---

title: Full text search capabilities integrated into distributed file systems— incrementally indexing files
abstract: A hierarchical distributed search mechanism is integrated into a distributed file system. Traditional file system APIs (create, open, close, read, write, link, rename, delete, . . . ) and the over-the-wire protocols employed to project these APIs into remote client sites (CIFS, NFS, DDS, Appletalk) are extended to enable the dynamic creation of temporary directories containing links to objects identified by search engines (executing at sites “close” to “their” data) as meeting the search criteria specified by the first parameter of a search function call. The search function, derived from the standard file system API function create, is added to the file system API.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08504565&OS=08504565&RS=08504565
owner: 
number: 08504565
owner_city: 
owner_country: 
publication_date: 20050909
---
This application claims the benefit of U.S. Provisional Patent Application Nos. 60 608 229 filed on Sep. 9 2004 and 60 621 208 filed Oct. 22 2004.

The present disclosure relates generally to full text indexing and searching applied to distributed file systems.

The volume of information contained within a single file system has increased dramatically since file systems were first designed and implemented. Whereas early file systems managed tens of megabytes of data today s distributed file systems often encompass tens of terabytes. This represents a million fold increase and the end is not in sight. Consider the following 

Over time the file system application programming interface API of the earliest file system implementations has been enhanced to include new functionalities. And it is time once again to extend the definition and capabilities of a file system.

Distributed Data Service DDS is a distributed file system that integrates industry standard file servers Unix Linux Windows Mac into highly distributed multi protocol virtual file servers of vast proportions. A single DDS virtual file server may encompass hundreds of petabytes. Fundamental concepts underlying a DDS virtual file server are disclosed in U.S. Pat. Nos. 5 611 049 5 892 914 6 026 452 6 205 475 6 366 952 B2 6 505 241 B2 and 6 804 706 B2 . All of the immediately preceding United States patents are hereby incorporated by reference as though fully set forth here.

DDS global file systems accessible via a DDS virtual file server encompass entities that might not normally be thought of as files so when describing DDS global file systems the term object is often used to denote a superset class which includes what is conventionally identified as a file.

DDS constructs virtual file servers from heterogeneous collections of industry standard file servers. A single DDS virtual file server provides a highly distributed file service perhaps incorporating as many as thousands of geographically dispersed file servers. As stated previously DDS is also capable of providing remote access to objects other than files such as live video feeds. Accordingly the term object is generally used throughout this document to denote a file a data stream or some other data entity that might stretch the definition of file .

The DDS architecture provides a framework for highly distributed multi protocol file caching. illustrates a basic structure for a DDS cache module referred to by the general reference character . The DDS cache module may be installed on file servers client workstations and intermediate network nodes such as routers switches and dedicated file caching appliances.

DDS implements a file level cache layered above all data sources. A data source is usually a file system either local or remote but it could be for example a real time data stream. When appropriate each DDS cache module automatically caches whatever data is being accessed through its file level cache regardless of the source of data.

Individual file level caches using both local RAM and local disk for data storage may vary dramatically in size. Some DDS cache modules perhaps within switches and routers may implement only RAM based caching. Other DDS cache modules in high capacity locations might be configured with 16 gigabytes of RAM and a terabyte or more of disk storage.

Although some current distributed file system implementations employ callback mechanisms to synchronously invalidate file images cached just below the multiple client processes accessing a shared file all processes remain unaware of the consistency operations. When a process reads a file the response includes the most recently written data the modification and whatever consistency operations were required to ensure the currency of the response remains hidden from file system clients.

Sprite CIFS and NFSv4 each implement consistency callback mechanisms as described above. Therefore since cache consistency is maintained through private communications between the server and the client components of these distributed file systems it is impossible for one process to detect another process s modification of a shared file except by reading the file. Consequently detecting shared file modifications when using distributed file systems such as Sprite CIFS and NFSv4 requires use of a polling loop that periodically reads the shared file.

All DDS cache modules maintain the consistency of cached images via origin file server callbacks. Files which are in use or have been recently used are registered with the origin file server and may receive a callback at the onset of a concurrent write sharing condition to invalidate or flush the cached file image. DDS incorporates a consistency disconnect reconnect mechanism described in U.S. Pat. No. 5 946 690 the 690 patent whereby a cached file image including the file s metadata may be disconnected from the origin file server and then at a later time weeks months years reconnected and revalidated. This is an essential mechanism for implementing high capacity long term persistent caches. The 690 patent is hereby incorporated by reference.

The DDS protocol is a remote file access protocol providing functionality comparable to NFS and or CIFS. It is designed to efficiently stream file data and metadata into large RAM disk caches distributed throughout a network and to maintain the consistency of cached images at a level which approaches that of a local cache. The DDS protocol transfers and caches images of files and objects from many different sources UFS VxFS NTFS file systems video cameras . . . with no image degrading translations between the source object and its cached image. Protocol translation is always performed at DDS Client Terminator Sites and is required only for heterogeneous with respect to the origin file server clients.

A basic concept of DDS is that DDS projects the source file system at the DDS Server Terminator Site into distant DDS cache modules . Consequently an image of data present in an upstream DDS cache buffer is identical to that in an internal file system buffer at the DDS Server Terminator Site. After a write operation modifies a file system buffer either local or remote performance is enhanced if the buffer is asynchronously written to the server s disk at the DDS Server Terminator Site. However file modifications are safeguarded when they re synchronously written to disk or some other form of stable storage. Flush levels allow both the client and the DDS Server Terminator Site to express their level of paranoia regarding file consistency. The most paranoid of the client and the DDS Server Terminator Site prevails.

The three preceding file system control operations provide the functionality required to ensure the integrity of file modifications to implement cache consistency and to quickly detect network partition events that compromise cache consistency.

The DDS protocol facilitates efficient transfers by allowing a single DDS LOAD or DDS FLUSH request to specify an array of file segments each ranging in size up to 4 gigabytes as targets of the request.

DDS LOAD and DDS FLUSH requests include flags that indicate whether the requesting DDS cache module shares memory DDS LOAD COMMON MEMORY or disk DDS LOAD COMMON DISK with the downstream DDS cache module . Whenever data is being passed between DDS cache modules with a common memory pointers to the data are returned rather than the data itself.

A distributed consistency mechanism an integral component of the DDS protocol and its implementation enables a file s consistency control site CCS only exists when there s a concurrent write sharing condition present to dynamically relocate itself as necessary ensuring that it is always positioned as far upstream from the DDS Server Terminator Site as possible but still able to monitor and coordinate all file writing operations.

The DDS protocol endeavors with a minimum number of operations to provide all the functions described above and to thereby implement a superset of the functionality provided by all remote file access protocols. The protocol employs discriminated unions to virtualize the file object metadata that flows through and is cached within the DDS layer. Metadata is represented in its native format and a discriminator identifies the format whenever the metadata is referenced by a client intercept routine in the course of responding to a file access request. This virtualization of metadata is the means that enables DDS to transparently service file access requests from unmodified client workstations regardless of the homogeneity heterogeneity of the client with respect to the origin file server.

For example in the process of responding to an NFS request the NFS client intercept routine must access the file s metadata. When the discriminator identifies the metadata format as NFS or UFS an NFS client intercept routine CIR can easily interpret the metadata and generate its response. However when the metadata format is NTFS an NFS CIR requires the services of an NTFS to UFS translation module in order to respond to the request.

U.S. Pat. No. 6 847 968 B2 the 968 patent discloses the methods employed by DDS cache modules to organize themselves into a hierarchy of domains. The 968 patent is hereby incorporated by reference as though fully set forth here.

Internet contains two top level domains com and edu. The com directory contains cnn hp ibm and inca. And finally the inca directory contains the inca domain tree depicted in . The cnn hp ibm and inca directories are each the root of a company s domain tree. As illustrates when a domain tree root directory is opened inca in this case the next level sub domains corp eng marketing sales appear.

Comparing FIG. s inca domain with the inca folder in clarifies the relationship between domains and folders they are essentially the same thing. They are both resource containers that may recursively contain other resource containers and or resource objects. A folder is a visual representation for a domain and there may be other representations.

For example the visual representation for a company s domain tree might be the corporate icon with the well known filename logo.icon stored in the root directory of the domain tree .

The Network Namespace ties together the disjunct namespaces of all the individual exported file systems to create a single namespace. DDS employs the existing network name resolution infrastructure to construct the Network Namespace. This results in the binding of exported file systems into the reference framework with which users and system administrators are already familiar.

This massive amount of data demands improved mechanisms for navigating through the global file system s namespace and for locating content of interest. Obviously valuable content that cannot be located is actually valueless.

The Internet as it exists today is an instance of a read only mostly distributed file system on the same order of magnitude as what the DDS global file system will become. Today Internet users routinely employ search engines to locate content of interest. These search engines appear to work quite well but one should consider that users generally aren t aware of relevant content that a search fails to reveal.

The DDS global file system requires a search mechanism substantially faster and more efficient than the currently deployed Internet search engines. Recognize that DDS provides a file access service complete with consistency guarantees. The Internet by comparison is an electronic distribution system for published content. Its content once published is unlikely to be modified. Furthermore when an object is modified a generous grace period is acceptable to allow the new content to migrate to distant access points web proxy cache sites .

Even after most proxy cache sites have loaded the latest version of an object it may be hours or even days before a web crawler fetches a copy to feed into an indexing engine. So new content and modifications to existing content may not show up in search results for several days.

In contrast the DDS global file system supports collaboration between individuals and groups. Whenever a document is created or modified other users often need to be aware of the changes as quickly as possible. This gives rise to a requirement that DDS to the maximum extent possible index new and modified content in real time such that a search performed a few seconds after the creation of a new document will locate that document if it does in fact satisfy the criteria of the search.

DDS provides the functionally required to enable unmodified industry standard workstations to access remote files using their native CIFS or NFS implementations. DDS virtual file servers receive NFS or CIFS requests and service them from cached data when possible and when valid cached data is not present DDS issues requests directed towards origin file servers to fetch the requested data.

Although the DDS protocol is highly streamlined and simplified in comparison with CIFS and NFS it provides essentially the same capabilities. After all the DDS protocol is designed to enable client access to files residing on very remote file servers. DDS implements the functionality provided by the file system APIs provided by Linux Unix Windows and other major operating systems.

Using a DDS NFS CIFS UFS NTFS . . . API an application establishes a connection to a content object through a series of operations 

Using the preceding method a user can laboriously navigate throughout a file system and explore its content. However discovering content by scanning directories becomes very inadequate when individual file systems encompass hundreds or thousands of petabytes of data. For such large file systems this method becomes unviable because users just don t live long enough. For large file systems users and processes require more powerful methods for locating content which enables them to quickly and efficiently establish connections to objects of possible interest.

For the Internet the problem of searching the content of large files systems has already been addressed. Internet search engines accept user s queries and in general respond by providing the user with links to Internet objects that appear to contain something which meet a query s criteria. The user then uses the links to easily connect to objects of potential interest so their content may be perused and a final user determination made as to their relevance.

It is noteworthy that Internet search engines actually represent only the most recent instance of at least three 3 successive generations of computer search engines which provide content searching 

Content based retrieval systems search engines are generally implemented as two distinct sets of applications 

Presently search engines continue to generate their inverted index structures in batch mode. Internet Web crawlers prowl sites discover new content and ship the new content back to index generation sites which are usually sites also hosting search engines . New content continuously flowing in from web crawlers accumulate at the indexing sites. Eventually the accumulated new content exceeds a threshold thereby causing it to be forwarded to an indexing engine. The indexing engine processes the new content extracting and sorting index terms and then merging the new terms into an inverted file. When invoked the indexing engine processes all the accumulated new content in a single batch operation.

Although search engine technology has changed over the last thirty five 35 years progressing from mainframe computer implementations to local area network LAN implementations and then from LAN implementations to wide area network WAN implementations the indexing component still retains its lineage indexing is still performed as a batch mode process.

There appears to be no consensus about how terms associated with full text retrieval are used. Therefore to avoid ambiguity some definitions for full text retrieval terms appear below 

In some full text retrieval implementations inverted file records are actually files. In which case inverted file as defined above refers to the set of inverted files. And in which case there is no inverted file index since the containing file system provides the indexing required to locate an inverted file record.

Although indexing and retrieval isn t the first thing that comes to mind when file system is mentioned file systems do provide fairly complete name based as opposed to content based indexing capabilities. When an object is created a new entry is created in a parent directory. The entry typically contains the object s name and a link to the object s attributes which are stored within an inode or equivalent . One of the inode s attributes is an extent map specifying the device addresses usually expressed as disk block numbers where the object itself the object s data is stored within the file system.

File systems generally use a hierarchical indexing structure that facilitates rapidly adding new entries and removing deleted entries. file system performance directly impacts overall system performance so the speed at which entries can be created deleted and looked up has been a force that has molded all current file systems. In particular name based indexing which is fairly anemic when contrasted against content based indexing is employed by all commonly deployed file systems.

File system developers have consistently and uniformly concluded that file system performance requirements exclude considering content based indexing. They ve opted for speed over heavyweight indexing.

However the file systems landscape has changed considerably over forty years. Consider the following 

Incorporating a full text search capability into existing file system APIs as seamlessly as possible provides both users and processes with enhanced capabilities for locating identifying and establishing connections based upon file content.

An object of the present disclosure is to integrate a search capability into standard file system APIs such that existing programs with little or no modifications can transparently locate and discover content as an integral step in the connection establishment process.

Another object of the present disclosure is to provide a highly scalable distributed indexing capability.

Another object of the present disclosure is to provide a highly scalable distributed searching capability.

Another object of the present disclosure is to facilitate the extremely rapid indexing of new and modified objects so that these objects can be located based on their current content.

Another object of the present disclosure is to provide a method for generating a global scope object identifier which uniquely identifies an object contained within a global file system.

Another object of the present disclosure is to employ global scope object identifiers as accession numbers see the preceding Definition of Terms for objects indexed by a content retrieval system allowing the inverted files generated in various sub domains to be merged into a single composite inverted file.

Another object of the present disclosure is to distribute the functionality of a content retrieval system such as full text retrieval throughout the nodes of a global distributed file system such that generating indexing and manipulating retrieving of index terms is performed close to the content.

Another object of the present disclosure is to provide a means by which for any given global scope object identifier the object system as in file system containing the associated object can be quickly located even when the object system is frequently un mounted from one DDS object server and mounted on another such that it is essentially a wandering object system.

Another object of the present disclosure is to provide an extensible means by which the icons used in a graphical file management tool such as Windows Explorer to represent various domains in a global file system may be defined by an administrator for that domain.

Briefly one aspect of the present disclosure is a method for incrementally indexing information contained in files within a distributed file system residing upon a virtual file server assembled by integrating a plurality of file servers. The indexing method includes 

Another aspect of the present disclosure includes methods for ensuring that each inverted file entry uniquely specifies the source of the content identified by the inverted file entry e.g. the particular file within a particular file system. The disclosed methods include generating a unique global object system id for a file system included in a distributed file system residing on a virtual file server by concatenating 

These and other features objects and advantages will be understood or apparent to those of ordinary skill in the art from the following detailed description of the preferred embodiment as illustrated in the various drawing figures.

Embedding a full text search engine into a distributed file system to automatically index the file system s content requires that the search engine 

New content becomes instantly searchable when content indexing is integrated directly into the main code path of the software routines implementing a distributed file system. However the sheer volume of information stored in large distributed file systems demands more powerful indexing capabilities. Fortunately the resources are now available to provide very robust indexing at the demanding speeds required by file systems. However content based indexing requires such a substantial amount of additional processing that speed and efficiency must be the prime directives shaping its inclusion in a distributed file system. In particular speed and efficiency dictates that inverted file index generation should be performed at a site as close to the object as possible preferably at the same site as where the object is stored.

1. Shortly after the last byte of data has been written to a newly created or modified object the client process creating the object invokes the file system s API close routine at step . In traditional file systems hierarchical name based indexing only a few attribute updates file size modification time are required to finalize some of the attributes associated with the new object. These updates are performed as usual.

2. Then at step the new object is immediately parsed. Potentially up to every word excepting junk words like and or the . . . is extracted and converted into an inverted index entry at step . As discussed further below this may include creating from the parsed information a global scope object id which uniquely specifies an object contained within the distributed file system.

4. After sorting at step the inverted index entries contained in the index term buckets are merged into the inverted file. For example the three sorted entries in the computer bucket are merged into the computer inverted file record which contains the sorted set of inverted index entries that specifically identify each occurrence of computer throughout the complete set of objects that had been previously indexed. As discussed herein see Differential Inverted File Updates below the merger may be accomplished by differencing the sorted inverted index entries against the inverted index entries for a prior version of the file to produce a difference file containing inverted index entries that indicate additions and deletions to the file and then using the inverted index entries of the difference file to update the inverted file that is associated with the content of the distributed file system.

5. After the merge completes the object is fully indexed and can be located using content based searches.

6. The close operation may return immediately after initiating a new thread to perform the full text indexing of the new object or it may return only after the full text indexing has completed. In the latter case the application that just created or modified the object is assured that the object is completely searchable from the moment the close function returns.

The preceding process updates the inverted file incrementally one object at a time. This is a departure from the batch mode updates where thousands of objects are typically processed at a time that are usually employed by today s full text retrieval systems. While updating the inverted file incrementally may not be new its integration into a file system s close operation departs significantly from known file system practice.

The process of generating an index for a collection of objects requires that every object be scanned and parsed index terms extracted . Following the parsing phase the inverted index entries are sorted and merged into the inverted file. This process is both cpu intensive and i o intensive.

As enumerated above the full text indexing of a new object may require two three or even four orders of magnitude more processing than the traditional directory hierarchy style indexing. This is a marked increase in the processing required during a file system s close operation. Therefore full text indexing must be invoked judiciously. There may be many instances where it s known beforehand that full text indexing isn t warranted for certain types of objects e.g. files containing pictures or images.

The invocation of full text indexing during a file system s close operation is optional and is controlled by either a flag bit parameter of the close function call and or the definition of a new file system API close and index.

A flag bit parameter to the close or close and index functions determines whether the full text indexing is completed before the file system s close operation returns to its caller.

Another way to increase index generation scalability is to reduce the amount of work required to update the indices for a file following its modification.

Consider a book on computer networks being written by several authors. Assume each author is writing a chapter in a separate file and all authors are interested in changes to any chapter being visible to all of them.

After a particular co author modifies Chapter 7 and the close and index routine is called the following sequence of operations occurs 

The advantage of differential updates becomes apparent when the composite document collection consists of millions of documents. The task of selectively updating book.if in this case is substantially less than the effort required to merge millions of xxxx.if files.

A preferred method for seamlessly integrating a full text search capability into the DDS virtual file server framework is to incorporate a content retrieval capability into DDS and to extend DDS s verb set distributed file system API to make this new capability accessible to DDS clients.

In addition to the standard file system verbs open close read write link rename . . . a new verb is added search. DDS clients may invoke a full text retrieval mechanism the preferred content retrieval capability by calling upon the new search file system API routine.

The response to a successful search request is a set of inverted index entries. As described previously an inverted index entry generally has the form which typically takes the form . The object id of an inverted index entry identifies an object and the other information within an inverted index entry points to a location within the object where the index term associated with the entry occurred.

Indexing content within objects of a distributed file system requires that the object id included in each inverted file entry uniquely specify the source of the content identified by the inverted file entry e.g. the particular file within a particular file system. Ensuring the existence of unique object ids globally throughout an entire distributed file system requires that the distributed file system at least maintain a registry of unique identifiers e.g. unique file system identifiers. Basically two approaches exist for registering unique identifiers 

Currently file systems for Unix Solaris and Linux are capable of generating object identifiers that are essentially unique within a particular file system. A preferred method for generating global scope object ids is to prepend to this particular type of file system object id a globally unique object system id. Accordingly a global scope object id which uniquely identifies an object throughout a global domain preferably has the following structure 

A preferred global object system id is a twelve byte number generated when a file system the most prevalent type of object system is created by for example either a newfs or mkfs Unix or Solaris command. The first four bytes of the global object system id are preferably the origin file server s ip address and the next eight bytes are preferably a high resolution time stamp microsecond or better provided by the origin file server which reflects the current time.

The first step in creating a new file system is to append the current time high resolution mode 8 bytes to four bytes representing the origin file server s ip address and use the resulting twelve byte number as a candidate for the global object system id for the file system about to be created. Next an attempt is made to register the candidate global object system id with a DDS provider locator service described below . If the global object system id is already in use the locator service responds with an error.

When the a DDS provider locator service refuses to register a global object system id because it is not unique the origin file server once again appends the current time to four bytes representing the origin file server s ip address. Because the high resolution mode current time being appended to the origin file server s ip address necessarily is for a later time the subsequently generated global object system id necessarily differs from that rejected by the DDS provider locator service. Then this new and different global object system id is submitted for registration with the DDS provider locator service. This iterative process repeats until the origin file server successfully registers a global object system id with the DDS provider locator service.

Having successfully registered a global object system id with the DDS provider locator service the origin file server proceeds with creating the new file system. After the file system is created the registered global object system id is entered into the file system superblock thereby assigning a unique and permanent identifier to the file system.

It is readily apparent to those skilled in the relevant art that there exist many other techniques which may be employed for generating and registering a unique global object system id.

An object id is a number created by a provider for the purpose of uniquely identifying an object. An object id may be temporary or it may be permanent and some providers generate both types.

For example on a Solaris file server a local process might open the same file on two different occasions and receive two different file descriptors 11 the first time and 7 the second time. A file descriptor is one type of object id. 

However a remote NFS client accessing the same file would receive a file handle that uniquely identified the file forever. An NFS client may present a file handle that it received ten years ago and hasn t used since back to the file server and that server must either establish a connection with the original file or respond with an error indicating that the file handle is no longer valid. A file handle is another type of object id. 

A method commonly used by Unix based NFS file servers to create a permanent file id is to concatenate two 32 bit numbers the inode number and the inode generation number to create a 64 bit file id. Since each time an inode is assigned to a new file its generation number is incremented an inode would have to be re used over 4 billion times before a file id of this type could repeat. These 64 bit file ids are essentially good forever.

The locator service provides a means of dynamically re routing DDS network traffic such that traffic to a specific file follows that file as the file system holding the file is repeatedly un mounted from one file server and then mounted on another server.

Whenever a new file system is mounted or un mounted a message is sent to the DDS provider locator service informing it that file system X a twelve byte global object system id is being mounted un mounted on host X a fully qualified domain name that can be resolved to an ip address .

Combining a method to create global object system ids such as the one described above with a method of determining which file server currently has a specified file object system mounted effectively decouples an object id from the server that created it.

Windows Linux and Unix file servers generate local scope object ids which can only be interpreted by the servers that generated them. The method described here enables file servers to interpret the object ids for files contained within all currently mounted file systems regardless of which file server originally generated the object id.

Consider a DDS client with a ten year old file handle. Suppose that the file associated with the old file handle resided within a file system on a disk drive that had recently been shipped to a distant location. The disk is subsequently installed on a DDS configured file server and that server mounts the file system. Then when the DDS client attempts to read the file the old server responds with an error indicating no such file system . This causes the client system to query the locator service requesting the name of the server currently providing access to file system X . The client then re directs the read request towards the new server .

The combination of global object system ids and the DDS provider locator service enables object system migration without client disruption. This capability facilitates and greatly simplifies implementing failover load balancing archival and disaster recovery type products.

The preferred method incorporates a search capability in a way that enables unmodified application programs to employ the new capability. The following example illustrates how this is accomplished 

Another method of extending standard file system APIs is to define a new function the search function. The search function s first parameter is a search specification text string and the remaining parameters are the same as those of the CreateDirectory function. One of those remaining parameters is the pathname of the domain to be searched.

When a search produces results a directory is created and it is immediately populated with links to the results. The caller opens the new directory and follows the links within to establish connections to objects that satisfied the search criteria.

An integrated content search capability gives file system clients a powerful new tool for locating content. However placing this tool within easy reach of users and there are many users creates some major scalability issues.

Given a new search verb it s imperative that DDS respond to search requests quickly and efficiently. Not only do DDS virtual file servers encompass huge pools of information but they also support millions of users concurrently. Since thousands of search requests may be in progress simultaneously searches must be performed relatively quickly and must not excessively burden the network. However responding to a search request generally places a far heavier burden on a virtual file server s infrastructure than any of the other file access requests a client might submit.

The magnitude of the content retrieval scalability issues completely dwarfs the issues associated with real time full text indexing.

Consider a single user submitting a search request specifying dds Internet com as the root of the subtree to be searched 

Clearly effectively addressing the content retrieval scalability issues is an enormous task. Accordingly a variety of methods each of which focuses on some aspect of retrieval scalability are employed to implement fast responsive and highly scalable retrieval capabilities. Each of these various methods can be categorized by its basic approach to the problem.

The following sections and sub sections follow the immediately preceding categorization and provide methods within each category.

DDS global file systems are organized as domain hierarchies. If a single monolithic search engine were used to implement a global file system s search function that search engine would be continuously burdened with the processing of every search request generated by all users and the number of users at any one time might number in the tens of millions. Obviously this monolithic approach lacks scalability.

An alternative to a monolithic solution is hierarchically distributed search engines. This approach delegates the responsibility burden of performing searches down into the sub domains. And each sub domain may instead of actually executing any search routines rely on its sub domains to provide the search capability for each of its sub domain s respective resources. In this way delegating search request processing to sub domains becomes recursive. Atomic domains leaf nodes which do not contain sub domains must either service the request or respond with an error code indicating that this domain does not provide a retrieval capability.

When a domain generates a response to a search request it merges the responses received from its sub domains if any with its own response if any .

The complete flexibility to execute searches at various levels of the hierarchy and to merge the results derives from the exclusive use of global scope object ids to identify all objects within the namespace.

Inverted files are usually generated in atomic domains leaf nodes where most of the content within a global domain resides. Generating indexes in the leaf nodes 

Consider the inca domain tree depicted in . Let s step through the processing of a search request. Referring back to a user decides to search the inca domain for all resources indexed by both computers and networking . The user right clicks on the inca folder and selects a Search . . . option which appears in a pop up menu.

A Search Dialog Box pops up and the user enters computers AND networking and initiates the search resulting in the following system call being made 

The search system call eventually results in a search request arriving at one of the inca domain portals. A DDS domain portal is an access point for the domain s resources. It is an ip address where the DDS service provides access to the domain s resources. This request is handled by a search engine integrated into DDS which may 

A dds Internet com inca  Search Results  computers AND networking directory is created for storing links to the objects identified by the search and a file descriptor for the newly created directory is returned to the caller. Using the returned file descriptor the caller may read the directory s contents and thereby begin the process of exploring the parallel namespace created by the search engine see Navigable Namespaces for Search Results Parallel Namespaces below populated with the results of the query.

  Search Results  is the root of a parallel namespace dynamically created by the integrated search engine in response to queries. Its purpose is to keep all search results in a separate namespace with only the portal to that namespace visible to users. When the user lists the contents of the dds Internet com inca directory his search results and those of other users are not displayed only the  Search Results  directory is shown. However the user can easily navigate into the  Search Results  directory to view the results of his prior searches.

A parallel namespace contains a subset of the objects contained in a primary namespace the subset composed of objects that matched a content retrieval query. For example computers AND networking is the parallel namespace root directory created by the content retrieval query computers AND networking . The computers AND networking directory is contained within dds Internet com inca  Search Results  which is the root of all parallel namespaces created by searches of the inca domain .

The  Search Results  directory also serves an administrative purpose. Search results are usually automatically deleted on a least recently used basis whenever DDS decides it s time to recover disk space. Keeping all search results under a single directory facilitates recovering disk space.

When inverted file caching is employed the consistency maintained between a source inverted file and its projections into parent domains may be subject to the mechanisms described in this section.

Searches may be executed by referencing remote inverted files contained within sub domains. DDS s caching mechanism is very effective at making static remote inverted files data that rarely changes appear to be local. However when remote inverted files are modified frequently the network traffic required to maintain cache consistency completely current indices becomes substantial. The following sections present strategies for executing searches when the content is changing at various rates.

Static domains contain documents that rarely if ever change. For example the published documents domain of a large corporation might contain employee manuals company procedures annual reports product specifications and other documents that have been the subject of a formal review process. These documents are fairly static they don t tend to change very often. The inverted files generated from these documents also tend to be static and are excellent candidates for caching in parent domains. The implication here is 

Referring to the pat domain and joe domain sub domains of the eng domain are static domains. A search executed on the hal workstation a node of the eng domain could reference remote inverted files generated by and contained within the pat domain and joe domain . Those segments of the remote inverted files accessed by the search process executing on the hal workstation would be cached locally.

Assuming the availability of cache space the hal workstation s cache would eventually be populated with whatever indices are required to support the type of queries handled by this node. These indices might be a small subset of the complete set of remote inverted files.

Energetic domains represent the other end of the spectrum. When a domain s content is constantly changing the associated inverted file is subject to continuous modifications. These modifications render inverted file caching within parent domains ineffective. So for domains with volatile content a good rule is 

Referring to the bob domain and svrail domain are both energetic sub domains of the eng domain . A search request received by the hal workstation may be forwarded to the bob domain and svrail domain and then the hal workstation may perform the search for the pat domain and joe domain . After all four searches have completed the hal workstation merges the results into a single response.

Energetic domains may be efficiently searched by remote processes by relaxing the consistency constraints on cached image projections of inverted files. Instead of ensuring that a read request always returns the most current data the consistency mechanism can be set such that a read request returns data that was current as of an hour ago.

Suppose computer is one of the search terms comprising a query. Employing relaxed consistency when the search engine references the computer indices cached at this site it checks an associated timestamp indicating when the computer indices data was last refreshed. New indices are loaded only if the cached image is out of date by more than a specified threshold e.g. one hour .

Of course many variations of delayed consistency can be conjured up to capitalize on the fact that in most instances a search that discovers all relevant content based on indices generated very recently is sufficient.

However there are situations where collaborative efforts between numbers of individuals or processes demand that content modifications be instantly visible to all members. The cost associated with maintaining this level of visibility is substantial so a mechanism is provided to selectively deliver the higher levels of indexing consistency.

A distributed search routing switch determines where a search is actually executed within a global file system hierarchy. Referring once again to let s step through the processing of a search request 

A single unrestricted search the only kind described so far targeting the com domain would generate a global wave of network traffic. The search request delivered to the millions of domains plugged into dot com would recursively propagate from domains to sub domains until every node within the com domain had participated in the search.

Obviously the amount of network activity required to satisfy a single user request is excessive and doesn t scale beyond a relatively limited number of users.

Therefore several methods may be employed to limit the distribution of search requests targeting public namespaces such as con edu gov mil net . . . . The following sub sections present some of these methods.

Referring back to the X Internet com directory contains only four entries cnn hp ibm and inca. These entries represent only a small subset of the registered members of the com domain. But these entries are the only ones contained in this windowed view of the com public namespace.

Windowed views sometimes referred to as just windows or views limit the scope of search requests to the user s world . Both implicit and explicit methods are employed to construct views conforming to each user s interest profile.

DDS monitors user activities and creates interest profiles. Window entries are created implicitly from the user interest profiles and explicitly whenever a public namespace directory is accessed.

A user can easily determine his current windowed view by simply listing or displaying the contents of the appropriate public namespace directory. And a user can easily add or remove entries by right clicking on the directory and selecting either an Add or Remove menu item.

Limiting the scope of search to a windowed view drastically reduces the number of nodes participating in a search. However a huge number of search requests are still likely to be delivered to well known domains.

As with other file system requests executing a search request may require the user to have a particular authorization level. For example a search request from a random user received by boeing.com might be forwarded to all next level sub domains where it would be rejected by all sub domains except one the public.boeing.com sub domain.

Another user an American Airlines employee submits a search request to boeing.com. This request also forwarded to all sub domains is accepted by aa.customer.boeing.com marketing.boeing.com and engineering.boeing.com in addition to public.boeing.com.

When a search request arrives at a domain portal a domain manager may route the request on to specific sub domains based on the user s identity credentials and authorization. For example when boeing.com received the search request from the American Airlines employee a boeing.com domain manager might route the request on to only aa.customer.boeing.com the American Airlines customer domain of the Boeing Company s global file system.

Selective routing filters out traffic that would otherwise be loading a domain s infrastructure. And more importantly selective routing actively directs the flow of incoming traffic and prevents malicious traffic from being indiscriminately sprayed into sub domains.

The ability of a domain manager to actively control the flow of incoming traffic is consistent with a DDS principle set forth in documents identified earlier as being included in this disclosure that a domain manager is in complete control of its resources. This principle applies to controlling the flow of network traffic within the domain.

An enterprise may decide for security or other reasons that its domain will not accept any network traffic from unknown sources. Searches will not be performed for anonymous users. However there may be public object document collections scattered throughout the enterprise s domain and these objects should be searchable and accessible by the public.

Top level enterprise domains may register the inverted files of public object collections with public search engines such as Google Alta Vista and Lycos.

The registered inverted files may be periodically downloaded to public search engines and merged into composite inverted files which are the files referenced to satisfy user queries. An individual query may be executed against multiple composite inverted files and the results may be merged into a single response.

The grouping that comprises a composite inverted file is generally an association of some sort. For example all aviation related companies might be grouped together.

Individual composite inverted files are periodically reloaded and rebuilt and then brought online replacing the previous version composite inverted file. The update cycle period is days weeks or months depending on the particular group of inverted files.

When the results of a query against several composite inverted files are merged each inverted file entry contains a global scope object id that can be presented at any DDS portal to establish a connection to the object. Of course the user must have proper credentials and authorization to actually establish a connection.

Instead of downloading registered inverted files the inverted files in remote top level enterprise domains may be remotely referenced by public search engines and dynamically cached as they re referenced. The cached indices may often constitute only a small fraction of the full set of indices. When this is the case it is more efficient to employ dynamic inverted file caching than to download and merge the complete inverted file.

When a domain search is executed a parallel namespace populated with links to primary namespace objects satisfying the search criteria is created and the file handle of the root of this namespace is returned to the process that initiated the search. The user or application may navigate this new namespace in the same manner used for the primary namespace. For example a Windows Explorer user may double click on the icon representing the  Search Results  directory within the Internet com inca folder and the computer OR PDA AND network folder and possibly other folders created by previous searches comes into view. The user may continue double clicking folders to explore the space and any of the content included within the space.

An individual link which may be a directory a symbolic link a hard link a global scope object id or even a URL has the property that it points towards an object. There are two types of links 

An object s attributes convey information about the object such as its size its creation date and its owner. Additional attributes may be defined that indicate how the object or object collection was scored by a search evaluation routine. By associating these scores with indirect links the paths to the targets are in effect scored. This path scoring greatly facilitates a user s ability to quickly home in on the most relevant content.

Indirect links are structural elements from which high resolution parallel namespaces may be constructed. The resolution of a parallel namespace is the degree to which the parallel namespace reflects its primary namespace. For example suppose the hal workstation returned a response containing links to one thousand objects. Consider the various forms the response might take 

When there are only a few results to report there is not much need to discriminate between results. The caller can just scan and evaluate each object. So an un scored direct response is an appropriate response form.

When there are a moderate number of hits to report but they re all from the same source a scored direct response is appropriate. Scores associated with each object convey hints as to which objects are the most likely to be relevant.

However when the results number in the thousands or millions search engines must structure the results in a manner that facilitates the caller s quest to locate some specific content. Indirect responses associate relevance scores with the paths to sub domains enabling the caller to discriminate between the results and navigate towards the desired content.

Any attempt to create a directory within a search results parallel namespace is interpreted and processed as a search request. The directory name the last component of the CreateDirectory pathname parameter is interpreted both as a search specification string and as the new directory s name. So for example if the user navigates to the folder Internet com inca  Search Results  computer OR PDA AND network eng and attempts to create a directory the search mechanism is invoked to search the eng domain with the directory name interpreted as the search specification. The content searched includes only the content contained within the current parallel namespace the results of a previous search .

This is a means of selectively refining a search by navigating into a region of dense results and then applying additional search criteria to further discriminate the results. Note that various dense regions of a search may be selectively discriminated using different criteria.

The . . .  Search Results  computer OR PDA AND network eng folder contains content matching the query computer OR PDA AND network within the eng domain . This folder may be searched for content matching Palm OR Handspring and the results references to Palm or Handspring PDAs with networking capabilities will be stored the . . .  Search Results  computer OR PDA AND network eng Palm OR Handspring folder.

Namespace coherency is the namespace property exhibited by the example just presented. Each component of the pathname of the Palm OR Handspring results folder accurately describes the content of that folder 

Geographically distributed applications may employ a global file system such as DDS to concurrently access a common file and through a series of read and write operations interact with each other. The DDS consistency mechanism guarantees clients that a read request always returns the most recently written data even when continents and oceans separate the reader and the writer. Obviously a strong consistency guarantee makes shared file access a more viable form of interprocess communication.

Without strong consistency guarantees the burden of clear and consistent communications must be carried by the applications. This of course adds complexity to all applications and requires that application level programmers provide a solution to a difficult problem that most likely lies outside of their areas of expertise.

Out of band signaling provides an alternative to polling for detecting shared file modifications. It provides an extensible means for a process to define and register the types of file access events for which the process should receive immediate notification.

These messages are private flowing only between a server and its client side components. They are also out of band meaning these messages exchange control information outside of normal file traffic data flow.

A server and its client side components can be viewed as a distributed process. The service collectively provided is enhanced by out of band consistency control operations.

Two methods illustrating the use of an out of band communication channel were presented above but there are practically an unlimited number of ways that multiple processes can coordinate their activities using out of band communications.

A method of establishing out of band communication channels is to extend the functionality of the consistency callback mechanisms employed by local file systems such as NTFS and distributed file systems such as DDS NFS and CIFS in the following manner 

Although the present invention has been described in terms of the presently preferred embodiment it is to be understood that such disclosure is purely illustrative and is not to be interpreted as limiting. The methods disclosed herein integrate a document retrieval mechanism into a distributed file system. The preferred retrieval mechanism is a full text retrieval system. However the disclosed methods are also applicable to other retrieval systems which are integratable into a distributed file system using the disclosed methods. Though described in the context of DDS virtual file servers the disclosed methods are also applicable to other distributed file systems such as NFS CIFS and Appletalk and to local file systems such as NTFS UFS and EXT2FS. Consequently without departing from the spirit and scope of the disclosure various alterations modifications and or alternative applications will no doubt be suggested to those skilled in the art after having read the preceding disclosure. Accordingly it is intended that the following claims be interpreted as encompassing all alterations modifications or alternative applications as fall within the true spirit and scope of the disclosure including equivalents thereof. In effecting the preceding intent the following claims shall 

