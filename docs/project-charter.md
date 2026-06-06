# Project Charter

## Mission

Help researchers turn COMSOL/FEA simulation evidence into manuscript claims that
are clear, bounded, reproducible, and resilient to peer review.

## Non-Goals

- Running COMSOL.
- Replacing engineering judgment.
- Certifying safety, clinical performance, structural integrity, or regulatory
  compliance.
- Providing legal, medical, or professional engineering advice.
- Generating synthetic validation data, mesh convergence, material parameters,
  software versions, or repository links.

## First-Class Risks

- Boundary-condition overclaim.
- Mesh-convergence mismatch.
- Verification/validation confusion.
- Contact/friction sensitivity.
- Coupling and nonlinear solver instability.
- Figure overinterpretation.
- Missing reproducibility artifacts.

## Expansion Policy

Add a new domain only when it brings a distinct risk model. Good future
extensions include electromagnetics, acoustics, MEMS, batteries, porous media,
geomechanics, CFD, and manufacturing simulation. Each extension should add:

1. One `simulation_domain` fragment.
2. Claim-specific fragments if the existing ones are insufficient.
3. At least one eval prompt.
4. A note on what prior-art ideas were absorbed and rejected.
