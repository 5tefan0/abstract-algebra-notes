# Change-of-Basis Matrices and Linear Transformations

## Summary

A **change-of-basis matrix** converts the coordinate column of a vector from one ordered basis to another.

More generally, if

$$T:V\longrightarrow W$$

is linear, its matrix depends on two choices: a basis of the domain $V$ and a basis of the codomain $W$. Changing either basis changes the matrix representation, even though the underlying linear transformation stays the same.

Throughout, all vector spaces are over a fixed field $F$.

## 1. Coordinates Depend on the Basis

Let $V$ be $n$-dimensional, and choose an ordered basis

$$\mathcal B=(v_1,\ldots,v_n).$$

Every $v\in V$ can be written uniquely as

$$v=a_1v_1+\cdots+a_nv_n.$$

Its coordinate column relative to $\mathcal B$ is

$$
[v]_{\mathcal B}
=
\begin{pmatrix}
a_1\\
\vdots\\
a_n
\end{pmatrix}.
$$

The coordinate column is not the vector itself. It records the coefficients of the vector relative to a particular basis.

## 2. Two Different Bases

Let

$$\mathcal C=(w_1,\ldots,w_n)$$

be another ordered basis of $V$. The same vector has a second coordinate column, $[v]_{\mathcal C}$.

There is a unique invertible matrix

$$P_{\mathcal C\leftarrow\mathcal B}$$

such that

$$
[v]_{\mathcal C}
=P_{\mathcal C\leftarrow\mathcal B}[v]_{\mathcal B}
$$

for every $v\in V$. It is the change-of-coordinate matrix **from $\mathcal B$-coordinates to $\mathcal C$-coordinates**.

The arrow in the subscript records the direction:

$$
\mathcal B\text{-coordinates}
\xrightarrow{\;P_{\mathcal C\leftarrow\mathcal B}\;}
\mathcal C\text{-coordinates}.
$$

## 3. Constructing the Matrix

To construct $P_{\mathcal C\leftarrow\mathcal B}$, express each vector of $\mathcal B$ in the basis $\mathcal C$. These coordinate columns become the columns of the matrix:

$$
P_{\mathcal C\leftarrow\mathcal B}
=
\begin{pmatrix}
|&&|\\
[v_1]_{\mathcal C}&\cdots&[v_n]_{\mathcal C}\\
|&&|
\end{pmatrix}.
$$

Why does this work? If

$$v=a_1v_1+\cdots+a_nv_n,$$

then

$$
\begin{aligned}
P_{\mathcal C\leftarrow\mathcal B}[v]_{\mathcal B}
&=
P_{\mathcal C\leftarrow\mathcal B}
\begin{pmatrix}
a_1\\
\vdots\\
a_n
\end{pmatrix}\\
&=
a_1[v_1]_{\mathcal C}
+\cdots+
a_n[v_n]_{\mathcal C}\\
&=[v]_{\mathcal C}.
\end{aligned}
$$

The reverse change is the inverse matrix:

$$
P_{\mathcal B\leftarrow\mathcal C}
=P_{\mathcal C\leftarrow\mathcal B}^{-1}.
$$

## 4. Example: Changing Coordinates

In $\mathbb R^2$, let

$$
\mathcal B=
\left(
\begin{pmatrix}1\\0\end{pmatrix},
\begin{pmatrix}0\\1\end{pmatrix}
\right)
$$

be the standard basis, and let

$$
\mathcal C=
\left(
\begin{pmatrix}1\\1\end{pmatrix},
\begin{pmatrix}1\\-1\end{pmatrix}
\right).
$$

Since

$$
\begin{pmatrix}1\\0\end{pmatrix}
=
\frac12
\begin{pmatrix}1\\1\end{pmatrix}
+
\frac12
\begin{pmatrix}1\\-1\end{pmatrix},
$$

and

$$
\begin{pmatrix}0\\1\end{pmatrix}
=
\frac12
\begin{pmatrix}1\\1\end{pmatrix}
-
\frac12
\begin{pmatrix}1\\-1\end{pmatrix},
$$

we have

$$
[e_1]_{\mathcal C}
=
\begin{pmatrix}\tfrac12\\\tfrac12\end{pmatrix},
\qquad
[e_2]_{\mathcal C}
=
\begin{pmatrix}\tfrac12\\-\tfrac12\end{pmatrix}.
$$

Therefore

$$
P_{\mathcal C\leftarrow\mathcal B}
=
\begin{pmatrix}
\tfrac12&\tfrac12\\
\tfrac12&-\tfrac12
\end{pmatrix}.
$$

For example, if $v=(4,2)$, then

