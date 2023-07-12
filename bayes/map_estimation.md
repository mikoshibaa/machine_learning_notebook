# 最大事後確率推定 (MAP推定)


## 事後確率

観測データ $x$ がなんらかの原因 $z$ から発生したとして，その $z$ の不確からしさをはかりたい.

事後確率 $p(z|x)$ はベイズの定理より

$$
\begin{align}
    p(z|x) \propto p(x|z)p(z) 
\end{align}
$$

である．

この事後確率を用いて新たに予測等もする．ほかにも期待値を取ったりする．

さて，事後確率を最大とする $z^*$ を見つけることにする．

$$
\begin{align}
    z^* = \arg\max_z p(z|x)
\end{align}
$$


## KLダイバージェンスとMAP推定の関連

MAP推定は不確からしさがどんより漂っている事後確率 $p(z|x)$ から1点 $z^*$ のみをエイッと代表させていることから，事後確率にデルタ関数を近づけていると解釈できる．

KLダイバージェンスで表現してみる．

$$
\begin{align*}
    \min_{z_0} KL\bigg( \delta(z-z_0) \bigg|\bigg| p(z|x) \bigg) 
    &= \min_{z_0} -\int  \log \frac{ p(z|x) }{\delta(z-z_0)} \delta(z-z_0)dz \\
        &= \min_{z_0} -p(z_0|x)\\
        &= \max_{z_0} p(z_0|x)
\end{align*}
$$

