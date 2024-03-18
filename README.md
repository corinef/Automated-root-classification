# Automated-root-classification


Table of content

# Description of code logic.
<!-- What this code is for and how it is constructed. -->
This code is for classifying hyperspectral images that were generated using the IMEC VNIR SNAPSCAN camera. The code may be used for other hyperspectral datasets, however to use the data from Spectral Angle Mapper supervised classification, the images will need to be processed in other software if HSI Studio from IMEC is not available. The code is split into four separate scripts, which need to be run one after the other, to save computer memory when using larger number of sample data. 

## What to achieve with this code.
<!-- What results and data format you will get from this code. -->
This code will generate four separate folders under 'Data_classification_results' which will contain the K-Means classified data as a classified image (.png) and the binary data (.csv), the data pre-treatments 

## What files are needed (type of data).
<!-- Preparation and pre-processing needed on files before running it. -->
Two images in 'Data_files' are provided as an example of how the code works. The raw image data is in ENVI format, containing a header file (.hdr) and raw data file (.raw). Both are needed to extract the raw data. The classified image data from SAM in HSI Studio (IMEC) contains the class image (.png) and the spectra for each class (.csv). 

# Protocol of running code.
<!-- If you want even not-so-computer-savy people be able to run your code it would help to prepare very detailed installation manual here. -->
## How to install.
<!-- Installation guide (in this case just copy main.py file (most likelly :) ) -->
Download [Anaconda](https://www.anaconda.com/download)


## Dependecies needed.
<!-- List of libraries and other dependancies needed to make code run properly. -->


## Step-by-step guide for processing images.
<!-- Here you go one-by-one how to ger desired results. -->
### File loading. (<--example name for one chapter)
Iterating thru all files in the folder. One-by-one:
```py
import matplotlib as mpl
for i in range(0,8):
    print(i)
```
Some more text.





### ETC step 2 or 3 or whatever next step.
Some even more text.

# Interpretations of results.
## Example of image interpretation.
![Some result pic](docs/pics/sample_result.JPG "Streamsync Builder screenshot")<br>
Results of SAM and KMeans.







# Libraries used.
Library used in Python code:
- matplotlib:
  - website: [https://matplotlib.org/](https://matplotlib.org/)
  - citation: [J. D. Hunter, "Matplotlib: A 2D Graphics Environment", Computing in Science & Engineering, vol. 9, no. 3, pp. 90-95, 2007.](https://ieeexplore.ieee.org/document/4160265)
  - license: "Matplotlib only uses BSD compatible code, and its license is based on the PSF license."


# License
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

# Notice
- Added "NOTICE.txt" file with list of who made it and libraries used with their licenses.
- Add this as a (``` header ```) to your main.py file:
