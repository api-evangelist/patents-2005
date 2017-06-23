---

title: Program flow control in computer systems
abstract: Application programs supporting multiple contexts on a computer system having an operating system supporting threads. The method comprises processing a context processing instruction from the run-time application program, evaluating said instruction in relation to program-flow control yielding context-defining processing parameters, analyzing the context-defining processing parameters from the execution context of the context processing instruction in regard of program flow management by threads, mapping the context-processing instruction to a selected thread managing instruction, or to a selected set of thread managing instructions, having a respective program flow control effect equivalent to that of context-processing instruction, invoking the selected thread managing instruction or the set thereof, together with selected parameters so that that during runtime of the application program only one thread is allowed to execute at a time, and the program state of a thread is stored at a given point in time and is restored later from the point in time.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07559063&OS=07559063&RS=07559063
owner: International Business Machines Corporation
number: 07559063
owner_city: Armonk
owner_country: US
publication_date: 20050603
---
The present invention relates to program flow control in computer systems and in particular to a method for running application programs on a computer system having an operating system supporting threads semaphore mechanisms and long jumps wherein said operating system does not support context processing due to the lack of a mechanism to access the central processing unit CPU state.

The general purpose computer a finite approximation of the universal Turing machine maintains state only in a finite set of transistors and optionally in a limited magnetic storage. A specific portion of the state of a program running within a computer is defined herein a context as used in prior art terminology. A context may be regarded as a snapshot of the runtime flow of a program as seen by the CPU. In large this snapshot contains the set of CPU computational registers the instruction pointer a record of the execution path of the program ie the invocation stack and the possibly separate but associated automatic storage and function call parameters residing along the execution path ie the parameter stack. A context does not encapsulate memory allocated from heap and does not maintain a copy of the static storage used in runtime of the application program.

Maintaining multiple contexts is useful for programs wishing to sustain multiple concurrent runtime states but where only one state is active at a time. Discrete simulation is a typical example modeled entities might maintain state by running as separate computational tasks. In this case in prior art computer systems supporting context processing a simulation manager orchestrates which entity performs each discrete simulation step. After each step the entity returns control to the manager.

For example on UNIX platforms so called u context functions are provided as part of the operating system. Such u context functions may be seen herein as a standard Application Programming Interface API for storing and restoring a program s runtime context. Any reference thereto is to be understood broadly and shall include also implementations other than UNIX.

The API set consists of four functions. All functions operate on a structure defined as ucontext t. The information in ucontext t is sufficient for restoring the CPU to a precise program execution state. In alphabetical order 

In general the need to keep multiple program flows active and interacting with one another while each flow is independent is best satisfied in prior art by the use of context processing . Prior art contexts also provide a basic infrastructure needed for co operative multitasking. One prior art approach to task orchestration is to rely on a sort of context to context messaging to provide the context switch triggering events.

Disadvantageously in many business environments there are many platforms in use that do not support context processing while applications increasingly require the ability to process multiple contexts. The basic structure of the prior art thread based program control is depicted in . A runtime version of an application program depicted left in comprises exemplarily a number of three tasks A B C. Each task is executed in a respective thread A B C. At the end of the thread run which flows in a direction from bottom to top as indicated by the arrow a respective semaphore mechanism A B C indicates the end of the thread to the CPU . The application itself must control the sequence of the threads e.g. by prior art semaphore mechanisms.

Generally such environments are platforms in which the operating system does not offer any instruction which enables updating the CPU state as described above. Examples for such platforms are the IBM iSeries server which is used in enterprises successfully since more than 15 years further platforms on which interpretive languages run on which platform independent languages like Java run.

A prior art approach discloses a mechanism to swap contexts between threads. Disadvantageously this prior art approach does not offer full context compatibility as it does not provide a setcontext and getcontext capability.

It is thus an objective of the present invention to offer the ability to run application programs designed for context processing on above mentioned platforms which per se do not support context processing.

