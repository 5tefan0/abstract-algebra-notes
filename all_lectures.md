# Abstract Algebra — Harvard (Gross) — Complete Notes, Lectures 1–12

---

# Lecture 1 — Introduction to Groups via Matrices

## 1. Square Matrices and the Space $M_n(\mathbb{R})$

Let $M_n(\mathbb{R})$ denote the set of all $n \times n$ matrices with real entries. A matrix $A \in M_n(\mathbb{R})$ has entries $A_{ij} \in \mathbb{R}$, where $i$ is the row index and $j$ is the column index.

As a real vector space, $M_n(\mathbb{R})$ has dimension $n^2$. The two vector-space operations are:

- **Addition:** $(A + B)_{ij} = A_{ij} + B_{ij}$
- **Scalar multiplication:** $(\alpha A)_{ij} = \alpha A_{ij}$ for $\alpha \in \mathbb{R}$

## 2. Matrix Multiplication

Given $A, B \in M_n(\mathbb{R})$, their product $C = AB$ is defined by

```math
C_{ij} = \sum_{k=1}^{n} A_{ik} B_{kj}.
```

**Interpretation.** Matrices represent linear operators on $\mathbb{R}^n$. If $A$ represents $T$ and $B$ represents $S$, then $AB$ represents $T \circ S$ (first apply $S$, then $T$).

**Key properties:**
- **Associativity:** $(AB)C = A(BC)$.
- **Identity matrix:** $I_n$ has $1$s on the diagonal and $0$s elsewhere; $IA = AI = A$.
- **Non-commutativity:** In general $AB \neq BA$.

**Example of non-commutativity (2×2):**

```math
A = \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}, \quad B = \begin{pmatrix} 0 & 0 \\ 1 & 0 \end{pmatrix}: \qquad AB = \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix}, \quad BA = \begin{pmatrix} 0 & 0 \\ 0 & 1 \end{pmatrix}.
```

## 3. Invertible Matrices

**Definition.** $A \in M_n(\mathbb{R})$ is **invertible** if there exists $B$ with $AB = BA = I_n$. Such $B$ is unique and denoted $A^{-1}$.

**2×2 formula.** For $A = \begin{pmatrix} a & b \\ c & d \end{pmatrix}$, $A$ is invertible iff $\det(A) = ad - bc \neq 0$, and
```math
A^{-1} = \frac{1}{ad - bc}\begin{pmatrix} d & -b \\ -c & a \end{pmatrix}.
```

### The Determinant

There is a function $\det: M_n(\mathbb{R}) \to \mathbb{R}$ with:
- $A$ is invertible $\iff$ $\det(A) \neq 0$.
- **Multiplicativity:** $\det(AB) = \det(A)\det(B)$.
- Explicit formula: $\det(A) = \sum_{\sigma \in S_n} \mathrm{sgn}(\sigma) \prod_{i=1}^n A_{i,\sigma(i)}$.

## 4. The General Linear Group $\mathrm{GL}_n(\mathbb{R})$

```math
\mathrm{GL}_n(\mathbb{R}) = \{ A \in M_n(\mathbb{R}) : \det(A) \neq 0 \}.
```

This set is closed under multiplication (since $\det(AB) = \det(A)\det(B) \neq 0$), contains $I_n$, and every element has an inverse. It is not closed under addition.

## 5. Definition of a Group

**Definition.** A **group** is a set $G$ with a binary operation $G \times G \to G$ satisfying:

1. **Closure:** $g, h \in G \implies g \cdot h \in G$.
2. **Associativity:** $(g \cdot h) \cdot k = g \cdot (h \cdot k)$.
3. **Identity:** $\exists\, e \in G$ with $e \cdot g = g \cdot e = g$ for all $g$.
4. **Inverses:** $\forall\, g \in G$, $\exists\, g^{-1}$ with $g \cdot g^{-1} = g^{-1} \cdot g = e$.

$G$ is **abelian** if $g \cdot h = h \cdot g$ for all $g, h$.

## 6. Examples of Groups

| Group | Operation | Identity | Inverse of $g$ |
|---|---|---|---|
| $\mathrm{GL}_n(\mathbb{R})$ | matrix multiplication | $I_n$ | $A^{-1}$ |
| $\mathbb{Z}$ | addition | $0$ | $-n$ |
| Any vector space $V$ | addition | $\mathbf{0}$ | $-\mathbf{v}$ |
| $\mathrm{Sym}(T)$ | composition | identity map | inverse bijection |

## 7. The Symmetric Group $S_n$

Let $T = \{1, 2, \ldots, n\}$. The **symmetric group** $S_n$ is the group of all bijections $T \to T$ under composition. $|S_n| = n!$.

$\mathrm{GL}_n(\mathbb{R})$ is the subgroup of $\mathrm{Sym}(\mathbb{R}^n)$ consisting of bijections that preserve the linear structure. This illustrates a general principle: interesting groups arise as symmetry groups of structured sets.

---

# Lecture 2 — Subgroups, the Symmetric Group $S_3$, and Cyclic Subgroups

