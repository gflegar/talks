How to Solve a Linear System
============================

Krylov solvers are one of the most commonly used methods for the solution of
large, sparse linear systems. However, depending on the numerical properties of
the system matrix these methods may converge slowly, or even diverge.
Preconditioning is an effective method which aims to improve the numerical
properties of the matrix, and thus, the convergence rate of the Krylov solver.
The solver performance and memory footprint can be further improved by choosing
a suitable matrix format and sparse-matrix vector product (SpMV) algorithm for
the system matrix in question, or even employ a matrix-free method.

In this talk, I describe various components required for effective solution of
linear systems via Krylov solvers. I also present the Ginkgo framework
developed by our group, which aims at removing the burder from the application
scientist when solving linear systems, while also enabling easy extensibility
with custom components needed by distinct applications.

Get the slides
[here](https://github.com/gflegar/talks/raw/master/rwth_aachen_2018_09/slides.pdf).

