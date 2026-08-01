# Change of Basis and Matrix Representations: A Deeper Guide

# Overview

A linear transformation is an abstract function between vector spaces. A
matrix is **not** the transformation itself---it is merely a description
of that transformation after coordinate systems (bases) have been
chosen.

This distinction is the key idea behind change of basis.

------------------------------------------------------------------------

# 1. The Abstract Picture

Suppose

\[ T:V`\rightarrow `{=tex}W. \]

There are three different objects:

-   the vector spaces (V) and (W),
-   the linear map (T),
-   coordinate systems (bases) used to describe vectors.

The map exists independently of any coordinates.

------------------------------------------------------------------------

# 2. Coordinates are a Translation

Choosing a basis

\[ `\mathcal `{=tex}B=(v_1,`\ldots`{=tex},v_n) \]

creates a coordinate map

\[
`\phi`{=tex}\_{`\mathcal `{=tex}B}:V`\rightarrow`{=tex}`\mathbb `{=tex}R\^n,
\]

defined by

\[ `\phi`{=tex}*{`\mathcal `{=tex}B}(v)=\[v\]*{`\mathcal `{=tex}B}. \]

This map is an isomorphism.

Likewise, choosing a basis

\[ `\mathcal `{=tex}D \]

for (W) creates

\[
`\phi`{=tex}\_{`\mathcal `{=tex}D}:W`\rightarrow`{=tex}`\mathbb `{=tex}R\^m.
\]

Coordinates simply translate abstract vectors into column vectors.

------------------------------------------------------------------------

# 3. The Commutative Diagram

The relationship is

``` text
             T
      V -------------> W
      |                |
 φ_B  |                | φ_D
      |                |
      v                v
     R^n ----A-------> R^m
```

where

\[ A=\[T\]\_{`\mathcal `{=tex}D`\leftarrow`{=tex}`\mathcal `{=tex}B}. \]

The diagram says

\[
A=`\phi`{=tex}*{`\mathcal `{=tex}D}`\circ `{=tex}T`\circ`{=tex}`\phi`{=tex}*{`\mathcal `{=tex}B}\^{-1}.
\]

Equivalently,

\[ \[T(v)\]*{`\mathcal `{=tex}D} = A\[v\]*{`\mathcal `{=tex}B}. \]

This is the fundamental definition of a matrix representation.

------------------------------------------------------------------------

# 4. Computing the Matrix

For each basis vector

\[ v_i`\in`{=tex}`\mathcal `{=tex}B, \]

compute

\[ T(v_i). \]

Express each image in basis (`\mathcal `{=tex}D).

Those coordinate vectors become the columns.

------------------------------------------------------------------------

# 5. Example: Different Dimensions

Consider

\[ T:`\mathbb `{=tex}R^3`\rightarrow`{=tex}`\mathbb `{=tex}R^2 \]

defined by

\[ T(x,y,z)= (x+z,, 2y-z). \]

Choose

\[ `\mathcal `{=tex}B= {(1,0,0),(0,1,0),(0,0,1)} \]

and

\[ `\mathcal `{=tex}D= {(1,1),(1,-1)}. \]

Compute

\[ T(e_1)=(1,0), \]

whose coordinates in (`\mathcal `{=tex}D) are

\[
```{=tex}
\begin{bmatrix}
1/2\\
1/2
\end{bmatrix}
```
. \]

Similarly,

\[ T(e_2)=(0,2) `\rightarrow`{=tex}
```{=tex}
\begin{bmatrix}
1\\
-1
\end{bmatrix}
```
, \]

and

\[ T(e_3)=(1,-1) `\rightarrow`{=tex}
```{=tex}
\begin{bmatrix}
0\\
1
\end{bmatrix}
```
. \]

Therefore

\[ \[T\]\_{`\mathcal `{=tex}D`\leftarrow`{=tex}`\mathcal `{=tex}B} =
```{=tex}
\begin{bmatrix}
1/2&1&0\\
1/2&-1&1
\end{bmatrix}
```
. \]

