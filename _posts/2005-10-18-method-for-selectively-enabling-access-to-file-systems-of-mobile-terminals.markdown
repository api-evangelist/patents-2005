---

title: Method for selectively enabling access to file systems of mobile terminals
abstract: Users of mobile terminals in a communication network are provided controlled access to files in a file system through the steps of configuring the files as a file body containing a file content and a file header containing content profile information; providing a security identity module and a secure agent; storing in the security identity module user profile information identifying a set of content profiles allowed for access to the file system; extracting, via the secure agent, the content profile information from the headers of the files; retrieving, via the secure agent, the user profile information stored in the security identity module; checking the user profile information and the content profile information; and providing the user with access to those files in the file system for which the user profile information and the content profile information are found to match.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08572372&OS=08572372&RS=08572372
owner: Telecom Italia S.p.A.
number: 08572372
owner_city: Milan
owner_country: IT
publication_date: 20051018
---
This application is a national phase application based on PCT EP2005 011194 filed Oct. 18 2005 the content of which is incorporated herein by reference.

The invention relates to techniques for controlling access to file systems. The invention was developed with specific attention paid to its possible application in user terminals for mobile communication networks that provide contents and services.

File systems of mobile terminals for use in present day mobile communications networks developed primarily in view of voice services do not ensure file confidentiality authenticity and integrity this applies both to mobile operator files and to user files. Data and applications stored in the file system of a mobile terminal are thus physically accessible for instance via a simple PC connection. In fact information and data transfer is simplified when the mobile terminal user stores his personal data in a memory card.

Equipment such as personal computers may be configured to provide file confidentiality authenticity and integrity based on passwords Smart Cards or other authentication means. Most of these solutions are DRM oriented DRM being an acronym for Digital Rights Management . Exemplary of these prior art arrangements is the arrangement disclosed in US A 2004054894. This arrangement aims at stopping Operating System OS services that would enable unauthorized access to DRM protected content.

Other solutions do permit ciphering of personal data by means of an external password stored by example on a Smart Card but do not permit secure distribution of contents to third parties. For instance U.S. Pat. No. 5 987 123 discloses a file system that validates an entity attempting access to a file before allowing the entity to perform file operations. A method and apparatus are disclosed that allow a computer system to trust both program and data files without the intervention of the user. This arrangement is based on two levels of validation for programs and data the former level specifies sources that the user has identified as trustworthy and not trustworthy the latter level specifies sources that the system itself considers trustworthy and not trustworthy. Data are acceptable when both levels yield positive results in a check process based on an affidavit verification mechanism. Applicants remark that this approach does not guarantee data confidentiality and the user cannot distribute secure contents to third parties.

Still other solutions are generally related to network infrastructure devices that support access to remotely stored data see e.g. WO A 2004 010304 or refer to a server architecture see e.g. WO A 2004 036350 .

Solutions also exist that can be based on secure storage devices like a SIM Security Identity Module as in EP A 1 513 040 this document discloses an arrangement where external licenses are verified by the SIM but the user cannot generate new licenses to distribute contents to third parties.

The preceding discussion indicates that the need exists for arrangements that may selectively enable i.e. control access to the file systems of mobile terminals such as e.g. terminals of mobile communication networks by simultaneously fulfilling the basic following requirements 

According to the present invention that object is achieved by means of a method having the features set forth in the claims that follow. The invention also relates to a corresponding system a SIM card for use therein as well as a computer program product loadable in the memory of at least one computer and including software code portions for performing the steps of the method of the invention when the product is run on a computer. As used herein reference to such a computer program product is intended to be equivalent to reference to a computer readable medium containing instructions for controlling a computer system to coordinate the performance of the method of the invention. Reference to at least one computer is evidently intended to highlight the possibility for the present invention to be implemented in a distributed modular fashion.

A preferred embodiment of the arrangement described herein is thus a method of providing at least one user of a mobile terminal in a communication network with controlled access to files in a file system the method comprising the steps of 

Essentially the preferred embodiment of the invention gives rise to a trusted file system. This implements a virtual trusted layer that makes the physical file system in a mobile terminal or a memory card truly secure. This arrangement ensures protection of files created by users and third parties by means of dynamic management of user profiles stored in a SIM by enabling the access to a single file or to distribution channels file classes .

