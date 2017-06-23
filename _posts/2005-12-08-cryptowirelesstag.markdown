---

title: Crypto-wireless-tag
abstract: The crypto-wireless-tag containing a data set, which is characterized in that it comprises at least one block of crypto data.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07881469&OS=07881469&RS=07881469
owner: 
number: 07881469
owner_city: 
owner_country: 
publication_date: 20051208
---
The invention relates to a wireless tag wireless label commonly known as RFID Radio Frequence Identification Tag or wireless label with crypto properties hereinafter crypto wireless tag i.e. a feature to hold blocks of data containing encrypted data corresponding crypto or encryption keys and or digital signatures furthermore the invention relates to a method to operate the crypto wireless tag and a wireless crypto system for the use of the crypto wireless tag.

Wireless tags are marker as e.g. labels containing a set of data of different length often as the power of 2 i.e. 32 bit 64 bit 128 bit etc. The data sets are readable and or writeable in a contactless manner typically by a radio signal RFID Tag sent by a reading and or writing device. The way of reading is defined by a reading protocol which is specified by an instruction set. The reading and writing respectively can be done by standards as they will be approved or have been approved by the following organizations

The data sets can contain one or more blocks of data such as a block of data for a check sum a block of data for a manufacturer identification etc. Basically there may also exist one or more disposable blocks of data in the data set e.g. for manufacturer specific product information.

As a rule known wireless tags show the problem that the data set is also readable by unauthorized persons. Therefore it was proposed see Der Spiegel 46 2004 p. 194 columns 1 and 2 to protect the radio labels by a password which is expensive slow and complex.

Another problem is that the read data set can be interpreted and modified with relatively less effort. Thereby product pirates could if applicable using acknowledgement information of data sets of authentic wireless tags produce own tags which in general operation are not distinguishable from the genuine product. Also manufacturers or dealers could modify a product information e.g. a date of expiry etc. without being easily traceable.

Therefore it is an object of the present invention to provide a relatively easy and fast opportunity for solving one or more of above mentioned problems. In particular it is an object of the present invention to aggravate the readability of a wireless tag to unauthorized persons. It is another special object of the present invention to complicate falsifications of wireless tags. Yet another special object of the present invention is to facilitate authentication and or identification of the tag or items connected therewith.

This object will be solved by a crypto wireless tag according to claim a method to operate at least one wireless tag according to claim and a wireless crypto system according to claim . Advantageous embodiments are defined in dependent claims.

The crypto wireless tag contains a readable data set comprising at least one block of crypto data. Thereby in the first instance the form of the data set is irrelevant and not limited to standardized formats. The data set also can be the block of crypto data itself thus having no further blocks of data. The data set may have more blocks of crypto data of different functions and or keys. A block of crypto data means a data area to which at least one cryptographic key is associated to encrypt decrypt or identify e.g. for digital signing data i.e. comprises such a key and or comprises an information where such a key is provided.

Firstly by scanning of the key a crypto wireless tag can individually be identified and therefore authenticated whereas the key e.g. a digital signature can not easily be created or falsified due to its cryptographic nature. Secondly the key can be used alternatively or in combination to encrypt the whole further data set and or a part thereof so that only the authorized user can read and write the encrypted data respectively. Because keys do not need to be entered every time like a password the cryptographic methods can be performed easily and fast if applicable fully automatic.

Preferably the crypto wireless tag is compliant to one or more standards as for example mentioned above. This can be achieved for example by allocation of an empty array or partial array with the key and the key index respectively.

Any suitable encryption method can be used to encrypt and decrypt respectively data and or to sign and authenticate and verify respectively.

A crypto qualifier can be associated to the block of crypto data for its faster identification and designation respectively. A crypto qualifier means a string which indicates the presence of a block of crypto data. The crypto qualifier may be a block of data by itself or part of the block of crypto data.

Preferably the at least one block of crypto data i.e. the one block of crypto data or at least one of a multiplicity of blocks of crypto data comprises a cryptographic key for direct use of the cryptographic method since thus an external obtaining of the key which individually belongs to the wireless tag can be omitted due to the hint. The key may as well be split over several blocks of crypto data.

