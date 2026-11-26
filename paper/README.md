# ディリクレ L 関数の一般化リーマン予想

[日本語論文 PDF](grh-ja.pdf) · [証明の概説](OVERVIEW.md) · [LaTeX 原稿](grh-ja.tex)

Levent Alpöge と Claude による形式証明を、Luke Sernau らが整理した可読版を底本として日本語で再構成した稿です。素数冪和から零点を排除する解析、補助データの作り方、テータ持ち上げの上下の評価、ポアンカレ写像で必要な次元を確保する議論を、定理・補題・証明の形で記述しました。

局所テータ核、二次モーメントの局所密度、合同による射影の分母など、一部の技術的評価は使用する仮定と結論を本文に示して底本の宣言を引用しています。読解のために付した注記には青字で「補足」と表示しています。

底本は [lsernau/grh-lean の可読版](https://github.com/lsernau/grh-lean/tree/72fead102f663d5c7a407964a13dc0cf9d977207/grh)（`72fead102f663d5c7a407964a13dc0cf9d977207`）です。Lean と独立チェッカーによる検証結果は [底本の README](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/README.md#checks) と、同じコミットを検証した [Andrew Sutherland の記録](https://math.mit.edu/~drew/shortgrh/) を参照してください。原典の帰属とライセンスは [NOTICE](../grh/NOTICE) および [LICENSE](../LICENSE) に従います。

## 組版

LuaLaTeX、LuaTeX-ja、Harano Aji フォント、latexmk を備えた環境で、`paper/` から実行します。

~~~sh
mkdir -p .tmp/build
latexmk -lualatex -outdir=.tmp/build -halt-on-error -interaction=nonstopmode grh-ja.tex
~~~

生成先は `.tmp/build/grh-ja.pdf` です。
