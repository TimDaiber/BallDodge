# BallDodge
DodgeBall is a game I have written using html,css and javascript.
The basic concept of the game is that the user moves his ball around and
tries to dodge the balls on the screen.

## Requirements
An up to date browser like chrome.

## Goal of the Game
The goal of the game is to survive and dodge the balls for as long as possible

## How to play
The user plays the game by using the arrow keys on the keyboard.
Ever arrow key moves into the direction it is supposed to.

## Features
* Balls will spawn at certain times at certain positions of the canvas.
* None player ball collision is made done in a way that the player can not prepare for easily.
* 
 It is not a bug unless the two balls get stuck in each other. It is wanted behaviour.
* Timer as score system.
* At certain times radius's of balls change.

## How to make the game better
* Certain features could be added like: 
* Changing the acceleration of the balls at a certain time (Speed)
* Changing the color of the balls at certain time
* Making a ball invisible for a certain time (0.5 seconds) 
* Addidng a function that will only allow a player to stay in one spot for a certain time (i.e. 5 seconds)

The code could be cleaned up by using an array of ball objects.
This would also enable spawning an unlimited number of balls.
Using arrays would also clean up some collision functions. 
(I mean making one collision function that would work with all the balls in the 
ball array).

###Bugs
Known Bugs:
* ~~Balls get stuck to canvas at the start of the game.~~
    (Fixed)
* ~~Balls getting stuck to each other at the start of the game.~~
    (Fixed)
* ~~Still able to move character after game over.~~(Fixed)
    (Only happens if you die while a arrow key is pressed.)
* Balls getting stuck in canvas when resize methods are called.
* Balls getting stuck in each other when resize methods are called.

How to fix the last 2 bugs is create functions that move the ball on either x or y axis by 20 pixels 
on the x or y axis. This function would activate if a ball does not move position from either the x or y axis 
for 5 seconds.

###Resources
* Collision
https://developer.mozilla.org/en-US/docs/Games/Techniques/2D_collision_detection
* Collision
http://jsfiddle.net/gQ3hD/2/
* Naming error
http://stackoverflow.com/questions/33510442/collision-detection-between-balls-javascript
* Ball array
http://jsfiddle.net/hustlerinc/7Lmmx/
* Colour
http://www.rapidtables.com/web/color/Yellow_Color.htm
* Key codes
http://www.cambiaresearch.com/articles/15/javascript-char-codes-key-codes
* Elsapsed time counter
http://jsfiddle.net/cckSj/5/

And lab resources.

