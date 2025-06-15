# Implementing the Basic Simplex Method

Alright cowboys, here we go.

So what is the issue with the way we've been doing this so far? We've been
assuming that we can do exact arithmetic operations. We also need to find some
proper way of representing the dictionary in computer form so that stupid bleep
bloop computer can understand it (cringe).

For the second one, we introduce the LP tableau.

# The LP tableau

If you have a dictionary

\begin{align}
    \text{Maximize}&\ 5x_1 + 4x_2 + 3x_3\\
    \text{Subject to}&\ 2x_1 + 3x_2 + x_3 \leq 5\\
        &\ 4x_1 + x_2 + 2x_3 \leq 11\\
        &\ 3x_1 + 4x_2 + 2x_3 \leq 8\\
        &\ x_1, x_2, x_3 \geq 0\\
\end{align}

Then it becomes the following tableau

(actually I ain't writing all that, just look at the slides nerd)

Whoops looks like the guy writes that we shall prefer to use a dictionary in
implementations, so I guess this was just because he likes to talk about the
tableaus.

# Exact arithmetic

To avoid numeric issues, we can perform arithmetic using rational numbers
(fractions). This also assumes that we have rational numbers. Which is probably
the case. If we want to avoid an absolute explosion in the size of the numbers
in the denominator and the numerator, we will have to simplify once in a while,
which means that we will end up having to spend a long time doing GCD operations
(greatest common divisor, in order to find the best number to reduce the
fraction with).

So how do we fix that?

# Integer pivoting

We use integer pivoting, which is basically this:

\begin{itemize}
    \item Keep track of the negative of the last pivot coefficient. At the very
    start, it is initialized to just be 1.
    \item Select variables such that you are ready to do a pivot.
    \item Then, take the negative of the pivot coefficient (the coefficient on
    the variable at the intersection between the chosen row and the chosen
    column) and scale all the other rows (except the row of the basic variable
    chosen for leaving) by it.
    \item Do the pivot as you normally would.
    \item Now, divide through by the previous value you multiplied by, which you
    stored.
\end{itemize}

This approach will avoid construction of fractions altogether, which is super
nice, but does of course do additional multiplications. If you are willing to
take a precision hit, it might still be worth it to just use floating point
arithmetic.

# Floating-point number speed-up

Good thing is that it's very fast, since it's supported by the hardware, but
unfortunately there's a significant loss of precision, so a robust
implementation will be challenging (which we know from dealing with
implementation issues ourselves in Machine Learning). Errors will accumulate. (A
first intuition might be to just treat numbers inbetween some epsilon and its
negative as zero. My guy Kristoffer doesn't offer further thoughts on this on
his slides though LMAO.)
