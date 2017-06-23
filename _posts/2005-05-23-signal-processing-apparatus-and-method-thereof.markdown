---

title: Signal processing apparatus and method thereof
abstract: A signal processing apparatus performs a signal processing using a plurality of signal processing modules associated with a corresponding plurality of signal processing functions. The plurality of signal processing modules are graphically displayed. One or more of a plurality of available commands are received from a user. A virtual connection state of the plurality of signal processing modules is set that defines connections among the inputs and outputs of the plurality of signal processing modules. The virtual connection state is stored and managed. A sequence of corresponding signal processing functions is determined based on the virtual connection state. Signal processing is performed in accordance with the determined sequence of signal processing functions.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07752189&OS=07752189&RS=07752189
owner: Sony Corporation
number: 07752189
owner_city: 
owner_country: JP
publication_date: 20050523
---
The present invention contains subject matter related to Japanese Patent Application JP 2004 170692 filed in the Japanese Patent Office on Jun. 9 2004 the entire contents of which are incorporated herein by reference.

The present invention relates to a signal processing apparatus that performs in software a signal process composed of a plurality of signal processing units.

With ever higher performance computers can now play back moving images and music the playback of which was difficult before. Moving images and audio signals are currently easily real time processed without using a dedicated signal processing device and dedicated hardware such as a digital signal processor DSP .

A variety of signal processing middleware techniques support the signal processing applications. For example DirectShow is available from Microsoft see http msdn.microsoft.com library default.asp url library en us directx9 c directX htm directshow.asp MATLAB is available from the MathWork see http www.mathworks.com and Max MSP is available from Cycling 74 see http www.cycling74.com products maxmsp.html .

The function of the signal processing application is relatively easily performed by using such middleware techniques. For example audio signals are recorded replayed input and output mixed and subjected to special effects using the signal processing applications. As for moving images signal processing applications having sophisticated editing functions such as non linear editing are provided.

Applications having a plugin structure have been proposed as this type of middle ware see Japanese Unexamined Patent Application Publications Nos. 2001 109628 and 7 302195 . The plugin here refers to a modularized function and is a software application program. Throughout this specification the plugin refers to a software application program forming a signal processing module.

With plugin a user can use a required signal processing module in an add on manner as necessary. The plugin is typically used as a unit. Currently available several new systems provide a complex function by combining a plurality of plugins. Such a complex plugin system is expected to become a majority of systems creating a new value.

 e Controlling a sample accuracy level cannot be performed in audio and image synchronization and in updating of parameters.

Several middlewares overcoming some of the above drawbacks are currently available. However any middlewares free from all the drawbacks are not available. Because some drawbacks are contradictory to each other if one drawback is overcome another is adversely affected . For example it is extremely difficult to overcome drawbacks b and d at the same time.

Some of the drawbacks may present a major obstacle in the incorporation of a plugin into a conventional middleware product.

In accordance with one embodiment of the present invention a signal processing apparatus for performing in software a signal process composed of a plurality of signal processing units includes a plurality of signal processing modules for processing in software the plurality of signal processing units an input command receiving unit for receiving from a user a command to generate or delete the signal processing module and a command to connect the input and output of the signal processing module a signal processing module interconnection unit for setting a virtual connection state of the input and output of each of the plurality of signal processing modules in response to the command received from the user by the input command receiving unit a circuit arrangement information storage and management unit for storing and managing the virtual connection state of the input and output of each of the plurality of set signal processing modules a signal processing sequence determining unit for determining through an initial path search and a loop search a signal processing sequence of the plurality of signal processing modules stored in the circuit arrangement information storage and management unit and a signal processing executing unit for successively causing the signal processing modules to perform the signal process in accordance with the signal processing sequence determined by the signal processing sequence determining unit. The signal processing sequence determining unit searches through the initial path search the signal processing sequence of the plurality of signal processing modules stored in the circuit arrangement information storage and management unit through the initial path search searches through the loop search the signal processing modules forming a closed loop in a circuit arrangement of the plurality of signal processing modules stored in the circuit arrangement information storage and management unit and updates the signal processing sequence determined through the initial path search so that the signal processing module not forming the closed loop is ahead of in processing sequence the signal processing module at the front of the closed loop if the signal processing modules forming the closed loop are detected during the loop search and if the signal processing module not forming the closed loop contained in processing sequence between the signal processing module at the front of the closed loop and the signal processing module at the end of the close loop is detected during the initial path search.

Since the plurality of signal processing modules successively perform the software signal processing with the signal processing sequence fixed each signal processing module is free from an unnecessary process delay that is caused when the signal is processed after being stored in an asynchronization buffer.

The signal processing sequence is arranged to be different from signal processing module to signal processing module or signal processing group to signal processing group. More specifically the signal processing modules forming the closed loop are handled as one group in terms of the signal processing sequence.

Even if the group of signal processing modules not forming the closed loop processes the signals at a time as a feedforward circuit causality in signal processing is assured. More specifically since a function call or a calculation process is performed by packet unit or sample group unit the speed of the signal processing is increased.

In accordance with another embodiment of the present invention a signal processing apparatus for performing in software a signal process composed of a plurality of signal processing units includes a plurality of signal processing modules for processing in software the plurality of signal processing units an input command receiving unit for receiving from a user a command to generate or delete the signal processing module and a command to connect the input and output of the signal processing module a signal processing module interconnection unit for setting a virtual connection state of the input and output of each of the plurality of signal processing modules in response to the command received from the user by the input command receiving unit a circuit arrangement information storage and management unit for storing and managing the virtual connection state of the input and output of each of the plurality of set signal processing modules a signal processing sequence determining unit for determining a signal processing sequence of the plurality of signal processing modules stored in the circuit arrangement information storage and management unit and a signal processing executing unit for successively causing the signal processing modules to perform the signal process in accordance with the signal processing sequence determined by the signal processing sequence determining unit. If the command to generate or delete the signal processing module from the user and or a circuit arrangement update request to update a plurality of circuits based on the connection command of the input and output of each of the plurality of signal processing modules from the user is issued in the middle of the signal process performed by the signal processing executing unit the signal processing sequence determining unit searches a new signal processing sequence and the signal processing executing unit executes the signal process in accordance with the new signal processing sequence.

