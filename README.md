# Einsy Rambo on Makergear M2
## Marlin 1.1 was used in this project 
## In configuration.h (file in github files) the following changes were made:
 - ``` #ifndef MOTHERBOARD #define MOTHERBOARD BOARD_EINSY_RAMBO #endif ```
The board was changed from the RAMBo board to the Einsy RAMBo (The Einsy board should be in boards.h) 
 - ``` #define DEFAULT_NOMINAL_FILAMENT_DIA 1.75 ```
Define the filament diameter as 1.75 
 - ``` #define POWER_SUPPLY 1 ```
Define Power Supply as 1
 - ``` #define TEMP_SENSOR_0 1 #define TEMP_SENSOR_BED 1 ```
Define extruder and bed thermistor as on
 - ``` #define TEMP_RESIDENCY_TIME 5 #define TEMP_HYSTERESIS #define TEMP_WINDOW 2 ```
Define range in which a temperature is seen as close enough (these are the default M2 settings)
 - ```#define TEMP_BED_RESIDENCY_TIME 5 #define TEMP_BED_HYSTERESIS 4 #define TEMP_BED_WINDOW 2 ```
Define range in which bed temperature is seen as close enough (Copied from previous default settings)
 - ```#define HEATER_0_MAXTEMP 305 ```
Define max extruder temperature
 - ```#define BED_MAXTEMP 150 ```
Define max bed temperature
 - ``` #define DEFAULT_Kp 25.89 #define DEFAULT_Ki 1.94 #define DEFAULT_Kd 86.53 ```
PID settings
 - ```#define USE_ZMAX_PLUG  //#define USE_ZMIN_PLUG ``` 
Use Zmax plug and comment out Zmin plug
 - ```#define X_MIN_ENDSTOP_INVERTING true  #define Y_MIN_ENDSTOP_INVERTING true  #define Z_MIN_ENDSTOP_INVERTING false  #define           X_MAX_ENDSTOP_INVERTING false  #define Y_MAX_ENDSTOP_INVERTING false  #define Z_MAX_ENDSTOP_INVERTING true ```   
Input the following enstop inverting settings
 - ```#define X_DRIVER_TYPE TMC2130, #define Y_DRIVER_TYPE TMC2130, #define Z_DRIVER_TYPE TMC2130, #define E0_DRIVER_TYPE TMC2130 ```
Define motor driver types as TMC2130, the arduino IDE will not allow you to upload marlin to the board if these are not defined
 - ``` #define DEFAULT_AXIS_STEPS_PER_UNIT { 88.89, 88.89, 1058.4, 471.57 } ```
These settings are only for M2 motors, if you have different motors look at their datasheets to configure
 - ``` #define DEFAULT_MAX_FEEDRATE { 200, 200, 5, 25 } ```
These settings can be changed, these are the default settings for the printer
 - ``` #define DEFAULT_MAX_ACCELERATION { 900, 1000, 100, 2000 } ```
These settings can be changed, these are the default settings for the printer
 - ```#define DEFAULT_XJERK 4.0 #define DEFAULT_YJERK 4.0 #define DEFAULT_ZJERK 0.4 #define DEFAULT_EJERK 1.0 ```
These settings can be changed, these are the default settings for the printer
 - ``` #define INVERT_X_DIR false #define INVERT_Y_DIR true #define INVERT_Z_DIR true #define INVERT_E0_DIR true ```
These ensure the motors move in correct direction
 - ``` #define X_HOME_DIR -1 #define Y_HOME_DIR -1 #define Z_HOME_DIR  1 ```
These settings define the Xmin, Ymin, and Zmax endstops
 - ``` #define X_BED_SIZE 200 #define Y_BED_SIZE 250 #define Z_MAX_POS 200 ```
Limits of the M2 dimensions, all the min positions should be set to 0
 - ``` #define SDSUPPORT #define SD_CHECK_AND_RETRY ```
If you have a SD card input, then uncomment the following commands (sd check and retry is optional, just a precaution)
## In Configuration_adv.h (file in github files) the following changes were made:
 - ``` #include "TMC2130Stepper.h" ```
Include the arduino library for the TMC2130 SPI stepper control
 - ``` #define E0_AUTO_FAN_PIN  6 ```
The fan that comes with the M2 will need to be replaced by a 5v dc fan with an equal air flow value (bed cooling CFM is 12.5, other two are 6.5 (i think))
## In Pins_Einsy_Rambo.h (file in github files) the following change was made: 
 - ``` #define SDSS 53 ```
This change is for an sd card reader attachment
## In Sdfatconfig.h (file in github files) the following change was made:
 - ``` #define SOFT_SPI_CS_PIN 53 #define SOFT_SPI_MOSI_PIN 51 #define SOFT_SPI_MISO_PIN 50 #define SOFT_SPI_SCK_PIN 52 ```
This is for an sd card reader attachment

# Pin Out for Einsy board
- [Here](https://reprap.org/wiki/EinsyRambo_development) are all the pin locations on the einsy board
- The x and y min endstop wires will need to be removed from their three wire connectors and be placed into two wire connectors, these then can go into their respective spot on the einsy (keep in mind which wire is GND)
- The z endstop can stay in its three wire connector and should be placed into the - (blue) s (green) T (yellow) positions
- The motor wires can stay in their original connectors, simply remove them from the rambo board and plug them into their respective spots on the einsy, the top z motor plug is the standard plug
- The thermistors can stay in their original connectors and need to be plugged into their respective plugs (T0 and T2)
- The fans should be placed into a three wire connectors (even though there are only two wires) and go into their respective plugs, red on the middle peg (5v) and black on the ground peg. Keep in mind that the einsy rambo does not support 24 volt or 12 volt fans. 5 volt fans with the same cfm as their counterparts can be purchased or an external 24 volt or 12 volt power source can be used with the original fans.
- The extruder heat (heat 0) wires must be put into another connector (usually comes with the board, it is angled) and will be plugged into the "heater output" next to the fan outputs.
- The bed heat is no longer a regular pin on the board. The bed heat wires will need to be crimped and connected to the bed output pins on the board.
- The bed input and power input should come from your 24 volt power source. The wires from the power source will need the same crimps as the bed heat wires and should be screwed down in the designated area.
- If you wish to reinstall the sd card reader the pinout is a little tricky. The 5 volt power wire and the ground wire should be connected to pins 1(5v) and 2(GND) in the "ext 1" sections of the board. The MOSI wire should be connected to pin 12 on the extension J19. The SS wire should be connected to pin 5 on the extension J19. The SCK wire should be connected to pin 11 on the extension J19. The MISO wire should be connected to pin 9 on the extension J19. How you wish to connect this to the board is up to you.

 ## The Arduino IDE was used to upload the firmware to the Einsy Board. 
 ## The M2 Quickstart app can be used for leveling the bed, it should not, however, be used for printing or setting temperature. Programs such as Simplify3D and pronterface will allow you to print.
 
