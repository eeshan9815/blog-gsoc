---
layout: post
title: Getting Selected and First Two Weeks
---

The Summer of Code results came out April 23rd, 9:30pm, and I vividly rememeber the moment. I was elated and was surrounded by friends, who seemed equally elated about the results.
I got selected for Google Summer of Code 2018 under the umbrella organisation NumFOCUS, for a project under the Julia programming language.

Julia is a new, up-and-coming programming language, which launched back in 2012 and is undergoing a lot of development on a variety of topics, ranging from the core of the language to its packages for almost everything.

I got selected for a project under [JuliaIntervals](https://github.com/JuliaIntervals/), the project title being [Guaranteed Root Finding and Global Optimization with Intervals](https://summerofcode.withgoogle.com/projects/#5091150453538816).

## About The Project 

Interval arithmetic provides a way to perform computations with continuous sets of real numbers or vectors, for example to bound the range of a function over a given set.

This can be used to find roots (zeros) of functions in a guaranteed way, by excluding regions where there are no roots and zooming in on roots, but always within a given interval.

It can also be used to do global optimization of functions in a deterministic way, that is, find the global minimum of a non-convex, nonlinear function. Interval methods for global optimization provide a guaranteed bound for the global optimum, and sets that contain the optimizers.

This project proposes to significantly improve these methods using techniques found in the interval arithmetic literature. 
