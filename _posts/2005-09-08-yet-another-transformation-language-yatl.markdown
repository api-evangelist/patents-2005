---

title: Yet another transformation language (YATL)
abstract: A practical language for writing analysis and transformation tools for C/C++ and other languages is provided. This language, YATL, is imperative in style and designed to be easy to use for someone familiar with the grammar of the target language. It allows the developer to describe transformations with reference to elements of the target grammar through a pluggable personality to a compiler. This provides the means for powerful, yet easy to write, transformation programs, while fundamentally remaining language agnostic.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08813047&OS=08813047&RS=08813047
owner: Alcatel Lucent
number: 08813047
owner_city: Boulogne-Billancourt
owner_country: FR
publication_date: 20050908
---
The present invention relates generally to the field of computer software and in particular relates to meta programming and domain specific programming languages for writing source code transformations.

The proliferation of large and complex computer programs has made source code transformation solutions increasingly attractive. Source code transformations are a form of meta programming. Machine drive analysis and modification can relieve the manual developer of much of the burden of repetitive change. However for source code transformation to be successful the developer must be able to clearly define what and how modifications should be made. Herein lies the need for a transformation programming language.

Existing languages cannot attain high fidelity. Many existing languages require expertise in the use of functional or other programming paradigms that are not intuitive for developers familiar with procedural languages. Existing languages are too generalized and focus on rewriting abstract syntax trees AST in a general form without any provision for target language awareness in the transform language resulting in a lack of expressiveness. Existing languages are not sufficiently powerful and flexible. Existing languages are based on the specification of rules in the form of predicates and actions. This limits the usefulness of the language and the ability to perform auxiliary calculations.

Various deficiencies of the prior art are addressed by various exemplary embodiments of the present invention of a programming language YATL for writing source code transformation tools for a target language such as C C .

One embodiment is a method for generating analysis and transformation tools. One or more YATL program s for transforming ASTs are stored on a storage medium. The ASTs correspond to target source code. The YATL program s are compiled to produce one or more transformation program s . The transformation program s are executed with the ASTs as input to produce a number of transformed ASTs. The YATL program includes a tree traversal routine having access to a target symbol table. The target symbol table holds symbols from the target source code where each symbol is associated with a unique scope identifier. A scope is a programming language term to denote a range of existence for a symbol.

Another embodiment is a system for generating analysis and transformation tools including YATL programs a YATL compiler a YATL parser a run time one or more storage device s and a processor. The YATL compiler compiles the YATL programs and the YATL parser parses the YATL programs using a YATL grammar. The run time is an environment for executing YATL programs. The storage device s store the YATL programs YATL compiler YATL parser and run time. The processor compiles and executes the YATL programs. The YATL programs operate on ASTs to produce transformed ASTs. One of the YATL programs includes a tree traversal routine that has access to a target symbol table. The target symbol table holds symbols from the target source code where each symbol is associated with a unique scope identifier. The YATL program includes an on construct for altering a tree temporarily for a single action a using construct for altering a tree for the duration of a compound statement and a variable reference construct for permanently altering a tree across rules and functions.

Another embodiment is a computer readable medium that stores instructions for performing a method for generating analysis and transformation tools. The instructions include a YATL program that has one or more statement s . Each statement is one of the following a rule a function definition a callback function definition a preprocessor directive or a Stratego program. The rule includes rule followed by an identifier rule parameters and a compound statement. The function definition includes sub followed by the identifier function parameters and the compound statement. The compound statement includes at least one YATL statement optionally followed by an else clause. The YATL program includes a tree traversal routine having access to a target symbol table. The target symbol table holds symbols from a target source code where each symbol is associated with a unique scope identifier.

To facilitate understanding identical reference numerals have been used where possible to designate identical elements that are common to the figures.

The invention will be primarily described within the general context of an exemplary embodiment of a programming language YATL for writing source code transformation tools for any kind of target language such as C C . However those skilled in the art and informed by the teachings herein will realize that the invention encompasses obvious changes in grammar and syntax and is directed to the broad concepts implemented by the exemplary grammar syntax and constructs described. Exemplary embodiments of YATL have a wide variety of applications in automated source transformation including redundant code removal dead code removal code refactoring platform and application programming interface API migration debugging instrumentation and fault detection performance analysis instrumentation bug rectification source code watermarking security hole identification software fortification and many other applications.

