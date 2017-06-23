---

title: Information converter and a method for transforming information
abstract: An information converter includes: an input for receiving non-structured information transformation specification and a processor. The processor is adapted to (i) convert the non-structured information transformation specification to a structured information transformation specification; (ii) generate information transformation code responsive to the structured information transformation specification; and (iii) associate a code alteration indication to the non-structured information transformation specification in response to an alteration of the information transformation code. A method and a computer readable medium converts the non-structured information transformation specification to a structured information transformation specification; generates information transformation code responsive to the structured information transformation specification, and associates a code alteration indication to the non-structured information transformation specification in response to an alteration of the information transformation code.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07721270&OS=07721270&RS=07721270
owner: Informatica Corporation
number: 07721270
owner_city: Redwood City
owner_country: US
publication_date: 20050929
---
This application claims the benefit of U.S. Provisional Application No. 60 702 889 filed Jul. 26 2005 the content of which is incorporated herein by reference.

Method and computer readable medium for transforming information and information converters and especially methods for defining information transformations using structured and non structured information translation specifications.

Specification based transformation allows business analysts information analysts or system analysts to create an executable specification of the transformation needed for EAI Enterprise Application Integration . The specification needs to be simple enough for analysts to use while still being rigorous enough to allow execution

The current state of the art is that analysts create non structured information transformation specifications using various software tools such as but not limited to Microsoft Word and Microsoft Excel .

These non structured information transformation specifications are then passed to programmers which develop code that performs the information transformation that is defined in the non structured information specification.

The code can be developed by using a unique mapping tool provided by their EAI server vendor e.g. IBM or Webmethods or by programming the code. In many cases the programmers use a mixture of mapping tools and programming.

This dual stage process usually results in inconsistencies. Typically changes to the implementation code are not reflected back to the specification s and eventually the code does not accurately represent the initial non structured specification.

There is a need to perform information transformation while maintaining a correlations between the transformation code and the non structured information transformation specification. Especially there is a need to allow both programmer and analyst to use the tools they are used to without introducing inconsistencies between the information transformation code and the non structured information transformation specification.

An information converter that includes an input for receiving non structured information transformation specification and a processor. The processor is adapted to i convert the non structured information transformation specification to a structured information transformation specification ii generate information transformation code responsive to the structured information transformation specification and iii associate a code alteration indication to the non structured information transformation specification in response to an alteration of the information transformation code.

A computer readable medium that stored code that when executed by a processor causes the computer to i convert the non structured information transformation specification to a structured information transformation specification ii generate information transformation code responsive to the structured information transformation specification and iii associate a code alteration indication in response to an alteration of the information transformation code.

A method for converting information the method includes converting a non structured information transformation specification to a structured information transformation specification generating information transformation code responsive to the structured information transformation specification and associating a code alteration indication to the non structured information transformation specification in response to an alteration of the information transformation code.

The invention allows to convert non structured information transformation specifications to information transformation code and vice verse while tracking information transformation specifications alterations and tracking information transformation code alterations.

The non structured information transformation specification can have various formats. It is typically a spreadsheet format. It can also include semi structured format. For example it can be generated using a table GUI excel software or another tool. The information transformation code can have various formats such as but not limited to ContentMaster XSLT Java C and the like.

The invention provides methods information converters and computer readable medium. According to an embodiment of the invention they can be adapted to ease the creation of the non structured information transformation specification. For example the method can include a stage of providing indications of recommended non structured information transformation specification rules. Conveniently the method can include a stage of generating non structured information transformation specification shortcuts.

Yet for another example the method can help with the selection of source and or target through various UI metaphors such as name auto completion based on the source or target schemas facilitate viewing and selecting of the source and or target as a graphical structure allow to drag and between the source and target graphical structures or between the source target and the mapping specification. The method can also ensure that simple mistakes in mapping are eliminated for example they can ensure that the source contains only legal elements from the source structure and that the target contains only legal elements from the structure

According to one embodiment of the invention the non structured information transformation specifications includes a map which describes how a value constant computed or structure is inserted into a location in the target structure. An element in a structure is described by its xpath in the source or target structure. For example an xpath can be defined as a single column in the spreadsheet that defines its location in the spreadsheet or may be divided into multiple columns which when concatenated by a defined rule may describe the location in the structure. It may also be described as the source xpath in a word document or PDF. A specification can also use a syntax natural to the specification to access information e.g. reference to a cell in a spreadsheet reference to a figure in a document .

