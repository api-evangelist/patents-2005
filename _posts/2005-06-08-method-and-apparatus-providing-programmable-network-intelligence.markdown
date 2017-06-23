---

title: Method and apparatus providing programmable network intelligence
abstract: Programmable network intelligence approaches as disclosed herein provide apparatus, methods and tools to achieve programmable interfaces to a device, or group of devices or a network where native programmable interfaces are not available.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07721304&OS=07721304&RS=07721304
owner: Cisco Technology, Inc.
number: 07721304
owner_city: San Jose
owner_country: US
publication_date: 20050608
---
This application claims benefit of Provisional Appln. 60 521 633 filed Jun. 8 2004 the entire contents of which is hereby incorporated by reference as if fully set forth herein under 35 U.S.C. 119 e .

This application claims domestic priority under 35 U.S.C. 120 as a Continuation in part of U.S. application Ser. No. 11 012 885 filed Dec. 14 2004 the entire contents of which is hereby incorporated by reference as if fully set forth herein.

This application is related to U.S. application Ser. No. 11 148 709 filed Jun. 8 2005 of Krishnam Raju Datla et al. entitled Apparatus and Method for Intelligent Configuration Editor U.S. application Ser. No. 11 148 709 now U.S. Pat. No. 7 499 902 filed Jun. 8 2005 of Krishnam Raju Datla et al. entitled Method and Apparatus for Data Model Prediction U.S. application Ser. No. 11 148 489 filed Jun. 8 2005 of Krishnam Raju Datla et al. entitled Method and Apparatus Providing Unified Compliant Network Audit and U.S. application Ser. No. 11 148 708 filed Jun. 8 2005 of Krishnam Raju Datla et al. entitled Configuration Syntax and Semantic Validation. 

The present invention generally relates to network management. The invention relates more specifically to approaches for providing a management interface to a network device that does not have a native management interface.

A portion of the disclosure of this patent document contains material which is subject to copyright protection. The copyright owner has no objection to the facsimile reproduction by anyone of the patent document or the patent disclosure as it appears in the Patent and Trademark Office patent file or records but otherwise reserves all copyright rights whatsoever.

The approaches described in this section could be pursued but are not necessarily approaches that have been previously conceived or pursued. Therefore unless otherwise indicated herein the approaches described in this section are not prior art to the claims in this application and are not admitted to be prior art by inclusion in this section.

A typical computer network consists of various devices such as routers switches wireless access points firewalls etc. illustrates an example network that includes such elements.

A typical network device provides a command interface that is accessible using the telnet protocol a secure shell SSH connection or serial port interface to create update retrieve and store management information relating to the device. A network management station NMS can deliver commands through such an interface to provide a higher level or enhanced management capability to the network operator or administrator.

To interoperate with a network device the NMS must have knowledge of what commands the device supports so that the NMS can deliver commands that are compatible with the device s command interface and that produce desired results. One way to provide such knowledge to an NMS is by adding command definitions to the NMS manually either through a programmatic approach by updating the computer program code that forms the NMS or by changing a separate device data table that is used by the NMS. However this approach is slow and error prone especially when the NMS supports a large number of different devices.

Further whenever a change occurs in the set of commands that a particular device type supports a change is required to the NMS. Thus this approach requires ongoing software development efforts to keep the NMS compatible with the commands that devices recognize or support.

Therefore there is a need for a better way to provide knowledge about commands that a network device supports.

A typical network device such as a router or a switch as used in packet switched networks provides a command line interface CLI that is accessible through Telnet Secure Shell SSH and serial port interface for changing the device status or configuration. Each configuration command for the device has an associated syntax. A Network Management Station NMS can use the configuration commands to provide a higher level or enhanced management capability to the network operator. The NMS requires knowledge of the device configuration commands and the syntax of the commands to perform changing the configuration of a device.

One disadvantage with a CLI is that it is suitable for a human operator but not for programs that can configure and control the device. A programmable API is required for such tasks. The devices can be built with programmable APIs but providing a programmable interface on already existing systems and devices can be very expensive if not impractical. It would be beneficial to have an automated approach for generating a programmable interface for an existing device or for devices that are already deployed at operating sites.

The NETCONF network device configuration protocol under development by the Internet Engineering Task Force IETF provides mechanisms to install manipulate and delete the configuration of network devices. It uses an Extensible Markup Language XML based data encoding for the configuration data as well as the protocol messages. The NETCONF protocol operations are realized on top of a Remote Procedure Call RPC layer. NETCONF is an emerging standard and many network devices do not presently support it. Further many network devices cannot directly execute commands that are delivered in XML and many network management applications cannot interoperate with XML documents that conform to NETCONF.

Certain past approaches have attempted to implement a configuration interface layer on top of the CLI supported by Cisco IOS Software from Cisco Systems Inc. These approaches have supported a narrow range of device types and configuration. These implementations also have required manual coding of the CLI rules and since the data model is custom have also required manual coding of processes for transformation of the model to the CLI and CLI to the model.

A method and apparatus providing programmable network intelligence is described. In the following description for the purposes of explanation numerous specific details are set forth in order to provide a thorough understanding of the present invention. It will be apparent however to one skilled in the art that the present invention may be practiced without these specific details. In other instances well known structures and devices are shown in block diagram form in order to avoid unnecessarily obscuring the present invention.

The needs identified in the foregoing Background and other needs and objects that will become apparent for the following description are achieved in the present invention which comprises in one aspect a method comprising the machine implemented steps of receiving one or more command line interface commands associated with a network device that does not natively provide a programmable management interface creating and storing a knowledge base comprising a representation of a syntax and semantics of the commands receiving from the knowledge base a data structure representing a particular configuration command among the commands creating and storing an intermediate data model that represents the configuration command wherein creating the intermediate data model includes predicting one or more attributes of the configuration command based on the intermediate data model creating and storing a file defining an application programming interface for the network device.

According to a feature the application programming interface is generated at least in part based upon a capability matrix containing information about capabilities of the network device. According to another feature the predicting is performed at least in part based upon device capabilities that are derived from the capability matrix. According to still another feature an application request is received at the application programming interface and in response thereto the intermediate data model is selectively transformed into a text representation of the particular configuration command or into a structured document representation of the particular configuration command.

