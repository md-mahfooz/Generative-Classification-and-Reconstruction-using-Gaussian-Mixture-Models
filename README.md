# Generative Classification and Reconstruction using Gaussian Mixture Models

This project explores **generative multi-class classification using Gaussian Mixture Models (GMMs)** on the MNIST dataset, with a focus on both **standard classification** and **classification/reconstruction under missing pixels**.

The core idea is to model each class-conditional distribution as a **mixture of K Gaussians**, allowing the model to capture multiple writing styles within the same digit class.

---

## Methodology

### Generative Modeling
- Each digit class is modeled using a **K-component Gaussian Mixture Model**
- Parameters (means, covariances, mixture weights) are learned using the **Expectation–Maximization (EM)** algorithm
- Class priors are estimated from data

### Inference
- Classification is performed using **Bayesian decision theory**
- The predicted label maximizes the posterior probability:
- `argmax_c P(y = c) · P(x | y = c)`

### Handling Missing Pixels
- For censored images, likelihoods are computed by **marginalizing over unobserved pixels**
- Reconstruction is performed using **Gaussian conditional expectations**
- In the GMM case, reconstructions are obtained as a **responsibility-weighted average** across mixture components

---

## Experiments

Experiments were conducted by varying the number of mixture components:

**K = 1, 2, 5, 10, 15, 20**

### Observations
- Increasing K improves test accuracy up to an optimal point for uncensored images
- On censored images, accuracy continues to improve with larger K
- GMM-based reconstructions are significantly sharper and more realistic than single-Gaussian reconstructions
- Different digits exhibit different levels of structural variability, motivating varied K per class

---

## Results

- **Uncensored classification** shows a clear bias–variance trade-off with peak performance around moderate K
- **Censored classification** benefits consistently from increased mixture components
- **Reconstruction quality** improves substantially with higher K due to better style selection

Representative plots and reconstruction examples are included in the repository and discussed in detail in the accompanying report.

---

## Contents

- GMM training and inference code  
- Censored classification and reconstruction routines  
- Accuracy vs. K plots  
- Reconstruction visualizations  
