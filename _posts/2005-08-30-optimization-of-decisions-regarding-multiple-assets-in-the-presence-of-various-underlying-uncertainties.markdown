---

title: Optimization of decisions regarding multiple assets in the presence of various underlying uncertainties
abstract: A client-server based system for building and executing flows (i.e., interconnected systems of algorithms). The client allows a user to build a flow specification and send the flow specification to the server. The server assembles the flow from the flow spec and executes the flow. A decision flow builder allows the user to build a flow targeted for the analysis/optimization of decisions (modeled by decision variables) regarding a plurality of assets in view of various underlying uncertainties (modeled by uncertainty variables). The user may specify a global objective (as a function of asset level statistics) as well and one or more constraints for the optimization. The flow may account for inter-asset correlations and inter-asset dependencies between uncertainty variables, and, inter-asset constraints between decision variables.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08457997&OS=08457997&RS=08457997
owner: Landmark Graphics Corporation
number: 08457997
owner_city: Houston
owner_country: US
publication_date: 20050830
---
This application claims the benefit of priority to U.S. Provisional Application No. 60 676 484 filed on Apr. 29 2005 entitled Extensible Decision Management System invented by David Heath.

This invention relates generally to the field of decision uncertainty and optimization analysis and more particularly to a system and method for optimizing decisions regarding a system of assets in the presence of uncertainty.

There are a wide array of activities that are typically performed in the process of exploring developing and operating oil and gas fields assets e.g. activities such as 

While these activities require large expenditures of capital these expenditures are viewed as investments in the hope of gaining revenues e.g. from the sale of oil and gas that significantly exceed the total amount of the expenditures. Thus these activities may be referred to herein as investment activities.

Furthermore these decisions must be made in the context of a whole host of fundamental uncertainties e.g. uncertainties in factors such as 

Any way one makes a decision these fundamental uncertainties imply uncertainties in rewards such as production volume revenue and profit. Therefore there exists a need for systems and methods capable of assisting one in making decisions each decision having a range of available options regarding oil and gas field exploitation in view of fundamental uncertainties.

In one set of embodiments a method for optimizing decisions regarding a plurality of assets may involve the operations of 

Furthermore the method may involve displaying a graphical representation of at least a subset of the decision vectors of the reference set.

The optimization may be realized by any of variety of optimizers especially stochastic optimizers. For example the optimizer may employ a tabu search procedure and or a scatter search procedure.

In some embodiments a subset of the one or more quantity values for the asset may be computed using input data e.g. data from the data set as well as output data of the set of algorithms of the asset.

The information referred to in a above may specify one or more functional dependencies among the uncertainty variables. The operation c1 of generating the uncertainty vector may be performed in a manner that respects the one or more functional dependencies among the uncertainty variables.

The information may also specify one or more correlations among the uncertainty variables. In this case the operation c1 of generating the uncertainty vector respects said correlations. The uncertainty variables may include two or more subsets associated with two or more of the assets respectively. The correlations may include correlations between uncertainty variables across different assets.

The information may also specify one or more constraints on the decision variables. In this case the operation b of generating the decision vector may respect the one or more constraints on the decision variables.

The information may also specify one or more functional dependencies between the decision variables. In this case the operation b of generating the decision vector may respect the one or more functional dependencies between the decision variables.

The operation c of executing the evaluation process on the decision vector may produce a corresponding value of an auxiliary function in addition to said global objective value. Thus the operation c may additionally include 

The optimizer may use the global objective values and the auxiliary function values corresponding to the plurality of decision vectors in said repeated updating of the reference set in order to optimize the objective function subject to one or more constraints.

The user may specify the structure of the one or more constraints. For example the user may specify a constraint on a functional combination of the auxiliary function and the global objective. The functional combination may itself be specified by the user. As another example the user may specify a constraint on the auxiliary function.

The operation c8 may include combining the second subset of the statistics according to a linear combination whose coefficients are specified by said information.

Each of the decision variables has an associated set of attainable values representing possible outcomes of a corresponding decision. Furthermore each of the uncertainty variables has an associated set of attainable values. The attainable value sets may be finite sets of numeric values data structures programs etc. The attainable value sets may also be intervals of the real number line or more generally user specified regions in an n dimensional space where n is a positive integer.

In one embodiment the method may also involve displaying a plot of the global objective value versus auxiliary function value for each of said plurality of decision vectors.

The operation e of storing may include storing the decision vectors of the plurality of decision vectors along with their corresponding global objective values and the corresponding auxiliary function values in a database in the memory.

A graphical representation of a subset of the plurality of decision vectors that corresponds to a point on the optimal value locus may be displayed in response to a user s selection of the point.

A user may specify the plurality of assets the decision variables and the uncertainty variables for each asset and a set of one or more algorithms for each asset. The decision variables are variables that are subject to optimization. The uncertainty variables are variables that are randomly or pseudo randomly explored in order to create variation in the input supplied to algorithms of each asset.

The set of one or more algorithms for at least one of the assets may include an algorithm to estimate oil and gas production over time and economics for the asset. The algorithm to estimate oil and gas production over time may be 

Furthermore the set of one or more algorithms for at least one of the assets may include one or more of 

In another set of embodiments a method for optimizing decisions regarding a plurality of assets by means of executing program code on a first computer e.g. a server computer may involve the operations of 

The decision variables may include numeric valued decision variables and scenario valued decision variables. A numeric valued decision variable is a decision variable whose attainable values are numeric values. For example a single valued decision variable may be used to represent the possible outcomes for the number of wells to be drilled in a given asset. A scenario valued decision variable is a decision variable whose attainable values are data structures describing corresponding scenarios. For example a scenario valued decision variable may be used to represent a decision between multiple scenarios each scenario representing a different set of choices for the number of wells in a given asset the drilling schedules for the wells and the drilling geometries for the wells.

The global objective value may be computed based on output data generated by one or more algorithms acting on the decision variables. In some embodiments the global objective value may be total oil or gas reserves or production or net present value. In another embodiment the global objective value may be a statistic e.g. the mean of the reserves or net present value. In some embodiments other statistics of the global objective value are required to be met e.g. a standard deviation or any quantile value.

Some of the one or more quantities computed for each asset may be computed based on input data e.g. data of the corresponding iteration data set as well as output data from the set of algorithms of the asset.

The first computer and the one or more second computers may be coupled through a computer network e.g. a local area network an intranet a wide area network the Internet etc.

The operation of dispatching the iteration data sets induces distributed execution of the sets of algorithms on the iterations data sets on a plurality of the second computers. The second computers may be organized into a grid structure.

