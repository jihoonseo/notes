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

1) Install "[Required Build Tools and External Libraries](https://github.com/JuliaLang/julia/blob/master/README.md#required-build-tools-and-external-libraries)"
```
# apt-get install vim build-essential gfortran perl wget curl m4 patch cmake openssl \
libopenblas-dev libopenblas-base
```

2) [Source Download and Compilation](https://github.com/JuliaLang/julia/blob/master/README.md#source-download-and-compilation)
```Shell
~$ git clone git://github.com/JuliaLang/julia.git
~$ cd julia
~/julia$ git checkout release-0.4
~/julia$ make -j 8 # perform a parallel build
```
