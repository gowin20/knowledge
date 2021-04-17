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