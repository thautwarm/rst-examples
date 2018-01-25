
Position Specific (ane pseudo Position Specific)
-----------------------------------------------------

let :math:`e` is a series of sequences.

.. math ::

    & E = \{ e_{1}, e_{2}, e_{3}, \cdots, e_{N} \} \\
    & e_i = \{ e_{i1}, e_{i2}, \cdots, e_{iM}  \} \\
    & e_{ij} \in C \\

where :math:`N` is the number of sequences, 

:math:`M` is the length of a sequence(fixed length)

:math:`C` is a finite set of categories, 
without loss of generality, we assume the length of :math:`C` is also the symbol :math:`c`, :math:`c \in Z`.

* Position Specific Score Matrix(PSSM)

    * PSSM

        let :math:`R\;e` represents the frequency of :math:`e`. 

        .. math ::

            Normalize
            \left[
            \begin{matrix}
            R\;e_{11} & R\;e_{12} & \cdots & R\;e_{1M} \\
            R\;e_{21} & R\;e_{22} & \cdots & R\;e_{2M} \\
            \cdots & \cdots & \cdots & \cdots \\
            R\;e_{c1} & R\;e_{c2} & \cdots & R\;e_{cM} \\
            \end{matrix} 
            \right]


        We use all the sequences which are marked as positive to generate a :math:`PSSM_{pos}` ,
        apply the same operations to generate the :math:`PSSM_{neg}` .

        .. math ::

            PSSM = PSSM_{pos} - PSSM_{neg}


    * Bi Profile

        .. math ::

            Bi\;Profile =  \left[ \begin{matrix} PSSM_{pos}, PSSM_{neg} \end{matrix} \right]



    .. code :: python

        import numpy  as np
        import pandas as pd
        import numba as nb

        from sklearn.preprocessing import normalize


        @nb.jit
        def count_ps_matrix(
                        sequences: np.ndarray, 
                        bin_targets: np.ndarray,
                        ps_matrix: np.ndarray, 
                        categories: tuple):
            for tag, sequence in zip(bin_targets, sequences):
                for idx, e in enumerate(sequence):
                    ps_matrix[tag, categories.index(e), idx] += 1

        class Method:

            @staticmethod
            def position_specific(stats):
                return normalize(stats[1], axis=0) - normalize(stats[0], axis=0) 
            
            @staticmethod
            def bi_profile(stats):
                return np.hstack(
                        (normalize(stats[1], axis=0), normalize(stats[0], axis=0)))
                

        def represent(sequences: np.ndarray, 
                    bin_targets: np.ndarray, 
                    categories: tuple,
                    *methods: tuple):
            assert all(map(lambda e: e in (0, 1),  bin_targets))
            if not isinstance(categories, tuple):
                categories = tuple(categories)
            
            num, seq_length = sequences.shape
            psm = np.zeros((2, len(categories), seq_length), dtype=np.int64)
            
            # side effects
            count_ps_matrix(sequences, bin_targets, psm, categories)
            
            return [pd.DataFrame(method(psm), index=categories) for method in methods]




* N-Gram

    New way to encode the sequence.
    : **Window sliding**

    (P.S: stride)

    
* Pseudo

    Use n-gram method to generate new features and then apply **PSSM** on them.

    
















