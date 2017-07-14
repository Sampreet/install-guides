# Node.js/NPM Installation

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

