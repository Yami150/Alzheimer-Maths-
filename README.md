\documentclass[12pt,a4paper]{article}

\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[english]{babel}
\usepackage{amsmath,amssymb,amsthm}
\usepackage[a4paper,margin=2.5cm]{geometry}
\usepackage{xcolor}
\usepackage{listings}
\usepackage{hyperref}

\hypersetup{
    colorlinks=true,
    linkcolor=blue,
    urlcolor=blue
}

\lstdefinestyle{pythonstyle}{
    language=Python,
    basicstyle=\ttfamily\small,
    keywordstyle=\color{blue},
    commentstyle=\color{gray},
    stringstyle=\color{red!70!black},
    numbers=left,
    numberstyle=\tiny\color{gray},
    stepnumber=1,
    numbersep=8pt,
    showstringspaces=false,
    breaklines=true,
    frame=single,
    tabsize=4
}

\lstset{style=pythonstyle}

\title{\textbf{Alzheimer Maths}}
\author{Yami}
\date{}

\begin{document}

\maketitle

\section{Foundations of the System (Axioms)}

\subsection{The Initial Set}

The universe is initialized with a finite inventory containing the
integers $[1,\ldots,9]$, their negatives $[-1,\ldots,-9]$, and their
reciprocal fractions $[1,\ldots,1/9]$.

The $1$ here is considered a different iteration from $1$, but acts
as $1$.

And their negative reciprocal fractions.

\subsection{Axiom 1: Destructive Consumption}

Every mathematical operation permanently consumes its operands.
A number that is used is destroyed and no longer exists, unless it
is recreated by the result of an operation.

The available operations are multiplication and addition, and they
act as they do under the ZFC system.

\subsection{Axiom 2: Multiplicity}

The same number can exist in several distinct iterations (tokens)
within the inventory.

\subsection{Axiom 3: Operation P (Loss)}

The operation $P(x)$ consumes the token $x$ without generating
a new result. It is pure destruction.

\subsection{Axiom 4: Operation R (Reset)}

The operation $R$ clears the current inventory and resets the system
exactly to its initial state.

\subsection{Axiom 5}

A term, if it has only one iteration, cannot be used twice in the
same operation.

For example, if the set contains only $[1,0]$, the operation
\[
1-1
\]
is forbidden.

\section{Fundamental Theorems}

\subsection{Theorem 1: The Number of Numbers}

\textit{``There will always be fewer numbers in the system than
at the beginning.''}

\paragraph{Proof.}

Each binary operation ($+$, $\times$, $-$, $\div$) consumes two
tokens to generate only one (net change: $-1$ token).

Each operation $P$ consumes one token and generates zero
(net change: $-1$ token).

The total number of tokens strictly decreases at every step.

\subsection{Theorem 2: The End of the World}

\textit{``If you start with a set of $N$ numbers, you will have at
most $N$ operations in this system, and the $N$-th operation
different from $R$ will always be a $P$.''}

\paragraph{Proof.}

According to Theorem 1, each operation removes exactly one token
from the system.

After $N-1$ operations, the inventory contains only one token:
\[
N-(N-1)=1.
\]

At this point, binary operations are impossible due to a lack of
operands. The only remaining legal action different from $R$ is
the unary operation $P$.

The $N$-th operation that is not an $R$ is therefore inevitably
an extinction through $P$.

\subsection{Theorem 3: Maximum Possible Number}

Knowing that, for two positive integers $a$ and $b$ different from
$1$, we have
\[
a*b\geq a+b,
\]
the maximum possible number in our set is

\[
9! + \text{an even number of negative factors multiplied together,
greater than }1.
\]

Here, we can use at most eight negative factors:
\[
(-9)(-8)(-7)(-6)(-5)(-4)(-3)(-2)=9!.
\]

We therefore have
\[
(9!)^2.
\]

And we can add to this number the sum of the decimals, from $1$ to
$\frac{1}{9}$:

\[
(9!)^2
\left(
1+\frac12+\frac13+\frac14+\frac15+
\frac16+\frac17+\frac18+\frac19
\right)^2.
\]

Let us call this number, for simplicity, Max.

