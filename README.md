# Radiological Society of North America (RSNA) Lumbar Degeneration Classification Competition

# Overview
The lumbar reigion of the spine is a major cause of pain and disability worldwide, infact it is the leading cause of disability with around 600 million people suffering from the varying conditions arising from degeneration in the lumbar discs. The RSNA hosted this competition from June-September 2024 with the hopes that “Competitors will ... build algorithms that advance our ability to accurately and rapidly identify and classify lumbar degenerative spine disease. Such tools have the potential to improve current state-of-the art technology and transform the future of degenerative spine diagnosis and management”. 

The goal for the entrants of the competition is to use deep learning methods to accurately and reliably predict whether the patient has lumbar degeneration as well as the level of severity of said condition. The RSNA provides a dataset of 1,975 studies-worth of MRI scans with three differing types: Sagittal T1, Sagittal T2/STIR and Axial T2 (each study has 50 or more scans).

----------------------

### Type 1: Sagittal T1 Scan

A **Sagittal T1** image is taken from the sagittal plane of the body (side on) and T1 indicates that fat is more visible in the scan, due to the shorter times between pulses in the MRI scans.

<p align="center">
    <img src="https://github.com/user-attachments/assets/e80b2c67-f68e-47ea-b138-f28575ba272f" width="200">
    <img src="https://github.com/user-attachments/assets/46cbd5d5-f174-45d8-a2a8-26fdbd1d0049" width="200">
    <img src="https://github.com/user-attachments/assets/dadfc368-d26d-492e-aa53-45760f41eb85" width="200">
    <img src="https://github.com/user-attachments/assets/49b0b2ac-2460-49b6-98ba-1649f8e2f54a" width="200">
</p>

----------------------

### Type 2: Sagittal T2/STIR Scan

A **Sagittal T2/STIR** image is also taken from the sagittal plane, the T2/STIR indicates that water is more visible in the scan, hence revealing the spinal cord more - due to the longer times between pulses in the MRI scans.

<p align="center">
  <img src="https://github.com/user-attachments/assets/29d57c7f-296e-455c-ad29-d6dc5c78c346" width="200">
  <img src="https://github.com/user-attachments/assets/d9c3462f-ee60-4839-a9fc-b79a1926fdd5" width="200">
  <img src="https://github.com/user-attachments/assets/6810f71c-9665-40a7-8aff-c1ee44ab67df" width="200">
  <img src="https://github.com/user-attachments/assets/57b928c2-5022-4846-8c75-59041c0bb5f3" width="200">
</p>

----------------------

### Type 3: Axial T2 Scan

An axial T2 image is taken from the axial plane (i.e top down of the body), the T2 again indicating that water is more visible than fat in the scan.

<p align="center">
  <img src="https://github.com/user-attachments/assets/babb2988-232f-4ffb-be5b-bbc8bef63933" width="200">
  <img src="https://github.com/user-attachments/assets/3411a878-4228-43cc-ad1b-befefcd27385" width="200">
  <img src="https://github.com/user-attachments/assets/421b8866-3755-4d4d-a7d0-a6b4b5247681" width="200">
  <img src="https://github.com/user-attachments/assets/80f1ec3d-68e3-41e4-aa41-34ec2faa9368" width="200">
</p>

----------------------

Two files are provided with the respect to these images. One contains coordinates of the degenerative disc on a specific MRI scan, the other defines the name and severity of the patient's lumbar conditions along all 50+ scans of the study. Here's an example of a few MRI scans of a patient with conditions:


| spinal_canal_stenosis_l1_l2 | spinal_canal_stenosis_l2_l3 | spinal_canal_stenosis_l3_l4 | spinal_canal_stenosis_l4_l5 | spinal_canal_stenosis_l5_s1 |
|-----------------------------|-----------------------------|-----------------------------|-----------------------------|-----------------------------|
| Normal/Mild                 | Normal/Mild                 | Normal/Mild                 | Normal/Mild                 | Normal/Mild                 |

| left_neural_foraminal_narrowing_l1_l2 | left_neural_foraminal_narrowing_l2_l3 | left_neural_foraminal_narrowing_l3_l4 | left_neural_foraminal_narrowing_l4_l5 | left_neural_foraminal_narrowing_l5_s1 |
|---------------------------------------|---------------------------------------|---------------------------------------|---------------------------------------|---------------------------------------|
| Normal/Mild                           | Normal/Mild                           | Normal/Mild                           | Moderate                              | Normal/Mild                           |

| right_neural_foraminal_narrowing_l1_l2 | right_neural_foraminal_narrowing_l2_l3 | right_neural_foraminal_narrowing_l3_l4 | right_neural_foraminal_narrowing_l4_l5 | right_neural_foraminal_narrowing_l5_s1 |
|----------------------------------------|----------------------------------------|----------------------------------------|----------------------------------------|----------------------------------------|
| Normal/Mild                            | Normal/Mild                            | Moderate                               | Moderate                               | Normal/Mild                            |

