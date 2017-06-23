---

title: Portable application registry
abstract: This document describes techniques that enable an application to operate as if the application were running on its native computing system when it is actually running on another computing system. The techniques may do so by building a portable registry having metadata particular to the application, which can be stored in a portable device along with that application. When that portable device is connected to another computing system, the portable registry may be used to supplement or supplant the other computing system's registry to enable the application to operate with its particular functionality.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07917487&OS=07917487&RS=07917487
owner: Microsoft Corporation
number: 07917487
owner_city: Redmond
owner_country: US
publication_date: 20051213
---
Software applications often behave in particular ways based on changes made when using that application such as changes made by a user setting his or her preferences and or metadata about an application such as metadata providing components of the application with a roadmap to other components. A user may for instance customize toolbars for his spreadsheet application or a dictionary for his word processing application s spell checker.

Customizations and other application specific functionality are generally retained by the application s native computing system not the application itself. When an application is executed it interacts with its native computing system s registry to enable its particular functionality.

When an application is saved to a portable device and connected to another computing system however the application may behave differently. It can behave differently because the other computing system s registry may not have a record of the application s particular functionality. The afore mentioned user s spreadsheet application for example may have different toolbars or his dictionary not recognize particular words previously added by the user.

This document describes techniques that enable an application to operate as if the application were running on its native computing system when it is actually running on another computing system. The techniques may do so by building a portable registry having metadata particular to the application which can be stored in a portable device along with that application. When that portable device is connected to another computing system the portable registry may be used to supplement or supplant the other computing system s registry to enable the application to operate with its particular functionality.

This Summary is provided to introduce a selection of concepts in a simplified form that are further described below in the Detailed Description. This Summary is not intended to identify key or essential features of the claimed subject matter nor is it intended to be used as an aid in determining the scope of the claimed subject matter.

The same numbers are used throughout the disclosure and figures to reference like components and features.

The following document describes many techniques some of which enable a portable application to operate on a computing system with functionality associated with the application. These techniques may do so using a portable registry capable of supplementing or supplanting the computing system s registry.

For example these techniques may enable a user to operate his portable spreadsheet application on a new computing system and use his particular toolbars or operate his portable word processing application and spell check words that he previously added to his dictionary.

An environment in which these and other techniques may operate is set forth first below. This is followed by a section entitled Operating on a Computing System which describes exemplary ways in which a portable application may operate on a computing system using a portable registry.

Before describing the techniques in detail the following discussion of an exemplary operating environment is provided to assist the reader in understanding one way in which various inventive aspects of the techniques may be employed. The environment described below constitutes but one example and is not intended to limit application of the techniques to any one particular operating environment. Other environments may be used without departing from the spirit and scope of the claimed subject matter.

The portable registry may comprise application metadata which may be used by the portable application or an operating system to enable the portable application s particular functionalities and behavior. The application metadata may include information affecting how the portable application behaves such as how particular functionalities act or are presented e.g. a toolbar s appearance . For example the metadata may indicate which interfaces to expose to the portable application and a start menu icons or graphics that the portable application uses.

Here the portable storage device stores these elements for later use by a computing system . Computing system may initially lack some or all of the application metadata such that the portable application may not perform and behave on the computing system as it should. The computing system comprises one or more processor s and computer readable media . The system s processor s are capable of accessing and or executing the media. The media initially or eventually comprises or has access to a program loader portable application intermediary a system registry portable registry and application metadata . The portable application the intermediary the portable registry and the application metadata may be received from the portable device.

The following discussion describes exemplary ways in which an application may operate on a computing system using a portable registry.

Block receives a request for a function or data usable by a portable application. This request may be accessed through a system registry that were it made to the portable registry could enable functionality particular to the application.

The portable application s particular functionality may be affected by its own requests or requests from another entity. For example block may receive the request for a function from the portable application or a module associated with or usable by the portable application. If for instance the portable application causes additional library modules to be loaded which may also request functions affecting the portable application s particular functionality the module s requested functions may be handled similarly to those from the portable application itself.

Block intercepts the request such as by intermediary . The techniques may in cases where the intermediary is not part of the portable application enable the portable application and its associated modules to remain unaltered while still enabling the portable application s particular functionality. Block may do so by acting on a request that does not need to be altered or come from a requesting entity that needs to be altered.

In some other cases the intermediary is part of the portable application. In these cases the intermediary intercepts the request to preclude the portable application from requesting a function or data directly from the system registry.

