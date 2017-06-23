---

title: Automatic service apparatus and automatic service system
abstract: An automatic transaction system communicates with a Web server and performs automatic transaction according to the operation of a user. In order to decrease the download time with the Web server which is generated for each operation of the user, a screen frame of a browser of an automatic service device is divided into a transaction screen frame and an applet resident frame. And all applets are embedded in a screen content of the Web server, and are downloaded into the applet resident frame of the browser in advance when the device is started up. And in the subsequent Web communication, a method callup script is embedded in the image content, and a method of an applet of the resident frame is called up and the operation of I/O units are controlled.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08090804&OS=08090804&RS=08090804
owner: Fujitsu Frontech Limited
number: 08090804
owner_city: Tokyo
owner_country: JP
publication_date: 20050412
---
This application is based upon and claims the benefit of priority from the prior Japanese Patent Application No. 2004 208940 filed on Jul. 15 2004 the entire contents of which are incorporated herein by reference.

The present invention relates to an automatic service apparatus and automatic service system for executing screen control and automatic service operation according to the screen content from a Web server and more particularly to an automatic service apparatus and automatic service system which operate by the screen content where the screen information and the device control information related to the screen are embedded.

Automatic service apparatus are used for various service business such as automatic withdrawal machines and automatic deposit withdrawal machines in the financial field and automatic ticket machines and automatic issuing machines in other fields. Along with the recent advancements of networks such as the Internet such automatic service apparatus which deposit withdrawal issue tickets and output various information by using Web technology are being provided.

The server sends the Web page screen content to the automatic transaction apparatus that is ATM which is a client according to the request of the ATM . On this Web page a program for creating a screen to be displayed on the display device is created in a page description language HTML JavaScript and control programs of other devices card processing device cash processing device pass book processing device statement slip processing device which are driven and controlled in relation to the display content of this one page one screen are embedded as objects.

For example as shows a Web page is comprised of a screen creation program an applet tag for specifying an object applet a screen content for specifying the execution method thereof by script and applets where programs for executing the method of the object applet are set based on the HTML Hyper Text Markup Language page description language.

This Web page is downloaded to the browser of the ATM from the WWW server . In the ATM on the other hand ATM middleware operates and the I O operation transaction operation is executed based on the control of the kernel OS . The ATM has a card reader writer unit a receipt journal printer a bill coin processing unit a pass book processing unit and a user operation panel as the I O mechanical units.

The browser displays the screen on the user operation panel according to the screen creation program of the Web page analyzes the applet tag and the method name of the screen content executes the corresponding program of the applet and issues a command to the I O units .

In this ATM controlled by the Web browser it is proposed that the device interface assignment section Machine ID is specified for each device e.g. cash processor as an embedded object applet of the screen content and the operation method of each device is specified by the Script JavaScript of the screen content e.g. Japanese Patent Application Laid Open No. 2000 298752 .

In this method the device interface assignment section is specified by the applet tag of the screen content and the device interface assignment section sequentially reads the Script decodes assigns an operation instruction to the corresponding interface section and operates the corresponding I O units .

In this proposal when ATMs with the same functions are controlled by the Web a plurality of units can be operated by one applet tag of the screen content therefore the number of descriptions in HTML of the screen content can be decreased and there can be fewer embedded objects.

In the case of a Web controlled automatic service device however an operation guide screen such as a transaction screen is displayed using a browser. And an I O unit is controlled via the applet integrated into this transaction screen content . Therefore processing cannot be requested to the I O unit unless there is a download wait of an applet for each screen. As a result for the user to operate a plurality of operations a wait time is generated for each operation which makes the service time such as for a transaction long.

Also when multiple input button images are displayed on the operation guide screen the download time for applets and the download time for the button images become long which in some cases is not good. For example it is preferable in terms of visual sensation and design to dispose multiple buttons and change the button image display for normal status inversion status and gray out status according to the pressing by the user. But it takes time to display for HTML and Script so performance in terms of visual sensation improves if buttons are displayed by applets. But if applets are used time is taken for a download and the screen switching time becomes longer than HTML.

Because of this the time for the user to use an automatic service device becomes long which drops the operating rate and makes the response wait time for the user long.

With the foregoing in view it is an object of the present invention to provide an automatic service apparatus and an automatic service system for decreasing the wait time for operation of the user who receives the service even if Web control is used.

It is another object of the present invention to provide an automatic service apparatus and an automatic service system for decreasing the wait time for downloading applets of the operation guide screen even if Web control is used.

It is still another object of the present invention to provide an automatic service apparatus and an automatic service system for decreasing the screen switching time of the operation guide system even if Web control is used.

It is still another object of the present invention to provide an automatic service apparatus and an automatic service system for enabling screen transition during I O control and decreasing the transaction time by making control applets a resident frame.

