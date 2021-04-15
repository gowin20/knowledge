# Discord Bot

[https://realpython.com/how-to-make-a-discord-bot-python/](https://realpython.com/how-to-make-a-discord-bot-python/)

[https://top.gg/bot/461791942779338762](https://top.gg/bot/461791942779338762)

A discord bot which is built to offer functionality for the Sbeve discord server. It serves several various functions, outlined here.

## RNG Bot

$$-flip$$

- returns heads or tails. It's 50/50!

$$-roll\ \ n$$

- returns the result of rolling an n-sided die

$$-randhand \ \ n$$

- will play out a randomized poker hand with "n" players to determine who wins. Mini version of the actual thing without DMing anyone
    - Sends the board in 3 messages: flop, turn, river, then shows each respective person's hand
- other RNG stuff? we can literally do anything we want

# Poker Bot

A bot which allows people to play poker on our server

When you type **!game**, the bot will begin a game of poker. It starts by creating an empty lobby.

Players can join the game by typing **!play**. The game will begin when someone who is in the game types **!start**.

The bot starts a hand by DMing each player in the game a message containing their cards.

Here is the outline of the actual poker engine:

[[Poker Program Outline]]

This next doc contains my plan for migrating the poker engine to an actual discord bot, and building in functionality for discord interactions and graphics:

[[Bot Extension outline]]

- !game
- !play
- !playing
- !
- !rig
- TODO: figure out all the commands

# Image Bot

When specific commands are typed in chat, the bot will send a related photo. This can start out as a simple algorithm but has great potential for expansion

- -brad will send a random photo of someone from brad's / a group pic
- -sbeve will send some random thing related to the server
- -nice will send a picture of mike or something else nice
- 

## Images from Reddit

- -boobs will send a random photo of boobs, randomly chosen from subreddits

This bot does NOT have music functionality, at least not currently. Other bots out there provide music services better than I could at the moment.