# Radiological Society of North America (RSNA) Lumbar Degeneration Classification Competition

## Overview
The lumbar reigion of the spine is a major cause of pain and disability worldwide, infact it is the leading cause of disability with around 600 million people suffering from the varying conditions arising from degeneration in the lumbar discs. The goal of the competition is to use deep learning methods to accurately and reliably predict whether the patient has a condition and the level of severity of said condition. 

The RSNA provides a dataset of 1,975 studies (patients) MRI scans with three differing types: Sagittal T1, Sagittal T2/STIR and Axial T2.

A sagittal T1 image is taken from the sagittal plane of the body (side on) and T1 indicates that fat is more visible in the scan, due to the shorter times between pulses in the MRI scans.

![ST1_0000_0000](https://github.com/user-attachments/assets/e80b2c67-f68e-47ea-b138-f28575ba272f)
![ST1_0021_0000](https://github.com/user-attachments/assets/46cbd5d5-f174-45d8-a2a8-26fdbd1d0049)
![ST1_0036_0000](https://github.com/user-attachments/assets/dadfc368-d26d-492e-aa53-45760f41eb85)
![ST1_0029_0000](https://github.com/user-attachments/assets/49b0b2ac-2460-49b6-98ba-1649f8e2f54a)


A sagittal T2/STIR image is also taken from the sagittal plane, the T2/STIR indicates that water is more visible in the scan, hence revealing the spinal cord more - due to the longer times between pulses in the MRI scans.

![ST2_0265_0000](https://github.com/user-attachments/assets/29d57c7f-296e-455c-ad29-d6dc5c78c346)
![ST2_0272_0000](https://github.com/user-attachments/assets/d9c3462f-ee60-4839-a9fc-b79a1926fdd5)
![ST2_0318_0000](https://github.com/user-attachments/assets/6810f71c-9665-40a7-8aff-c1ee44ab67df)
![ST2_0346_0000](https://github.com/user-attachments/assets/57b928c2-5022-4846-8c75-59041c0bb5f3)


An axial T2 image is taken from the axial plane (i.e top down of the body), the T2 again indicating that water is more visible than fat in the scan.

![AX2_0003_0000](https://github.com/user-attachments/assets/babb2988-232f-4ffb-be5b-bbc8bef63933)
![AX2_0023_0000](https://github.com/user-attachments/assets/3411a878-4228-43cc-ad1b-befefcd27385)
![AX2_0028_0000](https://github.com/user-attachments/assets/421b8866-3755-4d4d-a7d0-a6b4b5247681)
![AX2_0067_0000](https://github.com/user-attachments/assets/80f1ec3d-68e3-41e4-aa41-34ec2faa9368)

Two files are provided with the respect to these images. One contains coordinates of the degenerative disc on a specific MRI scan, the other defines the name and severity of the patient's lumbar conditions along all 50+ scans of the study. Here's an example of a few MRI scans of a patient with 


## Issues with data availibility
Biomedical image classification requires segmentation masks, which essentially give a label to every pixel in a given image, this was not given in the data from RSNA, however if suitable public data was availiable, it can be used to pre-train a U-Net model to segment new images. Of course such segmentations will not be perfect, however given the dire performance of regular convolutional neural networks, the descision was made to use this approach. Unfortunatley, public data segmenting Axial T2 MRI scans is not readily available/easily accessible - this certainly has an impact on the accuracy of the model.
Sagittal T1 and T2 MRI scans are widely availible, hence models can be trained


## Results
### Trial run
To test the pipeline, a run of just 50 sagittal T1 scans was used and resulted in


### First run
First, every single segmentation my program successfully produced was fed into the nnUNet model, despite many incorrect and inaccurate masks. 
The train and validation dataset consisted of ~3000 sagittal T1 scans, ~2000 sagittal T2/STIR scans and X axial T2 scans. All scans ranged in quality, as shown below:

In spite of said inaccuracies, the pipeline achieved...
-> 43.7% accuracy on Sagittal T1 scans, identifying right/left neural foraminal narrowing and whether it was a normal/mild, moderate or severe case.

_Epoch 144_
_Current learning rate: 0.00869_
_Pseudo dice [0.8177, 0.5535, 0.5744, 0.5374, 0.4475, 0.3228, 0.2098, 0.2068, 0.5067, 0.4215, 0.1714, 0.0, nan, 0.0011, 0.5015, 0.412, 0.603, 0.5684, 0.5332, 0.4877, 0.4564, 0.3469, 0.5348, 0.471, 0.4174, 0.3639, nan, nan, 0.0, 0.1444, 0.5782, 0.8237, 0.7893, 0.7822, 0.7286, 0.6587, 0.3636]_

-> 0.yy accuracy in identifying right/left subarticular stenosis and whether it was a normal/mild, moderate or severe case.


-> 0.zz accuracy in identifying right/left spinal canal stenosis and whether it was a normal/mild, moderate or severe case.



The combined runtime was around 16 hours of GPU usage.

### My Approach
The process of applying deep learning to a new problem is challenging. First of all, there are a wide array of model architectures to choose from - for image classification, convolutional neural networks (CNNs) are usually the preffered choice. Secondly the data must be processed in suitable way for the model to understand the images and what categories they fall into. Then there are many parameters and hyperparameters to consider, such as the model depth, i.e how many layers (and of which type) will work for the data and task at hand.

My first approaches to this problem consisted of 5-10 layered convolutional neural networks coded in Pytorch. This is was a learning moment for me, I do not have to produce all of my results from scratch. Taking the time to test and trial different model architectures I have come up with when many brilliant engineers have created models which have been fine-tuned and trained on millions of images exist for the purpose of furthering others' research. I put models such as the ResNet18, ResNet152, EfficientNetB0 and DenseNet169 to work on my existing data pipeline. However while I saw some initial improvement, the model still failed to achieve high levels of accuracy - something was missing.

Coming back to the learning moment from before, I started to read more and more scientific literature around deep learning in biomedical image classification and found why my models hadn't performed all too well - CNNs fail to capture 'local features' in an image, therefore lack the spatial understanding of the relationships between organs, bones and how damage to these features look in biomedical images. In 2015 a revolutionary paper presenting a new architecture was published which adressed the aforementioned issues of the CNN. This architecture is called the U-Net (named for its U shape) and I will briefly explain how it works.

IMAGE OF UNET ARCHITECTURE


### Limitations With The Provided Data
Now armed with a new approach to the problem, an issue remained - U-Net needs images which have every single pixel labelled with its type a process called segmentation. An example of this is this image of a road.
IMAGE OF THE ORIGINAL ROAD AND SEGMENTED ROAD

As seen, the image is coloured accordingly to what the pixel represents - .... . 

Now applying this to the images of the spine - here the original image and the fully segmented image of the spine:
<img src="https://github.com/user-attachments/assets/e7282fb6-b80a-4467-8e96-7b850a678631" style="filter: grayscale(100%);"> <img src="https://github.com/user-attachments/assets/518cf58e-e088-4f62-8147-3574d08aaf2b" style="filter: grayscale(100%);">

The competition dictates that you may not use the internet to access anything external while running the submission notebook, however there is no rule on using publically avaliable data before the submission notebook is run on the Kaggle website. With that in mind, I was inspired by Kaggle user "" and their notebook "" which used a U-Net architecture with a ResNet backbone to train a model to label the vertebrae in an image of the spine, this used data from the Spider dataset. Here is what the evolution of the model through its training looked like:

IMAGE 1-15 OF TRAINING EPOCH PREDICTIONS

Now when tested on one of the MRI scans provided in the competition:

IMAGE OF SEGMENTED SPINE RSNA.

And we observe that it did a pretty good job! This is ample to move on to the next stage of segmenting the image, which is segmenting the discs in the image. My approach was to do this using the coordinates provided in the competition to make an educated guess to where the disc should be. Here's some examples of what I managed to generate for all N MRI scans.

### nnU-Net Model
Now, my original idea was to now use a second U-Net similar to the one used to segment the vertebrae and then use a CNN to classify the conditions and severities, however there is a very clever pre-built model by "" called the nnU-Net, which ... It is made for people with no programming experience and configures all parameters and hyperparameters for the user, due to its ease of use, I highly reccomend this as a base model in other biomedical image classification tasks.

IMAGE OF NNUNET ARCHITECTURE

Description of the nnunet architecture...

This yeilded impressive segmentation masks of the provided images, however there was an issue. During training this message shows: Pseudo dice [0.7606,.., 0.0, nan, nan, nan, 0.0, 0.0, 0.4707, 0.4522, 0.4519, 0.3517,,,0, nan, nan] which gives the accuracy of the model in predicting each class in the segmentation mask, most have been removed here but the closer the value to 1, the better the model is in predicting that class, however there were nan values, which indicated that there were missing samples, so for example the model will never see an MRI image with severe l4 l5 right neural foraminal narrowing, so it cannot then go on to predict if an image contains this condition or not. This required me to go back and ensure that all classes were equally represented.


### Limitations In External Data
There are few papers on the segmentation of the Axial T2 images to predict conditions in the lumbar region and their datasets are all request-only. To my knowledge there are no easily accessible segmentations of Axial T2 MRI scans. Due to this as well as the encroaching deadline, my approach to this was to create an extremely primitive segmentation mask which just segmented a 10x10 box around the coordinates given in the RSNA data, then running this segmentation mask and the original image through the nnU-Net.






























