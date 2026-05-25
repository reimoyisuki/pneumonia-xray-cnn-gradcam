# Pneumonia Detection from Chest X-Ray using Convolutional Neural Network (CNN) & Transfer Learning

Implementasi klasifikasi citra medis Chest X-Ray untuk mendeteksi pneumonia menggunakan pendekatan Deep Learning berbasis **Baseline CNN** dan **Transfer Learning ResNet50** dengan interpretabilitas model menggunakan **Grad-CAM**.


# 1. Deskripsi Proyek

Pneumonia merupakan penyakit infeksi paru-paru yang memerlukan diagnosis cepat dan akurat. Pada proyek ini dikembangkan sistem klasifikasi citra Chest X-Ray untuk membedakan dua kelas, yaitu:
- NORMAL
- PNEUMONIA

Pendekatan yang digunakan meliputi:
1. Baseline CNN (from scratch)
2. Transfer Learning menggunakan ResNet50 pretrained ImageNet
3. Fine-tuning parsial (`unfreeze layer4`)
4. Evaluasi multi-metrik
5. Interpretabilitas model menggunakan Grad-CAM


# 2. Arsitektur Model

## 1. Baseline CNN

Custom CNN sederhana dengan 3 convolution block:

- Conv2D(16) + ReLU + MaxPool
- Conv2D(32) + ReLU + MaxPool
- Conv2D(64) + ReLU + MaxPool
- Fully Connected Layer
- Dropout(0.5)
- Output 2 kelas

Input gambar:
- `224 × 224 × 3`
  

## 2. Transfer Learning - ResNet50

Menggunakan model:

- `torchvision.models.resnet50`
- pretrained ImageNet weights

Strategi training:

### Frozen Backbone
Seluruh backbone dibekukan dan hanya classifier head yang dilatih.

### Fine-Tuning Layer4
Dilakukan:
1. Warm-up classifier head
2. Unfreeze `layer4`
3. Fine-tuning dengan learning rate kecil


# 3. Dataset

Dataset yang digunakan:

## Chest X-Ray Pneumonia Dataset
Sumber:
- Kaggle
- Guangzhou Women and Children's Medical Center

Dataset terdiri dari:
- citra NORMAL
- citra PNEUMONIA


# Preprocessing

Tahapan preprocessing:
- Resize -> `224×224`
- Convert grayscale -> RGB (3 channel)
- Normalization (ImageNet mean/std)

Augmentasi data pada training set:
- Random Horizontal Flip
- Random Rotation (10°)
- Brightness adjustment
- Contrast adjustment


# 4. Training

## Baseline CNN

Training menggunakan:
- Adam Optimizer
- CrossEntropyLoss
- Learning rate = `0.001`

## Transfer Learning ResNet50

Menggunakan:
- FineTuner class
- ReduceLROnPlateau Scheduler
- Class Weights untuk mengatasi imbalance dataset
- Two-phase training

### Experiment 1
Frozen Backbone

### Experiment 2
Unfreeze Layer4

---

# 5. Evaluasi Model

Evaluasi dilakukan menggunakan:
- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC
- Confusion Matrix
- ROC Curve

Visualisasi tambahan:
- Prediction Samples
- Error Analysis
- Training Curves
- Model Comparison


# 6. Grad-CAM

Grad-CAM digunakan untuk interpretabilitas model dengan menghasilkan heatmap area citra yang paling berpengaruh terhadap prediksi model.

Target layer:
- `conv3` untuk Baseline CNN
- `layer4[-1].conv3` untuk ResNet50

Output:
- heatmap
- overlay heatmap pada citra asli
  

# 7. Hasil Akhir

## Baseline CNN

- Accuracy: 95.11%
- Precision: 95.65%
- Recall: 97.74%
- F1-score: 96.68%
- AUC-ROC: 0.989

## ResNet50 Fine-Tuning (Best Model)

- Accuracy: 98%
- F1-score: 98%

Hasil menunjukkan bahwa transfer learning dengan fine-tuning layer4 memberikan performa terbaik dibandingkan baseline CNN.


# 8. Future Work

Pengembangan lanjutan yang dapat dilakukan:
- Evaluasi pada dataset out-of-domain (CheXpert, MIMIC-CXR)
- Multi-class classification
- Lung segmentation menggunakan U-Net
- Eksperimen Vision Transformer (ViT)


# 9. Teknologi yang Digunakan

- Python
- PyTorch
- Torchvision
- Scikit-learn
- OpenCV
- Matplotlib
- Seaborn