---

title: Template driven type and mode conversion
abstract: Techniques for providing type (and/or mode) conversion of parameters for software applications are provided. In general, a type conversion utility accesses a template that defines type and mode conversions for parameters between different components. The type conversion utility utilizes information stored in the template for that direct how the parameters will be converted. Additionally, techniques are provided for returning output values.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07860894&OS=07860894&RS=07860894
owner: Oracle International Corporation
number: 07860894
owner_city: Redwood Shores
owner_country: US
publication_date: 20050511
---
This application claims priority to U.S. Provisional Application 60 570 344 filed May 12 2004 which is hereby incorporated by reference for all purposes.

The present invention relates to computer systems. More specifically the invention relates to providing template driven type and mode conversion for parameters in software applications.

Soon after the development of programming languages for computers the concept of modular programming was developed. Modular programming encourages designing and writing programs as interactions among functions where each performs a single well defined function.

For example a call is made to a function. The function call typically specifies one or more parameters or arguments . Each parameter has a specified type which defines the meaning of the value of the parameter. The one or more bits passed in as a parameter are interpreted according to the format specified by the type e.g. integer floating point string . In modern programming languages there are a myriad of different types specified by standards but the type refers to the format that should be utilized to give the bits meaning and therefore their value.

Parameters can also have different modes. The mode defines the relationship of the parameter between the caller and the callee or function . For example an in parameter is a parameter that is an input to the function. Even if the function modifies the parameter during execution the modification will not affect the parameter from the caller s end.

An out parameter is a parameter that is an output of the function. Typically the caller provides a pointer to a memory location e.g. address and the function writes the return value at that location. As with in parameters the format of the parameter is specified by the type. Lastly an in out parameter is one that is both an input and an output.

The above describes the basic initial concepts but it may be beneficial to describe a typical more complex application. shows a database environment that uses different interfaces between components. A database includes the hardware and software for performing among other things database queries. A Java virtual machine executes computer programs that can interact with database .

As shown Java Database Connectivity JDBC provides Application Programming Interfaces APIs for Java that supports Structure Query Language SQL commands to database . Additionally SQLJ can be utilized to embed SQL statements in Java source code that interacts with JDBC. As is known the APIs for JDBC have a defined call structure including parameter types and modes.

As shown web services of a web server communicates with Java virtual machine utilizing Apache web service types and modes. Extensible Markup Language XML is utilized to communicate input and output to web services as specified by XML schemas.

Database may have stored procedures that it would be desirable to access from web services . However there may be call mismatches such as parameter type and mode that make this difficult. For example the Oracle database system has stored procedures written in Procedural Language extensions to SQL PL SQL which is different than web service types such as XML values used by Apache. A conversion may need to be performed in order to allow calls from web services to stored procedures in database .

Additionally PL SQL supports parameters of in out and in out. However JDBC that provides calling mechanisms to database sends a copy of each parameter. If the parameter is modified a copy of the modified parameter is returned. Thus the before and after values of the parameter appear in separate objects. This creates a mode inconsistency between these parameters.

One solution is for the programmer to manually write Java classes in order to allow access or publish to the stored procedures in database by web services . Unfortunately this solution is very time consuming and prone to errors.

A utility know as JPublisher has been developed by Oracle Corporation in order to among other things facilitate accessing SQL objects and PL SQL in database . Although JPublisher has met with extreme success interfaces to PL SQL procedures are still manually created in many cases because the data types used by JDBC and the way in which out or in out arguments are treated necessitates writing code by hand to match the intended usage.

Accordingly it would be beneficial to have innovative techniques automatically publishing stored procedures of a database for use by other applications. Additionally it would be beneficial to provide type and mode conversions where desired.

The present invention provides innovative techniques for providing type and or mode conversion of parameters for software applications. In general a type conversion utility accesses a template that defines type and mode conversions for parameters. The type conversion utility utilizes information stored in the template that direct how the parameters will be converted. This provides great flexibility in publishing procedures and can be done efficiently as the manual writing code for this purpose is not necessary. The main use of the application is in the type and mode conversions between different models for desired type and mode representations. It encompasses different models between different programming languages as well as different models of type and mode mapping in the same programming language. Some specific embodiments of the invention are described below.

