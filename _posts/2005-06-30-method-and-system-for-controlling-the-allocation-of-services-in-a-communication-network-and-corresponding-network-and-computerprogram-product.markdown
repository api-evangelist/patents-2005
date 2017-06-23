---

title: Method and system for controlling the allocation of services in a communication network, and corresponding network and computer-program product
abstract: The provision of services to the users of a multi-resource communication network is controlled by modelling the system made up of these resources as a Markov chain, wherein each state of the Markov chain is identified by a respective set of values of the numbers of the users served by each of the resources, and the transitions between states are represented by the allocation and de-allocation to the users of the services provided by the resources. A cost function is defined wherein each of the states gives a respective contribution weighted by the probability that the Markov chain is in that state, such probability being a function of the possible transitions between the states. A plurality of transitions between the states is thus identified that optimizes the cost function, and the resources are allocated to the users according to such plurality of transitions that optimizes the cost function.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08339946&OS=08339946&RS=08339946
owner: Telecom Italia S.p.A.
number: 08339946
owner_city: Milan
owner_country: IT
publication_date: 20050630
---
This application is a national phase application based on PCT EP2005 007076 filed Jun. 30 2005 the content of which is incorporated herein by reference.

In particular the invention is applicable to Common Radio Resource Management CRRM techniques which in a heterogeneous mobile radio network i.e. a mobile radio network that can support technologies of different types enable joint management of the radio resources.

In the field of mobile radio networks there exist different technologies and numerous standards. The mobile radio networks that are currently most widespread the so called second generation ones such as for example the GSM system are already flanked and will in future be increasingly flanked by new generation mobile radio networks for example third generation ones such as the UMTS system or fourth generation ones which are still undergoing definition and by broadband networks of the Wireless LAN WLAN type. Second generation mobile radio networks are more suitable for supporting the voice service whilst new generation mobile radio networks for example third generation and fourth generation ones are designed for supporting in addition to the voice service also a series of services of data and multimedia type.

Within this context a tendency of the market is not to replace completely the second generation mobile radio networks already operating with the new generation mobile radio networks but to integrate the two types of networks. The integration between new generation mobile radio networks and second generation mobile radio networks is made possible by the characteristics of the new standards defined in such a way as to enable this integration. Within the 3GPP standard which defines the characteristics of third generation systems such as the UMTS system for example different procedures are specified that allow to interwork with the GSM network.

In particular in the documents 3GPP TR25.881 Improvement of RRM across RNS and RNS BSS Release 5 and 3GPP TR25.891 Improvement of RRM across RNS and RNS BSS Release 6 the functional models and the network architectures within which the CRRM techniques find application are defined.

Another market trend is to use within well determined regions of territory the so called hot spots the WLAN Wireless Local Area Network technologies in order to enable the users present in these regions to gain broadband access to a series of telecommunication services e.g. access to the Internet . WLAN technologies can also be integrated within a mobile radio network in particular in the access network segment.

For this reason in the definition of the specifications of the different systems whether mobile radio ones or WLAN ones a series of activities are in progress aimed at defining the most appropriate interworking mechanisms among these systems also enabling the use of WLAN technologies e.g. IEEE 802.11 or else HYPERLAN2 for accessing to the third generation transport mobile radio network. The document TR 23.934 3GPP system to Wireless Local Area Network WLAN Interworking Functional and architectural definition Release 6 of the 3GPP standard for example specifies the functional requirements that should be met by the various network architectures that include the WLAN accesses belonging to the IEEE 802.11 family in the UMTS system. Likewise the document TR 101.953 of the ETSI standard specifies the interworking mechanisms with the UMTS network of the standard of a WLAN broadband type referred to as HYPERLAN2.

For the reasons set forth above mobile terminals such as for example cellphones palm top computers PDAs connectivity cards for personal computers etc. are already commercially available which are referred to as multi mode mobile terminals because they are not limited to operate with a single network following just one standard but can use indifferently various systems belonging to different standards. An example in this sense is provided by multi mode terminals that are already today able to manage indifferently the GSM UMTS and WLAN 802.11b standards.

Specified in the various standards cited above are only the architectures procedures and mechanisms for the interworking of the different systems with one another including therein the initial selection of what system to use at the moment of a service request. When a certain type of service is requested which on account of its characteristics can be supplied indifferently through different access systems GSM UMTS or WLAN a network operator can thus select which system to use by exploiting these mechanisms.

For example in WO A 02 32160 a technique for determining cell allocation in a network supporting different communication standards is described.

