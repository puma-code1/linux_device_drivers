
# Device File Creation for Character Drivers

# INTRO:
The device file allows transparent communication between user-space applications and hardware.
They are not normal “files”, but look like files from the program’s point of view: you can read from them, write to them, mmap() onto them,
and so forth. 
When you access such a device “file,” the kernel recognizes the I/O request and passes it to a device driver,
which performs some operations, such as reading data from a serial port or sending data to hardware.

Device files (although inappropriately named, we will continue to use this term) provide a convenient way to access system resources
without requiring the application programmer to know how the underlying device works. Under Linux, as with most Unix systems,
device drivers themselves are part of the kernel.

All device files are stored in /dev directory.


# We can create a device file in two ways.

1- Manually
2- Automatically


1:
mknod -m <permissions> <name> <device type> <major> <minor>
<name> – Your device file name that should have a full path (/dev/name)
<device type> – Put c or b

c – Character Device
b – Block Device

<major> – major number of your driver
<minor> – minor number of your driver
for example:
sudo mknod -m 666 /dev/etx_device c 246 0
if we know the major and minor numbers of the device driver we can manually create device file

2: 

The automatic creation of device files can be handled with udev. Udev is the device manager for the Linux kernel that creates/removes device nodes in the /dev directory dynamically. Just follow the below steps.

Include the header file linux/device.h and linux/kdev_t.h
Create the struct Class
Create Device with the class which is created by the above step
