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

- **Magnetic objects:** A list of objects, some of them magnetic. All magnetic objects should be attracted to a common center-point with a given magnetic factor. *(We should probably provide the formula to find center-point of 3D vectors)*
- **RTS State Machine:** Create an *upside-down* state machine that holds references to the objects in the current state. The state machine should invoke its behaviour on each element in the state on every frame. This could be an archer AI, that can:
    - Move to a position in the world
    - Shoot at an object in the world
    - Flee when enemies are too close
- **FPS Controller:** Create a FPS controller that moves a character forwards on W, backwards on S, left on D and right on A. The controller should look around when the mouse is moved.
- **3rd Person Controller:** Create a 3rd person controller that moves a character forwards on W, backwards on S, left on D and right on A. The camera should rotate around the character when the mouse is moved.
- **Talent Tree Walker:** Given a tree of talens or perks, create a tree walker that can traverse the tree and reduce all effects of perks into a single object. Effects could include:
    - Strength
    - Intellect
    - Agility
- **Dialog Tree:** Build a dialog tree for a conversation. The nodes of the tree should hold things said by the NPC and edges hold things the player says. The leaves of the tree holds consequences of the dialog, which could be:
    - NPC turns hostile
    - NPC becomes your companion
    - The NPC gives you an item
- **Armour Graph:** Create an armour system for a RPG. In this system groups of items give perks to one-another. Example: Helm, chest plate and amulet is an item group. The player equips an amulet, which gives +10% stats to all items in group. The stat bonus of the helm and chest plate should increase by 10%.
- **Resource Splitting and Merging:** Create a resource system where several minor resources may be combined into larger resources and later split, if needed. Create a system that, given a collection of items, combines them into the largest possible resource type.