To achieve these objects the automatic service apparatus of the present invention is an automatic service apparatus for communicating with a Web server and performing guide display and service operation according to operation by a user has a display unit for displaying the guide operation a plurality of I O units for performing the service operation and a control unit for controlling the guide operation display on the screen of the display unit by a browser according to the screen content from the Web server and controlling the plurality of I O units according to a script embedded in the screen content. And the control unit stores in advance applets downloaded from the Web server in a resident frame of a browser screen that is divided into a service screen frame and a resident frame and performs the guide operation display by the screen content from the Web server as well as calls up a method of an applet for controlling the I O unit and controls the I O unit by a script embedded in the screen content.

The automatic service system of the present invention comprises a Web server and an automatic service apparatus which is connected to the Web server via a network for communicating with the Web server and performing guide operation display and service operation according to the operation by the user. And the automatic service apparatus further has a display unit for displaying the guide operation a plurality of I O units for performing the service operation and a control unit for controlling the guide operation display on the screen of the display unit by a browser according to the screen content from the Web server and controlling the plurality of I O units according to the script embedded in the screen content. The control unit stores in advance applets downloaded from the Web server in a resident frame of a browser screen that is divided into a service screen frame and the resident frame and performs the guide operation display by the screen content from the Web server as well as calls up a method of an applet for controlling the I O unit and controls the I O unit by the script embedded in the screen content.

The automatic service method of the present invention has the steps of storing applets downloaded from a Web server in a resident frame of a browser screen that is divided into a service screen frame and a resident frame of an automatic service apparatus performing guide operation display on a display device of the automatic service apparatus by the screen content from the Web server and calling up a method of an applet for controlling an I O unit of the automatic service apparatus and controlling the I O unit by the Script embedded in the screen content.

In the present invention it is preferable that the control unit sets the service screen frame to display and the resident frame to non display depending on the frame control content from the Web server.

Also in the present invention it is preferable that the control unit further has a browser which interprets the screen content and performs the guide operation display as well as interprets the script of the object embedded in the screen content and calls up a method in processing units of the transaction operation for synchronously controlling the plurality of I O units and synchronously controls the plurality of I O units from the browser.

Also in the present invention it is preferable that the browser of the control unit allows the screen of the service frame to transit according to the screen content from the Web server and does not allow the resident frame to transit except for the startup time.

Also in the present invention it is preferable that the I O unit further has at least a cash processing unit and a card processing unit.

Also in the present invention it is preferable that the control unit further receives a screen image generation applet for generating an image of the guide operation screen from the Web server and embeds it into the resident frame and generates an image file for displaying it on the service frame by the screen image generation applet when the device is started up.

Also in the present invention it is preferable that the control unit acquires the screen image file and displays it on the display unit when a callup instruction for the screen image generation applet is included in the screen content.

Also in the present invention it is preferable that the screen image generation applet creates the screen image from a pattern definition file.

Also in the present invention it is preferable that the screen image generation applet creates the arranged screen image file from multiple button images defined in the pattern definition file.

In the present invention the screen frame of the browser is divided into a transaction frame and a resident frame and all the applets are downloaded from the server to the resident frame of the browser of the automatic service device in advance. And during communication with the Web server for screen transition applets are not transmitted but the transaction screen where a tag for specifying the applet is embedded is transmitted. So the download time of the applet can be deleted when the transaction screen transits can be decreased. Therefore the wait time of the user for screen transition can be decreased the time for the user to use the automatic service apparatus can be decreased use can be more efficient and the operating efficiency of the apparatus also improves.

When the apparatus is started up e.g. at power ON the screen image generation applet in addition to the I O control applet is also downloaded from the server to the applet resident frame invisible frame of the browser in embedded foam. And in the resident frame the screen image generation applet acquires the button images to be used in the transaction screen and the screen image in advance and during communication with the server the transaction screen content is received according to the transaction operation and when the screen control applet is downloaded the screen image is acquired from the screen image generation applet of the resident frame and is drawn in the transaction frame.

Therefore the screen display time of the applets and the download time of the button images can be decreased at screen transition time so the screen switching time can be decreased. Even if a complicated pattern is displayed for visual sensation the image switching time can be decreased and this contributes to improving the visual sensation of the user during the operation input.

Embodiments of the present invention will now be described in the sequence of automatic service system I O control mechanism by Web control I O control method by Web automatic service processing screen switching control method and other embodiments.

As shows the automatic transaction apparatus has a card slot for inserting and ejecting a magnetic card pass book slot for inserting and ejecting a magnetic pass book a bill port for inserting and ejecting bills a coin port for inserting and ejecting coins a UOP User Operation Panel for guiding operation for users an operation display for displaying operating status to a user and a customer sensor for detecting the user.