| left_subarticular_stenosis_l1_l2 | left_subarticular_stenosis_l2_l3 | left_subarticular_stenosis_l3_l4 | left_subarticular_stenosis_l4_l5 | left_subarticular_stenosis_l5_s1 |
|----------------------------------|----------------------------------|----------------------------------|----------------------------------|----------------------------------|
| Normal/Mild                      | Normal/Mild                      | Normal/Mild                      | Moderate                         | Normal/Mild                      |

| right_subarticular_stenosis_l1_l2 | right_subarticular_stenosis_l2_l3 | right_subarticular_stenosis_l3_l4 | right_subarticular_stenosis_l4_l5 | right_subarticular_stenosis_l5_s1 |
|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|
| Normal/Mild                       | Normal/Mild                       | Normal/Mild                       | Normal/Mild                       | Normal/Mild                       |


### A Sagittal T1, Sagittal T2/STIR and an Axial T2 scan with coordinates.

<p align="center">
  <img src="https://github.com/user-attachments/assets/c2393da5-187d-4077-ab02-7649acc25eb0" width="300">
  <img src="https://github.com/user-attachments/assets/f5960680-f6d5-4ac6-bb2a-2f1be211030d" width="300">
  <img src="https://github.com/user-attachments/assets/6d857e34-20f8-4652-8265-29d0a5aae1a0" width="300">
</p>

_(Note: coordinates only exist if the condition is mild from the normal/mild class and of course if they are moderate or severe!)_


# Issues with data availibility
Biomedical image classification requires segmentation masks, which essentially give a label to every pixel in a given image, this was not given in the data from RSNA, however if suitable public data was availiable, it can be used to pre-train a U-Net model to segment new images. Of course such segmentations will not be perfect, however given the limited performance of regular convolutional neural networks (CNNs), the descision was made to use this approach. 