An exemplary embodiment of a programming language YATL for writing source code transformation tools for a target language such as C C is provided. YATL allows developers to specify and realize algorithms that both analyze and transform source code. Developers use YATL to write tools that perform analysis and modification of abstract syntax trees and their hybrid forms. YATL allows the developer to describe transformations with reference to elements of the target language grammar making powerful transformation easy to specify. YATL is target language agnostic through a compartmentalized piece of syntax that can be implemented as a pluggable personality of the compiler. YATL is PERL like in style e.g. typeless and procedural. Unlike existing code transformation languages YATL does not require any prior knowledge of computation linguistics and transformation programming techniques. Writing YATL transformations is intended to be easy for anyone who can write C and C programs.

In this exemplary embodiment a YATL system provides primitives and run time support for many capabilities including the following template based searching of program constructs through tree traversal specific to the target language program construction through templates and or by example basic flow control and failure handling basic data handling e.g. integers strings lists extensibility through direct access to the back end intermediate representation e.g. Stratego and C access to underlying operating system facilities e.g. console I O and support for target language symbol tables among others.

In this exemplary embodiment the YATL compiler takes YATL programs and builds a transformation tool executable. Some exemplary command line options for the YATL compiler include generating only backend e.g. Stratego code not using precompiled binaries for run time specifying an input source file specifying output file whether to keep intermediate files optimization levels and whether to turn on debugging.

An exemplary process for using the meta programming environment is as follows. A source program is given e.g. myprog.cpp . Then the YATL program is written e.g. simple.yatl . The transformation tool is generated e.g. simple . An XML project file is created that coordinates the execution of the transformation tool with respect to the target source files. The tool e.g. simple is executed which applies the transformation to the source program. Transformed programs are output to the output file e.g. myprog.cpp.out . Each of the tools that are generated from the YATL compiler is a stand alone executable in themselves. They are designed to be efficient and tailored for rapid execution.

Automated source code transformation a k a source transformation is defined as the machine executed modification of program source code that is directed by automated program analysis. As a software development paradigm source code transformation can be used to generate tools that reduce time frames and lower costs for a wide array of software maintenance tasks. Examples include software migration porting debugging and profiling instrumentation redundant code removal security vulnerability remediation and design refactoring e.g. conversion to object oriented design .

For many companies a significant portion of software development is done in the C and C programming languages. Furthermore it is source code written in these two languages that is predominantly involved in the software maintenance tasks listed above.

The term target language means the language that is the subject of transformation and the term transformation language describes the meta programming language itself i.e. YATL . Furthermore the phrase source code transformation means a class of meta programming that includes both static analysis and program modification.

In one embodiment of YATL design considerations included the degree that the language allows a developer to express his or her intent with respect to the domain e.g. source code transformation how much of the functionality of the program is expressed by its source code the extent that the language naturally allows the developer to avoid repetition and excess levels of verbosity and how intuitive the language is to the user. Many existing transformation languages are target language agnostic that is they are designed for writing transformations on nay target language. Examples include TXL and Stratego. Such generic languages are often cumbersome to use practically because making reference to elements of the target language grammar is difficult to do.

Stratego s ability to interface with native functions written in C provides excellent means for extensibility. Most of the back end logic of Proteus was implemented in Stratego or C with some elements in YATL itself. Other embodiments may be implemented in many other kinds of code.

One exemplary embodiment of YATL is typeless there is no type checking by the compiler. All data is represented as an ATerm tree or a forest of trees . Variables are not declared but like PERL memory is allocated when the variable is first used. All variable identifiers are prefixed with . An exemplary code excerpt for variable initialization is shown in Table 1.

In this exemplary embodiment introspection which allows one to determine the type of data is supported through method call style invocations on the variables. An exemplary code excerpt for variable introspection is shown in Table 2.

In this exemplary embodiment the basic YATL types are string list integer real number and blob size buffer pair . Other embodiments can have many different kinds of types.

In this exemplary embodiment the basis for transformation in this embodiment of YATL is the modification of target program representations in the form of abstract syntax trees ASTs . At any point in a YATL program there is the notion of the current tree i.e. the piece of data that is being modified. The piece of data is a tree representing a program in whole or in part. The current tree is accessible through the special variable  . If the YATL programmer wishes to change the subject of modification the programmer can either alter the current tree by explicit assignment to   or temporarily modify the subject of transformation through YATL s on construct. The on construct modifies the subject of transformation for the duration of the associated compound scope. The language term scope means the logical range of a program construct. The variable entry in the symbol table is updated at termination of the scope. An exemplary code excerpt for accessing the current tree is shown in Table 3.

Alternatively illustrates modification by reference this exemplary embodiment of YATL through the on primitive which allows making reference to one or more subtrees within the current tree as marked by a YATL pointer . Table 5 illustrates statements executed on each subtree marked by pointer p.

