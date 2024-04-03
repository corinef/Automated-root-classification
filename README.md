
# Automated-root-classification

This code is for classifying hyperspectral images that were generated using the IMEC VNIR SNAPSCAN camera. The code may be used for other hyperspectral datasets, however to use the data from Spectral Angle Mapper supervised classification, the images will need to be processed in other software if HSI Studio from IMEC is not available. The code is split into four separate scripts, which need to be run one after the other, to save computer memory when using larger number of sample data.

## What to achieve with this code.

This code will generate four separate folders under a new folder 'Data_classification_results' which will contain the K-Means classified data as a classified image (.png) and the binary data (.csv), the data pre-treatments 
## What files are needed (type of data).

Two images in 'Data_files' are provided as an example of how the code works. The raw image data is in ENVI format, containing a header file (.hdr) and raw data file (.raw). Both are needed to extract the raw data. The classified image data from SAM in HSI Studio (IMEC) contains the class image (.png) and the spectra for each class (.csv). 
# Protocol of running code.

### How to install.

Download [Anaconda](https://www.anaconda.com/download)

Download all scripts and extract the files in data_files.zip under a parent folder

Launch Jupyter Notebook

Navigate to parent folder and run each script in sequential order
  - Make sure to input the path to the parent folder under 'folder'

### Dependencies needed.

```py 
pip install -r https://github.com/corinef/Automated-root-classification/blob/main/requirements.txt
```

## Step-by-step guide for processing images.

### K-Means clustering
- Load data files
- Run K-Means
- Save classified images and spectral output

### Spectral data pre-treatment
- Load spectral output from SAM and K-Means
- Plot original spectra
- Run SG smoothing
- Take the average of all root spectra
- Find peaks
- Save selected bands to .csv

### Model training
- Load data files
- Load classified images
- Load selected bands
- Crop datacubes to a 300x300 pixel region and extract the pixel labels from the classification method
- Convert the datacube and pixel labels to a dataframe and reduce the bands (columns) to the selected bands
- Merge all datasets to one dataframe
- Run the classification model on the dataframe

# Interpretations of results.

## Example of image interpretation.
<img src = "https://github.com/corinef/Automated-root-classification/assets/82867617/6784af75-2d54-49eb-ae9f-374399e0d91e" width = "500">
<img src = "https://github.com/corinef/Automated-root-classification/assets/82867617/e6b2c7cb-4273-40cc-a2f6-81aaf5687df2" width = "500">
Results of SAM and KMeans classification

<img src = "https://github.com/corinef/Automated-root-classification/assets/82867617/19fd9f78-9f7e-4411-bc45-abe1116e6714"><br>
Comparison of classification method spectra

![Selected_wavelengths_SAM_rootspectra](https://github.com/corinef/Automated-root-classification/assets/82867617/7b760116-bae3-4ef2-b9b8-c173bb853c43)
![Selected_wavelengths_kmeans_rootspectra](https://github.com/corinef/Automated-root-classification/assets/82867617/f432c7a1-08e6-4aeb-acd6-566406a802f4)
Selected wavelengths from the root spectra second derivative

<img src = "https://github.com/corinef/Automated-root-classification/assets/82867617/154b37b5-72e8-4db5-8955-67f805f30388" width = "500">
<img src = "https://github.com/corinef/Automated-root-classification/assets/82867617/d0a9dcc5-34e5-4a3a-b55f-83d43242f486" width = "500"><br>
Cropped datacube and classified image<br>

<img src = "https://github.com/corinef/Automated-root-classification/assets/82867617/504c8ca7-ac35-4282-a4b0-7addd2ed78a0" width = "500">
<img src = "https://github.com/corinef/Automated-root-classification/assets/82867617/3b941722-3cc9-4760-9c56-c3b2e98d3c23" width = "500">
Random Forest (RF) model confusion matrix and RF predicted image

![Predicted_spectra](https://github.com/corinef/Automated-root-classification/assets/82867617/fc272c61-54fc-4d3a-a4e0-7d9e578c55d9)
Comparison of predicted spectra

## Libraries used.

- Spectral Python (SPy)
  - website: [https://www.spectralpython.net/](https://www.spectralpython.net/)
  - citation: [Boggs, T., March, D., kormang, McGibbney, L. J., Magimel, F., Mason, G., Banman, K., Jouni, M., Kumar, R., The Gitter Badger, Aarnio, T., Wang, W., & kidpixo. (2022)](https://doi.org/10.5281/zenodo.7135091)
  - license: The MIT License (MIT)
- matplotlib:
  - website: [https://matplotlib.org/](https://matplotlib.org/)
  - citation: [J. D. Hunter, "Matplotlib: A 2D Graphics Environment", Computing in Science & Engineering, vol. 9, no. 3, pp. 90-95, 2007.](https://ieeexplore.ieee.org/document/4160265)
  - license: "Matplotlib only uses BSD compatible code, and its license is based on the PSF license."
- 

  
## License

- Added "LICENSE.txt" file with text of Apache Licence.
- Add this as a (``` header ```) to your main.py file:
```
Licensed to the Apache Software Foundation (ASF) under one
or more contributor license agreements.  See the NOTICE file
distributed with this work for additional information
regarding copyright ownership.  The ASF licenses this file
to you under the Apache License, Version 2.0 (the
"License"); you may not use this file except in compliance
with the License.  You may obtain a copy of the License at

  http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing,
software distributed under the License is distributed on an
"AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
KIND, either express or implied.  See the License for the
specific language governing permissions and limitations
under the License.
```
- This project is licensed under the Apache 2.0 License.
- A bit info here: [https://www.apache.org/legal/src-headers.html](https://www.apache.org/legal/src-headers.html)
## Notice

- Added "NOTICE.txt" file with list of who made it and libraries used with their licenses.
- Add this as a (``` header ```) to your main.py file:
