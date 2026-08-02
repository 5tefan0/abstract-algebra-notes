# Lecture 5 — Cosets, Lagrange's Theorem, and Simple Groups

## 1. Equivalence Relations

**Definition.** An **equivalence relation** on a set $`S`$ is a relation $`\sim`$ satisfying:
1. **Reflexivity:** $`a \sim a`$ for all $`a \in S`$.
2. **Symmetry:** $`a \sim b \implies b \sim a`$.
3. **Transitivity:** $`a \sim b`$ and $`b \sim c \implies a \sim c`$.

An equivalence relation partitions $`S`$ into disjoint **equivalence classes**: subsets $`[a] = \{b \in S : b \sim a\}`$ whose union is all of $`S`$.

**Conversely**, any map $`f: S \to T`$ induces an equivalence relation on $`S`$:
```math
a \sim b \iff f(a) = f(b).
```
The equivalence classes are the **fibers** $`f^{-1}(t) = \{s \in S : f(s) = t\}`$ for $`t \in \mathrm{Im}(f)`$.

**Example.** The map $`f: \mathbb{R} \to S^1`$ defined by $`f(t) = e^{2\pi i t}`$ is a group homomorphism from $`(\mathbb{R}, +)`$ to the unit circle $`(S^1, \times)`$. Its fibers are $`f^{-1}(e^{2\pi i t_0}) = \{t_0 + n : n \in \mathbb{Z}\}`$, i.e., cosets of $`\mathbb{Z}`$ in $`\mathbb{R}`$.

## 2. Left Cosets

**Definition.** Let $`H \leq G`$ and $`a \in G`$. The **left coset** of $`H`$ containing $`a`$ is

```math
aH = \{ ah : h \in H \}.
```

**Proposition.** The equivalence classes of the relation $`a \sim b \iff a^{-1}b \in H`$ are exactly the left cosets of $`H`$.

**Proof.** We have $`f(a) = f(b)`$ (where $`f: G \to G'`$ is any homomorphism with $`\ker(f) = H`$) $`\iff`$ $`f(a)^{-1}f(b) = e'`$ $`\iff`$ $`f(a^{-1}b) = e'`$ $`\iff`$ $`a^{-1}b \in H`$ $`\iff`$ $`b \in aH`$. $`\square`$

### Cosets Partition $`G`$

For **any** subgroup $`H \leq G`$ (not just kernels), the left cosets of $`H`$ partition $`G`$:

- Every $`a \in G`$ lies in $`aH`$ (since $`a = a \cdot e \in aH`$).
- Two cosets are either **equal** or **disjoint**: if $`aH \cap bH \neq \emptyset`$, then there exists $`c \in aH \cap bH`$, so $`c = ah_1 = bh_2`$ for some $`h_1, h_2 \in H`$, giving $`a^{-1}b = h_1 h_2^{-1} \in H`$, so $`aH = bH`$.

### All Cosets Have the Same Size

**Lemma.** For any $`a \in G`$, the map $`H \to aH`$ given by $`h \mapsto ah`$ is a bijection of sets.

*Proof.* It is injective ($`ah = ah' \implies h = h'`$) and surjective by definition. $`\square`$

In particular, $`|aH| = |H|`$ for all $`a`$.

## 3. The Index and Lagrange's Theorem

**Definition.** The **index** of $`H`$ in $`G`$, written $`[G : H]`$, is the number of distinct left cosets of $`H`$ in $`G`$.

