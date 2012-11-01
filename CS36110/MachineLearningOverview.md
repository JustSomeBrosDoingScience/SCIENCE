## Machine Learning Like You're 5

# General Principle
> Machine Learning is the science of getting computers to act without being
> explicitly programmed.


>A computer program is said to learn from experience E with respect to some
>class of tasks T and performance measure P, if its performance at T, as
>measured by P, improves with experience E.

In short, machine learning is an iterative process that seeks to reduce the difference
between the output it gets, given its inputs, and the desired output - this is the *cost*
of the current state of the program. It does this by manipulating the program's parameters, ($\theta$), just like how you would manipulate the steering in a car to make the car turn rather than
open the door and drag your foot on the ground. The only thing you can change directly are the parameters.

A simple (lol) example as follows:

> You want your algorithm to learn that 1+1=2 <- that right there is your whole training set.
>
> The size of the training set, *m*, is **1**, the vector **x** is the input, *1+1*, and your desired output is **y**, *2*.
>
> In the training stage, you iterate over this training set as many times as you need to get the *cost*
> as close to zero as possible (ignoring the need for generalisation).
>
> When you start out, your parameter, $\theta$, is typically a matrix of zeros. Sparing you the details of how this
> happens for now, let's just say that after the very first iteration the *hypothesis*, or what your program thinks the
> answer is given $\theta$ and your inputs, is something retarded like 0. The *cost* function, the result of which that
> iteration just returned, is the difference between your hypothesis and the actual answer, so *1*.
>
> 1 is not 0 so you iterate over the whole training set again - but before you do, you make a change to $\theta$ that you
> know will yield the output you actually want. You actually make these changes to theta for each item in the training
> set within an iteration.