Import Image Montage {#importimagemontage}
=====

## Group (Subgroup) ##
ProcessModeling (Input)


## Description ##
Imports multiple images for the purpose of montage assembly. These images must be 8 bit greyscale, and have the same X pixel dimensions and the same Y pixel dimensions. Each image is stored in it's on attribute array.

Utilizes the *itkReadImage* filter.

## Parameters ##
Files Source Directory - Where the files you're trying to import 

Origin - Where in space these images you're importing are supposed to come from

Resolution - If you want to change the resolution of the images you're importing


## Created Arrays ##

Data Container - The name of the data container where everything from this filter will be created

Cell Attribute Matrix - The name of the attribute matrix where these images will be stored


## License & Copyright ##

Please see the description file distributed with this plugin.

## DREAM3D Mailing Lists ##

If you need more help with a filter, please consider asking your question on the DREAM3D Users mailing list:
https://groups.google.com/forum/?hl=en#!forum/dream3d-users

