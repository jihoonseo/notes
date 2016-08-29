

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

## Install CUDA
https://www.tensorflow.org/versions/r0.10/get_started/os_setup.html#optional-install-cuda-gpus-on-linux

### Download CUDA
https://developer.nvidia.com/cuda-downloads

1. Download `cuda-repo-ubuntu1404-7-5-local_7.5-18_amd64.deb`
2. `sudo dpkg -i cuda-repo-ubuntu1404-7-5-local_7.5-18_amd64.deb`
3. `sudo apt-get update`
4. `sudo apt-get install cuda`

### CUDA Installation Guide for Linux
http://developer.download.nvidia.com/compute/cuda/7.5/Prod/docs/sidebar/CUDA_Installation_Guide_Linux.pdf

### Download and install cuDNN
https://developer.nvidia.com/cudnn

* Download cuDNN v4 (v5 is currently a release candidate and is only supported when installing TensorFlow from sources).
(cuDNN v4 Library for Linux)

https://www.tensorflow.org/versions/r0.10/get_started/os_setup.html#optional-install-cuda-gpus-on-linux

1. `tar xvzf cudnn-7.5-linux-x64-v4.tgz`
2. `sudo cp cuda/include/cudnn.h /usr/local/cuda/include`
3. `sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64`
4. `sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*`

### (Linux) Enable GPU Support

https://www.tensorflow.org/versions/r0.10/get_started/os_setup.html#optional-linux-enable-gpu-support

* Append these lines to your `.bashrc` (e.g. `/home/jhseo/.bashrc`)
```Shell
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/cuda/lib64:/usr/local/cuda/extras/CUPTI/lib64"
export CUDA_HOME=/usr/local/cuda
export CUDA_ROOT=/usr/local/cuda
```

* Reboot your computer

`# sync;sync;reboot`

### Using the GPU
* Create `.theanorc` file in your home directory. (e.g. `/home/jhseo/.theanorc`)
```
[global]
device = gpu
floatX = float32

[cuda]
root = /usr/local/cuda
```

### Testing Theano with GPU
* Save below as `check1.py`
```Python
from theano import function, config, shared, sandbox
import theano.tensor as T
import numpy
import time

vlen = 10 * 30 * 768  # 10 x #cores x # threads per core
iters = 1000

rng = numpy.random.RandomState(22)
x = shared(numpy.asarray(rng.rand(vlen), config.floatX))
f = function([], T.exp(x))
print(f.maker.fgraph.toposort())
t0 = time.time()
for i in range(iters):
    r = f()
t1 = time.time()
print("Looping %d times took %f seconds" % (iters, t1 - t0))
print("Result is %s" % (r,))
if numpy.any([isinstance(x.op, T.Elemwise) for x in f.maker.fgraph.toposort()]):
    print('Used the cpu')
else:
    print('Used the gpu')
```

```Shell
$ THEANO_FLAGS=mode=FAST_RUN,device=cpu,floatX=float32 python check1.py
$ THEANO_FLAGS=mode=FAST_RUN,device=gpu,floatX=float32 python check1.py
```

### Test the newly installed packages
1. NumPy (~30s): `python -c "import numpy; numpy.test()"`
2. SciPy (~1m): `python -c "import scipy; scipy.test()"`
3. Theano (~30m): `python -c "import theano; theano.test()"`

### Speed test Theano/BLAS
`python /usr/local/lib/python2.7/dist-packages/theano/misc/check_blas.py`

### Test GPU configuration
`THEANO_FLAGS=floatX=float32,device=gpu python /usr/local/lib/python2.7/dist-packages/theano/misc/check_blas.py`
