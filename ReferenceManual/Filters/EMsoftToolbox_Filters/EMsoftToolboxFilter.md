EMsoftExecuteFilter {#emsofttoolboxfilter}
=============

## Group (Subgroup) ##
EMsoftToolbox (EMsoftToolbox)

## Description ##
This **EMsoftExecuteFilter** provides the user with a pull-down list of currently available EMsoft programs and asks the user to select a .json formatted input file.
The filter checks to make sure that the .json file has the appropriate entries for the selected EMsoft program.  When all is ok, pressing the Go button will launch
the EMsoft program in a separate Terminal window (on Mac OS X).

## Parameters ##

| Name | Type | Description |
|------|------|-------------|
| EMProgramSelector | QString | name of the program to execute |
| ProgramInputFile | QString | name of .json input file |

## Required Geometry ##
Not Applicable

## Required Objects ##
both parameters must be set by the user.

## Created Objects ##
Launches an EMsoft program in an external window.

## License & Copyright ##

Please see the description file distributed with this plugin.

## Funding Acknowledgment ##

This filter was developed with financial support from contract AFRL FA8650-10-D-5210, Task Order 0034.

## DREAM3D Mailing Lists ##

If you need more help with a filter, please consider asking your question on the DREAM3D Users mailing list:
https://groups.google.com/forum/?hl=en#!forum/dream3d-users
