---

title: Method to generate scripts from XML
abstract: An XML document can use tags such that scripts can be generated from the documents. The scripts can be start up scripts for different operating systems. For example, the same XML document can be used to produce a UNIX shell script as well as a Windows command file.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07703005&OS=07703005&RS=07703005
owner: BEA Systems, Inc.
number: 07703005
owner_city: Redwood Shores
owner_country: US
publication_date: 20050517
---
This application claims priority to U.S. Provisional Application No. 60 573 270 entitled Method to Generate Scripts from XML filed May 21 2004.

The present invention consists of interpreting tags and information in an XML document to produce a server start script for an operating system the XML document includes tags which are defined to indicate information such that the XML document can be used to produce server start scripts for multiple types of operating systems and storing the produced server start script in memory.

In one embodiment of the present invention tags and information in an eXtensible Markup Language XML document are interpreted to produce a server start script such as scripts and for an operating system. The XML document includes tags which are defined to indicate information so that the XML document can be used to produce server start scripts for multiple types of operating systems. Examples of XML tags and constructed script formats of one example is given below in the Script Generator Specification section. The produced server start script such as scripts and can be stored in memory.

The server start scripts can include UNIX shell scripts WINDOWS command files and other operating system scripts . A graphical user interface can be used to produce the XML document. Details of a graphical user interface of one embodiment are described below with respect to . The graphical user interface can be used to select the script type. WINDOWS and UNIX are operating systems.

The XML document can be merged with an extension XML document to produce a merged XML document from which the script is produced. The extension XML document can include tags defined for merging XML documents. Such tags can include marker tags append tags and replace tags.

An Application Programming Interface API can be used to create the scripts and or XML documents. The API allows users to design software that allows for the construction of the scripts and or XML files.

In one embodiment the graphical interface is used to produce an intermediate representation such as XML document . The intermediate representation can be such that it can be used to produce server start scripts and for multiple types of operating systems. The intermediate representation can be stored in memory.

The graphical user interface can allow the dragging and dropping of elements for the construction of the XML document. The graphical user interface can include selectable elements for the construction of the XML documents. The selectable elements can be selectable from a menu of the graphical user interface. The graphical user interface can allow the selection of the script for the correct operating system.

The construction of scripts from the XML can be automated by defining the XML tag structure i.e. e.g. the document type definition DTD or XML schema such that the XML document is sufficient to produce each type of script desired to be produced. In the script generator specification example given below the XML document structure is such that both a WINDOWS command file script and a UNIX shell script can be produced. The tags are used to identify information that can be plugged into the scripts automatically.

For example as shown below in the script generator specification example XML for the IF THEN statements can look as follows 

The and tags indicate the whole if then section. The and tags indicates the test to be done. The type is a variable to indicate the type of test. The and tags indicate the command or commands to execute if the test is true and the and tags indicate the command or commands to execute if the test is true.

For example if the type is string not is false and the case is false script for checking if one string equals another string is given by if string1 string2 command else expression for a WINDOWS command file and if string1 string2 then else for a UNIX shell script Where string1 is obtained from op1 and string2 is obtained from op2 .

The script generator specification example below is merely one non limiting example of a specification of the script generator. A number of different representations for the XML can also be used as long as the desired types of constructed scripts can be produced.

One embodiment includes a computer program product which is a storage medium media having instructions stored thereon in which can be used to program a computer to perform any of the features presented herein. The storage medium can include but is not limited to any type of disk including floppy disks optical discs DVD CD ROMs micro drive and magneto optical disks ROMs Rams EPROM s EPROM s Drams Rams flash memory devices magnetic or optical cards Nan systems including molecular memory ICs or any type of media or device suitable for storing instructions and or data.

Stored on any one of the computer readable medium media the present invention includes software for controlling both the hardware of the general purpose specialized computer or microprocessor and for enabling the computer or microprocessor to interact with a human user or other mechanism utilizing the results of the present invention. Such software may include but is not limited to device drivers operating systems execution environments containers and user applications.

The foregoing description of preferred embodiments of the present invention has been provided for the purposes of illustration and description. It is not intended to be exhaustive or to limit the invention to the precise forms disclosed. Many modifications and variations will be apparent to one of ordinary skill in the relevant arts. For example steps performed in the embodiments of the invention disclosed can be performed in alternate orders certain steps can be omitted and additional steps can be added. The embodiments were chosen and described in order to best explain the principles of the invention and its practical application thereby enabling others skilled in the art to understand the invention for various embodiments and with various modifications that are suited to the particular use contemplated. It is intended that the scope of the invention be defined by the claims and their equivalents.

