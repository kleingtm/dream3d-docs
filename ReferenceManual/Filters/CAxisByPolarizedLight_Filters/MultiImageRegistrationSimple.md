MultiImage Registration Simple {#multiimageregistrationsimple}
=============

## Group (Subgroup) ##
ImageProcessing (ImageProcessing)

## Description ##
This **Filter** utilizes the ImageCoRegistrationSimple filter to register multiple images onto one image. 
The first image on the stack will be considered the Origin image which every other image will be registered upon.


***How each mode works***
----------

**Consecutive (Stack) Registration**

- Start at the top of the stack
- Compare (register) the top image and the image beneath it to get the Transform Data
- Use the Transform Data to modify the above image
- Add modified image to a 'Modified' vector
- Use the Transform Data to modify every image in the 'Modified' vector
- Repeat until you get to the bottom of the stack

*The very basic registration. Due to resampling each image multiple times, data might be lost. Transforms each image down to the one beneath it. More accurate, longer run-time.*

----------

**Sum Registration**

- Start at the bottom of the stack (at the Origin image)
- Move up the stack comparing (registering) images and storing them in a vector of transform data
- Make an empty transform data variable
- Go back to the bottom of the stack, and modify each image by adding their transform data to the empty transform data variable
- Repeat until you reach the top of the stack

*A slightly better version of the Consecutive (Stack) Registration. Only resamples each image once, but adds up the rotation data as you move up the stack. Less blurry images, slightly faster run-time, less accurate.*


----------
**Single Multiplicative Registration**

- Start at the bottom of the stack
- Compare (register) the Origin image to the image above it to get the transform data (Lets call this Data 'OData')
- Move up the stack comparing (registering) images and storing them in a vector of transform data (Lets call this Data 'VData')
- Go back to the bottom of the stack, and modify each image using the rotation data from the OData and the center of rotation & translation data from VData
- Repeat until you reach the top of the stack

*Good for registrations of images that are all rotated by a certain amount every time. Has an average run-time, can be more or less accurate depending on human error.*

----------

**Fast Single Multiplicative Registration**

- Start at the bottom of the stack
- Compare (register) the Origin image to the image above it to get the transform data (Lets call this Data 'OData')
- Start back at the bottom of the stack, and modify each image using the rotation data from the OData
- Repeat until you reach the top of the stack

*Good for fast registrations of images that are all rotated by a certain amount every time, with minimal translations. Only does one real registration before resampling everything else. Has a fast run-time, can be more or less accurate depending on human error.*


## Parameters ##
- Attribute Array Images
- Maximum and Minimum Step Length:
	- Values to help the accuracy of the registration
	- Recommended that you start with low values and work your way up from there.


## Required Objects ##
8-Bit Grayscale images, all rotated the same amount of degrees at various intervals. (IE: 00 10 20 30 40 --- 10 degree intervals)

## Created Objects ##
Registered Images named: [ImageName]Registered

## Developer Notes ##
The usual algorithm used for registration is trademarked so this is a work around until a better alternative is found.

There is a method for a registration that is purely translation focused, but is currently if'd out as it is not fully complete.

This filter currently uses ITKRigid2DTransform as it's transform type with a MeanSquaresImageToImage metric. It uses ITK's RegularStepGradientDescentOptimizer.



## License & Copyright ##

Please see the description file distributed with this plugin.

## DREAM3D Mailing Lists ##

If you need more help with a filter, please consider asking your question on the DREAM3D Users mailing list:
https://groups.google.com/forum/?hl=en#!forum/dream3d-users