When the circuit arrangement update request is issued from the user the signal processing sequence determining unit works to search the new signal processing sequence and the signal processing executing unit performs the signal process in accordance with the new signal processing sequence.

Even in the middle of the signal process the circuit arrangement can be updated and the signal process is continuously performed by the updated circuit arrangement.

Even if the signal processing modules are cascaded the signal processing apparatus is free from a signal processing delay. The signal processing with the closed loop is performed in software. The circuit arrangement can be dynamically updated.

A signal processing apparatus of embodiments of the present invention is described below with reference to the drawings.

A general purpose signal processing middleware of the signal processing apparatus is a software signal processor SSP . In the following discussion of the embodiments the signal processing apparatus processes an audio signal.

As shown in the SSP is arranged between an general purpose operating system OS and an application software program. The application software program easily performs a sophisticated signal processing function using the SSP. The SSP in need of no graphical user interface GUI is used as a signal processing engine for an add on device having no display.

The SSP of the signal processing apparatus in accordance with one embodiment of the present invention is a middleware having a graph structure. The SSP is basically constructed of a single computer and may be constructed of a plurality of computers linked via a network.

The signal processing apparatus as the SSP in accordance with the embodiment of the present invention includes two major elements including a graph module hereinafter simply referred to as a graph implemented in software and a plugin module hereinafter simply referred to as a plugin implemented in software.

The plugin is a signal processing module software for performing a signal processing unit such as filtering equalizing gain controlling.

The plugin may include a plurality of input ports and a plurality of output ports. The plugin performs a signal process unique thereto on an audio signal input through an input port and outputs the processed audio signal from the output port therefrom.

A plurality of plugins are connected by connecting the output port of a plugin to the input port of another plugin establishing a virtually connected state rather than establishing a hardware connected state and a complex signal processing function is thus performed. In the connection of plugins the output of one plugin is connected to the input of another plugin but the inputs cannot be connected to each other and the inputs cannot be connected to each other.

The graph serves as a system of the SSP includes a plurality of plugins. In response to an operational input from a user the graph generates or deletes a plugin and performs port to port connections and stores resulting circuit arrangement information. The graph constructs any circuit composed of plugins.

When a signal processing function of the graph is called the graph relays received audio data with time information to plugins and thus inputs or outputs the audio data and additional information to or from the plugin.

The graph also has the feature of the plugin. The graph has input and output ports as the plugin and can connect to another plugin. The graph can include a plurality of plugins. By producing a graph a circuit block graph composed of a plurality of plugins is handled as a single plugin. The graph handled as a single plugin serves as a unitary component containing a plurality of circuits.

As shown in the user generates a root graph first and then generates a circuit composed of a plurality of plugins . Each of the plugins may be selected from plugins stored in the personal computer. The plugins in the stored state thereof are a template in an object oriented class and an actual object is not generated yet.

For example the user selects each of the plugins from the plugins stored in a memory of the personal computer and dynamically generates installs the plugins in the root graph . Objects in the object oriented are now generated. The user then commands the personal computer to connect output ports and input ports of the plugins and connects the root graph to each of the plugins and . The circuit of is thus established.

The root graph holds circuit arrangement information of the internal plugins . When the user calls a signal processing function of the root graph signal processing functions of the contained plugin are recursively called from the signal processing functions of the root graph . Calculation process relating to the signal process are successively performed. The transfer of the recursive signal processing function call is the SSP system itself.

As shown in a graph is a root graph. The root graph includes a branch graph and a plugin . The branch graph includes a plugin a plugin and a plugin . The plugin the plugin and the plugin in the branch graph remain invisible from the root graph and the branch graph appears as a single plugin.

The user first generates a root graph root graph as a root. By calling a plugin generation and deletion function of the root graph the user generates the branch graph and the plugin within the root graph.

By calling the plugin generation and deletion function in the branch graph the user generates the plugin the plugin and the plugin .

To perform a signal process the user calls first a signal processing function of the root graph . The signal processing function of the branch graph and the plugin as the contained plugins are recursively called from the signal processing functions of the root graph . The calculation process is successively performed. The graph has the function of determining the sequence of the recursive signal processing function calls.

In the branch graph the signal processing function of the branch graph is called. The signal processing functions of the plugin plugin and plugin to be contained are recursively called from the signal processing functions of the branch graph .

The SSP system is the above referenced function itself of the graph. The plugin called the graph performs the functions of the system including a generation and deletion process of the plugin a connection process of a plugin to plugin a relay of data from plugin to plugin a synchronization establishing process of the plugin between time information and each of audio information and video information a successive call process of a signal processing function of each plugin and a determination process of determining the call sequence.

The plugin class CPlugin inherits from a plugin interface IPlugin and implements an interface unique to the plugin. The plugin class holds a plurality of input port classes CInputPort and a plurality of output port classes COutputPort .

A plurality of types of plugin classes are available depending on functions. For example a plugin class for performing an addition is an adder plugin class Adder Plugin and a plugin class for performing a multiplication is a multiplier plugin class. These classes are classified as own plugin CMyPlugin . The own plugin class inherits from the plugin class. The user of the middleware can easily generate own plugin using a plugin template.

Graph class is described below. The graph class CGraph includes a plurality of plugin classes. As the plugin class the graph class inherits from the plugin interface IPlugin and the graph class itself is a single plugin class.

The graph class has a recursive layer structure in which one graph contains another graph and plugin therewithin. This structure corresponds to a composite pattern of a design pattern as a typical object oriented design technique.

The graph also serving as a plugin has input and output ports and is interconnected to another plugin. By producing a graph object a circuit block composed of a plurality of plugin objects is handled as a single component object.

Interface API is also defined in both the graph class and the plugin class. An application serving as a client of the SSP middleware can control the object by controlling the API. An operation the user performs on the SSP system means an operation to the two objects.

