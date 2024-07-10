
# MedGAN: Enhancing Medical Image Datasets through Generative Adversarial Networks

## Abstract
Medical image analysis often suffers from limited access to annotated datasets due to privacy concerns, high annotation costs, and the rarity of certain conditions. This paper introduces MedGAN, a generative adversarial network specifically engineered to augment medical imaging datasets by generating synthetic 128x128 images that mimic authentic scans. MedGAN presents a promising solution to the data scarcity and overfitting problems prevalent in medical image analysis.

## Methodology
### Image Preprocessing
- Images are resized to 128x128 pixels.
- Center cropping is applied to focus on primary image features.
- Images are converted to PyTorch tensors, scaling pixel intensity values to [0, 1].
- Tensors are normalized to a mean of 0.5 and standard deviation of 0.5 for each RGB channel, standardizing pixel values to [-1, 1].

### Generator Architecture
The generator transforms a latent vector into a 128x128 pixel medical image through a series of upsampling processes, using:
- Transposed convolutional layers for upscaling.
- Batch normalization to stabilize learning.
- ReLU activation functions to introduce non-linearity.
- A final Tanh activation function to normalize output pixel values to [-1, 1].

### Discriminator Architecture
The discriminator critically assesses the authenticity of generated images, using:
- Spectral normalized convolutional layers to reduce spatial dimensions while increasing feature map depth.
- Leaky ReLU activation functions to maintain gradient flow.
- Batch normalization to stabilize learning.
- A final sigmoid activation function to output the probability of an image being real or fake.

## Testing and Results
### Datasets Used
- **ISIC Dataset**: High-quality dermatological images for melanoma diagnosis.
- **Adenocarcinoma CT Scans**: Detailed lung nodule imaging.

### Metrics Used
- **Multi-Scale Gradient Magnitude Similarity Deviation (MS-GMSD)**: Evaluates similarity in gradient magnitude across multiple scales.
- **Learned Perceptual Image Patch Similarity (LPIPS)**: Quantifies perceptual differences using deep learning features.
- **Peak Signal-to-Noise Ratio (PSNR)**: Measures the ratio of signal power to corrupting noise.

### Results on ISIC Dataset
- Achieved PSNR: 12.89
- MSGMSD: 0.25
- LPIPS: 0.53

### Results on Adenocarcinoma Dataset
- Achieved PSNR: 11.80
- MSGMSD: 0.32
- LPIPS: 0.30

## Conclusion
The implementation of SNGAN for generating medical images demonstrates the potential to produce synthetic images that can augment existing datasets, enhancing diagnostic tools. Although the results indicate reasonable consistency with real images, further tuning and integration into clinical workflows are necessary for improved realism and practical utility.

For more detailed information, please refer to the [MedGAN paper](./MedGAN%20paper.pdf)
