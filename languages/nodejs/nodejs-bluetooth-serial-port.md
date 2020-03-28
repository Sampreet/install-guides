# Node.js Bluetooth Serial Port (Deprecated)

[![GitHub package.json version](https://img.shields.io/github/package-json/v/eelcocramer/node-bluetooth-serial-port?style=flat-square)](https://github.com/eelcocramer/node-bluetooth-serial-port)

> A guide to setting up and installing the bluetooth-serial-port module for Node.js.

*bluetooth-serial-port* is a node module that enables communication over Bluetooth serial port with devices running Node.js.

## Installation 

### On Raspbian

#### Node.js and Node Package Manager

[![npm](https://img.shields.io/npm/v/node?label=node&style=flat-square)](https://github.com/nodejs/node)
[![npm](https://img.shields.io/npm/v/npm?style=flat-square)](https://github.com/npm/npm)

*Node.js* is an open-source, cross-platform, JavaScript runtime environment used to write command line tools and server-side scripts.

*Node Package Manager* (NPM) is the package manager for the JavaScript programming language.

A complete installation guide for Node.js and Node Package Manager is available in [this link](https://github.com/Sampreet/install-guides/blob/master/languages/nodejs/nodejs-npm.md).

***Note: ```Node.js 13+``` is not supported.***

#### Python via Anaconda/Miniconda Distribution

[![Conda](https://img.shields.io/conda/v/conda-forge/python?style=flat-square)](https://github.com/python/cpython)
![Conda](https://img.shields.io/conda/dn/conda-forge/python?style=flat-square)

*Python* is an interpreted, high-level, general-purpose language supporting object-oriented programming with more emphasis on code-readibility and extensibility. 

A complete installation guide for Python via the Anaconda/Miniconda Distribution is available in [this link](https://github.com/Sampreet/install-guides/blob/master/languages/python/python-anaconda-miniconda.md).

***Note: ```Python 2.x``` needs to be installed specifically.***

#### GCC and G++

Install ```gcc``` and ```g++``` using the ```apt-get``` by running:

```
sudo apt-get install gcc-4.8 g++-4.8
```

Once installed, update the symbolic links:

```
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.8 50
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.8 50
```

Alternatively, install the development tools by running:

```
sudo apt-get install build-essentials
```

#### Build Tools

Install the build tools and bluetooth development packages by running:

```
sudo apt-get install -y build-essential libbluetooth-dev
```

Change the bluetoothd service configuration file by running:

```
sudo leafpad /lib/systemd/system/bluetooth.service
```

and adding the --compat flag to the ExecStart value:

```
ExecStart=/usr/lib/bluetooth/bluetoothd --compat
```

Repeat the same edit for ```/etc/systemd/system/dbus-org.bluez.service```. Finally, restart the service and change the permissions for SDP by executing the following commands:

```
sudo systemctl daemon-reload
sudo systemctl restart bluetooth
sudo chmod 777 /var/run/sdp
```

#### Bluetooth Serial Port

To install the ```bluetooth-serial-port``` module inside a Node.js application, run:

```
npm install bluetooth-serial-port
```

The modules will be configured and built using ```node-gyp``` available through npm.

## Testing

### On Raspbian

#### Client-side Usage

```javascript
var bluetooth = require('bluetooth-serial-port'),
    btSerial = new bluetooth.BluetoothSerialPort();

btSerial.on('closed', function() {
  console.log('connection closed');
});

btSerial.on('finished', function() {
  console.log('search completed');
});

btSerial.on('found', function (address, name) {
  btSerial.findSerialPortChannel(address, function(channel) {
    btSerial.connect(address, channel, function() {
      console.log('channel connected');
      var buffer = new Buffer ('Hello!', 'utf-8');
      btSerial.write(buffer, function(err, bytesWritten) {
        if (err) 
          console.log(err);
        if(bytesWritten)
          console.log('data written');
        btSerial.close();
      });
    }, function () {
      console.log('could not connect to channel');
    });
  }, function() {
    console.log('could not find channel');
  });
});

// search for devices
btSerial.inquire();
```

#### Server-side Usage

```javascript
var bluetooth = require('bluetooth-serial-port'),
    btServer = new bluetooth.BluetoothSerialPortServer();

const UUID = '00001101-0000-1000-8000-00805F9B34FB',
    CHANNEL=1;

btServer.listen(function(clientAddress) {
    console.log('client: ' + clientAddress + ' connected');
}, function (err) {
    console.log(err);
}, {
    uuid: UUID, 
    channel: CHANNEL
});

btServer.on('data', function (buffer) {
    // received data as buffer
});

btServer.on('closed', function () {
    console.log('connection closed');
});

btServer.on('failure', function (err) {
    console.log('connection failed');
});
```

## Issues and Workarounds

### SDP Connection Error

The error ```Cannot connect to SDP Daemon``` can be solved by changing the permissions to the ```/var/run/sdp``` folder. This can be done on a linux system by running:

```
sudo chmod 777 /var/run/sdp
```