As shown in a plugin includes a signal processor . Furthermore the plugin can have zero or more input ports and zero or more output ports . The plugin exchanges a signal audio data in this example with another plugin via the input port and the output port . An audio signal of one channel is input or output on a per port basis.

By commanding the plugin to add or delete the input port and the output port to the plugin the number of input ports and output port of the plugin is dynamically changed even in the middle of signal processing. The input port is numbered in the order of addition with an identification number from 0 to N N is any natural number and the output port is numbered in the order of addition with an identification number from 0 to M M is any natural number . The user can select one of the input ports and one of the output ports by specifying the identification numbers.

The plugin includes zero or more parameter storage units parameter buffers . The parameter storage unit can have zero or more parameter. The parameter refers to a variable that sets an amount of effect in the signal process and is input by the user. For example if the plugin is an amplifier the parameter is an amplification gain. The user using the plugin can change the effect of the signal process by modifying the parameter value of the plugin .

Here in this example the parameter is numbered with an identification number from 0 to K K is any natural number . By specifying any identification number the user can modify the content of the parameter buffer at any timing. The parameter input by the user is temporarily stored in the parameter storage unit in the plugin . The parameter is read from the parameter buffer based on information synchronized with sample data given to the system graph and is then transferred to the signal processor . The signal processor uses the parameter in the signal process thereof.

The plugin includes a time information register . The time information register continuously receives time information from the SSP system graph . The time information is a cumulative count of audio input and output samples from the start point of the SSP system at the beginning of the signal processing function of the graph . The cumulative count is the most basic time information of the SSP system.

In the SSP system of the embodiment of the present invention the time information is completely synchronized with the audio input and output data. More specifically the SSP system concurrently supplies the plugin with the audio data and the time information. The time information serves as a time stamp of the data sample of the audio data supplied to the plugin . The plugin can learn detailed time information concerning as to the sequence of a sample at absolute time of target input data to be processed. Since all plugins present in the SSP system are referenced to and synchronized with the absolute time the synchronized signal process at a sample accuracy level is performed as the entire circuit in the SSP system.

The plugin includes the signal processor . The audio data input from another plugin is transferred to the signal processor via the input port . The signal processor performs a signal process unique to the plugin onto the audio data input via the input port while referencing the time information and the parameter value sent to the signal processor . The audio data processed by the signal processor is transmitted to another plugin via the output port .

In synchronization with the time information the signal processor performs the process not only by sample unit but also by packet unit the packet unit composed of a plurality of sample units. In the plugin the signal processing function is called on a per process unit basis. When the signal process is performed by packet unit the call of the signal processing function is performed once per packet. The signal processing speed is increased more as the number of function calls becomes smaller.

When the video data is processed together with the audio data in this embodiment the processing of the audio data is synchronized with a video frame of the audio data in audio video AV synchronization . The audio video synchronization process will be described later. If the processing of the audio data is synchronized with the video frame of the video data vertical synchronization information Vs of the video data is supplied from the system to the plugin together with the time information.

The plugin checks the vertical synchronization signal Vs synchronized with the time information from the system. If the plugin determines that it is the timing of the vertical synchronization signal Vs the plugin performs processes to be performed with video synchronized with audio including an update process of a parameter to be sent to from the parameter buffer to the signal processor at the timing of the vertical synchronization signal Vs. In this way all parameters in all plugins in the circuit arranged in the graph are updated in synchronization with the vertical synchronization signal Vs and the AV synchronization is thus performed.

The graph has the feature of the plugin as previously discussed. The graph includes a signal processor an input port an output port a parameter buffer and a time information register . The signal processor reads plugins contained in the graph . The functions of the input port the output port the parameter buffer and the time information register are identical to the counterparts of the plugin discussed with reference to and are not discussed here. The parameter of the parameter buffer is the one for the graph .

The graph includes a plugin generator and storage unit . The graph can contain zero or more plugins. By commanding the graph to add or delete plugins the user dynamically generates or deletes plugins even in the middle of signal processing. The dynamic generation and deletion of the plugin during signal processing will be discussed in detail later.

In the graph added plugins are numbered in the order of addition with identification numbers 0 J J is an integer number . The user identifies each plugin by the identification number. The graph not necessarily stores the plugins in the plugin generator and storage unit in the order of the identification numbers. The plugins in the graph are stored in the plugin generator and storage unit in a state thereof sorted according to the sequence of sequential computation to be discussed later.

The user can command the graph to connect one plugin to another within the graph . Even in the middle of signal processing the user can dynamically modify the connection state of the output port of one plugin to the input port of another plugin. The user can modify the connection state by specifying the identification number of a plugin and the identification number of a port to the graph . In response to the connection update request from the user the graph updates the connection state of the plugins.

The user commands the graph to start the signal process. When the user calls the signal processing function of the graph the signal processing functions of the plugins contained in the graph from among the signal processing functions of the graph are recursively called. The signal processor of the graph or the plugin in the graph stored in the plugin generator and storage unit in the state thereof sorted in the sequence of the sequential computation performs computation process in accordance with the sequence. The computation process of the graph and the plugin contained in the graph is sequentially performed and a complex signal process of an entire circuit established in the graph is thus performed. The sequence of the sequential computation is determined by the system graph in accordance with the connection structure between the plugins.

If the updating of the circuit arrangement such as the addition and deletion of the plugin and the updating of the connection state of the input port and the output port is performed in response to the user command the graph performs a path search as will be discussed later. The graph automatically determines an optimum sequence of the sequential computation of the plugin and the graph contained therewithin. A branch graph automatically determines in the path search thereof the optimum sequence of the sequential computation of a plugin contained in the branch graph.

As a result of the path search performed by the graph a group of plugins including a branch graph as a plugin are stored in the plugin generator and storage unit in the state sorted according to the optimum sequence of the sequential computation. An algorithm of the path search of the graph will be discussed later.

