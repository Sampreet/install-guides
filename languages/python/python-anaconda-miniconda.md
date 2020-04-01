# Python via Anaconda/Miniconda Distribution

[![Conda](https://img.shields.io/conda/v/conda-forge/python?style=flat-square)](https://github.com/python/cpython)
![Conda](https://img.shields.io/conda/dn/conda-forge/python?style=flat-square)

> A guide for installing Python versions via the Anaconda/Miniconda distribution.

*Python* is an interpreted, high-level, general-purpose language supporting object-oriented programming with more emphasis on code-readibility and extensibility.

## Installation

### On Windows

Download the graphical installer (```.exe```) for [Anaconda](https://www.anaconda.com/distribution/#download-section) or [Miniconda](https://docs.conda.io/en/latest/miniconda.html) for the required version of Python and install. 

***Note: If Anaconda/Miniconda is the only distribution of Python in your system, make sure to check both "Add Anaconda to the system PATH environment variable" and "Register Anaconda as the system Python 3.x".***

### On Linux/MacOSX

Download the command line installer (```.sh```) for [Anaconda](https://www.anaconda.com/distribution/#download-section) or [Miniconda](https://docs.conda.io/en/latest/miniconda.html) for the required version of Python and install running the following command in the terminal by replacing ```path/to/downloaded/file``` by the complete path to the directory of the downloaded installer along with the file name:

```bash
bash path/to/downloaded/file.sh
```

### On Raspbian

***Note: A complete documentation for setting up an ssh environment on the Raspberry Pi 3 can be found in this [blog](http://thisdavej.com/beginners-guide-to-installing-node-js-on-a-raspberry-pi).***

Download the latest Minoconda package (```.sh```) for the required version of Python as well as the required device architecture (armv61/armv71) from the [Miniconda repository](https://repo.continuum.io/miniconda/). Run the following command in the terminal by replacing ```path/to/downloaded/file``` with the complete path to the directory of the downloaded installer along with the file name:

```bash
bash path/to/downloaded/file.sh
```

## Configuration

Open the Anaconda command prompt in the elevated (administrator) mode and add the ```conda-forge``` channel as the first hit channel:

```bash
conda config --add channels conda-forge
conda config --set channel_priority strict
```

Initialize the conda environment using:

```bash
conda init
```

## Package Management

To install a package, use the following command by replacing ```package``` with the name of the package and ```version``` with the requied version:

```bash
conda install package=version
```

To install multiple packages, append them one after the other separated by spaces.

To update all packages, use:

```bash
conda update --all
```

To list all installed packages, use:

```bash
conda list
```

To remove a package, use the following command by replacing ```package``` with the name of the package:

```bash
conda remove package
```


