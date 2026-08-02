# Lecture 2 — Subgroups, the Symmetric Group $S_3$, and Cyclic Subgroups

## 1. Review: Groups and $\mathrm{GL}_n$

Recall that $\mathrm{GL}_n(\mathbb{R})$ is the group of invertible $n \times n$ real matrices under multiplication. One can similarly define $\mathrm{GL}_n(\mathbb{C})$ and $\mathrm{GL}_n(\mathbb{Q})$ by allowing complex or rational entries respectively.

A **group** $G$ is a set with a binary operation that is:
1. **Associative:** $(gh)k = g(hk)$.
2. Has an **identity** $e$: $eg = ge = g$ for all $g$.
3. Has **inverses**: for every $g$ there exists $g^{-1}$ with $gg^{-1} = g^{-1}g = e$.

## 2. The Automorphism Group of a Set

Let $T$ be any set. The **automorphism group** (or **symmetry group**) of $T$ is

```math
\mathrm{Aut}(T) = \{ f : T \xrightarrow{\sim} T \mid f \text{ is a bijection} \}
```

with group operation given by **composition of functions**:

```math
(f \circ g)(t) = f(g(t)).
```

- **Composition of bijections** is a bijection: closure. ✓
- Composition is **associative**. ✓
- **Identity:** the identity map $\mathrm{id}_T(t) = t$. ✓
- **Inverse:** the inverse function $f^{-1}$ (exists because $f$ is a bijection). ✓

$\mathrm{GL}_n(\mathbb{R})$ is a subgroup of $\mathrm{Aut}(\mathbb{R}^n)$: it consists of those bijections $\mathbb{R}^n \to \mathbb{R}^n$ that are **linear** (i.e., preserve the vector space structure).

## 3. Subgroups

**Definition.** A subset $H \subseteq G$ is a **subgroup** of $G$, written $H \leq G$, if:

1. $H$ is **closed under multiplication:** $a, b \in H \implies ab \in H$.
2. $H$ **contains the identity:** $e \in H$.
3. $H$ is **closed under inverses:** $a \in H \implies a^{-1} \in H$.

A subgroup is itself a group (with the restricted operation).

**Trivial subgroups.** Every group $G$ has two trivial subgroups: $\{e\}$ (the smallest) and $G$ itself (the largest).

**Example.** For $k \leq n$, the group $S_k$ embeds as a subgroup of $S_n$ by identifying a permutation of $\{1, \ldots, k\}$ with the permutation of $\{1, \ldots, n\}$ that does the same on $\{1, \ldots, k\}$ and fixes $k+1, \ldots, n$:

```math
S_k \leq S_n \quad \text{(fixing letters } k+1, \ldots, n).
```

**Example.** The set of upper-triangular invertible 2×2 matrices

```math
H = \left\{ \begin{pmatrix} a & b \\ 0 & d \end{pmatrix} : a, d \neq 0 \right\} \leq \mathrm{GL}_2(\mathbb{R})
```

is a subgroup. It consists of linear maps of $\mathbb{R}^2$ that **stabilize** the $x$-axis (the line $y = 0$). Closure under multiplication:

```math
\begin{pmatrix} a & b \\ 0 & d \end{pmatrix}\begin{pmatrix} a' & b' \\ 0 & d' \end{pmatrix} = \begin{pmatrix} aa' & ab' + bd' \\ 0 & dd' \end{pmatrix}.
```

The bottom-left entry stays $0$. ✓

## 4. Subgroups of $(\mathbb{Z}, +)$

**Proposition.** Every subgroup of $\mathbb{Z}$ (under addition) has the form $b\mathbb{Z} = \{bn : n \in \mathbb{Z}\}$ for some integer $b \geq 0$.

**Proof.**

- The set $b\mathbb{Z}$ is clearly a subgroup for any $b$.
- Conversely, let $H \leq \mathbb{Z}$.
  - **Case 1:** $H = \{0\}$. Then $H = 0\mathbb{Z}$. ✓
  - **Case 2:** $H \neq \{0\}$. Since $H$ is closed under inverses, it contains a positive integer. Let $b$ be the **smallest positive integer** in $H$.
    - By closure under addition and inverses, $H$ contains all multiples $\{0, \pm b, \pm 2b, \ldots\} = b\mathbb{Z}$.
    - Suppose $h \in H$. By the **Euclidean division algorithm**, write $h = qb + r$ with $0 \leq r < b$.
    - Then $r = h - qb \in H$ (since $qb \in H$). Since $b$ was the smallest positive integer in $H$ and $0 \leq r < b$, we must have $r = 0$.
    - So $h = qb \in b\mathbb{Z}$. Hence $H = b\mathbb{Z}$. $\square$

