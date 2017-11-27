Copyright (c) 2017 The Linx Partnership

Distributed under the MIT/X11 software license, see the accompanying
file COPYING or http://www.opensource.org/licenses/mit-license.php.
This product includes software developed by the OpenSSL Project for use in the [OpenSSL Toolkit](http://www.openssl.org/). This product includes
cryptographic software written by Eric Young ([eay@cryptsoft.com](mailto:eay@cryptsoft.com)), and UPnP software written by Thomas Bernard.

RASPBERRY PI BUILD INSTRUCTIONS
===============================

Linx can be built and run on a Raspberry Pi v3.
A v2 Pi will run Linx just fine but may fail during the build due to the heavy
processor load.

It can be built on various distributions but by far the easiest, and the one
covered here is Ubuntu MATE.

What you'll need...

A Raspberry Pi Model 3 (https://www.raspberrypi.org/)
A Class 10 Micro SD card (At least 16GB)
A power adaptor for the Pi (You can run it from USB but it's not recommended)

1) Download Ubuntu MATE here
https://ubuntu-mate.org/raspberry-pi/ubuntu-mate-16.04.2-desktop-armhf-raspberry-pi.img.xz

2) Unarchive it

3) Burn the resulting .img file to a Micro SD card

4) Put the SD card in your Pi

5) Go through the on on screen setup, including setting up your wi-fi details if
you are not using a wired connection. Once complete we can get going.

We will be building in CLI mode as the build will likely freeze up due to the
processor intensive routines if the desktop GUI is also running.

6) Open a terminal and fire up raspi-config


`$ sudo raspi-config`

a) Select "Boot Options" from the menu.

b) Select "B1 Desktop / CLI"

c) Select "B1 Console Text Console"

Then choose "Finish" and when asked to reboot now select "Yes"

The Pi will reboot to the console where you will be prompted for your username
and password.

7) Install the dependencies


`$ sudo apt-get -y install build-essential libboost-dev libboost-system-dev libboost-filesystem-dev libboost-program-options-dev libboost-thread-dev libssl-dev`

`$ sudo apt-get -y install libtool autotools-dev autoconf`

`$ sudo apt-get -y install libboost-all-dev`

`$ sudo apt-get -y install libminiupnpc-dev`

`$ sudo apt-get -y install libdb++-dev`

We have to use an old version of BerkeleyDB (4.8) and it won't be available from
the current dist repo. You can build this yourself from source if you wish, full
instructions are located in build-unix.md, but to save time you can just add the
Bitcoin repo and install it directly.


`$ sudo apt-get install software-properties-common`

`$ sudo add-apt-repository ppa:bitcoin/bitcoin`

`$ sudo apt-get update`

`$ sudo apt-get install libdb4.8-dev libdb4.8++-dev`

8) Install git if you don't already have it

`$ sudo apt-get install git`

9) Clone Linx from our repo to your machine

`$ git clone https://github.com/linx-project/linX.git`

10) Build Linx

`$ cd linX/src`

`$ make -f makefile.unix`

The build process will take a very long time so grab a coffee or two.
When you get back, if all has gone well you are ready to launch Linx.

`$ ./linXd -daemon`

You will see a notice about setting your RPC username and password in the
config file.

11) Create and set up the config file

`$ cd`

`$ cd ./linX`

`$ sudo nano linX.config`

Paste in the following, changing the username and password to something secure
and save it.


```
rpcuser=YourUserName
rpcpassword=YourVeryStrongPassword
rpcport=12924
port=13925
addnode=seed.mylinx.io
addnode=testnet.mylinx.io
```

12) Fire up Linx on the mainnet and grab another coffee (or maybe even a beer,
you deserve it) while the blockchain syncs. This is going to take a while.

`$ cd`

`$ cd linX/src`

`$ ./linXd -daemon`

`$ ./linXd getinfo`

If you want to launch Linx on the testnet run

`$ ./linXd - testnet`

`$ ./linXd getinfo`

Enjoy!