In one embodiment a subset of the iteration data sets may be executed locally by the first computer depending in part on how much processing bandwidth is available on the first computer.

The information may be collected from a user by a process executing on a client computer and sent to the first computer by this process.

In yet another set of embodiments a method for optimizing decisions regarding a plurality of assets may involve the operations of 

The execution of the optimizer attempts to optimize i.e. maximize or minimize the global objective subject to a constraint on one or more of the auxiliary function and the global objective.

By employing a global objective which is a functional combination e.g. a linear combination with positive weighting coefficients various method embodiments described herein may be configured to enable the optimization of decisions regarding a plurality of assets taken together. The method embodiments may handle dependencies of uncertainty variables including dependencies across different assets. Furthermore the method embodiments may allow a user to specify constraints on the decision variables including constraints on decision variables across different assets.

Any or all of the method embodiments described herein may be implemented in terms of program instructions. The program instructions may be stored on any of various kinds of computer readable memory media such as magnetic disk magnetic tape semiconductor memory of various kinds bubble memory CD ROM etc.

The program instruction may be stored into the memory of a computer system or the memories of a set of computer systems . A processor of the computer system may be configured to read and execute the program instructions from the memory and thereby implement the method embodiment s .

The program instructions or subsets of the program instructions may also be transmitted through any of various transmission media e.g. a computer network.

U.S. patent application Ser. No. 10 653 829 filed on Sep. 3 2003 entitled Method and System for Scenario and Case Decision Management invented by Cullick Narayanan and Wilson is hereby incorporated by reference in its entirety.

While the invention is susceptible to various modifications and alternative forms specific embodiments thereof are shown by way of example in the drawings and are herein described in detail. It should be understood however that the drawings and detailed description thereto are not intended to limit the invention to the particular form disclosed but on the contrary the intention is to cover all modifications equivalents and alternatives falling within the spirit and scope of the present invention as defined by the appended claims.

In one set of embodiments a decision management system may be configured to provide mechanisms e.g. graphical user interfaces for a user to 

A flow is an interconnected set of algorithms for solving a problem. The decision management system may provide a graphical user interface that allows the user to select import or build algorithms and connect the algorithms together to form a flow.

A flow may be configured to include one or more computation loops. The loops may be nested. The loops of a flow may serve any of various purposes. For example a flow may include a loop in order to perform an optimization on the space corresponding to a number of variables. Variables that are subject to optimization are referred to herein as decision variables. As another example a flow may include a loop in order to explore the impact of variation in a space corresponding to a number of variables that represent uncertainties. Variables that represent uncertainties are referred to herein as uncertainty variables.

A loop may include an iterator an algorithm or more generally a collection of algorithms and optionally a dispatcher. When a flow is executed the iterator is responsible for generating iteration data sets for respective executions of the algorithm. Each execution of the algorithm is performed on a corresponding one of the iteration data sets. Each iteration data set contains data used as input by the algorithm. Each execution of the algorithm is referred to herein as an iteration . However the term iteration is not meant to require sequential processing of one iteration after another. Indeed the iterator and dispatcher may be configured to arrange for parallel iterations. For example the iterator may be configured to generate a number of iteration data sets in anticipation of a corresponding number of iterations. The dispatcher may locate other computers or processors that have available computational bandwidth and distribute the iteration data sets to the other computers so that the iterations may be performed in parallel or at least partially in parallel depending on the number of available computers.

In one embodiment the dispatcher may compress one or more of the iteration data sets to form an execution file and transfer the execution file to one of the remote computers having available computational bandwidth . The remote computer may decompress the execution file to recover the iteration data sets and execute the algorithm once for each of the iteration data sets. The algorithm may include code that sends the results of each execution back to the first computer i.e. the computer that the dispatcher is executing on for storage.

As noted above the execution file may include compressed iteration data sets. If a remote computer does not already have a copy of the executable code for the algorithm the dispatcher may compress a copy of the executable code and include the compressed code in the execution file.

As indicated above a flow is an interconnected set of algorithms for solving a problem. The algorithms operate on data structures. Different types of algorithms operate on different types of data structures. For example a reservoir flow simulator configured to predict rates of production of oil gas and water operates on a different set of data structures than an economic algorithm configured to predict economic returns. The decision management system may provide an interface through which the user may specify the source locations e.g. the file system locations on a network of files and or databases containing the data structures. Furthermore the decision management system may invoke tools that allow the user to create and modify data structures.

Each data structure includes a set of one or more data values. However some of the data values of a data structure may represent parameters or quantities that are uncertain. Thus the decision management system may provide a mechanism for the user to select a data value in a data structure and to promote the data value to an uncertainty variable by supplying a set of attainable values for the uncertainty variable and a probability distribution for the uncertainty variable. The original data value may be included by default as one of the values in the attainable value set of the uncertainty variable. Any number of data values in any number of data structures may be thusly promoted to uncertainty variables.

Furthermore a data value in a data structure may represent one possible outcome of a decision. The user may wish to consider other possible outcomes of the decision. Thus the decision management system may provide a mechanism for the user to select a data value in a data structure and to promote the data value to a decision variable by supplying a set of attainable values representing possible outcomes of the decision. For example the number of wells to be drilled in a given field may equal any integer from A to B inclusive. As another example the capacity of a given pump may equal any value in the range from X to Y cubic feet per minute. The original data value may be included by default as one of the elements of the attainable value set. Any number of data values in any number of data structures may be thusly promoted to decision variables.

The set of attainable values for a decision variable or an uncertainty variable may be a finite set e.g. a finite set of user specified numeric values or an infinite set e.g. an interval of the real line or a region in an n dimensional Euclidean space where n is a positive integer .

The user may specify the probability distribution for an uncertainty variable by various means. If the uncertainty variable has an attainable value set that is continuous the decision management system may allow the user to specify a probability density function PDF by selecting a PDF type such as normal uniform triangular etc. and to specify parameters defining a particular PDF within the selected type. If the uncertainty variable has an attainable value set that is finite the decision management system may allow the user to enter probability values or numeric values that may be subsequently normalized to probability values for the attainable values of the uncertainty variable. The decision management system may allow the user to qualitatively and quantitatively fit a PDF to an existing set of values for the uncertainty variable possibly from analogues .

It is possible that there are two or more data structures each of which could be supplied as input to a given algorithm or a given set of algorithms . The user may be uncertain as to which of the two or more data structures to use. For example there may two geocellular models for the same reservoir and it may not be clear which model is a better representation of the physical reservoir. Thus the user may desire to set up a flow that executes an algorithm a number of times each time using a randomly selected one of the two or more data structures. Therefore the decision management system may provide a mechanism for the user to create an uncertainty variable whose attainable values correspond respectively to the two or more data structures. The user may assign probability values to the two or more attainable values. Each probability value represents the probability that the corresponding data structure will be selected in any given realization of the uncertainty variable. The user may choose to construct any number of uncertainty variables of this kind. A set of data structures that are mapped to the attainable values of an uncertainty variable in this fashion are said to be subordinated to the uncertainty variable .

