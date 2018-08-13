---
layout: post
title: Coding Phase-III
---

This blog post covers the progress during the third and final phase of the Coding Period of Google Summer of Code 2018.

The major part of my project was the implementation of the `IntervalConstraintProgramming` using a ReverseDiff approach such that the function can be used as a black-box Julia function, which led to its easy accessibilty and use in various places such as Global Optimisation and Guaranteed Root Finding to make the algorithms much more efficient, especially for huge box sizes since they can reduce the box size by a lot in a single pass, as oppsoed to the normal contractors such as the Newton contractor, which can take several iterations for the same reduction since even quadratic convergence isn't that good when the box is huge. These contractors also tend to work much better for small boxes, that's why a common practice is to `bisect` the box and then contract again if the initial contraction wasn't good enough.
This gave major performance boosts when the box is huge, and was often a quite efficient and robust contractor. 
It was also extended to include tracking and reverse functions for more functions such as the `unary minus` etc.

This was also extended to solve the constrained optimisation problem, by appropriately contracting the domain using the existing constraints before each pass of reducing the global minimum and throwing out the boxes which can't contain the solution. The function which actually searches the space and reduces the global minimum had to be rethought since the new point has to satisfy the constraints as well. 

The most important part where the ICP using the `Tape` stuff was really useful was for contracting gradients of functions, and naturally extending this to be able to use the gradients as constraints in global optimisation. 
This took up a lot of time debugging an issue about recording the `getindex` of the Array returned by the gradient calculation due to a lot of stray recordings of `getindex` into the Tape. It was finally fixed, but has a potential to break while debugging with Juno, for instance, if a `getindex` is called on a TrackedArray to view its contents, it will end up recording that into the tape. The _correct_ way to fix it would be to use Cassette for ICP, and record things into the tape in a special _recording_ `Context`, and not in the _execution_ `Context`, and that is something I plan to implement in the future, especially since Cassette finally has a stable 0.1.0 release now.

The API of the Interval Optimisation was also improved, and the use of `icp` added as a keyword argument to the `minimise` function, and constrainted optimisation added as a multiple dispatch function. Moreover, docs and tests were written for the existing functions and finalized as the end of GSoC came near.

I also went to JuliaCon 2018 in London during this time and met a lot of amazing people who have created the Julia language and its incredible package ecosystem. It was a great experience, and I would like to thank the entire community for being so awesome! I also presented a poster there on my work which can be found [here](https://drive.google.com/file/d/1pY6oqiZOj6ZFEUiBy3sQg_DGuoTVSfKC/view?usp=sharing)

A final report for the work done during GSoC which includes the future goals and plans can be found [here](https://eeshan9815.github.io/blog-gsoc/final-report/)
