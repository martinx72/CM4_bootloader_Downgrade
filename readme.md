
You should just downgarde the bootloader of your Raspberry CM4 if you cannot boot from SD card. \
As newer bootloader somehow won't be able to detect the SD card. \
The **2021 Feb 16 verson (1613481816)** of bootloader is the best option during the test.

## You can do it just with **RGR's board** with **a USB thumb drive**

 - Step **1**, Use your computer to burn the latest version of retropie imag (the version supports CM4) to a USB thumb drive. \
 ( https://retropie.org.uk/download/, the Pi4/Pi400 version ) \
 You have to enable the **SSH access** and wifi setting(if your CM4 came with wifi hardware) via the buring tool "Raspberry Pi Imager". \
 ( Check this article: https://www.seeedstudio.com/blog/2021/01/25/three-methods-to-configure-raspberry-pi-wifi/ ). \
 \
 If your CM4 has no wifi built-in, I would suggest that you get a USB ethernet dongle to access your CM4 via network otherwise you can use USB keyboard to direct control the Linux system.
  - Step **2**, Copy the pre-configured bootloader **pieeprom-1613481816.bin** from current repo in the root folder of the USB thumb drive. And, modify the config.txt file to make sure your USB is enabled on CM4. Add this at the end of **config.txt**
>dtoverlay=dwc2,dr_mode=host
  - Step **3**, it is about time to boot the CM4, you can use **ssh** to access teh CM4 or just USB keyboard. And type this command to downgarde the bootloader of CM4
>sudo rpi-update
>sudo CM4_ENABLE_RPI_EEPROM_UPDATE=1 rpi-eeprom-update -d -f /boot/pieeprom-1613481816.bin
- Step **4**, Now you can reboot the CM4
>sudo reboot
- Step **5**, once the CM4 boot the system from the USB thumb drive correctly once again you should be ok to get the bootloader downgrade to the right verson. 
to check which bootloader version for your CM4 is, you can use this command:
>vcgencmd bootloader_version