The intermediary may intercept the request by first altering a table of addresses such as an exemplary simplified Import Address Table IAT in . This IAT is built by the program loader. It provides addresses by which the portable application when it is executing may request directly or indirectly through other modules data for a particular function. These requests may include opening a registry key reading or writing a value one or more times and closing the registry key.

The program loader populates the IAT with a location. This permits the portable application to call the address in the IAT which may simply be an integer related to data or a function s memory location also in the IAT rather than a particular path. The IAT comprises actual and original addresses shown at . It also comprises IAT addresses associated with these actual addresses. An application may call the IAT address instead of the actual address.

Here the intermediary replaces the original function addresses in the IAT prior to the request so that when the portable application first requests a particular IAT address the function associated with that IAT address prompts the intermediary to execute. The intermediary may replace the original function addresses prior to any original function being called by replacing the original function addresses in the IAT very early in the execution of the portable application e.g. by the portable application calling the intermediary first .

Block determines whether registry data exists to enable functionality particular to an application that is being operated from a portable device on a computing system having a system registry. In some cases application specific metadata related to the requested function is in the portable registry. In some others no application specific metadata is so related. In still others such as when the requested function repeats to enumerate a complete set of values application specific metadata related to the requested function may be in the portable registry but metadata in the system registry may also be related to the requested function.

If block determines that the requested registry data does not have associated metadata related to the portable application e.g. if the requested data does not exist in the portable registry it proceeds to block . Block does not supplant or supplement the system registry. Here block proceeds to block which reads the requested data from the system registry.

If block determines that the registry data requested has associated metadata related to the portable application and in some cases also that the system registry is not needed it proceeds to block . Block supplants the system registry with the portable registry or its metadata. The intermediary may supplant the system registry by routing a request for data to the portable registry instead of the system registry.

It then proceeds to block which reads the requested data from portable registry. Here the techniques seamlessly integrate metadata associated with particular functionality of the portable application with a system registry such that the portable application retains its particular functionality.

If block determines that the requested registry data has associated metadata related to the portable application and also needs the registry data to be requested from the system registry it proceeds to block . Block supplements the system registry with the portable registry and proceeds to block . Block reads the requested registry data from the portable registry. After block however the process proceeds to block to also read requested data from the system registry. This supplementing of the system registry may occur when multiple iterations of a function are needed such as to enumerate multiple values.

When the IAT address is called the intermediary function is instead executed thereby intercepting execution of the intended function at address and instead executing the intermediary function at the associated address .

When executed the intermediary function first attempts to open a key in the portable registry. The portable registry contains keys and values with the keys organized hierarchically. Keys may contain other keys or values. The intermediary may also read or write data from or to the portable or system registries. The intermediary function may also close a key.

IAT contains a list of references to Application Programming Interfaces APIs which are designed to act on the system registry. These APIs may be intercepted by the intermediary shown in using altered IAT which on a case by case basis decides from which registry portable or system to read. This decision may be made based on the name of the key or key handle HKEY provided by the requesting entity. Thus a given API may read the portable registry for one HKEY and the system registry for a different HKEY.

If the requested key is not available e.g. the HKEY does not represent a key in the portable registry the intermediary reads the requested data from the system registry e.g. calling one of original function addresses of using an appropriate HKEY for that original registry key . If the key is repeatedly read the system registry may be read in addition to the portable registry.

In some cases registry keys will need to be altered such as to write a value. The intermediary may know which registry was previously read for the key by retaining a record of which HKEYs have been successfully read from the portable registry and which have not. When a function is then called that will make an alteration the intermediary writes the key in the correct registry.

Effectively the conjunction of the system registry and the portable registry can be functionally similar or even identical to the result of installing a product to the system registry. Graphically this is shown in simplified form in . Here the altered addresses of the altered IAT are shown correlating to either a key in the portable registry or an address in the system registry API which is the same as that of the original function addresses of IAT . The sections of the portable registry without keys are shown blank. The correlation is shown between the original address and the portable or registries with arrows for clarity though they may not line up in this fashion.

The above described techniques enable an application to operate on a computing system as though it were installed on that computing system. These techniques may do so using a portable registry capable of supplementing or supplanting a computing system s registry. These techniques may provide significant improvements over the current state of the art potentially enabling users to use their portable applications on computing systems without those portable applications behaving differently than they would had they been installed to those computing systems. Although these techniques have been described in language specific to structural features and or methodological acts it is to be understood that the techniques defined in the appended claims are not necessarily limited to the specific features or acts described. Rather the specific features and acts are disclosed as exemplary forms of implementing the claimed techniques.

