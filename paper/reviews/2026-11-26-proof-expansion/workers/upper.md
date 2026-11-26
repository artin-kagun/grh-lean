# 第5節「上界」の数学的校閲記録

対象は日英の上界節。比較した刊行版は 4272447bcd3dcb7036a625830016aa8f63170f9c、底本は 72fead102f663d5c7a407964a13dc0cf9d977207。以下の Lean ファイルは底本の grh/src/ を起点とする。既存のテータ微分、方向選択、ヘッケ移送、ガウス積分の証明に続けて、下記を作成・照合した。

## シーソーの有限切断

- Lib/Weil/Periods/GradedLattice.lean:127–185,189–208,230–325 の次数付き Gram 行列と有限ユニポテント代表を追記した。非負次数の列の同じ Gram 行列に整 Witt 延長を適用し、次数零成分の可逆性と、変更行列が次数を上げることを示した。
- Lib/Weil/Periods/PointLattice.lean:425–461、Lib/Weil/Periods/LatticeBounds.lean:111–144,154–219、New/UpperBound/Seesaw/Frequency.lean:222–287,291–340、New/UpperBound/Seesaw/StandardLines.lean:478–563、New/UpperBound/Seesaw/UnfoldingStages.lean:973–1001,1005–1168、New/UpperBound/Seesaw/Sandwich.lean:112–232 を照合した。定数項で残る周波数の負次数成分を使う格子包含、標準格子の射影と共通部分の差、レベル素数での分岐による例外軌道の消滅を追記した。
- New/UpperBound/Seesaw/Cut.lean:40–122、New/UpperBound/Seesaw/IntegralAsCosetSum.lean:61–101,123–202 を照合した。有限商による軌道代表の有限性、支えの局所化、剰余群での安定化群の重みを追記した。
- 格子基底の Hermite 形と、原始列の組に対する整 Witt 延長を所定の仮定で使う。整係数の Witt 延長の補助証明は Lib/Adelic/Witt/WittTheorem.lean:326–381,442–529 にある。

## 標準データと全素数での整性

- Lib/Weil/Construction/VacuumProjections.lean:713–779、Lib/Weil/Construction/FiniteMultiplier.lean:989、New/UpperBound/Seesaw/AdmissibleCombinations.lean:445–480、New/Derivatives/Vacuum/JetIntegrality.lean:288–324 を照合した。真空直線への有限格子平均から Weil 作用の剰余類和を導き、標準データを作用が保つ理由を追記した。
- New/Derivatives/Vacuum/JetIntegrality.lean:72–98,100–194、New/Derivatives/Vacuum/Divisibility.lean:48–113、New/UpperBound/Divisibility/LocalDivisibility.lean:155–181 を照合した。CM の形式パラメータ、テータおよびその対数微分で生成する環を微分が保つこと、定数項の整性と規格化の比の冪を追記した。

## 例外素数のヘッケ作用素と単因子

- New/UpperBound/Divisibility/MarkOperator.lean:55–124,301–337,345–414 と New/UpperBound/Divisibility/HeckeEdges.lean:384–449,459–499,512–616,652–689,707–839 で、剰余体の Frobenius サイクル、両端の基底とパラホリック剰余類、座標模型から整保型形式への移送を照合した。
- New/UpperBound/ElementaryDivisors/Edges.lean:295–380,421–482,495–510,601–688、New/UpperBound/ElementaryDivisors/Depth.lean:548–659,727–795、New/UpperBound/ElementaryDivisors/ElementaryDivisorTheorem.lean:293–333,769–863,875–914 を照合した。中間格子の規格化指数、対角ペアリングでの転置随伴性、正規化ヘッケ作用の両端での因数分解と、飽和余長を抑える深さの計数を追記した。
- New/UpperBound/ElementaryDivisors/TwistingData.lean:147–192、New/UpperBound/ElementaryDivisors/Edges.lean:700–805、New/UpperBound/ElementaryDivisors/DefectCount.lean:665–784,939–983、New/UpperBound/ElementaryDivisors/AveragingMap.lean:451–616 を照合した。境界根の欠損量、欠損量の合同条件、旗と格子点の次元評価、平均のペアリング合同を追記した。
- New/UpperBound/ElementaryDivisors/ElementaryDivisorTheorem.lean:59–98,142–249,617–725,918–986,990–1214 を照合した。近似逆の積の合同、Smith 形で選んだ補空間の列の剰余体での独立性、Nakayama の補題による法の除去、二つの行列式と法の追加列の損失の加算を追記した。
- Depth.lean:95–121,245–367,383–546 と Lib/General/Algebra/MultivariatePolynomials.lean:182–245 に基づき、深い変数の冪の復元に使う unipotent 行列の位置、連立系の可逆性、重み付き除法と Taylor 係数空間の比較を追記した。RootLemma.lean:57–80,248–266,391–397,466–505,509–609,623–761,876–958,976–1067 から、補助多項式の置換と二つの Gauss 重み、一次因子の互いに素な積、欠損量の付値への帰着を追記した。
- DefectCount.lean:201–269,455–488,529–575,600–784,899–983 と PieriCone.lean:48–108,161–205,245–304,366–417,436–527 から、一つの多項式への係数の詰め込み、旗での最小高さの項、次数を切った格子点の体積、交互配置の指示行列式から一文字への帰着を追記した。
- InvariantAverage.lean:296–339,375–399,445–482,514–530,625–649,743–784,876–969、FrobeniusFactors.lean:67–103,727–779、AveragingMap.lean:381–449,477–499,512–616 に基づき、高い重みの部分空間のトレースを引く平均、共役不変性、Frobenius を進める行列積の重みの誤差、出力の合同の二つの適用を追記した。
- 補助証明の境界。FrobeniusFactors.lean:259–780 の内部で行列積の成分から Gauss フィルトレーションを導く一連の補正は、本文では具体的な指数とその誤差の出所を記し、個々の四則演算のフィルトレーション補題の証明までは展開していない。

