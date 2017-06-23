---

title: Method and system for efficiently handling navigational state in a portal
abstract: The present invention provides a method and system for efficiently handling navigational state by separating the latest navigational state into a base navigational state part and a delta navigational state part. The base navigational state which describes that part of the latest navigational state that is identical across all URLs is encoded in the header of the page markup to be submitted to the client's browser. The delta navigational part that describes the semantics of that specific URL is encoded in its associated URL. Each user interaction using such URL causes the browser to submit the base part as well as the delta part. On the server side the base and delta part are being merged resulting in new navigation state serving as a base for the rendering of the new page. The navigational state is represented as a hierarchical tree-like structure that can be serialized efficiently and compressed by prior art compression techniques. The hierarchical tree-like structure is based on a well-defined state model that is optimized in terms of state serialization. The state model arranges the contained navigational state information in character based information. That saves processing time as it avoids type conversion of navigational information. In addition the present invention includes further strategies to reduce the amount of information that must be serialized.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07801970&OS=07801970&RS=07801970
owner: International Business Machines Corporation
number: 07801970
owner_city: Armonk
owner_country: US
publication_date: 20051209
---
This application claims benefit under 35 U.S.C. 119 e to Provisional U.S. application entitled A Method for Efficiently Representing Navigational State in a Web Application Ser. No. 60 748 699 filed Dec. 8 2005.

The present invention relates to a method system and computer program product for efficiently handling navigational state in a Portal application and in particular to reduce the markup size of Portal pages reduce URL length and reduce processing time needed to generate the URLs being part of the Portal page.

Navigational state as used by the present invention describes the current view of the Portal that is the result of all navigational interactions of a particular client . The client can request query different views by interacting with the Portal page e.g. by navigating to a new page. This type of interaction does not change server side state but only requests a new view of the server it is therefore a safe operation in terms of HTTP. The nature of this interaction is such that the client can navigate back and forward through its recent views using the back and forward button of his browser and that clients can bookmark views and get back to them at a later point in time by invoking a browser bookmark.

One of the main features of HTTP is that it is a stateless protocol i.e. the notion of a session spanning multiple request response interactions does not exist in HTTP. But as nearly all application scenarios require some mechanism to save their state across requests some mechanisms have emerged that allow for creating logical stateful sessions and that can be certainly considered as state of the art nowadays. The two most popular prior art state saving mechanisms are the following 

To initiate a logical session between the client typically a browser and the server the server returns an extra set cookie response header to the client containing basically name value pairs. The client stores the cookie persistently in a file and associates it with the server s URL. With each request the client provides this cookie back to the server using the cookie request header. By analyzing the cookie the server not the HTTP server but the application or a server side script such as a servlet or CGI can identify the user specific session containing the needed state information. Note that cookies also allow for maintaining state across session boundaries as the persistent cookie file on the client typically lives longer than the corresponding session on the server.

This second variant exchanges the complete state information between server and client. The server stores the state in the markup of the requested page using a hidden input file of a HTML form. In addition the application makes sure that each URL in the markup of a page initiates a form submit causing the state being part of the hidden input field to flow along with the request to the HTTP server.

In today s Web applications even navigational state is mostly saved across requests using one of the outlined mechanisms. However both approaches have some major drawbacks with regard to bookmarkability caching back forward button and indexing by search engines crawlability .

Storing the navigational state in a logical server side HTTP session e.g. identified via a cookie has the following disadvantages 

Browser bookmarks do not work as the navigational state kept in the server side session has only a limited lifetime. Typically the session times out after a period of inactivity. After a session timeout the navigational state cannot be restored on the server i.e. the server will deliver a default view on the application.

Navigating back and forward through the recent views using the back and forward button of the browser does not work. Note that the state does not get lost in that case as long as the session is maintained but the operations of the back and forward button do not take any effect on that state.

The benefits of caching browser side server side and proxy caching are considerably reduced as such caches typically use the URL as their cache key. The cache entries are overwritten with almost each interaction leading to a cache hit rate of almost zero.

Web search engines cannot index the site well. Search engines work by storing information about a large number of Web pages which they retrieve from the Web itself. These pages are retrieved by a Web browser called Web crawler that follows every URL URL it sees on the page in the markup respectively .