The Applicant has noted that this technique is not particularly efficient in the maximization of the performance of a multi access network. In fact it is based only upon the association of a different level of priority to the cells of the various systems without taking into account the fact that in the cell different traffic situations may thus arise in time that do not enable assignment of the network resources in a dynamic and efficient way according to the state of the different systems.

In Kalyanasundaram S. Chong E. K. P. Shroff N. B. Optimal resource allocation in multi class networks with user specified utility functions Computer Networks vol. 38 No. 5 pp. 613 30 the problem is considered of resource allocation in multi service networks where users specify the value they attach to obtaining different amounts of resource by means of a utility function. A resource allocation scheme is developed that maximizes the average aggregate utility per unit time. This resource allocation problem is formulated as a Markov decision process. Implications of deliberate lying by users about their utility functions are also discussed and a pricing scheme that prevents such lying is developed.

For a network operator managing a multi access network for example one comprising GSM and UMTS technologies and WLAN hot spots there arises however the problem of using all these technologies in a coordinated and synergistic way so as to provide the service requested thus maximizing the overall efficiency and the exploitation of the entire multi access network. In particular for a network operator it is expedient to define the CRRM policy which will establish each time and according to the type of service requested by the user the most suitable system to use and what criterion to apply to achieve the efficiency targets set.

The solution described herein defines an automatic method based upon an analytical process which in the presence of a new service request is able to identify the choice to be made in terms of maximization of the global performance of the multi access network i.e. which access networks available can be used to provide the service according to at least the following parameters 

Furthermore in the case of optimization of the revenue another parameter usable is represented by the values that can be attributed to each service. In greater detail the solution described herein is based upon the definition of a mathematical model of the multi access network according to a representation that uses Markov chains. In this case such chains are not however rigidly defined but conserve many degrees of freedom corresponding to the possible policies of assignment of the resources. The solution through an iterative procedure defines the value to assign to the free variables in order to optimize the index of performance chosen e.g. the blocking probability or the revenue .

The common management policies derived by means of the solution described herein prove to be more efficient than the known ones because the choices of allocation made each time a new service request arrives are all aimed for example at minimizing in overall mathematical terms the overall blocking probability or else at maximizing once again in overall mathematical terms the revenue for the operator.

Since the solution described herein identifies the policy of management of the radio resources with the aim of optimizing the overall performance the resulting rules can then also envisage that in certain given situations the network refuses to meet a request that reaches it albeit having at that moment sufficient available resources. This circumstance can arise for example when the network is found almost at the maximum limit of use of the resources in such cases in fact the preventive blocking of a specific service request for example a data request that reaches the network can enable the few network resources still available to be left free to give the possibility of serving a greater number of requests of other types of service for example voice requests .

There may also arise situations in which at a given instant it proves convenient to assign one and the same type of requests to one system e.g. GSM or else to another e.g. UMTS albeit in the presence of free resources on both of the systems. Also in such cases in fact choosing one system or else an alternative system can affect the overall performance.

According to the present invention the above object is achieved by means of a method having the features set forth in the ensuing claims. The invention also relates to a corresponding system as well as to a corresponding network and computer program product which can be loaded into the memory of at least one computer and includes portions of software code for performing the steps of the method of the invention when the product is run on a computer. As used herein reference to such a computer program product is understood as being equivalent to reference to a computer readable medium containing instructions for controlling a computer system to co ordinate the performance of the method of the invention. Reference to at least one computer includes a network apparatus and or the possibility for the present invention to be implemented in a distributed modular fashion.

In the currently preferred embodiment the provision of services to the users via the resources of a multi resource communication network is controlled by 

A possible scenario of application of the CRRM policies for service allocation on a multi access network is illustrated in .

In particular in which exemplifies cases of interest treated herein a region of territory is served through the GSM mobile radio network and a subset of that region is served also by the UMTS mobile radio network it will in fact be appreciated that the area covered by the access segment of the UMTS network will be at most coincident with that of the GSM network . Also considered is the presence of one or more limited areas of territory in which the services are offered through a WLAN system areas known as hot spots such as for example airports stadiums small urban centers hotels commercial centers buildings etc. . In the cases of practical interest said areas are usually located within the region served also by the cells of the UMTS network given that their use is envisaged in all those cases characterized by the presence of a high concentration of users with low mobility who require services of a data type.

The network architecture within which the policy of resource allocation identified by the solution described herein can find application is represented in and in greater detail in .

