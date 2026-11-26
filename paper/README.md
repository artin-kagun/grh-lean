# ディリクレ L 関数の一般化リーマン予想

**日本語** · [English](README.en.md)

[日本語PDF](grh-ja.pdf) · [概説](OVERVIEW.md) · [LaTeX 原稿](grh-ja.tex)

Levent Alpöge と Claude による形式証明を、Luke Sernau らが整理した
`grh/`（底本の README でいう readable edition）に沿って記述した論文です。
PDF は主定理、証明の概説、詳細な証明、底本との対応表の順に読めます。
同じ構成の [英語PDF](grh-en.pdf) も収録しています。

上界では、シーソーの有限軌道和、テータ微分の整除性、例外素点での単因子評価を展開しています。
次元評価では、局所 Fourier 減衰からポアンカレ級数の二次モーメントを評価します。
下界では、射影の分母を拘束行の行列式で抑え、付値を達成するテータ係数と周期の比較から行列式比を求めます。
保型 Galois 表現の局所大域整合性や Weil 表現などの補助理論は、用いる形と出典を記しています。
本文の下に括弧で置いた「Lean 参照」の青字は、固定した底本へのリンクです。
L で始まる番号からは、巻末の対応表を経て個々の宣言を開けます。
読解のために付した注記は青字で「補足」と表示しています。
底本との照合範囲と引用した補助結果は[校閲記録](reviews/2026-11-26-proof-expansion/summary.md)に記載しています。

底本は [lsernau/grh-lean のコミット 72fead102f66](https://github.com/lsernau/grh-lean/tree/72fead102f663d5c7a407964a13dc0cf9d977207/grh) です。
Lean カーネルと独立チェッカーによる検証は [底本の README](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/README.md#checks) と、
同じコミットを調べた [Andrew Sutherland の記録](https://math.mit.edu/~drew/shortgrh/) に掲載されています。
原典の帰属とライセンスは [NOTICE](../grh/NOTICE) および [LICENSE](../LICENSE) を参照してください。

## 組版

LuaLaTeX と latexmk を使います。日本語版には LuaTeX-ja と Harano Aji フォントが必要です。
`paper/` から次を実行すると、両方の PDF が `.tmp/build/` にできます。

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
