LinX v0.9.0.2
================================

http://www.mylinx.io

Copyright (c) 2009-2014 Bitcoin Developers

Copyright (c) 2017 LinX Foundation

What is LinX?
----------------

LinX is an experimental crypto currency that uses scrypt as a proof-of-work algorithm.

 - 1 minute block targets
 - subsidy reduces in stages depending on current coin supply (50,25,10,5,1,0)
 - 100,000,000 total coins
 - Retargets every block using Dark Gravity Wave 3


Build Instructions
------------------

```
cd linX
qmake
make
```

See [docs](https://github.com/linX-project/linX/tree/master/doc) for flags, deps and more info.


Compiled Binaries Instructions
------------------------------

Precompiled Windows and Nix binaries available at https://mylinx.io

See instructions below.


Windows Setup
--------------------

- Double click the setup.exe file to install automatically

- Alternatively run **linX-qt.exe** or **linXd.exe** without using the installer

If the wallet doesn't automatically start syncing you will need to create a 
.conf file.

1) Close the Wallet / Daemon

2) Create a new text file

3) Inside paste the following (*changing the user and password*) :

```
rpcuser=ChooseAUserName
rpcpassword=ChooseAStrongRandomPassword
addnode=193.70.113.19
addnode=51.255.43.51
addnode=217.182.68.186
```

4) Save the file as **linX.conf**

5) Place it inside the following DIR :

```
/Users/<username>/AppData/Roaming/linX
```

6) Restart Wallet / Daemon


Nix Setup
--------------------

1) Navigate to the folder where linXd is and run it :

```
./linXd -daemon
```

LinX server will start and then stop saying it needs a missing config file.

In the folder you downloaded will find a file called **linX.conf.example.txt**

Open it and put your user and password in the correct places then save the file as **linX.conf**

Put this file in the following folder : 

```
.linX
```
          
It's a hidden folder click ctrl + H to display hidden folders if you can't see it.


linX-qt (The GUI Wallet)
------------------------

This is NOT a static build. It requires external libraries for it to work. If you have built other wallets on your computer before, the chances are that you will already have all of the required libraries. If not see the build [docs](https://github.com/linX-project/linX/tree/master/doc).


For more information, as well as pre-compiled versions of the latest LinX client sofware visit http://www.mylinx.io

Official LinX Mining pool : http://pool.mylinx.io

LinX Block Explorer : http://explorer.mylinx.io


License
-------------------

Developers work in their own trees, then submit pull requests when they think their feature or bug fix is ready.

If it is a simple/trivial/non-controversial change, then one of the linX development team members simply pulls it.

If it is a *more complicated or potentially controversial* change, then the patch submitter will be asked to start a discussion with the devs and community.

The patch will be accepted if there is broad consensus that it is a good thing.
Developers should expect to rework and resubmit patches if the code doesn't match the project's coding conventions (see `doc/coding.txt`) or are controversial.

The `master` branch is regularly built and tested, but is not guaranteed to be completely stable. [Tags](https://github.com/linX-project/linX/tags) are created regularly to indicate new official, stable release versions of linX.


Disclaimer
-------------------

LinX is an entirely experimental project and we offer no warranties or guarantees.
Use entirely at your own risk.

