# Einsy Rambo on Makergear M2
## Marlin 1.1 was used in this project 
## In configuration.h the following changes were made:
   - ``` #ifndef MOTHERBOARD #define MOTHERBOARD BOARD_EINSY_RAMBO #endif ```
*The board was changed from the RAMBo board to the Einsy RAMBo (The Einsy board should be in boards.h) 
   - ``` #define DEFAULT_NOMINAL_FILAMENT_DIA 1.75 ```
*Define the filament diameter as 1.75 
    - ``` #define POWER_SUPPLY 1 ```
*Define Power Supply as 1
  - ``` #define TEMP_SENSOR_0 1 #define TEMP_SENSOR_BED 1 ```
*Define extruder and bed thermistor as on
   - ``` #define TEMP_RESIDENCY_TIME 5 #define TEMP_HYSTERESIS #define TEMP_WINDOW 2 ```
*Define range in which a temperature is seen as close enough (these are the default M2 settings)
   - ```#define TEMP_BED_RESIDENCY_TIME 5 #define TEMP_BED_HYSTERESIS 4 #define TEMP_BED_WINDOW 2 ```
*Define range in which bed temperature is seen as close enough (Copied from previous default settings)
   -#define HEATER_0_MAXTEMP 305
*Define max extruder temperature
   -#define BED_MAXTEMP 150
*Define max bed temperature
   -``` #define DEFAULT_Kp 25.89 #define DEFAULT_Ki 1.94 #define DEFAULT_Kd 86.53 ```
*PID settings
    - ```#define USE_ZMAX_PLUG  //#define USE_ZMIN_PLUG ``` 
*Use Zmax plug and comment out Zmin plug
  - ```#define X_MIN_ENDSTOP_INVERTING true  #define Y_MIN_ENDSTOP_INVERTING true  #define Z_MIN_ENDSTOP_INVERTING false  #define X_MAX_ENDSTOP_INVERTING false  #define Y_MAX_ENDSTOP_INVERTING false  #define Z_MAX_ENDSTOP_INVERTING true ```   
*Input the following enstop inverting settings
  - ```#define X_DRIVER_TYPE TMC2130, #define Y_DRIVER_TYPE TMC2130, #define Z_DRIVER_TYPE TMC2130, #define E0_DRIVER_TYPE TMC2130 ```
*Define motor driver types as TMC2130, the arduino IDE will not allow you to upload marlin to the board if these are not defined
  
   
