Balanced CSR Sparse Matrix-Vector Product on Graphics Processors
================================================================
We propose a novel parallel approach to compute the sparse matrix-vector
product (SpMV) on graphics processing units (GPUs), optimized for matrices with
an irregular row distribution of the non-zero entries. Our algorithm relies on
the standard CSR format to store the sparse matrix, requires an inexpensive
pre-processing step, and consumes only a minor amount of additional memory
compared with significantly more expensive GPU-specific sparse matrix layouts.
In addition, we propose a simple heuristic to determine whether our method or
the standard CSR SpMV algorithm should be used for a specific matrix. As a
result, our proposal, combined with the standard CSR SpMV, can be adopted as
the default choice for the implementation of SpMV in general-purpose sparse
linear algebra libraries for GPUs.


Get the slides [here](https://github.com/gflegar/talks/raw/master/europar_2017/slides.pdf),
and the paper [here](https://link.springer.com/chapter/10.1007/978-3-319-64203-1_50).

