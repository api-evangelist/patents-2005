---

title: Sending a message securely over an insecure channel
abstract: Sending a message securely on an insecure channel. The message is encoded in the form of a singular matrix, and multiplied with a first non-singular matrix. The resulting first cipher data is sent to a receiver system. Receiver system multiplies the first cipher data with a second non-singular matrix and the resulting second cipher data is sent to the sender system. The sender system multiplies the second cipher data with the inverse of the first non-singular matrix, and the result is sent to the receiver system. The receiver system multiplies the received result with the inverse of the second non-singular matrix to recover the message.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07606361&OS=07606361&RS=07606361
owner: Oracle International Corporation
number: 07606361
owner_city: Redwood Shores
owner_country: US
publication_date: 20050502
---
The present invention generally relates to cryptography and more specifically to a method and apparatus for sending a message securely over an insecure channel.

In general data transmitted on insecure channels can potentially be intercepted and examined by unknown third parties intruders . There is a general recognised need in the industry to send messages securely i.e. an intruder cannot decipher a message encoded in the transmitted data even on such insecure channels.

Encryption technologies are often employed to transmit messages securely over an insecure channel. In general a sender encrypts a message to generate cipher data and send the cipher data on the insecure channel. An intruder can only decipher the message from the cipher data using a decryption technique consistent with the encryption technique.

One common encryption decryption technique combination is based on public key infrastructure PKI in which a receiver generates a key pair private key and public key using known mathematical approaches. The public key is then communicated to any of the potential senders.

A sender encrypts a message using the public key and sends the resulting cipher data on an insecure channel. In most practical scenarios only a receiver having access to the private key can recover the message from the cipher data. Accordingly messages may be sent in a secure manner even on insecure channels.

One problem with the keys based approach of above is that security of the messages depends on intruders not having access to the private key or any other key required for decryption . Once the private key is compromised an intruder may be able to decipher the messages with ease. As the key pair may not change for a long time the approach is particularly susceptible to compromise of the private key and thus of security.

What is therefore needed is a method and apparatus which enables messages to be sent securely on insecure channels while addressing one or more of the requirements noted above.

In the drawings like reference numbers generally indicate identical functionally similar and or structurally similar elements. The drawing in which an element first appears is indicated by the leftmost digit s in the corresponding reference number.

An aspect of the present invention enables sending of a message securely on an insecure channel by taking advantage of the facts that a singular matrix in which a row column is linearly dependent on the remaining rows columns when multiplied by a non singular matrix results in a singular matrix and singular matrices do not have inverses. Thus a sender system encodes a message to be sent in a singular matrix and multiples the singular matrix with a first non singular matrix. The resulting first cipher data is sent to the receiver system which further multiplies the first cipher data with a second non singular matrix to generate a second cipher data. The second cipher data is sent to the sender system.

The sender system multiplies the second cipher data with an inverse of the first non singular matrix to generate a third cipher data which is sent to the receiver system. The receiver system multiplies the third cipher data with an inverse of the second non singular matrix to recover the message.

At least from the description below it would be appreciated that an intruder having access to all the three cipher data may not be able to decipher the message. As a result the message is deemed to be sent in a secure manner even if the communication channel is insecure.

In addition the non singular matrices can be different dynamically generated for different messages and thus comprise of the keys may not be of substantial concern. Furthermore as no key exchange needs to potentially take place a priori the approach can be used to transfer messages between any pair of previously unknown systems.

In one embodiment the message thus exchanged forms a key which is then used for encryption decryption according to known approaches.

Several aspects of the invention are described below with reference to examples for illustration. It should be understood that numerous specific details relationships and methods are set forth to provide a full understanding of the invention. One skilled in the relevant art however will readily recognize that the invention can be practiced without one or more of the specific details or with other methods etc. In other instances well known structures or operations are not shown in detail to avoid obscuring the features of the invention.

In step sender system encodes a message M in the form of a singular matrix. The manner in which such encoding may be performed in an N N matrix is described in sections below with respect to in further detail.

In step sender system encrypts the message by multiplying the singular matrix M with a first non singular matrix X to obtain a matrix representing the first cipher data MX . In step sender system sends the first cipher data MX to receiver system on path . In step receiver system receives the first cipher data MX . The data transmission between sender system and receiver system can be according to any known protocols.

In step receiver system encrypts the received first cipher data MX by multiplying with a second non singular matrix Z to obtain a second cipher data ZMX . In step receiver system sends the second cipher data ZMX to sender system . In step sender system receives the second cipher data ZMX .

