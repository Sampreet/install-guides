# Node.js/NPM Installation

> A guide to installing Node.js and NPM versions

Node.js uses event-driven, non-blocking I/O model. NPM is the package manager for JavaScript.

## Installation on Linux

### Installing NVM

To install or update nvm via terminal, use the install script using cURL:
```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.1/install.sh | bash
```
or Wget:
```
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.31.1/install.sh | bash
```

### Installing Node.js

To install a specific version of Node.js, say v6.1.0:
```
nvm install 6.1.0
```

### Changing Version

To change the current version running to another, say v4.2:
```
nvm use 4.2
```

### Getting the Path

To get the path to the executable where a version of Node.js, say v5.0, was installed:
```
nvm which 5.0
```

### Migrating NPM Packages

To install a new version ```v2``` of Node.js ad migrate npm packages from a previous version ```v1```:
```
nvm install v2 --reinstall-packages-from=v1
```

## Installation on Raspbian

*Note: A complete documentation for setting up an ssh environment on the Raspberry Pi 3 can be found in this [blog](http://thisdavej.com/beginners-guide-to-installing-node-js-on-a-raspberry-pi/).*

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

Alternatively, one can download and build the binaries of ```Node.js``` from the official [Node.js downloads page](https://nodejs.org/en/download/) according to the architecture of the device and the OS installed.
