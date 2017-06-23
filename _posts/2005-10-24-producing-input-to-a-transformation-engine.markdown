---

title: Producing input to a transformation engine
abstract: Input to a transformation engine is produced, responsive to a client computer providing a data access service (DAS) computer with XML data for transformation, by creating a graph shell and XML store for the XML data, determining if the graph has a store; and, if so, requesting an empty TrAX result; requesting to fill the empty TrAX result using TrAX source, and requesting a store parser for events related to the XML store; while avoiding wrapping by the TrAX DAS of a graph shell with TrAX source, requesting by a TrAX source of a graph for one or more nodes, requesting by a graph from a store for one or more nodes, parsing of a buffer by a store, returning events from a store to a graph, building of a graph by the same graph, returning nodes from a graph to a TrAX source; and building events by a TrAX source.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08010888&OS=08010888&RS=08010888
owner: International Business Machines Corporation
number: 08010888
owner_city: Armonk
owner_country: US
publication_date: 20051024
---
In order for a client process to be able to access and manipulate data a client may request that a program henceforth called a Data Access Service or DAS convert the data into a hierarchical or other graph structure. WO0221291 discusses conversion of certain HTML files into tree structures such that the information contained within the tree structures may be used by other application programs. WO2004068320 discusses the conversion of HTML source into a tree structure such that that tree structure can be manipulated and transformed into a simplified HTML document.

The conversion of other data formats such as XML into hierarchical format for the purpose of data manipulation is also known. U.S. Pat. No. 6 785 685 for example describes the parsing of XML data in order to build a DOM tree from which a dynamic data object DDO or extended data object XDO can be constructed. US2003041077 is another example of a patent that discuses the conversion of a source document into hierarchical form in order that the data contained within can be referenced. Other graph structures are known such as SDO and Microsoft s ADO Microsoft is a registered trademark of Microsoft Corporation in the United States other countries or both .

A simplified overview of the processing required to construct and access a graph is illustrated by . Client requests DAS make a graph out of data data . In the case of XML data this may be achieved by a Simple API for XML SAX parser parsing the XML data to create events which DAS can then use to build the graph .

As shown in when client wishes to access a node within the graph client makes such a request via an operation to the graph itself. The operation traverses the existing graph according to the supplied path until the requested node is identified and sends this back to client for manipulation. US2004193575 discusses modelling of an XML document as a tree of nodes and navigating the tree of nodes to address parts of the XML document where a destination node is as a result of a path expression. The reader is also referred to the discussion of XPath at http www.w3.org TR xpath.

Nodes are only built when a client specifically requests them. For example shows that client issues a request for node b c . This request is received by graph which points to store containing buffer . Store parses the buffer to produce the events required by the graph in order to build the nodes in the path to the requested node. In the present case this produces graph . Once the requested node has been created by the graph this is then sent back to the client .

Thus a better performance can be achieved by building the graph on demand rather than by expending processing power up front.

Use of a store to build a graph on demand is described in the EMF javadoc found at http eclipse.org emf . The base technology is also described at http xml.apache.org xerces2 j xni config.html

In certain circumstances a client may require the data to be in a different format to that in which it is currently stored. Numerous patents patent applications discuss the concept of data transformation. See for example US2002073119 WO0073941 and US2004025117.

Transformation of data can be achieved by a transformation engine. There are two logical operations a transformation engine might be performing transcription i.e. transcoding in which the same logical information is expressed in a different wire format . In general a client would do this when it intends to forward the message to another agent. An example would be translating from English to French or XML to a legacy or cherished application format. The second which is a logical transformation changes the logical meaning of the graph for instance it might involve changing routing information in a message.

The present invention is particularly concerned with the process for achieving data transformation when the data to be transformed is constructed lazily.

According to a first aspect the invention provides a method for producing input to a transformation engine the method comprising receiving a request to transform some data determining whether the data is stored in a form permitting said data to be lazily constructed into a graph structure upon request by a client and if the data is stored in such a form determining whether to convert the data into a graph structure from which structure input to the transformation engine can be produced and in the affirmative converting the data into a graph structure and producing input to the transformation engine from this graph structure and otherwise producing input to the transformation engine directly from the stored data.

Preferably in order to determine whether to convert the stored data into a graph structure it is determined whether there is a relationship between the type of data stored and the type of input to the transformation engine which is produceable from the graph structure.

If it is determined that the data should be converted into a graph structure this is preferably done by parsing the stored data to create a first generalised form of the data e.g. events and the graph structure is then preferably built from the first generalised form.

In order to produce input to the transformation from this graph structure the graph structure is preferably traversed in order to create a second generalised form of the data e.g. events .

In some circumstances it is possible to produce input to the transformation engine directly from the stored data. In such circumstances the stored data is preferably parsed to create a generalised form e.g. events which can then be input into the transformation engine.

Irrespective of whether the graph construction phase is bypassed the input to the transformation engine will preferably be the same assuming the original data is the same .

According to another aspect the invention provides an apparatus for producing input to a transformation engine the apparatus comprising means for receiving a request to transform some data means for determining whether the data is stored in a form permitting said data to be lazily constructed into a graph structure upon request by a client means responsive to the data being stored in such a form for determining whether to convert the data into a graph structure from which structure input to the transformation engine can be produced means responsive to a positive determination for converting the data into a graph structure and for producing input to the transformation engine from this graph structure and means responsive to a negative determination for producing input to the transformation engine directly from the stored data.

