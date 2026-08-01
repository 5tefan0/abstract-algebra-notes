# Lecture 1 — Introduction to Groups via Matrices

## 1. Square Matrices and the Space $M_n(\mathbb{R})$

Let $M_n(\mathbb{R})$ denote the set of all $n \times n$ matrices with real entries. A matrix $A \in M_n(\mathbb{R})$ has entries $A_{ij} \in \mathbb{R}$, where $i$ is the row index and $j$ is the column index.

As a real vector space, $M_n(\mathbb{R})$ has dimension $n^2$. The two vector-space operations are:

- **Addition:** $(A + B)_{ij} = A_{ij} + B_{ij}$
- **Scalar multiplication:** $(\alpha A)_{ij} = \alpha A_{ij}$ for $\alpha \in \mathbb{R}$

## 2. Matrix Multiplication

Unlike arbitrary rectangular matrices, square matrices support **multiplication**. Given $A, B \in M_n(\mathbb{R})$, their product $C = AB$ is defined by

$$C_{ij} = \sum_{k=1}^{n} A_{ik} B_{kj}.$$

**Interpretation.** Matrices represent linear operators on $\mathbb{R}^n$. If $A$ represents the linear transformation $T$ and $B$ represents $S$, then $AB$ represents the composition $T \circ S$ (first apply $S$, then $T$).

**Key properties:**
- **Associativity:** $(AB)C = A(BC)$ — clear from composition of transformations.
- **Distributivity:** $A(B + C) = AB + AC$.
- **Identity matrix:** $I_n$ has $1$s on the diagonal and $0$s elsewhere; $IA = AI = A$ for all $A$.
- **Zero matrix:** $0 \cdot A = A \cdot 0 = 0$.
- **Non-commutativity:** In general $AB \neq BA$.

**Example of non-commutativity (2×2):**

$$A = \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}, \quad B = \begin{pmatrix} 0 & 0 \\ 1 & 0 \end{pmatrix}.$$

$$AB = \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix}, \qquad BA = \begin{pmatrix} 0 & 0 \\ 0 & 1 \end{pmatrix}.$$

So $AB \neq BA$.

## 3. Invertible Matrices

**Definition.** A matrix $A \in M_n(\mathbb{R})$ is **invertible** if there exists a matrix $B \in M_n(\mathbb{R})$ such that

$$AB = BA = I_n.$$

Such a $B$ is called the **inverse** of $A$ and is denoted $A^{-1}$.

**Uniqueness of inverses.** If $AB = I$ and $AC = I$, then $B = C$. *Proof:* From $AB = AC = I$, multiply on the left by $B$:

$$B(AB) = B(AC) \implies (BA)B = (BA)C \implies IB = IC \implies B = C.$$

**2×2 case.** For $A = \begin{pmatrix} a & b \\ c & d \end{pmatrix}$, $A$ is invertible if and only if $\det(A) = ad - bc \neq 0$, and

$$A^{-1} = \frac{1}{ad - bc}\begin{pmatrix} d & -b \\ -c & a \end{pmatrix}.$$

*Verification:*
$$A \cdot \begin{pmatrix} d & -b \\ -c & a \end{pmatrix} = \begin{pmatrix} ad - bc & 0 \\ 0 & ad - bc \end{pmatrix} = (ad-bc)\, I.$$

Dividing by $ad - bc \neq 0$ gives $A^{-1}$.

### The Determinant

There is a function $\det: M_n(\mathbb{R}) \to \mathbb{R}$ (the **determinant**) with the following properties:

- It is a polynomial of degree $n$ in the entries of $A$.
- **Fundamental criterion:** $A$ is invertible $\iff$ $\det(A) \neq 0$.
- **Multiplicativity:** $\det(AB) = \det(A)\det(B)$.

The formula $\det(A) = \sum_{\sigma \in S_n} \text{sgn}(\sigma) \prod_{i=1}^n A_{i,\sigma(i)}$ (sum over $n!$ terms) is correct but unwieldy; the multiplicativity property is its most important feature.

