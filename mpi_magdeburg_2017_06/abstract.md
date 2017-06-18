Flexible-Size Batched Inversion and Factorization Routines for Block-Jacobi Preconditioning on GPUs
===================================================================================================

As conventional ILU-based preconditioners offer only a limited degree of
concurrency, in both the factorization, as well as the triangular solve
phases, they are often not able to fully utilize the highly-parallel
accelerator hardware. In contrast, while usually offering a lower convergence
rate improvement, block-Jacobi preconditioning can be expressed in terms of
independent computations on small diagonal blocks, making it an ideal candidate
for these types of machines.
In this talk, I will describe several approaches for efficient generation and
application of block-Jacobi preconditioners on CUDA-enabled GPUs. All presented
kernels rely heavily on the increased register count and warp shuffle
instructions available in newer GPU hardware and are tuned specifically for
small problem sizes arising in block-Jacobi preconditioning. As a result, these
routines outperform their counterparts from both open-source, as well as
proprietary libraries, by a large margin.

