# Installation

This repository can be used as a Codex plugin or as a local skill folder.

## Codex Plugin

```bash
codex plugin marketplace add https://github.com/qq570850096/nature-comsol-simulation --ref main
codex plugin add nature-comsol-simulation@nature-comsol-simulation
```

Restart Codex if the plugin does not appear immediately.

## Manual Local Skill

Clone the repository:

```bash
git clone https://github.com/qq570850096/nature-comsol-simulation.git
cd nature-comsol-simulation
```

Install into Codex local skills:

```bash
mkdir -p ~/.codex/skills
cp -R skills/nature-comsol-simulation ~/.codex/skills/
```

Windows PowerShell:

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.codex\skills"
Copy-Item -Recurse -Force skills\nature-comsol-simulation "$env:USERPROFILE\.codex\skills\"
```

## Verify

Start a new Codex session and ask:

```text
Use nature-comsol-simulation to audit this COMSOL simulation paper for mesh convergence and reviewer risk.
```

The response should load the skill-specific router, state detected axes, and
return claim boundaries, missing inputs, and reviewer-risk flags.