As described above a client uses a Data Access Service DAS to convert data into a form such that it is accessible to the client. This form is a hierarchical or other graph structure. The hierarchical form used in accordance with a preferred embodiment of the present invention is SDO Service Data Objects .

Creating a complete graph of a client s data can be processor intensive and this is wasteful if the client is unlikely to visit every node in that graph. Thus the solution is to use a lazily constructed graph where nodes in the graph are only created when a client requests access to those specific nodes.

Whilst performance is gained in some respects this solution can however cause performance problems when a client either the same one or another client requests transformation of the data into a different format.

One possible but less preferred way of transforming lazily constructed data is explained with reference to .

The function purpose of components data such as client DAS store buffer and SAX Events have all been discussed previously and so will not be discussed in any more detail. In addition to these components data an XSLT Transformation Engine is provided. XSLT is described at http www.w3.org TRlxslt. This takes as input a Transformation API for XML TrAX Source which is created by TrAX DAS from graph . When a TrAX Source is input to Engine the output i.e. the transformed data is placed into TrAX Result . This result can then be returned to client as a tree of data or more loosely a graph of data which represents a tree structure .

Note TRAX is described at http java.sun.com j2se 1.4.2 docs api javax xml transform package summary.html and http xml.apache.org xalan j trax.html

The client or another client has already provided the XML DAS with some XML data upfront step . The XML DAS produces a lazily constructed graph from this data at step . In other words the DAS constructs a graph shell containing some functionality allowing the graph to build itself and in terms of nodes only the root of the graph. The root is then set to point towards store . Buffer is then filled with the XML data.

At some point the client indicates that it requires the data to be transformed into another format. The client does this by asking the TrAX DAS for TrAX Source which can then be input into the XSLT Transformation Engine step . The TrAX DAS wraps the graph shell with an instance of a TrAX Source class step . The client then asks the TrAX DAS for an empty TrAX Result step . The client subsequently requests that the XSLT Transformation Engine fill in the empty TrAX Result using the TrAX Source step . In other words the client requests that output from the Transformation Engine is entered into the empty TrAX Result.

At step the transformation engine asks the TrAX source for a sequence of events to perform the transformation on. It should be observed that this is a generic step which would be applied whatever the nature of the graph whether it be a truly disconnected graph or a graph which is underpinned by a store supplied by some other form of DAS or as in this case an XML based store. At step the TrAX Source asks the graph for its nodes. Because the data is constructed lazily the graph references the store to request these nodes step . The store then parses the buffer to generate events pertaining to the requested nodes step and returns the events to the graph step . The graph uses the events to build itself step . Having constructed itself the graph can then return the nodes to the TrAX Source step and the TrAX source builds events from the nodes returned to it step . These events can then be input as TrAX Source to the XSLT Transformation Engine step . The output of the Transformation Engine i.e. the transformed data is used to complete a TrAX Result for return to the client step .

Thus it can be seen that the transformation of data based upon a lazily constructed hierarchy and using the processing described above makes for a processor intensive task.

The inventors of the present solution have realised that in certain circumstances it is possible to short circuit the unwieldy process described with reference to .

The components and processing involved in a preferred embodiment of the present invention will now be discussed with reference to and

The first three steps are the same as those described with reference to . A client provides an XML DAS with some XML data step . The XML DAS creates a graph shell comprising some functionality enabling it to traverse and build itself and a root node and also an XML store step . The Client then asks TrAX DAS for TrAX Source step . This is where the processing of the present invention in accordance with a preferred embodiment differs from that described with reference to .

At step the TrAX DAS asks graph whether it points to a store graph querier . If the answer is yes then the TrAX DAS determines from the graph whether this is an XML store step graph querier and whether the store has an up to date buffer step graph querier . Note history information is preferably stored by the graph regarding changes made to it by the client note changes may be made by different clients but one is referred to here for ease . If there have been no changes then the buffer will be up to date.

The above functionality is provided by the following components owned by graph . A store determiner determines whether graph has a store. Store determiner contains a store type determiner which is used to determine whether any store contains an XML buffer. A store validity determiner is used to determine whether any buffer is up to date.

If the answer to any of the questions posed by steps is no then the short cut of the preferred embodiment is not possible. Instead the processing discussed with reference to must be used starting at step .

On the other hand if the answers to steps were all yes then at step the client asks the TrAX DAS for an empty TrAX Result. The client then asks the XSLT Transformation Engine to fill the TrAX Result using TrAX Source step . TrAX Source asks store querier the store parser not shown to parse the buffer in order to create events step and these are the events that are then input directly to the XSLT Transformation Engine step . As before output from the Transformation Engine is used to fill the TrAX Result step .

In this way it is possible in certain circumstances to circumvent much of the processing described with reference to .

In the particular embodiment described there is a special relationship between the TrAX DAS and the XML DAS that means that the events generated by parsing the buffer are suitable for direct input into the transformation engine and there is no need to create events from a hierarchical form of the data for input to the transformation engine.

It should be appreciated that whilst preferred embodiment has been described in terms of XML the invention is not limited to such. The invention can apply to any environment in which data is normally lazily constructed into a graph structure on request by a client where the events produced by a store parser when parsing stored data are suitable for direct input to a particular transformation engine. In such situations these events can be provided to the transformation engine instead of creating a graph structure first and then using this form to generate appropriate events for input to the transformation engine.

