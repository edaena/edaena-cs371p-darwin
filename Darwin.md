# Darwin's World #

---


The World of Darwin consists of a two dimensional grid. In this world, Creatures can lurk and do different actions in order to survive.


To Simulate Darwin's World, we established several Classes:
  * Instruction
  * Species
  * Creature
  * Board
### Class diagram ###
![http://dl.dropbox.com/u/1158059/Darwin.jpg](http://dl.dropbox.com/u/1158059/Darwin.jpg)


## Species ##

---

A Species contains a _program_ or a set of _instructions_. These instructions can be shared within different Creatures. When this occurs it is said that Creatures are of the _same_ _species_.

#### Infecting ####
A creature is vulnerable to be infected by another creature. When this occurs an infected creature becomes part of the species of the creature that infected it.

##### Example #####
Suppose you have a creature of the hover species, this creature becomes infected with a creature of the rover species, this will convert the first creature into a creature of the rover species.


## Instruction ##

---

In Darwin there are two types of instructions:
  1. Action: as the name implies, these instructions cause the Creature to take an action
  1. Control: these type of instructions affect the flow of control of the species program

### Action instructions ###
There are several action instructions:
| **Instruction name** | **Description** |
|:---------------------|:----------------|
| HOP | move forward if the space is empty |
| LEFT | turn to face left |
| RIGHT | turn to face right |
| INFECT | if there is an enemy Creature in front, infect it |

Each species is characterized by the set of actions it does. Each creature tries to survive in the World of Darwin by doing some of these actions.


### Control instructions ###
There are several control instructions:
| **Instruction name** | **Description** |
|:---------------------|:----------------|
| IF\_EMPTY n | if the space ahead is empty, go to line n, otherwise, go to the next line |
| IF\_WALL n | if the space ahead is a wall, go to line n, otherwise, go to the next line  |
| IF\_RANDOM n | randomly choose between going to line n or the next line |
| IF\_ENEMY n | if the space ahead contains a creature of a different species, go to line n, otherwise, go to the next line |
| GO n | go to line n |

This are core structures that help define what actions a creature would take depending on the conditions in Darwin's World.

##### Example Creature program #####
| **#** | **instruction** |
|:------|:----------------|
| 0 | if\_wall 3 |
| 1 | hop |
| 2 | go 0 |
| 3 | left |
| 4 | go 0 |

## Creature ##

---

The Creature class is designed to encapsulate the data relevant to a Creature.
A creature has a unique identifier, a Species pointer, Board pointer, and knows what direction it is facing.

##### Methods #####
This class contains a static method for comparing the species of two different Creature objects to determine whether or not they are enemies.
If two creatures are enemies, the Creature class can ask the board which creature to infect, and the Creature infect method can be called to infect the other creature with this creature's species type.


## Board ##

---

The Board is Darwin's World. It contains a list of Creature objects and keeps track of their positions in a map that maps each creature location to its unique identifier.

A map can look like this:
| **creature position** | 0 | 3 |
|:----------------------|:--|:--|
| **creature id** | 8 | 4 |

This means that creature with id 8 is at position 0 and that creature with id 4 is at position 3.


## References ##

---

http://www.cs.utexas.edu/users/downing/cs371p/drupal/darwin/