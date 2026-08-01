# Lecture 9 — Span, Linear Independence, Bases, and Dimension

Throughout, let $V$ be a vector space over a fixed field $F$.

## 1. Linear Combinations and Span

Given vectors $v_1,\ldots,v_n\in V$, a **linear combination** is a vector of the form

$$a_1v_1+\cdots+a_nv_n,\qquad a_i\in F.$$

For a finite set $S=\{v_1,\ldots,v_n\}$, its **span** is

$$\operatorname{span}(S)
=\left\{\sum_{i=1}^n a_iv_i:a_i\in F\right\}.$$

The order of the vectors does not affect the span. It is a subspace because sums and scalar multiples of linear combinations are again linear combinations.

More conceptually, $\operatorname{span}(S)$ is the **smallest subspace of $V$ containing $S$**: every subspace containing the $v_i$ must contain all their linear combinations.

By convention,

$$\operatorname{span}(\varnothing)=\{0\}.$$

This makes statements about spans and bases valid even for the zero vector space.

## 2. Finite-Dimensional Vector Spaces

**Definition.** $V$ is **finite-dimensional** if some finite subset $S\subseteq V$ spans $V$.

The standard vectors

$$e_1=(1,0,\ldots,0),\quad\ldots,\quad e_n=(0,\ldots,0,1)$$

span $F^n$, because

$$ (a_1,\ldots,a_n)=a_1e_1+\cdots+a_ne_n.$$

In contrast, $F[x]$ is not finite-dimensional. Given finitely many polynomials, let $d$ be the largest of their degrees. Every linear combination of them has degree at most $d$, so they cannot span $x^{d+1}$.

The subspace

$$F[x]_{\leq d}=\{f(x)\in F[x]:\deg f\leq d\}$$

is finite-dimensional and is spanned by $1,x,\ldots,x^d$.

## 3. Linear Independence

**Definition.** A set $\{v_1,\ldots,v_n\}$ is **linearly independent** if

$$a_1v_1+\cdots+a_nv_n=0$$

implies

$$a_1=\cdots=a_n=0.$$

Otherwise the set is **linearly dependent**. A nontrivial dependence relation allows one vector with nonzero coefficient to be solved for in terms of the others. This uses the field axiom: the nonzero coefficient is invertible.

**Example.** In $\mathbb R^3$, let

$$v_1=(1,0,0),\qquad v_2=(1,1,0),\qquad v_3=(1,2,3).$$

Then

$$\operatorname{span}(v_1,v_2)=\{(a,b,0):a,b\in\mathbb R\}.$$

The three vectors are linearly independent. Indeed, the third coordinate of

$$a_1v_1+a_2v_2+a_3v_3=0$$

gives $3a_3=0$, so $a_3=0$; then the second coordinate gives $a_2=0$, and finally $a_1=0$.

This coordinate proof depends on $3\neq0$ in the scalar field. It therefore illustrates why statements over arbitrary fields must be checked against the field's characteristic.

## 4. Bases and Coordinates

**Definition.** An ordered list

$$\mathcal B=(v_1,\ldots,v_n)$$

is a **basis** of $V$ if it spans $V$ and is linearly independent.

Equivalently, every $v\in V$ has a **unique** expansion

$$v=a_1v_1+\cdots+a_nv_n.$$

Existence follows from spanning. For uniqueness, if also $v=b_1v_1+\cdots+b_nv_n$, then

$$0=(a_1-b_1)v_1+\cdots+(a_n-b_n)v_n,$$

so linear independence gives $a_i=b_i$ for every $i$.

The scalars form the coordinate vector

$$[v]_{\mathcal B}=egin{pmatrix}a_1\\ \vdots\\ a_n\end{pmatrix}\in F^n.$$

The coordinate map

$$V\longrightarrow F^n,\qquad v\longmapsto[v]_{\mathcal B}$$

is a linear isomorphism. Thus choosing a basis identifies an abstract finite-dimensional vector space with a standard coordinate space, but the identification depends on the chosen basis.

## 5. Reducing a Spanning Set to a Basis

**Theorem.** Every finite spanning set contains a basis.

**Proof.** Let $S=\{v_1,\ldots,v_n\}$ span $V$. If $S$ is linearly independent, it is already a basis. Otherwise there is a nontrivial relation