In this exemplary embodiment when data is assigned to a YATL variable a copy of the right hand side tree is made. Replication of trees in this way is made efficient through the ATerm maximal sharing mechanism. This mechanism minimizes memory footprint by careful reuse of subtrees and a copy on modification scheme. As a result the overhead of pass by value is not a concern to the YATL programmer.

An alternative method of data passing in this exemplary embodiment is pass by reference. This is facilitated by YATL pointers which are prefixed with . Pointers are implemented as annotations on the tree which can be used to locate a given subtree at a later point in time.

In this exemplary embodiment there are two types of YATL pointers local and global. Local pointers are unique i.e. the annotation is different for each assignment. De referencing local pointers always results in zero or one iterations. Global pointers are prefixed with and use the exact same annotation for each assignment. De referencing a global pointer results in zero or more iterations. The global pointer is useful for marking a series of constructs of interest and then performing some action on all of them.

The on construct is also used to change the subject f transformation to that pointed to by the given pointer. However when pointer arguments are used with the on construct the primitive is implemented as a traversal on the current tree matching on the respective pointer annotation. Hence the current tree must contain the annotated subtree for the de reference to be successful. An exemplary code excerpt for setting a pointer to the current tree is shown in Table 6.

In this exemplary embodiment variables in YATL cannot be explicitly deleted. The ATerm garbage collection system frees any unused memory. However pointer annotations can be deletable through an explicit application of the rule clearptr that traverse the tree and removes the appropriate annotations. An exemplary code excerpt for applying the rule clearptr is shown in Table 7.

In this exemplary embodiment YATL variables can be directly used within strings like PERL. If the variable is not assigned then the replaced text will be empty. To protect a from interpolation a is prepended. An exemplary code excerpt for this protection is shown in Table 8.

However variable interpolation does come at a cost because the string is actually assembled at runtime. Therefore some embodiments avoid interpolation for constant strings. For example the following exemplary code excerpt shown in Table 9 is not ideal.

In this exemplary embodiment YATL variables are implemented as ATerm trees. Trees are put together to form a tuple. Given three individual trees A B and C a single tuple term A B C is constructed. The reverse process is deconstruction which splits a tuple into its constituents. Tuple deconstruction fails if the arity is incorrect. In this exemplary embodiment the YATL syntax for tuple construction and deconstruction is shown in the following exemplary code excerpt in Table 10. Construction and deconstruction is useful for returning data from functions that by design only return a single term value.

In this exemplary embodiment YATL support basic integer arithmetic. A summary of the supported operators in this exemplary embodiment is shown in Table 11. Other embodiments support various other classes and operators and have varying orders of precedence.

In this exemplary embodiment YATL programs are modularized through the use of rules and functions. Rules are defined by the keyword tifamily rule and functions are defined by the keyword tamily sub . Rules can be thought of as syntactic sugar for functions that take the current tree as a parameter and assign the result to the current tree. Rules are called through the apply primitive. They differ from functions in that they inherently act upon the current tree e.g. invisibly passed as the first parameter. The main rule serves as the entry point to the transformation.

In this exemplary embodiment calls to functions may also include the current tree but this must be explicitly passed as a parameter. Furthermore functions have no effect on the current tree unless the result of the call is explicitly assigned to the current tree variable  . The following code excerpt in Table 12 illustrates the use of rules and functions to modify the current tree.

In this exemplary embodiment both rules and functions support parameters. Parameters specified on the main rule correspond to command line parameters. For instance in the above excerpt in Table 12 the main rule parameter v corresponds to a command line parameter v where string s is assigned to the variable v.

In this exemplary embodiment rules and functions can also be passed as parameters to other rules and functions. The prefixes sub and rule are used to disambiguate an identifier rule is assumed by default . Of course conventional parameters variables and pointers can be passed in addition to functions and rules. An example is shown in the code excerpt in Table 13.

Many programming languages support controlled failure typically called exceptions . These program failures are from a logical point of view in that the program and or machine did not actually fail they are simply a means of handling unexpected events.

In this exemplary embodiment all statements in YATL including function calls and rule applications can fail. Failure is caused either by an explicit fail statement or through a failing primitive e.g. match once . Failures can be trapped through the try catch either or and else constructs. Table 14 shows an exemplary code excerpt illustrating catching failures.

In this exemplary embodiment failures are also propagated until they are caught. The following exemplary code excerpt in Table 15 shows how failure is propagated outwards through nested scopes and also across applied rules.

However the loop primitives while and for will not fail because the semantics are to loop while the condition exists irrespective of the state of the action as shown in Table 16.

For clarity the keyword continue in the exemplary embodiment of YATL can be used to continue execution without action. This primitive should not be confused with the C continue primitive which breaks the current execution path and moves to the next iteration of the loop.

