# Software
Caveatron Firmware, Utilities, and Desktop Software

## Contents
- Pre-compiled HEX files of the Caveatron software
- Pre-compiled HEX file of the Caveatron_Setup software and fonts and graphics files for loading to SPI flash
- Instructions for loading the HEX files.
- Utility code for uploading and downloading EEPROM-stored parameters
- Caveatron Process Desktop software

## Caveatron Software Release Notes
**Version 3 of the Caveatron software is for the Teensy 4.1 Rev C version of the Caveatron only.**

### Version 3.02
#### All Caveatron models:
- Fixed issue that resulted in the box dimensions being incorrectly loaded
- Minor display and formatting fixes
#### Caveatron:
- Fixed issue that would cause the LRF to freeze during scans
- Display of Room mode scan data in View Scans menu is now working correctly
- Improved display of Passage mode scans by implementing basic post-processing of the data
- Reworked method of detecting excess azimuth/inclination shifts during scans to make it independent of rotation speed
- Room mode scan now detects inclination shifts
- Removed LIDAR overflow error check since there doesn't seem to be any affect on the scans
#### Caveatron SV:
- Fixed issue in Manual Mode where LRF would stop working when switching from Quickshot mode
- Fixed issue in Manual Mode where "Done" button would not be displayed

### Version 3.01
- Moved numerous variables to a different Teensy memory area to hopefully prevent random system hangs and crashes
- Fixed bug in LRF code that may have been causing the LRF acquisition to freeze
- Fixed several issues with viewing LIDAR scans
- Fixed screen brightness setting bug
- Fixed screen dimming issue after exiting scan review mode
- Changed status bar redraw code to prevent flashing issues

### Version 3.00
#### Changes in this version for both the Caveatron and Caveatron SV:
- Major rewrites to support Teensy 4.1 - Teensy 3.6 no longer supported
- Fonts and graphics now are stored in SPI flash chip on Teensy 4.1 - external SPI flash module support removed
- BuyDisplay 3.5" capacitive touchscreen is now the only screen supported
- Added support for RM3100 magnetometer
- Removed support for MAX17043 battery level detection - resistor voltage divider is now the only supported method
- Added detection of excessive front-to-back-sight angle difference
- Added Reshoot mode to redo front and back sights after backsight taken
- Added detection and warning of magnetic anomalies when taking shots
- Changed enclosure dimensions to a user calibration parameter instead of being hard-coded.
- Full support for both HEX and ASCII versions of the JRT laser rangefinder modules.
- Changed some variable declarations for less memory usage
- Cleanup of some unused code
- Fixes of minor bugs
#### Changes for the Caveatron only:
- Added support for RPLIDAR S2
- Modifications to hopefully better support other RPLIDAR A-series units (not tested)
- New CVL file format with compressed binary storage of LIDAR data points and data integrity check
- Removed support for Scanse SWEEP LIDAR
- Rewrote Live LIDAR display mode for faster and better rendering
- Adjusted angle cutoff tolerance for Passage mode to account for inclination
- Disabled the 2K scan mode for the A1 series due to unresolved issues
- Added setting to enable or disable LIDAR window corrections for A1 series
#### Changes for the Caveatron SV only:
- Added ability to select point type for Points mode (plan, profile, cross section)


**The versions below are for the Teensy 3.6 Rev B version of the Caveatron**
### Version 2.23
#### All Caveatron models:
- Fix of freeze in Line Plot View for surveys with more than 100 shots.
- Line Plot View now displays most recent 100 shots.
- Added preliminary support for JRT LRF module with hex protocol (LRF hangs can occur in Passage Mode scans)
#### Caveatron:
- Increased Passage Mode reverse speed limit to 1 m/s.

### Version 2.22
#### All Caveatron models:
- Improved Compass Calibration:
	- doubled number of calibration points for better accuracy.
	- added 4 sectors to each quadrant for better point distribution.
	- dynamic timing for point capture.
- Improved Calibration Check to give a more meaningful result.
#### Caveatron SV:
- Fixed bug when an LRUD measurement fails.

### Version 2.21
The same firmware release works on both the regular Caveatron and the Caveatron SV models. The release note will indicate changes specific to each model and changes that are common across both models.
#### Caveatron:
- Fixed broken Manual Mode
#### All:
- Bug fix where LCD Dimming preference would not always save

### Version 2.20 
(Removed from download due to major bug in Manual Mode for standard Caveatron - replaced with v2.21)