In another feature the knowledge base is created and stored in an automatic command learning process based on receiving and interpreting a plurality of the commands as the commands are provided to the network device.

In yet another feature the predicting includes predicting one or more names of one or more parameters to the particular configuration command. According to various other features the predicting includes predicting whether a particular parameter is mandatory or optional to complete the particular command predicting data types of the parameters predicting a cardinality attribute of the particular configuration command and predicting an order of the parameters.

According to another feature the intermediate data model represents a command using one or more container objects and one or more properties objects. In yet another feature the knowledge base is created based on receiving information from one or more CLI management information bases MIBs and one or more SNMP MIBs supported on the device. In still a further feature selectively transforming includes selectively transforming the intermediate data model into an extensible markup language XML representation of the particular configuration command. The XML representation may conform to NETCONF protocol and may be transformed in response to receiving one or more NETCONF XML requests.

In other aspects the invention encompasses a computer apparatus and a computer readable medium configured to carry out the foregoing steps.

The apparatus and methods specified in this disclosure will achieve programmable interfaces using a capability detection engine to detect the capability of the devices a predicted data model which accurately model the data structures required to achieve command and configuration operations a validation engine to verify the validity of the predicted data model and a run time environment which provides the programmable interfaces.

According to one embodiment the approach described herein can build a data model that accurately represents the command line interface that is supported by one or more network devices. The data model predicts the data structures required to generate the device native commands. The data model can be used to generate programmable interfaces which can be used by other programs or network management systems to configure and control the devices.

A Data Model Prediction approach disclosed herein attempts tries to derive the data structures required to represent native commands supported on a particular device. Generally device commands follow certain syntax and semantics and may take one or more parameters. Each parameter may have an associated type and constraints. Some parameters may be mandatory and others are optional. The syntax for a particular device may require parameters to appear in a particular sequence. A command can have a single instance or multiple instances.

In one embodiment automated logic builds a knowledge base that represents the commands and the syntax for each command supported by a device under one or more command views. In an embodiment a Capability Detection engine builds the knowledge base. The knowledge base may comprise information stored in a database either in the form of binary data text or a set of structured electronic documents e.g. XML documents. The Data Model Prediction approach herein uses the command knowledge base to build an accurate data model.

According to an embodiment the Data Model Prediction approach herein predicts the data structures and parameters in the data structures with the following aspects Cardinality which specifies if the number of instances allowed whether a parameter is mandatory or optional data type of parameters such as integer Boolean string etc. and order of the parameters present in the structure such as sequence choice and all.

In one embodiment predicted data structures are represented in the form of Containers and Properties. A Container can contain other Containers and Properties. A Property represents a leaf item in the hierarchy and may represent a specific parameter in the command.

In an embodiment a command and its associated keywords and parameters are represented in a hierarchical structure of Containers and Properties. If a command has one keyword followed by a parameter which defines the value for the keyword then the command is represented by a property. As an example of a Data Model for a simple command the command hostname sj rtr1 may be represented in XML format as 

If a command has a keyword and followed by multiple parameters then the command is represented by a Container which may contain other Containers and Properties. As an example of a Data Model for such a more complex command the command ip address ip address mask secondary may be represented as shown in Table 1 

An embodiment determines a command name. Each container and property is identified with a name. The name is derived from the name of the parameter. Some parameters may not have associated name. In that case a name is derived from the description of the parameter using natural language processing.

An embodiment determines whether a command parameter is mandatory or optional. Whether a parameter is mandatory or optional is predicted by analyzing the command and its parameters. If the command can be completed without a particular parameter then the parameter is optional. If the command cannot be completed with a specific parameter then that parameter is mandatory. If a parameter is optional all the subsequent parameters may not be optional and may be dependent on the predecessor parameters. All parameters are analyzed completely to determine if a parameter is mandatory or optional.

An embodiment determines the cardinality of a command. A command can have one or more instances. If a command has cardinality of 1 that is a single instance then issuing multiple such commands causes a device to overwrite previous commands and apply only the most recently ones. If a command has cardinality of more than 1 then issuing multiple such commands causes a device to create and apply multiple instances in the device configuration.

In one embodiment the cardinality of a command is predicted using the negation version of that particular command. For example assume a command has the form hostname name and sets the name of the device in question. If the syntax of the negation command is no hostname or no hostname name which indicates that the name is an optional parameter then the hostname command has cardinality of 1. If the negation command syntax is no hostname name which indicates name is a mandatory parameter that must be specified to negate the command then the hostname command has cardinality of more than 1.

An embodiment determines the required order of parameters. A command can accept a parameter from a set of multiple parameters. In that case the data structure must specify the order as choice for the possible parameters. If the command has parameters that follow one another in a strict order then the sequence must be used.

A parameter may have a data type for values it can accept such as Integer String Boolean IP address etc. According to an embodiment the data type for the values of parameters is predicted. If a parameter accepts only digits then the type may be integer if a parameter accepts characters as valid input then the type is String if the parameter expects a numeric string with subfields delimited using periods then the type is IP address.

In an alternative embodiment system is disconnected from the network device and receives CLI commands from a configuration file network management system application or user input terminal.

SNMP detection engine and command detection engine receive copies of commands that a user or application issues to network device . SNMP detection engine detects commands that are issued using or conform to Simple Network Management Protocol SNMP and creates a structured representation of the commands in one or more SNMP XML documents . SNMP to DM builder receives the SNMP XML documents and forms at least a part of data model based on them.

Command detection engine detects commands that are conform to a general execution or configuration command syntax for network device and creates a structured representation of the commands in one or more command view XML documents . CLI view to DM builder receives the XML documents and forms at least a part of data model based on them.

A detailed description of example approaches for data model prediction are now described in the context of an Enhance Device Interface E DI system that provides an XML programmatic interface for configuring network devices from Cisco Systems Inc. San Jose Calif. that run Cisco IOS Software and Cisco CATOS Software. The E DI system allows a network management application to configure Cisco devices using the IETF NETCONF protocol. The description in this section is provided merely as one example of how to make and use the general approaches that are otherwise described and claimed herein. Thus the embodiment of this section is intended to provide one clear example but not to limit the full scope of the invention which is set forth in the appended claims.

