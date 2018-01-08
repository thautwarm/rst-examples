
应用回归作业
==================


Chapter 2
-------------

* 2.1

1. 正态条件(对所有统计量，偏差概率上趋近于0, 方差概率上趋近于相同的定值);

2. (题目所说为一元回归, 但考虑到理论的consistency在此处加上)


    自变量之间独立无关.  考察线性相关性:

    when :math:`\alpha = \beta`

        cov(:math:`\alpha, \beta`) = :math:`\sigma^2` 
    
    otherwise 
    
        cov(:math:`\alpha, \beta`) = 0 

* 2.2

.. math ::

    \beta_1 = \frac {\sum_i^n ( \overline x - x_i) y_i} {\sum_i^n (\overline x - x_i)^2}

=>

.. math ::

    \beta_1 = \frac {\sum_i^n y_i} {\sum_i^n x_i}

=>

.. math ::

    \beta_1 = \frac {\sum_i^n x_i y_i} {\sum_i^n x_i^2}

* 2.3

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


