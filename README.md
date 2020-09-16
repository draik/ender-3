# Ender-3 Pro Firmware
This will be where I maintain the changes to the firmware applied to the  
Ender-3 Pro 3D printer.

# Marlin 1.1.9
This contains the default build for Marlin 1.1.9.  
The build is compiled in Arduino IDE, and pushed through an Arduino Uno  
setup as an ISP, connected to the v1.1.3 Creality board (stock).  

## Marlin 1.1.9 Creality
Initial commit is the default Marlin 1.1.9 firmware. There is a Creality  
folder that contains Ender-3 specifics, but also works for the Ender-3 Pro.  
Nothing was changed when flashed to the Ender-3 Pro.

# Marlin 2.0
Marlin 2.0 supports 8-bit boards, like the stock Creality v1.1.3 motherboard,  
but now has the added bonus of supporting 32-bit boards. Such board is the  
Creality v1.1.5 motherboard which has silent motors. However, Creality has  
upgraded that v1.1.5 board to v4.2.7, flashed a bootloader, and given it a  
version of Marlin 2, but might need adjusting. Creality only provides the  
firmware.bin file on their site, without specifying their settings.  
The Marlin 2.0 firmware will work on the v1.1.3 board, but there will need to  
be options disabled to make it all fit on the small flash size.  

I purchased the v1.1.5 board, and received the upgraded v4.2.7 motherboard.  
One of the benefits to this board is that it has a connector made for the  
BLTouch auto-leveling tool. I purchased this and used it on the v1.1.3 before  
upgrading motherboards; worth it!  

I will not include the firmware setup for Marlin 2 on the v1.1.3 board, as it  
is not complete with all the features I had with v1.1.9; too many sacrifices  
adding BLTouch on Marlin firmware.  

*NOTE*: Marlin 2.0 firmware will refer to the v4.2.7 motherboard, including the  
addition of BLTouch to the Ender-3 Pro 3D printer.

## Building the Firmware
There is no ISP port on the v4.2.7 board, and firmware flashing is done via  
USB or the microSD card. Additionally, the USB port changed from mini-USB to  
micro-USB.  

Building the firmware is done through Visual Studio Code, along with the  
PlatformIO IDE and Auto Build Marlin plug-ins. There will be changes needed  
in the platformio.ini file, to ensure the proper board is used for compiling  
through the Auto Build Marlin plug-in.  

## Marlin 2.0 Default
The default configuration is the base for any 3D printer, and generally works  
for any board that can accept the Marlin 2.0 firmware. It is also highly  
recommended to be on a 32-bit board, even though 8-bit is still supported.  

Adding the default configuration as a base to the upcoming upgrades and  
enabled options for my Ender-3 Pro.  
