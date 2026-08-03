# Lecture 10 — Direct Sums, Matrices, and Change of Basis

Let $`V`$ be a finite-dimensional vector space over a field $`F`$.

## 1. Complements and Direct Sums

Start with a linearly independent list $`v_1,\ldots,v_n`$ and extend it to a basis

```math
v_1,\ldots,v_n,v_{n+1},\ldots,v_m
```

of $`V`$. Define

```math
W=\mathrm{span}(v_1,\ldots,v_n),\qquad
W'=\mathrm{span}(v_{n+1},\ldots,v_m).
```

Then

```math
W\cap W'=\{0\}.
```

Indeed, if $`w=w'`$ with $`w\in W`$ and $`w'\in W'`$, subtracting their basis expansions gives a linear relation among the full basis. Every coefficient must therefore be zero.

Every vector in $`V`$ is a sum of an element of $`W`$ and an element of $`W'`$, because the full list spans $`V`$. The expression is unique because the intersection is zero. Hence

```math
V=W\oplus W'.
```

Equivalently, the map

```math
W\times W'\longrightarrow V,\qquad (w,w')\longmapsto w+w'
```

is a linear isomorphism.

**Definition.** $`V=W\oplus W'`$ means both

```math
V=W+W'\qquad\text{and}\qquad W\cap W'=\{0\}.
```

The first condition gives existence of a decomposition; the second gives uniqueness.

## 2. Every Subspace Has a Complement

Let $`W\leq V`$. Choose a basis $`v_1,\ldots,v_n`$ of $`W`$ and extend it to a basis

```math
v_1,\ldots,v_n,v_{n+1},\ldots,v_m
```

of $`V`$. Then

```math
W'=\mathrm{span}(v_{n+1},\ldots,v_m)
```

is a complement and $`V=W\oplus W'`$.

If $`\pi:V\to V/W`$ is the quotient map, its restriction

```math
\pi|_{W'}:W'\xrightarrow{\sim}V/W
```

is an isomorphism. Consequently,

```math
V\cong W\oplus(V/W)
```

and

```math
\dim V=\dim W+\dim(V/W).
```

The complement $`W'`$ is usually not canonical: a different extension of the basis of $`W`$ can produce a different complement.

## 3. Splitting a Linear Map

Let $`T:V\to U`$ be linear. The First Isomorphism Theorem gives

```math
V/\ker T\cong\mathrm{Im}T.
```

Choose a complement $`C`$ of $`\ker T`$:

```math
V=\ker T\oplus C.
```

Then the restriction

```math
T|_C:C\xrightarrow{\sim}\mathrm{Im}T
```

is an isomorphism. Therefore, noncanonically,

```math
V\cong\ker T\oplus\mathrm{Im}T
```

and

```math
\dim V=\dim\ker T+\dim\mathrm{Im}T.
```

The dimension identity is the **rank–nullity theorem**. The splitting itself depends on a choice of complement.

This is much stronger than the corresponding statement for arbitrary groups. A short exact sequence of vector spaces always splits, whereas a short exact sequence of groups need not.

## 4. Bases as Coordinate Isomorphisms

Let $`\mathcal B=(v_1,\ldots,v_n)`$ be an ordered basis of $`V`$. Define

```math
\rho_{\mathcal B}:F^n\longrightarrow V,\qquad
\begin{pmatrix}a_1\\ \vdots\\ a_n\end{pmatrix}
\longmapsto \sum_{i=1}^n a_iv_i.
```

This is a linear isomorphism. Conversely, any isomorphism $`\rho:F^n\to V`$ determines the ordered basis

```math
\bigl(\rho(e_1),\ldots,\rho(e_n)\bigr),
```

where $`e_1,\ldots,e_n`$ is the standard basis of $`F^n`$. Thus ordered bases of $`V`$ correspond bijectively to isomorphisms $`F^n\to V`$.

The inverse $`\rho_{\mathcal B}^{-1}`$ is the coordinate map $`v\mapsto[v]_{\mathcal B}`$.

## 5. Linear Maps and Matrices

Linear maps $`F^n\to F^m`$ correspond bijectively to $`m\times n`$ matrices over $`F`$.

If $`S:F^n\to F^m`$ is linear, its matrix is

```math
[S]=\begin{bmatrix}S(e_1)&\cdots&S(e_n)\end{bmatrix}.
```

The $`j`$th column is $`S(e_j)`$. Conversely, a matrix $`A\in M_{m\times n}(F)`$ defines the map

