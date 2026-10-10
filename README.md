# Alzheimer-Maths-
A system of mathematics i did to better understand axioms and logic
\documentclass[12pt,a4paper]{article}

% Encodage et langue
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[french]{babel}

% Mathématiques et mise en page
\usepackage{amsmath,amssymb,amsthm}
\usepackage[a4paper,margin=2.5cm]{geometry}
\usepackage{xcolor}
\usepackage{listings}
\usepackage{hyperref}
\usepackage{enumitem}

% Configuration des liens
\hypersetup{
    colorlinks=true,
    linkcolor=blue,
    urlcolor=blue
}

% Configuration du code Python
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

% Environnements mathématiques
\newtheorem{axiome}{Axiome}
\newtheorem{theoreme}{Théorème}

\title{\textbf{Les Mathématiques d'Alzheimer}\\
\large Alzheimer Maths}
\author{Yami}
\date{}

\begin{document}

\maketitle

\begin{abstract}
Ce document présente les fondations, les théorèmes et une simulation
informatique du système appelé \textit{Les Mathématiques d'Alzheimer}.
\end{abstract}

\section{Les fondations du système : axiomes}

\subsection{Le set de départ}

L'univers est initialisé avec un inventaire fini contenant les entiers
de $1$ à $9$, leurs opposés de $-1$ à $-9$, ainsi que leurs fractions
inverses, de $1$ à $\frac{1}{9}$, et leurs fractions inverses négatives.

Le nombre $1$ présent dans les fractions inverses est considéré comme
une itération différente du nombre $1$ entier, mais agit comme $1$.

\subsection{Axiome 1 : consommation destructive}

Toute opération mathématique consomme définitivement ses opérandes.
Un nombre utilisé est détruit et n'existe plus, sauf s'il est recréé
par le résultat d'une opération.

Les opérations qui existent sont la multiplication et l'addition.
Elles agissent comme dans le système ZFC.

\subsection{Axiome 2 : multiplicité}

Un même nombre peut exister en plusieurs itérations (jetons)
distinctes dans l'inventaire.

\subsection{Axiome 3 : opération $P$ (perte)}

L'opération $P(x)$ consomme le jeton $x$ sans générer de nouveau
résultat. C'est une destruction pure.

\subsection{Axiome 4 : opération $R$ (reset)}

L'opération $R$ purge l'inventaire courant et réinitialise le système
exactement à son état de départ.

\subsection{Axiome 5 : interdiction de réutiliser un jeton}

Un même terme, s'il ne possède qu'une seule itération, ne peut pas
être utilisé deux fois dans la même opération.

Par exemple, si l'ensemble contient seulement les jetons $[1,0]$,
l'opération
\[
1-1
\]
est interdite, car un seul jeton de valeur $1$ est disponible.

\section{Les théorèmes fondamentaux}

\subsection{Théorème 1 : le nombre de nombres}

\textit{« Vous aurez toujours moins de nombres dans le système
qu'au départ. »}

\paragraph{Démonstration.}
Chaque opération binaire ($+$, $\times$, $-$, $\div$) consomme deux
jetons pour n'en générer qu'un seul. Le bilan est donc de $-1$ jeton.

Chaque opération $P$ consomme un jeton pour en générer zéro.
Le bilan est également de $-1$ jeton.

La quantité globale de jetons décroît strictement à chaque étape.

\subsection{Théorème 2 : la fin du monde}

\textit{« Si vous commencez avec un ensemble de $N$ nombres, vous aurez
au maximum $N$ opérations dans ce système, et la $N$-ième opération
différente de $R$ sera toujours un $P$. »}

\paragraph{Démonstration.}
D'après le théorème 1, chaque opération retire exactement un jeton
du système.

Après $N-1$ opérations, l'inventaire ne contient plus qu'un seul et
unique jeton :
\[
N-(N-1)=1.
\]

À cet état, les opérations binaires sont impossibles par manque
d'opérandes. La seule action légale restante, différente de $R$,
est l'opération unitaire $P$.

La $N$-ième opération qui n'est pas un $R$ est donc fatalement une
extinction par $P$.

\subsection{Théorème 3 : nombre maximal possible}

Sachant que, pour deux entiers positifs différents de $1$, $a$ et $b$,
on a :
\[
a \times b \geq a+b,
\]
le nombre maximal possible dans notre set est obtenu en multipliant
les entiers positifs, puis les facteurs négatifs appropriés.

On peut utiliser au maximum huit facteurs négatifs de valeur absolue
supérieure à $1$ :
\[
(-9)\times(-8)\times(-7)\times(-6)\times(-5)
\times(-4)\times(-3)\times(-2)=9!.
\]

On a donc :
\[
(9!)^2.
\]

On peut ajouter à ce nombre la somme des fractions positives,
de $\frac{1}{1}$ à $\frac{1}{9}$.

Ainsi :
\[
(9!)^2
\left(
1+\frac12+\frac13+\frac14+\frac15+
\frac16+\frac17+\frac18+\frac19
\right)^2.
\]

Appelons ce nombre, par simplicité, \textit{Max} :
\[
\boxed{
\mathrm{Max}=(9!)^2
\left(
1+\frac12+\frac13+\frac14+\frac15+
\frac16+\frac17+\frac18+\frac19
\right)^2
}
\]

Tout autre moyen est non optimal : additionner les termes négatifs
réduit la valeur, multiplier les fractions réduit la valeur, et
additionner des valeurs positives crée des nombres moins grands que
leur multiplication.

Il s'agit de l'ensemble des stratégies possibles, en prenant les
ensembles terme par terme.

\paragraph{Pour les nombres de $1$ à $9$.}
On peut les additionner ou les multiplier. Or, puisque
\[
a\times b\geq a+b,
\]
les multiplier crée alors un nombre plus grand.

\paragraph{Pour les nombres négatifs.}
On peut les additionner ou les multiplier. Les additionner crée des
nombres plus négatifs. Même si l'on essaie de les additionner puis
de les multiplier par $-1$, on créera un nombre moins grand qu'une
grande multiplication.

Pour créer un nombre encore plus grand avec le premier $9!$,
l'optimal est de les multiplier à nouveau.

\paragraph{Pour les fractions positives.}
Sachant qu'elles sont comprises entre $-1$ et $1$, les multiplier
créera toujours des nombres plus petits. Les additionner est le
choix optimal.

Leur somme sera supérieure à $1$ ; multiplier est alors le choix
optimal.

\paragraph{Pour les fractions négatives.}
La stratégie utilisant la logique des fractions consiste en une somme
utilisée comme terme d'un produit. Pour transformer la somme négative
en un terme positif dans un produit, on utilise le $-1$ laissé par
les termes négatifs.

L'ensemble des termes créés est supérieur à $1$. La manière optimale
de les associer est alors la multiplication.

On obtient alors :
\[
\boxed{\mathrm{Max}=\ldots}
\]

\section{Simulation Python}

\subsection{Vérification de la multiplicité des jetons}

La fonction \texttt{T2valide} vérifie qu'une opération ne réutilise
pas un jeton unique deux fois.

\begin{lstlisting}
def T2valide(t1, t2, nombres):
    if t1 != t2:
        return True
    else:
        n = 0

        for i in nombres:
            if i == t1:
                n += 1

        return n > 1
\end{lstlisting}

\subsection{Programme de simulation}

\begin{lstlisting}
print("On peut arreter la simulation en tapant stop")

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
            # Entiers positifs
            1.0, 2.0, 3.0, 4.0, 5.0,
            6.0, 7.0, 8.0, 9.0,

            # Entiers negatifs
            -1.0, -2.0, -3.0, -4.0, -5.0,
            -6.0, -7.0, -8.0, -9.0,

            # Fractions positives
            1.0, 1/2, 1/3, 1/4, 1/5,
            1/6, 1/7, 1/8, 1/9,

            # Fractions negatives
            -1.0, -1/2, -1/3, -1/4, -1/5,
            -1/6, -1/7, -1/8, -1/9
        ]

        New_world = False
        print("Nouvel inventaire :", nombres)

    else:
        operation = input(
            "L'operation a effectuer (+, *, P, R, stop) : "
        )

        if operation == "stop":
            Run = False

        elif operation == "R":
            New_world = True

        elif operation == "P":
            T1 = float(input("Nombre a detruire : "))

            if T1 in nombres:
                nombres.remove(T1)
                print("Inventaire :", nombres)
            else:
                print("Operation impossible : jeton absent.")

        elif operation in ("+", "*"):
            T1 = float(input("Premier nombre : "))

            if T1 not in nombres:
                print("Premier jeton absent.")
                continue

            T2 = float(input("Deuxieme nombre : "))

            if T2 not in nombres or not T2valide(
                T1, T2, nombres
            ):
                print("Operation impossible : jetons indisponibles.")
                continue

            # Consommation des deux jetons
            nombres.remove(T1)
            nombres.remove(T2)

            # Creation du resultat
            if operation == "+":
                resultat = T1 + T2
            else:
                resultat = T1 * T2

            nombres.append(resultat)

            print("Resultat :", resultat)
            print("Inventaire :", nombres)

        else:
            print("Operation non acceptee.")
\end{lstlisting}

\end{document}
