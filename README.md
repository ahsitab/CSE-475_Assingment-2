# Self-Supervised Learning for SylFishBD: A Comprehensive Study

## 📖 Overview
This repository contains a comprehensive exploration of self-supervised learning techniques applied to the SylFishBD dataset. The project implements and compares multiple state-of-the-art SSL methods including Pseudo-Labeling, SimCLR, MoCo v2, and DINOv3 for fish species classification tasks.

## 🎯 Project Goals
- Implement and compare various self-supervised learning approaches
- Evaluate SSL methods on the SylFishBD fish classification dataset
- Explore multi-phase training strategies for SSL
- Benchmark different architectures and frameworks

## 📂 Repository Structure

### 1. **SSL with Pseudo-Labeling**
**File:** `cse-475-ssl-pseudo-labeling-for-sylfish-bd.ipynb`
- Semi-supervised learning approach using pseudo-labeling
- Iterative labeling of unlabeled data
- Confidence thresholding for reliable pseudo-labels

### 2. **SimCLR Implementation**
**Phase 1:** `cse-475-phase-1-self-sl-simclr-for-sylfish-bd.ipynb`
- Contrastive learning framework
- Positive pair generation through augmentations
- Projection head for representation learning

**Phase 2:** `cse-475-phase-2-self-sl-simclr-for-sylfish-bd.ipynb`
- Fine-tuning phase on learned representations
- Linear evaluation protocol
- Transfer learning to downstream tasks

### 3. **MoCo v2 Implementation**
**File:** `cse-475-phase-1-self-sl-moco-v2-for-sylfish-bd.ipynb`
- Momentum Contrast framework
- Dynamic dictionary with queue
- Momentum encoder updates
- Key encoder maintenance

### 4. **DINOv3 Implementation**
**File:** `cse-475-dinov3-self-sl-sylfishbd-dataset.ipynb`
- Self-distillation with no labels framework
- Vision transformer backbone
- Multi-crop strategy
- Knowledge distillation approach

## 🏗️ Model Architectures

### **SimCLR Architecture**
```
Input Image → Augmentation (Random Crop, Color Jitter, etc.)
    ↓
Base Encoder (ResNet-50)
    ↓
Projection Head (MLP)
    ↓
Contrastive Loss (NT-Xent)
```

### **MoCo v2 Architecture**
```
Query Encoder (ResNet-50) ← Momentum Update → Key Encoder (ResNet-50)
    ↓                                ↓
Projection Head                 Projection Head
    ↓                                ↓
Contrastive Loss against Dictionary Queue
```

### **DINOv3 Architecture**
```
Student Network (ViT) ← Gradient Flow → Teacher Network (ViT)
    ↓                      ↑
Multi-crop Images   EMA Update
    ↓
Self-Distillation Loss
```

### **Pseudo-Labeling Workflow**
```
Labeled Data → Teacher Model → Predict Unlabeled Data
    ↓               ↓
Training    Confidence Filtering
    ↓               ↓
Student Model ← Pseudo-Labels
```

## 📊 Dataset: SylFishBD
- **Source:** Kaggle dataset `syfish-bd`
- **Content:** Fish species native to Bangladesh
- **Classes:** Multiple fish species categories
- **Use:** SSL pretraining and fine-tuning evaluation

## 🚀 Training Details

### **Hardware Configuration**
- **Runtime:** 3 minutes 12 seconds
- **GPU:** T4 x2 (Kaggle environment)
- **Framework:** PyTorch

### **Training Strategies**
1. **Two-Phase Training:** 
   - Phase 1: Self-supervised pretraining
   - Phase 2: Supervised fine-tuning

2. **Evaluation Protocols:**
   - Linear evaluation (frozen features + linear classifier)
   - Fine-tuning evaluation (end-to-end training)
   - Transfer learning to downstream tasks

## 📈 Results & Predictions

### **Sample Prediction**

![Prediction Example](prediction_example.png)
*Example of model prediction on SylFishBD test images*

### **Key Findings**
- Contrastive methods (SimCLR, MoCo) show strong representation learning
- DINOv3 provides excellent transfer capabilities
- Pseudo-labeling effectively utilizes unlabeled data
- Multi-phase training improves final accuracy

## 👥 Authors
1. **Asfar Hossain Sitab** (2022-3-60-275)
2. **Parmita Hossain Simia** (2022-3-60-253)
3. **Md. Omor Faruq** (2022-1-60-335)
4. **Ahnaf Ahmed** (2022-3-60-151)

## 📜 License
This project is released under the **Apache 2.0** open source license.

## 🔗 Kaggle Notebooks
All implementations are available as interactive Kaggle notebooks:
- [Pseudo-Labeling Implementation](https://www.kaggle.com/code/asfarhossainsitab/cse-475-ssl-pseudo-labeling-for-sylfish-bd)
- [SimCLR Phase 1](https://www.kaggle.com/code/asfarhossainsitab/cse-475-phase-1-self-sl-simclr-for-sylfish-bd)
- [SimCLR Phase 2](https://www.kaggle.com/code/asfarhossainsitab/cse-475-phase-2-self-sl-simclr-for-sylfish-bd)
- [MoCo v2 Implementation](https://www.kaggle.com/code/asfarhossainsitab/cse-475-phase-1-self-sl-moco-v2-for-sylfish-bd)
- [DINOv3 Implementation](https://www.kaggle.com/code/asfarhossainsitab/cse-475-dinov3-self-sl-sylfishbd-dataset)

## 💻 Usage
To run these notebooks:
1. Clone the repository or access via Kaggle
2. Ensure access to the SylFishBD dataset
3. Run cells sequentially in any Kaggle notebook environment
4. Modify hyperparameters as needed for your specific use case

## 🤝 Contributing
This project serves as a comprehensive reference for self-supervised learning implementations. Feel free to experiment with different architectures, datasets, or training strategies based on this foundation.

## 📚 References
- SimCLR: A Simple Framework for Contrastive Learning
- MoCo: Momentum Contrast for Unsupervised Visual Representation Learning
- DINO: Emerging Properties in Self-Supervised Vision Transformers
- Pseudo-Label: The Simple and Efficient SSL Method