Unfortunatley, public data segmenting Axial T2 MRI scans is not readily available/easily accessible - this certainly has an impact on the accuracy of the model. However, segmented Sagittal T1 and T2 MRI scans are  availible from the [Spider Dataset](https://spider.grand-challenge.org/data/), hence models will be trained off of this to create segmentations of the vertebrae on new the given MRI scans.


# Results
## Trial run
To test the model, a training set of 50 idyllic sagittal T1 segmentation (generated by the data pipeline) masks was used.

It resulted in a **low ~10% accuracy**, which aligned with previous accuracies of using a regular pretrained CNN (I tested everything from a ResNet18 to a Densenet169) which leveraged the whole of the dataset. *(Note: I did not save an example of such a pipeline that I had created, but this Kaggle notebook used the same pretrained ResNet18 model and resulted in very similar predictions to me [RSNA ResNET starter notebook - Coderrkj](https://www.kaggle.com/code/coderrkj/rsna-resnet-starter-notebook))*.

The model struggled to even construct the segmentation mask, let alone predict whether a condition was normal/mild, moderate or severe.

<p align="center">
  <img src="https://github.com/user-attachments/assets/fb54080e-08d6-4ad6-bde8-abf5c7548d60" width="200">
  <img src="https://github.com/user-attachments/assets/a678aca8-a45c-45c0-ab26-0a62f7f582f2" width="200">
  <img src="https://github.com/user-attachments/assets/3d0e7288-882e-40fa-928b-08eb33b683d9" width="200">
  <img src="https://github.com/user-attachments/assets/66b3ed7c-b9f5-4c4b-996f-3c5c10d36dfd" width="200">
</p>

Where colouring the vertebrae grey, and the conditions, normal/mild, moderate and severe as green, blue and red respectivley makes for a better viewing experience.

<p align="center">
  <img src="https://github.com/user-attachments/assets/bc56dd8b-371b-4130-bfda-451b5a3a224a" width="200">
  <img src="https://github.com/user-attachments/assets/28aa1c2f-168e-40c0-a7ae-54c0e54e396b" width="200">
  <img src="https://github.com/user-attachments/assets/28d08632-bf6d-419c-b5a5-9c6d2d31967e" width="200">
  <img src="https://github.com/user-attachments/assets/8b77b372-d8a6-48c2-9837-2364d56073c7" width="200">
</p>

While this performance leaves alot to be desired, the results on such a small sample size are promising and the next step was to increase the amount of data by a factor of 600.

-------------------------------

## First run
First, every single segmentation my program successfully produced was fed into the nnUNet model, despite many incorrect and inaccurate masks. 
The train and validation dataset consisted of ~3,000 sagittal T1 scans, ~2,000 sagittal T2/STIR scans and ~12,000 axial T2 scans. All segmentation masks ranged in quality, as shown below:

<p align="center">
  <img src="" width="200">
  <img src="" width="200">    
  <img src="" width="200">
  <img src="" width="200">
</p>

## Initial Run of nnU-Net on Biomedical Image Classification Task

---

### Accuracy
- **Sagittal T1 scans:** *43.7% accuracy*
- **Sagittal T2/STIR scans:** *50.3% accuracy*
- **Axial T2 scans:** *16.6% accuracy* on normal cases, 2.5% when including all classes
- **Overall Accuracy:** *~47%* not considering the Axial scans or *~30%* when considered.

---

### Results 

#### Example Predictions:

### Two pairs of label/prediction images for Sagittal T1 scans:
<p align="center">
  <img src="https://github.com/user-attachments/assets/c35b3a9d-45d1-4fa9-9ea0-fb92af31234b" width="200">
  <img src="https://github.com/user-attachments/assets/001e7724-74c7-4716-9b24-96511abcbb8a" width="200">
  <img src="https://github.com/user-attachments/assets/65fa6981-e8b2-4993-84cb-62b714eef289" width="200">
  <img src="https://github.com/user-attachments/assets/e3f232fa-4ce9-4f61-8e7b-ec0ccfd68595" width="200">
</p>

- **Observations**:
  - The model tended to miss moderate and severe cases, sometimes identifying moderate conditions as normal/mild (for example in the first pair, the l5_s1 disc is incorrectly green, not blue).
  - In the loss function (pseudo dice), there were a few 0.0 and nan values, implying that some of the classes do not appear in the training data.
  
- **Potential Improvements**:
  - The classes (the conditions and severities) need to be better distributed across the dataset, the quality of the data may is a consideration as well.

- Rather interestingly, the model actually improves upon previous U-Net segmentation quality, showing smoother and fuller vertebrae/disc segmentation.

> **Note**: Due to the error in the label segmentation masks, the model is penalised unfairly due to actually having a higher accuracy in locating the actual vertebrae/disc pixels in raw MRI images
>
> Could consider training a second model on these improved predictions to refine the label segmentations' accuracy.

---

#### Sagittal T2/STIR Scans
<p align="center">
  <img src="" width="200">
  <img src="" width="200">    
  <img src="" width="200">
  <img src="" width="200">
</p>

- **Observations**:
  - Improved performance compared to Sagittal T1 scans, the pre-training dataset consisted of only Sagittal T2/STIR scans, potentially leading to more accurate segmentation masks of the Sagittal T2 type.
  - Slight class Imbalance: pseudo dice scores showed a 3% and 0% for two classes, indicating underrepresentation of these classes, this was much better than the Sagittal T1 distribution though.

- **Potential Improvements**:
  - Again, the same as Sagittal T1 scans, increase the quality of the scans, omitting potentially harmful ones.
  - Improve the distribution through augmentation.

---

#### Axial T2 Scans
- **Observations:**
    - Low accuracy (2.5%) across nearly 40 classes using only basic segmentation labels, suggesting the need for better-quality segmentation data.
    - Even basic segmentation masks heavily impact model performance, underscoring the potential value of a high-quality, widely available biomedical segmentation dataset.
  
> **Note:** Going forward, the Axial MRI scans will no longer be considered, due to this roadblock of no segmentations.

---

### Runtime and Efficiency
- **Total CPU Runtime:** ~2 hours, dedicated to pretraining the U-Net and preprocessing MRI scans. 
- **Total GPU Runtime:** ~16 hours. However the best model accuracy was achieved earlier in the training, if early stopping was implemented, the training time was around 10 hours. 
---

### Additional Observations

- **NaN and 0.0 Values in Pseudo Dice**: 
  - **NaN Values**: Indicate that specific classes were not present in any training examples.
  - **0.0 Values**: Suggest a mix of limited data for some classes and difficulty distinguishing specific features. Likely caused by the inherent complexity of the classes or insufficient data for those classes.

---

### Next Steps and Potential Improvements

1. **Refine Training Data**:
   - For Sagittal T1 and T2, filter out unsatisfactory segmentation masks.
   - Consider two approaches:
     - Aggressively remove any imperfect masks.
     - Filter out unrealistic masks that may negatively impact learning.

2. **Augment Axial T2 Data**:
   - Use the Albumentations library to create a more balanced distribution across conditions and severities to improve performance.

3. **Further Experimentation**:
   - Test early stopping based on initial peak accuracy to potentially save GPU time.

---

### Final Thoughts

This initial run provides a promising foundation with significant room for improvements, especially by refining the segmentation data quality. Future experimentation, particularly with data augmentation and more precise filtering, will likely yield better accuracy and segmentation quality across all s

### Second Run
Taking the best performing group - Sagittal T2/STIR MRI scans, manually go through the segmentation masks and remove ones which may impact model performance, keeping imperfect ones. Now that the quality of the images has been increased, it can be observed whether the accuracy of the model is impacted by quality.





### Conclusions and further work
While a great performance increase was observed from the original ResNet18 approach, it is important to remember that biomedical image segmentation requires a very high degree of accuracy, ensuring there are no misdiagnoses, potentially missing causes for their pain, or worse. I enjoyed learning about the advanced methods in segmentation and has most certainly improved my approach to deep learning problems - it is important to read others' research and look for way to improve performance on their work, or by combining multiple people's work together, rather than attempting to conquer the problem entirely by oneself.

This project has increased my knowledge of computer vision and these models and ideas I have learnt through the project have wide applications in research and industry, for example - self-driving cars.

Further work may include:
- Improving the quality of the segmentation masks of the sagittal T1 and T2 MRI scans. Either by hand or using more data and a better pretrained U-Net.
- When a suitable dataset for axial T2 images is available, performance on this pipeline will likely skyrocket.
