Upon receiving from the user the plugin generation and deletion command the input and output port connection command and the parameter input command the command input receiver relays the plugin generation and deletion command to the plugin generator and deleter and the input and output port connection command to the plugin connection processor . In response to the plugin generation and detection command and the input and output port connection command the command input receiver activates the path searcher to perform the path search. Upon receiving the parameter input command the command input receiver stores the parameter input to the parameter buffer thereof.

In response to the plugin generation and deletion command from the command input receiver the plugin generator and deleter generates or deletes a plugin. When a plugin is generated the plugin generator and deleter tags the generated plugin with an identification number and transfers plugin generation information containing the identification number to the circuit arrangement information storage and manager . During the plugin deletion the plugin generator and deleter transfers deletion information containing the identification number of a deleted plugin and a deletion request to that plugin to the circuit arrangement information storage and manager .

Upon receiving the plugin connection command from the command input receiver the plugin connection processor transfers to the circuit arrangement information storage and manager connection information concerning the output port and the input port of a plugin specified by the connection command.

The circuit arrangement information storage and manager stores and manages information of a circuit established in the graph based on the generation information the deletion information and the connection information from the plugin generator and deleter and the plugin connection processor .

Upon receiving an activation request responsive to the plugin generation and deletion command or the input and output port connection command from the command input receiver the path searcher activates and executes an algorithm of the path search to be discussed later. Information concerning the sequence of the sequential computation signal processing sequence of the plugins determined as a result of execution of the path search algorithm is then transferred to the signal processor and sequence manager . As previously discussed the signal processor and sequence manager stores in the plugin generator and storage unit the identification information of the plugins arranged in the signal processing sequence as previously discussed.

The signal processing execution unit includes a data relay a signal processing function caller a signal processing time manager and a signal processing synchronization manager as shown in .

The signal processing execution unit starts the signal process with the circuit established in the graph in accordance with a signal processing start command input via the command input receiver . When the user issues a call of the signal processing function of the graph the signal processing function caller reads the signal processing function of the graph issued from the signal processing function storage unit . In response to the user command the signal processing function caller recursively reads the signal processing functions of the plugins in the graph in the sequence of the signal processing functions within the graph.

The data relay in the signal processing execution unit references circuit information stored in the circuit arrangement information storage and manager and transfers the audio data in this case to the plugins in accordance with the circuit arrangement.

The signal processing time manager manages time of data sample unit from the data relay . The signal processing synchronization manager manages a packet synchronization process at the signal processing of a packet unit such as management of the front of a packet and AV synchronization for synchronizing the processing timing of the audio data with the video data frame.

The path searcher receives an update request to update the circuit arrangement in the graph from the command input receiver even in the middle of the signal processing of the signal processing execution unit . In accordance with the updated circuit arrangement the path searcher performs a path search and sends search results to each of the circuit arrangement information storage and manager and the signal processor and sequence manager . The signal processing execution unit performs the signal process in the updated circuit arrangement in accordance with the signal processing sequence based on the updated path search results.

The flow of a generation process of a signal processing circuit in accordance with one embodiment of the present invention is discussed with reference to . As shown in the signal processing circuit is formed in the graph. In the discussion that follows each of the graph and the plugin are referred to as an object. The object thus refers to an object oriented instance and a graph or plugin itself.

Default number of input and output ports of the graphs and plugins during the object generation is listed below. The user is enabled to add or delete an input port and or an output port subsequent to the object generation.

In the discussion that follows a number following the input port and the output port is a port number of the corresponding port and could be one of 0 1 and 2.

The generation procedure of the circuit of signal processing function storage unit is described below with reference to flowcharts of . To simplify explanation user commands and process steps of the signal processing apparatus are shown to correspond to each other. The signal processing apparatus displays on a display a screen corresponding to the user command input and the user enter an operational input while viewing the display screen.

The user issues a command to generate an object as a graph root graph user command 1 . The signal processing apparatus generates and registers the root graph step S .

The user commands the object as the graph to generate an object as a plugin user command 2 . The signal processing apparatus generates the plugin in the graph with the plugin generation and deletion function of the generated graph step S . The path searcher in the graph executes a path search in response to the plugin generation command step S .

The user commands the object as the graph to generate an object of a plugin user command 3 . The signal processing apparatus generates and registers the plugin in the graph using the plugin generation and deletion function of the graph step S . The path searcher in the graph executes a path search in response to the plugin generation command step S .

The user commands the object as the graph to generate an object of a graph branch graph user command 4 . The graph generates and registers the branch graph therewithin using the plugin generation and delection function thereof step S . The path searcher in the graph performs a path search in response to the plugin generation command step S .

The user commands the object as the graph to generate an input port 0 external user command 5 . In response the signal processing apparatus generates and registers the input port 0 external as a function of the generated branch graph in the branch graph step S . In the branch graph an output port 0 internal corresponding to the input port 0 external is automatically generated step S . The path searcher in the graph executes a path search in response to the port generation command step S .

The user commands the object as the graph to generate an output port 0 external user command 6 . In response the signal processing apparatus generates and registers as a function of the generated branch graph an output port 0 external in the branch graph step S . In the branch graph an internal input port 0 internal corresponding to the output port external is automatically generated step S . The path searcher in the branch graph performs a path search in response to the port generation command step S .

The user commands the object as the branch graph to generates an object as a plugin user command 7 . The branch graph then generates and registers the plugin in the branch graph using the plugin generation and deletion function thereof step S . The path searcher in the branch graph performs a path search in response to the plugin generation command step S .

The user commands the object as the branch graph to generate an object as a plugin user command 8 . The branch graph generates and registers the plugin in the branch graph using the plugin generation and deletion function thereof step S . The path searcher in the branch graph performs a path search in response to the plugin generation command step S .

The user commands the object as the branch graph to generate an object as a plugin user command 9 . The branch graph generates and registers the plugin in the branch graph using the plugin generation and deletion function thereof step S . The path searcher in the branch graph performs a path search in response to the plugin generation command step S .

