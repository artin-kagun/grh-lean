# The generalized Riemann hypothesis for Dirichlet L-functions

[日本語](README.md) · **English**

[English PDF](grh-en.pdf) · [Overview](OVERVIEW.en.md) · [LaTeX source](grh-en.tex)

This paper presents the formal proof by Levent Alpöge and Claude in ordinary mathematical prose. It follows the `grh/` project, which Luke Sernau and collaborators call the readable edition. The PDF starts with the main theorem and an overview, then gives the detailed argument and a correspondence with the Lean source. The [Japanese PDF](grh-ja.pdf) has the same structure.

The upper bound develops the finite orbit sum in the seesaw identity, the divisibility of theta derivatives, and the elementary-divisor estimate at exceptional places. The dimension estimate derives the Poincaré second moment bound from local Fourier decay. For the lower bound, determinants of relation rows control the projection denominators, and sharp theta coefficients and comparisons of periods give the determinant ratios. We give the forms used and the sources for auxiliary results such as local–global compatibility for automorphic Galois representations and the Weil representation.

The parenthesized “Lean source” notes below the text contain blue links to the pinned source. References beginning with L go to the appendix, which links to individual declarations. Blue blocks headed “Note” contain editorial explanations. The [review record](reviews/2026-11-26-proof-expansion/summary.md) details the passages checked against the source and the auxiliary results cited.

The source is [lsernau/grh-lean at commit 72fead102f66](https://github.com/lsernau/grh-lean/tree/72fead102f663d5c7a407964a13dc0cf9d977207/grh). Verification by Lean's kernel and independent checkers is documented in the [upstream README](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/README.md#checks) and [Andrew Sutherland's report on the same commit](https://math.mit.edu/~drew/shortgrh/). See [NOTICE](../grh/NOTICE) and [LICENSE](../LICENSE) for attribution and licensing.

## Build

Use LuaLaTeX and latexmk. The Japanese edition also requires LuaTeX-ja and the Harano Aji fonts. From `paper/`, the following command builds both PDFs in `.tmp/build/`.

~~~sh
output="$PWD/.tmp/build"
mkdir -p "$output"
cp grh-ja.tex grh-en.tex lean-links.tex lean-correspondence.tex overview-sources.tex "$output/"
cp -R sections sections-en "$output/"
(
  cd "$output"
  TMPDIR="$output" latexmk -lualatex -halt-on-error -interaction=nonstopmode grh-ja.tex grh-en.tex
)
~~~
