# Valve-System
All type of valve automizetion 

### Singel *.ino file can do every valve setting without needed any extra file

File get update.until sketch finish.

so check daily for update.

when sketch finish we notify you.

notify us for any improvement in our sketch we will try to improve with ideas.



# PID Equation

We can express PID control mathematically with the following equation.
P, I, and D are represented by the three terms that add together here.
Kp, Ki, and Kd are constants that tune how the system reacts to each factor:

![PID calculation 1](https://user-images.githubusercontent.com/59052001/87008211-07bf4780-c1e1-11ea-8f74-7d3ff5304f46.png)
 
We can also replace Ki and Kd with 1/Ti and Td, respectively.
This change gives the equation a better relationship to
its physical meaning and allows the units to work out properly to a unitless number:

![PID calculation 2](https://user-images.githubusercontent.com/59052001/87008271-1f96cb80-c1e1-11ea-8ba7-ae551f0909b5.png)

We can also transpose the equation to extract the Kp value
and apply it to the entire equation,
in what's known as the standard form.
One advantage of this form is that we can adjust
the overall Kp constant for the whole equation at one time:

![PID calculation 3](https://user-images.githubusercontent.com/59052001/87008298-2cb3ba80-c1e1-11ea-8018-b5cfbd246929.png)

All of this may look a bit intimidating, perhaps even to someone who graduated with an engineering degree.
The good news is that you don't have to dig out your Modeling and Analysis of Dynamic Systems textbook to
understand what's going on here. And while it never hurts, you don't even have to be able to do calculus.

Breaking the first equation down, we produce u(t)—the unitless controller output on the left-hand side of 
the equation—by adding three mathematical elements on the right-hand side of the equal sign: P, I, and D. 
Each element has a constant K value in front (Kp, Ki, and Kd), which signifies each element's weight as 
they form u(t), or the control output at a specific time. We can individually tune each K value for better 
system performance, which we'll explain further below:

Proportional (P—Kp)

The first and most crucial term in this equation is the e(t). As such, the Kp value that comes before it 
is generally larger than the other K values in the equation. Here, e(t) is simply the instantaneous error 
at a point in time—the actual value of a controlled device minus the desired value. Multiply this by Kp and
you have its contribution to the overall controller output.

Integral (I—KI)

The second term in this equation has to do with the combined error over time. It's the sum of all errors
experienced on the device:

Each time a controller calculates u(t), it adds the instantaneous error to a running tally.

This figure is then multiplied by Ki and added into u(t). 

Consider a situation where a force holds a motor in place and doesn't allow it to return to the setpoint under
normal conditions. As it's out of spec longer and longer, the I term will continue to increase, eventually 
overcoming this force or reaching the limits of the motor's capability.

Derivative (D—Kd)

The third term in this equation has to do with how fast the error changes:

Theoretically, if you only had a D term in this equation and your process steadily maintained the wrong value,
this term would remain zero and wouldn't contribute to the proper output. On the other hand, if one of the 
other two terms tries to make the device's output snap back into place too quickly, the derivative can help
dampen the effect.

While the calculus-based expression of this concept can be useful, the reality of PID control is much less
magical than it first appears. Practically speaking, we calculate output using only addition, subtraction,
and multiplication, factoring in the error and time between readings. In fact, we used pneumatic systems to 
implement early forms of PID control, using mechanical means to input each "term."

1. Controllers take an instantaneous error reading.

2. Subtract the previous instantaneous reading from it.

3. Multiply that resulting valueby Kd to calculate its contribution to u(t). 


## How To Genaret Pulse for stepper motor

How many turns (N t = number of turns)
Stepper Driver microsteps (steps/revolution)
minimun turn value(Nmin = number of minimun turn > value in float)
maximun turn value (= number of turns)(Nmax = number of maximum turn > value in float)

What we need maximum pulse and minimum pulse?
Pmin = ?
Pmax = ?

example:
N t = 5
steps/revolution = 200

Pmax = N t X steps/revolution
     = 4 X 200
Pmax = 800

Pmin = Nmin X steps?revolution
     = 0.5 X 200
Pmin = 100

Analog Output is between = 1 to 1023

simple math use here
 Analog Out Max         Pmax
 1023                   800
 Analog Out             P
 45                     ?

P = (45 X 800)/1023
P = (36000)/1023 
P = 35.19061583577713‬
P = 35
