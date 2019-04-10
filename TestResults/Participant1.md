# Participant 1
## IDE: Visual Studio
---

#### F# Task 1: First Person Controller
* 02:17 Opened wrong IDE
* 03:57 Explicitly defined the velocity variable's type, wasn't sure if it was necessary (it was)
* 04:30 Progressed to assignment 2
* 05:35 Informed about FRP and told to implement task using FRP instead of with `update`
* 07:03 Notices that `update` can be reacted to, thus circumventing the FRP system
* 08:22 First idea written as comment
* 09:17 Participant asked to explain code examples, correctly explains FRP reaction, but misses lambda expression handler
* 12:10 Indentation was incorrect, but it was fixed
* 12:32 F# is compiled with F6
* 14:30 Compilation failed even though code was correct. __Test code did not compile__
* 15:10 Code compiled correctly
* 16:08 Participant reacted correctly to `update` event
* 16:55 Implemented own `update` method
* 17:23 Next version participant wants to react to inputs directly via `ReactTo<>`
* 18:34 Events where "Unity standard"
* 20:03 `this` must be used explicitly
* 21:30 Looking at code examples and wraps lambda expression in parenteses
* 22:30 Attempting to use Unity's get component method
* 23:03 Reminded that `this` must be explicit
* 24:20 Issue with mutability, can't increment and cannot create new Vector
* 25:08 Participant forgot a comma
* 25:40 Velocity variable has wrong type, __strong typing is a barrier__
* 26:52 Function had the wrong return type
* 27:27 Confusion about assignment operator `<-` vs declaration/equality operator `=`
* 29:40 _Getting used to not writing semicolons and curly braces is going to be difficult_
* 31:35 Participants wants to react to any key, but wants to know which key is pressed
* 32:20 Shown the move-axis `FRPEvent`
* 34:02 `GetAxis` explained
* 36:55 `ReactTo` explained to participant
* 37:22 Understood predicate, but pointed out that values needed
* 37:49 Told that having multiple predicates meant that `ReactTo` only reacted sometimes (when _both_ predicates where true)
* 41:54 Reminded to use indents instead of curly brackets
* 43:35 Adding a jump event
* 44:30 Add new Vector as force instead of as new position
* 47:43 Task complete

#### C# Task 1: Third Person Controller
* 50:34 Declare variables can be edited in the editor
* 51:04 Solution using `GetKeyDown` in `update`
* 51:30 Using `RigidBody` to apply force
* 51:59 Using `update` to check input and apply force accordingly
* 53:04 Could have used force on `RigidBody` in F#
* 54:30 Terrain eats too many resources
* 54:46 Gravity was disabled
* 55:00 Assignment 1 complete
* 55:12 Work on mouse movement
* 56:34 Get current mouse position and an original mouse position, calculate delta every frame
* 57:37 Reminded of which axises to rotate around
* 59:12 _I have never really implemented game controllers before_
* 1:01:20 Controller rotates around itself
* 1:03:10 When mouse delta is zero the angle becomes zero and the method doesn't add rotation, but sets it
* 1:04:40 It _is_ an incremental angle, just not enough
* 1:05:45 Not sure how to proceed
* 1:10:17 Mouse move works

#### FRP
* Can see the idea behind it
* More readable code
* Forces much more readable code (and modular)
* F# syntax was problematic
* Prefers strictly typed (_F# is strictly typed_, but inferred)
* Would not use it for production
  * Too used to C#
  * F#
    * What about implicit parallelisation
  * Likes FRP
