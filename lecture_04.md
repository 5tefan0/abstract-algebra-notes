# Lecture 4 — Kernels, Normal Subgroups, and Homomorphisms

## 1. Basic Properties of Homomorphisms

Let $f: G \to G'$ be a group homomorphism.

**Proposition.** A homomorphism automatically preserves the identity and inverses:

1. $f(e_G) = e_{G'}$
2. $f(g^{-1}) = f(g)^{-1}$ for all $g \in G$

**Proof of (1).** Since $e \cdot e = e$ in $G$, apply $f$:
$$f(e) \cdot f(e) = f(e \cdot e) = f(e).$$
Multiplying both sides by $f(e)^{-1}$ gives $f(e) = e'$. $\square$

**Proof of (2).** We have $g \cdot g^{-1} = e$, so $f(g) \cdot f(g^{-1}) = f(g \cdot g^{-1}) = f(e) = e'$. By uniqueness of inverses, $f(g^{-1}) = f(g)^{-1}$. $\square$

**Composition.** If $f: G \to G'$ and $h: G' \to G''$ are homomorphisms, then $h \circ f: G \to G''$ is a homomorphism:
$$h(f(xy)) = h(f(x)f(y)) = h(f(x))h(f(y)).$$

## 2. The Kernel

**Definition.** For a homomorphism $f: G \to G'$, the **kernel** is

$$\ker(f) = \{ g \in G : f(g) = e' \}.$$

The kernel is a subgroup of $G$ (since $f(e) = e'$, and if $f(g) = f(h) = e'$ then $f(gh^{-1}) = f(g)f(h)^{-1} = e' \cdot e' = e'$).

**Key fact:** An isomorphism is precisely a homomorphism with $\mathrm{Im}(f) = G'$ and $\ker(f) = \{e\}$.

## 3. Normal Subgroups

The kernel is a special kind of subgroup — a **normal** subgroup.

**Definition.** A subgroup $H \leq G$ is **normal**, written $H \trianglelefteq G$, if

$$gHg^{-1} = H \quad \text{for all } g \in G,$$

where $gHg^{-1} = \{ghg^{-1} : h \in H\}$. Equivalently, $gH = Hg$ as sets for all $g \in G$.

The operation $h \mapsto ghg^{-1}$ is called **conjugation** of $h$ by $g$.

**Theorem.** The kernel of any homomorphism is a normal subgroup.

**Proof.** Let $H = \ker(f)$, and let $h \in H$, $g \in G$ be arbitrary. Then
$$f(ghg^{-1}) = f(g) \cdot f(h) \cdot f(g^{-1}) = f(g) \cdot e' \cdot f(g)^{-1} = e'.$$
So $ghg^{-1} \in \ker(f) = H$. Since $g$ was arbitrary, $gHg^{-1} \subseteq H$ for all $g$, which gives $H \trianglelefteq G$. $\square$

**Observation.** In an abelian group, every subgroup is normal (since $ghg^{-1} = h \in H$ trivially).

### Non-Normal Subgroup

To see that normality is a genuine restriction, consider $S_3$ and the subgroup $H = \{e, \tau\}$ where $\tau = (1\,2)$.

Conjugate $\tau$ by $\tau' = (2\,3)$: compute $\tau' \tau (\tau')^{-1} = \tau' \tau \tau'$ (since $\tau'^2 = e$).

Evaluate on $3$: $\tau'(\tau(\tau'(3))) = \tau'(\tau(2)) = \tau'(1) = 1$.  
So $\tau' \tau \tau'$ takes $3 \mapsto 1$, which is not fixed. Thus $\tau' \tau \tau' = \tau'' = (1\,3) \notin H$.

Hence $\tau' H (\tau')^{-1} = \{e, \tau''\} \neq H$, so $H$ is **not** normal in $S_3$.

## 4. Examples of Kernels and Normal Subgroups

### The Special Linear Group

The **determinant map** $\det: \mathrm{GL}_n(\mathbb{R}) \to \mathbb{R}^*$ is a surjective homomorphism (surjective: given $\lambda \neq 0$, take the diagonal matrix with $\lambda$ in the $(1,1)$ entry and $1$s elsewhere). Its kernel is

$$\mathrm{SL}_n(\mathbb{R}) = \ker(\det) = \{ A \in \mathrm{GL}_n(\mathbb{R}) : \det(A) = 1 \},$$

the **special linear group**. By the theorem above, $\mathrm{SL}_n(\mathbb{R}) \trianglelefteq \mathrm{GL}_n(\mathbb{R})$.

*Direct verification of normality:* For $A \in \mathrm{SL}_n(\mathbb{R})$ and $B \in \mathrm{GL}_n(\mathbb{R})$:
$$\det(BAB^{-1}) = \det(B)\det(A)\det(B^{-1}) = \det(B) \cdot 1 \cdot \frac{1}{\det(B)} = 1.$$
So $BAB^{-1} \in \mathrm{SL}_n(\mathbb{R})$. ✓

### Permutation Matrices

**Definition.** For $\sigma \in S_n$, the **permutation matrix** $A_\sigma$ is the $n \times n$ matrix with

$$(A_\sigma)_{ij} = \begin{cases} 1 & \text{if } i = \sigma(j) \\ 0 & \text{otherwise.} \end{cases}$$

