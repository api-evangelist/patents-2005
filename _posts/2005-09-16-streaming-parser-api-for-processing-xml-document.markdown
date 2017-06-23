---

title: Streaming parser API for processing XML document
abstract: A streaming parser API expands a base parser by building an iterative method on top of the base parser. The iterative method allows a user to pass a selected element type to the base parser, which can step through the XML document until it locates a matching element. The base parser can then extract the element, process the element as an event, and place the event on an event stream for use by an application.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08074160&OS=08074160&RS=08074160
owner: Oracle International Corporation
number: 08074160
owner_city: Redwood Shores
owner_country: US
publication_date: 20050916
---
This application claims priority to U.S. Provisional Patent Application No. 60 362 773 filed Mar. 8 2002 entitled STREAMING PARSER API which is hereby incorporated herein by reference.

U.S. patent application Ser. No. 10 304 353 entitled System and Method for XML Data Binding by Chris Fry and Scott Ziegler filed Nov. 26 2002.

U.S. patent application Ser. No. 10 304 233 entitled System and Method for Fast XSL Transformation by Chris Fry filed Nov. 26 2002.

U.S. patent application Ser. No. 10 304 280 entitled System and Method for XML Parsing by Chris Fry filed Nov. 26 2002.

A portion of the disclosure of this patent document contains material which is subject to copyright protection. The copyright owner has no objection to the facsimile reproduction by anyone of the patent document of the patent disclosure as it appears in the Patent and Trademark Office patent file or records but otherwise reserves all copyright rights whatsoever.

The eXtensible Markup Language otherwise known as XML has become a standard for inter application communication. XML messages passing between applications contain tags with self describing text. The self describing text allows these messages to be understandable not only to the applications but also to humans reading an XML document. XML is currently used to define standards for exchanging information in various industries. These document standards are available in various forms.

Several XML based communication protocols exist such as the Simple Object Access Protocol SOAP and the ebXML protocol. The ebXML protocol is an open XML based infrastructure that enables the global use of electronic business information. SOAP is a lightweight XML protocol which can provide both synchronous and asynchronous mechanisms for sending requests between applications. The transport of these XML documents is usually over a lower level network standard such as TCP IP.

XML documents need to be valid and well formed. An XML document is considered to be well formed if it conforms to the particular XML standard. An XML document is considered valid if it complies with a particular schema. At the core of an XML document is an XML parser which will check to verify that a document is well formed and or valid.

The processing of XML has become a standard function in many computing environments. When parsing XML it is necessary to get data from the XML file and transform the data such that the data can be handled by a Java application or other application running the parser. Efficient XML processing is fundamental to the server. As more and more documents become XML based more and more traffic on the server will be in XML. The latest push into web services with SOAP as the transport has also highlighted the fundamental need for fast XML processing. Web services use XML over HTTP as the transport for remote procedure calls. These calls cannot be done in a timely manner if the XML parser is slow. There are primarily two standard approaches for processing XML 1 SAX or Simple API for XML and 2 DOM or Document Object Model. Each protocol has its benefits and drawbacks although SAX presently has more momentum as an XML processing API.

SAX is an event based API for parsing XML documents presenting a document as a serialized event stream. An API or application programming interface provides a defined method for developing and utilizing applications. With SAX a Java application can work with any XML parser as long as the parser has a SAX driver available. In SAX an event is generated every time a piece of the XML document is processed. That event is sent to a document handler which is an object that implements the various SAX handler APIs. Handlers can receive callbacks during the processing of an XML document. Some of the main benefits of this style of XML document processing are that it is efficient flexible and relatively low level. It is also possible to change handlers during the processing of an XML document allowing the use of different handlers for different sections of a document.

One drawback to using a SAX API is that a programmer must keep track of the current state of the document in the code each time an XML document is processed. This may be an unacceptable amount of overhead for XML processing and may further lead to convoluted document processing code.

Another problem with SAX is that it is necessary to have an event sent to a user. Events cannot be requested as they are needed but are instead pushed to the user only as the events occur.

DOM the other standard approach requires loading an entire XML document into memory and provides a programmer with APIs to be used in manipulating an in memory tree structure. DOM is a tree based API as opposed to the event based SAX. DOM is referred to as tree based because it utilizes a logical structure based on nodes for branching through a document. At first glance DOM might seem like a preferred approach to parsing for an application developer as the developer does not have to write specific parsing code. This perceived simplicity comes at a price however in that performance takes a significant hit. Even for very large documents the entire document must still be read into memory before taking appropriate actions based on the data. DOM can also be restrictive in how it loads data into memory. A programmer must use a DOM tree as the base for handling XML in the document. This can be too restrictive for most application needs. For example most application server development descriptors need to be bound to specific Java classes and not DOM trees.

The present invention overcomes deficiencies with existing XML parsers by presenting systems and methods for efficiently handling XML documents.

Systems and methods in accordance with the present invention expand upon base parsers to provide for the parsing of XML streams generated from an XML document. An iterative method can be built upon a base parser such as a SAX or DOM parser which allows the name of a selected element to be passed to the method. The base parser can begin processing the XML document to locate an element tag signifying an element of the XML document. The iterative method can then direct the base parser to step through the elements in the document until the tag is located that corresponds to the selected element. The base parser can extract the selected element from the XML document and process the element such as by generating an event that can be read by a Java application. The event can then be placed on an event stream for use by an application.

