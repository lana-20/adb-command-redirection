# <img src="https://user-images.githubusercontent.com/70295997/222836016-f4e626f9-6824-42cf-9cf2-2c771b896864.png" width=40> If you have several Android devices (virtual emulators and/or physical phones) connected to your machine, how do you install an application?

If you have multiple devices available but only one is an emulator, use the <code>-e</code> option to send commands to the emulator. If there are multiple devices but only one hardware device attached, use the <code>-d</code> option to send commands to the hardware device.

There is a difference in ADB commands used for installing mobile apps on Android devices vs emulators. In command <code>adb [-d |-e | -s serial_number] install <path_to_apk_file></code> the options in <code>[]</code> are the differentiators:
* <code>-d</code> is for device
* <code>-e</code> is for emulator
    - Use the <code>-e</code> option for a physical device, if it's connected to your computer via **WiFi** and not via the USB cable. Point the command to the UDP/TCP port (used by emulators) in lieu of the USB port. 
 
* <code>-s</code> is for serial number for either physical or virtual device.
   
For example:

      adb -s emulator-5554 install helloWorld.apk
      adb -s A6PVD6LNFQ578HUS install ~/apk_files/helloWorld.apk

To install an app on either an Android or a physical device using ADB, I use command <code>adb install <path_to_apk_file></code>.  Command <code>adb install app.apk</code> will install the app on a single connected device, whether it's virtual or physical. If more than one device is running, I get the following error:

      adb: error: failed to get feature set: more than one device/emulator

Overall the process of installing apps on Android emulators or physical devices using ADB is similar. But there are some differences to consider:

* **Emulators**: Need to create and configure the emulators in a development environment like Android Studio. This involves setting up the emulator’s hardware and software configurations and launching the emulator.
* **Physical Devices**: Need to connect the devices to your machine using USB cables. Make sure that USB debugging is enabled on the devices.