Furthermore it is possible that there are two or more data structures which represent alternative outcomes of a decision. For example there may be two or more data structures each of which represents a possible realization for well locations and facility pipeline connections. Thus the decision management system may provide a mechanism for the user to create a decision variable whose attainable values correspond respectively to the two or more data structures. A set of data structures that are mapped to the attainable values of a decision variable in this fashion are said to be subordinated to the decision variable .

Some of the data structures may be referred to as models since they describe or characterize systems of interest. For example the data structures may include geocellular reservoir models well plan models etc. The objects resulting from the operations 2 3 and 4 are also referred to herein as models.

The decision management system may be configured to support the use of highly rigorous physical reservoir models well models production flow models and economic models.

Some of the uncertainty variables may be correlated. Thus the decision management system allows the user to specify correlations between pairs of uncertainty variables. For example the user may select a pair of uncertainty variables and enter a correlation coefficient to specify the correlation between the pair of uncertainty variables. In some embodiments the user may select a group of two or more uncertainty variables and enter a correlation matrix for the group. When a flow is executed the uncertainty variables are instantiated in a way that the respects the user specified correlations.

Some of the uncertainty variables may have functional dependencies between them e.g. functional dependencies of the form Y f X Y f X X Y f X X X and so on where X X X Xand Y are uncertainty variables. Thus the decision management system may provide a user interface which allows the user to specify such functional dependencies. Any of a wide variety of functions including linear and nonlinear functions may be supported. In some embodiments the user interface allows the user to construct an arbitrary algebraic function of the uncertainty variables. When a flow is executed the uncertainty variables are instantiated in a way that respects these functional dependencies. For example if Y f X an instantiation for Y may be obtained by first instantiating X and then evaluating the function f on the instantiation of X. Similarly the decision variables may have functional dependencies between them e.g. functional dependencies of the form Y f X Y f X X Y f X X X and so on where X X X Xand Y are decision variables. Thus the same user interface or a different user interface may be used to specify such functional dependencies between decision variables.

Some of the decision variables or functional combinations of decision variables may be constrained. Thus the decision management system may provide a user interface which allows the user to specify constraints such as 

on decision variables such as X X X Xand Y where .ineq. may be any of the inequality operators or . Any of a wide variety of functions f including linear and nonlinear functions may be supported. In some embodiments the user interface allows the user to construct an arbitrary algebraic function of the decision variables. When a flow executes an optimization is performed that respects the user specified constraints on the decision variables.

The decision management system may also provide a user interface through which the user may specify an execution control data set. An execution control data set contains information for controlling and qualifying the execution of a flow. For example an execution control data set may include information such as 

In a Monte Carlo mode of instantiation the uncertainty variables or some subset of the uncertainty variables may be instantiated randomly using random number generators. In a Latin hypercube mode of instantiation the uncertainty variables or some subset of the uncertainty variables may be instantiated using the well known Latin hypercube method. In an experimental design mode of instantiation the uncertainty variables or some subset of the uncertainty variables may be instantiated using any of various well known experimental design methods.

Over time the user may construct a number of flows a number of sets of models and a number of execution control data sets. The decision management system may allow the user to select a flow a set of models and an execution control data set and invoke execution of the flow with respect to the execution control data set and the set of models. The decision management system may also provide the user more control over how a flow can be executed. For example in some embodiments a flow can executed to run specific iterations that might have failed to execute for a variety of reasons in previous executions of the flow. In other embodiments additional iterations might be executed on flows that have been previously executed.

The decision management system may provide various tools for the user to design various different kinds of flows. For example in some embodiments the decision management software may include a decision flow builder that is configured to automate the process of building a flow for the optimization of decisions related to the exploitation of a set of assets e.g. a set of oil and gas fields in a manner that takes into account various uncertainties associated with the set of assets.

The decision management system may be implemented by executing decision management software on a set of one or more computers.

The decision management software may be partitioned into a client application and a server application with a communication protocol between the client application and the server application. For example the communication protocol may be realized using remote method invocation RMI or WEB Services.

The client application may execute on a client computer and the server application may execute on a server computer. However there is no requirement that the client application and server application must execute on separate computers. If a computer has sufficient computational power both the client application and the server application may execute on that computer.

The server application may be configured to use dispatchers. A dispatcher is a program or system of programs configured to distribute self contained groups of computations e.g. iterations of a large job to other processors or computers for execution on those other processors. The other processors may be distributed across a network such as a local area network a wide area network or the Internet. The other processors may also be part of a shared memory hardware unit such as a cluster and may be used as a single unit e.g. in a parallel computation environment 

In some embodiments the major modules of the client application and the server application i.e. the flow server may be as shown in .

The client application may include a flow builder a model manager a flow runner and an output analyzer .

The flow builder provides a user interface through which the user states a problem and creates a flow to solve it.

The model manager provides an interface through which the user may create build and modify models including decision variables and uncertainty variables.

The flow runner is used to launch the execution of flows. In response to a user request for the execution of a flow the flow runner sends the flow along with a compatible set of models and a compatible execution control data set to the flow server so that the flow may be executed. The flow runner may also receive status information from the flow server regarding currently executing flows and pending flows and display the status information to the user. The flow server may send the results of a flow execution back to the flow runner and or store the results in a database.

The flow server may include a remote API for communicating with client applications such as client application .

The flow server may execute flows or direct the execution of flows which are submitted as jobs from the client application. The flow server may provide status information about the jobs that are being executed to the flow runner. The flow server also allows jobs to be cancelled.

As noted above the client application may be partitioned into a number of modules as suggested in . Each module may have an associated API application programming interface through which the different modules communicate. Thus the client application may include a model manager API a decision flow builder API a flow builder API a flow runner API and an output analyzer API .

In some embodiments these APIs are the only allowed interface between the modules thus enabling the modules to be developed independently.

Each of the modules that require communication with external applications may also have a remote API. Thus in some embodiments the client application may include a model manager remote API and a flow runner remote API .

The model manager may provide an interface which allows the user to import create edit and maintain models including uncertainty variables and decision variables as described above. The model manager may also maintain the models in projects or other organizations specified by the user.

