# Computer Vision Week 3

This repository demonstrates **image blurring using linear filtering**, implemented in two mathematically equivalent ways:

1. **Spatial-domain convolution**
2. **Frequency-domain filtering using the Fourier transform**

The goal is to verify, both conceptually and numerically, the result taught in classical image processing:

> **Convolution in the spatial domain is equivalent to multiplication in the Fourier domain.**

This equivalence is shown explicitly using real images and quantitative comparisons.

---

---

## Dataset

The images used in this project are located in the **`sample_images/`** directory.

- These images are taken from an **autonomous driving dataset**
- They depict **murals and large wall paintings** captured in urban driving scenes
- The images are grayscale-converted and normalized before processing

The dataset is used purely for educational purposes to demonstrate filtering behavior on real-world imagery.

---

## Methodology

### 1. Spatial-Domain Filtering

- A **Gaussian smoothing filter** is defined as a discrete convolution kernel
- The image is padded to handle boundary effects
- Convolution is performed directly using the discrete convolution definition
- The kernel is explicitly flipped to ensure true convolution (not correlation)

This method follows the definition of a **linear shift-invariant system (LSIS)** implemented via convolution.

---

### 2. Frequency-Domain Filtering

- The same image and Gaussian kernel are zero-padded to identical sizes
- The kernel is centered correctly before applying the Fourier transform
- Both the image and kernel are transformed using the **2D Discrete Fourier Transform (DFT)**
- Filtering is performed by **pointwise multiplication** in the frequency domain
- The inverse DFT reconstructs the spatial-domain result

---

## Verification

The outputs of the two methods are compared pixel-by-pixel.

- Maximum absolute differences are on the order of **\(10^{-15}\)**
- Differences arise only from floating-point roundoff
- This confirms **numerical equivalence** of the two approaches

---

## Implementation

All code is contained in **`main.ipynb`**, which:

- Loads and preprocesses all images
- Applies Gaussian blurring in the spatial domain
- Applies equivalent filtering in the Fourier domain
- Visualizes results for all images
- Computes quantitative error metrics to verify equivalence

The notebook is self-contained and can be run end-to-end.

---

## Key Takeaway

This project illustrates a fundamental result in image processing:

> **Spatial convolution and frequency-domain multiplication are mathematically identical operations when implemented correctly.**

By carefully handling padding, kernel alignment, and output cropping, both approaches produce the same filtered image.

---

## Requirements

- Python 3
- NumPy
- OpenCV
- Matplotlib
- Jupyter Notebook

---

## Notes

- The Gaussian kernel size is chosen to be odd to ensure a well-defined center
- The standard deviation (σ) controls the degree of smoothing
- The implementation follows classical definitions as taught in first-principles computer vision and signal processing courses

---

## License

This repository is intended for academic and educational use.
