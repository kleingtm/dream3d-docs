 EMsoftEBSD {#emsoftebsd}
=============

## Group (Subgroup) ##
EMsoftToolbox (EMsoftToolbox)

## Description ##
This EMsoftEBSD filter asks the user for all the parameters needed by the **EMEBSD** program and subsequently generates a json file that can be read by this program.

## Parameters ##
| Name | Type | Default Value | Description |
|------|------|------|------|
| XtalName| QString                  | "undefined"  | Crystal structure file name |
| numsx | integer(kind=irg)          | 640 | Number of camera pixels along x | 
| numsy | integer(kind=irg)          | 480 | Number of camera pixels along y | 
| binning | integer(kind=irg)        | 1 | Binning factor [1, 2, 4, or 8]|
| nthreads | integer(kind=irg)       | 1 | Number of OpenMP threads |
| energyaverage | integer(kind=irg)  | 0 | Use energy averaged background ? (faster) |
| L | real(kind=sgl)                 |15000.0 | Distance beam incidence point to scintillator [micron] |
| thetac | real(kind=sgl)            | 0.0| Camera tilt angle w.r.t. horizontal [degrees, down > 0] |
| delta | real(kind=sgl)             | 25.0 | Camera pixel size on scintillator surface [micron] |
| omega | real(kind=sgl)             | 0.0 | Sample tilt axis around RD axis [degrees] |
| xpc | real(kind=sgl)               | 0.0 | Pattern center x in units of pixel size w.r.t. camera center |
| ypc | real(kind=sgl)               | 0.0 | Pattern center y |
| energymin | real(kind=sgl)         | 15.0 | Minimum energy to consider in energy sum [keV] |
| energymax | real(kind=sgl)         | 30.0 | Maximum energy to consider in energy sum [keV] |
| gammavalue | real(kind=sgl)        | 1.0 | Gamma scaling factor for contrast/brightness |
| axisangle | real(kind=sgl)         | 0,0,1,0 | Axis-angle pair to be applied to orientation [n,omega] |
| beamcurrent | real(kind=dbl)       | 150.0 | Beam current [nA] |
| dwelltime | real(kind=dbl)         | 100.0 | Dwell time [micro s] |
| maskpattern | QString              | "n" | Use circular mask on pattern? |
| scalingmode | QString              | "not" | Scaling mode selector |
| eulerconvention | QString          | "tsl" | Euler angle convention |
| outputformat | QString             | "bin" | Outputformat [to be deprecated] |
| spatialaverage | QString           | "n" | Spatial average ? |
| anglefile | QString                | "undefined" | Angular input file |
| masterfile | QString               | "undefined" | EBSD master pattern file |
| energyfile | QString               | "undefined" | Monte Carlo energy file |
| datafile | QString                 | "undefined" | Output file |




*Comment 1:* 

## Required Geometry ##

Not Applicable

## Required Objects ##

Not Applicable

## Created Objects ##

This filter creates a single file in json format that can be used as an input file for the EMsoft **EMEBSD** program.

## License & Copyright ##

Please see the description file distributed with this plugin.

## DREAM3D Mailing Lists ##

If you need more help with a filter, please consider asking your question on the DREAM3D Users mailing list:
https://groups.google.com/forum/?hl=en#!forum/dream3d-users