Because YATL data is realized as ATerm trees in this exemplary embodiment constructs that provide tree traversals and manipulation of subtrees are useful.

Source code transformation languages need the ability to match upon elements of programs i.e. trees by traversed repetitive testing. In this exemplary embodiment of YATL tree equality can be tested through the eq operator or through the using match operators. Integer trees can also be tested with the simple conditional operator . Tables 17 and 18 illustrate different variations on the same semantics for traversal constructs.

In this exemplary embodiment the match primitive is designed to be used with super types. It assumes a match against the current term unless the using construct is used to explicitly specify the subject of comparison.

This exemplary embodiment of YATL also provides a number of basic traversal primitives as shown in Table 17. These traversals fulfill most of the transformation program needs. In line with the semantics of this exemplary embodiment of YATL s basic looping constructs continual traversal e.g. foreach match will not fail while once traversals e.g. match once will fail if a match is unsuccessful.

Other embodiments include more complex traversals but these basic traversals are sufficient for many transformation applications.

In this exemplary embodiment of YATL the underlying trees are manipulated by YATL meta programs. The underlying trees are inherently complicated due to the complexity of the target language grammar e.g. C C and the augmentation of the basic AST with literal and layout information e.g. commenting white space . YATL super types provide the abstraction over this detail. Super types are orthogonal to the core YATL language and implemented as a plug in compiler personality in this exemplary embodiment.

Each super type supports parameters that are used to define concrete values that must hold for a match to succeed. The parameters as also used to make copies into variables and to bind pointers to elements of the matched tree. The basic syntax for super type matching is shown in Table 19 and an example is shown in Table 20.

In Table 20 the example matching super type will match on all calls to a function named foo with exactly one parameter that is a decimal literal zero. The generated Stratego matching strategy which is congruent is given in table 21.

The generated Stratego is less intuitive for a user of imperative languages to understand. Furthermore this exemplary embodiment of YATL is able to abstract upon the complexity of the hybrid AST that contains augmented layout information. The generated Stratego code must specify actions for all nodes in the subject tree.   is effectively a matching wildcard on the layout nodes.

YATL variables can be used to define concrete values for super types in this exemplary embodiment. Furthermore subtrees of a given match can be bound to YATL variables or marked with a YATL pointer. The exemplary code excerpt in Table 22 de references the variable f as a concrete value for the function name while making a copy of the parameter subtree into variable p and setting a pointer q to the same subtree in the original tree.

This exemplary embodiment of YATL also provides support for basic loops and branching. In all of these primitives the associated compound statement must be encapsulated with and no potential for dangling else . Table 23 summarizes the loop and branching constructs in this exemplary embodiment of YATL.

As well as performing identification of program elements transformations typically replace existing code with new code in this exemplary embodiment. This requires the ability to construct new program elements. This exemplary embodiment of YATL supports program construction through build super types. There are two classes of build super types concrete and free text. Concrete super types use a predefined free template together with a number of concrete values literal or variable to form the respective tree. The syntax is the same as that when super types are used for matching.

Build super types are used with the new construct. This is the basic primitive for creating new trees. For example the following excerpt in Table 24 illustrates the construction of a function call using the FunctionCall super type.

Concrete super types are useful for building smaller elements of code but become cumbersome when constructing larger program fragments. Free text super types provide a mechanism for building such elements in this exemplary embodiment of YATL. Free text super types allow the YATL programmer to use an excerpt of code i.e. by example to construct a new program tree. Free text super types can also be embedded with YATL variables that will be later interpolated. There are three free text super types for this exemplary embodiment of YATL FreeStatement FreeExpression and FreeCompound. The program excerpt passed to these super types must conform to the target language grammar for a statement expression and compound statement respectively. Table 25 illustrates with the following code excerpt.

When free text super types are used with multi line programs the left hand margin is marked with a colon. This is used as the reference point for intelligent indentation performed by the system during the insertion process as shown in Table 26.

This exemplary embodiment of YATL provides a number of constructs for adding and removing subtrees i.e. program elements in the target code. Deletion and insertion is done with reference at before or after to a previously established pointer. The following exemplary code excerpt in Table 27 illustrates the use of statement insertion and deletion.

In this exemplary embodiment of YATL the insert statement and delete statement primitives depend upon the given pointers marking a valid statement as opposed to a subtree within a statement which was a common mistake for developers learning YATL. If the pointer parameter cannot be located at the appropriate level of subtree then the insertion deletion will be successful and furthermore no failure will occur.

