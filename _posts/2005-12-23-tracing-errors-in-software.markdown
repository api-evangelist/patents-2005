---

title: Tracing errors in software
abstract: An error tracing analysis tool applies static code analysis to software source code to identify error paths in the code and determine how many of these error paths have trace statements.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07774760&OS=07774760&RS=07774760
owner: Microsoft Corporation
number: 07774760
owner_city: Redmond
owner_country: US
publication_date: 20051223
---
A portion of the disclosure of this patent document contains material which is subject to copyright protection. The copyright owner has no objection to the facsimile reproduction by anyone of the patent document or the patent disclosure as it appears in the Patent and Trademark Office patent file or records but otherwise reserves all copyright rights whatsoever. The following notice applies to the software and data as described below and in the drawings hereto Copyright 2005 Microsoft Corporation All Rights Reserved.

It is often difficult to determine the root cause of an error in complex multilayered software. In some situations upper layers of software abstract the details of the errors caused by lower layers and present a more user friendly output to the person using the software. This abstraction of failures makes diagnosing the exact cause of the error difficult.

One of the technologies that can be used to counteract this loss of information due to abstraction of errors is tracing. Optional trace statements for example calls to the application programming interface API of a tracing tool are embedded in the code to record the error at each layer in the software thus creating a trace of the errors across the cross section of the multilayered software. This trace may be used to better understand the error and to rapidly determine the root cause.

However if an error occurs in a portion of the software which lacks trace statements the root cause of the error may not be clear to the person analyzing the problem.

This Summary is provided to introduce a selection of concepts in a simplified form that are further described below in the Detailed Description. This Summary is not intended to identify key features or essential features of the claimed subject matter nor is it intended to be used as an aid in determining the scope of the claimed subject matter.

Tracing helps people understand what a software program is doing by showing how the program is executed. It is good practice for a programmer to add tracing statements for example calls to the application programming interface API of a tracing tool to the software code of the program. If the tracing is enabled while the program is running the trace statements will output trace messages to a debugger or to a log file.

A software function may return a value to the function that called it. If a called function behaves as intended it may return a value to indicate the success of the called function. However if the called function does not behave as intended it may return a value that indicates that an error has occurred.

An error tracing analysis tool applies static code analysis to software source code to identify error paths in the code and determine how many of these error paths have trace statements. Recommendations to include trace statements in error paths that are identified as lacking trace statements may be made. Trace statements may be automatically inserted in error paths that are identified as lacking trace statements.

Trace statements that identify the reason for the error provide more information than trace statements that merely indicate that an error has occurred. The quality of error tracing in the code may be quantified based on the percentage of error paths having trace statements that identify the reason for the error and or the percentage of error paths having trace statements of any kind. These and similar quantifications may be used to compare the quality of error tracing in different pieces of code.

It will be appreciated that for simplicity and clarity of illustration elements shown in the figures have not necessarily been drawn to scale. For example the dimensions of some of the elements may be exaggerated relative to other elements for clarity.

In the following detailed description numerous specific details are set forth in order to provide a thorough understanding of embodiments of the invention. However it will be understood by those of ordinary skill in the art that the embodiments may be practiced without these specific details. In other instances well known methods procedures and components have not been described in detail so as not to obscure the embodiments of the invention.

According to some embodiments of the invention an error tracing analysis tool applies static code analysis to software source code to identify error paths in the code and determine which if any of these error paths have trace statements. In one example an error path is defined as starting a point in the code where an error could be returned from a function called by the current function and as ending either where the error is returned by the current function or at the start of another error path that starts before the error is returned by the current function.

A non exhaustive list of examples of trace statements includes statements that print a trace message to an output file or a printer calls to the application programming interface API of a tracing tool and statements that log the error in a circular buffer in the memory.

The error tracing analysis tool may make recommendations to include trace statements in error paths that are identified as lacking trace statements. For example the error tracing analysis tool may produce output that identifies the starting points of error paths that lack trace statements. A software engineer may then add trace statements to the software source code. Trace statements may be automatically inserted in error paths that are identified as lacking trace statements. The automatic insertion of trace statements may be performed by the error tracing analysis tool or by another tool that makes use of the output of the error tracing analysis tool.

Trace statements that identify the particular error that has occurred provide more information than trace statements that merely indicate that an error has occurred. The quality of tracing in the code may be quantified based on the percentage of error paths having trace statements that identify the error and or the percentage of error paths having trace statements of any kind. These and similar quantifications may be used to compare the quality of tracing in different pieces of code.

At the tool systematically detects error paths in the software code using static code analysis. For example this systematic detection may include matching code constructs in the software code to predefined patterns.

In one specific example the OPAL functional programming language an informal specification of which is found at http www.cs.oberlin.edu jwalker opal spec was used to define the following patterns for the start of error paths 

These error path start patterns are matched if a function is called that returns a value of a specified type and the value is not equal to the return value that indicates no error.

At the tool automatically determines using static code analysis which if any of those error paths detected at that include at least one trace statement. Again this may be accomplished by matching code constructs in the software code to predefined patterns. To continue the specific OPAL based example the following patterns may be used to define and recognize a trace statement 

The p Trace pattern is matched if a function the name of which includes WPP SF  is called that returns a value. The p TraceNoError pattern is matched if a function the name of which includes WPP SF  is called that does not return a value or if a function with one of the other names listed above is called. WPP is an acronym for Windows software trace processor.

