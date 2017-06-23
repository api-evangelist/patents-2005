---

title: Preventing a copy of a protected window
abstract: A method, system and computer readable program on a medium for masking a window or a visible part of a window during a copy screen or copy window operation which:


url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07600267&OS=07600267&RS=07600267
owner: International Business Machines Corporation
number: 07600267
owner_city: Armonk
owner_country: US
publication_date: 20050614
---
The present invention relates to computers and more particularly to a method and system for preventing a copy of a protected window displayed on a computer screen.

When a mail is sent to a recipient some operations may be forbidden by the sender. In Lotus Notes Lotus Notes is a trademark of International Business Machines Corporation the sender can decide to prevent the copy of a mail by selecting the option prevent copy in the delivery options menu. This has for effect to prevent either the forwarding of the message to another person or the printing of the message or the copy paste of the message content. However in the Microsoft Windows Windows is a trademark of Microsoft Corporation operating system it is always possible to capture the entire screen Ctrl PrintScreen or the active window Alt PrintScreen to the clipboard. This may lead to diffuse restricted information to third parties without the authorization or control of the mail originator.

The present invention is directed to a system method and computer program as defined in independent claims for preventing copy of a protected window.

The main object of the present invention is to mask the window or a visible part of the window during the copy screen or copy window operation. The invention 

The foregoing together with other objects features and advantages of this invention can be better appreciated with reference to the following description claims and drawings.

The principle of the solution is to mask a window or the visible part of a window comprising sensitive information. So after a copy screen all the windows comprising sensitive information for instance confidential information or information that must be kept secret are masked. shows the result of a copy of a screen according to the present invention. The sensible information in the copy protected window is masked when a window or screen copy event occurs. shows the copy of the same screen when the present invention is not implemented. Similarly shows the result of a copy of a copy protected active window according to the present invention. The sensible information in the active window is masked. shows the copy of the same active window when the present invention is not implemented.

The preferred embodiment of the present invention relies on all the Microsoft Windows operating system family. In a graphical Microsoft Windows based application a window is a rectangular area of the screen where the application displays output and receives input from the user. A window shares the screen with other windows including windows from other applications. Only one window at a time can receive input from the user. The user can use the mouse the keyboard or other input devices to interact with this window and the application that owns it. Microsoft windows can be of different types Overlapped Pop up Child Layered Message Only . The various window types will not be described in detail in the present description. The most important principles to understand the problem that the present invention proposes to solve are 

The z order of a window indicates the window s position in a stack of overlapping windows. This window stack is oriented along an imaginary axis the z axis extending outward from the screen. The window at the top of the z order overlaps all other windows. The window at the bottom of the z order is overlapped by all other windows.

The system maintains the z order in a single list. It adds windows to the z order based on whether they are topmost windows top level windows or child windows.

In the Microsoft Windows operating system a hook is a mechanism by which a function can intercept events messages mouse actions keystrokes before they reach an application. The function can act on events and in some cases modify or discard them. Functions that receive events are called filter functions and are classified according to the type of event they intercept. For example a filter function may want to receive all keyboard or mouse events. For Windows the filter function must be installed that is attached to a Windows hook for example to a keyboard hook . Attaching one or more filter functions to a hook is known as setting a hook. If a hook has more than one filter function attached Windows maintains a chain of filter functions. The most recently installed function is at the beginning of the chain and the least recently installed function is at the end.

The Microsoft Win32 Win32 is a trademark of Microsoft Corporation application programming interface API provides a set of functions to access modify 

With the Microsoft Windows Operating system all the graphical windows are message driven. All the windows have at least one thread responsible to process messages received from the system for instance user mouse events . This thread is called the WindowProc and can send messages to any other windows applications.

Hooks mechanisms provide powerful capabilities for Windows based applications. These applications can use several options to set a hook 

In a preferred embodiment of the invention two primitives are defined. The objectives of these primitives are 

With the Microsoft Windows operating system a hook filter is a dynamic library registered at the system level. To set such hook filter it is necessary to initialize and configure the hook mechanism using the SetWindowsHook win32 API. The same kind of action is necessary to remove such hook filter from the system using the UnhookWindowsHook win32 API. The method according to the present invention comprises the following steps and the system includes logic to invoke the commands 

In Lotus Notes each time a user opens a mail an external program is called to check whether the mail is protected or not. Technically the interception of the mail is performed using a queryopen event of the memo form. The value of the internal Lotus Notes variable called KeepPrivate indicates whether the document is protected or not. The way to call an external program is described in the following section.

LotusScript LotusScript is a trademark of International Business Machines Corporation allows the call external C language functions. The principle is to implement external C functions inside a named library module that generally comprises several C functions. With Windows this is a Dynamic Link Library DLL . All Windows users have access to the libraries in the Windows application programming interface API . The C functions that are in the DLLs shared libraries must be exported. Different platforms have different rules and ways for exporting them.

The Declare statement is used to call C functions comprised in an external library module from LotusScript. To avoid the declaration of external library functions in multiple scripts Declare Public statements are used in a module which remains loaded.

By default LotusScript passes arguments to functions by reference. If the argument is an array a user defined data type variable or an object reference variable the arguments are passed by reference. Generally the ByVal keyword is used to pass variables by value.

What has been described is merely illustrative of the application of the principles of the present invention. Other arrangements and methods can be implemented by those skilled in the art without departing from the spirit and scope of the present invention.

