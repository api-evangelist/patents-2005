---

title: Data retrieval method
abstract: A method of retrieving data from any one of a plurality of data sources is disclosed. The data stored by each data source are arranged according to an associated data format. The method comprises: issuing a retrieval request for data stored on a designated one of the plurality of data sources to a control process; passing the retrieval request from the control process to the one a plurality of retrieval processes that is associated with the designated data source, said one of the retrieval processes retrieving the requested data from the designated data source and rearranging the retrieved data into a common output format, if it is not already in the common output format; and passing the data in the common output format to the control process.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07949675&OS=07949675&RS=07949675
owner: Oracle International Corporation
number: 07949675
owner_city: Redwood Shores
owner_country: US
publication_date: 20050510
---
The present invention relates to a method of data retrieval and to a system for performing such a method.

Many software products have multiple sources for the metadata that they use. For example the run time metadata used by a business intelligence query tool may be drawn from a core repository stored in a database. However some business intelligence tools have the capability to populate their core repository based on the contents of the core repository of an older version or of another product for example a competitor s product or based on metadata derived from the contents of a database s online dictionary.

However a problem exists with this arrangement since the techniques used to retrieve data from these different sources of data are very different and this results in inconsistent presentation of the data to the user and increase the complexity of the product. Furthermore the data processing facilities that may be available for data from one of the sources may differ from those available to data from other sources.

As will be appreciated by those skilled in the art a core repository is a store for storing a set of metadata that is associated with a software product. A business intelligence tool is a software product that assists a user in interpreting gathered data and in using that data in decision making processes.

According to one aspect of the present invention there is provided a method of retrieving data from any one of a plurality of data sources the data stored by each data source being arranged according to an associated data format the method comprising 

issuing a retrieval request for data stored on a designated one of the plurality of data sources to a control process 

passing the retrieval request from the control process to the one of a plurality of retrieval processes that is associated with the designated data source said one of the retrieval processes retrieving the requested data from the designated data source and rearranging the retrieved data into a common output format if it is not already in the common output format and passing the data in the common output format to the control process.

Thus the invention solves the problem inherent with the prior art by rearranging or converting the data retrieved from each source into a desired common output format if necessary so that consistent processing and display of the data is possible. Accordingly the user s experience in accessing data from these different sources is consistent and the user is not aware that any transformation of data into a common representation is occurring.

The invention may operate on a variety of data formats. For example it may use data stored in a spreadsheet such as Microsoft Excel or it may use data stored in a database for example database tables or views.

Further at least one of the data sources may contain data representing an online dictionary of a relational database.

In one embodiment the associated data format of one of the data sources relates to a previous version of a business intelligence tool and the common output format relates to a current version of the business intelligence tool.

Advantageously the associated data format of one of the data sources may relate to a first type of business intelligence tool and the common output format may relate to a second type of business intelligence tool.

Many different data structures may be used to represent the data retrieved from the data sources. The typical data structure which is used to display the common output format data is a tree. This allows the display of data from different data sources to be displayed in respective branches of the tree whilst the whole tree behaves coherently.

In accordance with a second aspect of the present invention there is provided a system for retrieving data the system comprising a processor connected to a plurality of data sources each source storing data arranged according to an associated format wherein the processor is adapted to 

i issue a retrieval request for data stored on a designated one of the plurality of data sources to a control process 

ii pass the retrieval request from the control process to the one of a plurality of retrieval processes that is associated with the designated data source said one of the retrieval processes retrieving the requested data from the designated data source and rearranging the retrieved data into a common output format if it is not already in the common output format and iii pass the data in the common output format to the control process.

In accordance with a third aspect of the present invention a computer program comprises computer program code means adapted to perform the steps of the first aspect of the invention when said program is run on a computer.

In accordance with a fourth aspect of the present invention a computer program product comprises computer program code means adapted to perform the steps of the first aspect of the invention.

Metadata is a well known term in the art and in a sense it is data that describes other functional data. For example it may assign characteristics such as user friendly names to data and indeed it may indicate the purpose of the data and what processes can be performed on it.

Retrieval and storage of metadata from any of the sources to is performed by a metadata access application programming interface API . When data is retrieved this outputs the metadata in the form of unified metadata and it provides a template for the required metadata format i.e. unified metadata from lower level software processes.

These lower level software processes are plug ins to each one being associated with a respective one of the sources to

The core repository plug in performs no processing on the metadata retrieved or stored from the data source since this is already in the desired format. Instead it merely performs the necessary storage and retrieval of the data.