The RPR Receipt Printer unit prints the transaction result on receipt paper by a print head and ejects the receipt through the card slot . The RPR unit also stores the receipt returned through the slot when the ejected receipt is not removed by the user within a predetermined time.

JPR Journal Printer unit prints the transaction status and result on journal paper by a print head. The UOP User Operation Panel unit has the UOP which is a display with a touch panel and the control circuit thereof. The pass book PPR processing unit reads the magnetic pass book inserted into the pass book slot prints the transaction result on the magnetic pass book and ejects it through the pass book slot .

The bill coin processing unit performs the deposit operation for verifying and counting the bills and coins inserted into the bill port and the coin port storing them in a stacker and performs the withdrawal operation for taking out the requested bills and coins from the cash stacker and releasing the currency to the bill port and the coin port .

The control unit is connected to these processing units and via a network such as a LAN and performs automatic transaction processing according to the configuration of the software which will be described later in .

Device drivers has a card unit driver for driving the card CRW unit a receipt journal unit driver for driving the receipt journal unit RPR JPR and a BRU driver for driving the BRU bill unit a CRW driver for driving the CRU coin unit a graphic driver and a touch screen driver for driving the UOP and PPR driver for driving the pass book unit .

The browser is constructed of such a Web browser as Internet Explorer Microsoft Corp. requests the Web server to send content and interprets and displays the screen content Web page sent by the Web server . In this case the browser requests the Web page required for a transaction constructed by HTML and JavaScript interprets the transmitted Web page and controls the ATM middleware and the screen of the UOP .

The kernel is constructed of a known OS Operating System such as Windows Microsoft Corp. and Linux and under the operation of the kernel the browser ATM middleware and device drivers operate.

The ATM middleware has a parameter file I O control layer I O client layer I O server layer and I O service provider layer .

This I O client layer is for controlling an individual I O unit installed in the apparatus the I O server layer is for starting and ending an I O operation and controlling the communication protocol and the I O service provider layer is for converting the messages addressed to each I O unit. These are conventional middleware which are designed according to the functional range type of apparatus and specifications of the I O units connected thereto.

The I O control layer on the other hand transmits receives commands and data with the Web server by using a middleware common application programming interface protocol. Since the functional range is different depending on the apparatus model this common application programming interface API is constructed of common commands and a data system which can operate all models and will be described later in .

The I O control layer integrates the application programming interface API of the I O client layer and constructs a common API with a high degree of abstraction. The parameter file is for storing the input parameters fixed parameters which are uniquely determined depending on the system specifications which are specific to a vendor ATM manufacturer .

The I O control layer calls up the parameters unique to each I O client from the parameter file when calling up the I O client layer and converts the common API into the conventional client API.

By this the common API with a high degree of abstractions can be converted into a client API that matches the type of ATM middleware and the I O unit of the automatic transaction apparatus and can operate the conventional ATM middleware and the I O unit. In other words the conventional ATM middleware can be customized so as to operate with a common API.

As shows the agents defined in processing units of the ATM are embedded as applets of the screen content of the Web page. And operation of the I O units required for processing is controlled in processing units by the agent . Also as described later the necessary applets are downloaded to the browser of the control unit of the ATM from the server when the apparatus is started up.

As described for and later the applet name is defined in processing units such as synchronous control or initialization control of synchronous control hereafter called an agent and method is also defined in processing units. In other words an applet agent having a method for controlling operation of the I O unit corresponding to the processing is created and the applet agent and method are specified in processing units.

Because of this even when a plurality of units are synchronously operated the operation can be performed in processing units. Furthermore an applet name can be assigned in processing units therefore the locations of changes on a Web page can be few for the Web control for ATMs having different functions and a Web page can be easily created even for complicated automatic transaction control.

Also a plurality of I O units can be controlled simply by calling up one method so a plurality of I O units can be parallel controlled the processing speed can be increased the ATM control time can be decreased even if Web control is used and the wait time for the user can be decreased.

The I O control mechanism by Web control will now be described. is a block diagram of the Web browser and the I O controller in the configuration in is a block diagram depicting the ATM middleware in the configuration in and is a table showing the commands of the common API in and .

As shows the screen content HTML JavaScript and the Agents applets are downloaded from the WWW server to the Web browser . The Agent has a control agent group for controlling each unit a POST Agent for performing post processing a View Agent for constructing a screen and the communication DLL Dynamic Link Library group for communicating with the I O controllers via the Java Native Interface and common API interface .

When all interfaces are the same the communication DLL group is unnecessary. For the control agent group only the control Agent required for transaction control is downloaded in advance when the apparatus is started up after which it resides in the browser . As described for or later the control Agent is constructed in processing units in the ATM transaction.

