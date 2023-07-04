# Facial-Segmentation-For-Style-Transfer-Using-Neural-Networks
MSc Project
# Facial Segmentation For Style Transfer Using Neural Networks
by Peiwen Chi


## Dependencies

* Geometric Warping: [VLFeat](http://www.vlfeat.org/) and [MatConvNet](http://www.vlfeat.org/matconvnet/)
* Texture Rendering: [PyTorch](http://pytorch.org/), [CUDA](https://developer.nvidia.com/cuda-downloads) and [cuDNN](https://developer.nvidia.com/cudnn)

Pre-trained Models:
* Download the [model](https://drive.google.com/uc?id=1PJJQ0KG2JYfJZDkU4ZOePndKJw63d7Yr&export=download) for geometric warping
 ```
 cd geometric_warping
 mkdir model
 ```
* Download the model for texture rendering
 ```
 cd texture_rendering
 python models/download_model.py
 ```

## Usage

### 1. Run geometric style transfer to warp the content image:
- use MATLAB
- put images in the folder "inputs" (I've already put all the pics I show in my project inside the folder)
- the output will save in the folder "save"
- please see my project appendix for more details(screenshots)
- I edited the code

```
%% Read content image and style imagedyt
CONTENT_IMAGE = imread('/Users/peiwen/Desktop/clone/learning-warp-st/geometric_warping/inputs/[--CONTENT_IMAGE]');
STYLE_IMAGE =   imread('/Users/peiwen/Desktop/clone/learning-warp-st/geometric_warping/inputs/[--STYLE_IMAGE]');
```

After warping, empty background regions (if appear) are inpainted with pixels nearby.

### 2. Run texture style transfer to render the warped image:
- use python 3
- GPU = c (beware that some mac cant process GPU, hence I changed GUP=0 into GPU = c)
- put images in the folder "inputs" (I've already put all the pics I show in my project inside the folder)
- the output will be in the "texture_rendering" folder
- please see my project appendix for more details(screenshots)
- I edited the code

```
cd texture_rendering

./multi_scale_st.sh /Users/peiwen/Desktop/clone/learning-warp-st/texture_rendering/examples/inputs/ [--STYLE_IMAGE] /Users/peiwen/Desktop/clone/learning-warp-st/texture_rendering/examples/inputs/ [--CONTENT_IMAGE]
```
