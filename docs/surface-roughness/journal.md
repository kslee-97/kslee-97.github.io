---
layout: mathjax
title: Journal Reviews
parent: Surface Roughness
nav_order: 1
permalink: /docs/surface-roughness/journal
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

#### Isotropic Emissivity Signal

1. Dependency on **Wind**:  
    In general, $$\Delta E_W$$ increases as the wind speed increases (up to 40 m/s), and this relationship is fitted to a fifth-order polynomial with binned analysis (0.5 m/s size).  
    $$\Delta E_W^i (W,T_{ref}) = \delta^i (W) = \sum_{k=1}^5 \delta_k^i \cdot W^k$$  

2. Dependency on **Sea Surface Temperature**:  
    Emissivity $$\Delta E_W$$ is slightly larger in cold water. Since the dependence of $$\Delta E_W$$ on $$T_S$$ resembles the dependence of $$E_0$$ on $$T_S$$, this dependency can be modeled by the below equation.  
    $$\Delta E_W^i (W,T_S,S) = \delta^i (W) \cdot \frac{E_0^i (T_S,S)}{E_0^i (T_{ref},S)}$$  
    This parameterization seems adequate, and eliminates one degree of freedom in the fitting.  

3. Dependency on **Earth Incidence Angle**:  
    H-pol emissivity $$\Delta E_W^h$$ weakly increases, and V-pol emissivity $$\Delta E_W^v$$ decreases with increasing EIA. $$\Delta E_W^{nad}$$ comes from $$\Delta E_W^h$$ and $$\Delta E_W^v$$ around 55 degree, the EIA dependence can be parameterized.  
    $$\Delta E_W^{p,f} (\theta_i, W, T_S, S) = \Delta E_W^{nad, f} (W, T_S, S) + \left[\Delta E_W^{p,f} (\theta_{ref}, W, T_S, S) - \Delta E_W^{nad, f} (W, T_S, S)\right] \cdot \left(\frac{\theta_i}{\theta_{ref}}\right)^{x_p}$$  
    $$\Delta E_W^{nad,f} (W, T_S, S) = \frac{1}{2} \left[\Delta E_W^{v,f}(\theta_{ref}, W, T_S, S) + \Delta E_W^{h,f} (\theta_{ref}, W, T_S, S)\right]$$  
    This fits well with other dataset between 25~70 degree.  

4. Dependency on **Frequency**:  
    H-pol emissivity increases linearly with $$\mathrm{log}(f)$$.  
    V-pol emissivity is almost independent with frequency between 6.8 and 24 GHz, and decreases with increasing frequency (becomes negative at low wind).  

#### Downwelling Scattered Atmospheric Radiation

The radiation coming from the ocean surface contains the scattered downwelling sky radiation. Radiations that come from different directions have travelled different atmospheric path length; the correction is done by adding the atmospheric path length correction term $$\tau \cdot T_{B,scat}$$.  
$$T_{B,scat,p} = \Omega_p (\tau, W) \cdot \left[T_{BD}+\tau\cdot T_{cold}-T_{cold}\right]\cdot R$$  
The values of $$\Omega_p$$ are precomputed using GO model, and the slope distribution variance comes from Cox and Munk (1954).  
The size of $$\Omega_p$$ depends on frequency and $$\tau$$. For low frequency channels, $$\tau$$ is almost 1; for high frequency channels, $$\tau$$ becomes considerablly low. The path length correction increases brightness temperature for H-pols and the effect increases with increasing frequency; the correction stays small for V-pols.  
If the path length correction is neglected, the wind-induced emissivity becomes effective emissivity: this approach might be valid if the range of $$\tau$$ is narrow.

#### Wind Directional Signal (Stokes Parameters)

Model function of $$\Delta E_\varphi$$ : four Stokes parameters  
V-pol and H-pol: even function in $$\varphi$$  
Third and Fourth Stokes parameter: odd function in $$\varphi$$  
Errors increase for higher frequencies because of the errors in atmospheric transmittance, and errors in h-pol signal is twice as large as errors in v-pol.  
Dominant coef: 1st harmonic v-pol, 2nd harmonic h-pol  

#### Validation & Error Assessment

Two methods to assess the accuracy of the emissivity model function:  
1. Analyze the difference between measured / RTM-computed TOA TB as a function of ground truth parameters.  
2. Direct comparison of the geophysical parameters derived by a physical algorithm based on the model.  

Three limitations: (1) quality of the ground truth, (2) only provides overall assessment of the channels, (3) error in the atmospheric absorption model or systematic error in water vapor/cloud water.  

The result shows almost excellent match except in low SST regions. Five possible reasons:  
1. WV/LCW retrieved by the radiometer is too high.  
2. WV continuum absorption in RTM functino is too high.  
3. The assumption that the temperature dependence of $$\Delta E_W$$ resembles that of $$E_0$$ is not valid.  
4. Observed deficiency in high wind speeds caused inaccuracy in the atmospheric path length correction.  
5. The assumption that $$\Delta E_W$$ goes to zero with wind speed is not valid.  

Some other differences: fifth-order polynomial fit may not fully explain the behavior.  

#### High Wind Speed Area


### Conclusions



---