Any other method is non-optimal. Adding the negative terms reduces
the value, multiplying the fractions reduces the value, and adding
positive values creates numbers smaller than multiplying them.

This considers the set of possible strategies, taking each group
separately.

For the numbers from $1$ to $9$, we can add or multiply them.
Since
\[
a*b\geq a+b,
\]
multiplying them creates a larger number.

For negative numbers, we can add or multiply them. Adding them
creates more negative numbers. Even if we try to add them and then
multiply them by $-1$, we will create a number smaller than a large
multiplication.

To create an even larger number with the first $9!$, the optimal
choice is to multiply them again.

For positive fractions, knowing that they are between $-1$ and $1$,
multiplying them will always create smaller numbers. Adding them is
the optimal choice.

Their sum will be greater than $1$, so multiplication is then
the optimal choice.

For negative fractions, the strategy follows the same logic as for
fractions: a sum is used as a term in a product. To transform the
negative sum into a positive term in a product, we use the $-1$
left over from the negative terms.

The set of terms created is greater than $1$. The optimal way to
combine them is therefore multiplication.

We obtain:

\[
\boxed{
\mathrm{Max}
=
(9!)^2
\left(
1+\frac12+\frac13+\frac14+\frac15+
\frac16+\frac17+\frac18+\frac19
\right)^2
}
\]

Since
\[
1+\frac12+\frac13+\frac14+\frac15+
\frac16+\frac17+\frac18+\frac19
=
\frac{7129}{2520},
\]
we have
\[
\boxed{
\mathrm{Max}
=
(362880)^2
\left(\frac{7129}{2520}\right)^2
}
\]

Numerically,
\[
\boxed{
\mathrm{Max}\approx 1.0538\times 10^{12}
}
\]

\section{Python Simulation}

\subsection{Checking Token Multiplicity}

\begin{lstlisting}
def T2valide(t1, t2, nombres):
    if t1 != t2:
        return True
    else:
        n = 0
        for i in nombres:
            if i == t1:
                n += 1

        if n > 1:
            return True

    return False
\end{lstlisting}

\subsection{Simulation Program}

\begin{lstlisting}
print("Type stop to end the simulation")

Run = True
New_world = True


def T2valide(t1, t2, nombres):
    if t1 != t2:
        return True

    n = 0

    for i in nombres:
        if i == t1:
            n += 1

    return n > 1


while Run:

    if New_world:
        nombres = [
            # Positive integers
            1.0, 2.0, 3.0, 4.0, 5.0,
            6.0, 7.0, 8.0, 9.0,

            # Negative integers
            -1.0, -2.0, -3.0, -4.0, -5.0,
            -6.0, -7.0, -8.0, -9.0,

            # Positive fractions
            1.0, 1/2, 1/3, 1/4, 1/5,
            1/6, 1/7, 1/8, 1/9,

            # Negative fractions
            -1.0, -1/2, -1/3, -1/4, -1/5,
            -1/6, -1/7, -1/8, -1/9
        ]

        New_world = False
        print("New inventory:", nombres)

    else:
        operation = input(
            "Operation to perform (+, *, P, R, stop): "
        )

        if operation == "stop":
            Run = False

        elif operation == "R":
            New_world = True

        elif operation == "P":
            T1 = float(input("Number to destroy: "))

            if T1 in nombres:
                nombres.remove(T1)
                print("Inventory:", nombres)
            else:
                print("Invalid operation: token not found.")

        elif operation in ("+", "*"):
            T1 = float(input("First number: "))

            if T1 not in nombres:
                print("First token not found.")
                continue

            T2 = float(input("Second number: "))

            if T2 not in nombres or not T2valide(
                T1, T2, nombres
            ):
                print("Invalid operation: tokens unavailable.")
                continue

            # Consume both tokens
            nombres.remove(T1)
            nombres.remove(T2)

            # Create the result
            if operation == "+":
                resultat = T1 + T2
            else:
                resultat = T1 * T2

            nombres.append(resultat)

            print("Result:", resultat)
            print("Inventory:", nombres)

        else:
            print("Unsupported operation.")
\end{lstlisting}

\end{document}