Storing the navigational state in a hidden input field of a HTML form has less disadvantages but it also does not solve all problems summarized. Bookmarkability works as long as the respective page is cached. The back and forward button works. The caching and crawlability problem remains. Note that state management relying on hidden input fields cannot be applied in the Portal area as the mechanism requires a page level form. However a page level form cannot be used the markup of JSR 168 compliant portlets may also make use of HTML forms thus causing nested forms forbidden by the HTML standard .

It is object of the present invention to provide a method system and computer program product for efficiently encoding navigational state of a Portal avoiding the disadvantages of the existing prior art.

The present invention provides a method system and computer program product for efficiently handling navigational state by separating the navigational state into a base navigational state part and a delta navigational state part. The base navigational state which describes that part of the latest navigational state that is identical across all URLs is encoded in the header of the page markup to be submitted to the client s browser. The delta navigational part that describes the semantics of that specific URL is encoded in its associated URL. Each user interaction using such URL causes the browser to submit the base part as well as the delta part. On the server side the base and delta part are being merged resulting in new latest navigation state serving as a basis for the rendering of the new page. The new latest navigational state is represented as a hierarchical tree like structure that can be serialized efficiently and compressed by prior art compression techniques. The hierarchical tree like structure is based on a well defined state model that is optimized in terms of state serialization. The state model arranges the contained navigational state information in character based information. That saves processing time as it avoids type conversion of navigational state information. In addition the present invention includes further strategies to reduce the amount of information that must be serialized.

Today s Web applications become more and more complex in particular in the Portal environment where several components Portlets are combined into a larger Portal application. This leads to the problem that the navigational state describing a certain view of the Web application becomes quite voluminous. In the Portal scenario for example it must aggregate the navigational state of all portlets the user interacted with.

The invention provides a method for efficiently handling navigational state with following advantages compared to the prior art solutions 

Encoding the navigational state into each URL takes the risk of considerably increasing the size of the markup that has to be transferred to the client. That will be avoided by the present invention.

Disregarding markup size it is also important to keep the single URLs as short as possible. HTTP limits the maximum length of an URL to 2 KB. If this limit is exceeded proxy servers receiving such a long URL typically shorten the URL to 2 KB. The present invention makes sure that that limit is not exceeded.

The prior art navigation state handling involves pages offering a lot of URLs hundreds of URLs per page are not exceptional . Therefore the processing time needed to generate an URL has a big impact on the overall server side rendering time and thus on the overall performance of the Portal. The present invention keeps the processing time as low as possible in particular the time that is needed to serialize the complex navigational state into an URL because that is crucial to meet the performance requirements in terms of server side processing time.

The present invention describes how above mentioned advantages with respect to markup size URL length and URL generation processing time are achieved by using a delta encoding method as claimed in claim .

The basic idea of the present invention delta encoding is to separate the navigational state a URL must encode into two parts 

The so called base navigational state latest base navigational state describes the complete navigational state a user currently sees on his or her client device and

the so called delta navigational state expresses the specific semantics of an URL. In other words the state delta defines the state transition that should be done in case that the URL is invoked e.g. by clicking on it .

Note that the base navigational state is typically much more complex than the delta navigational state because the base navigational state reflects the complete navigational state that has been piled up little by little by previous interactions. The delta navigational state in turn just consists of a small piece of information that represents the semantics of the respective URL.

The distinction between the base navigational state and the URL specific delta navigational state might be explicitly reflected in the URL itself. For instance the URL generation implementation might choose to serialize the base state as well as the delta state into the path info of the URL like this the base token indicates the serialized base state and the delta token in turn the serialized delta state http www.myportal.com 80 portal public base ajasdkjh6zuz7hjhsg iuzrakjssdfkjhsakjizutejhsdkhjjhgsdf delta hsdjhuh

When receiving a request using such an URL the target servlet merges the base navigational state with the delta navigational state to obtain the complete navigational state or view that was requested latest new navigational state . The resulting state called new latest navigational state serves as the new request specific base state for all URLs generated within that request. To avoid serializing the base navigational state for each URL created during rendering the base navigational state can be pre serialized right after the action phase because after action processing is completed the base navigational state cannot be altered any more.

The writing of an URL to the markup during rendering depends on whether the URL needs to be absolute server relative or relative.

Server relative URLs start with the servlet context path. Protocol hostname and port information is implied by the browser.

In the case of a relative URL the browser appends the URL to either the current request URL or to the value of the HTML base tag if any .

Absolute and server relative URLs need to encode the base state and the delta state. To create such URLs the pre serialized base state can be included into the URL as is whereas the URL specific delta state has to be serialized before appending it to the URL.

