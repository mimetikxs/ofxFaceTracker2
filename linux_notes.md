# How to compile Dlib on Linux

Dlib 19.24

Tested on Ubuntu 24.04, Nvidia Driver 550.120, CUDA 12.4

### Check hardware capabilities
```
nvcc --version
```
```
nvidia-smi
```

### Install CUDA Toolkit if needed

Follow the [guide](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html) to install CUDA and make sure the [latest version is active](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#select-the-active-version-of-cuda).

NOTE: You can use Ubuntu's `Software & Updates > Additional Drivers` graphical interface to select the driver.

### Install cuDNN if needed

Download [cuDNN](https://developer.nvidia.com/cudnn-downloads?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=24.04&target_type=deb_local) and follow the [installation guide](
https://docs.nvidia.com/deeplearning/cudnn/installation/latest/linux.html)

```
sudo apt-get -y install cudnn9-cuda-12
```

### Download and compile Dlib

[Download](https://github.com/davisking/dlib/releases/tag/v19.24) or [clone](https://github.com/davisking/dlib/tags) dlib

It's recommended to install OpenBLAS
```
sudo apt-get install libopenblas-dev liblapack-dev
```

Compile as shared lib ([+info](https://stackoverflow.com/questions/33996361/create-a-shared-library-for-dlib)):
```
cd dclib/dlib
mkdir build
cd build
cmake -DBUILD_SHARED_LIBS=1 ..
make
```

### Copy to addon folder

Copy headers and compiled libs to the appropriate folder in the addon.

You might remove 

### Resources

[Manage multiple CUDA environments (gist)](https://gist.github.com/garg-aayush/156ec6ddda3d62e2c0ddad00b7e66956)

https://github.com/davisking/dlib/issues/3008