In the operation of the configuration in the method of the control Agent is called up by the method name described in the JavaScript in the screen content . The called up method issues a command to the I O controller via the communication DLL group .

The I O controller operates the corresponding unit via the ATM middleware and receives an operation completion notice. The I O controller responds to the execution result of the command to the control Agent . The control Agent sends a POST request or drawing request to the POST Agent for performing post processing or the View Agent for updating the screen so as to have post processing or screen update processing to be executed.

Before describing the Agent the common API will be described first. shows an example of command types of the common API. A card insertion command and card eject command are provided as CRW Card Reader Writer commands.

A print command and an eject command are provided as RPR Receipt Printer commands. And a pass book insertion command print command MS Magnetic Stripe write command pass book eject command and auto turn page command are provided as PPR Pass book Printer commands.

An initialization command receive count command store command deposited money return command feed command eject command capture command transport path check command and jam reset command are provided as BRU Bill Recycle Unit commands. CRU Coin Recycle Unit commands are the same and the description thereof is omitted.

The configuration of the ATM middleware in and will now be described with reference to . The I O control layer has the I O control library group I O controllers for controlling each I O.

In this case the I O control library group has a pass book control library CRW control library numeric keypad control library receipt control library bill control library coin control library journal control library and transaction control library .

These control libraries are called up by a task e.g. card control EXE specified by the common API and the task is converted into the client API of the conventional middleware using the above mentioned parameter table .

The I O client layer of the conventional middleware is for controlling an individual I O unit mounted on the apparatus and here the card CRW client coin client bill client RPR client JPR client and PPR client are disposed.

The I O server layer is also divided into individual I Os for starting up and ending an individual I O operation and controlling communication protocol. In other words the card CRW server coin server bill server RPR Receipt Printer server JPR server and PPR pass book printer server are disposed.

In the same way the I O service provider layer is also divided into individual I Os for converting a message addressed to an individual I O unit. In other words the card CRW service provider coin service provider bill service provider RPR service provider JPR service provider and PPR service provider are disposed.

In other words the control library client server and service provider constituting the ATM middleware are disposed corresponding to an individual unit and the I O control converts requested commands and parameters of the common API into commands and parameters of the conventional middleware API and operates the I O unit via the conventional middleware.

Now the above mentioned Agent will be described with reference to and . AS shows the synchronous Agent is a program for synchronously controlling a plurality of I O units and has initialization mechanical reset bill coin insertion media simultaneous eject print feed MS write eject preparation deposit return storage forced eject capture unit information acquisition transaction status setting two screen display control deposit withdrawal preparation forced replenishment jam rest and card pass book insertion as methods programs .

Each method issues a command to the I O controllers that is the I O units indicated by a black dot in and receives a response on the result of command execution. For example the initialization method issues an initialization command to the bill controller coin controller pass book controller card controller receipt controller journal controller transaction control controller and numeric keypad controller see has each controller execute initialization processing and receives the initialization processing result from each controller as a response.

In the same way the mechanical reset method issues a mechanical reset command to the bill controller coin controller pass book controller card controller receipt controller and journal controller see has each controller execute mechanical reset processing and receives the mechanical reset processing result from each controller as a response.

In the same way the bill coin insertion method issues an insertion command to the bill controller and the coin controller see has each controller execute the insertion processing and receives an insertion processing result from each controller as a response.

In the same way the POST Agent has a post processing method and a post data holding method. The View text display Agent has a font setting method text display method and text delete method.

Also as shows the applets for controlling a single I O unit are also defined as agents for controlling with the same architecture. In other words as shows the bill control Agent pass book control Agent card control Agent receipt control Agent transaction control Agent and numeric keypad Agent are disposed.

And the bill control Agent has a receiving counting method storage method deposit return method eject method and cancellation method for controlling bill controller respectively. The pass book control Agent has a line set page mark read method MS Magnetic Stripe read method auto turn page method page check auto turn method and pass book configuration information setting method for controlling pass book controller respectively.

The card control Agent has a card insertion method cancellation method bank transfer card printing method bank transfer card issuing method and eject preparation method for controlling card CRW controller respectively. The receipt control Agent has an overlay registration method and eject preparation method for controlling each receipt controller .

In the same way the transaction control Agent has a transaction information setting method device status monitoring method device status acquisition method operation information setting method and cancellation method for controlling transaction control controller respectively. The numeric keypad Agent has a numeric keypad input start method and numeric keypad input end method for controlling numeric keypad controller respectively.

