# Lab: Self-Driving Racecars

Team members (edit these):
1. Team member 1
1. Team member 2

### Before you start...

Make sure to write down your name and your teammate's name at the top of this file and at the top of your Java code!
   When you're working on this project, if you start running into syntax problems or issues with your Java file, first, 
   talk to me!  If you're unable to debug a problem in your Java code as you're completing the lab, do your best to solve
   the problem, but submit your Java file with your attempt included.  In this case, please provide a description of the problem you encountered and the steps you took to fix it here.
   
   Also, make *sure* that you submit both your files and that both have your answers recorded!!

## Goals

In this lab, you will modify some classes to design a 
self-driving race car class that can navigate its way 
around a track.

When you're done, you and your partner should be able to:
- Interpret classes, including instance variables,
methods and constructors.
- Create objects and call methods on them.
- Apply critical thinking more effectively.

## Part A: The `Car` class.

Open up the `Car` class (in `Car.java`). Read the Javadoc 
comment at the top of the `Car.java` file, and skim through
the rest of the file.

- How many instance variables (also called class variables-these are variables that are declared inside the class but outside of any function) does the `Car` class have?

__Your answer here__

- Now open the `CarDemo` class (`CarDemo.java`).  Run the
file.  

  When the line of code that says `System.out.println(racecar);`
  is encountered, what instance method inside the Car class
  does `println()` automatically seem to call behind the scenes?
  (Look at all the methods in `Car` --- one of them is
  being implicitly called by `println()`.)

__Your answer here__

- Modify this method so that the `println()` call will
  also print out the current speed of the car.

__(Put your answer in the Java file)__

- Find the *constructor* in the `Car` class.  Constructors
  are automatically called by Java when the `new` keyword
  is used to instantiate an object; their main purpose
  is to initialize the instance variables of an object
  and put the object into a usable state.  They look like
  regular instance methods, but the way to tell a method
  is a constructor is that it will always have the same
  name as the class itself and won't have a return type.

  According to the constructor, what direction does each
  car face when it is created?

__Your answer here__

- Modify the constructor so a car will face east when
it is created.  Verify that the println statement in 
CarDemo prints out the new direction.

__(Put your answer in the Java file)__

- Modify `CarDemo` to call instance methods on our
racecar object so that it will be at location (2, 5),
face south, and have a speed of 3.  Verify that the println
statement in CarDemo prints out this information 
correctly.

__(Put your answer in the Java file)__

- Modify `CarDemo` to create a second `Car` object, and
call its instance methods to set its location to (6, 2),
face west, and have speed of 5.  Use println on this second
car to verify the information.

__(Put your answer in the Java file)__

- Right now the `Car` class is ready to be used, except we
want to add one more instance variable: a **color** so 
that we can distinguish cars from each other on the track.
Add a color instance variable to the class --- this variable
should be a `Color` object (not a String!).  Then add
`getColor()` and `setColor(Color newColor)` instance methods 
to the class.  Pick a default color for cars and change the 
constructor so cars will be this color when they are created.  

__(Put your answer in the Java file)__

- Now, use `setColor()` in CarDemo to change the colors
of your two cars.  Modify the toString() method so the
color of a car will be part of its String representation,
and verify that the cars' colors are changed.

## Part B: The first race

- Open the `Racetrack` class.  This class represents a
racetrack your cars will drive on.  Look over the file,
paying particular attention to the instance variables
`trackDiagram` and the `cars` array.  

In the constructor for the Racetrack, how does one
specify the number of cars that will compete in the race?
What does the constructor do with this information
regarding the `cars` array?

__Your answer here__

- Open the `RaceDemos` class and look at the code for
`demo1()`.  Notice how the code creates a new Racetrack,
creates a new car, and adds the car to the track.  Then
the race starts.  **Run the demo now.**

What did the car do?  Why did it do this?  Hint: What
does the `drive()` method for the `Car` class always 
tell it to do?  (We will fix this soon.)

__Your answer here__

- Let's add a second car to the race!  In `RaceDemos.java`,
go back to the `demo1()` function.  Before `startRace()`
is called, create a second car and start it at position
(1, 1) facing south, with a speed of 1.  Modify the instantiation
of the `RaceTrack` object so that the track can hold 2 cars,
not just 1.  Then use `addCar()` to add your new car to index 1.
Do you see two white cars that drive straight off the 
track? (you should!)  

__Your answer here__

- Now let's fix the car colors.  In the `Racetrack` class,
modify the `draw()` method so that each car is drawn
in its own color.  The code that draws the cars is at
the very end of `draw()`.  Hint: use `getColor()` to 
obtain the color of a car, and replace the code that
draws the car in white with code that uses the color of
the car.  

__(Put your answer in the Java file)__

