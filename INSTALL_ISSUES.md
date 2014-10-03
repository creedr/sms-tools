# Installation Issues
For getting software installed and running properly for the Coursera Class **Audio Signal Processing for Music Applications by Prof Xavier Serra, Prof Julius O Smith, III**

## System
Linux Mint 13 
amd64 architecture

## Python Distribution
[Anaconda 2.1](https://store.continuum.io/cshop/anaconda/)

## Issues
1. sms-tools has problem with importing pygame -- seems to be problem with Anaconda
2. SonicVisualiser 2.4.x has several dependency issues that I couldn't resolve

To fix the **pygame** problem:
============================

Download the **pygame-1.9.1release.tar.gz** file from [pygame.org](http://www.pygame.org/download.shtml)

From the terminal change to the Downloads directory.
Let's move this .tar.gz to your Anaconda directory with the commands
	mv pygame-1.9.1release.tar.gz ~/anaconda/pkgs

Now navigating to the **~/anaconda/pkgs** directory, extract the contents of the archive with the command
	tar -zxvf pygame-1.9.1release.tar.gz

Now 
	cd pygame-1.9.1release.tar.gz

and build the package by running
	python setup.py build

Once this gets done running, then you can run python and try **import pygame**.  This may result in an error similar to
	ImportError: /home/username/anaconda/bin/../lib/libm.so.6: version `GLIBC_2.15' not found (required by /usr/lib/x86_64-linux-gnu/libpulse.so.0)

To fix this import error, 
	cd ../lib

Now we will create a backup of the **libm.so.6** file and delete the old one with the command
	mv libm.so.6 libm_backup.so.6

This should resolve the import error, so try running python again and **import pygame**.  If you get no error, then you're good to go.  If you get another error, then try backing up and deleting the old **~/anaconda/include/math.h** file with the command
	mv ../include/math.h ../include/math_backup.h

and then recompile pygame by navigating to the appropriate directory and running
	python setup.py build

Hopefully this will resolve any pygame import errors with the Anaconda distribution and you will be good to go.



To fix the SonicVisualiser 2.4.x install problem:
===========================================

As of 10/02/2014 for the computer arcitecture and system mentioned above, the easiest workaround to this problem was to install an earlier version of SonicVisualiser.

Navigate to your downloads folder:
	cd ~/Downloads
	
and run the following commands:
	wget -c code.soundsoftware.ac.uk/attachments/download/908/sonic-visualiser_2.3cc-1_amd64.deb
	sudo dpkg -i sonic-visualiser_2.3cc-1_amd64.deb
	sudo apt-get install -f

This installs SonicVisualiser 2.3 on the amd64 architecture.  Make sure your machine has the amd64 architecture or else this download may not install on your machine.  You may need to search for the link for a different architecture such as i386, etc.  