## 5. The Symmetric Group $S_3$

$S_3$ is the group of all permutations of $\{1, 2, 3\}$. It has $3! = 6$ elements:

| Element | Action | Description |
|---|---|---|
| $e$ | $1 \mapsto 1, 2 \mapsto 2, 3 \mapsto 3$ | identity |
| $\tau$ | $1 \mapsto 2, 2 \mapsto 1, 3 \mapsto 3$ | transposition of $1,2$ |
| $\tau'$ | $1 \mapsto 1, 2 \mapsto 3, 3 \mapsto 2$ | transposition of $2,3$ |
| $\tau''$ | $1 \mapsto 3, 2 \mapsto 2, 3 \mapsto 1$ | transposition of $1,3$ |
| $\sigma$ | $1 \mapsto 2, 2 \mapsto 3, 3 \mapsto 1$ | 3-cycle |
| $\sigma'$ | $1 \mapsto 3, 2 \mapsto 1, 3 \mapsto 2$ | 3-cycle (inverse of $\sigma$) |

**Transpositions** are permutations that fix all but exactly two elements and exchange those two.

### Non-commutativity of $S_3$

Compute $\tau \sigma$ and $\sigma \tau$ (applying right-hand permutation first):

- $(\tau\sigma)(1) = \tau(\sigma(1)) = \tau(2) = 1$, $(\tau\sigma)(2) = \tau(3) = 3$, $(\tau\sigma)(3) = \tau(1) = 2$. So $\tau\sigma = \tau'$.
- $(\sigma\tau)(1) = \sigma(\tau(1)) = \sigma(2) = 3$, $(\sigma\tau)(2) = \sigma(1) = 2$, $(\sigma\tau)(3) = \sigma(3) = 1$. So $\sigma\tau = \tau''$.

Since $\tau\sigma = \tau' \neq \tau'' = \sigma\tau$, **$S_3$ is non-abelian**.

Also note: $\sigma^{-1} = \sigma'$ (since $\sigma' \circ \sigma = e$) and $\tau^2 = e$ (every transposition is its own inverse).

**Corollary.** $S_n$ is **non-abelian for all $n \geq 3$**.

*Proof.* $S_3$ is a subgroup of $S_n$ (fixing letters $4, \ldots, n$), and $S_3$ contains two non-commuting elements. Those same elements are non-commuting in $S_n$. $\square$

## 6. Cyclic Subgroups and Order of an Element

**Definition.** Given a group $G$ and an element $g \in G$, the **cyclic subgroup generated by $g$** is

```math
\langle g \rangle = \{ g^n : n \in \mathbb{Z} \} = \{ \ldots, g^{-2}, g^{-1}, e, g, g^2, g^3, \ldots \}
```

where $g^0 = e$ and $g^{-n} = (g^{-1})^n$.

This is the **smallest** subgroup of $G$ containing $g$.

**Closure:** $g^m \cdot g^n = g^{m+n} \in \langle g \rangle$. ✓  
**Identity:** $g^0 = e \in \langle g \rangle$. ✓  
**Inverses:** $(g^n)^{-1} = g^{-n} \in \langle g \rangle$. ✓

**Definition.** The **order** of $g \in G$ is:
- The smallest positive integer $m$ such that $g^m = e$, denoted $\mathrm{ord}(g) = m$; or
- $\infty$ if no such positive $m$ exists (we say $g$ has **infinite order**).

**Examples:**
- In $\mathbb{Z}$, every nonzero integer has infinite order.
- In $S_3$: transpositions have order $2$ (e.g., $\tau^2 = e$); the 3-cycles $\sigma, \sigma'$ have order $3$ ($\sigma^3 = e$ but $\sigma \neq e, \sigma^2 \neq e$).
- The matrix $\begin{pmatrix} 1 & 1 \\ 0 & 1 \end{pmatrix}^n = \begin{pmatrix} 1 & n \\ 0 & 1 \end{pmatrix}$, so this element has infinite order in $\mathrm{GL}_2(\mathbb{R})$.
- The matrix $-I \in \mathrm{GL}_2(\mathbb{R})$ has order $2$ since $(-I)^2 = I$.

**Key observation.** The powers of $g$ need not all be distinct. If $g^m = e$ for some $m > 0$, then $|\langle g \rangle| = \mathrm{ord}(g)$.

**Preview (Lagrange's Theorem, Lecture 5).** In a finite group, the order of every element divides the order of the group.
