# Anaconda/Miniconda Python

![PyPI](https://img.shields.io/pypi/pyversions/Django.svg?style=flat-square)

> A guide to installing Python versions via Anaconda/Miniconda package

## Installation on Raspbian

### Installing Python via Miniconda 

Download the latest Minoconda package for Python (v2.x or v3.x depending on requirement) for the device architecture (armv6/armv7) from the [Miniconda repository](https://repo.continuum.io/miniconda/). Navigating to the downloaded directory, run the following command and install the Miniconda Python package through the terminal:

```
bash <miniconda-file-name>.sh
```

Set the python environment to the installed version of Python by running:

```
sudo npm config set python /path/to/miniconda/bin
```

Additionally, install the build tools necessary for compilation of some node modules.

```
npm install --global --production windows-build-tools
