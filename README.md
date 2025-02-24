# Lumbar Degeneration Classification on MRI Images of The Spine

# Overview
The lumbar reigion of the spine is the leading cause of disability with around 600 million people suffering from the varying conditions arising from degeneration in the lumbar discs. Hence why the RSNA (Radiological Society of North America) curated the largest public dataset consisting of X thousand patients, with a total of X hundred thousand labelled MRI scans.

The goal for the entrants of the competition is to use deep learning methods to accurately and reliably predict whether the patient has lumbar degeneration as well as the level of severity of said condition. The RSNA provides a dataset of 1,975 studies-worth of MRI scans with three differing types: Sagittal T1, Sagittal T2/STIR and Axial T2 (each study has 50 or more scans).

# Final Results


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

_(Note: coordinates only exist if the condition is mild from the normal/mild class and if they are moderate or severe!)_


# Issues with data availibility
Biomedical image classification requires segmentation masks, which essentially give a label to every pixel in a given image, this was not given in the data from RSNA, however if suitable public data was availiable, it can be used to pre-train a U-Net model to segment new images. Of course such segmentations will not be perfect, however given the limited performance of regular convolutional neural networks (CNNs), the descision was made to use this approach. 

Unfortunatley, public data segmenting Axial T2 MRI scans is not readily available/easily accessible - this certainly has an impact on the accuracy of the model. However, segmented Sagittal T1 and T2 MRI scans are  availible from the [Spider Dataset](https://spider.grand-challenge.org/data/), hence models will be trained off of this to create segmentations of the vertebrae on new the given MRI scans.


# Results
## Trial run
To test the model, a training set of 50 idyllic sagittal T1 segmentation (generated by the data pipeline) masks was used. The evaluation metric used for the rest of the analysis is the **Dice score**, which is a number from 0 to 1, representing the correct pixel value overlap between the label and the prediction from the model. I will be presenting the Dice score as a percentage, for ease of interpretation.

This trial run resulted in a **low ~10% Dice score**, which aligned with previous accuracies of using a regular pretrained CNN (I tested everything from a ResNet18 to a Densenet169) which leveraged the whole of the dataset. *(Note: I did not save an example of such a pipeline that I had created, but this Kaggle notebook used the same pretrained ResNet18 model and resulted in very similar predictions to me [RSNA ResNET starter notebook - Coderrkj](https://www.kaggle.com/code/coderrkj/rsna-resnet-starter-notebook))*.

The model struggled to even construct the segmentation mask, let alone predict whether a condition was normal/mild, moderate or severe.

<p align="center">
  <img src="https://github.com/user-attachments/assets/a678aca8-a45c-45c0-ab26-0a62f7f582f2" width="250">
  <img src="https://github.com/user-attachments/assets/3d0e7288-882e-40fa-928b-08eb33b683d9" width="250">
  <img src="https://github.com/user-attachments/assets/66b3ed7c-b9f5-4c4b-996f-3c5c10d36dfd" width="250">
</p>

Where colouring the vertebrae grey, and the conditions, normal/mild, moderate and severe as green, blue and red respectivley makes for a better viewing experience.

<p align="center">
  <img src="https://github.com/user-attachments/assets/28aa1c2f-168e-40c0-a7ae-54c0e54e396b" width="250">
  <img src="https://github.com/user-attachments/assets/28d08632-bf6d-419c-b5a5-9c6d2d31967e" width="250">
  <img src="https://github.com/user-attachments/assets/bc56dd8b-371b-4130-bfda-451b5a3a224a" width="250">
</p>

And when overlayed onto a their respective input images:

<p align="center">
    <img src="https://github.com/user-attachments/assets/77e2820a-9a33-4d08-a9c2-b458a12c5255" width="250">
    <img src="https://github.com/user-attachments/assets/9e3e332f-b783-4696-aadf-3b653a57245a" width="250">
    <img src="https://github.com/user-attachments/assets/e12f92cf-d2bf-418e-b6b5-d3e646e557b2" width="250">
</p>
    

While this performance leaves alot to be desired, the results on such a small sample size are promising and the next step was to increase the amount of data by a factor of 600.

-------------------------------

## First run of nnU-Net on RSNA data
First, every single segmentation my program successfully produced was fed into the nnUNet model, despite many incorrect and inaccurate masks. 
The train and validation dataset consisted of ~3,000 sagittal T1 scans, ~2,000 sagittal T2/STIR scans and ~12,000 axial T2 scans. All segmentation masks ranged in quality, as shown below (good/bad Sagittal T1 masks, good/bad Sagittal T2 masks, standard Axial T2 mask):

<p align="center">
    <img src="https://github.com/user-attachments/assets/f9bcb8dc-9b69-4c4d-b102-b0e7d49fae28" width="200">
    <img src="https://github.com/user-attachments/assets/d159189d-57d1-4b47-99cb-e10a6f40e7e6" width="200"> 
    <img src="https://github.com/user-attachments/assets/1765af7d-a347-4ad1-89ca-bbcbb829b547" width="200">
</p>


<p align="center">
    <img src="https://github.com/user-attachments/assets/5dca35a2-1909-49cc-ac32-fa1840b477a7" width="200">
    <img src="https://github.com/user-attachments/assets/11d39120-51a2-4013-a2c1-36774422851d" width="200">
</p>



### Accuracy
- **Sagittal T1 scans:** *43.7% Dice score*
- **Sagittal T2/STIR scans:** *50.3% Dice score*
- **Axial T2 scans:** *16.6% Dice score* on normal cases, >5% when including all classes
- **Overall Dice score:** *~47%* not considering the Axial scans or *~30%* when considered.

---

### Examples of label-prediction-overlays of Sagittal T1 scans:
<p align="center">
    <img src="https://github.com/user-attachments/assets/c35b3a9d-45d1-4fa9-9ea0-fb92af31234b" width="200">
    <img src="https://github.com/user-attachments/assets/001e7724-74c7-4716-9b24-96511abcbb8a" width="200">
    <img src="https://github.com/user-attachments/assets/3862ca02-fe28-4004-87af-cb2a8d191f8d" width="200">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/65fa6981-e8b2-4993-84cb-62b714eef289" width="200">
  <img src="https://github.com/user-attachments/assets/e3f232fa-4ce9-4f61-8e7b-ec0ccfd68595" width="200">
    <img src="https://github.com/user-attachments/assets/7fdd6066-6182-4362-8f2c-6e48147f5888" width="200">
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

### Sagittal T2/STIR Scans

- **Observations**:
  - Improved performance compared to Sagittal T1 scans, the pre-training dataset consisted of only Sagittal T2/STIR scans, potentially leading to more accurate segmentation masks of the Sagittal T2 type.
  - Slight class Imbalance: pseudo dice scores showed a 3% and 0% for two classes, indicating underrepresentation of these classes, this was much better than the Sagittal T1 distribution though.

- **Potential Improvements**:
  - Again, the same as Sagittal T1 scans, increase the quality of the scans, omitting potentially harmful ones.
  - Improve the distribution through augmentation.
> By improving the class imbalance in the data, any skew of the accuracy due to the lack of moderate/severe cases will be gone.

---

### Axial T2 Scans
- **Observations:**
    - Low Dice >5% across nearly 40 classes using only basic segmentation labels, suggesting the need for better-quality segmentation data.
    - Even basic segmentation masks heavily impact model performance, underscoring the potential value of a high-quality, widely available biomedical segmentation dataset.
  
> **Note:** Going forward, the Axial MRI scans will no longer be considered, due to this roadblock of having no segmentations.

---

### Runtime and Efficiency
- **Total CPU Runtime:** ~2 hours, dedicated to pretraining the U-Net and preprocessing MRI scans. 
- **Total GPU Runtime:** ~16 hours. However the best model Dice score was achieved earlier in the training, if early stopping was implemented, the training time would be around 10 hours. 
---

### Additional Observations

- **NaN and 0.0 Values in Pseudo Dice** observed when training:
  - **NaN Values**: Indicate that specific classes were not present in any training examples.
  - **0.0 Values**: Suggest a mix of limited data for some classes and difficulty distinguishing specific features. Likely caused by the inherent complexity of the classes or insufficient data for those classes.
 
This leads to the next section where the effects of this are attempted to minimised.

---

### Next Steps and Potential Improvements

1. **Refine Training Data**:
   - For Sagittal T1 and T2, filter out unsatisfactory segmentation masks.
   - Considering the two approaches:
     - Aggressively removing any imperfect masks.
     - Filtering masks that may negatively impact learning.

2. **Augment Axial T2 Data**:
   - Use the Albumentations library to create a more balanced distribution across conditions and severities to improve performance.

3. **Early Stopping**:
   - Implement early stopping to save GPU time.

---


## Second Run of nnU-Net on RSNA (Sagittal T2 Scans)
The initial run gave a promising foundation, by refining the data quality, the performance should be improved. Taking the best performing group - Sagittal T2/STIR MRI scans, manually go through the segmentation masks and remove ones which may impact model performance, keeping imperfect ones. Collect the distribution of conditions, augmenting moderate and severe up to a higher percentage of the dataset. The training and validation dataset consisted of roughly 8000 images.

#### This increase in image variation, as well as a better distributed dataset led to a ~66% Dice score.

### Examples of input-prediction overlays on the new Sagittal T2/STIR classifier.

<p align="center">
    <img src="https://github.com/user-attachments/assets/c4a359fc-b7b1-4cf4-9ce4-e02364f3a7ac" width="200">
    <img src="https://github.com/user-attachments/assets/2091495c-4869-4110-b98d-2adb4c13e5df" width="200">  
    <img src="https://github.com/user-attachments/assets/5bdd6ba6-0d0a-4784-b8bf-a44a4c828102" width="200">
    <img src="https://github.com/user-attachments/assets/e4371d8e-dc58-44f9-9f59-d3706aa41411" width="200">
</p>

---

<p align="center">
    <img src="https://github.com/user-attachments/assets/e254cc3c-5b05-4696-9f80-fbcba45a7895" width="200">
    <img src="https://github.com/user-attachments/assets/fa021719-64af-4543-b7f0-43d2f593c8f9" width="200">
    <img src="https://github.com/user-attachments/assets/a81a4ae5-6e58-4c2e-8d71-52fa0be9decb" width="200">
    <img src="https://github.com/user-attachments/assets/47f39f4c-97b7-487e-b973-3ab78b7d12f2" width="200">
</p>

---

<p align="center">
    <img src="https://github.com/user-attachments/assets/48c07e93-51e3-4167-93bf-9934e04573a3" width="200">
    <img src="https://github.com/user-attachments/assets/356f4fed-8b2c-4544-97b7-cc0588cfaf9b" width="200">
</p>


Interestingly, while the model achieved a higher accuracy, the same smoothing effect didnt happen on the segmentation masks! Perhaps the greater training pool led to the predictions being more like the input, or perhaps the model needed further training. The training curve suggested that the model had not generalised yet and that further training could be done to improve the accuracy further.

### Runtime and Efficiency
- **Total GPU Runtime:** ~40 hours.
  
---

### Additional Observations

- **Dice score**: This was the Dice score after 24 hours, however it did not seem to plateau, so running this model further may produce a more accuracte model.
- **Compute time**: A much higher compute time was necessary (4x12hr kaggle GPU sessions), however around 10 of these hours were wasted as the nnU-Net checkpoints happen every 50 epochs, leading to these wasted hours.
 
---


## Conclusions and further work
A performance increase of 10% to 66% was observed from the original ResNet18 approach, which is a result I am proud of. However it is important to remember that biomedical image segmentation requires a very high degree of accuracy, ensuring there are a minimised number of false positives/negative diagnoses. I enjoyed learning about the advanced methods in segmentation and has significantlly improved my approach to deep learning problems - it is important to read others' research and look for way to improve performance on their work, or by combining multiple people's work together, rather than attempting to conquer the problem on one's own. The project has also increased my knowledge of computer vision and these models and ideas I have learnt through the project have wide applications in research and industry.

Further work:
- Improving the quality and the quantity of the segmentation masks of the sagittal T1 and T2 MRI scans. Ideally with a better trained U-Net or even an nnU-Net, since only about a third of the sagittal MRIs made it through the algorithmic segmentation process.
- Trial and error of the augmentations for the data, 8000 led to a good performance but a long time of convergence, perhaps there is a better balance to be struck between these components.
- If a suitable dataset for axial T2 images becomes available, performance on this pipeline will certainly lead to massive gains in predictive power.



## Appendix: Algorithimically Segementing the Images
This process goes from this mask, produced by the pretrained U-Net, to a this segmentation mask, ready to be fed into the classification model.
<p align="center">
    <img src="https://github.com/user-attachments/assets/ed4ecef9-680b-46b1-a6cb-8dae85d5daa8" width="300">
    <img src="https://github.com/user-attachments/assets/8d7f8bf1-ab96-42b2-ac69-8d882e85db4c" width="300">
</p>


First, the general process this algorithm follows.
```{p}
"""
Label the masks with the vertebrae class as well as the disc class. (From either st1_classes or st2_classes
General Process: -> Take the highest disc from the dataframe (l1_l2)
-> Find the center and sides of the vertebrae
-> Fill a rectangle below the disc, not overlapping the vertebrae below, representing the disc between the two vertebrae
-> Append to an array when completed
-> Repeat until l5_s1 is reached
-> Label s1
-> Compare the array of completed discs/vertebrae to the list of all discs
-> Move up to staring vertebrae, until all discs/vertebrae are completed
-> Label the remaining vertebrae as "other_vertebrae": 2.
"""
```

Using skimage, automatically label the islands (vertebrae) in the segmentation mask since the original image is a black and white (0 and 1) image (above). Then shift the pixel values outside of the range of the actual class values of degeneration (0-40).
```{p}
def auto_label_mask(mask):
    labeled_mask, num_features = label(mask) 
    return labeled_mask
    
def correct_labels_for_overlap(mask, classes):
    #First change the auto-assigned background color(s) to 0.
    sorted_indices = np.argsort(counts)[::-1] # Sort in descending order.
    class_values = classes.values()
    for u in np.unique(mask):
        if u == 0:
            continue
        if u in class_values:
            mask[mask == u] = u + 70 # Adding 70 ensures the automatically assigned pixel value is now completely unique.
    return mask

def auto_label_and_correct_mask(mask, classes):
    color_mask = auto_label_mask(mask)
    corrected_color_mask = correct_labels_for_overlap(color_mask, classes)
    return corrected_color_mask
```

Now, using these different class values, find the 'highest' vertebrae in the mask - align this to a value and work down from there, assigning the actual class (pixel) values which are defined before.
```{p}
def disc_to_vert_and_class(highest_disc, condition):
    n = 15 if condition == "spinal_canal_stenosis" else 0
    if highest_disc == "l1_l2": return "l1", (32 - n)
    elif highest_disc == "l2_l3": return "l2", (33 - n)
    elif highest_disc == "l3_l4": return "l3", (34 - n)
    elif highest_disc == "l4_l5": return "l4", (35 - n)
    elif highest_disc == "l5_s1": return "l5", (36 - n)


def align_verts_to_val(highest_vert, vert_val):
    if highest_vert == "l1": 
        return {"l1": vert_val + 0, "l2": vert_val + 1, "l3": vert_val + 2, "l4": vert_val + 3, "l5": vert_val + 4, "s1": vert_val + 5}
    elif highest_vert == "l2": 
        return {"l1": vert_val - 1, "l2": vert_val + 0, "l3": vert_val + 1, "l4": vert_val + 2, "l5": vert_val + 3, "s1": vert_val + 4}
    elif highest_vert == "l3": 
        return {"l1": vert_val - 2, "l2": vert_val - 1, "l3": vert_val + 0, "l4": vert_val + 1, "l5": vert_val + 2, "s1": vert_val + 3}
    elif highest_vert == "l4": 
        return {"l1": vert_val - 3, "l2": vert_val - 2, "l3": vert_val - 1, "l4": vert_val + 0, "l5": vert_val + 1, "s1": vert_val + 2}
    elif highest_vert == "l5": 
        return {"l1": vert_val - 4, "l2": vert_val - 3, "l3": vert_val - 2, "l4": vert_val - 1, "l5": vert_val + 0, "s1": vert_val + 1} 
    else:
        print(f"Vertebrae {highest_vert} invalid!")
    #There is no "s1" condition.
        
def find_vert_with_coords(mask, x, y):
    central_x_est, central_y_est = int(x) - 11, int(y) - 8
    vert_val = mask[central_y_est, central_x_est]
    if vert_val == 0:
        offsets = [(dx, dy) for dx in range(-3, 4) for dy in range(-3, 4)]
        for dx, dy in offsets:
            temp_x_est, temp_y_est = central_x_est + dx, central_y_est + dy
            
            if 0 <= temp_y_est < mask.shape[0] and 0 <= temp_x_est < mask.shape[1]:
                vert_val = mask[temp_y_est, temp_x_est]
                if vert_val != 0:
                    return vert_val
        return None
    else:
        return vert_val

def locate_vertebrae(mask, highest_vert_str, highest_vert_class, x, y, all_vertebrae = ["l1", "l2", "l3", "l4", "l5", "s1"]):
    vertebrae_val = {v: 0 for v in all_vertebrae}
    #Find the highest vertebrae to act as a reference point within the image, as to what vertebrae are present and their class number.
    vert_val = find_vert_with_coords(mask, x, y)
    if vert_val == None:
        return None
    #Align this with order now.
    vert_val_dict = align_verts_to_val(highest_vert_str, vert_val)
    return vert_val_dict

def calculate_disc_bboxes(regions):
    #Unpack lx and lx+1 vert bboxes.
    bboxes = []
    for i in range(len(regions) - 1):
        top_u, left_u, bottom_u, right_u = regions[i] #Box above.
        top_l, left_l, bottom_l, right_l = regions[i + 1] #Box below.
        #Choose largest out of the x values, so nothing is missed.
        bbox = bottom_u - 3, min(left_u, left_l), top_l + 3, max(right_u + 5, right_l + 5) #Add some height to the bbox to fill dead space created otherwise.
        bboxes.append(bbox)
    return bboxes

def label_sag_mask(path, mask, chunk, classes, class_numbers_verts):    
    chunk = chunk.sort_values("level").reset_index() #Sort down l1_l2 -> l5_s1.
    x, y, level = chunk.x[0], chunk.y[0], chunk.level
    highest_disc = level[0]
    condition = chunk["condition"].values[0]
    highest_vert_str, highest_vert_class = disc_to_vert_and_class(highest_disc, condition)

    vert_val_dict = locate_vertebrae(mask, highest_vert_str, highest_vert_class, x, y) #Use these values to switch the values on the color mask to their respective class values.
    if vert_val_dict is None:
        #print("vert_val_dict is None.")
        return None
    for idx, vert_val in enumerate(vert_val_dict.values()):
        mask[mask == vert_val] = class_numbers_verts[idx] #Won't line up due to them being about 20-30 difference.
    #Assign all values but class_numbers and 0 to be a 1 (other_disc class).

    class_mask = mask.copy().astype(int)
    acceptable_vals = class_numbers_verts + [0]
    filter_mask = ~np.isin(class_mask, acceptable_vals) #Makes all other detected islands of pixels as a default value.
    class_mask[filter_mask] = 1 #~[0, 1, 32...37]

    no_other_mask = class_mask.copy()
    no_other_mask[no_other_mask == 1] = 0 #Make a copy of the classly labeled mask and remove the other_discs to simplify finding the disc regions between the vertebrae.
    no_other_mask = no_other_mask.astype(int)
    debug = np.unique(no_other_mask.copy())
    no_verts = len(np.unique(no_other_mask)) - 1
    regions = []
    for i in np.unique(no_other_mask):
        if i == 0:
            continue
        temp_mask = np.where(no_other_mask == i, i, 0)
        region = regionprops(temp_mask)
        regions.append(region[0].bbox)
    disc_bboxes = calculate_disc_bboxes(regions)

    #Using the class numbers and the bounding boxes, fill the class mask.
    class_numbers = chunk["class_number"].to_list() #Will be the values to assign the discs to (top down).
    def_discs = [2, 3, 4, 5, 6]
    if "right" in condition:
        def_discs = list(np.array(def_discs) + 15)

    all_discs = {"l1_l2": 0, "l2_l3": 0, "l3_l4": 0, "l4_l5": 0, "l5_s1": 0}
    for idx, disc in enumerate(all_discs.keys()):
        disc_info = chunk[chunk["level"] == disc]
        if disc_info.empty:
            all_discs[disc] = def_discs[idx]
        else:
            all_discs[disc] = class_numbers[0]
            class_numbers.remove(class_numbers[0])

    passive_mask = np.zeros_like(class_mask)
    class_numbers_padded = list(all_discs.values())
    for idx, bbox in enumerate(disc_bboxes):
        bottom, left, top, right = bbox
        passive_mask[bottom:top, left:right] = class_numbers_padded[idx]
    merged_mask = np.where(class_mask > 0, class_mask, passive_mask)
    #Must follow the equation no_vertebrae + no_discs - classes[0, 1] == unique - classes[0, 1], where #no_discs = no_vertebrae - 1.
    if 2 * no_verts - 3 != len(np.unique(merged_mask)) - 2: 
        return merged_mask, True
    else:
        return merged_mask, False
```

Segmenting degeneration loop (Runtime: ~2 minutes)
```{p}
# Execute the segmentation process on Sagittal T1 images.
fail_rates = {"Successful": 0, "Fail to load": 0, "Fail within loop": 0}
print(f"Labeling {len(st1_class_df.groupby(["series_id", "instance_number"]))} Sagittal T1 MRIs.")

for idx, chunk in st1_class_df.groupby(["series_id", "instance_number"]):
    segment_path = os.path.join("nnUNet_segments", str(chunk["study_id"].values[0]),
                                 str(chunk["series_id"].values[0]), f"{chunk["instance_number"].values[0]}.npy") 
    if os.path.isfile(segment_path):
        gray_mask = np.load(segment_path) #Is grayscale img.
    else:
        fail_rates["Fail to load"] = fail_rates["Fail to load"] + 1
        continue
    color_mask = auto_label_and_correct_mask(gray_mask, st1_classes)
    png_path = segment_path.replace("npy", "png").replace("nnUNet_segments", "train_png")
    sag_t1_mask, not_failed = label_sag_mask(path = png_path, mask = color_mask, chunk = chunk, classes = st1_classes, 
                                    class_numbers_verts = [32, 33, 34, 35, 36, 37])
    if not_failed:
        fail_rates["Successful"] = fail_rates["Successful"] + 1
        save_mask_as_png(sag_t1_mask, segment_path, 'nnUNet_segments_labeled')
    elif not not_failed:
        save_mask_as_png(sag_t1_mask, segment_path, 'nnUNet_segements_failed')
        fail_rates["Fail within loop"] = fail_rates["Fail within loop"] + 1
print(fail_rates)
```
An improvement of this model would be to increase the number of useful samples obtained from this algorithm, as over 60% of samples fed into the loop are rejected!



