Conveniently the structure of a map includes the following components source default value target location condition translation lookup grouping mechanism dynamic lookup table and cardinality.

The source is described by an element in the source structure or a value either static or computed . The default value can be used as the value to be placed in the target structure if the source element is null. The target location is described by an element in the source structure. A condition can include a precondition and a post condition. A precondition is evaluated on original value a post condition is evaluated on the value after translation.

The translation lookup is an expression that modifies the value either through computation or static lookup in another spreadsheet . The grouping mechanism allows mappings to be aggregate together in a group. The dynamic lookup table is based on source mechanism. It allows lookup tables to be created from value in the specifications e.g. an appendix in a document another spreadsheet .

The cardinality enables mapping a complex element to another complex element where the cardinality of the target element is different from the cardinality of the source element. The change in cardinality is indicated by this column. If the cardinality column is empty the default is First . Conveniently the possible values of a cardinality column include each first last Nth any By Key and By Function.

If the cardinality value is each then for each source element create a target element in the information. If the cardinality value is first then the process creates only a target element appropriate for the first source element in the source information. If the cardinality value is last then the process creates a target element appropriate for the last source element in the source information. If the cardinality value is Nth then the process creates a target element appropriate for the nth source element in the source information. If the cardinality value is any then the process selects a random source element and use it to create a target element.

If the cardinality value is By Key then the process maps a complex element to another complex element by a key in the input element. The number of relevant elements in the target may be equal to the number of unique input elements. For example everyone with the same department in a source element gets mapped into the same target element. The atomic unit should also contain a simple mapping row defining an element as a key.

If the cardinality value is By Function then the process Maps a complex element to another complex element as a function of the input element. The number of relevant elements in the target may be equal to the number of unique input elements as computed by the function. For example Average could be a function that returns only one new source element the one which denotes the average value. The actual function is named in the translation column.

According to various embodiments of the invention i a source value can be modified by an expression e.g. lookup table before being mapped to the target ii a basic map may be conditional on the value either the original value or after modification ii the ordering of the basic maps has no significance iii the specification allows for the description of transactional group where a failure of any map causes all of the maps in a group to fail iv the specification allows for the description of conditional groups where when a map fails the next map is executed until one mapping is successful within the group then processing of that group is complete v the specification allows for the description of iteration groups. An iteration group describes how to map a source structure with cardinality greater than one to a target structure. It allows the mapping to specify different grouping and plurality cardinality of source elements then that described by the source structure. If the map does not contain an iteration group for mapping a target structure with a target structure greater than one an algorithm is used to find the legal mapping based on source and target cardinality or a heuristic is used to find the best mapping which is validated with the user.

According to other various embodiments of the invention i the target location van include one or more columns ii the condition once evaluated may be true or fault iii a spreadsheet or structure syntax can be used to access information iv single maps or group can be named for a designation error reporting or reuse purposes v a specification may contain only a subset of a map constituent component in which case the map may be executable with only specific information instances or must be augmented by a programmer vi a simple specification should include source and target columns.

Conveniently a non structured information transformation specification that is provided as a spreadsheet typically also includes i metadata sheet describing the source XSD target XSD authors etc. ii which cleansing and enrichment algorithms are applicable to the input iii parsing sheet source description sheet iv mapping sheet and v reverse mapping sheet. Additional spreadsheets can include a serializing sheet a sequencing sheet an input examples sheet and a result sheet for testing the specified transformation and the like.

According to the various embodiments of the invention there may be provided a set of tools that ease the creation of the mapping. These tools help with the selection of source and or target through various UI metaphors such as name auto completion based on the source or target schemas allowing viewing and selection of the source and or target as a graphical structure allowing drag and between the source and target graphical structures or between the source target and the mapping specification in order to create a new map or modify an existing map. The tools can also ensure that simple mistakes in mapping are eliminated for example they can ensure that the source contains only legal elements from the source structure and that the target contains only legal elements from the structure.

