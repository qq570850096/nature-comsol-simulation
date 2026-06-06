# Example: Contact-Pressure Reviewer Response

## User input

```text
Reviewer comment:
The contact-pressure simulations do not demonstrate that the proposed surface
texture reduces wear. The manuscript overinterprets a pressure contour plot.

Known evidence:
- COMSOL contact model with friction coefficient 0.18 from literature.
- Same normal load for smooth and textured surfaces.
- Textured surface shows lower peak contact pressure and larger contact area.
- No Archard wear model.
- No experimental wear test yet.
```

## Skill behavior

```text
Detected axes:
simulation_domain=contact-friction;
model_claim=contact-pressure, validation-calibration;
artifact=response-strategy.
```

## Output excerpt

**Response strategy**

1. Accept the distinction between contact pressure and wear.
2. Downgrade the claim from "reduces wear" to "redistributes contact pressure".
3. Add contact-model details: friction law, coefficient source, contact
   formulation, local mesh refinement, and convergence.
4. Add a planned or completed wear model/experiment before restoring the wear
   claim.

**Draft response**

We thank the reviewer for identifying this important distinction. We agree that
the current COMSOL contact analysis directly supports a redistribution of
contact pressure, rather than a direct demonstration of reduced wear. We have
therefore revised the Results and Discussion to avoid interpreting the pressure
contours as wear validation. In the revised manuscript, we now state that the
textured surface reduced the simulated peak contact pressure and increased the
contact area under the specified normal load. We also expand the Methods to
report the friction coefficient source, contact formulation, and mesh refinement
near the contact interface. A direct wear-reduction claim will require an
explicit wear model or experimental wear testing, which we now identify as a
required validation step.

**Manuscript edits**

- Replace "the texture reduced wear" with "the texture redistributed simulated
  contact pressure under the tested load case".
- Add a figure panel with quantitative peak/average pressure and contact area,
  not only contours.
- Add a reviewer-visible limitation sentence.

## What this demonstrates

- The skill does not defend an overclaim.
- It preserves the usable part of the simulation result.
- It turns a reviewer objection into a concrete revision plan.
