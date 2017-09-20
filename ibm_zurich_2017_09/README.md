Accelerating the Solution of Sparse Linear Systems with GPUs
============================================================

Krylov solvers are one of the most commonly used methods for the solution of
large, sparse linear systems. However, depending on the numerical properties of
the system matrix these methods may converge slowly, or even diverge.
Preconditioning is an effective method which aims to improve the numerical
properties of the matrix, and thus, the convergence rate of the Krylov solver.
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
proprietary libraries, by a large margin. Finally, I will give an overview of
the current research pursued by our group, which aims to further improve the
effectiveness of block-Jacobi preconditioning, by reducing its memory
footprint, as well as its energy consumption.

Get the slides
[here](https://github.com/gflegar/talks/raw/master/ibm_zurich_2017_09/slides.pdf).