## 1. The Automorphism Group of a Set

Let $T$ be any set. The **automorphism group** of $T$ is

```math
\mathrm{Aut}(T) = \{ f : T \xrightarrow{\sim} T \mid f \text{ is a bijection} \}
```

under composition. $\mathrm{GL}_n(\mathbb{R})$ is the subgroup of $\mathrm{Aut}(\mathbb{R}^n)$ consisting of linear bijections.

## 2. Subgroups

**Definition.** A subset $H \subseteq G$ is a **subgroup** of $G$, written $H \leq G$, if:
1. $a, b \in H \implies ab \in H$ (closed under multiplication).
2. $e \in H$.
3. $a \in H \implies a^{-1} \in H$.

**Examples:**
- $S_k \leq S_n$ (extend permutations by fixing $k+1, \ldots, n$).
- Upper-triangular invertible matrices: $H = \left\{ \begin{pmatrix} a & b \\ 0 & d \end{pmatrix} : a, d \neq 0 \right\} \leq \mathrm{GL}_2(\mathbb{R})$.

## 3. Subgroups of $(\mathbb{Z}, +)$

**Proposition.** Every subgroup of $\mathbb{Z}$ is $b\mathbb{Z} = \{bn : n \in \mathbb{Z}\}$ for some $b \geq 0$.

**Proof.** If $H = \{0\}$, take $b = 0$. Otherwise, let $b$ be the smallest positive integer in $H$. Clearly $b\mathbb{Z} \subseteq H$. For any $h \in H$, write $h = qb + r$ with $0 \leq r < b$; then $r = h - qb \in H$, forcing $r = 0$ by minimality of $b$. So $H = b\mathbb{Z}$. $\square$

## 4. The Symmetric Group $S_3$

$S_3$ has $3! = 6$ elements:

| Element | Action | Description |
|---|---|---|
| $e$ | $1 \mapsto 1, 2 \mapsto 2, 3 \mapsto 3$ | identity |
| $\tau$ | $1 \leftrightarrow 2$ | transposition $(1\,2)$ |
| $\tau'$ | $2 \leftrightarrow 3$ | transposition $(2\,3)$ |
| $\tau''$ | $1 \leftrightarrow 3$ | transposition $(1\,3)$ |
| $\sigma$ | $1 \mapsto 2 \mapsto 3 \mapsto 1$ | 3-cycle $(1\,2\,3)$ |
| $\sigma'$ | $1 \mapsto 3 \mapsto 2 \mapsto 1$ | 3-cycle $(1\,3\,2) = \sigma^{-1}$ |

**Non-commutativity:** $\tau\sigma = \tau' \neq \tau'' = \sigma\tau$, so $S_3$ is non-abelian. Hence $S_n$ is non-abelian for all $n \geq 3$.

## 5. Cyclic Subgroups and Order of an Element

**Definition.** The **cyclic subgroup** generated by $g \in G$ is $\langle g \rangle = \{g^n : n \in \mathbb{Z}\}$, the smallest subgroup containing $g$.

**Definition.** The **order** of $g$ is the smallest positive $m$ with $g^m = e$, or $\infty$ if none exists.

**Examples:**
- Transpositions have order $2$; 3-cycles in $S_3$ have order $3$.
- $\begin{pmatrix} 1 & 1 \\ 0 & 1 \end{pmatrix}$ has infinite order in $\mathrm{GL}_2(\mathbb{R})$.

If $g^m = e$ for some $m > 0$, then $|\langle g \rangle| = \mathrm{ord}(g)$.

---

# Lecture 3 — Isomorphisms and Homomorphisms

## 1. Isomorphisms

**Definition.** An **isomorphism** $f: G_1 \to G_2$ is a bijection satisfying $f(xy) = f(x)f(y)$. Groups are **isomorphic**, $G_1 \cong G_2$, if such a map exists.

**Example.** $G_1 = \{1,-1,i,-i\}$ under multiplication and $G_2 = \{e, \rho, \rho^2, \rho^3\}$ (generated by the 4-cycle $\rho$) are isomorphic via $f(i^k) = \rho^k$.

## 2. Cyclic Groups

**Definition.** $G$ is **cyclic** if $G = \langle g \rangle$ for some $g$ (a **generator**).

**Theorem.** Any two cyclic groups of the same finite order $n$ are isomorphic.

*Proof.* Map $x_1^k \mapsto x_2^k$ (well-defined since both generators have order $n$). $\square$

## 3. The Klein Four-Group $V_4$

$V_4$ is the group of order 4 in which every non-identity element has order 2. It is not cyclic.

**Realization in $S_4$:** $V_4 = \{e, (1\,2)(3\,4), (1\,3)(2\,4), (1\,4)(2\,3)\}$.

**$V_4 \not\cong \mathbb{Z}/4\mathbb{Z}$:** $\mathbb{Z}/4\mathbb{Z}$ has an element of order 4; $V_4$ does not. Isomorphisms preserve element orders.