## レベル素数 N

- New/UpperBound/Divisibility/ColengthAtLevel.lean:75–288、New/UpperBound/Divisibility/SetupAtLevel.lean:32–86,245–319、New/UpperBound/Objects/LiftLawsModuloN.lean:154–224,380–399,511–540,623–825,860–930 を照合した。最後の座標の格子変更、行と列を指定した持ち上げの構成、剰余群上の置換、上昇作用素のレベル不変性、標準充填による余長、逆像の反復、接合データからの非原始項の消去を追記した。
- New/UpperBound/Divisibility/ValuationAtLevel.lean:53–214,225–320,323–439,449–557 を照合した。角の条件と上昇作用素の可換式、二段の定数、直接のデータへ変換した後のテータ微分の分母、合計の損失を追記した。

## 無限素点

- Lib/CM/ChowlaSelberg.lean:364、New/Derivatives/Vacuum/IntegralVacuum.lean:56–100,225–276,361–381,595–650、New/Derivatives/Vacuum/TightFrames.lean:509–523、New/UpperBound/Kernels/JetConjugatesAndBounds.lean:98–136,149–215,238–273 を照合した。半周期のテータ関数についての CM 相互法則の使用形、共役したテータ積から有限 Heisenberg 平行移動上に半線形写像を作る手順、付随する加法指標の共役則、面積と尺度の関係を追記した。
- Lib/Weil/DualPair/GaloisLaw.lean:53–166,234–309,377–385 を照合した。有限平行移動の共役をノルム 1 の因子と単元の因子に分け、Weil 作用の共役乗数が絶対値 1 であることを追記した。
- New/UpperBound/Kernels/JetConjugatesAndBounds.lean:283–434,446–489、Lib/General/Analysis/PackingAndSobolev.lean:38–83 を照合した。真空の行列係数のテータ和、台の二乗ノルムの整性、球の体積による充填、階数 1 の有界性から積と Hilbert ノルムを経由する一様評価を追記した。
- Lib/Weil/Construction/ThetaJets.lean:85–112、Lib/Weil/MixedModel/RealTheta.lean:96–104、New/UpperBound/Kernels/JetConjugatesAndBounds.lean:566–655 と、共役微分のガウス積分の規格化および多重指数の階乗の相殺を照合した。
- CM の相互法則、ガウス模型の真空の行列係数とテータ値の二乗和、標準格子の有限 Heisenberg 平均による真空への射影を用いる。前二者の全構成を本文では再証明していない。

## 静的照合

既存ラベルをすべて保持した。日英の label 27 件、eqref 35 件、leanref 13 件が一致し、環境の対と底本コミット内の 51 種の参照先を確認した。組版は統合作業で行う。

統合稿ではさらに、重みを各行列変数に与え、成分の Frobenius 合同、行列積での中間添字の消去、余因子、対称冪を経て必要な付値の指数に至る比較を追記した。照合箇所は FrobeniusFactors.lean 306–426、534–565 および 571–709 行。