In overview the E DI XML interface provides for device configuration using a data model that follows closely the native device CLI command structure. The E DI can replicate a complete CLI command set of the managed devices externally. Thus XML interface covers a complete set of capabilities that are available through the CLI. Furthermore because E DI uses an automated CLI learning process E DI can support to a wide variety device versions and software versions.

A foundation of XML interface includes a data model definition and processes providing for the transformation from XML to CLI X2C and CLI to XML C2X . The following subsections describes the E DI data model or Intermediate Data Model IDM an algorithm for deriving the data model from the CLI knowledge base and algorithms for the X2C and C2X transformations.

In one embodiment the E DI interoperates with an automatically generated CLI command knowledge base. By generating the XML data model using a generic rule from the CLI knowledge base E DI can perform the X2C and C2X transformation. Therefore the XML interface is not a separate feature that needs to be developed separately instead once the CLI is supported for a specific device the XML interface is automatically available. Further in an embodiment the E DI data model as its CLI counterpart is device and software version specific and reflects the true capabilities of the device.

In an embodiment at run time the IDM is built from the CLI View on demand as X2C and C2X transformation for a specific device type and software version is needed. To conserve memory the IDM may be removed from memory when it is not used for an extended period of time.

The CLI View is a graph of Parser Nodes that an E DI CLI parser uses to parse or validate CLI that is entered by a user at an E DI console. A CLI View is created for each IOS CLI mode. Thus a complete CLI knowledge base is composed of a set of CLI Views bound by the entry commands that lead one view to another view.

In an embodiment E DI CLI Views are packaged or organized per device family and major IOS release. For example one package of the CLI knowledge base is provided for the Cisco 29xx router family with IOS version 12.2. This document describes details of CLI structure that are relevant to IDM conversion.

As a comparison also shows how the commands within a CLI command mode relate to internal functional subsystems of a network operating system. The main command mode includes a parser subsystem and one or more functional subsystems A B C. The main command mode is associated with commands contributed by many subsystems. Typically a command from a particular subsystem A B C will start with the same prefix for example aaa . Other sub modes other than the interface sub modes generally contain commands contributed by a specific subsystem.

A particular token may contain a carriage return tag that specifies that the command can terminate there as seen in described further below. A particular token also may contain a negation carriage return tag that specifies that the negation or no version of the command can terminate there. Proceeding downward from a root node such as mode node the token that has the first from the root can be used to specify a delineation of the command. A delineating node accepts a delete management operation that deletes the entire command from the IDM. Information below the delineating node represents parameters of the command while information above the delineating node is grouping criteria prefix or a naming parameter key of the command.

In an embodiment a command is defined strictly syntactically based on the first position not based on the actual semantic of the command. A CommandContainer may be a Container of one or more semantically separate but related commands.

In an embodiment the CLI command structure is represented in E DI as a graph of ParserNodes. Child nodes represent choices of next acceptable tokens following the parent node. A ParserNode can be visited from multiple parent nodes thus a sub graph or a node can be shared or referenced from multiple parent nodes. A node can also refer back to one of its ancestor nodes creating a loop. Excluding any loops if the shared sub graphs or nodes were duplicated the structure would appear as a tree of CLI tokens.

Each subclass represents a type of CLI input token. There are two basic categories of tokens keyword token and parameter tokens. A keyword token is represented by the KeywordNode class and parameter tokens are represented by StringNode class NumberNode class and IpAddressNode class which are associated with command parameter nodes .

A simple example of the ParserNodes for a simple hostname command consists of only two nodes. More complex examples are shown in . is a diagram showing a first example CLI parser graph and is a diagram showing a second example CLI parser graph. Referring first to a parser graph represents the following three commands 

The commands represented in the graph may be delineated by walking the graph from the root mpls node downward until the first tag is reached in a branch of the graph. For example the first command is delineated by visiting mpls node label node and range node which has a tag. The third command is delineated by nodes which also has a tag.

The second example of illustrates a more complex graph in which a sub graph and nodes are shared or referenced by multiple nodes. Specifically graph comprises a sub graph that a DistributeList node references. Further an IPACLName sub graph is referenced by both in node and out node .

In an embodiment the IDM data model is packaged in a manner that mirrors the E DI CLI view packaging. For each CLI command mode a package is created. shows a sample hierarchy of an IDM package. In one embodiment a hierarchy comprises a root node representing a root configuration mode and one or more child nodes A B representing top level configuration modes. Each child node may have one or more further child nodes that represent corresponding command sub modes. In an embodiment hierarchy is defined in one XSD document per command mode.

Since a common CLI View package may be shared across different devices in a device family and across devices that use different software versions the IDM package associated with the shared CLI View may be shared as well. No IDM specific sharing is required.

According to an embodiment the E DI model provides for automatic definition of the data model from CLI and for automatic run time transformation from XML to CLI and from CLI to XML. IDM automated model generation is facilitated using a data model that follows the CLI command structure. Elements and grouping of elements of the data model reflect the syntactical structure of the CLI and not necessarily the semantics of the elements.

Thus the IDM structure matches almost one to one with the CLI model structure. In general one leaf node of a CLI parser graph is associated with one leaf IDM node such as a Property that represents a Value or Parameter. Further one non leaf IDM CLI node produces one non leaf IDM node namely a Container and an optional leaf IDM node which is a Property. A shared sub graph in the CLI model also translates into a shared sub graph in the IDM. Likewise a loop in the CLI model translates into a loop in the IDM.

To relate the IDM with the CLI commands from which it is derived Containers are categorized based on their position relative to the Mode and Command boundary into CLI mode submode ModeContainer PrefixContainer CommandContainer and DataContainer objects.

A CommandContainer indicates the boundary of a CLI command. Some very simple commands may contain only one property and are directly contained under a ModeContainer or PrefixContainer. In this case the CLI command boundary is the Property node. The definition of what a Command is strictly defined based on the first position not based on the actual semantic of the command. A CommandContainer may in fact be a Container of one or more semantically separate but related commands.

A NamingContainer is a special container created to group the command s naming properties or keys for commands that can have multiple instances non singleton .

