# Computational Snow Mechanics & Tire–Snow Interaction

This repository presents selected results from my research on the
computational modeling of hard-packed snow for tire–snow interaction.

The work combines **finite-strain continuum mechanics**, **constitutive
modeling**, **experimental calibration and validation**, the **Finite Element
Method (FEM)**, and the **Material Point Method (MPM)** to describe the
complex mechanical response of snow under large deformation.

A major focus of this research is the development of constitutive models
capable of representing plastic compaction, strain localization, damage,
healing, fragmentation, and repeated degradation and recovery of hard-packed
snow under loading conditions relevant to tire–snow interaction.

> Research conducted at TU Dresden in collaboration with Continental AG.

---

## Research Overview

Hard-packed snow undergoes strongly nonlinear mechanical processes during
tire interaction. Snow beneath and around the tread is compacted, sheared,
fragmented, transported into tread grooves, and subsequently recompacted.

These processes require numerical models that can capture both the
constitutive response of snow and the very large deformations occurring
during cutting, milling, and groove filling.

The research presented here therefore combines:

- finite-strain elastoplasticity,
- cohesive Modified Cam-Clay plasticity,
- damage and healing mechanics,
- implicit gradient regularization,
- experimental model calibration and validation,
- FEM for constitutive and material-level analysis,
- B-spline MPM for large-deformation simulation,
- and level-set-based contact for rigid-body interaction.

---

## Constitutive Modeling

The constitutive framework is based on a finite-strain cohesive
Modified Cam-Clay model.

The model development progressed through several stages, from a
gradient-enhanced damage formulation toward coupled damage–healing models
for hard-packed snow.

The latest formulation introduces a **rate-type scalar damage–healing
variable**. Damage is primarily driven by deviatoric plastic deformation,
whereas healing is activated by plastic volumetric compaction.

This rate-type formulation allows the material to undergo repeated
sequences of:

**damage → compaction/healing → renewed damage**

without the saturation limitations associated with earlier algebraic
damage–healing formulations.

An implicit gradient enhancement introduces an internal length scale and
regularizes strain localization and softening.

---

## Numerical Framework

Two complementary numerical frameworks are used.

### Finite Element Method

FEM is used for constitutive verification, material-test simulations,
parameter selection, and investigation of gradient-enhanced localization.

The investigated material tests include:

- Oedometer compression
- Triaxial compression
- Uniaxial compression
- Direct shear test

### Material Point Method

Large-deformation processes are simulated using an explicit
**B-spline Material Point Method**.

MPM is particularly suitable for snow cutting and transport because the
material undergoes severe deformation, fragmentation, and large relative
motion that would lead to severe mesh distortion in conventional
Lagrangian finite-element simulations.

The large-deformation framework also incorporates level-set-based contact
for interaction with rigid geometries.

---

## Experimental Validation & Localization

The constitutive models are calibrated and assessed using experimental
material data.

One important aspect of the work is the treatment of strain localization.
The implicit gradient formulation introduces an internal length scale so
that the width of localized deformation zones does not collapse with grid
refinement.

The direct-shear simulations demonstrate the difference between a local
damage formulation and the gradient-enhanced model.

![Direct shear regularization](media/figures/DSTmeshconv.pdf)
![Direct shear regularization](media/figures/nonlocal_DST.pdf)

*Direct-shear simulations illustrating regularized localization under grid
refinement. Figure adapted from Moeineddin et al., International Journal of
Plasticity (2026), CC BY 4.0.*

---

## Large-Deformation Snow-Cavity Simulations

The Snow-Cavity (SC) configuration is designed to reproduce important
mechanisms occurring during tire–snow interaction.

During forward motion, the cutting edge removes snow from the underlying
track and transports it into the cavity. The simulation therefore includes
milling, fragmentation, groove filling, and subsequent compaction of the
snow plug.

### Forward Snow-Cavity Simulation

The forward SC simulation represents the transition from initial cutting
and transport to groove filling and strong compaction of the accumulated
snow.

▶ **[Watch the forward SC simulation](media/videos/sc_forward.mp4)**

As the cavity fills, localized damage develops around the cutting region,
while volumetric compaction inside the filled cavity activates healing and
increases the stiffness of the snow plug.