The types of data structures to be included in the models targeted for a given flow will depend on the algorithms included in the flow. Thus the model manager may communicate with the flow builder to ensure that the user supplies data structures that are consistent with the algorithms of the given flow. For example the model manager may receive from the flow builder a list of algorithms in the flow. The model manager may then focus on prompting the user for the types of data structures appropriate for the listed algorithms. Conversely the models chosen by user might dictate the type of flow that can be executed. Thus if the user builds and supplies a data structure the user might then be prompted to choose from only those flows that are capable of executing that model.

In some embodiments the model manager may be configured to invoke well known software tools to create and edit certain types of models. For example each model may have a specific type and each type may have a specific tool registered to allow its creation editing viewing etc. This design may be similar to the JavaBean Property Editors which allow a custom GUI graphical user interface to be registered against a JavaBean. Furthermore this design may utilize some of the notions within the JavaBeans Activation Framework.

As the data structures supplied by the user may not include decision variables or uncertainty variables the model manager may provide generic mechanisms for promoting data values in data structures to decision variables and uncertainty variables with data structures and for subordinating data structures to decision variables and uncertainty variables.

The model manager may function as a case manager allowing an existing model to be cloned and sub components altered.

Algorithms are the building blocks of flows. An algorithm can be viewed as a process that has inputs and generates outputs. A flow is a set of algorithms that have been linked together to perform a certain task. It is noted that a flow can itself be converted into an algorithm if desired.

The flow builder provides a user interface UI through which the user may build arbitrary flows. For example the flow builder may allow the user to select algorithms from a set of available algorithms and connect the algorithms together i.e. connect the outputs of algorithms to the inputs of other algorithms to form a flow. The set of available algorithms may include a variety of algorithms useful to one planning the exploration development and or operation of set of fields e.g. algorithms such as geology or geostatistics simulators material balance simulators reservoir flow simulators well tubing simulators facility process simulators pipeline network simulators and economic algorithms. In some embodiments the simulators may be configured using one or more commercial or open source tools e.g. Landmark s VIP reservoir simulator or another finite difference finite element or streamline simulator Petex GAP surface pipe line simulator Microsoft s Excel Petex MBAL material balance simulator GSLIB geostatisics generator .

Furthermore the flow builder may allow the user to build algorithms from scratch or import programs that are to be used as algorithms. In some embodiments the flow builder may allow the user to specify an arbitrary algebraic function as an algorithm or import a neural network to use as an algorithm.

In one set of embodiments when forming directed connections between algorithms the flow builder may impose data type restrictions. For example the flow builder may allow an integer output from one algorithm to be connected to a floating point input of a second algorithm but disallow a connection from a float output to an integer input.

The flow builder may incorporate a search engine for finding algorithms. The search engine may support searching on algorithm category such as production profile algorithm type of input type of output etc.

In some embodiments the flow builder may be configured using one or more commercial tools e.g. Landmark s DecisionSpace Decision Management System .

The flow runner may provide a user interface that allows the user to invoke execution of flows. When the user asserts a command to invoke execution of a flow with respect to a set of models and an execution control data set the flow runner assembles a job including the flow the set of models and the execution control data set and submits the job to the flow server. The flow server may generate a unique ID for the job and send the job ID to the flow runner. The flow runner may record the job ID.

In addition to acquiring flows from the flow builder and models from the model manager the flow runner may also load the description of a flow and its related models from a set of input files e.g. XML files specified by the user.

The flow runner may display a list of jobs including jobs that are currently running including their current status and jobs that are pending. The flow runner interface allows the user to cancel jobs. Furthermore the flow runner interface may allow the user to access any results already available for a job. The results may be displayed through the output analyzer s user interface.

The flow runner may be configured to submits jobs to any of a plurality of flow servers. The flow servers may execute on a number of computers through a network. The flow runner may allow the client to decide which flow server a job is to be submitted to. Different flow servers may be customized for executing different kinds of jobs.

The primary purpose of the output analyzer may be to provide a means for the user to comprehend the output data obtained from executing a job i.e. a flow with respect to a specified set of models and execution control data set . The output data may be complex since the flow may have a complex structure e.g. a structure with an outer loop and multiple inner loops.

The output analyzer may be configured to allow the user to examine the output data from a completed flow and to view results from a flow still executing on the flow server.

The output analyzer may have access to a full suite of data analysis tools as well as being able to format the output data so it can be analyzed in a third party tool such as Microsoft Excel .

The client application may also include a results calculator interface not illustrated in the Figures . The results calculator interface allows the user to specify special calculations that are to be embedded in a flow. The special calculations may be useful when the output of a first algorithm or first set of algorithms is not exactly the input required by a second algorithm or second set of algorithms but can be used to calculate the input required by the second algorithm. The results calculator interface allows the user to 

The flow builder or the decision flow builder may use this information to generate a result calculator algorithm that implements the specified function to embed the result calculator algorithm into the flow between the first set of algorithms and the second algorithm. The user may specify any desired number of special calculations to be performed at the time of flow execution between algorithms or sets of algorithms in a flow.

The flow server may be partitioned into a number of separate modules e.g. as suggested in . The flow server may be configured to execute jobs. A job includes a flow and a input data set.

Depending on the number of jobs the flow server is capable of running concurrently the flow server may queue pending executions. The flow server may have the ability to cancel jobs or change the priority of jobs.

The flow server may typically execute on different computer than the client application. However the flow server may also execute on the same computer as the client application.

The flow server holds a conversation with the flow runner informing the flow runner on the status of jobs etc.

The communication between the flow runner and the flow server may be based on any of a wide variety of known protocols such as RMI or WEB Services.

The decision management system is configured to execute flows which include a set of interconnected algorithms. The flow may operate on models with associated uncertainty variables and decision variables as input. For example models may include data values that have been promoted to decision variables data values that have been promoted to uncertainty variables data structures that are subordinated to decision variables data structures that are subordinated to uncertainty variables or any combination thereof.

A flow may include loops configured to iteratively execute sets of algorithms. Dispatchers may be used to distribute iterations to multiple computers for parallel execution.

A default dispatcher which executes all the iterations of its associated loop on the local host computer may be provided.

A network dispatcher which searches for available computers on a network and distributes iterations to those available computers may also be provided.

The number of models especially memory resident models and the number of algorithms that act upon the models is very likely increase over time. Thus the decision management system may be configured to allow new models and algorithms to be plugged in at will.

In some embodiments the decision management system may have a command type interface. User inputs directed through the command type interface may be captured and stored. This provides a means for repeating a set of interactions if desired.

The client application of the decision management software may also include a decision flow builder. The decision flow builder may provide a user interface that accelerates the process of building a flow for the optimization of decisions relating to the exploration development and production of assets such as oil and gas fields.

