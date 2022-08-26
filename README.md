# **Ubuntu Installation**

- Hard Drive Partition
- Requirements
- Installation


## **Hard Drive Partition**

  1.  In windows 11 search bar type `computer management` and type enter (a window will be opened).
  2.  Select `Disk Management` from `Storage` section.
  3.  Click on the largest partition(In new laptop mostly like C Drive) and click on `shrink volume` (A dialog box will appear)
  4.  Enter **200000** (Four lakh MB = 200GB) in the input with label `Enter the amount of space to shrink in MB`
  5. Click on Shrink (200 GB of empty partition will be created)
  6. Right click on newly created 200GB space 
  7. Select new simple volume
  8. Click next (leave the values as default)
  9. Click next (remember the value in drop down, most likely **E** drive)
  10. Click next
  11. Click Finish

## **Requirements**

  - Pendrive with minimum 8 GB memory.
(preferably empty pendrive, Data will be erased in pendrive while making bootable USB)

  - Ubuntu ISO File (click this link to download)
[ubuntu-22.04.1-desktop-amd64.iso](https://releases.ubuntu.com/22.04/ubuntu-22.04.1-desktop-amd64.iso)

  - Rufus (click this link to download) [download rufus](https://github.com/pbatard/rufus/releases/download/v3.20/rufus-3.20.exe)

## **Installation**
### **Burning OS into USB/ Creating bootable USB** 
0. Install the Rufus and attach the USB to laptop
1. Select the USB drive attached to our system that you want to use.
2. Choose the downloaded ISO file of Jammy JellyFish.
3. After that simply click on the Start button. For more clear idea see the below screenshot.
![](rufus.png)
4. Wait until it the process completes.(takes upto 15 mins)

### **Booting the OS**

restart the device and click `ESC` during several times startup and selecting the USB device from the system-specific boot menu.

press **F10** to go to `BIOS`

Go to `system configuration` section (use arrow keys)

Set the `Intel Rapid Start Technology` is **Disabled** (use arrow key and enter key to change the option)

Go to `boot` section (use arrow keys)
Set the `USB Boot` **Enabled**

save the changes (You will find a key to save the changes in bottom/side menu)

The computer will start booting,Now press ESC for 6-10 times.
(Alternative: restart the computer and press ESC for 6-10 times if you missed the above step)

select **F9** to go to `Boot Menu`

Use arrow key to select USB

Now, You will see a window with two options
1. Try Ubuntu
2. Install Ubuntu

### Select `Install Ubuntu`

### **Language selection**

Select English as default language(English is pre-selected), click next.

### **Updates and other software section**

select normal installation 
select download updates while installing ubuntu(in Other Options)
select Install third party software for graphics and wifi hardware

### **Installation type**

select `something else` option

you will see the internal disk of 512 GB at bottom
![](disk.png)

(like 480.1 GB in the picture)

scroll the list until you find largest free space about 200 GB and click on it.(as in below pic)
_**Do not modify any other partitions**_
![](disk1.png)

click on the plus button(Just above device for boot loader installation)

from the 200 GB of free space create a partition
allocate 85 GB to root
  - Give Size as 85000 
  - Use as Ext4 journaling file system
  - Mount point as **/** (as in pic below pic)
  - Click OK
- a new partition for root will be created (Now the free space will be decreased by 85 GB, nearly 115 GB will be remaining)
![](disk2.png)

from the 115 GB of free space create another partition
allocate 100 GB to home
  - Give Size as 100000 
  - Use as Ext4 journaling file system
  - Mount point as **/home** (as in pic below pic)
  - Click OK
  - a new partition for home will created
![](disk3.png)

from the 15 GB of free space create last partition
allocate 15 GB to Swap
  - Give Size as 15000 
  - Use as swap area
  - Click OK
  - a new partition for swap will created 
![](disk3.png)

click **Install Now** button
click `continue` in the dialog box

### **Time zone**

select Kolkata as timezone place

### **Create User Account**

fill the form and remember the password(minimum of 8 letters word is preferred)

click `continue`

The installation will begin and it may take 15 to 20 minutes

After installation click `restart now` (Make sure to remove the bootable pendrive before restarting)

## Installing Java

paste the command to update and upgrade the system

    sudo apt update -y && sudo apt upgrade -y

[Download Java 17](https://download.oracle.com/java/17/latest/jdk-17_linux-x64_bin.deb)

After Downloading open the terminal using pressing `Ctrl+Alt+T` altogether

type the command to navigate to **Downloads** directory

    cd Downloads

you will see the
 **jdk-17_linux-x64_bin.deb** file

type the command to install this package

    sudo dpkg -i jdk-17_linux-x64_bin.deb
(Use the same password, the one we used in user account setup)

<!-- `sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-17/bin/java 1`

`sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk-17/bin/javac 1` -->

open new terminal using `Ctrl+Alt+T`  and type the command to verify installation

    java -version

output should be similar to the below

` java version "17.0.1" 2021-10-19 LTS
 Java(TM) SE Runtime Environment (build 17.0.1+12-LTS-39)
 Java HotSpot(TM) 64-Bit Server VM (build 17.0.1+12-LTS-39, mixed mode, sharing)`

## setting path for java

type the following command
    
    ls /usr/lib/jvm/

You will get output similar to

`jdk-17.0.1` (might not be exact in our case)

copy this output

    sudo gedit /etc/profile

 to edit the file with super user privilages

type the following text

**JAVA_HOME=/usr/lib/jvm/(paste the above output)** with no spaces

Save and exit from the file

update the paths using the below command

    source /etc/profile

verify the change using the below command

    echo $JAVA_HOME

the output will be

`JAVA_HOME=/usr/lib/jvm/(the text we pasted)`


## Installing Android Studio

install snap using the below command

    sudo apt install snapd

install android studio with snap using below command

    sudo snap install android-studio --classic

after installation

click `windows key` and type `android studio`, you will android studio application and click on it, it will open

a pop will appear for very first time after installing android studio asking **import settings**

let it be default(do not import) and click **OK**

Now you will see another pop up called **Data Sharing** click on `Don't Send`

Now you will see the window showing different logos (phones, watches, TVs, etc)

let it be default(standard), click on next
select dark theme(dracula), click on next

Now you will see Verify settings, click on next
At last you will see finish, click on finish.

## Installing Node.js (version 16)

install curl using below commad

    sudo apt install curl

execute the below command to set the nodejs version to 16

    sudo curl -fsSL https://deb.nodesource.com/setup_16.x | sudo bash -

install the node.js using the below command

    sudo apt install -y nodejs

verify whether it is installed

    node -v

output should be similar to 

`v16.16.0`
