---

title: Data processing in a mediation or service provisioning system
abstract: Embodiments of the invention include a data processing system and method for processing data in a mediation or service provisioning system of a communications network. In the invention, a special logic definition structure is formed based on the processing logic. The logic definition structure is designed so that it is easy to modify and efficient to execute. This is made possible by defining the processing logic in the form of a series of byte code instructions, wherein each instruction contains a pointer to a piece of program code performing a function and a pointer to parameters to be used in performing the function. The instructions, the program codes performing the functions, the pointers and the data under processing are preferably stored in arrays thus allowing the use of efficient pointer mechanisms together with flexibility and ease of modification.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08042106&OS=08042106&RS=08042106
owner: Comptel Corporation
number: 08042106
owner_city: Helsinki
owner_country: FI
publication_date: 20050616
---
In particular the present invention relates to processing structured data records containing data fields and data in the data fields. One example of such a data record is an event record containing data on usage of a communications network.

Hence an embodiment of the present invention relates to mediation methods and systems. Mediation is a process wherein usage data is collected from a communication network and delivered to operator s Operation and Business Support System s OSS BSS . Mediation software collects usage data from the network by interfacing various different network elements. The mediation layer then aggregates correlates enriches validates formats and or rates the data so that it is readable by the target OSS BSS system s and it contains all the required information.

In modern telecommunications networks there is a demand for handling events as soon as the data is available in the network. Continuous streaming mediation which is also called real time mediation has been developed to fulfill these requirements. Especially in continuous streaming mediation quality reliability and effectiveness of data processing are very important.

In modern telecommunications networks there is also a need for easy adaptation of the system to provide new services and process the event records according to varied processing requirements. The above mentioned objectives are often in contrast to each other easy adaptation of the system tends to reduce the throughput whereas a system having an optimized throughput usually required intensive work to reconfigure.

Another embodiment of the present invention relates to provisioning systems and methods. Service provisioning and service activation is a process wherein any types of services in all types of networks are provisioned and activated to network elements. These can be for instance activating all consumer and corporate services such as voice ADSL WLAN access and VPN with the same provisioning system to help the operator to remove lots of costly unnecessary and overlapping processes.

U.S. Pat. No. 6 449 618 discloses one real time event processing system. The system presented in the publication has poor flexibility.

U.S. Pat. No. 6 366 657 discloses a system of supporting and managing telecommunications services. The principle idea of U.S. Pat. No. 6 366 657 is that the system comprises a Service Creation Environment SCE . The SCE simplifies creation provision and management of new services for subscribers. This is done by toolkits for specifying object definitions in an object oriented framework. The system presented in the publication is directed to telecommunication operators to simplify provision of services.

There are two alternative ways to develop the known systems further in attempt to combine effectiveness and easy modification and management.

The first alternative would be to generate some scripting language from the predefined processing logic. One suitable scripting language is Perl. An advantage of this approach is that the resulting code can be viewed and is human readable. Hence the code is easy to debug. However there are several disadvantages in the scripting language approach. For example the performance is relatively poor as the scripting languages even Perl are slower than native code. It is also difficult to generate valid code and to ensure that the variable names etc. do not cause any conflicts in the system.

The second alternative would be to generate C or Java source code and compile it before the execution. This solution produces the fastest code if C is used because no interpreting is needed. However with this solution it is challenging to compile the source code and ensure that the system really works correctly. If rapid changes to the logic are needed the processing logic created in this way could not be tested before use. This makes the system unreliable and risky. Compilation is also very difficult if not impossible because it has to be performed in a customer environment and on different platforms. Hence this approach involves serious risks and is extremely difficult. However if the problems involved in this solution could be solved the solution would offer a very high performance.

It is an object of the present invention to create a reliable data processing system and method that both provide a relatively high performance and are relatively easy to adapt to new processing logics.

The object of the invention is achieved by forming a special logic definition structure based on the processing logic. The logic definition structure is designed so that it is easy to execute efficiently. The logic definition structure is also designed such that making modifications to the processing logic requires relatively limited and straightforward alterations in the logic definition structure. This is made possible by defining the processing logic in the form of a series of byte code instructions wherein each instruction contains a pointer to a piece of program code performing a function and a pointer to parameters to be used in performing the function. The instructions the program codes performing the functions the pointers and the data under processing are preferably stored in arrays thus allowing the use of efficient pointer mechanisms together with flexibility and ease of modification.

In an embodiment the logic definition structure comprises a parameter array containing pointers to the values of the parameters needed in the processing logic. The logic definition structure also includes a function code set containing program codes for performing the functions needed in the processing logic and a series of byte code instructions. Each of the instructions points to pointers in the parameter array and a function code that are needed in the execution of the instruction.

