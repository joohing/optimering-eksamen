# Alright guys here we go, lecture 3!

So basically it starts out by repeating a bunch of stuff. Hope nothing new was
there because I didn't read it.

Then we get some details about the feasibility of the origo.

# Non-feasible origo

A non-feasible origo occurs when ANY of the $b_i$'s is negative. Obviously,
however, this can be solved by constructing the Auxiliary problem (which is
fancy talk for adding a large number to the $b_i$'s so that they are not
negative, as talked about in lecture 2).

# Crucial property about the Auxiliary problem (woah! so crucial!)

The optimal value of the auxiliary problem will be 0 IF AND ONLY IF the original
problem is feasible. Also an optimal solution is feasible for the original.

Apparently, which he didn't mention in the last lecture, you should also choose
the entering variable (when removing $x_0$ from the basic variables) such that
$b_i$ is minimal. So remember that I guess lmao).

# Now, what's the running time of all this?

Very large. It's $(n+m)!/(n!m!)$. Which means exponential in $m$ and $n$. That's
crazy!

For the Klee-Minty example (which I guess is some research duo that found a
particularly bad example for the Simplex algorithm), it takes $2^n$ pivots.

The reason is that the feasible region, which is basically a hyperbox, has $2^n$
corners, and the Simplex algorithm (with the largest coefficient rule) visits
each and every one of these.

# Is wurst-case analysis even useful?

Long story short - not super useful. Sure, it's nice to have theoretical
guarantees, but it turns out that the simplex algorithm is super good for most
"natural" cases of input. 

# Practical experiments

The book gives an example of running on i.i.d. normally distributed entries of
$A$, $b$, $c$, $n$ and $m$ picked at random between 10 and 1000 with some weird
distribution. For this they found $0.150 \text{min}(m, n)^{1.70}$ to be the case for
when there is an optimal solution. For unbounded problems, it was slightly
faster at $0.180 \text{min}(m, n)^{1.42}$

The rest of this lecture is about duality, which is not in the scope of this
exam subject so I ain't repeating it here.
