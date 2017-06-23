---

title: Token handler API
abstract: A token handler API which can be instantiated to allow for custom token types. The token handler API can interact with a web service security handler and security service provider interfaces of security framework in order to do a number of security functions such as authentication, digital signatures and encryption for SOAP messages in a Web Service security system.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07788716&OS=07788716&RS=07788716
owner: Bea Systems, Inc.
number: 07788716
owner_city: Redwood Shores
owner_country: US
publication_date: 20050518
---
This application claims priority to U.S. Provisional Application No. 60 573 268 entitled Token Handler API filed May 21 2004.

Web Services WS allow applications to share data and to invoke capabilities from other applications without regard to how those applications were built what operating system or platform they run on and what devices are used to access them. Web Services are invoked over the Internet by means of industry standard protocols including the Simple Object Access Protocol SOAP the eXtensible Markup Language XML and Universal Description Discovery and Integration UDDI .

SOAP is an XML based messaging technology standardized by the World Wide Web Consortium W3C which specifies the rules for locating Web services integrating them into applications and communicating between them. UDDI is a public registry where one can publish and inquire about Web services.

Web services security is also defined by standards. The Organization for the Advancement of Structured Information Standards OASIS has produced the SOAP message security standard. Part of the standard is the use of security tokens. These tokens are typically defined or referenced in the header of the SOAP message. The security tokens can be used for message authentication digital signature and encryption decryption. The specification defines a number of token types including User Password pairs X.509 certificates and Kerbos tickets.

The token handler API can be instantiated to define custom security token types for Web Services. This allows newly developed token standards to be implemented without affecting the SSPI or web services security handler or security service provider interface. The token handler API allows designers to customize the token types used with the SOAP messages without recompiling the entire web services software. Updates for new token types can be added as new instances of the token handler API on a web page such as a developer web page. Different instances of the credential mapper SSPI and or identify assert SSPI can be also created from the customer token type.

A security service provider interface SSPI such as the credential mapper SSPI identity assert SSPI or certificate lookup and validation SSPI can interact with the token handler API. The token handler API can use pre written or customized SSPIs.

The SSPI can connect to or be part of a security framework such as the security framework in WebLogic Server or WebLogic Enterprise Security available from BEA Systems Inc. of San Jose Calif.

The token handler API can include a number of sub interfaces. The token handler API can convert token XML into java object credentials for processing by the SSPI. The headers of the SOAP messages include tokens or references to tokens.

Looking at a SOAP message comes to the web service . In the Web Services logic is a Web Service security handler . The Web Service Security Handler can provide tokens to the token handler API . Other handlers for operating on incoming SOAP messages and constructing out going SOAP messages can also be used. The token handler API and SSPI and can be used for authorization digital signatures and encryption. In one embodiment the token handler API and SSPIs and security framework checks the authorization before the web service provides a response to a user. The Web Service can use the binding function and Enterprise Java Beans EJBs .

Message security can include integrity to ensure that the message or part of the message received has not been altered in transit. This can be implemented using digital signatures. Message security can include confidentiality to ensure that no one besides the sender and recipient can read the contents of the message or parts of the message. This can be implemented using encryption. Message security can include authentication to ensure that the person who claims to have sent signed encrypted the data is really the one who did send sign encrypt it. This can be implemented by the inclusion in the message of

The concept of message level authentication can apply to both the entire message and to specific parts of the message which may have been authenticated by a different person than the sender.

Digital Signatures Dsig and encryption can use security tokens that are included in the SOAP message. These security tokens can be of various types which are defined in auxiliary WS Security profiles . Auxiliary WS Security profiles can include 

The choice s of what token type is supported is part of the security policy of a web service and can be set from a server console such as an administration console for the WebLogic Server available from BEA Systems Inc. of San Jose Calif.

Custom token types are not uncommon because users frequently define their own authentication schemes. A TokenHandler API can be used to define and integrate custom security token types. This API can support attaching additional user defined information to the security context that is associated with the message.

The WS Security Custom Token Provider Interfaces WSS TPI can include SecurityToken SecurityTokenReference SecurityTokenHandler which extends the sub interfaces SecurityTokenFactory SecurityTokenReferenceFactory SecurityTokenProvider SecurityTokenReferenceProvider SecurityTokenProcessor and CredentialProvider. The WS Security Custom Token Provider Interfaces can reuse SPI interfaces for the CredentialMapper and IdentityAsserter.

SPI interfaces can be integrated into the WSS TPI. For example the CredentialMapper SPI can be integrated into the WSS TPI CredentialProvider. A getCredential method for WSS TPI can use a getcredential method from the CredentialMapper SPI on the server side where a subject is available. The WSS TPI implementor can use policy information to determine if a credential from CredentialMapper can should be used e.g. in case the SecurityToken assertion has only token type info use the current subject to get credential from the CredentialMapper else get the credential from the CredentialMapper in anyway and use it if it matches issuerName and claims .

The IdentityAsserter SPI can be integrated into the WSS TPI SecurityTokenProcessor. The SecurityTokenProcessor method Subject getSubject SecurityToken token can be replaced with Object getCredential SecurityToken token ContextHandler ctxHandler . The ContextHandler can be used to pass information that might be needed to validate the token or derive the credential from it the SOAP message XMLSignature and EncrpytedType objects created from it the call is made after the whole header has been processed call depends on config info. The WSS runtime can use the obtained credential to call PrincipalAuthenticator.assertIdentity String tokenType Object token ContextHandler contextHandler . This will call the IdentityAsserter configured for the tokenType implementors of WSS TPI can either map their WSS tokenType to aleady existing security tokenTypes or implement and register a custom IdentityAsserter for their tokenType.

The custom IdentityAsserter can return a CallbackHandler that can handle NameCallback filling in the user name from the token that has been passed in to IdentityAsserter

Embodiments of the present invention may be implemented using a conventional general purpose or a specialized digital computer or microprocessor s programmed according to the teachings of the present disclosure as will be apparent to those skilled in the computer art. Appropriate software coding can readily be prepared by skilled programmers based on the teachings of the present disclosure as will be apparent to those skilled in the software art. The invention may also be implemented by the preparation of integrated circuits or by interconnecting an appropriate network of conventional component circuits as will be readily apparent to those skilled in the art.

One embodiment includes a computer program product which is a storage medium media having instructions stored thereon in which can be used to program a computer to perform any of the features presented herein. The storage medium can include but is not limited to any type of disk including floppy disks optical discs DVD CD ROMs micro drive and magneto optical disks ROMs Rams EPROM s EPROM s Drams Rams flash memory devices magnetic or optical cards Nan systems including molecular memory ICs or any type of media or device suitable for storing instructions and or data.

Stored on any one of the computer readable medium media the present invention includes software for controlling both the hardware of the general purpose specialized computer or microprocessor and for enabling the computer or microprocessor to interact with a human user or other mechanism utilizing the results of the present invention. Such software may include but is not limited to device drivers operating systems execution environments containers and user applications.

The foregoing description of preferred embodiments of the present invention has been provided for the purposes of illustration and description. It is not intended to be exhaustive or to limit the invention to the precise forms disclosed. Many modifications and variations will be apparent to one of ordinary skill in the relevant arts. For example steps performed in the embodiments of the invention disclosed can be performed in alternate orders certain steps can be omitted and additional steps can be added. The embodiments were chosen and described in order to best explain the principles of the invention and its practical application thereby enabling others skilled in the art to understand the invention for various embodiments and with various modifications that are suited to the particular use contemplated. It is intended that the scope of the invention be defined by the claims and their equivalents.