In one embodiment the invention provides a method of converting types of parameters between two applications utilizing different types. A first type is received for a parameter from a first application to be sent to a second application utilizing different types. A template is retrieved that specifies a conversion of the first type to a second type for the second application. The first type is converted to the second type as specified in the template and the parameter is passed to the second application as the second type. In addition a returned data type can be converted as specified in the template.

In another embodiment the invention provides a method of returning an output value as a parameter. An array is declared and a before value of a parameter is assigned to an element of the array. The array is passed to a wrapper method. An underlying method of the wrapper method is then executed. An after value of the parameter is assigned to an element of the array. Lastly the after value of the parameter is extracted from the array.

An embodiment of the invention in the JPublisher product utilizes this template driven mechanism to create Java language sources that implement an API for invoking stored procedures running in an Oracle database and implemented in PL SQL. The advantage of the template mechanism lies in the fact that different mode and type models can be mapped simply and quickly by switching modifying or extending the template. This invention is not limited to a particular programming language to particular type models or to particular models for representing modes.

Other features and advantages of the invention will become readily apparent upon review of the following description and association with the accompanying drawings where the same or similar structures are designated with the same reference numerals.

In the description that follows the present invention will be described in reference to embodiments that provide template driven type and mode conversion for software applications. Additionally embodiments will be described in terms of a three tiered database architecture such as is available from Oracle Corporation Redwood Shores Calif. However embodiments of the invention are not limited to any particular architecture language environment application or implementation. For example although some embodiments utilize stored procedures in specific languages the invention can be advantageously applied to any programming language or environment. Therefore the description of the embodiments that follows is for purposes of illustration and not limitation.

A fairly common database management system architecture is the three tiered architecture that is shown in . At the core of the database management system is a central storage that stores a database . Database is typically stored on one or more hard drives which is typically part of a larger computer system. The information can be stored on database in a variety of formats with relational database management systems relying heavily on tables to store the information.

Database servers are instances of a program that interacts with database . Each instance of the database server can among other things independently query database and store information therein. Database servers may not include user friendly interfaces to access database . Database and database servers comprise the lowest tier of the hierarchy.

One or more application server can provide the user interfaces to database server . For example application server can be a web application server on the Internet or other network . Application server can accept commands from users for accessing database through database server . As an example application server can be an SQL server. Thus application server is in the middle tier of the hierarchy.

Although application server can accept user commands a web browser or other client application can be utilized to access application server through a user friendly interface. Web browser is an example of an application in the highest tier in the hierarchy.

A fixed storage can store computer programs and data such that it is typically persistent and provides more storage when compared to memory . At present a common fixed storage for databases is multiple e.g. arrays hard drives. A removable storage provides mobility to computer programs and or data that are stored thereon. Examples of removable storage are floppy disks tape CD ROM flash memory devices and the like.

Memory fixed storage and removable storage provide examples of computer readable storage media that can be utilized to store and retrieve computer programs incorporating computer codes that implement the invention data for use with the invention and the like. An input allows a user to interface with the system. Input can be done through the use of a keyboard a mouse buttons dials or any other input mechanism. An output allows the system to provide output to the user. Output can be provided through a monitor display screen LEDs printer or any other output mechanism.

A network interface allows the system to interface with a network to which it is connected. The system bus architecture of computer system is represented by arrows . The components shown in can be found in many computer systems. However components can be added deleted and combined. For example fixed storage could be a file server that is accessed through a network connection. Thus is for illustration purposes and not limitation.

Now that exemplary database applications and environments have been described it may be beneficial to discuss embodiments of the invention. Although specific embodiments are described features can be added and combined without departing from the spirit and scope of the invention. For example features from more than one of the embodiments can be advantageously implemented in other embodiments.