At the tool identifies the location in the software code of an error path detected at and not identified at as including at least one trace statement. For example this location may be identified by code line number and may be provided to the user of the tool via a suitable output such as a log file. The output is effectively a recommendation to the user to insert at least one trace statement in the software code in the detected error path that currently lacks trace statements. The identification of locations of error paths that lack trace statements may be performed for one or more of such error paths in the software code.

At the tool automatically inserts a trace statement into the detected error path that does not include at least one trace statement. The inserted trace statement may be a simple trace statement that merely indicates that an error occurred. Alternatively the inserted trace statement may identify the particular error that has occurred.

The identification of the locations is optional and may depend upon the implementation and or configuration of the tool. The automatic insertion of trace statements is optional and may depend upon the implementation and or configuration of the tool.

At the tool automatically determines using static code analysis whether the trace statements identified at identify the particular error of the detected error path. This determination may occur at as part or all of the process of automatically determining which if any of the detected error paths includes at least one trace statement. Alternatively the automatic determination at may be a secondary process that further filters the trace statements detected at .

The determination of whether a trace statement indicates the particular error of the detected error path is optional and may depend upon the implementation and or configuration of the tool.

The tool may quantify an error tracing quality of the software code at . In one example this quantification is based on a total number of detected error paths detected at and on a number of the detected error paths that are determined at to include at least one trace statement. In another example this quantification is based on a total number of detected error paths detected at and on a number of the detected error paths that are determined at to include at least one trace statement that identifies the particular error. Other suitable quantifications of an error tracing quality are also possible. The error tracing quality of different pieces of software code can be compared using any of these quantifications.

Some embodiments of the invention may be described in the general context of computer executable instructions such as program modules executed by one or more computers or other devices. Generally program modules include routines programs functions dynamic linked libraries DLLs applets native instructions objects components data structures etc. that perform particular tasks or implement particular abstract data types. Typically the functionality of the program modules may be combined or distributed as desired in various embodiments.

There is another error path from line where FunctionC the called function could potentially return an error to line where an error value is returned by FunctionB the current function . There is no trace statement in this error path.

Tool comprises a static code analysis engine . A non exhaustive list of examples for static code analysis engine includes Lint PREfast PREfix and the like.

In some embodiments static code analysis engine comprises a component to implement a finite state machine. Examples of finite state machines to be implemented by component are described below with respect to .

A specification is provided to static code analysis engine to configure its behavior. For example specification may specify the code constructs to be identified by static code analysis engine and the states events and transitions of the finite state machine to be implemented by component .

Tool may optionally comprise a component for automatic trace statement insertion. Component may use the locations of detected error paths that lack trace statements to determine where in software code to insert trace statements. The output of component is a revised software code that includes the inserted trace statements.

When none of the three events have been detected the state machine is in its initial state start. When the e ErrorRaised event is detected there is a transition from the start state to the s TraceRequired state and a logging message indicative of or describing this transition for example Error Raised is output to file .

In the s TraceRequired state there is a condition that would require tracing. For example a function called by the current function has returned an error. There is a transition from the s TraceRequired state to the s TraceExecuted state when the e TraceCalled event is detected and a logging message indicative of or describing this transition for example Trace Executed is output to file . There is a transition from the s TraceRequired state to the error state when the e FuncExit event is detected and a logging message indicative of or describing this transition for example No tracing of error is output to file .

The s TraceExecuted state is a terminal state which causes the static code analysis engine to halt the processing for this state machine.

The error state represents a situation where an error path has been detected but no trace statements in that error path have been detected.

To continue the specific OPAL based example specification may include in addition to the pattern definitions given above the following definition of finite state machine 

In another version of the specific OPAL based example specification may include in addition to the pattern definitions given above the following definition of finite state machine 

In this specific example the s TraceExecuted state is reached only if a trace statement that does not identify the error is detected before the end of the error path.

Additionally device may also have additional features or functionality. For example device may also include additional storage removable and or non removable including but not limited to magnetic or optical disks or tape. Such additional storage is illustrated in by removable storage and non removable storage .

Computer storage media includes volatile and nonvolatile removable and non removable media implemented in any method or technology for storage of information such as computer readable instructions data structures program modules or other data. Memory removable storage and non removable storage are all examples of computer storage media. Computer storage media includes but is not limited to random access memory RAM read only memory ROM electrically erasable programmable ROM EEPROM flash memory or other memory technology compact disk ROM CD ROM digital versatile disks DVD or other optical storage magnetic cassettes magnetic tape magnetic disk storage or other magnetic storage devices or any other medium which can be used to store the desired information and which can be accessed by computing device . Any such computer storage media may be part of device .

Device may also contain communication connection s that allow the device to communicate with other devices. Communication connection s is an example of communication media. Communication media typically embodies computer readable instructions data structures program modules or other data in a modulated data signal such as a carrier wave or other transport mechanism and includes any information delivery media. The term modulated data signal means a signal that has one or more of its characteristics set or changed in such a manner as to encode information in the signal. By way of example and not limitation communication media includes wired media such as a wired network or direct wired connection and wireless media such as acoustic RF infrared and other wireless media. Combinations of any of the above should also be included within the scope of computer readable media. The term computer readable media as used herein includes both storage media and communication media.

Device may also have input device s such as keyboard mouse pen voice input device touch input device etc. Output device s such as a display speakers printer etc. may also be included. All these devices are well known in the art and need not be discussed at length here.

Although the subject matter has been described in language specific to structural features and or methodological acts it is to be understood that the subject matter defined in the appended claims is not necessarily limited to the specific features or acts described above. Rather the specific features and acts described above are disclosed as example forms of implementing the claims.

