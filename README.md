##Setting up an Ubuntu 14.04 Server in VirtualBox.

The end result of these instructions will be a base VirtualBox Ubuntu 14.04 Server virtual machine that can act as a template for building clusters on VirtualBox. 

###Instructions
1. Install VirtualBox
2. Download [Ubuntu 14.04 Server](http://www.ubuntu.com/download/server/thank-you?country=US&version=14.04.2&architecture=amd64). (I haven't tried the 32 bit architecture with Hadoop or Spark).
3. Open VirtualBox:
  1. Click *New*
    1. Name the VM *ClusterBase*.
    2. Select Linux and the architecture that you downloaded in step 2.
    3. Give the VM a decent amount of memory. Remember, however, that you will be running multiple instances. On my machine with 4G of RAM, I allocated 1G.
    4. Select the defaults until done.
  2. Create a Host-Only Network:
    1. Under *File*
    2. Select *Preferences.*
      1. Select *Network*
        1. Select *Host-Only Networks*
          1. Click the *+* icon.
          2. Click OK
  3. Configure the VM
    1. Click *Settings*
    2. Under *System*, deselect *Floppy Disk*.
    3. Under *Storage*
      1. Click the CD icon
      2. Under Attributes, click that CD icon
      3. Choose the *Ubuntu* *.iso* file downloaded in step 2.
    3. Click *Network*
      1. Under *Adapter 1*
        1. Make Sure 'Enable Network Adapter' is selected.
        2. Under attached to, choose *Host-only Adapter*
        3. Under name, choose the Adapter created in step 2. (Probably named vboxnet0.)
      2. Under *Adapter 2*
        1. Make Sure 'Enable Network Adapter' is selected.
        2. Under attached to, choose *NAT*
      3. Click OK
  3. Start the VirtualMachine.
4. In the new Virtual Machine
  1. Choose Install
  2. 'Enter' through the defaults until you get to *Configure the Network.*
    1. Select *eth1*
  3. Name the server *cluster*.
  5. Set username to *cluster* and pick a password.
  6. 'Enter' through the defaults until you reach *Partition disks*. (The screen may go blank for a while during one stage.)
    1. Select *Guided - entire disk*.
    2. Press 'Enter'.
    3. Select *'Yes'*.
  7. 'Enter' through the defaults until the *Software Selection* menu, then select
    1. OpenSSH Server
    2. 'Continue'
  8. 'Enter' through the defaults.
  9. *Reboot* the machine when prompted to so do.

5. Log in and run:
  1. `sudo apt-get update; sudo apt-get upgrade -y;`
  1. `sudo apt-get install -y git openjdk-7-jdk;`
  8. `sudo halt -p;` 

## This VirtualMachine should be left in this state.#
It should be used only as a template for creating other VMs. 