However replacement by assignment has to be done carefully to ensure that the new tree is the same form as the tree being replaced in this exemplary embodiment. If not a malformed tree will result. Malformed trees may appear to be correct from the built output but they may nevertheless cause problems through misinterpretation in a later stage of transformation.

In this exemplary embodiment of YATL replacement through explicit assignment is often desirable because replacement through explicit assignment allows modification with respect to the current tree as opposed to a pointer reference. YATL also supports a primitive called replace with that allows a single statement as the current tree to be replaced by one or more new statements. Table 30 shows an example.

The replace with construct is implemented through a technique known as term mutation. The basic idea is that a single term is temporarily replaced by another single term of the form Mutant I where I is a list of new terms that will ultimately replace the Mutant term. The replacement is actually performed when the outer context is made available to the transformation engine.

This exemplary embodiment of YATL includes a run time. The YATL run time provides auxiliary support for transformations. This includes logic specific to the target language e.g. scoping rules symbol tables as well as access to the underlying operating system services e.g. file I O .

In this exemplary embodiment the YATL programmer may need to implement part of a transformation directly in the underlying Stratego language in some cases. This is facilitated through native constructs. Single statements are defined with the native keyword while complete rules and functions are defined by encapsulating the native code in and . Table 31 is an exemplary code excerpt illustrating native constructs.

In this exemplary embodiment native functions can also be used to call C implemented functions via the Stratego prim construct. This provides great flexibility in implementing custom functionality. Table 32 illustrates using native functions to call C implemented functions.

In this exemplary embodiment native Stratego can also be used to directly implement custom super types. The Native super type takes a single string parameter that defines the Stratego code for the strategy executed during each iteration of the traversal. Table 33 illustrates custom super types.

In this exemplary embodiment it is possible to bind YATL variables and pointers to subtrees using the Native super type. To do so appropriate calls to add yatl symbol are made so that the variables are added to YATL s rule function symbol table.

In this exemplary embodiment there is a library support that provides access to the underlying operating system. The YATL run time leverages existing Stratego system libraries in addition to some custom built libraries that are written in C. Other embodiments include other and different libraries. The suite of libraries in this exemplary embodiment includes support for file I O console I O network I O date time program execution e.g. exec basic string handling e.g. strcmp and data structure handling e.g. list table . Table 34 illustrates the loading of a YATL list from a file and then printing out each element to the console.

A symbol table is a data structure used to record identifiers used in the source program and collect information about various attributes of each. From the perspective of a program transformation system the symbol table effectively provides a cached representation of information that can be directly derived from the source tree.

In this exemplary embodiment the target symbol table i.e. hldig symbols from the target language as opposed to YATL variables is implemented as a Stratego hash table. Other embodiments implement the symbol table differently. A key element of the symbol table for C and C is the scope to which each symbol belongs. In this exemplary embodiment each new scope in the complete AST is associated with a unique scope identifier. Other embodiments may be modified according to various other language characteristics.

In this exemplary embodiment access to the target symbol table is provided through a number of APIs that allow table lookups and synchronized modifications between table and tree. The basic symbol lookup functions are symbol lookup xxx where xxx is one of the suffixes such as those listed in Table 35.

In this exemplary embodiment each of the above APIs takes a scope identifier pair and returns a scope declaration pair except typedecl deep which takes an additional start scope. The C and C scoping rules are used to perform a series of symbol lookups until a result is found. If a given identifier is not found even in the global scope then the lookup API fails. Table 36 illustrates a symbol lookup function.

In this exemplary embodiment the symbol table can also be used as a reference for identifier rewriting. The rewrite APIs are implemented as rules. Other embodiments implement them differently. Each takes a scope identifier pair and a rule that is applied to the associated declaration. Modifications on the declaration are synchronized between both the symbol table and the corresponding subtree. Table 35 illustrates the use of the symbol rewrite API.

It is quite common for the symbol table to become out of synchronization with the transformed ATerm tree. To re synchronize the rule RebuildSymbols can be applied to a given subtree. This rule flushes the existing symbols re annotates the tree with new scope identifiers and populates the symbol table with new symbols for the respective tree.

An example transformation rewrites code so that it conforms to a Hungarian like variable naming convention. This convention derives a prefix from the variable type that is prepended to the variable name. Thus given a variable name the data type is inherently deducible.

In this example a YATL function GetHungarianPrefix was implemented that generated a Hungarian prefix from a given type specification as shown in Table 38. This program sequentially matched on the type which was passed as a parameter using an either or construct. Of course a table could have been used to store the mappings but this is a simple example. Note that in matching the type specifications the LooseTypeSpec super type was used. The LooseTypeSpec super type ignores declaration sequencing and the inclusion of any type qualifiers e.g. static const .

