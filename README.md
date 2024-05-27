
# Automated-root-classification

## Description
This code is for classifying hyperspectral images that were generated using the IMEC VNIR SNAPSCAN camera. The code may be used for other hyperspectral datasets, however to use the data from Spectral Angle Mapper supervised classification, the images will need to be processed in other software if HSI Studio from IMEC is not available. The code is split into four separate scripts, which need to be run one after the other, to save computer memory when using larger number of sample data. <br>

This code will generate the results under a new folder 'Data_classification_results'. These will contains:<br>
(1) The K-Means classified data as a classified image and the labelled pixel matrix <br>
(2) The data pre-treatments comparing the selection spectra, selected bands, and the selected wavelengths plotted over the second derivative of the root spectra<br>
(3) The generation of the classification model, with the model training confusion matrix, and classification report<br>
(4) The model predicted images, labelled pixel matrices, confusion matrics, accuracy reports, comparison of the predicted spectra, and PLS-DA plots, and estimated biomass<br>

## Files needed
Two images in [Data_files](Data_files.md) are provided as an example of how the code works. The raw image data is in ENVI format, containing a header file (.hdr) and raw data file (.raw). Both are needed to extract the raw data. The classified image data from SAM in HSI Studio (IMEC) contains the class image (.png) and the spectra for each class (.csv). 

# Protocol of running code.

