# Participant 5
## IDE: Visual Studio
---

<!-- Types+ ReactTo++ Types-- -->

### F# Task 1: Magnetism
* 02:20 Clarification of sequential/parallel vs synchronous/asynchronous
* 03:50 Participants first strategy would be to create a class and attach it to all objects
* 04:30 Get magnetic objects and calculate the center. Minor clarification of center of balls' position instead of center of plane. (__hint__)
* 06:33 Spots `Type` and deduces that it is equivalent to classes
* Identifies and understands that FRP behaviour is similar to mono behaviour
* 7:50 Participant asks what `member` and `this` means
* 09:03 Realises that there are no end statements (`;`) or block delimiters (`{ }`) (__relevant__)
* 10:35 Participant looks up loops and if statements
* 11:30 Clarification of `[1..3]` (__hint__)
* 14:22 Participant attempted to get the minimum floating point number
* 15:15 Uses infinite and negative infinite instead of float min and max
* 16:28 Clarification of indexing in F# (`var.[i]` instead of `var[i]`) (__hint__)
* 18:28 Boolean operator used by accident instead of assignment operator
* 19:00 Participant did not declare his variables as `mutable` and therefore encountered errors
* 20:56 Type inference confused the participant for a moment and he assumed the language was dynamically typed (__relevant__)
* 23:25 First compilation attempt succeed
* 23:49 Index out of bounds error
* 24:54 Calculated the wrong center point (center of x and y, instead of x and z)
* 25:53 Center was calculated
* 26:29 In order to move the balls towards the center the participant would move the balls in the `update` method
* 27:01 Participant identifies that `ReactTo` can react to an `update` event
* 28:14 Participant correctly describes the behaviour of the predicate and the handler in the `ReactTo` function
* 29:37 Participant creates a new function
* 32:25 Encountered some type problems with the array type, monitor clarified that `[]` denoted the array type (__hint__)
* 33:30 Participant accidentally created a tuple by assuming comma separation between function arguments (__relevant__)
* 33:47 _Så man kan gøre sådan her? I like it!_
* 35:22 Participant will move the balls by iterating over them and moving them towards the calculated center
* 36:23 Monitor hints that a variable could be a serialisable field (__hint__)
* 40:26 Participant reasons over how to gradually move the balls towards the center
* 42:59 A misspelling, which had caused confusion and errors, was corrected
* 43:33 Balls moved towards center correctly, but the center was not correctly calculated

### C# Task 1: AI + Currency
* 46:08 Monitor explains inverse statemachine
* 46:26 Participant explains that the shooters could be put in a list and iterated over
* 48:47 Clarification of the task (__hint__)
* 49:31 Clarification of shooters (__hint__)
* 50:26 First solution uses update to handle shooters, in order to compute their state each frame
* 51:04 Participant opts for a loop iterating over all shooters
* 53:42 First assignment complete
* 54:58 Participant is familiar with asynchronous tools in C# and uses those added in .NET 4.0 (tasks?)
* 56:12 Participant asked for clarification of _how_ to parallelise the state management of the shooters
* Monitor clarifies the `Task.Run` method
* Monitor suggests using `Tasks.WhenAll` as synchronisation
* Task complete
* 74:11 Switch to Currency
* 82:02 assignment complete

### FRP
* F# was difficult
  * Main issues where habitual
    * Significant habitual changes required
  * Structure was good
  * IDE support was good
  * Immutable is an advantage
    * As a memory concern
    * As well as readability
* FRP and Reactive
  * Like it
  * Points out that FRP is largely syntactic sugar
* Events are used very often by the participant, and thus maybe also FRP
  * Binding behaviour to events is a _very_ good ide in game development
  * It ensures proper structure
    * And thus readability and comprehensibility
* F# makes sense for developers that are used to F#
  * Including python developers and mathematicians
* C# is more popular, which makes the language a better choice
  * Documentation purposes
  * Industry practice and convention
* F#'s type system remains a bit muddled
* If F# had a performance penalty
  * It still depends on the developers
  * Productivity is more important then performance
    * __Performance is provided by the engine, not the game__
    * However there is a lower threshold
