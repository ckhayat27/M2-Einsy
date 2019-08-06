Marlin 1.1 was used in this project /n
In configuration.h the following changes were made:
  -The board was changed from the RAMBo board to the Einsy RAMBo (The Einsy board should be in boards.h) 
        #ifndef MOTHERBOARD
          #define MOTHERBOARD BOARD_EINSY_RAMBO
        #endif 
  -#define DEFAULT_NOMINAL_FILAMENT_DIA 1.75 
  -#define POWER_SUPPLY 1
  -#define TEMP_SENSOR_0 1 and #define TEMP_SENSOR_BED 1 (there are only two thermistors on makergear M2)
  -#define TEMP_RESIDENCY_TIME 5, #define TEMP_HYSTERESIS 4, and #define TEMP_WINDOW 2 (values from original M2 marlin files on github)
  -#define TEMP_BED_RESIDENCY_TIME 5, #define TEMP_BED_HYSTERESIS 4, and #define TEMP_BED_WINDOW 2 (These commands did not exist in original M2 marlin file, so the values were copied from the previous lines (shown above))
  -#define HEATER_0_MAXTEMP 305 (limit of the extruder heater)
  -#define BED_MAXTEMP 150 (limit of bed heater)
  -#define DEFAULT_Kp 25.89, #define DEFAULT_Ki 1.94, and #define DEFAULT_Kd 86.53 (values from original M2 marlin files on github)
  -#define USE_ZMAX_PLUG and comment out #define USE_ZMIN_PLUG (the lower bound of z on printer should be 200 and the higher bound of z should be 0)
  -#define X_MIN_ENDSTOP_INVERTING true, #define Y_MIN_ENDSTOP_INVERTING true, #define Z_MIN_ENDSTOP_INVERTING false, #define X_MAX_ENDSTOP_INVERTING false, #define Y_MAX_ENDSTOP_INVERTING false, and #define Z_MAX_ENDSTOP_INVERTING true        
      (Einsy inverts some of the logic of the endstops, these changes should fix that)
  -#define X_DRIVER_TYPE TMC2130, #define Y_DRIVER_TYPE TMC2130, #define Z_DRIVER_TYPE TMC2130, #define E0_DRIVER_TYPE TMC2130
      (These commands must be defined for the Einsy board, the arduino IDE will prevent any uploading unless these are defined)
  -