The user commands the object as the graph to connect the output port of the plugin to the input port 0 external of the branch graph user command 10 . The plugin connection processor in the graph connects the output port 0 of the plugin to the input port 0 external of the branch graph and registers the connection step S . The path searcher in the graph performs a path search in response to the port connection command step S .

The user commands the object as the graph to connect the output port 0 external of the branch graph to the input port 0 of the plugin user command 11 . The plugin connection processor in the graph connects the output port 0 external of the branch graph to the input port 0 of the plugin and registers the connection in the graph step S . The path searcher in the graph performs a path search in response to the port connection command step S .

The user commands the object as the branch graph to connect the output port 0 internal of the branch graph to the input port 0 of the plugin user command 12 . The plugin connection processor in the branch graph connects the output port 0 internal of the branch graph to the input port 0 of the plugin and registers the connection in the branch graph step S . The path searcher in the branch graph performs a path search in response to the port connection command step S .

The user command the object as the branch graph to connect the output port 0 of the plugin to the input port 0 of the plugin user command 13 . The plugin connection processor in the branch graph connects the output port 0 of the plugin to the input port 0 of the plugin and registers the connection in the branch graph step S . The path searcher in the branch graph performs a path search in response to the port connection command step S .

The user commands the object as the branch graph to connect the output port 1 of the plugin to the input port 0 of the plugin user command 14 . The plugin connection processor in the branch graph connects the output port of the plugin to the input port 0 of the plugin and registers the connection in the branch graph step S . The path searcher in the branch graph performs a path search in response to the port connection command step S .

The user commands the object as the branch graph to connect the output port 0 of the plugin to the input port 1 of the plugin user command 15 . The plugin connection processor in the branch graph connects the output port 0 of the plugin to the input port 1 of the plugin and registers the connection in the branch graph step S . The path searcher in the branch graph performs a path search in response to the port connection command step S .

The user commands the object as the branch graph to connect the output port 0 of the plugin to the input port 0 internal of the plugin user command 16 . The plugin connection processor in the branch graph connects the output port 0 of the plugin to the input port 0 of the plugin and registers the connection in the branch graph step S . The path searcher in the branch graph performs a path search in response to the port connection command step S .

The circuit of is thus generated in the graph through the above procedure. When the user commands the graph to start the signal process the signal processes are sequentially performed by the plugins in accordance with the signal processing sequence determined by the path search.

The signal processing apparatus of the present embodiment performs a total of 16 user commands on the graph object. The graph structure changes each time the procedure responsive to each user command is performed. The system graph automatically performs the path search algorithm at each procedure. When the generation process of the circuit arrangement is complete the path search is also complete and the signal processing sequence is determined.

The plugin generator and storage unit in the graph stores the plugins in the state thereof sorted in the optimum sequence of the sequential computation in accordance with the path search algorithm. As shown in the flow of the signal process execution is discussed on the assumption that the plugins are already stored in the optimum sequence.

 3 The signal processing function of the plugin from among the signal processing functions of the graph is performed.

 4 The signal processing function of the branch graph from among the signal processing functions of the graph is performed.

 4 1 The signal processing function of the plugin from among the signal processing functions of the branch graph is performed.

 4 2 The signal processing function of the plugin from among the signal processing functions of the branch graph is performed.

 4 3 The signal processing function of the plugin from among the signal processing functions of the branch graph is performed.

 5 The signal processing function of the plugin from among the signal processing functions of the graph is performed.

In the above procedures only step 1 of commanding the graph to start the signal process is issued by the user. The other steps 2 5 are automatically performed by the graph and the branch graph .

The path search algorithm as the process function of the graph in accordance with the present embodiment is described below.

The path search algorithm forms a major portion of the system of the present embodiment. The plugins contained in the graph are sorted according to the optimum sequence using the path search algorithm. During the signal process the signal processing functions unique to the respective plugins are called and executed in the sequence applied in the sorting.

If the signal process is performed by a signal process device such as a digital signal processor DSP a computing circuit such as a arithmetic logical unit ALU in the DSP typically performs sequential computation to perform the desired signal process. The sequential process performed by the DSP is also applicable to the computation performed by a central processing unit CPU of the middleware of the present embodiment.

More specifically a given circuit is treated as a signal flow graph in accordance with the present embodiment. The sequence of the sequential computation is searched for in the graph. The sequential computation is performed in the sequence as a result of search. The SSP as the middleware of the present embodiment has a path search algorithm unique thereto.

Using the path search algorithm any digital circuit arrangement containing a feedback loop can be fully emulated. The SSP thus performs dynamic circuit arrangement updating which no currently available hardware circuits can perform.

In accordance with the present embodiment the path search algorithm determines the sequence of the sequential computation as to which plugin to start with in the signal process of the signal processing circuit composed of the plugins connected in a graph. The circuit established in the graph as a target of the path search may contain a feedback loop circuit.

The path search algorithm is held by the graph and the plugin generator and storage unit in the graph executes the path search algorithm.

When the user performs an operation on the graph to modify the graph structure the graph automatically performs a path search and determines a new sequence of the sequential computation. If a plurality of graphs are contained in the graph any graph to be updated performs the path search independent of the other graph. The path search is very simple and completed within a short period of time.

In the path search algorithm of the present embodiment a plugin as an element of the circuit arranged in a graph is treated as a node. The node is an element in the graph theory. In the present embodiment the circuit is expressed by an arrow headed directed edge that connects one node to another. An arrow directed to a node is defined as an input to that node and an arrow leaving from a node is defined as an output from that node. The path search algorithm of the present embodiment scans the nodes connected in a graph thereby determining signal processing order. The path search algorithm of the present embodiment is also referred to as a node scan algorithm.

The node scan algorithm is composed of an initial path search algorithm primary node scan algorithm serving as a base for path searching and a loop search algorithm for performing a search also paying attention to loop information of paths.

In accordance with the present embodiment as shown in the initial path search algorithm is performed first in the node scan algorithm step S . In succession to the completion of the initial path search algorithm step S the loop search algorithm is performed step S .

The initial path search algorithm sets up propositions to be solved and solves the propositions under the following search conditions .

