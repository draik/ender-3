# Marlin 2.0.6 Build 7 (firmware-20201016-150145.bin)
Setup PID for hotend and bed, after running PID Autotune.  

## Changes
**Configuration.h**

    - #define DEFAULT_Kp 26.61
    - #define DEFAULT_Ki 2.63
    - #define DEFAULT_Kd 67.19

    - #define DEFAULT_bedKp 104.79
    - #define DEFAULT_bedKi 18.68
    - #define DEFAULT_bedKd 392.00

# Marlin 2.0.6 Build 6 (firmware-20200924-124550.bin)
Enable the custom boot screens  

## Changes
**Configuration.h**

    - #define SHOW_CUSTOM_BOOTSCREEN
    - #define CUSTOM_STATUS_SCREEN_IMAGE

# Marlin 2.0.6 Build 5 (firmware-20200921-181810.bin)
Enabled the ability for OctoPrint to push M73 status updates to the screen  

## Changes
**Configuration_adv.h**

    - #define LCD_SET_PROGRESS_MANUALLY
    - #define USE_M73_REMAINING_TIME

# Marlin 2.0.6 Build 4 (firmware-20200916-211044.bin)
Disabling an additional option to ensure the printer sets the progress information.  

## Changes
**Configuration_adv.h**

    - //#define LCD_SET_PROGRESS_MANUALLY (disable setting manually)

# Marlin 2.0.6 Build 3 (firmware-20200916-174937.bin)
Making minor changes to the the probing position, nozzle parking, and LCD  
status updates. The OctoPi can provide M73 status bar updates, but it  
requires a plug-in for that. Instead, I will let the firmware handle it.  

## Changes
**Configuration.h**

    - #define Z_AFTER_PROBING             5 (enable and set to 5mm height)
    - #define NOZZLE_PARK_POINT { X_MIN_POS, Y_MIN_POS, 20 } (park the nozzle at home)

**Configuration_adv.h**
    - #define LCD_SET_PROGRESS_MANUALLY (enable setting the progress bar manually; M73)
    - #define LCD_SHOW_E_TOTAL (show how much filament has been used)
    - #define PRINT_PROGRESS_SHOW_DECIMALS (show progress with XX.Y percentage)
    - #define SHOW_REMAINING_TIME (enable show remaining time)
    - #define ROTATE_PROGRESS_DISPLAY (cycle progress, elapsed, remaining time)

# Marlin 2.0.6 Build 2 (firmware-20200915-204809.bin)
Almost caught the printer on fire during power up. This was caused from how  
BLTouch was being connected to the Creality v4.2.7 board. Disabled the  
connection method that I was not using, removed the Z stop connector, and  
plugged in the BLTouch as I did with the v1.1.3 board. Everything is working  
as expected, with all options I need.

## Changes
**Configuration.h**

    - //#define Z_MIN_PROBE_PIN 17 // Pin 32 is the RAMPS default

# Marlin 2.0.6 Build 1 (firmware-20200914-215152.bin)
This is the first official build with my own changes, and known to be working  
on the new board: Creality v4.2.7. The BLTouch was included, but not verified  
as working, due to pin connection issues. There are 2 methods for connecting  
the BLTouch, and there is a required attention to detail when connecting the  
pins. Colors are changed due to the Creality v1.1.3 board, and the on-board  
pins for Creality v4.2.7 motherboard.  

## Changes
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

# Marlin 2.0.x Configuration Bugfix
This was more for the core Marlin 2.0 firmware than the configurations, but  
applying these here as they were used for testing stability; it worked.  

# Marlin 2.0 Ender-3 Pro v1.5
This firmware example is made for the Creality v4.2.2 boards that were becoming  
the new standard for motherboards on the Ender-3 3D printer as of 2020.  
This is the base configuration for Ender-3 Pro on v4.2.7 motherboard.  

# Marlin 2.0 Default
The default configuration is the base for any 3D printer, and generally works  
for any board that can accept the Marlin 2.0 firmware. It is also highly  
recommended to be on a 32-bit board, even though 8-bit is still supported.  

Adding the default configuration as a base to the upcoming upgrades and  
enabled options for my Ender-3 Pro.  

# Marlin 1.1.9
This contains the default build for Marlin 1.1.9.  
The build is compiled in Arduino IDE, and pushed through an Arduino Uno  
setup as an ISP, connected to the v1.1.3 Creality board (stock).  

# Marlin 1.1.9 Creality
Initial commit is the default Marlin 1.1.9 firmware. There is a Creality  
folder that contains Ender-3 specifics, but also works for the Ender-3 Pro.  
Nothing was changed when flashed to the Ender-3 Pro.

