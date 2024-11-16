# Radiological Society of North America (RSNA) Lumbar Degeneration Classification Competition

## Overview
The lumbar reigion of the spine is a major cause of pain and disability worldwide, infact it is the leading cause of disability with around 600 million people suffering from the varying conditions arising from degeneration in the lumbar discs. The RSNA hosted this competition from June-September 2024 with the hopes that “Competitors will ... build algorithms that advance our ability to accurately and rapidly identify and classify lumbar degenerative spine disease. Such tools have the potential to improve current state-of-the art technology and transform the future of degenerative spine diagnosis and management”. 

The goal for the entrants of the competition is to use deep learning methods to accurately and reliably predict whether the patient has lumbar degeneration as well as the level of severity of said condition. The RSNA provides a dataset of 1,975 studies (patients) MRI scans with three differing types: Sagittal T1, Sagittal T2/STIR and Axial T2.

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

Two files are provided with the respect to these images. One contains coordinates of the degenerative disc on a specific MRI scan, the other defines the name and severity of the patient's lumbar conditions along all 50+ scans of the study. Here's an example of a few MRI scans of a patient with *****




## Issues with data availibility
Biomedical image classification requires segmentation masks, which essentially give a label to every pixel in a given image, this was not given in the data from RSNA, however if suitable public data was availiable, it can be used to pre-train a U-Net model to segment new images. Of course such segmentations will not be perfect, however given the dire performance of regular convolutional neural networks (CNNs), the descision was made to use this approach. Unfortunatley, public data segmenting Axial T2 MRI scans is not readily available/easily accessible - this certainly has an impact on the accuracy of the model.
Sagittal T1 and T2 MRI scans are widely availible, hence models can be trained to create segmentations of the vertebrae on new MRI scans.


## Results
### Trial run
To test the pipeline, a run of just 50 idyllic sagittal T1 scans was used.
It resulted in around a poor 10% accuracy, which aligned with previous accuracies of using a regular pretrained CNN which leveraged the whole of the dataset. *(Note: I did not save an example of such a pipeline that I had created, but this Kaggle notebook used the same pretrained ResNet18 model and resulted in similar predictions to me [RSNA ResNET starter notebook - Coderrkj](https://www.kaggle.com/code/coderrkj/rsna-resnet-starter-notebook))*.

It struggled to even construct the segmentation mask, let alone predict whether a condition was normal/mild, moderate or severe.
![ST1_0000](https://github.com/user-attachments/assets/fb54080e-08d6-4ad6-bde8-abf5c7548d60)
![ST1_0015](https://github.com/user-attachments/assets/a678aca8-a45c-45c0-ab26-0a62f7f582f2)
![ST1_0023](https://github.com/user-attachments/assets/3d0e7288-882e-40fa-928b-08eb33b683d9)
![ST1_0028](https://github.com/user-attachments/assets/66b3ed7c-b9f5-4c4b-996f-3c5c10d36dfd)

Where colouring the vertebrae grey, and the conditions, normal/mild, moderate and severe as green, blue and red respectivley makes for a better viewing experience.

![color_2](https://github.com/user-attachments/assets/bc56dd8b-371b-4130-bfda-451b5a3a224a)
![color_1](https://github.com/user-attachments/assets/28aa1c2f-168e-40c0-a7ae-54c0e54e396b)
![color_4](https://github.com/user-attachments/assets/28d08632-bf6d-419c-b5a5-9c6d2d31967e)
![color_3](https://github.com/user-attachments/assets/8b77b372-d8a6-48c2-9837-2364d56073c7)

While this performance leaves alot to be desired, the results on such a small sample size are promising and the next step was to increase the amount of data by a factor of 600.


### First run
First, every single segmentation my program successfully produced was fed into the nnUNet model, despite many incorrect and inaccurate masks. 
The train and validation dataset consisted of ~3000 sagittal T1 scans, ~2000 sagittal T2/STIR scans and X axial T2 scans. All segmentation masks ranged in quality, as shown below:




In spite of displayed inaccuracies, the pipeline achieved:

-> **43.7% accuracy on Sagittal T1 scans**, identifying right/left neural foraminal narrowing and whether it was a normal/mild, moderate or severe case. Below is two label (left)/prediction (right) pairs produced.

![label_1](https://github.com/user-attachments/assets/c35b3a9d-45d1-4fa9-9ea0-fb92af31234b)
![pred_1(1)](https://github.com/user-attachments/assets/001e7724-74c7-4716-9b24-96511abcbb8a)
![label_4](https://github.com/user-attachments/assets/65fa6981-e8b2-4993-84cb-62b714eef289)
![pred_2](https://github.com/user-attachments/assets/e3f232fa-4ce9-4f61-8e7b-ec0ccfd68595)

The model misses more severe conditions, as seen in the first pair, where the prediction shows the model wrongly identified a moderate condition for a normal/mild one, it did however manage to recognise the other two moderate conditions. A surprisingly interesting effect of the model is that it improves on the previous U-Net's and the automatic box labelling algorithm's ability to segment the vertebrae and discs! 

Removing the 0.0s from the average gives an accuracy of **48%** _on all well represented classes within the dataset._

-> **40% accuracy on Sagittal T2/STIR scans** identifying right/left subarticular stenosis and whether it was a normal/mild, moderate or severe case.


-> **0% accuracy on Axial T2 scans** identifying right/left spinal canal stenosis and whether it was a normal/mild, moderate or severe case.



The combined runtime was around 16 hours of GPU usage - this is over the limit, and will be considered once satisfactory results are achieved in furture training runs.

It can be observed that in the pseudo dice, there are some nan values and some 0.0 values - the nan values indicate that none of the training examples contained that specific class number. The 0.0 values could indicate there was not enough data for that class or that these features were hard to distinguish from others - possibly a combination of both. 

Improvements can be made, such as the refinement of the training data, for sagittal T1 and T2, removing a subset of masks I am not happy with. To do this, I can either be very aggressive, removing any mask which isn't perfect, or, removing unrealistic masks which look like they would be unhelpful to the model's learning. For the axial T2 masks, I can use the albumentations library to create a fair distribution of the conditions and their severities to see if that improves performance.

### Second Run
Now that the quality of the images has been reduced



























