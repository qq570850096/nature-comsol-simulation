# nature-comsol-simulation

`nature-comsol-simulation` 是一个独立的 Codex skill / plugin 项目，面向 COMSOL Multiphysics 与机械工程有限元仿真论文。

它帮助作者写作、审查和修改 COMSOL/FEA 论文中的 Results、Methods、figure plan、验证策略、网格收敛报告、边界条件审查、求解器报告、审稿回复、可复现性清单和综述思路。

它不是 COMSOL 求解器，不是 GUI 自动化工具，也不是泛化 CAE agent。它的目标更窄：**判断仿真 claim 是否经得住审稿，并把模型假设、数值可信度和论文表达绑定起来。**

## 为什么要单独做这个项目

仿真论文常见问题不是语言不好，而是模型证据不够支撑 claim：

- 把应力云图写成真实测量事实。
- 只做了位移网格收敛，却用来支撑峰值应力 claim。
- 把参数扫描趋势写成机制证明。
- 边界条件、接触设置、材料假设没有报告。
- 非线性收敛、求解器 warning、失败案例被隐藏。
- 只有 mesh convergence，却写成真实系统 validation。

这个项目把这些风险变成一个明确的论文契约：

```text
几何 + 材料 + 边界条件 + 网格 + 求解器 + verification
+ validation + 导出证据 -> 有边界的论文 claim
```

## 做什么，不做什么

| 做 | 不做 |
|---|---|
| COMSOL/FEA 论文写作与审稿风险审查 | 完整替代 COMSOL/Abaqus/Ansys 自动化 |
| 网格收敛、求解器、边界条件、验证和 Methods 报告 | 把 GUI 控制作为核心工作流 |
| reviewer-risk flags 与 claim 降级 | 编造参数、版本、验证数据或结果 |
| `.mph`、脚本、导出数据、日志的可复现清单 | 做一个通用 FEM 求解器框架 |
| 仿真论文综述和 related work 规划 | 泛化 prompt 模板集合 |

## 三条设计主轴

| 主轴 | 取值 |
|---|---|
| `simulation_domain` | solid mechanics、structural dynamics、contact/friction、thermal-mechanical、fluid-structure、biomechanics、fracture/materials |
| `model_claim` | stress-strain、deformation、modal frequency、contact pressure、thermal stress、parametric sensitivity、validation/calibration、optimization/design |
| `artifact` | Results、Methods、figure plan、review-risk audit、response strategy、reproducibility checklist、literature-review plan |

## 吸收，也做减法

这个项目吸收公开 GitHub 项目的架构经验，但不是照单全收：

| 来源 | 吸收 | 删掉/不吸收 |
|---|---|---|
| [`scientific-agent-skills`](https://github.com/K-Dense-AI/scientific-agent-skills) | 科学 skill 分类和目录治理 | 不做横跨所有科学领域的大合集 |
| [`NVIDIA/skills`](https://github.com/NVIDIA/skills) | skill 可验证、可维护的包装方式 | 不吸收 GPU/HPC 工具链细节 |
| [`MPh`](https://github.com/MPh-py/MPh) | COMSOL 参数、脚本、导出的可追踪性 | 不重新实现 COMSOL scripting |
| [`COMSOL_Multiphysics_MCP`](https://github.com/wjc9011/COMSOL_Multiphysics_MCP) / [`sim-cli`](https://github.com/svd-ai-lab/sim-cli) | 工具边界、session、日志和 solver artifacts | 不把 GUI/求解器执行作为项目核心 |
| [`Kratos`](https://github.com/KratosMultiphysics/Kratos)、[`DOLFINx`](https://github.com/FEniCS/dolfinx)、[`SfePy`](https://github.com/sfepy/sfepy) | 模型 specification、verification、模块化物理域 | 不复制完整 FEM 框架 |
| [`preCICE`](https://github.com/precice/precice) | 耦合透明度和 coupling convergence | 不构建耦合库 |
| [`OpenRadioss`](https://github.com/OpenRadioss/OpenRadioss)、[`OpenSees`](https://github.com/OpenSees/OpenSees) | 动力学、接触、结构验证习惯 | 不吸收 solver-specific deck |

详细说明见 [docs/absorbed-and-rejected.md](docs/absorbed-and-rejected.md)。

## 鸣谢

感谢这些公开 GitHub 项目的维护者和贡献者。它们在 scientific agent skills、COMSOL 自动化、CAE agent runtime、开源 FEM/多物理场仿真等方面给了本项目重要启发。完整鸣谢和独立性声明见 [ACKNOWLEDGEMENTS.md](ACKNOWLEDGEMENTS.md)。

## 安装

Codex 插件安装：

```bash
codex plugin marketplace add https://github.com/qq570850096/nature-comsol-simulation --ref main
codex plugin add nature-comsol-simulation@nature-comsol-simulation
```

手动安装 local skill：

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.codex\skills"
Copy-Item -Recurse -Force skills\nature-comsol-simulation "$env:USERPROFILE\.codex\skills\"
```

## 示例

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

## 输出形态

通常会返回：

1. 检测到的路由轴。
2. claim-evidence map。
3. 可直接使用的论文文本、清单、figure plan 或回复。
4. missing inputs。
5. reviewer-risk flags。
6. 需要补做的关键分析或降级写法。

## 状态

Draft。首版已经完成模型契约和审稿风险架构，下一步应使用真实 COMSOL 论文和审稿意见做更多测试。
