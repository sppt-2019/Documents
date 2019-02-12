# Game Engine Architecture
This document gives a summary of the book [Game Engine Architecture](https://aub-primo.hosted.exlibrisgroup.com:443/desktop:Samlet:AUB01_ALEPH002011881) by Jason Gregory.

## Chapter 1: Introduction
This chapter introduces the art of game programming. It first discusses the different competances a game developer must possess and how a typical game studio is organized. Afterwards it discusses what a game is, underlining that video games can be classified as soft realtime system, and tries to draw the line between the game and the game engine. The most important take is that truly genre-agnostics game engines cannot exist and thus game studios will often want to make changes to existing multi-genre engine (Unity, Unreal etc) and states that a data-driven architecture is what differentiates game engines from game software. 

The next two sections first presents an overview of different genres and how they relate to different game engines, followed by a survey of popular game engines. Section 1.6 presents a game engine architecture consisting of multiple layers, underlining that calls between layers are only accepted from upper layers and downwards, i.e. the architecture is acyclic. This architecture is followed by a brief description of each layer.

The final section of the chapter discusses asset creation tools and the asset conditioning pipeline. The asset conditioning pipeline is responsible for importing 3D models, audio etc and storing them in an asset database for use in the game. The asset conditioning pipelines may also include a world editor.

## Chapter 2: Tools of the trade
This chapter covers important tools used in game development and game engine development. It starts with an overview of version control systems. 

It continues with a discussion of different C/C++ compilers and gives a rather detailed description on how to configure Visual Studio to game engine development in C++. The author suggests using three compile configurations, debug, development and ship. Debug compiles without optimization and all debug information, development compiles with optimization and all debug information and ship compiles for release with all optimizations and no debug information. The section also discusses how to use Visual Studio's debugger with instruction- and memory breakpoints.

The two next sections covers profiling tools, underlining that these are of utmost importance in game engine development. The section suggests both performance and memory profilers.

The last section presents a list of other tools that may also be handy during game engine development, such as diff and merge tools, along with hex editors.

## Chapter 3: Fundamentals of Software Engineering for Games
This chapter presents an overview of object-oriented programming with a root in C++. As this stuff should be quite familiar to both of us, I will only highlight the topics that stood out to me when I read the chapter.

**Multiple Inheritance**: C++ allows multiple inheritance. The chapter states that it should primary be used with mix-in classes, which are simple classes that have no parent, as this allows additional functionality to be introduced at arbitrary points in the inheritance tree.

**Resource Allocation is Initialization (RAII)**: Design pattern that treats resource allocation as classes. In this pattern a local instance of a *Janitor*-class is allocated before allocating a resource. When the local instance drops out of scope the class's destructor is called, which deallocates the resource. This could be used for dynamic memory management with the `AllocJanitor` class:
```C++ 
class AllocJanitor { 
    public: explicit AllocJanitor(mem::Context context) { 
        mem:: PushAllocator (context);
    } 
    ~AllocJanitor() { 
        mem:: PopAllocator (); 
        }
    };
```
And in use:
```C++
void f() { 
    // do some work...
    
    // allocate temp buffers from single-frame allocator 
    { 
        AllocJanitor janitor (mem::Context::kSingleFrame);
        U8* pByteBuffer = new U8[SIZE];
        float* pFloatBuffer = new float[SIZE];
        
        // use buffers...
        
        // (NOTE: no need to free the memory because we used a single-frame allocator) 
    } 
    // janitor pops allocator when it drops out of scope // do more work...
}
```

**Error handling**: The author advices against using logging functionality to raise awareness on "creative" assets, such as meshes, as they are far too easy to miss. He instead suggests painting a big red box in the world whenever the mesh should have rendered. He argues that a game engine must be robust to programmatic errors, as developer-time is too valuable.

**Assertions:** The author states that assertions are the key to writing good code, as they cause bugs to manifest quicker. He states that the C assertion library may be used, but also provides an implementation of a finer-grained assertion library, that is more suited for game development:
```C++
#if ASSERTIONS_ENABLED
// define some inline assembly that causes a break
// into the debugger -- this will be different on each
// target CPU
#define debugBreak () asm { int 3 } 
// check the expression and fail if it is false 
#define ASSERT (expr) \
    if (expr) { } \
    else \
    { \
        reportAssertionFailure (#expr, \ __FILE__,  __LINE__); \
        debugBreak ();\
    }
#else 
#define ASSERT (expr) // evaluates to nothing 
#endif
```
