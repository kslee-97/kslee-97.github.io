---
layout: mathjax
title: Journal Reviews
parent: Surface Roughness
nav_order: 1
permalink: /docs/surface-roughness
---

# Journal Reviews

## Meissner and Wentz, 2012, IEEE TGRS

### Introduction

Microwave emissivity of roughened surface is crucial.

- As the driver for measuring ocean surface wind speed  
    (Emissivity accuracy of 1.0 K is needed for wind speed accuracy of 1.0 m/s)

- As wind-induced emissivity is unwanted source for the retrieval of other variables.

Three types of roughness scales:

1. **Large Gravity Waves**: long wavelengths, mix V/H polarizations, change local incidence angle

2. **Small Gravity-Capillary Waves**: small RMS height, cause diffraction (Bragg scattering)

3. **Sea Foam**: surface emissivity increasing, important above 7 m/s

Emissivity signals from these mechanisms are largely isotropic.

**Two-scale surface model**: ensemble of tilted facets (*large-scale*), RMS height as a perturbative parameter (*small-scale*) - if the curvature of large-scale waves is not too large, geometric optics and Kirchhoff approximation can be used.

To develop the wind-induced ocean emissivity model on actual TB measurements, for the whole microwave spectrum (from C-band to W-band), a large interval of EIA (from nadir to 65 deg.), and for up to high wind speeds (about 40 m/s).

Central assumption: The roughness of the ocean surface only depends on wind.

This paper does:

- Derive the wind-induced emissivity model (and how it is connected to the absolute calibration)

- Validate the new model function and compare it with other studies

- Provide the detailed forms and coefficients of the emissivity model function

### Methodology

#### Data

TB measurements from WindSat and SSM/I F13: processed from Level 0 count to Level 2 resampled TB (separate channels to common location)

Physical algorithms: trained with simulated TB that are from RTM with realistic scenes.

Self-consistency: model development, calibration, retrieval, validation

#### Methods

RTM: 1-dimensional (depends only on the altitude); plane-parallel approximation

Ocean Surface Emissivity has three components: $$E = E_0 + \Delta E_W + \Delta E_\varphi$$

1. Emissivity of the specular surface: $$E_0 = E_0 (f, \theta_i, T_S, S)$$  
    This is determined by means of the Fresnel equations, where the complex dielectric constant comes from a double Debye relaxation law [Meissner and Wentz, 2004].
    
2. Isotropic wind-induced emissivity: $$\Delta E_W = \Delta E_W (f, \theta_i, W)$$  
    We get $$\Delta E_W + \Delta E_\varphi$$ by solving the RTM equation and subtracting $$E_0$$. By using large global data, the contribution of wind direction drops out and the isotropic part $$\Delta E_W$$ is determined.

3. Stokes vector of the wind direction signal: $$\Delta E_\varphi = \Delta E_\varphi (f, \theta_i, \varphi)$$  
    Same procedure with 2, but analyze the residuum $$E - (E_0 + \Delta E_W)$$.

Atmospheric absorption: $$\alpha = \alpha_L + \alpha_V + \alpha_O$$  
Upper limit of $$L$$ to minimize possible errors.

Computation of the atmospheric parts: (1) numerical integrals, (2) derive for typical scenes, (3) derive regression formulas.

#### Absolute Calibration

1. Radiometer counts (level 0) to antenna temperatures: use two external targets of known temperatures (cold space, hot load)  
    $$T_{A, p} = T_{hot} + \lambda (C_{Earth, p}) \cdot (T_{cold} - T_{hot})$$

2. Antenna temperatures to TOA TB (level 2): antenna pattern correction (APC), correcting cross-polarization contamination and spillover  

Calibration parameters cannot be measured accurately to obtain the required precision of TB.

### Results





### Conclusions



---



