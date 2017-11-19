---
title: FloatX: Custom Floating Point Type Emulation Library
author: Goran Flegar, Cristiano Malossi, Enrique S. Quintana-Orti, Florian ???
date: 23 November 2017
---

-------------------------------------------------------------------------------

Why FloatX?
-----------

*   Transprecision hardware under development
*   Develop transprecision algorithms
    *    Even if hardware __not__ available
    *    Need emulation library: __FloatX__ (Float Extended)

-------------------------------------------------------------------------------

Design principles
=================

-------------------------------------------------------------------------------

As efficient as possible
------------------------

*   enables larger simulations (e.g. DNNs)
*   use floating point types supported by the hardware as "backend",
    artificially reduce precision after every operation to simulate desired
    type
*   avoid using extra memory (size of emulated type should not exceed size of
    backend type)
*   if emulated type exactly matches a hardware-supported type, avoid any
    overheads (e.g. emulated double should be as efficient as plain double)
*   CUDA support

-------------------------------------------------------------------------------

As easy to use as native types
------------------------------

*   Arithmetic and relational operations, assignements
    *   `a` and `b` FloatX numbers
    *   `a + b`, `a / b`, ...
    *   `a < b`, `a > b`, ...
    *   `a = b`, `a += b`, `a -= b`, ...
*   Interoperability between different emulated types (`1.2f + 3.0` is valid)
    *   `a` and `b` FloatX numbers of __different__ precision
    *   arithmetic, relational operations, assignments
    *   need generalization of standard "type propagation" rules
        (e.g. `a = b + c`)
        *   if `a` and `b` are of the same type, the result stored in `a`
            should be a correctly rounded result of `b + c` in `decltype(a)`
        *   if `a` and `c` are of the same type, the result stored in `a`
            should be a correctly rounded result of `b + c` in `decltype(a)`
    *   concept of _common type_: `common_type(S, T)` is the least precise type
        which is more precise than both `S` and `T`
*   Interoperability between emulated and native types
    *   `a = a + 3`, `a -= 3.5`, `auto x = a + 3.5` (`decltype(x)`?)

-------------------------------------------------------------------------------

Language of choice: C++
-----------------------

*   0-overhead abstractions
*   high efficiency
*   operator overloading
*   powerful compile-time type manipulation via template metaprogramming

-------------------------------------------------------------------------------

Example
-------

```c++
floatx<7, 12> a = 1.2, b = 3.2;
floatx<10, 9> c;
float d = 3.2;
double e = 5.2;

std::cin >> c;

std::cout << a + b << std::endl;    // decltype(a + b) == floatx<7, 12>
std::cout << a < b << std::endl;

a += c;

std::cout << a / c << std::endl;    // decltype(a / c) == floatx<10, 12>
std::cout << c - d << std::endl;    // decltype(c - d) == floatx<10, 23>
std::cout << a * e << std::endl;    // decltype(a * e) == floatx<11, 52>
```

-------------------------------------------------------------------------------

Current status
--------------

*   What works:
    *   arithmetic, relational ops, assignment
        *   same floatx type, different floatx types, floatx and native type
    *   round to nearest, tie to even rounding policy

*   In progress:
    *   _backend type_ other than `double`
    *   optimal performance for native type equivalents
    *   CUDA support

-------------------------------------------------------------------------------

Bonus
-----

*   Having the precisions of the types fixed at compile time "cripples"
    experimentation.
*   There is a _runtime_ version of FloatX type:

```
floatxr<> ra(5, 7, 3.2);
std::cout << ra + 3.4 << std::endl;
floatx<8, 9> b;
std::cout << ra - b << std::endl;
ra.set_precision(2, 8);
```

-------------------------------------------------------------------------------

FlexFloat vs FloatX
-------------------

*   FlexFloat
    *   C library (also callable from other languages)
    *   Function-based syntax
    *   Enables access to transprecission hardware if available

*   FloatX
    *   C++ library (cannot call from other languages)
    *   Well-known, operator-based syntax, behaviour of builtin types
    *   Cannot access transprecission hardware directly (but can use FlexFloat
        as backend type!)

-------------------------------------------------------------------------------
