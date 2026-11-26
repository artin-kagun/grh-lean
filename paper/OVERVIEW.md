# ディリクレ $L$ 関数の一般化リーマン予想をどう証明するか

**テータ持ち上げを約 $\sqrt{x}$ 回重ねると、素数冪和の剰余が $m$ 倍されて現れる。その項を残して、同じグラム行列式の上下の評価で主項を消す。** 以下では、この二つの仕組みを [日本語の論文本文](grh-ja.pdf) に対応させる。底本は Luke Sernau らの [Lean 可読版](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/GUIDE.md)。

## 1　テータ持ち上げをなぜ繰り返すのか

有限体上の曲線に対する Stepanov の方法では、補助関数をたくさんの点で高い位数で消し、消滅位数の総和を補助関数の次数と比較する。Alpöge は公表文の1頁と4頁で、この多重度に相当する役割を数体上ではテータ持ち上げの反復に担わせ、素数冪和の長さ $x$ に対して約 $\sqrt{x}$ 段を選ぶと説明している。Robin Zhang の予備ノートでも、各段の有限素点での付値評価を足し合わせると、主要な寄与が段数 $m$ 倍になる点が取り上げられている。[Alpöge の公表文](https://alpo.ge/remark.pdf) · [Zhang、§4.1、27頁](https://www.ihes.fr/~rzhang/files/GRH%20note.pdf#page=27)

可読版では、テータ核を微分して得る量が有限素点でどれだけ割り切れるかを調べる。二次指標 $\chi_K$ の値によって決まる $1-\chi_K(p^j)$ と打切りの重みが、$p^j$ の寄与に入る。各素数の付値の利得に $2\log p$ を掛けて足すと、これらが重み付き素数冪和になる。シーソー恒等式によって、この整除性を計算できる持ち上げの列と、後で行列式を評価する側の持ち上げの列が結ばれる。[局所素数和と利得](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/src/New/UpperBound/Size/ShortColumns.lean#L65-L83) · [利得の総和](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/src/New/UpperBound/Size/ArchimedeanSize.lean) · [本文第5節](sections/upper-bound.tex)

## 2　同じ量を上下から評価する

$n$ 個の形式を持ち上げ、グラム行列式でその張る平行多面体の体積の二乗を測る。$c$ はその値の対数の上界、$\delta$ は有限素点での整性を得るための対数指数の上界である。積公式に現れる組み合わせは $c+2\delta$。二つの指数の寄与は、グラム行列の第一変数と第二変数にそれぞれ現れる。$h$ を目標空間の次元、$H_0$ を共通の主項、$\mathcal R$ を重み付き素数冪和の総剰余とする。可読版の比較は、$f$ を補助数体の無限素点の個数、$b$ を重さの一つ、$a=xb$ として次の形になる。[積公式](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/src/New/Reduction/Lattices/TwistedLattice.lean) · [比較不等式](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/src/New/Reduction/MainInequality.lean#L82-L141)

$$
\begin{aligned}
 h(H_0-3E_4)
 &\le c+2\delta\\
 &\le n(H_0-m\mathcal R+E_4)
       +20h\log(1+2b^2)E_3,
 \qquad E_j=fa(\log b)^j .
\end{aligned}
$$

- **上から抑える。** 持ち上げの有限素点での整除性を使ってポアンカレ写像を正規化する。無限素点でのノルムを評価すると、各形式に対して $H_0-m\mathcal R$ が現れる。さらに少数の平行移動の像で目標空間のほぼ全体を張ることを二次モーメントから示し、$n$ を $h$ に近づける。[底本の定理 A・B](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/src/New/Reduction/ShortAndEnough.lean) · [本文第5節](sections/upper-bound.tex) · [第6節](sections/spanning.tex)
- **下から抑える。** 各有限素点で整性を扱いやすい捻りを選ぶ。正確には素数 $\ell$ と体同型 $\iota\colon\mathbb C\simeq\overline{\mathbb Q}_\ell$ の組ごとに $\xi_\iota$ を選び、無限素点で測る捻りなしのグラム行列式と、選んだ捻りのグラム行列式を比で結ぶ。その比の高さを評価するには、Hecke $L$ 値の比に加え、テータ持ち上げの像への射影に生じる分母を制御する必要がある。これらを積公式に入れると同じ $H_0$ を含む下界が得られる。[底本の定理 C](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/src/New/Determinant/Twist/LongForms.lean) · [本文第4節](sections/lattices.tex) · [第7節](sections/determinant-estimates.tex)

$n\le h$ と $H_0\ge0$ を使って $H_0$ を消し、$n\ge h/2$ で割ると、$m\mathcal R\le fa(\log b)^5$ が残る。無限素点の重さを二種類に分けた恒等式で、この総剰余から算術級数の剰余 $R_{q_0}(x)$ を取り出せる。大きい打切り点 $x_1$ の項を素数定理で抑えると、残る主な誤差は $\varphi(q_0)(\log b)^6/m$。ここで $m\ge\sqrt{x}$ を使う。規模の選び方により $\log b$ は $x$ の任意に小さい正の冪以下に抑えられるため、上界 $x^{-1/2+\varepsilon}$ が得られる。[総剰余の恒等式](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/src/New/Reduction/PrimeSums.lean) · [片側評価](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/src/New/Reduction/OneSidedBound.lean#L27-L155) · [本文第8節](sections/conclusion.tex)

> **補足（専門家による発見の読み方）**　Michael Rubinstein が公開したゼータ関数の場合の作業稿では、長い初版において素数和の係数で正規化した後に現れる $x/m$ と $m$ の二つの誤差が $\sqrt{x}$ で釣り合うと説明している。この説明は初版の誤差を扱い、上の可読版の数式は可読版の宣言に従っている。[Rubinstein の案内](https://math.uwaterloo.ca/~mrubinst/alpoge_claude_grh/) · [作業稿 v2、§I.7–I.9](https://math.uwaterloo.ca/~mrubinst/alpoge_claude_grh/zeta-paper_v2.pdf#page=18)

## 3　上側の誤差だけで零点を排除できる理由

対象とする法を $q_0$ とし、$\Lambda$ を von Mangoldt 関数、$d$ を指定の剰余類の素数とする。$(n/d)$ はルジャンドル記号である。$R_{q_0}(x)$ は

$$
\sum_{\substack{n\le x\\ n\equiv 1\bmod q_0}}
 \Lambda(n)\bigl(1-(n/d)\bigr)\left(\frac1n-\frac1x\right)
$$

から $\log x/\varphi(q_0)+c_{q_0}$ を引いた量である。$\varphi$ は Euler のトーシェント関数で、定数 $c_{q_0}$ は $d$ と $q_0$ を固定したときに剰余が $0$ に収束するように選ぶ。この重みでは、$R_{q_0}$ の変換に元の指標の $L$ 関数の零点と、二次捻りの $L$ 関数の零点が逆符号で入る。そこで排除したい零点の虚部に応じて $d$ を選び、必要な範囲に二次捻りの零点が出ないようにする。実軸上で残りの留数は非負になる。片側上界の定数を調整し、そこから剰余を引いた非負の差を使って測度を作る。Landau の補題を適用すると、対象の零点による極が排除される。最後に関数等式で臨界線の左側にも結論を移す。[零点判定の底本](https://github.com/lsernau/grh-lean/blob/72fead102f663d5c7a407964a13dc0cf9d977207/grh/src/New/Reduction/Zeros/Criterion.lean) · [本文第2節](sections/analytic.tex)

## 専門家の解説と底本

- **Siniša Slijepčević、11月21日。** §1.3 は、以前の長い版でどのように局所利得と格子の傾きの不等式を片側評価につないでいるかを説明する。初版の解析では、いくらでも大きい $Y$ について区間 $[Y,Y^{3/2}]$ 上の上界を使う。§11 には著者が解明できていない箇所も挙げられている。[解説 §1.3](https://hexagonmath.org/pdf/2611.00812#page=3)
- **Robin Zhang、11月22日。** §1 は証明の仕組みを既存の数学との関係からたどり、§4 は周期の付値と無限素点での大きさをどう比較するかを説明する。文献的な来歴を扱う予備ノートで、§0 に著者が AI を用いて論点を整理した経緯と照合の範囲が記されている。[予備ノート](https://www.ihes.fr/~rzhang/files/GRH%20note.pdf)
- **Michael Rubinstein、11月22日版。** 旧版をゼータ関数に特化して読んだ作業稿。§I.7–I.9 は比較の仕組みと平方根のスケールを、§III.11 は旧版の主不等式を13個の入力から導く議論を扱う。[作業稿 v2](https://math.uwaterloo.ca/~mrubinst/alpoge_claude_grh/zeta-paper_v2.pdf)

可読版の式を先に追うなら、本文の **第8節 → 第3節 → 第4–7節 → 第2節** の順に読むと、比較から零点の結論までのつながりを確認できる。本稿の底本と同じコミットについて、Andrew Sutherland は可読版・コンパクト版両方のビルド、Lean カーネルでの再検査、独立チェッカーによる照合の結果を公開している。[論文本文](grh-ja.pdf) · [Sutherland の検証記録](https://math.mit.edu/~drew/shortgrh/)
