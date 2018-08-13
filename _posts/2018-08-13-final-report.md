---
layout: post
title: Final Report
---

## Basic Info

**Name:** Eeshan Gupta ([eeshan9815](https://github.com/eeshan9815))

**Proposal:** Guaranteed Root Finding and Global Optimization with Intervals ([link](https://summerofcode.withgoogle.com/projects/#5091150453538816))

**Mentor:** [David Sanders](http://sistemas.fciencias.unam.mx/~dsanders/) ([dpsanders](https://github.com/dpsanders))

**Organization:** NumFOCUS (Julia)

**Category:** Package

**Major repositories for the work:** [IntervalConstraintProgramming.jl](https://github.com/JuliaIntervals/IntervalConstraintProgramming.jl), [IntervalRootFinding.jl](https://github.com/JuliaIntervals/IntervalRootFinding.jl), [IntervalOptimisation.jl](https://github.com/JuliaIntervals/IntervalOptimisation.jl), [IntervalArithmetic.jl](https://github.com/JuliaIntervals/IntervalArithmetic.jl) 

## Pull Requests

| Tasks                 | Related PRs | Status |
|:---------------------:|:------------------:|:------:|
| Interval Constraint Propagation using a Tape | [IntervalConstraintProgramming.jl#97](https://github.com/JuliaIntervals/IntervalConstraintProgramming.jl/pull/97) | Open |
| Recording `getindex` to make gradients work  | [IntervalConstraintProgramming.jl#100](https://github.com/JuliaIntervals/IntervalConstraintProgramming.jl/pull/100) | Open |
| Global Optimisation | [IntervalOptimisation.jl#9](https://github.com/JuliaIntervals/IntervalOptimisation.jl/pull/9) | Open |
| Interval Newton Method for one dimension | [IntervalRootFinding.jl#39](https://github.com/JuliaIntervals/IntervalRootFinding.jl/pull/39) | Merged |
| Robustness and efficiency for `newton1d` | [IntervalRootFinding.jl#50](https://github.com/JuliaIntervals/IntervalRootFinding.jl/pull/50) | Merged |
| System of Linear Equations | [IntervalRootFinding.jl#67](https://github.com/JuliaIntervals/IntervalRootFinding.jl/pull/67) | Merged |
| Solvers for Quadratic Interval Equations | [IntervalRootFinding.jl#68](https://github.com/JuliaIntervals/IntervalRootFinding.jl/pull/68) | Merged |
| Automatic evaluation of slope expansions | [IntervalRootFinding.jl#69](https://github.com/JuliaIntervals/IntervalRootFinding.jl/pull/69) | Merged |
| Slope Interval Newton method | [IntervalRootFinding.jl#73](https://github.com/JuliaIntervals/IntervalRootFinding.jl/pull/73) | Open |
| Automatic evaluation of multidimensional slope | [IntervalRootFinding.jl#76](https://github.com/JuliaIntervals/IntervalRootFinding.jl/pull/76) | Open |
| Linear Hull | [IntervalRootFinding.jl#79](https://github.com/JuliaIntervals/IntervalRootFinding.jl/pull/79) | Open |
| Multidimensional Interval Newton Method | [IntervalRootFinding.jl#81](https://github.com/JuliaIntervals/IntervalRootFinding.jl/pull/81) | Open |
| Fix deprecations and upgrade to 0.7 | [IntervalRootFinding.jl#89](https://github.com/JuliaIntervals/IntervalRootFinding.jl/pull/89) | Open |
| `extended_div` | [IntervalArithmetic.jl#111](https://github.com/JuliaIntervals/IntervalArithmetic.jl/pull/111) | Merged |
| `abs2` | [IntervalArithmetic.jl#101](https://github.com/JuliaIntervals/IntervalArithmetic.jl/pull/101) | Merged |
| Bug in `extended_div` | [IntervalArithmetic.jl#146](https://github.com/JuliaIntervals/IntervalArithmetic.jl/pull/146) | Merged |
| Set Operations | [IntervalArithmetic.jl#154](https://github.com/JuliaIntervals/IntervalArithmetic.jl/pull/154) | Merged |
| Hashing for Intervals | [IntervalArithmetic.jl#161](https://github.com/JuliaIntervals/IntervalArithmetic.jl/pull/161) | Merged |
| Interoperability between IntervalBox and SVector | [IntervalArithmetic.jl#166](https://github.com/JuliaIntervals/IntervalArithmetic.jl/pull/166) | Merged |

## Blog Posts

Blog posts summarizing the work done during the entire period.

1. [Getting Selected and First Two Weeks](https://eeshan9815.github.io/blog-gsoc/getting-selected/)
2. [Weeks 3 and 4](https://eeshan9815.github.io/blog-gsoc/weeks-3-and-4/)
3. [Coding Phase-II](https://eeshan9815.github.io/blog-gsoc/coding-phase-2/)
4. [Coding Phase-III](https://eeshan9815.github.io/blog-gsoc/coding-phase-3/)


## Future Work

- Integrate the global optimisation into [JuMP](https://github.com/JuliaOpt/JuMP.jl/) since it's the standard for Mathematical Optimisation in Julia
- Improve constrained optimisation using John Conditions
- Rewrite IntervalConstraintProgramming using Cassette and follow the development cycle of Capstan
- Keep maintaining everything implemented until now, and finding new algorithms to improve the performance and robustness
- Integrate ICP into IntervalRootFinding and make root finding more efficient

## Acknowledgements

I would like to thank Dr David P. Sanders for mentoring me throughout the project, and for his incredible patience and support.

My code builds upon 
- [julia](https://github.com/JuliaLang/julia)
- [IntervalArithmetic.jl](https://github.com/JuliaIntervals/IntervalArithmetic.jl), authored by Dr. David P. Sanders and Dr. Luis Benet
- [IntervalContractors.jl](https://github.com/JuliaIntervals/IntervalContractors.jl), authored by Dr. David P. Sanders
- [IntervalConstraintProgramming.jl](https://github.com/JuliaIntervals/IntervalConstraintProgramming.jl), authored by Dr. David P. Sanders
- [IntervalRootFinding.jl](https://github.com/JuliaIntervals/IntervalRootFinding.jl), authored by Dr. David P. Sanders and Dr. Luis Benet
- [IntervalOptimisation.jl](https://github.com/JuliaIntervals/IntervalOptimisation.jl), authored by Dr. David P. Sanders

Shoutout to the entire Julia community for being awesome and amazingly helpful!