The present invention makes it possible to construct a reliable data processing system and method that both provide a relatively high performance and are relatively easy to adapt to new processing logics.

The inventive concept allows also several useful and advantageous embodiments which provide further advantages.

In an embodiment of the invention adaptation of provisioning logic can be implemented and visualised through a graphical user interface. New services and service packages regardless of their complexity can be rapidly introduced without having to make timely and costly changes to OSS BSS system of an operator.

The invention also offers embodiments of a mediation system which can be operated continuously once started because all of the configurations can be made while the system is in production.

There are also embodiments which allow both batch type processing and real time processing of event records.

As is apparent from the above disclosure the present invention can be applied in a great variety of applications requiring fast and reliable processing of event records.

Data Record A data record is a record containing data on e.g. a service usage or provisioning request. Data Record typically contains several data fields and may be structured records contain other records . In communication systems examples of data records include CDR Call Detail Record ER Event Record UDR Usage Data Record and IPDR Internet Protocol Detail Record.

Field Field is a single unit of a data record. Normally field contains a value that can be any data date integer string etc .

Event Event is a transaction occurring in a telecommunications network. Events are typically caused by actions taken by a subscriber while using telecommunication services. Events may also be based on actions taken by the telecommunication network or an apparatus connected to it e.g. while executing telecommunications services. Some events may be even generated automatically while executing service programs and performing other functions for providing services to the customers.

Event Record Event Record is a data record that indicates that an event has occurred. That is an even record provides information that a subscriber has used a telecommunications service. Event record contains also detailed information about the event. Hence an event record may contain information on the usage e.g. if the used telecommunication service is a phone call the event record may indicate how long the call lasted or if the service is downloading a file from an FTP server the event record may contain information about the size of the transferred data block.

Real time In contrast to batch processing real time processing refers to passing event record through mediation system in streaming format. That is as soon as a certain node in mediation stream has processed e.g. enriched the record it is passed to the next node. In batch processing a great number of event records are first collected in an intermediate storage and then the lot of event records is processed from the intermediate storage. Hence in batch processing processing delays experienced by the event records are typically long and vary between the event records. In real time processing processing delays experienced by the event records are typically short and substantially the same in magnitude between the event records.

Pass through time in a real time system may be e.g. from about 1 millisecond to 10 seconds. In some embodiments events may pass through the system even faster. Sometimes depending on the embodiment and application the term real time may also comprise pass through times longer that stated above. In general a real time service is a service that does not include considerable delays such that a user of the service considers acts being taken and services provided essentially at the moment the services are ordered i.e. events supplied to the mediation system .

Input record An input record is a data record that is read by a processing node. The format and structure of the input record are preferably predefined and known by the node.

Output record An output record is a data record that is written by a processing node. The format and structure of the output record are predefined and known by the processing node.

Processing Logic Executor Processing Logic Executor is a node application in a mediation system. Processing Logic Executor manages predefined processing logic in a processing stream. It executes the user defined rule set using existing prototype functions for rules.

Node Base Node Base provides an interface for reading input records and writing output records. Processing Logic Executor gets field values using the name of the field from Node Base. Node Base implements the functionality for operations like creating a new output record and rejecting existing record.

Arrow or actually a group of arrows pointing to a single field represent a function. Function is a prototype of one processing rule e.g. field validation value matching or conversion.

Function code Function code is a program code for performing a function needed in the predefined logic. In a preferred embodiment function code is a binary code directly executable by an operating system. Code uses function parameters for decisions that need to be made during function execution.

Instruction Instruction is a single unit of Processing Logic Byte Code. In a preferred embodiment an instruction contains a pointer to the function code pointer to the function parameters and the number of parameters. Instructions are created during the compilation process.

Byte Code Executor Byte Code Executor is the component that takes care of instruction fetching decoding and execution. Thus the Byte Code Executor takes the next instruction from array and calls the function of the instruction using the parameters of the instruction.

Shared library files Shared library files contain function code for both core and custom functions. The code is produced by C compiler and is fast to execute. Functions are loaded into memory from the files when the Processing Logic Executor node is started.

The system comprises a Compiler that uses the Predefined processing logic file as a source code and builds a Processing Logic byte code on the basis of the Predefined processing logic. The compilation is performed every time the logic is tested or saved into the persistent storage . The persistent storage holds all Processing Logic configurations and the compiled byte codes for them.