The online dictionary plug in normally operates as a read only process although it could be a read write process. It is operable to list the schemas present on the database by generating a corresponding list of folders to convert a schema into a folder and to convert a database table or join definition into a unified metadata definition. The online dictionary plug in could also be operable to read cubes and dimensions.

The upgrade plug in again is normally read only but could be a read write process. It is operable to retrieve metadata from the core repository of an older business intelligence product and to convert these to the unified metadata format required by the API .

The third party product plug in is similar to the upgrade plug in but instead is operable to retrieve data from a third party product s data repository

As such it is not necessary for any of the metadata stored in any of the data sources to to be used to populate the core repository of data source in order that they can be read and operated upon and by converting them into a unified metadata format a consistent user interface is achieved for all the data from any source to and consistent processing of the data can be performed.

The data output by API can be processed by any subsequent software routine for example to generate a display of a tree data structure representing the metadata in the respective data sources to with each source of metadata being represented by a branch of the tree.

The spreadsheet data of are managed by a plug in known as the Excel Spreadsheet Plug In not shown in . This plug in forms an interface between the data source in this case an Excel Spreadsheet and the metadata access API .

On initiation of the software a retrieval request is passed to the metadata access API for the root information for all available data sources. In this example these data sources are the spreadsheet shown in and the database table shown in . In response to this the Excel spreadsheet plug in converts the name of the spreadsheet that is Employee Information into the unified metadata format. In this instance the unified metadata format may be a metadata directory. The retrieval request also causes the generation of a unique identifier for the spreadsheet.

In addition the on line dictionary plug in converts the name of the database that is ora10 stored on source into the unified metadata format. Again a metadata directory may be used. A unique identifier for the database is also generated.

These two items can then be displayed to the user as the first branches of the tree structure shown in namely items Spreadsheet Employee Information and Database Online Dictionary ora10 .

The user may then cause a further retrieval request to be passed to the metadata access API in order to retrieve the contents of the spreadsheet called Employee Information which will be referred to using the previously obtained unique identifier . This will cause the Excel spreadsheet plug in to return a listing of all the sheets in the spreadsheet in this case including the sheet named Employee Salary . The Excel spreadsheet plug in converts the sheet into a set of unified metadata format values for example metadata item folders each representing one of the sheets in the spreadsheet and each having a unique identifier. This can then be displayed to the user as a list of these sheets within the spreadsheet as shown in .

The user may wish to see the contents of the sheet Employee Salary within the Employee Information spreadsheet and to do this he would select a sheet on the tree causing a retrieval request to be passed to the metadata access API . The metadata access API would use the previously claimed unique identifier to cause the Excel spreadsheet plug in to return the information representing the structural contents of the sheet in a unified metadata format for example a metadata item folder . Each column in the sheet will be converted to a unified metadata format for example a metadata item and information such as the heading and type of data may be included in the definition. The items are added as part of the item folder representation of the sheet. The items are then displayed as part of the tree shown in .

The user may also wish to view the contents of the database ora10 . To do so he would select this on the tree causing a retrieval request to be passed to the metadata access API for the contents of the database ora10 using the previously obtained unique identifier. This will cause the online dictionary plug in to return a list of schemas in the database. The online dictionary plug in converts the schema names into a set of unified metadata format values for example metadata directories representing each of the schemas in the database and each having a unique identifier in this case a single value for a schema known as SCOTT .

The user may select this schema to reveal the tables within it. This will cause a retrieval request to be passed to the metadata access API using the previously obtained unique identifier and this will cause the online dictionary plug in to return a list of the tables in the schema. The online dictionary plug in converts the table names into a set of unified metadata format values for example metadata item folders each representing one of the tables in the database and each having a unique identifier in this case a single value for table EMP .

Finally the user may reveal the contents of the table EMP by selecting it on the tree shown in which causes a retrieval request to be passed to the metadata access API using the previously obtained unique identifier and causing the online dictionary plug in to return the information without the table contents in the unified metadata format for example a metadata item folder representing the structural contents of the table. Each column in the table will be converted to the unified metadata format for example a metadata item and information such as the heading and type of data included in the item definition. The items are included as part of the item folder representation of the table which is then displayed on the tree as shown in .

It is important to note that while the present invention has been described in a context of a fully functioning data processing system those of ordinary skill in the art will appreciate that the processes of the present invention are capable of being distributed in the form of a computer readable medium of instructions and a variety of forms and that the present invention applies equally regardless of a particular type of media actually used to carry out distribution. Examples of computer readable media include recordable type media such as floppy disks a hard disk drive RAM and CD ROMs.

