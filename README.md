# FEI-Quanta-400F-HDF5-Data-Extraction
This repository is designed to extract intensity vs wavelength data from HDF5 files that an FEI Quanta 400F SEM outputs.

This is the final and most optimized version of the HDF5 to CSV converter code for the FEI Quanta 400F that I could manage to get. The code is designed to extract and create a CSV file with an identical name to its HDF5 progenitor. This CSV file is the raw data of the intensity wavelength plot in the original HDF5 file.

To run this code successfully, the user would need to only have 3 Python libraries working: os, pandas, h5py. I am also assuming that this code is being run on an internal Python terminal or VS Studio Code.

The os library is the Python library that deals with data paths and file directories, it is the key for the code to navigate to and from your folder when accessing data or uploading the newly created CSVs. There is nothing to install here. The os library is already preinstalled with the installation of Python.

The Pandas library is used for the conversion of the raw metadata into Python interpretable arrays. This library will have to be enabled using the Command window/PowerShell Prompt and type in the command (cmd). Then type (pip install pandas).

The h5py library is a modified version of the Numpy library that deals specifically with this file format. This library will have to be enabled using the Command window/PowerShell Prompt and type in the command (cmd). Then type (pip install h5py).

You can check the two downloads working in Python by importing the libraries and then printing their version using the line (print('library_name'._version_))


The HDF5 file is a more complicated version of a standard Python dictionary meaning that values in the document are essentially stored as key-value pairs. Dictionaries fundamentally have no 
