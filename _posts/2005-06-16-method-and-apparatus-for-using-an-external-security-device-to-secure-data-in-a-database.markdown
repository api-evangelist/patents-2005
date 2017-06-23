---

title: Method and apparatus for using an external security device to secure data in a database
abstract: One embodiment of the present invention provides a system that facilitates using an external security device to secure data in a database without having to modify database applications. The system operates by receiving a request at the database to perform an encryption/decryption operation, wherein the encryption/decryption operation is performed with the assistance of the external security module in a manner that is transparent to database applications. In response to the request, the system passes a wrapped (encrypted) column key (a key used to encrypt data within the database) to an external security module, wherein the wrapped column key is a column key encrypted with a master key that exists only within the external security module. The system then unwraps (decrypts) the wrapped column key in the external security module to retrieve the column key. Next, the system returns the column key to the database. The system then performs an encryption/decryption operation on data in the database using the column key. Finally, the system erases the column key from memory in the database.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07639819&OS=07639819&RS=07639819
owner: Oracle International Corporation
number: 07639819
owner_city: Redwood Shores
owner_country: US
publication_date: 20050616
---
The present invention relates to databases. More specifically the present invention relates to a method and an apparatus for using an external security device to secure data in a database without having to modify database applications.

Banks government agencies and other security conscious Relational Database Management System RDBMS users are often required to protect sensitive information. To this end many of these companies are starting to utilize certified tamper resistant external security modules ESMs to protect their data.

However due to the large amount of data that needs to be stored and processed in today s information systems it is desirable for this level of security to be made available through the RDBMS without compromising the full performance and scalability capabilities of the RDBMS. Furthermore using an ESM to protect data in an RDBMS should ideally not require changes to existing applications even if an application accesses data protected by the ESM.

External Security Modules are physical or logical devices created to be highly resistant to unauthorized access if used properly. A physical ESM is referred to as a Hardware Security Module or HSM. In an HSM all sensitive data is stored in a separate physical storage device with its own access control policies. The physical storage device along with its software interfaces are usually certified or tested against both physical and software based intrusion attempts.

A logical ESM is referred to as a Software Security Module or SSM. Sensitive data is usually encrypted in an SSM and all cryptographic processing is typically done in a protected memory space on the machine that hosts the SSM.

While existing systems that use ESMs provide an unparalleled level of security for RDBMS users they require developers of applications using the RDBMS to be aware of the type of ESM being used. Furthermore these developers must produce code within the applications to properly utilize the features of the ESM. Because of this different types of ESMs can require different programming methods and the extra customized programming overhead required before one can use an ESM can be costly.

Hence what is needed is a method and an apparatus for utilizing the security features of external security modules with relational database management systems without the problems discussed above.

One embodiment of the present invention provides a system that facilitates using an external security device to secure data in a database without having to modify database applications. The system operates by receiving a request at the database to perform an encryption decryption operation wherein the encryption decryption operation is performed with the assistance of the external security module in a manner that is transparent to database applications. In response to the request the system passes a wrapped encrypted column key a key used to encrypt data within the database to an external security module wherein the wrapped column key is a column key encrypted with a master key that exists only within the external security module. The system then unwraps decrypts the wrapped column key in the external security module to retrieve the column key. Next the system returns the column key to the database. The system then performs an encryption decryption operation on data in the database using the column key. Finally the system erases the column key from memory in the database.

In a variation on this embodiment the system generates the master key by sending a request to the external security module to create a random key with a data key type to be used as the master key. The system then flags the master key as non exportable. Finally the system receives a handle from the external security module at the database that facilitates referencing the master key during subsequent database transactions.

In a variation on this embodiment the system generates the wrapped column key by generating a random number in the external security module for use as the column key. The system then encrypts the column key with the master key in the external security module. Next the system flags the wrapped column key as exportable and passes the wrapped column key to the database. Finally the system stores the wrapped column key in a column key metadata table.

In a variation on this embodiment the system generates the wrapped column key by generating a random number in the database for use as the column key. The system then passes the column key to the external security module. Next the system wraps the column key with the master key in the external security module and flags the wrapped column key as exportable. The system then passes the wrapped column key to the database and stores the wrapped column key in a column key metadata table.

In a variation on this embodiment the external security module can be a hardware security module or a software security module.

In a variation on this embodiment the external security module is authenticated to the database via a direct attachment to the database a username and a password or a strong authentication method including a security token or a smart card.

In a variation on this embodiment the encryption can be either symmetric encryption or asymmetric encryption.