The IDM structure resembles a tree but some nodes can have extra references from other parent nodes. These multi reference IDM nodes correspond to multi referenced CLI nodes.

In addition to categorization based on position each Container can be categorized based on the order of its child nodes. Such an order relates to the syntactical constraints of an IDM XML configuration request for use in the X2C and C2X transformation processes and not the model structure in the Device component. This ordering approach is consistent with CLI configuration rules in which the same command that affects the same data can appear more than once in configuration file and the last command instance overrides all other previous instances of the same command.

In an embodiment IDM uses as Orders Choice Sequence Sequence of Choice and Loop. Choice means that there can be only one child under the Container and it must be one of the child Containers or Properties. Sequence means that the child Containers or Properties must appear in the defined sequence. Sequence of Choice is a Sequence of zero or more members of the Choice. Loop is represents a looping or list structure in XSD this is a sequence of group that contains a sequence and choice tags.

Since a non keyword parser node represents a value the non keyword parser node maps to both a Container and Property. For example CLI node D maps to IDM Sequence D and Value D. Generally the extra Property in the mapping is the Value Property of the Container which is treated as part of the Container Order. A Value Property that appears above the Command boundary is the Key Property Value which is defined inside an extra Container called Naming. Thus a non keyword parser node maps into either a Choice Container and a Value or a Sequence of Choice Container and a Naming Container.

In one embodiment two exceptions to the Sequence of Choice and Choice Container types are provided Sequence and Loop. A Sequence is created in a few cases in which a non branching series of CLI parser nodes is found. In IDM a Sequence can only contain leaf Property nodes and an optional Choice or Sequence of Choice last child. For example structure A B C D is invalid instead it will be expressed as A BD CD .

In one embodiment by mirroring the CLI Model structure an IDM Container or Property name is derived from their associated CLI node. The name of an IDM Container represents a group of nodes that syntactically follow that Container node but does not necessarily represent a semantic grouping of the child nodes.

A loop container is created when a CLI parser node revisit one of its ancestor node or itself. In IDM the resulting loop is flattened and instead of creating an infinite nesting structure an infinite sequence is created. That is instead of . . . the tags . . . . are used. The use of loop containers is discussed further in this document.

An embodiment of the IDM also supports a delete operation and cardinality functions. A close mirroring of the CLI model structure and the IDM structure is also reflected in how the CLI and tags map to delete operations and cardinality concepts in the IDM. A tag in a CLI parser node means that the IDM Container associated with that node can be empty or does not require any child nodes. Therefore the child nodes have a cardinality of minOcc 0 optional . A tag in a CLI parser node corresponds to a Container or Property that accepts a delete operation or that can be empty. illustrates the foregoing relationships.

In one embodiment the effect of a delete operation is determined according to the following set of rules. The meaning of a delete operation depends on where the delete operations are specified. A delete operation specified in a NamingContainer node deletes a multi instance command identified by the name inside the NamingContainer. Semantically a delete operation specified in a NamingContainer node deletes multiple related configuration nodes that are identified by the key property. A delete operation in a CommandContainer node deletes a singleton command. For certain CommandContainer nodes the delete operation deletes multiple related configuration sharing the same prefix. A delete operation in a Command Property node deletes a simple singleton command. A delete operation in the DataContainer or simple Property node sets the data to false or null.

According to one embodiment the IDM provides X2C and C2X Mapping Data. Since the IDM is automatically generated from CLI data and the IDM and CLI structure are similar a relationship between the generated IDM node and CLI node is known. The mapping of all IDM Properties and an IDM Container with corresponding CLI nodes is captured for use in performing X2C and C2X transformation processes. Since the mapping is primarily done through the IDM Property a CLI node maps to a Property if a Property is created from that CLI node. If only a Container is created then the CLI node maps to the Container.

According to one embodiment the IdmBuilder module primarily determines from an input CLI View whether a CLI View element represents a Container or Property the Container type and the Order. These characteristics determine the basic structure of the IDM to which the following additional information is added Name of Container and Property Description Property type Naming Property Cardinality and mapping information between IDM and CLI.

In an embodiment the IDM is created using a recursive algorithm implemented in appropriate software hosted on a general purpose data processor configured as a network management station which traverses the CLI parser graph. For example a method Build may be implemented according to the pseudocode of Table 2 

The following further describes the rules used within the Build method given in the example of Table 2.

Determining whether a Container or Property is represented is the primary decision in building the IDM. The decision determines the structure of the IDM model and affects the naming decision as well. The primary criteria in determining the presence of a Container or Property are the CLI parser node s child node count and the presence or absence of the and tags. Generally in an embodiment a leaf CLI node maps to a Property and a non leaf IDM CLI node maps to a Container and optionally to a Property if the CLI node is a non keyword node.

In one embodiment logical rules implemented in the Build method drive determining whether a Container or Property is represented. A container creation rule and a property creation rule may be implemented. For example a container creation rule may express the logic shown in Table 3.

A Container can be created both for keyword and non keyword parser nodes. A Container created from a keyword node that contains a tag is a Boolean container since an empty container represents a Boolean value.

As another example a property creation rule may provide that a Property is created for a Non keyword parser node and a Leaf keyword parser node that has not been used to create a Boolean Container. In an embodiment when both Container and Property are created for the same parser node the Property is set as the Value Property of the Container. The new Container will be passed into the recursive Build method to be used as a parent for the IDM node created for the child parser nodes. If no new Container and Property are created then the collected keyword derived name is passed to all child node processing. Table 4 presents an example of the resulting model structure.

In the example of Table 4 the cdp keyword becomes a Container because it has multiple child nodes. The holdtime value does not become a Container because it only has a tag and not a tag. The name HoldTime is used in creating the integer property.

The Container Type signifies the position of the Container within the IDM Containment hierarchy. In an embodiment the following rules are used to identify Container types.

Container Order determines the ordering constraints of an IDM XML configuration request. In an embodiment the following are rules used to identify the Container Order for a given Parser Node and its parent. Since CLI nodes represent Choice order the general rules are 

2. of child node 1 a Choice for Command Container or below and Sequence of Choice for Prefix Container. One exception is Member of a Container that contains Naming Container is a Sequence of Choice.