Notice that nothing requires the domain and codomain to have the same
dimension.

------------------------------------------------------------------------

# 6. General Change-of-Basis Formula

Suppose

-   old basis of (V): (`\mathcal `{=tex}B),
-   new basis of (V): (`\mathcal `{=tex}B'),
-   old basis of (W): (`\mathcal `{=tex}D),
-   new basis of (W): (`\mathcal `{=tex}D').

The matrix changes according to

\[ \[T\]*{`\mathcal `{=tex}D'`\leftarrow`{=tex}`\mathcal `{=tex}B'} =
P*{`\mathcal `{=tex}D'`\leftarrow`{=tex}`\mathcal `{=tex}D}
\[T\]*{`\mathcal `{=tex}D`\leftarrow`{=tex}`\mathcal `{=tex}B}
P*{`\mathcal `{=tex}B`\leftarrow`{=tex}`\mathcal `{=tex}B'}. \]

Why?

Starting with coordinates in (`\mathcal `{=tex}B'),

1.  convert to old coordinates using
    (P\_{`\mathcal `{=tex}B`\leftarrow`{=tex}`\mathcal `{=tex}B'}),
2.  apply the old matrix,
3.  convert the output into the new codomain basis using
    (P\_{`\mathcal `{=tex}D'`\leftarrow`{=tex}`\mathcal `{=tex}D}).

Reading these operations from right to left immediately gives the
formula.

------------------------------------------------------------------------

# 7. Special Case: Similarity

When

\[ T:V`\rightarrow `{=tex}V, \]

and only one basis changes,

\[ \[T\]*{`\mathcal `{=tex}B'} =
P*{`\mathcal `{=tex}B'`\leftarrow`{=tex}`\mathcal `{=tex}B}
\[T\]*{`\mathcal `{=tex}B}
P*{`\mathcal `{=tex}B`\leftarrow`{=tex}`\mathcal `{=tex}B'}. \]

Since

\[ P\_{`\mathcal `{=tex}B`\leftarrow`{=tex}`\mathcal `{=tex}B'} =
P\_{`\mathcal `{=tex}B'`\leftarrow`{=tex}`\mathcal `{=tex}B}\^{-1}, \]

this becomes

\[ A' = P\^{-1}AP \]

(or (PAP\^{-1}) depending on the convention for (P)).

Matrices related by similarity represent the **same linear
transformation**, merely written in different coordinate systems.

------------------------------------------------------------------------

# 8. Common Misconceptions

## "The matrix is the transformation."

False.

The transformation is abstract.

The matrix depends on the chosen bases.

------------------------------------------------------------------------

## "Changing bases changes the transformation."

False.

Only the numerical description changes.

------------------------------------------------------------------------

## "Every linear transformation has one matrix."

False.

A transformation has infinitely many matrix representations---one for
every pair of bases.

------------------------------------------------------------------------

# 9. Summary Table

  Concept                  Depends on Basis?
  ------------------------ -------------------
  Vector                   No
  Linear transformation    No
  Coordinates              Yes
  Matrix representation    Yes
  Change-of-basis matrix   Yes

------------------------------------------------------------------------

# Key Takeaways

1.  Coordinates are basis-dependent.
2.  Change-of-basis matrices convert coordinate vectors.
3.  A matrix represents a linear transformation only after choosing
    bases.
4.  Columns of the matrix are the images of the domain basis vectors
    expressed in the codomain basis.
5.  The general formula

\[ \[T\]*{`\mathcal `{=tex}D'`\leftarrow`{=tex}`\mathcal `{=tex}B'} =
P*{`\mathcal `{=tex}D'`\leftarrow`{=tex}`\mathcal `{=tex}D}
\[T\]*{`\mathcal `{=tex}D`\leftarrow`{=tex}`\mathcal `{=tex}B}
P*{`\mathcal `{=tex}B`\leftarrow`{=tex}`\mathcal `{=tex}B'} \]

contains every change-of-basis formula as a special case.
