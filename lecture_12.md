# Lecture 12 — Invariant Subspaces, Eigenvalues, and the Characteristic Polynomial

Let $V$ be an $n$-dimensional vector space over a field $F$, and let $T:V\to V$ be a linear operator.

## 1. Invariant Subspaces and Block Matrices

**Definition.** A subspace $W\leq V$ is **$T$-invariant** if

```math
T(W)\subseteq W.
```

Choose a basis $w_1,\ldots,w_r$ of $W$ and extend it to a basis of $V$. Since each $T(w_j)$ lies in $W$, the matrix of $T$ has block upper-triangular form

```math
[T]=
\begin{pmatrix}
A&B\\
0&D
\end{pmatrix}.
```

If $W$ has a $T$-invariant complement $W'$ so that

```math
V=W\oplus W',
```

then choosing a basis of $W$ followed by a basis of $W'$ gives the block diagonal form

```math
[T]=
\begin{pmatrix}
A&0\\
0&D
\end{pmatrix}.
```

Every subspace has a vector-space complement, but an invariant subspace need not have an invariant complement. That extra requirement is exactly what can fail in diagonalization problems.

## 2. Eigenvectors and Eigenvalues

A one-dimensional subspace $Fw$ with $w\neq0$ is $T$-invariant exactly when

```math
T(w)=\lambda w
```

for some $\lambda\in F$.

**Definition.** A nonzero vector $w$ satisfying this equation is an **eigenvector** of $T$, and $\lambda$ is its **eigenvalue**. The corresponding **eigenspace** is

```math
E_\lambda(T)=\ker(T-\lambda I).
```

Every nonzero vector in $E_\lambda(T)$ is an eigenvector with eigenvalue $\lambda$.

If $V$ has a basis $v_1,\ldots,v_n$ of eigenvectors, with

```math
T(v_i)=\lambda_iv_i,
```

then

```math
[T]_{(v_1,\ldots,v_n)}=
\begin{pmatrix}
\lambda_1&&0\\
&\ddots&\\
0&&\lambda_n
\end{pmatrix}.
```

Such an operator is **diagonalizable over $F$**. Equivalently, $V$ is a direct sum of eigenspaces.

## 3. Two Ways Diagonalization Can Fail

### A Rotation over $\mathbb R$

Rotation of $\mathbb R^2$ through an angle $\theta$ has standard matrix

```math
R_\theta=
\begin{pmatrix}
\cos\theta&-\sin\theta\\
\sin\theta&\cos\theta
\end{pmatrix}.
```

If $\theta\not\equiv0,\pi\pmod{2\pi}$, no real line is invariant, so there are no real eigenvectors. The same operator has complex eigenvalues $e^{\pm i\theta}$ after the scalar field is enlarged to $\mathbb C$.

### An Invariant Line without an Invariant Complement

Over any field, define

```math
T(e_1)=e_1,\qquad T(e_2)=e_1+e_2.
```

Its matrix is

```math
A=\begin{pmatrix}1&1\\0&1\end{pmatrix}.
```

The line $Fe_1$ is invariant. If $v=ae_1+be_2$ is an eigenvector with eigenvalue $\lambda$, then

```math
T(v)=(a+b)e_1+be_2=\lambda ae_1+\lambda be_2.
```

Thus

```math
a+b=\lambda a,\qquad b=\lambda b.
```

If $b\neq0$, then $\lambda=1$, and the first equation forces $b=0$, a contradiction. Hence every eigenvector lies in $Fe_1$. There is only one independent eigenvector, so no basis of eigenvectors exists.

These examples show two different obstructions:

- the characteristic polynomial may not split over the field;
- it may split but have eigenspaces too small to span $V$.

## 4. Detecting Eigenvalues by Invertibility

For $\lambda\in F$,

```math
T(w)=\lambda w
\iff
(T-\lambda I)w=0.
```

Therefore

```math
\lambda\text{ is an eigenvalue}
\iff
\ker(T-\lambda I)\neq\{0\}
\iff
T-\lambda I\text{ is not invertible}.
```

Choose a basis of $V$ and let $A$ be the matrix of $T$. Then

```math
\lambda\text{ is an eigenvalue}
\iff
\det(A-\lambda I)=0
\iff
\det(\lambda I-A)=0.
```

## 5. The Characteristic Polynomial

**Definition.** The **characteristic polynomial** of $T$ is

```math
\chi_T(t)=\det(tI-A),
```

where $A$ is the matrix of $T$ in any basis.

This is a monic polynomial of degree $n$. Its roots in $F$ are precisely the eigenvalues of $T$.

For a general $2\times2$ matrix

```math
A=\begin{pmatrix}a&b\\c&d\end{pmatrix},
```

one obtains

```math
\chi_A(t)=t^2-(a+d)t+(ad-bc)
=t^2-\operatorname{tr}(A)t+\det(A).
```

In general, the coefficient of $t^{n-1}$ is $-\operatorname{tr}(A)$ and the constant term is $(-1)^n\det(A)$.