With reference to the architecture envisages the presence of an access network of a GERAN GPRS EDGE Radio Access Network type used by the GSM GPRS EDGE systems an access network of a UTRAN Universal Terrestrial Radio Access Network type used by the UMTS system and an access network of a BRAN Broadband Radio Access Network type used by WLAN systems. It will be appreciated that for reasons of simplicity the same reference numbers and have been used for distinguishing both the territorial areas mentioned previously and the access systems that serve them.

A transport segment 3G Core Network of the multi access network is interconnected with the GERAN access network through an interface called interface A or else interface Gb according to the core network domain to which it is connected with the access network UTRAN through an interface corresponding to the Iu interface and with the BRAN WLAN access through an interface in many cases called Iu like interface .

A network device that controls the radio resources of the GSM system known as BSC Base Station Controller a network device that controls the radio resources of the UMTS system known as RNC Radio Network Controller and a network device that controls the access points to the WLAN network known as APC Access Point Controller can exchange information through the transport segment also known as Core Network.

Alternatively the network device that controls the radio resources of the GSM system the network device that controls the radio resources of the UMTS system and the network device that controls the access points to the WLAN network can communicate directly through an interface corresponding to the Iur interface and an interface in many cases called Iur like interface .

The CRRM technique generated by the solution described herein can reside and be executed within the network device that controls the radio resources of the GSM system the network device that controls the radio resources of the UMTS system and the network device that controls the access points to the WLAN network. Alternatively it can reside and be applied within a network entity specifically assigned to the CRRM of the multi access network known as CRRM Server illustrated in .

The CRRM Server entity can request information on the GSM cells from the network device that controls the radio resources of the GSM system through an interface on the UMTS cells from the network device that controls the radio resources of the UMTS system through an interface and on the WLAN hot spots from the network device that controls the access points to the WLAN network via an interface for the moment the type of interfaces has not been specified in the standards . Both the architecture that envisages distribution of the parts of CRRM in the individual network controllers BSC RNC and APC and the architecture of in which the CRRM Server entity is present are suitable for supporting a generic CRRM technique.

As a whole in the scenario described real time services of different types are considered. For this type of services in fact it is important for the network to guarantee a well defined quality profile which cannot vary in time and hence if the network does have not the resources to be able to supply the service requested with the appropriate level of quality it is preferable for the new requests for that service to be blocked. By way of example together with the classic voice service it is also possible to hypothesize the presence of one or more data services of a real time type such as for example a video phone call data service belonging to CONVERSATIONAL class or the exploitation of multimedia content supplied by a network server data service belonging to STREAMING class .

According to the specific type each service can be allocated on one or more access networks that constitute the multi access network. The voice service for example can be offered via the GSM network or the UMTS network whilst a generic data service can be offered via the UMTS network or the WLAN network.

The solution described herein enables identification of a CRRM policy which in the presence of the possible service requests determines for each state of the system whether to accept or refuse the request and which access system to use to offer the service.

The solution described herein is founded on the modelling of the multi access network by means of a continuous time Markov chain CTMC . In the course of the present description the designation continuous time Markov chain will be used to designate a model of sequences of events where the probability of an event occurring depends upon the fact that a preceding event has occurred . For a mathematical definition of a CTMC it is possible for example to consult D. L. Isaacson and R. W. Madsen Markov chains Theory and Applications John Wiley Sons 1976 chap. 7 pp. 229 249.

A second element of the solution described herein is represented by the choice of the cost function to be optimized e.g. the blocking probability or the revenue deriving from the supply of the services .

The solution described herein takes concrete form in the implementation via the system elements illustrated in of an optimal CRRM policy by means of a technique that envisages alteration of the CTMC based upon the gradient of the cost function that has been chosen.

There now follows a description of modelling of the multi access network by means of a continuous time Markov chain.

Consider by way of example a system constituted by a GSM cell a UMTS cell and a WLAN hot spot with partially overlapping coverages see and users which require two different real time services a voice service and a generic data service. In the example presented herein it is supposed for reasons of simplicity without any loss of generality that there are just two services the voice service together with just one type of data service.

Assuming the presence of the constraints described above it is possible to define the N states of the multi access network through the following quadruple 

To model the behaviour of the multi access network through a continuous time Markov chain in which the generic state is constituted by the preceding quadruple also the maximum number of users of each service that can be managed with the radio resources made available by the individual access systems is specified.

In the case of the GSM cell the maximum number of voice users is represented simply by the number of circuits managed by the cell.

