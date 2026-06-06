# Acknowledgements

`nature-comsol-simulation` was designed after studying public GitHub projects in
scientific agent skills, COMSOL automation, CAE agent runtimes, and open
finite-element simulation.

We gratefully acknowledge the maintainers and contributors of the following
projects. Their public work helped shape this project's architecture, especially
around skill taxonomy, reproducibility, tool boundaries, model verification,
coupling transparency, and reviewer-facing simulation reporting.

## Scientific Agent Skill Projects

- [`K-Dense-AI/scientific-agent-skills`](https://github.com/K-Dense-AI/scientific-agent-skills)
  for demonstrating large-scale scientific skill organization and task taxonomy.
- [`NVIDIA/skills`](https://github.com/NVIDIA/skills)
  for public agent skill packaging and skill governance patterns.

## COMSOL and CAE Agent Projects

- [`MPh-py/MPh`](https://github.com/MPh-py/MPh)
  for showing how COMSOL models can be treated as scriptable, inspectable
  objects with parameter and export provenance.
- [`wjc9011/COMSOL_Multiphysics_MCP`](https://github.com/wjc9011/COMSOL_Multiphysics_MCP)
  and [`777gegewu/comsol-mcp`](https://github.com/777gegewu/comsol-mcp)
  for public examples of COMSOL MCP/session-control exploration.
- [`svd-ai-lab/sim-cli`](https://github.com/svd-ai-lab/sim-cli)
  for highlighting command, plugin, solver-log, and artifact boundaries in
  agent-operated CAE workflows.
- [`jianyingwu/pfczm-comsol`](https://github.com/jianyingwu/pfczm-comsol)
  for a concrete example of specialized COMSOL implementation where material
  calibration, verification, and reproducibility matter.

## Open Simulation and FEM Projects

- [`KratosMultiphysics/Kratos`](https://github.com/KratosMultiphysics/Kratos)
  for modular multiphysics simulation architecture.
- [`FEniCS/dolfinx`](https://github.com/FEniCS/dolfinx)
  for explicit computational problem definition and reproducible numerical
  formulation.
- [`sfepy/sfepy`](https://github.com/sfepy/sfepy)
  for readable finite-element problem specification patterns.
- [`precice/precice`](https://github.com/precice/precice)
  for coupling transparency, interface mapping, and convergence discipline.
- [`OpenRadioss/OpenRadioss`](https://github.com/OpenRadioss/OpenRadioss)
  for dynamic-event simulation reporting concerns such as time-step stability,
  contact settings, and energy balance.
- [`OpenSees/OpenSees`](https://github.com/OpenSees/OpenSees)
  for structural simulation practice around constraints, loading protocols,
  calibration, and validation.

## Independence Statement

This project uses these repositories as design inspiration only. It does not
copy their code, documentation, datasets, model files, trademarks, or branding.
All names, licenses, and rights remain with their respective projects and
maintainers.

Any mistakes in interpreting the lessons from these projects are ours.
