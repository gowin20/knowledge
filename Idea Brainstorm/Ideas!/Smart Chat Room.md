# Smart Chat Room

Type: tech

# What is it?

A basic chatroom like Discord. Rely on mostly just text channels, but could expand to voice channels for ASR as well if that's the vibe

**Goal:** represent the "internal data structure" that humans use to connect things together

- The chat room will attempt to parse messages sent by users into useful data!
- Uses X-Bar theory, binding theory, and our basic understanding of human syntax to parse sentences into syntax trees.
- It then stores these trees in a database, based on time and when they were said in relation to other sentences
- After that, it will do a second pass at this database and attempt to clean up the data. It will extract DPs/NPs and make a database with each DP/NP as a primary key
    - this should allow for good information indexing.
    - For example, after people talk about me,

Humans use event-based memories, so primary indexing by time / event makes sense and is easy

Uses Binding Theory and X-Bar theory to create smart informative models. Stores these models in a sequential thing where each one links to the next

Possibly:

- derive a bot from this which prints out information in chat

I'm not really interested in making a conversational AI. They're kinda stinky lol. I just want to make a program which *understands* the things we tell it

# Applications:

- Would have direct applications in AI / Machine Learning, give me a background in that
- could be used to effectively glean user data on websites (comments on cobble or the like!)