Preferably the at least one other block of data if required including another block of crypto data is encrypted based on the at least one block of crypto data to complicate an unauthorized reading and modifying. Thus also manufacturers instructions product IDs dates of expiry etc. can be protected from unauthorized access.

Preferably as a secure and commonly used encryption method a public key method is used which applies a distinct crypto key pair also designated as public key and private key secret key . Preferred known examples of encryption for utilization according to a crypto wireless tag are based on the international standard OpenPGP RFC2440 or PGP. Particularly preferred is the encryption program GNU Privacy Guard GnuPG developed by the GNU Privacy Project GnuPP is preferred.

These asymmetric encryption methods can be used e.g. if the at least one block of crypto data comprises the public Key. Preferably the private secret key is archived at a special key server e.g. of the manufacturer or at a trustcenter.

It is understood that other symmetric and asymmetric encryption methods with corresponding keys can also be used. The encryption method is not limited therefore it can be based on other encryption algorithms and encryption programs respectively such as conventional RSA Encryptions SSL SSH SHA 1 MD 5 different Huffman methods etc.

Key and key pairs respectively may also be designed as One time pads OTPs analog to PIN TAN method for Online Banking.

A wireless tag may also simultaneously contain digital signatures and crypto data keys thus the signature can be encrypted simultaneously.

The object is also solved by a method to operate at least one crypto wireless tag in which at least one block of crypto data is read by at least one reading device and at least one cryptographic method is performed by using at least one key assigned to the at least one block of crypto data. Assigned means herein that the key is either contained in the block of crypto data and if applicable has to be extracted or may be obtained by a linked access. By means of the cryptographic method encryption and or decryption can be performed or a digital signature can be verified e.g. depending on the type of tag the decoding or encoding method and the key type.

For this purpose an adequate infrastructure is required which can comprise e.g. secure data links e.g. SSL encrypted databases e.g. at specific crypto servers devices e.g. access controlled or secured with Dongles programs e.g. access controlled .

Particularly preferred especially for the use of asymmetric encryption methods the performance of a cryptographic method occurs by means of an asymmetric encryption method such as a RSA based method such as PGP or GnuPG etc. in which at least one of the blocks of crypto data of the tag comprises a public key and the at least one external block of crypto data comprises a secret key.

To ensure secure performance of the method it is advantageous if the other external block of crypto data is derived from a crypto database particularly if the crypto database is part of a trustcenter or of a specifically secured area.

For protection from unauthorized reading of the data set of a tag it is also advantageous if at least one other block of data possibly another block of crypto data of the crypto wireless tag which has been encrypted based on the at least one block of crypto data is set out decrypted and readable not until the cryptographic method is performed.

In this context it is initially irrelevant at which instance e.g. a program or the end user the data are set out readable and at which layer layers see description of performing of the cryptographic method occurs respectively.

Preferably the at least one signature contained on at least one block of crypto data of the crypto wireless tag is verified by the use of the cryptographic method for fast and easy authentication.

For operation of the method it is also advantageous if the use of the cryptographic method in the reading device occurs within a downstream external crypto client or crypto module corresponding to a crypto program component hereinafter designed as crypto module here a hardware or software implemented own device to perform the crypto method and or within a middleware e.g. at the so called Point of Sales POS. The crypto client or the crypto module may also be integrated into the writing reading device or into other programs particularly middleware in which case a call of the crypto client or crypto module preferably occurs via an own Application Programming Interface API .

In case that the reading device in reading of the wireless tag initially does not recognize the presence of the at least one block of crypto data it is advantageous in particular for easy and fast reading of tags particularly by using encrypted and normal wireless tags if the reading device is configured depending on displayed error message to recognize the at least on block of crypto data and the reading process is repeated at least once.

 Reading relating to the above described method also means writing of data whereas the reading device or reading writing device is then configured to write data and the above mentioned method is reversed accordingly in a suitable manner for example instead of a decryption an encryption is required namely before operation of the writing device or reading writing device .

