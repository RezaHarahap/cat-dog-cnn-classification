# Cat vs Dog Image Classification with CNN

## Overview
This project builds a **Convolutional Neural Network (CNN)** to classify images as either a **cat** or a **dog**.

The project covers data preparation, CNN training, validation, test evaluation, inference, and model export to multiple deployment formats.

## Dataset
- Total images: **25,000**
- Classes: Cat and Dog
- Split:
  - Training: 70%
  - Validation: 15%
  - Testing: 15%
- Image size used by the model: **150 × 150 pixels**

## Preprocessing
- Resize images to 150 × 150
- Normalize pixel values to 0–1
- Create train, validation, and test generators
- Use stratified splitting to preserve class balance

## Model Architecture
The CNN uses:
- Conv2D layers
- MaxPooling2D layers
- Flatten
- Dense layers
- Dropout
- Sigmoid output for binary classification

Optimizer: **Adam**  
Loss: **Binary Crossentropy**

Total parameters: approximately **4.83 million**.

## Results
After 15 epochs:
- Final training accuracy: approximately **97.56%**
- Final validation accuracy: approximately **85.87%**
- Test accuracy: approximately **85.62%**

The gap between training and validation/test accuracy suggests some overfitting, which provides a clear direction for future improvement.

## Model Export
The trained model is exported to:
- TensorFlow SavedModel
- TensorFlow Lite
- TensorFlow.js

This makes the project suitable for experimentation with deployment on web, mobile, or other TensorFlow-compatible environments.

## Tech Stack
- Python
- TensorFlow / Keras
- CNN
- Pandas
- NumPy
- PIL
- Matplotlib
- TensorFlow Lite
- TensorFlow.js
- Jupyter Notebook

## Future Improvements
- Stronger data augmentation
- Transfer learning with MobileNet / EfficientNet
- Early stopping
- Learning-rate scheduling
- Reduce model overfitting
- Add confusion matrix, precision, recall, and F1 score
- Build an interactive inference demo