```math
x\longmapsto Ax.
```

The correspondence respects the algebraic operations:

```math
[aS+bT]=a[S]+b[T],
```

and, whenever the composition is defined,

```math
[S\circ T]=[S][T].
```

Matrix multiplication is therefore the coordinate expression of composition of linear maps. Its associativity reflects the associativity of composition.

## 6. The Matrix of an Abstract Linear Map

Let $`T:V\to W`$, with ordered bases

```math
\mathcal B=(v_1,\ldots,v_n),\qquad
\mathcal C=(w_1,\ldots,w_m).
```

The matrix of $`T`$ with respect to these bases is

```math
[T]_{\mathcal C\leftarrow\mathcal B}
=\rho_{\mathcal C}^{-1}\,T\,\rho_{\mathcal B}\in M_{m\times n}(F).
```

If

```math
T(v_j)=\sum_{i=1}^m a_{ij}w_i,
```

then

```math
[T]_{\mathcal C\leftarrow\mathcal B}=(a_{ij}).
```

Thus the $`j`$th column contains the $`\mathcal C`$-coordinates of $`T(v_j)`$. For every $`v\in V`$,

```math
[T(v)]_{\mathcal C}
=[T]_{\mathcal C\leftarrow\mathcal B}[v]_{\mathcal B}.
```

After bases are fixed, the vector space $`\mathrm{Hom}_F(V,W)`$ is identified with $`M_{m\times n}(F)`$.

## 7. Composition in Coordinates

Suppose

```math
V\xrightarrow{T}W\xrightarrow{S}X
```

and choose bases $`\mathcal B,\mathcal C,\mathcal D`$ of the three spaces. Then

```math
[S\circ T]_{\mathcal D\leftarrow\mathcal B}
=[S]_{\mathcal D\leftarrow\mathcal C}
[T]_{\mathcal C\leftarrow\mathcal B}.
```

The order matters: $`T`$ acts first, so its matrix appears on the right.

Under the same dictionary:

- $`\ker T`$ corresponds to the nullspace of the matrix.
- $`\mathrm{Im}T`$ corresponds, in target coordinates, to the column space.
- Row reduction computes bases and dimensions for these spaces.

This turns structural questions about linear maps into explicit algorithms.

## 8. Change of Basis

Let $`\mathcal B`$ and $`\mathcal B'`$ be bases of $`V`$. Define

```math
P=\rho_{\mathcal B}^{-1}\rho_{\mathcal B'}.
```

Then $`P`$ converts $`\mathcal B'`$-coordinates to $`\mathcal B`$-coordinates:

```math
[v]_{\mathcal B}=P[v]_{\mathcal B'}.
```

Its $`j`$th column is $`[v'_j]_{\mathcal B}`$.

Similarly, for bases $`\mathcal C,\mathcal C'`$ of $`W`$, let

```math
Q=\rho_{\mathcal C}^{-1}\rho_{\mathcal C'}.
```

For $`T:V\to W`$,

```math
[T]_{\mathcal C'\leftarrow\mathcal B'}
=Q^{-1}[T]_{\mathcal C\leftarrow\mathcal B}P.
```

The precise placement of inverses depends on the convention used to define a change-of-basis matrix; defining $`P`$ and $`Q`$ first removes the ambiguity.

## 9. Similarity as Conjugacy

For an endomorphism $`T:V\to V`$, use the same basis in the domain and codomain. If $`A=[T]_{\mathcal B}`$ and $`A'=[T]_{\mathcal B'}`$, then

```math
A'=P^{-1}AP.
```

Thus two matrices represent the same abstract endomorphism in different bases exactly when they are **similar**, or equivalently conjugate in $`\mathrm{GL}_n(F)`$.

This connects linear algebra directly to group theory: choosing a convenient basis means choosing a convenient representative of a conjugacy class.

## 10. The General Linear Group of a Vector Space

Define

```math
\mathrm{GL}(V)=\{T:V\to V:T\text{ is a linear isomorphism}\}.
```

It is a group under composition. If $`\dim V=n`$ and a basis $`\mathcal B`$ is chosen, the matrix map gives a group isomorphism

```math
\mathrm{GL}(V)\xrightarrow{\sim}\mathrm{GL}_n(F).
```

The abstract group $`\mathrm{GL}(V)`$ does not require a basis. The coordinate group $`\mathrm{GL}_n(F)`$ appears after a basis is chosen, and changing that basis conjugates all representing matrices simultaneously.