Embodiments of the invention can convert simultaneously both modes of parameters between two different models of representing modes as well as types of parameters between two different models of representing types. The outer function will refer to the function that utilizes the first or outer parameter type and mode model. The inner function will refer to the function that utilizes the second or inner parameter type and mode model. A template is used for driving the automatic creation of an application that implements the outer function and that in turn invokes the inner function.

The following describes the principles for conversion between parameter types in the first outer model and parameter types in the second inner model. For every parameter type or possibly sets of parameter types in the outer model the template includes among others definitions of the following 

In one embodiment of the invention the inner parameter mode model utilizes arrays to represent out or in out values. In that particular embodiment the inner parameter mode and type model may for example utilize a particular style of Java code generated for invoking PL SQL stored procedures in an Oracle database via JDBC.

Although shows both a type and mode conversion embodiments can implement type or mode conversion. The following will describe different variants of the steps of in more detail.

A first variant of step is described herein. The following description of the template driven conversion process of will be common when the inner parameter mode utilizes arrays to represent out or in out values. For parameters with out or in out modes a one element array of type array parameter type of inner type model is declared. For parameters with in modes a variable of type parameter type of inner type model is declared instead. The outer to inner conversion expression is constructed as follows 

A second variant of step is described herein. The following description of the template driven conversion process will be common when the inner parameter mode utilizes holders to represent out or in out values. For parameters with out or in out modes a corresponding holder instance of parameter type of inner type model is defined. If the holder type of parameter type of inner type model is neither predefined nor previously defined then define it. For parameters with in modes a variable of type parameter type of inner type model is declared instead. The outer to inner conversion expression is constructed as follows 

A third variant of step is described herein. The following description of the template driven conversion process will be common when the inner parameter mode utilizes a compound return type to represent out and in out values as well as a return value if any . For parameters with out or in out modes and for the return value a corresponding compound type is declared. This compound type holds instances fields attributes for each out and in out parameter is of type parameter type of inner type model. If the inner function returns a value then this compound type also holds an instance for the return value of type return type of inner type model. Typically the names of the instances attributes fields of this compound type could be derived from the parameter names. For parameters with in modes and for parameters with in out modes a variable of type parameter type of inner type model is declared. The outer to inner conversion expression is constructed as follows 

At step the inner to outer conversion expression for all out and in out parameters and the return if any of the inner method is constructed similarly to what was described earlier. This time the inner placeholder in the inner to outer conversion expression is replaced by the after value. The after value is obtained as follows. In the particular case where the inner parameter mode uses one element arrays to represent out and in out arguments the after value is obtained by accessing the first element of the array. In the particular case where the inner parameter mode uses holders to represent out and in out arguments the after value is obtained by retrieving the underlying value in the holder. In both of these cases the return value if any is directly retrieved from the invoked function. In the case where the inner parameter mode uses the return value to represent out and in out arguments a structured type with components consisting of an attribute for the return value if any and an attribute each for all out and in out parameter values would be returned and the after value is obtained by accessing the specific return or parameter attribute.

As shown Java Database Connectivity JDBC provides Application Programming Interfaces APIs for Java that supports Structure Query Language SQL commands to database . Additionally SQLJ can be utilized to embed SQL statements in Java source code that interacts with JDBC. As is know the APIs for JDBC have a defined call structure including parameter types and modes.

Web services of a web server communicate with Java virtual machine and XML is utilized to communicate input and output to web services as specified by XML schemas.

A type conversion utility is responsible for performing type and or mode conversions of parameters as specified by a template . As will be described below there may be multiple templates but one is shown for simplicity.

Type conversion utility can be written in the Java programming language and therefore interact with Java virtual machine . However the type conversion utility can be implemented in any programming language. Template specifies among other things mappings between source types and target types. Additionally template can include computer code for performing actions for the conversion where desired.

