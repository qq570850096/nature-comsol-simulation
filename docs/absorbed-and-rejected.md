# Absorbed and Rejected Design Decisions

This document records the subtraction step. The project does not absorb every
feature from prior GitHub projects; it keeps only what improves a COMSOL/FEA
publication skill.

We gratefully acknowledge the projects listed below. They are design
inspirations, not dependencies or copied sources. See
[`../ACKNOWLEDGEMENTS.md`](../ACKNOWLEDGEMENTS.md).

## Absorbed

| Source | Absorbed principle | Implementation in this project |
|---|---|---|
| `scientific-agent-skills` | Large scientific skill collections need explicit taxonomies | Router axes: `simulation_domain`, `model_claim`, `artifact` |
| `NVIDIA/skills` | Skills should be packaged, discoverable, and testable | `.codex-plugin/plugin.json`, `agents/openai.yaml`, eval prompts |
| `MPh` | COMSOL work should expose model files, scripts, parameters, and exports | Reproducibility checklist asks for `.mph`, scripts, parameter tables, exported data, logs |
| COMSOL MCP projects | AI tool use needs clear session and model-state boundaries | Skill refuses to pretend it inspected COMSOL state unless evidence is supplied |
| `sim-cli` | Solver commands, logs, plugins, and outputs should be artifacts | Solver-study reporting and reproducibility references treat logs as evidence |
| `Kratos`, `SfePy`, `DOLFINx` | FEM work should make problem specification and numerical formulation inspectable | Methods checklist requires physics interface, geometry, materials, mesh, solver, outputs |
| `preCICE` | Coupled simulation needs mapping and coupling convergence | FSI/thermal-mechanical fragments require coupling direction, interface mapping, convergence |
| `OpenRadioss` | Dynamic/contact simulations require time-step stability and energy/contact checks | Structural dynamics and contact fragments add solver/contact risk checks |
| `OpenSees` | Structural simulation needs calibrated loading, constraints, and validation | Solid mechanics/biomechanics fragments emphasize loading, constraints, calibration, validation |

## Rejected

| Rejected idea | Why it was rejected |
|---|---|
| Full COMSOL automation | The project is for publication support, not solver execution |
| GUI/MCP control as the core workflow | GUI/session state is brittle and hard to verify in manuscript support |
| Full FEM solver framework | Rebuilding Kratos/FEniCS/OpenRadioss would bury the writing/audit goal |
| All simulation domains at once | First version focuses on mechanical-engineering simulation; expansion should be fragment-based |
| Generic high-impact prose templates | Strong language without model evidence increases reviewer risk |
| Invented missing values | Versions, parameters, mesh sizes, validation data, and solver settings must come from user evidence |
| Treating convergence as validation | Numerical convergence supports numerical trust, not real-world validity |
| Contour-first figure logic | Figures must connect setup, mesh, quantitative extraction, convergence, and validation |

## Practical Rule

When deciding whether to add a new feature, ask:

```text
Does this make COMSOL/FEA manuscript claims more traceable, bounded, and review-proof?
```

If not, do not add it to this project.