In the case of the WLAN hot spot it is possible instead to hypothesize that there is a maximum number of data users beyond which the WLAN access is no longer able to guarantee the profile of quality of service requested by the service. In the practical cases said maximum number of users can be identified by the persons skilled in the field for example considering the specific WLAN technology involved e.g. IEEE 802.11b and the throughput requested by the considered data service setting for example a minimum limit for the transfer speed of the data that it is intended to offer to each users or alternatively a limit to the maximum tolerable transfer delay .

Likewise in the case of the UMTS cell the different combinations constituted by the maximum number of voice and data users service mix that the cell can manage with the radio resources available are considered. As a whole said combinations identify the capacity region of the cell.

In general terms the capacity region can be defined uniquely by means of the function Cd n which expresses the maximum number of data users acceptable by the system in the presence of nvoice users and its inverse CV n which expresses the maximum number of voice users acceptable by the system in the presence of ndata users.

In practical cases the functions Cd and Cv that constitute the capacity region of a specific UMTS cell can be identified by persons skilled in the sector considering the profile of quality of service requested by the services considered and the amount of radio resources made available by the cell. A possible example of capacity region for a cell of the UMTS system which has to manage the voice service and the data service of a streaming type at 16 kbit skbit s in the uplink and 128 kbit skbit s in the downlink is illustrated in where given on the axis x is the number of voice users n and on the axis y the number of data users n . The boundary of the capacity region represented by the curve illustrated in corresponds to the limit beyond which the cell is no longer able to accept further users each of its points then represents the optimal traffic mix in which the cell works at full load. Instead underneath the curve the cell would be under used since it is possible to allocate other users on the basis of free available radio resources. In the case of the multi access network it should be considered that in addition to the UMTS cell that is able to manage both voice users and data users also the GSM cell and the WLAN hot spot are present. It is therefore possible to determine a corresponding joint capacity region as for example described in the deliverable D11 of the project IST EVEREST available on the Internet for download via the URL http www.everest ist.upc.es at the filing date of the present patent application section public documents document First report on the evaluation of RRM CRRM algorithms .

In general terms on the basis of the considerations made the capacity limits of the three access systems considered can be represented through the following relations 0 n GSMcap 0 Cv n 0 Cd n 0 n WLAMcap

According to the values assigned to the quantities just described and to the capacity region considered for the UMTS cell the multi access network is then represented by a continuous time Markov chain formed by a certain number N of states.

As regards the possibility of evolution of the system it is hypothesized that the traffic offered to the multi access network is made up of the following four types 

The four types of traffic just described are the ones that can occur in the scenario considered already presented with reference to .

Frequently in real cases in fact it is not always possible to use whatever access networks in field for each service request. This occurs above all because the areas of coverage differ in general from one access network to the other as a result of the characteristics proper to each access network it is known for example that an access of a WLAN type covers only a rather limited region of territory referred to as hot spot whilst a single cell of the GSM network or else of the UMTS network is able to cover a much wider region . Another reason for which it is not always possible to choose the most suitable network in absolute terms for providing a certain service lies in the fact that the service request can come from a specific terminal that is able to use only one particular type of access since it is not compatible with different standards .

On these traffic hypotheses the evolution of the system in the model with continuous time Markov chain can be viewed with reference to the i th state characterized by the quadruple i n n n n in the way represented in .

From the generic i th state at the centre of figure the system can then evolve towards the adjacent states represented as a result of the termination of a service in progress or else because the system accepts a new service request that reaches the multi access network.

As regards instead the frequencies of acceptance of the calls sessions quantities i they depend not only upon the requests and the resources available but also upon the CRRM policy implemented which according to the state has the purpose of choosing to which access system to assign the service request or else to establish when it is convenient to refuse the new request.

Furthermore on account of how the service requests are characterized the following constraints exist on the frequencies of the transitions regarding the voice calls i and i 

Likewise on account of the frequencies of the transitions regarding the data sessions i and i there are the following constraints 

Given the dependence of the frequencies of acceptance of the service requests upon the particular CRRM policy adopted as long as the values of the quantities are not specified the model so far described herein is able to represent the evolution in time of the multi access network constituted by a GSM cell a UMTS cell and a WLAN hot spot in which any CRRM policy whatsoever for assignment of the service requests is implemented. Consequently as explained in what follows the method proposed makes use of this mathematical representation for identifying through an iterative method the CRRM policy that is able to maximize the desired index of performance. Consequently at the end of the process of identification of the optimal CRRM policy the values of the quantities i i i i will be identified for each of the possible states i 1 2 . . . N .

