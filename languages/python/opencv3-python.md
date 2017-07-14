# OpenCV v3 for Python

> A guide to installing the OpenCV3 libraries for Python

## Installation on Linux

A alternate installation guide for OpenCV for Image Processing in Python 2.7.11+ is available [here](http://docs.opencv.org/2.4/doc/tutorials/introduction/linux_install/linux_install.html).

### Prerequisites

#### Installing Python 2.7.11+

In terminal:
```
sudo apt-get install build-essential checkinstall
sudo apt-get install libreadline-gplv2-dev libncursesw5-dev libssl-dev libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev
```

Navigate to the download folder, say ```Downloads```:
```
cd ~/Downloads/
```
Download the python build 2.7.11 using wget:
```
wget http://www.python.org/ftp/python/2.7.11/Python-2.7.11.tgz
```

Extract and go to the directory ```Python-2.7.11```:
```
tar -xvf Python-2.7.11.tgz
cd Python-2.7.11
```
In terminal:
```
./configure
make
sudo checkinstall
```

### Installing Dependencies for OpenCV

Install the dependencies for OpenCV:
```
sudo apt-get install build-essential
sudo apt-get install python-numpy python-scipy python-matplotlib
sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
sudo apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev
```

### Downloading OpenCV

Launch Git client and clone [OpenCV repository](http://github.com/itseez/opencv). Or, via terminal:
```
cd ~/<working _directory>
git clone https://github.com/Itseez/opencv.git
```

### Installing OpenCV

Put the generated Makefiles in a temporary directory:
```
cd ~/opencv
mkdir release
cd release
cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local ..
```

Install OpenCV:
```
make
sudo make install
```
