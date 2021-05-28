# Software
Caveatron Firmware, Utilities, and Desktop Software

## Contents
- Pre-compiled HEX files of the Caveatron software
- Pre-compiled HEX file of the Caveatron_Setup software and fonts and graphics files for loading to SPI flash
- Instructions for loading the HEX files.
- Utility code for uploading and downloading EEPROM-stored parameters
- Caveatron Process Desktop software

## Caveatron Software Release Notes
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
