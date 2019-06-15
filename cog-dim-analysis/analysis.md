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
* __Diffuseness/Terseness__
* __Error-proneness__
  * Poor documentation leads to more errors
  * Job Scheduling
* __Hard Mental Operations__
  * `TransformAccess` does not have the same methods as `Transform`, which means the programmer is forced to manually calculate vectors
  * Scheduling requires the programmer to manually determine dependencies
  * Job management: attack cool-down. What is the job and what is the system responsible for?
* __Premature Commitment__
  * Use of singleton. It is not obvious whether this is a good idea or simply enforced by Unity
  * Poor documentation means that the programmer needs to guess what to do
* __Progressive Evaluation__
* __Role-expressiveness__
  * Some of the constructs are not named in accordance with naming conventions of C#, e.g. `NativeContainer` should be called `NativeCollection`
* __Secondary Notation and Escape from Formalism__
* __Viscosity__
* __Visibility and Juxtaposability__
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