According to an embodiment of the invention the structured information transformation specification has an XML format of a derivative of the XML formal such as mXML or other formats such as CAM by Oasis. Conveniently the structured information transformation specification is also referred to as scheme.

The information transformation code can be generated in various manners known in the art as well as according to various embodiments of the invention. illustrates an exemplary method while illustrates examples of a structured information transformation specification.

Conveniently the WORKSPACE element is a root element and can have the following child elements SCHEMAS FUNCTIONS RESTRICTIONS RELATIONSHIPS LOOKUPS OVERRIDES and MAPPERS.

SCHEMAS conveniently describes all schemas used in the mapping specification. Each schema is described by a SCHEMA element such as SCHEMA . SCHEMAS element can include multiple SCHEM elements such as elements and each SCHEMA element for example SCMEMA element includes a source and a name such as xs schema .

Conveniently the SCHEMA element can describe an input schema an output schema or a lookup schema. Conveniently a SCHEMA element can be specified in one of two ways i by using the SOURCE element to specify the schema URL. If the URL is a relative file path the program looks for the schema in the same directory as the input XML. The .xsd extension is optional. ii By using xs schema element to specify the schema definition inline.

An exemplary SCHEMAS element that includes three SCHEMA elements INPUT schema that is specified using SOURCE element OUPUT schema that is specified using SOURCE element and a Lookup schema that is specified inline is illustrated below 

The RESTRICTIONS element describes the schema restrictions used in a certain mapping specification. Schema restrictions are XSD elements that constraint the schema definition.

For convenience of explanation only a key type constraint xs key and unique type constraint xs unique are illustrated. It is noted that this elements is not limited to these two identity restrictions but can also include for example various restrictions and specific facets on defined restriction.

Conveniently restrictions should be specified on a schema. In practice however there are situations where restrictions are needed only for specific mapping specification. In such cases the RESTRICTIONS element should be used. Conveniently each schema restriction is described by a RESTRICTION element.

As illustrated in a RESTRICTION element includes two components i a parent path specified using XPATH element and ii a next element is an XSD definition of the restriction.

Restrictions define restrictions that are imposed on the XSD or the mapping. For example an element can be allowed to be unique only thus preventing children elements with the same values. These restrictions may result as a function of the schema the schema allows only unique elements or because of the mapping. Another restriction is key which means that you can use the value of an element to find it and its siblings subtree quickly.

RESTRICTIONS element is linked to multiple RESTRICTION elements . Each RESTRICTION element for example element is linked to an XPATH and to various elements such as key element and unique element . The key element can be linked to include limitations relating to various elements collectively denoted such as annotation selector and field elements. The unique element can be linked to include limitations relating to various elements collectively denoted such as annotation selector and field elements.

A parent element is linked to one or more OUTPUT RECORD1 elements that in turn are linked to one or more OUTPUT RECORD2 elements that are linked to one or more OUTPUT RECORD3 elements . The mapping specification requires that the OUTPUT RECORD1 elements should be grouped based on the value of a1 attribute while the OUTPUT RECORD2 elements should be grouped based on the value of a2 attribute inside OUTPUT RECORD1 elements .

This requires addition of two key schema elements one to specify the first grouping and second to specify the second grouping. The parent of the first grouping is OUTPUT RECORDS which provides the uniqueness scope for a1. The key element selector is OUTPUT RECORD1 the unique element in this grouping. The fields list contains only a1 which provides the key value. The resulting restriction is defined as follows 

The second RESTRICTION element is constructed in a similar manner. The resulting RESTRICTIONS element looks as follows 

Conveniently a LOOKUP element is contained in an XML file with path specified by the FILE element or originates from a information base with retrieval parameters specified by the DB element or is explicitly specified by in line XML. The optional DEFAULT element allows to specify the value returned by the LOOKUP function in case the input value is not found.

The ROOT element identifies a global element in the XML schema that describes the lookup XML. The schema should be defined under the SCHEMAS element.

Conveniently the schema that describes the lookup XML has at least one identity constraint key or unique defining the access key s . The identity constraint may be defined as a part of the schema or it may be defined under RESTRICTIONS element. If the lookup is defined in line then the corresponding schema conveniently has a separate target namespace and the lookup XML must use this namespace. This is to prevent possible naming conflicts.