The Web operation for calling such Agents and methods will be described with reference to to . First according to the present invention Agents applets are downloaded in advance and reside in the browser when the apparatus is started up and at the subsequent transaction operation the applets are not transmitted by the Web content but the applet related to the screen is specified. is a diagram depicting the screen frame of the Web browser and is a diagram depicting the operation in .

As shows the screen memory of the browser is divided into a plurality of frames and . In other words the screen is divided into the transaction screen frame and the applet resident frame where the transaction screen frame is set to display 100 and the applet resident frame is set to display 0 . Therefore in the UOP the applet resident frame is not displayed and only the transaction screen frame is displayed.

And as shows when the apparatus is started up e.g. at power ON all the applets are downloaded and embedded in the applet resident frame invisible frame of the browser of the ATM from the server in advance.

Then according to the transaction operation the transaction screen content described by HTML JSP Java Server Page JavaScript is received from the server to communicate with the server the transaction screen is displayed on the UOP by the transaction frame . While the applets in the applet also called Agent resident frame are called up by the method request instruction in the transaction screen content the I O is controlled via the ATM middleware and the control result is responded sent to the transaction screen side via the applet.

In other words the screen of the transaction screen frame transits according to the transaction operation as shown in but the screen of the applet resident frame does not transit except for the apparatus startup time.

 S When the ATM notifies the server of the startup of the apparatus via the network by the power ON of ATM the server transmits HTML JSP for frame division to the browser of the ATM via the network as shown in . As shows JSP is for instructing a frame set FRAMESET and a frame is constructed of a menu frame and sub main frame where the display rates COLS thereof is set to 0 and 100 respectively. So as shows in the browser the menu resident in this case frame is set to display 0 and the sub main transaction in this case frame is set to display 100 .

 S When this setup ends the server downloads all the applets shown in to the resident frame memory of the browser of the ATM . As shows each applet method shown in and are downloaded along with the applet tags. For example the first applet in is an initialization method of the synchronous control Agent in . The browser of the ATM stores this downloaded applet in the resident frame memory and allows it to reside there.

Now processing in the transaction operation will be described. is a flow chart depicting the I O control processing of the browser during the transaction operation of the present invention shows the configuration of the transaction screen of the transaction frame shows the transaction frame and is a diagram depicting the I O control by the transaction screen in .

 S The browser of the ATM receives the image content HTML JSP of the transaction frame from the server . As and show the transaction screen content JSP described in HTML page description language is constructed of the header setup description of the frame name of the transaction screen script column screen content and body and does not include applets. The script column has a JavaScript function for the applet to notify the output information to the screen side a script of the screen content and a specifications column to specify the Agent name to be called up on the screen.

Then the function to be called up by PostAgent is defined by the javascript . And the screen content itself is defined by JavaScript . Here an example of displaying screen Please Wait on the screen is shown. Finally the method of the Agent to be requested from the transaction screen side is specified by javascript . In other words calling up the initialization method of the synchronous control Agent is specified by the description ret parent.frame2.document U agtSync initial.initial .

 S When the screen content of the transaction frame is downloaded to the browser the method of the applet of the resident frame is called up from the transaction frame HTML JSP . As shows the initialization method of the synchronous control Agent is called up by the script C. Along with this screen content is displayed on the screen as described above by the script 

 S The called up initialization method requests the ATM middleware by a command. For example the initialization method issues the initialization command to the bill controller coin controller pass book controller card controller receipt controller journal controller transaction control controller and numeric keypad controller see has each controller execute initialization processing and receives the initialization processing result from each controller as a response.

 S The initialization method which was called up continuously issues the initialization command to the bill controller coin controller pass book controller card controller receipt controller journal controller transaction control controller and numeric keypad controller see and receives a response from these controllers sequentially as each completes processing. Therefore I O units can be controlled in parallel and even a plurality of I O units can be controlled in a short time. The applet calls up the JavaScript function of the transaction frame transaction screen side by the Script description and notifies the output result by an argument. By this the transaction screen processing ends.

In this way the screen frame of the browser is divided into the transaction frame and the resident frame and all the applets are downloaded from the server to the resident frame of the browser of the control unit of the ATM when the apparatus is started up.

And during communication with the Web server for screen transition applets are not transmitted but the transaction screen where the tags for specifying an applet are embedded is transmitted so the applet download time when the transaction screen transits can be decreased. Therefore the wait time for the user when the screen transits can be decreased the operating time of the user can be decreased operation becomes efficient and the operating efficiency of the apparatus can also be improved.

And the above mentioned Agents are disposed in processing units to which a processing unit name is assigned so an ATM with various functions can be supported with the same applet tag and method names merely by slightly changing the content in processing units. In this example this is implemented by changing the input Param in the parenthesis of the method name of the above mentioned method callup SCRIPT. In other words the input Param is constructed of 8 bit information for setting an input flag in each I O controller bill coin pass book card receipt journal transaction control and numeric keypad and the input flag indicates allowing input of the method to the I O controller where 1 is set.