However in the frequent case of relative URLs it is sufficient to include the serialized delta state into the URL whereas the pre serialized base state can be kept in the HTML base tag which accordingly has to be written only once per page as it refers to all relative URLs being part of the page . The markup fragment depicted below illustrates the usage of relative URLs. When clicking on one of the two toolbar URLs the browser will append the relative URL delta . . . to the value of the base tag.

As highlighted in the screenshot depicted in the navigational state that corresponds with the depicted view comprises the state of several page elements including Portlets. Typically each URL contained in the displayed markup encodes the navigational state of all those elements. Additionally each URL encodes the state delta which determines what the Portal should do in case that a user clicks on such an URL.

In other words all URLs of a page define a state transition matrix. The target state of a transition is equivalent with the state that can be obtained by merging the delta state with the base state. Thus the state transition matrix is extended dynamically depending on the URL the user clicked on.

The table above shows a simple state transition matrix. The second column Generated URLs lists the base state delta state pairs for all URLs generated during the render phase of the respective request processing first column . The third column lists the potential result state that would form the new base state when processing the respective URL. The first request represents the initial request going to the Portal. It is typically triggered by the user entering the Portal URL into the browser address bar. The response on this initial request delivers a default view on the Portal. Therefore the rendered URLs do not contain a base navigational state because the default navigational state can be implied by the Portal . Assuming that the user clicks on the third URL next third row in the table the new base navigational state Bwould correspond with the delta state D as no merge is required . Assuming that the clicked URL does not switch to a different Portal page the Portal potentially renders again the four URLs. However this time the URLs contain the base navigational state Bbecause disregarding which URL is activated next the navigational state should be maintained. Subsequently the user might click on the forth URL of that page eighth row in the table resulting in the new base state Band so on.

The present invention is preferably implemented in a Portal structure which is described in connection with .

The Portal structure preferably comprises function components which are already part of each prior art Portal and those components which are newly added in order to provide the inventive functionality.

The Servlet is the front controller that receives the incoming HTTP requests. It typically prepares the request processing engine for processing the received HTTP request by initializing the components involved. After that the servlet delegates the processing of the request to the request processing engine .

The request processing engine is also part of the front controller being responsible for controlling the processing of the incoming requests. Typically it defines a request processing lifecycle that is made up of several request processing phases. In a Portal a request has to walk through four phases. First the init phase performs request specific initialization tasks followed by the action phase being responsible for authentication and action execution Portlet actions as well as commands . After the action phase the render phase is executed by invoking the aggregation process. The terminal phase concludes request processing by performing request specific cleanup tasks.

The aggregation component is invoked during the render phase of the request processing lifecycle. It is responsible for transforming the layout model of the requested page into a presentation tree as well as writing the markup that corresponds to this presentation tree to the response.

The authentication component is responsible for verifying the identity of the user. Each incoming request has to pass authentication. The Portal uses the user identity to determine the content the user is authorized to access as well as the commands to execute.

The Portlet container provides unified access to the Portlets. In particular it allows for gathering the markup of a certain Portlet or executing a Portlet action. The Portlet container invokes Portlets by means of the Portlet API.

The command API application programming interface provides an abstraction layer for Portal specific commands. In particular it allows for executing commands via a unified interface. Commands may be used to perform administrative tasks such as creating and or deleting Portal pages adding and or removing Portlets to and or from Portal pages arranging Portlets on existing pages and so on.

The navigational state management component component is the key component realizing the present invention in the Portal . The responsibilities of this new component are the following defining a lifecycle for navigational state as well as providing an interface that enables the request processing engine to incorporate the defined state processing tasks into the overall request processing lifecycle 

defining an object model to represent navigational state as well as providing an application programming interface API that allows for reading and writing modifying navigational state providing a framework that allows for efficiently serializing the object representation of navigational state into an URL as well as de serializing navigational state from an incoming URL to restore the internal object representation. The framework needs to include interfaces that can be invoked by the URL generation component to create URLs carrying navigational state URL Generation API

The URL generation API provides as the name implies an API that allows for creating URLs for a variety of use cases. It enables the programmer to associate navigational state with the created URL as well as to write the URL to a given destination stream. This write operation involves serializing the navigational state that has been associated with the created URL. In addition to creating URLs programmatically the URL generation API typically offers some URL tags to create URLs within JSPs.

Note that by default a created URL is initialized with the request specific navigational state to make sure that the navigational state of previous interactions does not get lost. To determine the specific semantics of the URL this navigational state may be changed for this particular URL only.

