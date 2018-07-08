---
layout: post
title: Coding Phase-II
---

This blog post covers the progress during the Phase-II of the Coding Period of Google Summer of Code 2018.

## Global Optimisation

As mentioned at the end of my previous blog post, I started working on Global Optimisation in the repo [`IntervalOptimisation`](https://github.com/JuliaIntervals/IntervalOptimisation.jl/) parallelly with [root finding](https://github.com/JuliaIntervals/IntervalRootFinding.jl/) and [interval arithmetic](https://github.com/JuliaIntervals/IntervalArithmetic.jl/).
I implemented an algorithm for the unconstrained global optimisation problem [#9](https://github.com/JuliaIntervals/IntervalOptimisation.jl/pull/9/) as mentioned in various resources such as `Global Optimisation using Interval Analysis by Eldon Hansen` and `Applied Interval Analysis by Luc Jaulin`. 
The existing implementation used a [`SortedVector`](https://github.com/JuliaIntervals/IntervalOptimisation.jl/blob/master/src/SortedVectors.jl) which means each insertion, updation, minimum retrieval was `O(n)` in time, and thus not efficient enough. Instead, I benchmarked a version that uses a `min-heap` from [`DataStructures.jl`](https://github.com/JuliaCollections/DataStructures.jl). That meant `O(logn)` retrievals and hence showed substantial performance improvements, with time improvements as good as around 50% for the 1-D case.
The initial implementation however didn't contract the box in any form, and only bisected it again and again while removing boxes which couldn't contain the global minimum. This however, suffers the curse of dimensionality, and slows down exponentially with the number of dimensions.
To tackle this, various contractors were implemented, such as the ones that use the first derivative and solve the linear equation, and the ones that uses the second derivative as well, and solve the quadratic equation, which was implemented earlier as a part of my project. This made global optimisation much more robust, albeit suffering a little in the 1-D case due to the slightly heavy computation of first and second order derivatives.

Even then, these contractors and even the bisection worked well only for small boxes and were really inefficient at contracting larger boxes. In contrast, techniques such as hull consistency performed really well in contracting large boxes, after which the control could be shifted to other contractors for further reduction in the size of the box until it was atomic. This would lead to the most efficient performance.
Hull Consistency isn't trivial to implement though, and after a lot of discussion with my mentor, David Sanders, we decided that the best way to go about it is to use the forward-reverse contractor mentioned in the book `Applied Interval Analysis by Luc Jaulin`, which is implemented by David Sanders in [`IntervalConstraintProgramming.jl`](https://github.com/JuliaIntervals/IntervalConstraintProgramming.jl). Other ideas were to use tools such as `ModelingToolkit.jl` and `DataFlow.jl` to parse the expressions in a better way.

## Interval Constraint Programming

The problem here was that `IntervalConstraintProgramming.jl`'s API had to be fed an expression, which was then parsed using Julia's metaprogramming functionalities to form a syntax tree through which interval constraints were then propagated, first forward and then reverse to appropriately contract the system. Also, it didn't form and store a DAG in the form of a topologically sorted tape, so repeated use, thus, would have ended up being very costly and inefficient. Clearly more work had to be done on this.
On David's suggestions, I understood auto differentiation and how the reverse mode AD is quite similar to Interval Constraint Programming. [`ReverseDiff`](https://github.com/JuliaDiff/ReverseDiff.jl) is a package for reverse-mode AD authored by Jarrett Revels and it doesn't suffer from the problems mentioned earlier. It uses the `function` as a blackbox and intercepts the system calls to make a DAG and then a rather clean tape of instructions from it which can be stored and then reused for efficiency. So, after discussions with David, I decided to rewrite `IntervalConstraintProgramming.jl` using the ideas and style derived from `ReverseDiff.jl`.
This is still a work-in-progress. Though, I have a firm understanding of `ReverseDiff` and how to use it for ICP in my mind, and a lot of it on code as well. 

I also decided to rewrite `IntervalContractors.jl`, which has a lot of reverse functions, in the style of `DiffRules.jl` for better compatibility with ReverseDiff's format and framework. 

This was the major part of the work done during this phase and also included learning a lot about Julia, it's several functionalities such as metaprogramming and easy multiple dispatch, as well as auto-diff and interval constraint programming. Also, I spent a lot of time understanding `Cassette.jl`'s functionalities, uses and API.

## Interval Arithmetic

Other work included adding hashing for intervals in `IntervalArithmetic.jl`[#161](https://github.com/JuliaIntervals/IntervalArithmetic.jl/pull/161), adding seamless interoperability between a `SVector` of `Interval`s and `IntervalBox`es [#166](https://github.com/JuliaIntervals/IntervalArithmetic.jl/pull/166), some new set operations for intervals [#154](https://github.com/JuliaIntervals/IntervalArithmetic.jl/pull/154).
Also, maintenance and review of previous PRs in `IntervalRootFinding.jl` was also handled.

## Moving Forward

I plan to complete the rewrite of `IntervalConstraintProgramming.jl` and `IntervalContractors.jl` in the upcoming days, and then incorporate the ideas of Hull Consistency and Forward-Reverse Contractors to improve contraction of large boxes in Global Optimisation and Guaranteed Root Finding.
Also, a new-and-upcoming package for Julia 0.7 called [`Cassette.jl`](https://github.com/jrevels/Cassette.jl) is being developed, which will soon take over ForwardDiff, ReverseDiff and a lot of other packages. `Capstan.jl` is a proof-of-concept implementation for AD which will soon be the major AD package for Julia, and is based on `Cassette`.
I have a fair understanding of `Cassette` now, and I plan to keep up with `Capstan`'s development cycle for Interval Constraint Programming. 

This has been an amazing month, and I have learnt a lot about both Julia and math, and have become a much more active part of the community. 
Shout-out to David Sanders for his amazing support throughout!
