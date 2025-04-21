
# **Image Segmentation using U-Net Architecture on Oxford-IIIT Pet Dataset**

---

### 📌 Project Overview:

This project focuses on **image segmentation**, a crucial task in computer vision where the goal is to classify each pixel of an image into a meaningful class. We implemented a **U-Net based convolutional neural network** to segment pet images from the **Oxford-IIIT Pet Dataset**, identifying not just the pet in an image but also the precise boundaries and regions associated with it.

---

### 🔍 What is Image Segmentation?

Image segmentation is a technique in computer vision that involves dividing an image into multiple segments (sets of pixels) to simplify or change the representation of an image into something more meaningful and easier to analyze. Unlike image classification, which labels an entire image, segmentation provides pixel-level annotations, enabling detailed understanding of image content.

There are typically three types:
- **Semantic Segmentation** – Labels each pixel with a class (e.g., pet vs. background).
- **Instance Segmentation** – Differentiates between separate objects of the same class.
- **Panoptic Segmentation** – Combines both.

In this project, we use **semantic segmentation** to label each pixel of an image as either pet, background, or outline.

---

### 🧱 U-Net Architecture Overview:

U-Net is a **convolutional neural network architecture** specifically designed for biomedical and image segmentation tasks. It was introduced by Olaf Ronneberger et al. in 2015.

It has a **U-shaped structure**, consisting of two paths:

1. **Contracting Path (Encoder)**:  
   - Downsamples the image using convolutional layers followed by max pooling.  
   - Captures the context and features at multiple levels.

2. **Expanding Path (Decoder)**:  
   - Upsamples the image back to the original size using transposed convolutions.  
   - Combines features from the encoder using skip connections.  
   - Helps in precise localization using contextual information.

The **skip connections** are a key feature of U-Net, allowing the decoder to retain high-resolution features lost during downsampling.

---

### 🐶 Dataset Description: Oxford-IIIT Pet Dataset

The **Oxford-IIIT Pet Dataset** contains:
- **37 categories of pets** (different dog and cat breeds)
- Around **7,000 labeled images**
- Each image comes with:
  - The original pet image
  - A **segmentation mask** which highlights three regions:
    - Class 1: Pet
    - Class 2: Border of the pet
    - Class 0: Background

This dataset is ideal for segmentation tasks because of its well-annotated masks and variability in poses, lighting, and backgrounds.

---

### ⚙️ How the Model Works:

1. **Data Preparation**:
   - Loaded and preprocessed the images and their corresponding masks.
   - Resized to 128x128 and normalized the values.
   - Created training and test datasets using TensorFlow’s `tf.data` pipeline.

2. **Model Architecture**:
   - Constructed the U-Net with multiple convolutional and pooling layers for the encoder.
   - Used upsampling and concatenation in the decoder to restore image size.
   - Final layer outputs a 3-channel prediction corresponding to the mask classes.

3. **Training**:
   - Used `sparse_categorical_crossentropy` loss for multi-class segmentation.
   - Optimized using Adam optimizer.
   - Trained for 20 epochs with batch size 64.

4. **Prediction & Visualization**:
   - The model outputs a segmentation map.
   - Predictions are visualized alongside input images and ground truth masks.

---

### 🎯 Applications:

- Medical image segmentation (MRI, CT scans)
- Autonomous driving (road/lane detection)
- Robotics (object localization)
- Animal recognition and monitoring

---

