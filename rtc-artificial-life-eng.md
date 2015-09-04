<permalink>rtc-artificial-life-eng</permalink>
<month>5</month>
<year>2015</year>

# Collaborative artificial life

I have always been fascinated with artificial life and decided to make my own real-time collaborative cellular automaton in [Node.js](https://nodejs.org/). More specifically I wanted to bring the magic of real-time collaboration to the Conway's Game of Life so that every single user that loads the game will be <a class='mintip'>interacting with the same board<span><img src='articles/images/alife-final-animated.gif'/></span></a>.

The Game of Life was created by [the British mathematician John Horton Conway](https://en.wikipedia.org/wiki/John_Horton_Conway). In an attempt to find an "self-replicating machine" Conway drastically simplified the an earlier <a class='mintip'>automaton by John von Neumann<span><img src='articles/images/neumann-automaton.gif'/></span></a> which contained several complex rules. The Conway's model appeared on the page 120 of the <a class='mintip'>1970's issue of the Scientific American<span><img src='articles/images/sa-1970.jpg'/></span></a> and made him instantly famous.

Most of the cellular automatons have very simple rules, here is a simple example of these mathematical models work:

Let's say we have a chessboard grid and a bunch of pawns which we will call a *living cells* from now on. If there is a *living cell* on the board that grid square is considered to be alive, if there is not living cell then that square is considered to be dead. These two states are can be easily represented on a computer by using the binary system, so that the equivalence ends up being **1 for a living cell** and **0 for a dead cell**.

Now image that you throw 5 living pawns on the 8x8 board and you end up in the following pattern:

![](articles/images/chessboard-gen0.PNG)

This is called the generation 0, to compute the next generation we will follow these 4 rules:

<br/>

**1.- Any living cell with fewer than two live neighbors dies, as if caused by under-population.**

**2.- Any living cell with two or three live neighbors lives on to the next generation.**

**3.- Any living cell with more than three live neighbors dies, as if by overcrowding.**

**4.- Any dead cell with exactly three living neighbors becomes a living cell, as if by reproduction.**

<br/>

By applying these simple rules we end up with the next generation which looks like this:

![](articles/images/chessboard-gen1.PNG)

And then,

![](articles/images/chessboard-gen2.PNG)


And so on, if you keep iterating you will notice that <a class='mintip'>successive generations will make the pattern move away<span><img src='articles/images/glider-animation.gif'/></span></a> from where it started. This pattern will eventually perish when it reaches the border of the chessboard.

There are <a class='mintip'>several<span><img src='articles/images/gl-example0.gif'/></span></a>, <a class='mintip'>many<span><img src='articles/images/gl-example1.gif'/></span></a>, <a class='mintip'>many<span><img src='articles/images/gl-example2.gif'/></span></a> <a class='mintip'>structures<span><img src='articles/images/gl-example3.gif'/></span></a> that create different results. You can try them on a real chessboard, a piece of paper, or you could use my simulator at [alife.adelriosantiago.com](http://alife.adelriosantiago.com).

That’s it! With some really simple rules you end up having an living ecosystem (or an artificially living ecosystem to be precise).

This is how the finished project looks like:

<a href='http://alife.adelriosantiago.com'>![](articles/images/alife-final.PNG)</a>

Click on the image to load the simulator and play with it creating some structures, don't forget to set your nickname! As stated previously, note that **the app is real-time collaborative**, every user is actually seeing and interacting with the same board, I made it this way to see how it evolves with time, I plan to leave running this project running for a looong time...