One embodiment of the present invention provides a system that facilitates using an external security device to secure data in a database without having to modify database applications. The system operates by receiving a request at the database to perform an encryption decryption operation wherein the encryption decryption operation is performed with the assistance of the external security module in a manner that is transparent to database applications. In response to the request the system passes a wrapped column key and data to an external security module wherein the wrapped column key is a column key wrapped with a master key that exists only within the external security module. The system then decrypts the wrapped column key within the external security module to retrieve the column key. Next the system performs an encryption decryption operation on the data within the external security module using the column key. Finally the system returns the encrypted decrypted data to the database.

The following description is presented to enable any person skilled in the art to make and use the invention and is provided in the context of a particular application and its requirements. Various modifications to the disclosed embodiments will be readily apparent to those skilled in the art and the general principles defined herein may be applied to other embodiments and applications without departing from the spirit and scope of the present invention. Thus the present invention is not intended to be limited to the embodiments shown but is to be accorded the widest scope consistent with the principles and features disclosed herein.

The data structures and code described in this detailed description are typically stored on a computer readable storage medium which may be any device or medium that can store code and or data for use by a computer system. This includes but is not limited to magnetic and optical storage devices such as disk drives magnetic tape CDs compact discs and DVDs digital versatile discs or digital video discs and computer instruction signals embodied in a transmission medium with or without a carrier wave upon which the signals are modulated . For example the transmission medium may include a communications network such as the Internet.

Database includes column key metadata table that includes the wrapped column keys for encrypting and decrypting data in other tables such as data table . Note that all some or none of the data in data table may be encrypted. Note that in one embodiment of the present invention it is possible to have a row key metadata table and additionally encrypt data in different rows with different keys.

External security module includes master key . Master key is contained by external security module and is not known outside of external security module .

Note that the system may operate in two modes. The first mode is a two tiered approach where column keys are encrypted as data and passed to the database for storage in the column key metadata . Upon encrypting and decrypting data the encrypted column key is passed to the ESM and the key is decrypted. A clear text version of the column key is then sent to database so that database can perform the encryption decryption operation. Upon completion of the operation the clear text version of the column key is destroyed form memory on database .

In the second mode the system handles all encryption decryption operations inside of ESM . In this mode column keys are not allowed to exist outside of ESM in clear text. This adds another level of security but potentially does not exhibit the same performance as the two tiered approach.

Note that it is also possible to have a hybrid system that uses both of the modes listed above. Data that is deemed more critical can be stored under the ESM only mode while data that might need to be accessed more readily and is not as much of a security concern might be accessed in the two phase mode. Also note that it is possible to secure extremely sensitive data in the ESM itself.

The system then performs an encryption decryption operation in database using the column key step . Upon completion to ensure security of the column key database erases the clear text version of the column key from memory step .

The following is an exemplary embodiment of the present invention. Note that the present invention is not meant to be limited to this exemplary embodiment. Below a Hardware Security Module is used as an example of an External Security Module and kernel refers to a specific implementation of a database.

From this point forward master key or MK will refer to a key that is stored within the Hardware Security Module HSM . The HSM is attached to the database and the phrase the database s HSM refers to the HSM used by that database. The key is assumed to only be accessible to the kernel. The master key should never be exposed to anyone and should only be used for encryption decryption operations by the kernel.

From this point forward assume the phrase wrapped Column Key refers to a generic Column Key encrypted wrapped under the current Master Key. The term wrapped is generally used when referring to the encryption of key material instead of data.

Note that regardless of the particular Application Programming Interface API used to access cryptographic functionality in an HSM the critical authentication stage is often designed or augmented by specific HSM vendors.

For maximum flexibility this section is written assuming that the API to interact with the HSM is based on RSA s PKCS 11 standard. This interface is the most commonly implemented standard by HSM vendors but various HSM vendors also support other APIs such as Microsoft s CAPI CryptoAPI which may also be used to provide the below functionality. Note that this is intended as a guideline for a skilled programmer to use to implement the invention. Depending on the specific HSM used the various function calls may differ. The function calls outlined may also not be the best possible implementation and may require some minor changes to ensure correctness as is common for all software.

Current PKCS 11 function definitions are taken from the following reference RSA Security Inc. PKCS 11 Cryptographic Token Interface Standard. An RSA Laboratories Technical Note Version 2.20 June 2004. Note that any HSM vendor will have to support all of the functions listed below for compatibility and also provide mechanisms for secure authentication.

Assuming PKCS 11 is used to access the token there are two types of users a Security Officer SO who is in charge of setting up user accounts and Normal Users who have access to private objects within the token. The Security Officer has account management rights only and cannot access private token objects.

Note that the first person to access the PKCS 11 token must be the Security Officer. When the token is initialized without any secrets the first contact is trusted to set up a root of trust. When the Security Officer SO performs this initial contact is when she sets up both the Security Officer account and the Normal User account.

