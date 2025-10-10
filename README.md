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