The method called up refers to this input flag and decides the I O controller to which the command is issued. Therefore even an ATM with different functions can execute the same processing using the same applet tag and method names by operating the input flag using the Web server .

For example in the case of the transaction apparatus which does not handle coins the input flag of the coins is set to 0 in advance then issuing a command to the coin controller can be prevented. In the same way in the case of a transaction apparatus which does not handle a pass book the input flag of the pass book is set to 0 in advance then issuing a command to the pass book controller can be prevented.

Also by ParseInt postMode in the parenthesis of the method name of SCRIPT the POST agent is specified within this agent. Therefore POST processing can be smoothly executed based on the control of the Agent.

Now the relationship of the screen content of the Web server user operation screen UOP Agents and methods and I O controllers will be described using the card deposit transaction in as an example.

When the apparatus is started up the Web server downloads applets by JSP Java Server Page and allows them to reside in the browser . Then the Web server issues the screen content where a specified applet name is embedded of the transaction type selection to the ATM . In the ATM the transaction type select screen is displayed on the user operation screen of the UOP by the browser .

And in the ATM the deposit withdrawal preparation method of the synchronous control Agent in is called up by the applet name and method name embedded in the screen content and called up method issues the deposit withdrawal preparation command to the bill controller and coin controller to have them prepare for deposit withdrawal. Both controllers and respond with completion to the deposit withdrawal preparation method when preparation for deposit withdrawal completes.

When the deposit key is pressed on the type select screen of the UOP this is reported to the Web server . By this the Web server transits to the card start processing by JSP and issues the screen content of the insertion processing to the ATM . In ATM the card insertion screen is displayed on the user operation screen of the UOP by the browser .

And in the ATM the card insertion method of the card control Agent is called up by the applet name card control and the method name card insertion embedded in the screen content and the called up method issues the card insertion command by the card controller . The controller operates the card unit by the card insertion command. When the card unit detects insertion of the card and reads the card card insertion completion is responded to the card insertion method by the card control library .

And the card insertion method requests POST of the transaction status card insertion detection and card read data in this case and the POST agent transmits a request to the Web server . In this case the same control is possible by calling up the card pass book insertion method of the synchronous control Agent and setting this input flag in the card controller in advance.

Then the JSP of the Web server issues the screen content of the cash insertion processing to the ATM by a request at the end of card insertion processing. In the ATM the browser displays the cash insertion screen on the user operation screen of the UOP according to the screen content. And by the card control Agent which is an applet name embedded in the screen content and the card insertion which is a method name the bill coin insertion method of the synchronous control Agent is called up and the receive count command is issued to the bill controller and coin controller .

The bill controller and coin controller operate the bill unit and coin unit by the receive count command. The bill and coin units open the insertion port detect inserted bills and coins close the insertion port and count the inserted bills and coins. When counting is over the bill controller and coin controller respond with the completion of receiving counting to the bill coin insertion method. And the bill coin insertion method request POST of the transaction status received number of bills coins total amount and the POST agent sends a request to the Web server .

The JSP of the Web server transits to the deposit processing such as a balance update by a request at the end of cash insertion processing issues the screen content of the computer screen to the ATM and the ATM displays the Please Wait screen on the user operation screen of the UOP .

And the browser calls up the print feed MS write eject preparation method see of the synchronous Agent see by the synchronous control Agent which is an applet name embedded in the screen content and the print feed MS write eject preparations which are method names and issues the MS write command and eject preparation command to the card controller the print command and eject preparation command to the receipt controller and print command to the journal controller .

By this the card unit writes the data on the magnetic stripe of the card and prepares for an eject of the card the receipt printer prints the receipt and prepares for an eject and the journal printer prints the data on the journal. Each controller and responds with completion to the print feed MS write eject preparation method by the completion of command execution.

And the print feed MS write eject preparation method requests POST of the transaction status eject preparation completion in this case and the POST agent sends a request to the Web server .

The JSP of the Web server transits to medium eject processing and issues the screen content of the medium eject to the ATM . In the ATM the browser displays the medium eject screen on the user operation screen of the UOP . And the browser calls up the medium eject method see of the synchronous control Agent by the synchronous control Agent which is an applet name embedded in the screen content and medium eject which is a method name and issues the eject command to the card controller the eject command to the receipt controller and the bell regeneration command to the sound controller which is not illustrated.

By this the card unit ejects the card and the receipt printer ejects the receipt and detects the removal of the card and receipt. And if at least one of them is not removed within a predetermined time a continuous sound is output. Each controller and responds with completion to the medium eject method by a completion of command execution.

