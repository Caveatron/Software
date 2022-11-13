# Caveatron Setup Firmware

This firmware is used to perform initial setup of the Caveatron after assembly. It includes a function for screen calibration, creating and loading the hardware code, loading fonts and graphics to the SPI Flash memory IC, initializing the calibration parameters, and a set of hardware test functions.

## Files

NOTE: The HEX files do not download properly if you try to right click on them. You must click on the link for one, then click on the RAW button in the upper right and then you can download it. Alternatively, just download the ZIP file which contains all the different versions.

You must select the version that is compatible with your display or Caveatron model for it to work correctly.
### For the Caveatron Rev C
- Caveatron_Setup_v20 - This version is for the Rev C Teensy 4.1 version of either the Caveatron or Caveatron SV.
*This is a beta version and has not been fully tested.*
### For the Caveatron Rev B
- ILI9488_16 - *The new standard display model going forward.* This is the version for the BuyDisplay 3.5" 480x320 display with the resistive touchscreen, 16-bit, and 3.3V options. 
- CTE35IPS_Normal - This version is for Coldtears Electronics 3.5" IPS touchscreens with non-inverted colors. This appears to include newer models that use the UTFT_GHL library as well as older models that used the a previous library. If the colors are inverted using this version (black text on a white background) then use the "Inverted" version.
- CTE35IPS_Inverted - This version is for use with certain Coldtears Electronics 3.5" IPS touchscreens with the UTFT_GHL library that produce inverted colors. Use this version to correct the colors back to normal.
- CTE40 - This version is for the Coldtears Electronics 4.0" touchscreen.
- Caveatron_SV - Version for the new survey-focused Caveatron (uses the ILI9488_16 BuyDisplay module).

The cvfont32.bin file contains the Caveatron fonts and graphics and must be loaded onto the SPI flash IC using the Caveatron_Setup firmware. It needs to be copied to a microSD card (32GB or smaller) that is inserted into the Teensy processor microSD slot in order for it to be loaded to the SPI flash.

## Summary of Setup Steps

Detailed instructions can be found in the document "Caveatron Setup & Calibration Instructions" in the documentation directory.

1. Load the Caveatron_Setup firmware to the Caveatron (see instructions in the software folder about loading firmware).
2. Place the cvfont32.bin file on the internal microSD card.
3. (Rev B only) Turn on the Caveatron and wait 10 sec for the Screen Calibration routine to start.
4. (Rev B only) Run the Screen Calibration routine (saving at the end will overwrite any previous calibration).
5. (Rev B only) Restart the Caveatron and tap the screen to enter setup.
6. Run the Hardware Setup routine to create the hardware code and initialize the calibration parameters (saving at the end will overwrite any previous hardware code or calibration).
7. Run the Load Fonts & Graphics routine to load the data from the microSD card file to the SPI flash IC.
8. (Optional) Run the Test Hardware routines to verify that the major hardware components are functioning properly.