The preferred embodiment of the invention ensures privacy of user data and protection of mobile operator and third parties files. User privacy is guaranteed in that the personal files stored in the trusted file system are not accessible by other people as these people do not own a valid user profile within the SIM Card and possibly are not in possession of the right PIN number. By using such a trusted file system a mobile network operator can manage in a dynamic way accesses to his own resources and services. Similarly a third party content provider can deliver his own contents in a secure and transparent way with a flexible mechanism that allows creation of single content delivery thematic channel distribution or user communities.

A basic feature of the trusted file system arrangement described herein is a transparent virtual layer interposed between a trusted application layer and the original file system layer of a mobile terminal as schematically shown in .

Access to the files stored in the trusted file system is managed by a secure agent a security identity module and a software library .

The secure agent is a software application running in the security identity module . Agent is secure in that it resides into a module the security identity module whose access is strictly controlled for example by means of password encryption. The security identity module can be for example the SIM card Subscriber Identity Module of the mobile terminal or in case the terminal is not provided with a SIM a secure repository of subscriber identity information such as a Smart Card either removable or embedded into the terminal.

Preferably the software library providing a set of functions for the associated application will be included in trusted applications running on the mobile terminal . Alternatively the software library may be shared by a plurality of trusted applications as a dynamic library residing in the operating system of the terminal .

Each file in the trusted file system considered is comprised of two parts namely a header and a body . In general the files of the trusted file system are stored in a memory of the mobile terminal either a memory physically resident on the terminal or a memory residing on a peripheral of the same terminal e.g. a memory card inserted in the terminal or a Bluetooth peripheral provided with storage capacity such as a Personal Computer .

The header contains a random identifier RI and a Content Profile CP. The Content Profile is ciphered and signed by means of a Service Key KS.

The Service Key KS is produced by means of a secret preferably non invertible function F of a Master Key MK stored in the security identity module in this embodiment the SIM card of the terminal and the Random Identifier RI generated at file creation time KS F MK RI Exemplary of such a secret function is a customized symmetric ciphering algorithm based on AES or 3 DES.

The Secure Agent is aware of the secret Function F and is thus able to decipher the Content Profile CP by reading the Random Identifier RI from the header

The Content Profile CP contains the content features required in order to characterize the content for example in terms of content identifier and the content key KC. Preferably the Content Profile CP contains type class content identifier release date user pin the content key KC and content issuer information. Other content features can be used in order to characterize particular classes of contents. In particular the issuer information allows verifying the content authenticity.

The SIM card contains the User Profile UP information that describes the user privileges related to the access to the trusted file system in other words the User Profile UP identifies all the types of file contents that are allowed for access by a given user.

Secure communication between the SIM and the software library is based on a trusted channel generated by means of methods to create secure sessions. Exemplary of these methods are cryptographic techniques based on the Diffie Hellmann algorithm and variations thereof.

When a trusted application tries to access some existing trusted file through the software library the content header is transferred to the secure agent which extracts the content profile CP after calculating the service key KS.

After receiving the content profile CP the secure agent retrieves the user privileges stored in the user profile UP and starts the matching operation. After successful verifications the secure agent sends the content key KC to the software library by means of a trusted channel and the trusted application is able to request read and write operations. In the other cases an error code is generated.

When a trusted application tries to create a new trusted file through the software library then a respective content header is created according to the preferred content profile CP and a random content key KC.

The content header once created is sent to the secure agent . After receiving the header the secure agent generates the random identifier RI completes the content profile CP with additional information e.g. issuer information etc. and encrypts the header by means of the service key KS calculated as described above.

The encrypted header is sent to the software library by means of a trusted channel . The software library is now ready to fill the new trusted file by using the content key KC.

The encrypted content includes a final hash string which can be used by the software library to check the integrity of the trusted file.

The user profile UP is managed by the mobile operator who can remove add new policy lines at each user subscription unsubscription. The user profile has at least one policy line which is the issuer information stored as a unique identifier number of the user. This line is used when new trusted files are created and it is stored in the content profile CP as content identifier ID associated to the class local and to the type document . In that way the trusted file can be read at least by the user profile that generated it.

The following lines etc. are added by the mobile operator at each user subscription in order to manage contents generated by third parties.

The content profile is managed by the content issuer generator it contains the content issuer identification and other information about the content features such as the type music video data etc. the class local event channel etc. the content identifier ID associated to each class the release date etc.

The information items may include a user PIN for use in providing additional security as better described in the following.

The secure agent searches in the user profile a grant line corresponding to the content profile and verifies the user credentials.

In general the trusted files can be generated in a local mode i.e. on board the mobile terminal or in a remote mode e.g. from an external system .

