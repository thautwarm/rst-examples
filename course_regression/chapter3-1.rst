
应用回归作业
==================


Chapter 3
-------------


* 3.1

写出多元线性回归模型的矩阵形式，并给出多元线性回归模型的基本假设。

矩阵形式:

.. math ::

    \bold X \bold A + \bold \epsilon = \bold Y 


多元线性回归模型有哪些基本假定?

    - 1. 高斯-马尔科夫条件。
    
    - 2. 自变量为常数。

    - 3. 正态分布。

    - 4. 回归参数个数小于方程个数。

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

.. math ::

    \Rightarrow D(\bold e) = \sigma^2 (\bold I - \bold H)

而

.. math ::

    & tr(\bold I - \bold H) = tr(\bold I) - tr(\bold H) = n - (p+1) \\
    & \sum_i D(e_i) = \sum_i c_{ii} = \sum \sigma^2 tr(\bold I - \bold H) = \sigma^2 (n-p-1)

则可得 :math:`\hat \sigma^2` 无偏估计, 同证明所示。


* 3.4

不能依据样本决定系数和复相关系数来判断拟合效果。 

小样本时容易虚高，其值也不能表征检验效果。检验效果还与p, n等值有关。

* 3.5

假设 :math:`H_0 : \beta_1 = 0` ,当 :math:`t_{\beta_1} > t_{\frac {\alpha} {2}}` 时, 拒绝 :math:`H_0` ,
假设不成立, 即 :math:`x_1` 是显著的。

否则, :math:`H_0` 假设成立, :math:`x_1` 不显著。


* 3.6

中心化可以减少一个拟合参数( :math:`\beta_0` )的计算，标准化可以在数据单位量级差距大的时候减小误差。

* 3.7

证:

.. math ::

    & \hat y = \hat \beta_0 + \hat \beta_1 x_1 + \cdots + \hat \beta_p x_p \\
    & \hat y - y = \hat \beta_1 (x_1 - \overline x_1) + \cdots + \hat \beta_p (x_p - \overline x_p)\\
    & \frac {
        \hat y - y
    }{ 
        \sqrt {L_{yy}}
    } = \hat \beta_1 \frac{x_1 - \overline x_1}{\sqrt {L_{11}}} 
        \frac {\sqrt {L_{11}}} {\sqrt {L_{yy}}}
    + \cdots + \hat \beta_p \frac{x_p - \overline x_p}{\sqrt {L_{pp}}}
         \frac {\sqrt {L_{pp}}} {\sqrt {L_{yy}}} \\
    & \because x_{ij}^{*} = \frac {x_{ij} - \overline x_j}{\sqrt {L_{jj}} },
    y_{i}^{*} = \frac {y_{i} - \overline y}{\sqrt {L_{yy}} },\\
    & \therefore y_{i}^{*} = \hat \beta_1^{*} x_{i1}^{*} + \cdots + \hat \beta_p^{*} x_{ip}^{*} \\
    & \Rightarrow \hat \beta_j^* = \frac {\sqrt {L_{jj}}} {\sqrt {L_{yy}}} \hat \beta_j


* 3.8

.. math ::

   & \because r_{12 ; 3} = \frac {
                    - \Delta_{12}
                    } 
                    {
                        \sqrt { \Delta_{11} \Delta_{22} }
                    } \\
   & \Delta_{11} = 1 - r_{23}r_{32} = 1 - r_{23}^2 \\
   & -\Delta_{12} = r_{21} - r_{23} r_{31} = r_{12} - r_{13} r_{23} \\
   & \Delta_{22} = 1 - r_{13} r_{31} = 1 - r_{13}^2 \\
    & r_{12;3} = \frac {r_{12} - r_{13} r_{23}} {\sqrt{ (1 - r_{13})^2 (1 - r_{23})^2 }} 


* 3.9

.. math ::

    \because & F_j = \frac {
            SSR - SSR_j
        }
        {
        SSE / (n-p-1)} =
        \frac {
            SSE_j - SSE
        } 
        {
            SSE / (n-p-1)
        }\\
    & r^2 = \frac {
        SSE_j - SSE
    }
    {
        SSE_j
    }\\

:math:`\therefore` 二者均为通过 :math:`SSE_j - SSE` 所占比值大小, 检验 :math:`x_j` 的显著性。

故而 :math:`F_j, r^2` 等价

* 3.10

.. math ::

    &  R^2 = \frac {SSR} {SST} = \frac {SSR} {SSR + SSE}\\  
    & \because F = \frac {SSR/p} {SSE/(n-p-1)} \\
    & \therefore SSR = \frac {F SSE} {n-p-1} p \\
    & \therefore R^2 = \frac{F P} {F P + (n-p-1)} = \frac {F} {F + (n-p-1)/p}

* 3.11

1. 

.. image :: 3-11-r.png


2.

.. math ::

    y = 3.75404*x_1 + 7.10071*x_2 + 12.44747*x_3 -348.28017


3. 

.. math ::

    R^2 = 0.8055


4. 

F统计量为 :math:`8.28318` , 显著水平为 :math:`0.98513` , 显然显著。

5. 

:math:`\beta_1,\beta_2,\beta_3` 的t分布量为

.. math ::

     [ 1.94176  2.46528  1.1777]

显著水平分别为

.. math ::

    [0.9499   0.97562  0.85825]

发现居民非商品支出的显著性不够强。


6. 

.. math ::

   y = 4.67563*x_1 + 8.97096*x_2 -459.62365

系数检验, t统计量与显著程度如下

.. math ::

    & t_{\beta_1} = 2.57459, t_{\beta_2} =  3.63423 \\
    & 1 - \alpha_1 = 0.98162 , 1 - \alpha_2 =  0.99582 \\

回归方程检验

.. math ::

    & F = 11.11674 \\
    & 1 - \alpha = 0.99328


7. 置信区间

工业总产值的系数: :math:`(3.62765, 3.88043)`

农业总产值的系数: :math:`(6.91242, 7.28901)`

居民非商品支出的系数: :math:`(11.75651, 13.13843)`



8. 标准化回归方程

.. math ::

    y^* = 0.385*x_1^* + 0.535*x_2^* + 0.277*x_3^*

9. 

.. math ::

    &\hat y_0(x_1 = 75, x_2 = 42, x_3 = 3.1) = 270.089 \\

95%置信区间 :math:`(268.61969960782068, 271.5596291601633)`


* 3.12

不能合理解释，有参数为通过检验。

但使用所有3个特征能够合理解释:

.. image :: 3-12-1.png
.. image :: 3-12-2.png
.. image :: 3-12-3.png

目标正好是三个特征的线性相加。