Given the main prefix generation function the basic algorithm is defined in Table 39. This algorithm was kept simple for brevity. A practical tool would likely be more comprehensive.

In this example variable declarations were matched through the VarDecl super type. Using this a YATL variable pointer was bound to the declared type and the list of variable identifiers. In order to modify the variable identifiers in place without reconstructing the rest of the declaration a pointer was used as shown in Table 40. Otherwise a copy would have been modified without effect.

Given the type from the declaration the type was resolved through possible type definitions by using the symbol lookup typedecl deep call. See line 21 of Table 38. This API used the symbol table to fully resolve the type from the given scope because types are scoped. If this call failed then there was no further resolution of the type and therefore the type was treated as a basic type assuming that all types were available. Storing was also done at the pointer level. For example given type T defined as typedef unsigned long T the type is unsigned long and the pointer level is 1. This pointer level was later added to the level associated with the individual declaration. See line 37 of Table 38 .

The next stage was to build the Hungarian prefix from the fully resolved type using the GetHungarianPrefix function. Iteration through each of the declarators in the declaration list was done and then the identifier was assembled and replaced. Part of the assembly included adding the letter p to the prefix for each pointer level. See lines 43 45 of Table 38 . The name replacement was performed by matching on the Id term and then using explicit assignment on the current term. The complete main rule is shown in Table 41.

All of the constructs in this exemplary embodiment of YATL operate on a given input tree known as the current subject. For convenience a tree can be thought of as a fragment of program source code. The constructs may or may not modify the subject but in any case another tree results.

This exemplary embodiment of YATL is typeless that is variables do not have a type. Variables are identified by the prefix followed by an identifier. All variables are locally scoped to the rule and like PERL variables do not need to be explicitly declared. Variables are initialized when they are first assigned.

In this exemplary embodiment variables can be re bound at any time and represent a copy of whatever they have been bound to. They are bound through the assignment operator either within super type matching or an explicit assignment statement. Table 42 illustrates variable assignment.

This exemplary embodiment of YATL has one special variable  .   Refers to the current tree e.g. program segment .

In this exemplary embodiment global variables are scope across rules. A global variable is declared by simply prepending the variable identifier with the double colon symbol. Table 43 illustrates a global variable. Global variables are not released until the transformation program exists.

In this exemplary embodiment variables make copies of the program they are bound to. Marker variables allow transformations by reference. They behave in a manner akin to conventional pointers. Marker variables are denoted with an asterisk. Table 44 illustrates marker variables.

Markers are either unique or replicated indicated with . Unique markers are changed each time the marker is assigned. Markers are referenced using the on construct. The on construct applied to a unique marker results in a single application while the on construct applied to a replicated marker repeats for each of the occurrences of the marker.

In this exemplary embodiment one data type is the string. Any LL AST or subtree can be converted to a string. Stringification is achieved by the concatenation of all strings within the tree from left to right. Table 45 illustrates strings.

In this exemplary embodiment one or more data items e.g. trees strings integers can be combined into a single tree using bracketing. This is particularly useful in building return values for functions. Unification equates to building a term given a number of siblings. Table 46 illustrates data unification.

In this exemplary embodiment unified data can be split using a specialized form of assignment. Table 47 illustrates split assignments of the form list of variables term expression . Split assignments may include the current term variable  . Note that the leftmost use of the   in the last example in Table 47 is bound to the current term.

This exemplary embodiment of YATL supports modularization of functionality into subroutines. In YATL there are two types of subroutines rules and functions.

In this exemplary embodiment rules form the basic unit of transformation on the current subject that is they cause effect on the current subject. Rules are identified by a unique identifier and optionally support parameters except the main rule that does not have parameters. The rule identified by main is the entry point from the transformation execution and must exist in every YATL program. Parameters that are specified on rule main map to command line arguments for the tool. Arguments are supported with default or without a value prefix noarg . The order of the parameters declared does not matter. The values of the parameter variables scope to function main are coudn to the command line values as a string or the value 1 where there is no argument. They are used in the same way as any other YATL variables. Table 48 illustrates rules.

In this exemplary embodiment rules other than the main rule are called using the apply expression. The result of the apply expression changes the current tree to that which results from the particular rule. Table 49 illustrates applying rules when the apply command is within a foreach match loop. Using the apply operator in the context apply R1 R2 means apply rule R2 if and only if R1 succeeds. If a rule is applied without explicitly handling its failure the whole transformation may stop. The else clause is used to catch exceptions and continue.