The local mode is suitable to protect personal files photos audios videos texts office data and so on such as those created by the user. Users of the arrangement described herein can thus create new trusted files by means of a content profile that binds the trusted file to their own SIM with a user PIN if necessary . This is possible by using the first line of the user profile as described above to generate a local class content profile.

When the secure agent checks the user profile information and the content profile information for a possible match in this case the match is made between the unique identifier number of the user and the content identifier in order to provide access to the file s for which the user profile information and the content profile information are found to match the secure agent may locate a user PIN possibly included in the content profile and require the user to input such a PIN into the terminal as a pre requisite to allow access to the file or files in question.

The remote mode is suitable when trusted contents are generated to be communicated to one or several users. This is useful for instance when the mobile operator has to delivery new selective services or when content providers want to delivery protected contents that is in typical DRM scenarios.

Unlike common delivery solutions where individual content items are generated with related protected license files the trusted file system arrangement described herein allows each content item to be generated according to the method described. It will be appreciated that such a content item can be generated without a related license.

An exemplary use of the remote mode is when the operator wants to delivery a selective update of subscribed services. Any user that is already a subscriber to a given service already has in his SIM a user profile line that enables access to the service contents.

The line can exhibit a format such as e.g. TYPE Data CLASS Channel ID MO12345678 FROM 1 Jan. 2006 TO 31 Dec. 2006.

This line indicates that the user in question can access all the trusted contents of the mobile operator MO with a specific ID 12345678 over a given period such as e.g. January to December 2006.

The operator generates the service update as a new trusted content with specific content profile that allows the secure agent to match the described user profile line.

The content profile will contain at least the issuer information and other descriptions similar to the user profile line such as TYPE Data CLASS Channel ID MO12345678 DATE 18 Apr. 2006.

The software library includes an interface made up of standard file system access APIs Application Programming Interfaces and in addition a set of integrity checking functions.

The following is an example of a minimal set of functions CREATE OPEN READ WRITE SEEK SIZE CHECK CLOSE.

The CREATE function is used when new local trusted files are generated or third parties create new remote trusted files. As described above this function must be provided with the content profile required to create the content header passed on to the function as an argument and if necessary with a user PIN in order to protect the content when the mobile terminal within the enabled SIM is not in the owner s hands. The CREATE function thus generates the content key KC in order to allow the WRITE function to fill the trusted file and returns the trusted file ID that will be used as the argument for other functions to specify what trusted file should be accessed. If no argument is passed on to the function a local trusted file is generated and it is accessible only by the owner SIM.

The OPEN function is used when an existing trusted file should be accessed. As described above the function checks the user profile policies and after retrieving the content key KC it returns the trusted file ID enabling the use of the other functions. If the check operation is not successful then the trusted file ID is not returned and the other functions are not enabled. If necessary a user pin can be passed to the function.

The READ WRITE functions are enabled only after successful OPEN or CREATE operations. These functions allow accessing the trusted file in a transparent way decoding or encoding the content.

The SEEK function is enabled only after successful OPEN or CREATE operations. This function allows moving the internal logical file pointer. The logical file pointer is the pointer of the original content while the physical file pointer is the pointer of the current trusted content.

The SIZE function is enabled only after successful OPEN or CREATE operations. This function retrieves the logical size of the content. The logical size is the original content size while the physical size is the current trusted content size with header and hash code .

The CHECK function is enabled only after successful OPEN or CREATE operations. This function executes the integrity check of the trusted content and returns the issuer information. This is useful to guarantee the integrity and the authenticity of the content before using it at application level.

The CLOSE function is enabled only after successful OPEN or CREATE operations. This function destroys the trusted content key KC and deletes the trusted file ID in the software library .

The arrangement described herein i.e. trusted File System technology can be used to ensure application integrity and authenticity. In particular a mobile operator can use such an arrangement to trust his own services implementations.

In fact each time an application accesses a database or a resource file associated with a certain configuration file the security identity module will enable file access only if the user possesses the correct rights. In that way protection of the contents conveyed by the configuration file is provided already at the level of such databases and or resource files.

The software library is useful also for mobile terminal management in terms of trusted upgrade delivery and can support any kind of DRM arrangement for copyrighted content distribution for instance the trusted file system arrangement described herein may be used i.a. for distributing DRM licenses.

The trusted file arrangement described herein thus makes it possible for the user to lock personal data files address book messages photos .

Without prejudice to the underlying principles of the invention the details and the embodiments may vary even appreciably with reference to what has been described by way of example only without departing from the scope of the invention as defined by the annexed claims.