Necessary authentication material will still be stored outside of the HSM within a secured wallet a software secret store . The kernel will use this information to authenticate with the HSM and establish a secure connection. Note that the ability to use the key materials within the HSM depends on this authentication process but that the Master Key will never be exposed outside of the HSM. The function OpenHSMSession will make the following PKCS 11 calls 

The Master Key will be a symmetric AES256 key generated using the HSM s Key Generate function. This key will be based on the internal random number generator within the HSM. The Master Key will be flagged as not exportable to insure it can never leave the HSM in the clear.

Under the two tiered security system model the Master Key will be generated as a Data Key . Only Data Keys are allowed to decrypt inputs and return the plaintext outside of the HSM boundary. Wrapper or Export Keys are only allowed to decrypt a key within the HSM for internal use.

Under the HSM only security model the Master Key will be generated as a Wrapper Key . The Master Key will still be used to encrypt Column Keys but the plaintext column keys will never be seen in the clear outside of the HSM. The purpose of the Master Key is only for backup purposes. Wrapped Column Keys can be freely backed up outside of the HSM.

The object handle can be used by the kernel in the future to reference the Master Key. The argument pTemplate is of importance here as it designates the object as a key with particular attributes. The attribute vector will establish the key as appropriate length sensitivity and use. Specifically the key will be flagged as non exportable can t ever be exported encrypted and sensitive can t be exported in the clear .

The Column Key will also be a symmetric key generated using the GenerateColumnKey function. The specific type of the key will be taken as an input to the function. The underlying code will execute almost identically as in the GenerateMasterKey function but the attribute vector will differ.

In the two tiered security system model the Column Keys will be flagged as non sensitive . This means they will be exportable off the HSM as plaintext for use by the Database for encryption. Depending on the implementation of the HSM the Column Keys may need to be generated simply as random data to be interpreted by the database as a key in order to exist in the clear outside of the HSM.

In the HSM Only security system the Column Keys will be flagged as sensitive and will not be exportable in the clear.

In both cases the Column Key will be designated as being able to perform Encrypt and Decrypt a data key and of the desired type.

All keys within the HSM will have a key handle or identifier. The function EnumerateKeys will enumerate all key handle identifiers to the caller. This function can be used to find a particular key handle that has been forgotten to audit TDE usage or to monitor key store space. The function will call 

The template holds the attributes that are searched for. In this example EnumerateKeys will perform several searches until all desired key types are found.

PKI Support is mainly intended as a key recovery management tool. As the rest of this document makes clear the bulk of encryption decryption is done with symmetric keys. Even in the event that asymmetric keys are used for encryption decryption it is unlikely that the private keys will be distributed to individual users which eliminates much of the need for a conventional Certificate Authority CA . In this case the secure HSM will be the root of trust and can be viewed as a CA.

As the main concern is now key recovery it is important to note that many HSM vendors will have out of band methods for backing up and recovering keys that may or may not use PKCS 11. The problem of key recovery and backup is left largely to the vendors. Below is a conventional way of recreating a key in the HSM by importing the plaintext key. This solution is less than ideal because customers will prefer that the plaintext key will never be exposed outside of the HSM boundaries.

The function DeriveKey can be used to import keys into the HSM using PKCS 11. The function will call the associate PKCS 11 function 

The significant information is contained in pTemplate which is used to specify the key information. The specific mechanism to import a key will be handled by the function we create and not by the HSM. In fact the HSM will always flag the key as a non local key. The base key may have to be generated using a call to C CreateObject.

Lastly there is some mention in various sources of an in bound way of importing PKCS 12 certificates to import private keys into a PKCS 11 token but specifics are vague.

The function RemoveKey will remove a key based on an identifier if the proper authentication and authorization are present. Note that keys can be created in a way that will prevent them from being destroyed even in the event that the entire device is re initialized. The main purpose of this function will be during the learning phase of a Security Officer. During this time the SO may desire to create some test keys and then later destroy them to save space. This function will call 

This function will destroy the specified object which may or may not be a key . The implementation may perform various checks to make sure the object being destroyed is a key by verifying template using a C FindObjects call.

In the two tiered security system model the kernel will feed the wrapped Column Key and the Master Key handle as inputs into the HSM. The HSM will then decrypt the wrapped Column Key with the specified Master Key and return the clear Column Key to the kernel. Then the Column Key will be used as in today s Oracle Corporation s Server Held Key model to encrypt or decrypt data from the specified table.

In the HSM only model the kernel will feed the data directly into the HSM along with the wrapped Column Key and the current Master Key handle. The HSM will unwrap decrypt the wrapped Column Key and use the key to encrypt or decrypt the data. The plaintext or ciphertext will then be returned to the kernel. In this case the HSM must support large amounts of data and this operation cannot be row by row for performance reasons. The HSM must be able to handle large groups of rows as input in order to streamline the process.

