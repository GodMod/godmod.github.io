---
title: Dices
sidebar: sidebar9
permalink: dices_index.html
folder: dices
---

## Introduction

This Plugins adds three dices. Each dice can be configured or enabled independently.
The random value is saved with the message, therefore a manipulation of the value is visible.

## Usage - Generic Dice
You have to specify what the dice should do. Therefore add the number of throws, seperated with `d` and the size of the dice. 
For example: `[dice]6d30[/dice]` will throw a 30-side dice 6 times.

## Usage - Dice1-Dice3
To add the random value, just click on the BBCode-Button of the dice, or enter `[dice1][/dice1]` into the message.
You can enter a number of throws as content of the BBCode (if "Number of throws" is set to 0): `[dice1]8[/dice1]`. This will generate 8 random numbers.

## Settings

### BBCodes
At the BBCode Management, you can adjust the Button Values and Icons for dice, dice1, dice2 and dice3.

### Dices 1-3
* Name - *The Name will be shown at the output of the random number*
* Lowest value - *The lowest value of the dice.*
* Highest value - *The highest value of the dice.*
* Enable dice - *This will not remove the BBCode-Button (you can do this at the BBCode-Management), but will prevent the generation of random numbers*
* Number of throws - *How many random numbers should be generated. Insert 0 to let the user choose how many throws should be done, by applying a number at the BBCode: `[dice1]8[/dice]` will generate 8 random numbers.*

### Generic Dice
* Enable dice - *This will not remove the BBCode-Button (you can do this at the BBCode-Management), but will prevent the generation of random numbers*
* Name - *The Name will be shown at the output of the random number*
* Highest value - *The highest value of the dice.*
* Maximum Number of throws - *Maximum number of generated random numbers.*

## License
[GMLv1](license.html)

{% include links.html %}
