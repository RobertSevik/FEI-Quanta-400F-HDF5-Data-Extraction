# FEI-Quanta-400F-HDF5-Data-Extraction
This repository is designed to extract intensity vs wavelength data from HDF5 files that an FEI Quanta 400F SEM outputs.

This is the final and most optimized version of the HDF5 to CSV converter code for the FEI Quanta 400F that I could manage to get. The code is designed to extract and create a CSV file with an identical name to its HDF5 progenitor. This CSV file is the raw data of the intensity wavelength plot in the original HDF5 file.

To run this code successfully, the user would need to only have 3 Python libraries working: os, panda, h5py. 

The os library is the Python library that deals with data paths and file directories, it is the key for the code to navigate to and from your folder when accessing data or uploading the newly created CSVs. 

The Panda library is used for the conversion of the raw metadata into Python interpretable arrays. 

The h5py library is a modified version of the Numpy library that deals specifically with this file format. 



The HDF5 file is a more complicated version of a standard Python dictionary meaning that values in the document are essentially stored as key-value pairs. Dictionaries fundamentally have no 
