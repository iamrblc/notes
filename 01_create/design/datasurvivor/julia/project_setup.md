---
title: Setting up projects
tags:
  - julia
  - init
  - pkg
---

## Setting up projects

Similar to what you have in `R` or how `uv` handles `python` projects, `Julia` relies on `.toml` files. `Project.toml` can be generated manually or automatically. This is some high level stuff. `Manifest.toml` is the real deal with all the nuances. It is automatically generated. It's okay if you already have a `pyproject.toml`. They work separately.

In terminal:

```bash
julia --project=.
```

This will open up the Julia REPL (read-evaluate-print loop) and set up the environment in the given folder (.) Then you can activate the environment. 

```julia
] activate .
] add Turing DataFrames CSV StatsPlots
```

You can add as many packages as you want, but these are the ones that you most likely need to start basic data and statistical modelling work. This will run for a while for sure. Especially if you are used to `uv`...

Important, that this only activates the environment within the REPL. If you write scripts, you have to start with this.

```julia
using Pkg
Pkg.activate(@__DIR__)
```
## Julia MOC
[[0_julia_moc]]