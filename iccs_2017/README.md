Variable-Size Batched Gauss-Huard for Block-Jacobi Preconditioning
==================================================================

In this work we present new kernels for the generation and application 
of block-Jacobi precon-ditioners that accelerate the iterative solution
of sparse linear systems on graphics processing units (GPUs). 
Our approach departs from the conventional LU factorization and
decomposes the diagonal blocks of the matrix using the Gauss-Huard
method. When enhanced with column pivoting, this method is as stable as
LU with partial/row pivoting. Due to extensive use of GPU registers and
integration of implicit pivoting, our variable size batched Gauss-Huard
implementation outperforms the batched version of LU factorization.
In addition, the application kernel combines the conventional two-stage
triangular solve procedure, consisting of a backward solve followed by
a forward solve, into a single stage that performs both operations
simultaneously.

Get the [slides](https://github.com/gflegar/talks/raw/master/iccs_2017/slides.pdf)
and the [full paper](http://www.sciencedirect.com/science/article/pii/S1877050917307731).
