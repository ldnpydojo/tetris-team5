# London Python Dojo - Tetris

The task for tonight is to create a clone of Tetris. This page lays out some
of the decisions and tasks.

This is an aid to coordinating as a remote team.


# Game engine

You will need to decide on a 2D game framework. Some candidates are:

* [Pygame Zero](https://pygame-zero.readthedocs.io/en/stable/)
* [Wasabi2D](https://wasabi2d.readthedocs.io/en/latest/)
* [Arcade](https://arcade.academy/)
* [PursuedPyBear](https://ppb.dev/)
* [ursina](https://www.ursinaengine.org/)

I would not recommend these for this project:

* [Pygame](https://www.pygame.org/news) - you will have to write a game loop
  and event handling yourself before beginning.
* [Pyglet](https://pyglet.readthedocs.io/en/latest/) - being lower-level to
  OpenGL, this does not have a simple API for polygon/rectangle drawing, only
  sprites and text.


# Tasks

The following tasks are split up according to a "Model-View-Controller"
pattern to make it easier to visualise the dependencies between the tasks,
but this is not the only way (and may not be the best way) to write the game.


## Model

1. Describe the seven tetronimo pieces (as
   [described here](https://tetris.fandom.com/wiki/Tetromino)).
1. Generate a random piece. Show the next piece that will be generated.
1. Rotate a tetronimo. This requires a centre of rotation for each tetronimo.
   See [here for a description of this in the official games](https://strategywiki.org/wiki/Tetris/Rotation_systems).
1. Model the grid of filled cells.
1. Allow testing whether a tetronimo intersects filled cells at a given
   position.
1. Write a tetronimo into the filled cells.
1. Remove each line that is filled and collapse lines above.
1. Keep score.


## View

1. Create a game window.
1. Draw the boundary of the play area.
1. Draw the filled cells.
1. Draw the active tetronimo.
1. Draw the next tetronimo to drop.
1. Animate the removal of a line.
1. Show the score.
1. Allow drawing "game over" over the screen.


## Controller

1. At the start of the game, make the next tetronimo the active tetronimo.
1. Drop one step every *t* seconds. If the tetronimo cannot occupy the space
   below it, write it into the filled cells. Trigger an animation if a line is
   filled. Then make the next tetronimo active.
1. Add keys for left/right. These do nothing if there is no space for the
   tetronimo.
1. Add keys for rotate clockwise/anticlockwise. These do nothing if there is
   no space for the rotated tetronimo. At the walls, tetronimos may be moved
   outwards to accomodate the rotation.
1. If there is no room to introduce the active piece, show game over.
1. On the game over screen, press a key to restart.
1. Implement the "drop all the way" operation.


## Publication

1. Describe requirements in a requirements.txt
1. Write a README.


## Stretch goals

1. Animate the rotation of the pieces.
1. Animate the drop operation(s).
1. Make the game speed increase very slowly (logarithmically?)
1. Add [juice](https://youtu.be/Fy0aCDmgnxg) - screen shake, trails, particles,
   sound effects.
1. Add a title screen.
1. Publish to PyPI.