The delta encoding method can be put into practice by defining a lifecycle for navigational state. The lifetime of the navigational state that is associated with a particular client is one HTTP request. B shows a component interaction diagram that illustrates how the different steps are aligned with the superior request processing lifecycle 

During the init phase the navigational state has to be decoded from the incoming request URL. State decoding is delegated to the navigational state management component and involves de serializing the base navigational state B as well as the delta navigational state D and after de serialization merging the delta navigational state D with the base navigational state B to obtain the new base navigational state B for this request. After initialization is completed the object representing the new latest base navigational state B is passed to the action phase for further processing.

During the action phase the business logic is executed. Portlet actions are invoked via the portlet container and commands via the command API note that these steps are not depicted in the diagram for simplicity reasons . The base state B is potentially modified during action processing let B be the result of these modifications.

As the base state B must not be altered any more after action processing it is serialized before starting the rendering. Let B be the serialized base state B .

At the very beginning of the render phase more precisely when writing the HTML header of the page that should be displayed the pre serialized base navigational state B is included as part of an absolute URL into the HTML tag.

The actual rendering performed subsequently involves the generation of multiple URLs. In this step has been dumbed down to the components generating the URLs. Actually these components are invoked indirectly via the Portlet container or aggregation component depending on whether the URLs are part of Portlet markup or not. For each URL created via the URL generation API the implementation performs the following steps Before changing the navigational state to specify the semantics of the specific URL a so called delta proxy is created. The delta proxy B is a wrapper enclosing the navigational state object B that records the state modifications applied to B .

Subsequently the URL generation component creates the target navigational state of the respective URL by applying the needed changes according to the usage of the URL generation API to the obtained delta proxy B .

Finally the created URL is written to the markup. This involves serializing the delta state Drecorded by the delta proxy B and in case that the URL cannot be relative pre prending the pre serialized base state B .

The crucial steps of the delta encoding are the following the merging step performed during state decoding init phase makes sure that the delta navigational states created during rendering are minimal deltas. This implies that the serialized delta navigational states remain minimal in terms of length the merging step during state decoding and the base state pre serialization step at the end of the action phase ensure that the URLs can be generated very fast during rendering. In case of non relative URLs the already serialized base state can be included into the URL as is. The creation of relative URLs during the render phase keeps the URLs short thus reducing the markup size of the rendered page considerably because the URLs need only contain the minimum delta state whereas the serialized base state being much longer is part of the URL contained in the base tag.

Therefore it is recommended to model navigational state using a hierarchic document model containing un typed state information represented as characters or Strings in terms of Java . The character based memory representation allows to efficiently serializing navigational state into URLs because it avoids time and CPU consuming object to string conversions during the serialization process.

One of the common object oriented design patterns is to separate read only interfaces from read write interfaces controllers . Accordingly the used object model should offer two interfaces to the state document.

The DocumentModel interface provides read access to the state document offering the following methods UML notation getRooto Node Returns the root node of the state document getchildren parent Node List Returns a list of nodes representing the child nodes of the given parent getParent node node Node Returns a node representing the parent of the given node. If the given node corresponds with the document root the method will return null. Other methods such as hasChildren hasAttributes and getAttributes.

The DocumentController interface provides read write access i.e. it additionally allows for modifying the hierarchic state document.

The DocumentController interface offers the following methods insert new Node next Node parent Node Node Inserts the given node newNode into the state document at the specified position 

create namespace String name String Node Creates a new node with the given name and namespace and returns the created Node object. Subsequently the created node can be inserted into the state hierarchy using the insert method.

The used interface Node models a single node in the document model hierarchy. This node is not aware of its position in the hierarchy or of its attributes but only of its content.

When serializing the base navigational state the complete state document has to be serialized to be included into URLs or into the HTML base tag during rendering. The needed serialization mechanism has to serialize the minimal information the so called entropy that is needed to restore de serialize the complete state document when receiving an URL. This includes the document structure i.e. parent child relationships and the document content data i.e. node names values and attributes.

To keep the URLs short this information has to be encoded as compact as possible. A compact encoding of the document structure can be achieved by using a simple bit encoding that writes the level of each element the depth relative to the root using a given traversal algorithm e.g. depth first traversal .

However the document content data cannot be serialized as easy. Just traversing the state document and writing the complete information making up a node would result in an extremely long serialized form.

