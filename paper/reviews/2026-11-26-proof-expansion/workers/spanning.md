# 第6節の校閲記録

## 対象

- 底本 `72fead102f663d5c7a407964a13dc0cf9d977207` の `grh/src`。
- 比較した刊行稿 `4272447` の `paper/sections/spanning.tex` と `paper/sections-en/spanning.tex`。
- `git diff --quiet 72fead102f66 -- grh/src` により、読んだ作業木の底本が固定底本と一致することを確認。

## 本文に展開した推論

| 本文の箇所 | 照合した底本のファイルと範囲 `grh/src/` から | 照合内容 |
| --- | --- | --- |
| 共通格子を数える際の一軌道の振幅 | `New/Spanning/RemainingTerms/Size.lean` 236–306, 309–376, 440–551, 577–703, 737–793行、`RemainingTerms/SchurTest.lean` 37–62, 100–142, 242–299行、`RemainingTerms/SchurOrbit.lean` 195–228, 413–633, 638–775, 806–1006行、`RemainingTerms/OneRealPlace.lean` 919–1010行 | 判別式と首座小行列式による分岐、相反する体積比、等方行格子の指数、Eichler 平行移動による格子和の展開、Hua 型局所積分、左右の指数と \(M,b,\tau\) の比較。 |
| 大細胞での局所積分と軌道展開 | `New/Spanning/Bessel/OpenCellBound.lean` 355–474, 605–739行、`Bessel/SobolevBound.lean` 582–654行、`Bessel/OpenCellPairing.lean` 95–212, 240–275行、`RemainingTerms/OrbitSize.lean` 64–154, 165–259, 266–377行 | Gram 断面上の微分評価から作用素の二乗評価へ移す際の測度の正規化、コンパクト台とテンソル積化、切断誤差、\(10^5n^4+k-1\) の減衰を \(k\) 乗に換える比較。 |
| ノルムの選別と球面密度 | `Lib/SiegelWeil/OneVector/SiegelClassSum.lean` 152–211, 373–472, 565–600, 654–754行、`New/Spanning/MainTerm/SiegelTopBound.lean` 119–235, 420–451行、`Lib/SiegelWeil/OneVector/FinitePlaceDensity.lean` 580–693行 | 一ベクトルの公式の適用条件、ユニポテント Fourier 係数によるノルム選別、剪断直線の零項の展開、Gaussian と測度の定数、有限テストの分解、縮む集合での平均による反転。 |
| 局所形式と2種類の Fourier 評価 | `New/Spanning/Frames/Correlations.lean` 45–85, 446–535行、`Frames/QuadricPlancherel.lean` 96–148, 170–238, 260–384行、`Frames/Gains.lean` 155–333, 370–465, 474–602, 862–998行、`Lib/DiscreteSeries/Bruhat/FourierKernels.lean` の二つの二次曲面の核 | 双曲対を除いた商での局所形式、共通の座標と逆数差の二つの位相、2組の独立座標による二次曲面上の Plancherel、深さの逆重みを交差させる Cauchy–Schwarz。 |
| 深さ・分母による局所減衰 | `New/Spanning/Frames/Levels.lean` 177–224行、`Frames/OneFrame.lean` 65行以降、`Frames/Shells.lean` 34–48, 92–280行、`Frames/FiniteDepth.lean` 221–411行、`Frames/FiniteShells.lean` 112–316, 384–552, 596–742行、`Frames/RealShells.lean` 353–575, 597–700行、`MainTerm/FiniteSieveSystem.lean` 110–134, 285–335行 | 有限素点の分母イデアルと無限素点の位置の箱、深さの利得、指数を \(H^{-1}\) に残す総和、有限素点で先頭積から尺度を作る計算、分母指数の三乗と無限素点の \(\min(1,|\xi|^{-6})\) の導出。 |
| 零段の評価 | `New/Spanning/Frames/BesselVector.lean` 590–655行、`Frames/RealBandLimits.lean` 305–387, 407–640行、`MainTerm/FiniteSieveSystem.lean` 58–82, 145–198行 | 局所 Bessel ベクトルのペアリングの台とその体積、切断前の係数の Schur 直交性、近い箱での一様切断誤差、遠い箱の減衰と \(1+b^{-10}\) の定数。 |
| 良い型への射影と誘導指標 | `Lib/LocalGL/Green/TauFunctions.lean` 655–798行、`Lib/Analytic/Primes.lean` 34–78行、`New/Spanning/MainTerm/BadTypes.lean` 45–191, 221–274行、`SecondMoment/SpanningTheorem.lean` 214–250行、`Unfolding/Moments.lean` 680–777, 840–961, 991–1024行 | Green の積と単位元での重みの下界、ラベルの除外計数、二つのレベル素数の射影、有理 Bessel 元の固定成分の消滅、還元剰余類から共役平均の \(L^2\) 評価を得る計算。 |
| 分岐始域の制限 | `New/UpperBound/Size/ShortColumns.lean` 470–528, 675–760, 818–958行、`New/UpperBound/Objects/LiftChains.lean` 535–542行、`Lib/Shimura/HeckeTower/HeckeData.lean` 929–975行 | 剰余体のスカラー作用の位数、自由なレベル間での類数の比、幾何級数の核と可換作用素の積の像、余次元の総和。 |

## 残る引用の境界

- 階数一 Siegel–Weil 公式そのもの、Poisson 和公式、Plancherel、Schur の直交関係、Hua 積分で用いる行列式積分、Green の有限群の指標理論は背景の結果として用いた。本文には、この証明で使う仮定・規格化および数値への換算を記した。
- §6 の使用する Bessel 系、整基底、Weil 表現の構成は全体を再構成していない。特に `New/Spanning/Bessel/FillingData.lean` に依存する離散系列の選択、定常位相と導関数の各評価、および `New/Spanning/Frames/FiniteDepth.lean` の安定ベクトルから行列成分を復元する全成分の校閲は、この分担の本文では補助入力として残る。
- 上の表は形式化の各行を独立に再証明したという記録ではない。数式の定数、両言語の式と参照、および本文へ補った推論を固定底本の宣言・証明と照合した。Lean の実行と PDF の組版は親担当の統合確認に委ねた。

統合稿では、安定ベクトルの双対成分による正規化、商空間の一段での補正、および全空間での行列成分の読取りも展開した。Depth.lean 778–905 行と TwoGauges.lean 97–203 行を照合した。
