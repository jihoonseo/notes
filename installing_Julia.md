# 

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

### 2) [Source Download and Compilation](https://github.com/JuliaLang/julia/blob/master/README.md#source-download-and-compilation)
```Shell
~$ git clone git://github.com/JuliaLang/julia.git
~$ cd julia
~/julia$ git checkout release-0.4
~/julia$ make -j 8 # perform a parallel build
```

* add a soft link to the `julia` executable in the `julia` directory to `/usr/local/bin` (or any suitable directory already in your path)
```
# cd /usr/local/bin
# ln -s /home/jhseo/julia/usr/bin/julia ./
```

### 2-1) [General troubleshooting](https://github.com/JuliaLang/julia/blob/master/README.md#general-troubleshooting)
* Try `make clean` and `make -j 8` again.
* If above is not enough, try `make cleanall` and `make -j 8` again.

### 2-2) [Updating an existing source tree](https://github.com/JuliaLang/julia/blob/master/README.md#updating-an-existing-source-tree) (when you want to update Julia)
```Shell
~$ cd julia
~/julia$ git pull
~/julia$ make -j 8 # perform a parallel build
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