Processing Logic byte code is a plain text file that describes how the predefined processing logic should be executed. It has a sequential set of instructions and their parameters. All instructions are saved using the original function names.

The system also comprises a Processing Logic Executor which may be a node application that can be executed using Node Base. Processing Logic Executor itself comprises a function library byte code parser and a Byte Code Executor .

Function library holds all functions of the Processing Logic. In the figure the function library is divided into core functions and custom functions .

Byte code parser parses the plain text byte code and produces a more efficient form of the code. The complete byte code does not have any function names but direct pointers to them.

Byte Code Executor executes the parsed byte code. Hence the Byte Code Executor acts as the logic execution means for executing the predefined processing logic. The code is executed blindly without knowing what the functions do.

Hence in the embodiment the graphical user interface can be used to set up the system to process data records according to a desired processing logic . After defining the processing logic Compiler analyses the processing logic and compiles it into a format Processing Logic byte code that is fast and easy to execute. Compilation means reading the processing logic XML file creating a data structure of it and producing byte code file using the data structure. Compiler removes all useless information that is not needed in execution from the processing logic and flattens the structure of the logic. Compiler also reserves a field array to which all the fields are placed. After this fields are no longer referenced by their names but the index of the array. Byte code parser changes the index to direct memory location.

Required instructions are added into the byte code when compiler either encounters a function in processing logic definition or needs to add a function for e.g. jumping from one place to another in the code. When the compiler adds an instruction it also adds the parameters of the function as a list of indexes of the fields. Byte code parser builds the parameter array using this information. After the compilation is ready the compiler calculates the values for byte code header fields.

In an advanced embodiment a user can also define and add custom functions via the graphical user interface . When adding a custom function the system adds a new plug in screen for defining the function parameters in the graphical user interface . The system also adds a corresponding function code in the function code array of the Processing Logic Executor . For the custom function functionality the compiler includes a custom function extension for modifying the logic definition structure to include the custom function and parameters of the custom function in the field arrays of the system.

In the embodiment fields in input and output records are the fields read by the node base . The node base reads the fields from an input file and creates a data structure for the record. Each field can be fetched or written using the field name. The Processing Logic Executor does not have to read all fields from the input record.

In the embodiment internal fields in the Processing Logic Executor are temporary fields that the Processing Logic Executor has produced. Internal fields may hold the original data read from the node base or data generated by the functions . Internal fields can also be constants inside the Processing Logic Executor .

In the embodiment Processing Logic Executor allocates memory for all temporary fields in initialisation phase to make the execution more efficient. Fields are grown automatically during the execution if needed. The fields read from node base do not need any space node base takes care of that and they cannot be modified inside Processing Logic Executor .

In the embodiment the fields can be mapped directly from the input record into the output record without modifying the field or using it for any other fields.

In the figure each arrow or a group of arrows pointing to same field represent a function in Processing Logic Executor . Function may be e.g. string concatenation which takes two input fields and produces an output field. Processing Logic byte code includes of pointers to these functions and their parameters.

In the embodiment instructions in and are pointers to function codes . Function code exists in memory only once even if there are many instructions using it. Byte Code Executor always executes the instruction to which its program counter points. Byte Code Executor increases the program counter by one after each function call.

In the embodiment Processing Logic Executor gets its entire configuration in node application parameters and in byte code file . Node application parameters include all predefined processing logic specific parameters and the settings of Processing Logic Executor . Break points in the byte code and other debugging parameters are set using node parameters if needed. These parameters are used e.g. in debug mode.

Function pointer Function pointer points to the actual function code that is used in the execution of this instruction .

Number of parameters Function can use different number of parameters depending on the use of the function. E.g. value match function may get 3 N parameters depending on the number of values for matches.

Pointer to parameters Pointer to parameters points to the parameter array which contains all parameters needed in entire predefined processing logic. All parameters of this instruction are in the array one after another. The pointer refers to the first parameter and the number of parameters tells how many of them should be used. Parameter list can contain both input and output parameters.

In the embodiment function gets both number of parameters and the pointer to parameter list as function arguments.

In the embodiment Byte Code Executor handles the execution of the byte code . The execution is performed blindly without regard for the functions that are executed. The byte code is divided in three different parts initialisation processing and shutdown parts. Byte code execution is a straightforward task 

2. Call the function of the instruction using parameter count and parameter pointer as function parameters.

b. If the execution has reached the end return from process function and give the control back to the node base.

Processing Logic Executor of the above described embodiment is a very flexible component. A user can program new custom functions into the system without modifying the existing implementation. This makes it possible to create even very complicated logic using Processing Logic and make customer specific modifications to the system if needed without affecting the performance.

