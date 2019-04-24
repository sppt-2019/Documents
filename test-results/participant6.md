# Participant 6
## IDE: Visual Studio
---

### F# Task 1: Dialogue
* 01:54 Monitor clarifies the assignments (__hint__)
* 02:50 Participant would parse the node list as a small language and use a function to acquire the correct output (__interesting__)
* 05:16 Participant explains an example functions from the sample sheet
* 06:36 Boolean vs assignment operator confusion (__relevant__)
* 08:39 Clarification of provided data structure
* 10:40 Monitor suggests looking at the documentation for a solution of the specific problem (__hint__)
* 11:35 `Node` does not have a default constructor
* 12:30 Attempted to modify the `Node` class, but could not due to it being implemented in C#
* 13:53 Defined a recursive data structure to hold the calculated tree
* 16:10 Monitor suggests using an empty list as a place holder
* 16:50 assignment 1 complete
* 18:00 Participant wants to iterate over the dialogue list to find a node, Monitor suggests using `List.Itter` (__hint__)
* 20:01 Participant confuses unit type with monads
* 20:43 Monitor clarifies that function arguments are space separated
* 21:38 Participant partitions the code into more functions (__relevant__)
* 22:35 Monitor points that `let` expressions must come before `member` expressions (__relevant__)
* 24:31 Participant realises that they don't want to iterate over all list elements
* 24:33 Monitor suggests using `List.Find` instead
* 25:16 Participant identifies and correctly explains predicate functions
* 25:42 F# indexing causes confusion `var[i]` vs `var.[i]` (__relevant__)
* 27:13 Variable declaration is clarified
* 27:42 Participant identifies problem in predicate function and rectifies
* 28:44 Participant muses over how to traverse the tree
* 29:20 Build a tree consisting of the root node and the first child
* 30:20 Monitor explains that functions implicitly returns the last line of a function (__relevant__)
* 31:15 Monitor explains how to deconstruct C# tuples
* 32:57 Deconstruction of C# tuples is not permitted and this is an error in the test setup
* 35:45 Participant muses over using recursion or map over a nodes children
* 37:24 Switches to a binary tree strategy
* 39:42 Monitor suggests using `None`

### C# Task 1: Currency
* 42:29 First strategy is a bottom-up approach
* 43:23 Monitor asks about the result of a certain expression and participant explains
* 46:54 First attempt did yield the correct values
* 47:49 Trail and error approach
* 48:32 First level of conversion works
* 51:09 assignment 1 complete
* 52:26 _Nu copi/paster jeg kode, det er ikke godt, men det er spiludvikling_
* 53:29 Monitor points out a flaw in the participants approach
* 55:07 _Det er grim kode, det er faktisk rigtig grim kode._
* 56:09 Participant finds a flaw in their approach and asks monitor for a hint (__hint__)
* 57:47 Monitor affirms that an expression is valid (__hint__)
* 59:10 Monitor hints to a possible solution and participant figures out a solution (__hint__)
* 61:20 assignment 2 complete

### FRP
* F# likes functional
  * It might be problematic to use in games
  * Needs more time to try and play around
  * Not a lot of game programming, more programming-programming in this task
* Tasks are quite close to actual games (__relevant__)
* F#
  * Pro
    * Some things are just easier in functional programming i.e. trees
    * List handling is better in functional
  * Con
    * Object instantiation is harder in F#
