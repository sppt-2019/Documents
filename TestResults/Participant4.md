# Participant 4
## IDE: Visual Studio
---

### F# Task 1: Dialogue -> FPS Controller
* 04:25 Participant is given a hint about how to make class equivalents in F# (__hint__)
* 06:10 Difference between functions and methods is clarified (__hint__)
* 07:50 Participant has not used tree structures before outside of theoretic education (__RELEVANT__)
* 09:20 Participant is given a hint about how to populate a tree based on a list (__hint__)
* 11:30 Recursion is also not a theme the participant is familiar with (__RELEVANT__)
* 12:20 Switch to FPS controller task
* 13:05 The participant has implemented movement controllers before
* 15:07 Indentation causes minor issues
* 15:24 Participant comments on mutable variables and correctly understands their purpose
* 16:35 Indentation as block structure is not a favourite of the participant
* 17:42 Compilation successful on first try (of compilation)
* 18:10 Monitor hinted about `ReactTo<>` and FRP
* 18:45 Participant is asked to explain `ReactTo<>` and is largely correct. He mistakes events for key events.
* 19:20 The participant is not familiar with lambda expressions (__RELEVANT__)
* 21:06 Monitor explains lambda expressions (__hint__)
* 22:10 Participant comments that mouse move becomes input axis, which might not be the best option in all cases (__Unity Knowledge__)
* 25:02 Method and function declarations are looked up, and additional hints are offered by the Monitor based on experience from previous tests
* Indentation causes a bit of confusion again, but participant realises that indentation occurs whenever curly braces would have occurred in C#
* 27:08 Participant's strategy is to handle movement events and calculate a `Vector3` and apply it at the end
* 28:13 ___Det er svært med så mange parenteser, det ligner en hel mase banananer.___
* 29:32 Assignment operator is looked up
* 31:10 First solution did not work
* 31:19 Monitor points out that the calculated `Vector3` is never applied to the `RigidBody`
* 32:20 Participant is a little confused over lambda expressions with and without parameters `fun () -> printfn 'Hello World'` and `fun str -> printfn str`
* 34:34 Participant added semicolons by habit
* 34:58 Confusion about the return type of the function
* 35:28 Previous error based on misuse of `=` instead of `<-`
* 36:09 Forward movement works, solution listens to key down event instead of axis event
* 38:41 Participant points out that rotating the camera will _not_ rotate the player character
* 39:21 Handle movement using `ReactTo` as next strategy
* 39:55 Participant expresses minor confusion over tuples
* 40:16 Monitor hints about the mouse movement example (__hint__)
* 41:13 Participant points out that mouse move has ambiguous values, either new position, delta position or direction vectors. It uses direction vectors.
* 43:52 Indentation causes minor issues again
* 44:56 Monitor hints that a function body may not end with a `let` (__hint__)
* 47:01 Monitor asked about an erroneous function and participant explains, thus finding his error
* 48:59 Assignment completed

### C# Task 1: Third Person Controller
* 56:30 Jumping works first attempt
* 58:16 The rotation direction of the camera is discussed
* 59:58 Participant muses over how to apply rotation value after figuring how to calculate said value
* 60:44 Participant uses get axis method from Unity to acquire direction vectors of the mouse movement
* 63:08 Camera can yaw
* 64:38 Participant gets the camera's transform and uses it for pitch
* 66:05 Monitor gives a hint about the use of `RotateAround` (__hint__)
* 66:50 Camera can pitch
* 68:26 Monitor suggests scaling the forward direction (__hint__)
* 70:15 Strafing is supported, however jumping has stopped working

### FRP
* F# was very difficult
  * Even with a performance increase F# would not be used
  * Most games will likely not need the performance gain
  * Might be more useful for a game development studio, but not for indie developers
  * Developers do not think about resource consumption, most devices can handle it
  * The main motivation for using a tool is it's ease of use
    * Productivity is king
* Uses unity and C# every day and has not used the tools of the functional paradigme
* Cannot speak about whether it would be easier for a beginner
* Participant would never switch to F#
  * C# is so familiar, that syntax errors are not a problem
  * Therefore learning a new language means a lot of inefficiency
* FRP makes a lot of sense, at least the event based approach
* A pro/con of F# is that it will likely produce fewer problems, but that can also be a problem because the scope and specification of game must be well understood
