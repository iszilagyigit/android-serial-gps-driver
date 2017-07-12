Android Serial GPS Driver

How to use:

To set serial port, add a property "ro.kernel.android.gps" and set it equal to your GPS device file.
ie. ro.kernel.android.gps=ttyO1

Default baud rate is 9600, to adjust add a property "ro.kernel.android.gpsttybaud" and set it equal to the needed rate. (4800-115200)
ie. ro.kernel.android.gpsttybaud=9600

To add power management for your target product, `cp power-stubs.c power-$(TARGET_PRODUCT).c` and fill in the stubs.

Notes:
* If using a USB device make sure you have the necessary kernel modules loaded or built in to the kernel.
* Make sure the permissions on your device file are correct

Donate:
If you find any of this useful and want to show appreciation see below:

PayPal: keith.conger@gmail.com
Bitcoin: 1Pg54vVnaLxNsziA6cy9CTefoEG5iAm9Uh


Additional notes:

command line compile for RTAndroid 7.1.1 ARM (RPI 3):

see also:
https://developer.android.com/about/versions/nougat/android-7.0-changes.html


git clone https://github.com/iszilagyigit/platform_hardware_libhardware.git
git clone https://github.com/iszilagyigit/platform_system_core.git


arm-linux-androideabi-gcc 
	-I/opt/dev/android-ndk-tc-arm-api24/sysroot/usr/include
	-I../platform_hardware_libhardware-android-7.1.1_r43/include
	-I../platform_system_core-android-7.1.1_r43/include 
	-L../../gitclones/gps-glonass-android-driver/jni/libs/armeabi
	-llog
	-lcutils
	-lm
	gps.c power-stub.c

Note:  list of all dynamically linked shared libraries of a given .so
example:
 arm-linux-androideabi-readelf -dW /opt/dev/gitclones/gps-glonass-android-driver/jni/libs/armeabi/libcutils.so