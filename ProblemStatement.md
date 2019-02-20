# Problem Statement

The gurus John Carmack and Tim Sweeney present two different approach to the use of functional programming in game development. Using the .NET runtime both approaches can be put into practise. C# presents an incarnation of Carmack's suggested approach, while F# with minor modifations supports Sweeney's approach.

- Are these approaches viable in a game development setting? 
- What are the performance impacts of these two approaches? 
- Are experienced game developers capable of putting these two approaches to use?

## Practical setting
Implement a series of 10 or so benchmarks in C# and F# in Unity, measure the speeds of the implementations.

Find 4-7 experienced game developers, have them develop 5 out of 10 of the benchmarks in each language, such that each benchmark is only implemented once by each developer.

**Performance:** Compare the performance of the developers' solutions with our's.

**Usability:** Examince the frustrations and confusion of the developers and any possible errors in their code relative to those of the other language.

## Time schedule
Feburary 22nd: All PR material is done, i.e. poster has been made, printed and hanged and mails have been sent to game companies in Aalborg.

March 1st: Report introduction and problem statement done.

March 15th: F# and C# benchmarks are formulated and implemented.

March 15th to April 1st: Write cheetsheats and find relevant material for use in benchmarks.

April 1st: All test subjects have been selected.

Mid April: Execute tests.

Rest of April and May:
- Look at the results from the test
- Cognitive Dimensions?
- Performance studies
  - Our implementation of benchmarks: F# vs. C#
  - Test subjects' implementations vs. ours

June: Report finalization and corrections. 

# Usability Evaluation Planning:

## What are we testing?
- Functional-style C#: 
    - Task-based list mapping
- Functional Reactive Programming in F#
    - Create event handlers that carry out game logic
- Lenient evaluation strategy (F#)
    - Does game developers know how to write F#?

## Participant requirements:
Primary criteria:
- Unity experience
- C# experience
- Game programmer
- Relation to game industry (ranked):
    1) Employed at a game studio
    2) Industry experience, i.e. have published a game
    3) Medialogy students

Optional, but nice:
- Functional Programming/F# experience
 
 ## Test Cases
Magnetic objects: A list of objects, some of them magnetic. All magnetic objects should be attracted to a common center-point with a given magnetic factor. *(We should probably provide the formula to find center-point of 3D vectors)*

Move towards: Given an object and a destination, rotate the object towards the object and move it forward.

Jump: Have a characted jump by applying upwards force to his rigidbody.