# Example: Solid-Mechanics Results Audit

## User input

```text
Use nature-comsol-simulation.

Task:
1. Audit whether our COMSOL stress and deformation figures support the claim
   that a porous implant has better mechanical performance.
2. Write a concise Nature-style Results paragraph.
3. List missing inputs and reviewer-risk flags.

Evidence:
- COMSOL Solid Mechanics, stationary study.
- Two designs: baseline and porous lattice.
- Outputs: von Mises stress and displacement contours.
- Mesh convergence: three mesh levels, but only displacement was monitored.
- Validation: compression test planned, not yet completed.
```

## Skill behavior

```text
Detected axes:
simulation_domain=solid-mechanics;
model_claim=stress-strain, deformation-displacement, optimization-design;
artifact=results.
```

## Output excerpt

**Claim-evidence map**

| Claim | Support | Required downgrade |
|---|---|---|
| The porous lattice changed the stress and displacement fields | Supported as a model prediction under the stated load case | Keep as simulated behavior |
| The porous lattice has better mechanical performance | Partially supported numerically | Downgrade until stress convergence and compression validation are supplied |
| The design reduces failure risk | Not supported yet | Requires failure criterion, material limits, and validation |

**Nature-style Results paragraph**

Under the prescribed stationary loading condition, the COMSOL Solid Mechanics
model predicted a redistribution of the von Mises stress field and a reduction
in simulated displacement for the porous lattice relative to the baseline
geometry. Because the mesh-convergence assessment monitored displacement but not
the stress quantity used for the main mechanical claim, these results support a
bounded conclusion that the lattice geometry altered the simulated load-bearing
response. A stronger claim of improved failure resistance will require
stress-focused mesh convergence and validation against the planned compression
test.

**Reviewer-risk flags**

| Severity | Risk | Fix |
|---|---|---|
| High | Stress claim relies on stress contours, but mesh convergence monitored only displacement | Add convergence for peak/averaged stress at claim-critical regions |
| High | Design-superiority claim lacks experimental validation | Add compression-test comparison with error metric |
| Medium | Material model and boundary conditions are not described | Add parameter sources, units, constraints, and load path |

## What this demonstrates

- The skill writes usable Results text.
- It does not let polished language hide missing stress convergence.
- It separates model prediction, design inference, and real-world failure claim.