In some embodiments the decision flow builder may be specially configured to accelerate the construction of a flow including an outer optimization loop and a set of inner uncertainty exploration loops e.g. one inner loop per asset.

The decision flow builder may generate a flow having an outer optimization loop and a set of inner loops according to the information specified by the user.

As noted in b above the asset types may include exploration field development field and operational field. Other types of assets are contemplated as well.

As noted in c above the user may specify one or more algorithms e.g. process simulation algorithms to be included in an inner loop for each asset. The decision flow builder may receive user input specifying a particular asset on which attention is to be currently focused and display a list or some graphical representation of a set of algorithms appropriate for the type of the asset under consideration from which the user may choose. Different kinds of algorithms are appropriate for different assets.

As noted in d above the user may specify sources of data structures consistent with the algorithms specified in c . For example the decision flow builder interface may be configured to allow the user to specify for each asset file system locations e.g. file system locations in a computer network for data files or data bases containing the data structures. Furthermore the user may specify entries or sets of entries in databases containing the data structures.

Other examples of data structures include reservoir models economic models pipeline network models facility processing models and well tubing models.

The types of data structures that are specified for an asset may depend on the types of algorithms that are to be used for the asset. For example a material balance simulator of analytical or algebraic expressions may rely on a tank model for an asset where the tank model has a single set of properties to represent the whole asset. A reservoir flow simulator with partial differential equation representation of flow in porous media and a finite difference formulation may rely on a 3 dimensional spatial reservoir model to predict flows of oil gas and water over time. An economic algorithm may rely on an economic model including prices tax rates and fiscal complexities to predict revenue over time. The decision flow builder may prompt the user to enter data structures of types consistent with the algorithms that have already been specified for the asset in c .

As noted in e above the user may operate on the data structures to build models for each of the assets especially models including decision variables and uncertainty variables. For example the user may 

Global decision variables are decision variables that are not uniquely associated with a single asset. For example the amount of capital to be available for the set of assets is an example of a global decision variable. Global uncertainty variables are uncertainty variables that are not uniquely associated with a single asset. For example oil price is an example of a global uncertainty variable.

As noted in g above the user may specify functional dependencies between uncertainty variables and functional dependencies between decision variables. In some embodiments the decision flow builder interface may be configured to allow the user to 

The set Vof uncertainty variables associated with the current problem includes the uncertainty variables specified in e and the global uncertainty variables.

The set Vof uncertainty variables associated with the current problem may include the global decision variables and the decision variables specified in e .

The decision flow builder may allow the user to specify any number of functional dependencies by repeated use of the decision flow builder interface as described above. For example the user may specify functional dependencies of the following forms 

An algebraic function is a function which is determined by an expression involving only the algebraic operations of addition subtraction multiplication division integer or rational root extraction and integer or rational powers on the function arguments.

As noted in h above the user may specify correlations between uncertainty variables. In one set of embodiments decision flow builder interface may be configured to allow the user to 

The user may specify any number of such correlations by repeated use of the decision flow builder interface as described above. For example the user may specify correlations between pairs of uncertainty variables having the following forms 

In some embodiments the user may select a group of two or more uncertainty variables and enter a correlation matrix for the group.

When a flow is executed the uncertainty variables are instantiated in a way that the respects the user specified correlations.

As noted in i above the user may specify constraints on the decision variables or functional combinations of the decision variables. In one set of embodiments the decision flow builder interface may be configured to allow the user to 

Furthermore the decision flow builder interface may be configured to allow the user to specify constraints of the form Y .ineq. C where C is a user specified constant.

The set Vof decision variables may include the global decision variables and the decision variables specified in e . Any of a wide variety of functions f including linear and nonlinear functions may be supported. In some embodiments the decision flow builder interface allows the user to construct an arbitrary algebraic function of the selected decision variables X X . . . X.

The decision flow builder interface may be configured to allow the user to specify any number of constraints on the decision variables by repeated use of the decision flow builder interface as described above. For example the user may specify constraints having the following forms 

As noted in j1 above the user may specify one or more quantities of interest for each asset A k k 1 2 . . . N. In one set of embodiments the user may specify a quantity for the asset A k by 

Furthermore the decision flow builder interface may display a list of commonly used quantities appropriate for the kinds of algorithms that are associated with the asset A k under current consideration. The user may specify quantities of interest by selecting quantities from the list.

Examples of quantities of interest for an asset include quantities such as net present value total reserves total produced oil etc.

As noted in j2 the user may specify statistics to be computed for each asset A k k 1 2 . . . N i.e. statistics on the one or more quantities that have been specified for the asset A k . In one set of embodiments the decision flow builder interface may allow the user to specify a statistic for each of the one or more quantities that have been specified for each asset by 

Furthermore the decision flow builder interface may allow the user to specify more than one statistic on the same quantity. For example the user may wish to compute both the mean and the standard deviation of net present value for an asset.

As part of the execution of a flow the one or more quantities specified for each asset may be evaluated a number of times resulting in a population of values for each quantity. Each statistic specified for a quantity is computed on the corresponding population.

As noted in k1 above the user may specify a global objective S as a functional combination of a first subset of the statistics. To this end in one set of embodiments the decision flow builder interface may be configured to allow the user to 

In one typical scenario the user may select one statistic Scorresponding to each asset A k k 1 2 . . . N and specify the global objective S as a linear combination of the form

The user may enter the values of the coefficients Cthat are to multiply the respective statistics S. As an example the user may configure the global objective S to represent a linear combination of the mean net present value for each asset A k .

As noted above in k2 the user may specify one or more auxiliary functions each auxiliary function being a functional combination of a corresponding subset of the statistics. In one set of embodiments in order to specify an auxiliary function the decision flow builder interface may allow the user to 

In one typical scenario the user may define an auxiliary function H by selecting one statistic Tcorresponding to each asset A k k 1 2 . . . N and specifying a linear combination of the form

The user may enter the values of the coefficients athat are to multiply the respective statistics. As an example the user may configure the auxiliary function H to represent a linear combination of the squared standard deviation of net present value for each asset A k .

As noted in k3 above the user may specify one or more constraints involving the one or more auxiliary functions and or the global objective S. In one set of embodiments the user may specify one or more constraints each having the form where J is a user specified function whose arguments are selected from the set Fincluding the one or more auxiliary functions and the global objective function S where .rel. is a relation selected from the set where C is a user specified constant. The user may specify such a constraint by 

In one typical scenario the user may rely on this procedure to specify a constraint of the form J H S