---

### Backward Snow-Cavity Simulation

After the cavity has been filled and the snow plug compacted, the direction
of motion is reversed.

The backward simulation investigates the transition from a bonded,
compacted snow–snow interface to debonding and subsequent sliding.

▶ **[Watch the backward SC simulation](media/videos/sc_backward.mp4)**

The rate-type damage–healing formulation allows renewed damage to develop
at the snow–snow interface after the previously compacted material has
healed.

---

## Research Progression

This research program has progressively developed the constitutive and
computational description of hard-packed snow:

1. **Finite-strain Modified Cam-Clay with gradient damage**  
   Development of a finite-strain elastoplastic framework with implicit
   gradient regularization for snow softening and localization.

2. **Rubber–snow interaction and experimental validation**  
   Application of the constitutive framework to computational analysis of
   rubber interacting with hard-packed snow.

3. **Finite-strain damage–healing model**  
   Extension of the constitutive framework to include coupled degradation
   and stiffness recovery under tire-relevant loading paths.

4. **Rate-type damage–healing and large-scale MPM simulations**  
   Development of a rate-type damage–healing formulation capable of repeated
   degradation and recovery, together with large-deformation cutting,
   groove-filling, and snow–snow friction simulations.

---

## Publications

### 2026 — International Journal of Plasticity

**A. Moeineddin**, K. Wiese, F. Hamad, J. Platen, C. Boston,
C. Bederna, M. Kaliske

**A rate-type damage–healing Cam-Clay model for hard-packed snow:
Material tests and large-scale cutting simulations by the gradient-enhanced
Material Point Method**

*International Journal of Plasticity*, 203, 104747.

[DOI: 10.1016/j.ijplas.2026.104747](https://doi.org/10.1016/j.ijplas.2026.104747)

---

### 2026 — Computer Methods in Applied Mechanics and Engineering

**A. Moeineddin**, J. Platen, Y. Zhao, J. Choo, M. Kaliske

**A damage–healing finite-strain Cam-Clay model for hard-packed snow**

*Computer Methods in Applied Mechanics and Engineering*, 455, 118864.

[DOI: 10.1016/j.cma.2026.118864](https://doi.org/10.1016/j.cma.2026.118864)

---

### 2025 — Tire Science and Technology

**A. Moeineddin**, J. Platen, J. Meyer, F. Hamad, K. Wiese,
R. Nojek, C. Bederna, M. Kaliske

**Computational analysis of rubber–snow interaction:
Incorporating advanced snow models and experimental validation**

*Tire Science and Technology*, 53(4), 295–318.

[DOI: 10.2346/TST-24-029](https://doi.org/10.2346/TST-24-029)

---

### 2024 — International Journal for Numerical Methods in Engineering

**A. Moeineddin**, J. Platen, M. Kaliske

**Constitutive description of snow at finite strains by the modified
Cam-Clay model and an implicit gradient damage formulation**

*International Journal for Numerical Methods in Engineering*,
125(24), e7595.

[DOI: 10.1002/nme.7595](https://doi.org/10.1002/nme.7595)

---

## Code & Data Availability

The production research codes, experimental datasets, and calibrated
material parameter sets associated with this industrial research project
are not publicly distributed due to collaboration and confidentiality
restrictions.

This repository therefore serves as a **research showcase**, providing
selected visualizations, methodological descriptions, simulation results,
and links to the associated peer-reviewed publications.

Only material that is already publicly available or suitable for public
dissemination is included here.

---

## Collaboration

This research was conducted at the **Institute for Structural Analysis,
TU Dresden**, in collaboration with **Continental AG**.

The work forms part of a broader research effort toward predictive
computational modeling of snow and tire–terrain interaction.

---

## Contact

**Ahmad Moeineddin**

Computational Mechanics & Scientific Computing  
TU Dresden

- [GitHub Profile](https://github.com/Ahmadmoein)
- [LinkedIn](https://www.linkedin.com/in/ahmad-moeineddin-599837175/)
- [ORCID](https://orcid.org/0000-0002-0427-4119)
- [Google Scholar](https://scholar.google.com/citations?user=eOQXTPIAAAAJ)
