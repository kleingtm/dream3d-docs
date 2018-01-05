Image Co-Registration Simple {#imagecoregistrationsimple}
=============

## Group (Subgroup) ##
ImageProcessing (ImageProcessing)

## Description ##
This **Filter** is for simple rotational image registration. Images registered should be of the same object rotated a certain amount, with minimal translation movement.
Steps for registration are:

1. Bring in images to be registered
2. Get registration transform data using the ITK Registration Framework
3. Modify the moved image using the transform data found
4. Return modified moved image

The usual algorithm used for registration is trademarked so this is a work around until a better alternative is found.

There is a method for a registration that is purely translation focused, but is not fully supported at the moment.

This filter currently uses:



- Transform Type: CenteredRigid2DTransform
- Optimizer Type: RegularStepGradientDesecentOptimizer
- Interpolator Type: LinearInterpolateImageFunction
- Registration Type: ImageRegistrationMethod
- Metric Type: MeanSquaresImageToImageMetric

All from the ITK library

Setting up the optimizer scales seem to have no actual effect on the registration process so that code has been left out.

## Parameters ##
- Origin Image: 
	- The image that remains stationary and is used as a reference to register on to
- Moved Image:
	- The image that needs to be registered (in this case rotated) onto the Origin Image
- Maximum and Minimum Step Length:
	- Values to help the accuracy of the registration
	- Recommended that you start with low values and work your way up from there.

Developers note:
There is a hidden variable called 'Resample' that is true by default. Turning this variable to false will turn off steps 3 and 4.

## Required Objects ##
Two different 2D 8-Bit grayscale images

## Created Objects ##
Registered 8 Bit Image Data

## License & Copyright ##

Please see the description file distributed with this plugin.

## DREAM3D Mailing Lists ##

If you need more help with a filter, please consider asking your question on the DREAM3D Users mailing list:
https://groups.google.com/forum/?hl=en#!forum/dream3d-users