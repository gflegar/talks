Flexible-Size Batched LU for Small Matrices and its Integration into Block-Jacobi Preconditioning
=================================================================================================

We present a set of new batched CUDA kernels
for the LU factorization of a large collection of independent
problems of different size, and the subsequent triangular
solves. All kernels heavily exploit the registers of the graphics
processing unit (GPU) in order to deliver high performance for
small problems. The development of these kernels is motivated
by the need for tackling this embarrasingly-parallel scenario
in the context of block-Jacobi preconditioning that is relevant
for the iterative solution of sparse linear systems.

Get the slides [here](https://github.com/gflegar/talks/raw/master/icpp_2017/slides.pdf),
and the paper [here]().