The nodes arranged in a graph are sequentially scanned. A scan sequence satisfying that all nodes are scanned at a single cycle under the following conditions is desired. It is not necessary that nodes to be scanned are directly connected to each other and it is perfectly acceptable that the nodes are scanned with some nodes skipped.

 d If the output of a node B connected to the input of a node A is fixed the input of the node A is fixed.

The nodes are assigned unique numbers in sequence as identifiers. The identification numbers are referred to as node numbers. The node number is not any number but is the number assigned in the sequence of object generation as the plugin. The plugins are divided into a latency type plugin LTP and a non latency type plugin NLTP . The LTP is a delay element and causes a delay at least one sample. The NLTP is a gate element and causes no delay.

A first node is checked step S and it is determined in step S whether the first node is assigned the node sequence number hereinafter referred to as a node index . If it is determined that the first node is assigned with the node index it is also determined in step S whether all nodes are assigned with node indices. If it is determined that all nodes are assigned the respective node indices the process routine ends.

If it is determined in step S that all nodes are not yet assigned respective node indices a next node is checked step S . The process routine returns to step S to repeat step S and subsequent steps.

If it is determined in step S that the first node is not assigned the node index it is determined in step S whether the first node is to be scanned unconditionally in other words whether the first node as a plugin is an LTP.

If it is determined in step S that the first node is not to be scanned unconditionally it is determined in step S whether all inputs to the node are fixed. If it is determined in step S that all inputs are not fixed a next node is checked step S . The process routine returns to step S to repeat step S and subsequent steps.

If it is determined in step S that the node is to be scanned unconditionally or if it is determined in step S that all inputs to the node are fixed the output of that node is fixed after scanning that node step S . The input of a node connected to the node is fixed step S . That node is then assigned a node index step S .

If it is determined in step S whether all nodes are assigned respective node indices. If it is determined that all nodes are assigned respective node indices the process routine ends.

A specific example of the node index assignment in accordance with the initial path search algorithm is described below with reference to . illustrates a circuit arrangement of the graph. As shown target nodes are seven namely nodes No. No. . The nodes No. and No. are LTPs. The initial path search algorithm functions as discussed below. Nodes No. through No. are checked in sequence. Nodes No. through No. are checked in one cycle and the check cycle is repeated until all nodes are scanned.

One check cycle of the nodes is thus completed. A second check cycle is performed on nodes that have not yet scanned successfully with any output thereof unfixed as below.

 1 Node No. is scanned successfully because all inputs 0 and 1 are fixed. The output 0 of node No. is thus fixed.

 2 Node No. is scanned successfully because all inputs 0 1 and 2 are fixed. The outputs 0 1 and 2 of node No. are fixed.

 3 Node No. is scanned successfully since the input 0 thereof is fixed. The output of node No. is thus fixed.

All nodes are thus scanned with all outputs thereof fixed. The search operation is thus completed. In this case the search operation is completed after two check cycles.

If the nodes are assigned the numbers in the order of fixing in the search procedure of the initial path search algorithm the path search results are determined. The sequence number of each new node is the node index. lists the search result of the circuit arrangement of the graph of .

The plugins in the graph are stored in the plugin generator and storage unit in the order of node indices. Each time the path search algorithm is executed the storage order of the plugins in the plugin generator and storage unit is updated. During the signal processing the graph calls the signal processing function of each plugin in the sequence of the node indices thereby performing a desired signal process.

In the initial path search algorithm the nodes are checked to second to third cycles until the solution to the proposition is determined. In the first search cycle at least one node that can be scanned is found.

There is one exception. If an LTP as a delay element is not contained in a feedback any node that can be scanned cannot be found in a first search cycle. That is an abnormal case in the circuit arrangement.

The digital signal processing theory requires that at least one delay element be contained in a feedback loop to satisfy the principle of causality. In accordance with the initial path search algorithm of the present embodiment the above exception occurs if the user produces a circuit without following the above basic requirement.

In accordance with the initial path search algorithm of the present embodiment the occurrence of the exceptional case is used to trigger an error message. More specifically if the user produces a feedback circuit containing no delay element the above described exceptional case of the path search occurs in the initial path search algorithm. If the exceptional case is detected the system warns the user to reconstruct the circuit.

The loop search algorithm is described below. The loop search algorithm lightens workload on a CPU during signal processing. Assuring real time property in the signal processing is an important technique.

The search results obtained in the initial path search algorithm provide a desired circuit for signal processing. However the search results obtained in the initial path search algorithm from a circuit arrangement including a feedback loop are not very much advantageous in terms of speed performance.

The circuit arrangement including a feedback loop must satisfy the principle of causality of the digital signal processing theory that an output cannot be fixed in a state that an input remains unfixed. For this reason the signal process of the plugin must be successively performed on a per sample unit basis in a circuit including a feedback loop. More specifically on a per sample unit basis the inputting and outputting of the audio data to and from the plugin and the signal process to the plugin must be performed.

Here a function call to be performed at each signal process becomes a problem. In software process the function call typically increases a workload on a CPU thereby becoming costly. In the real time software signal processing the smaller the number of function calls the higher the process performance speed becomes. A method of reducing the number of function calls is needed to heighten speed performance.

A process of handing a plurality of data samples for example a packet unit as one unit is available as a typical method of reducing the function calls. Rather than processing the data one sample by one sample the system processes the data block by block each block containing a predetermined number of data samples. If a packet size is 1024 samples the audio data of 1024 samples are unified into one block and are processed in response to one function call. The number of function calls is reduced in this way.

If the circuit includes a feedback loop the function call must be performed on a per sample unit basis. The packet process cannot be performed.

This drawback is overcome by performing the loop search algorithm subsequent to the initial path search algorithm.

A node forming a loop in the circuit including the feedback loop is typically part of the entire circuit. Taking advantage of this fact a group of nodes forming a loop is separated from a group not forming a loop in the signal processing sequence in the loop search algorithm of the present embodiment. The packet process is enabled in the group of nodes not forming the loop to achieve high speed performance in the entire signal processing.

