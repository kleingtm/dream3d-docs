ImageRegistration {#itkimageregistration}
=====

## Group (Subgroup) ##
ImageProcessing (Misc)


## Description ##
Uses itk's rigid translation image registration to calculate slice alignments using the specified image comparison metric and optimizer on the selected array. If apply shifts is selected subpixel shifts well be applied with linear interpolation. More information on comparison metrics and optimizers can be found in itk's documentation: http://www.itk.org/Doxygen/html/RegistrationPage.html

## Optimizer Parameters ##
| Optimizer | Parameter 1 | Suggested Value | Parameter 2 | Suggested Value | Suggested Iterations |
|-----------|-------------|-----------------|-------------|-----------------|----------------------|
| Gradient Descent | Learning Rate | 0.001-5.0 | Not Used | - | 200 |
| Regular Step Gradient Descent | Minimum Step Length | 0.0001-0.01 | Maximum Step Length | 0.1-4.0 | 200-500 |
| LBFGS | Line Search Accuracy | 0.9 | Default Step Length | 1.5 | 1000 |
| Amoeba | Convergence Tolerance | 0.1-0.25 | Function Convergence Tolerance | 0.001 | 200 |
| One Plus One Evolutionary | Initialize Value | 0.01-0.05 | Epsilon | 0.001 | 2000-4000 |


## Parameters ##
| Name             | Type |
|------------------|------|
| Selected Array | String |
| Similarity Metric | String |
| Optimizer | String |
| Optimizer Parameter 1 | Float |
| Optimizer Parameter 2 | Float |
| Maximum Iterations | Float |
| Apply Shifts | Bool |
| Write Alignment Shift File | Bool |
| Alignment File | String |

## Required Arrays ##

| Type | Default Array Name |
|------|--------------------|
| UInt8 | ImageData |


## Created Arrays ##

None




## License & Copyright ##

Please see the description file distributed with this plugin.

## DREAM3D Mailing Lists ##

If you need more help with a filter, please consider asking your question on the DREAM3D Users mailing list:
https://groups.google.com/forum/?hl=en#!forum/dream3d-users




