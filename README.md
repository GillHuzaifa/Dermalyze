
# Dermalyze – AI-Powered Skin Lesion Detection App

Dermalyze is an Android application designed to detect and classify skin lesions using deep learning. Built with Kotlin and TensorFlow Lite, the app enables users to scan skin lesions and receive instant predictions directly on their smartphones. It is particularly useful in regions with limited access to dermatologists, providing a preliminary diagnosis tool that runs offline.

---

## Project Motivation

Skin conditions like melanoma can become life-threatening if not detected early. In many parts of the world, timely access to dermatological services is limited. Dermalyze was created to address this problem by offering a mobile, AI-based solution for early lesion detection using real-time image classification.

---

## Features

* Capture images of skin lesions using the phone camera
* Classify lesions into one of seven categories using a trained AI model
* PDF report generation for each scan
* Scan history tracking with image previews
* Firebase integration for user authentication and data storage

---

## Supported Lesion Classes

The model classifies images into the following seven categories, based on the HAM10000 dataset:

* Melanocytic nevi (nv)
* Melanoma (mel)
* Benign keratosis-like lesions (bkl)
* Basal cell carcinoma (bcc)
* Actinic keratoses / Intraepithelial carcinoma (akiec)
* Vascular lesions (vasc)
* Dermatofibroma (df)

---

## AI Model Overview

* **Dataset**: [HAM10000](https://www.kaggle.com/kmader/skin-cancer-mnist-ham10000)
* **Architecture**: MobileNetV2 (transfer learning)
* **Loss Function**: Focal Loss (to handle class imbalance)
* **Optimizer**: Adam (learning rate = 0.001)
* **Metrics**: Accuracy, Precision, Recall, F1 Score, Top-2 and Top-3 Accuracy
* **Model Format**: Exported to `.tflite` for mobile deployment

---

## Model Pipeline

1. **Data Preprocessing**

   * Resize images to 224×224 pixels
   * Normalize pixel values
   * Apply data augmentation techniques
   * One-hot encode labels

2. **Model Training**

   * Use MobileNetV2 as base (frozen layers)
   * Add custom classification head
   * Train using focal loss and Adam optimizer
   * Save best model using ModelCheckpoint
   * Evaluate on test set using multiple metrics

3. **Deployment**

   * Convert trained model to `.tflite`
   * Integrate with Android app using TensorFlow Lite Interpreter
   * Use Firebase for storing images, results, and authentication

---

## Evaluation Metrics

* **Accuracy**: Overall correct predictions
* **Precision & Recall**: Class-specific performance
* **F1 Score**: Balance between precision and recall
* **Confusion Matrix**: Visual comparison of predicted vs actual labels
* **Top-2 and Top-3 Accuracy**: Measures if the correct class is among top 2 or 3 predictions

---

## Source Reference

The AI model was adapted from the [Skin-Lesion-Analyzer project](https://github.com/vbookshelf/Skin-Lesion-Analyzer), with key improvements including:

* Integration of **Focal Loss**
* Enhanced data augmentation
* Export to TensorFlow Lite
* End-to-end mobile app deployment

---

## Getting Started

1. Clone this repository
2. Open the Android project in Android Studio
3. Add your `google-services.json` file for Firebase
4. Ensure `skin_model.tflite` is placed in the `assets` folder
5. Build and run the app on an Android device or emulator

---

## License

This project is licensed under the MIT License.