And the medium eject method requests POST of the transaction status removal completion in this case and the POST Agent method sends a request to the Web server .

Then the JSP of the Web server receives the request at the completion of removal from the ATM transits to the transaction end processing and issues the screen content of the transaction end to the ATM . In the ATM the end screen is displayed on the user operation screen of the UOP by the browser . The browser calls up the bill coin method see of the synchronous control Agent by the synchronous control Agent which is an applet name embedded in the screen content and the bill coin storage which is a method name and issues the storage command to the bill controller and the coin controller .

By this the bill unit and coin unit store the counted bills and coins in the internal stacker. Each controller and responds with completion to the bill coin method at the completion of command execution. And the bill coin method requests POST of the transaction status storage completion in this case and the POST agent sends a request to the Web server . By this the Web server returns to the above mentioned transaction type select processing and repeats the same processing.

In this way the applets Agents are downloaded from the Web server in advance so at screen transition the screen can transit without downloading the applets. Also the Agents for each processing of transaction processing are embedded in the screen content so operation of a plurality of I O units can be controlled by calling up one method in processing units and a general transaction processing flow can be commonly used for different automatic transaction apparatus.

Therefore screen content for controlling automatic transaction apparatus with different functions and configurations by the Web can be easily created. And parallel control becomes possible and high speed I O unit control can be implemented. By this the wait time of the automatic transaction device for the user can be decreased and the operating rate can be improved. This example was described using the card deposit processing but the present invention can be applied in the same way to withdrawal processing deposit processing and withdrawal processing using a pass book entry processing and balance inquiries.

A method of increasing the speed of screen drawing will be described next. is a diagram depicting a system configuration according to the second embodiment of the present invention is a block diagram depicting the Web browser and I O controller in the configuration in and shows the configuration of the Agent in .

As shows according to this embodiment not only the control Agent applet but also the screen image generation applet are downloaded in advance when the apparatus is started up and are allowed to reside in the browser. And in the subsequent transaction operation the applet related to the screen is specified without transmitting the applet as Web content.

In other words as shows the screen memory of the browser is divided into a plurality of frames and . This means that the screen is divided into the transaction screen frame and the applet screen frame where the transaction screen frame is set to display 100 and the applet resident frame is set to display 0 . Therefore the applet resident frame is not displayed on the UOP and only the transaction screen frame is displayed.

And as shows when the apparatus is started up e.g. at power ON all the applets the screen image generation applet is added in this case are downloaded from the server and embedded in the applet resident frame invisible frame of the browser of the ATM . And when the apparatus is started up the screen image generation applet called DispAgent acquires the button images of the transaction screen and generates the screen image in advance in the resident frame

Then according to the transaction operation the transaction screen content described by HTML JSP Java Server Page JavaScript is received from the server to communicate with the server the transaction screen is displayed on the UOP by the transaction frame the applets of the applet also called Agent resident frame is called up by the method request instruction in the transaction screen content. The called up applet controls I O via the ATM middleware and responds with the control result to the transaction screen side via the applets. When the screen control applet described later in is downloaded to the transaction frame at this time the screen image is acquired from the DispAgent applet of the resident frame and the image is drawn.

In other words as shows the screen of the transaction screen frame transits according to the transaction operation but the applet resident frame does not transit except for the apparatus start up time.

As shows the screen content HTML JavaScript and the Agent applet are downloaded from the WWW server to the Web browser .

The Agent has the control Agent group for controlling each unit the POSTAgent for performing post processing the ViewAgent for constructing a screen and the communication DLL Dynamic Link Library group for communicating with the I O controller via the Java Native Interface and a common API interface . The Agent further has the above mentioned DispAgent .

For the control Agent group and the DispAgent the agents required for transaction control are downloaded in advance when the apparatus is started up and reside in the browser . As described for and later the control Agent is constructed in the processing units of an ATM transaction.

In the case of the operation of the configuration shown in the method of the control Agent is called up with the method name described by JavaScript in the screen content . The method which was called up issues a command to the I O controller via the communication DLL group .

The I O controller operates the corresponding units via the ATM middleware and receives the operation completion response. The I O controller responds with the command execution result to the control Agent . The control Agent requests POST or requests drawing to the POST Agent which performs POST processing or the ViewAgent which updates screens to have them execute post processing or screen update processing.

The DispAgent acquires the button images of the downloaded transaction screen and generates the screen image in advance. Then according to the transaction operation the screen image is acquired from the DispAgent applet of the resident frame and the image is drawn in the case when the screen control applet is downloaded in the transaction frame of the server .