The optional FILE element specifies where the lookup information is stored and how it is to be loaded. TABLE 7 describes the attributes of the FILE element 

The optional DB element specifies how the lookup information is stored and accessed. TABLE 8 describes the attributes of the DB element 

Assuming that the following LOOKUP TABLE is provided input values black blue brown cyan gray green pink red white and yellow should be translated to the corresponding output values schwarts blau braun turkis grau grun rosa rot weiss and gelb. This translation can be defined by a in line schema and in line defined information. The scheme is illustrated herein and is followed by the in line information definition 

It is noted that the schema contains a UniqueColor key definition and that the schema defines http www.itemfield.com Lookup1 target namespace.

The in line information definition uses an alias clr. It was created using the XMLs attribute in schema root 

A parent element GeoInformation is linked to a one or more STATE elements that are linked to one or more CITY elements the two last elements are also referred to as GeoInformation type elements .

Parent element GeoInformation is defined using multiple access keys segmented key multiple output values external files and external key definitions. It is noted that a LOOKUP function is used in calculations.

MAPPERS element is linked to one or more MAPPER element and each MAPPER element can be linked to ROOTS element OUTPUTS element and MAPPING GROUPS element . Each ROOT element can be linked to one or more ROOT element . Each OUTPUTS element can be linked to one or more OUTPUT element . A MAPPER element definition corresponds to a mapper definition in the output or to a re usable mapping definition between complex types and or complex elements.

The ROOTS element allows to identify the global elements in schemas that are used as roots of the output XMLs. The different roots may not belong to the same schema. Conveniently the first ROOT element is written to the standard result file. The rest of the ROOT elements should to be written to different output files. The OUTPUTS element is used to define the paths of these files. The correspondence to the roots is positional.

MAPPING GROUPS element is linked to one or more MappingGroupsChoice elements that in turn are linked to CONDITIONAL GROUP element TRANSACTIONAL GROUP element and ITERATION GROUP element .

Conveniently the actual children allowed under MAPPING GROUPS depend on the implementation stage as illustrated by TABLE 10 

The semantics of TRANSACTIONAL GROUP are conveniently equivalent to CONTENTMASTER GroupMapping Any failure including false result in condition evaluation in enclosed groups or maps can stop the execution of the group and unless marked with propagateFailure false the failure may be propagated to the enclosing entity.

Conveniently implementation the TRANSACTIONAL GROUP elements are translated directly into CONTENTMASTER. In later stages their content may be shuffled and additional groups added based on such criteria as optional inputs and outputs.

Conveniently in most cases there should be only one TRANSACTIONAL GROUP directly under MAPPING GROUPS and enclosing all other maps and groups. The TRANSACTIONAL GROUP element is used to enclose maps and other groups that constitute a transactional unit if one fails all should be rolled back. The value of propagateFailure should be set to false in order to allow rollback localization in case of failure. The source attribute of TRANSACTIONAL GROUP should have value if the element has been generated. The description attribute of TRANSACTIONAL GROUP should contain a short description of the group s purpose.

Conveniently another attribute can be included in this group an index that allows the map to choose a specific instance of a repeating complex structure in the source schema.

MappingGroupChoice element is linked to a CONDITIONAL GROUP element a TRANSACTIONAL GROUP element and to an ITERATION GROUP element .

Conveniently the semantics of CONDITIONAL GROUP are equivalent to CONTENTMASTER AlternativeMappings If any enclosed map or group fails the next one is executed If an enclosed map or group does not fail the rest of the maps groups are not executed. Conveniently when combined with conditions on maps these semantics provide an if then elseif else construct.

Conveniently implementation the CONDITIONAL GROUP elements are translated directly into CONTENTMASTER AlternativeMappings. In later stages their content may be shuffled and additional groups added based on such criteria as optional inputs and outputs.

Conveniently CONDITIONAL GROUP can be used in order to implement if then else if else logic. Conveniently propagateFailure should be set to false in order to perform rollback localization in case of failure. Conveniently a catch all group should be included as a last clause of CONDITIONAL GROUP. The source attribute of CONDITIONAL GROUP should have value if the element has been generated. The description attribute of CONDITIONAL GROUP should contain a short description of the group s purpose.

