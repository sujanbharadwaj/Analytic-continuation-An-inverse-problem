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
Traditional Bayesian Approach (MEM):
The Maximum Entropy Method (MEM) uses Bayesian inference to determine the most probable spectral function given the data and prior knowledge. A reference PDF is available in the MaxEnt_pdf directory.
Modern Machine Learning Approach:
A fully connected neural network (FCNN) trained on a large, synthetic dataset is used to learn the mapping from imaginary- to real-frequency data. (Code will be uploaded soon).
