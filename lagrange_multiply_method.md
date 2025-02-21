拉格朗日乘子法 Lagrange Multiply method 

# 等式约束问题
假设$x$是一个$d-dimension$的向量，且我们有如下的优化问题：（ $g(x)$ 确定一个 d-1 维的空间）

$$
\min \quad f(x),\\
s.t.\quad g(x)=0.
$$

首先我们知道 $\nabla g(x)$ 一定垂直于约束空间，这是因为 $g(x)$ 的值等于 $0$，也就是说 $x$ 在约束空间中的移动不影响 $g(x)$ 的值。

其次，假设 $x^* $是上述约束问题的解，则 $\nabla f(x^* )$ 一定垂直于约束空间，这是因为如果 $\nabla f(x^* )$不垂直于约束空间，则我们一定可以在约束空间中找到 $f(x)$ 的一个下降方向，从而找到一个更优解，这与 $x^*$ 是上述问题的解的结论相矛盾。

所以，从上述的性质中，我们可以得出以下结论：在最优解 $x^* $处，$\nabla g(x^* )$ 与 $\nabla f(x^* )$ 只可能同向或者反向（事实上，$\nabla f(x^* )$ 可以用 $\nabla g(x^* )$ 线性表示。这在有多个等式约束的时候也可以这样理解：$\nabla f(x^* )=\sum\lambda_i g_i(x^* )$, $\exist \lambda_i$ ）。所以我们可以以下的式子成立：

$$
\nabla f(x^* ) + \lambda \nabla g(x^* ) = 0.\quad \quad(1)
$$

所以我们可以按照如下的形式定义我们的拉格朗日函数：

$$
L(x, \lambda) = f(x) + \lambda g(x).
$$

观察我们的拉格朗日函数，如果我们想令 （1） 式成立，只需要令 $\nabla_x L(x, \lambda)$ 等于 $0$；而如果我们还想满足约束条件 $g(x)=0$，只需要令 $\nabla_\lambda L(x, \lambda)$ 也等于 $0$。所以原来的带约束问题就转换成了无约束问题，变为求解 $\nabla L(x, \lambda) = 0$。


# 一般约束问题
现在我们在问题的约束中，引入不等式的约束，定义为 $h(x)\le 0$ （所有的不等式约束问题都可以通过简单的变换成此形式）。

$$
\min \quad f(x),\\
s.t.\quad h(x) \le 0.
$$

对于这种约束的形式，如果最优解 $x^* $ 最终落在 $h(x) <  0$ 的空间中，则上述约束不起作用，我们就可以简单地通过令 $\nabla f(x) = 0$ 来计算，这跟令 $\mu = 0$ 且 $\nabla_x L(x, \mu) = 0$ 是等价的。

而如果最优解 $x^* $ 最终落在 $h(x) = 0$ 的空间中，情况将与上述讨论过的等式约束问题是一样的，只不过此时 $\nabla h(x^* )$ 与 $\nabla f(x^* )$ 的方向只可能是反方向，也即 $\mu > 0$ 。这是因为 $\nabla h(x^* )$ 的方向只可能指向约束空间外，否则约束空间内存在 $x_0$ 使得 $h(x_0) > 0$ ，这与约束空间的定义矛盾；而 $\nabla f(x^* )$的方向只可能指向约束空间内，否则约束空间内存在使得 $f(x)$ 更小的 $x$ 的存在，与最优解落在 $h(x) = 0$ 的区域的假设矛盾；而且 $\nabla h(x^* )$ 与 $\nabla f(x^* )$ 与 $h(x) = 0$ 的空间垂直（如 等式约束问题 部分所述）。

所以我们能得到如下的约束：

$$
\left\lbrace
\begin{array}{ll} 
h(x) \le 0, \\ 
\mu \ge 0,\\
\mu h(x) = 0.
\end{array} \right.
$$

这也就是我们熟知的 Karush-Kuhn-Tucker condition（KKT 条件）。

所以假设我们有如下的一般约束问题：

$$
\min \quad f(x),\\
s.t. \quad g_i(x) = 0 \quad (i = 1, ... ,m),\\
h_j(x) \le 0 \quad (j = 1, ... , n).
$$

我们引入拉格朗日乘子 $\lambda = (\lambda_1, ... ,\lambda_m)^T$ 和 $\mu = (\mu_1, ... ,\mu_n)^T$，进而得到拉格朗日函数

$$
L(x, \lambda, \mu) = f(x) + \sum_{i = 1}^m\lambda_ig_i(x) + \sum_{j=1}^n\mu_jh_j(x) \quad \quad (2)
$$

和我们对应的 KKT 条件

$$
\left\lbrace
\begin{array}{ll} 
h_j(x) \le 0, \\ 
\mu_j \ge 0,\\
\mu_j h_j(x) = 0
\end{array} \right.
$$

我们可以求解处 （2） 式的无约束问题的解，最后检验我们的解是否满足 KKT 条件，进而确定原约束问题的解。