The object is also solved by a wireless crypto system which comprises at least one reading device for reading or writing device for writing of the at least one block of crypto data of a crypto wireless tag furthermore a data link to a crypto database as well as a device for performing the cryptographic method by the use of at least one block of crypto data of the crypto wireless tag as well as an external block of crypto data available from the crypto database wherein the device for performing the cryptographic method is configured for receipt of the block of crypto data of the crypto wireless tag and for receipt of the external block of crypto data. Depending on the operation mode reading writing unencrypted data can be read out to a middleware or encrypted data can be sent to the writing device.

A particularly preferred wireless crypto system has a device for performing the cryptographic method which is a hardware or software implemented crypto client or a crypto module which is e.g. implemented within the writing reading device and or in an independent form e.g. a dongle or a crypto box downstream to the reading device and or integrated into a middleware. In case of integration into other programs the crypto module can be e.g. called via APIs or as sub program.

It is understood that a wireless crypto system is also encompassed which is instead of or additionally not only equipped for reading and decryption of data stored on the crypto wireless tag but also for encryption and writing of data to the crypto wireless tag.

Layer represents the physical layer and is defined by the specification for different wireless tags. This layer describes how data is written and read from a wireless tag.

Layer represents the encoding layer. This layer describes the structure of a data stream which is written to a wireless tag or read from a wireless tag i.e. among other things which arrays of information it contains and in which way these arrays the data of these arrays are interpreted by corresponding writing or reading devices and or the middleware software. Layer can contain the encoding schemes of conventional standards such as EAN and others. This layer is predominantly used for backward compatibility of presently existing encoding schemes. Generally it is possible to define new encoding schemes preferably not conflicting with existing encoding schemes so that consistency of already existing encoding standards is preserved. The terms encoding and decoding respectively do not refer to cryptographic methods and should not mistaken with terms encryption and decryption .

Layer is designated as User Data Layer and contains freely definable data. Layer can contain character data as well as numeric data. In general Layer can contain any kind of data which a user intends to write on a wireless tag. Of course the existing memory limitation has to be taken into account. It is not mandatory that the data contained in Layer are stored in a structure defined by a standard and therefore it is required to control these data by superior software and or hardware instances. Within this layer no interpretation of data occurs.

Layer represents the data instance and is designated as application layer. This is a suitable infrastructure software and or hardware having the information how to interpret data of layer and or layer . Layer receives and produces data and processes these data into corresponding usable data e.g. usable by the user. This may be a software application e.g. a sub program a device driver or any resource operating with layer .

The process through the layers is achieved by passing through from higher layers down to lower layers or vice versa. The layers are independent from each other and therefore each layer provides an interface for data exchange. This is necessary to define for example the architecture of devices such as reading devices or of software applications. In case a reading device to read wireless tags exists which is conceived to read layer the software for the reading device has to be a layer compliant software to obtain full functionality through the layers.

Relating to this layer model crypto technology can be applied to layer layer and layer see lock symbol .

For easier demonstration this figure does not distinguish between encryption decryption of information and digital signing of information and the wireless tag per se respectively.

It is possible to differentiate on which layer the decryption or encryption occurs respectively and which information stored on a wireless tag is encrypted. That means that all or parts of stored data here encryption decryption or a digital signature are encrypted cryptographically secured .

In principle all known crypto encryption methods can be used to encrypt and decrypt data from a crypto wireless tag. For implementation and e.g. creation of an infrastructure it is advantageous to use conventional crypto as used e.g. to encrypt and decrypt emails respectively. For this purpose crypto technologies known in the art can be used such as PGP Pretty Good Privacy or GnuPG crypto programs and crypto algorithms respectively. In this a limited or unlimited bit stream passes through a crypto process and is transformed into an encrypted bit stream. Since at present wireless tags have a limitation in memory capacity the encrypted bit stream may be adapted according to the size of the physically available memory. As a consequence the amount of recordable data is limited by the physical layer .