**Theorem (Lagrange's Theorem).** For any subgroup $`H \leq G`$ with $`G`$ finite,

```math
|G| = |H| \cdot [G : H].
```

*Proof.* The cosets partition $`G`$ into $`[G:H]`$ pairwise-disjoint subsets, each of size $`|H|`$. $`\square`$

**Corollary 1.** The order of any subgroup divides the order of the group: $`|H| \mid |G|`$.

**Corollary 2.** The order of any element divides the order of the group: $`\mathrm{ord}(g) \mid |G|`$ for all $`g \in G`$.

*Proof.* Apply Lagrange to $`H = \langle g \rangle`$, which has $`|H| = \mathrm{ord}(g)`$. $`\square`$

**Corollary 3.** For any $`g \in G`$ with $`|G| = n`$: $`g^n = e`$.

### Analogy with Linear Algebra

Lagrange's theorem for groups is analogous to the **rank-nullity theorem** for linear maps:

```math
\dim V = \dim(\ker T) + \dim(\mathrm{Im}\, T)
```

corresponds to

```math
|G| = |\ker(f)| \cdot |\mathrm{Im}(f)|
```

(when $`G`$ is finite and $`f: G \to G'`$ is a homomorphism).

## 4. Application: Order of the Alternating Group

**Proposition.** For $`n \geq 2`$, the alternating group $`A_n`$ has order $`n!/2`$.

*Proof.* The sign homomorphism $`\mathrm{sgn}: S_n \to \{+1, -1\}`$ is surjective (the identity is even; any transposition is odd) with $`\ker(\mathrm{sgn}) = A_n`$. By Lagrange:

```math
|S_n| = |A_n| \cdot |\mathrm{Im}(\mathrm{sgn})| \implies n! = |A_n| \cdot 2 \implies |A_n| = n!/2. \quad \square
```

**Examples:** $`|A_3| = 3`$, $`|A_4| = 12`$, $`|A_5| = 60`$.

## 5. Groups of Prime Order

**Theorem.** If $`|G| = p`$ is prime, then $`G`$ is cyclic, and every non-identity element of $`G`$ is a generator. Furthermore, the only subgroups of $`G`$ are $`\{e\}`$ and $`G`$ itself.

**Proof.** Let $`g \in G`$ with $`g \neq e`$. By Lagrange, $`\mathrm{ord}(g) \mid p`$. Since $`p`$ is prime, $`\mathrm{ord}(g) \in \{1, p\}`$. Since $`g \neq e`$, $`\mathrm{ord}(g) \neq 1`$, so $`\mathrm{ord}(g) = p`$. Thus $`|\langle g \rangle| = p = |G|`$, and since $`\langle g \rangle \subseteq G`$ with $`|\langle g \rangle| = |G|`$, we get $`\langle g \rangle = G`$.

For the second part: any subgroup $`H \leq G`$ has $`|H| \mid p`$, so $`|H| \in \{1, p\}`$, giving $`H = \{e\}`$ or $`H = G`$. $`\square`$

## 6. Simple Groups

**Definition.** A group $`G`$ is **simple** if its only normal subgroups are $`\{e\}`$ and $`G`$ itself.

Intuitively, simple groups cannot be "factored" into smaller groups via a quotient.

**Examples:**
- Every group of **prime order** $`p`$ is simple (and cyclic). These are the only simple **abelian** groups.
- The alternating group $`A_n`$ is simple for all $`n \geq 5`$. (This will be proved later in the course.)

**Theorem (Feit–Thompson, 1963).** Every finite non-abelian simple group has **even** order.

This deep theorem shows that odd-order groups are never simple (unless cyclic of prime order). By the end of the 20th century, mathematicians achieved a **complete classification** of all finite simple groups:
- Cyclic groups $`\mathbb{Z}/p\mathbb{Z}`$ (prime order).
- Alternating groups $`A_n`$ ($`n \geq 5`$).
- Groups of Lie type (e.g., $`\mathrm{PSL}_n(\mathbb{F}_q)`$).
- 26 "sporadic" groups (the largest being the Monster group of order $`\approx 8 \times 10^{53}`$).

## 7. Summary of Coset Machinery

Given $`H \leq G`$ and a homomorphism $`f: G \to G'`$ with $`\ker(f) = H`$:

```math
G = \bigsqcup_{a \in \text{coset reps}} aH, \quad |aH| = |H| \text{ for all } a.
```

The equivalence classes of $`a \sim b \iff f(a) = f(b)`$ are the cosets $`\{aH\}`$. The set of cosets bijects with $`\mathrm{Im}(f)`$. This gives:

```math
|G| = |H| \cdot |\mathrm{Im}(f)|
```

when $`G`$ is finite — a fundamental count underlying all of finite group theory.