The exceptions to the rules are Sequence and Loop. A Sequence is created generally for a string of non branching nodes below the Command boundary. Specifically a node that satisfies the following condition maps to a Sequence 

c. child 1 AND of sibling 0 check the parent s first child. If parent s first child s child nodes 0 Container is Sequence.

In an embodiment the Loop attribute is not determined during Container creation but later when a loop condition is detected when the node is revisited. Loop creation is discussed separately herein.

In an embodiment a Container name and Property name are determined. In one embodiment a Container is named according to the logic in Table 5.

In one embodiment a name may be derived from a description. Names derived from CLI keywords do not require extensive processing. However names derived from description text requires additional rules so that the constructed name is well formed and can be understood within the context of the Container. In one embodiment to convert description text into a name the description text is tokenized into words and rules are applied to each word. After applying the word rules additional rules are then applied to create the name.

In one embodiment the rules for preparing the word tokens are driven by the data shown in Table 7 which can be stored along with a specific IDU to ensure that the naming for that package remains the same given a version of the naming algorithm.

Certain embodiments provide for resolving naming conflicts. For example an IDM Container and Property name must be unique within a parent Container. In most cases such conflicts are caused by an insufficient number of tokens used in a name that is derived from a text description. In some cases CLI could result in duplicated Properties derived from separate Parser nodes that are semantically equal. These observations may be used in one embodiment in a process summarized in the pseudo code of Table 9 in which child node processing resolves naming conflicts.

Since the IDM processes described thus far do not understand the semantics of any of the commands naming conflict resolution does not detect duplicated properties and may result in semantically common Properties with different names. For example the Properties MonthYear1 and MonthYear1 DayMonth are semantically same as MonthYear and DayMonth however they map to different CLI nodes and hence result in duplicated names. In this case the duplicate name MonthYear is resolved by adding 1 as suffix and the duplicate name DayMonth is resolved by appending the MonthYear1 as prefix.

In one embodiment a Key Property or Properties compound key uniquely identifies a parent Container from sibling Containers. For non sub mode commands assuming that a single negation command will not clear multiple lines of configuration Key Properties are detected by examining the Properties that precede the first tag. For sub mode commands the Key Properties are Properties that precede the Sub mode node. Not all actual Keys can be detected however one such exception is a list command.

In an embodiment Property Data Types are derived from the CLI parser node types by stripping the Node suffix. Two exceptions are that a KeywordNode translates to Boolean and a NumberNode translates to Integer. These are the basic Data Types that are exposed in the XSD documents others may be provided in other embodiments.

In an embodiment each Container and Property is marked to indicate whether it can be deleted. For example a Container or Property created from one or more Parser Nodes that are followed by a tag accepts delete operation in the XML request. The first tag from the root that is associated with the CommandContainer corresponds to a delete operation to delete the entire Command Container. An inner tag specifies disabling or nullifying only the Data Container or Property.

A Key Properties delete operation is moved to its Naming Container. The Naming Container becomes capable of deletion and the flag indicating deletion capability is cleared for the Naming Properties inside the Naming Container. Properties within a delete able Container may also be delete able consistent with the associated CLI behavior. For example in the command kw the second tag translates to a delete able Property for nullifying the property.

In an embodiment a Delete operation is distinct from a Nullify operation. For example the no keyword before a CLI command causes a device either to delete the entire command or to nullify a command s parameter. In an embodiment the no keyword translates to the IETF NETCONF protocol delete operation on the XML element to be deleted or nullified. The no for deleting the entire command translates into delete operation in the CommandContainer for singleton command or the NamingContainer of a multi instance command. The no for nullifying a parameter translates into delete operation on the Property associated with the parameter or on the Container if the no applies to all the parameters in the Container.

A Container and Property with delete can have child XML elements that will be ignored. This approach is consistent with a CLI that allows values in the no command. Further this approach allows a configuration to be negated by simply apply the no prefix in CLI or the delete operation in XML. For a Property with a numeric value a dummy numeric value must be supplied for XML correctness.

Container and Property Cardinality values determine the minimum and maximum occurrences of the node under its parent Container. Cardinality values for Containers at the Command level or above are minOcc 0 and maxOcc unbounded since there can be 0 or more command lines in a configuration file. The cardinality values do not specify whether the Command is singleton or multi instance. A multi instance Command is specified by its Naming Container. In an embodiment for Containers and Properties under the Command level the following logical rules apply 

1. Default min and max occurrences are which implies no specific constraints are explicitly specified. In XML this implies min and max occurrences of 1.

2. If parent parser node has then the min occurrence of the Container and Property created for the current parser node is 0. Optional 

3. If parser node is the same as the node we have a loop. Mark members of the Loop Container max occurrence UNBOUNDED.

The following paragraphs address techniques for handling multi referenced IDM Nodes and Loops. As described above both the CLI structure and IDM structure defined herein may contain nodes that are referenced from multiple parents. Such multiple referencing occurs below the Command boundary and it is a necessary feature for constructing complex CLI syntax that contains optional tokens multiple complex options sharing common CLI phrases or a loop.

In the CLI View in an embodiment multi referenced CLI nodes are directly referenced as Java references from multiple parents. In the IDM View a multi referenced IDM node has one parent and optional reference parents. Thus the structure resembles a logical tree. References from additional nodes are stored as a reference parent list. Additionally the same multi referenced child DM node can appear as more than one member within the same IDM node.

In one embodiment to support multi referenced CLI nodes the rules of Table 10 are used in constructing the IDM.

An IDM node that references parents will require special handling in the X2C and C2X processing for the correct parent path to be chosen.

A Loop Container is a special case of the multi referenced IDM node in which the node that is revisited is one of its ancestors. Instead of creating a reference to the ancestor creating a loop in the IDM structure the loop referencing the IDM Container it must be a Container simply maintains the ID of the multi referenced IDM node as its loopRefId. A Loop Container does not fit one of the standard Orders Sequence Choice or Sequence of Choice. In terms of XSD a Loop is a Sequence of Group with Group max occurrence being unbounded and where the Group is defined as 

The following is a simple example that illustrates loop structure. Assume that the CLI supports a command having the form 

As another example Table 12 presents XML text for a command of the form filter map6 vlan list 6 7 9 10.

