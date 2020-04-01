#  Python Support in Node.js

> A guide to integrate Python support in Node.js.

## Installation

### On Windows/Linux/MacOSX/Raspbian

#### Node.js and Node Package Manager

[![npm](https://img.shields.io/npm/v/node?label=node&style=flat-square)](https://github.com/nodejs/node)
[![npm](https://img.shields.io/npm/v/npm?style=flat-square)](https://github.com/npm/npm)

*Node.js* is an open-source, cross-platform, JavaScript runtime environment used to write command line tools and server-side scripts.

*Node Package Manager* (NPM) is the package manager for the JavaScript programming language.

A complete installation guide for Node.js and Node Package Manager is available in [this link](https://github.com/Sampreet/install-guides/blob/master/languages/nodejs/nodejs-npm.md).

#### Python via Anaconda/Miniconda Distribution

[![Conda](https://img.shields.io/conda/v/conda-forge/python?style=flat-square)](https://github.com/python/cpython)
![Conda](https://img.shields.io/conda/dn/conda-forge/python?style=flat-square)

*Python* is an interpreted, high-level, general-purpose language supporting object-oriented programming with more emphasis on code-readibility and extensibility. 

A complete installation guide for Python via the Anaconda/Miniconda Distribution is available in [this link](https://github.com/Sampreet/install-guides/blob/master/languages/python/python-anaconda-miniconda.md).

## Configuration

### On Raspbian

Set the python environment to the installed version of Python by running:

```bash
sudo npm config set python /path/to/miniconda/bin
```

Additionally, install the build tools necessary for compilation of some node modules.

```bash
npm install --global --production windows-build-tools
```