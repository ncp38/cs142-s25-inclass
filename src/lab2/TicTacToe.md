# Tic Tac Toe

Team members (edit these):
1. Team member 1
2. Team member 2

## Before you begin...

   Make sure to write down your name and your teammate's name at the top of this file and at the top of your Java code!
   When you're working on this project, if you start running into syntax problems or issues with your Java file, first, 
   talk to me!  If you're unable to debug a problem in your Java code as you're completing the lab, do your best to solve
   the problem, but submit your Java file with your attempt included.
   
   Also, make *sure* that you submit both your files and that both have your answers recorded!!

## Goals

By the time you are done with this activity, you should be able to:
* decompose a program into static methods with Javadoc comments.
* use multidimensional arrays.
* instantiate objects and call instance methods on them.
* work with your team more effectively.

## Playing the game

Run `TicTacToe.java` to play the game. This is a two-player game, so you should play against your partner.
You should play two or three times before going on to the first section.

## Part A: Representing the game board on the canvas

* A tic-tac-toe board has three rows and three columns.  But how big is the
    canvas the program uses (width by height, in pixels)?

__Your answer here__

* Look at the `draw()` function.  What do the four `drawLine()` calls do?

__Your answer here__

* What does the nested for loop do?  What is the purpose of the `centerX` and 
`centerY` variables and why are they calculated the way they are (on lines 20
and 21)?  In particular, why does `centerX` use `col` and `centerY` use `row`?

__Your answer here__

* Go to the `handleMouseClick()` function.  Notice the variables 
`mouseX`, and `mouseY`.  Add a `println()` statement to print out these
variables after they are defined.  Now play the game again.

What do these variables represent in the game?

__Your answer here__

* Now look at the variable definitions for `row` and `col` in the same 
function.  Add in code to print them out as well.  Play the game again.

What do these variables represent in the game?

__Your answer here__

* Drawing on your work for the previous questions, explain in a few
sentences how the game uses math/geometry to simultaneously store the state of the
game in a 3x3 board and also display it on a 300x300 canvas.  How are the
(row, col) coordinates on a 3x3 board converted back and forth to/from
(x, y) coordinates on the canvas?

__Your answer here__

### End of Part A: Do you feel like you understand the material so far?  If not, stop and check in!

## Part B: Static methods and Javadoc comments

* Find the `main` method.  This method has a few calls to the `draw()`
method.  Hover over one of them, and you'll get a pop-up tooltip. 
Where (in this program) did the descriptive text in the tooltip come from?

__Your answer here__

* Does editing that text change what appears in the tooltip?

__Your answer here__

* Does the tooltip still use that text if the comment starts with `/*` instead
   of `/**`?

__Your answer here__

* What causes the loop below to end?  You may need to look inside the
`gameOver()` method.

```
while (!gameOver(board)) {
  handleMouseClick(canvas, board, currentPlayer);
  currentPlayer = opposite(currentPlayer);
  draw(canvas, board);
}
```

__Your answer here__

* How does the behavior of the game change if you comment out the line that
begins `currentPlayer = opposite...` 
Note that you can comment out the line by adding `//` to the beginning of the
line.

__Your answer here__

* Copy the line of code that you just commented out and paste it into the
program at the end of the `handleMouseClick()` method (after the while
loop ends).  So this line of code should be still commented out in `main()`
but now should happen at the end of `handleMouseClick()` instead.

Does this restore the game's behavior to how it is supposed to be?  Why
or why not?

__Your answer here__

### Restore the game to a working state if you need to.  Ctrl + z or command + z (the Windows and Mac undo shortcuts, respectively) may be helpful for this, depending on what system you're programming on.
**Remove the line you added to `handleMouseClick()` and 
uncomment it in `main()`.**

* Do you feel like you understand how this program works at a high level?

__Your answer here__

* Do you feel like you understand the details of `draw()`, `gameOver()`,
and `handleMouseClick()`?  If not, raise your hand and let's talk about any parts you're not sure about!

__Your answer here__

### End of Part B: You just learned about how a mouse click function in a graphics-based game works!!  That's pretty awesome.

## Part C: Multidimensional arrays

* After the line in the `main` method

```
char[][] board = new char[3][3];
```

