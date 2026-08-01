# Change of Basis Matrices and Matrix Representations of Linear Transformations

## Summary

A **change of basis matrix** converts the coordinates of a vector from
one basis to another. More generally, if you have a linear
transformation

\[ T:V`\to `{=tex}W, \]

its matrix depends on **two choices of bases**: one for the domain (V)
and one for the codomain (W). Changing either basis changes the matrix
representation, even though the underlying linear map stays the same.

------------------------------------------------------------------------

# 1. Coordinates Depend on the Basis

Suppose (V) is an (n)-dimensional vector space.

Choose a basis

\[ `\mathcal `{=tex}B=(v_1,`\dots`{=tex},v_n). \]

Every vector (v`\in `{=tex}V) can be written uniquely as

\[ v=a_1v_1+`\cdots`{=tex}+a_nv_n. \]

Its coordinate vector is

\[ \[v\]\_{`\mathcal `{=tex}B} =
```{=tex}
\begin{bmatrix}
a_1\\
\vdots\\
a_n
\end{bmatrix}
```
. \]

The coordinate vector is **not** the vector itself---it simply records
the coefficients relative to the chosen basis.

------------------------------------------------------------------------

# 2. Two Different Bases

Suppose we also have another basis

\[ `\mathcal `{=tex}C=(w_1,`\dots`{=tex},w_n). \]

The same vector has coordinates

\[ \[v\]\_{`\mathcal `{=tex}C}. \]

There exists a unique matrix

\[ P\_{`\mathcal `{=tex}C`\leftarrow`{=tex}`\mathcal `{=tex}B} \]

such that

\[ \[v\]*{`\mathcal `{=tex}C} =
P*{`\mathcal `{=tex}C`\leftarrow`{=tex}`\mathcal `{=tex}B}
\[v\]\_{`\mathcal `{=tex}B}. \]

This matrix is called the **change of basis matrix**.

------------------------------------------------------------------------

# 3. Constructing the Change of Basis Matrix

To build

\[ P\_{`\mathcal `{=tex}C`\leftarrow`{=tex}`\mathcal `{=tex}B}, \]

express every basis vector of (`\mathcal `{=tex}B) in terms of the basis
(`\mathcal `{=tex}C).

The coordinate vectors become the columns:

\[ P\_{`\mathcal `{=tex}C`\leftarrow`{=tex}`\mathcal `{=tex}B} =
```{=tex}
\begin{bmatrix}
[v_1]_{\mathcal C}&
[v_2]_{\mathcal C}&
\cdots&
[v_n]_{\mathcal C}
\end{bmatrix}
```
. \]

## Why This Works

If

\[ v=a_1v_1+`\cdots`{=tex}+a_nv_n, \]

then

\[ \[v\]\_{`\mathcal `{=tex}B} =
```{=tex}
\begin{bmatrix}
a_1\\
\vdots\\
a_n
\end{bmatrix}
```
. \]

Multiplying,

\[
P\_{`\mathcal `{=tex}C`\leftarrow`{=tex}`\mathcal `{=tex}B}\[v\]*{`\mathcal `{=tex}B}
= a_1\[v_1\]*{`\mathcal `{=tex}C} +`\cdots`{=tex}
+a_n\[v_n\]\_{`\mathcal `{=tex}C}, \]

which is exactly

\[ \[v\]\_{`\mathcal `{=tex}C}. \]

------------------------------------------------------------------------

# Example

Take

\[ `\mathcal `{=tex}B= `\left`{=tex}{
```{=tex}
\begin{bmatrix}1\\0\end{bmatrix}
```
,
```{=tex}
\begin{bmatrix}0\\1\end{bmatrix}
```
`\right`{=tex}}, \]

and

\[ `\mathcal `{=tex}C= `\left`{=tex}{
```{=tex}
\begin{bmatrix}1\\1\end{bmatrix}
```
,
```{=tex}
\begin{bmatrix}1\\-1\end{bmatrix}
```
`\right`{=tex}}. \]

Expressing the standard basis vectors in basis (`\mathcal `{=tex}C),

\[ \[e_1\]\_{`\mathcal `{=tex}C} =
```{=tex}
\begin{bmatrix}
1/2\\
1/2
\end{bmatrix}
```
, `\qquad
[e_2]`{=tex}\_{`\mathcal `{=tex}C} =
```{=tex}
\begin{bmatrix}
1/2\\
-1/2
\end{bmatrix}
```
. \]

Hence

\[ P\_{`\mathcal `{=tex}C`\leftarrow`{=tex}`\mathcal `{=tex}B} =
```{=tex}
\begin{bmatrix}
1/2&1/2\\
1/2&-1/2
\end{bmatrix}
```
. \]

------------------------------------------------------------------------

# 4. Matrix Representation of a Linear Transformation

Suppose

\[ T:V`\to `{=tex}W. \]

Choose

-   a basis (`\mathcal `{=tex}B) for (V),
-   a basis (`\mathcal `{=tex}D) for (W).