The ITERATION GROUP represents iteration on multiple inputs. Actions performed on each input are enclosed into a separate SOURCE GROUP. illustrates a case where multiple SOURCE GROUP elements are required. When iterating on children of INPUT RECORDS the result can be a RECORD or FIELD elements. Conveniently actions taken on RECORD are grouped into a separate SOURCE GROUP from the actions taken on FIELD.

Conveniently when an ITERATION GROUP contains only one SOURCE GROUP it is translated into a RepeatingGroupMapping object directly containing the translation of the SOURCE GROUP content. Conveniently when an ITERATION GROUP contains more than one SOURCE GROUP elements the resulting RepeatingGroupMapping object will contain AlternativeMappings with a separate GroupMapping for each source.

Conveniently propagateFailure is set to false in order to support rollback localization in case of failure. Conveniently the source attribute of SOURCE GROUP should have value if the element has been generated. Conveniently the description attribute of SOURCE GROUP should contain a short description of the group s purpose.

The DESTINATION element specifies the full XPath of the node to be created. TABLE 16 describes the attributes of the DESTINATION element 

Conveniently the mXML should contain a MAP element for each node created in output including root. The order of MAP elements is important creation of a parent should precede the creation of child. The source attribute of DESTINATION should have value if the element has been generated.

The optional VALUE element specifies the value to be assigned to the created node. In mXML this should be an expression that is specified using EXPRESSION DEF element.

The VALUE expression may be a constant or a function invocation. A special case is invocation of VALUEOF function with XPath specifying an input complex element without value. In such case the output node is created but no value is assigned.

If VALUE expression is a constant the output node is created with that value without dependence on any input. If VALUE is not specified the output node is created with no value without dependence on any input. Conveniently VALUE should include either VALUEOF or CALCULATE VALUE invocation. The source attribute of VALUE should have value if the element has been generated.

The optional CONDITION element specifies the condition for the creation of an output node. In mXML this should be a boolean MSEL expression see ContentMaster Proposed Expression Language for Mapping Specifications MSEL specified using EXPRESSION DEF element.

Conveniently conditions control output node creation only. If the node value is created using some conditional logic that logic should be implemented in the VALUE expression. For example if input value is less than or equal 100 the output value should be SMALL and if input value is greater than 100 the output value should be LARGE .

Conveniently CONDITION should contain ENSURE CONDITION invocation. CONDITION may be used in any group and not only CONDITIONAL GROUP. The source attribute of CONDITION should have value if the element has been generated

Method starts by stage of receiving a mXML specification and validating the specification stage and checking if the specification is legal note query stage error . If it is not legal stage is followed by stage of writing error messages stage to an error file .

Else if the specification is valid stage is followed by stage of loading the mXML into a semantic model and query stage of checking if the mXML specification can be loaded into an internal object model. If the answer is negative stage is followed by stage else it is followed by query stage of determining whether to validate the semantic model box or to create iterations box . The iterations involve using heuristics that help fill in a gap between what the user specifies and what he wants for example by using hints from the source or target schema to fill gaps in the mapping .

Stages and are followed by stage of determining if the internal object model includes enough information in order to proceed. If the answer is negative stage is followed by stage else it is followed by stage of translating to CONTENTMASTER. Stage is followed by stage of checking errors. If there are no errors stage is followed by stage of providing CONTENTMASTER code. Else stage is followed by stage .

Method starts by stage of converting a non structured information transformation specification to a structured information transformation specification. Referring to a non structured information transformation specification such as a spreadsheet type specification is converted to a structured information transformation specification such as mXML. This is illustrates by box that is connected via arrow sXML a simple one to one XML representation of the data in the spreadsheet to box denoted mapping via Content Master . The latter is a tool that converts sXML to mXML. Conveniently the constructs in mXML are linked back to the spreadsheet rows that generated them.

Stage is followed by stage of generating information transformation code responsive to the structured information transformation specification. Referring to box denoted Translation mXML to ContentMaster is connected by arrow mXML to box provide a code such as ContentMaster format code. Conveniently the ContentMaster constructs are linked back to the mXML which generated them.

Stage is followed by stage of altering the information transformation code. Referring to and assuming that the code can be altered by using a man machine interface tool known as ContentMaster Studio see box the ContentMaster code can be altered.

