# GRH for Dirichlet L-functions, in Lean 4

## 日本語

ディリクレ L 関数の一般化リーマン予想の形式証明を、`grh/`（元のREADMEでいう readable edition）に沿って日本語で記述しました。PDF に証明の概説と、青字の Lean 参照を収録しています。

[論文PDF](paper/grh-ja.pdf) · [証明の概説](paper/OVERVIEW.md) · [原稿と組版手順](paper/README.md)

## English

An exposition of the formal proof of Dirichlet GRH, following the readable edition in `grh/`. The PDF includes a proof overview and links to the Lean source.

[Paper PDF](paper/grh-en.pdf) · [Proof overview](paper/OVERVIEW.en.md) · [Sources and build instructions](paper/README.en.md)

## Upstream Lean development

The Lean 4 development proves the Riemann hypothesis and the generalized
Riemann hypothesis for Dirichlet L-functions. It builds on Mathlib and uses
the axioms `propext`, `Classical.choice`, and `Quot.sound`.

[Luke Sernau and collaborators' repository](https://github.com/lsernau/grh-lean)
contains a shorter version of the proof announced by
[Levent Alpöge with Claude](https://alpo.ge/remark.pdf).

### Two editions

- [`grh/`](grh/GUIDE.md) is the readable edition, about 300,000 lines.
- [`grh-compact/`](grh-compact/README.md) proves the same five theorems in about 76,000 lines.

Each folder is its own Lake project. The machine checks are documented in
the [readable edition's README](grh/README.md#checks) and the
[compact edition's README](grh-compact/README.md#checks).

### Build the Lean development

Use Lean v4.35.0 and Mathlib at commit 56a00585. In either folder:

    lake exe cache get
    lake build
    lake env lean scripts/PrintAxioms.lean

A build takes one to two hours on 12 cores with 24 GB of memory (about
85 minutes more if the Mathlib cache is missing).

### License

Apache 2.0, Copyright 2026 Anthropic, PBC. See [LICENSE](LICENSE) and
the `NOTICE` and `ATTRIBUTION.md` files in each Lean folder.
