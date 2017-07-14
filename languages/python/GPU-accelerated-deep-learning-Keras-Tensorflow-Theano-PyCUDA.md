# GPU-ACCELERATED DEEP LEARNING (Keras, Theano, PyCUDA, Tensorflow)

> A guide to installing the deep learning toolkits for Python

## Installation on Windows

### Installing Microsoft Visual Studio

Download the setup wizard for [Visual Studio Community 2017](https://www.visualstudio.com/downloads/) and install the [essential components](http://docs.nvidia.com/cuda/cuda-installation-guide-microsoft-windows/index.html#system-requirements). The followning components are necessary for Theano and CUDA and should be checked:

```
C++/CLI support
C++ profiling tools
VC++ 2015.3 toolset
Visual C++ compilers and libraries for ARM
Visual C++ runtime for UWP
Visual C++ tools for CMake
Windows 8.1 SDK
Windows 10 SDK (10.0.10240.0)
Windows Universal C Runtime
Windows Universal CRT SDK
```

Update the installed components through the ```Visual Studio Installer``` application.

Alternatively, [Visual Studio Community 2015 Update 3](https://download.microsoft.com/download/b/e/d/bedddfc4-55f4-4748-90a8-ffe38a40e89f/vs2015.3.com_enu.iso) can be installed with the following components:

```
Common Tools for Visual C++ 2015
Universal Windows App Development Tools (1.4.1)
Windows 8.1 SDK
Windows 10 SDK (10.0.10240.0)
Windows 10 SDK (10.0.14393.0)
Windows Universal CRT SDK
```

The SDKs can be separately downloaded from the [Windows SDK and Emulator Archive](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive) as well.

Update the following System Environment Variables:

```
PATH = C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\bin
INCLUDE = C:\Program Files (x86)\Windows Kits\10\Include\10.0.10240.0\ucrt
LIB = C:\Program Files (x86)\Windows Kits\10\Lib\10.0.10240.0\um\x64;C:\Program Files (x86)\Windows Kits\10\Lib\10.0.10240.0\ucrt\x64
```

### Installing Python using Anaconda3

Download and install the appropriate version of [Anaconda3-4.2.0](https://repo.continuum.io/archive/index.html) for Python 3.5.x specifically.

Once installed, run the following command in Anaconda Prompt:

```
conda install numpy scipy libpython mkl-service nose nose-parameterized sphinx pydot-ng
conda update --all
```

If the system already has another version of Anaconda installed, create a new environment for Python 3.5.x and Anaconda3 using the following commands in Anaconda Prompt (replace py35 with any desired name for the environment):

```
conda create -n py35 python=3.5 anaconda
```

In this case, update the System Environment Variables as:

```
PYTHON_HOME = <path\to\Anaconda3>\envs\py35
PATH = %PYTHON_HOME%;%PYTHON_HOME%\Scripts;%PYTHON_HOME%\Library\bin
```

For more information on managing environments in Anaconda, click [here](https://conda.io/docs/using/envs.html).

Activate the environment and install libpython:

```
activate py35
conda install numpy scipy libpython mkl-service nose nose-parameterized sphinx pydot-ng
conda update --all
```

**NOTE: All commands hereafter should be run on Anaconda Prompt (inside the py35 environment) unless specified otherwise.**

### Installing the CUDA Toolkit

Download and install the appropriate version of CUDA Toolkit 8.0.61 from [here](https://developer.nvidia.com/cuda-downloads).
Refer to the [Installation Documenatation](http://docs.nvidia.com/cuda/cuda-installation-guide-microsoft-windows/index.html) for advanced instructions (optional).

Also, it is preferable to install [NVIDIA CUDA Deep Neural Network (cuDNN)] (https://developer.nvidia.com/rdp/cudnn-download#a-collapseTwo) library for training convnets.

### Installing a G++ Complier

Download the [MinGW-w64 Web Installer](https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win32/Personal%20Builds/mingw-builds/installer/) and install version 5.4.0 (newer versions are not supported by Theano).

Update the following System Environment Variables:

```
MINGW_HOME = C:\Program Files\mingw-w64\x86_64-5.4.0-posix-seh-rt_v5-rev0
PATH = C:\Program Files\mingw-w64\x86_64-5.4.0-posix-seh-rt_v5-rev0\mingw64\bin
```

Alternatively, a fully-compatible version of GCC can be obtained through the ```m2w64-toolchain``` package using:

```
conda install m2w64-toolchain
```

### Installing Keras and Theano

Run the following command to install Keras and Theano:

```
pip install Keras==2.0.4
```

Create a ```.theanorc``` file in the home directory and copy the following contents replacing the nvcc variables to Anaconda ```lib``` directory and ```cl.exe``` directory respectively:

```
[global]
floatX = float32
device = cuda
init_gpu_device = cuda0
enable_initial_driver_test = True

[nvcc]
flags=-L<path\to\Anaconda>\envs\py35\libs
compiler_bindir=C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\bin
```

Update the following System Environment Variables:

```
THEANO_FLAGS_CPU = floatX=float32,device=cpu,lib.cnmem=0.8
THEANO_FLAGS_GPU = floatX=float32,device=gpu,dnn.enabled=False,lib.cnmem=0.8
```

Theano uses the ```libgpuarray``` library for GPU/CPU code generation on CUDA and can be installed the ```pygpu``` library as:

```
conda install pygpu
```

### Installing PyCUDA and SkCUDA

Download the appropriate package for PyCUDA satisfying the OS and Anaconda builds from [here](http://www.lfd.uci.edu/~gohlke/pythonlibs/#pycuda) and run the following command in Anaconda Prompt:

```
pip install "<path\to\downloaded\pycuda\file>"
pip install scikit-cuda
```

### Installing Tensorflow

To install Tensorflow in an Anaconda environment, run the following commands in serial:

```
pip install --ignore-installed --upgrade https://storage.googleapis.com/tensorflow/windows/cpu/tensorflow-1.1.0-cp35-cp35m-win_amd64.whl
pip install --ignore-installed --upgrade https://storage.googleapis.com/tensorflow/windows/gpu/tensorflow_gpu-1.1.0-cp35-cp35m-win_amd64.whl
```
**NOTE: Currently, Tensorflow libraries for Python only support 3.5.x versions on 64-bit processors.**