## 4. The General Linear Group $\mathrm{GL}_n(\mathbb{R})$

**Definition.**

$$\mathrm{GL}_n(\mathbb{R}) = \{ A \in M_n(\mathbb{R}) : \det(A) \neq 0 \} = \{ A \in M_n(\mathbb{R}) : A \text{ is invertible} \}.$$

**Properties of $\mathrm{GL}_n(\mathbb{R})$:**

1. **Closed under multiplication.** If $A, B \in \mathrm{GL}_n(\mathbb{R})$, then $(AB)^{-1} = B^{-1}A^{-1}$ exists, so $AB \in \mathrm{GL}_n(\mathbb{R})$.

   *Alternatively:* $\det(AB) = \det(A)\det(B) \neq 0$.

2. **Identity element.** $I_n \in \mathrm{GL}_n(\mathbb{R})$.

3. **Inverses.** By definition, every $A \in \mathrm{GL}_n(\mathbb{R})$ has $A^{-1} \in \mathrm{GL}_n(\mathbb{R})$.

4. **Associativity.** Inherited from $M_n(\mathbb{R})$.

**What is lost:** $\mathrm{GL}_n(\mathbb{R})$ is **not** closed under addition (e.g., $I + (-I) = 0 \notin \mathrm{GL}_n(\mathbb{R})$), so it does not carry the vector space structure.

## 5. Definition of a Group

**Definition.** A **group** is a set $G$ together with a binary operation (called **multiplication** or the **group law**)

$$G \times G \to G, \quad (g, h) \mapsto g \cdot h,$$

satisfying the following four axioms:

1. **Closure:** $g, h \in G \implies g \cdot h \in G$.
2. **Associativity:** $(g \cdot h) \cdot k = g \cdot (h \cdot k)$ for all $g, h, k \in G$.
3. **Identity:** There exists an element $e \in G$ (called the **identity**) such that $e \cdot g = g \cdot e = g$ for all $g \in G$.
4. **Inverses:** For every $g \in G$ there exists $g^{-1} \in G$ such that $g \cdot g^{-1} = g^{-1} \cdot g = e$.

A group $G$ is **abelian** (or **commutative**) if $g \cdot h = h \cdot g$ for all $g, h \in G$.

> *Historical note.* The theory of groups was developed in the early 19th century by the Norwegian mathematician Niels Henrik Abel and the French mathematician Évariste Galois. Both died in their 20s. Galois's work (discovering that the solvability of a polynomial equation depends on the structure of a certain group) was largely ignored for 50 years until Camille Jordan recognized its importance.

## 6. Examples of Groups

| Group | Operation | Identity | Inverse of $g$ |
|---|---|---|---|
| $\mathrm{GL}_n(\mathbb{R})$ | matrix multiplication | $I_n$ | $A^{-1}$ |
| $\mathbb{Z}$ | addition | $0$ | $-n$ |
| Any vector space $V$ | addition | $\mathbf{0}$ | $-\mathbf{v}$ |
| $\mathrm{Sym}(T)$ | composition of bijections | identity map | inverse bijection |

## 7. The Symmetric Group $S_n$

Let $T = \{1, 2, \ldots, n\}$. The **symmetric group** $S_n$ is the group of all bijections $T \to T$ (permutations) under composition.

$$|S_n| = n!$$

because there are $n$ choices for where to send $1$, then $n-1$ choices for $2$, etc.

**Example:** $S_1 = \{e\}$ (trivial group). $S_2 = \{e, \tau\}$ where $\tau$ swaps $1$ and $2$; this has order $2$.

**Observation.** $\mathrm{GL}_n(\mathbb{R})$ arises as the subgroup of $\mathrm{Sym}(\mathbb{R}^n)$ (all bijections of $\mathbb{R}^n$) consisting of those bijections that **preserve the linear structure** (i.e., linear maps).

This illustrates a general principle: interesting groups arise as **symmetry groups of structured sets** — bijections of a set that preserve some additional structure.
