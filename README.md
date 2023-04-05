# U-Net for Microglia Segmentation

## Environment Set-Up
To set-up the conda environment to run these IPython notebooks, run the following while referring to the requirements.txt file in this repo:
`conda create --name <env> --file requirements.txt`
<br/>
## Annotating Images
Crop images of microglia down to n x n (I usually use 384x384pxl images) and create a trimap mask similar to the following:
![mglia_0158](https://user-images.githubusercontent.com/59164303/230128021-254b9b70-80b9-4629-886f-21158ca1186c.png)
![mask_0158](https://user-images.githubusercontent.com/59164303/230127970-002540eb-3b63-44d8-91a0-820a60398f47.png)
<br/>
<br/>
## Data Augmentation Script
Before running the training script it is best to augment training images. This means alter the images to produce a larger data set for the model to train from. Put original images in an 'orig' folder (or whatever folder you change `orig_img_dir` to) in a folder named 'microglia', with their respective masks in a folder names 'masks' and execute the script `augment_images.ipynb`. The augmentation script will produce a training set of the size 48x original set.
<br/>
## U-Net Training Script
Make sure the u-net script is referring to the newly augmented images in the set-up parameters, change any other parameters necessary (it's important to pay attention to the image size parameter) and run the script. Depending on image size, batch size and number of epochs this may take a few hours (progress should be displayed per epoch if model runs successfully). The resulting model will be saved as microglia_seg_model_0423.h5 unless this is changed.
<br/>
## Segmentation Script
Make sure script is pointing to the latest trained u-net and tweak any other parameters such as directories necessary then run. Script should create new folders containing segmented microglia images and ROI coordinate txt files of segmentations.
<br/>
