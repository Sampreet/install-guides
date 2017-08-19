# Remix OS on VirtualBox

> A complete step-by-step guide for installing *Remix OS* in a virtual machine.

## About

The guide provides an elaborated process for installation of *Remix OS* inside a *VirtualBox* virtual machine and the level of description is set to beginner level. Advanced users can skip some of the contents of the guide and extract only the relevant details out of the same.

## Table of Contents

* [Prerequisites](#prerequisites)
  * [Oracle VM VirtualBox](#virtualbox)
  * [Xubuntu LTS](#xubuntu)
  * [Remix OS](#remix)
* [Creating a Virtual Machine](#createvm)
  * [Step 1: Name and Operating System](#createvm-step-1)
  * [Step 2: Memory Size](#createvm-step-2)
  * [Step 3: Hard Disk](#createvm-step-3)
* [Pratitioning the Virtual Hard Disk](#partition)
  * [Step 1: Virtual Optical Disk Drive](#partition-step-1)
  * [Step 2: Xubuntu Live CD](#partition-step-2)
  * [Step 3: GParted](#partition-step-3)
  * [Step 4: Partition](#partition-step-4)
  * [Step 5: Reboot](#partition-step-5)
* [Installing the Operating System](#installos)
  * [Step 1: Installation](#installos-step-1)
  * [Step 2: GRUB Configuration](#installos-step-2)
  * [Step 3: Remix OS Setup](#installos-step-3)

<a name="prerequisites"/>

## Prerequisites

<a name="virtualbox"/>

### Oracle VM VirtualBox

The latest version of *Oracle VM VirtualBox* is available for download at [VirtualBox's website](https://www.virtualbox.org/wiki/Downloads). Install the downloaded file by following the on-screen instructions. *VirtualBox* will be used to create a virtual machine for the installation of *Remix OS*.

<a name="xubuntu"/>

### Xubuntu LTS

***Note**: Check the architecture of the current operating system before downloading Xubuntu. For information on how to check the system architecture, visit [this link](https://superuser.com/questions/173788/how-to-find-the-architecture-of-os-installed).*

The latest LTS version of *Xubuntu* is available for download at [Xubuntu's website](https://xubuntu.org/getxubuntu/). Save the downloaded ```.iso``` file in a known location for later use. This file will be used as a live CD of *Xubuntu* for the creation of partitions for the *Remix OS* virtual machine.

***Note**: To aid in the partition creation for the Remix OS virtual machine, any linux-based live CD can be used. Still, a copy of Xubuntu's Xfce desktop environment could come handy at some point of time. If the current operating system supports 64-bit architecture, go for the 64-bit version.*

<a name="remix"/>

### Remix OS

***Note**: Check the architecture of the current operating system before downloading Remix OS. For information on how to check the system architecture, visit [this link](https://superuser.com/questions/173788/how-to-find-the-architecture-of-os-installed).*

The latest version of *Remix OS* is available for download at [Jide's website](http://www.jide.com/remixos-for-pc#downloadNow). Download and extract the contents of the downloaded ```.zip``` file. Save the ```.iso```file in a known location for later use. This file will be used to install *Remix OS* inside the virtual machine.

***Note**: To avoid lags while running Remix OS, it is highly recommended to download the 32-bit version.*

<a name="createvm"/>

## Creating the Virtual Machine

<a name="createvm-step-1"/>

### Step 1: Name and Operating System

Open *VirtualBox*. In the ```Machine``` menu, select ```New...```. (Alternatively, press ```Ctrl+N```). A dialog appears prompting for the name of the virtual machine and the operating system type of the installation media.

***Note**: If the dialog does not resemble the screenshot displayed below, it means the dialog is running on ```Expert Mode```. Click on the ```Guided Mode``` button at the bottom of the dialog to resolve this conflict.*

Add a suitable name for the operating system in the ```Name``` entry.

Select ```Linux``` in the ```Type``` drop-down menu.

Select ```Other Linux (64-bit)``` or ```Other Linux (32-bit)``` in the ```Version``` drop-down menu depending on the version of Xubuntu downloaded.

The dialog should resemble something like this:

![Name and Operating System](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-createvm-step-1.PNG "Creating the Virtual Machine: Step 1")

Click ```Next```.

<a name="createvm-step-2"/>

### Step 2: Memory Size

Use the slider or the entry box to select a suitable amount RAM to allocate for the operating system.

***Note**: To avoid lags while running Remix OS, it is highly recommended to set the RAM value above 2048 MB.*

The dialog should resemble something like this:

![Memory Size](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-createvm-step-2.PNG "Creating the Virtual Machine: Step 2")

Click ```Next```.

<a name="createvm-step-3"/>

### Step 3: Hard Disk

Select the ```Create a virtual hard disk now``` option in the dialog.

![Hard Disk](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-createvm-step-3-1.PNG "Creating the Virtual Machine: Step 3.1")

Click ```Create```. A new dialog appears for creation of a new virtual hard disk.

Select the ```VDI (VirtualBox Disk Image)``` option.

![Hard Disk File Type](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-createvm-step-3-2.PNG "Creating the Virtual Machine: Step 3.2")

Click ```Next```. On the storage growth type prompt, select the ```Dynamically allocated``` option.

![Storage on Physical Hard Disk](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-createvm-step-3-3.PNG "Creating the Virtual Machine: Step 3.3")

Click ```Next```. On the final dialog for the file name and size settings, add a suitable name (preferably the name of the virtual machine) for the virtual hard disk and slide/enter the size of the virtual hard disk.

***Note**: To avoid storage memory problems while running Remix OS, it is highly recommended to set the virtual hard disk size above 8.00 GB.*

![File Location and Size](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-createvm-step-3-4.PNG "Creating the Virtual Machine: Step 3.4")

Finally, click ```Create```.

The *VirtualBox Manager* will show the details of the created virtual machine beside its name and will resemble something like this:

![Virtual Machine Details](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-createvm-step-4.PNG "Creating the Virtual Machine: Step 4")

<a name="partition"/>

## Partitioning the Virtual Hard Disk

<a name="partition-step-1"/>

### Step 1: Virtual Optical Disk Drive

Inside the *VirtualBox Manager*, select the virtual machine and click on ```Start``` through the ```Machine``` menu or the toolbar. The virtual machine will start on a new window and will prompt for a start-up disk. Browse and select the Xubuntu's ```.iso``` file downloaded earlier.

![Virtual Optical Disk Drive](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-partition-step-1.PNG "Partitioning the Virtual Hard Disk: Step 1")

Click ```Start```.

<a name="partition-step-2"/>

### Step 2: Xubuntu Live CD

Wait till *Xubuntu* boots from the virtual optical disk drive. Once complete, a screen similar to the one below will appear.

![Xubuntu Live CD](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-partition-step-2.PNG "Partitioning the Virtual Hard Disk: Step 2")

Click ```Try Xubuntu```.

<a name="partition-step-3"/>

### Step 3: GParted

After *Xubuntu Live CD* has completed booting into the home screen, click on the ```Whisker Menu``` icon at the top left of the home screen to show the applications menu.

![Applications](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-partition-step-3-1.PNG "Partitioning the Virtual Hard Disk: Step 3.1")

Click on ```Terminal Emulator```. The *Terminal* window pops up. Enter the following command:

```
sudo gparted
```

![Terminal Emulator](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-partition-step-3-2.PNG "Partitioning the Virtual Hard Disk: Step 3.2")

Press ```Enter```. 

<a name="partition-step-4"/>

### Step 4: Partition

The *GParted* application window appears displaying the unallocated volume on the virtual hard disk.

![Unallocated Volume](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-partition-step-4-1.PNG "Partitioning the Virtual Hard Disk: Step 4.1")

On the ```Device``` menu, Select ```Create Partition Table...```. A warning dialog appears prompting the partition type. Select ```msdos```.

![Partition Table Type](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-partition-step-4-2.PNG "Partitioning the Virtual Hard Disk: Step 4.2")

Click ```Apply```. 

From the ```Partition``` menu, select ```New```. In the ```Create new Partition``` dialog, update the following properties:

```
File system:  ext4
Label:        RemixOS
```

Verify that the dialog rembles the following image.

![Create Partition](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-partition-step-4-3.PNG "Partitioning the Virtual Hard Disk: Step 4.3")

Click ```Add``` button. 

In the ```Edit``` menu, select ```Apply All Operations```. A prompt will appear to asking the user to confirm the editing done.

![Apply Operations](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-partition-step-4-4.PNG "Partitioning the Virtual Hard Disk: Step 4.4")

Click ```Apply```.

Wait for the operations to complete. On completion, a dialog appears which is similar to this:

![Operations Completed](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-partition-step-4-5.PNG "Partitioning the Virtual Hard Disk: Step 4.5")

Click ```Close```. 

The virtual hard disk is now partitioned with the format described in the window and is ready for installation of *Remix OS*.

![Partition Table](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-partition-step-4-6.PNG "Partitioning the Virtual Hard Disk: Step 4.6")

<a name="partition-step-5"/>

### Step 5: Reboot

On the *Xubuntu* home screen, click on the ```Wisker Menu``` icon on the top left and select ```Log Out``` at the right bottom of the application menu.

![Logout](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-partition-step-5-1.PNG "Partitioning the Virtual Hard Disk: Step 5.1")

The *Log out Live session* dialog appears. Uncheck the ```Save session for future logins``` option.

![Shut Down](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-partition-step-5-2.PNG "Partitioning the Virtual Hard Disk: Step 5.2")

Click the ```Shut Down``` button.

After shutdown, go to the ```Devices``` menu, select ```Optical Drives```, and then click ```Choose disk image...```. 

![Choose Disk Image](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-partition-step-5-3.PNG "Partitioning the Virtual Hard Disk: Step 5.3")

Browse for and load the downloaded *Remix OS* ```.iso``` file. 

On the ```Machine``` menu, select ```Reset```. A prompt might appear to confirm the same.

![Reset](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-partition-step-5-4.PNG "Partitioning the Virtual Hard Disk: Step 5.4")

Click ```Reset```.

<a name="installos"/>

## Installing the Operating System

<a name="installos-step-1"/>

### Step 1: Installation

Wait until the *Remix OS* boots to the install mode selection page. Press ```Arrow Down``` key before it auto-selects the default option. Select the ```Resident mode``` option and press ```Tab``` for extra options. Add the following option after the ```CREATE_DATA_IMG=1``` with a space in between:

```
INSTALL=1
```

The resultant should look something like this:

![Select Mode](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-1-1.PNG "Installing the Operating System: Step 1.1")

Press ```Enter```. Select the partition that was created in the previous step.

![Select Partition](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-1-2.PNG "Installing the Operating System: Step 1.2")

Select ```OK``` and press ```Enter```. On the next screen, select the ```Do not format``` option.

![Format Filesystem](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-1-3.PNG "Installing the Operating System: Step 1.3")

Select ```OK``` and press ```Enter```. Skip the prompts for installation of GRUB if they appear.

![Skip GRUB installation](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-1-4.PNG "Installing the Operating System: Step 1.4")

Select ```Yes``` when asked whether to install /system directory as read-write.

![Read-Write Permission](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-1-5.PNG "Installing the Operating System: Step 1.5")

After opting ```Yes```, wait for the system to install in the virtual hard disk. The progress will be shown on the screen. Upon completion of installation, the following dialog appears:

![Installed successfully](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-1-6.PNG "Installing the Operating System: Step 1.6")

Select ```Reboot``` and then ```OK```. When the mode selection page appears, stop the auto-selection process by pressing the ```Arrow Down``` key. On the ```Devices``` menu, select ```Optical Drives``` and then select the *Xubuntu* ```.iso``` file from the list of recently used disk images.

![Select Disk Image](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-1-7.PNG "Installing the Operating System: Step 1.7")

If a dialog appears saying ```Unable to insert the virtual optical disk...```, click on ```Force Unmount```. Go to the ```Machine``` menu and select ```Reset```. Confirm the reboot by clicking on the ```Reset``` button on the dialog that appears.

![Reboot to Xubuntu](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-1-8.PNG "Installing the Operating System: Step 1.8")

<a name="installos-step-2"/>

### Step 2: GRUB Configuration

Boot into the *Xubuntu Live CD* and open the *Terminal Emulator* by following the [Step 2](#partition-step-2) and [Step 3](#partition-step-3) of the section, [Partitioning the Virtual Hard Disk](#partition). Once the *Terminal* window appears, enter the following commands one after the other in the given order:

```
sudo grub-install --root-directory=/media/xubuntu/RemixOS /dev/sda
cd /media/xubuntu/RemixOS/boot/grub/
sudo touch grub.cfg
sudo mousepad grub.cfg
```

The terminal screen should resemble something like this:

![Terminal GRUB Install](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-2-1.PNG "Installing the Operating System: Step 2.1")

Inside Mousepad, add the following lines to the file grub.cfg:

```
set default=0 
set timeout=10
set gfxmode=800x600
terminal_output gfxterm

menuentry 'Remix OS' --class android-x86 {
        search --file --no-floppy --set=root /RemixOS/kernel
        linux /RemixOS/kernel root=/dev/sda1 androidboot.hardware=remix_x86 androidboot.selinux=permissive SERIAL=random DATA=/data
        initrd /RemixOS/initrd.img
}
```

***Note**: If the downloaded Remix OS was a 64-bit ```.iso```, replace ```androidboot.hardware=remix_x86``` by ```androidboot.hardware=remix_x86_64```.*

![Mousepad GRUB Configuration](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-2-2.PNG "Installing the Operating System: Step 2.2")

Log out of the live session following the first two sections of [Step 5](#partition-step-5) of the section, [Partitioning the Virtual Hard Disk](#partition). However, instead of selecting an ```.iso``` image for virtual optical drive, opt for ```Remove disk from virtual drive```. Restart the system using the ```Reset``` option from the ```Machine``` menu. Confirm the reboot by clicking on the ```Reset``` button of the prompt. 

<a name="installos-step-3"/>

### Step 3: Remix OS Setup

The *GNU GRUB* appears displaying the entry ```Remix OS```. Press ```Enter``` to start the operating system.

![GNU GRUB](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-3-1.PNG "Installing the Operating System: Step 3.1")

The *Remix OS* logo flashes for some time till the system prepares itself for setup and first use. This might take some time.

![Remix OS Logo](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-3-2.PNG "Installing the Operating System: Step 3.2")

After the initialization, the setup displays the language selection window.

![Select Language](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-3-3.PNG "Installing the Operating System: Step 3.3")

Select ```English (United States)``` (or whichever is your preferred language). The *User Agreement* screen appears.

![User Agreement](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-3-4.PNG "Installing the Operating System: Step 3.4")

Click on ```Agree```. Skip the Wi-Fi setup using the ```Skip``` button at the top right corner of the screen.

![Wi-Fi setup](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-3-5.PNG "Installing the Operating System: Step 3.5")

Click ```Continue on the *Discover Apps* advertisement.

![Discover Apps](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-3-6.PNG "Installing the Operating System: Step 3.6")

Select the required applications in the subsequent *Popular Apps*, *Useful Apps* and *Entertainment Apps* screens, navigating via the ```Next``` buttons at the bottom right corner of the pages.

![Popular Apps](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-3-7.PNG "Installing the Operating System: Step 3.7")

![Useful Apps](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-3-8.PNG "Installing the Operating System: Step 3.8")

![Entertainment Apps](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-3-9.PNG "Installing the Operating System: Step 3.9")

Verify the selected apps in the *Summary* page and click on ```Install```.

![Install Summary](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-3-10.PNG "Installing the Operating System: Step 3.10")

Click ```Finish``` on the next page.

![All Done](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-3-11.PNG "Installing the Operating System: Step 3.11")

If prompted for *Google Play* activation, uncheck the ```I would like to activate Google Play services.``` option and click on ```Next```.

![Activate Google Play](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-3-12.PNG "Installing the Operating System: Step 3.12")

And finally, the home screen of *Remix OS* appears...

![Home Screen](https://raw.githubusercontent.com/Sampreet/install-guides/master/virtual-machines/remixos/screenshots/remixos-virtualbox-installos-step-3-13.PNG "Installing the Operating System: Step 3.13")

Enjoy exploring Remix OS!
