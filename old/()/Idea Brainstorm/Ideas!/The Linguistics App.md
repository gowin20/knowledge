# The Linguistics App

Type: tech

# What is it?

This all-in-one app aims to provide a platform to linguistics students + professors to discuss linguistics and become friends.

In addition to a basic chatroom, the service will also offer several built-in tools for completing linguistics work and conducting research.

- would be a great way for me to flex my linguistic and CS knowledge

### Basic App Outline:

1. Chatroom
2. Syntax Section
    1. Sentence Parser
    2. Lexical Entry Database
3. Phonetics and Phonology Section
    1. IPA Chart and Pronunciation Guide
    2. Features resource (similar to pheatures perhaps)
4. Semantics section? I haven't taken 120C yet

### MVP:

- it might be overambitious to try and do ALL of this. lots of work
- I'll focus on completing only the chatroom, because that's what i'm most passionate about
- If i'm on a good pace (which i hopefully will be), I can then implement the syntax section, then finally the phonetics/phonology section as a stretch goal

# Chatroom

The main functionality that I care about. It's a chatroom which also serves as a testing grounds for various linguistic models

A basic chatroom like Discord. Rely on mostly just text channels, but could expand to voice channels as well if that's the vibe

**Goal:** represent the "internal data structure" that humans use to connect things together

- The chat room will attempt to parse messages sent by users into useful data!
- Uses X-Bar theory, binding theory, and our basic understanding of human syntax to parse sentences into syntax trees.
- It then stores these trees in a database, based on time and when they were said in relation to other sentences
- After that, it will do a second pass at this database and attempt to clean up the data. It will extract DPs/NPs and make a database with each DP/NP as a primary key
    - this should allow for good information indexing.
    - For example, after people talk about me,

Humans use event-based memories, so primary indexing by time / event makes sense and is easy

Uses Binding Theory and X-Bar theory to create smart informative models. Stores these models in a sequential thing where each one links to the next

## Data Visualization

- Shown as another tab on the side
- visual, graphical representation of all the data parsed fomr the chatroom

# Syntax Section

## Sentence Parser

Type in a sentence, and it will try to make it into a syntax tree

Could also have this section encode a chart with information specific to XP Phrases

## Lexical Entry Database

Definitive lexical entries for words - primarly VERBS

- part of speech
- theta criterion assigned
- what lies within its maximal projection
- include all possible definitions and entries for each word
- perhaps the actual definition of the word as well? maybe overkill

# IPA Chart and Guide

Phonetics stuff

# Feature Chart

Phonology stuff