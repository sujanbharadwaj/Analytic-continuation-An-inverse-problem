# Analytic-continuation-An-inverse-problem
This repository presents results on the ill-posed problem of analytic continuation using noisy Quantum Monte Carlo (QMC) data. It explores two complementary approaches:
Maximum Entropy Method (MEM) – the traditional Bayesian framework.
Deep Learning, a modern, fully connected neural network (FCNN).
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

### Modern Machine Learning Approach:
This project showcases a "separator" autoencoder architecture built with TensorFlow and Keras. Instead of learning a compressed representation, the encoder is trained to separate the input signal into its two constituent parts: the clean Green's function and the random noise.

The model's effectiveness is evaluated by comparing the denoised Green's function against the ground-truth clean signal, demonstrating a significant reduction in noise.

#### Data
The project requires two data files: 1. Giw_noise.csv (The noisy Green's function data - features), 2. Giw_clean.csv (The clean Green's function data).
#### Model Architecture
The core of this project is the Separator model, a custom Keras model with a deep "funnel" architecture:

Input: A 200-dimensional vector representing the noisy G(i$\omega_n$).

Encoder (Separator): A series of 5 Dense layers with Batch Normalization and Dropout, which learns to map the input to a 400-dimensional output.

1024 -> 512 -> 256 -> 128 -> 128

Output: A 400-dimensional vector, interpreted as the concatenation of the predicted clean signal (200 dimensions) and the predicted noise (200 dimensions).

Decoder (Implicit): A simple Lambda layer that adds the two halves of the Separator's output to reconstruct the original noisy input. This reconstruction is used for calculating the training loss.

The model is trained to minimize the Mean Squared Error between the reconstructed input and the original noisy input, thereby forcing the Separator to learn the optimal signal-noise separation.