In a more complex loop the Loop Referencing Container may not be a direct child of the Loop Container but contained under one or more hierarchy of Containers.

The Loop Property is a Property that has a maximum occurrences maxOcc value of unbounded and associated with a CLI parser node that references itself.

Optionally in one embodiment certain model simplifications may be performed. In one embodiment an enumeration simplification is performed either during or after model construction. Enumeration post processing converts a Choice Container of Boolean Properties into an enumeration. Boolean Properties that are reverted back to its numeration are renamed with their original CLI keyword values.

In another embodiment simplification involves not handling certain command patterns. For example as noted above an IDM Sequence cannot contain another Container. Therefore although the following three patterns can be detected they cannot be used as it would require custom naming rule that is inconsistent with the IDM naming C B C

Referring again to in an embodiment a C2X module transforms one or more CLI commands from a network device into XML data for use in an XML response or notification such as a response or notification that is compatible with the NETCONF protocol. In an embodiment the C2X module performs a transformation using the mapping information in the IDM View that is produced by the IdmBuilder during model generation. According to an embodiment the C2X module implements the algorithm set forth in Table 13.

In Table 13 steps 6 to 8 determine which parent to traverse up to in step 3 while handling any multi referenced IDM Node. illustrates the C2X transformation for an example set of nodes A to H inclusive. If a parsing error arises when the CLI commands are parsed at step 1 in an embodiment the device configuration commands that fail parsing are not dropped. In addition to reporting errors the CLIs that fail parsing are in the generated XML document delimited by a cmd tag.

Referring again to in an embodiment an X2C Transformation module receives transforms XML data such as data from a NETCONF XML request into CLI for a target device. The X2C Transform process is performed using the mapping information in the IDM View that is produced by the IdmBuilder module during model generation. According to an embodiment the X2C Transform process uses the algorithm of Table 14 

Step 7 is used to determine which parent to chose in traversing up the CLI View parser graph in step 4 above taking into account any multi referenced IDM Node. illustrates X2C transformation.

In the foregoing approaches CLI commands can be embedded inside XML configuration statements wrapped inside the cmd tag. One use of this approach is to support transformation of CLI that is not known to the E DI CLI parser at the time that transformation is performed.

In one embodiment when the C2X Transform module of is used to transform CLI to XML errors may be reported by the E DI CLI Parser as it performs a syntax check of the CLI. A list of command lines that failed CLI parsing is reported. In another embodiment CLI commands or lines that failed a syntax check may be embedded in a CLI tag. In another embodiment in the X2C Transform module of the location of errors is reported as the String Path of the element in error.

In either embodiment E DI run time provides the following error processing options Stop Ignore or Skip. Stop means to stop processing when an error is encountered. Ignore which is applicable only to X2C means to ignore the error and generate output for the element in error. Skip means to skip to the next valid input and do not produce invalid output.

An example interface design is shown in which illustrates the main classes associated with IdmBuilder. In an embodiment to allow versioning client code does not instantiate the IdmBuilder class directly but performs instantiation through the IdmBuilderFactory class. Which IdmBuilder to instantiate is determined based on the namespace in an XML request.

In one embodiment a method and system for automatically determining commands for a network element are implemented using an auto learning software framework that learns commands that particular network devices support in an automated manner and builds a command knowledge base. A network management system or station NMS can use the knowledge base to provide management for a large number of different types of devices quickly and efficiently. The disclosed approach is less error prone compared to manual entry or coding of device commands.

An example embodiment is now described with reference to and . is a block diagram of an auto learner framework according to some embodiments is a ladder diagram of an auto learning process is a flow diagram of an auto learning process and is an example command knowledge base in XML format.

Referring now to according to one embodiment an auto learner framework comprises device command syntax knowledge a seed command special case handling logic a request generator and a response handler . An embodiment may implement framework in one or more computer programs or other software elements firmware or any combination thereof. Framework is coupled to or includes a knowledge base which provides a repository for storing information that defines commands that a network element supports. Framework is coupled directly or indirectly through one or more networks to network element .

In an embodiment before interacting with network element framework has information identifying a type of network element and syntax knowledge defining a general command syntax used by the network element. However framework does not have information specifying the complete command set that the network element supports. Further framework does not have information indicating whether the command set of the network element has changed recently.

Network element may comprise any network end station or infrastructure element that supports a command language for configuration or management such as a router switch wireless access point firewall etc. Thus the techniques herein apply broadly to any network end station or infrastructure element that supports such a command language for any purpose. Further in this description the term device refers broadly to any network end station or infrastructure element.

In an embodiment auto learner framework assumes that commands that a device supports conform to a certain syntax. Information defining the general syntax used for a device is stored in device command syntax knowledge . For example device command syntax knowledge defines what data types or classes of values can be used as parameters for particular commands. The syntax knowledge also defines command contexts if a particular device implements command contexts. For example certain commands cause a network element to enter a different context and subsequent commands issued in one context will produce a different result than if the same commands are issued in a different context. The syntax knowledge further defines what part of a response indicates that a command definition is complete. The use of information contained in syntax knowledge is clarified in the description below.

The seed command defines a particular device command which when sent to network element will cause network element to reply with a list of supported commands.

Special case handling logic provides program code or other software elements for handling exceptions to the general rules that are defined in syntax knowledge . Such exceptions may be the same for all devices in a family of devices or may apply only to the functionality or feature that is being learned at a particular time.

Request generator forms and sends commands or information requests to network element . Response handler processes replies that are received from the network element and creates data for storage in the knowledge base .

Referring now to in one embodiment the techniques herein use active interaction with a device to learn device commands. In one approach a command expressing a request is sent to the device as indicated by arrow . At arrow a response is received from the device the response is analyzed and information defining a learned command is stored based on the response. Further requests are sent to get more information on the command if the received response does not represent a complete definition of the command or if the response is insufficient to build complete knowledge of a command. The preceding process is repeated until all the supported commands are learned. Command syntax information is stored in a device command knowledge base is built as shown by arrow .

