

### Install "Required Build Tools and External Libraries"
`apt-get install vim build-essential gfortran perl wget curl m4 patch cmake openssl git`

### Install OpenBLAS
`apt-get install libopenblas-dev libopenblas-base`

### Install LAPACK
`apt-get install liblapack-dev liblapack3 liblapack-pic liblapacke liblapacke-dev liblapack3gf`

### Don't install ATLAS
`apt-get remove libatlas-base-dev libatlas-dev libatlas3-base libatlas3gf-base`
> "OpenBLAS is faster then ATLAS"
http://deeplearning.net/software/theano/install_ubuntu.html#install-ubuntu

### Upgrade pip
`pip install -U pip`

### Easy Installation of an Optimized Theano on Current Ubuntu
http://deeplearning.net/software/theano/install_ubuntu.html#install-ubuntu
```Shell
sudo apt-get install python-numpy python-scipy python-dev python-pip python-nose g++ libopenblas-dev git
sudo pip install Theano
```

### Install python packages
```Shell
pip install keras
```
