# Poker Program Outline

![[Poker Program Outline/Untitled.png]]

First, I will make a poker program which can simply run poker. I'm using object oriented programming in Python

- Card class containing:
    - [x]  Card Value
    - [x]  Card Color
- List of cards - deck
    - [x]  Contains every card exactly once, for 52 total cards
    - [x]  cards are "dealt" from copies of this deck for each hand.
- Player classes:
    - [x]  Can be assigned hands of cards
    - [x]  A "human" player which is prompted for input
- Master list containing all of the players in the turn order
    - [x]  Dictates who goes when
    - [x]  Changes can be made to the list (remove & append) to get the proper rotation from hand to hand
    - [ ]  Blinds and other stuff is determined this way as well
- Bet function and a working economy
    - [ ]  you bet values of money
    - [ ]  money is subtracted
    - [ ]  you can't bet if you don't have enough money
- Side pot functionality
    - [ ]  if someone goes all in, the maximum amount they can win is the amount they bet multiplied by the number of players that match their bet
- Poker logic
    - Master dictionary containing all possible hands along with their associated rankings
        - [x]  Used to check for relative hand value.
    - Function which calculates hand value
        - Smaller level functions which check for individual hands
            - [x]  Function which checks for:
                - [x]  Pairs
                - [x]  Trips
                - [x]  Quads
                - [x]  Then counts the number of each, and determines if you have anything like 2 pair or a full house. Returns null if no hand, hand name otherwise
            - [x]  Function which checks for straights
            - [x]  Function which checks for flushes
    - Function which returns the name of the hand you have
        - [ ]  Used for printing
        - [ ]  Includes specifics of the hand
    - Function which compares 2 hands to determine a winner
        - [x]  Simple comparison of relative hand value
        - [ ]  IF relative value is the same, the players have the same hand. Winner is thus determined by card value
            - [ ]  Extra IF statements to check winner
            - [ ]  IF exact tie, return "die"
    - Tournament loop which takes in the list of all players, and returns a the winning player by comparing the individuals' hands
- [x]  Game class containing EVERYTHING!
- Hand class containing information about the current hand
    - [x]  number of rounds (usually 4)
    - [x]  each entry has an associated number of cards dealt
    - [x]  a counter dis
- Round class containing information about the current round
    - [x]  A number of cards dealt
    - [x]  Deals cards first
    - [x]  Betting round next
    - [x]  Uses a copy of the player order list
        - [x]  While the list is still around, keep going
        - [x]  When someone bets, it appends the people who have already gone in the list to the end
- Statistics output
    - [ ]  each ROUND object is saved and written to a file as JSON data
    - [ ]  format: each ROUND has all of its member variables stored, then the hands used in the round associated with them

    ```python
    game_info = {"Boards":[boards],"P1":[hands],"P2":[hands],...}
    ```

    the ORDER of the lists is what determines hand number. Designed to be used with data libraries such as Pandas and Numpy in Python for easy data analysis. Probably also useful for R.

- POKER TEXT GRAPHICS
    - [x]  print out a cool ASCII art of poker for the title screen
- ASCII POKER BOARD
    - [x]  ASCII art for all of the cards in poker, found here: [https://www.asciiart.eu/miscellaneous/playing-cards](https://www.asciiart.eu/miscellaneous/playing-cards)
    - [x]  BOARD PRINTING FUNCTION in the game object
    - [x]  Hand printing function as well
    - [x]  print_board will be very complex and may require its own object, the "board"
    - Combine_hand_strings function
        - Read through string literals one by one, with a "level" variable
        - when a newline is detected (should happen on both the exact same time, because of card format), skip the newline, move level up one, and add a newline when that happens
- Pygame graphics?
    - [ ]  EXTENSION: Expand the program to use Pygame for an actual GUI, with images of the cards and everything. This is another project on its own!

![[Poker Program Outline/Untitled 1.png]]