# Change of Basis and Matrix Representations: A Deeper Guide

## Overview

A linear transformation is an abstract map between vector spaces. A matrix is not the transformation itself; it is the coordinate description of that transformation after bases have been chosen.

This distinction explains why one linear map can have many different matrices and why changing basis acts by matrix multiplication.

Throughout, let $V$ and $W$ be finite-dimensional vector spaces over a field $F$, with

```math
\dim_F V=n,\qquad \dim_F W=m.
```

## 1. The Abstract Picture

Suppose

```math
T:V\longrightarrow W
```

is linear. There are three separate kinds of objects:

- the vector spaces $V$ and $W$;
- the linear transformation $T$;
- the ordered bases used to express vectors as coordinate columns.

The spaces and the map exist independently of coordinates. A basis makes them computationally accessible.

## 2. Coordinate Isomorphisms

Choose ordered bases

```math
\mathcal B=(v_1,\ldots,v_n)\quad\text{of }V,
```

```math
\mathcal D=(w_1,\ldots,w_m)\quad\text{of }W.
```

Every $v\in V$ has a unique expression

```math
v=a_1v_1+\cdots+a_nv_n.
```

Its coordinate column is

```math
[v]_{\mathcal B}
=
\begin{pmatrix}
a_1\\
\vdots\\
a_n
\end{pmatrix}
\in F^n.
```

The coordinate map

```math
\phi_{\mathcal B}:V\longrightarrow F^n,\qquad
\phi_{\mathcal B}(v)=[v]_{\mathcal B}
```

is a linear isomorphism. Similarly,

```math
\phi_{\mathcal D}:W\longrightarrow F^m
```

is a linear isomorphism.

Coordinates translate abstract vectors into standard column vectors. They do not change the vectors themselves.

## 3. The Commutative Diagram

The abstract map and its matrix fit into the diagram

~~~ text
                  T
          V --------------> W
          |                 |
      φ_B |                 | φ_D
          |                 |
          v                 v
         F^n ------ A ----> F^m
~~~

The matrix in these coordinates is

```math
A=[T]_{\mathcal D\leftarrow\mathcal B}
=\phi_{\mathcal D}\circ T\circ\phi_{\mathcal B}^{-1}.
```

Equivalently, for every $v\in V$,

```math
[T(v)]_{\mathcal D}
=[T]_{\mathcal D\leftarrow\mathcal B}[v]_{\mathcal B}.
```

This identity is the fundamental definition of a matrix representation.

## 4. Computing the Matrix

For each basis vector $v_j\in\mathcal B$, write

```math
T(v_j)=\sum_{i=1}^m a_{ij}w_i.
```

Then

```math
[T]_{\mathcal D\leftarrow\mathcal B}
=
\begin{bmatrix}
[T(v_1)]_{\mathcal D}&\cdots&[T(v_n)]_{\mathcal D}
\end{bmatrix}
=(a_{ij}).
```

Thus the $j$th column is the $\mathcal D$-coordinate vector of $T(v_j)$.

## 5. Example with Different Dimensions

Consider

```math
T:\mathbb R^3\longrightarrow\mathbb R^2,\qquad
T(x,y,z)=(x+z,\,2y-z).
```

Use the standard basis

```math
\mathcal B=(e_1,e_2,e_3)
```

of $\mathbb R^3$ and the basis

```math
\mathcal D=\bigl((1,1),(1,-1)\bigr)
```

of $\mathbb R^2$. We compute

```math
T(e_1)=(1,0),\qquad
[T(e_1)]_{\mathcal D}
=
\begin{pmatrix}
\tfrac12\\
\tfrac12
\end{pmatrix},
```

```math
T(e_2)=(0,2),\qquad
[T(e_2)]_{\mathcal D}
=
\begin{pmatrix}
1\\
-1
\end{pmatrix},
```

and

```math
T(e_3)=(1,-1),\qquad
[T(e_3)]_{\mathcal D}
=
\begin{pmatrix}
0\\
1
\end{pmatrix}.
```

Therefore

```math
[T]_{\mathcal D\leftarrow\mathcal B}
=
\begin{pmatrix}
\tfrac12&1&0\\
\tfrac12&-1&1
\end{pmatrix}.
```

Nothing requires the domain and codomain to have the same dimension. The matrix has $m$ rows and $n$ columns because $T:F^n\to F^m$ after coordinates are chosen.

