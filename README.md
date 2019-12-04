#  Intracranial Hemorrhage Detection
#### Kristina Joos

![cover.png](attachment:../visuals/cover.png)


---
## Executive Summary

__Diagnosing Intracranial Hemorrhage is time-consuming and challenging__

Intracranial hemorrhage is bleeding that occurs in the head. Intracranial hemorrhages are a relatively common condition with many different causes (strokes, trauma, high blood pressure, aneurysms, blood clotting disorders). They can have dire consequences for the patient and often need immediate and intensive medical interventions.
The diagnosis, especially identifying location and type of bleeding, is difficult and time-consuming. Radiologists use computed tomography scans to localize and characterize the hemorrhage to determine the risks for the patient and if immediate surgery is required.

In this project, I will try to build a model to detect intracranial hemorrhage and the different subtypes, to help the medical community identify the presence, location, and subtype of bleeding to quickly and effectively treat affected patients.

__Data and Modeling__

The data set contains roughly 874 000 DICOM files, totaling approximately 460 GB of data.
Every file has six possible labels: The "any" label and 5 sub-labels. Several sub-labels can occur at once.
The label distribution is very unbalanced, having six times more samples without any hemorrhage than with hemorrhage.

Since the images come from different CT scans, the pixel arrays need to be rescaled to Hounsfield units.
To visualize the brain structures, we also need to "window" the images, meaning we focus only on pixels displaying a particular density of interest (brain structures).

Because the data set is big, memory space might not be big enough to load all the data for the model at once.
The data generator will generate the data needed for modeling on multiple cores in real-time and feed it into the model right after creation. 

I built a variety of different Convolutional Neural Network and compared their performance using a  multi-label logarithmic loss (the "any" label is weighted double) and the score my predictions received in the Kaggle Competition: RSNA Intracranial Hemorrhage Detection. I experimented with transfer learning, multi-head CNN, simple CNNs, oversampling of the positive "any" label, and different augmentation of the images. 

For the model with the best performance, I used Google's Inception V3 model as backbone with one additional Dense Layer, Global Average Pooling and Dropouts. This model has a validation loss of 0.0765, a test loss of 0.0823 (loss function: Weighted Log Loss) and it scored 0.39061 on Kaggle, and being in the top 30% of the leaderboard.





 