In step a seed command is sent. For example auto learner framework sends seed command to network element . In step a list of all supported commands for the device is received and stored. For example network element responds with information defining all commands that it supports. In one embodiment the seed command is a help or command and in response the network element provides a list of all commands that are allowed in the then current context of the network element. Routers switches and other network devices from Cisco Systems Inc. San Jose Calif. support seed commands of the type just described.

At step the process selects one command in the received list for further processing. Step represents the start of a loop that ends at step and includes steps for determining what parameters the network element requires uses or defines as part of the selected command. For example at step the process sends a request for parameters for the selected command. At step the process determines if all parameters for the request have been received based on receiving and analyzing a response from the network element as shown by step .

If not all the parameters were received for the selected command then control returns to step and further parameter requests are sent. If all parameters have been received then at step information defining the selected command is stored.

For example assume that the network element supports a command named cmd1 that requires two parameter values to be set and that the required syntax is cmd1 parameter1 value1 parameter2 value2. In one case step involves sending the request help cmd1 and in response the network element provides a complete listing of parameters and values. In another case step involves sending an incomplete command and the network element responds by providing a complete listing of parameters and values.

In yet another case step involves sending an incomplete command and a response from the network element indicates only the next parameter that the command syntax requires. For example sending a request of the form cmd1 parameter1 causes the network element to respond indicating that it needs a value of type X. The particular one of the foregoing cases applicable to a particular type of network element may vary according to the vendor of the network element the operating system or other factors. The particular one of the foregoing cases applicable to a particular type of network element may be defined in one embodiment in syntax knowledge .

Requests sent at step might require a literal value for a parameter in order to enable the process of to determine the next valid parameter for a command. In one embodiment step involves forming a command that includes valid sample values for any parameters that require specifying a value as a condition to learn the next parameter. For example to induce a response that defines additional parameters for a command relating to setting parameters on a fast Ethernet interface of a wireless access point the command must include a valid IP address for the interface. In this example step involves generating a sample Ethernet interface address to include in the command.

Some commands that some network elements support may allow an unlimited number of parameters and values. Therefore the approach of is provided with a mechanism to prevent endless loops. For example assume that at step and step the following command example and reply are sent and processed respectively 

In this case the same set of parameters and descriptions has been provided by the network element in responses for both commands identifying the community node and node. The second request included 123 as a sample node identifier value and received the same result as when the first request included community as a node identifier. Therefore sending further commands that specify additional nodes will not yield additional useful information and an unlimited list of parameter values is allowed. Therefore the process detects an endless loop and discontinues requesting parameters for the current command.

In an embodiment the presence of a recursive command that will cause an endless loop is detected as follows. First the process compares the help command result which is a list of parameter hints and descriptions for the current node s parent with the current node s help results. In this context node refers to a data structure in the knowledge base that defines and is associated with a command. If the result information is the same for both nodes then the process of considers an unlimited parameter list to exist and this is represented in the command knowledge base.

At step a test is performed to determine if all commands have been processed. If so then at step the command knowledge base is created. The command knowledge base may be structured according to any convenient text or binary format.

In one embodiment the command knowledge base is stored in Extensible Markup Language XML format according to the example schema shown in . In operation an NMS can receive parse and use such a command knowledge base.

Using the preceding general process based on basic command syntax knowledge an auto learner framework generates a series of requests and analyzes responses from a network element until all commands are completely learned.

Certain network elements and operating systems support multiple command views or contexts. For example when a particular command is executed the view or context changes and subsequent commands have different meaning or cause different results than if the same commands were executed in the prior context. The new view or context typically contains different commands than the commands allowed in the preceding view or context. Further the same commands may require different parameters in a different context or view.

In one embodiment analyzing a response at step of further involves identifying whether a context change has occurred. If a context change occurs then the process of is recursively invoked to capture all commands and parameters for the new context or view.

In one embodiment detecting a context change involves detecting when a response from a network element uses a different prompt string. In other embodiments detecting a context change may involve detecting other information in a response from a network element. The syntax knowledge may define for each supported network device or device type what information in a response from a network element indicates a context change.

Additionally or alternatively a change in context or view is identified by comparing a list of commands in a current view to a parent view. If any change in context or view occurs the process creates a new view in the knowledge base and changes the current view to the newly created view.

1. Information defining how to generate a sequence of related requests to cause a network element to reply with a complete command definition. For example such information may specify how to use help commands or the equivalent to cause the network element to provide information that defines commands.

2. Information defining how to interpret a response from a network element to determine if the command is complete if the command is incomplete and still needs some more parameters or is incorrect if the command is invalid the type of valid values that the network element expects for parameters whether a parameter is mandatory and the correct execution context for the command.

1. The command causes the device to reply with a list of valid commands for the current view or context including command name and description. An example of output in response to a command is 

2. Sending a valid command followed by the character causes the device to reply with a specification of the next parameter for the command. Example commands and reply output is 

3. Sending an invalid command causes the device to generate a response containing the string Invalid command. 

4. Sending an incomplete command causes the device to generate a response containing the string Incomplete command. 

5. When the string TOKEN appears in a response text input is required at the position indicated by TOKEN.

6. When a response includes values of the form A.B.C.D an Internet Protocol IP address is required in a valid complete command at the position indicated by A.B.C.D. 

For devices from Cisco Systems Inc. the following values of TOKEN are stored in syntax knowledge and recognized in commands IPADDRESS IPV6ADDRESS IPADDRESSMASK MASK WORD LINE FILENAME HOSTNAME MACADDRESS CHAR LOWCHAR MONTH DAY SIMPLETIME COMMUNITY VPNCOMMUNITY TIME DELAY METRIC HEXDESCR HEXDATA HEXSTRING HEXNUM APPLETALKIP NOVELLEIGRPIP VINES APOLLO. In other embodiments syntax knowledge may identify different recognized keywords or token values.

The programmable network intelligence approaches presented in this disclosure define apparatus methods mechanisms and tools to generate components required for providing programmable APIs to a device or group of devices or a network. The approaches are described herein with reference to and . is an illustration of Programmable Network Intelligence architecture. is a block diagram of a method and apparatus for generating Programmable interfaces.

Referring first to the following components are defined. A Feature Correlation Engine contains a correlation matrix of features supported by different devices and different operating system versions. A Capability Detection Engine uses the feature correlation matrix to generate device capability and command knowledge. The Capability Detection Engine builds a device capability and command knowledge base . The database contains information defining device capabilities device command intelligence such as command syntax parameter constraints and command views.