In the circuit of the nodes forming the loops are three namely node No. node No. and node No. and are less than half the whole number of nodes namely .

The nodes forming the loops are processed on a per sample unit basis while the remaining nodes are processed on a per packet unit basis. Reduction in speed performance is thus limited to minimum. The smaller the ratio of the nodes forming the loops in the entire circuit the more efficiently the reduction in speed performance is controlled.

If it is determined in step S whether a node not forming a loop is interposed between nodes forming a loop in the signal processing sequence determined in the initial path search algorithm.

If it is determined in step S that a node not forming a loop is interposed between nodes forming a loop in the signal processing sequence the signal processing sequence is modified in step S so that the node not forming the loop precedes the nodes forming the loop. In other words the nodes are re assigned the node indices.

If it is determined in step S that a node not forming a loop is not interposed between nodes forming a loop in the signal processing sequence the loop search algorithm ends.

If the loop search algorithm is executed the signal processing sequence is modified in step S so that a node not forming a loop precedes a node forming a loop.

Even with the modified signal processing sequence the proposition of the initial path search algorithm must be satisfied. It is acceptable that whether the proposition of the initial path search algorithm is satisfied or not is checked subsequent to the modification of the signal processing sequence in the loop search algorithm. Alternatively such a check operation is eliminated by placing the node not forming the loop ahead of a front node of the loop in the signal processing sequence. The above referenced sequence modification keeps the sequence of signal processing in a correct state.

As shown in node No. and node No. are LTPs and have the feature that the output thereof is fixed even if the input thereof remains unfixed. Taking advantage of this feature node No. and node No. may be processed subsequent to node No. .

As shown in the signal processing sequence is modified in the loop search algorithm so that node No. forming no loop is third in the signal processing sequence ahead of node No. as a front node forming the loop.

The nodes forming the loops are grouped as hatched in . The node group forming the loop is thus localized in the signal processing sequence.

The number of function calls is thus minimized by performing the signal process in the signal processing sequence of as described below.

 1 The nodes having node indices 1 through 3 are outside the loop and are processed on a per packet unit basis.

 2 The nodes having node indices 4 through 6 are within the loops and are processed on a per sample unit basis.

 3 The node having index number 7 is outside the loop and is thus processed on a per sample unit basis.

If the signal process is performed as described above the number of function calls is reduced and a speed performance drop in the signal process is avoided. For example a signal process with a packet size of 1024 samples is described below.

In the above referenced signal processing steps of 1 through 5 a total of 3076 function calls are required to process 1024 sample signals.

If all nodes were processed on a per sample unit basis a total number of function calls would become 7168. The node scan algorithm of the present embodiment is performed to localize the node group forming the loop. The function call is performed on a per sample unit basis in only the node group. One function is performed on a per packet unit basis in the nodes not forming any loop. In the above described example about 57 percent of the function calls is thus eliminated.

In accordance with the system of the present embodiment the packet size can be dynamically modified rather than being fixed.

As previously discussed the signal processing apparatus of the present embodiment can calculate a sample accuracy and can perform the AV synchronization at the sample accuracy. Known middlewares are subject to a delay proportional to the number of connections if a plurality of plugins are cascade connected and cannot process all plugins in synchronization.

In contrast in accordance with the present embodiment no increase is caused in delay in any connection and the plugins are operable in synchronization at the sample accuracy. The AV synchronization is thus performed at the sample accuracy.

For AV synchronization the system graph attaches a V synchronization flag as the vertical synchronization signal Vs of the audio data to the time information. Since the time information is updated on a per sample unit basis the V synchronization flag is attached to all samples. The V synchronization flag becomes 0 at the timing of a front frame and becomes 1 in the rest of time.

The V flag is synchronization pulse information for associating the frame of video with a sample of the audio data. For example if video information is 30 frames s and the sampling frequency of the audio data is 48 kHz and the number of samples of the audio data per frame of the video information is 48000 30 1600 samples frame . To process the audio data per packet unit the packet fails to match the frame if the number of samples per packet is 1024. The AV synchronization is performed using the V synchronization flag.

The system graph calculates beforehand the number of audio data samples per frame of the video information. When the audio data is input to a plugin in the system graph the V synchronization flag is also input together with sample time information of the audio data to the plugin. The V synchronization flag indicates whether the sample time is at the front of the video frame.

Upon detecting from the V synchronization flag that the input audio data is at the front of one frame of the video information each plugin performs an AV synchronization process by updating the internally stored parameter in synchronization with the front of the video frame.

As a precondition to the AV synchronization the time information of the sample unit from the system graph must associated with the V synchronization flag of the video frame by any method. In the signal processing apparatus of the present embodiment the start time of signal process is defined as a front of the video frame and time information subsequent to the start time is associated with the V synchronization flag using the number of audio data samples per one frame of the video information calculated beforehand by the system graph .

In synchronization with the inputting of the audio data sample to the plugin absolute time count t is acquired as the time information input to the plugin from the system step S . The system writes the time information on a per sample unit basis. The V synchronization flag attached to the time information is also acquired from the system.

Depending on whether the V synchronization flag on a per sample unit basis is 1 the plugin checks whether the V synchronization flag is true in other words whether it is at the front of the video frame step S . If it is determined that the V synchronization flag is true the parameter is updated in the AV synchronization process step S . The signal process is thus performed at time t step S .

If it is determined that the V synchronization flag is not true the signal process is thus performed at time t step S without updating the parameter step S .

A next absolute time count t 1 input in synchronization with the inputting of a next audio sample to the plugin is acquired step S . The same process as steps S S is repeated steps S S . In synchronization with the inputting of the sample the above process is repeated.

In accordance with the signal processing apparatus of the present embodiment the graph structure is modified in response to the graph update command from the user even in the middle of the signal processing. Since the path search algorithm node scan algorithm is performed even in the middle of the signal process the circuit arrangement is modified.

