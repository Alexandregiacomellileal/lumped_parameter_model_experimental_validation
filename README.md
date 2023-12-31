## Lumped Parameter Model Experimental Validation

![reduce_scale_git](https://github.com/Alexandregiacomellileal/lumped_parameter_model_experimental_validation/assets/96079504/944fe6ab-ffac-4d92-acf9-e7ef5fc7e408)



### Overview

This repository contains the experimental validation details for the lumped parameter model introduced in Section 2.2 of the associated research paper. The validation experiments were conducted using a scaled-down multi-grounded system, as described below.

### Experimental Setup

<center> **Figure 1**
<img width="1019" alt="image" src="https://github.com/Alexandregiacomellileal/lumped_parameter_model_experimental_validation/assets/96079504/3e9322f1-e0cb-4e47-9824-b0129ceb2dde">

To validate the lumped parameter model introduced in Section 2.2 of the associated research paper, experiments were conducted using a scaled-down multi-grounded system. The system consisted of three 1.5 m rods spaced 7.5 m apart, interconnected to a 15 m horizontal electrode. Each copper rod symbolized a turbine grounding, boasting a cross-sectional area of 126 mm², while the copper horizontal electrode had a cross-sectional area of 35 mm².

The horizontal electrode was buried 0.12 m below the ground. Two different conditions were tested for the variable $s$, specifically at values 0.22 and 1.5 m. The radial connection between the rods and the horizontal electrode was established using an insulated wire. The soil had an average low-frequency resistivity of 86.8 Ω·m.

### Measurements clamp-on ground meter

Measurements Zmed <sub>meter</sub> were conducted using the UT-278A clamp-on meter attached to the interconnection cable linking each rod to the horizontal electrode. The measurements were compared with simulated readings Zmed <sub>LPM</sub> obtained from the proposed equivalent electrical circuit model. The instrument resolution is 0.1 Ω, and its accuracy is ± (1.0% + 1 dig) for a range from 0.10 − 49.9 Ω. For a range from 50.0 − 99.9 Ω, its resolution is 0.5 Ω, and its accuracy is ± (1.5% + 1 dig).

### Electrical Circuit and Grounding Resistance Calculation

The electrical circuit for the measurements was established and simulated in ATP to acquire the meter readings Zmed<sub>LPM</sub> following the procedures detailed in Section 2.2 of the associated research paper. Furthermore, the lumped parameter modeling used in [our previous work](https://github.com/Alexandregiacomellileal/A-New-Approach-Towards-Error-Reduction-in-Ground-Resistance-Measurements-Based-on-Clamp-on-Method) was also established and simulated in ATP for comparative purposes. The ATP files used by the authors are attached and named *23_model.acp*, *23_model_rod1.acp*, *23_model_rod3.acp*, *celulapi_COMSOL_k_RLC.acp*, *celulapi_COMSOL_k_RLC_rod1.acp*, and *celulapi_COMSOL_k_RLC_rod3.acp*. 

Notably, the approach used to calculate the grounding resistance of the rod differs, utilizing the Sunde formula. This formula is particularly suitable for scenarios where cylindrical electrodes are vertically installed, especially when their length significantly exceeds their cross-section. 

The grounding resistance of the rod R<sub>rod</sub> is calculated as follows:

$\ R_{\text{rod}} = \frac{\rho_a^{\text{rod}}}{2 \pi l_{\text{rod}}} \left( \ln\left(\frac{4l_{\text{rod}}}{a_{\text{rod}}}\right) - 1 \right) \, \Omega \$

Where:
- $\rho_a^{rod}$ represents the apparent resistivity observed by the rod ($\Omega \cdot \text{m}$),
- $l_{rod}$ is the rod's length (m),
- $a_{rod}$ is the rod's radius (m).

The rod shunt capacitance C<sub>rod</sub> is calculated using the formula:

$\ C_{rod} = \frac{\rho_a^{rod} \ \varepsilon}{R_{rod}} \, \text{F} \$

Where:
- $\varepsilon$ represents the permittivity of the soil, estimated at $7.9686 \times 10^{-11} \, \text{F/m}$.

### Driven Rod Method for Measuring Apparent Resistivities

The apparent resistivities $\rho_a^{rod}$ are measured using the driven rod method with the low-frequency Fall-of-Potential method. The equipment used for these measurements is the digital earth meter MTR-1522. The instrument resolution is 0.01 Ω, and its accuracy is ± (2.0% + 20 dig).

The apparent resistivity observed by the horizontal electrode is determined by averaging the apparent resistivities observed by the rods. This observation is cross-validated using the Fall-of-Potential method.

The apparent resistivity for the cylinder electrodes was estimated at 115.8, 86.0, and 56.2 $\Omega \cdot m$. Correspondingly, the apparent resistivity for the horizontal electrode sections was recorded at 100.9 and 71.1 $\Omega \cdot m$.

### $k$ Parameter Estimation

In our quest to mitigate the impact of mutual coupling in measurements and address distortions arising from the utilization of an equivalent semi-spherical representation of the horizontal electrode, we are engaged in refining the estimation process. Our focus is on enhancing accuracy and reliability by systematically assessing and adjusting the parameters involved in the measurement system.

As per Section 3.1 of the associated research paper, the parameter $k$ was estimated to be 0.74 for an $s$ value of 0.22 m and 0.90 for an $s$ value of 1.5 m.
The COMSOL models used by the authors are attached and named *rod_1.5_he_k.mph* and *rod_1.5_two_sphere_k.mph*. Figure 2 displays images generated through the COMSOL Multiphysics computer simulation software. The image above the Figure 2 is associated with the estimation of $Zmed_{lumped}^{short} (\Omega)$ using the COMSOL model *rod_1.5_two_sphere_k.mph*, while the one below is related to the estimation of $Zmed_{wire}^\infty (\Omega)$ using *rod_1.5_he_k.mph*. 

$Zmed_{wire}^\infty (\Omega)$ is the clamp-on reading taken with the turbine grounding and the horizontal electrode separated by a large distance, in a such way that the mutual couplings between these elements can be considered negligible. On the other hand, the $Zmed_{lumped}^{short} (\Omega)$ is the clamp-on reading taken with the turbine grounding and the horizontal electrode separated by a smaller distance $s$ and with the horizontal electrode being represented by two semi-spherical electrodes spaced so that one does not be influenced by the other. For a single lumped parameter cell representing the horizontal electrode, each semi-spherical electrode must have twice its grounding resistance. 

**Figure 2**
![COMSOL_top_rod](https://github.com/Alexandregiacomellileal/lumped_parameter_model_experimental_validation/assets/96079504/fec3c28d-00eb-4525-b1e6-71c5f1f8a3f4)

Table 1 displays COMSOL simulation results obtained at an average soil resistivity of 115.82 $(\Omega.m)$. Notably, extensive computer simulations indicate that the parameter $k$ remains constant, regardless of changes in soil resistivity from 20 to 10240 $(\Omega.m)$.

**Table 1**
  | $s \ (m)$ | $\rho \ (\Omega.m)$| ${Zmed}_{lumped}^{short} (\Omega) $ | ${Zmed}_{wire}^\infty (\Omega)$| $k$             | 
|---------|---------|------------------------|-----------------------|-----------------|
| 0.220   | 115.82 | 68.828                | 93.064                | 0.740     | 
| 1.500   |  115.82 | 84.037           | 93.064               | 0.903     | 

The graph of Figure 3 depicts the fluctuation of the parameter $k$ about the increasing distance $s$ between the rods and the horizontal electrodes. 

**Figure 3**

<img src="https://github.com/Alexandregiacomellileal/lumped_parameter_model_experimental_validation/assets/96079504/f3d72683-0fc8-4b29-bddf-039e2b4e0f16" width="400" height="300">


### Results

The obtained results demonstrate a robust agreement, with a Mean Absolute Percentage Error of (1.39 ± 0.12) %, between the values registered by the clamp-on meter and those predicted by the proposed equivalent electrical circuit model. It is important to mention that an measurement error propagation study was carried out to address measurement uncertainties.

### Table of Results 

**Table 2**
| $s$ (m) | $k$ | Rod | Zmed<sub>meter</sub> (Ω) | Zmed<sub>LPM</sub> (Ω) | APE<sub>LPM</sub> (%) |
|-------|---|-----|-------------------|----------------|---------------|
| 0.22  | 0.74 | 1 | 63.5 ± 1.5 | 64.37 ± 3.84 | 1.37 ± 0.09 |
| 0.22  | 0.74 | 2 | 46.3 ± 1.2 | 47.06 ± 2.86 | 1.64 ± 0.13 |
| 0.22  | 0.74 | 3 | 35.5 ± 0.5 | 35.34 ± 2.20 | 0.45 ± 0.17 |
| 1.50  | 0.90 | 1 | 72.5 ± 1.6 | 73.43 ± 4.35 | 1.28 ± 0.08 |
| 1.50  | 0.90 | 2 | 56.0 ± 1.3 | 55.45 ± 3.34 | 0.98 ± 0.11 |
| 1.50  | 0.90 | 3 | 39.1 ± 0.5 | 40.12 ± 2.47 | 2.61 ± 0.15 |


### Conclusion

The results serve as validation for the proposed lumped parameter model, with a strong agreement between experimental and simulated data.

