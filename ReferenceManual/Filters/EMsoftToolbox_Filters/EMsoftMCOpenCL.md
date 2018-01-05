EMsoftMCOpenCL {#emsoftmcopencl}
=============

## Group (Subgroup) ##
EMsoftToolbox (EMsoftToolbox)

## Description ##
This EMsoftMCOpenCL filter asks the user for all the parameters needed by the EMMCOpenCL Monte Carlo program and subsequently calls and executes the external subroutine *EMsoftCgetMCOpenCL*, which is part of the EMsoft package.  This routine returns two accumulator arrays, one for energy (accum_e), one for depth (accum_z), that can subsequently be used by the **EMsoftEBSDmaster** filter.  The routine also provides the option to store the results as an EMsoft HDF5 file which can then be read by other EMsoft programs outside of DREAM.3D; by default, the accumulator arrays are only stored as part of a regular .dream3d file when the user calls the appropriate write filter at the end of the pipeline.  The filter also offers the option to store the parameters in a .json file, which can then be read as an input file by the EMsoft *EMMCOpenCL* program.  Note that this program makes use of the GPU card on your system, if one is available.

## Parameters ##
| Name | Type | Default Value | Description |
|------|------|------|------|
| XtalName| QString | "undefined" | Crystal structure file name |
| Mode | choice | "EBSD" | "EBSD" for regular MC, "ECP" for BSE1 output only|
| Sig | double | 70.0 | Mode=EBSD: sample tilt angle around TD [degrees] |
| Omega | double | 0.0 | Mode=EBSD: sample tilt angle around RD [degrees] |
| Sigstart | double | 0.0 | Mode=ECP: starting sample tilt angle around TD [degrees] |
| Sigend | double | 30.0 | Mode=ECP: ending sample tilt angle [degrees] |
| Sigstep | double | 2.0 | Mode=ECP: sample tilt step size [degrees] |
| EkeV | double | 30.0 | SEM accelerating voltage [kV] |
| Ehistmin| double |15.0 | low energy limit of energy histogram [kV]|
| Ebinsize| double |0.5 | energy histogram step size [kV]| 
| Depthmax| double | 100.0 | maximum depth for depth histogram [nm]|
| Depthstep| double |1.0| depth histogram step size [nm]|
| Numsx | int | 501 | number of pixels along horizontal square Lambert projection|
| Numel | int |10|number of electrons per thread *(comment 1)*|
| Totnumel | int | 2000000000 | number of electrons in Monte Carlo simulation *(comment 3)* |
| Multiplier | int | 1 | multiplier for number of electrons *(comment 3)* |
| Devid|int|1| GPU device ID *(comment 2)*|
| Globalworkgrpsz|int|150| GPU Global workgroup size *(comment 1)*|
| JsonFile|QString|"EMMCOpenCL.json"|name of json output file for this filter (Optional)|
| DataName| QString |"MCoutput.h5" |name of Monte Carlo EMsoft HDF5 [.h5] output file (Optional) |

*Comment 1:* The GPU related parameters (Numel and Globalworkgrpsz) have default values that are based on the dual AMD D500 GPU cards found in the Mac Pro "trash can" computers and will need to be adjusted for other GPU models. We post here a list of recommended settings for various GPUs as they become available. The highlighted number indicates the value for which the program execution is fastest, and that execution time is listed in the last column.  The test runs were executed using the default parameters above for the Al.xtal structure.  The only difference between the various runs is the globalworkgrpsz parameter.

|GPU type | Numel | Globalworkgrpsz | Fastest Time (s)|
|---------|-------|-----------------|-----------|
|AMD D500 (Mac Pro)| 10 | 150, **300** | 741 |
|ATI Radeon HD 6970M  (iMac)|10|64, 150, **300**, 450| 3,613 |
|NVidia Tesla K80 (multi-GPU Linux)| 10 |128, 256, **512**, 1024| 437|

It should be noted that on some cards, *any* value of the globalworkgrpsz will work, and on others only very specific values will produce results.  For instance, on the ATI Radeon and AMD cards, any values other than the ones listed above will return zero for the accumulator arrays (zero BSE yield).  For the Tesla K80 card on the other hand, any number less than or equal to 1024 (e.g., 463) works fine, but only powers of two will result in fast execution times.

*Comment 2:* If your computer has more than one GPU card (you should be so lucky...), then you can use the Devid parameter to indicate on which card you wish the program to be executed.
To find out which resources are available on your computer, either type in a large number for the device parameter (and the filter will list the available devices in yellow at the bottom of the GUI), or use the *EMsoftGetGPUInfo* filter to create a .json file containing all device parameters for your system.

*Comment 3:* The total number of electrons to be considered is described by a 32-bit int variable Totnumel; the GUI will not allow you to enter a number larger than 2,147,483,647.  If you want more electrons, you can set the Multiplier to an integer larger than 1.

## Required Geometry ##

Not Applicable

## Required Objects ##

Not Applicable

## Created Objects ##
| Kind | Default Name | Type | Component Dimensions | Description |
|------|--------------|-------------|---------|----------------|
| **Data Container** | EMsoftDataContainer | N/A | N/A | Created **Data Container** name **EMsoftDataContainer**|
| **Attribute Matrix** | EMsoftAttributeMatrix | Generic | N/A | Created **Cell Attribute Matrix** name |
| **Generic Attribute Array** | (accum_e; user defined) | int32_t | (1 tuple; 3D array) | Created **Generic Attribute Matrix** name |
| **Generic Attribute Array** | (accum_z; user defined) | int32_t | (1 tuple; 4D array) | Created **Generic Attribute Matrix** name |

## License & Copyright ##

Please see the description file distributed with this plugin.

## Funding Acknowledgment ##

This filter was originally developed with financial support from contract AFRL FA8650-10-D-5210, Task Order 0034;  this includes the direct calling of the EMsoftCgetMCOpenCL EMsoft routine to execute the Monte Carlo run as a filter.

## DREAM3D Mailing Lists ##

If you need more help with a filter, please consider asking your question on the DREAM3D Users mailing list:
https://groups.google.com/forum/?hl=en#!forum/dream3d-users
