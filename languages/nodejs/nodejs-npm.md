# Node.js and Node Package Manager

[![npm](https://img.shields.io/npm/v/node?label=node&style=flat-square)](https://github.com/nodejs/node)
[![npm](https://img.shields.io/npm/v/npm?style=flat-square)](https://github.com/npm/npm)

> A guide to installing Node.js and Node Package Manager

*Node.js* is an open-source, cross-platform, JavaScript runtime environment used to write command line tools and server-side scripts. 

*Node Package Manager* (NPM) is the package manager for the JavaScript programming language.

## Installation

### On Windows/MacOSX

Download the installers for Node.js from the official [Node.js page](https://nodejs.org/en/download) for your operating system and install.

### On Linux using Binaries

Download the Linux binaries for Node.js rom the official [Node.js page](https://nodejs.org/en/download). Run the following command in the terminal by replacing ```path/to/downloaded/file``` with the complete path to the directory of the downloaded installer along with the file name:

```bash
bash path/to/downloaded/file.sh
```

### On Linux via Node Version Manager

#### Node Version Manager

[![GitHub package.json version](https://img.shields.io/github/package-json/v/nvm-sh/nvm?style=flat-square)](https://github.com/nvm-sh/nvm)
![GitHub](https://img.shields.io/github/license/nvm-sh/nvm?style=flat-square)

*Node Version Manager* is a version manager for Node.js, designed to be installed per-user, and invoked per-shell. It helps manage and switch between multiple Node.js versions with ease.

To install or update nvm via terminal, use the install script using cURL:
```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.1/install.sh | bash
```
or Wget:
```
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.31.1/install.sh | bash
```

#### Node.js and Node Package Manager

To install a specific version of Node.js, say v6.1.0:
```
nvm install 6.1.0
```

### On Raspbian

***Note: A complete documentation for setting up an ssh environment on the Raspberry Pi 3 can be found in this [blog](http://thisdavej.com/beginners-guide-to-installing-node-js-on-a-raspberry-pi).***

Run the following lines on terminal to install Node.js v6.x in it:

```
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs
``` 

To install Node.js v8.x.x, run:

```
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get install -y nodejs
``` 

## Package Management

### On Linux

To change the current version running to another, say v4.2:
```
nvm use 4.2
```

To get the path to the executable where a version of Node.js, say v5.0, was installed:
```
nvm which 5.0
```

To install a new version ```v2``` of Node.js ad migrate npm packages from a previous version ```v1```:
```
nvm install v2 --reinstall-packages-from=v1
```