Thus stored procedures on database may be conveniently published through wrapper methods a wrapper method wraps an underlying method and may include computer code before and or after the call to the underlying method by specifying type conversions for the stored procedures in template . As web services access the stored procedures through the wrapper methods type conversion is provided as specified in template .

At a step a first type for a parameter from a first application is received. The parameter is to be sent to a second application that utilizes different types than the first application. A template is retrieved that specifies a conversion of the first type to a second type for the second application at a step . The template can specify mappings from source types to target types.

The first type is converted to the second type as specified in the template at a step . At a step the parameter is passed to the second application as the second type. Although the flowchart in is directed to type conversions a similar process can be performed for mode conversions which can also be specified in a template.

After the second application finishes the return data from the second application if any and if necessary is converted to a type that is supported by the first application. Such mapping from the target type to the source type is also defined in the template.

An embodiment of the invention can be implemented in the JPublisher utility from Oracle Corporation that uses the Oracle SQLJ SQL in Java implementation generating SQLJ code as an intermediate step in most circumstances whenever wrapper methods are created either for classes representing PL SQL packages or for classes representing SQL object types that define methods PL SQL stored procedures . In these circumstances JPublisher uses the Oracle SQLJ translator during compilation and the Oracle SQLJ runtime during program execution. In addition to mapping SQL objects the entire PL SQL packages can be encapsulated as Java classes. JPublisher offers functionality to create Java wrapper methods for the stored procedures of a PL SQL package.

The concept of representing PL SQL stored procedures as Java methods can present problems however. Arguments to such functions or procedures may use the PL SQL mode out or in out but there are no equivalent modes for passing arguments in Java. A method that takes an int argument for example is not able to modify this argument in such a way that its callers can receive a new value for it.

In one embodiment JPublisher generates single element arrays for out and in out arguments. For an array int abc for example the input value is provided in abc 0 and the modified output value is also returned in abc 0 . JPublisher also uses a similar pattern when generating code for SQL object type methods.

To publish database entities JPublisher connects to the database and retrieves descriptions of SQL types PL SQL packages or server side Java classes that can be specified on the command line or in an INPUT file.

JPublisher generates a Java class for each SQL type or PL SQL package that it translates and each server side Java class that it processes. Generated classes include code required to read objects from and write objects to the database. When a wrapper method on an instance of a class that was generated for a SQL object is called the SQL value for the corresponding object is sent to the server along with any in or in out arguments. Then the underlying method stored procedure or function is invoked and the new object value is returned to the client along with any out or in out arguments.

The JPublisher code that is generated is in terms of parameter types and modes are the inner parameter type and mode methods. The generated Java code typically ends up with a different type and or mode model than the code that is desired by the user which are the outer parameter and mode methods. Embodiments of the invention allow efficient translation between these two when desired.

JPublisher style files allow Java to Java type mappings to be specified. This is to ensure for example that generated classes can be used in Web services. As a particular example CLOB types such as java.sql.Clob and oracle.sql.CLOB cannot be used in Web services but the data can be used if converted to a type such as java.lang.String that is supported by Web services.

Typically templates or style files are provided by Oracle but there may be situations in which a user would want to edit or create her own. The key portion of a style file is the TRANSFORMATION section everything between the TRANSFORMATION tag and END TRANSFORMATION tag. This section describes type transformations Java to Java mappings to be applied to types used for object attributes or in method signatures.

For convenience there is also an OPTIONS section in which any other JPublisher option settings can be specified. In this way a style file can replace the functionality of any other JPublisher properties file in addition to specifying mappings.

This Style File TRANSFORMATION Section provides a template for a style file TRANSFORMATION section with comments. Within the TRANSFORMATION section there is a MAPPING section from a MAPPING tag to an END MAPPING tag for each mapping that is specified. Each MAPPING section includes a number of subtags with additional information. SOURCETYPE and TARGETTYPE subtags are required. Within each TARGETTYPE section information for at least the RETURN IN and OUT cases using the corresponding tags should be specified.

Below is a high level outline of the template format and of the various pieces of information that can be supplied in the template.