- The cars still always drive off the track.  Let's fix
that.  The self-driving car code is all contained
in the Car's `drive()` method.  Read the JavaDoc comment
above the function to remind yourself how this method
is supposed to work.  This method gets data
from the car's three cameras, and therefore you have
`char` variables representing the view of the immediate
square ahead of the car, and the squares to the car's left and right.
Notice that `drive()` should return 0, -1, or 1, indicating
which direction the car should head (relative to the
direction it is facing; so if a car is heading south
and returns -1 to "turn left", it will now be heading
west.)

Modify this method to examine the three `char` variables
you are given to figure out which one is the road.  It's
guaranteed (for now) that only one of the three
will ever be viewing the road, since this track has no
forks.  Note that you do not need to call setDirection() 
in this drive() code, the pre-written code in the Racetrack
will set your car's direction for you once you return 0,
1 or -1.  

Are your cars driving correctly around the track now,
in their appropriate colors?

__Your answer here__

- Change the speed of one of the cars to 2.  (Do this in
the code for the `demo1()` function).   When the 
faster car overtakes the slower one, do they crash or
pass each other?  Why?

__Your answer here__

- Make one of the cars drive around the track 
in the opposite direction.  When the cars encounter
each other, do they crash or pass each other?

__Your answer here__

- Could an individual car detect a "crash" with another
car?  (In other words, could you put code in the `Car` class
that could detect when two cars are occupying the same
space on the track?  Why or why not?  If not, where
would this code have to go?

__Your answer here__

- What happens when you add the same car to two
different indices in the `cars` array with `addCar`?
Example: with myCar, doing `addCar(0, myCar)` followed
by `addCar(1, myCar)`?

__Your answer here__

- What happens when you add two different cars to 
the same index in the `cars` array with `addCar`?
Example: with 2 cars called myCar and myCar2, 
doing `addCar(0, myCar)` followed
by `addCar(0, myCar2)`?

__Your answer here__

## Part C: The second race

In `main()`, comment out the call to `demo1()` and uncomment
`demo2()`.  Run the second demo.  You should see two cars
again that go around a track, but it's possible that
the new yellow square (which is part of the track) will
cause them to drive off the road.  This depends on how
you wrote your `drive()` code.

- If your cars drive off the road again, fix `drive()`
so that they are allowed to drive on the yellow part
of the road, which is a "power up" that you can drive
over and go faster (which right now won't do anything).

You will also want to set the color of each car so you
can tell them apart.

__(Put your answer in the Java file)__

- When a car drives over the power-up square, what we
want to happen is the car gets an extra speed boost
for 5 seconds (5 cycles of driving).  The way we will
do this is when the Racetrack sees a car drive over
the power-up, it will call a method called `powerup()`
on the car.  This new method should increase the speed
of the car, but only for 5 cycles of driving.

To get started, uncomment the code in Racetrack that
detects the power-up square (it is inside the nested
loop in startRace()).  You will get a red squiggly
because you haven't written the powerup() method yet.
Add this method to the Car class (make it blank for now).
This should be a void method that takes no arguments.

At this point your code should run, and a message should
be printed whenever a car drives over the power-up.
Do you see the messages?

__Your answer here__

The way the power-up will work is that when a car receives
a power-up, it will immediately increase its speed by 1.
It will also set a counter instance variable to 5, 
indicating that the power-up lasts for 5 cycles of driving.
Every time drive() is called, your drive() code will
decrease this counter variable by 1, and when it goes
to 0, decrease the speed of the car by 1 (ending the
power-up).

First, create an instance variable called 
`powerupTimeRemaining`.  

Second, inside your powerup() method,
set this variable to 5 and increase the speed of the car
by 1.

**Run the demo now, and when your car drives over
the powerup, it should get faster.  However, we haven't
written any code to eventually decrease the speed, so
the car will get faster forever.**

Third, modify your drive() method so that it always
decreases `powerupTimeRemaining` and when it hits zero,
decrease the speed of the car.  

**Run the demo now, and when your car drives over
the powerup, it should get faster.  But it should
only last five seconds.**

- Why do we have to make `powerupTimeRemaining` an
instance variable?  Why can't we make it a local
variable in `powerup()` or `drive()`?

__Your answer here__

## Final check

Once you have finished the lab, make sure to submit your files to Canvas!  **Both** partners are required to submit the completed assignment!

Each week, you need to submit **your programming files** (the files in the project that you've changed) and your **text file** (this file, with your answers filled in).   Make sure that your .java file has a header comment on it with **your teams' names**.  Your text file also needs to have the names of both team members at the top.

After you submit your files to Canvas, I strongly encourage you to go back and double-check:
- That you have submitted both the programming files and the text file.
- That both files have your changes and latest updates in them.
- That the programming file has a header with team names and honor code and that the text file has team names as well.

It is your responsibility to submit these files to Canvas so be careful to avoid missing or unedited files.