## 4. Testing for Isomorphism

If $G_1 \cong G_2$, then: (1) $|G_1| = |G_2|$; (2) $G_1$ abelian $\iff$ $G_2$ abelian; (3) same number of elements of each order. These are necessary but not sufficient.

## 5. Automorphisms

$\mathrm{Aut}(G) = \{f: G \xrightarrow{\sim} G\}$ under composition is a group. Example: $\mathrm{Aut}(V_4) \cong S_3$ (any automorphism permutes the three non-identity elements, and any such permutation extends to an automorphism).

## 6. Homomorphisms

**Definition.** A **homomorphism** $f: G_1 \to G_2$ satisfies $f(xy) = f(x)f(y)$.

**Examples:**
- $\det: \mathrm{GL}_n(\mathbb{R}) \to \mathbb{R}^*$ (not an isomorphism: non-injective, and domain is non-abelian for $n \geq 2$).
- Trivial homomorphism: $f(g) = e_{G_2}$ for all $g$.
- Inclusion $S_k \hookrightarrow S_n$.
- Parity map $f: \mathbb{Z} \to \{e, \tau\}$: even $\mapsto e$, odd $\mapsto \tau$.

The **image** $\mathrm{Im}(f) = \{f(x) : x \in G_1\}$ is a subgroup of $G_2$.

---

# Lecture 4 — Kernels, Normal Subgroups, and Homomorphisms

## 1. Basic Properties of Homomorphisms

