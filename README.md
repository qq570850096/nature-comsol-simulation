# nature-comsol-simulation

`nature-comsol-simulation` is a standalone Codex skill/plugin project for
Nature-style COMSOL Multiphysics and mechanical-engineering simulation papers.

It helps authors write, audit, and revise publication artifacts for COMSOL/FEA
work: Results, Methods, figure plans, validation strategy, mesh-convergence
reporting, boundary-condition review, solver-study reporting, reviewer-response
strategy, reproducibility checklists, and literature-review plans.

The project is deliberately **not** a COMSOL solver, GUI automation layer, or
general CAE agent. Its job is narrower and sharper: judge whether a simulation
claim can survive peer review, then help write the manuscript without hiding the
model's assumptions.

## Why this exists

Simulation papers often fail for reasons that polishing cannot fix:

- A stress contour is written as if it were a measured physical fact.
- A mesh-independent displacement is used to justify a peak-stress claim.
- A parameter sweep is described as mechanism without validation.
- Boundary conditions, contact settings, and material assumptions are hidden.
- Solver warnings, nonlinear convergence, and failed cases are not reported.
- A model is called "validated" when only numerical convergence was shown.

This project turns those risks into an explicit publication contract:

```text
geometry + materials + boundary conditions + mesh + solver + verification
+ validation + exported evidence -> bounded manuscript claim
```

## Core scope

| Included | Excluded |
|---|---|
| COMSOL/FEA manuscript writing and audit | Full COMSOL/Abaqus/Ansys automation |
| Mesh-convergence, solver, and boundary-condition reporting | GUI-control as the main workflow |
| Reviewer-risk flags and claim downgrading | Fabricated parameters, versions, validation, or results |
| Reproducibility checklists for `.mph`, scripts, exported data, logs | A general-purpose numerical solver framework |
| Literature-review and related-work planning for simulation papers | One-size-fits-all prompt templates |

## Design axes

The skill routes every request through three axes:

| Axis | Values |
|---|---|
| `simulation_domain` | solid mechanics, structural dynamics, contact/friction, thermal-mechanical, fluid-structure, biomechanics, fracture/materials |
| `model_claim` | stress-strain, deformation, modal frequency, contact pressure, thermal stress, parametric sensitivity, validation/calibration, optimization/design |
| `artifact` | Results, Methods, figure plan, review-risk audit, response strategy, reproducibility checklist, literature-review plan |

This keeps the project focused. New domains can be added as fragments without
turning the skill into a bulky CAE platform.

## What was absorbed, and what was rejected

The project learns from public GitHub projects, but it intentionally performs
subtraction before adoption.

| Source | Absorbed | Rejected |
|---|---|---|
| [`scientific-agent-skills`](https://github.com/K-Dense-AI/scientific-agent-skills) | Skill taxonomy and scientific task governance | Huge cross-domain catalog inside this repo |
| [`NVIDIA/skills`](https://github.com/NVIDIA/skills) | Verifiable skill packaging and simulation/modeling categories | GPU/HPC tooling outside the paper-audit goal |
| [`MPh`](https://github.com/MPh-py/MPh) | Scriptable COMSOL provenance and parameter/export traceability | Reimplementing COMSOL scripting |
| [`COMSOL_Multiphysics_MCP`](https://github.com/wjc9011/COMSOL_Multiphysics_MCP) and [`sim-cli`](https://github.com/svd-ai-lab/sim-cli) | Tool/session boundaries, logs, and solver artifacts | Making GUI/solver execution the core of this project |
| [`Kratos`](https://github.com/KratosMultiphysics/Kratos), [`DOLFINx`](https://github.com/FEniCS/dolfinx), [`SfePy`](https://github.com/sfepy/sfepy) | Model specification, verification, modular physics | Copying a full FEM framework |
| [`preCICE`](https://github.com/precice/precice) | Coupling transparency and convergence discipline | Building a coupling library |
| [`OpenRadioss`](https://github.com/OpenRadioss/OpenRadioss), [`OpenSees`](https://github.com/OpenSees/OpenSees) | Dynamics/contact/structural validation habits | Solver-specific decks and workflows |

Detailed notes: [docs/absorbed-and-rejected.md](docs/absorbed-and-rejected.md)
and
[skills/nature-comsol-simulation/references/prior-art-design-notes.md](skills/nature-comsol-simulation/references/prior-art-design-notes.md).

## Acknowledgements

We thank the maintainers and contributors of the public GitHub projects that
inspired this work, including scientific agent skill projects, COMSOL automation
projects, CAE agent runtimes, and open FEM/multiphysics frameworks. See
[ACKNOWLEDGEMENTS.md](ACKNOWLEDGEMENTS.md) for the full list and independence
statement.

## Install

### Codex plugin

```bash
codex plugin marketplace add https://github.com/qq570850096/nature-comsol-simulation --ref main
codex plugin add nature-comsol-simulation@nature-comsol-simulation
```

Restart Codex after installation if the skill does not appear immediately.

### Manual local skill

Copy the skill folder into your local Codex skills directory:

```bash
mkdir -p ~/.codex/skills
cp -R skills/nature-comsol-simulation ~/.codex/skills/
```

On Windows PowerShell:

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.codex\skills"
Copy-Item -Recurse -Force skills\nature-comsol-simulation "$env:USERPROFILE\.codex\skills\"
```

## Example prompts

```text
Use nature-comsol-simulation to audit this COMSOL solid-mechanics Results section.
Focus on mesh convergence, boundary conditions, validation, and reviewer risk.
```

```text
帮我检查这个 COMSOL 热-结构耦合模型的 Methods，重点看网格收敛、边界条件、求解器设置和审稿风险。
```

```text
Reviewer says our contact-pressure simulation does not prove wear reduction.
Draft a response strategy and list what evidence must be added.
```

## Expected output

For most tasks, the skill returns:

1. Detected axes.
2. Claim-evidence map.
3. Ready-to-use manuscript text, checklist, figure plan, or response.
4. Missing inputs.
5. Reviewer-risk flags.
6. Concrete next fixes when needed.

## Project structure

```text
nature-comsol-simulation/
├── .codex-plugin/
│   └── plugin.json
├── skills/
│   └── nature-comsol-simulation/
│       ├── SKILL.md
│       ├── manifest.yaml
│       ├── static/
│       │   ├── core/
│       │   ├── shared/
│       │   └── fragments/
│       ├── references/
│       ├── agents/
│       └── evals/
├── docs/
│   ├── absorbed-and-rejected.md
│   └── project-charter.md
├── README.md
├── README-zh.md
├── install.md
├── CONTRIBUTING.md
└── LICENSE
```

## Status

Draft. The model-contract and reviewer-risk architecture is defined; broader
testing on real COMSOL manuscripts should come next.
