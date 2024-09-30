# FEI-Quanta-400F-HDF5-Data-Extraction
This repository is designed to extract intensity vs wavelength data from HDF5 files that an FEI Quanta 400F SEM outputs.

This is the final and most optimized version of the HDF5 to CSV converter code for the FEI Quanta 400F that I could manage to get. The code is designed to extract and create a CSV file with an identical name to its HDF5 progenitor. This CSV file is the raw data of the intensity wavelength plot in the original HDF5 file.

To run this code successfully, the user would need to only have 3 Python libraries working: os, pandas, h5py. I am also assuming that this code is being run on an internal Python terminal or VS Studio Code.

The os library is the Python library that deals with data paths and file directories, it is the key for the code to navigate to and from your folder when accessing data or uploading the newly created CSVs. There is nothing to install here. The os library is already preinstalled with the installation of Python.

The Pandas library is used for the conversion of the raw metadata into Python interpretable arrays. This library will have to be enabled using the Command window/PowerShell Prompt. Type in the command (cmd). Then type (pip install pandas).

The h5py library is a modified version of the Numpy library that deals specifically with this file format. This library will have to be enabled using the Command window/PowerShell Prompt. Type in the command (cmd). Then type (pip install h5py).

You can check the two downloads working in Python by importing the libraries and then printing their version using the line (print('library_name'._version_)) 
*The word version is surrounded by underscores, I realized that does not pop up on the ReadMe*

The HDF5 file is a more complicated version of a standard Python dictionary meaning that values in the document are essentially stored as key-value pairs. Below I will outline the structure of a generic HDF5 file that the FEI Quanta F400 outputs.

The final file containing everything is named internally as '/'. This is called the root, essentially the container that contains everything else.

In the case of our microscope, there are two groups within the root: Acquisition0 and Acquisition1. Acquisition0 is the TIFF image and Acquisition1 is the CSV-esque data table.

Each of the acquisitions has 4 groups in them: ImageData, PhysicalData, SVIData, StateEnumeration.

ImageData is a group that contains 10 subgroups for the TIFF and 11 subgroups for the CSV-esque data table: 
- Image
- DimensionScaleC (only in the Acquisition1 case)
- DimensionScaleX
- DimensionScaleY
- DimensionScaleZ
- PrimaryGlassMediumInterfacePosition
- SecondaryGlassMediumInterfacePosition
- TOffset
- XOffSet
- YOffset
- ZOffset

These however are mostly all empty in both cases. The only data of interest is the Image array for the TIFF and the DimensionScaleC (wavelength) and Image (intensity) arrays for the intensity-wavelength plots

Physical data is by far the largest group with 30 subgroups in it:
- BackprojectedIlluminationPinholeRadius
- BackprojectedIlluminationPinholeSpacing
- BackprojectedPinholeRadius
- Baseline
- ChannelDescription
- EmissionWavelength
- ExcitationBeamOverfillFactor
- ExcitationPhotonCount
- ExcitationWavelength
- ExtraSettings
- HardwareName
- HardwareVersion
- ImagingDirection
- ImagingDirectionEnumeration
- ImagingDirectionStr
- IntegrationTime
- Magnification
- MicroscopeMode
- MicroscopeModeEnumeration
- MicroscopeModeStr
- MicroscopeType
- MicroscopeTypeEnumeration
- MicroscopeTypeStr
- MirrorPositionBottom
- MirrorPositionTop
- NumericalAperture
- ObjectiveQuality
- RefractiveIndexLensImmersionMedium
- RefractiveIndexSpecimenEmbeddingMedium
- Title

As far as I can tell, this is the group that contains all of our initial conditions.

SVIData is the smallest group by far with only 6 subgroups:
- Company
- FileSpecificationCompatibility
- FileSpecificationVersion
- ImageHistory
- URL
- WriterVersion

This group is just the manufacturer information and other essential information about the make and software on the SEM.

Lastly, we have StateEnumeration which is not a group but instead a 32-bit integer. I have no idea what purpose this serves.
