# Julia implementation of Kullback-Leibler divergences and kl-UCB indexes

This repository contains a small, simple and efficient module, implementing various [Kullback-Leibler divergences](https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence) for parametric 1D continuous or discrete distributions.


## References
- [Garivier & Cappé & Kaufmann, 2012](http://mloss.org/software/view/415/), for the pymaBandits project on which this implementation is based,
- [Besson, 2018](https://github.com/SMPyBandits/SMPyBandits/), SMPyBandits project for improvements on the initial implementation,
- [Filippi & Cappé & Garivier, 2011](https://arxiv.org/pdf/1004.5229.pdf),
- [Garivier & Cappé, 2011](https://arxiv.org/pdf/1102.2490.pdf),
- [Kullback & Leibler, 1951](http://www.jstor.org/stable/2236703) for the first article introducing the so-called Kullback & Leibler divergences.

## Examples
### Simple usage
If the [`KullbackLeibler.jl`](src/KullbackLeibler.jl) file is accessible in your PATH or in Python's path:

```julia
julia> using KullbackLeibler
julia> KullbackLeibler.klBern(0.5, 0.5)
0.0
julia> KullbackLeibler.klBern(0.1, 0.9)
1.757779...
julia> KullbackLeibler.klBern(0.9, 0.1)  # And this KL is symmetric
1.757779...
julia> KullbackLeibler.klBern(0.4, 0.5)
0.020135...
julia> KullbackLeibler.klBern(0.01, 0.99)
4.503217...
```

You can also use the common function that supports different distributions using the [`Distributions`](https://juliastats.github.io/Distributions.jl/) module.

```julia
julia> using Distributions
julia> Bern1 = Distributions.Bernoulli(0.33)
Distributions.Bernoulli{Float64}(p=0.33)
julia> Bern2 = Distributions.Bernoulli(0.42)
Distributions.Bernoulli{Float64}(p=0.42)
julia> ex_kl_1 = KL( Bern1, Bern2 )  # Calc KL divergence for Bernoulli R.V
0.017063...
julia> klBern(0.33, 0.42)  # same!
0.017063...
```

### Vectorized version?
All functions are *not* vectorized, and assume only one value for each argument.
If you want vectorized function, [please ask](https://github.com/Naereen/KullbackLeibler.jl/issues/new) and we will try to add them.

### Documentation
See [this file](https://naereen.github.io/KullbackLeibler.jl/docs/index.html).

----

## Install and build
### Manually ?
Easy! Download the [`KullbackLeibler.jl`](src/KullbackLeibler.jl) and copy it to your working folder.

I will add this package to `METADATA.jl` as soon as possible, and then it will be possible to install it using:

```julia
julia> Pkg.add("KullbackLeibler")
```

----

## Python implementation ?

This module was initially a Python module, see [here on GitHub](https://github.com/Naereen/Kullback-Leibler-divergences-and-kl-UCB-indexes).

----

## About
### Language and dependencies
[Julia, v0.6+](REQUIRE).

Dependencies

- [`Distributions`](https://github.com/JuliaStats/Distributions.jl/), v0.15+.

### :scroll: License ? [![GitHub license](https://img.shields.io/github/license/Naereen/KullbackLeibler.jl.svg)](https://github.com/Naereen/badges/blob/master/LICENSE)
[MIT Licensed](https://lbesson.mit-license.org/) (file [LICENSE](LICENSE)).
© [Lilian Besson](https://GitHub.com/Naereen), 2018.

[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://GitHub.com/Naereen/KullbackLeibler.jl/graphs/commit-activity)
[![Ask Me Anything !](https://img.shields.io/badge/Ask%20me-anything-1abc9c.svg)](https://GitHub.com/Naereen/ama)
[![Analytics](https://ga-beacon.appspot.com/UA-38514290-17/github.com/Naereen/KullbackLeibler.jl/README.md?pixel)](https://GitHub.com/Naereen/KullbackLeibler.jl/)

[![ForTheBadge uses-badges](http://ForTheBadge.com/images/badges/uses-badges.svg)](http://ForTheBadge.com)
[![ForTheBadge uses-git](http://ForTheBadge.com/images/badges/uses-git.svg)](https://GitHub.com/)

[![forthebadge made-with-julia](https://img.shields.io/badge/Made%20with-Julia-1abc9c.svg)](https://www.julialang.org/)
[![ForTheBadge built-with-science](http://ForTheBadge.com/images/badges/built-with-science.svg)](https://GitHub.com/Naereen/)
