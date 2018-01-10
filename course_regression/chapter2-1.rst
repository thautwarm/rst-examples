
应用回归作业
==================


Chapter 2
-------------

* 2.1

一元线性回归模型有哪些基本假定?

    - 1. 正态条件(对所有统计量，偏差概率上趋近于0, 方差概率上趋近于相同的定值);

    - 2. (虽然题目仅要求一元回归, 但考虑到理论的consistency在此处加上)

        自变量之间独立无关.  考察线性相关性:

        when :math:`\alpha = \beta`

            cov(:math:`\alpha, \beta`) = :math:`\sigma^2` 
        
        otherwise 
        
            cov(:math:`\alpha, \beta`) = 0 

* 2.2

.. math ::

    y_i = \beta_i + \epsilon_i, i = 1, 2, \cdots

在误差满足基本假定，但 :math:`\beta_0 = 0` 的一元线性模型中，求 :math:`\beta_1` 的最小二乘估计。

解:

列出Square Error式, 使之对 :math:`\beta_1` 导数为0 直接有

.. math ::

    \beta_1 = \frac {\sum_i^n x_i y_i} {\sum_i^n x_i^2}

* 2.3

证明满足求解条件的 :math:`\sum_{i=0}^n e_i = 0, \sum_{i=0}^n x_i e_i = 0`.

证:

.. math ::

    \sum_{i \in I} e_i 
        = \sum_{i \in I}   y_i - \hat y_i 
        = \sum_{i \in I}   (y_i - \overline y_i) + (\overline y_i - \hat y_i)
        = 0 + 0

而对于

.. math ::

    \sum_{i \in I} x_i e_i
        = \sum_{i \in I}  x_i (y_i - \hat y_i)
        = \sum_{i \in I}  x_i (y_i -  \beta_1 x_i - \beta_0 )


注意到最小二乘法求解要求上式为0， 证毕。

* 2.3

回归方程 :math: `E(y) = \beta_0 + \beta_1 x`的参数 :math:`\beta_0, \beta_1`的最小二乘估计与最大似然估计在什么条件下等价?

解与证明:

当满足正态条件时， :math:`y_i` 服从如下正态分布。

.. math ::

    y_i ~ N(\beta_0 + \beta_1 x_i, \sigma^2)

对应概率密度函数为    

.. math ::

    f(y_i; \theta) = \frac  1 {\sqrt{2 \pi} \sigma} exp \{ -\frac 1 {2\sigma^2} [ y_i - (\beta_0 + \beta_1 x_i) ]^2 \}

其中 :math:`\theta` 蕴含 :math:`\beta_0, \beta_1`。

n个独立样本的最大似然

.. math ::

    L(\theta; y_1, y_2, \cdots) = \prod_{i=1}^n f(y_i, \theta)
    = {\frac  1 {\sqrt{2 \pi} \sigma}}^n exp 
    \{ -\frac 1 {2\sigma^2} \sum_{i=1}^n [ y_i - (\beta_0 + \beta_1 x_i) ]^2 \}

易得，当 :math:`\sigma` 一定，要使 :math:`L` 最大，必有项 :math:`[ y_i - (\beta_0 + \beta_1 x_i) ]^2` 最小。

上述过程可以反推，即 :math:`L` 最大时Square Error最小。




* 2.5

证明 :math:`\hat \beta_0` 是 :math:`\beta` 的无偏估计。

证:

由

.. math ::

    \overline y = \hat \beta_1 \overline x  + \hat \beta_0

且 :math:`\beta_1` 无偏, 则 

.. math ::

    E(\hat \beta_0) = E(\overline y) - \beta_1 \overline x
                    = E(\sum_{i \in I} \beta_0 + \beta_1 x_i) - \beta_1 \overline x
                    = \beta_0 + \beta_1 \overline x - \beta_1 \overline x
                    = \beta_0


* 2.6

证明

.. math ::

    var(\hat \beta_0) = [\frac 1 n + \frac {(\overline x)^2} {\sum_{i \in I} (x_i - \overline x)^2}] \sigma^2

证:

.. math ::

    var(\hat \beta_0) = var(\overline y - \hat {\beta_1} \overline x)
                      = var(\frac 1 n \sum_{i \in I} y_i) +  {\overline x}^2 var(\hat \beta_1)
                      = \frac 1 {n^2} \sum_{i \in I} var(y_i) +  {\overline x}^2 var(\hat \beta_1)

由

.. math ::

    var(\hat \beta_1) = \frac {\sigma^2} {L_{xx}}

所以

.. math ::

    var(\hat \beta_0) = \frac 1 n \sigma^2 + \frac {\sigma^2} {L_{xx}} {\overline x}^2 
                      = \sigma^2 [\frac 1 n + \frac {{\overline x}^2}  {L_{xx}}]
                      
* 2.7

证明平方和分解式 :math:`SST = SSR + SSE`.

证:

.. math ::

    SST = L_{yy} = \sum_{i \in I} (y_i - \overline y)^2 

.. math ::

    SSR = \sum_{i \in I} (\hat y_i - \overline y)^2

.. math ::

    SSE = \sum_{i \in I} (\hat y_i - y_i)^2
    


.. math ::

    [SST - (SSR + SSE)]_i 
    \triangleq  
    (y_i - \overline y)^2  - [(\hat y_i - \overline y)^2 +  (\hat y_i - y_i)^2]
    = - 2 y_i \overline y - 2 (\hat y_i)^2 + 2 \hat y_i (\overline y + y_i)

根据残差性质

.. math ::

    &\sum_{i \in I} e_i = 0 \\
    &\sum_{i \in I} x_i e_i = 0

所以

.. math :: 

    \sum_{i \in I}  & [SST - (SSR + SSE)]_i  \\
    &= \sum_{i \in I}  - 2 (\hat y_i)^2 + 2 \hat y_i y_i \\
    &= \sum_{i \in I} - 2 \hat y_i (\hat y_i - y_i) \\
    &= \sum_{i \in I} 
    - 2 \hat y_i e_i \\
    &= \sum_{i \in I} 
    (\beta_1 x_i + \beta_0) e_i \\ 
    & = 0 + 0

证毕

* 2.8

验证三种检验的关系:
    
    - t检验和卡方检验

    .. math ::

        t = \frac {\hat \beta_1 \sqrt L_{xx}} {\hat \sigma} = \frac {\sqrt {n-2} r} {\sqrt {1 - r^2}}


    - F检验和t检验
    





    