The preferred embodiment is to map the node names attribute names and pre defined values to short character representations. To put this into practice the structure of a state document has to be precisely specified either in a document type definition DTD or in a XML schema XSD . From this specification a mapping table can be derived that can be used for state serialization and state de serialization. The depicted document type definition in D shows an exemplary structure of a state document. The depicted tree in visualizes this structure.

The preferred embodiment to create the needed mapping table is to parse the DTD and map each element name attribute and value found to a short character representation. However one can also exploit the hierarchic structure of the DTD and build a corresponding hierarchic mapping tree. Taking a character set such as UTF 8 as a basis for the short character representations one can define a really complex state structure without needing to make use of character representations that are longer than one character because the mappings need to be only unique within the set of children of a particular element .

An example of a mapping tree that corresponds with the state structure of above is shown in E the hierarchy is modelled via indentations .

Assume a Portlet on a page that wants to offer an URL that sets the Portlet into the Portlet mode Configure to enable the user to switch to the view that allows for configuring the Portlet. To create this URL the Portlet uses the URL generation API to request a Portlet mode change URL. Internally the URL generation API implementation performs the mode change using the DocumentController interface. Actually the Portlet uses the Portlet API to generate the URL. However under the covers the Portal delegates this request to the central URL generation API of the Portal.

Let the identifier of the portlet be 5 . Assuming that the underlying base state is the one that corresponds with the document illustrated in the result navigational state base delta would look like the state document as shown in . The portlet mode change results in the nodes and edges that are highlighted red being added.

According to the delta encoding approach the generated URL should only reflect this change and the change should certainly not modify the base state that has already been pre serialized at this time of request processing .

The preferred embodiment is to get the URL generation implementation to believe that it really modifies the state document it operates on. However under the covers the respective modification operations are intercepted and handled specially. This can be easily put into practice by using a proxy pattern i.e. by creating a proxy document that encloses the real state document.

The proxy approach is depicted in . The delta proxy is created for each URL that should be created. The delta proxy also exposes the DocumentModel DM and DocumentController DC interface. However the proxy implementation merely delegates the DocumentModel read invocations to the underlying state document representing the base state. The modification operations done via the DocumentController interface are intercepted and recorded in an internal modification history.

When encoding the delta state into the URL it is sufficient to serialize the recorded series of modification operations. To achieve a compact serialized form the following strategies can be used 

The operation encoded at the beginning implies the number of nodes that belong to these operations. For example if the operation sequence starts with 0 corresponds to insert the first three arguments must belong to it because the insert method of the DocumentController requires three arguments. The same strategy can be applied to the tokens in case of a encoded create method the delta decoding can imply that there are two tokens specifying the node that should be created qualified name and namespace .

Assuming the mapping tables listed above and applying them to the above modification history the delta state is encoded as follows 

The figures include block diagram illustrations of methods apparatus s and computer program products according to an embodiment of the invention. It will be understood that each block of the figures and combinations of these blocks can be implemented by computer program instructions. These computer program instructions may be loaded onto a computer or other programmable data processing apparatus to produce a machine such that the instructions which execute on the computer or other programmable data processing apparatus create means for implementing the functions specified in the block or blocks. These computer program instructions may also be stored in a computer readable memory that can direct a computer or other programmable data processing apparatus to function in a particular manner such that the instructions stored in the computer readable memory produce an article of manufacture including instruction means which implement the function specified in the block or blocks. The computer program instructions may also be loaded onto a computer or other programmable data processing apparatus to cause a series of operational steps to be performed on the computer or other programmable apparatus to produce a computer implemented process such that the instructions which execute on the computer or other programmable apparatus provide steps for implementing the functions specified in the block or blocks.

Those skilled in the art should readily appreciate that programs defining the functions of the present invention can be delivered to a computer in many forms including but not limited to a information permanently stored on non writable storage media e.g. read only memory devices within a computer such as ROM or CD ROM disks readable by a computer I O attachment b information alterably stored on writable storage media e.g. floppy disks and hard drives or c information conveyed to a computer through communication media for example using wireless baseband signaling or broadband signaling techniques including carrier wave signaling techniques such as over computer or telephone networks via a modem.

While the invention is described through the above exemplary embodiments it will be understood by those of ordinary skill in the art that modification to and variation of the illustrated embodiments may be made without departing from the inventive concepts herein disclosed. Moreover while the preferred embodiments are described in connection with various illustrative program command structures one skilled in the art will recognize that they may be embodied using a variety of specific command structures.