In other words, column $j$ of $A_\sigma$ has a $1$ in row $\sigma(j)$ and $0$s elsewhere.

**Example.** For $\sigma = (1\,2\,3) \in S_3$ (i.e., $1 \mapsto 2, 2 \mapsto 3, 3 \mapsto 1$):

$$A_\sigma = \begin{pmatrix} 0 & 0 & 1 \\ 1 & 0 & 0 \\ 0 & 1 & 0 \end{pmatrix}.$$

The map $S_n \to \mathrm{GL}_n(\mathbb{R})$, $\sigma \mapsto A_\sigma$ is a group homomorphism (injective, since distinct permutations give distinct matrices). The image is the group of **permutation matrices**.

## 5. The Sign of a Permutation and the Alternating Group

Since $\det(A_\sigma) = \pm 1$ for every permutation matrix (only one nonzero term in the determinant expansion), composing the two homomorphisms

$$S_n \xrightarrow{\sigma \mapsto A_\sigma} \mathrm{GL}_n(\mathbb{R}) \xrightarrow{\det} \mathbb{R}^*$$

gives a homomorphism $\mathrm{sgn}: S_n \to \{+1, -1\}$ called the **sign homomorphism**.

**Examples:**
- $\mathrm{sgn}(e) = \det(I) = 1$ (even).
- A transposition $(i\,j)$ has determinant $-1$ (odd).

**Definition.** A permutation $\sigma$ is **even** if $\mathrm{sgn}(\sigma) = +1$ and **odd** if $\mathrm{sgn}(\sigma) = -1$.

The **alternating group** is

$$A_n = \ker(\mathrm{sgn}) = \{ \sigma \in S_n : \mathrm{sgn}(\sigma) = +1 \}.$$

$A_n \trianglelefteq S_n$ (as the kernel of a homomorphism).

**Alternative description.** Any permutation can be written as a product of transpositions. The parity of the number of transpositions used is an invariant (not the number itself, just whether it's even or odd). Even permutations are products of an even number of transpositions.

**Example ($S_3$):**
- Even: $\{e, \sigma, \sigma'\}$ where $\sigma = (1\,2\,3)$ and $\sigma' = (1\,3\,2) = \sigma^2$.  
  So $A_3 = \{e, (1\,2\,3), (1\,3\,2)\}$, a cyclic group of order 3.
- Odd: $\{\tau, \tau', \tau''\}$ (the three transpositions).

## 6. The Center of a Group

**Definition.** The **center** of a group $G$ is

$$Z(G) = \{ z \in G : zg = gz \text{ for all } g \in G \}.$$

The center consists of all elements that commute with **every** element of $G$.

**Properties:**
- $Z(G) \trianglelefteq G$ (normal subgroup). 
- $G$ is abelian $\iff$ $Z(G) = G$.
- $Z(S_n) = \{e\}$ for $n \geq 3$ (no non-identity permutation commutes with all others).
- $Z(\mathrm{GL}_n(\mathbb{R})) = \{ \lambda I : \lambda \in \mathbb{R}^* \}$ (scalar matrices).

## 7. The Conjugation Homomorphism

For any group $G$, there is a natural homomorphism

$$\Phi: G \to \mathrm{Aut}(G)$$

defined by $\Phi(g) = \varphi_g$, where $\varphi_g: G \to G$ is **conjugation by $g$**:

$$\varphi_g(h) = ghg^{-1}.$$

**$\varphi_g$ is an automorphism:** $\varphi_g(hh') = g(hh')g^{-1} = (ghg^{-1})(gh'g^{-1}) = \varphi_g(h)\varphi_g(h')$, and $\varphi_g$ is bijective with inverse $\varphi_{g^{-1}}$.

**$\Phi$ is a homomorphism:**
$$\varphi_{gg'}(h) = gg'h(gg')^{-1} = g(g'hg'^{-1})g^{-1} = \varphi_g(\varphi_{g'}(h)) = (\varphi_g \circ \varphi_{g'})(h).$$
So $\Phi(gg') = \Phi(g) \circ \Phi(g')$. ✓

**The kernel of $\Phi$:**
$$\ker(\Phi) = \{ g \in G : ghg^{-1} = h \text{ for all } h \in G \} = Z(G).$$
So the center is the kernel of the conjugation map.

**Definition.** The image $\Phi(G) \leq \mathrm{Aut}(G)$ consists of the **inner automorphisms** of $G$.

### Automorphism Group of the Klein Four-Group

For $V_4 = \{e, \tau_1, \tau_2, \tau_3\}$, every inner automorphism is trivial (since $V_4$ is abelian, $Z(V_4) = V_4$, so the conjugation map has trivial image).

However, $\mathrm{Aut}(V_4) \cong S_3$. Here is why: any automorphism of $V_4$ must permute the three non-identity elements $\{\tau_1, \tau_2, \tau_3\}$ (they all have order 2 and cannot be sent to $e$). Conversely, any permutation of $\{\tau_1, \tau_2, \tau_3\}$ extends to an automorphism of $V_4$ (since the multiplication table $\tau_i \tau_j = \tau_k$ is symmetric under relabeling). This gives an isomorphism $\mathrm{Aut}(V_4) \cong S_3$.

So $V_4$ has trivial inner automorphism group but non-trivial full automorphism group $S_3$.
