# Heart segmentation
In this project we have to basically segment 3 heart chambers that are left ventricular endocardium, left ventricular epicardium, Left atrium. 
## 1. Dataset Description
- we have used CAMUS DATASET (Cardiac acquisitions for multi-structure ultrasound segmentation).
- Total 500 patient data. Each patient is having 2 chamber and 4 chamber electrocardiography images during systole and diastole.
- Per person is having 4 images so we have total of 200 images which we have to segment.
- We have taken our input images using ultrasound and our input images consist of dimension 549x389x20 which we get from ultrasound and along with that we have ground truth that is single channel image which has different portions of hearts segmented.
- As shown below we have our input image on left hand side and our ground truth image on right side.
- The dataset fromat is nifti images which is used to store the medical images and we have extracted it using nibabel library which is used for thsi purpose.
- Further these images contain many information but we need info for only height and width and channels so for that we use lab.get_fdata function.
  
![cmos_inverter_schematic](./Images/dataset.png)<br>

## 2. Model description

- We mostly use U-net for training our model but here we are using Deeplabv3 model which is little different from unet model and gives better accuracy.
- We first gives input to dataloader as one input image and one single channel ground truth and our custom dataloader returns the same input image and 4 different ground truth images which are segmented into 4 different classes that are background, left ventricular endocardium, left ventricular epicardium, Left atrium. Means our 4 output images will have only single channel and that is the pixels of that particular class rest other are not present.
- so after spiltting our image into 4 channels we are getting output as shown below.

  
![cmos_inverter_schematic](./Images/gt1.png)<br>
![cmos_inverter_schematic](./Images/gt2.png)<br>
![cmos_inverter_schematic](./Images/gt3.png)<br>
![cmos_inverter_schematic](./Images/gt4.png)<br>



-  We have a batch size of 12 for training and batch size of 4 for testing. We also do transfrom in which we just reshape our image into a dimension of 256x256x20 and then convert the image into tensor.
- We spit our traning and testing data in 80:20 ratio i.e 1600 samples for training and 400 samples for testing.
- Also the crucial part here we have done is we are getting 4 output images as ground truth 

