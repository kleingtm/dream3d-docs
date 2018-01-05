Find Average Sines For C-Axis Patches {#findavgsinesforcaxispatches}
======

## Group (Subgroup) ##
Unsupported (ImageProcessing)

## Description ##
This Filter determines the average c-axis location of each **Feature** by the following algorithm:

1. Gather all **Cells** that belong to the **Feature**
2. Determine the location of the c-axis in the sample *reference frame* for the rotated quaternions for all **Cells**.

3.  average the locations and store as the average for the **Feature**.

Note: This filter will only work properly for *Hexagonal* materials.  The filter does not apply any symmetry operators because there is only one c-axis (<001>) in *Hexagonal* materials and thus all symmetry operators will leave the c-axis in the same position in the sample *reference frame*.  However, in *Cubic* materials, for example, the {100} family of directions are all equivalent and the <001> direction will change location in the sample *reference frame* when symmetry operators are applied. 

 

## Parameters ##
None

## Required Arrays ##

| Type | Default Name | Description | Comment |
|------|--------------|-------------|---------|
| UInt8 | VectorData | | |
| Float | FitQuality | | |
| 4x Float | Quats | Four (4) values (floats) that specify the orientation of the **Cell** in quaternion representation| |

## Authors ##

**Copyright:** 2012 Michael A. Groeber (AFRL),2012 Michael A. Jackson (BlueQuartz Software)

**Contact Info:** dream3d@bluequartz.net

**Version:** 1.0.0

**License:**  See the License.txt file that came with DREAM3D.




See a bug? Does this documentation need updated with a citation? Send comments, corrections and additions to [The DREAM3D development team](mailto:dream3d@bluequartz.net?subject=Documentation%20Correction)

