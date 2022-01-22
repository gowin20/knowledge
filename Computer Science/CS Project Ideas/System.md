# System

# Overview

System

notetaking / structuring app which allows you to create things in an incredibly creative manner

Probably can expand to way more than just notes

Fundamentally non-typed - you can have any type of information in combination with others

- Like Google Drive, Prezi, and Evernote/Notion rolled into one.

The real trick is, since the elementary components of all of those things are the same, it's still roughly the same amount of work

- Intuitive system for creating text boxes
- By default, the space is UNBOUNDED. Looks like Scratch's IDE
- Navigable menu of blocks on the lefthand side
- Allows for embedded code and programming right there in the thing.
- Add "Terminal" blocks to show output wherever
- 
- Still supports normal "page" layout for traditional papers and stuff. Easily click a button to toggle between modes
    - Give elements of the project an ordering, which determines where they will appear when the document is transformed into page layout
    - Automatically assigns these numbers based on an algorithm about position
        - after release: do some image recognition to make an AI. Probably could use user data in order to feasibly do this
    - Still allows manual reordering. Goal: be WAY easier to use than fucking google drive's picture shit
    - Page layout allows creation of text boxes that can appear anywhere. Basically a "superset of normal documents" because it allows for a traditional lined document like Word, but also allows for creation of text boxes and such as in a powerpoint / photoshop
    - 

# Supports Code

- Supports embedded code into "code" windows, allowing for super easy sharing of ideas
- Can run code in a terminal, and create "terminal boxes" in presentations and docs
- Good for communication between teams and instantly sharing code

Supports its own block-based programming language

Functions like Minecraft Redstone! Except it actually allows for productive things

# How does it work?

The "smallest unit" or something of the like is applicable to MANY things

Everything is the same size - a "chunk"

- Code and Notes could be homogenous "chunks"? kind of like Minecraft blocks
- Really big raster, where each pixel could contain any kind of information you want it to
    - Could be made in Python for this reason

Basically, this will be a world which allows us to simulate whatever we want

However, we're not using graphics or making games or anything (well, not yet)

Everything works because the program itself operates at a very low level of abstraction. There's nothing predefined in any way, whatsoever.

Thusly, creating text boxes and other things are hardcoded "functions" of the System programming language/app itself. This means that the user is able to write blocks like this themselves, to create more text boxes and other such automated tasks. It's SO SIMPLE TO USE BECAUSE IT'S VISUALLY DRAG-AND-DROP

One layer. One layer. Both code and the objects code creates exist on the same layer, in the physical world. I feel like that would break something about reality lol

This means that code itself is instantiated as objects in the program. These objects can interact with others

All objects interact with each other in the same way. They can connect together (either linearly or in any direction) in order to make things

Basically, **I want to make a Minecraft-esque sandbox work space** that allows anyone to do pretty much anything they want.

- Optimize their productivity
- 
- Take notes in an informative and visual style
- Work collaboratively with others

### I want to create a system which allows for intuitive creation of containers!

You can kinda see what I'm talking about here in Notion. Even though this app is text-based, all lines of text are in essentially div containers

Imagine using Notion, but you can drag blocks around anywhere in order to visually represent things effectively

Additionally, you are also able to draw on the space, making intuitive notetaking even easier

I'm kinda describing OneNote here aren't I

However, this will offer functionality that OneNote does not. 

- It allows for explicit nesting of objects in order to create groupings and "functional units"
- It supports embedding and executing code
- It also supports interaction with the boxes, and groupings of functional units
- Basically, you can program your notes!
- MVP: We create blocks kinda like Scratch which interact with the notes
- Add support for as many programming languages as possible later. Talk to [Repl.it](http://repl.it) for support / funding?

Additionally, System will have a switch you can flip which allows you to toggle on and off "Page Layout." When in this mode, everything still works as normal, but the screen shifts from a boundless space to a traditional document layout. Things in the space are rearranged to fit into the document, and preferably look good. Lots of this is up to the user at first

# Use Cases

- note system
    - button to save the contents of a directory as a note
        - Create a "table of contents" note listing a link to every file in a directory
        - Filter notes by tag or ID to only list specific notes
        - add to the system!
- visual presentations
- collaborative work
- Creating projects and games