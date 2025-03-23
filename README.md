## Table of Contents

- Common Test I. Multi-Class Classification
- Specific Test II. Lens Finding
- Specific Test III. Image Super-resolution
- Specific Test IV. Diffusion Models
- Specific Test VI. Foundation Model

---

### Common Test I. Multi-Class Classification
#### Architecture

- **Models**: ResNet50, EfficientNet-B0, DenseNet121 with ImageNet pre-trained weights.
- **Dataset**: Custom dataset with normalized images.
- **Training**: Cross-Entropy Loss, Adam optimizer.

#### Results

| **Model**       | **AUC-ROC Score** |
|-----------------|-------------------|
| DenseNet121     | 0.5092            |
| EfficientNet-B0 | 0.9859            |
| ResNet50        | 0.5093            |

**Visuals**:
- ![Task1](https://github.com/user-attachments/assets/66839f35-d3a3-40d9-bd3d-d0b672826d6e)
- ![Task1A](https://github.com/user-attachments/assets/5a8da167-21a3-46a8-bdca-63cb66f06d38)
- ![Task1ResNet](https://github.com/user-attachments/assets/ea2b48f8-025f-400a-aa76-5e2dae8bc4a2)
- ![Task1ResNetPer](https://github.com/user-attachments/assets/3578e741-d993-4ecf-904f-6888399fb1e0)

---

### Specific Test II. Lens Finding

#### Architecture

- **Models**: ResNet18, EfficientNet-B0 with ImageNet pre-trained weights.
- **Dataset**: Custom dataset with normalized images.
- **Training**: Binary Cross-Entropy Loss, Adam optimizer, weighted random sampling for class imbalance.

#### Results

| **Model**       | **AUC-ROC Score** |
|-----------------|-------------------|
| ResNet18        | 0.965             |
| EfficientNet-B0 | 0.959             |

**Visuals**:
- ![Task2EfficientNetROC](https://github.com/user-attachments/assets/d92a8d18-3f9e-445a-b49a-dfa9aca4c5f4)
- ![Task2ResNetAUC](https://github.com/user-attachments/assets/52ae7e2d-0201-44fc-93eb-19766a74cc26)

---

### Specific Test III. Image Super-resolution

#### Architecture

- **Model**: EDSR with residual blocks, convolutional layers, and pixel shuffle.
- **Training**: MSE Loss, Adam optimizer (lr=1×10⁻⁴), 10 epochs on synthetic data, 10 epochs fine-tuning on real-world data.

#### Results

**Synthetic Dataset**:
- MSE: 0.000059
- SSIM: 0.9777
- PSNR: 42.34 dB

**Real-World Dataset**:
- MSE: 0.001903
- SSIM: 0.7571
- PSNR: 29.65 dB

**Visuals**:
- ![Task3AImagesComparison](https://github.com/user-attachments/assets/0ffbaad1-0b23-4a2e-bc66-b0c59c363983)
- ![Task3BFinetune](https://github.com/user-attachments/assets/bc6d8df7-b143-42a4-a374-7f78624be678)

---

### Specific Test IV. Diffusion Models

#### Architecture

- **Model**: DDPM with UNet (sinusoidal embeddings, downsampling, upsampling).
- **Training**: MSE Loss, Adam optimizer (lr=1×10⁻⁴), 50 epochs, DDIM sampling.

#### Results

- **Training Loss**: 0.0611 to 0.0020.
- **FID Score**: Affected by OutOfMemoryError during generation.

---

### Specific Test VI. Foundation Model

#### Architecture

- **MAE**: Encoder with residual blocks, 75% patch masking, decoder with transposed convolutions.
- **Classifier**: MAE encoder, GAP, fully connected layer.
- **SR Model**: MAE encoder layers, transposed convolutions.

#### Results

- **MAE Loss**: 0.0619 to 0.0574.
- **Classifier Loss**: 0.0986 to 0.0000.
- **SR Metrics**: MSE: 0.0001, PSNR: 38.28 dB, SSIM: 0.9439.

**Visuals**:
- ![Task6A](https://github.com/user-attachments/assets/b9cf0a35-994e-451a-bf36-f70e459eb53a)
- ![Task6B](https://github.com/user-attachments/assets/acc43dda-e1a8-43cd-be38-55af69f9a24d)

---