As shows in this example the synchronous Agent has synchronous control initialization mechanical reset bill coin insertion simultaneous medium eject print feed MS write eject preparation deposit return storage forced eject capture unit information acquisition transition status setup two screen display control deposit withdrawal preparation forced replenishment jam reset and card pass book insertion methods.

Each Agent method issues a command to an I O controller that is I O unit indicated by the black dots in and receives the response of the command execution result. For example the initialization Agent method of synchronization control issues the initialization command to the bill controller coin controller pass book controller card controller receipt controller journal controller transaction control controller and numeric keypad controller see has each controller execute initialization processing and receives the initialization processing result from each controller as a response.

In the same way the mechanical reset Agent method of synchronous control issues a mechanical reset command to the bill controller coin controller pass book controller card controller receipt controller and journal controller see has each controller execute the mechanical reset processing and receives the mechanical reset processing result from each controller as a response.

In the same way the bill coin insertion agent method of the synchronous control issues an insertion command to the bill controller and coin controller see has each controller execute the insertion processing and receives the insertion processing result from each controller as a response.

The screen control key control agent is also disposed and as applets in screen units thereof the password number input amount input telephone number input account number input and user recipient name input are disposed.

For example the pattern file A with pattern and high speed mode is a pattern definition displayed in the transaction frame in and defines each button image file storage location display message character font layout position and color. And the image file pattern high speed mode B with the button image by Japanese language shown in the transaction frame in is created in advance by execution screen image generation panel and button layout and button image acquisition embedding at the apparatus startup of the DispAgent .

When the user name recipient name input applet at the resident side is called up by the transaction frame as shown in the resident screen B is acquired and the data is displayed. In this example the user name recipient name input applet is defined as agtDisp.U agtDisp inputName.class by the applet tag in the transaction frame as a screen control applet and the width and height are set to 800 and 600 display . As parameters the pattern name is specified as StrPatternNo and the mode is specified as the high speed mode strFastMode VALUE 1 .

Because of this the pattern file B at the resident side is immediately displayed as shown in . In this example the screen image creation applet and the screen control applet have the same applet name agtDisp.U agtDisp inputName.class and are distinguished by the parameters pattern name strPatternNo 1 and the mode strFastModeValue . However another applet name may be used.

In this way when the apparatus is started up e.g. at power ON the screen generation image applet in addition to the control applet is downloaded and embedded in the applet resident frame invisible frame of the browser of the ATM from the server . And when the apparatus is started up the screen image applet also called DispAgent acquires the button image of the transaction screen and generates the screen images in advance in the resident frame

Then according to the transaction operation in the case of communicating with the server the transaction screen content described in HTML JSP Java Server Page JavaScript is received the transaction screen is displayed on the UOP by the transaction frame applets of the applet also called Agent resident frame are called up by the method request instruction in the transaction screen content and the I O is controlled and the control result is responded to the transaction screen side via the applet through the ATM middleware . At this time when the image drawing applet name is downloaded to the transaction frame the screen image is acquired from the Disp Agent applet of the resident frame and the image is drawn.

Therefore the download time of applets and the download time of button images can be saved when the screen transits so the screen switching time can be decreased. Even if a complicated pattern is displayed for sensation the image switching time can be decreased and this contributes to improving the sensation of the user during operation input.

In the above embodiments the automatic transaction apparatus in was described using the example of an automatic deposit withdrawal machine but the present invention can be applied to other apparatus including a withdrawal machine automatic cash loan machine and automatic issuing machine. The network was described as the Internet but the present invention can be applied to other networks and for the server the script is not limited to JavaScript but other scripts can also be used.

Also the middleware control customized by a common API was described as an example but the present invention can also be used for middleware control without using this common API.

The present invention was described by the embodiments but the present invention can be varied and modified within the scope of the essential character of the present invention and these shall not be excluded from the scope of the present invention.

In this way the screen frame of the browser is divided into the transaction frame and the resident frame and applets are downloaded from the server to the resident frame of the browser in advance when the apparatus is started up. And during communication with the Web server for screen transition applets are not transmitted but a transaction screen where tags for specifying applets are embedded is transmitted so the applet download time at transaction screen transition can be decreased and the operating efficiency of the device improves.

When the apparatus is started up e.g. at power ON the screen image generation applet in addition to the control applet is downloaded to and embedded in the applet resident frame and the screen image generation applet acquires the button images of the transaction screen and generates the screen image in advance. And according to the transaction operation the transaction screen content is received to communicate with the server and the screen image is acquired from the resident fame and the image is drawn when the screen control applet is downloaded to the transaction frame.

Therefore the screen display time of the applets and the download time of button images can be decreased when the screen transits so the screen switching time can be decreased. Also even if a complicated pattern for visual sensation is displayed the screen switching time can be decreased which contributes to improving the visual sensation of the user in operation input.