Stage is followed by stage of associating a code alteration indication to the non structured information transformation specification.

Referring to this may include boxes and . If for example the alteration is valid and can be transferred to the spreadsheet format these conditions can be checked by box than represents the ContentMaster engine that performs code verification compilations and the like and the sequence continues to box denoted reverse translation ContentMaster to mXML of performing a reverse translation from the information transformation code to a structured information transformation specification. Box is followed by box of converting the XML specification to a spreadsheet type specification. This conversion provides an altered non structured information transformation specification that represents the information transformation code alteration. The alterations can be marked in various manners.

If for example the alteration is not valid and or can not be transferred to the spreadsheet format then the sequence follows to generating an error indication translating the error to a structured information transformation specification error format box and providing error indications to the user of the spreadsheet .

Conveniently stage includes stage of performing a information transformation code to structured information transformation specification conversion to generate the code alteration indication. Referring to this is represented by stages .

Conveniently stage includes stage of performing a structured information transformation specification to a non structured information transformation specification code conversion to generate the code alteration indication.

Conveniently stage includes stage of determining if the alteration of the information transformation code can be converted to a non structured information specification conversion format. Referring to this is represented by box .

Conveniently the code alteration indication affects the non structured information transformation specification.

Conveniently the non structured information transformation specification is a spreadsheet format information transformation specification.

Conveniently method includes stage of storing versions of the information transformation code. Stage can include determining an alteration by comparing between at least two versions of the information transformation code.

Conveniently method includes stage of storing versions of the structured information transformation specification. Stage can include determining an alteration by comparing between at least two versions of the structured information transformation specification.

Conveniently method includes stage of storing versions of the non structured information transformation specification. Stage can include determining an alteration by comparing between at least two versions of the non structured information transformation specification.

Conveniently method includes stage of altering the non structured information transformation specification and attempting to generate a structured information transformation specification that represents the altered non structured information transformation specification.

Referring back to box includes translating a spreadsheet to mXML schema by ContentMaster. Conveniently The constructs in mXML schema are linked back to the spreadsheet rows that generated them. The mXML schema is transformed to code by a compiler such as a MapperBuilder. The code constructs are linked back to the mXML which generated them.

It is assumed that an analyst alters the spreadsheet and a programmer alters the code then. When the programmer changes the code the new resulting code is compared to the previous code. Changes are translated back into mXML and can show up to the analyst as a modification to spreadsheet. Conveniently the programmer can to modify the spreadsheet directly using tools such as but not limited to the ContentMaster studio development environment.

Conveniently if the code alterations cannot be translated back to mXML schema they can be added to an override object linked to the related mXML schema. The affected mXML construct is marked so that the analyst will know that there is new semantics attached to the relevant portion of the specification.

Conveniently if the analyst changes the spreadsheet the programmer modified parts of the executable not affected by those changes will not changed. This relationship between the analyst changes and previously altered code can be determined by comparing new versions and prior versions on both before and after versions of the mXML schemas and the ContentMaster code. If the changes become too difficult to track the effected part of the specification can be marked for the analyst and any changes to that portion of the specification will be marked for the requires the intervention of a programmer.

Conveniently every object in the override set is actually a new template describing how to create a more specific mapping model appropriate for this specific customer from the generic mXML schema.

Conveniently if there is a runtime or other error the error is linked to the appropriate construct in the ContentMaster code which is translated to the appropriate construct in the mXML intermediate model it can be displayed to the analyst by translating the mXML construct back to the spreadsheet construct which defined it.

The following example will further illustrates the translation from code alteration to specification alteration. It is assumed that an analyst creates the specifications of the transformations needed for two applications to interchange real time data. Method or at least some of its stages convert the specification to code. The analyst can be responsible to this transformation. It is further assumed that a scripter can augment the executable script created by the analyst if needed. Usually the scripter or programmer handles the hard problems or extreme cases. The scripter needs to make sure that any changes do not conflict with the correctness as defined by the analyst.

Methods and try to ensure that the specification created by analyst and the script reflect each other. The Analysts needs to be able to vet the changes made to a specification s implementation by the Scripter.

