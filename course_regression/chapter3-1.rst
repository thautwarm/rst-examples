
应用回归作业
==================


Chapter 3
-------------


* 3.1

写出多元线性回归模型的矩阵形式，并给出多元线性回归模型的基本假设。

一元线性回归模型有哪些基本假定?

    - 1. 高斯马尔科夫条件.
     
        随机误差项平均值为0，随机误差协方差为0或某定值。

        考察线性相关性:

        when :math:`i = j`

            cov(:math:`\epsilon_i, \epsilon_j`) = :math:`\sigma^2` 
        
        otherwise 
        
            cov(:math:`\epsilon_i, \epsilon_j`) = 0 
    
    - 2 正态条件

    .. math ::

        & \epsilon_i \sim N(0, \sigma^2) \\

        & \epsilon_1, \epsilon_2, \cdots  \text{  mutual independent}

* 3.2

样本数量小于p+1, 参数无法求解。

* 3.3

求证无偏样本方差位 :math:`\hat {\sigma^2} = \frac{1}{n-p-1}SSE`  

证:

.. math ::

    & SSE = \sum_i (y_i - \hat y_i)^2 = \sum_i c_{ii} \\

由

.. math ::

    & D(\bold e) = cov((\bold I - \bold H)y, (\bold I - \bold H)y) \\ 
    
    & = (\bold I - \bold H) cov(y, y) (\bold I - \bold H)^T \\

由 :math:`\bold H` 是对称幂等阵

    \Rightarrow D(\bold e) = \sigma^2 (\bold I - \bold H)

而

.. math ::

    & tr(\bold I - \bold H) = tr(\bold I) - tr(\bold H) = n - (p+1) \\
    & \sum_i D(e_i) = \sum_i c_{ii} = \sum \sigma^2 tr(\bold I - \bold H) = \sigma^2 (n-p-1)

则可得 :math:`\hat \sigma^2` 无偏估计, 同证明所示。


* 3.4

不能依据样本决定系数和复相关系数来判断拟合效果。 

小样本时容易虚高，其值也不能表征检验效果。检验效果还与p, n等值有关。
















