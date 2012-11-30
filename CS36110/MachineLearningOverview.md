## Machine Learning Like You're 5

*There's a class on [coursera.org](coursera.org/course/ml) covering much, if not all, of the syllabus of CS361.
It is highly recommended that you go through the content of that course too since Prof. Andrew Ng is basically God.*


# General Principle
> Machine Learning is the science of getting computers to act without being
> explicitly programmed.


> A computer program is said to learn from experience E with respect to some
> class of tasks T and performance measure P, if its performance at T, as
> measured by P, improves with experience E.

In short, machine learning is an iterative process that seeks to reduce the difference
between the output it gets and the desired output - this difference is the *cost*
of the current state of the program. It does this by manipulating the program's parameters, ($\theta$),
just like how you would manipulate the steering wheel in a car to make the car turn rather than
physically pushing it under your own strength. The only thing you can change directly are these parameters.


*Note about $\theta$: The term $\theta$ can change in meaning depending on which ML technique you're looking at.
In terms of ANNs, $\theta$ refers to the matrices representing the weights between layers. In Linear Regression it's
the parameters for the hypothesis that tries to fit the data. What all these definitions have in common is that $\theta$
is the value you can change to alter the program's output.*

*The cost function could be the 'squared error' function thusly:*

![Cost Function](https://raw.github.com/JustSomeBrosDoingScience/SCIENCE/develop/CS36110/cost_function_example.png)

*That's (1/2m), I'll change the image when I can be bothered XD.

A simple (hurr) example as follows:


*Addendum by James:* Where Craig talks about 'Cost', the ML lady has been
talking about 'Error Function'.

> You want your algorithm to learn that 1+1=2 <- that right there is your whole training set.
>
> The size of the training set, **m**, is *1*, the vector **x** is the input, *1+1*, and your desired output, **y**, is *2*.
>
> In the training stage, you iterate over this training set as many times as you need to get the *cost*
> as close to zero as possible or for a predetermined number of iteations - whichever comes first.
>
> When you start out, your parameter, $\theta$, is typically a matrix of random values between +/- 0.12 ($\epsilon$). Sparing you the details of how this
> happens for now, let's just say that after the very first iteration the *hypothesis*, what your program thinks the
> answer is given $\theta$ and your inputs, is something retarded like 0. The *cost* function, the result of which that
> iteration just returned, is the difference between your hypothesis and the actual answer, so the cost is *2-0=2*.
>
> 2 is not 0 so you iterate over the whole training set again - but before you do, you make a change to $\theta$ that you
> know will bring the cost closer to 0 and the hypothesis a little bit closer to what you actually want - that change is called $\delta\theta$. You actually make these changes to
> theta for each item in the training set within an iteration over the training set. The idea is that, evetually, $\theta$
> be a set of values that satisfy all items in the training set.

> **In short**, If $\theta$ started out as 0, and your hypothesis is 0 after your first iteration over the whole training set,
> you alter \$theta$ such that the function *cost($\theta$)* approaches 0 and, as a result, the hypothesis approache the
> correct answer. Do this as many times as necessary.

I should point out that the program doesn't actually carry out the calculation of *1+1*, all it does it map the inputs to outputs.
If you had a dataset of lots of different examples of the addition operation, such as 5+5=10, the program could learn how to add
numbers together that it has never seen before but not actually *do* the calculation. It's just rote learning.

*Note: It is possible to use ML to learn how to carry out the calcultions but that is rather advanced.*

##Gradient Descent
Here's a really shitty image of how the cost reduces as \$theta$ is changed - the function is supposed to be parabolic but looks hyperbolic because I cannot into MS Paint.

![Gradient Descent](https://raw.github.com/JustSomeBrosDoingScience/SCIENCE/develop/CS36110/grad_descent.png)
