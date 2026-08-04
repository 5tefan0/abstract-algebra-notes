# Quotient Groups, Normal Subgroups, and Kernels

## 1. Cosets and Lagrange's Theorem

Let $`H \le G`$ be a subgroup.

The **left cosets** of $`H`$ are

```math
aH=\{ah:h\in H\}.
```

The left cosets partition $`G`$. Therefore, if $`G`$ is finite,

```math
|G| = |H|\,[G:H],
```

where $`[G:H]`$ is the number of left cosets.

This is **Lagrange's Theorem** and does **not** require $`H`$ to be normal.

---

## 2. When do the cosets form a group?

The natural candidate for multiplication is

```math
(aH)(bH)=(ab)H.
```

This multiplication is well-defined **if and only if** $`H\trianglelefteq G`$.

Therefore:

- If $`H\trianglelefteq G`$, then $`G/H`$ is the **quotient group**.
- If $`H`$ is not normal, then $`G/H`$ is only a set of cosets.

---

## 3. Why is normality necessary?

Suppose

```math
aH=a'H,\qquad bH=b'H.
```

For multiplication to be well-defined we must have

```math
(ab)H=(a'b')H.
```

If this fails, then the product depends on the chosen representatives.

### Example

Let

```math
G=S_3,\qquad
H=\{e,(12)\}.
```

The subgroup $`H`$ is **not** normal.

Since

```math
H=eH=(12)H,
```

compute the product in two different ways.

Using the representative $`e`$,

```math
(eH)((13)H)=(13)H.
```

Using the representative $`(12)`$,

```math
((12)H)((13)H)
=((12)(13))H
=(132)H.
```

But

```math
(13)H\neq(132)H.
```

Therefore the multiplication is **not well-defined**, so the cosets cannot form a quotient group.

---

## 4. Intuition

A coset is an **equivalence class**, just like a rational number.

For example,

```math
\frac12=\frac24.
```

Any operation on equivalence classes must give the same result regardless of which representative is chosen.

Normality is precisely the condition that guarantees this for cosets.

---

## 5. Kernels

Given a homomorphism

```math
\varphi:G\to K,
```

its kernel is

```math
\ker(\varphi)=
\{g\in G:\varphi(g)=e_K\}.
```

Every kernel is a normal subgroup.

Indeed,

```math
\varphi(ghg^{-1})
=
\varphi(g)\varphi(h)\varphi(g)^{-1}
=
e,
```

so

```math
g\,\ker(\varphi)\,g^{-1}
=
\ker(\varphi).
```

Hence

```math
\ker(\varphi)\trianglelefteq G.
```

---

## 6. Two ways to construct quotient groups

### Method 1 — Start with a homomorphism

Given

```math
\varphi:G\to K,
```

1. Compute

   ```math
   H=\ker(\varphi).
   ```

2. Since $`H`$ is normal, form

   ```math
   G/H.
   ```

3. By the First Isomorphism Theorem,

   ```math
   G/H\cong\mathrm{Im}(\varphi).
   ```

---

### Method 2 — Start with a normal subgroup

Given

```math
H\trianglelefteq G,
```

form the quotient group

```math
G/H.
```

The natural projection is

```math
\pi:G\to G/H,\qquad
g\mapsto gH,
```

whose kernel is

```math
\ker(\pi)=H.
```

---

## 7. First Isomorphism Theorem

For every homomorphism

```math
\varphi:G\to K,
```

```math
G/\ker(\varphi)\cong\mathrm{Im}(\varphi).
```

---

## 8. Normal subgroups

A group may have many normal subgroups.

Examples:

- $`A_5`$: only $`\{e\}`$ and $`A_5`$.
- $`S_3`$: $`\{e\}`$, $`A_3`$, and $`S_3`$.
- Every subgroup of an abelian group is normal.

However, a **single homomorphism** has exactly **one** kernel.

---

## 9. Correspondence

There is a one-to-one correspondence

```math
\boxed{
\text{Normal subgroups of }G
\longleftrightarrow
\text{Kernels of homomorphisms from }G.
}
```

Every normal subgroup is the kernel of the canonical projection

```math
G\to G/H,
```

and every homomorphism has a unique kernel.

---

## 10. Action on cosets

Even when $`H`$ is not normal, there is always a homomorphism

```math
G\longrightarrow \mathrm{Sym}(G/H),
```

defined by

```math
g\cdot(aH)=gaH.
```

Here $`G/H`$ is viewed only as a **set**, and $`\mathrm{Sym}(G/H)`$ is the permutation group of that set.

The kernel is

```math
\mathrm{Core}_G(H)
=
\bigcap_{g\in G} gHg^{-1},
```

the largest normal subgroup contained in $`H`$.