It is further assumed that that there is a Script Generator or some equivalent stages of either one of methods or that can take a specification and create an equivalent script. There also exists a Specification Generator or some equivalent stages of either one of methods or that can take a script and in most case generate a specification. If the specification generator cannot create an equivalent spec then there is a mechanism such as via a remark that can be used to notify the analyst of the information missing from the formal part of the specification. If the script created is relevant to a specific part of the specification created by the analyst that part of the spec is made read only so that the analyst understands that changing that part of the spec requires the intervention of a scripter. The goal is to keep such dead specs to a minimum.

For a mapping specification created in Excel it is assumed that for the most part there is no meaning to the order of the rows unless specifically required by the analyst.

The first example assumes that the analyst modified the specification for example Excel specification and that the script was correct before this modification.

The alteration is followed by a stage of using the script generator to create SCRIPTfrom the specification referred to as SPEC . SCRIPTalso includes the appropriate back references from the SPEC that caused the script objects to be generated.

The next stage includes using the specification generator on SCRIPTto create SPEC. SPECincludes the appropriate back references to SCRIPTobjects that generated the SPECobjects.

Then the specification generator generates SPECfrom SCRIPT with the appropriate back references to the SCRIPT objects which generated the SPECobjects.

The following stage includes useing the script generator to generate SCRIPTfrom SPEC again with the appropriate back references to the objects which generated the SPECobjects . It is noted that SCRIPTis used for as a control comparison and filtering.

The next stage includes finding the most closely related rows in SPECand SPEC. This stage is followed by linking SCRIPTobjects to their related SCRIPT objects this is based on the simple linkages of the basic relationships between simple script objects and heuristics that take into account how the script is used to group objects. This gives the basis to understand the changes in specification and how they should effect the script.

Accordingly there are 3 main entities that used to synchronize the changes i SCRIPT the source for user changes ii SCRIPT the basis for filtering and finding changes that need to propagated and iii SCRIPT the target for the changes. The changes are merged into SCRIPT in order to provide the new modified script.

It is noted that if SCRIPTobject property equals SCRIPTobject property then there is no change to SCRIPT. If SCRIPTobject property equals SCRIPTobject property then the SCRIPT should be updated with the change. If SCRIPTobject property doesn t exist as an SCRIPTobject property in then the SCRIPT should be updated with the new script object. If SCRIPTobject property doesn t exist in SCRIPTas an object property then the object should be deleted from SCRIPT.

Information converter includes an input for receiving non structured information transformation specification and a processor . The processor is adapted to i convert the non structured information transformation specification to a structured information transformation specification ii generate information transformation code responsive to the structured information transformation specification altering the information transformation code and iii associate a code alteration indication to the non structured information transformation specification.

It is noted that information converter can include memory units such as memory for storing the various structured information transformation specifications and or non structured information transformation specifications information transformation code information transformation generating code.

Information converter also include one or more displays in order to display to the analyzer and programmer various information and to allow alterations of the information transformation code non structured information transformation code and the like.

Information converter can have a distributed architecture a centralized architecture and the like. It usually include various software components hardware components and the like. It may include or be adapted to read or otherwise access a computer readable medium that includes code that when executed by the processor causes the information converter to i converting the non structured information transformation specification to a structured information transformation specification ii generate information transformation code responsive to the structured information transformation specification altering the information transformation code and iii associate a code alteration indication to the non structured information transformation specification.

The present invention can be practiced by employing conventional tools methodology and components. Accordingly the details of such tools component and methodology are not set forth herein in detail. In the previous descriptions numerous specific details such as a certain compression standard are set forth in order to provide a thorough understanding of the present invention. However it should be recognized that the present invention might be practiced without resorting to the details specifically set forth.

Only exemplary embodiments of the present invention and but a few examples of its versatility are shown and described in the present disclosure. It is to be understood that the present invention is capable of use in various other combinations and environments and is capable of changes or modifications within the scope of the inventive concept as expressed herein.

The following examples show the mapping specification that uses the information for lookup. The specification takes a list of pairs as input and produces for each city its area and population as percentage of corresponding state value 

It is noted that the schema and information are defined in external files. Accordingly there is no need to add a separate namespace. The key definitions are under the RESTRICTIONS element and not in the schema. Multiple keys are defined on the same information and used in separate calls to LOOKUP function. Values returned by the LOOKUP function are used in calculation.

