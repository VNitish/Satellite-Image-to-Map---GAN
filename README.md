# 🌍 Satellite-to-Map Translation using Pix2Pix GAN

PyTorch implementation of the [Pix2Pix](https://arxiv.org/abs/1611.07004) conditional GAN framework to translate satellite imagery into map-like representations. Built from scratch with a U-Net-based Generator and CNN Discriminator.

---

## 🔧 Features

- Trains a U-Net Generator with cGAN Discriminator
- Converts satellite images to maps (image-to-image translation)
- Implements Pix2Pix from scratch using PyTorch
- Includes pretrained weights and dataset download links

---

## 🧪 Results

| Satellite Image | → | Translated Map |
|-----------------|---|----------------|
| (Insert sample here) | | |

---

## 📁 Downloads

- 🔗 [Trained Weights (Generator & Discriminator)](URL_HERE)
- 🔗 [Sat2Map Dataset](URL_HERE)

---

## ⚙️ Training Details

| Hyperparameter       | Value         |
|----------------------|---------------|
| Batch Size           | 1             |
| Image Size           | 256×256       |
| Learning Rate        | 0.0002        |
| Optimizer β Values   | (0.5, 0.999)  |
| L1 Loss Weight (λL1) | 100           |

---

## 🧠 Key Concepts

### 🎲 What is Pix2Pix?

Pix2Pix is a **conditional GAN (cGAN)** where the Generator learns to map an **input image `x`** to an **output image `y`**, rather than generating from random noise.

- **Generator (U-Net)** learns: `G(x) → y`
- **Discriminator (CNN)** learns: `D(x, y) → real or fake`

## 📉 GAN Loss Function

The GAN loss for the Generator \( G \) and Discriminator \( D \) is defined as:

## GAN Loss Function

### Discriminator Loss
![GAN loss](Images/GAN_loss.png)

### Generator Loss
![Generator Loss](https://latex.codecogs.com/png.image?\dpi{120}L_G=-E_{x}[\log%20D(x,G(x))]%20+%20\lambda%20\cdot%20||y-G(x)||_1)

*Where λ controls the importance of L1 loss (e.g., 100).*

This enables **controllable image generation**.

### ⚙️ Generator: U-Net

- **Encoder**: Extracts feature representations from input images.
- **Decoder**: Translates encoded features into output maps.
- **Skip Connections**: Preserve spatial information to boost translation quality.

### 🛡️ Discriminator: PatchGAN

- Classifies if image pairs (x, y) are real or generated.
- Operates on image patches to ensure local realism.

---

## 📌 References

- [Pix2Pix Paper](https://arxiv.org/abs/1611.07004)
- [U-Net Paper](https://arxiv.org/abs/1505.04597)

---

## 🚀 How to Run

```bash
git clone https://github.com/your-username/satellite-pix2pix
cd satellite-pix2pix
python train.py
