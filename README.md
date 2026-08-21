
# Lightweight Session Dependent Hybrid Image Encryption Using CNN Driven Dynamic Seed Generation and Bidirectional Diffusion

## Overview

This repository contains the implementation of the proposed lightweight session-dependent hybrid image encryption framework for secure image transmission.

The implementation integrates one-time session key generation, domain-separated key derivation, CNN-driven dynamic seed generation, reversible modular transformation, hybrid BNM-Hénon chaotic keystream generation, Fisher-Yates permutation, block/channel permutation, and bidirectional diffusion.

The same source file contains both the encryption and decryption procedures.

## Method

The encryption process consists of the following major stages:

1. Input image loading and preprocessing.
2. One-time 256-bit session key generation from conditioned runtime environmental noise.
3. Domain-separated key derivation for the CNN, BNM, Hénon, permutation, forward diffusion, and backward diffusion stages.
4. CNN-driven dynamic seed generation using a lightweight 1D CNN.
5. Generation of dynamic position-dependent parameters (a_i) and (b_i).
6. Reversible modular transformation of the image pixels.
7. Generation of BNM and Hénon chaotic sequences.
8. Hybrid chaotic keystream generation.
9. Fisher-Yates global permutation.
10. Block and channel permutation.
11. Forward diffusion.
12. Backward diffusion to produce the final encrypted image.

The decryption process performs the corresponding inverse operations in reverse order to recover the original image.

## Encryption and Decryption

The repository contains a single source file implementing both encryption and decryption.

### Encryption

The encryption procedure:

* Loads an input image.
* Generates a fresh session key.
* Derives domain-specific subkeys.
* Generates the CNN-based dynamic seed.
* Generates dynamic transformation parameters.
* Generates BNM and Hénon chaotic sequences.
* Produces the hybrid keystream.
* Applies permutation and block/channel scrambling.
* Performs forward and backward diffusion.
* Saves the encrypted image as a PNG file.

### Decryption

The decryption procedure:

* Loads the encrypted image.
* Regenerates the required cryptographic parameters using the corresponding session key.
* Reconstructs the hybrid chaotic keystream.
* Reverses backward diffusion.
* Reverses forward diffusion.
* Reverses block/channel permutation.
* Reverses the Fisher-Yates permutation.
* Applies the inverse modular transformation.
* Recovers the original image.

The implementation also performs an exact recovery check between the original and decrypted images.

## Requirements

The implementation is designed to run in a Python/Google Colab environment.

The required Python packages include:

* NumPy
* OpenCV
* Pillow
* Matplotlib
* scikit-image
* PyTorch
* BLAKE3

The main dependencies can be installed using:

```bash
pip install blake3 opencv-python pillow scikit-image matplotlib torch
```

## How to Run

### Step 1: Open the Source File

Open the provided source file in Google Colab or a compatible Python environment.

### Step 2: Install the Required Packages

Run the package installation command provided at the beginning of the source code.

### Step 3: Run the Encryption Section

Execute the encryption part of the source code.

The program will prompt the user to upload an input image. After processing, the encrypted image will be generated and saved as:

```text
<original_filename>_encrypted.png
```

### Step 4: Run the Decryption Section

Execute the decryption part of the same source file and provide the corresponding encrypted image when prompted.

The decrypted image will be generated and saved as:

```text
decrypted_original.png
```

### Step 5: Verify Exact Recovery

The implementation automatically compares the original and decrypted images.

Successful decryption is indicated by:

```text
Exact recovery     : True
```

and:

```text
Maximum difference : 0
Different values   : 0
```

## Session Key

A fresh 256-bit session key is generated for each encryption execution. The session key is not a fixed key and is not hard-coded in the source code.

The corresponding session key is required to regenerate the cryptographic parameters during decryption. Actual secret session keys should not be published or stored in a public repository.

## Reproducibility

The source code provided in this repository contains the encryption and decryption implementation associated with the proposed research work. The implementation is intended to support reproducibility of the proposed encryption framework and its exact image recovery procedure.

## Citation

If you use this implementation in academic research, please cite the associated research paper.

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.22041975.svg)](https://doi.org/10.5281/zenodo.22041975)


The Zenodo DOI will be added to this section after the repository is archived and a DOI is assigned.

## License

This repository is provided for academic and research purposes.