A Data Modeling Engine builds data models from the device knowledge base . In one embodiment Data Modeling Engine generates Data Model DM files in XML format. Elements of the run time environment use the DM files to transform XML requests to device native commands and vice versa. The techniques of Section 3.0 hereof may be used to generate the DM files using a predictive approach described above.

A Verification and Packaging Engine verifies the accuracy of the data model represented by a DM. The Verification and Packaging Engine also builds XML schemas based on the data model represented by the DM file. The XML schemas represented by XSD are published to users so that users can generate valid requests from applications or environments and to interpret the responses.

In one embodiment one or more Reverse Model Analyses receive DM files and apply analysis to determine if the data model accurately reflects device commands. As a result a refined DM is produced and provided to the Verification and Packaging Engine .

Referring now to in one embodiment creating programmable network intelligence begins in a development process and results in creating the runtime environment . Developer input such as information defining new hardware software platforms new software releases and new services are received at capability detection engine and data modeling engine . The capability detection engine and data modeling engine generate a runtime environment or architecture for one or more devices that provides service bundles and device packages . The service bundles encapsulate service level intelligence. The device packages encapsulate element level intelligence.

The capability detection engine and data modeling engine also generate a software development kit SDK comprising one or more programmable APIs and a runtime data model . External applications can manage devices by calling routines of the APIs with data or commands that conform to the runtime data model .

In one embodiment an API for a device is generated by walking a tree representation in the data model and automatically generating stub code containing command invocation methods that have method names matching a command name and method parameters matching names and data types of command parameters found in the data model. The APIs reflect a combination of requests defined by the IETF NETCONF standard and XSDs that are generated based on the data model. The NETCONF standard defines different types of requests to edit create delete or retrieve configuration from devices. The XSDs define the actual legal content of these requests for particular devices. The XSDs are generated using the data model.

In essence based on the feature correlation matrix and other developer input and based upon detecting what commands and a parameters are correct for a particular target network device type the approaches herein can automatically generate an abstract data model representing the features and commands of the device and generate one or more programmable APIs that applications can use to manage the device and access features or commands of the device. As a result applications gain programmatic access to devices that do not provide a native network management interface.

Computer system may be coupled via bus to a display such as a cathode ray tube CRT for displaying information to a computer user. An input device including alphanumeric and other keys is coupled to bus for communicating information and command selections to processor . Another type of user input device is cursor control such as a mouse trackball stylus or cursor direction keys for communicating direction information and command selections to processor and for controlling cursor movement on display . This input device typically has two degrees of freedom in two axes a first axis e.g. x and a second axis e.g. y that allows the device to specify positions in a plane.

The invention is related to the use of computer system for data model prediction. According to one embodiment of the invention data model prediction is provided by computer system in response to processor executing one or more sequences of one or more instructions contained in main memory . Such instructions may be read into main memory from another computer readable medium such as storage device . Execution of the sequences of instructions contained in main memory causes processor to perform the process steps described herein. In alternative embodiments hard wired circuitry may be used in place of or in combination with software instructions to implement the invention. Thus embodiments of the invention are not limited to any specific combination of hardware circuitry and software.

The term computer readable medium as used herein refers to any medium that participates in providing instructions to processor for execution. Such a medium may take many forms including but not limited to non volatile media volatile media and transmission media. Non volatile media includes for example optical or magnetic disks such as storage device . Volatile media includes dynamic memory such as main memory . Transmission media includes coaxial cables copper wire and fiber optics including the wires that comprise bus . Transmission media can also take the form of acoustic or light waves such as those generated during radio wave and infrared data communications.

Common forms of computer readable media include for example a floppy disk a flexible disk hard disk magnetic tape or any other magnetic medium a CD ROM any other optical medium punchcards papertape any other physical medium with patterns of holes a RAM a PROM and EPROM a FLASH EPROM any other memory chip or cartridge a carrier wave as described hereinafter or any other medium from which a computer can read.

Various forms of computer readable media may be involved in carrying one or more sequences of one or more instructions to processor for execution. For example the instructions may initially be carried on a magnetic disk of a remote computer. The remote computer can load the instructions into its dynamic memory and send the instructions over a telephone line using a modem. A modem local to computer system can receive the data on the telephone line and use an infrared transmitter to convert the data to an infrared signal. An infrared detector can receive the data carried in the infrared signal and appropriate circuitry can place the data on bus . Bus carries the data to main memory from which processor retrieves and executes the instructions. The instructions received by main memory may optionally be stored on storage device either before or after execution by processor .

Computer system also includes a communication interface coupled to bus . Communication interface provides a two way data communication coupling to a network link that is connected to a local network . For example communication interface may be an integrated services digital network ISDN card or a modem to provide a data communication connection to a corresponding type of telephone line. As another example communication interface may be a local area network LAN card to provide a data communication connection to a compatible LAN. Wireless links may also be implemented. In any such implementation communication interface sends and receives electrical electromagnetic or optical signals that carry digital data streams representing various types of information.

Network link typically provides data communication through one or more networks to other data devices. For example network link may provide a connection through local network to a host computer or to data equipment operated by an Internet Service Provider ISP . ISP in turn provides data communication services through the world wide packet data communication network now commonly referred to as the Internet . Local network and Internet both use electrical electromagnetic or optical signals that carry digital data streams. The signals through the various networks and the signals on network link and through communication interface which carry the digital data to and from computer system are exemplary forms of carrier waves transporting the information.

Computer system can send messages and receive data including program code through the network s network link and communication interface . In the Internet example a server might transmit a requested code for an application program through Internet ISP local network and communication interface . In accordance with the invention one such downloaded application provides for data model prediction as described herein.

The received code may be executed by processor as it is received and or stored in storage device or other non volatile storage for later execution. In this manner computer system may obtain application code in the form of a carrier wave.

In the foregoing specification the invention has been described with reference to specific embodiments thereof. It will however be evident that various modifications and changes may be made thereto without departing from the broader spirit and scope of the invention. The specification and drawings are accordingly to be regarded in an illustrative rather than a restrictive sense.