### How to install
### Prerequisites
- [Anaconda](https://www.anaconda.com/download)

### Dependencies needed
```py 
pip install -r https://github.com/corinef/Automated-root-classification/blob/main/requirements.txt
```

## Step-by-step guide for processing images

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

### Model prediction
- 

## Example of image interpretation.
<img src = "https://github.com/corinef/Automated-root-classification/assets/82867617/6784af75-2d54-49eb-ae9f-374399e0d91e" width = "400">
<img src = "https://github.com/corinef/Automated-root-classification/assets/82867617/e6b2c7cb-4273-40cc-a2f6-81aaf5687df2" width = "400"><br>

**Results of SAM (left) and K-Means (right) classification**

<img src = "https://github.com/corinef/Automated-root-classification/assets/82867617/7d22336d-8959-42fa-b425-536b0a67f9db"><br>

**Comparison of classification method spectra**

![Selected_wavelengths_SAM_rootspectra](https://github.com/corinef/Automated-root-classification/assets/82867617/6b123e38-7e23-4e96-b7d3-1a926312dfaf)
![Selected_wavelengths_kmans_rootspectra](https://github.com/corinef/Automated-root-classification/assets/82867617/159a9158-4002-4ab1-944c-2afd12162f91)

**Selected wavelengths from the second derivative of the root spectra**

<img src = "https://github.com/corinef/Automated-root-classification/assets/82867617/a4f648a4-f4b2-4d44-a19f-cd26db86a852" width = "300">
<img src = "https://github.com/corinef/Automated-root-classification/assets/82867617/2f3ba667-f64c-40f4-ab30-1ac828f865b0" width = "300">
<img src = "https://github.com/corinef/Automated-root-classification/assets/82867617/e67938c2-605b-4c6f-aab9-e4d955a152a3" width = "300"><br>

**Cropped region of datacube (left), SAM classified image (middle), K-Means classified image (right)**

<img src = "https://github.com/corinef/Automated-root-classification/assets/82867617/8a69f13f-8475-4a55-8f41-4acc7f07a7f9" width = "500">
<img src = "https://github.com/corinef/Automated-root-classification/assets/82867617/3c3dfbf7-d7f7-4b2b-b519-ed6ab7e8e841" width = "500">

**Random Forest (RF) model confusion matrix, SAM (left), K-Means (right)**

<img src = "https://github.com/corinef/Automated-root-classification/assets/82867617/ca46aa83-8dd1-42bc-9ff0-2ce0dca34212" width = "500">
<img src = "https://github.com/corinef/Automated-root-classification/assets/82867617/37cf849a-b540-452e-94ae-ad6a09f43f30" width = "500">

**RF predicted image from SAM (left), K-Means (right)**

![Accuracy_reports](https://github.com/corinef/Automated-root-classification/assets/82867617/a8d8ba61-1ca0-4224-80b0-5ccd378895b9)

**Accuracy reports**

![Predicted_spectra](https://github.com/corinef/Automated-root-classification/assets/82867617/4a105369-0e4d-4c92-a009-f9d41ed28f9c)

**Comparison of predicted spectra**

![Biomass](https://github.com/corinef/Automated-root-classification/assets/82867617/7549c3c1-032b-42b9-8f8b-42323edad765)

**Estimated biomass**


## Libraries used
- Spectral Python (SPy)
  - website: [https://www.spectralpython.net/](https://www.spectralpython.net/)
  - citation: [Boggs, T., March, D., kormang, McGibbney, L. J., Magimel, F., Mason, G., Banman, K., Jouni, M., Kumar, R., The Gitter Badger, Aarnio, T., Wang, W., & kidpixo. (2022)](https://doi.org/10.5281/zenodo.7135091)
  - license: "The MIT License (MIT)"
- Pandas:
  - website:[https://pandas.pydata.org/](https://pandas.pydata.org/)
  - citation: [The Pandas Development Team. (2022). pandas-dev/pandas: Pandas (1.4.2).](https://doi.org/10.5281/zenodo.10426137)
  - license:  "Pandas is distributed under the modified (3-clause) BSD License"
- matplotlib:
  - website: [https://matplotlib.org/](https://matplotlib.org/)
  - citation: [J. D. Hunter, "Matplotlib: A 2D Graphics Environment", Computing in Science & Engineering, vol. 9, no. 3, pp. 90-95, 2007.](https://ieeexplore.ieee.org/document/4160265)
  - license: "Matplotlib only uses BSD compatible code, and its license is based on the PSF license."
- seaborn:
  - website: [https://seaborn.pydata.org/](https://seaborn.pydata.org/)
  - citation:
  - license:  "The MIT License (MIT)" 
- SciPy :
  - website:[https://scipy.org/](https://scipy.org/)
  - citation: [Virtanen, P., Gommers, R., Oliphant, T. E., Haberland, M., Reddy, T., Cournapeau, D., Burovski, E., Peterson, P., Weckesser, W., Bright, J., van der Walt, S. J., Brett, M., Wilson, J., Millman, K. J., Mayorov, N., Nelson, A. R. J., Jones, E., Kern, R., Larson, E., . . . SciPy, C. (2020). Author Correction: SciPy 1.0: fundamental algorithms for scientific computing in Python. Nature Methods, 17(3), 352-352.](https://doi.org/10.1038/s41592-020-0772-5 )
  - license:  "SciPy is distributed under the modified (3-clause) BSD license."
- Pillow (PIL Fork):
  - website:[https://pypi.org/project/pillow/](https://pypi.org/project/pillow/)
  - citation: [Clark, A. (2015). Pillow (PIL Fork) Documentation. (9.0.1). readthedocs.](https://buildmedia.readthedocs.org/media/pdf/pillow/latest/pillow.pdf )
  - license:  "Pillow is licensed under the open source HPND License"
- Scikit-learn:
  - website:[https://scikit-learn.org/stable/index.html](https://scikit-learn.org/stable/index.html)
  - citation: [Pedregosa, F., Varoquaux, G., Gramfort, A., Michel, V., Thirion, B., Grisel, O., Blondel, M., Prettenhofer, P., Weiss, R., Dubourg, V., Vanderplas, J., Passos, A., Cournapeau, D., Brucher, M., Perrot, M., & Duchesnay, É. (2011). Scikit-learn: Machine Learning in Python. Journal of Machine Learning Research, 12, 2825–2830.](https://scikit-learn.org/stable/index.html )
  - license:  "Scikit-learn is distributed under the modified (3-clause) BSD license."
  
## License
- This project is licensed under the Apache 2.0 License.