In this exemplary embodiment functions differ from rules in that functions do not pass an inherent program tree and on calling functions do not effect the current program tree. Rules are in fact syntactic sugar over functions. Functions are defined with the sub keyword and called as illustrated in Table 50.

In this exemplary embodiment of YATL all statements can succeed i.e. a tree is returned or fail if failure is not explicitly handled by an else clause the program stops. Table 51 illustrates handling failure with an else clause.

In this exemplary embodiment the continue construct continues the program but is useful when an explicit else action is not desired. Table 52 illustrates the continue construct.

In this exemplary embodiment statement blocks including function calls can be checked for failure through the try clause. The try construct executes the try block and if the block fails then executes the catch block.

In this exemplary embodiment isolate is used to protect the current tree from being affected allowing temporary modifications. The isolate construct is used for a single statement or a complete block. Table 53 illustrates the isolate construct.

In this exemplary embodiment simple conditional flow is supported through an if statement. Full statement parentheses are used to avoid the dangling else problem. Table 54 illustrates the if else statement.

In this exemplary embodiment the either or statement is used to execute a number of statement blocks until one succeeds. At least one alternative is provided. Table 55 illustrates the either or statement.

In this exemplary embodiment while loops are a basic pre test looping command. The loop action is applied to the current subject and the expression is isolated. Table 56 illustrates the while statement.

In this exemplary embodiment the do while statement is a variation on the while statement for the post test looping. Table 57 illustrates the do while statement.

In this exemplary embodiment the for statement provides syntactic sugar for while loops with initialization test and increment. The for statement s action causes effect on the current tree. Unlike C the condition is required in the for statement. Table 58 illustrates the for statement.

In this exemplary embodiment the fail statement explicitly causes a match or function call to fail. Table 60 illustrates explicit failure.

In this exemplary embodiment foreach match is the principal construct for recursively searching with the current subject. This construct matches on a given tree built using a super type within the current subject. The semantics of the call are for each matching tree in the current subject tree perform the following action on that matching tree. The traversal used for this match is top down. Table 61 illustrates searching the current subject and for each matching function call to the function atol applying the rule R2. R2 replaces the call with mynew atol transposing the parameters also. Match expressions may be or ed together to avoid repetition.

In this exemplary embodiment match once is used to perform a traversal until a single match within the current subject succeeds. The action is only applied on the first match. If no match is found the else action is applied to the current subject. Table 62 illustrates the match once statement.

In this exemplary embodiment match once and match once else operate in a top down fashion while foreach match bottomup search ion a bottom up fashion so that the leaves are processed first. Table 63 illustrates foreach match bottomup.

In this exemplary embodiment the match expression facilitates an exact match. There is no inherent traversal involved. Match is typically used in conjunction with a conditional. Match conditions can also be directed on a given tree by using the using construct. Table 64 illustrates match using.

In this exemplary embodiment the developer can match against a piece of code held within a variable or explicitly specified. The parameter to match construct is a term expression that builds a tree. Table 65 illustrates exact matching without a super type.

In this exemplary embodiment the on statement applies some transformation action to a tree e.g. program segment held in a variable without affecting the current tree. Table 66 illustrates the on statement.

In this exemplary embodiment of YATL super types are one way to abstract upon the complexity of the target grammar and the LL ASTs that are produced. The super types are specific to the target language and implemented as a personality on the YATL compiler. Super types allow the YATL programmer to both search match against segments of program code and also to build new segments of code. Table 67 illustrates a super type.

In this exemplary embodiment super type parameters are standard across all super types parameters include three different optional elements criteria field identifier and attributes. The criteria define the value or variable to which the field data is bound. The field identifier qualifies the field when it cannot be implied from the parameter ordering. Attributes change search strategies and formations. Table 68 illustrates super type parameters.

In this exemplary embodiment matching super types are used by the YATL programmer to locate program segments of interest. A matching super type is like a template for a piece of code where each template is of a given form and contains a number of holes wildcards . These holes are filled in using the constructor parameters. Super type parameters are dependent upon the implementation of the respective super type constructor. Parameters are typically a mixture of YATL variables and constants. The parameters are specified as a comma separated list and their order is meaningful. When YATL variables are used in a super type constructor they are used in either reference or assignment. That is reference e.g. x . means use the contents of x whereas assignment e.g. x means that when the super type matches the matching value is assigned to variable x. Table 69 illustrates match super types.

In this exemplary embodiment of YATL a second family of super types is that of building which allows the YATL programmer to construct new fragments of code either from scratch or from existing pieces. Table 70 illustrates build super types. The FreeStatement super type build constructors allows the YATL developer to directly write a complete C C statement as part of their transformation program. The FreeExpression super type build constructor allows the YATL developer to directly write a C C expression as part of their transformation program. The FreeExpression super type is used in the same way as the FreeStatement super type.