This objective of the invention is achieved by the features stated in enclosed independent claims. Further advantageous arrangements and embodiments of the invention are set forth in the respective subclaims. Reference should now be made to the appended claims.

According to the basic aspect of the present invention a method is disclosed for running application programs supporting multiple contexts on a computer system having an operating system supporting threads and not supporting multiple context processing instructions 

b evaluating said instruction in relation to program flow control yielding context defining processing parameters 

c analyzing said context defining processing parameters from the execution context of said context processing instruction in regard of program flow management by threads 

d mapping said context processing instruction to a selected thread managing instruction or to a selected set of thread managing instructions having a respective effect of program flow control equivalent to that of said context processing instruction 

e invoking said selected thread managing instruction or said set thereof together with selected parameters for guaranteeing that during runtime of said application program 

e2 the program state of a thread may be stored at a given point in time and may be restored later from said point in time.

The state of a program may be understood in here to comprise the values of sp stack pointer fp frame pointer and pc program counter . A program state is thus completely defined by these set of registers and the contents of the memory which includes e.g. the heap and the stack.

In simpler words the inventional method performs a mapping of semantics and syntax of existing prior art context processing functionality and in particular of the so called ucontext API functionality used for prior art context processing to said threads semaphore mechanisms and long jumps for emulating context semantics wherein the context semantic is defined as the ability to store the current state of a processor in any point of runtime of the application program and to restore any previous processor state. Thus above measures e and e provide for successful mapping between context processing and thread management either in single threaded but in particular in multi threaded environments.

Thus the general advantage is achieved that applications which are designed for context processing may be run on platforms which do not support context processing. The present invention allows to use application programs using prior art context processing in multi threaded operation environments without needing to change the application code. For the sake of concreteness the context processing is herein described exemplarily by aid of u context processing instructions.

The idea behind this inventional approach is that the information in a context is a superset of that which is required by prior art setjmp or sigsetjmp operating system operations The setjmp interface provides a method to return to any previous point in a program. The ucontext interface in contrast is able to manage separate and complete invocation paths.

The difference between threads and contexts is semantic contexts are serial in nature whereas threads are parallel only one context is active at a time. Like threads contexts provide the ability for a program to contain multiple execution flows though unlike threads contexts guarantee serial access to resources.

Further advantageously the execution of a thread may be stopped by a semaphore instruction when in the the run time application program execution a getcontext instruction is executed.

Further advantageously a thread is encapsulated by a class providing invocation suspend and resume methods.

According to the invention contexts and threads may coexist. A thread itself can contain multiple contexts such that any single thread is executing only one context at a time but multiple threads could be executing their current contexts in parallel.

The u context interface in particular has the ability for a context switch to return to any previous save point inside a context. The program sequence initiating the switch can select to switch to any save point inside another context. This is an advantageous feature not intrinsically possible with threads alone.

Thus the above mentioned prior art by Novell may be greatly improved by the inventional context to thread mapping mechanism. Further in existing applications which only use makecontext and swapcontext APIs the swapping context reduces to simple semaphore control without the need to record CPU state in sigjmp buf buffer structures. During swapcontext the current thread is thus stopped and the one to be activated is released.

With general reference to the Figures an exemplary implementation of the inventional method will be described in more detail.

With reference to a system diagram is given first representing the most important structural elements used in the inventional method. With concurrent reference to respective basic steps of the control flow during the inventional method are depicted.

Again the Application program is depicted left. It is designed for context processing and thus comprises the prior art context processing APIs and in particular those mentioned earlier ie set context and getcontext instructions depicted by reference sign .

The currently active context is depicted logically within the Application program which is dependent on context processing as a mechanism for internal process flow control. The application program profits from the advantages inherent of context processing. The context is defined to comprise the elements as known from prior art namely invocation stack parameter stack storage call parameters instruction pointer etc.

The before mentioned prior art application program is designed for context processing and may be assumed to be linked with an inventional program implementing the before mentioned mapping or conversion layer between context and thread instruction.

