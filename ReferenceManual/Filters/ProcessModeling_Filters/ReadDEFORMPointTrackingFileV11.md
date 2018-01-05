Read DEFORM Point Tracking File (Version 11.1) {#readdeformpointtrackingfilev11}
=====

## Group (Subgroup) ##

ProcessModeling (Input)

## Description ##

This filter reads a select number of fields from a DEFORM v11.1 CSV formatted file. All time steps within the file are read and a new DataContainer with a Vertex Geometry is created for each time step. The following columns are read from the input file. All other columns are ignored:

|  Column Index (Zero Based) | Column Name | Type |
|----------------------------|-------------|------|
| 0 |  Point #  | Int32 |
| 1 | Step #  | Int32 |
| 2 | Dimension  | Int32 |
| 3 | Time  | Float |
| 6 | R/X Coord.  | Float |
| 7 | Z/Y Coord.  | Float |
| 8 |  Eff. Strain | Float |
| 9 | Eff.Strain Rate  | Float |
| 11 | Damage Factor  | Float |
| 12 | Temperature  | Float |
| 20 | X/R Plastic Strain  | Float |
| 21 | Y/Z Plastic Strain  | Float |
| 22 | Z/Theta Plastic Strain  | Float |
| 23 | XY/RZ Plastic Strain  | Float |

There is now an option to import a single Time Step instead of the entire file.

### Note 1 ###

The names of the created AttributeArrays are taken from the actual headers in the input file with some character substitutions (replace '/' with '_') so if the user has changed the header those changes would be reflected in the final DREAM.3D data structure that is created. This also means that any CSV file conforming to the general specification should be able to be imported using this file.

### Note 2 ###

ONLY the indicated columns are imported. NO other columns are imported.

### Note 3 ###
 ONLY the 2D headers are used. The 3D headers are ignored by the filter.

### Example Header ##

Below is an example header


    *
    *
    * Point Tracking Output Data  DEFORM-2D/3D V11.1
    *
    *
    * Each RECORD contains ONE line with following data stored
    *
    *
    * 2D FORMAT:
    * Point #, Step #, Dimension, Time, Stroke-X, Stroke-Y, R/X Coord., Z/Y Coord., Eff. Strain, Eff. Strain Rate, Relative Density, Damage Factor, Temperature, X/R Stress, Y/Z Stress, Z/Theta Stress,  XY/RZ Stress, Mean Stress, Effective Stress, Maximum Principle Stress,X/R Plastic Strain,Y/Z Plastic Strain,Z/Theta Plastic Strain, XY/RZ Plastic Strain, Max prn Plastic strain,X/R Str-rt, Y/Z Str-rt, Z/Theta Str-rt,  XY/RZ Str-rt, Max prn str-rt,Min Principle str-rt, Min Principle stress, Min Principle Strain, Back stress eff, Back str mean, X/R Back Str, Y/Z Back str, Z/Theta Back str, XY/RZ Back str, Max prn back str, Min prn back str, Displacement total, Displacement x, Displacement y, Velocity total, Velocity x, velocity y, Normal pressure, Material Axis, Eff. Elastic strain, Mean Elastic Strain, Max Prn elastic strain,Min prn elastic strain, X/R elastic strain, Y/Z elastic strain, Z/theta elastic strain, XY/RZ elastic strain, Eff. Creep strain, Mean Creep Strain, Max Prn Creep strain, Min prn Creep strain, X/R Creep strain, Y/Z Creep strain, Z/theta Creep strain, XY/RZ Creep strain, Eff. Transform strain, Mean Transform Strain, Max Prn Transform strain,Min prn Transform strain, X/R Transform strain, Y/Z Transform strain, Z/theta Transform strain,XY/RZ Transform strain, Eff. Total strain, Mean Total Strain, Max Prn Total strain,Min prn Total strain, X/R Total strain, Y/Z Total strain, Z/theta Total strain, XY/RZ Total strain, Thermal volumn, Volume tranformation, Toolwear interface temp.,Toolwear sliding velocity, Toolwear interface pressure, Toolwear current depth,toolwear total depth, Effective strain original data, Current Flux total, Current Flux R, current Flux z, Nodal damage, Nodel Eff strain, Nodal Eff stress, Nodal mean stress, Nodal max prn stress, Nodal min prn stress, Nodal stress x, nodal stress y, nodal stress z, nodal stress xy
    * 3D FORMAT:
    * Point #, Step #, Dimension, Time, Stroke-X, Stroke-Y, Stroke-Z, X Coord, Y Coord, Z Coord, Eff. Strain, Eff. Strain Rate, Relative Density, Damage Factor, Temperature, Stress-x, Stress-y, Stress-z, Tau-xy, Tau-yz, Tau-zx, Mean Stress, Effective Stress, Maximum Principle Stress, Inter. Principle Stress, Min Principle Stress, Strain-x, Strain-y, Strain-z, Strain-xy, Strain-yz, Strain-zx, Mean Strain, Maximum Principle Strain, Inter. Principle Strain, Min Principle Strain,Strain Rate-x, Strain Rate-y, Strain Rate-z, Strain Rate-xy, Strain Rate-yz,  Strain Rate-zx, Mean Strain Rate, Max Principle Strain Rate,Inter. Principle Strain Rate, Min Principle Strain Rate, Eff Back Stress, Back Stress -x, Back Stress -y, Back Stress-z,Back Stress-xy,Back Stress-yz,Back Stress-zx,Mean Back stress, Max Principle Back stress, Inter. Principle back stress,Min principle back stress,Disp.-total,Disp.-x,Disp.-y,Disp.-z, Velocity-total, Velocity -x, Velocity-y, Velocity-z,Normal Pressure,original eff strain, elastic strain effective, elastic strain mean,elastic strain max prn,elastic strain inter prn, elastic strain min prn,elastic strain x, elastic strain y, elastic strain z, elastic strain xy, elastic strain yz, elastic strain zx,creep strain effective,creep strain mean,creep strain max prn, creep strain inter prn, creep strain min prn,creep strain x, creep strain y, creep strain z,creep strain xy, creep strain yz, creep strain zx, trans strain effective,trans strain mean,trans strain max prn,trans strain inter prn, trans strain min prn,trans strain x, trans strain y, trans strain z, trans strain xy, trans strain yz, trans strain zx,total strain effective,total strain mean,total strain max prn,total strain inter prn, total strain min prn,total strain x, total strain y, total strain z,total strain xy, total strain yz, total strain zx,thermal volum, volum trans, material axis 1 x, material axis 1 y, material axis 1 z,metarial axis 2 x, material axis 2 y, material axis 2 z,material axis 3 x,  material axis 3 y, material axis 3 z, Velocity Gradient - 1 x, Velocity Gradient - 1 y, Velocity Gradient - 1 z,Velocity Gradient - 2 x, Velocity Gradient - 2 y, Velocity Gradient - 2 z, Velocity Gradient - 3 x, Velocity Gradient - 3 y, Velocity Gradient - 3 z, Deformation Gradient - 1 x, Deformation Gradient - 1 y, Deformation Gradient - 1 z,Deformation Gradient - 2 x, Deformation Gradient - 2 y, Deformation Gradient - 2 z, Deformation Gradient - 3 x, Deformation Gradient - 3 y, Deformation Gradient - 3 z


## Parameters ##

| Name       | Type |
|------------|------|
| Input File | String |
| Import Single Time Step | bool |
| Single Time Step | int32 |


## Required Arrays ##

| Type | Default Array Name | Description | Comment |
|------|--------------------|-------------|---------|
| Int  | SomeName           | ....        | other   |


## Created Arrays ##

| Type | Default Array Name | Description | Comment |
|------|--------------------|-------------|---------|
| Time Step Data Container Name  | DataContainer_X           | where "X" is the timestep index |   |
| Time Series Bundle Name  | TimeSeriesBundle  | The name of the DataContainerBundle |  |


## Authors: ##

BlueQuartz Software.

## License & Copyright ##

Please see the description file distributed with this plugin.

## DREAM3D Mailing Lists ##

If you need more help with a filter, please consider asking your question on the DREAM3D Users mailing list:
https://groups.google.com/forum/?hl=en#!forum/dream3d-users