The user can thus modify the circuit arrangement of the signal processing apparatus of the present embodiment to a new one while listening to a sound processed and output by the signal processing apparatus. The signal processing apparatus of the present embodiment finds applications in live playing apparatuses.

The signal process is performed at time t step S . Even in the middle of the signal process the graph determines whether one of the plugin generation and deletion command the input and output port generation and connection command and the graph modification command is issued step S .

If it is determined in step S that the graph modification command is issued the graph performs the path search while re structuring the circuit arrangement of the graph step S . The signal process at time t 1 is performed step S . If it is determined in step S that the graph modification command is not issued processing proceeds to the signal process at time t 1 step S .

As previously discussed parameter attributes may be entered in the signal process of the signal processing apparatus of the present embodiment. The parameter herein refers to a multiplication factor in the case of a multiplier.

Ordinary middlewares permit the parameter to be intermittently modified in response to a parameter setting function from the user. The signal processing apparatus of this embodiment has a structure identical to a known one shown in . More specifically the plugin includes the parameter storage unit as shown in . The parameter storage unit is designed to allow the setting to be modified intermittently in response to the parameter setting function from the user. As shown in a signal processor is a gain control amplifier and the gain of the signal processor is controlled by a parameter stored in a parameter storage unit .

In the arrangement of the parameter cannot be varied continuously and accurately on a per sample unit basis. Widely available operating systems OS s have difficulty in assuring real time feature to one sample time of about 20 microseconds of the audio data sample and intervals between function calls become as long as several tens of milliseconds. Even if the real time feature is assured on an ordinary OS an accuracy level of several milliseconds to several tens of milliseconds is the maximum level achievable. Because of time variations in software timing control of parameter modification function cannot be performed to within the sample accuracy level on the order of several microseconds.

In accordance with the present embodiment the parameter setting method is improved to accurately vary the parameter to within one sample accuracy. More specifically the parameter stored in the plugin is not set in response to the function call from the user. The graph is provided with the function that assigns the function call to the input port of the plugin. A new parameter setting method is implemented. The new parameter setting method is referred to as parameter binding.

The parameter in the plugin is not updated in response to the setting function call from the user but in response to the audio data value input to the input port 1. The audio data value as is becomes a parameter value and updated by sample unit.

In this case there is no particular distinction between the parameter and the audio data. Since the audio data are synchronized with each other at the sample accuracy in accordance with the present embodiment synchronization between the parameter updating and the audio data is maintained. For example the user generates a parameter signal synchronized with the audio data and inputs the parameter signal to the input port connected to the parameter storage unit of a desired plugin. The parameter modification is performed in synchronization with the audio data at the sample accuracy level.

The audio data functioning as the parameter is input to the added input port step S . The registration of parameter binding has been completed.

The registration and release of the parameter bind can be performed at any timing even in the middle of signal processing.

The signal processing apparatus of the present embodiment is implemented by a single computer and the signal process is performed on the single computer. By sharing the signal process among a plurality of computers connected via a network CPU workload is distributed on a real time basis.

Distributed processing is implemented using a distributed object technique as one of widely available computing techniques. For example techniques called COM DCOM component object model distributed component object model and COBRA common object request broker architecture are those techniques.

The case of COM DCOM technique mainly used on Windows based OS s is described below. The objects of the plugin in the middleware in the present embodiment are implemented as COM objects. The COM object is an object oriented component model and is characteristic of location transparency. The location transparency refers to a function that a COM object is generated on a remote computer as if a COM object were generated on a local computer.

With the location transparency an object is generated using the same operation regardless of the local computer or the remote computer. The object of the plugin as the COM object is consistently generated on a plurality of computers without being aware of a network. Not only the generation of the plugin but also other processes are performed using a consistent operation regardless of the local computer or the remote computer.

For example an audio input and output plugin object is arranged on the local computer while an echo plugin object is arranged on the remote computer and a whole circuit is formed of the two objects.

With reference to the flow of the circuit production is discussed. The user produces a circuit on the local computer as if using only the local computer . The user is aware of the remote computer in only a portion of the whole process.

 1 The user produces an object as the root graph . The object as the root graph is generated on the local computer .

 4 The user commands the object as the root graph to generate an object as a plugin . An identifier of the remote computer is attached to a plugin generation function.

 6 The user commands the object as the root graph to connect an output port 0 of the plugin to an input port 0 of the plugin .

 7 The user commands the object as the root graph to connect an output port 0 of the plugin to an input port 0 of the plugin .

 8 The user commands the object as the root graph to connect an output port 0 of the plugin to an input port 0 of the plugin .

 9 The user commands the object as the root graph to connect an output port 0 of the plugin to an input port 1 of the plugin .

The circuit is completed. The user is aware of the remote computer in step 4 only. The execution of the signal processing described above is not different from that performed by the local computer only.

With signal processing stages cascaded a circuit causing no increase in process delay in the software signal process is provided. Any digital signal processing circuit containing a feedback structure is generated.

The circuit arrangement of a digital signal processing circuit is dynamically updated. In this case circuit elements dynamically updatable includes the addition and deletion of the plugin the connection state between the plugins the addition and deletion of the input and output ports of the plugins the parameter modification and parameter binding of the plugin and parameters relating to the signal process such as a packet size and a sampling frequency during the signal process.

A product containing a dynamically updatable circuit is produced by implementing the middleware of the signal processing apparatus of the present embodiment.

The produced signal processing circuit is stored in a file for later use. By exchanging such a file the circuit is exchanged or reused.

Even if the signal processing circuit includes a circuit arrangement having a feedback loop the number of signal processing function calls is minimized. As a result a CPU workload required to perform the real time signal process is reduced.

The synchronization between the updating of the circuit parameter and the audio data is controlled to within the sample accuracy. The parameter value is updated using the audio data parameter binding function .

The real time distributed process is performed using a network. A plurality of circuits over the network are operated in synchronization on a real time basis.

It should be understood by those skilled in the art that various modifications combinations sub combinations and alterations may occur depending on design requirements and other factors insofar as they are within the scope of the appended claims or the equivalents thereof.

