# 第7.1節の数学的校閲

対象は日英の §7.1。底本の Lean は 72fead102f663d5c7a407964a13dc0cf9d977207、改訂前の論文は 4272447bcd3dcb7036a625830016aa8f63170f9c。改訂前の `paper/sections/determinant-estimates.tex` の SHA-256 は `1a5c44f5643fb1fdd845bd47d446284170330b316e2f5bbbc53e8595c85f30ff`、英語版は `2393d45a0dd57e471daa17c58a5950b1101215f31681cf67a4be0f0da8f5d1e2`。

## 展開して底本と照合した推論

- `denominator-main-summands.tex`。良い固有形式に \(e_0\) の成分を選び、主合同レベルから局所型を回収する。ずらした跳躍を階数 \(r\) と階数一の両方で検算し、原始根の Frobenius 周期と剰余 Vandermonde により全整行列環を得る。Hecke 多項式の一次項から跡の恒等式を取り、Frobenius の極限で拡張する。照合範囲は `RowsFromEigensystems.lean` 64–223, 268–435, 443–458, 480–560、`AttachedRepresentations.lean` 641–700、`RowsAndColumnsFromLabels.lean` 356–608、`LabelCharacters.lean` 561–600、`Pseudorepresentations.lean` 111–184、`FitTwistsExist.lean` 265–354。
- `denominator-stickelberger.tex`。臨界点が 2 以上では持ち上げの二重類和、点 1 では階数二の行列式周期を用いる。積の係数の分母、有限イデールへの移行、群環への押し出し、指標評価、片側の法を増やした Euler 因子、馴生成元での基準付値を照合した。`AlgebraicPartIntegrality.lean` 70–84, 280–385、`ClassSums.lean` 92–147, 169–385、`LValueSystems.lean` 58–151, 155–229, 236–364。
- `denominator-ribet-block.tex`。主成分と指標の直和の半素性を確かめて跡から整格子を取り、座標行、共通左イデアルと四種の関係、拘束行の双対による主ブロックの長さ、同じ正規化を与える行の選択を追った。`TraceRelations.lean` 402–486、`SemisimpleRepresentations.lean` 352–390、`RibetMatrices.lean` 164–506, 539–571、`FittingBlock.lean` 351–437, 619–669。
- `denominator-local-cost.tex`。Artin–Rees からコサイクルの整格子のグラフを得る段階、局所 Tate 双対の有限係数への移行、結晶条件の相対長さ、純馴分岐と結晶的な三場合、主ブロックと偶奇指標成分への適用を照合した。`LocalLoss/Basic.lean` 386–435、`TateDualBound.lean` 101–277、`CrystallineDefect.lean` 64–98, 217–289, 407–414, 424–535, 538–646、`CrystallineCocycles.lean` 333–545, 571–647、`CupOrthogonalityBounds.lean` 340–423、`CutExponentBounds.lean` 592–653, 805–857, 991–1058、`FewLowJumps.lean` 945–1037、`TraceRelations.lean` 528–638, 673–859、`TateTwistCocycles.lean` 156–240、`RibetElement.lean` 214–270。
- `denominator-ribet-characters.tex`。共通単元行、消去後の余長と双対、同じ指数と先行指数の行の扱い、行列式アイデアル商への \(CX_j\) の入り方、初項の生成と持ち上げ、全指標を同時に揃える行の選択を追った。`FittingBlock.lean` 46–215, 326–347, 484–596, 675–765、`RibetMatrices.lean` 573–780, 782–990。
- `denominator-ribet-multiplier.tex`。Amitsur による係数の降下を nilpotent なずらしと Sylvester の恒等式から追い、補助変数での Cayley–Hamilton、随伴行列、右作用の関係、各ブロックの正規化と重みづけ、イデアルへの所属と最上係数を検算した。`RibetMethod.lean` 51–260, 281–358, 362–427, 441–590。`RibetElement.lean` 105–140, 289 以降で共通素数ごとの係数へ渡す。
- `denominator-odd-classes.tex`。指数ゼロの類群、Bernoulli 行列、二つの法で Euler 因子を外す合同、共役の交換子での指標分解、奇成分の零化を追った。長さには小さい素数で類体論の生成元を使い、大きい素数で Jacobi 族の微分の降順の議論を使う。法 \(\ell\) の相互法則の座標で単元性を使う箇所も記した。`Voronoi.lean` 393–459、`OddSha.lean` 91–255, 414–505, 507–679、`ReciprocityComponentBounds.lean` 380–508, 530–544, 558–740, 806–1164、`DerivativeCocycles.lean` 224–235, 889–1032。

## 本文で使う定理と細部の範囲

標準的な入力として、階数とレベルを満たす代数的固有形式の付随表現と局所大域整合性、Chebotarev、Hilbert 90、大域・局所類体論、Dirichlet \(L\) 関数の関数等式と Euler 積、Artin–Rees、Smith 標準形、局所 Tate 双対・Bloch–Kato の結晶的直交性、Brauer–Nesbitt と Wedderburn を用いる。本文では必要な作用・仮定・結論をその適用箇所に記した。周期の計算では本文の階数一の鋭い内積公式と第一点の行列式周期恒等式を用いる。

深い補助計算のうち、次をこの分担で行ごとに再展開していない。

- `CutExponentBounds.lean` 603–653 の切断点間の延長の比較と、`FewLowJumps.lean` 945以前の深さの局所計算は細部を展開していない。Kummer チャートの入力、切断点と部分加群の構成、三場合の数値比較は本文に記した。
- `ReciprocityComponentBounds.lean` 167–379 の Artin 相互法則の局所退化と `DerivativeCocycles.lean` 320–722 の Jacobi 族の分配、局所還元、微分計算の個々の補題。微分コサイクルの定義、評価関係、および大域 Kolyvagin の降順は本文に記した。`Voronoi.lean` 136–150 の床関数合同には名前と実際に使う形を与えた。
- §7.1.1 の補助素点の構成と剰余体上の指標の選択、§7.1.2 の Taylor–Wiles 素点の検出順序と最後の内積への移行は今回の断片の外。刊行前原稿にもある既存部分であり、今回の断片による再検証には含めていない。

## 統合と確認

日英それぞれ同じ位置で挿入する。主成分は §7.1.1 の「主成分に課される条件」のソースリンク直後。群環値 \(L\) 系は `LValueSystems.lean#L312` のリンク直後、補助素点選択の前。拘束行の四断片は \(K\) を定めた段落の後から、付値の総和に入る段落の前で、順に block、local-cost、characters、multiplier。以前の \(s\) と \((X-1)o_v(X)\) の記述を挿入直前に残す。奇部分は §7.1 最終小項の \(L_\ell\) の表示後から \(e_\ell\) の表示前までを置き換える。

日英 7 組のファイルに対して、波括弧、環境の閉じ方、底本を指定した 27 ファイルのリンクの行が存在することを確認した。全体の組版は統合側で確認する。一時スクリプトは保存していない。
