# 🚗 Self Driving Car - Semantic Segmentation with DeepLabV3+

Proyek ini membangun model semantic segmentation untuk kebutuhan self-driving car menggunakan arsitektur DeepLabV3+ berbasis PyTorch dan segmentation_models_pytorch.

Model dilatih untuk mengenali berbagai kelas pada jalan seperti lane, kendaraan, trotoar, dan objek lainnya.

## 📌 Features
* DeepLabV3+ dengan encoder ResNet50 (pretrained ImageNet)
* Class imbalance handling (class weights + sampler)
* Custom Class-Aware Cropping (fokus ke kelas langka)
* Advanced augmentation dengan Albumentations
* Mixed precision training (AMP)
* Kombinasi loss:
  ** CrossEntropy
  ** Dice Loss
  ** Focal Loss
* Early stopping + learning rate scheduler
* IoU evaluation metric

## 📂 Struktur Folder
```
SelfDrivingCar/
│
├── dataset/
│   ├── images_prepped_train/
│   └── annotations_prepped_train/
│
├── model/
│   └── deeplabv3plus_best.pth
│
└── train.py
```

## ⚙️ Installation

Install dependencies:
pip install -q segmentation-models-pytorch albumentations

## 🧠 Model Architecture
Model yang digunakan:

Architecture: DeepLabV3+
* Encoder: ResNet50
* Input size: 512x512
* Output: Multi-class segmentation mask

## 📊 Training Strategy
1. Class Imbalance Handling
* Menggunakan class weights
* WeightedRandomSampler untuk sampling seimbang
2. Custom Cropping
* ClassAwareCrop memastikan kelas langka muncul saat training
3. Data Augmentation
* Horizontal Flip
* Random Crop & Resize
* Motion Blur
* Gaussian Noise
* Brightness & Contrast

## ⏱️ Training Setup
* Epochs: 10
* Batch size: 8
* Optimizer: AdamW (lr=1e-4)
* Scheduler: ReduceLROnPlateau
* Early stopping: patience = 2

## 💾 Output
Model terbaik akan disimpan di:
```
/model/deeplabv3plus_best.pth
```
