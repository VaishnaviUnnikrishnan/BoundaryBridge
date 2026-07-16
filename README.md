# Boundary Bridge
### Boundary-Aware Document Image Segmentation using Dual-Task U-Net

Boundary Bridge is a deep learning framework for document image segmentation that improves segmentation accuracy by simultaneously learning **semantic regions** and **document boundaries**. The project implements a **Boundary-Aware U-Net** architecture with robust annotation fusion, advanced data augmentation, and automated inference to accurately segment complex document layouts.

---

## Project Overview

Traditional semantic segmentation models often struggle to accurately identify object boundaries, leading to merged regions and imprecise masks. BoundaryEdge addresses this limitation by introducing a dual-task learning strategy that predicts both:

- **Semantic segmentation masks**
- **Boundary (edge) maps**

The boundary supervision helps the network learn sharper object contours, resulting in more precise document segmentation.

---

## Key Features

- Boundary-Aware U-Net architecture
- Dual-output learning (Segmentation + Boundary Prediction)
- Majority voting for multi-annotator label fusion
- IoU-based noisy annotation handling
- Advanced image augmentation pipeline
- Cosine Annealing Learning Rate Scheduler
- Automatic checkpoint saving
- Batch inference on unseen test images
- Submission-ready mask generation

---

## Dataset

The model is trained on document images with multiple expert annotations.

### Annotation Pipeline

- Three independent annotations per image
- Majority voting to generate robust ground-truth masks
- IoU agreement analysis for annotation quality assessment
- Noise-aware training using low-confidence label detection

---

## Model Architecture

```
                Input Image
                     │
          ┌──────────▼──────────┐
          │ Boundary-Aware U-Net │
          └──────────┬──────────┘
                     │
          ┌──────────┴──────────┐
          │                     │
 Segmentation Head      Boundary Head
          │                     │
 Semantic Mask        Edge Probability Map
```

The network jointly optimizes both tasks using a combined loss function, encouraging better localization of document boundaries.

---

## Training Pipeline

1. Data Loading
2. Annotation Fusion
3. Image Augmentation
4. Boundary Mask Generation
5. Boundary-Aware U-Net Training
6. Validation
7. Model Checkpointing
8. Test Image Inference
9. Submission Generation

---

## Technologies Used

- Python
- PyTorch
- OpenCV
- Albumentations
- NumPy
- Pandas
- Torchvision
- Matplotlib

---

## Repository Structure

```
BoundaryEdge/
│
├── colab_train.ipynb        # Complete training pipeline
├── README.md
├── checkpoints/             # Saved model weights
├── predictions/             # Generated segmentation masks
├── outputs/                 # Training outputs
└── requirements.txt
```

---

## Installation

```bash
git clone https://github.com/<username>/BoundaryEdge.git

cd BoundaryEdge

pip install -r requirements.txt
```

---

## Running the Notebook

Open

```
colab_train.ipynb
```

and execute all cells sequentially.

The notebook performs:

- Dataset preprocessing
- Annotation fusion
- Model training
- Validation
- Checkpoint generation
- Test prediction
- Submission file creation

---

## Results

BoundaryEdge improves segmentation quality by leveraging explicit boundary supervision, enabling:

- Sharper document boundaries
- Reduced region merging
- Improved localization of fine structures
- More robust predictions on noisy annotations

---

## Future Improvements

- Attention-based Boundary U-Net
- Transformer encoder backbone
- Deep supervision
- Mixed precision training
- Test Time Augmentation (TTA)
- Boundary refinement using CRFs

---

## Applications

- Document Layout Analysis
- OCR Preprocessing
- Historical Document Digitization
- Medical Image Segmentation
- Satellite Image Segmentation
- Instance Segmentation Pipelines

---

## Results

<img width="412" height="130" alt="image" src="https://github.com/user-attachments/assets/48d9fb9d-0b94-4ff9-b6ae-0919ff20e27a" />
<img width="397" height="307" alt="image" src="https://github.com/user-attachments/assets/3d22217b-c7ac-4a32-bf83-d68baadceea7" />
<img width="396" height="303" alt="image" src="https://github.com/user-attachments/assets/21719232-1806-47d4-886f-6379bc255927" />

---

