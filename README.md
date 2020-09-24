# Ender-3 Pro Firmware
This will be where I maintain the changes to the firmware applied to the  
Ender-3 Pro 3D printer.

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

## Marlin 2.0.6 Build 6 (firmware-20200924-124550.bin)
Enable the custom boot screens  

### Changes
**Configuration.h**

    - #define SHOW_CUSTOM_BOOTSCREEN
    - #define CUSTOM_STATUS_SCREEN_IMAGE

## Marlin 2.0.6 Build 5 (firmware-20200921-181810.bin)
Enabled the ability for OctoPrint to push M73 status updates to the screen  

### Changes
***Configuration_adv.h**

    - #define LCD_SET_PROGRESS_MANUALLY
    - #define USE_M73_REMAINING_TIME

## Marlin 2.0.6 Build 4 (firmware-20200916-211044.bin)
Disabling an additional option to ensure the printer sets the progress information.  

### Changes
**Configuration_adv.h**

    - //#define LCD_SET_PROGRESS_MANUALLY (disable setting manually)

## Marlin 2.0.6 Build 3 (firmware-20200916-174937.bin)
Making minor changes to the the probing position, nozzle parking, and LCD  
status updates. The OctoPi can provide M73 status bar updates, but it  
requires a plug-in for that. Instead, I will let the firmware handle it.  

### Changes
**Configuration.h**

    - #define Z_AFTER_PROBING             5 (enable and set to 5mm height)
    - #define NOZZLE_PARK_POINT { X_MIN_POS, Y_MIN_POS, 20 } (park the nozzle at home)

**Configuration_adv.h**
    - #define LCD_SET_PROGRESS_MANUALLY (enable setting the progress bar manually; M73)
    - #define LCD_SHOW_E_TOTAL (show how much filament has been used)
    - #define PRINT_PROGRESS_SHOW_DECIMALS (show progress with XX.Y percentage)
    - #define SHOW_REMAINING_TIME (enable show remaining time)
    - #define ROTATE_PROGRESS_DISPLAY (cycle progress, elapsed, remaining time)

## Marlin 2.0.6 Build 2 (firmware-20200915-204809.bin)
Almost caught the printer on fire during power up. This was caused from how  
BLTouch was being connected to the Creality v4.2.7 board. Disabled the  
connection method that I was not using, removed the Z stop connector, and  
plugged in the BLTouch as I did with the v1.1.3 board. Everything is working  
as expected, with all options I need.

### Changes
**Configuration.h**

    - //#define Z_MIN_PROBE_PIN 17 // Pin 32 is the RAMPS default

## Marlin 2.0.6 Build 1 (firmware-20200914-215152.bin)
This is the first official build with my own changes, and known to be working  
on the new board: Creality v4.2.7. The BLTouch was included, but not verified  
as working, due to pin connection issues. There are 2 methods for connecting  
the BLTouch, and there is a required attention to detail when connecting the  
pins. Colors are changed due to the Creality v1.1.3 board, and the on-board  
pins for Creality v4.2.7 motherboard.  

### Changes
**Configuration.h**

    - BOARD_CREALITY_V427 (was only V4)  
    - Z_MIN_PROBE_PIN 17 (was pin 32)  
    - #define BLTOUCH (enabling BLTouch)  
    - #define NOZZLE_TO_PROBE_OFFSET { -40, -10, 0 }  
    - //#define MIN_SOFTWARE_ENDSTOP_Z (allows for negative value)  
    - #define AUTO_BED_LEVELING_BILINEAR (enable bilinear bed leveling)  
    - #define LCD_BED_LEVELING (enable bed leveling menu)  
    - #define Z_SAFE_HOMING (lift Z so as to not scrape on print or bed)  
    - #define PREHEAT_1_TEMP_BED     70 (pre-heat PLA bed to 70C)  
    - #define NOZZLE_PARK_FEATURE (enable nozzle parking)  
    - #define SPEAKER (32-bit board with space; re-enable the speaker)  

**Configuration_adv.h**

    - #define BLTOUCH_DELAY 500 (enable BLTouch delay)  
    - #define ADVANCED_PAUSE_FEATURE (enable advanced pause feature)  
    - #define PARK_HEAD_ON_PAUSE (park during pause and filament change)  
    - #define HOME_BEFORE_FILAMENT_CHANGE (go home before filament change)  

## Marlin 2.0.x Configuration Bugfix
This was more for the core Marlin 2.0 firmware than the configurations, but  
applying these here as they were used for testing stability; it worked.  

## Marlin 2.0 Ender-3 Pro v1.5
This firmware example is made for the Creality v4.2.2 boards that were becoming  
the new standard for motherboards on the Ender-3 3D printer as of 2020.  
This is the base configuration for Ender-3 Pro on v4.2.7 motherboard.  

## Marlin 2.0 Default
The default configuration is the base for any 3D printer, and generally works  
for any board that can accept the Marlin 2.0 firmware. It is also highly  
recommended to be on a 32-bit board, even though 8-bit is still supported.  

Adding the default configuration as a base to the upcoming upgrades and  
enabled options for my Ender-3 Pro.  

# Marlin 1.1.9
This contains the default build for Marlin 1.1.9.  
The build is compiled in Arduino IDE, and pushed through an Arduino Uno  
setup as an ISP, connected to the v1.1.3 Creality board (stock).  

## Marlin 1.1.9 Creality
Initial commit is the default Marlin 1.1.9 firmware. There is a Creality  
folder that contains Ender-3 specifics, but also works for the Ender-3 Pro.  
Nothing was changed when flashed to the Ender-3 Pro.