The object handle hKey must point to a key with CKA ENCRYPT set to true a data key . The pMechansim points to the encryption mechanism algorithm . Then the call 

This continues the encryption. Finally once the encryption with a particular key is finished a call to 

In the two tiered mode the unwrapping of the column key is skipped. Instead the wrapped encrypted column key is fed in as the data and the appropriate master key flagged as a data key is used to decrypt it. Then the decrypted column key is fed back to the kernel. The kernel then uses the clear column key to perform encryption decryption as needed using whatever mechanism is desired.

This function will create a signature hash and then encrypt with a specified key . This function will be mainly used to preserve data integrity. Conventionally keyed hashing specifically HMAC is used to preserve message integrity between two parties that have a shared secret. This is not to be confused with signatures which are used for both data integrity as well as non repudiation the sender cannot deny that they signed a message because the key used is only known by them . In our case keyed hashing will not have a sender and receiver but rather the HSM will act as both the sender and receiver. The actual value of HMAC in this case is somewhat limited. Specifically it may only be useful in that a brute force attacker will have one less test to verify when they have successfully cracked an encryption key.

Until the value of Keyed Hashing becomes clear the specific implementation will not be discussed. However PKCS 11 does support HMAC and HMAC verification.

Standard Hashing without a key will be called by HashData can be done using a similar code path but using the following functions. This function will create a signature hash and then encrypt with a specified key . This function will be mainly used to preserve data integrity. Most likely the data will be a column key and the hash will be stored with the wrapped key for an integrity check. To initiate the hash of data first we call 

To verify this hash the database will simply have the hash regenerated and compare the stored and re generated versions.

This function will be used to sign data with an HSM private key. This may be useful in the future when multiple HSMs wish to share keys or communicate. Signatures will insure that data arrives uncorrupted and will prevent allow HSMs to verify the source of information. This call HSMSign will proceed as follows 

This will initialize the signature with the specified key. To generate the signature the function will call 

This function signs the data. Much like the encryption function if the data is large and must be fed in piece by piece the function KeyedHash will call 

To verify the signature will use the functions and have the name HSMVerify. It will call the following functions along the same lines as the hash generation. Again we initiate the verification by calling 

To terminate a session the function EndHSMSession will be used. This function should be called whenever the HSM is not being used by the database to prevent an attacker from accessing the HSM through an open session. This function will call 

 To indicate that the application is finished with the Cryptoki library RSA Security Inc. PKCS 11 Cryptographic Token Interface Standard. An RSA Laboratories Technical Note Version 2.20 June 2004 . Then 

To setup the Token the SO must first connect to the database and call InitializeHSM. As explained above this function establishes the root of trust with the first person to contact the HSM. The function will initiate a session with the Token and then call 

to initialize the normal user PIN. This normal user PIN will be used by the kernel to authenticate to the device. Once an initial normal user PIN has been established it will be stored in the wallet or returned to the caller depending on the mode.

It must be possible to delete or revoke an existing client account in the event that a client has become compromised. To delete or revoke an existing client account call InitializeHSM and return the PIN to the calling user. This will deny the Kernel access to the HSM. InitializeHSM will destroy all keys on the HSM that are labeled as destroyable. Note that the MasterKey will be labeled as not destroyable.

To change the password call ResetNormalUserPass which in turn will login as the normal user and call 

The new PIN will be placed into the wallet. This should be used on a fairly regular basis to prevent a brute force attack on the HSM.

Recovery of the Master Key is HSM dependent and not implemented by Oracle although Oracle will support various HSM key recovery systems.

Because Column Keys exist in insecure memory encrypted by the Master Key they can be backed up on insecure memory. The wrapped keys are of no value in themselves so key recovery will simply involve rewriting the Column Key meta data table from a backup. Then encryption decryption operations proceed as before assuming the Master Key has not been lost.

If the HSM is not a shared device the HSM shall provide customers with a secure means of replicating the content of one HSM in another HSM. Some customers may deploy standby databases that can provide full access to data should the primary database fail. If the standby databases have their own HSMs the HSM must contain the same set of keys as the HSM for the primary database. Replication of data across multiple HSMs is left to the HSM manufacturer.

The foregoing descriptions of embodiments of the present invention have been presented for purposes of illustration and description only. They are not intended to be exhaustive or to limit the present invention to the forms disclosed. Accordingly many modifications and variations will be apparent to practitioners skilled in the art. Additionally the above disclosure is not intended to limit the present invention. The scope of the present invention is defined by the appended claims.

