# ディリクレ L 関数の一般化リーマン予想

**日本語** · [English](README.en.md)

[日本語PDF](grh-ja.pdf) · [概説](OVERVIEW.md) · [LaTeX 原稿](grh-ja.tex)

Levent Alpöge と Claude による形式証明を、Luke Sernau らが整理した
`grh/`（底本の README でいう readable edition）に沿って記述した論文です。
PDF は主定理、証明の概説、詳細な証明、底本との対応表の順に読めます。
同じ構成の [英語PDF](grh-en.pdf) も収録しています。

補助素数の存在、テータ微分の整除性と付値を達成する係数、ポアンカレ級数の局所二次モーメント、
補助捻りと射影分母の評価については、可読版の証明の途中の式も本文で追えます。
Weil 表現の構成や局所軌道の Fourier 評価など、証明で用いる補助定理は適用箇所に出典を示しました。
本文の L で始まる参照番号から、巻末の対応表と Lean の該当行を開けます。
読解のための注記は青字で「補足」と表示しています。

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
