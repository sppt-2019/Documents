# Analysis of Concurrent Implementation in Unity

## Cognitive Dimensions

* __Abstraction Gradient__
  * Unity imposes a lower level of abstraction in their concurrency system
* __Closeness of Mapping__
  * Scene behaviour vs. singleton objects holding managers
  * Object properties set in the related system and not on the object itself
  * System manages attack target and _not_ the object
* __Consistency__
  * `NativeArray` requires a non-nullable value as it's type. In direct conflict with the object oriented paradigm of C#
  * `TransformAccess` does not have the same methods as `Transform`
  * `NativeArray` cannot be extended and must therefore either be resized or consigned to a fixed size
  * `NativeArray` breaks from the object oriented paradigm and behaves like a `C` style array
  * Programmer must manually clear memory, this is not the C# way
    * Exceptions messages could be clearer
    * Programmer has to comment out code to find the source of exceptions, is a clear sign of poor error messages
  * Object cannot be instantiated outside of the main thread. This conflicts with object oriented thinking and arguably parallel thinking
  * `UnityEngine.Random.Range` can only be called from the main thread
* __Diffuseness/Terseness__
  * In place element manipulation of `NativeArray`s requires multiple statements to increment/decrement elements
* __Error-proneness__
  * Poor documentation leads to more errors
  * Job Scheduling
  * Ideal code structure is not obvious
* __Hard Mental Operations__
  * `TransformAccess` does not have the same methods as `Transform`, which means the programmer is forced to manually calculate vectors
  * Scheduling requires the programmer to manually determine dependencies
  * Job management: attack cool-down. What is the job and what is the system responsible for?
  * Memory management
    * Keeping track of allocated memory
    * Clearing the memory at the correct time
* __Premature Commitment__
  * Use of singleton. It is not obvious whether this is a good idea or simply enforced by Unity
  * Poor documentation means that the programmer needs to guess what to do
* __Progressive Evaluation__
  * Errors caused by Editor
    * Persistent memory between distinct presses of the play button
      * i.e. exceptions carry over to next run
    * Requires restart of Unity
  * Editor crashes multiple times
* __Role-expressiveness__
  * Some of the constructs are not named in accordance with naming conventions of C#, e.g. `NativeContainer` should be called `NativeCollection`
  * System is a bit vague
* __Secondary Notation and Escape from Formalism__
* __Viscosity__
  * Change in one of the three interconnected systems, requires changes in all three
* __Visibility and Juxtaposability__
  * A schedule graph or similar may have helped
* __Notes__
  * Poor documentation
  * `EulerAngle` &rightarrow; `Quarternion`



## Attention Investment
* __Cost__
  * Lower abstraction (closer to machine)
  * Scheduling
  * Division of work
  * Additional management systems
* __Investment__
  * Schedule understanding
  * Object restructuring
* __Pay-off__
  * Increased performance
  * Greater resource utilisation
* __Risk__
  * No pay-off
  * Error introduction
    * Deadlocks
    * Race conditions
  * Failed implementation