The details about templates or style files are provided to illustrate an exemplary embodiment. Other embodiments may utilize different templates so the invention is not limited to the embodiments described herein.

By using a template mechanism the JPublisher product can easily be adapted to generate code for different platforms 

For convenience in the concrete JPublisher embodiment templates can include other templates using an INCLUDE directive. For example webservices common.properties is used by webservices.properties and webservices.properties. Additionally via the OPTIONS section the templates in the concrete JPublisher embodiment are enabled to provide directives into JPublisher such as the style for the representation of out and in out arguments. For example jpub.outarguments return specifies that out in out and return values be represented through a compound return type in the outer method representation.

The TRANSFORMATION section consist of a sequence of MAPPING directives that map between SOURCETYPE described as the outer parameter or return type in the rest of this document and the TARGETTYPE described as the inner parameter or return type in the rest of this document . In some cases it need only be noted that a particular predefined HOLDER is to be employed. In some cases patterns are employed to define whole families of conversions. A pattern may for example use p to correspond to the package name and c to correspond to the class name.

If the identity constitutes the conversion function then no conversion expressions need to be defined. Otherwise the code fragment between IN and END IN defines the conversion from the outer type to the inner type where the placeholders 1 and 2 stand in for instances of outer and respectively inner types that may be appropriately replaced with expressions or variables depending on the concrete type and mode representation in effect.

Conversely code fragments between OUT and END OUT define conversion expressions in the opposite directions from an inner type to a corresponding outer type. Again placeholders 1 and 2 stand in for instances of the outer type and respectively for the inner type.

Additional facilities used in the concrete embodiment of the template driven type and mode conversion in the JPublisher product are as follows 

The DEFAULT HOLDER segment provides a generic definition of holder classes as well as code fragments that define how values are inserted into or extracted from the generated holder class in the various cases that we have described.

In the following we provide additional details on the template driven type and mode conversion as embodied in JPublisher.

The Oracle style files webservices common.properties webservices.properties and webservices.properties through their SOURCETYPE and TARGETTYPE specifications have a number of important Java to Java type mappings to support Web services and mappings of REF CURSORs.

The webservices and webservices files include webservices common before specifying their own mappings. For SimpleXMLType note that DocumentFragment overrides String if style webservices is set and Source overrides String if style webservices is set.

JPublisher allows multiple style options in the command line. The OPTIONS sections are concatenated and the TRANSFORMATION sections are concatenated except entries in MAPPING subsections are overridden as applicable. A MAPPING entry from a style file specified later in the command line overrides a MAPPING entry with the same SOURCETYPE specification from a style file specified earlier in the command line.

This functionality is useful if it is desirable to overwrite earlier defined type mappings or add new type mappings. For example if to map SYS.XMLTYPE into java.lang.String the setting style xml2string can be appended to the JPublisher command line assuming for this example that this will access the style file . xml2string.properties which is defined as follows 

Stored procedures called through JDBC do not have the same parameter passing behavior as ordinary Java methods. This affects the code that is written that calls a wrapper method that JPublisher generates.

When ordinary Java methods are called parameters that are Java objects are passed as object references. The method can modify the object. By contrast when a stored procedure through JDBC is called a copy of each parameter is passed to the stored procedure. If the procedure modifies any parameters copies of the modified parameters are returned to the caller. Therefore the before and after values of a modified parameter appear in separate objects.

A wrapper method that JPublisher generates contains JDBC statements to call the corresponding stored procedure. The parameters to the stored procedure as declared in the CREATE TYPE or CREATE PACKAGE declaration have three possible parameter modes IN OUT or IN OUT. Parameters that are IN OUT or OUT are returned to the wrapper method in newly created objects. These new values must be returned to the caller somehow but assignment to the formal parameter within the wrapper method does not affect the actual parameter visible to the caller.

In Java there are no OUT or IN OUT designations but values can be returned through holders. In JPublisher one of three alternatives for holders that handle PL SQL OUT or IN OUT parameters can be utilized arrays JAX RPC holder types and function returns.