As noted in 1 above the user may select an optimizer. In one set of embodiments the decision flow builder may allow the user to select from a set of supported optimizers. The global objective S is likely to be highly nonlinear and to have many local minima or maxima over the global space defined by the decision variables. Furthermore this global space over which the optimization is to be performed may have isolated islands of feasible vectors in seas of infeasible vectors. Thus it is desirable to use optimizers that do not terminate upon finding a single local minimum or maximum and do not get trapped inside a single island. Thus the set of supported optimizers may include stochastic optimizers i.e. optimizers that use randomness in their search methodology.

In some embodiments the decision flow builder may allow the user to select from optimizers such as the following 

The set Vof decision variables of a flow represent decisions that are subject to being controlled. Each decision variable has a user specified set of attainable values. The Cartesian product of the attainable value sets of the decision variables in Vis a global decision space over which the optimization is to be performed subject to any constraints the user may specify for the decision variables or functional combinations of the decision variables and subject to the one or more constraints defined in k3 involving the one or more auxiliary functions and or the global objective.

A vector in the global decision space is referred to as a decision vector. In other words a decision vector is a vector of values i.e. one value selected from each of the attainable value sets of the decision variables in V.

In some embodiments the decision flow builder might allow the user to supply some set of initial guess vectors that the optimizer might use in its search process.

The set Vof uncertainty variables of a flow represent uncertainties. Each uncertainty variable has a user specified set of attainable values. The Cartesian product of the attainable value sets of the uncertainty variables in Vis a global uncertainty space which is to be iteratively explored. A vector in the global uncertainty space is referred to as an uncertainty vector. In other words an uncertainty vector is a vector of values i.e. one value selected from each of the attainable value sets of the uncertainty variables in V.

In some embodiments the decision flow builder may generate a flow in response to the information a n specified by the user. The flow may include the optimizer selected by the user in 1 and an evaluation process as illustrated in . The optimizer may generate decision vectors x in the global decision space subject to the user specified constraints on the decision variables. The evaluation process operates on the decision vectors x to generate corresponding values S x of the global objective S and corresponding values H x of an auxiliary function H as described below.

The global objective values S x and the auxiliary function values H x are supplied to the optimizer. The optimizer uses these values to generate updated decision vectors in an attempt to minimize or maximize the global objective subject to the user specified constraint on the auxiliary function H x . The optimizer may operate according to any of a variety of optimization algorithms. The loop structure including the optimizer and the evaluation process is referred to herein as the outer loop.

In one set of embodiments the optimizer may be configured to operate according to the following methodology as illustrated in . The optimizer may execute on the server computer.

In operation the optimizer may construct a reference set of feasible decision vectors. A decision vector is said to be feasible if it satisfies the user specified constraints on the decision variables. In the first iteration of operation the reference set may be constructed by generating an initial set of decision vectors that are spatially diverse e.g. using random methods and then mapping the initial set of decision vectors to feasible decision vectors. However in any succeeding iteration of operation the reference set may be constructed by 

The optimizer may sort the nbest decision vectors in order of their global objective values S x . The optimizer may also sort the nadditional vectors according to a distance measure.

In operation the optimizer may generate new vectors Xby forming combinations e.g. linear combinations of subsets of the reference set vectors. The new vectors are not necessarily feasible vectors. The subsets may include two or more reference set vectors.

In operation the optimizer may map the new decision vectors to feasible decision vectors xusing a linear program and or a mixed integer program.

In operation the optimizer may supply the feasible decision vectors xto the evaluation process for computation of the global objective values S x and the auxiliary function values H x corresponding to the feasible decision vectors x.

In operation the optimizer may update the reference set using the global objective values S x and auxiliary function values H x computed in operation . In one embodiment the optimizer may examine each of the feasible vectors xto determine 

In either case the optimizer may replace the worst vector with the feasible vector. If none of the feasible vectors xsatisfies either condition 1 or 2 the reference set remains the same i.e. the update is a null update.

In operation the optimizer may determine if the reference set has changed as a result of operation . If so the optimizer may perform another iteration of operations . If the reference set has not changed the optimizer may continue with operation .

In operation the optimizer may determine if a termination condition is satisfied. If the termination condition is not satisfied the optimizer may continue with operation in order to regenerate the reference set with a different set of ndiverse feasible vectors. If the termination condition is satisfied the optimizer may continue with operation .

Various termination conditions are contemplated for various embodiments. For example the termination condition may be the condition that 

In operation the optimizer may store the reference set vectors along with their corresponding global objective values and auxiliary function values in a database. The output analyzer may read the database and display a graphical representation of the global objective value and auxiliary function value s for each of the reference set vectors or alternatively for the nbest vectors of the reference set .

In one set of embodiments the evaluation process may be configured to operate according to the following methodology as indicated in . The evaluation process may execute on the server computer.

In operation an instantiation module of the evaluation process may generate Nuncertainty vectors in a way that respects the user specified functional dependencies and correlations between uncertainty variables where Nis a user specified positive integer. The Nuncertainty vectors explore the global uncertainty space. The uncertainty vectors may be generated according to a user specified mode of instantiation as described above. Each uncertainty vector U j 1 2 . . . N contains an instantiated value for each of the uncertainty variables in the set V i.e. the set of all uncertainty variables associated with the current problem . Each instantiated value is selected from the attainable value set of a corresponding one of the uncertainty variables.

In operation the evaluation process may generate Niteration data sets from models in anticipation of N inner loop iterations for each asset A k k 1 2 . . . N where Nis the number of iterations and Nis the number of assets. For example the evaluation process may generate the iteration data sets according to the following pseudo code 

The For Loop on index k need not execute in a strictly sequential manner. For example this For Loop may be configured to operate in a multi threaded manner e.g. one thread per value of k.

The values of the decision subvector x k and the values of the uncertainty subvector U k may be used to determine one or more data structures from the models. In particular one or more of the values of decision subvector x k and or one or more of the values of uncertainty subvector U k may be used to select data structures from models including sets of alternative data structures. Furthermore one or more values of the decision subvector x k and or one or more values of the uncertainty subvector U k may be substituted into models including decision variables and or uncertainty variables. The data structures determined by the values of the decision subvector x k and the values of the uncertainty subvector U k may be included in the iteration data set IDS kj . The iteration data set may include sufficient data to execute the set of algorithms that have been assigned to asset A k . The subvectors x k are not necessarily disjoint. For example values corresponding to the global decision variables may appear in more than one of the subvectors x k . Similarly the subvectors U k are not necessarily disjoint.

In operation a dispatcher of the evaluation process may dispatch i.e. send the Niteration data sets for each asset A k k 1 2 . . . N to one or more other computers where Nis the number of iterations to be performed on each asset. For example the dispatcher may operate according to the following pseudo code 

