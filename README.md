#  Satellite to Map Translation with Pix2Pix GAN

A PyTorch implementation of a **Pix2Pix-style GAN** that transforms satellite imagery into corresponding map views. This project builds the model architecture from scratch using U-Net for the generator and a conditional discriminator for training.

**Paper Reference**: [Image-to-Image Translation with Conditional Adversarial Networks (Isola et al., 2016)](https://arxiv.org/abs/1611.07004)

---

## Sample Output

![Sample Output](path_to_sample_image.png) <!-- Replace with actual image path -->

---

## 📦 Pretrained Models

- [Download Trained Generator & Discriminator Weights](#)
- [Download Sat2Map Dataset](#)

---

## Hyperparameters Used

| Parameter         | Value        |
|------------------|--------------|
| Batch Size       | 1            |
| Image Resolution | 256 × 256    |
| Learning Rate    | 0.0002       |
| Adam Betas       | (0.5, 0.999) |
| L1 Loss Weight   | 100          |

---

## Understanding cGANs

Unlike classic GANs that generate images from random noise `z`, **Conditional GANs** (cGANs) take both noise and an input image `x` to generate an output `G(z|x)`. This ensures the generated image is not just realistic but also relevant to the input.

The discriminator evaluates pairs `(x, y)` and decides whether `y` is a plausible translation of `x`. This makes cGANs ideal for tasks like satellite-to-map translation.

---

## Generator - U-Net Architecture

- Uses an **Encoder-Decoder** design with skip connections.
- Based on the [U-Net model](https://arxiv.org/abs/1505.04597), popular in image segmentation.
- Retains spatial features via connections between encoder and decoder layers.

> This project uses a U-Net adapted for 256x256 images.

---

## Discriminator - PatchGAN

- A convolutional classifier that judges small patches of the image.
- Inputs are the **concatenation** of the source (satellite) and target (map) images.
- Outputs a grid where each cell evaluates a local patch as real or fake.

---

## Project Structure (Recommended)
.
├── data/
│ └── sat2map/
├── checkpoints/
├── outputs/
├── models/
├── utils/
├── train.py
├── test.py
└── README.md


---

## To-Do

- [ ] Upload pretrained weights  
- [ ] Add visual training logs  
- [ ] Extend model to other datasets (e.g. facades, edges2shoes)

---

## License

This repository is intended for educational and research purposes. See [LICENSE](LICENSE) for more details.