More in particular the frequencies of transition and regarding the arrival of new requests of the voice service i.e. the first type of service provided by the multiresource network at the end of the process of identification of the optimal CRRM policy can assume the values indicated in Table 1.

The frequencies of transition and regarding the arrivals of new requests for data service i.e. the second type of service provided by the multiresource network can instead assume the values indicated in the Table 2.

Described hereinafter is the behaviour in steady state conditions of the continuous time Markov chain.

On the hypotheses of exponential inter arrivals and of exponentially distributed service times it is known that the CTMC chain is homogeneous and by resorting to the Chapman Kolmogorov equation used for the solution of homogeneous CTMCs the techniques for analytical solution of the chain i.e. the calculation of the probability Pof each state of the system in steady state conditions are known for this topic see again for example the text of D. L. Isaacson and R. W. Madsen Markov Chains Theory and Applications John Wiley Sons 1976 already cited previously and in particular Chapter 7 .

It is consequently possible to calculate the values P with i 1 . . . N of the probability associated to the N states of the system through which as described hereinafter it is possible to determine both the probability of blocking the service requests and the mean number of users served which is a quantity directly proportional to the revenue that can be derived from the supply of the two services considered .

The identification of the optimal CRRM policy can be executed having defined a priori a criterion of optimization minimization of a cost or maximization of a gain . The technique proposed can then be applied once the reference cost function has been decided.

It is possible to define the blocking probability and the revenue associated to each state of the system in the following way 

where designate respectively the revenue associated to the provision of the individual voice service on GSM voice service on UMTS data service on UMTS and data service on WLAN.

At a global level the overall indices of performance of the CRRM policy are derived in the following way 

By choosing either one or the other criterion of optimization it is then possible to design the optimal CRRM policy with respect to said criterion.

It will on the other hand be appreciated that the cost functions identified previously correspond to just two examples of possible choice evidently linked to normal criteria of management of telecommunication networks. It will on the other hand be appreciated that the invention is in no way constrained to any particular choices of cost functions.

In what follows a technique is described that considers the optimization based upon the minimization of the blocking probability. In an altogether similar way it is possible to consider the maximization of the revenue.

As mentioned previously maintaining the constraints of Equations 1 2 3 and 4 the values of i with j 1 . . . 4 can be assigned for each state i depending upon the CRRM policy used. For some states some of the will not be freely assignable but constrained by the system itself for example in the proximity of the states of the system corresponding to completely occupied resources .

Consider the list of the i freely assignable albeit constrained to Equations 1 2 3 and 4 and let said variables be designated by with k 1 . . . R where R is their number obviously R N 4 .

The indices of performance B and S or others that may be identified for example the total number of the calls in progress or linear combinations of the indices cited above can be viewed as functions of the .

is equivalent to identification of the best possible CRRM policy at least on the hypothesis of expected traffic characteristics.

The search for said absolute minimum is in general not trivial. In practical cases also the search for a local minimum may be sufficient for determining CRRM policies the performance of which is clearly superior respect to known methods as will be briefly shown in the sequel of the present description.

The method described in what follows is able to find a CRRM policy with optimized performance corresponding to a local minimum by using of the gradient 

There now follows a description of the technique of optimization of the CRRM policies based upon the gradient of the cost function.

Starting from a gradient vector G . . . defined in what follows described here is an iterative method for optimizing the CRRM policy once the desired index of performance blocking probability or revenue has been chosen. To optimize the CRRM policy for allocation of the services it is necessary to calculate a vector . . . in such a way as to minimize the cost function F.

Usually this starting solution is chosen in such a way as to correspond already to a sub optimal solution of the problem identified for example by resorting to known analytical techniques or to heuristic criteria of common sense such as the simple policy to which reference will be made in what follows.

In a step there are identified the set Cof the indices of the components of the vector which are candidates for being reduced to their minimum value and the set Cof the indices of the components of the vector which are candidates for being increased to their maximum value namely 0 

In terms of operation it means identifying on the Markov chain that describes the system with some degrees of freedom the transitions that are still free which can be suppressed or entered respectively. Let Cbe the union of the components identified namely 

If so in a step the technique has found an optimal solution defined by the vector and the process terminates.

Identified in a step is the subset C Cof the indices of the components of for which the gradient of the cost function is at least 10 of 10 is considered an empirical value to achieve good results a value that is too low slows down too much the numerical calculation a value that is too high risks the loss of good solutions .

The subset C Cof the indices of the components of for which the gradient of the cost function is at least 10 of is then identified.