$$a_1v_1+\cdots+a_nv_n=0.$$

After reordering, assume $a_n\neq0$. Then

$$v_n=-a_n^{-1}(a_1v_1+\cdots+a_{n-1}v_{n-1}),$$

so $v_n$ lies in the span of the others and may be removed without changing the span. Repeat. Because $S$ is finite, the process terminates at a linearly independent spanning set. $\square$

This is the **pruning principle**: remove redundant vectors from a spanning set.

## 6. Extending an Independent Set to a Basis

**Theorem.** Every finite linearly independent set in a finite-dimensional vector space can be extended to a basis.

**Proof.** Let $L$ be linearly independent. If it spans $V$, it is already a basis. Otherwise choose $v\notin\operatorname{span}(L)$. Then $L\cup\{v\}$ is linearly independent: in a relation

$$a_1w_1+\cdots+a_mw_m+bv=0,$$

if $b\neq0$, then $v$ would lie in $\operatorname{span}(L)$; hence $b=0$, and then every $a_i=0$ by independence of $L$.

Choose the added vectors from a fixed finite spanning set of $V$. Repeating must eventually produce a spanning independent set. $\square$

This is the **extension principle**: add genuinely new directions to an independent set.

## 7. The Exchange Bound

**Theorem (Steinitz Exchange Bound).** If $S=\{v_1,\ldots,v_n\}$ spans $V$ and $L=\{w_1,\ldots,w_m\}$ is linearly independent, then

$$m\leq n.$$

**Idea.** Write each $w_j$ as a linear combination of the $v_i$. If $m>n$, the resulting homogeneous system has more unknown coefficients than equations, so it has a nonzero solution. That solution produces a nontrivial relation among the $w_j$, contradicting their independence.

An equivalent exchange formulation says that the independent vectors $w_1,\ldots,w_m$ can successively replace $m$ members of the spanning set while the resulting set continues to span. Hence the original spanning set must contain at least $m$ vectors.

## 8. Dimension

**Corollary.** Any two bases of a finite-dimensional vector space have the same number of elements.

If $\mathcal B$ and $\mathcal C$ are bases, apply the exchange bound first with $\mathcal B$ spanning and $\mathcal C$ independent, and then with their roles reversed:

$$|\mathcal C|\leq|\mathcal B|,\qquad |\mathcal B|\leq|\mathcal C|.$$

Thus $|\mathcal B|=|\mathcal C|$.

**Definition.** The common number of elements in a basis is the **dimension** of $V$, denoted $\dim_FV$.

Consequences:

- Every spanning set has at least $\dim V$ elements.
- Every linearly independent set has at most $\dim V$ elements.
- A linearly independent set of $\dim V$ vectors is automatically a basis.
- A spanning set of $\dim V$ vectors is automatically a basis.
- $\dim\{0\}=0$ and $\dim F^n=n$.

## 9. Bases of Subspaces and Quotients

Let $W\leq V$, and suppose

$$w_1,\ldots,w_m$$

is a basis of $W$. It is also linearly independent in $V$, so extend it to a basis

$$w_1,\ldots,w_m,v_{m+1},\ldots,v_n$$

of $V$. Under the quotient map $\pi:V\to V/W$, the first $m$ basis vectors vanish, while

$$\pi(v_{m+1}),\ldots,\pi(v_n)$$

form a basis of $V/W$. Therefore

$$\dim V=\dim W+\dim(V/W).$$

If

$$W'=\operatorname{span}(v_{m+1},\ldots,v_n),$$

then $W\cap W'=\{0\}$ and every $v\in V$ has a unique expression $v=w+w'$ with $w\in W$ and $w'\in W'$. Thus

$$V=W\oplus W'.$$

Moreover, $\pi|_{W'}:W'\to V/W$ is an isomorphism. Every subspace of a finite-dimensional vector space therefore has a complement.

This splitting is special to vector spaces. A group extension need not split: in $\mathbb Z/4\mathbb Z$, the subgroup $2\mathbb Z/4\mathbb Z$ and the quotient are both cyclic of order $2$, but there is no second subgroup of order $2$ complementary to the first.
