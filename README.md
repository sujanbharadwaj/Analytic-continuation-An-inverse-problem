# Analytic-continuation-An-inverse-problem
This repository presents results on the ill-posed problem of analytic continuation using noisy Quantum Monte Carlo (QMC) data. It explores two complementary approaches:
 - Maximum Entropy Method (MEM) – the traditional Bayesian framework.
 - Machine learning approach.
The goal is to provide a resource for researchers interested in both established statistical methods and emerging machine learning techniques for analytic continuation.

## Problem Overview
Analytic continuation is the task of reconstructing a real-frequency spectral function from imaginary-frequency QMC data. This step is essential in quantum many-body physics, where numerical simulations typically operate in imaginary time/frequency, but experiments probe real frequencies.
The problem is fundamentally ill-posed:
Input data is noisy and incomplete.
Multiple plausible spectral functions can correspond to the same input.
Thus, developing stable and accurate continuation techniques is critical.


## Approaches
### Traditional Bayesian Approach (MEM):
The Maximum Entropy Method (MEM) uses Bayesian inference to determine the most probable spectral function given the data and prior knowledge. All relevant details of MEM are provided in the reference PDF, which is available in the MaxEnt_pdf directory.

### Machine Learning Approach:
This project implements a Denoising Autoencoder (DAE) architecture using TensorFlow and the Keras library. The model is specifically designed to filter noise from Quantum Monte Carlo (QMC) Green's function data ($G(\tau)$), which is crucial for subsequent analysis like analytic continuation. The model's effectiveness is evaluated by comparing the denoised Green's function output against both the original noisy input and the ground-truth clean signal, demonstrating a significant reduction in noise.

#### Data
The project requires two data files: 
 + Gtau_noise.csv (The noisy Green's function data - features)
 + Giw_clean.csv (The clean Green's function data).
#### Model Architecture
This model consists of the following:
 - Encoder: Consists of two blocks, each containing: Conv1D layer, BatchNormalization, MaxPooling1D (downsampling), Dropout.
 - Bottleneck: A Conv1D layer, BatchNormalization, and Dropout.
 - Decoder: UpSampling, Conv1D layer, BatchNormalization, Dropout.
 - Output: A final Conv1D layer to reconstruct the denoised G(τ).
