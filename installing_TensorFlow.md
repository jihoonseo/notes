
## Environments
* OS: Ubuntu 14.04 desktop amd64


## Download and setup
https://www.tensorflow.org/versions/r0.10/get_started/os_setup.html

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
```

* Reboot your computer

`# sync;sync;reboot`

## Install TensorFlow (Pip Installation)
`sudo apt-get install python-pip python-dev`

```Shell
# Then, select the correct binary to install:
# Ubuntu/Linux 64-bit, GPU enabled, Python 2.7
# Requires CUDA toolkit 7.5 and CuDNN v4. For other versions, see "Install from sources" below.
$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.10.0rc0-cp27-none-linux_x86_64.whl

# Install TensorFlow:
# Python 2
$ sudo pip install --upgrade $TF_BINARY_URL
```

## Test the TensorFlow installation



### Run TensorFlow from the Command Line
```Python
>>> import tensorflow as tf
>>> hello = tf.constant('Hello, TensorFlow!')
>>> sess = tf.Session()
>>> print(sess.run(hello))
Hello, TensorFlow!
>>> a = tf.constant(10)
>>> b = tf.constant(32)
>>> print(sess.run(a + b))
42
>>>
```

### Run a TensorFlow demo model
```Shell
$ python /usr/local/lib/python2.7/dist-packages/tensorflow/models/image/mnist/convolutional.py
OR
# python /usr/local/lib/python2.7/dist-packages/tensorflow/models/image/mnist/convolutional.py
```