$$
[v]_{\mathcal C}
=
P_{\mathcal C\leftarrow\mathcal B}[v]_{\mathcal B}
=
\begin{pmatrix}
\tfrac12&\tfrac12\\
\tfrac12&-\tfrac12
\end{pmatrix}
\begin{pmatrix}4\\2\end{pmatrix}
=
\begin{pmatrix}3\\1\end{pmatrix}.
$$

Indeed,

$$
(4,2)=3(1,1)+1(1,-1).
$$

## 5. Matrix of a Linear Transformation

Let

$$T:V\longrightarrow W,$$

and choose ordered bases

$$\mathcal B=(v_1,\ldots,v_n)\quad\text{of }V,$$

$$\mathcal D=(w_1,\ldots,w_m)\quad\text{of }W.$$

The matrix representation is denoted

$$[T]_{\mathcal D\leftarrow\mathcal B}.$$

It is characterized by

$$
[T(v)]_{\mathcal D}
=[T]_{\mathcal D\leftarrow\mathcal B}[v]_{\mathcal B}
$$

for every $v\in V$.

To compute it, write each image $T(v_j)$ in the basis $\mathcal D$:

$$
[T]_{\mathcal D\leftarrow\mathcal B}
=
\begin{pmatrix}
|&&|\\
[T(v_1)]_{\mathcal D}&\cdots&[T(v_n)]_{\mathcal D}\\
|&&|
\end{pmatrix}.
$$

The domain basis determines the columns to which $T$ is applied; the codomain basis determines how those image vectors are recorded.

## 6. Example: A Nonstandard Domain and Codomain Basis

Define

$$T:\mathbb R^2\longrightarrow\mathbb R^2,\qquad
T(x,y)=(x+y,\,2x-y).$$

Choose

$$
\mathcal B=\bigl((1,1),(1,-1)\bigr)
$$

for the domain and

$$
\mathcal D=\bigl((1,0),(1,1)\bigr)
$$

for the codomain.

First,

$$T(1,1)=(2,1)=1(1,0)+1(1,1),$$

so

$$
[T(1,1)]_{\mathcal D}
=
\begin{pmatrix}1\\1\end{pmatrix}.
$$

Next,

$$T(1,-1)=(0,3)=-3(1,0)+3(1,1),$$

so

$$
[T(1,-1)]_{\mathcal D}
=
\begin{pmatrix}-3\\3\end{pmatrix}.
$$

Therefore

$$
[T]_{\mathcal D\leftarrow\mathcal B}
=
\begin{pmatrix}
1&-3\\
1&3
\end{pmatrix}.
$$

## 7. Changing Both Bases

Suppose $[T]_{\mathcal D\leftarrow\mathcal B}$ is known, and we switch to

- a new domain basis $\mathcal B'$;
- a new codomain basis $\mathcal D'$.

The new matrix is

$$
[T]_{\mathcal D'\leftarrow\mathcal B'}
=
P_{\mathcal D'\leftarrow\mathcal D}
[T]_{\mathcal D\leftarrow\mathcal B}
P_{\mathcal B\leftarrow\mathcal B'}.
$$

Reading from right to left:

1. $P_{\mathcal B\leftarrow\mathcal B'}$ converts new input coordinates to old input coordinates;
2. $[T]_{\mathcal D\leftarrow\mathcal B}$ applies $T$ in the old coordinates;
3. $P_{\mathcal D'\leftarrow\mathcal D}$ converts old output coordinates to new output coordinates.

Thus:

- changing the domain basis acts on the right;
- changing the codomain basis acts on the left.

## 8. Endomorphisms and Similarity

If $T:V\to V$, use one basis for both the domain and codomain. Let

$$A=[T]_{\mathcal B},\qquad A'=[T]_{\mathcal B'}.$$

If

$$P=P_{\mathcal B\leftarrow\mathcal B'},$$

then

$$A'=P^{-1}AP.$$

The matrices $A$ and $A'$ are **similar**. They describe the same linear operator in different bases.

If a source defines $P$ in the reverse direction, its formula will appear as $A'=PAP^{-1}$. Always determine what coordinate conversion $P$ performs before using a memorized formula.

## 9. Conceptual Picture

The complete process is

$$
V
\xrightarrow{\;\text{coordinates in }\mathcal B\;}
F^n
\xrightarrow{\;[T]_{\mathcal D\leftarrow\mathcal B}\;}
F^m
\xrightarrow{\;\text{interpret in }\mathcal D\;}
W.
$$

The abstract vector spaces and the transformation do not change. Only their coordinate descriptions depend on the selected bases.

## Key Takeaways

1. Coordinates depend on an ordered basis.
2. The columns of a change-of-basis matrix are basis vectors expressed in the target coordinate system.
3. The columns of a transformation matrix are images of domain basis vectors expressed in the codomain basis.
4. Change-of-basis directions determine where inverses appear.
5. Similar matrices represent the same endomorphism in different bases.
