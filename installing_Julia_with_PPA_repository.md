# Julia installation guide

## Timestamp of this document
* Created: 160718 (yymmdd)
* Last update: 160718 (yymmdd)

## Environment
* Ubuntu 16.04 desktop

## Installation guide
https://github.com/JuliaLang/julia/blob/master/README.md


## Notation
* `#` means that you should run the command with root privilege.
* `$` means that it is recommended to run the command without root privilege.
* `~` is equivalent to your home directory. (e.g. `/home/jhseo`)


## Steps

### 1) Install "[Required Build Tools and External Libraries](https://github.com/JuliaLang/julia/blob/master/README.md#required-build-tools-and-external-libraries)"
```
# apt-get update
# apt-get install vim build-essential gfortran perl wget curl m4 patch cmake openssl \
libopenblas-dev libopenblas-base git
```

### 2) [Add PPA repository and install Julia](http://julialang.org/downloads/platform.html)
```Shell
$
sudo add-apt-repository ppa:staticfloat/juliareleases
sudo add-apt-repository ppa:staticfloat/julia-deps
sudo apt-get update
sudo apt-get install julia
```

### 3) [Install `ParallelAccelerator.jl` package in Julia](http://parallelacceleratorjl.readthedocs.io/en/latest/install.html)
At the `julia>` prompt, run these commands:
```Julia
Pkg.add("ParallelAccelerator")          # Install this package and its dependencies.

Pkg.checkout("ParallelAccelerator")     # Switch to master branch
Pkg.checkout("CompilerTools")           # Switch to master branch
Pkg.build("ParallelAccelerator")        # Build the C++ runtime component of the package.
Pkg.test("CompilerTools")               # Run CompilerTools tests.
Pkg.test("ParallelAccelerator")         # Run ParallelAccelerator tests.
```

### 3-1) [Updating `ParallelAccelerator.jl`](http://parallelacceleratorjl.readthedocs.io/en/latest/install.html) (when you want to update `ParallelAccelerator.jl`)
At the `julia>` prompt, run these commands:
```Julia
Pkg.checkout("ParallelAccelerator")     # Switch to master branch
Pkg.checkout("CompilerTools")           # Switch to master branch
Pkg.build("ParallelAccelerator")        # Build the C++ runtime component of the package.
Pkg.test("CompilerTools")               # Run CompilerTools tests.
Pkg.test("ParallelAccelerator")         # Run ParallelAccelerator tests.
```
