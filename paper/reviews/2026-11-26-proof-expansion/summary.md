# Proof expansion review

## 日本語

比較した刊行稿は `4272447bcd3dcb7036a625830016aa8f63170f9c`。照合対象は [可読版の Lean ソース](https://github.com/lsernau/grh-lean/tree/72fead102f663d5c7a407964a13dc0cf9d977207/grh/src) である。

- シーソーの有限切断、局所 Weil 作用とテータ微分、例外素点とレベル素数での余長、共役とガウス積分を照合した。本文ではさらに、Frobenius の行列積で添字ごとの重みが相殺し、余因子・対称冪を経て単項式の付値条件を得る計算を展開した。 [第5節の記録](workers/upper.md)
- 局所 Fourier 減衰、ノルム選別、軌道の Schur 評価、有限群の型と誘導指標の計数、分岐始域の制限を照合した。安定ベクトルから短い双対を作り、等方枠に沿う商の比較を行列成分へ戻す帰納法も展開した。 [第6節の記録](workers/spanning.md)
- 保型 Galois 表現の主成分、群環に値を持つ $L$ 値系、主成分と指標成分の余長、Ribet の行列式の最高次係数、奇コサイクルの長さを照合した。 [第7.1節の記録](workers/lower.md)
- 第7.2節以降では、短いトレース双対基底で付値を達成する構成、階数一のノルムの正規化、擬似持ち上げの周期の消滅、テータ積分の交換と持ち上げの連鎖、基底を補う形式と最終経路の計算を照合した。日英の各節に、使用した底本のファイルまたは宣言へのリンクを置いた。
- 読解のための注記は「補足」として表示した。テータ交換では局所の Gram 断面に沿った Fourier 変換、階数を落とす定数項、交換の随伴を介して一段の行列式比に至る流れを記した。

本文は保型 Galois 表現の局所大域整合性、Weil 表現の構成、CM 相互法則、Siegel–Weil 公式、離散系列の構成などを補助入力として用いている。法を変える Gauss 和の局所還元や周期環の補助計算には、必要な式や引用先を示した箇所がある。各節の記録に詳しい。この照合は、Lean の全依存宣言や Mathlib の再証明を含まない。

## English

The preceding edition was commit `4272447bcd3dcb7036a625830016aa8f63170f9c`. The source for the comparison was the [pinned readable edition](https://github.com/lsernau/grh-lean/tree/72fead102f663d5c7a407964a13dc0cf9d977207/grh/src).

Sections 5–6 now develop the finite seesaw argument, the elementary-divisor estimates, the local Fourier estimates, and their use in the second moment. Section 7 develops the local and global denominator bounds, the extraction of the top coefficient by determinants, and the constructions and period calculations used in comparing the lifts.

The exposition uses auxiliary results on the Weil representation, local–global compatibility, CM reciprocity, the Siegel–Weil formula, and the construction of discrete series. Some auxiliary reductions for Gauss sums and period rings are invoked in the stated form with pointers to the pinned source. The Japanese section records above specify those boundaries and list the files checked.

## 組版と参照の確認 / PDF and link checks

日本語版は120ページ、英語版は114ページ。概説はいずれも2ページ、ご提示の箇所に対応する参照は日本語版13ページ、英語版12ページにある。組版ログに定義されていない参照、文字の欠落、欄外にはみ出す行の警告はない。本文の括弧付き参照は日本語296箇所、英語298箇所。巻末の対応表への内部リンクと、固定した底本へのリンクの青字表示および各参照先を確認した。
