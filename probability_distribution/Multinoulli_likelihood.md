# ラグランジュの未定乗数法を用いない多項分布の最尤推定 (ボツ)

多項分布のパラメータの最尤推定は対数尤度に対してラグランジュの未定乗数法で求めるのが一般的だが，ここでは対数尤度を内積と見て幾何的に導出したかった（ボツ）．


## 用いる記号
* $x \in \mathbb{R}^K$ : $K$ カテゴリを示す1-of-K表現．とくに $\sum_k x_k = 1$
* $\boldsymbol{\theta} \in \mathbb{R}^K$ : $K$ カテゴリを生成する確率． $K$ 面サイコロと解釈. とくに $\sum_k \theta_k = 1$ の単体上にある．
* $cat(x|\boldsymbol{\theta})$ : $K$ 面サイコロを振って $x$ が出る尤度 
    -    $cat(x|\boldsymbol{\theta}) = \prod_k \theta^{x_k}$

* $X$ : 教師データ $\{x_n\}$
## 状況

データ $\{ x_n \}$ が手元にある．カテゴリ $k$ の数が $N_k$ 個であったとする．

### 尤度

$$
\begin{align*}
    p(X|\theta) &= \prod_k \theta_k^{N_k}
\end{align*}
$$

### 対数尤度

$$
\begin{align*}
    l(\boldsymbol{\theta}) &= \sum_k N_k \log \theta_k
\end{align*}
$$

## 対数尤度最大化に対するアプローチ

### ラグランジュの未定乗数法

$\sum_k \theta_k = 1$ の制約を用いてラグランジュの未定乗数法を使う．

結論：

$$
\begin{align*}
    \hat{\theta_k} &= \frac{N_k}{N}
\end{align*}
$$

教師データのうち，カテゴリ $k$ を観測した割合という素直に理解しやすい結果．

### 内積と見るアプローチ(ボツ)

最大化したい対数尤度 $l(\boldsymbol{\theta})$ はパラメータの対数変換した領域ででの重み付き和と考えられる．以下， 次の記号を導入する

$$
\begin{align*}
    \phi_k &:= \log \theta_k\\
    \mathbb{R}^K \ni \boldsymbol{\phi} &:= 
    \begin{pmatrix}
        \phi_1\\
        \vdots\\
        \phi_K
    \end{pmatrix}\\
    &= 
    \begin{pmatrix}
        \log \theta_1\\
        \vdots\\
        \log \theta_K
    \end{pmatrix}
\end{align*}
$$

すると対数尤度は以下のように重みつき和で表現される.

$$
\begin{align*}
    l(\boldsymbol{\phi}) &= \sum_k N_k \phi_k
\end{align*}
$$

ベクトル $\boldsymbol{N} := (N_1, N_2, \cdots, N_K)$ と　ベクトル $\boldsymbol{\phi}$ の内積なので，これらが最大のとき，2ベクトルが重なる時だと思った．しかしながらベクトル $\boldsymbol{\phi}$ は各要素が全てマイナスなので幾何的な最大化は導き出せなかった(第I象限，第III象限にベクトル $\boldsymbol{N}$ , $\boldsymbol{\phi}$ があるイメージ).