In this exemplary embodiment a new statement is inserted with reference to a YATL marker as illustrated in Table 72. Markers used for statement insertion point to a statement or expression statement rather than a subtree of a statement.

In this exemplary embodiment it is often useful to replace a statement with a new statement without explicitly setting up marker variables. This is achieved through the replace with construct which replaces the current statement with one or more new statements as illustrated in Table 74. The replacement is not actually performed until the inner most loop is exited.

In this exemplary embodiment pointer references are used to insert layout before or after a given statement as illustrated in Table 75. Insertion after a statement prepends the given string to the layout. Insertion before a statement appends the given string to the layout.

This exemplary embodiment supports basic integer arithmetic. Arithmetic expression include multiply divide add subtract modulo division increment decrement postfix and conditional expression include 

In this exemplary embodiment the scoping constructs transform uses X where Y and transform deci X where Y allow changing the declaration of a variable based on how it is used or vice versa. In both constructs the first parameter X is the name for a YATL rule that changes uses decis. The second parameter Y is a rule that matches the uses of a variable given the name of the variable which is passed into the rule as a parameter. Table 77 illustrates scoping in the example of match use is listed below p contains the variable name and specifies that a variable that is assigned the return value of function call rn getseg.

Computer program listings pertaining to Table 77 are provided in electronic format as permitted under 37 C.F.R. 1.52 e and 1.96 c . The submitted compact disc the contents of which is herein incorporated by reference contains the following file 11222418 wordcode tables77 79.doc

This exemplary embodiment of YATL supports the ability to interface directly into Stratego. This is achieved in one of two ways using a native statement or a Stratego block. The native statement can be used to call Stratego code directly. This is useful to access more complex Stratego functionality that cannot be expressed directly in YATL. The native statement is also useful for debugging purposes. Table 78 illustrates the native statement. Complete blocks of Stratego can be inserted into the YATL code. The contents of these blocks are directly pasted in their declared position. Native blocks are encapsulated with and . The native block also allows the YATL programmer to directly interface with C code using the Stratego primitives construct. If there is no super type available for a given construct the native super type is used. This super type allows the use of Stratego match expressions directly.

Computer program listings pertaining to Table 78 are provided in electronic format as permitted under 37 C.F.R. 1.52 e and 1.96 c . The submitted compact disc the contents of which is herein incorporated by reference contains the following file 11222418 wordcode tables77 79.doc

Table 79 contains a grammar for an exemplary embodiment of the YATL language. Those skilled in the art and informed by the teachings herein will realize that the invention encompasses obvious changes in grammar and syntax and instead is directed to the broad concepts implemented by the exemplary grammar syntax and constructs.

Computer program listings pertaining to Table 79 are provided in electronic format as permitted under 37 C.F.R. 1.52 e and 1.96 c . The submitted compact disc the contents of which is herein incorporated by reference contains the following file 11222418 wordcode tables77 79.doc

The processor cooperates with conventional support circuitry such as power supplies clock circuits cache memory and the like as well as circuits that assist in executing the software routines stored in the memory . As such it is contemplated that some of the steps discussed herein as software methods may be implemented within hardware for example as circuitry that cooperates with the processor to perform various method steps. The computer also contains input output I O circuitry that forms an interface between the various functional elements communicating with the computer .

Although the computer is depicted as a general purpose computer that is programmed to perform various functions in accordance with the present invention the invention can be implemented in hardware as for example an application specific integrated circuit ASIC or field programmable gate array FPGA . As such the process steps described herein are intended to be broadly interpreted as being equivalently performed by software hardware or a combination thereof.

The present invention may be implemented as a computer program product wherein computer instructions when processed by a computer adapt the operation of the computer such that the methods and or techniques of the present invention are invoked or otherwise provided. Instructions for invoking the inventive methods may be stored in fixed or removable media and or stored within a working memory within a computing device operating according to the instructions.

An exemplary embodiment of the YATL program transformation language and some features are described. Other embodiments include additional features. YATL has many advantages. By design YATL is intuitive for programmers of procedural languages to learn and use. YATL provides powerful support for writing transformations in reference to elements of the target grammar through a compiler personality. YATL is also fully extensible providing in line access to the supporting Stratego and C back end. Of course other embodiments may be implemented differently. Already YATL has had much success in writing practical program transformations for C and C in a commercial setting. Successful transformation applications include debugging instrumentation byte ordering refactoring compiler migration and others. In these applications it has taken much less time to write YATL tools than to perform the modifications by hand as done conventionally.

