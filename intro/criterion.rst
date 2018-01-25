
Criterion
--------------------


Confusion Matrix
=============================

        +-----+------+------+
        |     |  P   |  N   |
        +-----+------+------+
        |P    | TP   | FP   |
        +-----+------+------+
        |N    | FN   | TN   |
        +-----+------+------+

criterions:


* :math:`TP` (True Positive)

* :math:`TN` (True Negative)

* :math:`FP` (False Positive)

* :math:`FN` (False Negative)

* :math:`ACC` 
    
    Accuracy

    .. math :: 

        \frac{TP+TN}{Total}



* :math:`Pre` 

    Precision

    .. math ::

        \frac{TP}{TP + FP}



* :math:`Rec`

    Recall

    .. math :: 

        \frac{TP}{TP+FN}

    

* :math:`MCC` (Matthews correlation coefficient)

    Evalutate criterion on imbalanced datasets.

    .. math ::
    
        \frac{TP \cdot TN - FP \cdot FN} {\sqrt {(TP + FN) \cdot (TP+FN) \cdot (TN+FP) \cdot (TN + FN)}}



* :math:`F_n -` score 

    .. math ::

        (1+\beta^2) \frac {Pre \cdot Rec} {\beta^2 Pre + Rec }


* :math:`Spe`

    Specificity

    .. math ::

        \frac {TN} {TN + FP}

* :math:`Sen`

    Sensitivity

    .. math ::

        \frac {TP} {TP + FN}


Soft Classification
===============================

Produce the possibility to be positive of each sample.


.. math ::

    P(target=1 | sample) \in [0, 1]


Curve Metrics
====================


* Threshold

    A prediction of soft classification could be separated into the positive and
    negative by using a threshold.

    .. math ::

        & T \in [0, 1]\\
        & prediction = (y_1, y_2, \cdots, y_n), \forall i = 1, 2, \cdots, n, \;, y_i \in [0, 1]\\
        & positive\;\;prediction = \{ i | y_i \ge T \} \\
        & negative\;\;prediction = \{ i | y_i < T \}



    One :math:`T`, one confusion matrix.

* ROC curve:

    For each :math:`T \in sorted(distinct(prediction))` ,
    giving a series of confusion matrix :math:`\{M_n \}`, results in ascending sequences 
    :math:`{(1-Spe_n, Sen_n)}`.

    Plot this ascending sequences we get ROC curve.


    .. image :: roc.png


Model Evaluation
===================

* model :math:`A` is better than :math:`B` on datasets :math:`D`


    :math:`ROC(A, D)` is above :math:`ROC(B, D)`




    