Then the resulting executable program may be assumed to specify at any given point of run time a u context specific instruction. The inventional method processes this instruction by reading it step . Then an evaluation step is performed aiming at exactly emulating the context processing with thread processing. Thus the read context instruction is interpreted in this sense and in a subsequent step the thread processing is prepared by generating the thread specific parameters required to run a thread instead of the context originally planned by the application programmer.

So for example a getcontext invocation done by the application program takes a snapshot of the current context ie computing state whereas a setcontext invocation requires a context specified by either makecontext API or getcontext API and switches the CPU to start executing in the new context.

According to the invention this is realized by thread switching step as well as by setjmp see step and longjmp calls which are thread specific instructions see step and the box which thus provides for a kind of u context emulating layer between the Application and the CPU as it converts the u context requests issued by the Application program code to thread managing instructions as in particular to setjmp and longjmp calls and semaphore mechanisms or whatever control functions the operating system offers for thread control.

Those calls however instruct the CPU to execute the new threads see step as defined by said calls. Thus the CPU behaves as if executing in a new context. As visible from the drawing a thread can be stopped according to the inventional method by semaphores advantageously at any desired location within a thread which is symbolically indicated in box . In the context C is depicted to be executed by the CPU after being invoked by the instruction setcontext C in the Application code left side . A Thread buffer is used comparable to prior art use in order to store the processor state relevant to the point in time when the getcontext invocation see e.g. getcontext C was done. The setcontext invocation thus triggers a read out of the data collected in the thread pool for context C and a respective executing thereof with CPU .

Thus a thread provides the invocation stack for a context. Further semaphores i.e. program instructions implementing a prior art semaphore mechanism are advantageously used to control which one of the threads is active at any point in time. It should be noted that the semantics of the context APIs make prior art thread switching using only semaphores insufficient as described above in the description of prior art as the application programmer is free to call the getcontext function at any time in his program. As by definition it must be thus possible to jump into any active execution point stored by getcontext a setcontext must first switch to the thread to be activated using semaphores then it must restore the in the thread context.

Next the definition of the prior art ucontext t structure is given in order to improve clarity which is used to record and transfer the CPU state. Many elements familiar to the Unix implementation remain advantageously for the reason of compatibility most notably the member uc stack is typically set by Unix applications to allocate a call stack for new contexts before the call to makecontext .

According to the invention within the ucontext t structure two independent sets of flow control information are present 

This processor state buffer is advantageously the standard sigjmp buf buffer used by sigsetjmp and siglongjmp functions . For C programming language runtime programs that do not maintain masks for asynchronous signals the buffer jmp buf as known to a skilled reader is sufficient.

The three APIs getcontext makecontext and setcontext are described next by flow chart diagrams in and respectively wherein the direct mapping to thread control instructions according to this inventional embodiment is disclosed where applicable.

With reference to the getcontext instruction mapping is disclosed next in more detail using a C macro left portion calling a C function right portion 

The main purpose is to record a snapshot of the CPU and of the signal state. This function getcontext ucontext t ucp initializes the ucontext t structure passed into the function retrieves the current signal mask and then calls the function sigsetjmp left portion to acquire the register set. In this specific implementation the portion of the function that invokes sigsetjmp must be contained within a C language macro as it needs to run in the stack frame of the caller.

With reference to the inventional makecontext instruction mapping is disclosed in a similar way. This function builds up an ucontext t structure such that a specified function with specified parameters is invoked when the context is made active.

According to the inventional embodiment a thread is encapsulated by a class providing invocation suspend and resume methods. An instance of the thread class is created at this point and the pointer is assigned to the uc thread of the input argument to makecontext . Then the thread is started.

With further reference to which may be subsumed under the step in started by makecontext the thread s bootstrap function immediately suspends the thread awaiting to be awoken by setcontext at a later point in time. with reference to a call from another context to setcontext has made the context referenced in active this context had been suspended at the end of signals are unblocked by applying the signal mask of the parent context acquired during getcontext .