The simplest way to solve the problem of returning output values in Java is to pass an OUT or IN OUT parameter to the wrapper method in a single element array. Think of the array as a container that holds the parameter.

The before value of the parameter is assigned to the first element of the array show as Array 0 . A call is then made to the wrapper method passing the array as a parameter. The wrapper method then makes a JDBC call to the stored procedures passing the first element of the array as a parameter.

After the database stored procedure executes the wrapper method assigns the after value of the parameter to the first element of the array. In this way the after value is extracted from the array. The array is then returned to the web service as the output parameter.

A setting of outarguments array the default instructs JPublisher to use this single element array mechanism to publish any OUT or IN OUT argument.

Assume that x is an instance of a JPublisher generated class that has the method f which is a wrapper method for a stored procedure that uses a SQL PERSON object as an IN OUT parameter. The type PERSON maps to the Java class Person p is a Person instance and pa is a single element Person array.

Although shows an array data structure array that can be used for passing parameters or return values other data structures can also be utilized. For example holders and compound types can be utilized in other embodiments.

The before value of the parameter is assigned to the first element of the array. Although in some embodiments the parameter is assigned to the first element the parameter can be assigned to any element in the array so long as the location is known. For example an array could store values for multiple parameters that were of the same type.

At a step the array is passed to a wrapper method. The wrapper method wraps an underlying method and includes a call to the underlying method. The underlying method is executed at a step .

After the underlying method is executed the after value is assigned to the first element or a known element of the array. This is performed in the wrapper method. Upon returning from the wrapper method the after value is extracted from the array at a step .

The array technique for passing OUT or IN OUT parameters may require the addition of a few extra lines of code to the program for each parameter. As another example consider the PL SQL function created by the following SQL Plus command 

SQL create or replace function g a0 number a1 out number a2 in out number a3 clob a4 out clob a5 in out clob return clob is begin return null end 

Problems similar to those described earlier arise when the this object of an instance method is modified.

The this object is an additional parameter passed in a different way. Its mode as declared in the CREATE TYPE statement may be IN or IN OUT. If the mode of this is not explicitly declared its mode is IN OUT if the stored procedure does not return a result or IN if it does.

If the mode of the this object is IN OUT then the wrapper method should return the new value of this. The code generated by JPublisher implements this functionality in different ways depending on the situation 

For a stored procedure that does not return a result the new value of this is returned as the result of the wrapper method. As an example assume that the SQL object type MYTYPE has the following member procedure 

Also assume that JPublisher generates a corresponding Java class MyJavaType. This class defines the following method 

For a stored function a stored procedure that returns a result the wrapper method returns the result of the stored function as its result. The new value of this is returned in a single element array passed as an extra argument the last argument to the wrapper method.

The f2 method returns the VARCHAR2 function return as a Java string and returns the modified this object value as an array element in the MyJavaType array.

For PL SQL static procedures or functions Jpublisher generates instance methods not static methods in the wrapper class. This is the logistic for associating a database connection with each wrapper class instance. The connection instance is used in initializing the wrapper class instance so that it is not required to subsequently explicitly provide a connection or connection context instance when calling wrapper methods.

The JAX RPC specification explicitly specifies holder classes in the javax.xml.rpc.holders package for the Java mapping of simple XML data types and other types. Typically Holder is appended to the type name for the holder class name. For example BigDecimalHolder is the holder class for BigDecimal.

Given a setting of outarguments holder JPublisher uses holder instances to publish OUT and IN OUT arguments from stored procedures. Holder settings are specified in a JPublisher style file in the HOLDER subtag inside the TARGETTYPE section for the appropriate mapping. If no holder class is specified then Jpublisher can choose one according to defaults.

SQL create or replace function g a0 number a1 out number a2 in out number a3 clob a4 out clob a5 in out clob return clob is begin return null end 

