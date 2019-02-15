# Problem Statement (Entity Component System)
<head>
<style>
.warning-box {
    background-color: yellow;
    color: black;
    border-radius: 4px;
    padding: 4px 8px;
}
.warning-box::before {
    content: "Warning!";
    display: block;
    font-weight: bold;
    font-size: 1.2em;
    text-align: center;
    margin-bottom: 4px;
    border-bottom: 1px dashed black;
}
</style>
</head>

<div class="warning-box">
This problem statement like requires a pretty extreme amount of code to be written. We therefore feel more like the second option in this document.
</div>

Modern game engines, such as Unity, are experiencing a swift from Scene Graphs to Entity Component Systems (ECSs), which promises higher parallelisability and performance. Can an ECS be implemented in the Godot Engine and how does that affect its performance?

Based on findings in previous work [P9 report] .NET Core is a highly performance managed language candidate for engine programming. This is supported by [Bent, Sestoft], that found the .NET Core scheduler highly capable of handling large sets of small tasks. Can an ECS for Godot be implemented in .NET Core and how does that affect its performance?

## Planning
1) Research Engine of choice (Godot)
2) Integrate with .NET Core
3) Construct modification
4) Verification
   
---
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

## Possible benchmarks

Magnetic objects: A list of objects, some of them magnetic. All magnetic objects should be attracted to a common center-point with a given magnetic factor. *(We should probably provide the formula to find center-point of 3D vectors)*

Move towards: Given an object and a destination, rotate the object towards the object and move it forward.

Jump: Have a characted jump by applying upwards force to his rigidbody.

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