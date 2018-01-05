 EMsoftEMEBSD {#emsoftemebsd}
=============

## Group (Subgroup) ##
EMsoftToolbox (EMsoftToolbox)

## Description ##
This EMsoftEMEBSD filter asks the user for all the parameters needed by the **EMEBSD** program and subsequently generates a json file that can be read by this program.

## Parameters ##
| Name | Type | Default Value | Description |
|------|------|------|------|
| XtalName| QString | "undefined" | Crystal structure file name |

        integer(kind=irg)       :: numsx :: Number of camera pixels along x :: 640
        integer(kind=irg)       :: numsy :: Number of camera pixels along y :: 480
        integer(kind=irg)       :: binning :: Binning factor [1, 2, 4, or 8]:: 1
        integer(kind=irg)       :: nthreads :: Number of OpenMP threads :: 1
        integer(kind=irg)       :: energyaverage :: Use energy averaged background ? (faster) :: 0
        real(kind=sgl)          :: L    :: Distance beam incidence point to scintillator [micron] :: 15000.0
        real(kind=sgl)          :: thetac  :: Camera tilt angle w.r.t. horizontal [degrees, down > 0] :: 0.0
        real(kind=sgl)          :: delta  :: Camera pixel size on scintillator surface [micron] :: 25.0
        real(kind=sgl)          :: omega  :: Sample tilt axis around RD axis [degrees] :: 0.0
        real(kind=sgl)          :: xpc    :: Pattern center x in units of pixel size w.r.t. camera center :: 0.0
        real(kind=sgl)          :: ypc    :: Pattern center y :: 0.0
        real(kind=sgl)          :: energymin :: Minimum energy to consider in energy sum [keV] :: 15.0
        real(kind=sgl)          :: energymax :: Maximum energy to consider in energy sum [keV] :: 30.0
        real(kind=sgl)          :: gammavalue :: Gamma scaling factor for contrast/brightness :: 1.0 
        real(kind=sgl)          :: axisangle(4) :: Axis-angle pair to be applied to orientation [n,omega] :: 0.0,0.0,1.0,0.0
        real(kind=dbl)          :: beamcurrent :: Beam current [nA] :: 150.0
        real(kind=dbl)          :: dwelltime :: Dwell time [micro s] :: 100.0
        character(1)            :: maskpattern :: Use circular mask on pattern? :: n
        character(3)            :: scalingmode :: Scaling mode selector :: not
        character(3)            :: eulerconvention :: Euler angle convention :: tsl
        character(3)            :: outputformat :: Outputformat [to be deprecated] :: bin
        character(1)            :: spatialaverage :: Spatial average ? :: n
        character(fnlen)        :: anglefile :: Angular input file :: undefined
        character(fnlen)        :: masterfile :: EBSD master pattern file :: undefined
        character(fnlen)        :: energyfile :: Monte Carlo energy file :: undefined
        character(fnlen)        :: datafile :: Output file :: undefined




*Comment 1:* 

## Required Geometry ##

Not Applicable

## Required Objects ##

Not Applicable

## Created Objects ##

This filter creates a single file in json format that can be used as an input file for the EMsoft xxx program.

## License & Copyright ##

Please see the description file distributed with this plugin.

## DREAM3D Mailing Lists ##

If you need more help with a filter, please consider asking your question on the DREAM3D Users mailing list:
https://groups.google.com/forum/?hl=en#!forum/dream3d-users

