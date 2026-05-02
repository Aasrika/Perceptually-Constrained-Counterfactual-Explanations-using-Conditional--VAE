# Perceptually Constrained Counterfactual Generation for Explainable AI

## Overview

This project explores Explainable AI (XAI) through the generation of counterfactual explanations for deep vision models. Instead of only explaining model decisions, the system generates realistic alternative inputs that minimally modify an image while changing the model’s prediction.

The approach combines a Conditional β-Variational Autoencoder (β-VAE) with a CNN classifier, guided by perceptual loss constraints to ensure visual realism and semantic consistency.

The goal is to improve interpretability of deep neural networks by producing human-understandable, visually plausible counterfactual examples.


## Key Idea

Given an input image classified into a label *A*, the system generates a counterfactual image that:

* Closely resembles the original image
* Satisfies minimal necessary changes
* Forces the classifier to predict a different label *B*
* Remains perceptually realistic



## Architecture

The system consists of the following components:

### 1. Conditional β-VAE

* Learns a structured latent space of images
* Enables controlled generation of counterfactual variations
* Conditioning helps guide generation toward target class attributes

### 2. CNN Classifier

* Used to evaluate original and generated images
* Provides feedback for counterfactual validity

### 3. Perceptual Loss Module

* Ensures generated counterfactuals remain visually realistic
* Computed using high-level feature distances (instead of pixel-only loss)

### 4. Counterfactual Optimization Pipeline

* Optimizes latent representations to:

  * Flip model prediction
  * Maintain minimal deviation from original input
  * Preserve semantic consistency



## Datasets Used

* **CIFAR-10** – General object classification
* **PathMNIST** – Medical imaging dataset
* **CelebA** – Facial attribute dataset

These datasets help evaluate generalization across:
* Natural images
* Medical domain
* Facial attribute variation


## Methodology

1. Train a CNN classifier on each dataset
2. Train a conditional β-VAE to learn latent representations
3. Encode input images into latent space
4. Optimize latent vector to:
   * Change classifier output
   * Minimize reconstruction + perceptual loss
5. Decode optimized latent vector to generate counterfactual image
6. Evaluate validity and perceptual quality



## Results

The model successfully generates:

* Visually realistic counterfactual images
* Minimal but meaningful modifications
* Consistent label flipping across multiple datasets

Key observations:

* Perceptual loss significantly improves realism
* Conditional latent space improves controllability
* Medical dataset (PathMNIST) shows strong interpretability potential



## Tech Stack

* Python
* PyTorch / TensorFlow (mention whichever you used)
* NumPy, Pandas
* Matplotlib / Seaborn (for visualization)
* Google Colab (training environment)



## Key Contributions

* Designed a conditional β-VAE framework for counterfactual generation
* Integrated perceptual loss for realism preservation
* Demonstrated cross-domain applicability (natural + medical + facial images)
* Provided a structured pipeline for explainable vision models



## Limitations

* Computationally expensive latent optimization
* Quality depends on VAE reconstruction capability
* Class boundary sensitivity varies across datasets



## Future Work

* Extend to diffusion-based counterfactual generation
* Improve latent disentanglement for better control
* Add user-interactive explanation interface
* Apply to real-world medical decision systems


Publication

This work has been published in IEEE Xplore.

👉 Paper Link: https://ieeexplore.ieee.org/document/11481918 
👉 DOI: 10.1109/COMP-SIF69752.2026.11481918 

If you use this work, please cite:

@INPROCEEDINGS{11481918,
  author={Aasrika, Kambhampati and Reddy, Dhriti and Chauda, Kanika and Kodipalli, Ashwini and Thomas, Merin and J, Vidya M},
  booktitle={2026 2nd International Conference on Computing for Sustainability and Intelligent Future (COMP-SIF)}, 
  title={Perceptually-Constrained Counterfactual Explanations Using Conditional $\beta$-VAE}, 
  year={2026},
  volume={},
  number={},
  pages={1-6},
  keywords={Filtering;Filters;System-on-chip;Pixel;Protocols;Product lifecycle management;HTTP;Internet;Prognostics and health management;Communication systems;Counterfactual Explanations;Explainable AI;Variational Autoencoders;Perceptual Loss;Multi-Domain Evaluation;Statistical Validation},
  doi={10.1109/COMP-SIF69752.2026.11481918}}