Assigned to the components identified in C is the minimum value admissible i.e. zero assigned to the components identified in C is the maximum value admissible refer to the previous reported Table 1 and Table 2 .

The solutions thus identified define according to the criteria exemplified in Tables 1 and 2 above the policy of management of the multi access network.

In order to evaluate the performance of the methods proposed as initial solution referred to in step of the flowchart of the choice has been to use the elementary CRRM policy referred to in what follows as simple policy proceeding in the following way 

The simple policy hence envisages assigns a voice request preferably on the GSM and as a second choice if possible on the UMTS likewise a data request is preferably assigned on the WLAN and as a second choice if possible on the UMTS.

Illustrated in what follows are the values considered in the example for generating an optimized method and evaluating its performance with respect to the initial simple policy 

Where a numerical value is indicated this means that the value is assumed always as the one specified. In the other cases distinguished by the value will be specified each time even resorting if necessary to the following compact notation 

to specify completely the conditions on which the method has been generated and evaluated the criterion of optimization according to blocking probability or according to revenue will be specified separately .

The graph shows how using the CRRM policy obtained through the proposed method it is possible to obtain probabilities of blocking of the service requests that are considerably lower than the ones corresponding to the starting simple policy.

The graph shows that also using the CRRM policy optimized for revenue an all round better performance is obtained. Both the blocking probability and hence the revenue are markedly better than what can be obtained through the elementary reference policy.

Since a generic CRRM policy is called upon to manage the radio resources at the level of individual cells of the different access segments the description of the proposed method is limited to considering just one cell for each of the access networks present.

This is in no way prejudicial to the possibility of applying the method in a more general context. To define a CRRM policy valid for an entire portion of a multi access network that regards a specific region of territory in fact it is simply necessary to take into consideration the different cells present in the region of territory considered analysing what relation exists between the cells of the different access networks that cover portions of territory jointly. From the mean distribution of the traffic over all the specific region of territory considered and from the configuration of the radio resources of the cells it is then possible to derive the frequency of the service requests that can be managed by one or more of the access networks.

The method proposed has been illustrated considering the access networks GSM and UMTS and a WLAN hot spot. The method is in any case applicable in the case where there is present a different number of access networks and or access networks of a different type. In fact the method in itself is not based upon any specific mechanism of the access systems considered but takes into consideration only the maximum number of users that can be managed with the radio resources available. It is therefore sufficient that the various systems involved should envisage in a direct or else indirect way a maximum limit to the number of users of a given service that can be managed with the radio resources available. This occurs in all the real cases in which in general the various mobile radio systems can avail themselves of a necessarily limited amount of radio resources. According to the specific standard considered the limit will be determined by the particular techniques of transmission adopted and by the corresponding practical factors involved.

It is known for example that each cell of the GSM system has a maximum number of voice circuits identified during the sizing of the system whilst in the UMTS system said limit can be due according to the cases either to the maximum amount of interference that the system is able to manage with the powers available or to the code number that can be used to identify each user. In other systems for example in the case of an area served by a hot spot of a WLAN type the maximum number of users for a given service could be determined on the basis of the minimum level of quality of service that it is intended to offer to the users establishing for example a minimum limit for the throughput of the data that it is intended to offer to each of the users present or else a limit to the tolerable transfer delays .

The method has been illustrated with reference to a system in which two services voice and data are envisaged which give rise to four types of requests voice only on GSM voice on GSM or UMTS data only on UMTS data on UMTS or WLAN . It may however be extended in a similar way to a generic case with an arbitrary number of types of services and requests of various types.

Also the method for optimizing the cost function can be replaced by similar methods for example by setting the threshold of step to 5 without changing substantially the logic followed by the method. In this sense for example further conditions for instance by stopping the process of optimization when the cost function does no longer vary significantly in order to evaluate the conditions of termination of the iterative process can be used instead of what has been described without altering the logic of the method illustrated.

The method described herein at a high level through the flowchart of can be conveniently implemented and translated into any language suitable for its automatic execution for example using the well known Matlab tool. In turn the policy of resource allocation generated by the method can be implemented within the microprocessors present in the network devices that manage the radio resources of the systems present.

The sequence of operations described aimed at identifying an optimal policy of management of a multi resource network can be executed periodically and or at time intervals identified in such a way as to correspond to different conditions of operation of the network for example according to various traffic conditions.

Consequently without prejudice to the underlying principles of the invention the details and the embodiments may vary even appreciably with respect to what has been described by way of example only without departing from the scope of the invention as defined by the annexed claims.

