# Brain Tumor Detection from MRI Images using EfficientNet-B0

## Project Overview

This project presents a deep learning-based approach for detecting brain tumors from MRI images. Leveraging transfer learning with EfficientNet-B0, the model classifies MRI scans into two categories: tumor present (“yes”) and no tumor (“no”).

The workflow covers the entire machine learning pipeline, including data preparation, preprocessing, model training, evaluation, prediction, interpretability, and model persistence. The project emphasizes both performance and explainability, which are critical in medical imaging applications.

---

## Problem Statement

Brain tumors are life-threatening conditions that require early and accurate diagnosis. MRI imaging is a standard diagnostic tool, but interpretation depends heavily on expert radiologists.

Manual analysis can be:

* Time-consuming
* Subject to human error
* Limited in scalability

There is a need for an automated system that can assist in:

* Rapid detection of tumors
* Consistent and accurate classification
* Providing visual insights into model decisions

---

## Project Objective

The objectives of this project are:

* To develop a deep learning model capable of detecting brain tumors from MRI images
* To utilize transfer learning for improved performance on limited medical data
* To address class imbalance in the dataset
* To evaluate the model using robust performance metrics
* To implement model interpretability using Grad-CAM
* To build a reusable and deployable model pipeline

---

## Dataset Description

The dataset consists of MRI brain scans divided into two classes:

* **Yes**: Images containing brain tumors
* **No**: Images without brain tumors

### Class Distribution

![Class Distribution](https://github.com/Phenomkay/Brain-Tumor-Detection-from-MRI-Images-using-EfficientNet-B0/blob/43eb1a478a117b354521d9ed146e4059ccc42613/class%20distribution.png)

The dataset contains:

* 155 tumor images
* 98 non-tumor images

**Analysis:**
The dataset is slightly imbalanced, with more tumor samples than non-tumor samples. This imbalance can bias the model toward predicting the majority class. To mitigate this, class weights were applied during training.

---

## Data Exploration

### Tumor Samples

![Tumor Samples](sandbox:/mnt/data/03a78830-baf1-4394-8adc-be2fa7a28502.png)

### Non-Tumor Samples

![Non-Tumor Samples](sandbox:/mnt/data/b2662329-38ab-4757-88e5-0b5ac2cac679.png)

**Insights:**

* Tumor images exhibit irregular bright regions, indicating abnormal tissue growth
* Non-tumor images show more symmetrical and consistent brain structures
* There is variation in orientation, contrast, and intensity across images

These observations justify the use of augmentation techniques to improve generalization.

---

## Data Preprocessing

The following preprocessing steps were applied:

* Resizing images to 224 × 224 pixels
* Normalization using ImageNet mean and standard deviation
* Data augmentation:

  * Random horizontal flipping
  * Random rotation

**Purpose:**
These steps were performed in order to standardize inputs, reduce overfitting, and improve the model’s ability to generalize across unseen data.

---

## Model Architecture

The model is built using EfficientNet-B0, a pre-trained convolutional neural network.

### Key Modifications

* The final classification layer was replaced with a fully connected layer for binary classification
* The model was fine-tuned on the MRI dataset

### Justification

EfficientNet-B0 was selected due to:

* Its efficiency in terms of parameters and computation
* Strong feature extraction capabilities
* Proven performance on image classification tasks

---

## Training Strategy

* **Device**: CPU (no GPU acceleration available)
* **Optimizer**: AdamW
* **Learning Rate**: 0.0001
* **Loss Function**: Weighted Cross-Entropy Loss
* **Epochs**: 10
* **Batch Size**: 32

### Handling Class Imbalance

Class weights were applied:

* Tumor class assigned higher importance
* Non-tumor class assigned lower weight

This was done in order to balance the influence of each class during training.

---

## Model Performance

### Accuracy Over Epochs

![Accuracy Curve](sandbox:/mnt/data/4dfec982-1371-42d4-b12e-944b0a15e2ec.png)

**Observations:**

* Rapid improvement in early epochs due to transfer learning
* Validation accuracy stabilizes at approximately **96%**
* Training accuracy approaches 100%

**Analysis:**

* The model learns effectively from the dataset
* The small gap between training and validation accuracy indicates mild overfitting, but overall generalization remains strong

---

## Prediction Results

![Predictions](sandbox:/mnt/data/2f888729-f00e-4e31-ab23-f1865042d588.png)

**Observations:**

* Most predictions are correct (green labels)
* The model demonstrates strong classification capability
* Very few misclassifications

**Interpretation:**

The model is reliable in distinguishing between tumor and non-tumor images, achieving high predictive performance on unseen validation data.

---

## Model Interpretability (Grad-CAM)

![Grad-CAM Heatmap](sandbox:/mnt/data/6f0b3bdb-1c60-4f3b-9b38-3f8c2b7d7e7a.png)

**Analysis:**

* The heatmap highlights regions that influenced the model’s decision
* High-intensity regions correspond to areas likely containing tumors
* This provides transparency and increases trust in the model

Grad-CAM is particularly important in medical applications where explainability is critical.

---

## Model Inference

The model outputs:

* Predicted class (“yes” or “no”)
* Confidence score

Example:

* Prediction: Tumor present
* Confidence: 95%

---

## Model Persistence

The trained model was saved along with:

* Model weights
* Class labels
* Architecture information

This enables:

* Easy reuse for inference
* Integration into applications such as web-based tools

---

## Key Achievements

* Developed a complete deep learning pipeline for medical image classification
* Achieved approximately **96% validation accuracy**
* Successfully applied transfer learning using EfficientNet-B0
* Addressed class imbalance using weighted loss
* Implemented Grad-CAM for model interpretability
* Built a reusable and deployable model

---

## Limitations

* Dataset size is relatively small
* Slight class imbalance persists
* Model trained on CPU, limiting training speed
* Generalization to real-world clinical datasets requires further validation

---

## Future Improvements

* Train on larger and more diverse datasets
* Use advanced augmentation techniques
* Experiment with alternative architectures (ResNet, DenseNet)
* Deploy as a web application (e.g., Streamlit)
* Extend to multi-class tumor classification
* Incorporate segmentation for precise tumor localization

---

## Conclusion

This project demonstrates the effectiveness of deep learning in detecting brain tumors from MRI images. By leveraging transfer learning and proper preprocessing techniques, the model achieves high accuracy while maintaining reasonable generalization.

The integration of Grad-CAM enhances interpretability, making the model more suitable for real-world healthcare applications. Overall, this work provides a strong foundation for building AI-assisted diagnostic tools and highlights the potential of computer vision in medical imaging.
