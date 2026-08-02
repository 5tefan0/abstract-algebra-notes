# Lecture 11 — Rank–Nullity, Matrix Representations, and Simple Forms

Let $`V`$ and $`W`$ be finite-dimensional vector spaces over a field $`F`$, and let $`T:V\to W`$ be linear.

## 1. Differentiation as a Linear Operator

Let

```math
V=F[x]_{\leq n},\qquad W=F[x]_{\leq n-1}.
```

Formal differentiation defines a linear map

```math
D:V\to W,\qquad
D\left(\sum_{k=0}^n a_kx^k\right)=\sum_{k=1}^n ka_kx^{k-1}.
```

It is linear because

```math
D(f+g)=D(f)+D(g),\qquad D(cf)=cD(f).
```

Over a field of characteristic $`0`$, $`D`$ is surjective and

```math
\ker D=F,
```

the one-dimensional space of constant polynomials.

Over $`F=\mathbb{F}_p`$, new phenomena occur. Since $`p=0`$ in the field,

```math
D(x^p)=px^{p-1}=0.
```

If $`n\geq p`$, the kernel therefore contains both $`1`$ and $`x^p`$, and $`x^{p-1}`$ is not in the image. This is a first warning that familiar real-linear statements involving integer coefficients can change in positive characteristic.

## 2. The Rank–Nullity Theorem

**Theorem.** For every linear map $`T:V\to W`$,

```math
\dim V=\dim\ker T+\dim\operatorname{Im}T.
```

The two terms on the right are called the **nullity** and **rank** of $`T`$:

```math
\operatorname{nullity}(T)=\dim\ker T,\qquad
\operatorname{rank}(T)=\dim\operatorname{Im}T.
```

### Proof by an Adapted Basis

Choose a basis

```math
v_1,\ldots,v_k
```

of $`\ker T`$ and extend it to a basis

```math
v_1,\ldots,v_k,v_{k+1},\ldots,v_n
```

of $`V`$. We claim

```math
T(v_{k+1}),\ldots,T(v_n)
```

is a basis of $`\operatorname{Im}T`$.

**Spanning.** If $`y=T(v)`$, expand

```math
v=\sum_{i=1}^k a_iv_i+\sum_{i=k+1}^n b_iv_i.
```

Then

```math
y=T(v)=\sum_{i=k+1}^n b_iT(v_i),
```

because $`T(v_i)=0`$ for $`i\leq k`$.

**Independence.** Suppose

```math
\sum_{i=k+1}^n b_iT(v_i)=0.
```

Then $`v_0=\sum_{i=k+1}^n b_iv_i`$ lies in $`\ker T`$, so it is also a linear combination of $`v_1,\ldots,v_k`$. Subtracting the two expansions gives a relation among the basis vectors of $`V`$, forcing every $`b_i=0`$.

Thus $`\dim\ker T=k`$, $`\dim\operatorname{Im}T=n-k`$, and the formula follows. $`\square`$

## 3. Consequences of Rank–Nullity

If $`\dim V=\dim W<\infty`$, then the following are equivalent:

- $`T`$ is injective.
- $`\ker T=\{0\}`$.
- $`T`$ is surjective.
- $`\operatorname{Im}T=W`$.
- $`T`$ is an isomorphism.

For the quotient projection $`\pi:V\to V/U`$, rank–nullity gives

```math
\dim V=\dim U+\dim(V/U).
```

For differentiation $`D:F[x]_{\leq n}\to F[x]_{\leq n-1}`$ in characteristic $`0`$,

```math
n+1=1+n,
```

matching its one-dimensional kernel and $`n`$-dimensional image.

## 4. A Linear Map Is Determined by Its Values on a Basis

Choose bases

```math
\mathcal B=(v_1,\ldots,v_n)\quad\text{of }V,
\qquad
\mathcal C=(w_1,\ldots,w_m)\quad\text{of }W.
```

Write

```math
T(v_j)=\sum_{i=1}^m a_{ij}w_i.
```

The matrix

```math
A=[T]_{\mathcal C\leftarrow\mathcal B}=(a_{ij})
```

has the coordinates of $`T(v_j)`$ in its $`j`$th column. If

```math
v=\sum_{j=1}^n x_jv_j,\qquad
T(v)=\sum_{i=1}^m y_iw_i,
```

then