Systems and methods in accordance with the present invention utilize a streaming API to provide an efficient way of handling XML documents that is uniquely suited to the runtime needs of an application server. A streaming API can be implemented on top of an existing XML parser. This approach can also be referred to as pull parsing or event based processing. 

A streaming API or streaming parser is a mechanism by which a user can request events for an XML document. It is possible to request a bunch of events that will be sent to a particular place and will generate a result object. This is done at a higher level than SAX and is much more convenient for dealing with XML data.

Such a streaming parser for XML can be implemented for example on top of SAX. The streaming parser takes SAX events and constructs an easily manipulated event stream that is available to the application programmer. The streaming parser gives parsing control to the programmer by exposing a simple iteration based API to the programmer.

The parser would then reach element type two in the XML document corresponding to another StartElementEvent element in the event stream. This would generate a substream in the Java environment to handle the second element type. Values of element type two are placed onto the event stream and correspond to the Java substream. Element type two ends when another end tag is reached in the document corresponding to an EndElementEvent in the event stream with another EndElementEvent corresponding to the end of document tag .

A method for utilizing such an event stream is shown in . The name of an element to be extracted from the XML document is passed to an iterative method built on top of a base parser such as a SAX API or DOM parser . An element tag of the XML document is located and the element type read by the base parser without necessarily reading the sub elements or text of that element . The elements of the XML document are then stepped through by the base parser in combination with the iterative method until the element to be extracted is located read and processed by the base parser . An event is generated that is related to the element and placed on an event stream for use by an application such as a Java application .

A public access point to an XML processor can take the form of an interface such as an XMLEventStream interface. A concrete implementation of such an interface or API can be in a class such as an XMLEventStream class. With an event stream a programmer controls the parser rather than having to write a handler for the parser. For example the following example program would get all the start elements of a document 

The streaming parser can extend the base parser and expose a single method to the XMLEventStream class. This single method such as for example streamParseSome can put all the XML events generated by this call onto the stream.

The base parser can be relied upon to handle the guts of the XML processing forming the base class for all XML processors in the parsing paradigm including for example the StreamParser and SAXDriver. The base parser iterates over XML Elements which can then be encapsulated in the Element class. Currently StreamEvents are created by a factory that accepts Elements and generates events. The same model can be used to create SAXEvents from XML events. The base parser can enforce higher level well formedness constraints such as proper element nesting and proper namespace declaration and scoping.

A scanner can be used to deal with the low level reading of XML and to generate tokens for the base parser which consumes the tokens. To a parser a token is a string of characters that functions as a unit which is typically as small as possible. The 

SAX support can also be handled in a SAXDriver class for example which can generate SAX events and implement an XMLReader class from SAX.

One streaming parser that can be used in accordance with the present invention is based on a standard API called JAXP or Java API for XML Processing. JAXP makes it easier to deal with parsing tasks and makes it possible to handle some vendor specific tasks. JAXP does not provide parsing functionality but provides a way to get to XML parsers. The JAXP classes typically sit on top of an existing parser.

The JAXP API can be hooked up to a management system which can include a console that is accessible to users. The JAXP API can be plugged directly into a configuration system and can be used to select an XML parser in order to process XML. The selected XML parser reads the XML and converts it into an object that a Java application can read.

JAXP can utilize a SAX protocol comprising a series of callbacks. A start callback for example can be invoked every time an opening tag is encountered in an XML document by a SAX parser. SAX provides a class called HandlerBase that implements the callbacks and provides default implementations of the callback methods. A SAX developer needs to extend the HandlerBase class and implement methods that require the insertion of specific logic. The key is to provide code for these various callbacks then allow a parser to trigger the callbacks as necessary. The SAX component of JAXP provides a relatively simple way to accomplish this task.

JAXP allows a programmer to provide a parser as a Java system property. In this way changing the parser being used requires only a change in classpath setting to move from one parser implementation to another. Changing the parser does not require any code recompilation.

The process of dealing with DOM in JAXP is similar to the process of dealing with SAX. As described above DOM utilizes an in memory tree structure including nodes to represent elements attributes and other XML constructs. With DOM JAXP does not have to fire callbacks as it does for SAX instead being responsible only for returning a DOM document object as a result of parsing. DOM methods are similar to SAX methods except that variations of a parse method do not take an instance of the SAX HandlerBase class but instead return a DOM Document instance representing the XML document that was parsed.

There are many different XML parsers which can be based on SAX or DOM and users may want to be able to plug one of these parsers into an application without changing their code. Since the parsers operate using certain minimum standards JAXP can allow for the addition of one of these parsers by configuring the appropriate mechanisms.

The foregoing description of preferred embodiments of the present invention has been provided for the purposes of illustration and description. It is not intended to be exhaustive or to limit the invention to the precise forms disclosed. Many modifications and variations will be apparent to one of ordinary skill in the art. The embodiments were chosen and described in order to best explain the principles of the invention and its practical application thereby enabling others skilled in the art to understand the invention for various embodiments and with various modifications that are suited to the particular use contemplated. It is intended that the scope of the invention be defined by the following claims and their equivalence.