In step sender system multiplies the second cipher data ZMX with an inverse of the first non singular matrix X 1 to obtain a third cipher data equaling ZM . In step sender system sends the third cipher data ZM to receiver system .

In step receiver system multiplies the third cipher data ZM with an inverse of the second non singular matrix Z 1 to obtain the original message M in receiver system . The method thus ends in step .

Accordingly it may be appreciated that the original message is recovered in receiver system . The basis for asserting that the message is transmitted securely is described below.

By examining the flow chart of it may be appreciated that the set of cipher data transmitted on path include MX ZMX and ZM. Since M is a singular matrix all three cipher data represent singular matrices and thus each of the three cipher data does not have a corresponding inverse. Thus it may not be possible for an intruder to decipher Z based on ZMX and MX and X from ZMX and ZM even assuming that the intruder has access to all three cipher data .

By appropriate choice of size large dimension and elements of the three base matrices M X and Z the task of factoring deciphering individual base matrices can be made substantially computationally intensive as can be readily appreciated by one skilled in the relevant arts. However as described above the message to be transmitted is to be encoded in a singular matrix step . The manner in which such encoding can be performed is described below.

Thus with respect to the message to be transmitted is first encoded in the N 1 rows with each row having N elements . The Ith element of the Nth row MNI is then computed using the following formula 

MNI MJI RJ wherein J has values from 1 to N 1 RJ represents any number used consistently for the corresponding column in computation of each element of the Nth row and represents the cumulative addition.

Thus it may be appreciated that the message is sent securely as well. It may be further desirable to ensure that man in the middle attacks in which an intruder intercepts each data sent on path and sends some other data to the corresponding destination while the recipient does not know the actions of the intruder have not occurred in the data exchanges of the flow chart of . The manner in which sender system and receiver system may confirm that such attacks have not occurred is described below with respect to .

In step sender system generates a hash of the locally computed third cipher data ZM . In an embodiment MD5 hash well known in the relevant arts is generated. In step sender system encrypts the generated hash using a first random number as a key. Various encryption techniques well known in the relevant arts can be used. In step sender system sends the encrypted hash and the first random number to receiver system potentially in different packets on path .

In step sender system receives from receiver system an encrypted hash of the perceived third cipher data generated in step described above and a second random number used to encrypt the hash of the perceived third cipher data. The received encrypted hash is generated similar to the encrypted hash generated in step and the second random number is used similar to the first random number as in step but in receiver system .

In step sender system decrypts the received encrypted hash using the second random number. The decryption needs to be consistent with the encryption approach used in receiver system . In step sender system checks for equality of the hash generated in step with the decrypted hash. If there is equality absence of man in the middle attack is assumed. The flowchart ends in step .

It should be appreciated that the third cipher data is used in the flowchart of since ZM is computationally generated in both sender and receiver systems based on the value they received from the other party. Thus by using the approach of systems and may confirm the absence of man in the middle attacks.

It should be further appreciated that the features described above can be implemented in various embodiments. The description is continued with respect to an embodiment in which various features are operative when software instructions are executed.

CPU may execute instructions stored in RAM to provide several features of the present invention. CPU may contain multiple processing units with each processing unit potentially being designed for a specific task. Alternatively CPU may contain only a single general purpose processing unit. RAM may receive instructions from secondary memory using communication path .

Graphics controller generates display signals e.g. in RGB format to display unit based on data instructions received from CPU . Display unit contains a display screen to display the images defined by the display signals. Input interface may correspond to a key board and or mouse. Network interface provides connectivity to a network e.g. using Internet Protocol and may be used to communicate on path .

Secondary memory may contain hard drive flash memory and removable storage drive . Secondary memory may store the data and software instructions e.g. methods instantiated by each of client system which enable system to provide several features in accordance with the present invention. Some or all of the data and instructions may be provided on removable storage unit and the data and instructions may be read and provided by removable storage drive to CPU . Floppy drive magnetic tape drive CD ROM drive DVD Drive Flash memory removable memory chip PCMCIA Card EPROM are examples of such removable storage drive .

the data and instructions. Thus removable storage unit includes a computer readable storage medium having stored therein computer software and or data.

In this document the term computer program product is used to generally refer to removable storage unit or hard disk installed in hard drive . These computer program products are means for providing software to system . CPU may retrieve the software instructions and execute the instructions to provide various features of the present invention described above.

While various embodiments of the present invention have been described above it should be understood that they have been presented by way of example only and not limitation. Thus the breadth and scope of the present invention should not be limited by any of the above described exemplary embodiments but should be defined only in accordance with the following claims and their equivalents. Also the various aspects features components and or embodiments of the present invention described above may be embodied singly or in any combination in a data storage system such as a database system.

