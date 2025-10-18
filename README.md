# Face Recognition with PCA, LDA, and KNN

![Face Recognition](https://img.shields.io/badge/Project-Face%20Recognition-blueviolet) ![Python](https://img.shields.io/badge/Python-3.8%2B-blue) ![License](https://img.shields.io/badge/License-MIT-green)

A comprehensive machine learning project for face recognition using the ORL (AT&T) Database of Faces. This project implements *Principal Component Analysis (PCA)* and *Linear Discriminant Analysis (LDA)* for dimensionality reduction, followed by *K-Nearest Neighbors (KNN)* classification to identify individuals from facial images.

---

## 📖 Table of Contents

- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Features](#features)
- [Methodology](#methodology)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Visualizations](#visualizations)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgements](#acknowledgements)

---

## 🌟 Project Overview

This project demonstrates a face recognition pipeline using the ORL Database of Faces, which contains images of 40 distinct subjects. The goal is to preprocess facial images, reduce dimensionality using PCA and LDA, and classify them using a KNN classifier. The notebook includes detailed steps for data loading, preprocessing, model training, evaluation, and visualization of results.

### Objectives
- Load and preprocess grayscale face images from the ORL dataset.
- Apply PCA and LDA for feature extraction and dimensionality reduction.
- Train a KNN classifier to predict subject identities.
- Visualize eigenfaces, reconstructed images, predictions, and a confusion matrix.
- Provide functionality to predict the identity of a new face image.

---

## 📂 Dataset

The project uses the **[ORL Database of Faces](https://www.cl.cam.ac.uk/research/dtg/attarchive/facedatabase.html)** (also available on [Kaggle](https://www.kaggle.com/datasets/kasikrit/att-database-of-faces)). The dataset contains:

- *40 subjects* (labeled s1 to s40).
- *10 images per subject*, resulting in a total of 400 images.
- *Image format*: .pgm (Portable GrayMap).
- *Image size*: 92x112 pixels (grayscale).
- *Directory structure*:
  
  att_faces/
  ├── s1/
  │   ├── 1.pgm
  │   ├── 2.pgm
  │   └── ...
  ├── s2/
  └── ...
  

Ensure the dataset is placed in the correct directory (e.g., C:\Users\DELL\Desktop\Machine Learning\ML assignment 3\data) or update the DATA_PATH variable in the notebook.

---

## ✨ Features

- *Data Inspection and Loading*: Validates dataset structure and loads images into memory as flattened vectors.
- *Preprocessing*: Standardizes features using StandardScaler for better model performance.
- *Dimensionality Reduction*:
  - *PCA*: Extracts eigenfaces to reduce feature dimensionality while preserving variance.
  - *LDA*: Enhances class separability for better classification.
- *Classification*: Uses KNN to classify faces based on reduced features.
- *Visualizations*:
  - Sample face images.
  - Eigenfaces from PCA.
  - PCA vs. LDA reconstructed images.
  - KNN prediction results.
  - Confusion matrix heatmap.
- *Single Image Prediction*: Predicts the subject ID for a new face image.

---

## 🧠 Methodology

1. *Data Loading*:
   - Images are loaded from the ORL dataset using OpenCV (cv2) in grayscale mode.
   - Each image is flattened into a 1D vector (10304 features = 92 × 112).
   - Labels are assigned based on subject IDs (s1 to s40).

2. *Preprocessing*:
   - Features are standardized using StandardScaler to ensure zero mean and unit variance.

3. *Dimensionality Reduction*:
   - *PCA*: Reduces the feature space to a specified number of components (e.g., 50).
   - *LDA*: Projects data into a lower-dimensional space (39 components, constrained by the number of classes - 1).

4. *Classification*:
   - A KNN classifier is trained on the reduced feature set.
   - Performance is evaluated using accuracy and a confusion matrix.

5. *Visualization*:
   - Displays sample images, eigenfaces, reconstructed images, predictions, and a confusion matrix using Matplotlib and Seaborn.

6. *Prediction*:
   - A function is provided to predict the subject ID of a new image using the trained model.

---

## 🛠 Installation

### Prerequisites
- Python 3.8 or higher
- Jupyter Notebook or JupyterLab
- Required libraries:
  bash
  pip install numpy opencv-python matplotlib seaborn scikit-learn tqdm
  

### Steps
1. *Clone the Repository*:
   bash
   git clone https://github.com/yourusername/face-recognition-orl.git
   cd face-recognition-orl
   

2. *Install Dependencies*:
   bash
   pip install -r requirements.txt
   

3. *Download the Dataset*:
   - Download the ORL dataset from [Kaggle](https://www.kaggle.com/datasets/kasikrit/att-database-of-faces) or [Cambridge](https://www.cl.cam.ac.uk/research/dtg/attarchive/facedatabase.html).
   - Extract it to a directory (e.g., data/att_faces/).
   - Update the DATA_PATH variable in the notebook if necessary.

4. *Run the Notebook*:
   bash
   jupyter notebook mlass3_updated_modified.ipynb
   

---

## 🚀 Usage

1. *Open the Notebook*:
   Launch Jupyter Notebook and open mlass3_updated_modified.ipynb.

2. *Run All Cells*:
   Execute the cells sequentially to:
   - Load and inspect the dataset.
   - Preprocess the data.
   - Train PCA, LDA, and KNN models.
   - Generate visualizations.
   - Test predictions on a sample image.

3. *Predict on a New Image*:
   Use the predict_single_image function to classify a new .pgm image:
   python
   test_img_path = "path/to/your/image.pgm"
   img, pred = predict_single_image(test_img_path, knn, pca)
   plt.imshow(img, cmap='gray')
   plt.title(f"Predicted: s{pred+1}")
   plt.show()
   

---

## 📊 Results

- *Dataset Size*: 400 images (40 subjects × 10 images each).
- *Feature Space*: Original: 10304 features; PCA: ~50 components; LDA: 39 components.
- *Performance*: The KNN classifier's accuracy is evaluated on a test set, with results visualized via a confusion matrix.
- *Visualizations*:
  - Sample face images from the dataset.
  - Eigenfaces representing principal components.
  - Comparison of PCA and LDA reconstructed images.
  - KNN predictions vs. actual labels.
  - Confusion matrix heatmap for model performance.

---

## 📈 Visualizations

### Sample Face Images
Displays a 2x5 grid of sample images with their corresponding subject IDs.

### Eigenfaces
Shows the top 16 eigenfaces derived from PCA, representing the principal components of the face data.

### PCA vs. LDA Reconstruction
Compares the original image with reconstructions using PCA and LDA components.

### KNN Predictions
Visualizes predictions on test images, showing true and predicted subject IDs.

### Confusion Matrix
A heatmap illustrating the classification performance across all subjects.

---

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository.
2. Create a new branch (git checkout -b feature/your-feature).
3. Make your changes and commit (git commit -m "Add your feature").
4. Push to the branch (git push origin feature/your-feature).
5. Open a pull request.

Please ensure your code follows the project's structure and includes appropriate documentation.

---

## 📜 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- *ORL Database of Faces*: Provided by AT&T Laboratories Cambridge.
- *Libraries*: Thanks to the developers of NumPy, OpenCV, Matplotlib, Seaborn, Scikit-learn, and TQDM.
- *Inspiration*: This project is inspired by coursework in machine learning and computer vision.

---

*Happy Face Recognition!* 😊
