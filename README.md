Chess Bash
==========
A simple chess game written in a bash script.

Screenshot
----------
Running in GNOME-Terminal on Ubuntu 14.04 with default configuration - just increased font size.
![ChessBa.sh in action](screenshot.png?raw=true)

Features
--------
  * Pure Bash script
  * Chess engine / computer enemy (and even computer versus computer)
  * Unicode support (nice figures to represent the pieces)
  * Colored output (using ANSI Codes)
  * Network support (aka Multiplayer)
  * Permanent transposition tables (import/export)
  * Keyboard cursor and mouse support
  * Partial redraw (by cursor movements)
  * "Graphical" configuration (dialog utils)

*Hey, this is just a fast scrawled script, what do you expect?*


Usage
-----
No installation or configuration required, of course.
Just make it executable ( `chmod +x chessba.sh` ) and start the script by typing (obviously):

    ./chessba.sh

This will start a player versus computer game.

Additional modes and settings are available; to list them just take a look at

    ./chessba.sh -h

**Controls:** Simply input the coordinates (the columns are denoted by the letters [a]-[h] and the rows are denoted by the numbers [1]-[8]) from the piece you want to move, afterwards the target coordinates (in the same format).


Rules
-----
For simplicity, there are some cutbacks on the implemented [chess rules](http://en.wikipedia.org/wiki/Rules_of_chess) (yet).
Besides the basic movement of pieces only the pawn promotion is considered - with the limitation that pawns automatically become queens. So castle and en passant moves are not yet implemented.

At the moment no special regard is taken to check/checkmate - the game ends, when one loses his king.

These limitations are at the moment mainly based on the lack of an easy incorporation with the input, but might be solved in future releases.


Tips and Tricks
---------------
  * Invalid piece selections/moves are discarded with an warning message. If you've chosen the wrong piece at the input, just re-enter the same coordinates and now you can select another piece.
  * For a better gaming experience (= bigger and nicer pieces), use [Ubunto Mono](http://font.ubuntu.com/#charset-mono-regular) or [Droid Sans Mono](http://www.droidfonts.com/info/droid-sans-mono-fonts/).
  * If you start a multiplayer game, the first player (with the script parameter `-b "remote"`) should run the game script first, because he acts as server.


But why Bash??? (Notes from original author)
---------------
In a normal case, nobody will ask for the motivation - but in this special case it seems necessary to explain it:

Well, I started playing chess again because my girlfriend wanted to learn the game - and I rediscovered some notes about game theory.

Therefore writing a own chess game is obvious - like millions of developer did before :)

In fact it seems that chess is the most popular game for computer scientists:
In my youth all news reported about IBM Deep Blue [playing against Kasparov](http://en.wikipedia.org/wiki/Deep_Blue_versus_Garry_Kasparov) - and defeating him. Since this time super computers are known to be invincible (at least in chess), and the continuous increase in calculating capacity makes it not a real challenge anymore (to be fair, we currently also profit from techniques developed in previous time with strongly limited memory and cpu).

Hence, many hackers decided to bring up a new challenge: Writing the smallest chess game. And they were incredible successful:
[1023 bytes Javascript](http://js1k.com/2010-first/demo/750),
[1009 bytes C source](http://nanochess.org/chess3.html)
or even [487 bytes assembler](
http://www.pouet.net/prod.php?which=64962) for complete games including engine!

Putting all together, we have both really good engines easily defeating grandmasters and damn tiny chess games - so what easy opportunities are left, not solved by generations of great programmers?

Yes, writing chess in inappropriate languages - in my case **Bash**, because when I began writing the script I was on a ferry without Internet access having only a plain Ubuntu on the notebook.
And if you are crazy enough to look at the code: The main part was written there travelling on a rainy day on the sea (I had a few hours), therefore don't expect a clean organized script!


Internals
---------
**Algorithm:**
While I first started with a classic [Minimax](http://en.wikipedia.org/wiki/Minimax) it was gradually enhanced, the current version uses [Negamax with Alpha/Beta pruning and transposition table](http://en.wikipedia.org/wiki/Negamax#NegaMax_with_Alpha_Beta_Pruning_and_Transposition_Tables).

**Functions** are mostly avoided (in the engine) for performance concerns. But in the case they are still required, I use global variables and the exit status code for interaction - this might explain several design decisions.

Of course, **builtin** solutions are preferred where available (as every script should do).


Contribute
----------
If you have an idea, for example how to speed up the code (without using another language!), just let me know!

But always remember: This is just a recent fun project emerged by a few boring hours.