Let $f: G \to G'$ be a homomorphism. Then:
1. $f(e_G) = e_{G'}$ (apply $f$ to $e \cdot e = e$, then cancel).
2. $f(g^{-1}) = f(g)^{-1}$ (apply $f$ to $g \cdot g^{-1} = e$).
3. Composition of homomorphisms is a homomorphism.

## 2. The Kernel

```math
\ker(f) = \{ g \in G : f(g) = e' \}.
```

$\ker(f)$ is a subgroup of $G$. An isomorphism has $\ker(f) = \{e\}$ and $\mathrm{Im}(f) = G'$.

## 3. Normal Subgroups

**Definition.** $H \leq G$ is **normal**, $H \trianglelefteq G$, if $gHg^{-1} = H$ for all $g \in G$ (equivalently, $gH = Hg$ for all $g$).

**Theorem.** $\ker(f) \trianglelefteq G$ for any homomorphism $f$.

**Proof.** If $h \in \ker(f)$ and $g \in G$: $f(ghg^{-1}) = f(g)e'f(g)^{-1} = e'$. So $ghg^{-1} \in \ker(f)$. $\square$

In any abelian group, every subgroup is normal.

**Non-normal example.** In $S_3$, $H = \{e, (1\,2)\}$ is not normal: $(2\,3)(1\,2)(2\,3) = (1\,3) \notin H$.

## 4. Examples of Kernels

- **Special linear group:** $\mathrm{SL}_n(\mathbb{R}) = \ker(\det) \trianglelefteq \mathrm{GL}_n(\mathbb{R})$.
- **Permutation matrices:** $S_n \hookrightarrow \mathrm{GL}_n(\mathbb{R})$ via $\sigma \mapsto A_\sigma$ ($(A_\sigma)_{ij} = 1$ if $i = \sigma(j)$, else $0$).

## 5. The Sign Homomorphism and Alternating Group

Composing $S_n \to \mathrm{GL}_n(\mathbb{R}) \xrightarrow{\det} \mathbb{R}^*$ gives $\mathrm{sgn}: S_n \to \{+1,-1\}$.

- Transpositions are odd ($\mathrm{sgn} = -1$); identity is even.
- Any permutation decomposes into transpositions; parity is an invariant.

```math
A_n = \ker(\mathrm{sgn}) = \{\sigma \in S_n : \mathrm{sgn}(\sigma) = +1\} \trianglelefteq S_n.
```

$A_3 = \{e, (1\,2\,3), (1\,3\,2)\}$ (cyclic of order 3).

## 6. The Center

```math
Z(G) = \{z \in G : zg = gz\ \forall\, g \in G\} \trianglelefteq G.
```

$G$ is abelian $\iff$ $Z(G) = G$. For $n \geq 3$: $Z(S_n) = \{e\}$; $Z(\mathrm{GL}_n(\mathbb{R})) = \{\lambda I : \lambda \neq 0\}$.

## 7. The Conjugation Homomorphism

```math
\Phi: G \to \mathrm{Aut}(G), \quad \Phi(g) = \varphi_g, \quad \varphi_g(h) = ghg^{-1}.
```

$\varphi_g$ is an automorphism; $\Phi$ is a homomorphism with $\ker(\Phi) = Z(G)$. The image $\Phi(G)$ consists of the **inner automorphisms** of $G$.

---

# Lecture 5 — Cosets, Lagrange's Theorem, and Simple Groups

## 1. Equivalence Relations

An **equivalence relation** on $S$ satisfies reflexivity, symmetry, and transitivity, and partitions $S$ into **equivalence classes**. Any map $f: S \to T$ induces the equivalence $a \sim b \iff f(a) = f(b)$; equivalence classes are the fibers $f^{-1}(t)$.

## 2. Left Cosets

**Definition.** For $H \leq G$ and $a \in G$: $aH = \{ah : h \in H\}$.

**Proposition.** Left cosets partition $G$:
- Every $a \in G$ lies in $aH$ (since $a = ae \in aH$).
- If $aH \cap bH \neq \emptyset$, then $aH = bH$.

**Lemma.** $|aH| = |H|$ for all $a$ (the map $h \mapsto ah$ is a bijection $H \to aH$).

## 3. Lagrange's Theorem

**Definition.** The **index** $[G:H]$ is the number of distinct left cosets.

**Theorem (Lagrange).** For finite $G$ and $H \leq G$:
```math
|G| = |H| \cdot [G : H].
```

**Corollaries:**
1. $|H| \mid |G|$.
2. $\mathrm{ord}(g) \mid |G|$ for all $g \in G$.
3. $g^{|G|} = e$ for all $g \in G$.

For a homomorphism $f: G \to G'$: $|G| = |\ker(f)| \cdot |\mathrm{Im}(f)|$ (analogous to rank-nullity).

## 4. The Alternating Group

**Proposition.** $|A_n| = n!/2$.

*Proof.* $\mathrm{sgn}: S_n \to \{\pm 1\}$ is surjective with kernel $A_n$; Lagrange gives $n! = |A_n| \cdot 2$. $\square$

## 5. Groups of Prime Order

**Theorem.** If $|G| = p$ (prime), then $G$ is cyclic and every non-identity element is a generator. The only subgroups are $\{e\}$ and $G$.

*Proof.* For $g \neq e$: $\mathrm{ord}(g) \mid p$, so $\mathrm{ord}(g) = p$, giving $\langle g \rangle = G$. $\square$

## 6. Simple Groups

**Definition.** $G$ is **simple** if its only normal subgroups are $\{e\}$ and $G$.

**Examples:**
- Groups of prime order (the only simple abelian groups).
- $A_n$ for $n \geq 5$.

**Theorem (Feit–Thompson, 1963).** Every finite non-abelian simple group has even order.

**Classification of Finite Simple Groups:** Cyclic groups $\mathbb{Z}/p\mathbb{Z}$; alternating groups $A_n$ ($n \geq 5$); groups of Lie type (e.g., $\mathrm{PSL}_n(\mathbb{F}_q)$); 26 sporadic groups (largest: the Monster, order $\approx 8 \times 10^{53}$).

---

# Lecture 6 — Modular Arithmetic and Quotient Groups (Preview)

## 1. Congruence Modulo $n$

**Definition.** $a \equiv b \pmod{n}$ if $n \mid (a - b)$.

This is an equivalence relation (reflexive, symmetric, transitive). The equivalence class of $a$ is

```math
\bar{a} = a + n\mathbb{Z} = \{a + kn : k \in \mathbb{Z}\},
```

the left coset of $n\mathbb{Z}$ containing $a$.

**The $n$ distinct residue classes are $\bar{0}, \bar{1}, \ldots, \overline{n-1}$** (by the division algorithm).

## 2. The Group $\mathbb{Z}/n\mathbb{Z}$

```math
\mathbb{Z}/n\mathbb{Z} = \{\bar{0}, \bar{1}, \ldots, \overline{n-1}\}, \quad \bar{a} + \bar{b} = \overline{a+b}.
```

**Well-defined:** $n \mid (a-a')$ and $n \mid (b-b') \implies n \mid ((a+b)-(a'+b'))$.

$(\mathbb{Z}/n\mathbb{Z}, +)$ is an **abelian group**: identity $\bar{0}$, inverses $-\bar{a} = \overline{n-a}$, inherited associativity and commutativity.

$\mathbb{Z}/n\mathbb{Z}$ is **cyclic of order $n$** generated by $\bar{1}$. The natural map $\pi: \mathbb{Z} \to \mathbb{Z}/n\mathbb{Z}$, $a \mapsto \bar{a}$, is a surjective homomorphism with $\ker(\pi) = n\mathbb{Z}$.

## 3. Ring Structure on $\mathbb{Z}/n\mathbb{Z}$

Define $\bar{a} \cdot \bar{b} = \overline{ab}$ (well-defined since $ab - a'b' = a(b-b') + b'(a-a')$). With both addition and multiplication, $\mathbb{Z}/n\mathbb{Z}$ is a **ring**.

## 4. Units: The Group $(\mathbb{Z}/n\mathbb{Z})^\times$

**Definition.** $(\mathbb{Z}/n\mathbb{Z})^\times = \{\bar{a} : \exists\, \bar{c}\text{ with }\bar{a}\bar{c} = \bar{1}\}$.

**GCD and Bézout.** $m\mathbb{Z} + n\mathbb{Z} = \gcd(m,n)\mathbb{Z}$, so $\gcd(m,n) = mr + ns$ for some $r, s \in \mathbb{Z}$.

**Theorem.** $\bar{a} \in (\mathbb{Z}/n\mathbb{Z})^\times \iff \gcd(a,n) = 1$.

**Examples:**
- $(\mathbb{Z}/p\mathbb{Z})^\times = \{\bar{1}, \ldots, \overline{p-1}\}$, order $p-1$.
- $|(\mathbb{Z}/p^e\mathbb{Z})^\times| = p^{e-1}(p-1)$.

## 5. A Computation

**Problem.** Find the last two digits of $2^{1000}$.

**Solution.** $2^{10} \equiv 24$, $2^{20} \equiv 24^2 = 576 \equiv 76$, $76^2 = 5776 \equiv 76$; so $76^k \equiv 76$ for all $k \geq 1$. Then $2^{1000} = (2^{20})^{50} \equiv 76^{50} \equiv 76 \pmod{100}$. The last two digits are $\mathbf{76}$.

---

# Lecture 7 — Quotient Groups and the First Isomorphism Theorem

## 1. Review: $\mathbb{Z}/n\mathbb{Z}$ as a Quotient

The residue classes modulo $n$ are the cosets of $n\mathbb{Z}$ in $\mathbb{Z}$. The quotient $\mathbb{Z}/n\mathbb{Z}$ inherits a group structure: $\bar{a} + \bar{b} = \overline{a+b}$. This construction, due to Gauss (1801), is the first example of a quotient group in the literature.

## 2. When Does a Quotient Group Exist?

Given $H \leq G$, we ask: when is the **naive multiplication**

```math
(aH)(bH) \stackrel{?}{=} (ab)H
```

on the set $G/H = \{aH : a \in G\}$ well-defined?

### Case 1: $H = \ker(f)$

The cosets of $H$ biject with the elements of $\mathrm{Im}(f) \leq G'$ (each coset is a fiber of $f$). Transporting the group structure from $\mathrm{Im}(f)$ to $G/H$ gives a well-defined group law: $(aH)(bH) = (ab)H$.

### Case 2: Arbitrary Subgroup — Naive Multiplication Can Fail

If $aHa^{-1} \not\subseteq H$ for some $a$, there exists $h \in H$ with $aha^{-1} \notin H$. The product $(ah) \cdot a^{-1}$ (with $ah \in aH$ and $a^{-1} \in a^{-1}H$) gives $aha^{-1} \notin H$, so two products from $(aH)(a^{-1}H)$ must both equal $eH = H$, but not all of them land in $H$. The multiplication is **not well-defined**.

### Case 3: $H \trianglelefteq G$ — Naive Multiplication Works

**Theorem.** If $H \trianglelefteq G$, then $(aH)(bH) = (ab)H$ is well-defined and $G/H$ is a group.

**Proof.** Compute the set of all products $\{ah \cdot bh' : h, h' \in H\}$:

```math
aH \cdot bH = a(Hb)H = a(bH)H = (ab)(HH) = (ab)H,
```

using $Hb = bH$ (normality) and $HH = H$ ($H$ is a subgroup). $\square$

**Converse.** If the naive multiplication is well-defined, then $H$ must be normal. Hence:

> $(aH)(bH) = (ab)H$ defines a group on $G/H$ **if and only if** $H \trianglelefteq G$.

**Group structure on $G/H$:** identity = $H$; inverse of $aH$ is $a^{-1}H$; associativity inherited from $G$.

## 3. The Natural Homomorphism

When $H \trianglelefteq G$, there is a natural surjective group homomorphism

```math
\pi: G \to G/H, \quad a \mapsto aH, \quad \ker(\pi) = H.
```

**Corollary.** $H \trianglelefteq G \iff H$ is the kernel of some group homomorphism from $G$.

This completes the circle: kernels are always normal (Lecture 4), and every normal subgroup is a kernel (exhibited by $\pi$).

## 4. The First Isomorphism Theorem

**Theorem.** Let $f: G \twoheadrightarrow G'$ be a surjective homomorphism with $\ker(f) = H$. Then $f$ induces an isomorphism

```math
\bar{f}: G/H \xrightarrow{\;\sim\;} G', \quad \bar{f}(aH) = f(a).
```

**Proof sketch:**
- **Well-defined:** $aH = a'H \implies f(a) = f(a')$ (since $a'^{-1}a \in H = \ker f$).
- **Homomorphism:** $\bar{f}((aH)(bH)) = \bar{f}(abH) = f(ab) = f(a)f(b)$.
- **Surjective:** $f$ is surjective.
- **Injective:** $\bar{f}(aH) = e' \implies a \in H \implies aH = H = e_{G/H}$. $\square$

**Factorization.** Any homomorphism $f: G \to G'$ factors as

```math
G \xrightarrow{\;\pi\;} G/\ker(f) \xrightarrow{\;\sim\;} \mathrm{Im}(f) \hookrightarrow G'.
```

## 5. Short Exact Sequences

A **short exact sequence** is a diagram of group homomorphisms

```math
1 \to H \xrightarrow{\;g\;} G \xrightarrow{\;f\;} G' \to 1
```

where $g$ is injective, $f$ is surjective, and $\mathrm{Im}(g) = \ker(f)$. This says $G$ is an extension of $G'$ by $H$: the First Isomorphism Theorem gives $G' \cong G/H$.

## 6. Warning: Extensions Are Not Unique

Knowing $H$ and $G' \cong G/H$ does **not** determine $G$.

**Example.** Both $S_3$ and $\mathbb{Z}/6\mathbb{Z}$ appear in short exact sequences with kernel $\cong \mathbb{Z}/3\mathbb{Z}$ and quotient $\cong \mathbb{Z}/2\mathbb{Z}$:

```math
1 \to A_3 \to S_3 \xrightarrow{\mathrm{sgn}} \mathbb{Z}/2\mathbb{Z} \to 1,
```
```math
1 \to \{\bar{0},\bar{2},\bar{4}\} \to \mathbb{Z}/6\mathbb{Z} \xrightarrow{a \bmod 2} \mathbb{Z}/2\mathbb{Z} \to 1.
```

Yet $S_3 \not\cong \mathbb{Z}/6\mathbb{Z}$ ($S_3$ is non-abelian, $\mathbb{Z}/6\mathbb{Z}$ is abelian). The extra data needed to reconstruct $G$ from $H$ and $G/H$ — how $G/H$ acts on $H$ by conjugation — is the **group extension problem**.

---

# Lecture 8 — The Correspondence Theorem, Fields, and Vector Spaces

## 1. Subgroups of a Quotient

Let $H\trianglelefteq G$ and let $\pi:G\to G/H$ be the quotient map. There is an inclusion-preserving bijection

```math
\{K\leq G:H\leq K\}\longleftrightarrow\{L\leq G/H\}
```

given by

```math
K\mapsto K/H=\pi(K),\qquad L\mapsto\pi^{-1}(L).
```

Normality is also preserved:

```math
K\trianglelefteq G\iff K/H\trianglelefteq G/H.
```

**Example.** If $p$ is prime and $p\mathbb Z\leq K\leq\mathbb Z$, then $K/p\mathbb Z$ is a subgroup of the prime-order group $\mathbb Z/p\mathbb Z$. Hence $K=p\mathbb Z$ or $K=\mathbb Z$, so $p\mathbb Z$ is maximal in $\mathbb Z$.

## 2. Fields and Prime Fields

A **field** $F$ is an abelian group under addition, its nonzero elements form an abelian group under multiplication, and multiplication distributes over addition. Thus every nonzero element is invertible.

$\mathbb Q$, $\mathbb R$, and $\mathbb C$ are fields; $\mathbb Z$ is not. For every prime $p$,

```math
\mathbb{F}_p=\mathbb Z/p\mathbb Z
```

is a field. If $\bar a\neq0$, maximality gives $p\mathbb Z+a\mathbb Z=\mathbb Z$, so $rp+sa=1$ for some integers $r,s$; modulo $p$, $\bar s\bar a=\bar1$.

If $n$ is composite, $\mathbb Z/n\mathbb Z$ has nonzero zero divisors and is not a field.

The **characteristic** of $F$ is the least $n>0$ with $n\cdot1_F=0$, or $0$ if none exists. A field's characteristic is $0$ or prime. Every finite field has order $p^n$; for each prime power there is, up to isomorphism, one field $\mathbb{F}_{p^n}$.

## 3. Vector Spaces over $F$

An $F$-vector space is an abelian group $(V,+)$ with scalar multiplication satisfying

```math
1v=v,\quad (ab)v=a(bv),\quad a(v+w)=av+aw,\quad(a+b)v=av+bv.
```

Examples include $\{0\}$, $F$, $F^n$, and $F[x]$.

A subspace is an additive subgroup stable under scalar multiplication. A map $T:V\to W$ is linear if

```math
T(av+bv')=aT(v)+bT(v').
```

Its kernel and image are subspaces. If $U\leq V$, then $V/U$ is a vector space with

```math
a(v+U)=av+U,
```

and the projection $V\to V/U$ is linear with kernel $U$. Thus

```math
V/\ker T\cong\operatorname{Im}T
```

as vector spaces.

---

# Lecture 9 — Span, Linear Independence, Bases, and Dimension

## 1. Span and Finite Dimension

For $S=\{v_1,\ldots,v_n\}$,

```math
\operatorname{span}(S)=\left\{\sum_{i=1}^n a_iv_i:a_i\in F\right\},
```

the smallest subspace containing $S$. By convention, $\operatorname{span}(\varnothing)=\{0\}$.

$V$ is **finite-dimensional** if some finite set spans it. The standard vectors span $F^n$. The space $F[x]$ is infinite-dimensional because a finite set of polynomials has bounded degree and cannot span polynomials of arbitrarily high degree.

## 2. Independence and Bases

$\{v_1,\ldots,v_n\}$ is **linearly independent** if

```math
\sum a_iv_i=0\implies a_1=\cdots=a_n=0.
```

An ordered list $\mathcal B=(v_1,\ldots,v_n)$ is a **basis** if it spans and is linearly independent. Equivalently, each $v\in V$ has a unique expansion

```math
v=a_1v_1+\cdots+a_nv_n.
```

The coordinate map $v\mapsto(a_1,\ldots,a_n)$ is a linear isomorphism $V\cong F^n$.

## 3. Pruning, Extension, and Exchange

- Every finite spanning set contains a basis: if a dependence relation has $a_n\neq0$, solve for $v_n$ and remove it without changing the span.
- Every independent set in a finite-dimensional space extends to a basis: while it does not span, adjoin a vector outside its span.
- If $n$ vectors span $V$ and $m$ vectors are independent, then $m\leq n$ (the Steinitz exchange bound).

It follows that every basis has the same size. This common size is $\dim_FV$.

Consequently, spanning sets have at least $\dim V$ elements, independent sets have at most $\dim V$ elements, and a spanning or independent list of exactly $\dim V$ vectors is automatically a basis.

## 4. Subspaces, Quotients, and Complements

If $w_1,\ldots,w_m$ is a basis of $W\leq V$, extend it to

```math
w_1,\ldots,w_m,v_{m+1},\ldots,v_n
```

as a basis of $V$. Then the cosets of $v_{m+1},\ldots,v_n$ form a basis of $V/W$, so

```math
\dim V=\dim W+\dim(V/W).
```

With $W'=\operatorname{span}(v_{m+1},\ldots,v_n)$,

```math
V=W\oplus W',\qquad W'\cong V/W.
```

Every finite-dimensional subspace has a complement, although the complement is not canonical. This splitting need not occur for arbitrary group extensions.

---

# Lecture 10 — Direct Sums, Matrices, and Change of Basis

## 1. Direct Sums and Splitting

$V=W\oplus W'$ means

```math
V=W+W',\qquad W\cap W'=\{0\}.
```

Equivalently, every $v\in V$ is uniquely $w+w'$. The map $W\times W'\to V$, $(w,w')\mapsto w+w'$, is then an isomorphism.

For a linear map $T:V\to U$, choose a complement $C$ to $\ker T$. The restriction

```math
T|_C:C\xrightarrow{\sim}\operatorname{Im}T
```

gives the noncanonical splitting

```math
V\cong\ker T\oplus\operatorname{Im}T
```

and the rank–nullity formula

```math
\dim V=\dim\ker T+\dim\operatorname{Im}T.
```

## 2. Bases and Matrix Coordinates

An ordered basis $\mathcal B=(v_1,\ldots,v_n)$ gives an isomorphism

```math
\rho_{\mathcal B}:F^n\to V,\qquad(a_i)\mapsto\sum a_iv_i.
```

For $T:V\to W$ and a basis $\mathcal C$ of $W$,

```math
[T]_{\mathcal C\leftarrow\mathcal B}
=\rho_{\mathcal C}^{-1}T\rho_{\mathcal B}.
```

If $T(v_j)=\sum_i a_{ij}w_i$, its matrix is $(a_{ij})$: the $j$th column is the coordinate vector of $T(v_j)$. Hence

```math
[T(v)]_{\mathcal C}=[T]_{\mathcal C\leftarrow\mathcal B}[v]_{\mathcal B}.
```

For composable maps,

```math
[S\circ T]_{\mathcal D\leftarrow\mathcal B}
=[S]_{\mathcal D\leftarrow\mathcal C}[T]_{\mathcal C\leftarrow\mathcal B}.
```

Thus matrix multiplication is composition in coordinates. Kernels become nullspaces, images become column spaces, and row reduction becomes a structural tool.

## 3. Change of Basis and Conjugacy

If $P=\rho_{\mathcal B}^{-1}\rho_{\mathcal B'}$, then

```math
[v]_{\mathcal B}=P[v]_{\mathcal B'}.
```

If $Q=\rho_{\mathcal C}^{-1}\rho_{\mathcal C'}$, then

```math
[T]_{\mathcal C'\leftarrow\mathcal B'}
=Q^{-1}[T]_{\mathcal C\leftarrow\mathcal B}P.
```

For an endomorphism using one basis in domain and codomain,

```math
[T]_{\mathcal B'}=P^{-1}[T]_{\mathcal B}P.
```

Similar matrices are therefore conjugate representatives of the same abstract operator.

The group of linear automorphisms is

```math
\mathrm{GL}(V)=\operatorname{Aut}_F(V),
```

and a choice of basis identifies it with $\mathrm{GL}_n(F)$.

---

# Lecture 11 — Rank–Nullity, Matrix Representations, and Simple Forms

## 1. Differentiation and Characteristic

Formal differentiation is a linear map

```math
D:F[x]_{\leq n}\to F[x]_{\leq n-1}.
```

In characteristic $0$, it is surjective with kernel the constants. In characteristic $p$, however,

```math
D(x^p)=px^{p-1}=0,
```

so the kernel grows and $x^{p-1}$ is absent from the image. Linear algebra works over every field, but the field's characteristic affects examples.

## 2. Rank–Nullity

Choose a basis $v_1,\ldots,v_k$ of $\ker T$ and extend it to a basis $v_1,\ldots,v_n$ of $V$. Then

```math
T(v_{k+1}),\ldots,T(v_n)
```

is a basis of $\operatorname{Im}T$. Therefore

```math
\dim V=\underbrace{\dim\ker T}_{\text{nullity}}
+\underbrace{\dim\operatorname{Im}T}_{\text{rank}}.
```

If $T:V\to W$ and $\dim V=\dim W$, injectivity, surjectivity, and invertibility are equivalent.

## 3. Matrices and Invertibility

For an endomorphism $T:V\to V$ with matrix $A$, the following are equivalent:

```math
T\text{ is an automorphism}
\iff\ker T=0
\iff\operatorname{Im}T=V
\iff A\text{ is invertible}
\iff\det A\neq0.
```

**Example.** $\mathbb{F}_2^2$ has three nonzero vectors. Every element of $\mathrm{GL}_2(\mathbb{F}_2)$ permutes them, giving

```math
\mathrm{GL}_2(\mathbb{F}_2)\cong S_3.
```

Indeed,

```math
|\mathrm{GL}_2(\mathbb{F}_2)|=(4-1)(4-2)=6.
```

## 4. Adapted Bases and Rank Normal Form

If $r=\operatorname{rank}T$, independent choices of bases in the domain and codomain put $T$ into the form

```math
[T]=\begin{pmatrix}I_r&0\\0&0\end{pmatrix}.
```

This classifies linear maps up to independent changes of bases by rank. For an endomorphism, the same basis must be used on both sides, so only conjugation is allowed. The search for simple representatives under conjugation leads to invariant subspaces and eigenvectors.

---

# Lecture 12 — Invariant Subspaces, Eigenvalues, and the Characteristic Polynomial

## 1. Invariant Subspaces and Diagonalization

$W\leq V$ is **$T$-invariant** if $T(W)\subseteq W$. A basis beginning with a basis of $W$ gives

```math
[T]=\begin{pmatrix}A&B\\0&D\end{pmatrix}.
```

If $W$ has an invariant complement, the matrix is block diagonal.

A nonzero $v$ is an eigenvector with eigenvalue $\lambda$ if

```math
T(v)=\lambda v.
```

The eigenspace is $E_\lambda(T)=\ker(T-\lambda I)$. A basis of eigenvectors makes $[T]$ diagonal; equivalently, $V$ is the direct sum of its eigenspaces.

Diagonalization can fail because a polynomial has no roots in $F$ (a nontrivial real rotation), or because the eigenspaces are too small. For

```math
A=\begin{pmatrix}1&1\\0&1\end{pmatrix},
```

the only eigenspace is $E_1=Fe_1$, so $A$ is not diagonalizable.

## 2. Characteristic Polynomial

For a matrix $A$ of $T$, define

```math
\chi_T(t)=\det(tI-A).
```

Since

```math
\lambda\text{ is an eigenvalue}
\iff T-\lambda I\text{ is singular}
\iff\chi_T(\lambda)=0,
```

the roots in $F$ are precisely the eigenvalues.

The polynomial is basis-independent: if $A'=P^{-1}AP$, then

```math
\det(tI-A')=\det\bigl(P^{-1}(tI-A)P\bigr)=\det(tI-A).
```

For $A=\begin{pmatrix}a&b\\c&d\end{pmatrix}$,

```math
\chi_A(t)=t^2-(a+d)t+(ad-bc).
```

Thus trace and determinant are similarity invariants.

## 3. Roots and Eigenvectors

A nonzero degree-$n$ polynomial over a field has at most $n$ distinct roots. Hence an endomorphism of an $n$-dimensional vector space has at most $n$ distinct eigenvalues.

Eigenvectors with distinct eigenvalues are linearly independent. Therefore, if

```math
\chi_T(t)=\prod_{i=1}^n(t-\lambda_i)
```

with all $\lambda_i\in F$ distinct, then $T$ has an eigenbasis and is diagonalizable. The converse in this form is false: diagonalizable operators may have repeated eigenvalues.

For a rotation through $\theta$,

```math
\chi(t)=t^2-2\cos\theta\,t+1,
```

which has no real roots when $\theta\not\equiv0,\pi$. For $\begin{pmatrix}1&1\\0&1\end{pmatrix}$, $\chi(t)=(t-1)^2$ but the eigenspace is only one-dimensional.

## 4. Cayley–Hamilton

Every linear operator satisfies its own characteristic polynomial:

```math
\chi_T(T)=0.
```

For a $2\times2$ matrix,

```math
A^2-\operatorname{tr}(A)A+\det(A)I=0.
```

Polynomial evaluation here occurs in $\operatorname{End}_F(V)$, where multiplication is composition. Cayley–Hamilton begins the connection between polynomial factorization and canonical forms for linear operators.