The matrix representation is

\[ \[T\]\_{`\mathcal `{=tex}D`\leftarrow`{=tex}`\mathcal `{=tex}B}, \]

defined by

\[ \[T(v)\]*{`\mathcal `{=tex}D} =
\[T\]*{`\mathcal `{=tex}D`\leftarrow`{=tex}`\mathcal `{=tex}B}
\[v\]\_{`\mathcal `{=tex}B}. \]

## How to Compute It

Take each basis vector of the domain,

\[ v_1,`\ldots`{=tex},v_n, \]

compute

\[ T(v_i), \]

express each image in the codomain basis, and use those coordinate
vectors as columns:

\[ \[T\]\_{`\mathcal `{=tex}D`\leftarrow`{=tex}`\mathcal `{=tex}B} =
```{=tex}
\begin{bmatrix}
[T(v_1)]_{\mathcal D}&
[T(v_2)]_{\mathcal D}&
\cdots&
[T(v_n)]_{\mathcal D}
\end{bmatrix}
```
. \]

------------------------------------------------------------------------

# Example

Let

\[ T(x,y)=(x+y,;2x-y). \]

Choose

\[ `\mathcal `{=tex}B= `\left`{=tex}{
```{=tex}
\begin{bmatrix}1\\1\end{bmatrix}
```
,
```{=tex}
\begin{bmatrix}1\\-1\end{bmatrix}
```
`\right`{=tex}}, `\qquad`{=tex} `\mathcal `{=tex}D= `\left`{=tex}{
```{=tex}
\begin{bmatrix}1\\0\end{bmatrix}
```
,
```{=tex}
\begin{bmatrix}1\\1\end{bmatrix}
```
`\right`{=tex}}. \]

Then

\[ T(1,1)=(2,1), \]

whose coordinates in (`\mathcal `{=tex}D) are

\[
```{=tex}
\begin{bmatrix}
1\\
1
\end{bmatrix}
```
, \]

and

\[ T(1,-1)=(0,3), \]

whose coordinates are

\[
```{=tex}
\begin{bmatrix}
-3\\
3
\end{bmatrix}
```
. \]

Therefore

\[ \[T\]\_{`\mathcal `{=tex}D`\leftarrow`{=tex}`\mathcal `{=tex}B} =
```{=tex}
\begin{bmatrix}
1&-3\\
1&3
\end{bmatrix}
```
. \]

------------------------------------------------------------------------

# 5. Changing the Bases

Suppose the matrix of (T) is known with respect to bases

\[ (`\mathcal `{=tex}B,`\mathcal `{=tex}D), \]

and we switch to new bases

-   (`\mathcal `{=tex}B') for (V),
-   (`\mathcal `{=tex}D') for (W).

Then

\[ \[T\]*{`\mathcal `{=tex}D'`\leftarrow`{=tex}`\mathcal `{=tex}B'} =
P*{`\mathcal `{=tex}D'`\leftarrow`{=tex}`\mathcal `{=tex}D}
\[T\]*{`\mathcal `{=tex}D`\leftarrow`{=tex}`\mathcal `{=tex}B}
P*{`\mathcal `{=tex}B`\leftarrow`{=tex}`\mathcal `{=tex}B'}. \]

Interpretation:

-   Left multiplication changes the **output (codomain) coordinates**.
-   Right multiplication changes the **input (domain) coordinates**.

------------------------------------------------------------------------

# Special Case: (V=W)

If (T:V`\to `{=tex}V), then

\[ \[T\]*{`\mathcal `{=tex}B'} =
P*{`\mathcal `{=tex}B'`\leftarrow`{=tex}`\mathcal `{=tex}B}
\[T\]*{`\mathcal `{=tex}B}
P*{`\mathcal `{=tex}B`\leftarrow`{=tex}`\mathcal `{=tex}B'}. \]

Since

\[ P\_{`\mathcal `{=tex}B`\leftarrow`{=tex}`\mathcal `{=tex}B'} =
P\_{`\mathcal `{=tex}B'`\leftarrow`{=tex}`\mathcal `{=tex}B}\^{-1}, \]

this becomes the familiar similarity transformation

\[ \[T\]*{`\mathcal `{=tex}B'} = P\^{-1}\[T\]*{`\mathcal `{=tex}B}P, \]

or equivalently

\[ P\[T\]\_{`\mathcal `{=tex}B}P\^{-1}, \]

depending on the convention used for the direction of the
change-of-basis matrix.

------------------------------------------------------------------------

# Conceptual Picture

The coordinate maps and the matrix representation fit together as

\[ V `\xrightarrow{\text{coordinates in }\mathcal B}`{=tex}
`\mathbb `{=tex}R\^n
`\xrightarrow{[T]_{\mathcal D\leftarrow\mathcal B}}`{=tex}
`\mathbb `{=tex}R\^m
`\xrightarrow{\text{interpret in }\mathcal D}`{=tex} W. \]

The linear transformation itself never changes. Only its matrix
representation changes when different bases are chosen.
