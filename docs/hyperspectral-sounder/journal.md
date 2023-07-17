---
layout: mathjax
title: Journal Reviews
parent: Hyperspectral Sounder
nav_order: 1
permalink: /docs/hyperspectral-sounder/journal
---

# Journal Reviews

## G. Camps-Valls et al., 2012, IEEE TGRS

### Introduction

Observations from spaceborne high spectral resolution infrared
sounding instruments can be used to calculate the profiles of
such atmospheric parameters with unprecedented accuracy and
vertical resolution.

|Sensor|Channels|Spectral Coverage|Spectral Resolution|Spatial Resolution|
|---|---|---|---|---|
|Metop-A IASI|8461|3.62~15.5 $$\mathrm{\mu m}$$|0.25 $$\mathrm{cm^{-1}}$$|25 $$\mathrm{km}$$|
|MTG IRS|1738|LW 700~1210 $$\mathrm{cm^{-1}}$$<br>MW 1600~2175 $$\mathrm{cm^{-1}}$$|0.625 $$\mathrm{cm^{-1}}$$|4 $$\mathrm{km}$$|

The inverse problem (hyperspectral measurements to atmospheric state) is a complex nonlinear physical process: this is not trivial.

 - Physical based method
 - Statistical regression method (Linear / Nonlinear)

The proposed nonlinear regression method achieves
similar (and sometimes better accuracies and bias scores) with
a much lower computational cost.

### Methodology

Input : Channel informations (max. 100 features/eigenvalues)  
Output : 270 dimension state vector (90 each for T, Q, O3)

Four steps to estimate atmospheric profiles:

1. Feature Selection : Select the most informative channels

    1. "Aires" : Radiative impact of different atmospheric parameters  
        Refer to Aires et al., 2002, Section 6a.

    2. "Collard" : Potential 300 channels  
        To avoid redundancy and effects of interfering atmospheric species, and provide robustness against the choice of background error and atmospheric state.

    3. "Calbet" : Minimize measurement errors - applying noise bias-covariance criteria

2. Feature Extraction : dimensionality reduction through PCA (EOF) and PLS  
    To find optimal number of components for nonlinear regression.

3. Linear / Nonlinear Regression

    1. Neural Network (NN) : Structure of neurons (LR) with connection links (weights) and nonlinear function *f*  

    2. Cascade NN : NN with additional layers

    3. Kernel Ridge Regression (KRR) : Mapping spectra $$\mathrm{x}$$ to $$\phi ({\mathrm{x}})$$ of very high dimensionality. Then the model becomes  
        $$Y=\Phi W+b$$  
        Minimize the regularized squared loss function :  
        $$L = ||Y-\Phi W||^2 + \lambda ||W||^2$$  
        But the calculation of $$\Phi\Phi^T$$ is computationally expensive, we simply use **Kernel matrix** which is $$K = \Phi\Phi^T$$. The selection of kernel function has the same effect with the selection of mapping to high dimensionality and calculation of inner product.  
        Some typical examples of kernel function : Linear, Polynomial, **RBF (Radial basis function)**, ...  
        We need to tune some free parameters (hyperparameters).  
        Fast training, heavy testing. (Inverting the kernel is computationally demanding)

4. Linear Model Combination : usually reduces bias, but computational cost increases.

    1. Mean combination : the average over predictions

    2. Unconstrained optimal linear combination (UOLC) : optimize weight by MSE

    3. Constrained optimal linear combination (COLC) : UOLC with sum-to-one constraints

### Results

#### Synthetic Data Sets

MetOp-IASI and MTG-IRS TOA radiance of each FOVs calculated from ECMWF atmospheric profiles by OSS IR radiative transfer.

* Feature Selection & Extraction  
RMSE decreases with increasing number of features.  
Best method for retrieving T/Q: PCA(Calbet)+KRR, O3: PCA(Collard)+KRR  
Nonlinear regressions are better; KRR needs less features than LR (40~50)

* Accuracy and Bias  
All nonlinear models show similar results and outperform LR.  
KRR shows slightly better results (especially in Q), and MTG-IRS data gives better results.  

#### Real Data Sets

Similar with synthetic data sets: nonlinear models outperform; NN and KRR perform similarly.  
The OLC method shows lower error and bias, but computational cost is high.



### Conclusions



---

## W. Blackwell, 2005, IEEE TGRS

