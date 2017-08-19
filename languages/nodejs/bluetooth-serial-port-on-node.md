# Bluetooth Serial Port on Node.js

> A guide to setting up and installing the *bluetooth-serial-port* module for Node.js

## Installation on Raspbian

### Prerequisites

#### Node.js and NPM

A complete guide for setting up an ssh environment on the Raspberry Pi 3 can be found in [The DaveJ's blog](http://thisdavej.com/beginners-guide-to-installing-node-js-on-a-raspberry-pi/). 

Once SSH has been set up, install Node.js and NPM by following the steps mentioned in [here](https://github.com/Sampreet/install-guides/blob/master/languages/nodejs/nodejs-npm.md). Installation of the LTS version of Node.js, namely, v6.x.x, is recommended.

#### Python 2.x

Python 2.x can be installed using Miniconda package from Continuum Analytics. The installation procedure on Raspbian can be found [here](https://github.com/Sampreet/install-guides/blob/master/languages/python/anaconda-miniconda-python.md).

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

### Configuring Bluetooth

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

### Module Installation

To install the ***bluetooth-serial-port*** module inside a Node.js application, run:

```
npm install bluetooth-serial-port
```

The modules will be configured and built using ```node-gyp``` available through npm.

## Client-side Usage

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

## Server-side Usage

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

## Common Issues and Workarounds

### SDP Connection Error

The error ```Cannot connect to SDP Daemon``` can be solved by changing the permissions to the ```/var/run/sdp``` folder. This can be done on a linux system by running:

```
sudo chmod 777 /var/run/sdp
```