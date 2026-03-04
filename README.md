# ScientificAgentBench

A curated collection of 67 benchmarks for evaluating LLM-based agents, organized from general to domain-specific.

> Based on deep research reports:
> - [LLM 智能体系统基准测试综述](../0-Research-Automation/1-deep-research-output/5-benchmarks/llm-agentic-benchmarks-long-context/phase6_report/report.md)
> - [Coordination Benchmarks for Scientific Multi-Agent Systems](../0-Research-Automation/1-deep-research-output/5-benchmarks/coordination-benchmarks-scientific/phase6_report/report.md)

## Overview

| Category | Benchmark | Venue | Local |
|----------|-----------|-------|-------|
| **A. Static Knowledge** | | | |
| | [GPQA](#gpqa) — PhD-level Physics/Chem/Bio | 2023 | `data/GPQA` |
| | [MMLU-Pro](#mmlu-pro) — 14 domains, 12K+ MCQ | NeurIPS 2024 | `data/MMLU-Pro` |
| | [SuperGPQA](#supergpqa) — 285 disciplines, 100K+ MCQ | 2025 | `data/SuperGPQA` |
| | [HLE](#hle) — Humanity's Last Exam, 2,500 MCQ | Nature 2025 | `data/HLE` |
| | [OlympiadBench](#olympiadbench) — Math/Physics olympiad | 2024 | `data/OlympiadBench` |
| | [UGPhysics](#ugphysics) — Undergraduate physics, 13 subjects | 2025 | `data/UGPhysics` |
| **B. Long Context** | | | |
| | [RULER](#ruler) — Multi-needle, configurable | 2024 | `data/RULER` |
| | [LongBench](#longbench) — Bilingual, 4K-2M | ACL 2024 | `data/LongBench` |
| | [InfiniteBench](#infinitebench) — 100K+ length tasks | 2024 | `data/InfiniteBench` |
| | [BABILong](#babilong) — Distributed fact reasoning | NeurIPS 2024 | `data/BABILong` |
| | [SCBench](#scbench) — Shared-context evaluation | ICLR 2025 | `data/SCBench` |
| | [HELMET](#helmet) — 7 task types, 8K-128K | ICLR 2025 | `data/HELMET` |
| | [CogniLoad](#cogniload) — Cognitive load 3D control | ICLR 2026 | `data/CogniLoad` |
| | [GSM-Infinite](#gsm-infinite) — Math + infinite context | 2025 | `data/GSM-Infinite` |
| | [R-Horizon](#r-horizon) — Compositional multi-step | 2025 | `data/R-Horizon` |
| | [LOCA-bench](#loca-bench) — Long context agent | 2025 | `data/LOCA-bench` |
| **C. Tool Calling** | | | |
| | [BFCL](#bfcl) — Function calling, 2000 QA | 2024-25 | `data/BFCL` |
| | [ToolBench](#toolbench) — 16K+ real APIs | ICLR 2024 | `data/ToolBench` |
| | [ShortcutsBench](#shortcutsbench) — Apple Shortcuts tool use | ICLR 2025 | `data/ShortcutsBench` |
| | [tau-bench](#tau-bench) — Domain APIs + policy, pass^k | ICLR 2025 | `data/tau-bench` |
| | [TRAJECT-Bench](#traject-bench) — 1,228 APIs, trajectory metrics | 2025 | `data/TRAJECT-Bench` |
| | [MCPMark](#mcpmark) — MCP tool calling | ICLR 2026 | `data/MCPMark` |
| | [MCP-Bench](#mcp-bench) — 250 MCP tools, cross-domain | ICLR 2026 | `data/MCP-Bench` |
| | [FuncBenchGen](#funcbenchgen) — Anti-contamination DAG | ICLR 2026 | `data/FuncBenchGen` |
| **D. Multi-step Agent** | | | |
| | [SWE-bench](#swe-bench) — Code / Git, 2,294 tasks | 2024 | `data/SWE-bench` |
| | [GAIA](#gaia) — General AI assistant, 466 tasks | 2023 | `data/GAIA` |
| | [TheAgentCompany](#theagentcompany) — Workplace tasks | 2024 | `data/TheAgentCompany` |
| | [MLAgentBench](#mlagentbench) — ML research agent | 2023 | `data/MLAgentBench` |
| | [MLE-bench](#mle-bench) — 75 Kaggle competitions | ICLR 2025 | `data/MLE-bench` |
| | [RE-Bench](#re-bench) — Research engineering | METR 2024 | `data/RE-Bench` |
| | [PaperBench](#paperbench) — Paper reproduction | ICML 2025 | `data/PaperBench` |
| | [ACADREASON](#acadreason) — Academic reasoning | 2025 | `data/ACADREASON` |
| | [PaperArena](#paperarena) — Scientific literature agent | 2025 | `data/PaperArena` |
| | [WindowsAgentArena](#windowsagentarena) — Windows desktop agent | ICML 2025 | `data/WindowsAgentArena` |
| | [EmbodiedBench](#embodiedbench) — Embodied AI | ICML 2025 Oral | `data/EmbodiedBench` |
| | [VisualAgentBench](#visualagentbench) — Visual foundation agents | ICLR 2025 | `data/VisualAgentBench` |
| | [Terminal-Bench](#terminal-bench) — Terminal/CLI agent | ICLR 2026 | `data/Terminal-Bench` |
| **E. Multi-Agent Coordination** | | | |
| | [MARBLE](#marble) — LLM multi-agent, 6 scenarios × 4 topologies | ACL 2025 | `data/MARBLE` |
| | [SwarmBench](#swarmbench) — Decentralized swarm, 5 tasks | 2025 | `data/SwarmBench` |
| | [Collaborative Gym](#collaborative-gym) — Human-agent collaboration | ICLR 2026 | `data/CollaborativeGym` |
| | [SMACv2](#smacv2) — Cooperative MARL, 18 scenarios | NeurIPS 2023 | `data/SMACv2` |
| | [Melting Pot](#melting-pot) — Mixed-motive Markov games | NeurIPS 2024 | `data/MeltingPot` |
| **F. Scientific Research** | | | |
| | [AstaBench](#astabench) — 11 sub-benchmarks, E2E discovery | ICLR 2026 Oral | `data/AstaBench` |
| | [ScienceAgentBench](#scienceagentbench) — 4-discipline discovery | ICLR 2025 | `data/ScienceAgentBench` |
| | [LiveResearchBench](#liveresearchbench) — Citation-grounded deep research | ICLR 2026 | `data/LiveResearchBench` |
| | [InfiAgent-DABench](#infiagent-dabench) — Data analysis agent | ICML 2024 | `data/InfiAgent-DABench` |
| | [DSBench](#dsbench) — Data science benchmark | ICLR 2025 | `data/DSBench` |
| | [ChemBench](#chembench) — Chemistry knowledge | Nature Chem 2025 | `data/ChemBench` |
| | [LAB-Bench](#lab-bench) — Life science literature/protocol | 2024 | `data/LAB-Bench` |
| | [BixBench](#bixbench) — Bioinformatics (broad) | 2025 | `data/BixBench` |
| | [HeurekaBench](#heurekabench) — AI Co-scientist, single-cell | ICLR 2026 | `data/HeurekaBench` |
| | [MedAgentBench](#medagentbench) — Medical EHR | NEJM AI 2025 | `data/MedAgentBench` |
| | [InnovatorBench](#innovatorbench) — Scientific innovation | ICLR 2026 | `data/InnovatorBench` |
| | [DeepResearchBench](#deepresearchbench) — Deep research eval | ICLR 2026 | `data/DeepResearchBench` |
| **G. Code** | | | |
| | [BigCodeBench](#bigcodebench) — Large-scale code eval | 2024 | `data/BigCodeBench` |
| | [LiveCodeBench](#livecodebench) — Contamination-free code | ICLR 2025 | `data/LiveCodeBench` |
| **H. Meta-evaluation & Efficiency** | | | |
| | [OckBench](#ockbench) — Token efficiency | NeurIPS 2025 WS | `data/OckBench` |
| | [AutoLibra](#autolibra) — Automatic metric induction | 2025 | `data/AutoLibra` |
| | [LiveBench](#livebench) — Continuously updated | ICLR 2025 Spotlight | `data/LiveBench` |
| | [JudgeBench](#judgebench) — LLM-as-judge evaluation | ICLR 2025 | `data/JudgeBench` |
| | [ImpossibleBench](#impossiblebench) — Unanswerable questions | ICLR 2026 | `data/ImpossibleBench` |
| | [MAESTRO](#maestro) — Multi-agent system evaluation | 2025 | `data/MAESTRO` |
| | [HAL Harness](#hal-harness) — Holistic agent leaderboard | ICLR 2026 | `data/HAL-Harness` |
| | [InspectAI](#inspectai) — UK AISI evaluation framework | 2024 | `data/InspectAI` |
| | [InspectEvals](#inspectevals) — 100+ community evaluations | 2024 | `data/InspectEvals` |
| | [OpenHands Benchmarks](#openhands-benchmarks) — 15+ agent benchmarks | 2024 | `data/OpenHands-Benchmarks` |
| **I. Safety** | | | |
| | [AgentSecurityBench](#agentsecuritybench) — Agent security | ICLR 2025 | `data/AgentSecurityBench` |

**Not available**: MathHay (repo private), FrontierMath (private), PRiSM (no repo), OrchestrationBench (no repo), InnoGym (no repo), BioinformaticsBench (no repo), ScienceBoard (no repo), NewtonBench (no repo)

---

## A. Static Knowledge Benchmarks

### GPQA
Graduate-level Google-proof Q&A benchmark.
- **Paper**: Rein et al., 2023 | **Repo**: https://github.com/idavidrein/gpqa
- **Scale**: ~200 MCQ in physics, chemistry, biology — PhD-level
- **Local**: `data/GPQA`

### MMLU-Pro
Enhanced massive multi-task language understanding.
- **Paper**: [arXiv:2406.01574](https://arxiv.org/abs/2406.01574) (NeurIPS 2024) | **Repo**: https://github.com/TIGER-AI-Lab/MMLU-Pro
- **Scale**: 12K+ questions across 14 domains
- **Local**: `data/MMLU-Pro`

### SuperGPQA
Super graduate-level QA across 285 disciplines.
- **Paper**: [arXiv:2502.14739](https://arxiv.org/abs/2502.14739) | **Repo**: https://github.com/SuperGPQA/SuperGPQA
- **Scale**: 100K+ graduate-level questions
- **Local**: `data/SuperGPQA`

### HLE
Humanity's Last Exam — frontier-level questions across 100+ disciplines.
- **Paper**: [arXiv:2501.14249](https://arxiv.org/abs/2501.14249) (Nature 2025) | **Repo**: https://github.com/centerforaisafety/hle
- **Scale**: 2,500 questions
- **Local**: `data/HLE`

### OlympiadBench
Bilingual multimodal olympiad benchmark.
- **Paper**: He et al., 2024 | **Repo**: https://github.com/OpenBMB/OlympiadBench
- **Domain**: Math + Physics olympiad | **Best**: ~30-50%
- **Local**: `data/OlympiadBench`

### UGPhysics
Undergraduate physics benchmark across 13 subjects.
- **Paper**: [arXiv:2502.00334](https://arxiv.org/abs/2502.00334) | **Repo**: https://github.com/YangLabHKUST/UGPhysics
- **Scale**: 5,520 questions
- **Local**: `data/UGPhysics`

---

## B. Long Context Benchmarks

### RULER
Configurable multi-needle long context evaluation.
- **Paper**: [arXiv:2404.06654](https://arxiv.org/abs/2404.06654) | **Repo**: https://github.com/NVIDIA/RULER
- **Tasks**: Multi-needle retrieval, multi-hop, aggregation
- **Local**: `data/RULER`

### LongBench
Bilingual long-context multi-task benchmark (v1 + v2).
- **Paper**: ACL 2024 / [arXiv:2412.15204](https://arxiv.org/abs/2412.15204) (v2) | **Repo**: https://github.com/THUDM/LongBench
- **Scale**: v1 4K-100K; v2 8K-2M with 503 MCQ
- **Local**: `data/LongBench`

### InfiniteBench
100K+ token length evaluation.
- **Paper**: [arXiv:2402.13718](https://arxiv.org/abs/2402.13718) | **Repo**: https://github.com/OpenBMB/InfiniteBench
- **Key**: Tasks genuinely requiring 100K+ tokens
- **Local**: `data/InfiniteBench`

### BABILong
Distributed fact reasoning at arbitrary context length.
- **Paper**: NeurIPS 2024 | **Repo**: https://github.com/booydar/babilong
- **Key**: Extends bAbI tasks to arbitrary context lengths
- **Local**: `data/BABILong`

### SCBench
Shared-context long-context evaluation.
- **Paper**: ICLR 2025 | **Repo**: https://github.com/microsoft/MInference (`scbench/`)
- **Authors**: Microsoft
- **Local**: `data/SCBench`

### HELMET
How to Evaluate Long-context Language Models Effectively and Thoroughly.
- **Paper**: [arXiv:2410.02694](https://arxiv.org/abs/2410.02694) (ICLR 2025) | **Repo**: https://github.com/princeton-nlp/HELMET
- **Scale**: 51 models x 7 task types x 8K-128K
- **Key finding**: Synthetic tasks (NIAH) are poor predictors of real performance (Spearman ≤ 0.8)
- **Local**: `data/HELMET`

### CogniLoad
Cognitive load theory-driven 3D evaluation.
- **Paper**: [arXiv:2509.18458](https://arxiv.org/abs/2509.18458) (ICLR 2026) | **Repo**: https://github.com/kaiserdan/cogniload
- **Three axes**: ECL, Number of Thoughts, Information Density
- **Key finding**: U-shaped distractor response; accuracy and token efficiency rankings inconsistent
- **Local**: `data/CogniLoad`

### GSM-Infinite
Infinitely scalable, anti-contamination math + context evaluation.
- **Paper**: [arXiv:2502.05252](https://arxiv.org/abs/2502.05252) | **Repo**: https://github.com/Infini-AI-Lab/gsm_infinite
- **Authors**: CMU + Meta
- **Key finding**: RULER/LongBench solvable by 2048-token RAG; performance decay follows sigmoid (R² > 0.98)
- **Local**: `data/GSM-Infinite`

### R-Horizon
Reasoning horizon limits via query composition.
- **Paper**: [arXiv:2510.08189](https://arxiv.org/abs/2510.08189) | **Repo**: https://github.com/LuLuLuyi/R-HORIZON
- **Authors**: Fudan + Meituan
- **Key finding**: DeepSeek-R1 87.3% → 24.6% at n=5; composition training helps both multi-step and single-step
- **Local**: `data/R-Horizon`

### LOCA-bench
Long context agent benchmark.
- **Paper**: [arXiv:2602.07962](https://arxiv.org/abs/2602.07962) | **Repo**: https://github.com/hkust-nlp/LOCA-bench
- **Authors**: HKUST NLP
- **Local**: `data/LOCA-bench`

---

## C. Tool Calling Benchmarks

### BFCL
Berkeley Function Calling Leaderboard (inside Gorilla project).
- **Paper**: Patil et al. | **Repo**: https://github.com/ShishirPatil/gorilla (`berkeley-function-call-leaderboard/`)
- **Scale**: 2000 QA pairs, multi-step
- **Local**: `data/BFCL`

### ToolBench
Large-scale real API tool use benchmark.
- **Paper**: ICLR 2024 Spotlight | **Repo**: https://github.com/OpenBMB/ToolBench
- **Scale**: 16K+ real APIs
- **Local**: `data/ToolBench`

### ShortcutsBench
Apple Shortcuts-based tool use benchmark.
- **Paper**: ICLR 2025 | **Repo**: https://github.com/EachSheep/ShortcutsBench
- **Domain**: Real-world iOS Shortcuts API composition
- **Local**: `data/ShortcutsBench`

### tau-bench
Tool-Agent-User interaction in real-world domains.
- **Paper**: [arXiv:2406.12045](https://arxiv.org/abs/2406.12045) (ICLR 2025) | **Repo**: https://github.com/sierra-research/tau-bench
- **Key metric**: pass^k — gpt-4o pass^1 ≈ 50%, pass^8 < 25%
- **Local**: `data/tau-bench`

### TRAJECT-Bench
Trajectory-aware tool calling with 4 orthogonal metrics.
- **Paper**: [arXiv:2510.04550](https://arxiv.org/abs/2510.04550) | **Repo**: https://github.com/PengfeiHePower/TRAJECT-Bench
- **Scale**: 1,228 real APIs, 5,870 queries
- **Key finding**: 3→5 tool calls = performance cliff [CONVERGENT]
- **Local**: `data/TRAJECT-Bench`

### MCPMark
MCP tool calling benchmark.
- **Paper**: ICLR 2026 | **Repo**: https://github.com/eval-sys/mcpmark
- **Domain**: MCP protocol-based tool evaluation
- **Local**: `data/MCPMark`

### MCP-Bench
Cross-domain tool orchestration via MCP servers.
- **Paper**: [arXiv:2508.20453](https://arxiv.org/abs/2508.20453) (ICLR 2026) | **Repo**: https://github.com/Accenture/mcp-bench
- **Scale**: 250 tools, multi-step orchestration
- **Local**: `data/MCP-Bench`

### FuncBenchGen
Anti-contamination controllable function calling via DAG.
- **Paper**: [arXiv:2509.26553](https://arxiv.org/abs/2509.26553) (ICLR 2026) | **Repo**: https://github.com/megagonlabs/FuncBenchGen
- **Key finding**: State tracking is the core bottleneck (VNYK = 66-81%); GPT-5 only 15% at 20 core functions
- **Local**: `data/FuncBenchGen`

---

## D. Multi-step Agent Benchmarks

### SWE-bench
Software engineering agent benchmark.
- **Repo**: https://github.com/SWE-bench/SWE-bench
- **Scale**: 2,294 real GitHub issues
- **Local**: `data/SWE-bench`

### GAIA
General AI Assistant benchmark.
- **Paper**: [arXiv:2311.12983](https://arxiv.org/abs/2311.12983) | **Dataset**: https://huggingface.co/datasets/gaia-benchmark/GAIA
- **Authors**: Meta | **Scale**: 466 multi-step reasoning tasks
- **Local**: `data/GAIA` (from HuggingFace)

### TheAgentCompany
Real-world workplace task benchmark.
- **Paper**: [arXiv:2412.14161](https://arxiv.org/abs/2412.14161) | **Repo**: https://github.com/TheAgentCompany/TheAgentCompany
- **Domain**: Professional workplace tasks (coding, PM, HR, finance, admin)
- **Local**: `data/TheAgentCompany`

### MLAgentBench
ML research agent benchmark.
- **Paper**: 2023 | **Repo**: https://github.com/snap-stanford/MLAgentBench
- **Authors**: Stanford SNAP
- **Domain**: Agents autonomously perform ML research tasks
- **Local**: `data/MLAgentBench`

### MLE-bench
ML engineering evaluation on 75 Kaggle competitions.
- **Paper**: [arXiv:2410.07095](https://arxiv.org/abs/2410.07095) (ICLR 2025) | **Repo**: https://github.com/openai/mle-bench
- **Key results**: o1-preview + AIDE = 16.9% medal rate; AIDE vs MLAB = **11x gap** (same model)
- **Local**: `data/MLE-bench`

### RE-Bench
Research engineering benchmark.
- **Paper**: METR 2024 | **Repo**: https://github.com/METR/RE-Bench
- **Domain**: Research engineering tasks requiring extended autonomous work
- **Local**: `data/RE-Bench`

### PaperBench
AI paper reproduction with hierarchical scoring.
- **Paper**: [arXiv:2504.01848](https://arxiv.org/abs/2504.01848) (ICML 2025) | **Repo**: https://github.com/openai/frontier-evals (`project/paperbench/`)
- **Scale**: 20 ICML papers, 8,316 subtasks | **Key**: Best AI 21-43% vs human PhD 41.4%
- **Local**: `data/PaperBench`

### ACADREASON
Research-level academic reasoning.
- **Paper**: [arXiv:2510.11652](https://arxiv.org/abs/2510.11652) | **Repo**: https://github.com/OPPO-PersonalAI/Acadreason-benchmark
- **Scale**: 50 questions (CS, Econ, Law, Math, Philosophy) | **Key**: GPT-5 16%, OAgents 34%
- **Local**: `data/ACADREASON`

### PaperArena
Scientific literature agentic reasoning.
- **Paper**: [arXiv:2510.10909](https://arxiv.org/abs/2510.10909) | **Repo**: https://github.com/Melmaphother/PaperArena
- **Local**: `data/PaperArena`

### WindowsAgentArena
Windows desktop agent benchmark.
- **Paper**: ICML 2025 | **Repo**: https://github.com/microsoft/WindowsAgentArena
- **Authors**: Microsoft
- **Domain**: Windows OS desktop task automation
- **Local**: `data/WindowsAgentArena`

### EmbodiedBench
Embodied AI benchmark.
- **Paper**: ICML 2025 Oral | **Repo**: https://github.com/EmbodiedBench/EmbodiedBench
- **Domain**: Embodied cognition in dynamic scenarios
- **Local**: `data/EmbodiedBench`

### VisualAgentBench
Visual foundation agent benchmark.
- **Paper**: ICLR 2025 | **Repo**: https://github.com/THUDM/VisualAgentBench
- **Domain**: Embodied (OmniGibson, Minecraft), GUI (Mobile, WebArena), Visual Design (CSS)
- **Local**: `data/VisualAgentBench`

### Terminal-Bench
Terminal/CLI agent benchmark.
- **Paper**: ICLR 2026 | **Repo**: https://github.com/laude-institute/terminal-bench
- **Domain**: Command-line interface task automation
- **Local**: `data/Terminal-Bench`

---

## E. Multi-Agent Coordination Benchmarks

### MARBLE
First comprehensive LLM multi-agent coordination benchmark.
- **Paper**: ACL 2025 | **Repo**: https://github.com/MultiagentBench/MARBLE
- **Scale**: 6 scenarios (research, Minecraft, database, coding, Werewolf, bargaining) × 4 topologies (star, chain, tree, graph)
- **Key findings**: Graph topology best; **scaling ceiling at 3 agents**; performance peaks at 7 iterations then drops
- **Local**: `data/MARBLE`

### SwarmBench
Decentralized swarm coordination for LLMs.
- **Paper**: [arXiv:2505.04364](https://arxiv.org/abs/2505.04364) | **Repo**: https://github.com/RUC-GSAI/YuLan-SwarmIntell
- **Scale**: 5 tasks (pursuit, synchronization, foraging, flocking, transport), 13 LLMs, 5×5 local perception
- **Key findings**: Physical coordination predicts success far better than semantic communication; o4-mini leads
- **Local**: `data/SwarmBench`

### Collaborative Gym
Human-agent collaboration framework via POMDP.
- **Paper**: ICLR 2026 | **Repo**: https://github.com/SALT-NLP/collaborative-gym
- **Scale**: 3 tasks (travel planning, related work writing, tabular analysis), asynchronous non-turn-taking
- **Key findings**: Collaborative agents win 86% (travel), 74% (data), 66% (writing) over autonomous; **65% cases show communication failures**
- **Local**: `data/CollaborativeGym`

### SMACv2
Gold standard for cooperative multi-agent reinforcement learning.
- **Paper**: NeurIPS 2023 | **Repo**: https://github.com/oxwhirl/smacv2
- **Scale**: 18 scenario configurations (5v5 to 20v23), 3 races, procedural generation
- **Key innovations**: Extended Partial Observability (EPO) — parameter p controls information asymmetry, creating genuine communication requirements
- **Local**: `data/SMACv2`

### Melting Pot
Largest open-source benchmark for general-sum Markov games.
- **Paper**: NeurIPS 2024 | **Repo**: https://github.com/google-deepmind/meltingpot
- **Scale**: 50+ substrates, 256+ test scenarios, 2-16 agents
- **Key innovations**: Focal/background population protocol tests social generalization; mixed-motive design; NeurIPS 2023 contest — only 11% beat baselines
- **Local**: `data/MeltingPot`

---

## F. Scientific Research Benchmarks

### AstaBench
Most comprehensive scientific agent benchmark (ICLR 2026 Oral).
- **Paper**: ICLR 2026 Oral | **Repo**: https://github.com/allenai/asta-bench
- **Scale**: 11 sub-benchmarks across 4 categories: literature understanding (4), coding/execution (3), data analysis (1), end-to-end discovery (2)
- **Key findings**: Best overall 53.0%; literature QA ~85-90%; code execution <25%; **E2E discovery <1% completion rate**; open-source models only 11.1%
- **Local**: `data/AstaBench`

### ScienceAgentBench
Language agents for data-driven scientific discovery.
- **Paper**: [arXiv:2410.05080](https://arxiv.org/abs/2410.05080) (ICLR 2025) | **Repo**: https://github.com/OSU-NLP-Group/ScienceAgentBench
- **Scale**: 102 tasks from 44 papers, 4 disciplines, 9 SME validators
- **Local**: `data/ScienceAgentBench`

### InfiAgent-DABench
Data analysis agent benchmark.
- **Paper**: ICML 2024 | **Repo**: https://github.com/InfiAgent/InfiAgent
- **Domain**: Automated data analysis tasks
- **Local**: `data/InfiAgent-DABench`

### DSBench
Data science benchmark.
- **Paper**: ICLR 2025 | **Repo**: https://github.com/LiqiangJing/DSBench
- **Domain**: End-to-end data science tasks
- **Local**: `data/DSBench`

### ChemBench
Chemistry knowledge and reasoning.
- **Paper**: Nature Chemistry 2025 | **Repo**: https://github.com/lamalab-org/chembench
- **Key finding**: LLMs have surpassed the best human chemists
- **Local**: `data/ChemBench`

### LAB-Bench
Literature, databases, sequences, and protocols.
- **Paper**: [arXiv:2407.10362](https://arxiv.org/abs/2407.10362) | **Repo**: https://github.com/Future-House/LAB-Bench
- **Authors**: FutureHouse | **Scale**: 2,400+ questions, 5 subdomains
- **Local**: `data/LAB-Bench`

### BixBench
Comprehensive computational biology benchmark.
- **Paper**: [arXiv:2503.00096](https://arxiv.org/abs/2503.00096) | **Repo**: https://github.com/Future-House/BixBench
- **Scale**: 205 questions from 53 capsules (RNA-seq, genomics, phylogenetics, single-cell, etc.)
- **Key results**: Claude 3.5 Sonnet 17%, GPT-4o 9%, K-Dense Analyst 29.2%
- **Local**: `data/BixBench`

### HeurekaBench
AI Co-scientist framework (single-cell biology).
- **Paper**: [arXiv:2601.01678](https://arxiv.org/abs/2601.01678) (ICLR 2026) | **Repo**: https://github.com/mlbio-epfl/HeurekaBench
- **Scale**: 50 OEQ + 50 MCQ, 13 Nature/Cell papers, 44GB data
- **Key results**: Best planner 2.58/5.0; end-critic +22% for open-source models
- **Local**: `data/HeurekaBench`

### MedAgentBench
Virtual EHR environment for medical LLM agents.
- **Paper**: [NEJM AI 2025](https://ai.nejm.org/doi/full/10.1056/AIdbp2500144) | **Repo**: https://github.com/stanfordmlgroup/MedAgentBench
- **Scale**: 300 tasks, 10 categories, 700K+ data elements
- **Key results**: Claude 3.5 Sonnet 69.7%, GPT-4o 64.0%
- **Local**: `data/MedAgentBench` (benchmark), `data/MedAgentBench-dev` (AgentBench framework)

### InnovatorBench
Scientific innovation benchmarking.
- **Paper**: ICLR 2026 | **Repo**: https://github.com/GAIR-NLP/InnovatorBench
- **Domain**: Evaluating LLM ability to generate novel research ideas
- **Local**: `data/InnovatorBench`

### DeepResearchBench
Deep research evaluation benchmark.
- **Paper**: ICLR 2026 | **Repo**: https://github.com/Ayanami0730/deep_research_bench
- **Domain**: End-to-end deep research capability evaluation
- **Local**: `data/DeepResearchBench`

### LiveResearchBench
Citation-grounded deep research evaluation.
- **Paper**: ICLR 2026 | **Repo**: https://github.com/SalesforceAIResearch/LiveResearchBench
- **Scale**: 100 expert-curated deep research tasks, 17 systems evaluated
- **Key findings**: Multi-agent 69.5 > single-agent Deep Research 66.4 > Web Search 62.8; multi-agent wins on citation association (61.9 vs 52.9); even best systems have 13-92 unsupported claims per report
- **Local**: `data/LiveResearchBench`

---

## G. Code Benchmarks

### BigCodeBench
Large-scale code evaluation.
- **Repo**: https://github.com/bigcode-project/bigcodebench
- **Domain**: Diverse code generation tasks with complex function calls
- **Local**: `data/BigCodeBench`

### LiveCodeBench
Contamination-free code evaluation.
- **Paper**: ICLR 2025 | **Repo**: https://github.com/LiveCodeBench/LiveCodeBench
- **Key**: Continuously updated with new problems to prevent contamination
- **Local**: `data/LiveCodeBench`

---

## H. Meta-evaluation & Efficiency

### OckBench
Token efficiency measurement for LLM reasoning.
- **Paper**: [arXiv:2511.05722](https://arxiv.org/abs/2511.05722) (NeurIPS 2025 WS) | **Dataset**: https://huggingface.co/datasets/ockbench/ockbench
- **Scale**: 400 problems (math + coding)
- **Key finding**: 5.0x token variance between similar-accuracy models
- **Local**: `data/OckBench` (from HuggingFace)

### AutoLibra
Automatic metric induction from human feedback.
- **Paper**: [arXiv:2505.02820](https://arxiv.org/abs/2505.02820) | **Repo**: https://github.com/Open-Social-World/autolibra
- **Key**: Discovers expert-missed metrics; 95% human agreement
- **Local**: `data/AutoLibra`

### LiveBench
Continuously updated, contamination-resistant benchmark.
- **Paper**: ICLR 2025 Spotlight | **Repo**: https://github.com/LiveBench/LiveBench
- **Key**: Monthly updates with new questions to avoid data leakage
- **Local**: `data/LiveBench`

### JudgeBench
Evaluating LLM-as-judge capability.
- **Paper**: ICLR 2025 | **Repo**: https://github.com/ScalerLab/JudgeBench
- **Domain**: How well can LLMs serve as evaluation judges
- **Local**: `data/JudgeBench`

### ImpossibleBench
Testing LLMs on unanswerable/impossible questions.
- **Paper**: ICLR 2026 | **Repo**: https://github.com/safety-research/impossiblebench
- **Key**: Can models correctly refuse when a question has no valid answer?
- **Local**: `data/ImpossibleBench`

### MAESTRO
Multi-Agent Evaluation Suite for Testing, Reliability, and Observability.
- **Paper**: [arXiv:2601.00481](https://arxiv.org/abs/2601.00481) | **Repo**: https://github.com/sands-lab/maestro
- **Scale**: 12 MAS across 4 frameworks (LangGraph, AutoGen, ADK, MCP-Agent), 40+ trace attributes
- **Key finding**: **Architecture dominates over model choice** — upgrading LLMs doesn't reliably improve MAS performance; 75.17% of failures are silent semantic errors
- **Local**: `data/MAESTRO`

### HAL Harness
Holistic Agent Leaderboard — unified multi-benchmark evaluation.
- **Paper**: ICLR 2026 | **Repo**: https://github.com/princeton-pli/hal-harness
- **Scale**: 9 benchmarks, 4 domains, 21,730 agent rollouts, ~$40K total cost, 2.5B tokens
- **Key findings**: Scaffold selection as important as model selection; more reasoning effort decreases accuracy in 21/36 configs; agents can be 100× more expensive but only 1% better
- **Local**: `data/HAL-Harness`

### InspectAI
UK AI Safety Institute evaluation framework.
- **Repo**: https://github.com/UKGovernmentBEIS/inspect_ai
- **Domain**: Extensible framework for LLM evaluation with 100+ built-in evals; foundation for AstaBench
- **Local**: `data/InspectAI`

### InspectEvals
Community evaluation collection for InspectAI.
- **Repo**: https://github.com/UKGovernmentBEIS/inspect_evals
- **Scale**: 100+ community-contributed evaluations across safety, reasoning, coding, agents
- **Local**: `data/InspectEvals`

### OpenHands Benchmarks
Multi-benchmark evaluation harness for code agents.
- **Repo**: https://github.com/All-Hands-AI/OpenHands
- **Scale**: 15+ benchmarks including SWE-bench, HumanEvalFix, GPQA, MATH, etc.
- **Domain**: Unified evaluation for OpenHands code agent framework
- **Local**: `data/OpenHands-Benchmarks`

---

## I. Safety

### AgentSecurityBench
Agent security evaluation benchmark.
- **Paper**: ICLR 2025 | **Repo**: https://github.com/agiresearch/ASB
- **Domain**: 10 attack scenarios, 10 LLM agents, 400+ test cases
- **Local**: `data/AgentSecurityBench`
