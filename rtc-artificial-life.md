<permalink>rtc-artificial-life</permalink>
<month>5</month>
<year>2015</year>

# Collaborative artificial life

I have always been fascinated with artificial life and decided to make a cellular automaton, one of the most known artificial life models out there.

In case you don’t know what a cellular automaton is, allow me to explain what it is with a very simple example.

A cellular automaton is a form of artificial life that creates structures that “act like if they were alive”. Imagine a chess board, but instead of having several different chess pieces this time you only have 1 type which we will call a living cell. If there is a living cell on the board that cell is considered to be alive, if there is not living cell then that square is considered to be dead.

Fortunately these two states are can be easily represented on a computer by using the binary system, so that the equivalence ends up being 1 for a living cell and 0 for a dead cell.

Now image that you throw 5 living cells on the 8 x 8 board that end up in the following pattern:

[image]

This is called to be the generation 0, to compute the next generation we will follow these 4 rules:

1.- Any living cell with fewer than two live neighbors dies, as if caused by under-population.
2.- Any living cell with two or three live neighbors lives on to the next generation.
3.- Any living cell with more than three live neighbors dies, as if by overcrowding.
4.- Any dead cell with exactly three living neighbors becomes a living cell, as if by reproduction.

So that the next generation will look like this:

[image]

And consequent generations will actually make the pattern move away from where it started and will eventually die until it reaches the border of the chessboard.

[animation]

This last example is on of several structures that create different results. You can try it on a real chessboard or a piece of paper, or you could simply use my project [here].

And that’s it! With some really simple rules you end up having an living ecosystem (well and artificially living one).

This is how the projects looks like:

[]

Click on the image to load the board and play with it creating some structures, bear in mind that the app is real-time collaborative, every user is actually seeing the same board and changing the same board, I made it this way to see how it evolves with time, I plan to run leave this project running for a looong time...