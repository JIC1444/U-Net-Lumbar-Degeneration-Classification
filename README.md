# RSNA Lumbar Degeneration Classification Competition

## Competition Overview
The lumbar reigion of the spine is a major cause of pain and disability worldwide, infact it is the leading cause of disability with around 600 million people suffering from the varying conditions arising from degeneration in the lumbar discs. The goal of the competition is to use deep learning methods to accurately and reliably predict whether the patient has a condition and the level of severity of said condition. 
The RSNA provides a dataset of N studies (patients) MRI scans with three differing camera settings/positions, these being Sagittal T1, Sagittal T2/STIR and Axial T2.
A sagittal T1 image is taken from the sagittal plane of the body (i.e side on) and the T1 indicates that fat is more visible in the scan.
SAGITTAL T1 EXAMPLE IMAGES
A sagittal T2/STIR image is also taken from the sagittal plane, however the T2/STIR indicates that water is more visible in the scan, hence revealing the spinal cord more.
SAG T2 EXAMPLE IMAGES
An axial T2 image is taken from the axial plane (i.e top down of the body).
AX T2 EXAMPLE IMAGES
They also provide a file with the coordinates of the degenerative disc along with the condition name as well as the severity of the damage to the disc. These include:
IMAGES OF THE DEGENERATION TYPES WITH COORDINATES

### My Approach
The process of applying deep learning to a new problem is challenging. First of all, there are a wide array of model architectures to choose from - for image classification, convolutional neural networks (CNNs) are usually the preffered choice. Secondly the data must be processed in suitable way for the model to understand the images and what categories they fall into. Then there are many parameters and hyperparameters to consider, such as the model depth, i.e how many layers (and of which type) will work for the data and task at hand.

My first approaches to this problem consisted of 5-10 layered convolutional neural networks coded in Pytorch. This is where I made my first mistake - I took the time to test and trial different model architectures when there exist models which have been trained on millions of images which can be loaded and used with a line of code. I learned the important lesson that I don't have to write everything from the ground up and it is nessecary to use others' work and research to inform my own. However while I saw some initial improvement, the model still failed to achieve high levels of accuracy - something was missing.

Now that I had hit this roadblock, I started to read more and more scientific literature around deep learning in biomedical image classification and found why my models hadn't performed all too well - CNNs fail to capture 'local features' in an image, therefore lack the spatial understanding of the relationships between organs, bones and how damage to these features look in biomedical images. In 2015 a revolutionary paper presenting a new architecture was published which adressed the aforementioned issues of the CNN. This architecture is called the U-Net (named for its U shape) and I will briefly explain how it works.

IMAGE OF UNET ARCHITECTURE


### Limitations With The Provided Data
Now armed with a new approach to the problem, an issue remained - U-Net needs images which have every single pixel labelled with its type a process called segmentation. An example of this is this image of a road.
IMAGE OF THE ORIGINAL ROAD AND SEGMENTED ROAD

As seen, the image is coloured accordingly to what the pixel represents - .... . 

Now applying this to the images of the spine - here is a fully segmented image of the spine 
SEGMENTED IMAGE OF A SPINE MRI

The competition dictates that you may not use the internet to access anything external while running the submission notebook, however there is no rule on using publically avaliable data before the submission notebook is run on the Kaggle website. With that in mind, I was inspired by Kaggle user "" and their notebook "" which used a U-Net architecture with a ResNet backbone to train a model to label the vertebrae in an image of the spine, this used data from the Spider dataset. Here is what the evolution of the model through its training looked like:

IMAGE 1-15 OF TRAINING EPOCH PREDICTIONS

Now when tested on one of the MRI scans provided in the competition:

IMAGE OF SEGMENTED SPINE RSNA.

And we observe that it did a pretty good job! This is ample to move on to the next stage of segmenting the image, which is segmenting the discs in the image. My approach was to do this using the coordinates provided in the competition to make an educated guess to where the disc should be. Here's some examples of what I managed to generate for all N MRI scans.

### nnU-Net Model
Now, my original idea was to now use a second U-Net similar to the one used to segment the vertebrae and then use a CNN to classify the conditions and severities, however there is a very clever pre-built model by "" called the nnU-Net, which ... It is made for people with no programming experience and configures all parameters and hyperparameters for the user, due to its ease of use, I highly reccomend this as a base model in other biomedical image classification tasks.\

IMAGE OF NNUNET ARCHITECTURE

Description of the nnunet architecture...

This yeilded impressive segmentation masks of the provided images, however there was an issue. During training this message shows: Pseudo dice [0.7606,.., 0.0, nan, nan, nan, 0.0, 0.0, 0.4707, 0.4522, 0.4519, 0.3517,,,0, nan, nan] which gives the accuracy of the model in predicting each class in the segmentation mask, most have been removed here but the closer the value to 1, the better the model is in predicting that class, however there were nan values, which indicated that there were missing samples, so for example the model will never see an MRI image with severe l4 l5 right foraminal narrowing, so it cannot then go on to predict if an image contains this condition or not. This required me to go back and ensure that all classes were equally represented.


### Limitations In External Data
There are few papers on the segmentation of the Axial T2 images to predict conditions in the lumbar region and their datasets are all request-only. To my knowledge there are no easily accessible segmentations of Axial T2 MRI scans. Due to this, I have had to use a regular DenseNet CNN to classify the Axial MRIs as best possible.

## Results




























