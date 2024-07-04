# Malaria Detection Capstone Project

This project simulates a real-world problem-solving experience. This capstone project is part of the [MIT Professional Education](https://www.mygreatlearning.com/mit-data-science-program) Applied Data Science Program.

### Problem Definition

Malaria is a contagious disease caused by Plasmodium parasites that are transmitted to humans through the bites of infected female Anopheles mosquitoes. The parasites enter the blood and begin damaging red blood cells (RBCs) that carry oxygen, which can result in respiratory distress and other complications. The lethal parasites can stay alive for more than a year in a person’s body without showing any symptoms. Therefore, late treatment can cause complications and could even be fatal. Almost 50% of the world’s population is in danger from malaria. There were more than 229 million malaria cases and 400,000 malaria-related deaths reported over the world in 2019. Children under 5 years of age are the most vulnerable population group affected by malaria; in 2019 they accounted for 67% of all malaria deaths worldwide. Traditional diagnosis of malaria in the laboratory requires careful inspection by an experienced professional to discriminate between healthy and infected red blood cells. It is a tedious, time-consuming process, and the diagnostic accuracy (which heavily depends on human expertise) can be adversely impacted by inter-observer variability.

### Objectives

An automated system can help with the early and accurate detection of malaria. Applications of automated classification techniques using Machine Learning (ML) and Artificial Intelligence (AI) have consistently shown higher accuracy than manual classification. It would therefore be highly beneficial to propose a method that performs malaria detection using Deep Learning Algorithms.

### Data

There are a total of 24,958 train and 2,600 test [cell images](https://drive.google.com/file/d/1n3o1Xghpy9ufZwHkQFE5l5d9sUHQOUWM/view) (colored) that we have taken from microscopic images. 

These images are of the following categories:
1. Parasitized: The parasitized cells contain the Plasmodium parasite which causes malaria
2. Uninfected: The uninfected cells are free of the Plasmodium parasites

### Results

The final proposed model is Model 2 with Batch Normalization.

The model achieves about 97% accuracy on the test data, comparable to the validation data, indicating generalized performance. It has a high recall range, identifying ~99% of parasitized cells and ~95% of uninfected cells. This high recall for parasitized cells is crucial since identifying infected cells is more important. The model mainly confuses uninfected cells as parasitized. However, it takes longer to train compared to transfer learning techniques.

### Algorithms and models analysis

Data preprocessing: 
* Loading in Batches - loading the data in smaller batches allows you to train models on datasets that don't fit entirely in memory.
* Resize image & Normalization - normalization makes the training faster and reduces the chances of getting stuck at local optima.
It also helps to avoid exploding gradient problems in CNN.
* Applying Gaussian Blurring - for better training and feature highlight.

Models:
* Base Model - the very basic CNN model we compare other models to
* Model 1 - model with additional layers
* Model 2 - similar to model 1 but with regularization Dropout & BatchNormalization
* Model 3 - model with data augmentation
* Model 4 model VGG16 - transfer learning, pre-trained VGG16 model
* Model 5 model EfficientNetB0 - transfer learning, EfficientNetB0 offers a balance between model size and performance
* Ensemble - ensemble model based on the 3 best-performing models Model 2, model VGG16, EfficientNetB0

Results:
| Model         | Loss     | Accuracy   |
|---------------|----------|------------|
| CNN Model Base| 0.666585 | 0.613846   |
| CNN Model 1   | 0.637147 | 0.643846   |
| CNN Model 2   | 0.070281 | 0.973077   |
| CNN Model 3   | 0.663250 | 0.611538   |
| CNN Model 4   | 0.428520 | 0.798846   |
| CNN Model 5   | 0.374634 | 0.836538   |
| Ensemble      | 0.254677 | 0.911923   |