what is the value of `board.length`? Guess and then use
a `println` statement to see if you are correct.

__Your answer here__

* What is the value of `board[0].length`? Does this change if the two numbers
    on the line in the previous question are different? You can change the values
    and run the code to see what happens.

__Your answer here__

* What does the nested loop below accomplish?

```
for (int row = 0; row < board.length; row++) {
     for (int col = 0; col < board[row].length; col++) {
          board[row][col] = ' ';
     }
}
```

__Your answer here__

The `winner` method contains four sections labeled A, B, C, and D.
Let's look at section A.  Note that this section has a pair of 
nested for loops.  The outer loop loops over the rows, while the
inner loop loops over the columns.

Add three print statements to this section of code to help you understand
the `allMatch` variable.  Put a print statement that prints "allMatch set to true"
immediately after the line of code `boolean allMatch = true;`.  Put another
print statement that prints "allMatch set to false" immediately after the
line `allMatch = false;`.  Put a third print statement immediately *before*
the line `return board[row][0];` that prints "Win detected!"

Now play the game a few times, and watch the print
statements being printed.

* What kind of wins does Section A detect?

__Your answer here__

* When the *inner* for loop finishes, if the `allMatch` variable is true, what do we
know is true? In other words, what is the meaning of this variable at this point in time?

__Your answer here__

* Why do we change `allMatch` to true at the top of the outer loop?  Would the program
work if we set it to true *before* the outer loop started?  Why or why not?

__Your answer here__

* Why do we change `allMatch` to false inside the if statement in the inner for loop?

__Your answer here__

* Why does the inner for loop have a `break` after `allMatch` is set to false?
Would the program still work without this break?  Why or why not?

__Your answer here__

* Explain the statement `return board[row][0]`.  What does this do?

__Your answer here__

* Go on to section B.  It's almost the same as section A.  What kind of wins
does section B detect?  Feel free to add the same print statements as you did
to section A if you want.  (When done, you can remove all the print statements
that you added to sections A and B.)

__Your answer here__

* What kinds of wins do Sections C and D detect?

__Your answer here__

* Why do C and D only use one loop each (not nested loops)?

__Your answer here__

* Why does section C use `board[row][row]`?  What does this accomplish?

__Your answer here__

* Why does section D use a regular for loop that counts up (row++)
while simultaneously having a separate col variable that counts down (col--).  
What does this accomplish?

__Your answer here__

### End of Part C: Check in if you have any questions!

## Part D: Colors

* Notice how in `draw()`, the code always uses `Color.RED` and `Color.BLUE`
for the two players.  In this section we will make the game use
randomly-generated colors instead.

In the `main()` function, create two new Color objects after the call to
`canvas.show()`.  To create the objects, use the three-argument color
constructor with the values (0, 255, 0) for the first color (green), 
and whatever numbers you want for the second (but don't get distracted
finding pretty colors!)

Now edit your `draw()` function to take two additional parameters, that
will be the colors for the circles for the "X" player and the "O" player.
Modify the code in `draw()` to draw the circles using the colors specified
by these parameter variables, rather than just Color.RED and Color.BLUE.

Now edit `main()` so that green is used for the "X" player and your second
color is used for "O".  Do this by modifying the call to `draw()` in 
`main()`.

Does your game now display circles with green and your second color?

__Your answer here__

* Now we will modify `main()` to pick the colors randomly.  In `main()`,
write code to generate six random numbers between 0-255.  Use these
as arguments to the two Color constructors, replacing the numbers you 
had there before.

## Final check

Once you have finished the lab, make sure to submit your files to Canvas!  **Both** partners are required to submit the completed assignment!

Each week, you need to submit **your programming files** (which will just be TicTacToe.java this week) and your **text file** (this file, with your answers filled in).   Make sure that your .java file has a header comment on it with **your teams' names**.  Your text file also needs to have the names of both team members at the top.

After you submit your files to Canvas, I strongly encourage you to go back and double-check:
- That you have submitted both the programming files and the text file.
- That both files have your changes and latest updates in them.
- That the programming file has a header with team names and honor code and that the text file has team names as well.

It is your responsibility to submit these files to Canvas so be careful to avoid missing or unedited files.