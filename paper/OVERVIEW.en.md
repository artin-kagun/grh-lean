# How the proof of Dirichlet GRH works

[English paper](grh-en.pdf) · [日本語の概説](OVERVIEW.md)

Iterating about $\sqrt{x}$ theta lifts puts a factor of $m$ in front of the remainder of a prime-power sum of length $x$. Comparing upper and lower bounds for the same Gram determinant cancels a common main term and leaves an upper bound for the remainder. This overview also appears in the PDF. [Upstream readable edition](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/GUIDE.md)

## 1. Why iterate the theta lift?

Stepanov's method for curves over finite fields compares the total order of vanishing of an auxiliary function with its degree. Alpöge's announcement describes iterated theta lifts over number fields as taking the role of this multiplicity. Zhang's account of the original proof also traces how the leading finite-place valuation gains grow with the number $m$ of lifts. [Alpöge, pp. 1 and 4](https://alpo.ge/remark.pdf) · [Zhang, §4.1](https://www.ihes.fr/~rzhang/files/GRH%20note.pdf#page=27)

The readable edition measures divisibility after differentiating a theta kernel. At an inert prime $p$ of the imaginary quadratic field $K$, the factor $1-\chi_K(p^j)$ selects the odd powers of $p$. Weighting the local gains by $2\log p$ and summing gives the relevant weighted prime-power sums. A seesaw identity connects the chain on which divisibility is computed to the chain whose Gram determinant is estimated. [Local prime sums and gains](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/src/New/UpperBound/Size/ShortColumns.lean#L65-L83) · [Paper, §5](sections-en/upper-bound.tex)

## 2. The determinant comparison

Let $c$ bound the logarithm of the squared covolume of $n$ lifted forms, and let $\delta$ bound the logarithmic index required for integrality at the finite places. The index occurs twice because the Hermitian pairing has an integrality condition on each variable. Write $h$ for the target dimension, $H_0$ for the common main term, and $\mathcal R$ for the total remainder. Set $E_j=fa(\log b)^j$, where $f$ is the number of infinite places, $b$ is the weight at the selected places, and $a=xb$. The comparison is

$$
\begin{aligned}
 h(H_0-3E_4)
 &\le c+2\delta\\
 &\le n(H_0-m\mathcal R+E_4)+20h\log(1+2b^2)E_3 .
\end{aligned}
$$

- **Upper bound.** Divisibility provides a normalization of the Poincaré map. Bounding the archimedean norms of its images yields $H_0-m\mathcal R$ up to the error. A second moment for translates supplies $n\ge(1-4/b^2)h$ independent images of short forms. [Theorems A and B](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/src/New/Reduction/ShortAndEnough.lean) · [Paper, §5](sections-en/upper-bound.tex) · [§6](sections-en/spanning.tex)
- **Lower bound.** Select a twist at each finite place and compare its Gram determinant with the untwisted one. The height of this ratio involves Hecke $L$-values and denominators of the projections to the spaces of lifts. Applying the product formula gives the same $H_0$. [Theorem C](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/src/New/Determinant/Twist/LongForms.lean) · [Paper, §4](sections-en/lattices.tex) · [§7](sections-en/determinant-estimates.tex)

Since $n\le h$, $H_0\ge0$, and $n\ge h/2$, the comparison gives $m\mathcal R\le fa(\log b)^5$. The choice of two weights at infinity gives an identity expressing $\mathcal R$ through the remainder $R_{q_0}(x)$ and terms at a larger cutoff $x_1$. The fixed-modulus prime number theorem bounds the terms at $x_1$, leaving $\varphi(q_0)(\log b)^6/m$. With $m\ge\sqrt{x}$ and $\log b$ bounded by an appropriately small power of $x$, this yields $R_{q_0}(x)\le x^{-1/2+\varepsilon}$. [The comparison inequality](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/src/New/Reduction/MainInequality.lean) · [Paper, §8](sections-en/conclusion.tex)

> **Note on the square-root scale.** The working guide to the zeta case published by Michael Rubinstein explains how two errors in the original proof balance at $m\asymp\sqrt x$. After normalizing by the coefficient of the prime sum, their sizes are $x/m$ and $m$. The inequality above uses the normalization of the readable edition. [Rubinstein's guide, version 2, §§I.7–I.9](https://math.uwaterloo.ca/~mrubinst/alpoge_claude_grh/zeta-paper_v2.pdf#page=18)

## 3. Why the upper bound suffices

For an auxiliary prime $d$, $R_{q_0}(x)$ is the remainder after subtracting $\log x/\varphi(q_0)+c_{q_0}$ from

$$
\sum_{\substack{n\le x\\n\equiv1\bmod q_0}}
 \Lambda(n)\bigl(1-(n/d)\bigr)\left(\frac1n-\frac1x\right).
$$

In the transform of the remainder, zeros of the original $L$-functions and zeros of the quadratic twists enter with opposite residue signs. Choose $d$ to avoid twisted zeros in the region containing the candidate zero. The residues on the real axis are then nonnegative. Subtracting the remainder from its one-sided upper bound gives a nonnegative density after normalization. Landau's lemma excludes the pole associated to the candidate zero. The functional equation then gives the assertion on the other side of the critical line. [Zero-free criterion](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/src/New/Reduction/Zeros/Criterion.lean) · [Paper, §2](sections-en/analytic.tex)

## Related accounts

- Siniša Slijepčević explains the original proof's passage from local gains and a slope inequality to one-sided estimates. Its analytic reduction is stated on intervals $[Y,Y^{3/2}]$ with arbitrarily large $Y$. [Outline, §1.3](https://hexagonmath.org/pdf/2611.00812#page=3)
- Robin Zhang traces the repeated theta lifts and the comparison of lattices and periods in the original proof. [Preliminary note, §§1 and 4](https://www.ihes.fr/~rzhang/files/GRH%20note.pdf)
- The working guide published by Michael Rubinstein specializes the original argument to the Riemann zeta function and specifies the inputs it takes from Lean. [Guide and project page](https://math.uwaterloo.ca/~mrubinst/alpoge_claude_grh/)

For the readable edition's formulas, start with §8 of the paper, then follow §§3–7 and return to §2. Andrew Sutherland's verification records cover both Lean editions at the same pinned commit as this exposition. [English paper](grh-en.pdf) · [Sutherland's verification record](https://math.mit.edu/~drew/shortgrh/)
