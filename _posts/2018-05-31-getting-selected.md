---
layout: post
title: Getting Selected and First Two Weeks
---

The Summer of Code results came out April 23rd, 9:30pm, and I vividly rememeber the moment. I was elated and was surrounded by friends, who seemed equally elated about the results.
I got selected for Google Summer of Code 2018 under the umbrella organisation NumFOCUS, for a project under the Julia programming language under the mentorship of [David P. Sanders](http://sistemas.fciencias.unam.mx/~dsanders/).

Julia is a new, up-and-coming programming language, which launched back in 2012 and is undergoing a lot of development on a variety of topics, ranging from the core of the language to its packages for almost everything.

I got selected for a project under [JuliaIntervals](https://github.com/JuliaIntervals/), the project title being [Guaranteed Root Finding and Global Optimization with Intervals](https://summerofcode.withgoogle.com/projects/#5091150453538816).

## About The Project 

Interval arithmetic provides a way to perform computations with continuous sets of real numbers or vectors, for example to bound the range of a function over a given set.

This can be used to find roots (zeros) of functions in a guaranteed way, by excluding regions where there are no roots and zooming in on roots, but always within a given interval.

It can also be used to do global optimization of functions in a deterministic way, that is, find the global minimum of a non-convex, nonlinear function. Interval methods for global optimization provide a guaranteed bound for the global optimum, and sets that contain the optimizers.

This project proposes to significantly improve these methods using techniques found in the interval arithmetic literature. 

## Community Bonding Period

I spent the first two weeks of May, after my final examinations learning more about writing idiomatic Julia code, reading the docs, reading the books and research papers to build a better base about interval analysis and interacting with the Julia community.

The Julia community is delightful. The slack workspace is really active and there are a lot of channels for all purposes. Everyone is really helpful and fun to talk to. It has been a truly amazing experience being a part of this thriving community.

## Coding Period

Two weeks of the coding period have elapsed, and I am happy to say that I am definitely well on track according to the timeline I proposed as a part of my application. 

In the first week, I implemented the methods for solving a system of linear equations (Gauss-Seidel method and Gaussian Elimination) along with the testing and the benchmarking of the same [PR #67](https://github.com/JuliaIntervals/IntervalRootFinding.jl/pull/67). 
I also implemented methods for solving quadratic equations with interval coefficients [PR #68](https://github.com/JuliaIntervals/IntervalRootFinding.jl/pull/68).

In the second week, I implemented algorithms for automatically evaluating the slope of a function expanding about a point with respect to a given interval. Slopes tend to give better and tighter intervals as compared to derivatives, and this was an essential step to make the interval root-finding and optimisation methods more efficient [PR #69](https://github.com/JuliaIntervals/IntervalRootFinding.jl/pull/69).
