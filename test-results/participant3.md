# Participant 3
## IDE: Visual Studio
---

<!-- List+ List_ List-- Types-- Modularity+ -->

### F# Task 1: Armour Graph
* 01:49 Participant pointed out that the example code given was C#
* 03:18 Participant begins
* 03:33 First strategy: using `sum`
* 04:59 Issue "selecting" correct items
* 05:37 Switched to a reduce strategy
* 06:23 Issue attempting to open `Item` class
* 09:30 Reduce returns same type as elements of list, therefore items must be mapped first
* 11:03 Arrays and lists are not the same
* 13:00 Participant points out that the function can be reused (__Modularity!__)
* 15:32 Figuring out function definitions
* 16:06 F# function parameters explained to participant (__hint__)
* 17:33 `let` must be over `member`
* 17:50 Issue with passing the property to acquire to a function
* 21:08 Monitor pointed out that a newly defined function wasn't called (__hint__)
* 24:50 Participant declared a function solving the problem
* 25:20 assignment 1 complete
* 31:35 Error in test setup (__hint/error correction__)

### C# Task 1: Talent Tree
* 56:11 Participants first strategy is using LINQ to recurse over the tree
* 56:40 Switched to using a function to recurse over the talent tree
* 57:36 _I am much more used to working with lists_
* 58:22 Participant asked how to append/concatenate arrays
* 58:48 Monitor suggested using `array.ToList()` so that list functions could be applied
* 59:52 Participant next strategy is to flatten the tree into a single list
* 62:55 Monitor gave hint for the participants recursive function (__hint__)

### FRP
* Exciting
* It is a lot to solve a problem _and_ learn the language. In addition to a new paradigme
* Data orientation is _nice_, but it requires a little more learning
* F#'s syntax is very readable, LINQ is better
  * This is both a syntax thing and order of operations
  * SQL-like syntax is easer to read
* Difficult to say whether F# could be useful
  * The ideas behind it are nice
  * Current overhead is too great
* The guide is not very clear on the very basics of F#
  * Such as functions within functions
  * Currying example includes symbols that have not been explained
  * Give example functions obvious names such `functionName` to clarify identifiers and important keywords