FIRST RELEASE FOR THE NEW CAVEATRON SV! 
The same firmware release works on both the regular Caveatron and the Caveatron SV models. The release note will indicate changes specific to each model and changes that are common across both models.
#### Caveatron SV:
- Adds LRUD Mode for recording left, right, up, and down measurements at each station.
- Adds Point Mode for recording simple point measurements from a station to capture general passage dimensions. These are saved in a new file format, a .cvp file, that can be converted to a rudimentary point cloud in Caveatron Process.
- Modification to Manual Mode including a Quickshot mode that allows acquisition of a list of fast shots similar to a traditional disto.
#### Caveatron:
- Fixed bug in LIDAR scan display.
- Fixed bug where Caveatron units with v5 of the MinIMU and AltIMU would not write the scaling factor line to the IMU file.
#### All:
- Added zoom and pan to the Line Plot Viewer.
- Added screen brightness adjustment preference and auto-dimming function (requires connection of Teensy pin 9 to LCD pin 29).
- Added support for new battery monitor method using a resistor voltage divider connected to Teensy pin A10.
- When connected to a PC via USB, it now appears as "Caveatron" instead of "Teensy".
- Minor bug fixes.

### Version 2.10
WARNING! You will need to create a new survey after this update since the file storage format has changed! No existing files on the card are changed but the current survey will not be accessible by the Caveatron.
- New file storage configuration. All files for a survey are now stored together in their own directory name with the cave name and date. Settings for a survey are now stored in a .dat file in each folder (settings.txt is no longer used).
- Added capability to reopen and continue previous surveys (not backward compatible with surveys taken before 2.10).
- Added note entry capability. General survey info can be entered during new survey setup such as team member names, etc. This can also be edited or added later. Notes can also be entered/edited for each shot, such as whether there are interesting features or if it ties into an existing station.
- Added shot editing ability including editing station names and changing front-sights to back-sights and vise versa.
- Shot editing, deleting, and adding shot note are done through a new contextual menu in the View/Edit Shots page.
- Added more error checks when opening files.
- Added support for Pololu MinIMU-9 v5 and AltIMU-10 v5 compass modules. 
- Fixed bug so that multiple files/folders can now be copied together to/from a PC without corruption.

### Version 2.05
- Added support for BuyDisplay 3.5" 480x320 resistive touchscreen LCD module (Hardware code display=4)
- Fixed bug so that the LRF range calibration is applied in Shot and Manual modes
- Fixed bug with Manual Mode range toggle switch not turning off

### Version 2.04
- Fixed bug that caused a freeze when a Splay shot failed
- Fixed bug that caused an error when shot is deleted
- Changed some wording in GUI
- Changed shot delete to remove shot line from survey file instead of just marking it for removal

### Version 2.03
- Overhauled code related to LRF operation in Passage Mode to improve performance and stability
- Fixed multiple problems that prevented UT390v2 and JRT LRF modules from working properly in Passage Mode
- Fixed bug in LIDAR error handling
- Fixed bug in calibration view
- Fixed GUI for "no battery gauge" hardware setting

### Version 2.02
- Added ability to upload LIDAR Window Corner, Window Distortion, LIDAR orientation, and LRF offset calibration parameters via an IMU file.
- A fix to the RPLIDAR timeout and a new capability to display multiline wrapped text.

### Version 2.01
- Added LIDAR window distortion calibration parameters to IMU file.
- Added absolute scaling values for IMU sensors.
- Fixed shot/scan review to show most recent 96/88 entries (previously didn't work properly when entries maxed out).
- Changed shot & scan review pages to show 8 entries per page (previously showed 7).
- Improved statistics page.
- Bug fixes.

### Version 2.00
- Rewritten to work on the Teensy 3.6 platform. Arduino Due no longer supported.
- Numerous changes throughout to support new hardware and improve performance.
Major revisions:
- RPLIDAR can now scan at 8K pts/sec. Both rotation speed and scan rate are adjustable in settings.
- Gyroscope support added. IMU data now captured at 40msec intervals.
- LIDAR scanning code rewritten to grab LRF and IMU data more quickly and consistently.
- CVL LIDAR file format changed (v2) to store raw IMU data for enhanced position/orientation post processing.
- Can directly open microSD card on PC as MTP disk and drag and drop files. Caveatron Connect app no longer used.
- Auto power shutoff after user selectable interval.
- Support for saved preferences.
- Fonts and graphics now stored on separate SPI flash IC. No longer dependent on display module.
- Removed support for XV LIDAR and Sparkfun Battery Babysitter. No longer supports changing LIDAR modules.