Crypto technology according to the state of the art in combination with a corresponding infrastructure allows to used crypto key pairs as digital signature and identification key respectively on wireless tags against which an authentication can be applied. This digital signature and identification key may be used respectively to identify and or authenticate wireless tags and thus also items linked to this tag. Furthermore the digital signature and identification key respectively may be used as index to a source of data which may provide more information. Digital signing has the advantage that it is possible to operate with stable bit stream length. Each crypto key used for this method has a defined length depending on the used crypto mode e.g. 64 bit or 2024 bit crypto key . In case that bit stream length of the used key exceeds the bit stream length defined by layer compression algorithms may be used to adapt bit stream length of the crypto key. A crypto wireless tag can also hold several blocks of data with several functions such as encryption and signature.

The underlying infrastructure can be completely or partially opened to the public or can be completely or partially limited to instances.

The data set stored on the wireless tag possesses the general structure if applicable depending on respective layer B1 B2 . . . KB1 Bi Bi 1 KB2 . . . with B1 B2 . . . Bi Bi 1 . . . general blocks of data and KB1 KB2 blocks of crypto data. The number length and sequence of blocks of data can be adapted to individual requirements. For example KB1 can be a public key KB2 a digital signature etc. The general blocks of data B1 B2 . . . Bi Bi 1 . . . can be partially or completely encrypted by themselves or can be non encrypted as a whole. Blocks of data may be defined at each layer.

A wireless tag with an encoding scheme but without encryption is used. The data of the wireless tag are read by a reading device and processed by a middleware . The middleware e.g. an administration software based on SAP or the like processes data to information which have a significance to the end user here indicated as figures . These end user could be e.g. a salesperson a transport person a trader a customs officer or an end user. In this figure the encoding thus the conversion of information at a higher layer occurs downstream to the reading device if applicable also by an unit e.g. software integrated into a reading device and then in a further step forward to the end user the encoding and decoding respectively symbolically indicated by small wheels .

Writing of information to the wireless tag occurs in reversion of this method. In this context no reading device has to be used but a corresponding writing device preferably a combined reading writing device instead of encoding decoding is used.

The reading or writing device has the function to decrypt and encrypt wireless tags respectively. For this purpose the reading or writing device is connected to an appropriate infrastructure providing corresponding information which is required to encrypt and decrypt the wireless tag respectively. In this figure the infrastructure comprises a crypto database with information which is required to encrypt and decrypt respectively such as a secret key. The database can be part of the infrastructure e.g. of a company internal network or functionally connected to it e.g. as independent trustcenter which is connected via a data link to the company network.

Thus in this figure encrypted data are read from the reading device decrypted by means of the public key contained on the tag and the secret key of the crypto database and then processed as usual i.e. decoded or encoded.

In this case a corresponding instance designated as crypto client or Crypto module is inserted between the reading or writing device and the middleware . In this embodiment the data are not sent from the reading or writing device to the middleware or vice versa but pass through the crypto client or crypto module which performs the encryption and decryption respectively. The crypto client or crypto module is connected to an appropriate infrastructure here to a database providing corresponding information which is required to respectively encrypt and decrypt the data e.g. the public key.

This embodiment is very similar to the embodiment shown in unless the crypto client or crypto module is part of the middleware . The middleware itself e.g. a SAP program or another administration software has an Application Programming Interface API which may be used by an appropriate infrastructure in this case providing the relevant information from a crypto database which is required to encryption and decryption of the data respectively.

In this embodiment the crypto client crypto module is placed between the middleware and end user for encryption and decryption respectively.

The above mentioned as well as other suitable methods for operating the a crypto wireless tag may be used in manifold applications which are not limited by this description. In the following some application scenarios and examples are specified.

By using the present wireless tag technology the protection of the privacy is not guaranteed i.e. unauthorized third parties may access information which is sent by the unencrypted wireless tag. By using crypto wireless tags an unauthorized reading of information is completely or partially excluded. From a variety of possible applications for crypto wireless tags the following examples are given 

Presently a significant economic damage is caused over all branches by illegal produced falsified or copied products. Crypto wireless tags with a digital signature allow to keep a genuine certificate at product level. This is achieved by combining digitally signed crypto wireless tags with an appropriate environment e.g. a hierarchical trustcenter as authentication instance. Of a variety of possible applications for crypto wireless tags the following examples are given 