```math
\begin{pmatrix}y_1\\ \vdots\\ y_m\end{pmatrix}
=A
\begin{pmatrix}x_1\\ \vdots\\ x_n\end{pmatrix}.
```

### Example

Suppose

```math
T(v_1)=2w_1,\qquad T(v_2)=3w_1+4w_2.
```

Then

```math
[T]_{\mathcal C\leftarrow\mathcal B}
=\begin{pmatrix}2&3\\0&4\end{pmatrix}.
```

For $`v=7v_1+8v_2`$,

```math
\begin{pmatrix}2&3\\0&4\end{pmatrix}
\begin{pmatrix}7\\8\end{pmatrix}
=\begin{pmatrix}38\\32\end{pmatrix},
```

so $`T(v)=38w_1+32w_2`$.

## 5. Endomorphisms and Composition

An **endomorphism** is a linear map $`T:V\to V`$. After choosing one basis $`\mathcal B`$ for both copies of $`V`$, it is represented by a square matrix $`[T]_{\mathcal B}`$.

If $`S,T\in\operatorname{End}_F(V)`$, then

```math
[S\circ T]_{\mathcal B}=[S]_{\mathcal B}[T]_{\mathcal B}.
```

This explains both the definition and associativity of matrix multiplication: matrices multiply as they do so that they faithfully represent composition of linear operators.

## 6. Equivalent Tests for Invertibility

Let $`T:V\to V`$, where $`\dim V=n`$, and let $`A=[T]_{\mathcal B}`$. The following are equivalent:

1. $`T`$ is an automorphism.
2. $`\ker T=\{0\}`$.
3. $`\operatorname{Im}T=V`$.
4. $`A`$ is invertible.
5. $`\det A\neq0`$ in $`F`$.

The equivalence of injectivity and surjectivity uses equal finite dimensions. The equivalence with matrix invertibility comes from the compatibility of matrices with composition, while the determinant criterion is the standard matrix theorem.

Hence, after choosing a basis,

```math
\mathrm{GL}(V)\cong\mathrm{GL}_n(F).
```

## 7. Example: $`\mathrm{GL}_2(\mathbb{F}_2)\cong S_3`$

The vector space $`\mathbb{F}_2^2`$ has four vectors:

```math
(0,0),\quad(1,0),\quad(0,1),\quad(1,1).
```

An invertible linear map fixes $`(0,0)`$ and permutes the three nonzero vectors. This gives a homomorphism

```math
\mathrm{GL}_2(\mathbb{F}_2)\longrightarrow S_3.
```

It is injective because a linear map is determined by its action on the vectors of the space. Also,

```math
|\mathrm{GL}_2(\mathbb{F}_2)|=(2^2-1)(2^2-2)=3\cdot2=6.
```

Indeed, the first matrix column may be any nonzero vector, and the second may be any vector outside its one-dimensional span. Since both groups have order $`6`$, the injection is an isomorphism:

```math
\mathrm{GL}_2(\mathbb{F}_2)\cong S_3.
```

This is a concrete bridge between finite linear groups and permutation groups.

## 8. Change of Basis and Conjugation

If $`A`$ and $`A'`$ represent the same endomorphism in two bases, then

```math
A'=P^{-1}AP
```

for an invertible change-of-coordinate matrix $`P`$. Thus basis-independent properties of $`T`$ must be invariant under matrix conjugation. Examples include:

- determinant,
- trace,
- rank and nullity,
- characteristic polynomial,
- diagonalizability.

The point of changing basis is to find a conjugate matrix whose form makes the operator easier to understand.

## 9. Rank Normal Form

Let $`r=\operatorname{rank}T`$. There are bases of $`V`$ and $`W`$, chosen independently, for which

```math
[T]=
\begin{pmatrix}
I_r&0\\
0&0
\end{pmatrix}.
```

To construct them, choose a basis of $`\ker T`$, extend it by vectors $`u_1,\ldots,u_r`$, and use

```math
T(u_1),\ldots,T(u_r)
```

as the first $`r`$ vectors of a basis of $`W`$. In these adapted bases, $`T`$ is the identity on a complement of its kernel and zero on the kernel.

This form classifies linear maps up to independent changes of basis in the domain and codomain: two matrices are equivalent in this sense exactly when they have the same rank.

For an endomorphism $`T:V\to V`$, however, the domain and codomain basis must change together, so only conjugation is allowed. Finding the best form under this stricter equivalence leads to invariant subspaces, eigenvectors, diagonalization, and eventually canonical forms.