Processing Logic Executor of the above described embodiment also provides high performance. Interpretation overhead is minimal in this implementation meaning that running logic with Processing Logic Executor is almost like running a native code program specifically programmed for the customer s logic.

Processing Logic Executor of the above described embodiment is also very modular and thus easy to test. Each function is an independent software component that can be tested with an automated tool. This will save costs in porting of the product and makes it easier to implement new functionality to the system.

In the embodiment of the invention Processing Logic byte code is stored in plain text format to avoid problems with porting from one platform to another. Byte code contains following components 

Fields This section contains instructions for creating the field array. It lists all fields their lengths and initial values.

In the embodiment of the invention byte code parser takes care of reading the byte code file parsing it to internal structures and pre formatting fields. Internal structures include following components 

In the embodiment of the invention Processing Logic functions are tested with an automated test tool. The function developer may create some test data into a text file in a defined format and execute the test cases.

The automated test tool uses Processing Logic function library for loading the functions defined in test case file. No coding is needed for tests.

An embodiment of the invention includes processing data records in mediation systems with communications networks. Sophisticated mediation solutions have several beneficial features the most important of which are explained below.

In each node includes a node base and a node application . Node base provides the basic standard functionality for the node . It handles the internal usage data transmission mechanism between the nodes and encodes the internal usage data. Node base provides an interface to the node application for accessing the usage data and collecting customised audit information. For performing its tasks the node base may include several components for example a node input a node output a node API a node configuration and a node audit .

Node Input is responsible for reading the data input records from the internal input data sources parsing it and passing the data to Node Application interface. Node Input uses a Data Transmission Interface that defines the internal data format and data transmission mechanism.

Node Output is responsible for reading the data output records from the Node Application Interface and encoding and writing it to Data Transmission Interface . Node Output uses Data Transmission Interface that defines the internal data format and data transmission mechanism.

Node API provides the Node Application the access to the usage data. It hides to internal data transmission interface from the Node Application . Node API includes functionality for providing the usage data to and receiving it from the Node Application . It is also used for retrieving customised audit information from the Node Application and for providing configuration parameters to it.

Node Configuration is responsible for reading the configuration data from a Configuration Interface and for initialising the Node according to given configuration parameters. Node Configuration also passes Node Application specific parameters to the Node API. Node Configuration uses Configuration Interface that defines the configuration data format and transmission mechanism.

Node Audit is responsible for writing various audit data to an Audit Interface. Node Audit defines content for audit interface. Node Audit uses Audit Interface that defines the default audit data format and transmission mechanism. Node Audit uses also a Management Interface that defines monitored data format and transmission mechanism. This is used for example for indicating the status of the Node.

Data Transmission Interface and or buffering define the usage data format and data transmission mechanism between the Nodes.

Mediation consists of different processes like collection validation enrichment aggregation correlation rating conversion and delivery. The varied functionality allows OSS BSS systems to receive usage data just as they want it.

The keywords of the mediation solution architecture are simple and straightforward. The modular design of the solution according to an embodiment of the invention enables real time and distributable processes reliable operation and high performance.

Nodes are functional components specialised in different mediation processes such as collection aggregation validation correlation and formatting or a combination of these. Nodes are linked together to form processing streams for event record handling.

Each Node has standard functionality that provides an automated data transmission mechanism between the Nodes and processing information logging mechanism between the Node and the Node Manager not shown in figure . The actual usage data processing logic is implemented by different applications that reside in the Nodes. These applications are isolated from internal data transmission mechanism and internal data formats enabling easier application development. Applications are drawn as ovals in the presented. The system provides a standard interface through which the applications communicate with the processing framework.

Nodes can be further categorised according to their functionality. The functionality depends on the Node Application and the Node s position in the Processing Chain . The first Node in a Processing Chain can be called a Collector Node and the last Node a Distribution Node. In these cases the data parsing and formatting functionality needs to be performed by the application itself and the standard functionality provided by the Node Base is not used. The flow of usage data and the standard components that become obsolete are shown in the . In this Fig. it is assumed that the data source and destination both operate with some real time protocol i.e. they are using a socket connection for sending and receiving data.

If the output data destination requires the use of file based interface the applications take care of formatting and writing the data in the output files. In a case like this it might be necessary to separate the output file generation and the delivery of the output files to separate Nodes .

In an embodiment of the presented invention the Processing Logic Executor represents an example of a node application used in mediation systems.

The above description is only to exemplify the invention and is not intended to limit the scope of protection offered by the claims. The claims are also intended to cover the equivalents thereof and not to be construed literally.

