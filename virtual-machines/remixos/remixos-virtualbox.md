# Remix OS on VirtualBox

> A step-by-step guide for installing *Remix OS* as a virtual machine.

## Prerequisites

### Oracle VM VirtualBox

The latest version of *Oracle VM VirtualBox* is available for download at [VirtualBox's website](https://www.virtualbox.org/wiki/Downloads). Install the downloaded file by following the on-screen instructions. *VirtualBox* will be used to create a virtual machine for the installation of *Remix OS*.

### Xubuntu LTS

***Note**: Check the architecture of the current operating system before downloading Xubuntu. For information on how to check the system architecture, visit [this link](https://superuser.com/questions/173788/how-to-find-the-architecture-of-os-installed).*

The latest LTS version of *Xubuntu* is available for download at [Xubuntu's website](https://xubuntu.org/getxubuntu/). Save the downloaded ```.iso``` file in a known location for later use. This file will be used as a live CD of *Xubuntu* for the creation of partitions for the *Remix OS* virtual machine.

***Note**: To aid in the partition creation for the Remix OS virtual machine, any linux-based live CD can be used. Still, a copy of Xubuntu's Xfce desktop environment could come handy at some point of time. If the current operating system supports 64-bit architecture, go for the 64-bit version.*

### Remix OS

***Note**: Check the architecture of the current operating system before downloading Remix OS. For information on how to check the system architecture, visit [this link](https://superuser.com/questions/173788/how-to-find-the-architecture-of-os-installed).*

The latest version of *Remix OS* is available for download at [Jide's website](http://www.jide.com/remixos-for-pc#downloadNow). Download and extract the contents of the downloaded ```.zip``` file. Save the ```.iso```file in a known location for later use. This file will be used to install *Remix OS* inside the virtual machine.

***Note**: To avoid lags while running Remix OS, it is highly recommended to download the 32-bit version.*

## Creating the Virtual Machine

### Step 1: Name and Operating System

Open *VirtualBox*. In the ```Machine``` drop-down menu, select ```New...```. (Alternatively, press ```Ctrl+N```). A dialog appears prompting for the name of the virtual machine and the operating system type of the installation media.

***Note**: If the dialog does not resemble the screenshot displayed below, it means the dialog is running on ```Expert Mode```. Click on the ```Guided Mode``` button at the bottom of the dialog to resolve this conflict.*

Add a suitable name for the operating system in the ```Name``` entry.

Select ```Linux``` in the ```Type``` drop-down menu.

Select ```Other Linux (64-bit)``` or ```Other Linux (32-bit)``` in the ```Version``` drop-down menu depending on the version of Xubuntu downloaded.

The dialog should resemble something like this:

![Name and Operating System](https://github.com/Sampreet/install-guides/raw/master/virtual-machines/remixos/screenshots/remixos-virtualbox-createvm-step-1.PNG "Creating the Virtual Machine: Step 1")

Click ```Next```.

### Step 2: Memory Size

Use the slider or the entry box to select a suitable amount RAM to allocate for the operating system.

***Note**: To avoid lags while running Remix OS, it is highly recommended to set the RAM value above 2048 MB.*

The dialog should resemble something like this:

![Memory Size](https://github.com/Sampreet/install-guides/raw/master/virtual-machines/remixos/screenshots/remixos-virtualbox-createvm-part-2.PNG "Creating the Virtual Machine: Step 2")

Click ```Next```.

### Step 3: Hard Disk

Select the ```Create a virtual hard disk now``` option in the dialog.

![Hard Disk](https://github.com/Sampreet/install-guides/raw/master/virtual-machines/remixos/screenshots/remixos-virtualbox-createvm-part-3-1.PNG "Creating the Virtual Machine: Step 3.1")

Click ```Create```. A new dialog appears for creation of a new virtual hard disk.

Select the ```VDI (VirtualBox Disk Image)``` option.

![Hard Disk File Type](https://github.com/Sampreet/install-guides/raw/master/virtual-machines/remixos/screenshots/remixos-virtualbox-createvm-part-3-2.PNG "Creating the Virtual Machine: Step 3.2")

Click ```Next```. On the storage growth type prompt, select the ```Dynamically allocated``` option.

![Storage on Physical Hard Disk](https://github.com/Sampreet/install-guides/raw/master/virtual-machines/remixos/screenshots/remixos-virtualbox-createvm-part-3-3.PNG "Creating the Virtual Machine: Step 3.3")

Click ```Next```. On the final dialog for the file name and size settings, add a suitable name (preferably the name of the virtual machine) for the virtual hard disk and slide/enter the size of the virtual hard disk.

***Note**: To avoid storage memory problems while running Remix OS, it is highly recommended to set the virtual hard disk size above 8.00 GB.*

![File Location and Size](https://github.com/Sampreet/install-guides/raw/master/virtual-machines/remixos/screenshots/remixos-virtualbox-createvm-part-3-4.PNG "Creating the Virtual Machine: Step 3.4")

Finally, click ```Create```.

The *VirtualBox Manager* will show the details of the created virtual machine beside its name and will resemble something like this:

![Virtual Machine Details](https://github.com/Sampreet/install-guides/raw/master/virtual-machines/remixos/screenshots/remixos-virtualbox-createvm-part-4.PNG "Creating the Virtual Machine: Step 4")

