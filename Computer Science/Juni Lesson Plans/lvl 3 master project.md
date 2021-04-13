# lvl 3 master project

Created: Jun 19, 2020 12:58 PM
Status: Complete
Type: Python 3

### Student: George Gu

## Session 1

- [x]  Introduce Master Project
- [x]  Concept Review
- [x]  Show him resources
- [x]  HOMEWORK: Pick a research question / topic, try to find a database

## Session 2

- [x]  Review: Research Question / Topic
- [x]  Find a database - did he find one already?
- [x]  Learn more about the topic
    - [x]  What statistics will we need to calculate?
    - [x]  How can these statistics answer your research question?
    - [x]  Once you've figured that out, figure out how graphs and visual representations can communicate that / help us understand
        - [x]  Ideas on graphs right now?
- [x]  Brainstorm several ideas, topics
- [ ]  Work on Master Project
- Research Info:
    - Words!
    - **Question:** What properties do the most common words in English share?
    - wordsapi, other resources
- [x]  HOMEWORK: Ingest dataset on frequently used words, plan roadmap for projects

## Session 3

- switched to Meriam Webster's Dictionary API

## Session 4

- Make a request, collect the data that you want in a nice-looking data structure / dictionary
- add that data to the master dictionary, in this format: "word":data
- write that dictionary to a file using JSON4
- JSON file - basically just a dictionary in a file format
    - json.dump(dictionary,outfile)

## Session 5

- Start seaborn analysis
- Make sure all the data stuff is okay
- read from json file, make 3 graphs
    - Bar graph of word frequency
    - bar graph showing how many words of each syllable count
    - 

# George's Process:

1. Get a list of commonly used words from a website
2. process that list so you can use it in code
3. for each word in the list, make a request for another website which tells us extra stuff
4. take all that extra information, and store it in a special file
5. use the information stored in that file to make the 3 graphs you see