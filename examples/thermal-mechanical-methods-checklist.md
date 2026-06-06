# Example: Thermal-Mechanical Methods Checklist

## User input

```text
Help me write Methods for a COMSOL thermal-mechanical model.

Known details:
- Heat Transfer in Solids + Solid Mechanics.
- One-way coupling: temperature field imported as thermal load.
- Model predicts thermal stress near a bonded interface.
- Material properties from datasheets.
- Time-dependent heating for 600 seconds.
- Mesh convergence was done for maximum temperature, not thermal stress.
```

## Skill behavior

```text
Detected axes:
simulation_domain=thermal-mechanical;
model_claim=thermal-stress;
artifact=methods.
```

## Output excerpt

**Methods skeleton**

The thermal-mechanical response was simulated in COMSOL Multiphysics using the
Heat Transfer in Solids and Solid Mechanics physics interfaces. Heat transfer
was first solved in a time-dependent study over 600 s, and the resulting
temperature field was imported as a one-way thermal load for the structural
analysis. Material properties, including thermal conductivity, heat capacity,
elastic modulus, Poisson ratio, and coefficient of thermal expansion, were taken
from manufacturer datasheets and assigned to each domain with SI units. Thermal
stress was evaluated near the bonded interface by extracting [region/path metric]
from the structural solution.

**Missing inputs**

- COMSOL version and module list.
- Geometry source, dimensionality, and interface definition.
- Heat source, convection/radiation/contact-conductance boundary conditions.
- Datasheet citations and temperature-dependence of properties.
- Structural constraints and thermal expansion reference temperature.
- Mesh element type/order and final element count.
- Thermal-stress mesh convergence, not only temperature convergence.
- Solver tolerances, time-step settings, and convergence warnings.

**Reviewer-risk flags**

| Severity | Risk | Fix |
|---|---|---|
| High | Claim is about thermal stress, but convergence monitored only temperature | Add convergence for interface stress or region-averaged stress |
| Medium | One-way coupling may be insufficient if deformation changes thermal contact | Justify one-way assumption or add sensitivity |
| Medium | Datasheet properties may not match operating temperature | Report property ranges or temperature-dependent values |

## What this demonstrates

- The skill can draft Methods without inventing missing COMSOL settings.
- It forces claim-critical convergence, not generic convergence.
- It exposes coupling assumptions that reviewers often question.
