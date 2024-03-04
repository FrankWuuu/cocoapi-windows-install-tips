# Install cocoapi in Windows.

Install the COCO PythonAPI to the Python site-packages

- ## 1. Microsoft Visual C++ 14.0
  First of all, you should make sure that you have install the Microsoft Visual C++ 14.0 or greater.
  If you skip this step, you will mostly meet this error:
  `error: Microsoft Visual C++ 14.0 or greater is required. Get it with "Microsoft C++ Build Tools": https://visualstudio.microsoft.com/visual-cpp-build-tools/`
  - ### step 1
    download the ["Microsoft C++ Build Tools"](https://visualstudio.microsoft.com/visual-cpp-build-tools/)
  - ### step 2
    Make sure the Desktop development with C++ checkbox is checked and install.
    ![image](https://github.com/FrankWuuu/cocoapi-windows-tips/blob/main/cpp_build_tools_install.jpg)
- ## 2. Install pycocotools
  - ### step 1 install dependencies
    ```
    # in your conda environment install the dependencies
    pip install ninja yacs cython matplotlib
    # install torch torchvision 
    ```
  - ### step 2 clone the cocoapi
    ```
    git clone https://github.com/cocodataset/cocoapi.git
    ```
  - ### step 3 modify the setup.py in PythonAPI
    Remove the line `extra_compile_args=['-Wno-cpp', '-Wno-unused-function', '-std=c99']`
    ```
    |--COCOAPI
        |-- MatlabAPI
        |-- PythonAPI
            |-- pycocotools
            |-- setup.py
    ```
  - ### step 4 install pycocotools
    ```
    cd cocoapi/PythonAPI
    python setup.py build_ext install
    ```



## The following is a copy from [cocoapi](https://github.com/cocodataset/cocoapi/tree/master).

COCO API - http://cocodataset.org/

COCO is a large image dataset designed for object detection, segmentation, person keypoints detection, stuff segmentation, and caption generation. This package provides Matlab, Python, and Lua APIs that assists in loading, parsing, and visualizing the annotations in COCO. Please visit http://cocodataset.org/ for more information on COCO, including for the data, paper, and tutorials. The exact format of the annotations is also described on the COCO website. The Matlab and Python APIs are complete, the Lua API provides only basic functionality.

In addition to this API, please download both the COCO images and annotations in order to run the demos and use the API. Both are available on the project website.\
-Please download, unzip, and place the images in: coco/images/\
-Please download and place the annotations in: coco/annotations/\
For substantially more details on the API please see http://cocodataset.org/#download.

After downloading the images and annotations, run the Matlab, Python, or Lua demos for example usage.

To install:\
-For Matlab, add coco/MatlabApi to the Matlab path (OSX/Linux binaries provided)\
-For Python, run "make" under coco/PythonAPI\
-For Lua, run “luarocks make LuaAPI/rocks/coco-scm-1.rockspec” under coco/