The dispatcher may include a copy of the executable code for the algorithms associated with asset A k into the execution data file in the case that the computer Cdoes not already have a copy of this code. Furthermore the dispatcher may include an address of a data buffer INB k associated with asset A k into the execution data file. The data buffer INB k may be allocated in the memory of the server computer. The computer Cexecutes the set of algorithms associated with asset A k on each iteration data set IDS k j included in the execution data file collects the output data of the algorithms from the execution into a corresponding output data set ODS kj and sends the output data set ODS k j to the data buffer INB k .

The For Loop on index k need not execute in a strictly sequential manner. For example this For Loop may be configured to operate in a multi threaded manner e.g. one thread per value of k.

Furthermore operation and need not execute in a strictly sequential manner. For example the multiple threads of the For loop in operation may be executed in an multi threaded fashion with the multiple threads of the For loop on index k in operation . In one embodiment the kdispatch thread may be started soon after the kIDS generation thread is started. For example the kIDS generation thread may start the kdispatch thread after having stored one or more iteration data sets into iteration buffer IBUFF k .

In operation a results accumulator of the evaluation process may store the output data sets ODS k j generated by the other computers to which the execution data sets were distributed . The output data set ODS k j represents the output of the algorithms associated with asset A k having been executed on the iteration data set IDS k j . In one set of embodiments the results accumulator may operate according to the following pseudo code 

The For loop on index k need not execute in a strictly sequential fashion. For example this For Loop may be configured to operate in a multi threaded manner e.g. one thread per value of k.

Furthermore the operation and need not execute in a strictly sequential fashion. For example the multiple threads of the For loop in operation may be executed in an multi threaded fashion with the multiple threads of the For loop in operation . In one embodiment the kaccumulation thread may be started soon after the kdispatch thread is started. For example the kdispatch thread may start the kaccumulation thread after having dispatched a first execution data file for asset A k .

In operation A a results calculator of the evaluation process may compute for each asset A k k 1 2 . . . N and for each iteration j 1 2 . . . N a value for each user specified quantity for the asset using output argument values from the output data set ODS k j . Thus the results calculator generates a population of Nvalues for each user specified quantity.

In operation B the results calculator may compute for each asset A k k 1 2 . . . N a value for each user specified statistic for the asset based on a corresponding one of the populations.

In one set of embodiments the results calculator may be configured to implement operation according to the following pseudo code 

The For loop on index k need not execute in a strictly sequential fashion. For example this For Loop may be configured to operate in a multi threaded manner e.g. one thread per value of k.

Furthermore the operation and need not execute in a strictly sequential fashion. For example the multiple threads of the For loop in operation may be executed in an multi threaded fashion with the multiple threads of the For loop in operation . In one embodiment the kresults calculation thread may be started soon after the kresults accumulation thread has started. For example the kresults accumulation thread may start the kresults calculation thread after having stored a first of the output data sets ODS k j into the database.

In one set of embodiments a method for optimizing decisions regarding a plurality of assets may involve the following operations as illustrated in .

In operation a computer e.g. a server computer including one or more processors may receive information specifying 

In operation the computer may generate a decision vector. The decision vector includes a value for each of the decision variables. Each of the decision variables has an associated set of attainable values.

In operation the computer may execute an evaluation process on the decision vector to determine at least a value of a global objective for the decision vector. See below for a description of the evaluation process.

In operation the computer may execute an optimizer. The execution of the optimizer includes performing operations and repeatedly thereby generating a plurality of decision vectors and corresponding global objective values. The optimizer uses the plurality of decision vectors and the corresponding global objective values to generate and repeatedly update a reference set of decision vectors in order to optimize the global objective.

In operation the computer may store data including the plurality of decision vectors and their corresponding global objective values in a memory e.g. in the system memory of the computer .

In operation the computer may display a graphical representation of at least a subset of the decision vectors of the reference set.

The optimizer may be realized by any of variety of optimizers especially stochastic optimizers. For example the optimizer may be 

The operation of executing the evaluation process may include the following operations as illustrated in .

In operation A the computer may generate an uncertainty vector. The uncertainty vector includes a value for each of the uncertainty variables.

In operation B the computer may generate for each asset a data set for the corresponding set of algorithms using a corresponding subset of one or more values in the decision vector and a corresponding subset of one or more values in the uncertainty vector.

In operation C the computer may invoke execution of the set of algorithms for each asset on the corresponding data set to obtain output arguments corresponding to the asset. The computer may invoke execution on other computers e.g. by sending the data sets to the other computers and the executable code for the respective algorithms if necessary .

In operation D the computer may compute for each asset one or more values of one or more respective quantities from the output arguments corresponding to the asset.

In operation E the computer may perform operations including A through D a number of times thereby generating a population of values of each quantity for each asset.

In operation F the computer may compute one or more statistics for each asset based on corresponding ones of the populations.

In operation G the computer may combine a first subset of the statistics to determine the global objective value corresponding to the decision vector. The first subset of statistics may be combined according to a user specified functional combination e.g. a linear combination .

The information referred to in above may specify one or more functional dependencies among the uncertainty variables. The operation A of generating the uncertainty vector may be performed in a manner that respects the one or more functional dependencies among the uncertainty variables. The user may specify the functional dependencies e.g. through a client GUI that executes on another computer e.g. a client computer .

The information may also specify one or more correlations among the uncertainty variables. In this case the operation A of generating the uncertainty vector may be performed in a manner that respects said correlations. The uncertainty variables may include two or more subsets associated with two or more of the assets respectively. The correlations may include correlations between uncertainty variables across different assets.

The information may also specify one or more constraints on the decision variables. In this case the operation of generating the decision vector may respect the one or more constraints on the decision variables.

The operation of executing the evaluation process on the decision vector may produce a corresponding value of an auxiliary function in addition to said global objective value. Thus the operation may additionally include 

The optimizer may use the global objective values and the auxiliary function values corresponding to the plurality of decision vectors in said repeated updating of the reference set in order to optimize the objective function subject to one or more constraints.

The user may specify the structure of the one or more constraints. For example the user may specify a constraint on a functional combination of the auxiliary function and the global objective. The functional combination may itself be specified by the user. As another example the user may specify a constraint just on the auxiliary function.

The operation H may include combining the second subset of the statistics according to a linear combination whose coefficients are specified by said information.

Each of the decision variables has an associated set of attainable values representing possible outcomes of a corresponding decision. Furthermore each of the uncertainty variables has an associated set of attainable values. The attainable value sets may be finite sets of numeric values data structures programs etc. The attainable value sets may also be intervals of the number line or more generally user specified regions in an n dimensional space where n is a positive integer.

In one embodiment a plot of the global objective value versus auxiliary function value for each of said plurality of decision vectors may be displayed using a display device such as monitor projector head mounted display etc. .

The operation of storing the data may include storing the decision vectors of the plurality of decision vectors along with their corresponding global objective values and the corresponding auxiliary function values in a database in the memory.

A graphical representation of a subset of the plurality of decision vectors that corresponds to a point on the optimal value locus may be displayed in response to a user s selection of the point.

The user may specify the plurality of assets the decision variables and the uncertainty variables for each asset and a set of one or more algorithms for each asset. The decision variables are variables that are subject to optimization. The uncertainty variables may be variables that are randomly or pseudo randomly explored into create variation in the input supplied to algorithms of each asset.

The set of one or more algorithms for at least one of the assets may include an algorithm to estimate oil and gas production over time and economics for the asset. The algorithm to estimate oil and gas production over time may be 

Furthermore the set of one or more algorithms for at least one of the assets may include one or more of 

In another set of embodiments a method for optimizing decisions regarding a plurality of assets by means of executing program code on a first computer e.g. a server computer may involve the following operations as illustrated in .

In operation a first computer e.g. a server computer including one or more processors may receive information specifying decision variables and uncertainty variables for the plurality of assets and specifying for each asset a corresponding set of one or more algorithms.

In operation first computer may generate a decision vector where the decision vector includes a value for each of the decision variables.

In operation the first computer may execute an evaluation process on the decision vector to determine at least a value of a global objective for the decision vector.

In operation the first computer may execute an optimizer where said executing the optimizer includes performing operations and repeatedly thereby generating a plurality of decision vectors and corresponding global objective values and where the optimizer uses the plurality of decision vectors and the corresponding global objective values to generate and repeatedly update a reference set of decision vectors in order to optimize the global objective.

In operation the first computer may store data including the plurality of decision vectors and their corresponding global objective values in the memory.

The operation of executing the evaluation process may include the following operations as illustrated in .

In operation A the first computer may generate Nuncertainty vectors where each uncertainty vector contains instantiated values for each of the uncertainty variables where Nis a positive integer.

In operation B the first computer may generate Niteration data sets for each asset where each of the iteration data sets is generated using a portion of the decision vector and a portion of a corresponding one of the uncertainty vectors.

In operation C the first computer may dispatch the Niteration data sets for each asset to one or more second computers to invoke execution of the set of algorithms for the asset on each of the corresponding Niteration data sets where each execution of the set of algorithms for the asset on an iteration data set generates a corresponding output data set.

In operation D the first computer may receive the Noutput data sets for each of the assets from the one or more second computers and storing the Noutput data sets in a memory.

In operation E the first computer may compute for each asset and each of the Noutput data sets corresponding to the asset one or more values of one or more respective quantities based on the data in the output data set thereby generating a population of Nvalues of each quantity for each asset.

In operation F the first computer may compute one or more statistics for each asset based on corresponding ones of the populations.

In operation G the first computer may combine a first subset of the statistics to determine the global objective value corresponding to the decision vector.

The first computer and the one or more second computers may be coupled through a computer network e.g. a local area network an intranet a wide area network the Internet etc.

The operation of dispatching the iteration data sets induces distributed execution of the sets of algorithms on the iterations data sets on a plurality of the second computers. The second computers may be organized into a grid structure.

In one embodiment a subset of the iteration data sets may be executed locally by the first computer depending in part on how much processing bandwidth is available on the first computer.

The information may be collected from a user by a process executing on a client computer and sent to the first computer by this process.

In yet another set of embodiments a method for optimizing decisions regarding a plurality of assets may involve the following operations as illustrated in .

In operation a computer e.g. a server computing including one or more processors may receive information specifying the plurality of assets an asset objective for each of the assets and a set of algorithms for each asset.

In operation the computer may generate a decision vector including values for a set of decision variables.

In operation the computer may generate Nuncertainty vectors where each of the Nuncertainty vectors results from a separate instantiation of a set of uncertainty variables where Nis a positive integer.

In operation the computer may compute a first population of Nvalues for each asset objective by performing Niterations of executing the corresponding set of algorithms and operating on the output data generated in each of the Niterations of said executing where each execution of the corresponding set of algorithms operates on an input data set determined by the values of the decision variables and by a corresponding one of the uncertainty vectors.

In operation the computer may compute a first asset statistic on each asset objective from the corresponding population of values.

In operation the computer may compute a value of a global objective based on the first asset statistics.

In operation the computer may execute an optimizer where the execution of the optimizer includes performing through repeatedly thereby generating a plurality of decision vectors and corresponding global objective values and where the optimizer uses the plurality of decision vectors and the corresponding global objective values to generate and repeatedly update a reference set of decision vectors in order to optimize the global objective.

The execution of the optimizer may attempt to optimize i.e. maximize or minimize the global objective subject to a constraint on one or more of the auxiliary function and the global objective.

The computer system may include at least one central processing unit CPU i.e. processor which is coupled to a host bus . The CPU may be any of various types including but not limited to an x86 processor a PowerPC processor a CPU from the SPARC family of RISC processors as well as others. A memory medium typically including semiconductor RAM and referred to herein as main memory may be coupled to the host bus by means of memory controller . The main memory may store programs operable to implement any or all or any subset of the various methods embodiments described herein. The main memory may also store operating system software as well as other software for operation of the computer system.

The host bus may couple to an expansion or input output bus through a bus controller or bus bridge logic. The expansion bus may include slots for various devices such as a video card a hard drive storage devices such as a CD ROM drive a tape drive a floppy drive etc. and a network interface . The video card may couple to a display device such as a monitor a projector or a head mounted display. The network interface e.g. an Ethernet device may be used to communicate with other computers through a network.

Embodiments of computer system targeted for use as a server computer may be more richly endowed with processor capacity e.g. having multiple processors memory capacity and network access bandwidth than embodiments targeted for use as a client computer. The client computer may include the mouse keyboard speakers and video card or graphics accelerator whereas a server computer does not necessarily include these items.

Any method embodiment or portion thereof described herein may be implemented in terms of program instructions. The program instructions may be stored on any of various kinds of computer readable memory media. The program instructions are readable and executable by a computer or set of computers to implement the method embodiment or portion thereof . See the definition of memory medium given in the Terminology list below.

Although the embodiments above have been described in considerable detail numerous variations and modifications will become apparent to those skilled in the art once the above disclosure is fully appreciated. It is intended that the following claims be interpreted to embrace all such variations and modifications.

