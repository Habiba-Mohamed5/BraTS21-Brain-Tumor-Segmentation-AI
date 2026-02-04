# 🧠 BraTS 2021: 3D Brain Tumor Segmentation Pipeline

## 🚀 Overview
This repository contains a high-performance **3D medical imaging pipeline** developed for the BraTS 2021 Challenge. The project focuses on the precise segmentation of brain tumor sub-regions (Necrotic Core, Peritumoral Edema, and Enhancing Tumor) using advanced deep learning and post-processing techniques.

---

## 🛠️ Technical Stack
* **Frameworks:** `PyTorch`, `MONAI` (Medical Open Network for AI).
* **Core Libraries:** `nibabel` for NIfTI processing, `scipy` for morphological operations.
* **Architecture:** * **3D Ensemble:** A Weighted Voting system combining multiple model predictions.
    * **Confidence Weighting:** Assigned a **70%** weight to the primary high-scoring model to ensure result stability.

---

## ⚙️ Methodology & Optimization
### 1. Hybrid Loss Function
To handle extreme **Class Imbalance**, we utilized a combo loss:
* **Dice Loss:** For global overlap optimization.
* **Focal Loss:** To focus training on hard-to-segment tumor boundaries.

### 2. Post-processing (The Secret Sauce)
* **Binary Hole Filling:** Automated filling of internal segmentation gaps to ensure structural integrity.
* **Label-Specific Thresholding:** Applied a dynamic threshold of **0.45** for the **Enhancing Tumor** label to maximize recall in critical regions.

---

## 📊 Results & Visualization
* **Top Dice Score:** Achieved an optimized score of **~0.48** through weighted ensembling and morphological refinement.
* **3D Reconstruction:** Automated volumetric visualization of the tumor structure.
* **Spatial Analysis:** Z-axis distribution analysis to validate anatomical consistency across slices.



---

## 📂 Project Structure
```text
├── data/           # Data loading & Pre-processing
├── models/         # Model architectures (U-Net/Swin-UNETR)
├── losses/         # Custom Hybrid Loss functions
├── trainer/        # Training loops & Checkpointing logic
├── presentation/   # Project PDF and Slides
└── main.py         # Final inference pipeline