## 6. Why the Characteristic Polynomial Is Basis-Independent

If a change of basis replaces $A$ by

```math
A'=P^{-1}AP,
```

then

```math
\begin{aligned}
\det(tI-A')
&=\det(tI-P^{-1}AP)\\
&=\det\bigl(P^{-1}(tI-A)P\bigr)\\
&=\det(P^{-1})\det(tI-A)\det(P)\\
&=\det(tI-A).
\end{aligned}
```

Thus $\chi_T(t)$ depends only on the abstract operator $T$, not on the coordinates used to compute it. This is a central theme: similarity changes the matrix but preserves the operator's structural invariants.

## 7. A Polynomial over a Field Has at Most Its Degree Many Roots

**Lemma.** A nonzero polynomial $f(t)\in F[t]$ of degree $n$ has at most $n$ distinct roots in $F$.

**Proof.** If $c$ is a root, division by $t-c$ gives

```math
f(t)=(t-c)g(t),
```

where $\deg g=n-1$. If $c'\neq c$ is another root, then

```math
0=f(c')=(c'-c)g(c').
```

Since $F$ is a field and $c'-c\neq0$, cancellation gives $g(c')=0$. Induction on the degree completes the proof. $\square$

Therefore an operator on an $n$-dimensional vector space has at most $n$ distinct eigenvalues.

The field hypothesis matters. In the ring $\mathbb Z/8\mathbb Z$, the degree-two polynomial $t^2-1$ has four roots:

```math
\bar1,\bar3,\bar5,\bar7.
```

Cancellation fails because the ring has zero divisors.

## 8. Examples of Characteristic Polynomials

For a real rotation,

```math
\chi_{R_\theta}(t)=t^2-2\cos\theta\,t+1.
```

Its discriminant is

```math
4\cos^2\theta-4=-4\sin^2\theta.
```

When $\theta\not\equiv0,\pi$, this is negative, so the polynomial has no real roots and the rotation has no real eigenvalues.

For the non-diagonalizable matrix

```math
A=\begin{pmatrix}1&1\\0&1\end{pmatrix},
```

```math
\chi_A(t)=(t-1)^2.
```

The polynomial splits, but the eigenspace

```math
E_1(A)=\ker(A-I)=Fe_1
```

has dimension only $1$. Algebraic multiplicity $2$ does not force two independent eigenvectors.

## 9. Distinct Eigenvalues Give Independent Eigenvectors

**Theorem.** Eigenvectors belonging to distinct eigenvalues are linearly independent.

**Proof.** Let $v_1,\ldots,v_r$ have distinct eigenvalues $\lambda_1,\ldots,\lambda_r$, and suppose a shortest nontrivial relation exists:

```math
a_1v_1+\cdots+a_rv_r=0.
```

Apply $T-\lambda_rI$:

```math
a_1(\lambda_1-\lambda_r)v_1+\cdots
+a_{r-1}(\lambda_{r-1}-\lambda_r)v_{r-1}=0.
```

This is a shorter relation. By minimality, each coefficient is zero. Since the eigenvalues are distinct, each $\lambda_i-\lambda_r$ is nonzero and invertible, so $a_i=0$ for $i<r$. The original relation then gives $a_r=0$, a contradiction. $\square$

**Corollary.** If $\chi_T(t)$ splits in $F[t]$ into $n$ distinct linear factors,

```math
\chi_T(t)=\prod_{i=1}^n(t-\lambda_i),
```

then choosing one eigenvector for each $\lambda_i$ gives a basis of $V$. Hence $T$ is diagonalizable.

This is sufficient but not necessary: the identity operator is diagonalizable although its characteristic polynomial $(t-1)^n$ has a repeated root.

## 10. The Cayley–Hamilton Theorem

The space $\operatorname{End}_F(V)$ has dimension $n^2$. Therefore the $n^2+1$ operators

```math
I,T,T^2,\ldots,T^{n^2}
```

are linearly dependent. It follows that $T$ satisfies some nonzero polynomial of degree at most $n^2$.

The much stronger result is:

**Theorem (Cayley–Hamilton).** Every linear operator satisfies its own characteristic polynomial:

```math
\chi_T(T)=0.
```

Here polynomial evaluation takes place in the algebra $\operatorname{End}_F(V)$: the scalar term is multiplied by $I$, multiplication is composition, and $0$ is the zero operator.

For a $2\times2$ matrix, Cayley–Hamilton reads

```math
A^2-\operatorname{tr}(A)A+\det(A)I=0.
```

When $\chi_T$ has $n$ distinct roots, the theorem is easy to see in an eigenbasis: $T$ becomes diagonal, and substituting each diagonal entry $\lambda_i$ into $\chi_T$ gives zero. The general theorem remains true even when the polynomial has repeated roots or does not split over $F$.

Cayley–Hamilton links polynomial algebra to operator theory and leads naturally to the minimal polynomial, canonical forms, and a deeper analysis of diagonalizability.