## 6. Change-of-Coordinate Matrices

Let $\mathcal B$ and $\mathcal B'$ be ordered bases of $V$. Define

```math
P_{\mathcal B\leftarrow\mathcal B'}
=\phi_{\mathcal B}\circ\phi_{\mathcal B'}^{-1}.
```

It converts $\mathcal B'$-coordinates into $\mathcal B$-coordinates:

```math
[v]_{\mathcal B}
=P_{\mathcal B\leftarrow\mathcal B'}[v]_{\mathcal B'}.
```

Its columns are

```math
P_{\mathcal B\leftarrow\mathcal B'}
=
\begin{bmatrix}
[v_1']_{\mathcal B}&\cdots&[v_n']_{\mathcal B}
\end{bmatrix}.
```

Reversing the direction gives the inverse matrix:

```math
P_{\mathcal B'\leftarrow\mathcal B}
=P_{\mathcal B\leftarrow\mathcal B'}^{-1}.
```

Writing the direction in the subscript prevents the most common inverse error.

## 7. General Change-of-Basis Formula

Suppose

- $\mathcal B$ and $\mathcal B'$ are old and new bases of $V$;
- $\mathcal D$ and $\mathcal D'$ are old and new bases of $W$.

Starting with $[v]_{\mathcal B'}$:

1. convert it to old domain coordinates with $P_{\mathcal B\leftarrow\mathcal B'}$;
2. apply the old matrix $[T]_{\mathcal D\leftarrow\mathcal B}$;
3. convert the result to new codomain coordinates with $P_{\mathcal D'\leftarrow\mathcal D}$.

Therefore

```math
[T]_{\mathcal D'\leftarrow\mathcal B'}
=
P_{\mathcal D'\leftarrow\mathcal D}
[T]_{\mathcal D\leftarrow\mathcal B}
P_{\mathcal B\leftarrow\mathcal B'}.
```

The order is forced by function composition: the rightmost matrix acts first.

## 8. Similarity and Conjugation

Now suppose $T:V\to V$, and use the same basis in the domain and codomain. Let

```math
A=[T]_{\mathcal B},\qquad A'=[T]_{\mathcal B'}.
```

Set

```math
P=P_{\mathcal B\leftarrow\mathcal B'}.
```

The general formula becomes

```math
A'=P^{-1}AP.
```

Thus $A$ and $A'$ are similar, or conjugate, matrices. They represent the same abstract endomorphism in different coordinate systems.

Some texts define $P$ in the reverse direction. Their formula is $A'=PAP^{-1}$. Both conventions are correct when the direction of $P$ is stated explicitly.

## 9. What Similarity Preserves

Because similar matrices represent the same operator, they have the same basis-independent data:

- rank and nullity;
- determinant and trace;
- characteristic polynomial;
- eigenvalues over the chosen field;
- minimal polynomial;
- diagonalizability and Jordan-block structure, when applicable.

The individual entries and columns generally change.

## 10. Common Misconceptions

### “The matrix is the transformation.”

False. The transformation is abstract; the matrix depends on selected bases.

### “Changing basis changes the transformation.”

False. It changes only the numerical description.

### “A linear transformation has one matrix.”

False. Each ordered pair of domain and codomain bases gives a matrix representation.

### “The change-of-basis matrix always goes on the same side.”

False. Domain-coordinate changes act on the right, while codomain-coordinate changes act on the left.

## 11. Practical Checklist

When solving a change-of-basis problem:

1. state the old and new bases of each space;
2. state the direction of every change-of-coordinate matrix;
3. place coordinate vectors in columns;
4. confirm matrix dimensions before multiplying;
5. read compositions from right to left;
6. test the final formula on at least one basis vector.

## Summary

| Object | Basis-dependent? |
|---|---|
| Abstract vector | No |
| Linear transformation | No |
| Coordinate column | Yes |
| Matrix representation | Yes |
| Change-of-coordinate matrix | Yes |

The general identity

```math
[T]_{\mathcal D'\leftarrow\mathcal B'}
=
P_{\mathcal D'\leftarrow\mathcal D}
[T]_{\mathcal D\leftarrow\mathcal B}
P_{\mathcal B\leftarrow\mathcal B'}
```

contains the usual change-of-basis and similarity formulas as special cases.
