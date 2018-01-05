Read DEFORM File {#readdeformfile}
=====

## Group (Subgroup) ##
ProcessModeling (Input)


## Description ##
This filter will read .dat file that represents the connectivity for a Point Tracking file. The files are typically a Quad Mesh representation where the vertices are listed first then the connectivity, then any vertex or cell data. The read will create Cell and Vertex Attribute Matrix as needed based on scanning the file.

## Parameters ##
| Name             | Type |
|------------------|------|
| Feature Array Name | String |

## Required Arrays ##

| Type | Default Array Name | Description | Comment |
|------|--------------------|-------------|---------|
| Int  | SomeName           | ....        | other   |


## Created Arrays ##

| Type | Default Array Name | Description | Comment |
|------|--------------------|-------------|---------|
| Int  | SomeName           | ....        | other   |



## Authors: ##
BlueQuartz Software, LLC


## License & Copyright ##

Please see the description file distributed with this plugin.

## DREAM3D Mailing Lists ##

If you need more help with a filter, please consider asking your question on the DREAM3D Users mailing list:
https://groups.google.com/forum/?hl=en#!forum/dream3d-users

