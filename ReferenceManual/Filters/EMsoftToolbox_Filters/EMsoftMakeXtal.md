 EMsoftMakeXtal {#emsoftmakextal}
=============

## Group (Subgroup) ##
EMsoftToolbox (EMsoftToolbox)

## Description ##
This EMsoftMakeXtal filter asks the user for all the crystallographic parameters of a unit cell and subsequently generates an HDF5 file with extension .xtal inside the EMdatafolder/XtalFolder.  This file then serves as one of the input files for all the programs in the EMsoft suite.

## Parameters ##
| Name | Type | Default Value | Description |
|------|------|------|------|
| CrystalSystem| QString | "Cubic" | Select the crystal system from the pulldown menu|
| Lattice Parameters | Float | 0.4 | Lattice parameters in nanometers and degrees|
| Space Group Number | Integer | 0 | Space group number from the table below |
| Space Group Setting | Integer | 1 or 2 | Origin setting for space group |
| Asymmetric Unit | Floats | 0 | Table to enter atomic number, fractional coordinates, occupation factor and Debye-Waller factor|
| Output File Name | QString | | Output file name (will receive .xtal extension) |

## Detailed Descriptions ##
### Crystal Systems ###
There are seven crystal systems: cubic, tetragonal, orthorhombic, hexagonal, trigonal, monoclinic and triclinic (anorthic). For the trigonal case, there are two possible choices for the unit cell: hexagonal and rhombohedral; these are labeled as Trigonal/H and Trigonal/R in the pulldown menu.  The filter will automatically display the required fields for the lattice parameters; any parameters not shown in the list will be automatically set depending on the selected crystal system.

### Lattice Parameters ###
All lattice parameters are to be entered in nanometers, and angles are in degrees.

### Space Group Number ###
There are 230 3D crystallographic space groups.  The EMsoft package uses the conventions of the International Tables for Crystallography (Volume A) for the numbering and notation scheme.  All space groups are listed in the tables at the bottom of this help page, by crystal system and space group number; an underscore in the space group symbol indicates a subscript, a minus sign is an overbar on the next character. When you enter a space group number, the filter will verify that it falls in the correct range for the selected crystal system.  If you select the Trigonal/H setting of the trigonal system, then, for practical reasons, the last table below should be used, with space group numbers larger than 230; this is the only deviation from the International Tables.  Finally, some space groups have two origin settings, which can be selected using the pulldown menu. By default, this setting will be 1 ("first setting"); if a space group has only one setting, then selecting "2" will have no effect.  The user is referred to the International Tables for Crystallography (volume A) for details on the origin selections.

### Asymmetric Unit ###
The EMsoft package "knows" all space groups and their symmetry elements, so that it is only necessary to enter the atom coordinates inside the so-called **asymmetric unit**. The Table requires six entries for each atom in the asymmetric unit: the atomic number, the (x,y,z) fractional coordinates (note that all coordinates will be reduced to the range [0,1] when they are written to the output file), the site occupation factor (a number between 0 and 1), and the Debye-Waller factor (in nm^2 ).  This last number depends strongly on temperature and is not always easily found in the literature; for elemental solids, the user can refer to the following paper: L.-M. Peng, G. Ren, S.L. Dudarev, and M.J. Whelan, *Debye-Waller Factors and Absorptive Scattering Factors of Elemental Crystals*, Acta Cryst. A **52**, 456-470, 1996.  If the Debye-Waller factor is not known, then a safe value would be 0.004; note that a 0.0 value is not allowed.  The user can add as many atoms as needed by clicking the green + button below the table.  

### Crystal Structure File Name ###
The final entry is the crystal structure file name, which will automatically receive the extension ".xtal" and will be placed in the EMdatafolder/XtalFolder.  The file is in HDF5 format, and the filter will detect if a file with that name already exists; the user will not be able to overwrite an existing file.


## Required Geometry ##

Not Applicable

## Required Objects ##

Not Applicable

## Created Objects ##

This filter creates a single file in HDF5 format that can be used as an input file for all EMsoft programs.  This file will automatically be placed in the EMdatafolder/XtalFolder.

## License & Copyright ##

Please see the description file distributed with this plugin.

## Funding Acknowledgment ##

This filter was developed with financial support from contract AFRL FA8650-10-D-5210, Task Order 0034.

## DREAM3D Mailing Lists ##

If you need more help with a filter, please consider asking your question on the DREAM3D Users mailing list:
https://groups.google.com/forum/?hl=en#!forum/dream3d-users

# Space Group Tables #
Space groups with two origin settings are listed in bold face in the tables below.

## Triclinic (Anorthic) ##

| Number/symbol | Number/symbol |
|------|------|
| 1 / P1       | 2 / P-1      |

## Monoclinic ##
Monoclinic space groups are encoded with unique axis b, cell choice 1.

| Number/symbol | Number/symbol | Number/symbol | Number/symbol |
|------|------|------|------|
| 3 / P2        | 4 / P2_1       |  5 / C2        |  6 / Pm       |
| 7 / Pc        |  8 / Cm        |  9 / Cc        |  10 / P2/m     |
| 11 / P2_1/m     | 12 / C2/m      |  13 / P2/c      |  14 / P2_1/c    |
| 15 / C2/c      | | | |


## Orthorhombic ##
| Number/symbol | Number/symbol | Number/symbol | Number/symbol |
|------|------|------|------|
| 16 / P222    |  17 / P222_1   | 18 / P2_12_12  | 19 / P2_12_12_1|
| 20 / C222_1   | 21 / C222    | 22 / F222    |  23 / I222   |
| 24 / I2_12_12_1 | 25 / Pmm2    | 26 / Pmc2_1   | 27 / Pcc2   |
| 28 / Pma2    |  29 / Pca2_1   | 30 / Pnc2    |  31 / Pmn2_1  |
| 32 / Pba2    |  33 / Pna2_1   |  34 /Pnn2    |  35 / Cmm2   |
| 36 / Cmc2_1   |  37 / Ccc2    | 38 / Amm2    |  39 / Abm2   |
| 40 / Ama2    |  41 / Aba2    |  42 / Fmm2    |  43 / Fdd2   |
| 44 / Imm2    |  45 / Iba2    |  46 / Ima2    |  47 / Pmmm   |
| **48 / Pnnn**    |  49 / Pccm    |  **50 / Pban**    |  51 / Pmma   |
| 52 / Pnna    |  53 / Pmna    |  54 / Pcca    |  55 / Pbam   |
| 56 / Pccn    |  57 / Pbcm    |  58 / Pnnm    |  **59 / Pmmn**   |
| 60 / Pbcn    |  61 / Pbca    |  62 / Pnma    |  63 / Cmcm   |
| 64 / Cmca    |  65 / Cmmm    |  66 / Cccm    |  67 / Cmma   |
| **68 / Ccca**    |  69 / Fmmm    |  **70 / Fddd**    |  71 / Immm   |
| 72 / Ibam    |  73 / Ibca    |  74 / Imma    |  |


## Tetragonal ##
| Number/symbol | Number/symbol | Number/symbol | Number/symbol |
|------|------|------|------|
| 75 / P4        | 76 / P4_1       | 77 / P4_2       | 78 / P4_3      |
| 79 / I4        | 80 / I4_1       | 81 / P-4       |  82 / I-4      |
| 83 / P4/m      | 84 / P4_2/m     | **85 / P4/n**      |  **86 / P4_2/n**    |
| 87 / I4/m      | **88 / I4_1/a**     | 89 / P422    |  90 / P42_12  |
| 91 / P4_122   |  92 / P4_12_12  |  93 / P4_222   |  94 / P4_22_12 |
| 95 / P4_322   |  96 / P4_32_12  |  97 / I422    |  98 / I4_122  |
| 99 / P4mm    |  100 / P4bm    |  101 / P4_2cm   |  102 / P4_2nm  |
| 103 / P4cc    |  104 / P4nc    |  105 / P4_2mc   |  106 / P4_2bc  |
| 107 / I4mm    |  108 / I4cm    |  109 / I4_1md   |  110 / I4_1cd  |
| 111 / P-42m   |  112 / P-42c   |  113 / P-42_1m  |  114 / P-42_1c |
| 115 / P-4m2   |  116 / P-4c2   |  117 / P-4b2   |  118 / P-4n2  |
| 119 / I-4m2   |  120 / I-4c2   |  121 / I-42m   |  122 / I-42d  |
| 123 / P4/mmm  |  124 / P4/mcc  |  **125 / P4/nbm**  |  **126 / P4/nnc** |
| 127 / P4/mbm  |  128 / P4/mnc  |  **129 / P4/nmm**  |  **130 / P4/ncc** |
| 131 / P4_2/mmc | 132 / P4_2/mcm |  **133 / P4_2/nbc** |  **134 / P4_2/nnm**|
| 135  /P4_2/mbc | 136 / P4_2/mnm |  **137 / P4_2/nmc** |  **138 / P4_2/ncm**|
| 139 / I4/mmm  |  140 / I4/mcm  |  **141 / I4_1/amd** |  **142 / I4_1/acd**| 


## Trigonal/H ##
| Number/symbol | Number/symbol | Number/symbol | Number/symbol |
|------|------|------|------|
| 143 / P3        | 144 / P3_1       | 145 /  P32       | 146 / R3       |
| 147 / P-3       | 148 / R-3       |  149 / P312    |  150 / P321   |
| 151 / P3_112   |  152 / P3_121   |  153 / P3_212   |  154 / P3_221  |
| 155 / R32      |  156 / P3m1    |  157 / P31m    |  158 / P3c1   |
| 159 / P31c    |  160 / R3m      |  161 / R3c      |  162 / P-31m  |
| 163 / P-31c   |  164 / P-3m1   |  165 / P-3c1   |  166 / R-3m    |
| 167 / R-3c     | | | |


## Hexagonal ##
| Number/symbol | Number/symbol | Number/symbol | Number/symbol |
|------|------|------|------|
| 168 / P6        | 169 /  P6_1    | 170 / P6_5     | 171 / P6_2      |
| 172 / P6_4       | 173 / P6_3    | 174 / P-6      | 175 / P6/m     |
| 176 / P6_3/m     | 177 / P622    | 178 / P6_122   | 179 / P6_522  |
| 180 / P6_222   |  181 / P6_422   | 182 / P6_322   | 183 / P6mm   |
| 184 / P6cc    |  185 / P6_3cm   |  186 / P6_3mc   | 187 / P-6m2  |
| 188 / P-6c2   |  189 / P-62m   |   190 / P-62c    | 191 / P6/mmm |
| 192 / P6/mcc  |  193 / P6_3/mcm |  194 / P6_3/mmc | |



## Cubic ##
| Number/symbol | Number/symbol | Number/symbol | Number/symbol |
|------|------|------|------|
| 195 / P23     | 196 / F23     | 197 / I23      |  198 / P2_13    |
| 199 / I2_13   | 200 / Pm3     | **201 / Pn3**      |  202 / Fm3     |
| **203 / Fd3**     | 204 / Im3     | 205 / Pa3      |  206 / Ia3     |
| 207 / P432    | 208 / P4_232  | 209 / F432    |   210 / F4_132  |
| 211 / I432    | 212 / P4_332  | 213 / P4_132   |  214 / I4_132  |
| 215 / P-43m   | 216 / F-43m   | 217 / I-43m   |   218 / P-43n  |
| 219 / F-43c   | 220 / I-43d   | 221 / Pm-3m    |  **222 / Pn3n**   |
| 223 / Pm3n    | **224 / Pn3m**    | 225 / Fm-3m    |  226 / Fm3c   |
| **227 / Fd-3m**   | **228 / Fd3c**    | 229 / Im-3m    |  230 / Ia3d   | 

## Trigonal/R ##
The original space group number is shown in parentheses; the first number if the one used by EMsoft to distinguish the rhombohedral space group setting from the hexagonal one.

| Number/symbol | Number/symbol | Number/symbol | Number/symbol |
|------|------|------|------|
| 231 / R3   (146)| 232 / R-3 (148) | 233 / R32 (155) | 234 /  R3m (160)|
| 237 / R3c (161) | 238 / R-3m (166) | 237 / R-3c (167)| |