A user function passed to makecontext is awarded control see the right portion in the Figure. The user function is the main routine of this new context. Until the user function returns or the user function invokes another setcontext function this context will remain active. When this context runs to completion user function returns the bootstrap function activates the parent context the other context that had last invoked setcontext to make this context active so that it appears the parent returned from setcontext see Part in setcontext as defined further below and shown in .

With reference to and which may be subsumed under the step in the setcontext instruction mapping according to this inventional embodiment is disclosed next in more detail 

The setcontext function may be regarded as the very core of the u context routines. It performs three tasks in sequence depicted in and respectively. In words setcontext suspends the thread of the active context releases the thread of the destination context then loads the CPU with the register set stored in the CPU snapshot by calling longjmp with the information recorded by the associated getcontext .

As revealed from Part setcontext activates the destination context thread by releasing its semaphore. The activated thread context starts executing at Part or begins executing the function specified to makecontext . As revealed in Part the context that had invoked setcontext suspends itself by acquiring its own semaphore.

Note that the steps in the flow chart involving signal masks and blocking signals are included for completeness it is necessary to block asynchronous signals while in the midst of the context switch though under normal conditions asynchronous signals would not be sent to the application process.

As revealed in part if the destination thread context has not yet ended NO branch it loads the CPU with the snapshot from getcontext or in the YES branch it returns regularly if the function passed to makecontext ended normally. In the case where the destination thread context ended the user s context function passed to makecontext returned any thread resources allocated during makecontext are freed.

It should be noted that setcontext might be active in two threads simultaneously for a short moment the setcontext least recently invoked is the first to complete as Part and above executes in one thread and Part executes in another thread. The context executing in Part may be a context either 1 suspended by a previous call to setcontext or 2 built during a call to makecontext and suspended in ThreadMain the new context s bootstrap 

According to an inventional swapcontext function implementation is disclosed for showing the advantageous feature of swapping between contexts.

Basically this is a combination of getcontext followed by setcontext . A Boolean on the local stack flags the procedure to initiate setcontext or to return directly from getcontext .

With reference back to the general aspects of the invention without a specific figure in reference according to a preferred aspect of the invention two pointers maintain state information between different contexts. One is the global current context pointer. It is set to the context thread that is currently active. The other is the uc link field within each ucontext structure that points to the parent context. The uc link is not typically modified by the application. By modifying this field however an application could modify to which context control is returned when an active context ends by way of returning from the user defined function previously passed to makecontext .

In other words the uc link is either set to current context when getcontext is called or could be assigned by hand to construct a parent child relationship in order to obtain an atypical return sequence when context were to end see the description for above .

As the astute reader might recognize further optimizations can be made and some extensions may be incorporated as for example 

With a slight modification of the concept shown above it is also possible for a program that is itself multithreaded in the typical sense referred here to a program containing a set of primary threads to use contexts independently within each primary thread. Supporting this paradigm requires that current context information that is global in the single threaded case be stored in thread local storage the appended pseudo code example demonstrates multi threading capable code . The multi threading supporting implementation is transparent to the application using the u context APIs and is merely an enhancement that overcomes the single threading restriction of the before mentioned description.

The present invention can be realized in hardware software or a combination of hardware and software. A tool according to the present invention can be realized in a centralized fashion in one computer system or in a distributed fashion where different elements are spread across several interconnected computer systems. Any kind of computer system or other apparatus adapted for carrying out the methods described herein is suited. A typical combination of hardware and software could be a general purpose computer system with a computer program that when being loaded and executed controls the computer system such that it carries out the methods described herein.

The present invention can also be embedded in a computer program product which comprises all the features enabling the implementation of the methods described herein and which when loaded in a computer system is able to carry out these methods.

Computer program means or computer program in the present context mean any expression in any language code or notation of a set of instructions intended to cause a system having an information processing capability to perform a particular function either directly or after either or both of the following

Finally an exemplary C code example is appended in order to assure the completeness of the present disclosure.

The original version had a dependency on the uc link field that it had to point to a context containing a thread. This required that the thread context that a uc link was pointing had not to be deleted until all children referencing the context were deleted or at least not activated .

