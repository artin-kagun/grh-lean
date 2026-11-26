# The generalized Riemann hypothesis for Dirichlet L-functions

[日本語](README.md) · **English**

[English PDF](grh-en.pdf) · [Overview](OVERVIEW.en.md) · [LaTeX source](grh-en.tex)

This paper presents the formal proof by Levent Alpöge and Claude in ordinary mathematical prose. It follows the `grh/` project, which Luke Sernau and collaborators call the readable edition. The PDF starts with the main theorem and an overview, then gives the detailed argument and a correspondence with the Lean source. The [Japanese PDF](grh-ja.pdf) has the same structure.

The proofs include the existence of the auxiliary primes, both bounds for the theta coefficients, the local estimates for the second moment, and the choice of twists and control of projection denominators. The paper cites auxiliary results at their points of use, including the construction of the Weil representation and Fourier estimates for local orbits. References beginning with L link to the appendix and from there to the relevant source lines. Blue notes contain editorial explanations.

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
