# Heart segmentation
In this project we have to basically segment 3 heart chambers that are left ventricular endocardium, left ventricular epicardium, Left atrium. 
## 1. Dataset Description
- we have used CAMUS DATASET (Cardiac acquisitions for multi-structure ultrasound segmentation).
- Total 500 patient data. Each patient is having 2 chamber and 4 chamber electrocardiography images during systole and diastole.

- We have taken our input images using ultrasound and our input images consist of dimension 549x389x20 which we get from ultrasound and along with that we have ground truth that is single channel image which has different portions of hearts segmented.

![cmos_inverter_schematic](./Images/dataset.png)<br>

Our input images are of shape 549x389x20 where 20 represent different channels which has medical information present in it.