With outarguments holder the following is an example of how the function is published. In this case there is an extra level of abstraction because oracle.sql.CLOB is not supported by Web services it is mapped to String the JAX RPC holder class for which is StringHolder.

Assume the following JPublisher command to publish the function g. The webservices style file contains an entry for outarguments holder. 

The setting outarguments return can be used as a workaround for supporting method signatures in Web services that do not use JAX RPC holder types or arrays. In a situation in which there is no support for JAX RPC holders the outarguments return setting allows OUT or IN OUT data to be returned in function results.

SQL create or replace function g a0 number a1 out number a2 in out number a3 clob a4 out clob a5 in out clob return clob is begin return null end 

Assume the following JPublisher command a wraparound command with output also shown to publish the function g. Although the webservices style file specifies outarguments holder the outarguments return setting comes after the style setting so takes precedence.

The JPublisher output acknowledges that it is processing the SCOTT top level and also indicates the creation of the Java class ToplevelGUser g Out to support output values of the function g through return data.

The return type ToplevelGUser g Out encapsulates the values of the OUT and IN OUT parameters to be passed back to the caller of the function. As in the preceding section oracle.sql.CLOB is mapped to String by the webservices style file.

JPublisher style files enable Java to Java type mappings to be specified in some embodiments. A typical use for such mappings is to ensure that generated classes can be used in Web services. As a particular example CLOB types such as java.sql.Clob and oracle.sql.CLOB cannot be used in Web services. However the data can be used if converted to a type such as java.lang.String that is supported by Web services.

If the JPublisher style option is used to specify a style file JPublisher generates subclasses that implement the Java to Java type mappings specified in the style file. This includes the use of holder classes for handling output arguments data corresponding to PL SQL OUT or IN OUT types.

This command uses the style file webservices.properties for Java to Java type mappings. This style file is supplied by Oracle and is typically appropriate for using Web services in an Oracle Database 10g environment. The webservices.properties file specifies the following among other things 

The mapping of the Java type oracle.sql.SimpleXMLType which is not supported by Web services to the Java type javax.xml.transform.Source which is 

This setting directs JPublisher to use instances of the appropriate holder class in this case javax.xml.rpc.holders.SourceHolder for the PL SQL output argument of type XMLTYPE.

Based on the s foo pack FooPack specification to JPublisher the genpattern setting results in generation of the interface FooPack the base class FooPackBase and the user subclass FooPackUser which extends FooPackBase and implements FooPack.

The mapping of the Java type oracle.sql.CLOB which is not supported by Web services to the Java type java.lang.String which is 

The base class generated by JPublisher FooPackBase has the following corresponding method declaration 

This is because of the specified mapping of oracle.sql.SimpleXMLType to javax.xml.transform.Source the specified use of holder classes for output arguments and the specified mapping of oracle.sql.CLOB to java.lang.String all as described earlier .

Generated user subclasses employ the following general functionality for Java to Java type transformations in the wrapper method 

1. It retrieves a Source object from the SourceHolder object that is passed in to the foo method data input .

2. After processing which occurs inside the type conversion layer it assigns the SourceHolder object from the Source object that was retrieved and processed data output .

The type conversion layer first takes the target type TARGETTYPE from the style file next converts it to the source type SOURCETYPE from the style file then calls the corresponding method in the base class which uses JDBC to invoke the wrapped stored function and finally converts the source type returned by the base class method back into the target type to return to the holder layer.

3. It passes the SimpleXMLType object to the  foo method of the base class which uses JDBC to invoke the foo stored function.

4. It takes the SimpleXMLType object returned by the  foo method output from the foo stored function .

While the above is a complete description of preferred embodiments of the invention various alternatives modifications and equivalents can be used. It should be evident that the invention is equally applicable by making appropriate modifications to the embodiments described above. For example although properties of specific embodiments have been described embodiments of the invention are not limited to these properties. Therefore the above description should not be taken as limiting the scope of the invention that is defined by the metes and bounds of the appended claims along with their full scope of equivalents.

